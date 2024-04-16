# Explaining function of each component



## Components folder


-------------------------------

### /assets

Include photos for the background and some subcomponent icons such as password.  

To change the background, we need to modify the path in the `Dashboard.jsx` under `common` package and `index.css` under `src` folder.

--------------------------------------------

### /auth

#### LoginRegister.jsx
The `LoginRegister` component is used to handle user login and registration functionality.
##### Within the `LoginRegister.jsx` file:
State:
1. **action:** Tracks the current action, i.e., login or register.
2. **openDialogL** and **openDialogR:** Control the opening and closing of dialogs for login and registration.
3. **loginSuccess** and **registerSuccess:** Track whether login and registration were successful.
4. **loginJump:** Flags whether to navigate to the next page after a successful login.
5. **username and password:** Store the user-inputted username and password.
6. **navigate:** Used for navigation in React Router.

Functions:
1. **handleSubmit():** Handles the submission of login or registration forms. Sends login or registration requests to the backend using the axios library.
2. **handleLoginOpenSuccDialog()** and **handleLoginOpenFailDialog()**: Control the opening of dialogs for successful and failed logins.
3. **handleLoginCloseDialog():** Closes the login dialog and navigates to the next page after a successful login.
4. **onRetake():** Handles the navigation logic after a successful login, storing user information in local storage, and navigating to the 'camera' page.
5. **handleRegisterOpenSuccDialog()** and **handleRegisterOpenFailDialog():** Control the opening of dialogs for successful and failed registrations.
6. **handleRegisterCloseDialog():** Closes the registration dialog.

--------------------------------

### /challenge


#### subcomponents


##### Challenge.jsx
This functional component named `Challenge` is part of a React application utilizing the Material-UI library `(@mui/material)`. It represents a section within the application and is responsible for displaying icons for various actions and a placeholder for challenge content.

###### Within the `Challenge.jsx` file:
Functional Component:
- The component is exported as the default export.
- It is a functional component, which means it doesn't have internal state or lifecycle methods.
- The component returns JSX representing the UI structure.

Rendered Structure:
- The component renders a `Box` component containing two main sections: Action buttons and Challenge content.
- Action buttons section:
    1. Displays a row of buttons using the `Box` component and inline styles.
    2. Includes a `CameraAltIcon` button with the color set to 'success'.
    3. Includes two more buttons (`BoltIcon` and `RecyclingIcon`) inside a `Box` with specific styling.
- Challenge content section:
    1. Displays a placeholder for challenge content, which in this case is an `Avatar` component
    2. The `Box` containing the placeholder has specific styling for layout and positioning.

-------------------------------------

##### ChallengeDetail.jsx

###### Within the `ChallengeDetail.jsx` file:
Function:
`showCamera()`: 
- Description: Navigates to the camera route ("/camera") when called.
- Usage: Triggered by the "response" button click.

Parameters:
1. **`challenge` (Object):** The challenge object containing details to be displayed.
2. **`other` (Boolean):**  Indicates whether the challenge is from the "Other Challenges" section.
3. **`onlyPreview` (Boolean):** Indicates whether the component is for preview only, limiting the display of certain action buttons.

------------------------------------------

##### ChallengesList.jsx

###### Within the `ChallengesList.jsx` file:

