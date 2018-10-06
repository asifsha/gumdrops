`<Toggle>` components come in two flavors: radio and checkbox. Each one behaves in the same manner as their respective standard input type.

**NOTE**: This component can be controlled or uncontrolled. This component accepts any prop that you may want to add, which are applied to the input. The only drawback is that there is not validation for unlisted props.  **It is highly recommended that you use controlled components in React.**

*Recommended Props*: `name`, `checked`, `defaultChecked`, `onChange`

**Controlled example - Example for single Toggle**:
```
state = {
    myToggle: false
}

_handleToggle = () => {
    this.setState(({ myToggle }) => ({ myToggle: !myToggle }));
}

return (
    <Toggle
        name="myToggle"
        label="Default Toggle"
        checked={ this.state.myToggle }
        onChange={ this._handleToggle }
    />
)
```

**Uncontrolled example**:
```
_handleSubmit = (e) => {
    e.preventDefault();
    const { myToggle } = e.target.elements;
    console.log(myToggle.checked);
};

render() {
    return (
        <form onSubmit={ this._handleSubmit }>
            <FormGroup>
                { /* Pass defaultChecked if you want the input to be checked initially */ }
                <Toggle
                    name="myToggle"
                    label="Default Toggle"
                    defaultChecked
                />
            </FormGroup>
        </form>
    );
}
```
