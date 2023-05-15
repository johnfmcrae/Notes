# JUCE GUI Basics

## Adding a Window to an Application

Let's say you create a new JUCE application using the Projucer. The template  that you get has the basic code you need to run an app, but it does not include any windows. To make a window, you can create a class within the main application class which extends the `juce::DocumentWindow` class.

``` cpp
    class MainWindow : public juce::DocumentWindow
    {
    public:
        MainWindow (juce::String name) : DocumentWindow (name,
            juce::Colours::lightgrey,
            DocumentWindow::allButtons)
        {
            centreWithSize(300, 200);
            setVisible(true);
        }

        void closeButtonPressed() override
        {
            juce::JUCEApplication::getInstance()->systemRequestedQuit();
        }
    private:
        JUCE_DECLARE_NON_COPYABLE_WITH_LEAK_DETECTOR (MainWindow)
    };
```

In our above example class, we have a constructor, an override for the closed button and we have set the class to be non copyable with leak detection. To launch the window on application startup, add the following line to the main window's initialise method,

```cpp
    void initialise (const juce::String& commandLine) override
    {
        // Add your application's initialisation code here..
        mainWindow.reset(new MainWindow(getApplicationName()));
    }
```

Notice that there are three required arguments for the `DocumentWindow` constructor: window name, window colour, and title bar buttons. In the above case, we have all three of the common window bar buttons: minimize, maximize, and close. However, we can choose from `DocumentWindow::minimiseButton`, `DocumentWindow::maximiseButton`, and `DocumentWindow::closeButton` and combine whichever we like using the bar operator (|).

[contents](_main_JUCE_notes.md)
