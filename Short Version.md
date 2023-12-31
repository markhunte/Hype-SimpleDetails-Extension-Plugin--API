SHORT VERSION.

# Hype SimpleDetails Extension Plugin API Documentation

## Introduction

This documentation explains how to use the Hype SimpleDetails Extension plugin API.

The extension enables you to create HTML detail/summary elements in Tumult Hype projects using text boxes in scenes, making it easy to display additional information interactively on your web pages.

## Installation

To use this script, follow these steps:

1. Open your Tumult Hype project.
2. Go to the "Head HTML" section of your project.
3. Paste the provided script into the "Head HTML" section.

## Setting Up Your Elements

To use the Hype SimpleDetails Extension, set up your elements as follows:

1. Place text boxes in your scenes where you want to add detail/summary elements.
2. Add the `data-disclosure` attribute to each text box to designate it as a details element.
3. Add a second attribute, `data-id`, to each text box. This attribute will serve as a unique ID for each text box.

### Example Data-Id Key and Values

Here are some examples of `data-id` keys and values:

- Text box 1 has `data-disclosure` and `data-id` with the value of "foo1." This unique `data-id` value identifies the text box.
- Text box 2 has `data-disclosure` and `data-id` with the value of "foo2." This unique `data-id` value identifies another text box with the ID "foo2."

## Symbol Instances

When using detail/summary text box elements inside symbol instances, follow these guidelines:

- Give each symbol instance the `data-id` attribute instead of giving individual text boxes inside it.
- Ensure each symbol instance has a unique `data-id` value to distinguish it from other instances of the same symbol.

### Example Data-Id Key and Values for Symbol Instances

Here are some examples of `data-id` keys and values for symbol instances:

- One instance of a symbol named "symbolFoo" has `data-id` with the value of "symFoo1." This unique `data-id` value identifies this symbol instance.
- A second instance of the "symbolFoo" symbol has `data-id` with the value of "symFoo2." This unique `data-id` value identifies another symbol instance.

## Constructing API Calls

To create detail/summary elements, construct API calls by defining the following variables:

- `targetElement`: The value of either the containing symbol or the standalone text box's `data-id` attribute.
- `descriptionText`: The literal formatted text for the detail/summary (or plain text if preferred).
- `options`: Optional settings to style the resulting detail/summary.

### API Options

Here are some key API options:

- `splitTextAtWordNumber`: Specifies the number of leading words to display before the "Show more" button appears in the detail/summary element.
- `leadingTextColor`: Allows you to set the color for the leading summary text in the detail/summary element.
- `followingTextColor`: Lets you set the color for the following summary text in the detail/summary element.
- `fontSize`: Allows you to set the font size for the text within the detail/summary element.
- `acceptsAutoClose`: By default, details close independently. Set this option to `true` to make details with the same option close when others are opened.

### Global Auto Close Control

To globally control auto-closing behavior, use the API call `hypeDocument.descriptionAutoClose(true/false)`:

- `true`: Auto-closing is on (details with `acceptsAutoClose` will close others).
- `false`: Auto-closing is off (details will remain open independently).

Example JavaScript:

```javascript
if (element.id == 'turnoff') {
  hypeDocument.descriptionAutoClose(false);
} else {
  hypeDocument.descriptionAutoClose(true);
}
```

This script toggles auto-closing behavior on or off for details that have the `acceptsAutoClose` option set.

By following these steps, you can easily add and customize detail/summary elements in your Tumult Hype project using the Hype SimpleDetails Extension Plugin API.
