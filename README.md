## Description

Presenting a react-based approach to work around flex layout's deficiency in expanding flex divs with column-wrap properties, outlined here:
https://stackoverflow.com/questions/33891709/when-flexbox-items-wrap-in-column-mode-container-does-not-grow-its-width

View the demo <a href="https://codesandbox.io/s/react-flex-column-wrap-demo-6y9348">here</a>.

## Example

```javascript
import Column from "react-column-flex-wrap";
//...

function render(children) {
  const ref = useRef(null);
  //...

  return (
    <>
      <Column
        // optional props
        className="optional-class-name"
        constantWidth
        style={style}
        ref={ref}
      >
        {...children}
      </Column>

      <Column
        // optional props
        columnReverse
        wrapReverse
        maxHeight={100} // max-height in px
      >
        {...children}
      </Column>
    </>
  );
}
```

## Documentation

The core component employs several hooks to tabulate its children's dimensions and setting its width. It will override display and flex-direction to `column` and `wrap` by default, but supports `column-reverse` and `wrap-reverse`. These properties can be set via props, in-line styles, or css class.

Important! The column's max-height or height has to be specified via props, styles or css class (in px, %, vh, vw, em or rem).

Optional props:
<br />• `id: string`
<br />• `key: string`
<br />• `ref: React.MutableRefObject<any>` - Ref to be forwarded to the component
<br />• `className: string` - class name conferring styles
<br />• `styles: CSSProperties` - in-line styles
<br />• `columnReverse: boolean` - set flex-direction to `column-reverse`
<br />• `wrapReverse: boolean` - set flex-wrap to `wrap-reverse`
<br />• `maxHeight: number` - set max-height in px
<br />• `dependencies: any[]` - Dependencies for the core hook
<br />• `constantHeight: boolean` - Default false. Take the height of the first child as reference for the others to save on computation.
<br />• `constantWidth: boolean` - Default false. Take the width of the first child as reference for the others to save on computation.
<br />• `effectOn: boolean` - Default true. Boolean to toggle the effect
