/*! PhotoSwipe main CSS by Dmytro Semenov | photoswipe.com */


.pswp {
  --pswp-bg: #000;
  --pswp-placeholder-bg: #222;
  

  --pswp-root-z-index: 100000;
  
  --pswp-preloader-color: rgba(79, 79, 79, 0.4);
  --pswp-preloader-color-secondary: rgba(255, 255, 255, 0.9);
  
  /* defined via js:
  --pswp-transition-duration: 333ms; */
  
  --pswp-icon-color: #fff;
  --pswp-icon-color-secondary: #4f4f4f;
  --pswp-icon-stroke-color: #4f4f4f;
  --pswp-icon-stroke-width: 2px;

  --pswp-error-text-color: var(--pswp-icon-color);
}


/*
	Styles for basic PhotoSwipe (pswp) functionality (sliding area, open/close transitions)
*/

.pswp {
	position: fixed;
	top: 0;
	left: 0;
	width: 100%;
	height: 100%;
	z-index: var(--pswp-root-z-index);
	display: none;
	touch-action: none;
	outline: 0;
	opacity: 0.003;
	contain: layout style size;
	-webkit-tap-highlight-color: rgba(0, 0, 0, 0);
}

/* Prevents focus outline on the root element,
  (it may be focused initially) */
.pswp:focus {
  outline: 0;
}

.pswp * {
  box-sizing: border-box;
}

.pswp img {
  max-width: none;
}

.pswp--open {
	display: block;
}

.pswp,
.pswp__bg {
	transform: translateZ(0);
	will-change: opacity;
}

.pswp__bg {
  opacity: 0.005;
	background: var(--pswp-bg);
}

.pswp,
.pswp__scroll-wrap {
	overflow: hidden;
}

.pswp__scroll-wrap,
.pswp__bg,
.pswp__container,
.pswp__item,
.pswp__content,
.pswp__img,
.pswp__zoom-wrap {
	position: absolute;
	top: 0;
	left: 0;
	width: 100%;
	height: 100%;
}

.pswp__img,
.pswp__zoom-wrap {
	width: auto;
	height: auto;
}

.pswp--click-to-zoom.pswp--zoom-allowed .pswp__img {
	cursor: -webkit-zoom-in;
	cursor: -moz-zoom-in;
	cursor: zoom-in;
}

.pswp--click-to-zoom.pswp--zoomed-in .pswp__img {
	cursor: move;
	cursor: -webkit-grab;
	cursor: -moz-grab;
	cursor: grab;
}

.pswp--click-to-zoom.pswp--zoomed-in .pswp__img:active {
  cursor: -webkit-grabbing;
  cursor: -moz-grabbing;
  cursor: grabbing;
}

/* :active to override grabbing cursor */
.pswp--no-mouse-drag.pswp--zoomed-in .pswp__img,
.pswp--no-mouse-drag.pswp--zoomed-in .pswp__img:active,
.pswp__img {
	cursor: -webkit-zoom-out;
	cursor: -moz-zoom-out;
	cursor: zoom-out;
}


/* Prevent selection and tap highlights */
.pswp__container,
.pswp__img,
.pswp__button,
.pswp__counter {
	-webkit-user-select: none;
	-moz-user-select: none;
	-ms-user-select: none;
	user-select: none;
}

.pswp__item {
	/* z-index for fade transition */
	z-index: 1;
	overflow: hidden;
}

.pswp__hidden {
	display: none !important;
}

/* Allow to click through pswp__content element, but not its children */
.pswp__content {
  pointer-events: none;
}
.pswp__content > * {
  pointer-events: auto;
}


/*

  PhotoSwipe UI

*/

/*
	Error message appears when image is not loaded
	(JS option errorMsg controls markup)
*/
.pswp__error-msg-container {
  display: grid;
}
.pswp__error-msg {
	margin: auto;
	font-size: 1em;
	line-height: 1;
	color: var(--pswp-error-text-color);
}

/*
class pswp__hide-on-close is applied to elements that
should hide (for example fade out) when PhotoSwipe is closed
and show (for example fade in) when PhotoSwipe is opened
 */
.pswp .pswp__hide-on-close {
	opacity: 0.005;
	will-change: opacity;
	transition: opacity var(--pswp-transition-duration) cubic-bezier(0.4, 0, 0.22, 1);
	z-index: 10; /* always overlap slide content */
	pointer-events: none; /* hidden elements should not be clickable */
}

/* class pswp--ui-visible is added when opening or closing transition starts */
.pswp--ui-visible .pswp__hide-on-close {
	opacity: 1;
	pointer-events: auto;
}

/* <button> styles, including css reset */
.pswp__button {
	position: relative;
	display: block;
	width: 50px;
	height: 60px;
	padding: 0;
	margin: 0;
	overflow: hidden;
	cursor: pointer;
	background: none;
	border: 0;
	box-shadow: none;
	opacity: 0.85;
	-webkit-appearance: none;
	-webkit-touch-callout: none;
}

.pswp__button:hover,
.pswp__button:active,
.pswp__button:focus {
  transition: none;
  padding: 0;
  background: none;
  border: 0;
  box-shadow: none;
  opacity: 1;
}

.pswp__button:disabled {
  opacity: 0.3;
  cursor: auto;
}

.pswp__icn {
  fill: var(--pswp-icon-color);
  color: var(--pswp-icon-color-secondary);
}

.pswp__icn {
  position: absolute;
  top: 14px;
  left: 9px;
  width: 32px;
  height: 32px;
  overflow: hidden;
  pointer-events: none;
}

.pswp__icn-shadow {
  stroke: var(--pswp-icon-stroke-color);
  stroke-width: var(--pswp-icon-stroke-width);
  fill: none;
}

.pswp__icn:focus {
	outline: 0;
}

/*
	div element that matches size of large image,
	large image loads on top of it,
	used when msrc is not provided
*/
div.pswp__img--placeholder,
.pswp__img--with-bg {
	background: var(--pswp-placeholder-bg);
}

.pswp__top-bar {
	position: absolute;
	left: 0;
	top: 0;
	width: 100%;
	height: 60px;
	display: flex;
  flex-direction: row;
  justify-content: flex-end;
	z-index: 10;

	/* allow events to pass through top bar itself */
	pointer-events: none !important;
}
.pswp__top-bar > * {
  pointer-events: auto;
  /* this makes transition significantly more smooth,
     even though inner elements are not animated */
  will-change: opacity;
}


/*

  Close button

*/
.pswp__button--close {
  margin-right: 6px;
}


/*

  Arrow buttons

*/
.pswp__button--arrow {
  position: absolute;
  top: 0;
  width: 75px;
  height: 100px;
  top: 50%;
  margin-top: -50px;
}

.pswp__button--arrow:disabled {
  display: none;
  cursor: default;
}

.pswp__button--arrow .pswp__icn {
  top: 50%;
  margin-top: -30px;
  width: 60px;
  height: 60px;
  background: none;
  border-radius: 0;
}

.pswp--one-slide .pswp__button--arrow {
  display: none;
}

/* hide arrows on touch screens */
.pswp--touch .pswp__button--arrow {
  visibility: hidden;
}

/* show arrows only after mouse was used */
.pswp--has_mouse .pswp__button--arrow {
  visibility: visible;
}

.pswp__button--arrow--prev {
  right: auto;
  left: 0px;
}

.pswp__button--arrow--next {
  right: 0px;
}
.pswp__button--arrow--next .pswp__icn {
  left: auto;
  right: 14px;
  /* flip horizontally */
  transform: scale(-1, 1);
}

/*

  Zoom button

*/
.pswp__button--zoom {
  display: none;
}

