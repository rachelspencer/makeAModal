# How to make a Modal

This document will assist in making a modal for your app. When a user clicks a button, a modal will display. It will be displayed in the center of the screen and the background will be shaded in a darker color, so that the users attention is drawn to the content on the modal. The user will be able to dismiss or close the modal by clicking on a button that is inside the modal or by clicking anywhere in the background.

## A brief of Steps
1. Make a 'Modal' component
2. Detemine Parent component, create modal state
3. Add props to 'Modal'
4. Add some basic styling
6. Make the modal more resusable
7. Add some stylin' 🕶️

## Steps expanded
### Make a 'Modal' component
1. Navigate to your `Components` directory, inside your `src` directory create a `Modal.js` component.
![Modal](https://github.com/rachelspencer/makeAModal/assets/111473039/ead62ca5-6328-4af1-8ba1-4a6a7ea6a8c6)

### Detemine Parent component, create modal state
You may have a button that when clicked will show this modal (amongst other things). The component that owns this button would be a good place to store the state for the modal and will track whether the modal should be displayed or not.

For this exercise I have an `add book` button, when a user adds a book I want this modal to pop up and display the message "Book has been added to your library!". The user then clicks a close button inside the modal or anywhere on the screen and the modal will disapear. If something is going to change on the screen, then its a good indication that we need to create some state. So lets do that!

Inside the parent component, import the `Modal.js` component and useState and then add:
- a piece of state like `[showModal, setShowModal] = useState(false)`
- you'll want to conditinally render this Modal when the state switches to true, use JXS to render the Modal based on this and be sure to pass the `onClose` and `message` props. I'll explain these props shortly.
![Modal conditional render](https://github.com/rachelspencer/makeAModal/assets/111473039/9e632e2d-e683-4d42-9afb-81bfbb98fcc2)

- I already have an handleClick function in my parent component, this is attached to the 'add book' button and will create a book with the results from an api call, after this I want to set the modalState to true by adding `setModalState(true)` inside this function block
- for the `onClose` prop add a `closeModal` function in the parent component that will switch the modal state back to `false` when the `close` button is clicked, and ultimately close the modal window
- for the `message` prop add a string for whatever text you want to be displayed inside the Modal

### Add props to 'Modal'
Inside the `Modal.js` component add:
- an`onClose` prop on the button div that will call `onClose` when the user clicks the "Close" button on the modal 
- a `message` prop on the `<p></p>` tag that will display the string message inside the modal
![Modal + message   onClick](https://github.com/rachelspencer/makeAModal/assets/111473039/bd436354-7a7b-4e95-97b8-5c23bb728194)

Cool, so now you should have the modal appearing when you click the button that has `setshowModal(true)` in its handler.
<img width="1238" alt="Modal showing" src="https://github.com/rachelspencer/makeAModal/assets/111473039/15f69afa-b5d3-47a1-ab2c-dd7dca922bc3">

### Add some basic styling

Lets quickly add a little bit of styling just to see how its all going. Add these `classNames`, add a `Modal.css` file and import the css file into your `Modal.js` component.
![Add styling classNames](https://github.com/rachelspencer/makeAModal/assets/111473039/aaa4642c-e954-42de-b690-40147778f0a5)

![Modal base styling](https://github.com/rachelspencer/makeAModal/assets/111473039/6448521a-ccb0-435c-956c-305b2a4f5c7a)

It should look like this now that you have some basic styling in place:
<img width="1233" alt="Modal basic styling" src="https://github.com/rachelspencer/makeAModal/assets/111473039/0a0a84cf-3776-4cc3-94df-333d8c79be0e">


### Stylin' time 🕶️
We are going to create a portal for this modal. This is so that this component will never accidently have a 'positioned' parent, which will throw out styling off and potentially not cover the whole screen. By using the portal the Modal will be positioned to the HTML doc, and therefore its parent will be the Body. 

1. Inside the `Public` folder go to the index.html file. Scroll to the bottom and above the `</body>` closing tag add thr following:
![div in index file](https://github.com/rachelspencer/makeAModal/assets/111473039/477354e6-01c7-4211-b573-800c56c7107d)

After saving, refresh the app, and inspect the page. You should see the `div` just added. This is where we want to render the `Modal`.
![check index html in the dom](https://github.com/rachelspencer/makeAModal/assets/111473039/e632a94f-23a7-49a3-8124-dada6284c569)

2. Back in the `Modal.js` component, import `ReactDom`. Edit the return statement for the `Modal` by pasting the modals content in as the first argument and then adding a query selector as the second arguement which points to where this component should render.
