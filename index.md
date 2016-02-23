title: Polymer vs Angular 2
author:
  name: Mika Turunen
  twitter: mikaturunen
  url: http://github.com/mikaturunen
theme: sudodoki/reveal-cleaver-theme
output: index.html

--

# Polymer vs Angular 2

--

### What is Polymer?

* Effectively not a framework but a sugary and tasty syntax on top of web components.
* Leverages polyfills for non-evergreen browsers: [webcomponents.js, polyfills](http://webcomponents.org/polyfills/).
* Heavily thinks of the DOM as the framework and aims to leverage as much as possible from the DOM.
	* Should be fairly familiar to write if HTML is your forte.

&nbsp;

<img src="web-poly-stack.svg" style="width: 400px; text-align: center; margin: auto;"></img>

--

### What is Angular 2?

* "One framework" for mobile and desktop applications.
	* Mobile first.
* Aims to fulfill the following promise: Fast, Mobile and Flexible.
* Built of top of TypeScript and internally fully works with TS.

---

### Are they related?

* Not directly, even though both are written by engineers at Google.
* There are rumors about web component support for A2.
	* Extremely finicky "hax" currently available through full shadow DOM and polyfills.
* Comparing the two from learning perspective.

&nbsp;

<img src="mind_blown.gif" style="width: 400px; text-align: center; margin: auto;"></img>


---

Polymer

```
<link rel="import" href="bower_components/polymer/polymer.html">

<dom-module id="foo-bar">
  	<template>
		<h1>[[ title ]]</h1>
		<h2>[[ hero.name ]] details!</h2>
		<div><label>id: </label>[[ hero.id ]]</div>
		<div>
			<label>name: </label>
			<!-- Notice different binding syntax to native elements -->
			<div><input type="text" value="{{hero.name::change}}"></div>
		</div>
  	</template>

	<script>
		Polymer({
			is: "foo-bar",
			properties: {
				title: {
					type: String,  
					value: 'Tour of Heroes'
				},
				hero: {
					type: Object
					value: {
						id: 1,
						name: 'Windstorm'
					}
				}
			}
		});
	</script>
</dom-module>
```

```
<foo-bar></foo-bar>
```

---

Angular 2

```
import { Component, View, bootstrap, NgFor, NgIf } from 'angular2/angular2';

interface Hero {
  id: number;
  name: string;
}

@Component({
	selector: 'foo-bar',
	template:`
		<h1>{{title}}</h1>
		<h2>{{hero.name}} details!</h2>
		<div><label>id: </label>{{hero.id}}</div>
		<div>
			<label>name: </label>
			<div><input type="text" [(ngModel)]="hero.name"></div>
		</div>
	`,
	directives: []
})
export class FooBar {
	public title = 'Tour of Heroes';
	public hero: Hero = {
		id: 1,
		name: 'Windstorm'
	};
}
```

```
<foo-bar></foo-bar>
```

---

### Which one should I choose?

* Best bet is to get familiar with both. Little bit of that and little bit of this.
* A2 is still in Beta and no proven traction by developers.
* Polymer is in its first production ready version (1.x) and is heavily used internally by Google. Especially involved in the material design side of things.
* I personally find working with Polymer easy and extremely satisfying. This feels like the right way of composing and doing things.

&nbsp;

* Note: look up "classless object-oriented programming in JavaScript".

---

# Angular 2

* A2 is fairly verbose as it uses class decorators and other TypeScript features heavily.
	* Added benefit of being typed by nature. This is amazing!
* Uses sensible module loading internally to resolve dependencies.
* No more controllers. Controllers are gone! Follows similar route with ReactJS in that sense.
    * Components and Directives are the "core" now.
* No more satanic $digest issues! No circular dependencies and heavily wants to have unidirectional data flow.
	* Flux? "Yeah, baby, yeah".
* No more $scope!
* A2 is closer to a library than a framework in my honest opinion but it still is a framework.. ugh.. what?

---

# Polymer

* Sites / applications are commonly built starting from the smallest components and building towards bigger and more complex components.
* Complex components are mainly a declarative collection of smaller components.
* The higher you work in the hierarchy of the application, the more declarative your work should be.
* Write underlying base components once and reuse! Do not write the same thing twice.
* Typing available. Not as heavily endorsed as A2's but nothings stopping you.

---

## In conclusion..

* Both Polymer and A2 are extremely interesting and I'm guessing they both will be widely used in 2016.
* They are both definitely something you should aim to get under your belt.

---

## The takeaway from all this?

* Please, go full TypeScript and drop JavaScript completely.
* Don't focus on the frameworks but make sure you understand the underlying concepts and moving from a framework to a framework should be fairly trivial.

---

# Thank you!
## Questions, comments?
