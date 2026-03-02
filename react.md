# React boilerplate codes

## Rating Stars

```
import { Star } from "lucide-react";

export const RatingStars = ({ rating, total = 5 }) => {
  const fullStars = Math.floor(rating);
  const hasHalfStar = rating % 1 >= 0.5;
  const emptyStars = total - fullStars - (hasHalfStar ? 1 : 0);

  return (
    <div className="flex items-center gap-1">
      {/* Full stars */}
      {Array.from({ length: fullStars }).map((_, i) => (
        <Star
          key={`full-${i}`}
          className="w-5 h-5 fill-yellow-400 text-yellow-400"
        />
      ))}

      {/* Half star */}
      {hasHalfStar && (
        <div className="relative w-5 h-5">
          {/* Filled half */}
          <Star className="absolute w-5 h-5 fill-yellow-400 text-yellow-400 clip-half" />
          {/* Outline */}
          <Star className="absolute w-5 h-5 text-yellow-400" />
        </div>
      )}

      {/* Empty stars */}
      {Array.from({ length: emptyStars }).map((_, i) => (
        <Star key={`empty-${i}`} className="w-5 h-5 text-yellow-400" />
      ))}
    </div>
  );
};

```

## Scroll to up

```
import React, { useState, useEffect } from 'react';

const ScrollToTopButton = () => {
  const [showButton, setShowButton] = useState(false);

  // Logic to show/hide the button
  useEffect(() => {
    const handleScroll = () => {
      // Show button if user has scrolled down past a certain point (e.g., 400px)
      if (window.scrollY > 400) {
        setShowButton(true);
      } else {
        setShowButton(false);
      }
    };

    window.addEventListener('scroll', handleScroll);

    // Cleanup the event listener when the component unmounts
    return () => {
      window.removeEventListener('scroll', handleScroll);
    };
  }, []);

  // Function to scroll to the top
  const goToTop = () => {
    window.scrollTo({
      top: 0, // Scroll to the top of the page
      behavior: 'smooth', // Smooth animation for the scroll
    });
  };

  return (
    <>
      {showButton && (
        <button
          onClick={goToTop}
          style={{
            position: 'fixed',
            bottom: '20px',
            right: '20px',
            // Add other styling as needed
          }}
        >
          Scroll to Top
        </button>
      )}
    </>
  );
};

export default ScrollToTopButton;
```

## Price Range Slider

```
"use client";

import { useState } from "react";
import { Label } from "@/components/ui/label";
import { Slider } from "@/components/ui/slider";

export const title = "Price Range Slider";

const Example = () => {
  const [value, setValue] = useState([200, 800]);

  return (
    <div className="flex w-full max-w-md flex-col gap-2">
      <Label htmlFor="slider">Price Range</Label>
      <Slider
        id="slider"
        max={1000}
        min={0}
        onValueChange={setValue}
        value={value}
      />
      <div className="flex items-center justify-between text-muted-foreground text-sm">
        <span>${value[0]}</span>
        <span>${value[1]}</span>
      </div>
    </div>
  );
};

export default Example;
```
