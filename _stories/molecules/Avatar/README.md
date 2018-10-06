The `<Avatar>` component can display a user's photo, a brand's logo, or a flag icon for internationalization.

You can pass it an `image` src to display a photo or logo, or a `username` to display the user's first initial.

The avatar can include a dropdown menu, which is meant to be shown when the avatar is clicked on. If the avatar is expandable, pass in a `menuCallback` function that sets the state, and include the state in your component.

For the menu contents, you must pass in `menuOptions` (an array of objects of names and paths for the menu), and a `optionCallback` that will be called when the option is clicked. If you want to have a login option, you can include that in the `optionCallback`.

**Example**:

```
state {
    avatarOpen: false
}

const toggleAvatar = () => {
    this.setState({ open: !this.state.toggleAvatar });
};

const optionCallback = (path) => {
    // Example using a custom logout function if the path is logout
    // otherwise use React Router's history.push to change the path
    path === 'logout' ? logout() : browserHistory.push(path);
};

return(
    <Avatar
        open={ this.state.avatarOpen }
        username="Michele"
        optionCallback={ this.optionCallback }
        menuCallback={ this.toggleAvatar }
        menuOptions={ AvatarMenu }
    />
)
```

**Options Format**:

```
const AvatarMenu = [
    { name: 'Change Password', path: '/account/change-password' },
    { name: 'Change Brand', path: '/account/change-brand' },
    { name: 'Login to Twitter', path: '/account/twitter-login' },
    { name: 'Switch to Annotator', path: '/account/instagram-login' },
    { name: 'Logout', path: 'logout' }
];
```

**Keyboard Accessibility:**

When the avatar is in focus you can toggle the related menu opened/closed with the spacebar or enter keys.
