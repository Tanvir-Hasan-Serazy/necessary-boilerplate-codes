# Image Boilerplate codes

## Image Boilerplate

```
<div className="relative w-full max-w-44 h-44">
    <Image
     src={hotel.categoryThumbnail}
     alt="Hotel thumbnail"
     width={176} // max-w-44 = 176px (44 * 4)
     height={176} // h-44 = 176px (44 * 4)
     className="rounded-2xl object-cover w-full h-full"
      />
  </div>
```

## Image with fallback

```
"use client";
import Image from "next/image";
import { useState } from "react";

export const ImageWithFallback = (props) => {
  const { src, fallbackSrc, ...rest } = props;
  const [imgSrc, setImageSrc] = useState(src);
  return (
    <Image
      {...rest}
      src={imgSrc}
      onError={() => {
        setImageSrc(fallbackSrc);
      }}
    />
  );
};


// using as a component
<ImageWithFallback
  src={`${category?.image}`}
  alt="Category Image"
  fallbackSrc={FallbackImage}
  width={120}
  height={120}
  className="rounded-lg object-cover w-full h-full"
/>
```

## Card With Backgroud image

```
<div style={{
            background: `url("/images/dashboard/newsboard1.jpg") center/cover no-repeat`,
          }}
          className="relative min-h-[370px] max-w-sm rounded-2xl mt-10 lg:mt-20"
        >
          <span className="absolute p-1.5 bg-black/20 rounded-2xl  top-4 left-4 text-sm text-white">
            Featured
          </span>
          <div className="absolute p-3 bg-black/60 rounded-b-2xl w-full bottom-0 ">
            <p className="text-white font-bold text-lg lg:text-2xl">
              Ramadan Last Minue
            </p>
            <div className="flex items-center ">
              <p className="text-white font-bold text-lg lg:text-2xl">$650</p>
              <p className="text-[#B4ACAC] text-sm">/per person</p>
            </div>
          </div>
        </div>

```