Parameters:
1. **`challenges` (Array):** List of challenges to be displayed.
2. **`onClickMyChallenge` (Function):**: Callback function triggered when the "Look" button is clicked.
3. **`challenge (Object):**  Currently selected challenge.

Component Structure:
The component renders a list of challenges using the provided challenges array. Each challenge is displayed within a `Card` component, including an `Avatar`, challenge title, description, and a "Look" button. The appearance of the "Look" button is determined by comparing the challenge's ID with the currently selected challenge's ID.

-------------------------------

#### my-challenges.jsx

##### Within the `my-challenges.jsx` file:

Functions:
- **`handleLook()`:** Handles the click event when a challenge is selected to view details. Sets the selected challenge and enters the look mode.
    - `target` (Object): The selected challenge object.

Parameters:
1. **`challenges` (Array):** List of challenges to be displayed.
2. **`challenge` (Object):** Currently selected challenge.
3. **`isLook` (Boolean):** Indicates whether the component is in look mode.
4. **`setChallenge` (Function):** Setter function for the challenge state.
5. **`setIsLook` (Function):** Setter function for the isLook state.
6. **`navigate` (Function):** React Router hook for programmatic navigation.

Component Structure:
The component renders a list of challenges (`ChallengesList`) and allows users to view details. It manages state variables for the selected challenge and look mode. Depending on the look mode, it either displays the details of the selected challenge (`ChallengeDetail`) or the list of challenges (`ChallengesList`).

------------------------------------

#### other-challenges.jsx
##### Within the `other-challenges.jsx` file:

Functions:
- **`handleLook()`:** Handles the click event when a challenge is selected to view details. Sets the selected challenge and enters the look mode.
    - `target` (Object): The selected challenge object.

Parameters:
1. **`challenges` (Array):** List of challenges to be displayed.
2. **`challenge` (Object):** Currently selected challenge.
3. **`isLook` (Boolean):** Indicates whether the component is in look mode.
4. **`setChallenge` (Function):** Setter function for the challenge state.
5. **`setIsLook` (Function):** Setter function for the isLook state.

Component Structure:
The component renders a list of challenges (`ChallengesList`) and allows users to view details. It manages state variables for the selected challenge and look mode. Depending on the look mode, it either displays the details of the selected challenge (`ChallengeDetail`) or the list of challenges (`ChallengesList`).

----------------------
### /common

#### Dashboard.jsx
The `Dashboard` component is a React component that serves as the main dashboard layout. It consists of a `Paper` component with a background image, containing two main sections: `Playground` and either `MyChallenges` or `Studio` based on the active module.
##### Within the `Dashboard.jsx` file:

Functions:
1. **`onClickChallenge()`:** Callback function triggered when clicking the "Challenge" button in the `Playground` component. Usage: Updates the `module` state to switch to the 'challenge' module.
2. **`onClickMyChallenge()`:** Callback function triggered when clicking the "MyChallenges" button in the `Playground` component. Usage: Updates the `module` state to switch to the 'studio' module.

State:
1. **`module (String):`:** State variable to manage the active module, either 'studio' or 'challenge'.

--------------------------------

#### layout.jsx
The `layout` component is a React layout component for the application, providing a common structure for different pages. It includes a header section with tabs for navigating between different sections of the application.
##### Within the `layout.jsx` file:

Functions:
**`isActive()`:** Determines if a given pathname is currently active.

Custom Hooks:
1. **`useNavigate` (Custom Hook):** A custom hook from `react-router-dom` used for programmatic navigation.
2. **`useLocation` (Custom Hook):** A custom hook from `react-router-dom` used to get the current location.

--------------------------------

#### Playground.jsx
The `Playground` component is a React component that displays uploaded challenges along with a vertical logo and a challenge list.
##### Within the `Playground.jsx` file:

Component Properties:
**`onClickChallenge()`:** A function to be called when clicking on a challenge.

External Assets:
**`Logo` (Image):** An image asset representing a vertical logo.

--------------------------------------------
### /hooks

#### useMyChallenges.jsx
The `useMyChallenges` custom hook is designed to handle fetching and managing challenges specifically for the `MyChallenges` component.
##### Within the `useMyChallenges.jsx` file:

State:
**`challenges` (Array):** State to store the array of challenges. Initially set to an empty array. Updated by the `setChallenges` function when challenges are fetched.

-----------------------------------

#### useOtherChallenges.jsx
The `useOtherChallenges` custom hook is designed to handle fetching and managing challenges for components other than `MyChallenges`.
##### Within the `useOtherChallenges.jsx` file:

State:
**`challenges` (Array):** State to store the array of challenges. Initially set to an empty array. Updated by the `setChallenges` function when challenges are fetched.

--------------------------------------
### /studio

#### UploadChallenge.jsx
The `UploadChallenge` component handles the process of adding a challenge, including selecting an intended object, entering a caption, and uploading the challenge. 
##### Within the `Dashboard.jsx` file:

Functions:
1. **`uploadChallenge()`:** Sends challenge data to the backend.
2. **`handleOptionChange()`:** Handles the selection of an intended object from the dropdown.
3. **`handleCustomOptionChange()`:** Handles changes in the custom option input.
4. **`handleOpenDialog()`:** Opens the success dialog.
5. **`handleCloseDialog()`:**  Closes the success dialog and executes the `onRetake` callback.

State Variables:
1. **`option` (String):** Represents the selected intended object.
2. **`customOption` (String):** Represents the custom object input.
3. **`caption` (String):** Represents the caption entered by the user.
4. **`openDialog` (Boolean):** Controls the visibility of the success dialog.

--------------------------------------------

#### CapturePhoto.jsx
The `CapturePhoto` component manages capturing photos from the user's camera, handling camera access, switching between cameras, and identifying objects in the captured image using AI. 
##### Within the `CapturePhoto.jsx` file:

Functions:
1. **`getCameraAccess()`:** Requests access to the user's camera.
2. **`switchCamera()`:** Switches between the front and back camera.
3. **`getAIIdentification()`:** Sends the captured image to the backend for object identification.
4. **`captureImage()`:** Captures an image from the video stream and triggers callbacks for handling the image and identified objects.


State Variables:
1. **`currentCamera` (String):**  Represents the currently active camera (`'user'` for front camera, `'environment'` for back camera).
2. **`cameraEnable` (Boolean):** Represents whether camera access is enabled.

Refs:
1. **`videoRef`:**  Ref for the video element.
2. **`canvasRef`:** Ref for the canvas element used to draw the captured image.

useEffect Hook:
- **Camera Access Effect:** Represents the selected intended object.

----------------------------------------------

#### Studio.jsx
`Studio` component manages the process of capturing a photo and subsequently adding a challenge. It uses the `CapturePhoto` and `UploadChallenge` components for this purpose. 
##### Within the `Studio.jsx` file:

Functions:
**`handleRetake()`:** Resets the `image` and `objectsArray` states to `null`.


State Variables:
1. **`image` (String):**  Represents the captured image in base64 format.
2. **`objectsArray` (Array):** Represents an array of objects identified in the captured image.

------------------------------------------
## /Main


### App.js
`App` is set up using React Router and consists of different routes for handling authentication, challenges, and the studio. 
##### Within the `App.js` file:
Components Used:
1. **`LoginRegister`Component:**  Handles authentication and serves as the landing page.
2. **`MyChallenges` Component:**  Displays challenges specific to the logged-in user.
3. **`Studio` Component:** Represents the studio where users can capture and upload challenges.
4. **`OtherChallenges` Component:** Displays challenges created by other users.
