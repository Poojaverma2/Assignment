# Assignment
Creating a captivating and responsive user interface for the Refer & Earn landing page using React.js involves incorporating visually appealing design elements and intuitive interactions. We'll use Material-UI for building components and achieving a modern look. Below is a detailed approach to implement the required UI components:

### 1. Setting Up the Project

First, ensure you have React and Material-UI set up in your project:

```bash
npx create-react-app refer-and-earn
cd refer-and-earn
npm install @material-ui/core @material-ui/icons
```

### 2. Building the Landing Page

#### App.js

```jsx
import React from 'react';
import { Container, Button, Typography } from '@material-ui/core';

function App() {
  const handleReferNowClick = () => {
    // Open modal here
    console.log('Open modal for referral form');
  };

  return (
    <div className="App">
      <header className="App-header">
        <Container maxWidth="sm">
          <Typography variant="h3" component="h1" align="center" gutterBottom>
            Refer & Earn Program
          </Typography>
          <Typography variant="body1" align="center" paragraph>
            Refer a friend and earn rewards when they enroll in a course!
          </Typography>
          <Button
            variant="contained"
            color="primary"
            size="large"
            onClick={handleReferNowClick}
          >
            Refer Now
          </Button>
        </Container>
      </header>
    </div>
  );
}

export default App;
```

### 3. Implementing the Popup Modal

#### ReferModal.js

```jsx
import React from 'react';
import {
  Button,
  Dialog,
  DialogActions,
  DialogContent,
  DialogTitle,
  TextField,
} from '@material-ui/core';

const ReferModal = ({ open, onClose }) => {
  const handleSubmit = (e) => {
    e.preventDefault();
    // Handle form submission here
    console.log('Form submitted');
    onClose();
  };

  return (
    <Dialog open={open} onClose={onClose}>
      <DialogTitle>Refer a Friend</DialogTitle>
      <DialogContent>
        <form onSubmit={handleSubmit}>
          <TextField
            autoFocus
            margin="dense"
            id="referrerName"
            label="Your Name"
            type="text"
            fullWidth
            required
          />
          <TextField
            margin="dense"
            id="referrerEmail"
            label="Your Email Address"
            type="email"
            fullWidth
            required
          />
          <TextField
            margin="dense"
            id="friendName"
            label="Friend's Name"
            type="text"
            fullWidth
            required
          />
          <TextField
            margin="dense"
            id="friendEmail"
            label="Friend's Email Address"
            type="email"
            fullWidth
            required
          />
          <DialogActions>
            <Button onClick={onClose} color="primary">
              Cancel
            </Button>
            <Button type="submit" color="primary">
              Refer
            </Button>
          </DialogActions>
        </form>
      </DialogContent>
    </Dialog>
  );
};

export default ReferModal;
```

### 4. Styling and Theming

You can enhance the styling using Material-UI's theme customization or Tailwind CSS classes for additional customization. Here’s a basic example of setting up a theme:

#### App.js (continued)

```jsx
import React, { useState } from 'react';
import { Container, Button, Typography } from '@material-ui/core';
import ReferModal from './ReferModal';

function App() {
  const [modalOpen, setModalOpen] = useState(false);

  const handleReferNowClick = () => {
    setModalOpen(true);
  };

  const handleCloseModal = () => {
    setModalOpen(false);
  };

  return (
    <div className="App">
      <header className="App-header">
        <Container maxWidth="sm">
          <Typography variant="h3" component="h1" align="center" gutterBottom>
            Refer & Earn Program
          </Typography>
          <Typography variant="body1" align="center" paragraph>
            Refer a friend and earn rewards when they enroll in a course!
          </Typography>
          <Button
            variant="contained"
            color="primary"
            size="large"
            onClick={handleReferNowClick}
          >
            Refer Now
          </Button>
          <ReferModal open={modalOpen} onClose={handleCloseModal} />
        </Container>
      </header>
    </div>
  );
}

export default App;
```

### 5. Form Validation

Implementing form validation can be done using libraries like Formik or by custom validation functions. Here’s a basic example using native HTML5 validation:

```jsx
<TextField
  margin="dense"
  id="referrerName"
  label="Your Name"
  type="text"
  fullWidth
  required
  inputProps={{
    pattern: "[A-Za-z\\s]*", // Example pattern for alphabetic characters and spaces
    title: "Only alphabetic characters and spaces are allowed"
  }}
/>
```
