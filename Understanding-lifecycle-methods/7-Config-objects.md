SeasonDisplay.js

```javascript
import React from "react";

// Config object
const seasonConfig = {
  summer: {
    text: "Let's hit the beach",
    iconName: "sun",
  },
  winter: {
    text: "Burr it is cold!",
    iconName: "snowflake",
  },
};

const getSeason = (lat, month) => {
  if (month > 2 && month < 9) {
    return lat > 0 ? "summer" : "winter";
  } else {
    return lat > 0 ? "winter" : "summer";
  }
};

const SeasonDisplay = (props) => {
  const season = getSeason(props.lat, new Date().getMonth());
  //seasonConfig[season] /* {text, iconName}  This will return our object with the text and the icon name inside of it */
  // Now we can remove both of the ternary operation 
  // Destructure out 
  const {text, iconName} = seasonConfig[season];

  return (
    <div>
      <i classname={`${iconName} icon`} />
      <h1>{text}</h1>
      <i classname={`${iconName} icon`} />
    </div>
  );
};

export default SeasonDisplay;

```
