# How to make a Modal

This document will assist in making a modal for your app. When a user clicks a button, a modal will display. It will be displayed in the center of the screen and the background will be shaded in a darker color, so that the users attention is drawn to the content on the modal. The user will be able to dismiss or close the modal by clicking on a button that is inside the modal or by clicking anywhere in the background.

## A brief of Steps
1. Made a 'Modal' component
2. Detemine Parent component, create modal state
3. Add props to 'Modal'
4. Create `onClose` handler for Modal
5. Add some stylin' 🕶️

## Steps expanded
### Basic set up
1. Navigate to your `Components` directory, inside your `src` directory create a  `Modal.js` component.
![Modal](https://github.com/rachelspencer/makeAModal/assets/111473039/ead62ca5-6328-4af1-8ba1-4a6a7ea6a8c6)

2. You may have a button that when clicked will show this modal (amongst other things). The component that owns this button would be a good place to store the state for the modal and will track whether the modal should be displayed or not.

For this example I have an `add book` button, when a user adds a book I want this modal to pop up and display the message `Book has been added to your library!`. The user then clicks a close button inside the modal or anywhere on the screen and the modal will disapear.

First lets tackle just showing the modal and getting the modals `close` button working.

Inside the `Modal.js` component add:
- an`onClose` prop that will call a function when the user clicks the "Close" button in the modal 
- a `message` prop this will be a string that represents the messagae to be displayed inside the modal
![Modal + message   onClick](https://github.com/rachelspencer/makeAModal/assets/111473039/bd436354-7a7b-4e95-97b8-5c23bb728194)

Inside the parent component, import the component, useState and then add:
- a piece of state like `[showModal, setShowModal] = useState(false)`
- you'll want to conditinally render this Modal when the state switches to true, use JXS to render the Modal based on this and be sure to pass the `onClose` and `message` prop. I'll explain the props shortly.
![Modal conditional render](https://github.com/rachelspencer/makeAModal/assets/111473039/9e632e2d-e683-4d42-9afb-81bfbb98fcc2)

- I already have an handleClick function in my parent app, this will create a book with the results from an api call, after this I want to set the modalState to true by adding `setModalState(true)` inside this function block
- So now for the props, for the `message` prop add a string for whatever text you want to be displayed inside the Modal
- for the `onClose` prop add a `closeModal` function that will switch the modal state back to `false` when the `close` button is clicked, and ultimately close the modal window

Cool, so now you should have the modal appearing when you click the button that has `setshowModal(true)`.
<img width="1238" alt="Modal showing" src="https://github.com/rachelspencer/makeAModal/assets/111473039/15f69afa-b5d3-47a1-ab2c-dd7dca922bc3">

Thats good, but now lets add some real styling!
