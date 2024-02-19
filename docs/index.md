# Welcome to `dust`

`dust` is a local-first, synchronizable (_coming soon_) **database** and
**state management** solution built for Flutter developers. It is developed
while we are building a cross-platform handwriting note-taking app called
dynote. dynote has not been open-sourced yet, but we aim to release its
source code under GPLv3 when have some spare time. `dust` is built specifically
to [solve the frustrations](./blog/posts/1.md) that we faced when we were
building dynote.

**Supported Platforms**: iOS, Android, MacOS, Linux, Windows

## Fearless Local First

> _(This slogan sounds like a Rust copycat, huh?)_

When we were picking a database for dust, we could not find one that fitted our
needs for building a productivity software. We want to provide local-first
software targeting all the native flutter platforms as well as providing sync
capabilities. This is not possible with other database solutions. We could not
simply choose a local-first database without worrying about synchronization
later on.

## Error-free State Management

While we were building the app dynote, we had a lot of issues with State
Management. They were always too "smart" for us, and often times we will have
to work around their "smart" designs to trigger a rebuild. Further, we also
need to make sure that the application state is in sync with the database
state, which is very hard to do and and very prune to errors. We want to solve
this issue as well. It also often is the case that we forget to subscribe to
changes of a state -- wasting us precious time on debugging state related
issues.
