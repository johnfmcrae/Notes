# Steps to Making a Gain Plugin

## Step 1: Add a Slider

UI components are constructed in the `PluginEditor` files. To create the slider, define it in `PluginEditor.h`,

``` cpp
class Distortion01AudioProcessorEditor  : public juce::AudioProcessorEditor
{
public:
    Distortion01AudioProcessorEditor (Distortion01AudioProcessor&);
    ~Distortion01AudioProcessorEditor() override;

    //==============================================================================
    void paint (juce::Graphics&) override;
    void resized() override;

private:
    juce::Slider gainSlider; // ADD SLIDER HERE
    Distortion01AudioProcessor& audioProcessor;

    JUCE_DECLARE_NON_COPYABLE_WITH_LEAK_DETECTOR (Distortion01AudioProcessorEditor)
};
```

Next, let's add some customization ot our slider by going to the plugin editor's constructor in `PluginEditor.cpp`

```cpp
Distortion01AudioProcessorEditor::Distortion01AudioProcessorEditor (Distortion01AudioProcessor& p)
    : AudioProcessorEditor (&p), audioProcessor (p)
{
    // Add some slider customization
    gainSlider.setSliderStyle(juce::Slider::SliderStyle::LinearVertical);
    gainSlider.setRange(0.0f, 1.0f, 0.01f);
    gainSlider.setValue(0.05f);
    gainSlider.setTextBoxStyle(juce::Slider::TextBoxBelow, true, 50, 20);
    setSize (200, 300);
}
```

Using member functions of `juce::Slider`, we've changed the style to a linear vertical slider, changed the range from 0 to 1 with a 0.01 step size and made the default 0.5. Finally, we moved the text box which shows the slider values below the slider. Notice that the `.setSliderStyle` function takes an object of type [`Slider::SliderStyle`](https://docs.juce.com/master/classSlider.html#af1caee82552143dd9ff0fc9f0cdc0888), which is an **`enum`** which holds variables to a bunch of slider styles. In this case, we have chosen a linear vertical slider.

Next, we have to let the process editor know that we've added a slider. To do this, we need to invoke the  `addAndMakevisible` function, passing into it our slider variable,

```cpp
Distortion01AudioProcessorEditor::Distortion01AudioProcessorEditor (Distortion01AudioProcessor& p)
    : AudioProcessorEditor (&p), audioProcessor (p)
{
    gainSlider.setSliderStyle(juce::Slider::SliderStyle::LinearVertical);
    gainSlider.setRange(0.0f, 1.0f, 0.01f);
    gainSlider.setValue(0.05f);
    // Add the slider to the window
    addAndMakeVisible(gainSlider);
    
    setSize (200, 300);
}
```

Next, we'll change some of the contents of the `paint` function in the plugin editor. By default, the `paint` function will print "Hello World!" in the middle of the plugin. We'll erase that and instead, start by asking it to paint the plugin background black,

```cpp
void Distortion01AudioProcessorEditor::paint (juce::Graphics& g)
{
    g.fillAll(juce::Colours::black);
}
```

Now we can tell the plugin editor where to put the slider by going to the `resized` function.

```cpp
void Distortion01AudioProcessorEditor::resized()
{
    gainSlider.setBounds(getWidth()/2 - 50, getHeight()/2 - 75, 100, 150);
}
```

We've used the `setBounds()` function, which takes absolute pixel values, but then called the `getWidth()` and `getHeight()` functions of the window to position the slider relative to the plugin window.

## Step 2: Process the Audio

Start by adding a gain varaible to the `PluginProcessor.h` file, under `public` so that it can be accessed by the plugin editor later on,

```cpp
class Distortion01AudioProcessor  : public juce::AudioProcessor
{
public:
// ... auto-generated code

    // our variables go here
    float gainVal {0.5};
    
private:
    //==============================================================================
    JUCE_DECLARE_NON_COPYABLE_WITH_LEAK_DETECTOR (Distortion01AudioProcessor)
};
```

Next, we can modify the audio stream passing through the plugin by going to the `processBlock` in `PluginProcessor.cpp`. Take out the auto-generated comments and add a for loop to cycle through the samples in the audio buffer,

```cpp
void Distortion01AudioProcessor::processBlock (juce::AudioBuffer<float>& buffer, juce::MidiBuffer& midiMessages)
{
    juce::ScopedNoDenormals noDenormals;
    auto totalNumInputChannels  = getTotalNumInputChannels();
    auto totalNumOutputChannels = getTotalNumOutputChannels();

    for (auto i = totalNumInputChannels; i < totalNumOutputChannels; ++i)
        buffer.clear (i, 0, buffer.getNumSamples());
    
    for (int channel = 0; channel < totalNumInputChannels; ++channel)
    {
        auto* channelData = buffer.getWritePointer (channel);
        
        // added this loop
        for (int sample = 0; sample < buffer.getNumSamples(); ++sample)
        {
            channelData[sample] *= gainVal;
        }

    }
}
```

We are multiplying each sample by the gain amount to adjust the signal level.

## Step 3: Connecting the Slider to the Gain Variable

We can now connect the slider to the gain variable in the signal processor. The simplest way to connect the slider to the processor is to add a `juce::Slider::Listener` to the inheritance of the processor editor. The `Slider::Listener` class contains virtual functions, so we also need to provide their representation for our application (see the note on [virtual](../C++/Virtual.md)). In `ProcessEditor.h`,

```cpp
class Distortion01AudioProcessorEditor  : public juce::AudioProcessorEditor,
                                          public juce::Slider::Listener
{
public:
    Distortion01AudioProcessorEditor (Distortion01AudioProcessor&);
    ~Distortion01AudioProcessorEditor() override;

    //==============================================================================
    void paint (juce::Graphics&) override;
    void resized() override;

    // listener representation
    void sliderValueChanged (Slider *slider) override;

private:
    juce::Slider gainSlider;
    Distortion01AudioProcessor& audioProcessor;

    JUCE_DECLARE_NON_COPYABLE_WITH_LEAK_DETECTOR (Distortion01AudioProcessorEditor)
};
```

And then in `PluginEditor.cpp` we write our implementation,

```cpp
void Distortion01AudioProcessorEditor::sliderValueChanged (Slider *slider)
{
    if (slider == &gainSlider)
    {
        audioProcessor.gainValue = gainSlider.getValue();
    }

}
```

Let's break down that if statement. First, we are making sure that the slider input to the function is indeed our gain slider. Then, we make use of the audio processor variable which JUCE has already created for use, called `audioProcessor`. The processor variable holds an address to our processor class so that we can access it from the editor. Now, since what we want to be adjusting is the gain value, we use `audioProcessor.gainValue` and finally, we can give that variable the value from the slider using the `getValue()` function.

Next, an important and easy to forget step that we cannot must do is that we need to make the gain slider a listener in the plugin editor constructor. So, in `PluginEditor.cpp`,

```cpp
Distortion01AudioProcessorEditor::Distortion01AudioProcessorEditor (Distortion01AudioProcessor& p)
    : AudioProcessorEditor (&p), audioProcessor (p)
{
    gainSlider.setSliderStyle (juce::Slider::SliderStyle::LinearVertical);
    gainSlider.setRange (0.0f, 1.0f, 0.01f);
    gainSlider.setValue (0.05f);
    gainSlider.setTextBoxStyle (juce::Slider::TextBoxBelow, true, 50, 20);
    // add the listener
    gainSlider.addListener (this);
    addAndMakeVisible(gainSlider);

    setSize (200, 300);
}
```