.pswp--zoom-allowed .pswp__button--zoom {
  display: block;
}

/* "+" => "-" */
.pswp--zoomed-in .pswp__zoom-icn-bar-v {
  display: none;
}


/*

  Loading indicator

*/
.pswp__preloader {
  position: relative;
  overflow: hidden;
  width: 50px;
  height: 60px;
  margin-right: auto;
}

.pswp__preloader .pswp__icn {
  opacity: 0;
  transition: opacity 0.2s linear;
  animation: pswp-clockwise 600ms linear infinite;
}

.pswp__preloader--active .pswp__icn {
  opacity: 0.85;
}

@keyframes pswp-clockwise {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}


/*

  "1 of 10" counter

*/
.pswp__counter {
  height: 30px;
  margin-top: 15px;
  margin-inline-start: 20px;
  font-size: 14px;
  line-height: 30px;
  color: var(--pswp-icon-color);
  text-shadow: 1px 1px 3px var(--pswp-icon-color-secondary);
  opacity: 0.85;
}

.pswp--one-slide .pswp__counter {
  display: none;
}
.splide__container{box-sizing:border-box;position:relative}.splide__list{backface-visibility:hidden;display:-ms-flexbox;display:flex;height:100%;margin:0!important;padding:0!important}.splide.is-initialized:not(.is-active) .splide__list{display:block}.splide__pagination{-ms-flex-align:center;align-items:center;display:-ms-flexbox;display:flex;-ms-flex-wrap:wrap;flex-wrap:wrap;-ms-flex-pack:center;justify-content:center;margin:0;pointer-events:none}.splide__pagination li{display:inline-block;line-height:1;list-style-type:none;margin:0;pointer-events:auto}.splide:not(.is-overflow) .splide__pagination{display:none}.splide__progress__bar{width:0}.splide{position:relative;visibility:hidden}.splide.is-initialized,.splide.is-rendered{visibility:visible}.splide__slide{backface-visibility:hidden;box-sizing:border-box;-ms-flex-negative:0;flex-shrink:0;list-style-type:none!important;margin:0;position:relative}.splide__slide img{vertical-align:bottom}.splide__spinner{animation:splide-loading 1s linear infinite;border:2px solid #999;border-left-color:transparent;border-radius:50%;bottom:0;contain:strict;display:inline-block;height:20px;left:0;margin:auto;position:absolute;right:0;top:0;width:20px}.splide__sr{clip:rect(0 0 0 0);border:0;height:1px;margin:-1px;overflow:hidden;padding:0;position:absolute;width:1px}.splide__toggle.is-active .splide__toggle__play,.splide__toggle__pause{display:none}.splide__toggle.is-active .splide__toggle__pause{display:inline}.splide__track{overflow:hidden;position:relative;z-index:0}@keyframes splide-loading{0%{transform:rotate(0)}to{transform:rotate(1turn)}}.splide__track--draggable{-webkit-touch-callout:none;-webkit-user-select:none;-ms-user-select:none;user-select:none}.splide__track--fade>.splide__list>.splide__slide{margin:0!important;opacity:0;z-index:0}.splide__track--fade>.splide__list>.splide__slide.is-active{opacity:1;z-index:1}.splide--rtl{direction:rtl}.splide__track--ttb>.splide__list{display:block}.splide__arrow{-ms-flex-align:center;align-items:center;background:#ccc;border:0;border-radius:50%;cursor:pointer;display:-ms-flexbox;display:flex;height:2em;-ms-flex-pack:center;justify-content:center;opacity:.7;padding:0;position:absolute;top:50%;transform:translateY(-50%);width:2em;z-index:1}.splide__arrow svg{fill:#000;height:1.2em;width:1.2em}.splide__arrow:hover:not(:disabled){opacity:.9}.splide__arrow:disabled{opacity:.3}.splide__arrow:focus-visible{outline:3px solid #0bf;outline-offset:3px}.splide__arrow--prev{left:1em}.splide__arrow--prev svg{transform:scaleX(-1)}.splide__arrow--next{right:1em}.splide.is-focus-in .splide__arrow:focus{outline:3px solid #0bf;outline-offset:3px}.splide__pagination{bottom:.5em;left:0;padding:0 1em;position:absolute;right:0;z-index:1}.splide__pagination__page{background:#ccc;border:0;border-radius:50%;display:inline-block;height:8px;margin:3px;opacity:.7;padding:0;position:relative;transition:transform .2s linear;width:8px}.splide__pagination__page.is-active{background:#fff;transform:scale(1.4);z-index:1}.splide__pagination__page:hover{cursor:pointer;opacity:.9}.splide__pagination__page:focus-visible{outline:3px solid #0bf;outline-offset:3px}.splide.is-focus-in .splide__pagination__page:focus{outline:3px solid #0bf;outline-offset:3px}.splide__progress__bar{background:#ccc;height:3px}.splide__slide{-webkit-tap-highlight-color:rgba(0,0,0,0)}.splide__slide:focus{outline:0}@supports(outline-offset:-3px){.splide__slide:focus-visible{outline:3px solid #0bf;outline-offset:-3px}}@media screen and (-ms-high-contrast:none){.splide__slide:focus-visible{border:3px solid #0bf}}@supports(outline-offset:-3px){.splide.is-focus-in .splide__slide:focus{outline:3px solid #0bf;outline-offset:-3px}}@media screen and (-ms-high-contrast:none){.splide.is-focus-in .splide__slide:focus{border:3px solid #0bf}.splide.is-focus-in .splide__track>.splide__list>.splide__slide:focus{border-color:#0bf}}.splide__toggle{cursor:pointer}.splide__toggle:focus-visible{outline:3px solid #0bf;outline-offset:3px}.splide.is-focus-in .splide__toggle:focus{outline:3px solid #0bf;outline-offset:3px}.splide__track--nav>.splide__list>.splide__slide{border:3px solid transparent;cursor:pointer}.splide__track--nav>.splide__list>.splide__slide.is-active{border:3px solid #000}.splide__arrows--rtl .splide__arrow--prev{left:auto;right:1em}.splide__arrows--rtl .splide__arrow--prev svg{transform:scaleX(1)}.splide__arrows--rtl .splide__arrow--next{left:1em;right:auto}.splide__arrows--rtl .splide__arrow--next svg{transform:scaleX(-1)}.splide__arrows--ttb .splide__arrow{left:50%;transform:translate(-50%)}.splide__arrows--ttb .splide__arrow--prev{top:1em}.splide__arrows--ttb .splide__arrow--prev svg{transform:rotate(-90deg)}.splide__arrows--ttb .splide__arrow--next{bottom:1em;top:auto}.splide__arrows--ttb .splide__arrow--next svg{transform:rotate(90deg)}.splide__pagination--ttb{bottom:0;display:-ms-flexbox;display:flex;-ms-flex-direction:column;flex-direction:column;left:auto;padding:1em 0;right:.5em;top:0}
*, *::before, *::after {
  box-sizing: border-box;
}

* {
  margin: 0;
  padding: 0;
  border: 0;
}

body {
  line-height: 1.5;
  -webkit-font-smoothing: antialiased;
}

img, picture, video, canvas, svg, iframe, embed, audio {
  display: block;
  max-width: 100%;
}

input, button, textarea, select {
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
  border: 0;
  border-radius: var(--border-radius);
  background: none;
  color: inherit;
  font: inherit;
}

button {
  cursor: pointer;
}

p, h1, h2, h3, h4, h5, h6 {
  overflow-wrap: break-word;
}

ol, ul {
  list-style: none;
}

:root {
  --primary-font: {{ theme.primary_font | font_family }};
  --secondary-font: {{ theme.secondary_font | font_family }};
  --background-color: {{ theme.background_color }};
  --header-background-color: {{ theme.header_background_color }};
  --header-text-color: {{ theme.header_text_color }};
  --header-text-hover-color: {{ theme.header_text_hover_color }};
  --primary-text-color: {{ theme.primary_text_color }};
  --secondary-text-color: {{ theme.secondary_text_color }};
  --border-color: rgba(var(--primary-text-color-rgb), .4);
  --link-hover-color: {{ theme.link_hover_color }};
  --button-background-color: {{ theme.button_background_color }};
  --button-hover-background-color: {{ theme.button_hover_background_color }};
  --button-text-color: {{ theme.button_text_color }};
  --footer-background-color: {{ theme.footer_background_color }};
  --announcement-background-color: {{ theme.announcement_background_color }};
  --announcement-text-color: {{ theme.announcement_text_color }};
  --error-background-color: #950f1e;
  --error-text-color: #FFFFFF;
  --product-status-background-color: var(--background-color);
  --product-status-text-color: var(--primary-text-color);
  --border-radius: {{ theme.border_radius }};
  --header-height: 90px;
  --margin-size: 64px;
  --layout-width: 1200px;
  --side-padding: 40px;
}
@media screen and (max-width: 945px) {
  :root {
    --side-padding: 20px;
  }
}

html {
  min-height: 100%;
  position: relative;
  height: 100%;
}

body {
  background: var(--background-color);
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  color: var(--primary-text-color);
  display: flex;
  flex-direction: column;
  font-family: var(--secondary-font);
  font-size: 16px;
  min-height: 100%;
  height: 100%;
}
body.overlay-open {
  height: 100vh;
  width: 100vw;
  overflow: hidden;
  overscroll-behavior: none;
}

a.skip-link {
  transition: all 0.3s linear;
  background: var(--background-color);
  border: 1px solid var(--primary-text-color);
  color: var(--primary-text-color);
  left: 25px;
  padding: 15px 20px;
  position: absolute;
  text-decoration: underline;
  top: -150px;
  z-index: 100;
}
a.skip-link:focus {
  top: 20px;
}

.category-nav {
  cursor: pointer;
  position: relative;
  width: auto;
  z-index: 3;
}
@media screen and (max-width: 800px) {
  .category-nav {
    display: none;
    font-size: 1.25em;
  }
}
@media screen and (max-width: 668px) {
  .category-nav {
    font-size: 1em;
    max-width: 100%;
  }
}
.category-nav .category-nav-heading {
  display: -ms-flexbox;
  display: flex;
  -ms-flex-align: center;
  align-items: center;
  -ms-flex-pack: center;
  justify-content: center;
  gap: 8px;
  transition: color 0.2s linear;
}
@media (hover: hover) {
  .category-nav .category-nav-heading:hover {
    color: var(--header-text-hover-color);
  }
  .category-nav .category-nav-heading:hover .category-nav-page {
    text-decoration: underline;
  }
}
.category-nav .category-nav-heading:focus {
  color: var(--header-text-hover-color);
}
.category-nav .category-nav-page {
  text-underline-offset: 4px;
}
.category-nav .category-nav-arrow {
  fill: currentColor;
  pointer-events: none;
  width: 12px;
}
.category-nav .category-dropdown {
  background: var(--header-background-color);
  transition: opacity 0.2s linear, visibility 0.2s linear;
  border-radius: var(--border-radius);
  border: 1px solid var(--header-text-color);
  left: -20px;
  margin: 0 auto;
  min-width: 250px;
  opacity: 0;
  overflow-y: scroll;
  padding: 15px;
  position: absolute;
  text-align: left;
  visibility: hidden;
  height: auto;
  max-height: 50vh;
  z-index: 3;
  top: calc(100% + 16px);
  scrollbar-width: thin;
  scrollbar-color: rgba(var(--header-text-color-rgb),.5) transparent;
  scrollbar-gutter: stable;
}
.category-nav .category-dropdown[aria-hidden="false"] {
  opacity: 1;
  visibility: visible;
}
.category-nav .category-dropdown::-webkit-scrollbar {
  height: 0.375rem;
  width: 0.75rem;
}
.category-nav .category-dropdown::-webkit-scrollbar-track {
  background-color: transparent;
}
.category-nav .category-dropdown::-webkit-scrollbar-thumb {
  border-radius: 0.375rem;
  border: 3px solid transparent;
  background-color: rgba(var(--primary-text-color-rgb),.5);
  background-clip: content-box;
}
.category-nav .dropdown-list {
  list-style: none;
  margin: 0;
  padding: 0;
  position: relative;
  z-index: 4;
}
.category-nav .dropdown-list li {
  display: block;
}
.category-nav .dropdown-list li a {
  display: block;
  font-size: 0.925em;
  padding: 8px;
}

.header {
  background: var(--header-background-color);
  color: var(--header-text-color);
  font-family: var(--primary-font);
  height: var(--header-height);
  line-height: 1.2rem;
  position: relative;
  z-index: 11;
  width: 100%;
  transition: background 0.2s linear;
}
.header__wrapper {
  max-width: var(--layout-width);
  margin: 0 auto;
  padding: 0 var(--side-padding);
  display: grid;
  min-height: var(--header-height);
  align-items: center;
  grid-template-columns: 1fr 2fr 1fr;
  gap: 24px;
}
@media screen and (max-width: 945px) {
  .header__wrapper {
    grid-template-columns: 1fr 1fr;
    padding: 0 20px;
  }
}
.header.fixed {
  position: fixed;
  top: 0;
  left: 0;
}
.header.has-welcome {
  background: transparent;
}
.header.show-background {
  background: var(--header-background-color);
}
.header a {
  color: var(--header-text-color);
  text-decoration: none;
  transition: color 0.2s linear;
}
@media (hover: hover) {
  .header a:hover {
    color: var(--header-text-hover-color);
    text-decoration: underline;
  }
}
.header a:focus {
  color: var(--header-text-hover-color);
}

.header-logo {
  font-size: 1.5em;
  display: inline-flex;
  align-items: center;
  text-align: left;
}
.header-logo a {
  display: flex;
  line-height: 1.25em;
  align-items: center;
  max-width: 200px;
  padding: 8px 0;
  width: auto;
  outline-offset: 4px;
}
.header-logo.image img {
  max-height: 100%;
  max-width: 200px;
}
@media screen and (max-width: 668px) {
  .header-logo.image img {
    max-width: 140px;
  }
}
.header-logo.image a {
  height: 58px;
  max-width: 100%;
}

.header-icons {
  display: flex;
  align-items: center;
  justify-content: flex-end;
  gap: 20px;
  position: relative;
}
@media screen and (max-width: 668px) {
  .header-icons {
    gap: 12px;
    right: -6px;
  }
}
.header-icons li {
  position: relative;
}
.header-icons li > * {
  color: var(--header-text-color);
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  width: 40px;
  height: 40px;
  position: relative;
  padding: 0;
  transition: color 0.2s linear;
}
.header-icons li > *:hover, .header-icons li > *:focus {
  color: var(--header-text-hover-color);
}
.header-icons li > * svg {
  fill: currentColor;
  height: 30px;
  width: 30px;
}
.header-icons li.open_search svg {
  height: 28px;
  width: 28px;
  position: relative;
  top: 2px;
}
@media screen and (min-width: 946px) {
  .header-icons li.open_menu {
    display: none;
  }
}
.header-icons li.open_menu button span {
  border-radius: 2px;
  transform: rotate(0deg);
  display: block;
  background: currentColor;
  width: 100%;
  height: 2px;
  position: absolute;
  width: 28px;
}
.header-icons li.open_menu button span:nth-child(1) {
  top: 12px;
}
.header-icons li.open_menu button span:nth-child(2), .header-icons li.open_menu button span:nth-child(3) {
  top: 50%;
}
.header-icons li.open_menu button span:nth-child(4) {
  bottom: 10px;
}

@media screen and (max-width: 945px) {
  .header-navigation {
    display: none;
  }
}
.header-navigation .header-pages {
  display: flex;
  column-gap: 32px;
  row-gap: 4px;
  flex-wrap: wrap;
  list-style: none;
  margin: 0;
  padding: 0;
  text-align: center;
  flex-direction: row;
  justify-content: center;
}
.header-navigation .header-page-link a, .header-navigation .header-page-link .category-nav-heading {
  display: flex;
  position: relative;
  outline-offset: 4px;
  border-radius: 0;
}

.cart-count {
  position: absolute;
  right: -2px;
  top: 4px;
}

.cart-value {
  border-radius: 50%;
  background-color: var(--header-text-color);
  color: var(--header-background-color);
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: var(--secondary-font);
  font-size: 0.75em;
  height: 20px;
  width: 20px;
}

a {
  color: var(--primary-text-color);
  text-decoration: none;
  text-underline-offset: 4px;
  transition: color 0.2s linear;
}
a:focus {
  color: var(--link-hover-color);
}
@media (hover: hover) {
  a:hover {
    color: var(--link-hover-color);
    text-decoration: underline;
  }
}

button.button, a.button, div.button {
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
  background: var(--button-background-color);
  color: var(--button-text-color);
  border-radius: var(--border-radius);
  display: flex;
  min-height: 60px;
  align-items: center;
  justify-content: center;
  padding: 16px;
  max-width: 360px;
  text-decoration: none;
  text-align: center;
  white-space: pre-wrap;
  width: 100%;
  transition: background 0.2s linear;
}
@media screen and (max-width: 668px) {
  button.button, a.button, div.button {
    max-width: 100%;
  }
}
button.button:hover, button.button:focus, a.button:hover, a.button:focus, div.button:hover, div.button:focus {
  background: var(--button-hover-background-color);
}
button.button--minimal, a.button--minimal, div.button--minimal {
  background: none;
  border: 0;
  color: var(--primary-text-color);
  text-decoration: underline;
  font-weight: normal;
  transition: color 0.2s linear;
}
button.button--minimal:hover, button.button--minimal:focus, a.button--minimal:hover, a.button--minimal:focus, div.button--minimal:hover, div.button--minimal:focus {
  background: none;
  border: 0;
  color: var(--link-hover-color);
}
button.button--centered, a.button--centered, div.button--centered {
  margin: 0 auto;
}
button.button--secondary, a.button--secondary, div.button--secondary {
  background: none;
  border: 2px solid var(--primary-text-color);
  color: var(--primary-text-color);
}
button.button--secondary:hover, button.button--secondary:focus, a.button--secondary:hover, a.button--secondary:focus, div.button--secondary:hover, div.button--secondary:focus {
  background: none;
  border: 2px solid var(--link-hover-color);
  color: var(--link-hover-color);
}

.errors {
  background: var(--error-background-color);
  border-radius: var(--border-radius);
  color: var(--error-text-color);
  margin-bottom: 40px;
  text-align: center;
  padding: 16px;
  display: flex;
  flex-direction: column;
  text-align: center;
  gap: 10px;
}

.select {
  border-radius: var(--border-radius);
  position: relative;
  color: var(--primary-text-color);
  height: 56px;
  padding: 0;
  position: relative;
  width: 100%;
}
.select select {
  background: none;
  border: 1px solid var(--primary-text-color);
  height: 100%;
  padding: 0 40px 0 12px;
  position: relative;
  width: 100%;
  z-index: 2;
}
.select select option {
  background-color: #FFF;
  color: #000;
}
.select select:focus {
  box-shadow: none;
}
.select select::-ms-expand {
  display: none;
}
.select svg {
  fill: currentColor;
  height: 8px;
  position: absolute;
  pointer-events: none;
  right: 14px;
  top: 50%;
  transform: translateY(-50%);
  width: 14px;
  z-index: 1;
}

h1, h2, h3, h4, h5, h6 {
  font-family: var(--primary-font);
  font-weight: normal;
}

#main {
  flex: 1;
  padding-top: 96px;
  padding-bottom: var(--margin-size);
}
@media screen and (max-width: 668px) {
  #main {
    padding-top: 60px;
  }
}
#main .content-wrapper {
  margin: 0 auto;
  max-width: var(--layout-width);
  padding: 0 var(--side-padding);
}
#main .content-wrapper--home h1.page-title {
  margin-bottom: 48px;
}
#main .content-wrapper .custom-page {
  margin: 0 auto;
  max-width: 768px;
  width: 100%;
}
#main .content-wrapper--contact {
  max-width: 680px;
}
#main .content-wrapper--cart {
  max-width: 1200px;
}
#main .content-wrapper--product {
  max-width: var(--layout-width);
}

