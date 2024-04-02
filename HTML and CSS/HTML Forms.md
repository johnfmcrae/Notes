# HTML Forms

## Basic Elements

The principal container for a web form is the `<form>` element. Inside that, you can group form elements inside of `<fieldset>` elements. You can also add a `<legend>` element to give the fieldset a description. The legend is also what many screen readers will read out.

Here's an example form,

```html
<form>
  <fieldset>
    <legend>Fruit juice size</legend>
    <p>
      <input type="radio" name="size" id="size_1" value="small" />
      <label for="size_1">Small</label>
    </p>
    <p>
      <input type="radio" name="size" id="size_2" value="medium" />
      <label for="size_2">Medium</label>
    </p>
    <p>
      <input type="radio" name="size" id="size_3" value="large" />
      <label for="size_3">Large</label>
    </p>
  </fieldset>
</form>
```

## Labels and Inputs

Use the `<input>` element to get data from users and the `<label>` element to tell the user what the input is expecting. Input elements are self closing.

You should associate a label with an input using the `for` and `id` attributes. Fro example,

```html
<form>
    <fieldset>
    <label for="first-name">Enter Your First Name: 
        <input id="first-name" type="text" required />
    </label>
    <label for="last-name">Enter Your Last Name: 
        <input id="last-name" type="text" required />
    </label>
    </fieldset>
</form>
```

Notice that the values of the `for` attributes match the values of the `id` attributes.

The `required` attribute makes an input required for form submission. It is a boolean attribute and does not require a value. Its presence implies a value of true.
