![Add to Calendar Button React Wrapper](https://github.com/add2cal/add-to-calendar-button-react/blob/main/assets/readme-header.png?raw=true)

![Version](https://img.shields.io/npm/v/add-to-calendar-button-react?style=for-the-badge)
![Parent Script Version](https://img.shields.io/badge/Parent%20Script%20Version-v1.18.5-blue?style=for-the-badge)
[![GitHub Workflow Status](https://img.shields.io/github/workflow/status/add2cal/timezones-ical-library/npm%20publish?style=for-the-badge)](https://github.com/add2cal/timezones-ical-library/actions/workflows/npm-publish.yml)
![npm bundle size](https://img.shields.io/bundlephobia/minzip/add-to-calendar-button-react?style=for-the-badge)
[![npm Installations](https://img.shields.io/npm/dt/add-to-calendar-button-react?label=npm%20Installations&style=for-the-badge)](https://www.npmjs.com/package/add-to-calendar-button-react)

<br />

# The Add to Calendar Button - optimized for React

This is a wrapper repository for the popular [Add to Calendar Button](), making it even more convenient, to create beautiful buttons in React, where people can add events to their calendars.

<br /><br />

This is for everybody, who wants to include a button at their React application, which enables users to easily add a specific event to their calendars.
The main goal of this repository is to keep this process as easy as possible at maximum compatibility. Simply define your button configuration and everything else is automatically generated by the script.
Supporting calendars at Apple, Google, Microsoft (365, Outlook, Teams), Yahoo, and generic iCal.

![Supported Calendars: Apple (via iCal), Google, Microsoft (365, Outlook, Teams), Yahoo, generic iCal](https://github.com/add2cal/add-to-calendar-button-react/blob/main/assets/badge-supported-calendars.svg)

In terms of system support, **all modern browsers** (Chrome, Edge, Firefox, Safari) on **Windows, Mac, Android, and iOS** as well as rather restricted webview environments like the **Instagram** in-app browser are supported.

<br /><br />

---

<br />

## ▶️ Demo

See [add-to-calendar-button.com](https://add-to-calendar-button.com/) for a live demo and more documentation.

And remember to [⭐ **star** this repository](#) in order to stay up-to-date and save it for later! 🤗

<br />

---

<br />

## ✨ Features

Simple and convenient integration of 1 or many buttons, optimized to be used as React component.

### Supported Calendars

- **Google** Calendar.
- **Yahoo** Calender.
- **Microsoft 365, Outlook, and Teams**.
- Automatically generated **iCal/ics** files (for all other calendars, like **Apple**).

### Event Types

- Timed and all-day events.
- One-time, multi-date, recurring, or fluid.
- Most robust time zone and daylight saving management (via our own [TimeZones iCal Library](https://github.com/add2cal/timezones-ical-library)).
- Dynamic dates (like "today + 3").

### Look

- Beautiful and adjustable UI.
- Light and dark mode.
- Multiple themes.

### Accessibility

- Optimized and adjustable UX (for desktop and mobile).
- Dynamic dropdown positioning.
- Taking care of all those edge cases, where some scenarios do not support specific setups (like WebView blocking downloads); utilizing beautiful user guidance workarounds.
- Auto-generated Schema.org rich (structured) data for better SEO.
- Full support for mouse, touch, or keyboard input (W3C WAI compliant).
- Supporting 20+ languages, incl. RTL text for Arabic; but also custom labels and text blocks.

### And much more

- Well documented code, to easily understand the processes and build on top of it.
- No external module or backend dependencies.
- Therefore, fully GDPR, CCPA, and LGPD compliant - without the need of signing some data processing agreement.
- FREE and easy.

<br />

---

<br />

## 📦 Installation

Import the package using the following npm command:

```
npm install add-to-calendar-button-react
```

<br /><br />

## 🎛️ Setup & Configuration

Import the module into your project/component:

```
import { atcb_action, atcb_init } from 'add-to-calendar-button';
```

Either use `atcb_action` with your own buttons/forms/etc, or run `atcb_init` after the DOM has been loaded. To determine the right moment to execute the `atcb_init`, with React, you might want to include an event listener for `DOMContentLoaded` or use a hook in a functional component like `useEffect(() => atcb_init());`.

Include the css. Add `@import 'add-to-calendar-button/assets/css/atcb.css'` to some other css file - or include it in other more direct ways (like adding `import 'add-to-calendar-button/assets/css/atcb.css';` to the respective component) (use atcb-3d for an alternative style).

#### atcb_action

If you can't or don't want to use `atcb_init`, you can use the `atcb_action` import with your own buttons or other elements/components.

This may work better with React and other frontend frameworks, but it misses the Schema.org and button specific functionalities.

```js
import React from 'react';
import { atcb_action } from 'add-to-calendar-button';

const MyComponent = () => {
  const [name, setName] = React.useState("Some event");
  const changeName = e => {
    setName(e.target.value);
  };
  return (
    <form onSubmit={e => {
      e.preventDefault();
      atcb_action({
        name,
        startDate: "2022-10-14",
        endDate: "2022-10-18",
        options: ['Apple', 'Google', 'iCal', 'Microsoft365', 'Outlook.com', 'Yahoo'],
        timeZone: "Europe/Berlin",
        iCalFileName: "Reminder-Event",
      });
    }}>
      <input value={name} onChange={changeName} />
      <input type="submit" value="save" />
    </form>
  );
}
```

#### atcb_init

Alternatively, you could use `atcb_init` with a `useEffect` hook:

```js
import React from "react";
import { atcb_init } from "add-to-calendar-button";
import 'add-to-calendar-button/assets/css/atcb.css';

const MyComponent = () => {
  React.useEffect(atcb_init, []);
  return (
    <div className="atcb">
      { '{' }
        "name":"Add the title of your event",
        "description":"A nice description does not hurt",
        "startDate":"2022-02-21",
        "endDate":"2022-03-24",
        "startTime":"10:13",
        "endTime":"17:57",
        "location":"Somewhere over the rainbow",
        "label":"Add to Calendar",
        "options":[
          "Apple",
          "Google",
          "iCal",
          "Microsoft365",
          "Outlook.com",
          "Yahoo"
        ],
        "timeZone":"Europe/Berlin",
        "iCalFileName":"Reminder-Event"
      { '}' }
    </div>
  );
}
```

<br /><br />

### All options and hidden features

Find all information about the available options and how to configure specific features at the [github.com/add2cal/add-to-calendar-button/blob/main/DOCS.md](https://github.com/add2cal/add-to-calendar-button/blob/main/DOCS.md).

<br />

---

<br />

## ⚡ Changelog

- v1.0 : initial release

Mind that this is only referring to this wrapper repository and does not list any patches!

Find all changes regarding the parent main one at [github.com/add2cal/add-to-calendar-button/blob/main/CHANGELOG.md](https://github.com/add2cal/add-to-calendar-button/blob/main/CHANGELOG.md).

<br />

## 🙌 Contributing

Anyone is welcome to contribute, but mind the [guidelines](.github/CONTRIBUTING.md):

- [Bug reports](.github/CONTRIBUTING.md#bugs)
- [Feature requests](.github/CONTRIBUTING.md#features)
- [Pull requests](.github/CONTRIBUTING.md#pull-requests)

**IMPORTANT NOTE:** Run `npm install`, `npm run format`, and `npm run build` before you create any pull request!

<br />

## 📃 Copyright and License

Copyright (c) [Jens Kuerschner](https://jenskuerschner.de).

Licensed under [Apache-2.0 (with “Commons Clause” License Condition v1.0)](LICENSE.txt).

<br />

---

<br />

## 💜 Kudos go to

[uxwing.com](https://uxwing.com) as well as all contributors:

<a href="https://github.com/jekuer"><img src="https://avatars.githubusercontent.com/u/8572883?v=4" title="jekuer" width="60" height="60"></a>
<a href="https://github.com/add-to-calendar"><img src="https://avatars.githubusercontent.com/u/110406429?s=96&v=4" title="add-to-calendar" width="60" height="60"></a>
<a href="https://github.com/chadoh"><img src="https://avatars.githubusercontent.com/u/221614?v=4" title="chadoh" width="60" height="60"></a>
<a href="https://github.com/turcuciprian"><img src="https://avatars.githubusercontent.com/u/3309840?v=4" title="turcuciprian" width="60" height="60"></a>
<a href="https://github.com/lizakorab"><img src="https://avatars.githubusercontent.com/u/72821189?v=4" title="lizakorab" width="60" height="60"></a>
<a href="https://github.com/bryan-brancotte"><img src="https://avatars.githubusercontent.com/u/11556772?v=4" title="bryan-brancotte" width="60" height="60"></a>
<a href="https://github.com/nticaric"><img src="https://avatars.githubusercontent.com/u/824840?v=4" title="nticaric" width="60" height="60"></a>
<a href="https://github.com/Ortovoxx"><img src="https://avatars.githubusercontent.com/u/56805259?v=4" title="Ortovoxx" width="60" height="60"></a>
<a href="https://github.com/emilebosch"><img src="https://avatars.githubusercontent.com/u/303135?v=4" title="emilebosch" width="60" height="60"></a>
<a href="https://github.com/killerrin"><img src="https://avatars.githubusercontent.com/u/3269687?v=4" title="killerrin" width="60" height="60"></a>
<a href="https://github.com/acm-will"><img src="https://avatars.githubusercontent.com/u/103984058?v=4" title="acm-will" width="60" height="60"></a>
<a href="https://github.com/ssaaiidd"><img src="https://avatars.githubusercontent.com/u/29234802?v=4" title="ssaaiidd" width="60" height="60"></a>
<a href="https://github.com/c0rychu"><img src="https://avatars.githubusercontent.com/u/55235141?v=4" title="Cory Chu" width="60" height="60"></a>
<a href="https://github.com/Denperidge"><img src="https://avatars.githubusercontent.com/u/27348469?v=4" title="Cat" width="60" height="60"></a>
<a href="https://github.com/apps/dependabot"><img src="https://avatars.githubusercontent.com/in/29110?v=4" title="dependabot[bot]" width="60" height="60"></a>

<br />