.page-title {
  font-size: 2rem;
  margin-bottom: 48px;
  text-align: center;
}

.social-icons {
  display: -ms-flexbox;
  display: flex;
  gap: 16px;
  list-style: none;
  margin: 0;
  padding: 0;
  flex-wrap: wrap;
  justify-content: center;
}
@media screen and (max-width: 668px) {
  .social-icons {
    gap: 8px;
  }
}
.social-icons a {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
  width: 36px;
  height: 36px;
}
.social-icons a svg {
  fill: currentColor;
  height: 20px;
  width: 20px;
}
.social-icons a svg.tumblr-icon {
  width: 14px;
}

.message-banner {
  border-radius: var(--border-radius);
  background-color: var(--announcement-background-color);
  color: var(--announcement-text-color);
  padding: 16px;
  margin-bottom: 32px;
  text-align: left;
  width: 100%;
}
.message-banner--centered {
  text-align: center;
}
.message-banner--no-bg {
  color: var(--primary-text-color);
  background: none;
  padding: 0;
}

.footer {
  background: var(--footer-background-color);
  color: var(--footer-text-color);
  font-family: var(--secondary-font);
  display: flex;
  flex-shrink: 0;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  gap: 50px;
  padding: 60px 20px;
  text-align: center;
  width: 100%;
}
.footer a {
  color: var(--footer-text-color);
}
.footer a:hover {
  color: var(--link-hover-color);
}
.footer__nav {
  display: flex;
  flex-direction: column;
  row-gap: 40px;
}
.footer__pages {
  display: flex;
  column-gap: 30px;
  max-width: 640px;
  flex-wrap: wrap;
  justify-content: center;
  row-gap: 12px;
}
.footer__pages a {
  display: block;
  padding: 2px;
}
.footer__pages a:hover {
  text-decoration: underline;
}
.footer .bigcartel-credit {
  font-size: 14px;
  line-height: 1em;
  display: flex;
  align-items: center;
  gap: 8px;
  outline-offset: 4px;
  padding: 2px 0;
}
.footer .bigcartel-credit__text {
  position: relative;
}
.footer .bigcartel-credit__lockup {
  display: block;
  fill: currentColor;
  padding-top: 1px;
  width: 80px;
}

