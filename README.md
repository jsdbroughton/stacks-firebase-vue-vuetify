<!-- PROJECT SHIELDS -->
[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![LinkedIn][linkedin-shield]][linkedin-url]



<!-- PROJECT LOGO -->
<br />
<p align="center">
  <h3 align="center">Stacks: Vue + Vuetify + Firebase</h3>

  <p align="center">
    A template stack for a firebase hosted web UI frontend with 'serverless' backend.
    <br />
    <a href="https://github.com/jsdbroughton/stacks-firebase-vue-vuetify"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    <a href="https://github.com/jsdbroughton/stacks-firebase-vue-vuetify/issues">Report Bug</a>
    ·
    <a href="https://github.com/jsdbroughton/stacks-firebase-vue-vuetify/issues">Request Feature</a>
  </p>
</p>



<!-- TABLE OF CONTENTS -->
## Table of Contents

* [About the Project](#about-the-project)
  * [Built With](#built-with)
* [Getting Started](#getting-started)
	* [Prerequisites](#prerequisites)
	* [Installation](#installation)
	* [Post Installation](#post-installation)
* [Usage](#usage)
* [Roadmap](#roadmap)
* [Contributing](#contributing)
* [License](#license)
* [Contact](#contact)
* [Acknowledgements](#acknowledgements)



<!-- ABOUT THE PROJECT -->
## About The Project
Like so many things I eventually get fed up with making the same thing over and over. When this stack was first made, I was spinning up firebase projects and slapping a vuetify skinned vue instance in there.

Most backend functions I need relate to data - which firebase RTDB/Firestore are great at, and the advantage of hostign there as well is the secret sauce auth between frontend and backend. For eveything else from auth to asyncronous processing, firebase has me covered.

None of this is hard to do - both tools can be spun up from their excellent CLI toolsets. However, I tweak the same things over an dover, there are nuanced improvements or just quirks that I like and frankly I forget over and over how I fixed the esoteric clashes between intent and implementation.

This is a long way to say this is my template stack for doing this. Even better now we can mark a repo as tenplate and spin up direct from it.

### Built With
As might be guessed from the blurb above this template is built from Vue and Firebase and for ease of having a stack that is just so, right now, Vuetify. As it develops over time the stack might be tweaked to even more specificity, or maybe less. (I have an AtlasUI version bubblign away in tandem)
* [Firebase](https://https://firebase.google.com/)
* [VueJS](https://vuejs.org)
* [Vuetify](https://vuetifyjs.com/en/)

<!-- GETTING STARTED -->
## Getting Started

To get a local copy up and running follow these simple example steps. Essentially the Vue part and the Firebase part are two separate projects (until I magic them together in the future)

### Prerequisites

This is an example of how to list things you need to use the software and how to install them.
* npm
```sh
npm install npm@latest -g
```

* firebase

	I recommend you install the firebase toolset as a global rather than a project dependency, only because I use it for so many projects. If you were developing inside a container it would be much of a muchness of course
	```sh
	npm install firebase-tools -g
	```

	You'll need a firebase project to connect to. It's best to make this in advance and then link the cloned repo project to this. Instructions below on the Firebase CLI method to do this once you ave the proejct all ready to go.

### Installation

1. Clone the repo
```sh
git clone https://github.com/jsdbroughton/stacks-firebase-vue-vuetify.git
```
2. Install NPM packages
```sh
npm install
```
3. After you have the Firebase project as describe in the prerequisites, you can add your VueJS web app to it.

	[Register your app with Firebase](https://firebase.google.com/docs/web/setup?authuser=0#register-app)

4. Firestore Setup

	It's not clear from the firebase cli that there is an extra step required before you initialise the link between the Project and your code.

	Several services available for your app require a location setting, called your project's default Google Cloud Platform (GCP) resource location. This location is where your data is stored for GCP services that require a location setting. Installing any of these features (yes you will want to) will require this to be set pre-init.

	Because setting this for any one of the services sets it for all the others, the easiest is to set it within Firestore which is one of the top level services visible in the Firebase Console.

	> **WARNING**: After you set this location, you cannot change it later. Also, this location setting will be the location for your default Cloud Storage bucket.

	I usually default to the nearest multi-region domain.

	If you are linking to other Google Services the closer this multi-region domain is to what you use for these the better. It's just easier unless you have a very specific reason for doing so while we are in prototyping mode to go with this by default.

	Setting the location for Firestore will provision for a few moments.

	Go ahead and create a default storage bucket while you are at it. (the location you'll notice by now is greyed out to the one you specified for firestore)

	Documentation: [Cloud Resource Locations]( https://firebase.google.com/docs/projects/locations)


5. If you've completed the steps above time to go ahead and link your project with the Firebase project.
	```sh
	firebase init --project <projectid>
	```

	The CLI will prompt for a bunch of stuff.

	If you want to be specific what services you need, select here. If not type ```a``` and move on.

	This template uses all the standard names for the config files for each service, overwrite them or don't its up to you.

	**Functions Setup**

	If you are initialising Cloud Functions you'll get to the stage where you are asked if you are using Typescript or Javacript. This only affects the `functions` component of the VueJS is its own story. This template stack uses TypeScript. Don't say yes to TSLint as it is deprecated in favour of ESLint now with TS plugins.

	Likewise ignore all its other recommendations up to installing dependencies, what could it hurt to say yes?

	**Hosting Setup**

	* Accept the defualt `public` directory as the rest of this stack assumes that's what were using.
	* Configure it as a single page app.
	* Overwrite if you like - ultimately this is a sacrificial folder in any case.

	**Emulators Setup**

	I use Functions, Firestore and Hosting. Download them when prompted.

6. All this will have linked your new project with Firebase - there won't be much more to do at this point.

### Post Installation

Both the Functions and Frontend sections have specific instructions how to develop each stream separately.

<!-- USAGE EXAMPLES -->
## Usage

This template doesn't at present include any examples beyond the standard setup I have in place for my own preference.

There are no tips and tricks for the Cloud Functions yet.

There are a bunch of hacks to the npm scripts in the parent project and also for both the functions and the frontend sections. These are all the glue that makes for a pain-free (lol) development platform pre-deployment.

The broad intention is that development of frontend and backend be decoupled by-and-large.

Single-point deployment is advantageous, but the Firebase deployment tools is sufficient to learn rather than recreate it as an npm mask here.

<!-- ROADMAP -->
## Roadmap

See the [open issues](https://github.com/jsdbroughton/stacks-firebase-vue-vuetify/issues) for a list of proposed features (and known issues).

The main features and revisions coming to this repo come from tweaks made on live development projects and this will evolve to adopt those amendments that stick. Naturally this is less of a live project in that sense.

<!-- CONTRIBUTING -->
## Contributing

Contributions are what make the open source community such an amazing place to be learn, inspire, and create. Any contributions you make are **greatly appreciated**.

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

Or just raise an issue with anything you have in mind.

<!-- LICENSE -->
## License

I never really understood the difference between them all. This isn't really a live project repo - take it a screw with it as you see fit.

<!-- CONTACT -->
## Contact

Your Name - [@jsdbroughton](https://twitter.com/jsdbroughton) - jsdbroughton@stardotbmp.com

Project Link: [https://github.com/jsdbroughton/stacks-firebase-vue-vuetify](https://github.com/jsdbroughton/stacks-firebase-vue-vuetify)

<!-- ACKNOWLEDGEMENTS -->
## Acknowledgements
* [Img Shields](https://shields.io)

<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/jsdbroughton/stacks-firebase-vue-vuetify.svg?style=flat-square
[contributors-url]: https://github.com/jsdbroughton/stacks-firebase-vue-vuetify/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/jsdbroughton/stacks-firebase-vue-vuetify.svg?style=flat-square
[forks-url]: https://github.com/jsdbroughton/stacks-firebase-vue-vuetify/network/members
[stars-shield]: https://img.shields.io/github/stars/jsdbroughton/stacks-firebase-vue-vuetify.svg?style=flat-square
[stars-url]: https://github.com/jsdbroughton/stacks-firebase-vue-vuetify/stargazers
[issues-shield]: https://img.shields.io/github/issues/jsdbroughton/stacks-firebase-vue-vuetify.svg?style=flat-square
[issues-url]: https://github.com/jsdbroughton/stacks-firebase-vue-vuetify/issues
[license-shield]: https://img.shields.io/github/license/jsdbroughton/stacks-firebase-vue-vuetify.svg?style=flat-square
[license-url]: https://github.com/jsdbroughton/stacks-firebase-vue-vuetify/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=flat-square&logo=linkedin&colorB=555
[linkedin-url]: https://linkedin.com/in/jonathonbroughton
[product-screenshot]: images/screenshot.png
