# Ex05 Image Carousel
## NAME: SRILAKSHMI BH
## Date: 26/05/2026

## AIM
To create a Image Carousel using React 

## ALGORITHM
### STEP 1 Initial Setup:
Input: A list of images to display in the carousel.

Output: A component displaying the images with navigation controls (e.g., next/previous buttons).

### Step 2 State Management:
Use a state variable (currentIndex) to track the index of the current image displayed.

The carousel starts with the first image, so initialize currentIndex to 0.

### Step 3 Navigation Controls:
Next Image: When the "Next" button is clicked, increment currentIndex.

If currentIndex is at the end of the image list (last image), loop back to the first image using modulo:
currentIndex = (currentIndex + 1) % images.length;

Previous Image: When the "Previous" button is clicked, decrement currentIndex.

If currentIndex is at the beginning (first image), loop back to the last image:
currentIndex = (currentIndex - 1 + images.length) % images.length;

### Step 4 Displaying the Image:
The currentIndex determines which image is displayed.

Using the currentIndex, display the corresponding image from the images list.

### Step 5 Auto-Rotation:
Set an interval to automatically change the image after a set amount of time (e.g., 3 seconds).

Use setInterval to call the nextImage() function at regular intervals.

Clean up the interval when the component unmounts using clearInterval to prevent memory leaks.

## PROGRAM


ImageCarousel.jsx

```
import React, { useState, useEffect } from "react";

function ImageCarousel() {

  const images = [
    "https://picsum.photos/id/1015/800/400",
    "https://picsum.photos/id/1016/800/400",
    "https://picsum.photos/id/1018/800/400",
    "https://picsum.photos/id/1020/800/400"
  ];

  const [currentIndex, setCurrentIndex] = useState(0);

  const nextImage = () => {
    setCurrentIndex((currentIndex + 1) % images.length);
  };

  const prevImage = () => {
    setCurrentIndex(
      (currentIndex - 1 + images.length) % images.length
    );
  };

  useEffect(() => {
    const interval = setInterval(() => {
      nextImage();
    }, 3000);

    return () => clearInterval(interval);

  }, [currentIndex]);

  return (
    <div style={styles.container}>

      <h1 style={styles.title}>✨ Image Carousel ✨</h1>

      <div style={styles.card}>

        <img
          src={images[currentIndex]}
          alt="carousel"
          style={styles.image}
        />

        <div style={styles.buttons}>

          <button style={styles.btn} onClick={prevImage}>
            ◀ Previous
          </button>

          <button style={styles.btn} onClick={nextImage}>
            Next ▶
          </button>

        </div>

      </div>

    </div>
  );
}

const styles = {

  container: {
    display: "flex",
    flexDirection: "column",
    alignItems: "center",
    justifyContent: "center",
    minHeight: "100vh",
    background: "linear-gradient(to right, #141e30, #243b55)",
    color: "white",
    padding: "20px"
  },

  title: {
    marginBottom: "20px",
    textAlign: "center",
    fontSize: "40px"
  },

  card: {
    width: "90%",
    maxWidth: "900px",
    padding: "20px",
    borderRadius: "15px",
    background: "#1e293b",
    boxShadow: "0 0 15px black",
    textAlign: "center"
  },

  image: {
    width: "100%",
    height: "auto",
    maxHeight: "400px",
    borderRadius: "10px",
    objectFit: "cover",
    boxShadow: "0 0 10px black"
  },

  buttons: {
    marginTop: "20px",
    display: "flex",
    justifyContent: "center",
    gap: "20px",
    flexWrap: "wrap"
  },

  btn: {
    padding: "10px 25px",
    fontSize: "16px",
    borderRadius: "8px",
    border: "none",
    cursor: "pointer",
    background: "#38bdf8",
    color: "black",
    fontWeight: "bold"
  }

};

export default ImageCarousel;
```

App.jsx

```
import React from "react";
import ImageCarousel from "./ImageCarousel";

function App() {
  return (
    <div>
      <ImageCarousel />
    </div>
  );
}

export default App;
```

## OUTPUT

![alt text](image.png)

## RESULT
The program for creating Image Carousel using React is executed successfully.