.blur-up {
  transition: filter 0.2s ease;
  filter: blur(2px);
  transform: translate3d(0, 0, 0);
}
.blur-up.lazyloaded {
  filter: blur(0);
}

.sr-only {
  border: 0;
  clip: rect(0 0 0 0);
  height: 1px;
  margin: -1px;
  overflow: hidden;
  padding: 0;
  position: absolute;
  width: 1px;
}

.custom-page {
  max-width: 768px;
  margin: 0 auto;
}

.custom-page--content p, .product-detail__description p {
  margin: revert;
}
.custom-page--content > :first-child, .product-detail__description > :first-child {
  margin-top: 0;
}
.custom-page--content > :last-child, .product-detail__description > :last-child {
  margin-bottom: 0;
}
.custom-page--content ol, .custom-page--content ul, .product-detail__description ol, .product-detail__description ul {
  margin: 1em;
}
.custom-page--content ul, .product-detail__description ul {
  list-style: disc;
}
.custom-page--content ol, .product-detail__description ol {
  list-style: decimal;
}
.custom-page--content a, .product-detail__description a {
  text-decoration: underline;
}

@keyframes welcome-text {
  0% {
    opacity: 0;
    transform: translate3d(0, 10%, 0);
  }
  100% {
    transform: none;
    opacity: 1;
  }
}
@keyframes hide-welcome-text {
  0% {
    transform: none;
    opacity: 1;
  }
  100% {
    opacity: 0;
    transform: translate3d(0, 10%, 0);
  }
}
.welcome-image {
  background: var(--header-background-color);
  color: var(--header-text-color);
  height: 100vh;
  height: 100svh;
  left: 0;
  position: relative;
  text-align: center;
  top: calc(var(--header-height) * -1);
  width: 100%;
  display: flex;
  align-items: center;
  z-index: 2;
  flex-shrink: 0;
}
.welcome-image .welcome-image-bg {
  transition: opacity 0.3s ease-in;
  object-fit: cover;
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  opacity: 0;
}
.welcome-image .welcome-overlay {
  background: var(--header-background-color);
  bottom: 0;
  height: 100%;
  left: 0;
  opacity: 0.4;
  position: absolute;
  right: 0;
  top: 0;
  width: 100%;
}
.welcome-image .welcome-text {
  position: relative;
  animation: welcome-text ease-in 900ms forwards;
  padding: 0 20px;
  max-width: 1200px;
  margin: 0 auto;
}
.welcome-image .welcome-text.fade_out {
  animation: hide-welcome-text ease-in 200ms forwards;
}
.welcome-image .welcome-text .welcome-text-header {
  font-size: 3.75em;
  line-height: 1.2em;
  margin-bottom: 40px;
}
@media screen and (max-width: 668px) {
  .welcome-image .welcome-text .welcome-text-header {
    font-size: 9vw;
  }
}
.welcome-image .welcome-text .welcome-button {
  color: var(--header-text-color);
  font-size: 1.5em;
  padding: 10px;
  text-decoration-color: transparent;
  transition: text-decoration-color 0.1s linear;
  outline-offset: 4px;
}
.welcome-image .welcome-text .welcome-button:hover {
  text-decoration-color: var(--header-text-color);
  text-decoration: underline;
  text-decoration-thickness: 2px;
}

