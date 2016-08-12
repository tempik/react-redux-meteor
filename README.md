React Redux Meteor
=========================

React bindings for [Redux](https://github.com/reactjs/redux) + [Meteor](https://github.com/meteor/meteor). 

Performant and flexible.

This project is forked from [react-redux](https://github.com/reactjs/react-redux) and will not send PR to the original repo because it's for Meteor ONLY.

## Installation

React Redux Meteor requires **React 0.14 or later.**

```
npm install --save react-redux-meteor
```

## Documentation

- [Redux: Usage with React](http://redux.js.org/docs/basics/UsageWithReact.html)
- [API](docs/api.md#api)
  - [`<Provider store>`](docs/api.md#provider-store)
  - [`connect([mapTrackerToProps], [mapStateToProps], [mapDispatchToProps], [mergeProps], [options])`](docs/api.md#connectmapstatetoprops-mapdispatchtoprops-mergeprops-options)
- [Troubleshooting](docs/troubleshooting.md#troubleshooting)

## Example

The argument `mapTrackerToProps` is what's new in `react-redux-meteor`

The Tracker props are not stored in redux store because they are client read-only and reactive. You can  change Tracker props by calling Meteor methods.
```
const mapTrackerToProps = (state, props) => {
  if (Meteor.subscribe('posts').ready()) {
    return { posts: Posts.find().fetch() };
  }
  return { posts: [] };
};

const mapStateToProps = (state, props) => {
  return {
    // ...
  };
};

const mapDispatchToProps = (dispatch) => {
  return {
    // ...
  };
};

export default connect(
  mapTrackerToProps,
  mapStateToProps,
  mapDispatchToProps
)(PostList);
```

## How Does It Work?

We do a deep dive on how React Redux works in [this readthesource episode](https://www.youtube.com/watch?v=VJ38wSFbM3A).  
Enjoy!

## License

MIT
