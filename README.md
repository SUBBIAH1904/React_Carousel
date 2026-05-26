# Ex05 Image Carousel
## Date: 26/05/2026
## Name : Subbiah S
## Reg no : 212223220111

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
### index.html:
```
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Image Carousel</title>
  <style>
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background: #f3f6fb;
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
    }

    .carousel {
      width: 520px;
      max-width: 90%;
      background: white;
      padding: 20px;
      border-radius: 8px;
      box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
      text-align: center;
    }

    h1 {
      margin-top: 0;
      font-size: 24px;
      color: #222;
    }

    img {
      width: 100%;
      height: 300px;
      object-fit: cover;
      border-radius: 6px;
    }

    .buttons {
      margin-top: 16px;
      display: flex;
      justify-content: center;
      gap: 12px;
    }

    button {
      padding: 10px 18px;
      border: none;
      border-radius: 5px;
      background: #2563eb;
      color: white;
      font-size: 16px;
      cursor: pointer;
    }

    button:hover {
      background: #1d4ed8;
    }
  </style>
</head>
<body>
  <div id="root"></div>

  <script src="https://unpkg.com/react@18/umd/react.development.js"></script>
  <script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>
  <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>

  <script type="text/babel">
    function ImageCarousel() {
      const images = [
        "https://picsum.photos/id/1015/800/500",
        "https://picsum.photos/id/1025/800/500",
        "https://picsum.photos/id/1035/800/500",
        "https://picsum.photos/id/1043/800/500"
      ];

      const [currentIndex, setCurrentIndex] = React.useState(0);

      function nextImage() {
        setCurrentIndex((currentIndex + 1) % images.length);
      }

      function previousImage() {
        setCurrentIndex((currentIndex - 1 + images.length) % images.length);
      }

      React.useEffect(() => {
        const timer = setInterval(() => {
          setCurrentIndex((index) => (index + 1) % images.length);
        }, 3000);

        return () => clearInterval(timer);
      }, []);

      return (
        <div className="carousel">
          <h1>Image Carousel</h1>
          <img src={images[currentIndex]} alt="Carousel" />
          <div className="buttons">
            <button onClick={previousImage}>Previous</button>
            <button onClick={nextImage}>Next</button>
          </div>
        </div>
      );
    }

    const root = ReactDOM.createRoot(document.getElementById("root"));
    root.render(<ImageCarousel />);
  </script>
</body>
</html>
```

## OUTPUT
<img width="1919" height="867" alt="image_64" src="https://github.com/user-attachments/assets/182ee928-f844-45a3-9c71-0379eea9bcfe" />
<img width="1919" height="867" alt="image_63" src="https://github.com/user-attachments/assets/adfc2d60-e9ee-4300-8ff4-784259189087" />
<img width="1919" height="969" alt="image_62" src="https://github.com/user-attachments/assets/e807f648-a3dd-4dba-aaad-12f0a56ee7dd" />


## RESULT
The program for creating Image Carousel using React is executed successfully.