.welcome-image + main {
  margin-top: calc(var(--header-height) * -1);
}

.home-tagline {
  color: var(--secondary-text-color);
  font-family: var(--secondary-font);
  font-size: 1.25em;
  margin: 0 auto 96px;
  max-width: 680px;
  text-align: center;
  width: 100%;
}
@media screen and (max-width: 668px) {
  .home-tagline {
    margin: 0 auto 60px;
  }
}

.home-featured-products {
  margin-bottom: var(--margin-size);
}

a.all-products-button {
  margin-top: 48px;
}

.featured-categories h2 {
  text-align: center;
  font-size: 2rem;
  margin-bottom: 48px;
}
.featured-categories .category-list {
  --columns: {{ theme.max_categories_per_row }};
}
@media screen and (max-width: 945px) {
  .featured-categories .category-list {
    --columns: calc({{ theme.max_categories_per_row }} - 1);
    justify-content: flex-start;
  }
}
@media screen and (max-width: 668px) {
  .featured-categories .category-list {
    --columns: {{ theme.max_categories_per_row_mobile }};
  }
}

#maintenance {
  -ms-flex-align: center;
  align-items: center;
  display: -ms-flexbox;
  display: flex;
  font-size: 1.25em;
  padding: 100px 20px;
  text-align: center;
}
#maintenance .maintenance-container {
  display: grid;
  gap: 48px;
}
#maintenance .maintenance-store-name {
  font-size: 1.5em;
  margin: 0;
}

.category-list {
  margin: 0 auto 60px;
  text-align: center;
}
@media screen and (max-width: 668px) {
  .category-list {
    margin-bottom: 40px;
  }
}
.category-list ul {
  display: flex;
  align-items: center;
  justify-content: center;
  column-gap: 16px;
  row-gap: 8px;
  flex-wrap: wrap;
}
.category-list ul a {
  color: var(--secondary-text-color);
  display: block;
  font-size: 1.2em;
  padding: 2px 6px;
  outline-offset: 2px;
}
.category-list ul a:hover {
  color: var(--link-hover-color);
  text-decoration: underline;
}

.product-list {
  --gap: calc(var(--spacing-unit) * 4);
  --row-gap: 48px;
  --columns: {{ theme.max_products_per_row }};
  --spacing-unit: 8px;
  display: flex;
  flex-wrap: wrap;
  justify-content: flex-start;
  margin: var(--spacing-unit) 0 0;
  gap: var(--gap);
  row-gap: var(--row-gap);
  margin-top: 36px;
}
.product-list--center {
  justify-content: center;
}
@media screen and (max-width: 945px) {
  .product-list {
    --columns: calc({{ theme.max_products_per_row }} - 1);
  }
}
@media screen and (max-width: 668px) {
  .product-list {
    --columns: {{ theme.max_products_per_row_mobile }};
    --gap: calc(var(--spacing-unit) * 2);
    justify-content: flex-start;
  }
}

.product-list-thumb {
  position: relative;
  text-decoration: none;
  width: calc((100% / var(--columns)) - var(--gap) + (var(--gap) / var(--columns)));
}

a.product-list-link {
  text-decoration: none;
  outline-offset: 4px;
  position: relative;
}
@media (hover: hover) {
  a.product-list-link:hover .product-list-image {
    transform: translate3d(0, 0, 0) scale(1.05);
  }
  a.product-list-link:hover .product-list-thumb-name {
    text-decoration: underline;
  }
}

.product-list-image-container {
  border-radius: var(--border-radius);
  margin: 0;
  overflow: hidden;
  padding-bottom: 100%;
  position: relative;
  width: 100%;
}
.product-list-image-container-default {
  padding-bottom: 0;
}

.product-list-image {
  border-radius: var(--border-radius);
  transform: translate3d(0, 0, 0);
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  transition: transform 0.3s ease-in-out;
  z-index: 1;
}
.product-list-image.grid-default {
  position: relative;
}
.product-list-image.grid-cover {
  object-fit: cover;
}
.product-list-image.grid-contain {
  object-fit: contain;
}

.product-list-thumb-status {
  background: var(--product-status-background-color);
  border-radius: var(--border-radius);
  color: var(--product-status-text-color);
  top: 12px;
  right: 12px;
  font-size: 0.875rem;
  line-height: 1em;
  letter-spacing: 1.12px;
  font-weight: 500;
  position: absolute;
  text-transform: uppercase;
  padding: 6px;
  z-index: 2;
}

.product-list-thumb-info {
  line-height: normal;
  padding: 16px 0 0;
  position: relative;
  text-align: center;
  display: grid;
  gap: 8px;
}
.product-list-thumb-info .product-list-thumb-status {
  display: none;
}

.product-list-thumb-name {
  font-size: 1.1rem;
  word-break: break-word;
}

