# react-splitter-layout

This repo is fork of https://github.com/zesik/react-splitter-layout

This is only fixing the getBoundingClientRect problem across browser by below code. For everything else refer https://github.com/zesik/react-splitter-layout

```
function getPosition(elm) {
  let rect   = elm.getBoundingClientRect();
  // add window scroll position to get the offset position
  let left   = rect.left   + window.scrollX;
  let top    = rect.top    + window.scrollY;
  let right  = rect.right  + window.scrollX;
  let bottom = rect.bottom + window.scrollY;
  // polyfill missing 'x' and 'y' rect properties not returned
  // from getBoundingClientRect() by older browsers
  let x;let y;
  if ( rect.x === undefined ) x = left;
  else x = rect.x + window.scrollX;
  if ( rect.y === undefined ) y = top;
  else y = rect.y + window.scrollY;
  // width and height are the same
  let width  = rect.width;
  let height = rect.height;
  //manual adjust for if there is top to secondary div
  if (top) {
    top = top - 50;
  }
  return { left, top, right, bottom, x, y, width, height };
}
```