.product-list-thumb-price {
  font-size: 0.975rem;
}

.pagination {
  display: flex;
  align-items: center;
  justify-content: center;
  color: var(--primary-text-color);
  position: relative;
  text-align: center;
  width: 100%;
  gap: 24px;
  line-height: 2em;
  margin-top: var(--margin-size);
}
.pagination .page-link {
  display: flex;
  align-items: center;
  gap: 12px;
  padding: 0 8px;
}
.pagination .page-link.disabled {
  display: none;
}
.pagination .page-link svg {
  width: 10px;
  height: 16px;
}
.pagination .previous, .pagination .next {
  display: none;
}

.page-numbers {
  display: flex;
  gap: 24px;
}
.page-numbers .current {
  text-underline-offset: 4px;
  text-decoration: underline;
}
.page-numbers > a, .page-numbers span {
  padding: 0 8px;
}

.pagination-arrow {
  display: block;
  fill: currentColor;
  height: 17px;
  width: 17px;
}
.pagination-arrow.prev-arrow {
  margin-right: auto;
}
.pagination-arrow.next-arrow {
  margin-left: auto;
}

.product-breadcrumb {
  color: var(--secondary-text-color);
  margin-bottom: 24px;
}
.product-breadcrumb a {
  color: inherit;
  text-decoration: underline;
}
.product-breadcrumb a:hover {
  color: var(--link-hover-color);
}

.product-container {
  display: grid;
  grid-template-columns: 1fr 360px;
  column-gap: 60px;
  row-gap: 40px;
}
@media screen and (max-width: 945px) {
  .product-container {
    column-gap: 40px;
  }
}
@media screen and (max-width: 800px) {
  .product-container {
    grid-template-columns: minmax(0, 1fr);
  }
}

.reset-selection-button-container {
  text-align: center;
  width: 100%;
}
.reset-selection-button-container button.reset-selection-button {
  display: none;
}

.product-form {
  width: 100%;
}
.product-form button {
  max-width: 100%;
}
@media screen and (max-width: 945px) {
  .product-form {
    max-width: 100%;
  }
}

.product-selects {
  margin-bottom: 20px;
}

.product-option-groups {
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.product-detail {
  display: flex;
  flex-direction: column;
  row-gap: 36px;
}
.product-detail__header {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
}
.product-detail__status {
  text-transform: uppercase;
  font-size: 0.825rem;
  line-height: normal;
  font-weight: 500;
  display: inline-block;
  padding: 4px 6px;
  margin-left: 8px;
  border: 1px solid var(--border-color);
  border-radius: var(--border-radius);
  letter-spacing: 1.1px;
}
.product-detail__pricing {
  color: var(--secondary-text-color);
  display: flex;
  align-items: center;
  font-size: 1.5em;
}
.product-detail .page-title {
  margin-bottom: 0;
  text-align: left;
}

#instant-checkout-button {
  margin-top: 12px;
}

:root {
  --thumbnail-active-color: var(--link-hover-color);
  --thumb-scroller-color: var(--primary-text-color);
  --thumb-scroller-border-width: 1px;
  --thumb-scroller-border-color: var(--primary-text-color);
  --thumb-scroller-background: var(--background-color);
  --thumb-scroller-background-hover: transparent;
  --current-slide-background: var(--background-color);
  --current-slide-color: var(--primary-text-color);
  --active-slide-border-width: 2px;
  --active-slide-border-width-offset: -2px;
  --arrow-background-color: var(--background-color);
  --arrow-color: var(--primary-text-color);
  --gap-width: 16px;
  --num-images: 5;
}
@media screen and (max-width: 668px) {
  :root {
    --gap-width: 12px;
  }
}

.product-carousel .splide__list {
  align-items: flex-start;
}
.product-carousel .splide__slide {
  transition: height 0.2s ease;
}
.product-carousel .splide__slide img {
  display: block;
  width: 100%;
  height: auto;
}
.product-carousel .splide__slide:not(.is-active) {
  height: 0;
}

.splide__track {
  border-radius: var(--border-radius);
}

.splide__arrows {
  display: none;
}
@media (hover: hover) {
  .splide__arrows {
    display: block;
  }
}

.splide__arrow {
  transition: opacity 0.2s ease;
  opacity: 0;
  border-radius: var(--border-radius);
  width: 2em;
  height: 3em;
  background: var(--arrow-background-color);
  color: var(--arrow-color);
}
.splide__arrow:disabled {
  opacity: 0;
}
.splide__arrow--prev {
  left: 0.75em;
}
.splide__arrow--next {
  right: 0.75em;
}
.splide__arrow svg {
  fill: currentColor;
}

.splide:hover .splide__arrow:not(:disabled), .splide:focus-within .splide__arrow:not(:disabled) {
  opacity: 1;
}

.product-image {
  border-radius: var(--border-radius);
  width: 100%;
}

.product-thumbnails--list {
  display: flex;
  gap: var(--gap-width);
  list-style: none;
  flex: 1;
  padding: 0 calc(var(--gap-width) / 2);
  scroll-padding-left: calc(var(--gap-width) / 2);
  align-items: center;
  justify-content: center;
  position: relative;
  border-radius: var(--border-radius);
}
.product-thumbnails--list.mobile-overflow {
  padding-left: 0;
  padding-right: 0;
}
@media screen and (max-width: 668px) {
  .product-thumbnails--list .product-thumbnails--item {
    --num-images: 4;
  }
  .product-thumbnails--list.mobile-overflow {
    padding-left: 0;
    padding-right: 0;
  }
  .product-thumbnails--list.mobile-overflow .product-thumbnails--item {
    --num-images: 5;
  }
}
.product-thumbnails--list.is-overflow {
  justify-content: flex-start;
  overflow-x: auto;
  scroll-snap-type: x mandatory;
  scroll-behavior: smooth;
  scrollbar-width: none;
}
.product-thumbnails--list.is-overflow::-webkit-scrollbar {
  display: none;
}
.product-thumbnails--list.thumbnails {
  flex-wrap: wrap;
}
.product-thumbnails--item {
  width: calc(calc(100% / var(--num-images)) - calc(var(--gap-width) - calc(var(--gap-width) / var(--num-images))));
  flex-shrink: 0;
  cursor: pointer;
  border-radius: var(--border-radius);
  user-select: none;
  pointer-events: none;
  position: relative;
  scroll-snap-align: start;
}
.product-thumbnails--item:before {
  content: "";
  display: block;
  padding-bottom: 100%;
}
.product-thumbnails--item:not([aria-current="true"]):hover img {
  opacity: 0.8;
}
.product-thumbnails--item[aria-current="true"] .product-thumbnails--change-slide img {
  outline: var(--active-slide-border-width) solid var(--thumbnail-active-color);
  outline-offset: var(--active-slide-border-width-offset);
}
.product-thumbnails--item .product-thumbnails--change-slide {
  position: absolute;
  top: 0;
  left: 0;
  display: block;
  height: 100%;
  width: 100%;
  padding: 0;
  overflow: hidden;
  user-select: none;
  border-radius: var(--border-radius);
  pointer-events: auto;
}
.product-thumbnails--item .product-thumbnails--change-slide img {
  border-radius: var(--border-radius);
  height: 100%;
  width: 100%;
  object-fit: cover;
}

a.gallery-link {
  cursor: zoom-in;
  display: block;
}

.product-thumbnails-buttons-container {
  align-items: center;
  display: flex;
  gap: 4px;
  margin-top: var(--gap-width);
  width: 100%;
}
.product-thumbnails-buttons-container .thumb-scroller {
  display: none;
  align-items: center;
  justify-content: center;
  width: 32px;
  height: 48px;
  color: var(--thumb-scroller-color);
  background: var(--thumb-scroller-background);
  border-radius: var(--border-radius);
  border: var(--thumb-scroller-border-width) solid var(--thumb-scroller-border-color);
}
@media screen and (max-width: 668px) {
  .product-thumbnails-buttons-container .thumb-scroller {
    height: 44px;
  }
}
.product-thumbnails-buttons-container .thumb-scroller[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
.product-thumbnails-buttons-container .thumb-scroller:not([disabled]):hover {
  background: var(--thumb-scroller-background-hover);
}
.product-thumbnails-buttons-container .thumb-scroller svg {
  fill: currentColor;
  display: block;
  width: 16px;
}
.product-thumbnails-buttons-container .thumb-scroller--left svg {
  transform: rotate(90deg);
}
.product-thumbnails-buttons-container .thumb-scroller--right svg {
  transform: rotate(-90deg);
}
.product-thumbnails-buttons-container .thumb-scroller.hidden {
  display: none;
}

@media screen and (min-width: 669px) {
  .overlay-image-counter {
    display: none;
  }

  .desktop-stacked .splide .splide__list, .desktop-two-column .splide .splide__list {
    display: flex !important;
    flex-direction: column;
    gap: 16px;
  }
  .desktop-stacked .splide .splide__slide, .desktop-two-column .splide .splide__slide {
    height: auto;
    flex-shrink: 0;
    width: 100%;
  }
  .desktop-stacked .product-thumbnails-buttons-container, .desktop-two-column .product-thumbnails-buttons-container {
    display: none;
  }

  .desktop-two-column .splide .splide__list {
    flex-direction: row;
    flex-wrap: wrap;
  }
  .desktop-two-column .splide .splide__track {
    overflow: visible;
  }
  .desktop-two-column .splide .splide__slide {
    width: calc((100% / 2) - 8px);
  }
  .desktop-two-column .splide .splide__slide:not(:first-child):before {
    content: "";
    display: block;
    padding-bottom: 100%;
  }
  .desktop-two-column .splide .splide__slide:not(:first-child) .zoom-image-container {
    position: absolute;
    top: 0;
    left: 0;
    display: block;
    height: 100%;
    width: 100%;
    padding: 0;
    overflow: hidden;
    user-select: none;
    border-radius: var(--border-radius);
    pointer-events: auto;
  }
  .desktop-two-column .splide .splide__slide:not(:first-child) .zoom-image-container img {
    height: 100%;
    width: 100%;
    object-fit: cover;
  }
  .desktop-two-column .splide .splide__slide:first-child {
    width: 100%;
  }

  .desktop-carousel .thumb-scroller {
    display: flex;
  }
  .desktop-carousel .overlay-image-counter {
    display: flex;
  }

  .desktop-thumbnails .product-thumbnails {
    padding: 0px;
  }
  .desktop-thumbnails .product-thumbnails--list {
    list-style: none;
    display: grid;
    grid-template-columns: repeat(5, 1fr);
    padding: 0;
  }
  .desktop-thumbnails .product-thumbnails--item {
    width: 100%;
  }

  .mobile-buttons-indicator {
    display: none;
  }
}
@media screen and (max-width: 668px) {
  .mobile-show-thumbnails .mobile-buttons-indicator {
    display: none;
  }
  .mobile-show-thumbnails .thumb-scroller {
    display: flex;
  }

  .mobile-hide-thumbnails .overlay-image-counter {
    display: none;
  }
  .mobile-hide-thumbnails .product-thumbnails-buttons-container {
    display: none;
  }
  .mobile-hide-thumbnails .mobile-buttons-indicator {
    display: flex;
    font-size: 0.925rem;
    gap: 24px;
    align-items: center;
    justify-content: center;
    margin-top: 16px;
  }
  .mobile-hide-thumbnails .mobile-buttons-indicator .change-slide {
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 0;
    width: 40px;
    height: 40px;
    background: var(--thumb-scroller-background);
    color: var(--thumb-scroller-color);
  }
  .mobile-hide-thumbnails .mobile-buttons-indicator .change-slide svg {
    display: block;
    width: 16px;
  }
  .mobile-hide-thumbnails .mobile-buttons-indicator .change-slide--left svg {
    transform: rotate(90deg);
  }
  .mobile-hide-thumbnails .mobile-buttons-indicator .change-slide--right svg {
    transform: rotate(-90deg);
  }
}
.overlay-image-counter {
  position: absolute;
  right: 10px;
  bottom: 10px;
  font-size: 0.8rem;
  background: var(--current-slide-background);
  color: var(--current-slide-color);
  padding: 6px 8px;
  border-radius: var(--border-radius);
}

.cart-empty {
  display: flex;
  flex-direction: column;
  gap: 16px;
  max-width: 600px;
  align-items: center;
  margin: 0 auto;
  width: 100%;
}

.cart-columns {
  display: grid;
  align-items: flex-start;
  grid-template-columns: 2fr 1fr;
  column-gap: 64px;
}
@media screen and (max-width: 945px) {
  .cart-columns {
    grid-template-columns: 1fr;
  }
}

.cart-header {
  display: flex;
  align-items: flex-end;
  justify-content: flex-start;
  margin-bottom: 32px;
}
.cart-header .page-title {
  margin-bottom: 0;
}

.cart-items {
  border-bottom: 1px solid var(--border-color);
}

.cart-item {
  display: grid;
  grid-template-columns: auto 1fr 148px auto;
  justify-content: flex-start;
  align-items: flex-start;
  border-top: 1px solid var(--border-color);
  padding: 24px 0;
  gap: 16px;
}
@media (max-width: 945px) {
  .cart-item {
    grid-template-columns: auto 1fr auto;
    grid-template-rows: repeat(2, auto);
  }
}
@media screen and (max-width: 945px) {
  .cart-item .cart-item-image-holder {
    grid-area: 1/1/3/2;
  }
}
.cart-item .cart-item-image-link {
  display: block;
  height: 90px;
  overflow: hidden;
  width: 90px;
}
@media screen and (max-width: 945px) {
  .cart-item .cart-item-image-link {
    height: 64px;
    width: 64px;
  }
}
.cart-item .cart-item-image-link img {
  border-radius: var(--border-radius);
  height: 100%;
  object-fit: cover;
  width: 100%;
}
.cart-item .cart-item-detail {
  padding-right: 24px;
}
@media (max-width: 945px) {
  .cart-item .cart-item-detail {
    grid-area: 1/2/2/3;
    padding-right: 0;
  }
}
.cart-item .product-name {
  font-weight: 600;
  font-size: 1.1em;
  word-break: break-word;
}
.cart-item .option-name {
  font-size: 1em;
  font-weight: 400;
  margin-top: 4px;
}
.cart-item input {
  border: none;
  height: 100%;
  padding: 8px;
  text-align: center;
  width: 48px;
}
.cart-item input::-webkit-outer-spin-button, .cart-item input::-webkit-inner-spin-button {
  display: none;
}
.cart-item .cart-qty {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  width: 148px;
  gap: 8px;
}
@media (max-width: 945px) {
  .cart-item .cart-qty {
    align-items: center;
    grid-area: 2/2/3/4;
    justify-content: flex-start;
    flex-direction: row;
    width: 100%;
    gap: 24px;
  }
}
.cart-item .qty-holder {
  display: flex;
  align-items: center;
  border: 1px solid var(--primary-text-color);
  border-radius: var(--border-radius);
  gap: 8px;
}
.cart-item .qty-holder.disabled > * {
  opacity: 0.7;
  cursor: not-allowed;
  user-select: none;
  pointer-events: none;
}
.cart-item .qty-button {
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
  color: var(--primary-text-color);
  display: flex;
  align-items: center;
  justify-content: center;
  border: none;
  background: none;
  cursor: pointer;
  height: 44px;
  width: 36px;
}
.cart-item .qty-button:hover, .cart-item .qty-button:focus {
  color: var(--link-hover-color);
}
.cart-item .qty-button svg {
  width: 14px;
  height: 16px;
}
.cart-item .cart-remove-item--link {
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
  display: inline-block;
  height: auto;
  padding: 0.5em;
  line-height: 1em;
  font-weight: normal;
  font-size: 0.925em;
  padding: 8px 16px;
  text-decoration: underline;
  width: auto;
}
@media (max-width: 945px) {
  .cart-item .cart-remove-item--link {
    padding: 4px 0;
    margin-left: auto;
  }
}
.cart-item .cart-item-price {
  font-size: 1em;
  margin-left: auto;
  min-width: 100px;
  min-height: 42px;
  display: flex;
  justify-content: flex-end;
  text-align: right;
}
@media screen and (max-width: 945px) {
  .cart-item .cart-item-price {
    font-size: 1.2rem;
    min-height: 0;
    min-width: 0;
    grid-area: 1/3/2/4;
    margin-left: 0;
  }
}

.cart-footer {
  border: 1px solid var(--border-color);
  border-radius: var(--border-radius);
  display: grid;
  place-items: center;
  gap: 2rem;
  padding: 24px;
}
@media screen and (max-width: 945px) {
  .cart-footer {
    margin-top: 24px;
    padding: 0;
    border: 0;
  }
}

.cart-subtotal {
  display: flex;
  gap: 16px;
  font-size: 1.25rem;
  align-items: flex-start;
  width: 100%;
}
.cart-subtotal__label {
  font-weight: 700;
}
.cart-subtotal__amount {
  margin-left: auto;
}

.cart-submit {
  display: flex;
  flex-direction: column;
  gap: 8px;
  width: 100%;
}
.cart-submit .button {
  max-width: 100%;
  width: 100%;
}

.contact-form {
  display: flex;
  flex-direction: column;
  gap: 24px;
}

.contact-form-block {
  display: flex;
  flex-direction: column;
  gap: 8px;
}

.contact-label {
  font-weight: 700;
}

input, textarea {
  border-radius: var(--border-radius);
  background: var(--background-color);
  border: 1px solid var(--primary-text-color);
  font-weight: normal;
  width: 100%;
  font-size: 1rem;
  padding: 12px;
}

textarea {
  min-height: 220px;
  resize: vertical;
}

.recaptcha-note {
  font-size: 0.925rem;
  text-align: center;
}
.recaptcha-note a {
  text-decoration: underline;
}

.announcement-message {
  background-color: var(--announcement-background-color);
  color: var(--announcement-text-color);
  display: none;
  font-size: 1rem;
  padding: 18px 96px;
  line-height: 1.25em;
  position: relative;
  text-align: center;
  width: 100%;
  z-index: 1;
  align-items: center;
  justify-content: center;
}
@media screen and (max-width: 668px) {
  .announcement-message {
    padding: 14px 64px;
  }
}
.announcement-message.visible {
  display: flex;
}
.announcement-message__close-button {
  transform: translateY(-50%);
  display: flex;
  align-items: center;
  justify-content: center;
  color: var(--announcement-text-color);
  height: 32px;
  padding: 0;
  position: absolute;
  right: 32px;
  top: 50%;
  width: 32px;
}
@media screen and (max-width: 668px) {
  .announcement-message__close-button {
    right: 16px;
  }
}
.announcement-message__close-icon {
  height: 14px;
  width: 14px;
}

.search-modal {
  opacity: 0;
  visibility: hidden;
  position: fixed;
  z-index: 999;
  width: 100vw;
  height: 100vh;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  background-color: rgba(var(--background-color-rgb),.8);
  transition: opacity 0.2s ease, visibility 0.2s ease;
}
.search-modal[aria-hidden="false"] {
  opacity: 1;
  visibility: visible;
}
.search-modal__content {
  background-color: var(--background-color);
  border-bottom: 1px solid var(--primary-text-color);
  color: var(--primary-text-color);
  text-align: center;
  display: grid;
  grid-template-rows: 1fr;
  width: 100%;
}
.search-modal__wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  padding: 32px;
  max-width: 800px;
  position: relative;
  margin: 0 auto;
  width: 100%;
}
.search-modal__form {
  display: grid;
  font-weight: bold;
  grid-template-columns: 1fr;
  column-gap: 16px;
  row-gap: 8px;
  width: 100%;
}
.search-modal__input {
  grid-row: 2/2;
  grid-column: 1/1;
  border-radius: var(--border-radius);
  background: var(--background-color);
  border: 1px solid var(--primary-text-color);
  font-weight: normal;
  width: 100%;
  font-size: 1em;
  height: 48px;
  padding: 8px;
}
.search-modal__submit {
  color: var(--button-text-color);
  background: var(--button-background-color);
  grid-row: 2/2;
  grid-column: 2/2;
  padding: 0;
  height: 48px;
  width: 48px;
  display: flex;
  align-items: center;
  justify-content: center;
}
.search-modal__close {
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 0;
  font-size: 4em;
  cursor: pointer;
  width: 48px;
  height: 48px;
  margin-left: auto;
  color: var(--primary-text-color);
}
.search-modal__close-icon {
  height: 20px;
  width: 20px;
}
.search-modal__close:hover, .search-modal__close:focus {
  color: var(--link-hover-color);
}
.search-modal__label {
  text-align: left;
}

#navigation-modal {
  transition: opacity 0.2s, visibility 0s 0.2s;
  height: 100%;
  left: 0;
  opacity: 0;
  position: fixed;
  text-align: center;
  top: 0;
  visibility: hidden;
  width: 100%;
  z-index: 1000;
  overscroll-behavior: contain;
  background: var(--header-background-color);
}
#navigation-modal[aria-hidden="false"] {
  transition: opacity 0.2s;
  opacity: 1;
  visibility: visible;
}
#navigation-modal .overlay-content {
  height: 100%;
  overflow-y: scroll;
  padding: 0 0 90px;
}
#navigation-modal .navigation-modal-header {
  height: var(--header-height);
  padding: 20px;
  display: flex;
  align-items: center;
  justify-content: flex-end;
}
#navigation-modal .close-navigation {
  cursor: pointer;
  color: var(--header-text-color);
  height: 40px;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 0px;
  width: 40px;
}
#navigation-modal .close-navigation:hover {
  opacity: 0.85;
}
#navigation-modal .close-navigation svg {
  fill: currentColor;
}
#navigation-modal .navigation-modal-content {
  padding: 0 16px;
}
#navigation-modal .overlay-page-list {
  text-align: left;
  font-size: 1.25rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 24px;
  margin: 16px 0 32px;
}
#navigation-modal .overlay-page-list a {
  color: var(--header-text-color);
}
#navigation-modal .overlay-page-list a:hover {
  text-decoration: underline;
  opacity: 0.85;
}

#maintenance {
  -ms-flex-align: center;
  align-items: center;
  display: -ms-flexbox;
  display: flex;
  font-size: 1.25em;
  padding: 100px 20px;
  text-align: center;
}
#maintenance .maintenance-container {
  display: grid;
  gap: 48px;
}
#maintenance .maintenance-store-name {
  font-size: 1.5em;
  margin: 0;
}
/*


*/

/*============================================================
  Custom Styles - add and override styles below.
============================================================*/
