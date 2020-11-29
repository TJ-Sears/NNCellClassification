# NNCellClassification
Using Keras for Cell Classifcation from RNAseq data

<!DOCTYPE html>
<html>
<head><meta charset="utf-8" />

<title>NN_Cell_Classification</title>

<script src="https://cdnjs.cloudflare.com/ajax/libs/require.js/2.1.10/require.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/2.0.3/jquery.min.js"></script>



<style type="text/css">
    /*!
*
* Twitter Bootstrap
*
*/
/*!
 * Bootstrap v3.3.7 (http://getbootstrap.com)
 * Copyright 2011-2016 Twitter, Inc.
 * Licensed under MIT (https://github.com/twbs/bootstrap/blob/master/LICENSE)
 */
/*! normalize.css v3.0.3 | MIT License | github.com/necolas/normalize.css */
html {
  font-family: sans-serif;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
}
body {
  margin: 0;
}
article,
aside,
details,
figcaption,
figure,
footer,
header,
hgroup,
main,
menu,
nav,
section,
summary {
  display: block;
}
audio,
canvas,
progress,
video {
  display: inline-block;
  vertical-align: baseline;
}
audio:not([controls]) {
  display: none;
  height: 0;
}
[hidden],
template {
  display: none;
}
a {
  background-color: transparent;
}
a:active,
a:hover {
  outline: 0;
}
abbr[title] {
  border-bottom: 1px dotted;
}
b,
strong {
  font-weight: bold;
}
dfn {
  font-style: italic;
}
h1 {
  font-size: 2em;
  margin: 0.67em 0;
}
mark {
  background: #ff0;
  color: #000;
}
small {
  font-size: 80%;
}
sub,
sup {
  font-size: 75%;
  line-height: 0;
  position: relative;
  vertical-align: baseline;
}
sup {
  top: -0.5em;
}
sub {
  bottom: -0.25em;
}
img {
  border: 0;
}
svg:not(:root) {
  overflow: hidden;
}
figure {
  margin: 1em 40px;
}
hr {
  box-sizing: content-box;
  height: 0;
}
pre {
  overflow: auto;
}
code,
kbd,
pre,
samp {
  font-family: monospace, monospace;
  font-size: 1em;
}
button,
input,
optgroup,
select,
textarea {
  color: inherit;
  font: inherit;
  margin: 0;
}
button {
  overflow: visible;
}
button,
select {
  text-transform: none;
}
button,
html input[type="button"],
input[type="reset"],
input[type="submit"] {
  -webkit-appearance: button;
  cursor: pointer;
}
button[disabled],
html input[disabled] {
  cursor: default;
}
button::-moz-focus-inner,
input::-moz-focus-inner {
  border: 0;
  padding: 0;
}
input {
  line-height: normal;
}
input[type="checkbox"],
input[type="radio"] {
  box-sizing: border-box;
  padding: 0;
}
input[type="number"]::-webkit-inner-spin-button,
input[type="number"]::-webkit-outer-spin-button {
  height: auto;
}
input[type="search"] {
  -webkit-appearance: textfield;
  box-sizing: content-box;
}
input[type="search"]::-webkit-search-cancel-button,
input[type="search"]::-webkit-search-decoration {
  -webkit-appearance: none;
}
fieldset {
  border: 1px solid #c0c0c0;
  margin: 0 2px;
  padding: 0.35em 0.625em 0.75em;
}
legend {
  border: 0;
  padding: 0;
}
textarea {
  overflow: auto;
}
optgroup {
  font-weight: bold;
}
table {
  border-collapse: collapse;
  border-spacing: 0;
}
td,
th {
  padding: 0;
}
/*! Source: https://github.com/h5bp/html5-boilerplate/blob/master/src/css/main.css */
@media print {
  *,
  *:before,
  *:after {
    background: transparent !important;
    box-shadow: none !important;
    text-shadow: none !important;
  }
  a,
  a:visited {
    text-decoration: underline;
  }
  a[href]:after {
    content: " (" attr(href) ")";
  }
  abbr[title]:after {
    content: " (" attr(title) ")";
  }
  a[href^="#"]:after,
  a[href^="javascript:"]:after {
    content: "";
  }
  pre,
  blockquote {
    border: 1px solid #999;
    page-break-inside: avoid;
  }
  thead {
    display: table-header-group;
  }
  tr,
  img {
    page-break-inside: avoid;
  }
  img {
    max-width: 100% !important;
  }
  p,
  h2,
  h3 {
    orphans: 3;
    widows: 3;
  }
  h2,
  h3 {
    page-break-after: avoid;
  }
  .navbar {
    display: none;
  }
  .btn > .caret,
  .dropup > .btn > .caret {
    border-top-color: #000 !important;
  }
  .label {
    border: 1px solid #000;
  }
  .table {
    border-collapse: collapse !important;
  }
  .table td,
  .table th {
    background-color: #fff !important;
  }
  .table-bordered th,
  .table-bordered td {
    border: 1px solid #ddd !important;
  }
}
@font-face {
  font-family: 'Glyphicons Halflings';
  src: url('../components/bootstrap/fonts/glyphicons-halflings-regular.eot');
  src: url('../components/bootstrap/fonts/glyphicons-halflings-regular.eot?#iefix') format('embedded-opentype'), url('../components/bootstrap/fonts/glyphicons-halflings-regular.woff2') format('woff2'), url('../components/bootstrap/fonts/glyphicons-halflings-regular.woff') format('woff'), url('../components/bootstrap/fonts/glyphicons-halflings-regular.ttf') format('truetype'), url('../components/bootstrap/fonts/glyphicons-halflings-regular.svg#glyphicons_halflingsregular') format('svg');
}
.glyphicon {
  position: relative;
  top: 1px;
  display: inline-block;
  font-family: 'Glyphicons Halflings';
  font-style: normal;
  font-weight: normal;
  line-height: 1;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
.glyphicon-asterisk:before {
  content: "\002a";
}
.glyphicon-plus:before {
  content: "\002b";
}
.glyphicon-euro:before,
.glyphicon-eur:before {
  content: "\20ac";
}
.glyphicon-minus:before {
  content: "\2212";
}
.glyphicon-cloud:before {
  content: "\2601";
}
.glyphicon-envelope:before {
  content: "\2709";
}
.glyphicon-pencil:before {
  content: "\270f";
}
.glyphicon-glass:before {
  content: "\e001";
}
.glyphicon-music:before {
  content: "\e002";
}
.glyphicon-search:before {
  content: "\e003";
}
.glyphicon-heart:before {
  content: "\e005";
}
.glyphicon-star:before {
  content: "\e006";
}
.glyphicon-star-empty:before {
  content: "\e007";
}
.glyphicon-user:before {
  content: "\e008";
}
.glyphicon-film:before {
  content: "\e009";
}
.glyphicon-th-large:before {
  content: "\e010";
}
.glyphicon-th:before {
  content: "\e011";
}
.glyphicon-th-list:before {
  content: "\e012";
}
.glyphicon-ok:before {
  content: "\e013";
}
.glyphicon-remove:before {
  content: "\e014";
}
.glyphicon-zoom-in:before {
  content: "\e015";
}
.glyphicon-zoom-out:before {
  content: "\e016";
}
.glyphicon-off:before {
  content: "\e017";
}
.glyphicon-signal:before {
  content: "\e018";
}
.glyphicon-cog:before {
  content: "\e019";
}
.glyphicon-trash:before {
  content: "\e020";
}
.glyphicon-home:before {
  content: "\e021";
}
.glyphicon-file:before {
  content: "\e022";
}
.glyphicon-time:before {
  content: "\e023";
}
.glyphicon-road:before {
  content: "\e024";
}
.glyphicon-download-alt:before {
  content: "\e025";
}
.glyphicon-download:before {
  content: "\e026";
}
.glyphicon-upload:before {
  content: "\e027";
}
.glyphicon-inbox:before {
  content: "\e028";
}
.glyphicon-play-circle:before {
  content: "\e029";
}
.glyphicon-repeat:before {
  content: "\e030";
}
.glyphicon-refresh:before {
  content: "\e031";
}
.glyphicon-list-alt:before {
  content: "\e032";
}
.glyphicon-lock:before {
  content: "\e033";
}
.glyphicon-flag:before {
  content: "\e034";
}
.glyphicon-headphones:before {
  content: "\e035";
}
.glyphicon-volume-off:before {
  content: "\e036";
}
.glyphicon-volume-down:before {
  content: "\e037";
}
.glyphicon-volume-up:before {
  content: "\e038";
}
.glyphicon-qrcode:before {
  content: "\e039";
}
.glyphicon-barcode:before {
  content: "\e040";
}
.glyphicon-tag:before {
  content: "\e041";
}
.glyphicon-tags:before {
  content: "\e042";
}
.glyphicon-book:before {
  content: "\e043";
}
.glyphicon-bookmark:before {
  content: "\e044";
}
.glyphicon-print:before {
  content: "\e045";
}
.glyphicon-camera:before {
  content: "\e046";
}
.glyphicon-font:before {
  content: "\e047";
}
.glyphicon-bold:before {
  content: "\e048";
}
.glyphicon-italic:before {
  content: "\e049";
}
.glyphicon-text-height:before {
  content: "\e050";
}
.glyphicon-text-width:before {
  content: "\e051";
}
.glyphicon-align-left:before {
  content: "\e052";
}
.glyphicon-align-center:before {
  content: "\e053";
}
.glyphicon-align-right:before {
  content: "\e054";
}
.glyphicon-align-justify:before {
  content: "\e055";
}
.glyphicon-list:before {
  content: "\e056";
}
.glyphicon-indent-left:before {
  content: "\e057";
}
.glyphicon-indent-right:before {
  content: "\e058";
}
.glyphicon-facetime-video:before {
  content: "\e059";
}
.glyphicon-picture:before {
  content: "\e060";
}
.glyphicon-map-marker:before {
  content: "\e062";
}
.glyphicon-adjust:before {
  content: "\e063";
}
.glyphicon-tint:before {
  content: "\e064";
}
.glyphicon-edit:before {
  content: "\e065";
}
.glyphicon-share:before {
  content: "\e066";
}
.glyphicon-check:before {
  content: "\e067";
}
.glyphicon-move:before {
  content: "\e068";
}
.glyphicon-step-backward:before {
  content: "\e069";
}
.glyphicon-fast-backward:before {
  content: "\e070";
}
.glyphicon-backward:before {
  content: "\e071";
}
.glyphicon-play:before {
  content: "\e072";
}
.glyphicon-pause:before {
  content: "\e073";
}
.glyphicon-stop:before {
  content: "\e074";
}
.glyphicon-forward:before {
  content: "\e075";
}
.glyphicon-fast-forward:before {
  content: "\e076";
}
.glyphicon-step-forward:before {
  content: "\e077";
}
.glyphicon-eject:before {
  content: "\e078";
}
.glyphicon-chevron-left:before {
  content: "\e079";
}
.glyphicon-chevron-right:before {
  content: "\e080";
}
.glyphicon-plus-sign:before {
  content: "\e081";
}
.glyphicon-minus-sign:before {
  content: "\e082";
}
.glyphicon-remove-sign:before {
  content: "\e083";
}
.glyphicon-ok-sign:before {
  content: "\e084";
}
.glyphicon-question-sign:before {
  content: "\e085";
}
.glyphicon-info-sign:before {
  content: "\e086";
}
.glyphicon-screenshot:before {
  content: "\e087";
}
.glyphicon-remove-circle:before {
  content: "\e088";
}
.glyphicon-ok-circle:before {
  content: "\e089";
}
.glyphicon-ban-circle:before {
  content: "\e090";
}
.glyphicon-arrow-left:before {
  content: "\e091";
}
.glyphicon-arrow-right:before {
  content: "\e092";
}
.glyphicon-arrow-up:before {
  content: "\e093";
}
.glyphicon-arrow-down:before {
  content: "\e094";
}
.glyphicon-share-alt:before {
  content: "\e095";
}
.glyphicon-resize-full:before {
  content: "\e096";
}
.glyphicon-resize-small:before {
  content: "\e097";
}
.glyphicon-exclamation-sign:before {
  content: "\e101";
}
.glyphicon-gift:before {
  content: "\e102";
}
.glyphicon-leaf:before {
  content: "\e103";
}
.glyphicon-fire:before {
  content: "\e104";
}
.glyphicon-eye-open:before {
  content: "\e105";
}
.glyphicon-eye-close:before {
  content: "\e106";
}
.glyphicon-warning-sign:before {
  content: "\e107";
}
.glyphicon-plane:before {
  content: "\e108";
}
.glyphicon-calendar:before {
  content: "\e109";
}
.glyphicon-random:before {
  content: "\e110";
}
.glyphicon-comment:before {
  content: "\e111";
}
.glyphicon-magnet:before {
  content: "\e112";
}
.glyphicon-chevron-up:before {
  content: "\e113";
}
.glyphicon-chevron-down:before {
  content: "\e114";
}
.glyphicon-retweet:before {
  content: "\e115";
}
.glyphicon-shopping-cart:before {
  content: "\e116";
}
.glyphicon-folder-close:before {
  content: "\e117";
}
.glyphicon-folder-open:before {
  content: "\e118";
}
.glyphicon-resize-vertical:before {
  content: "\e119";
}
.glyphicon-resize-horizontal:before {
  content: "\e120";
}
.glyphicon-hdd:before {
  content: "\e121";
}
.glyphicon-bullhorn:before {
  content: "\e122";
}
.glyphicon-bell:before {
  content: "\e123";
}
.glyphicon-certificate:before {
  content: "\e124";
}
.glyphicon-thumbs-up:before {
  content: "\e125";
}
.glyphicon-thumbs-down:before {
  content: "\e126";
}
.glyphicon-hand-right:before {
  content: "\e127";
}
.glyphicon-hand-left:before {
  content: "\e128";
}
.glyphicon-hand-up:before {
  content: "\e129";
}
.glyphicon-hand-down:before {
  content: "\e130";
}
.glyphicon-circle-arrow-right:before {
  content: "\e131";
}
.glyphicon-circle-arrow-left:before {
  content: "\e132";
}
.glyphicon-circle-arrow-up:before {
  content: "\e133";
}
.glyphicon-circle-arrow-down:before {
  content: "\e134";
}
.glyphicon-globe:before {
  content: "\e135";
}
.glyphicon-wrench:before {
  content: "\e136";
}
.glyphicon-tasks:before {
  content: "\e137";
}
.glyphicon-filter:before {
  content: "\e138";
}
.glyphicon-briefcase:before {
  content: "\e139";
}
.glyphicon-fullscreen:before {
  content: "\e140";
}
.glyphicon-dashboard:before {
  content: "\e141";
}
.glyphicon-paperclip:before {
  content: "\e142";
}
.glyphicon-heart-empty:before {
  content: "\e143";
}
.glyphicon-link:before {
  content: "\e144";
}
.glyphicon-phone:before {
  content: "\e145";
}
.glyphicon-pushpin:before {
  content: "\e146";
}
.glyphicon-usd:before {
  content: "\e148";
}
.glyphicon-gbp:before {
  content: "\e149";
}
.glyphicon-sort:before {
  content: "\e150";
}
.glyphicon-sort-by-alphabet:before {
  content: "\e151";
}
.glyphicon-sort-by-alphabet-alt:before {
  content: "\e152";
}
.glyphicon-sort-by-order:before {
  content: "\e153";
}
.glyphicon-sort-by-order-alt:before {
  content: "\e154";
}
.glyphicon-sort-by-attributes:before {
  content: "\e155";
}
.glyphicon-sort-by-attributes-alt:before {
  content: "\e156";
}
.glyphicon-unchecked:before {
  content: "\e157";
}
.glyphicon-expand:before {
  content: "\e158";
}
.glyphicon-collapse-down:before {
  content: "\e159";
}
.glyphicon-collapse-up:before {
  content: "\e160";
}
.glyphicon-log-in:before {
  content: "\e161";
}
.glyphicon-flash:before {
  content: "\e162";
}
.glyphicon-log-out:before {
  content: "\e163";
}
.glyphicon-new-window:before {
  content: "\e164";
}
.glyphicon-record:before {
  content: "\e165";
}
.glyphicon-save:before {
  content: "\e166";
}
.glyphicon-open:before {
  content: "\e167";
}
.glyphicon-saved:before {
  content: "\e168";
}
.glyphicon-import:before {
  content: "\e169";
}
.glyphicon-export:before {
  content: "\e170";
}
.glyphicon-send:before {
  content: "\e171";
}
.glyphicon-floppy-disk:before {
  content: "\e172";
}
.glyphicon-floppy-saved:before {
  content: "\e173";
}
.glyphicon-floppy-remove:before {
  content: "\e174";
}
.glyphicon-floppy-save:before {
  content: "\e175";
}
.glyphicon-floppy-open:before {
  content: "\e176";
}
.glyphicon-credit-card:before {
  content: "\e177";
}
.glyphicon-transfer:before {
  content: "\e178";
}
.glyphicon-cutlery:before {
  content: "\e179";
}
.glyphicon-header:before {
  content: "\e180";
}
.glyphicon-compressed:before {
  content: "\e181";
}
.glyphicon-earphone:before {
  content: "\e182";
}
.glyphicon-phone-alt:before {
  content: "\e183";
}
.glyphicon-tower:before {
  content: "\e184";
}
.glyphicon-stats:before {
  content: "\e185";
}
.glyphicon-sd-video:before {
  content: "\e186";
}
.glyphicon-hd-video:before {
  content: "\e187";
}
.glyphicon-subtitles:before {
  content: "\e188";
}
.glyphicon-sound-stereo:before {
  content: "\e189";
}
.glyphicon-sound-dolby:before {
  content: "\e190";
}
.glyphicon-sound-5-1:before {
  content: "\e191";
}
.glyphicon-sound-6-1:before {
  content: "\e192";
}
.glyphicon-sound-7-1:before {
  content: "\e193";
}
.glyphicon-copyright-mark:before {
  content: "\e194";
}
.glyphicon-registration-mark:before {
  content: "\e195";
}
.glyphicon-cloud-download:before {
  content: "\e197";
}
.glyphicon-cloud-upload:before {
  content: "\e198";
}
.glyphicon-tree-conifer:before {
  content: "\e199";
}
.glyphicon-tree-deciduous:before {
  content: "\e200";
}
.glyphicon-cd:before {
  content: "\e201";
}
.glyphicon-save-file:before {
  content: "\e202";
}
.glyphicon-open-file:before {
  content: "\e203";
}
.glyphicon-level-up:before {
  content: "\e204";
}
.glyphicon-copy:before {
  content: "\e205";
}
.glyphicon-paste:before {
  content: "\e206";
}
.glyphicon-alert:before {
  content: "\e209";
}
.glyphicon-equalizer:before {
  content: "\e210";
}
.glyphicon-king:before {
  content: "\e211";
}
.glyphicon-queen:before {
  content: "\e212";
}
.glyphicon-pawn:before {
  content: "\e213";
}
.glyphicon-bishop:before {
  content: "\e214";
}
.glyphicon-knight:before {
  content: "\e215";
}
.glyphicon-baby-formula:before {
  content: "\e216";
}
.glyphicon-tent:before {
  content: "\26fa";
}
.glyphicon-blackboard:before {
  content: "\e218";
}
.glyphicon-bed:before {
  content: "\e219";
}
.glyphicon-apple:before {
  content: "\f8ff";
}
.glyphicon-erase:before {
  content: "\e221";
}
.glyphicon-hourglass:before {
  content: "\231b";
}
.glyphicon-lamp:before {
  content: "\e223";
}
.glyphicon-duplicate:before {
  content: "\e224";
}
.glyphicon-piggy-bank:before {
  content: "\e225";
}
.glyphicon-scissors:before {
  content: "\e226";
}
.glyphicon-bitcoin:before {
  content: "\e227";
}
.glyphicon-btc:before {
  content: "\e227";
}
.glyphicon-xbt:before {
  content: "\e227";
}
.glyphicon-yen:before {
  content: "\00a5";
}
.glyphicon-jpy:before {
  content: "\00a5";
}
.glyphicon-ruble:before {
  content: "\20bd";
}
.glyphicon-rub:before {
  content: "\20bd";
}
.glyphicon-scale:before {
  content: "\e230";
}
.glyphicon-ice-lolly:before {
  content: "\e231";
}
.glyphicon-ice-lolly-tasted:before {
  content: "\e232";
}
.glyphicon-education:before {
  content: "\e233";
}
.glyphicon-option-horizontal:before {
  content: "\e234";
}
.glyphicon-option-vertical:before {
  content: "\e235";
}
.glyphicon-menu-hamburger:before {
  content: "\e236";
}
.glyphicon-modal-window:before {
  content: "\e237";
}
.glyphicon-oil:before {
  content: "\e238";
}
.glyphicon-grain:before {
  content: "\e239";
}
.glyphicon-sunglasses:before {
  content: "\e240";
}
.glyphicon-text-size:before {
  content: "\e241";
}
.glyphicon-text-color:before {
  content: "\e242";
}
.glyphicon-text-background:before {
  content: "\e243";
}
.glyphicon-object-align-top:before {
  content: "\e244";
}
.glyphicon-object-align-bottom:before {
  content: "\e245";
}
.glyphicon-object-align-horizontal:before {
  content: "\e246";
}
.glyphicon-object-align-left:before {
  content: "\e247";
}
.glyphicon-object-align-vertical:before {
  content: "\e248";
}
.glyphicon-object-align-right:before {
  content: "\e249";
}
.glyphicon-triangle-right:before {
  content: "\e250";
}
.glyphicon-triangle-left:before {
  content: "\e251";
}
.glyphicon-triangle-bottom:before {
  content: "\e252";
}
.glyphicon-triangle-top:before {
  content: "\e253";
}
.glyphicon-console:before {
  content: "\e254";
}
.glyphicon-superscript:before {
  content: "\e255";
}
.glyphicon-subscript:before {
  content: "\e256";
}
.glyphicon-menu-left:before {
  content: "\e257";
}
.glyphicon-menu-right:before {
  content: "\e258";
}
.glyphicon-menu-down:before {
  content: "\e259";
}
.glyphicon-menu-up:before {
  content: "\e260";
}
* {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}
*:before,
*:after {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}
html {
  font-size: 10px;
  -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
}
body {
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
  font-size: 13px;
  line-height: 1.42857143;
  color: #000;
  background-color: #fff;
}
input,
button,
select,
textarea {
  font-family: inherit;
  font-size: inherit;
  line-height: inherit;
}
a {
  color: #337ab7;
  text-decoration: none;
}
a:hover,
a:focus {
  color: #23527c;
  text-decoration: underline;
}
a:focus {
  outline: 5px auto -webkit-focus-ring-color;
  outline-offset: -2px;
}
figure {
  margin: 0;
}
img {
  vertical-align: middle;
}
.img-responsive,
.thumbnail > img,
.thumbnail a > img,
.carousel-inner > .item > img,
.carousel-inner > .item > a > img {
  display: block;
  max-width: 100%;
  height: auto;
}
.img-rounded {
  border-radius: 3px;
}
.img-thumbnail {
  padding: 4px;
  line-height: 1.42857143;
  background-color: #fff;
  border: 1px solid #ddd;
  border-radius: 2px;
  -webkit-transition: all 0.2s ease-in-out;
  -o-transition: all 0.2s ease-in-out;
  transition: all 0.2s ease-in-out;
  display: inline-block;
  max-width: 100%;
  height: auto;
}
.img-circle {
  border-radius: 50%;
}
hr {
  margin-top: 18px;
  margin-bottom: 18px;
  border: 0;
  border-top: 1px solid #eeeeee;
}
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  margin: -1px;
  padding: 0;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  border: 0;
}
.sr-only-focusable:active,
.sr-only-focusable:focus {
  position: static;
  width: auto;
  height: auto;
  margin: 0;
  overflow: visible;
  clip: auto;
}
[role="button"] {
  cursor: pointer;
}
h1,
h2,
h3,
h4,
h5,
h6,
.h1,
.h2,
.h3,
.h4,
.h5,
.h6 {
  font-family: inherit;
  font-weight: 500;
  line-height: 1.1;
  color: inherit;
}
h1 small,
h2 small,
h3 small,
h4 small,
h5 small,
h6 small,
.h1 small,
.h2 small,
.h3 small,
.h4 small,
.h5 small,
.h6 small,
h1 .small,
h2 .small,
h3 .small,
h4 .small,
h5 .small,
h6 .small,
.h1 .small,
.h2 .small,
.h3 .small,
.h4 .small,
.h5 .small,
.h6 .small {
  font-weight: normal;
  line-height: 1;
  color: #777777;
}
h1,
.h1,
h2,
.h2,
h3,
.h3 {
  margin-top: 18px;
  margin-bottom: 9px;
}
h1 small,
.h1 small,
h2 small,
.h2 small,
h3 small,
.h3 small,
h1 .small,
.h1 .small,
h2 .small,
.h2 .small,
h3 .small,
.h3 .small {
  font-size: 65%;
}
h4,
.h4,
h5,
.h5,
h6,
.h6 {
  margin-top: 9px;
  margin-bottom: 9px;
}
h4 small,
.h4 small,
h5 small,
.h5 small,
h6 small,
.h6 small,
h4 .small,
.h4 .small,
h5 .small,
.h5 .small,
h6 .small,
.h6 .small {
  font-size: 75%;
}
h1,
.h1 {
  font-size: 33px;
}
h2,
.h2 {
  font-size: 27px;
}
h3,
.h3 {
  font-size: 23px;
}
h4,
.h4 {
  font-size: 17px;
}
h5,
.h5 {
  font-size: 13px;
}
h6,
.h6 {
  font-size: 12px;
}
p {
  margin: 0 0 9px;
}
.lead {
  margin-bottom: 18px;
  font-size: 14px;
  font-weight: 300;
  line-height: 1.4;
}
@media (min-width: 768px) {
  .lead {
    font-size: 19.5px;
  }
}
small,
.small {
  font-size: 92%;
}
mark,
.mark {
  background-color: #fcf8e3;
  padding: .2em;
}
.text-left {
  text-align: left;
}
.text-right {
  text-align: right;
}
.text-center {
  text-align: center;
}
.text-justify {
  text-align: justify;
}
.text-nowrap {
  white-space: nowrap;
}
.text-lowercase {
  text-transform: lowercase;
}
.text-uppercase {
  text-transform: uppercase;
}
.text-capitalize {
  text-transform: capitalize;
}
.text-muted {
  color: #777777;
}
.text-primary {
  color: #337ab7;
}
a.text-primary:hover,
a.text-primary:focus {
  color: #286090;
}
.text-success {
  color: #3c763d;
}
a.text-success:hover,
a.text-success:focus {
  color: #2b542c;
}
.text-info {
  color: #31708f;
}
a.text-info:hover,
a.text-info:focus {
  color: #245269;
}
.text-warning {
  color: #8a6d3b;
}
a.text-warning:hover,
a.text-warning:focus {
  color: #66512c;
}
.text-danger {
  color: #a94442;
}
a.text-danger:hover,
a.text-danger:focus {
  color: #843534;
}
.bg-primary {
  color: #fff;
  background-color: #337ab7;
}
a.bg-primary:hover,
a.bg-primary:focus {
  background-color: #286090;
}
.bg-success {
  background-color: #dff0d8;
}
a.bg-success:hover,
a.bg-success:focus {
  background-color: #c1e2b3;
}
.bg-info {
  background-color: #d9edf7;
}
a.bg-info:hover,
a.bg-info:focus {
  background-color: #afd9ee;
}
.bg-warning {
  background-color: #fcf8e3;
}
a.bg-warning:hover,
a.bg-warning:focus {
  background-color: #f7ecb5;
}
.bg-danger {
  background-color: #f2dede;
}
a.bg-danger:hover,
a.bg-danger:focus {
  background-color: #e4b9b9;
}
.page-header {
  padding-bottom: 8px;
  margin: 36px 0 18px;
  border-bottom: 1px solid #eeeeee;
}
ul,
ol {
  margin-top: 0;
  margin-bottom: 9px;
}
ul ul,
ol ul,
ul ol,
ol ol {
  margin-bottom: 0;
}
.list-unstyled {
  padding-left: 0;
  list-style: none;
}
.list-inline {
  padding-left: 0;
  list-style: none;
  margin-left: -5px;
}
.list-inline > li {
  display: inline-block;
  padding-left: 5px;
  padding-right: 5px;
}
dl {
  margin-top: 0;
  margin-bottom: 18px;
}
dt,
dd {
  line-height: 1.42857143;
}
dt {
  font-weight: bold;
}
dd {
  margin-left: 0;
}
@media (min-width: 541px) {
  .dl-horizontal dt {
    float: left;
    width: 160px;
    clear: left;
    text-align: right;
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
  }
  .dl-horizontal dd {
    margin-left: 180px;
  }
}
abbr[title],
abbr[data-original-title] {
  cursor: help;
  border-bottom: 1px dotted #777777;
}
.initialism {
  font-size: 90%;
  text-transform: uppercase;
}
blockquote {
  padding: 9px 18px;
  margin: 0 0 18px;
  font-size: inherit;
  border-left: 5px solid #eeeeee;
}
blockquote p:last-child,
blockquote ul:last-child,
blockquote ol:last-child {
  margin-bottom: 0;
}
blockquote footer,
blockquote small,
blockquote .small {
  display: block;
  font-size: 80%;
  line-height: 1.42857143;
  color: #777777;
}
blockquote footer:before,
blockquote small:before,
blockquote .small:before {
  content: '\2014 \00A0';
}
.blockquote-reverse,
blockquote.pull-right {
  padding-right: 15px;
  padding-left: 0;
  border-right: 5px solid #eeeeee;
  border-left: 0;
  text-align: right;
}
.blockquote-reverse footer:before,
blockquote.pull-right footer:before,
.blockquote-reverse small:before,
blockquote.pull-right small:before,
.blockquote-reverse .small:before,
blockquote.pull-right .small:before {
  content: '';
}
.blockquote-reverse footer:after,
blockquote.pull-right footer:after,
.blockquote-reverse small:after,
blockquote.pull-right small:after,
.blockquote-reverse .small:after,
blockquote.pull-right .small:after {
  content: '\00A0 \2014';
}
address {
  margin-bottom: 18px;
  font-style: normal;
  line-height: 1.42857143;
}
code,
kbd,
pre,
samp {
  font-family: monospace;
}
code {
  padding: 2px 4px;
  font-size: 90%;
  color: #c7254e;
  background-color: #f9f2f4;
  border-radius: 2px;
}
kbd {
  padding: 2px 4px;
  font-size: 90%;
  color: #888;
  background-color: transparent;
  border-radius: 1px;
  box-shadow: inset 0 -1px 0 rgba(0, 0, 0, 0.25);
}
kbd kbd {
  padding: 0;
  font-size: 100%;
  font-weight: bold;
  box-shadow: none;
}
pre {
  display: block;
  padding: 8.5px;
  margin: 0 0 9px;
  font-size: 12px;
  line-height: 1.42857143;
  word-break: break-all;
  word-wrap: break-word;
  color: #333333;
  background-color: #f5f5f5;
  border: 1px solid #ccc;
  border-radius: 2px;
}
pre code {
  padding: 0;
  font-size: inherit;
  color: inherit;
  white-space: pre-wrap;
  background-color: transparent;
  border-radius: 0;
}
.pre-scrollable {
  max-height: 340px;
  overflow-y: scroll;
}
.container {
  margin-right: auto;
  margin-left: auto;
  padding-left: 0px;
  padding-right: 0px;
}
@media (min-width: 768px) {
  .container {
    width: 768px;
  }
}
@media (min-width: 992px) {
  .container {
    width: 940px;
  }
}
@media (min-width: 1200px) {
  .container {
    width: 1140px;
  }
}
.container-fluid {
  margin-right: auto;
  margin-left: auto;
  padding-left: 0px;
  padding-right: 0px;
}
.row {
  margin-left: 0px;
  margin-right: 0px;
}
.col-xs-1, .col-sm-1, .col-md-1, .col-lg-1, .col-xs-2, .col-sm-2, .col-md-2, .col-lg-2, .col-xs-3, .col-sm-3, .col-md-3, .col-lg-3, .col-xs-4, .col-sm-4, .col-md-4, .col-lg-4, .col-xs-5, .col-sm-5, .col-md-5, .col-lg-5, .col-xs-6, .col-sm-6, .col-md-6, .col-lg-6, .col-xs-7, .col-sm-7, .col-md-7, .col-lg-7, .col-xs-8, .col-sm-8, .col-md-8, .col-lg-8, .col-xs-9, .col-sm-9, .col-md-9, .col-lg-9, .col-xs-10, .col-sm-10, .col-md-10, .col-lg-10, .col-xs-11, .col-sm-11, .col-md-11, .col-lg-11, .col-xs-12, .col-sm-12, .col-md-12, .col-lg-12 {
  position: relative;
  min-height: 1px;
  padding-left: 0px;
  padding-right: 0px;
}
.col-xs-1, .col-xs-2, .col-xs-3, .col-xs-4, .col-xs-5, .col-xs-6, .col-xs-7, .col-xs-8, .col-xs-9, .col-xs-10, .col-xs-11, .col-xs-12 {
  float: left;
}
.col-xs-12 {
  width: 100%;
}
.col-xs-11 {
  width: 91.66666667%;
}
.col-xs-10 {
  width: 83.33333333%;
}
.col-xs-9 {
  width: 75%;
}
.col-xs-8 {
  width: 66.66666667%;
}
.col-xs-7 {
  width: 58.33333333%;
}
.col-xs-6 {
  width: 50%;
}
.col-xs-5 {
  width: 41.66666667%;
}
.col-xs-4 {
  width: 33.33333333%;
}
.col-xs-3 {
  width: 25%;
}
.col-xs-2 {
  width: 16.66666667%;
}
.col-xs-1 {
  width: 8.33333333%;
}
.col-xs-pull-12 {
  right: 100%;
}
.col-xs-pull-11 {
  right: 91.66666667%;
}
.col-xs-pull-10 {
  right: 83.33333333%;
}
.col-xs-pull-9 {
  right: 75%;
}
.col-xs-pull-8 {
  right: 66.66666667%;
}
.col-xs-pull-7 {
  right: 58.33333333%;
}
.col-xs-pull-6 {
  right: 50%;
}
.col-xs-pull-5 {
  right: 41.66666667%;
}
.col-xs-pull-4 {
  right: 33.33333333%;
}
.col-xs-pull-3 {
  right: 25%;
}
.col-xs-pull-2 {
  right: 16.66666667%;
}
.col-xs-pull-1 {
  right: 8.33333333%;
}
.col-xs-pull-0 {
  right: auto;
}
.col-xs-push-12 {
  left: 100%;
}
.col-xs-push-11 {
  left: 91.66666667%;
}
.col-xs-push-10 {
  left: 83.33333333%;
}
.col-xs-push-9 {
  left: 75%;
}
.col-xs-push-8 {
  left: 66.66666667%;
}
.col-xs-push-7 {
  left: 58.33333333%;
}
.col-xs-push-6 {
  left: 50%;
}
.col-xs-push-5 {
  left: 41.66666667%;
}
.col-xs-push-4 {
  left: 33.33333333%;
}
.col-xs-push-3 {
  left: 25%;
}
.col-xs-push-2 {
  left: 16.66666667%;
}
.col-xs-push-1 {
  left: 8.33333333%;
}
.col-xs-push-0 {
  left: auto;
}
.col-xs-offset-12 {
  margin-left: 100%;
}
.col-xs-offset-11 {
  margin-left: 91.66666667%;
}
.col-xs-offset-10 {
  margin-left: 83.33333333%;
}
.col-xs-offset-9 {
  margin-left: 75%;
}
.col-xs-offset-8 {
  margin-left: 66.66666667%;
}
.col-xs-offset-7 {
  margin-left: 58.33333333%;
}
.col-xs-offset-6 {
  margin-left: 50%;
}
.col-xs-offset-5 {
  margin-left: 41.66666667%;
}
.col-xs-offset-4 {
  margin-left: 33.33333333%;
}
.col-xs-offset-3 {
  margin-left: 25%;
}
.col-xs-offset-2 {
  margin-left: 16.66666667%;
}
.col-xs-offset-1 {
  margin-left: 8.33333333%;
}
.col-xs-offset-0 {
  margin-left: 0%;
}
@media (min-width: 768px) {
  .col-sm-1, .col-sm-2, .col-sm-3, .col-sm-4, .col-sm-5, .col-sm-6, .col-sm-7, .col-sm-8, .col-sm-9, .col-sm-10, .col-sm-11, .col-sm-12 {
    float: left;
  }
  .col-sm-12 {
    width: 100%;
  }
  .col-sm-11 {
    width: 91.66666667%;
  }
  .col-sm-10 {
    width: 83.33333333%;
  }
  .col-sm-9 {
    width: 75%;
  }
  .col-sm-8 {
    width: 66.66666667%;
  }
  .col-sm-7 {
    width: 58.33333333%;
  }
  .col-sm-6 {
    width: 50%;
  }
  .col-sm-5 {
    width: 41.66666667%;
  }
  .col-sm-4 {
    width: 33.33333333%;
  }
  .col-sm-3 {
    width: 25%;
  }
  .col-sm-2 {
    width: 16.66666667%;
  }
  .col-sm-1 {
    width: 8.33333333%;
  }
  .col-sm-pull-12 {
    right: 100%;
  }
  .col-sm-pull-11 {
    right: 91.66666667%;
  }
  .col-sm-pull-10 {
    right: 83.33333333%;
  }
  .col-sm-pull-9 {
    right: 75%;
  }
  .col-sm-pull-8 {
    right: 66.66666667%;
  }
  .col-sm-pull-7 {
    right: 58.33333333%;
  }
  .col-sm-pull-6 {
    right: 50%;
  }
  .col-sm-pull-5 {
    right: 41.66666667%;
  }
  .col-sm-pull-4 {
    right: 33.33333333%;
  }
  .col-sm-pull-3 {
    right: 25%;
  }
  .col-sm-pull-2 {
    right: 16.66666667%;
  }
  .col-sm-pull-1 {
    right: 8.33333333%;
  }
  .col-sm-pull-0 {
    right: auto;
  }
  .col-sm-push-12 {
    left: 100%;
  }
  .col-sm-push-11 {
    left: 91.66666667%;
  }
  .col-sm-push-10 {
    left: 83.33333333%;
  }
  .col-sm-push-9 {
    left: 75%;
  }
  .col-sm-push-8 {
    left: 66.66666667%;
  }
  .col-sm-push-7 {
    left: 58.33333333%;
  }
  .col-sm-push-6 {
    left: 50%;
  }
  .col-sm-push-5 {
    left: 41.66666667%;
  }
  .col-sm-push-4 {
    left: 33.33333333%;
  }
  .col-sm-push-3 {
    left: 25%;
  }
  .col-sm-push-2 {
    left: 16.66666667%;
  }
  .col-sm-push-1 {
    left: 8.33333333%;
  }
  .col-sm-push-0 {
    left: auto;
  }
  .col-sm-offset-12 {
    margin-left: 100%;
  }
  .col-sm-offset-11 {
    margin-left: 91.66666667%;
  }
  .col-sm-offset-10 {
    margin-left: 83.33333333%;
  }
  .col-sm-offset-9 {
    margin-left: 75%;
  }
  .col-sm-offset-8 {
    margin-left: 66.66666667%;
  }
  .col-sm-offset-7 {
    margin-left: 58.33333333%;
  }
  .col-sm-offset-6 {
    margin-left: 50%;
  }
  .col-sm-offset-5 {
    margin-left: 41.66666667%;
  }
  .col-sm-offset-4 {
    margin-left: 33.33333333%;
  }
  .col-sm-offset-3 {
    margin-left: 25%;
  }
  .col-sm-offset-2 {
    margin-left: 16.66666667%;
  }
  .col-sm-offset-1 {
    margin-left: 8.33333333%;
  }
  .col-sm-offset-0 {
    margin-left: 0%;
  }
}
@media (min-width: 992px) {
  .col-md-1, .col-md-2, .col-md-3, .col-md-4, .col-md-5, .col-md-6, .col-md-7, .col-md-8, .col-md-9, .col-md-10, .col-md-11, .col-md-12 {
    float: left;
  }
  .col-md-12 {
    width: 100%;
  }
  .col-md-11 {
    width: 91.66666667%;
  }
  .col-md-10 {
    width: 83.33333333%;
  }
  .col-md-9 {
    width: 75%;
  }
  .col-md-8 {
    width: 66.66666667%;
  }
  .col-md-7 {
    width: 58.33333333%;
  }
  .col-md-6 {
    width: 50%;
  }
  .col-md-5 {
    width: 41.66666667%;
  }
  .col-md-4 {
    width: 33.33333333%;
  }
  .col-md-3 {
    width: 25%;
  }
  .col-md-2 {
    width: 16.66666667%;
  }
  .col-md-1 {
    width: 8.33333333%;
  }
  .col-md-pull-12 {
    right: 100%;
  }
  .col-md-pull-11 {
    right: 91.66666667%;
  }
  .col-md-pull-10 {
    right: 83.33333333%;
  }
  .col-md-pull-9 {
    right: 75%;
  }
  .col-md-pull-8 {
    right: 66.66666667%;
  }
  .col-md-pull-7 {
    right: 58.33333333%;
  }
  .col-md-pull-6 {
    right: 50%;
  }
  .col-md-pull-5 {
    right: 41.66666667%;
  }
  .col-md-pull-4 {
    right: 33.33333333%;
  }
  .col-md-pull-3 {
    right: 25%;
  }
  .col-md-pull-2 {
    right: 16.66666667%;
  }
  .col-md-pull-1 {
    right: 8.33333333%;
  }
  .col-md-pull-0 {
    right: auto;
  }
  .col-md-push-12 {
    left: 100%;
  }
  .col-md-push-11 {
    left: 91.66666667%;
  }
  .col-md-push-10 {
    left: 83.33333333%;
  }
  .col-md-push-9 {
    left: 75%;
  }
  .col-md-push-8 {
    left: 66.66666667%;
  }
  .col-md-push-7 {
    left: 58.33333333%;
  }
  .col-md-push-6 {
    left: 50%;
  }
  .col-md-push-5 {
    left: 41.66666667%;
  }
  .col-md-push-4 {
    left: 33.33333333%;
  }
  .col-md-push-3 {
    left: 25%;
  }
  .col-md-push-2 {
    left: 16.66666667%;
  }
  .col-md-push-1 {
    left: 8.33333333%;
  }
  .col-md-push-0 {
    left: auto;
  }
  .col-md-offset-12 {
    margin-left: 100%;
  }
  .col-md-offset-11 {
    margin-left: 91.66666667%;
  }
  .col-md-offset-10 {
    margin-left: 83.33333333%;
  }
  .col-md-offset-9 {
    margin-left: 75%;
  }
  .col-md-offset-8 {
    margin-left: 66.66666667%;
  }
  .col-md-offset-7 {
    margin-left: 58.33333333%;
  }
  .col-md-offset-6 {
    margin-left: 50%;
  }
  .col-md-offset-5 {
    margin-left: 41.66666667%;
  }
  .col-md-offset-4 {
    margin-left: 33.33333333%;
  }
  .col-md-offset-3 {
    margin-left: 25%;
  }
  .col-md-offset-2 {
    margin-left: 16.66666667%;
  }
  .col-md-offset-1 {
    margin-left: 8.33333333%;
  }
  .col-md-offset-0 {
    margin-left: 0%;
  }
}
@media (min-width: 1200px) {
  .col-lg-1, .col-lg-2, .col-lg-3, .col-lg-4, .col-lg-5, .col-lg-6, .col-lg-7, .col-lg-8, .col-lg-9, .col-lg-10, .col-lg-11, .col-lg-12 {
    float: left;
  }
  .col-lg-12 {
    width: 100%;
  }
  .col-lg-11 {
    width: 91.66666667%;
  }
  .col-lg-10 {
    width: 83.33333333%;
  }
  .col-lg-9 {
    width: 75%;
  }
  .col-lg-8 {
    width: 66.66666667%;
  }
  .col-lg-7 {
    width: 58.33333333%;
  }
  .col-lg-6 {
    width: 50%;
  }
  .col-lg-5 {
    width: 41.66666667%;
  }
  .col-lg-4 {
    width: 33.33333333%;
  }
  .col-lg-3 {
    width: 25%;
  }
  .col-lg-2 {
    width: 16.66666667%;
  }
  .col-lg-1 {
    width: 8.33333333%;
  }
  .col-lg-pull-12 {
    right: 100%;
  }
  .col-lg-pull-11 {
    right: 91.66666667%;
  }
  .col-lg-pull-10 {
    right: 83.33333333%;
  }
  .col-lg-pull-9 {
    right: 75%;
  }
  .col-lg-pull-8 {
    right: 66.66666667%;
  }
  .col-lg-pull-7 {
    right: 58.33333333%;
  }
  .col-lg-pull-6 {
    right: 50%;
  }
  .col-lg-pull-5 {
    right: 41.66666667%;
  }
  .col-lg-pull-4 {
    right: 33.33333333%;
  }
  .col-lg-pull-3 {
    right: 25%;
  }
  .col-lg-pull-2 {
    right: 16.66666667%;
  }
  .col-lg-pull-1 {
    right: 8.33333333%;
  }
  .col-lg-pull-0 {
    right: auto;
  }
  .col-lg-push-12 {
    left: 100%;
  }
  .col-lg-push-11 {
    left: 91.66666667%;
  }
  .col-lg-push-10 {
    left: 83.33333333%;
  }
  .col-lg-push-9 {
    left: 75%;
  }
  .col-lg-push-8 {
    left: 66.66666667%;
  }
  .col-lg-push-7 {
    left: 58.33333333%;
  }
  .col-lg-push-6 {
    left: 50%;
  }
  .col-lg-push-5 {
    left: 41.66666667%;
  }
  .col-lg-push-4 {
    left: 33.33333333%;
  }
  .col-lg-push-3 {
    left: 25%;
  }
  .col-lg-push-2 {
    left: 16.66666667%;
  }
  .col-lg-push-1 {
    left: 8.33333333%;
  }
  .col-lg-push-0 {
    left: auto;
  }
  .col-lg-offset-12 {
    margin-left: 100%;
  }
  .col-lg-offset-11 {
    margin-left: 91.66666667%;
  }
  .col-lg-offset-10 {
    margin-left: 83.33333333%;
  }
  .col-lg-offset-9 {
    margin-left: 75%;
  }
  .col-lg-offset-8 {
    margin-left: 66.66666667%;
  }
  .col-lg-offset-7 {
    margin-left: 58.33333333%;
  }
  .col-lg-offset-6 {
    margin-left: 50%;
  }
  .col-lg-offset-5 {
    margin-left: 41.66666667%;
  }
  .col-lg-offset-4 {
    margin-left: 33.33333333%;
  }
  .col-lg-offset-3 {
    margin-left: 25%;
  }
  .col-lg-offset-2 {
    margin-left: 16.66666667%;
  }
  .col-lg-offset-1 {
    margin-left: 8.33333333%;
  }
  .col-lg-offset-0 {
    margin-left: 0%;
  }
}
table {
  background-color: transparent;
}
caption {
  padding-top: 8px;
  padding-bottom: 8px;
  color: #777777;
  text-align: left;
}
th {
  text-align: left;
}
.table {
  width: 100%;
  max-width: 100%;
  margin-bottom: 18px;
}
.table > thead > tr > th,
.table > tbody > tr > th,
.table > tfoot > tr > th,
.table > thead > tr > td,
.table > tbody > tr > td,
.table > tfoot > tr > td {
  padding: 8px;
  line-height: 1.42857143;
  vertical-align: top;
  border-top: 1px solid #ddd;
}
.table > thead > tr > th {
  vertical-align: bottom;
  border-bottom: 2px solid #ddd;
}
.table > caption + thead > tr:first-child > th,
.table > colgroup + thead > tr:first-child > th,
.table > thead:first-child > tr:first-child > th,
.table > caption + thead > tr:first-child > td,
.table > colgroup + thead > tr:first-child > td,
.table > thead:first-child > tr:first-child > td {
  border-top: 0;
}
.table > tbody + tbody {
  border-top: 2px solid #ddd;
}
.table .table {
  background-color: #fff;
}
.table-condensed > thead > tr > th,
.table-condensed > tbody > tr > th,
.table-condensed > tfoot > tr > th,
.table-condensed > thead > tr > td,
.table-condensed > tbody > tr > td,
.table-condensed > tfoot > tr > td {
  padding: 5px;
}
.table-bordered {
  border: 1px solid #ddd;
}
.table-bordered > thead > tr > th,
.table-bordered > tbody > tr > th,
.table-bordered > tfoot > tr > th,
.table-bordered > thead > tr > td,
.table-bordered > tbody > tr > td,
.table-bordered > tfoot > tr > td {
  border: 1px solid #ddd;
}
.table-bordered > thead > tr > th,
.table-bordered > thead > tr > td {
  border-bottom-width: 2px;
}
.table-striped > tbody > tr:nth-of-type(odd) {
  background-color: #f9f9f9;
}
.table-hover > tbody > tr:hover {
  background-color: #f5f5f5;
}
table col[class*="col-"] {
  position: static;
  float: none;
  display: table-column;
}
table td[class*="col-"],
table th[class*="col-"] {
  position: static;
  float: none;
  display: table-cell;
}
.table > thead > tr > td.active,
.table > tbody > tr > td.active,
.table > tfoot > tr > td.active,
.table > thead > tr > th.active,
.table > tbody > tr > th.active,
.table > tfoot > tr > th.active,
.table > thead > tr.active > td,
.table > tbody > tr.active > td,
.table > tfoot > tr.active > td,
.table > thead > tr.active > th,
.table > tbody > tr.active > th,
.table > tfoot > tr.active > th {
  background-color: #f5f5f5;
}
.table-hover > tbody > tr > td.active:hover,
.table-hover > tbody > tr > th.active:hover,
.table-hover > tbody > tr.active:hover > td,
.table-hover > tbody > tr:hover > .active,
.table-hover > tbody > tr.active:hover > th {
  background-color: #e8e8e8;
}
.table > thead > tr > td.success,
.table > tbody > tr > td.success,
.table > tfoot > tr > td.success,
.table > thead > tr > th.success,
.table > tbody > tr > th.success,
.table > tfoot > tr > th.success,
.table > thead > tr.success > td,
.table > tbody > tr.success > td,
.table > tfoot > tr.success > td,
.table > thead > tr.success > th,
.table > tbody > tr.success > th,
.table > tfoot > tr.success > th {
  background-color: #dff0d8;
}
.table-hover > tbody > tr > td.success:hover,
.table-hover > tbody > tr > th.success:hover,
.table-hover > tbody > tr.success:hover > td,
.table-hover > tbody > tr:hover > .success,
.table-hover > tbody > tr.success:hover > th {
  background-color: #d0e9c6;
}
.table > thead > tr > td.info,
.table > tbody > tr > td.info,
.table > tfoot > tr > td.info,
.table > thead > tr > th.info,
.table > tbody > tr > th.info,
.table > tfoot > tr > th.info,
.table > thead > tr.info > td,
.table > tbody > tr.info > td,
.table > tfoot > tr.info > td,
.table > thead > tr.info > th,
.table > tbody > tr.info > th,
.table > tfoot > tr.info > th {
  background-color: #d9edf7;
}
.table-hover > tbody > tr > td.info:hover,
.table-hover > tbody > tr > th.info:hover,
.table-hover > tbody > tr.info:hover > td,
.table-hover > tbody > tr:hover > .info,
.table-hover > tbody > tr.info:hover > th {
  background-color: #c4e3f3;
}
.table > thead > tr > td.warning,
.table > tbody > tr > td.warning,
.table > tfoot > tr > td.warning,
.table > thead > tr > th.warning,
.table > tbody > tr > th.warning,
.table > tfoot > tr > th.warning,
.table > thead > tr.warning > td,
.table > tbody > tr.warning > td,
.table > tfoot > tr.warning > td,
.table > thead > tr.warning > th,
.table > tbody > tr.warning > th,
.table > tfoot > tr.warning > th {
  background-color: #fcf8e3;
}
.table-hover > tbody > tr > td.warning:hover,
.table-hover > tbody > tr > th.warning:hover,
.table-hover > tbody > tr.warning:hover > td,
.table-hover > tbody > tr:hover > .warning,
.table-hover > tbody > tr.warning:hover > th {
  background-color: #faf2cc;
}
.table > thead > tr > td.danger,
.table > tbody > tr > td.danger,
.table > tfoot > tr > td.danger,
.table > thead > tr > th.danger,
.table > tbody > tr > th.danger,
.table > tfoot > tr > th.danger,
.table > thead > tr.danger > td,
.table > tbody > tr.danger > td,
.table > tfoot > tr.danger > td,
.table > thead > tr.danger > th,
.table > tbody > tr.danger > th,
.table > tfoot > tr.danger > th {
  background-color: #f2dede;
}
.table-hover > tbody > tr > td.danger:hover,
.table-hover > tbody > tr > th.danger:hover,
.table-hover > tbody > tr.danger:hover > td,
.table-hover > tbody > tr:hover > .danger,
.table-hover > tbody > tr.danger:hover > th {
  background-color: #ebcccc;
}
.table-responsive {
  overflow-x: auto;
  min-height: 0.01%;
}
@media screen and (max-width: 767px) {
  .table-responsive {
    width: 100%;
    margin-bottom: 13.5px;
    overflow-y: hidden;
    -ms-overflow-style: -ms-autohiding-scrollbar;
    border: 1px solid #ddd;
  }
  .table-responsive > .table {
    margin-bottom: 0;
  }
  .table-responsive > .table > thead > tr > th,
  .table-responsive > .table > tbody > tr > th,
  .table-responsive > .table > tfoot > tr > th,
  .table-responsive > .table > thead > tr > td,
  .table-responsive > .table > tbody > tr > td,
  .table-responsive > .table > tfoot > tr > td {
    white-space: nowrap;
  }
  .table-responsive > .table-bordered {
    border: 0;
  }
  .table-responsive > .table-bordered > thead > tr > th:first-child,
  .table-responsive > .table-bordered > tbody > tr > th:first-child,
  .table-responsive > .table-bordered > tfoot > tr > th:first-child,
  .table-responsive > .table-bordered > thead > tr > td:first-child,
  .table-responsive > .table-bordered > tbody > tr > td:first-child,
  .table-responsive > .table-bordered > tfoot > tr > td:first-child {
    border-left: 0;
  }
  .table-responsive > .table-bordered > thead > tr > th:last-child,
  .table-responsive > .table-bordered > tbody > tr > th:last-child,
  .table-responsive > .table-bordered > tfoot > tr > th:last-child,
  .table-responsive > .table-bordered > thead > tr > td:last-child,
  .table-responsive > .table-bordered > tbody > tr > td:last-child,
  .table-responsive > .table-bordered > tfoot > tr > td:last-child {
    border-right: 0;
  }
  .table-responsive > .table-bordered > tbody > tr:last-child > th,
  .table-responsive > .table-bordered > tfoot > tr:last-child > th,
  .table-responsive > .table-bordered > tbody > tr:last-child > td,
  .table-responsive > .table-bordered > tfoot > tr:last-child > td {
    border-bottom: 0;
  }
}
fieldset {
  padding: 0;
  margin: 0;
  border: 0;
  min-width: 0;
}
legend {
  display: block;
  width: 100%;
  padding: 0;
  margin-bottom: 18px;
  font-size: 19.5px;
  line-height: inherit;
  color: #333333;
  border: 0;
  border-bottom: 1px solid #e5e5e5;
}
label {
  display: inline-block;
  max-width: 100%;
  margin-bottom: 5px;
  font-weight: bold;
}
input[type="search"] {
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
}
input[type="radio"],
input[type="checkbox"] {
  margin: 4px 0 0;
  margin-top: 1px \9;
  line-height: normal;
}
input[type="file"] {
  display: block;
}
input[type="range"] {
  display: block;
  width: 100%;
}
select[multiple],
select[size] {
  height: auto;
}
input[type="file"]:focus,
input[type="radio"]:focus,
input[type="checkbox"]:focus {
  outline: 5px auto -webkit-focus-ring-color;
  outline-offset: -2px;
}
output {
  display: block;
  padding-top: 7px;
  font-size: 13px;
  line-height: 1.42857143;
  color: #555555;
}
.form-control {
  display: block;
  width: 100%;
  height: 32px;
  padding: 6px 12px;
  font-size: 13px;
  line-height: 1.42857143;
  color: #555555;
  background-color: #fff;
  background-image: none;
  border: 1px solid #ccc;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  -webkit-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  -o-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
}
.form-control:focus {
  border-color: #66afe9;
  outline: 0;
  -webkit-box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
  box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
}
.form-control::-moz-placeholder {
  color: #999;
  opacity: 1;
}
.form-control:-ms-input-placeholder {
  color: #999;
}
.form-control::-webkit-input-placeholder {
  color: #999;
}
.form-control::-ms-expand {
  border: 0;
  background-color: transparent;
}
.form-control[disabled],
.form-control[readonly],
fieldset[disabled] .form-control {
  background-color: #eeeeee;
  opacity: 1;
}
.form-control[disabled],
fieldset[disabled] .form-control {
  cursor: not-allowed;
}
textarea.form-control {
  height: auto;
}
input[type="search"] {
  -webkit-appearance: none;
}
@media screen and (-webkit-min-device-pixel-ratio: 0) {
  input[type="date"].form-control,
  input[type="time"].form-control,
  input[type="datetime-local"].form-control,
  input[type="month"].form-control {
    line-height: 32px;
  }
  input[type="date"].input-sm,
  input[type="time"].input-sm,
  input[type="datetime-local"].input-sm,
  input[type="month"].input-sm,
  .input-group-sm input[type="date"],
  .input-group-sm input[type="time"],
  .input-group-sm input[type="datetime-local"],
  .input-group-sm input[type="month"] {
    line-height: 30px;
  }
  input[type="date"].input-lg,
  input[type="time"].input-lg,
  input[type="datetime-local"].input-lg,
  input[type="month"].input-lg,
  .input-group-lg input[type="date"],
  .input-group-lg input[type="time"],
  .input-group-lg input[type="datetime-local"],
  .input-group-lg input[type="month"] {
    line-height: 45px;
  }
}
.form-group {
  margin-bottom: 15px;
}
.radio,
.checkbox {
  position: relative;
  display: block;
  margin-top: 10px;
  margin-bottom: 10px;
}
.radio label,
.checkbox label {
  min-height: 18px;
  padding-left: 20px;
  margin-bottom: 0;
  font-weight: normal;
  cursor: pointer;
}
.radio input[type="radio"],
.radio-inline input[type="radio"],
.checkbox input[type="checkbox"],
.checkbox-inline input[type="checkbox"] {
  position: absolute;
  margin-left: -20px;
  margin-top: 4px \9;
}
.radio + .radio,
.checkbox + .checkbox {
  margin-top: -5px;
}
.radio-inline,
.checkbox-inline {
  position: relative;
  display: inline-block;
  padding-left: 20px;
  margin-bottom: 0;
  vertical-align: middle;
  font-weight: normal;
  cursor: pointer;
}
.radio-inline + .radio-inline,
.checkbox-inline + .checkbox-inline {
  margin-top: 0;
  margin-left: 10px;
}
input[type="radio"][disabled],
input[type="checkbox"][disabled],
input[type="radio"].disabled,
input[type="checkbox"].disabled,
fieldset[disabled] input[type="radio"],
fieldset[disabled] input[type="checkbox"] {
  cursor: not-allowed;
}
.radio-inline.disabled,
.checkbox-inline.disabled,
fieldset[disabled] .radio-inline,
fieldset[disabled] .checkbox-inline {
  cursor: not-allowed;
}
.radio.disabled label,
.checkbox.disabled label,
fieldset[disabled] .radio label,
fieldset[disabled] .checkbox label {
  cursor: not-allowed;
}
.form-control-static {
  padding-top: 7px;
  padding-bottom: 7px;
  margin-bottom: 0;
  min-height: 31px;
}
.form-control-static.input-lg,
.form-control-static.input-sm {
  padding-left: 0;
  padding-right: 0;
}
.input-sm {
  height: 30px;
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
}
select.input-sm {
  height: 30px;
  line-height: 30px;
}
textarea.input-sm,
select[multiple].input-sm {
  height: auto;
}
.form-group-sm .form-control {
  height: 30px;
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
}
.form-group-sm select.form-control {
  height: 30px;
  line-height: 30px;
}
.form-group-sm textarea.form-control,
.form-group-sm select[multiple].form-control {
  height: auto;
}
.form-group-sm .form-control-static {
  height: 30px;
  min-height: 30px;
  padding: 6px 10px;
  font-size: 12px;
  line-height: 1.5;
}
.input-lg {
  height: 45px;
  padding: 10px 16px;
  font-size: 17px;
  line-height: 1.3333333;
  border-radius: 3px;
}
select.input-lg {
  height: 45px;
  line-height: 45px;
}
textarea.input-lg,
select[multiple].input-lg {
  height: auto;
}
.form-group-lg .form-control {
  height: 45px;
  padding: 10px 16px;
  font-size: 17px;
  line-height: 1.3333333;
  border-radius: 3px;
}
.form-group-lg select.form-control {
  height: 45px;
  line-height: 45px;
}
.form-group-lg textarea.form-control,
.form-group-lg select[multiple].form-control {
  height: auto;
}
.form-group-lg .form-control-static {
  height: 45px;
  min-height: 35px;
  padding: 11px 16px;
  font-size: 17px;
  line-height: 1.3333333;
}
.has-feedback {
  position: relative;
}
.has-feedback .form-control {
  padding-right: 40px;
}
.form-control-feedback {
  position: absolute;
  top: 0;
  right: 0;
  z-index: 2;
  display: block;
  width: 32px;
  height: 32px;
  line-height: 32px;
  text-align: center;
  pointer-events: none;
}
.input-lg + .form-control-feedback,
.input-group-lg + .form-control-feedback,
.form-group-lg .form-control + .form-control-feedback {
  width: 45px;
  height: 45px;
  line-height: 45px;
}
.input-sm + .form-control-feedback,
.input-group-sm + .form-control-feedback,
.form-group-sm .form-control + .form-control-feedback {
  width: 30px;
  height: 30px;
  line-height: 30px;
}
.has-success .help-block,
.has-success .control-label,
.has-success .radio,
.has-success .checkbox,
.has-success .radio-inline,
.has-success .checkbox-inline,
.has-success.radio label,
.has-success.checkbox label,
.has-success.radio-inline label,
.has-success.checkbox-inline label {
  color: #3c763d;
}
.has-success .form-control {
  border-color: #3c763d;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
}
.has-success .form-control:focus {
  border-color: #2b542c;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #67b168;
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #67b168;
}
.has-success .input-group-addon {
  color: #3c763d;
  border-color: #3c763d;
  background-color: #dff0d8;
}
.has-success .form-control-feedback {
  color: #3c763d;
}
.has-warning .help-block,
.has-warning .control-label,
.has-warning .radio,
.has-warning .checkbox,
.has-warning .radio-inline,
.has-warning .checkbox-inline,
.has-warning.radio label,
.has-warning.checkbox label,
.has-warning.radio-inline label,
.has-warning.checkbox-inline label {
  color: #8a6d3b;
}
.has-warning .form-control {
  border-color: #8a6d3b;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
}
.has-warning .form-control:focus {
  border-color: #66512c;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #c0a16b;
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #c0a16b;
}
.has-warning .input-group-addon {
  color: #8a6d3b;
  border-color: #8a6d3b;
  background-color: #fcf8e3;
}
.has-warning .form-control-feedback {
  color: #8a6d3b;
}
.has-error .help-block,
.has-error .control-label,
.has-error .radio,
.has-error .checkbox,
.has-error .radio-inline,
.has-error .checkbox-inline,
.has-error.radio label,
.has-error.checkbox label,
.has-error.radio-inline label,
.has-error.checkbox-inline label {
  color: #a94442;
}
.has-error .form-control {
  border-color: #a94442;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
}
.has-error .form-control:focus {
  border-color: #843534;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #ce8483;
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 6px #ce8483;
}
.has-error .input-group-addon {
  color: #a94442;
  border-color: #a94442;
  background-color: #f2dede;
}
.has-error .form-control-feedback {
  color: #a94442;
}
.has-feedback label ~ .form-control-feedback {
  top: 23px;
}
.has-feedback label.sr-only ~ .form-control-feedback {
  top: 0;
}
.help-block {
  display: block;
  margin-top: 5px;
  margin-bottom: 10px;
  color: #404040;
}
@media (min-width: 768px) {
  .form-inline .form-group {
    display: inline-block;
    margin-bottom: 0;
    vertical-align: middle;
  }
  .form-inline .form-control {
    display: inline-block;
    width: auto;
    vertical-align: middle;
  }
  .form-inline .form-control-static {
    display: inline-block;
  }
  .form-inline .input-group {
    display: inline-table;
    vertical-align: middle;
  }
  .form-inline .input-group .input-group-addon,
  .form-inline .input-group .input-group-btn,
  .form-inline .input-group .form-control {
    width: auto;
  }
  .form-inline .input-group > .form-control {
    width: 100%;
  }
  .form-inline .control-label {
    margin-bottom: 0;
    vertical-align: middle;
  }
  .form-inline .radio,
  .form-inline .checkbox {
    display: inline-block;
    margin-top: 0;
    margin-bottom: 0;
    vertical-align: middle;
  }
  .form-inline .radio label,
  .form-inline .checkbox label {
    padding-left: 0;
  }
  .form-inline .radio input[type="radio"],
  .form-inline .checkbox input[type="checkbox"] {
    position: relative;
    margin-left: 0;
  }
  .form-inline .has-feedback .form-control-feedback {
    top: 0;
  }
}
.form-horizontal .radio,
.form-horizontal .checkbox,
.form-horizontal .radio-inline,
.form-horizontal .checkbox-inline {
  margin-top: 0;
  margin-bottom: 0;
  padding-top: 7px;
}
.form-horizontal .radio,
.form-horizontal .checkbox {
  min-height: 25px;
}
.form-horizontal .form-group {
  margin-left: 0px;
  margin-right: 0px;
}
@media (min-width: 768px) {
  .form-horizontal .control-label {
    text-align: right;
    margin-bottom: 0;
    padding-top: 7px;
  }
}
.form-horizontal .has-feedback .form-control-feedback {
  right: 0px;
}
@media (min-width: 768px) {
  .form-horizontal .form-group-lg .control-label {
    padding-top: 11px;
    font-size: 17px;
  }
}
@media (min-width: 768px) {
  .form-horizontal .form-group-sm .control-label {
    padding-top: 6px;
    font-size: 12px;
  }
}
.btn {
  display: inline-block;
  margin-bottom: 0;
  font-weight: normal;
  text-align: center;
  vertical-align: middle;
  touch-action: manipulation;
  cursor: pointer;
  background-image: none;
  border: 1px solid transparent;
  white-space: nowrap;
  padding: 6px 12px;
  font-size: 13px;
  line-height: 1.42857143;
  border-radius: 2px;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}
.btn:focus,
.btn:active:focus,
.btn.active:focus,
.btn.focus,
.btn:active.focus,
.btn.active.focus {
  outline: 5px auto -webkit-focus-ring-color;
  outline-offset: -2px;
}
.btn:hover,
.btn:focus,
.btn.focus {
  color: #333;
  text-decoration: none;
}
.btn:active,
.btn.active {
  outline: 0;
  background-image: none;
  -webkit-box-shadow: inset 0 3px 5px rgba(0, 0, 0, 0.125);
  box-shadow: inset 0 3px 5px rgba(0, 0, 0, 0.125);
}
.btn.disabled,
.btn[disabled],
fieldset[disabled] .btn {
  cursor: not-allowed;
  opacity: 0.65;
  filter: alpha(opacity=65);
  -webkit-box-shadow: none;
  box-shadow: none;
}
a.btn.disabled,
fieldset[disabled] a.btn {
  pointer-events: none;
}
.btn-default {
  color: #333;
  background-color: #fff;
  border-color: #ccc;
}
.btn-default:focus,
.btn-default.focus {
  color: #333;
  background-color: #e6e6e6;
  border-color: #8c8c8c;
}
.btn-default:hover {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
.btn-default:active,
.btn-default.active,
.open > .dropdown-toggle.btn-default {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
.btn-default:active:hover,
.btn-default.active:hover,
.open > .dropdown-toggle.btn-default:hover,
.btn-default:active:focus,
.btn-default.active:focus,
.open > .dropdown-toggle.btn-default:focus,
.btn-default:active.focus,
.btn-default.active.focus,
.open > .dropdown-toggle.btn-default.focus {
  color: #333;
  background-color: #d4d4d4;
  border-color: #8c8c8c;
}
.btn-default:active,
.btn-default.active,
.open > .dropdown-toggle.btn-default {
  background-image: none;
}
.btn-default.disabled:hover,
.btn-default[disabled]:hover,
fieldset[disabled] .btn-default:hover,
.btn-default.disabled:focus,
.btn-default[disabled]:focus,
fieldset[disabled] .btn-default:focus,
.btn-default.disabled.focus,
.btn-default[disabled].focus,
fieldset[disabled] .btn-default.focus {
  background-color: #fff;
  border-color: #ccc;
}
.btn-default .badge {
  color: #fff;
  background-color: #333;
}
.btn-primary {
  color: #fff;
  background-color: #337ab7;
  border-color: #2e6da4;
}
.btn-primary:focus,
.btn-primary.focus {
  color: #fff;
  background-color: #286090;
  border-color: #122b40;
}
.btn-primary:hover {
  color: #fff;
  background-color: #286090;
  border-color: #204d74;
}
.btn-primary:active,
.btn-primary.active,
.open > .dropdown-toggle.btn-primary {
  color: #fff;
  background-color: #286090;
  border-color: #204d74;
}
.btn-primary:active:hover,
.btn-primary.active:hover,
.open > .dropdown-toggle.btn-primary:hover,
.btn-primary:active:focus,
.btn-primary.active:focus,
.open > .dropdown-toggle.btn-primary:focus,
.btn-primary:active.focus,
.btn-primary.active.focus,
.open > .dropdown-toggle.btn-primary.focus {
  color: #fff;
  background-color: #204d74;
  border-color: #122b40;
}
.btn-primary:active,
.btn-primary.active,
.open > .dropdown-toggle.btn-primary {
  background-image: none;
}
.btn-primary.disabled:hover,
.btn-primary[disabled]:hover,
fieldset[disabled] .btn-primary:hover,
.btn-primary.disabled:focus,
.btn-primary[disabled]:focus,
fieldset[disabled] .btn-primary:focus,
.btn-primary.disabled.focus,
.btn-primary[disabled].focus,
fieldset[disabled] .btn-primary.focus {
  background-color: #337ab7;
  border-color: #2e6da4;
}
.btn-primary .badge {
  color: #337ab7;
  background-color: #fff;
}
.btn-success {
  color: #fff;
  background-color: #5cb85c;
  border-color: #4cae4c;
}
.btn-success:focus,
.btn-success.focus {
  color: #fff;
  background-color: #449d44;
  border-color: #255625;
}
.btn-success:hover {
  color: #fff;
  background-color: #449d44;
  border-color: #398439;
}
.btn-success:active,
.btn-success.active,
.open > .dropdown-toggle.btn-success {
  color: #fff;
  background-color: #449d44;
  border-color: #398439;
}
.btn-success:active:hover,
.btn-success.active:hover,
.open > .dropdown-toggle.btn-success:hover,
.btn-success:active:focus,
.btn-success.active:focus,
.open > .dropdown-toggle.btn-success:focus,
.btn-success:active.focus,
.btn-success.active.focus,
.open > .dropdown-toggle.btn-success.focus {
  color: #fff;
  background-color: #398439;
  border-color: #255625;
}
.btn-success:active,
.btn-success.active,
.open > .dropdown-toggle.btn-success {
  background-image: none;
}
.btn-success.disabled:hover,
.btn-success[disabled]:hover,
fieldset[disabled] .btn-success:hover,
.btn-success.disabled:focus,
.btn-success[disabled]:focus,
fieldset[disabled] .btn-success:focus,
.btn-success.disabled.focus,
.btn-success[disabled].focus,
fieldset[disabled] .btn-success.focus {
  background-color: #5cb85c;
  border-color: #4cae4c;
}
.btn-success .badge {
  color: #5cb85c;
  background-color: #fff;
}
.btn-info {
  color: #fff;
  background-color: #5bc0de;
  border-color: #46b8da;
}
.btn-info:focus,
.btn-info.focus {
  color: #fff;
  background-color: #31b0d5;
  border-color: #1b6d85;
}
.btn-info:hover {
  color: #fff;
  background-color: #31b0d5;
  border-color: #269abc;
}
.btn-info:active,
.btn-info.active,
.open > .dropdown-toggle.btn-info {
  color: #fff;
  background-color: #31b0d5;
  border-color: #269abc;
}
.btn-info:active:hover,
.btn-info.active:hover,
.open > .dropdown-toggle.btn-info:hover,
.btn-info:active:focus,
.btn-info.active:focus,
.open > .dropdown-toggle.btn-info:focus,
.btn-info:active.focus,
.btn-info.active.focus,
.open > .dropdown-toggle.btn-info.focus {
  color: #fff;
  background-color: #269abc;
  border-color: #1b6d85;
}
.btn-info:active,
.btn-info.active,
.open > .dropdown-toggle.btn-info {
  background-image: none;
}
.btn-info.disabled:hover,
.btn-info[disabled]:hover,
fieldset[disabled] .btn-info:hover,
.btn-info.disabled:focus,
.btn-info[disabled]:focus,
fieldset[disabled] .btn-info:focus,
.btn-info.disabled.focus,
.btn-info[disabled].focus,
fieldset[disabled] .btn-info.focus {
  background-color: #5bc0de;
  border-color: #46b8da;
}
.btn-info .badge {
  color: #5bc0de;
  background-color: #fff;
}
.btn-warning {
  color: #fff;
  background-color: #f0ad4e;
  border-color: #eea236;
}
.btn-warning:focus,
.btn-warning.focus {
  color: #fff;
  background-color: #ec971f;
  border-color: #985f0d;
}
.btn-warning:hover {
  color: #fff;
  background-color: #ec971f;
  border-color: #d58512;
}
.btn-warning:active,
.btn-warning.active,
.open > .dropdown-toggle.btn-warning {
  color: #fff;
  background-color: #ec971f;
  border-color: #d58512;
}
.btn-warning:active:hover,
.btn-warning.active:hover,
.open > .dropdown-toggle.btn-warning:hover,
.btn-warning:active:focus,
.btn-warning.active:focus,
.open > .dropdown-toggle.btn-warning:focus,
.btn-warning:active.focus,
.btn-warning.active.focus,
.open > .dropdown-toggle.btn-warning.focus {
  color: #fff;
  background-color: #d58512;
  border-color: #985f0d;
}
.btn-warning:active,
.btn-warning.active,
.open > .dropdown-toggle.btn-warning {
  background-image: none;
}
.btn-warning.disabled:hover,
.btn-warning[disabled]:hover,
fieldset[disabled] .btn-warning:hover,
.btn-warning.disabled:focus,
.btn-warning[disabled]:focus,
fieldset[disabled] .btn-warning:focus,
.btn-warning.disabled.focus,
.btn-warning[disabled].focus,
fieldset[disabled] .btn-warning.focus {
  background-color: #f0ad4e;
  border-color: #eea236;
}
.btn-warning .badge {
  color: #f0ad4e;
  background-color: #fff;
}
.btn-danger {
  color: #fff;
  background-color: #d9534f;
  border-color: #d43f3a;
}
.btn-danger:focus,
.btn-danger.focus {
  color: #fff;
  background-color: #c9302c;
  border-color: #761c19;
}
.btn-danger:hover {
  color: #fff;
  background-color: #c9302c;
  border-color: #ac2925;
}
.btn-danger:active,
.btn-danger.active,
.open > .dropdown-toggle.btn-danger {
  color: #fff;
  background-color: #c9302c;
  border-color: #ac2925;
}
.btn-danger:active:hover,
.btn-danger.active:hover,
.open > .dropdown-toggle.btn-danger:hover,
.btn-danger:active:focus,
.btn-danger.active:focus,
.open > .dropdown-toggle.btn-danger:focus,
.btn-danger:active.focus,
.btn-danger.active.focus,
.open > .dropdown-toggle.btn-danger.focus {
  color: #fff;
  background-color: #ac2925;
  border-color: #761c19;
}
.btn-danger:active,
.btn-danger.active,
.open > .dropdown-toggle.btn-danger {
  background-image: none;
}
.btn-danger.disabled:hover,
.btn-danger[disabled]:hover,
fieldset[disabled] .btn-danger:hover,
.btn-danger.disabled:focus,
.btn-danger[disabled]:focus,
fieldset[disabled] .btn-danger:focus,
.btn-danger.disabled.focus,
.btn-danger[disabled].focus,
fieldset[disabled] .btn-danger.focus {
  background-color: #d9534f;
  border-color: #d43f3a;
}
.btn-danger .badge {
  color: #d9534f;
  background-color: #fff;
}
.btn-link {
  color: #337ab7;
  font-weight: normal;
  border-radius: 0;
}
.btn-link,
.btn-link:active,
.btn-link.active,
.btn-link[disabled],
fieldset[disabled] .btn-link {
  background-color: transparent;
  -webkit-box-shadow: none;
  box-shadow: none;
}
.btn-link,
.btn-link:hover,
.btn-link:focus,
.btn-link:active {
  border-color: transparent;
}
.btn-link:hover,
.btn-link:focus {
  color: #23527c;
  text-decoration: underline;
  background-color: transparent;
}
.btn-link[disabled]:hover,
fieldset[disabled] .btn-link:hover,
.btn-link[disabled]:focus,
fieldset[disabled] .btn-link:focus {
  color: #777777;
  text-decoration: none;
}
.btn-lg,
.btn-group-lg > .btn {
  padding: 10px 16px;
  font-size: 17px;
  line-height: 1.3333333;
  border-radius: 3px;
}
.btn-sm,
.btn-group-sm > .btn {
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
}
.btn-xs,
.btn-group-xs > .btn {
  padding: 1px 5px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
}
.btn-block {
  display: block;
  width: 100%;
}
.btn-block + .btn-block {
  margin-top: 5px;
}
input[type="submit"].btn-block,
input[type="reset"].btn-block,
input[type="button"].btn-block {
  width: 100%;
}
.fade {
  opacity: 0;
  -webkit-transition: opacity 0.15s linear;
  -o-transition: opacity 0.15s linear;
  transition: opacity 0.15s linear;
}
.fade.in {
  opacity: 1;
}
.collapse {
  display: none;
}
.collapse.in {
  display: block;
}
tr.collapse.in {
  display: table-row;
}
tbody.collapse.in {
  display: table-row-group;
}
.collapsing {
  position: relative;
  height: 0;
  overflow: hidden;
  -webkit-transition-property: height, visibility;
  transition-property: height, visibility;
  -webkit-transition-duration: 0.35s;
  transition-duration: 0.35s;
  -webkit-transition-timing-function: ease;
  transition-timing-function: ease;
}
.caret {
  display: inline-block;
  width: 0;
  height: 0;
  margin-left: 2px;
  vertical-align: middle;
  border-top: 4px dashed;
  border-top: 4px solid \9;
  border-right: 4px solid transparent;
  border-left: 4px solid transparent;
}
.dropup,
.dropdown {
  position: relative;
}
.dropdown-toggle:focus {
  outline: 0;
}
.dropdown-menu {
  position: absolute;
  top: 100%;
  left: 0;
  z-index: 1000;
  display: none;
  float: left;
  min-width: 160px;
  padding: 5px 0;
  margin: 2px 0 0;
  list-style: none;
  font-size: 13px;
  text-align: left;
  background-color: #fff;
  border: 1px solid #ccc;
  border: 1px solid rgba(0, 0, 0, 0.15);
  border-radius: 2px;
  -webkit-box-shadow: 0 6px 12px rgba(0, 0, 0, 0.175);
  box-shadow: 0 6px 12px rgba(0, 0, 0, 0.175);
  background-clip: padding-box;
}
.dropdown-menu.pull-right {
  right: 0;
  left: auto;
}
.dropdown-menu .divider {
  height: 1px;
  margin: 8px 0;
  overflow: hidden;
  background-color: #e5e5e5;
}
.dropdown-menu > li > a {
  display: block;
  padding: 3px 20px;
  clear: both;
  font-weight: normal;
  line-height: 1.42857143;
  color: #333333;
  white-space: nowrap;
}
.dropdown-menu > li > a:hover,
.dropdown-menu > li > a:focus {
  text-decoration: none;
  color: #262626;
  background-color: #f5f5f5;
}
.dropdown-menu > .active > a,
.dropdown-menu > .active > a:hover,
.dropdown-menu > .active > a:focus {
  color: #fff;
  text-decoration: none;
  outline: 0;
  background-color: #337ab7;
}
.dropdown-menu > .disabled > a,
.dropdown-menu > .disabled > a:hover,
.dropdown-menu > .disabled > a:focus {
  color: #777777;
}
.dropdown-menu > .disabled > a:hover,
.dropdown-menu > .disabled > a:focus {
  text-decoration: none;
  background-color: transparent;
  background-image: none;
  filter: progid:DXImageTransform.Microsoft.gradient(enabled = false);
  cursor: not-allowed;
}
.open > .dropdown-menu {
  display: block;
}
.open > a {
  outline: 0;
}
.dropdown-menu-right {
  left: auto;
  right: 0;
}
.dropdown-menu-left {
  left: 0;
  right: auto;
}
.dropdown-header {
  display: block;
  padding: 3px 20px;
  font-size: 12px;
  line-height: 1.42857143;
  color: #777777;
  white-space: nowrap;
}
.dropdown-backdrop {
  position: fixed;
  left: 0;
  right: 0;
  bottom: 0;
  top: 0;
  z-index: 990;
}
.pull-right > .dropdown-menu {
  right: 0;
  left: auto;
}
.dropup .caret,
.navbar-fixed-bottom .dropdown .caret {
  border-top: 0;
  border-bottom: 4px dashed;
  border-bottom: 4px solid \9;
  content: "";
}
.dropup .dropdown-menu,
.navbar-fixed-bottom .dropdown .dropdown-menu {
  top: auto;
  bottom: 100%;
  margin-bottom: 2px;
}
@media (min-width: 541px) {
  .navbar-right .dropdown-menu {
    left: auto;
    right: 0;
  }
  .navbar-right .dropdown-menu-left {
    left: 0;
    right: auto;
  }
}
.btn-group,
.btn-group-vertical {
  position: relative;
  display: inline-block;
  vertical-align: middle;
}
.btn-group > .btn,
.btn-group-vertical > .btn {
  position: relative;
  float: left;
}
.btn-group > .btn:hover,
.btn-group-vertical > .btn:hover,
.btn-group > .btn:focus,
.btn-group-vertical > .btn:focus,
.btn-group > .btn:active,
.btn-group-vertical > .btn:active,
.btn-group > .btn.active,
.btn-group-vertical > .btn.active {
  z-index: 2;
}
.btn-group .btn + .btn,
.btn-group .btn + .btn-group,
.btn-group .btn-group + .btn,
.btn-group .btn-group + .btn-group {
  margin-left: -1px;
}
.btn-toolbar {
  margin-left: -5px;
}
.btn-toolbar .btn,
.btn-toolbar .btn-group,
.btn-toolbar .input-group {
  float: left;
}
.btn-toolbar > .btn,
.btn-toolbar > .btn-group,
.btn-toolbar > .input-group {
  margin-left: 5px;
}
.btn-group > .btn:not(:first-child):not(:last-child):not(.dropdown-toggle) {
  border-radius: 0;
}
.btn-group > .btn:first-child {
  margin-left: 0;
}
.btn-group > .btn:first-child:not(:last-child):not(.dropdown-toggle) {
  border-bottom-right-radius: 0;
  border-top-right-radius: 0;
}
.btn-group > .btn:last-child:not(:first-child),
.btn-group > .dropdown-toggle:not(:first-child) {
  border-bottom-left-radius: 0;
  border-top-left-radius: 0;
}
.btn-group > .btn-group {
  float: left;
}
.btn-group > .btn-group:not(:first-child):not(:last-child) > .btn {
  border-radius: 0;
}
.btn-group > .btn-group:first-child:not(:last-child) > .btn:last-child,
.btn-group > .btn-group:first-child:not(:last-child) > .dropdown-toggle {
  border-bottom-right-radius: 0;
  border-top-right-radius: 0;
}
.btn-group > .btn-group:last-child:not(:first-child) > .btn:first-child {
  border-bottom-left-radius: 0;
  border-top-left-radius: 0;
}
.btn-group .dropdown-toggle:active,
.btn-group.open .dropdown-toggle {
  outline: 0;
}
.btn-group > .btn + .dropdown-toggle {
  padding-left: 8px;
  padding-right: 8px;
}
.btn-group > .btn-lg + .dropdown-toggle {
  padding-left: 12px;
  padding-right: 12px;
}
.btn-group.open .dropdown-toggle {
  -webkit-box-shadow: inset 0 3px 5px rgba(0, 0, 0, 0.125);
  box-shadow: inset 0 3px 5px rgba(0, 0, 0, 0.125);
}
.btn-group.open .dropdown-toggle.btn-link {
  -webkit-box-shadow: none;
  box-shadow: none;
}
.btn .caret {
  margin-left: 0;
}
.btn-lg .caret {
  border-width: 5px 5px 0;
  border-bottom-width: 0;
}
.dropup .btn-lg .caret {
  border-width: 0 5px 5px;
}
.btn-group-vertical > .btn,
.btn-group-vertical > .btn-group,
.btn-group-vertical > .btn-group > .btn {
  display: block;
  float: none;
  width: 100%;
  max-width: 100%;
}
.btn-group-vertical > .btn-group > .btn {
  float: none;
}
.btn-group-vertical > .btn + .btn,
.btn-group-vertical > .btn + .btn-group,
.btn-group-vertical > .btn-group + .btn,
.btn-group-vertical > .btn-group + .btn-group {
  margin-top: -1px;
  margin-left: 0;
}
.btn-group-vertical > .btn:not(:first-child):not(:last-child) {
  border-radius: 0;
}
.btn-group-vertical > .btn:first-child:not(:last-child) {
  border-top-right-radius: 2px;
  border-top-left-radius: 2px;
  border-bottom-right-radius: 0;
  border-bottom-left-radius: 0;
}
.btn-group-vertical > .btn:last-child:not(:first-child) {
  border-top-right-radius: 0;
  border-top-left-radius: 0;
  border-bottom-right-radius: 2px;
  border-bottom-left-radius: 2px;
}
.btn-group-vertical > .btn-group:not(:first-child):not(:last-child) > .btn {
  border-radius: 0;
}
.btn-group-vertical > .btn-group:first-child:not(:last-child) > .btn:last-child,
.btn-group-vertical > .btn-group:first-child:not(:last-child) > .dropdown-toggle {
  border-bottom-right-radius: 0;
  border-bottom-left-radius: 0;
}
.btn-group-vertical > .btn-group:last-child:not(:first-child) > .btn:first-child {
  border-top-right-radius: 0;
  border-top-left-radius: 0;
}
.btn-group-justified {
  display: table;
  width: 100%;
  table-layout: fixed;
  border-collapse: separate;
}
.btn-group-justified > .btn,
.btn-group-justified > .btn-group {
  float: none;
  display: table-cell;
  width: 1%;
}
.btn-group-justified > .btn-group .btn {
  width: 100%;
}
.btn-group-justified > .btn-group .dropdown-menu {
  left: auto;
}
[data-toggle="buttons"] > .btn input[type="radio"],
[data-toggle="buttons"] > .btn-group > .btn input[type="radio"],
[data-toggle="buttons"] > .btn input[type="checkbox"],
[data-toggle="buttons"] > .btn-group > .btn input[type="checkbox"] {
  position: absolute;
  clip: rect(0, 0, 0, 0);
  pointer-events: none;
}
.input-group {
  position: relative;
  display: table;
  border-collapse: separate;
}
.input-group[class*="col-"] {
  float: none;
  padding-left: 0;
  padding-right: 0;
}
.input-group .form-control {
  position: relative;
  z-index: 2;
  float: left;
  width: 100%;
  margin-bottom: 0;
}
.input-group .form-control:focus {
  z-index: 3;
}
.input-group-lg > .form-control,
.input-group-lg > .input-group-addon,
.input-group-lg > .input-group-btn > .btn {
  height: 45px;
  padding: 10px 16px;
  font-size: 17px;
  line-height: 1.3333333;
  border-radius: 3px;
}
select.input-group-lg > .form-control,
select.input-group-lg > .input-group-addon,
select.input-group-lg > .input-group-btn > .btn {
  height: 45px;
  line-height: 45px;
}
textarea.input-group-lg > .form-control,
textarea.input-group-lg > .input-group-addon,
textarea.input-group-lg > .input-group-btn > .btn,
select[multiple].input-group-lg > .form-control,
select[multiple].input-group-lg > .input-group-addon,
select[multiple].input-group-lg > .input-group-btn > .btn {
  height: auto;
}
.input-group-sm > .form-control,
.input-group-sm > .input-group-addon,
.input-group-sm > .input-group-btn > .btn {
  height: 30px;
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
}
select.input-group-sm > .form-control,
select.input-group-sm > .input-group-addon,
select.input-group-sm > .input-group-btn > .btn {
  height: 30px;
  line-height: 30px;
}
textarea.input-group-sm > .form-control,
textarea.input-group-sm > .input-group-addon,
textarea.input-group-sm > .input-group-btn > .btn,
select[multiple].input-group-sm > .form-control,
select[multiple].input-group-sm > .input-group-addon,
select[multiple].input-group-sm > .input-group-btn > .btn {
  height: auto;
}
.input-group-addon,
.input-group-btn,
.input-group .form-control {
  display: table-cell;
}
.input-group-addon:not(:first-child):not(:last-child),
.input-group-btn:not(:first-child):not(:last-child),
.input-group .form-control:not(:first-child):not(:last-child) {
  border-radius: 0;
}
.input-group-addon,
.input-group-btn {
  width: 1%;
  white-space: nowrap;
  vertical-align: middle;
}
.input-group-addon {
  padding: 6px 12px;
  font-size: 13px;
  font-weight: normal;
  line-height: 1;
  color: #555555;
  text-align: center;
  background-color: #eeeeee;
  border: 1px solid #ccc;
  border-radius: 2px;
}
.input-group-addon.input-sm {
  padding: 5px 10px;
  font-size: 12px;
  border-radius: 1px;
}
.input-group-addon.input-lg {
  padding: 10px 16px;
  font-size: 17px;
  border-radius: 3px;
}
.input-group-addon input[type="radio"],
.input-group-addon input[type="checkbox"] {
  margin-top: 0;
}
.input-group .form-control:first-child,
.input-group-addon:first-child,
.input-group-btn:first-child > .btn,
.input-group-btn:first-child > .btn-group > .btn,
.input-group-btn:first-child > .dropdown-toggle,
.input-group-btn:last-child > .btn:not(:last-child):not(.dropdown-toggle),
.input-group-btn:last-child > .btn-group:not(:last-child) > .btn {
  border-bottom-right-radius: 0;
  border-top-right-radius: 0;
}
.input-group-addon:first-child {
  border-right: 0;
}
.input-group .form-control:last-child,
.input-group-addon:last-child,
.input-group-btn:last-child > .btn,
.input-group-btn:last-child > .btn-group > .btn,
.input-group-btn:last-child > .dropdown-toggle,
.input-group-btn:first-child > .btn:not(:first-child),
.input-group-btn:first-child > .btn-group:not(:first-child) > .btn {
  border-bottom-left-radius: 0;
  border-top-left-radius: 0;
}
.input-group-addon:last-child {
  border-left: 0;
}
.input-group-btn {
  position: relative;
  font-size: 0;
  white-space: nowrap;
}
.input-group-btn > .btn {
  position: relative;
}
.input-group-btn > .btn + .btn {
  margin-left: -1px;
}
.input-group-btn > .btn:hover,
.input-group-btn > .btn:focus,
.input-group-btn > .btn:active {
  z-index: 2;
}
.input-group-btn:first-child > .btn,
.input-group-btn:first-child > .btn-group {
  margin-right: -1px;
}
.input-group-btn:last-child > .btn,
.input-group-btn:last-child > .btn-group {
  z-index: 2;
  margin-left: -1px;
}
.nav {
  margin-bottom: 0;
  padding-left: 0;
  list-style: none;
}
.nav > li {
  position: relative;
  display: block;
}
.nav > li > a {
  position: relative;
  display: block;
  padding: 10px 15px;
}
.nav > li > a:hover,
.nav > li > a:focus {
  text-decoration: none;
  background-color: #eeeeee;
}
.nav > li.disabled > a {
  color: #777777;
}
.nav > li.disabled > a:hover,
.nav > li.disabled > a:focus {
  color: #777777;
  text-decoration: none;
  background-color: transparent;
  cursor: not-allowed;
}
.nav .open > a,
.nav .open > a:hover,
.nav .open > a:focus {
  background-color: #eeeeee;
  border-color: #337ab7;
}
.nav .nav-divider {
  height: 1px;
  margin: 8px 0;
  overflow: hidden;
  background-color: #e5e5e5;
}
.nav > li > a > img {
  max-width: none;
}
.nav-tabs {
  border-bottom: 1px solid #ddd;
}
.nav-tabs > li {
  float: left;
  margin-bottom: -1px;
}
.nav-tabs > li > a {
  margin-right: 2px;
  line-height: 1.42857143;
  border: 1px solid transparent;
  border-radius: 2px 2px 0 0;
}
.nav-tabs > li > a:hover {
  border-color: #eeeeee #eeeeee #ddd;
}
.nav-tabs > li.active > a,
.nav-tabs > li.active > a:hover,
.nav-tabs > li.active > a:focus {
  color: #555555;
  background-color: #fff;
  border: 1px solid #ddd;
  border-bottom-color: transparent;
  cursor: default;
}
.nav-tabs.nav-justified {
  width: 100%;
  border-bottom: 0;
}
.nav-tabs.nav-justified > li {
  float: none;
}
.nav-tabs.nav-justified > li > a {
  text-align: center;
  margin-bottom: 5px;
}
.nav-tabs.nav-justified > .dropdown .dropdown-menu {
  top: auto;
  left: auto;
}
@media (min-width: 768px) {
  .nav-tabs.nav-justified > li {
    display: table-cell;
    width: 1%;
  }
  .nav-tabs.nav-justified > li > a {
    margin-bottom: 0;
  }
}
.nav-tabs.nav-justified > li > a {
  margin-right: 0;
  border-radius: 2px;
}
.nav-tabs.nav-justified > .active > a,
.nav-tabs.nav-justified > .active > a:hover,
.nav-tabs.nav-justified > .active > a:focus {
  border: 1px solid #ddd;
}
@media (min-width: 768px) {
  .nav-tabs.nav-justified > li > a {
    border-bottom: 1px solid #ddd;
    border-radius: 2px 2px 0 0;
  }
  .nav-tabs.nav-justified > .active > a,
  .nav-tabs.nav-justified > .active > a:hover,
  .nav-tabs.nav-justified > .active > a:focus {
    border-bottom-color: #fff;
  }
}
.nav-pills > li {
  float: left;
}
.nav-pills > li > a {
  border-radius: 2px;
}
.nav-pills > li + li {
  margin-left: 2px;
}
.nav-pills > li.active > a,
.nav-pills > li.active > a:hover,
.nav-pills > li.active > a:focus {
  color: #fff;
  background-color: #337ab7;
}
.nav-stacked > li {
  float: none;
}
.nav-stacked > li + li {
  margin-top: 2px;
  margin-left: 0;
}
.nav-justified {
  width: 100%;
}
.nav-justified > li {
  float: none;
}
.nav-justified > li > a {
  text-align: center;
  margin-bottom: 5px;
}
.nav-justified > .dropdown .dropdown-menu {
  top: auto;
  left: auto;
}
@media (min-width: 768px) {
  .nav-justified > li {
    display: table-cell;
    width: 1%;
  }
  .nav-justified > li > a {
    margin-bottom: 0;
  }
}
.nav-tabs-justified {
  border-bottom: 0;
}
.nav-tabs-justified > li > a {
  margin-right: 0;
  border-radius: 2px;
}
.nav-tabs-justified > .active > a,
.nav-tabs-justified > .active > a:hover,
.nav-tabs-justified > .active > a:focus {
  border: 1px solid #ddd;
}
@media (min-width: 768px) {
  .nav-tabs-justified > li > a {
    border-bottom: 1px solid #ddd;
    border-radius: 2px 2px 0 0;
  }
  .nav-tabs-justified > .active > a,
  .nav-tabs-justified > .active > a:hover,
  .nav-tabs-justified > .active > a:focus {
    border-bottom-color: #fff;
  }
}
.tab-content > .tab-pane {
  display: none;
}
.tab-content > .active {
  display: block;
}
.nav-tabs .dropdown-menu {
  margin-top: -1px;
  border-top-right-radius: 0;
  border-top-left-radius: 0;
}
.navbar {
  position: relative;
  min-height: 30px;
  margin-bottom: 18px;
  border: 1px solid transparent;
}
@media (min-width: 541px) {
  .navbar {
    border-radius: 2px;
  }
}
@media (min-width: 541px) {
  .navbar-header {
    float: left;
  }
}
.navbar-collapse {
  overflow-x: visible;
  padding-right: 0px;
  padding-left: 0px;
  border-top: 1px solid transparent;
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.1);
  -webkit-overflow-scrolling: touch;
}
.navbar-collapse.in {
  overflow-y: auto;
}
@media (min-width: 541px) {
  .navbar-collapse {
    width: auto;
    border-top: 0;
    box-shadow: none;
  }
  .navbar-collapse.collapse {
    display: block !important;
    height: auto !important;
    padding-bottom: 0;
    overflow: visible !important;
  }
  .navbar-collapse.in {
    overflow-y: visible;
  }
  .navbar-fixed-top .navbar-collapse,
  .navbar-static-top .navbar-collapse,
  .navbar-fixed-bottom .navbar-collapse {
    padding-left: 0;
    padding-right: 0;
  }
}
.navbar-fixed-top .navbar-collapse,
.navbar-fixed-bottom .navbar-collapse {
  max-height: 340px;
}
@media (max-device-width: 540px) and (orientation: landscape) {
  .navbar-fixed-top .navbar-collapse,
  .navbar-fixed-bottom .navbar-collapse {
    max-height: 200px;
  }
}
.container > .navbar-header,
.container-fluid > .navbar-header,
.container > .navbar-collapse,
.container-fluid > .navbar-collapse {
  margin-right: 0px;
  margin-left: 0px;
}
@media (min-width: 541px) {
  .container > .navbar-header,
  .container-fluid > .navbar-header,
  .container > .navbar-collapse,
  .container-fluid > .navbar-collapse {
    margin-right: 0;
    margin-left: 0;
  }
}
.navbar-static-top {
  z-index: 1000;
  border-width: 0 0 1px;
}
@media (min-width: 541px) {
  .navbar-static-top {
    border-radius: 0;
  }
}
.navbar-fixed-top,
.navbar-fixed-bottom {
  position: fixed;
  right: 0;
  left: 0;
  z-index: 1030;
}
@media (min-width: 541px) {
  .navbar-fixed-top,
  .navbar-fixed-bottom {
    border-radius: 0;
  }
}
.navbar-fixed-top {
  top: 0;
  border-width: 0 0 1px;
}
.navbar-fixed-bottom {
  bottom: 0;
  margin-bottom: 0;
  border-width: 1px 0 0;
}
.navbar-brand {
  float: left;
  padding: 6px 0px;
  font-size: 17px;
  line-height: 18px;
  height: 30px;
}
.navbar-brand:hover,
.navbar-brand:focus {
  text-decoration: none;
}
.navbar-brand > img {
  display: block;
}
@media (min-width: 541px) {
  .navbar > .container .navbar-brand,
  .navbar > .container-fluid .navbar-brand {
    margin-left: 0px;
  }
}
.navbar-toggle {
  position: relative;
  float: right;
  margin-right: 0px;
  padding: 9px 10px;
  margin-top: -2px;
  margin-bottom: -2px;
  background-color: transparent;
  background-image: none;
  border: 1px solid transparent;
  border-radius: 2px;
}
.navbar-toggle:focus {
  outline: 0;
}
.navbar-toggle .icon-bar {
  display: block;
  width: 22px;
  height: 2px;
  border-radius: 1px;
}
.navbar-toggle .icon-bar + .icon-bar {
  margin-top: 4px;
}
@media (min-width: 541px) {
  .navbar-toggle {
    display: none;
  }
}
.navbar-nav {
  margin: 3px 0px;
}
.navbar-nav > li > a {
  padding-top: 10px;
  padding-bottom: 10px;
  line-height: 18px;
}
@media (max-width: 540px) {
  .navbar-nav .open .dropdown-menu {
    position: static;
    float: none;
    width: auto;
    margin-top: 0;
    background-color: transparent;
    border: 0;
    box-shadow: none;
  }
  .navbar-nav .open .dropdown-menu > li > a,
  .navbar-nav .open .dropdown-menu .dropdown-header {
    padding: 5px 15px 5px 25px;
  }
  .navbar-nav .open .dropdown-menu > li > a {
    line-height: 18px;
  }
  .navbar-nav .open .dropdown-menu > li > a:hover,
  .navbar-nav .open .dropdown-menu > li > a:focus {
    background-image: none;
  }
}
@media (min-width: 541px) {
  .navbar-nav {
    float: left;
    margin: 0;
  }
  .navbar-nav > li {
    float: left;
  }
  .navbar-nav > li > a {
    padding-top: 6px;
    padding-bottom: 6px;
  }
}
.navbar-form {
  margin-left: 0px;
  margin-right: 0px;
  padding: 10px 0px;
  border-top: 1px solid transparent;
  border-bottom: 1px solid transparent;
  -webkit-box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.1), 0 1px 0 rgba(255, 255, 255, 0.1);
  box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.1), 0 1px 0 rgba(255, 255, 255, 0.1);
  margin-top: -1px;
  margin-bottom: -1px;
}
@media (min-width: 768px) {
  .navbar-form .form-group {
    display: inline-block;
    margin-bottom: 0;
    vertical-align: middle;
  }
  .navbar-form .form-control {
    display: inline-block;
    width: auto;
    vertical-align: middle;
  }
  .navbar-form .form-control-static {
    display: inline-block;
  }
  .navbar-form .input-group {
    display: inline-table;
    vertical-align: middle;
  }
  .navbar-form .input-group .input-group-addon,
  .navbar-form .input-group .input-group-btn,
  .navbar-form .input-group .form-control {
    width: auto;
  }
  .navbar-form .input-group > .form-control {
    width: 100%;
  }
  .navbar-form .control-label {
    margin-bottom: 0;
    vertical-align: middle;
  }
  .navbar-form .radio,
  .navbar-form .checkbox {
    display: inline-block;
    margin-top: 0;
    margin-bottom: 0;
    vertical-align: middle;
  }
  .navbar-form .radio label,
  .navbar-form .checkbox label {
    padding-left: 0;
  }
  .navbar-form .radio input[type="radio"],
  .navbar-form .checkbox input[type="checkbox"] {
    position: relative;
    margin-left: 0;
  }
  .navbar-form .has-feedback .form-control-feedback {
    top: 0;
  }
}
@media (max-width: 540px) {
  .navbar-form .form-group {
    margin-bottom: 5px;
  }
  .navbar-form .form-group:last-child {
    margin-bottom: 0;
  }
}
@media (min-width: 541px) {
  .navbar-form {
    width: auto;
    border: 0;
    margin-left: 0;
    margin-right: 0;
    padding-top: 0;
    padding-bottom: 0;
    -webkit-box-shadow: none;
    box-shadow: none;
  }
}
.navbar-nav > li > .dropdown-menu {
  margin-top: 0;
  border-top-right-radius: 0;
  border-top-left-radius: 0;
}
.navbar-fixed-bottom .navbar-nav > li > .dropdown-menu {
  margin-bottom: 0;
  border-top-right-radius: 2px;
  border-top-left-radius: 2px;
  border-bottom-right-radius: 0;
  border-bottom-left-radius: 0;
}
.navbar-btn {
  margin-top: -1px;
  margin-bottom: -1px;
}
.navbar-btn.btn-sm {
  margin-top: 0px;
  margin-bottom: 0px;
}
.navbar-btn.btn-xs {
  margin-top: 4px;
  margin-bottom: 4px;
}
.navbar-text {
  margin-top: 6px;
  margin-bottom: 6px;
}
@media (min-width: 541px) {
  .navbar-text {
    float: left;
    margin-left: 0px;
    margin-right: 0px;
  }
}
@media (min-width: 541px) {
  .navbar-left {
    float: left !important;
    float: left;
  }
  .navbar-right {
    float: right !important;
    float: right;
    margin-right: 0px;
  }
  .navbar-right ~ .navbar-right {
    margin-right: 0;
  }
}
.navbar-default {
  background-color: #f8f8f8;
  border-color: #e7e7e7;
}
.navbar-default .navbar-brand {
  color: #777;
}
.navbar-default .navbar-brand:hover,
.navbar-default .navbar-brand:focus {
  color: #5e5e5e;
  background-color: transparent;
}
.navbar-default .navbar-text {
  color: #777;
}
.navbar-default .navbar-nav > li > a {
  color: #777;
}
.navbar-default .navbar-nav > li > a:hover,
.navbar-default .navbar-nav > li > a:focus {
  color: #333;
  background-color: transparent;
}
.navbar-default .navbar-nav > .active > a,
.navbar-default .navbar-nav > .active > a:hover,
.navbar-default .navbar-nav > .active > a:focus {
  color: #555;
  background-color: #e7e7e7;
}
.navbar-default .navbar-nav > .disabled > a,
.navbar-default .navbar-nav > .disabled > a:hover,
.navbar-default .navbar-nav > .disabled > a:focus {
  color: #ccc;
  background-color: transparent;
}
.navbar-default .navbar-toggle {
  border-color: #ddd;
}
.navbar-default .navbar-toggle:hover,
.navbar-default .navbar-toggle:focus {
  background-color: #ddd;
}
.navbar-default .navbar-toggle .icon-bar {
  background-color: #888;
}
.navbar-default .navbar-collapse,
.navbar-default .navbar-form {
  border-color: #e7e7e7;
}
.navbar-default .navbar-nav > .open > a,
.navbar-default .navbar-nav > .open > a:hover,
.navbar-default .navbar-nav > .open > a:focus {
  background-color: #e7e7e7;
  color: #555;
}
@media (max-width: 540px) {
  .navbar-default .navbar-nav .open .dropdown-menu > li > a {
    color: #777;
  }
  .navbar-default .navbar-nav .open .dropdown-menu > li > a:hover,
  .navbar-default .navbar-nav .open .dropdown-menu > li > a:focus {
    color: #333;
    background-color: transparent;
  }
  .navbar-default .navbar-nav .open .dropdown-menu > .active > a,
  .navbar-default .navbar-nav .open .dropdown-menu > .active > a:hover,
  .navbar-default .navbar-nav .open .dropdown-menu > .active > a:focus {
    color: #555;
    background-color: #e7e7e7;
  }
  .navbar-default .navbar-nav .open .dropdown-menu > .disabled > a,
  .navbar-default .navbar-nav .open .dropdown-menu > .disabled > a:hover,
  .navbar-default .navbar-nav .open .dropdown-menu > .disabled > a:focus {
    color: #ccc;
    background-color: transparent;
  }
}
.navbar-default .navbar-link {
  color: #777;
}
.navbar-default .navbar-link:hover {
  color: #333;
}
.navbar-default .btn-link {
  color: #777;
}
.navbar-default .btn-link:hover,
.navbar-default .btn-link:focus {
  color: #333;
}
.navbar-default .btn-link[disabled]:hover,
fieldset[disabled] .navbar-default .btn-link:hover,
.navbar-default .btn-link[disabled]:focus,
fieldset[disabled] .navbar-default .btn-link:focus {
  color: #ccc;
}
.navbar-inverse {
  background-color: #222;
  border-color: #080808;
}
.navbar-inverse .navbar-brand {
  color: #9d9d9d;
}
.navbar-inverse .navbar-brand:hover,
.navbar-inverse .navbar-brand:focus {
  color: #fff;
  background-color: transparent;
}
.navbar-inverse .navbar-text {
  color: #9d9d9d;
}
.navbar-inverse .navbar-nav > li > a {
  color: #9d9d9d;
}
.navbar-inverse .navbar-nav > li > a:hover,
.navbar-inverse .navbar-nav > li > a:focus {
  color: #fff;
  background-color: transparent;
}
.navbar-inverse .navbar-nav > .active > a,
.navbar-inverse .navbar-nav > .active > a:hover,
.navbar-inverse .navbar-nav > .active > a:focus {
  color: #fff;
  background-color: #080808;
}
.navbar-inverse .navbar-nav > .disabled > a,
.navbar-inverse .navbar-nav > .disabled > a:hover,
.navbar-inverse .navbar-nav > .disabled > a:focus {
  color: #444;
  background-color: transparent;
}
.navbar-inverse .navbar-toggle {
  border-color: #333;
}
.navbar-inverse .navbar-toggle:hover,
.navbar-inverse .navbar-toggle:focus {
  background-color: #333;
}
.navbar-inverse .navbar-toggle .icon-bar {
  background-color: #fff;
}
.navbar-inverse .navbar-collapse,
.navbar-inverse .navbar-form {
  border-color: #101010;
}
.navbar-inverse .navbar-nav > .open > a,
.navbar-inverse .navbar-nav > .open > a:hover,
.navbar-inverse .navbar-nav > .open > a:focus {
  background-color: #080808;
  color: #fff;
}
@media (max-width: 540px) {
  .navbar-inverse .navbar-nav .open .dropdown-menu > .dropdown-header {
    border-color: #080808;
  }
  .navbar-inverse .navbar-nav .open .dropdown-menu .divider {
    background-color: #080808;
  }
  .navbar-inverse .navbar-nav .open .dropdown-menu > li > a {
    color: #9d9d9d;
  }
  .navbar-inverse .navbar-nav .open .dropdown-menu > li > a:hover,
  .navbar-inverse .navbar-nav .open .dropdown-menu > li > a:focus {
    color: #fff;
    background-color: transparent;
  }
  .navbar-inverse .navbar-nav .open .dropdown-menu > .active > a,
  .navbar-inverse .navbar-nav .open .dropdown-menu > .active > a:hover,
  .navbar-inverse .navbar-nav .open .dropdown-menu > .active > a:focus {
    color: #fff;
    background-color: #080808;
  }
  .navbar-inverse .navbar-nav .open .dropdown-menu > .disabled > a,
  .navbar-inverse .navbar-nav .open .dropdown-menu > .disabled > a:hover,
  .navbar-inverse .navbar-nav .open .dropdown-menu > .disabled > a:focus {
    color: #444;
    background-color: transparent;
  }
}
.navbar-inverse .navbar-link {
  color: #9d9d9d;
}
.navbar-inverse .navbar-link:hover {
  color: #fff;
}
.navbar-inverse .btn-link {
  color: #9d9d9d;
}
.navbar-inverse .btn-link:hover,
.navbar-inverse .btn-link:focus {
  color: #fff;
}
.navbar-inverse .btn-link[disabled]:hover,
fieldset[disabled] .navbar-inverse .btn-link:hover,
.navbar-inverse .btn-link[disabled]:focus,
fieldset[disabled] .navbar-inverse .btn-link:focus {
  color: #444;
}
.breadcrumb {
  padding: 8px 15px;
  margin-bottom: 18px;
  list-style: none;
  background-color: #f5f5f5;
  border-radius: 2px;
}
.breadcrumb > li {
  display: inline-block;
}
.breadcrumb > li + li:before {
  content: "/\00a0";
  padding: 0 5px;
  color: #5e5e5e;
}
.breadcrumb > .active {
  color: #777777;
}
.pagination {
  display: inline-block;
  padding-left: 0;
  margin: 18px 0;
  border-radius: 2px;
}
.pagination > li {
  display: inline;
}
.pagination > li > a,
.pagination > li > span {
  position: relative;
  float: left;
  padding: 6px 12px;
  line-height: 1.42857143;
  text-decoration: none;
  color: #337ab7;
  background-color: #fff;
  border: 1px solid #ddd;
  margin-left: -1px;
}
.pagination > li:first-child > a,
.pagination > li:first-child > span {
  margin-left: 0;
  border-bottom-left-radius: 2px;
  border-top-left-radius: 2px;
}
.pagination > li:last-child > a,
.pagination > li:last-child > span {
  border-bottom-right-radius: 2px;
  border-top-right-radius: 2px;
}
.pagination > li > a:hover,
.pagination > li > span:hover,
.pagination > li > a:focus,
.pagination > li > span:focus {
  z-index: 2;
  color: #23527c;
  background-color: #eeeeee;
  border-color: #ddd;
}
.pagination > .active > a,
.pagination > .active > span,
.pagination > .active > a:hover,
.pagination > .active > span:hover,
.pagination > .active > a:focus,
.pagination > .active > span:focus {
  z-index: 3;
  color: #fff;
  background-color: #337ab7;
  border-color: #337ab7;
  cursor: default;
}
.pagination > .disabled > span,
.pagination > .disabled > span:hover,
.pagination > .disabled > span:focus,
.pagination > .disabled > a,
.pagination > .disabled > a:hover,
.pagination > .disabled > a:focus {
  color: #777777;
  background-color: #fff;
  border-color: #ddd;
  cursor: not-allowed;
}
.pagination-lg > li > a,
.pagination-lg > li > span {
  padding: 10px 16px;
  font-size: 17px;
  line-height: 1.3333333;
}
.pagination-lg > li:first-child > a,
.pagination-lg > li:first-child > span {
  border-bottom-left-radius: 3px;
  border-top-left-radius: 3px;
}
.pagination-lg > li:last-child > a,
.pagination-lg > li:last-child > span {
  border-bottom-right-radius: 3px;
  border-top-right-radius: 3px;
}
.pagination-sm > li > a,
.pagination-sm > li > span {
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
}
.pagination-sm > li:first-child > a,
.pagination-sm > li:first-child > span {
  border-bottom-left-radius: 1px;
  border-top-left-radius: 1px;
}
.pagination-sm > li:last-child > a,
.pagination-sm > li:last-child > span {
  border-bottom-right-radius: 1px;
  border-top-right-radius: 1px;
}
.pager {
  padding-left: 0;
  margin: 18px 0;
  list-style: none;
  text-align: center;
}
.pager li {
  display: inline;
}
.pager li > a,
.pager li > span {
  display: inline-block;
  padding: 5px 14px;
  background-color: #fff;
  border: 1px solid #ddd;
  border-radius: 15px;
}
.pager li > a:hover,
.pager li > a:focus {
  text-decoration: none;
  background-color: #eeeeee;
}
.pager .next > a,
.pager .next > span {
  float: right;
}
.pager .previous > a,
.pager .previous > span {
  float: left;
}
.pager .disabled > a,
.pager .disabled > a:hover,
.pager .disabled > a:focus,
.pager .disabled > span {
  color: #777777;
  background-color: #fff;
  cursor: not-allowed;
}
.label {
  display: inline;
  padding: .2em .6em .3em;
  font-size: 75%;
  font-weight: bold;
  line-height: 1;
  color: #fff;
  text-align: center;
  white-space: nowrap;
  vertical-align: baseline;
  border-radius: .25em;
}
a.label:hover,
a.label:focus {
  color: #fff;
  text-decoration: none;
  cursor: pointer;
}
.label:empty {
  display: none;
}
.btn .label {
  position: relative;
  top: -1px;
}
.label-default {
  background-color: #777777;
}
.label-default[href]:hover,
.label-default[href]:focus {
  background-color: #5e5e5e;
}
.label-primary {
  background-color: #337ab7;
}
.label-primary[href]:hover,
.label-primary[href]:focus {
  background-color: #286090;
}
.label-success {
  background-color: #5cb85c;
}
.label-success[href]:hover,
.label-success[href]:focus {
  background-color: #449d44;
}
.label-info {
  background-color: #5bc0de;
}
.label-info[href]:hover,
.label-info[href]:focus {
  background-color: #31b0d5;
}
.label-warning {
  background-color: #f0ad4e;
}
.label-warning[href]:hover,
.label-warning[href]:focus {
  background-color: #ec971f;
}
.label-danger {
  background-color: #d9534f;
}
.label-danger[href]:hover,
.label-danger[href]:focus {
  background-color: #c9302c;
}
.badge {
  display: inline-block;
  min-width: 10px;
  padding: 3px 7px;
  font-size: 12px;
  font-weight: bold;
  color: #fff;
  line-height: 1;
  vertical-align: middle;
  white-space: nowrap;
  text-align: center;
  background-color: #777777;
  border-radius: 10px;
}
.badge:empty {
  display: none;
}
.btn .badge {
  position: relative;
  top: -1px;
}
.btn-xs .badge,
.btn-group-xs > .btn .badge {
  top: 0;
  padding: 1px 5px;
}
a.badge:hover,
a.badge:focus {
  color: #fff;
  text-decoration: none;
  cursor: pointer;
}
.list-group-item.active > .badge,
.nav-pills > .active > a > .badge {
  color: #337ab7;
  background-color: #fff;
}
.list-group-item > .badge {
  float: right;
}
.list-group-item > .badge + .badge {
  margin-right: 5px;
}
.nav-pills > li > a > .badge {
  margin-left: 3px;
}
.jumbotron {
  padding-top: 30px;
  padding-bottom: 30px;
  margin-bottom: 30px;
  color: inherit;
  background-color: #eeeeee;
}
.jumbotron h1,
.jumbotron .h1 {
  color: inherit;
}
.jumbotron p {
  margin-bottom: 15px;
  font-size: 20px;
  font-weight: 200;
}
.jumbotron > hr {
  border-top-color: #d5d5d5;
}
.container .jumbotron,
.container-fluid .jumbotron {
  border-radius: 3px;
  padding-left: 0px;
  padding-right: 0px;
}
.jumbotron .container {
  max-width: 100%;
}
@media screen and (min-width: 768px) {
  .jumbotron {
    padding-top: 48px;
    padding-bottom: 48px;
  }
  .container .jumbotron,
  .container-fluid .jumbotron {
    padding-left: 60px;
    padding-right: 60px;
  }
  .jumbotron h1,
  .jumbotron .h1 {
    font-size: 59px;
  }
}
.thumbnail {
  display: block;
  padding: 4px;
  margin-bottom: 18px;
  line-height: 1.42857143;
  background-color: #fff;
  border: 1px solid #ddd;
  border-radius: 2px;
  -webkit-transition: border 0.2s ease-in-out;
  -o-transition: border 0.2s ease-in-out;
  transition: border 0.2s ease-in-out;
}
.thumbnail > img,
.thumbnail a > img {
  margin-left: auto;
  margin-right: auto;
}
a.thumbnail:hover,
a.thumbnail:focus,
a.thumbnail.active {
  border-color: #337ab7;
}
.thumbnail .caption {
  padding: 9px;
  color: #000;
}
.alert {
  padding: 15px;
  margin-bottom: 18px;
  border: 1px solid transparent;
  border-radius: 2px;
}
.alert h4 {
  margin-top: 0;
  color: inherit;
}
.alert .alert-link {
  font-weight: bold;
}
.alert > p,
.alert > ul {
  margin-bottom: 0;
}
.alert > p + p {
  margin-top: 5px;
}
.alert-dismissable,
.alert-dismissible {
  padding-right: 35px;
}
.alert-dismissable .close,
.alert-dismissible .close {
  position: relative;
  top: -2px;
  right: -21px;
  color: inherit;
}
.alert-success {
  background-color: #dff0d8;
  border-color: #d6e9c6;
  color: #3c763d;
}
.alert-success hr {
  border-top-color: #c9e2b3;
}
.alert-success .alert-link {
  color: #2b542c;
}
.alert-info {
  background-color: #d9edf7;
  border-color: #bce8f1;
  color: #31708f;
}
.alert-info hr {
  border-top-color: #a6e1ec;
}
.alert-info .alert-link {
  color: #245269;
}
.alert-warning {
  background-color: #fcf8e3;
  border-color: #faebcc;
  color: #8a6d3b;
}
.alert-warning hr {
  border-top-color: #f7e1b5;
}
.alert-warning .alert-link {
  color: #66512c;
}
.alert-danger {
  background-color: #f2dede;
  border-color: #ebccd1;
  color: #a94442;
}
.alert-danger hr {
  border-top-color: #e4b9c0;
}
.alert-danger .alert-link {
  color: #843534;
}
@-webkit-keyframes progress-bar-stripes {
  from {
    background-position: 40px 0;
  }
  to {
    background-position: 0 0;
  }
}
@keyframes progress-bar-stripes {
  from {
    background-position: 40px 0;
  }
  to {
    background-position: 0 0;
  }
}
.progress {
  overflow: hidden;
  height: 18px;
  margin-bottom: 18px;
  background-color: #f5f5f5;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 1px 2px rgba(0, 0, 0, 0.1);
  box-shadow: inset 0 1px 2px rgba(0, 0, 0, 0.1);
}
.progress-bar {
  float: left;
  width: 0%;
  height: 100%;
  font-size: 12px;
  line-height: 18px;
  color: #fff;
  text-align: center;
  background-color: #337ab7;
  -webkit-box-shadow: inset 0 -1px 0 rgba(0, 0, 0, 0.15);
  box-shadow: inset 0 -1px 0 rgba(0, 0, 0, 0.15);
  -webkit-transition: width 0.6s ease;
  -o-transition: width 0.6s ease;
  transition: width 0.6s ease;
}
.progress-striped .progress-bar,
.progress-bar-striped {
  background-image: -webkit-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: -o-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-size: 40px 40px;
}
.progress.active .progress-bar,
.progress-bar.active {
  -webkit-animation: progress-bar-stripes 2s linear infinite;
  -o-animation: progress-bar-stripes 2s linear infinite;
  animation: progress-bar-stripes 2s linear infinite;
}
.progress-bar-success {
  background-color: #5cb85c;
}
.progress-striped .progress-bar-success {
  background-image: -webkit-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: -o-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
}
.progress-bar-info {
  background-color: #5bc0de;
}
.progress-striped .progress-bar-info {
  background-image: -webkit-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: -o-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
}
.progress-bar-warning {
  background-color: #f0ad4e;
}
.progress-striped .progress-bar-warning {
  background-image: -webkit-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: -o-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
}
.progress-bar-danger {
  background-color: #d9534f;
}
.progress-striped .progress-bar-danger {
  background-image: -webkit-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: -o-linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
  background-image: linear-gradient(45deg, rgba(255, 255, 255, 0.15) 25%, transparent 25%, transparent 50%, rgba(255, 255, 255, 0.15) 50%, rgba(255, 255, 255, 0.15) 75%, transparent 75%, transparent);
}
.media {
  margin-top: 15px;
}
.media:first-child {
  margin-top: 0;
}
.media,
.media-body {
  zoom: 1;
  overflow: hidden;
}
.media-body {
  width: 10000px;
}
.media-object {
  display: block;
}
.media-object.img-thumbnail {
  max-width: none;
}
.media-right,
.media > .pull-right {
  padding-left: 10px;
}
.media-left,
.media > .pull-left {
  padding-right: 10px;
}
.media-left,
.media-right,
.media-body {
  display: table-cell;
  vertical-align: top;
}
.media-middle {
  vertical-align: middle;
}
.media-bottom {
  vertical-align: bottom;
}
.media-heading {
  margin-top: 0;
  margin-bottom: 5px;
}
.media-list {
  padding-left: 0;
  list-style: none;
}
.list-group {
  margin-bottom: 20px;
  padding-left: 0;
}
.list-group-item {
  position: relative;
  display: block;
  padding: 10px 15px;
  margin-bottom: -1px;
  background-color: #fff;
  border: 1px solid #ddd;
}
.list-group-item:first-child {
  border-top-right-radius: 2px;
  border-top-left-radius: 2px;
}
.list-group-item:last-child {
  margin-bottom: 0;
  border-bottom-right-radius: 2px;
  border-bottom-left-radius: 2px;
}
a.list-group-item,
button.list-group-item {
  color: #555;
}
a.list-group-item .list-group-item-heading,
button.list-group-item .list-group-item-heading {
  color: #333;
}
a.list-group-item:hover,
button.list-group-item:hover,
a.list-group-item:focus,
button.list-group-item:focus {
  text-decoration: none;
  color: #555;
  background-color: #f5f5f5;
}
button.list-group-item {
  width: 100%;
  text-align: left;
}
.list-group-item.disabled,
.list-group-item.disabled:hover,
.list-group-item.disabled:focus {
  background-color: #eeeeee;
  color: #777777;
  cursor: not-allowed;
}
.list-group-item.disabled .list-group-item-heading,
.list-group-item.disabled:hover .list-group-item-heading,
.list-group-item.disabled:focus .list-group-item-heading {
  color: inherit;
}
.list-group-item.disabled .list-group-item-text,
.list-group-item.disabled:hover .list-group-item-text,
.list-group-item.disabled:focus .list-group-item-text {
  color: #777777;
}
.list-group-item.active,
.list-group-item.active:hover,
.list-group-item.active:focus {
  z-index: 2;
  color: #fff;
  background-color: #337ab7;
  border-color: #337ab7;
}
.list-group-item.active .list-group-item-heading,
.list-group-item.active:hover .list-group-item-heading,
.list-group-item.active:focus .list-group-item-heading,
.list-group-item.active .list-group-item-heading > small,
.list-group-item.active:hover .list-group-item-heading > small,
.list-group-item.active:focus .list-group-item-heading > small,
.list-group-item.active .list-group-item-heading > .small,
.list-group-item.active:hover .list-group-item-heading > .small,
.list-group-item.active:focus .list-group-item-heading > .small {
  color: inherit;
}
.list-group-item.active .list-group-item-text,
.list-group-item.active:hover .list-group-item-text,
.list-group-item.active:focus .list-group-item-text {
  color: #c7ddef;
}
.list-group-item-success {
  color: #3c763d;
  background-color: #dff0d8;
}
a.list-group-item-success,
button.list-group-item-success {
  color: #3c763d;
}
a.list-group-item-success .list-group-item-heading,
button.list-group-item-success .list-group-item-heading {
  color: inherit;
}
a.list-group-item-success:hover,
button.list-group-item-success:hover,
a.list-group-item-success:focus,
button.list-group-item-success:focus {
  color: #3c763d;
  background-color: #d0e9c6;
}
a.list-group-item-success.active,
button.list-group-item-success.active,
a.list-group-item-success.active:hover,
button.list-group-item-success.active:hover,
a.list-group-item-success.active:focus,
button.list-group-item-success.active:focus {
  color: #fff;
  background-color: #3c763d;
  border-color: #3c763d;
}
.list-group-item-info {
  color: #31708f;
  background-color: #d9edf7;
}
a.list-group-item-info,
button.list-group-item-info {
  color: #31708f;
}
a.list-group-item-info .list-group-item-heading,
button.list-group-item-info .list-group-item-heading {
  color: inherit;
}
a.list-group-item-info:hover,
button.list-group-item-info:hover,
a.list-group-item-info:focus,
button.list-group-item-info:focus {
  color: #31708f;
  background-color: #c4e3f3;
}
a.list-group-item-info.active,
button.list-group-item-info.active,
a.list-group-item-info.active:hover,
button.list-group-item-info.active:hover,
a.list-group-item-info.active:focus,
button.list-group-item-info.active:focus {
  color: #fff;
  background-color: #31708f;
  border-color: #31708f;
}
.list-group-item-warning {
  color: #8a6d3b;
  background-color: #fcf8e3;
}
a.list-group-item-warning,
button.list-group-item-warning {
  color: #8a6d3b;
}
a.list-group-item-warning .list-group-item-heading,
button.list-group-item-warning .list-group-item-heading {
  color: inherit;
}
a.list-group-item-warning:hover,
button.list-group-item-warning:hover,
a.list-group-item-warning:focus,
button.list-group-item-warning:focus {
  color: #8a6d3b;
  background-color: #faf2cc;
}
a.list-group-item-warning.active,
button.list-group-item-warning.active,
a.list-group-item-warning.active:hover,
button.list-group-item-warning.active:hover,
a.list-group-item-warning.active:focus,
button.list-group-item-warning.active:focus {
  color: #fff;
  background-color: #8a6d3b;
  border-color: #8a6d3b;
}
.list-group-item-danger {
  color: #a94442;
  background-color: #f2dede;
}
a.list-group-item-danger,
button.list-group-item-danger {
  color: #a94442;
}
a.list-group-item-danger .list-group-item-heading,
button.list-group-item-danger .list-group-item-heading {
  color: inherit;
}
a.list-group-item-danger:hover,
button.list-group-item-danger:hover,
a.list-group-item-danger:focus,
button.list-group-item-danger:focus {
  color: #a94442;
  background-color: #ebcccc;
}
a.list-group-item-danger.active,
button.list-group-item-danger.active,
a.list-group-item-danger.active:hover,
button.list-group-item-danger.active:hover,
a.list-group-item-danger.active:focus,
button.list-group-item-danger.active:focus {
  color: #fff;
  background-color: #a94442;
  border-color: #a94442;
}
.list-group-item-heading {
  margin-top: 0;
  margin-bottom: 5px;
}
.list-group-item-text {
  margin-bottom: 0;
  line-height: 1.3;
}
.panel {
  margin-bottom: 18px;
  background-color: #fff;
  border: 1px solid transparent;
  border-radius: 2px;
  -webkit-box-shadow: 0 1px 1px rgba(0, 0, 0, 0.05);
  box-shadow: 0 1px 1px rgba(0, 0, 0, 0.05);
}
.panel-body {
  padding: 15px;
}
.panel-heading {
  padding: 10px 15px;
  border-bottom: 1px solid transparent;
  border-top-right-radius: 1px;
  border-top-left-radius: 1px;
}
.panel-heading > .dropdown .dropdown-toggle {
  color: inherit;
}
.panel-title {
  margin-top: 0;
  margin-bottom: 0;
  font-size: 15px;
  color: inherit;
}
.panel-title > a,
.panel-title > small,
.panel-title > .small,
.panel-title > small > a,
.panel-title > .small > a {
  color: inherit;
}
.panel-footer {
  padding: 10px 15px;
  background-color: #f5f5f5;
  border-top: 1px solid #ddd;
  border-bottom-right-radius: 1px;
  border-bottom-left-radius: 1px;
}
.panel > .list-group,
.panel > .panel-collapse > .list-group {
  margin-bottom: 0;
}
.panel > .list-group .list-group-item,
.panel > .panel-collapse > .list-group .list-group-item {
  border-width: 1px 0;
  border-radius: 0;
}
.panel > .list-group:first-child .list-group-item:first-child,
.panel > .panel-collapse > .list-group:first-child .list-group-item:first-child {
  border-top: 0;
  border-top-right-radius: 1px;
  border-top-left-radius: 1px;
}
.panel > .list-group:last-child .list-group-item:last-child,
.panel > .panel-collapse > .list-group:last-child .list-group-item:last-child {
  border-bottom: 0;
  border-bottom-right-radius: 1px;
  border-bottom-left-radius: 1px;
}
.panel > .panel-heading + .panel-collapse > .list-group .list-group-item:first-child {
  border-top-right-radius: 0;
  border-top-left-radius: 0;
}
.panel-heading + .list-group .list-group-item:first-child {
  border-top-width: 0;
}
.list-group + .panel-footer {
  border-top-width: 0;
}
.panel > .table,
.panel > .table-responsive > .table,
.panel > .panel-collapse > .table {
  margin-bottom: 0;
}
.panel > .table caption,
.panel > .table-responsive > .table caption,
.panel > .panel-collapse > .table caption {
  padding-left: 15px;
  padding-right: 15px;
}
.panel > .table:first-child,
.panel > .table-responsive:first-child > .table:first-child {
  border-top-right-radius: 1px;
  border-top-left-radius: 1px;
}
.panel > .table:first-child > thead:first-child > tr:first-child,
.panel > .table-responsive:first-child > .table:first-child > thead:first-child > tr:first-child,
.panel > .table:first-child > tbody:first-child > tr:first-child,
.panel > .table-responsive:first-child > .table:first-child > tbody:first-child > tr:first-child {
  border-top-left-radius: 1px;
  border-top-right-radius: 1px;
}
.panel > .table:first-child > thead:first-child > tr:first-child td:first-child,
.panel > .table-responsive:first-child > .table:first-child > thead:first-child > tr:first-child td:first-child,
.panel > .table:first-child > tbody:first-child > tr:first-child td:first-child,
.panel > .table-responsive:first-child > .table:first-child > tbody:first-child > tr:first-child td:first-child,
.panel > .table:first-child > thead:first-child > tr:first-child th:first-child,
.panel > .table-responsive:first-child > .table:first-child > thead:first-child > tr:first-child th:first-child,
.panel > .table:first-child > tbody:first-child > tr:first-child th:first-child,
.panel > .table-responsive:first-child > .table:first-child > tbody:first-child > tr:first-child th:first-child {
  border-top-left-radius: 1px;
}
.panel > .table:first-child > thead:first-child > tr:first-child td:last-child,
.panel > .table-responsive:first-child > .table:first-child > thead:first-child > tr:first-child td:last-child,
.panel > .table:first-child > tbody:first-child > tr:first-child td:last-child,
.panel > .table-responsive:first-child > .table:first-child > tbody:first-child > tr:first-child td:last-child,
.panel > .table:first-child > thead:first-child > tr:first-child th:last-child,
.panel > .table-responsive:first-child > .table:first-child > thead:first-child > tr:first-child th:last-child,
.panel > .table:first-child > tbody:first-child > tr:first-child th:last-child,
.panel > .table-responsive:first-child > .table:first-child > tbody:first-child > tr:first-child th:last-child {
  border-top-right-radius: 1px;
}
.panel > .table:last-child,
.panel > .table-responsive:last-child > .table:last-child {
  border-bottom-right-radius: 1px;
  border-bottom-left-radius: 1px;
}
.panel > .table:last-child > tbody:last-child > tr:last-child,
.panel > .table-responsive:last-child > .table:last-child > tbody:last-child > tr:last-child,
.panel > .table:last-child > tfoot:last-child > tr:last-child,
.panel > .table-responsive:last-child > .table:last-child > tfoot:last-child > tr:last-child {
  border-bottom-left-radius: 1px;
  border-bottom-right-radius: 1px;
}
.panel > .table:last-child > tbody:last-child > tr:last-child td:first-child,
.panel > .table-responsive:last-child > .table:last-child > tbody:last-child > tr:last-child td:first-child,
.panel > .table:last-child > tfoot:last-child > tr:last-child td:first-child,
.panel > .table-responsive:last-child > .table:last-child > tfoot:last-child > tr:last-child td:first-child,
.panel > .table:last-child > tbody:last-child > tr:last-child th:first-child,
.panel > .table-responsive:last-child > .table:last-child > tbody:last-child > tr:last-child th:first-child,
.panel > .table:last-child > tfoot:last-child > tr:last-child th:first-child,
.panel > .table-responsive:last-child > .table:last-child > tfoot:last-child > tr:last-child th:first-child {
  border-bottom-left-radius: 1px;
}
.panel > .table:last-child > tbody:last-child > tr:last-child td:last-child,
.panel > .table-responsive:last-child > .table:last-child > tbody:last-child > tr:last-child td:last-child,
.panel > .table:last-child > tfoot:last-child > tr:last-child td:last-child,
.panel > .table-responsive:last-child > .table:last-child > tfoot:last-child > tr:last-child td:last-child,
.panel > .table:last-child > tbody:last-child > tr:last-child th:last-child,
.panel > .table-responsive:last-child > .table:last-child > tbody:last-child > tr:last-child th:last-child,
.panel > .table:last-child > tfoot:last-child > tr:last-child th:last-child,
.panel > .table-responsive:last-child > .table:last-child > tfoot:last-child > tr:last-child th:last-child {
  border-bottom-right-radius: 1px;
}
.panel > .panel-body + .table,
.panel > .panel-body + .table-responsive,
.panel > .table + .panel-body,
.panel > .table-responsive + .panel-body {
  border-top: 1px solid #ddd;
}
.panel > .table > tbody:first-child > tr:first-child th,
.panel > .table > tbody:first-child > tr:first-child td {
  border-top: 0;
}
.panel > .table-bordered,
.panel > .table-responsive > .table-bordered {
  border: 0;
}
.panel > .table-bordered > thead > tr > th:first-child,
.panel > .table-responsive > .table-bordered > thead > tr > th:first-child,
.panel > .table-bordered > tbody > tr > th:first-child,
.panel > .table-responsive > .table-bordered > tbody > tr > th:first-child,
.panel > .table-bordered > tfoot > tr > th:first-child,
.panel > .table-responsive > .table-bordered > tfoot > tr > th:first-child,
.panel > .table-bordered > thead > tr > td:first-child,
.panel > .table-responsive > .table-bordered > thead > tr > td:first-child,
.panel > .table-bordered > tbody > tr > td:first-child,
.panel > .table-responsive > .table-bordered > tbody > tr > td:first-child,
.panel > .table-bordered > tfoot > tr > td:first-child,
.panel > .table-responsive > .table-bordered > tfoot > tr > td:first-child {
  border-left: 0;
}
.panel > .table-bordered > thead > tr > th:last-child,
.panel > .table-responsive > .table-bordered > thead > tr > th:last-child,
.panel > .table-bordered > tbody > tr > th:last-child,
.panel > .table-responsive > .table-bordered > tbody > tr > th:last-child,
.panel > .table-bordered > tfoot > tr > th:last-child,
.panel > .table-responsive > .table-bordered > tfoot > tr > th:last-child,
.panel > .table-bordered > thead > tr > td:last-child,
.panel > .table-responsive > .table-bordered > thead > tr > td:last-child,
.panel > .table-bordered > tbody > tr > td:last-child,
.panel > .table-responsive > .table-bordered > tbody > tr > td:last-child,
.panel > .table-bordered > tfoot > tr > td:last-child,
.panel > .table-responsive > .table-bordered > tfoot > tr > td:last-child {
  border-right: 0;
}
.panel > .table-bordered > thead > tr:first-child > td,
.panel > .table-responsive > .table-bordered > thead > tr:first-child > td,
.panel > .table-bordered > tbody > tr:first-child > td,
.panel > .table-responsive > .table-bordered > tbody > tr:first-child > td,
.panel > .table-bordered > thead > tr:first-child > th,
.panel > .table-responsive > .table-bordered > thead > tr:first-child > th,
.panel > .table-bordered > tbody > tr:first-child > th,
.panel > .table-responsive > .table-bordered > tbody > tr:first-child > th {
  border-bottom: 0;
}
.panel > .table-bordered > tbody > tr:last-child > td,
.panel > .table-responsive > .table-bordered > tbody > tr:last-child > td,
.panel > .table-bordered > tfoot > tr:last-child > td,
.panel > .table-responsive > .table-bordered > tfoot > tr:last-child > td,
.panel > .table-bordered > tbody > tr:last-child > th,
.panel > .table-responsive > .table-bordered > tbody > tr:last-child > th,
.panel > .table-bordered > tfoot > tr:last-child > th,
.panel > .table-responsive > .table-bordered > tfoot > tr:last-child > th {
  border-bottom: 0;
}
.panel > .table-responsive {
  border: 0;
  margin-bottom: 0;
}
.panel-group {
  margin-bottom: 18px;
}
.panel-group .panel {
  margin-bottom: 0;
  border-radius: 2px;
}
.panel-group .panel + .panel {
  margin-top: 5px;
}
.panel-group .panel-heading {
  border-bottom: 0;
}
.panel-group .panel-heading + .panel-collapse > .panel-body,
.panel-group .panel-heading + .panel-collapse > .list-group {
  border-top: 1px solid #ddd;
}
.panel-group .panel-footer {
  border-top: 0;
}
.panel-group .panel-footer + .panel-collapse .panel-body {
  border-bottom: 1px solid #ddd;
}
.panel-default {
  border-color: #ddd;
}
.panel-default > .panel-heading {
  color: #333333;
  background-color: #f5f5f5;
  border-color: #ddd;
}
.panel-default > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #ddd;
}
.panel-default > .panel-heading .badge {
  color: #f5f5f5;
  background-color: #333333;
}
.panel-default > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #ddd;
}
.panel-primary {
  border-color: #337ab7;
}
.panel-primary > .panel-heading {
  color: #fff;
  background-color: #337ab7;
  border-color: #337ab7;
}
.panel-primary > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #337ab7;
}
.panel-primary > .panel-heading .badge {
  color: #337ab7;
  background-color: #fff;
}
.panel-primary > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #337ab7;
}
.panel-success {
  border-color: #d6e9c6;
}
.panel-success > .panel-heading {
  color: #3c763d;
  background-color: #dff0d8;
  border-color: #d6e9c6;
}
.panel-success > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #d6e9c6;
}
.panel-success > .panel-heading .badge {
  color: #dff0d8;
  background-color: #3c763d;
}
.panel-success > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #d6e9c6;
}
.panel-info {
  border-color: #bce8f1;
}
.panel-info > .panel-heading {
  color: #31708f;
  background-color: #d9edf7;
  border-color: #bce8f1;
}
.panel-info > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #bce8f1;
}
.panel-info > .panel-heading .badge {
  color: #d9edf7;
  background-color: #31708f;
}
.panel-info > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #bce8f1;
}
.panel-warning {
  border-color: #faebcc;
}
.panel-warning > .panel-heading {
  color: #8a6d3b;
  background-color: #fcf8e3;
  border-color: #faebcc;
}
.panel-warning > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #faebcc;
}
.panel-warning > .panel-heading .badge {
  color: #fcf8e3;
  background-color: #8a6d3b;
}
.panel-warning > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #faebcc;
}
.panel-danger {
  border-color: #ebccd1;
}
.panel-danger > .panel-heading {
  color: #a94442;
  background-color: #f2dede;
  border-color: #ebccd1;
}
.panel-danger > .panel-heading + .panel-collapse > .panel-body {
  border-top-color: #ebccd1;
}
.panel-danger > .panel-heading .badge {
  color: #f2dede;
  background-color: #a94442;
}
.panel-danger > .panel-footer + .panel-collapse > .panel-body {
  border-bottom-color: #ebccd1;
}
.embed-responsive {
  position: relative;
  display: block;
  height: 0;
  padding: 0;
  overflow: hidden;
}
.embed-responsive .embed-responsive-item,
.embed-responsive iframe,
.embed-responsive embed,
.embed-responsive object,
.embed-responsive video {
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  height: 100%;
  width: 100%;
  border: 0;
}
.embed-responsive-16by9 {
  padding-bottom: 56.25%;
}
.embed-responsive-4by3 {
  padding-bottom: 75%;
}
.well {
  min-height: 20px;
  padding: 19px;
  margin-bottom: 20px;
  background-color: #f5f5f5;
  border: 1px solid #e3e3e3;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.05);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.05);
}
.well blockquote {
  border-color: #ddd;
  border-color: rgba(0, 0, 0, 0.15);
}
.well-lg {
  padding: 24px;
  border-radius: 3px;
}
.well-sm {
  padding: 9px;
  border-radius: 1px;
}
.close {
  float: right;
  font-size: 19.5px;
  font-weight: bold;
  line-height: 1;
  color: #000;
  text-shadow: 0 1px 0 #fff;
  opacity: 0.2;
  filter: alpha(opacity=20);
}
.close:hover,
.close:focus {
  color: #000;
  text-decoration: none;
  cursor: pointer;
  opacity: 0.5;
  filter: alpha(opacity=50);
}
button.close {
  padding: 0;
  cursor: pointer;
  background: transparent;
  border: 0;
  -webkit-appearance: none;
}
.modal-open {
  overflow: hidden;
}
.modal {
  display: none;
  overflow: hidden;
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 1050;
  -webkit-overflow-scrolling: touch;
  outline: 0;
}
.modal.fade .modal-dialog {
  -webkit-transform: translate(0, -25%);
  -ms-transform: translate(0, -25%);
  -o-transform: translate(0, -25%);
  transform: translate(0, -25%);
  -webkit-transition: -webkit-transform 0.3s ease-out;
  -moz-transition: -moz-transform 0.3s ease-out;
  -o-transition: -o-transform 0.3s ease-out;
  transition: transform 0.3s ease-out;
}
.modal.in .modal-dialog {
  -webkit-transform: translate(0, 0);
  -ms-transform: translate(0, 0);
  -o-transform: translate(0, 0);
  transform: translate(0, 0);
}
.modal-open .modal {
  overflow-x: hidden;
  overflow-y: auto;
}
.modal-dialog {
  position: relative;
  width: auto;
  margin: 10px;
}
.modal-content {
  position: relative;
  background-color: #fff;
  border: 1px solid #999;
  border: 1px solid rgba(0, 0, 0, 0.2);
  border-radius: 3px;
  -webkit-box-shadow: 0 3px 9px rgba(0, 0, 0, 0.5);
  box-shadow: 0 3px 9px rgba(0, 0, 0, 0.5);
  background-clip: padding-box;
  outline: 0;
}
.modal-backdrop {
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 1040;
  background-color: #000;
}
.modal-backdrop.fade {
  opacity: 0;
  filter: alpha(opacity=0);
}
.modal-backdrop.in {
  opacity: 0.5;
  filter: alpha(opacity=50);
}
.modal-header {
  padding: 15px;
  border-bottom: 1px solid #e5e5e5;
}
.modal-header .close {
  margin-top: -2px;
}
.modal-title {
  margin: 0;
  line-height: 1.42857143;
}
.modal-body {
  position: relative;
  padding: 15px;
}
.modal-footer {
  padding: 15px;
  text-align: right;
  border-top: 1px solid #e5e5e5;
}
.modal-footer .btn + .btn {
  margin-left: 5px;
  margin-bottom: 0;
}
.modal-footer .btn-group .btn + .btn {
  margin-left: -1px;
}
.modal-footer .btn-block + .btn-block {
  margin-left: 0;
}
.modal-scrollbar-measure {
  position: absolute;
  top: -9999px;
  width: 50px;
  height: 50px;
  overflow: scroll;
}
@media (min-width: 768px) {
  .modal-dialog {
    width: 600px;
    margin: 30px auto;
  }
  .modal-content {
    -webkit-box-shadow: 0 5px 15px rgba(0, 0, 0, 0.5);
    box-shadow: 0 5px 15px rgba(0, 0, 0, 0.5);
  }
  .modal-sm {
    width: 300px;
  }
}
@media (min-width: 992px) {
  .modal-lg {
    width: 900px;
  }
}
.tooltip {
  position: absolute;
  z-index: 1070;
  display: block;
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
  font-style: normal;
  font-weight: normal;
  letter-spacing: normal;
  line-break: auto;
  line-height: 1.42857143;
  text-align: left;
  text-align: start;
  text-decoration: none;
  text-shadow: none;
  text-transform: none;
  white-space: normal;
  word-break: normal;
  word-spacing: normal;
  word-wrap: normal;
  font-size: 12px;
  opacity: 0;
  filter: alpha(opacity=0);
}
.tooltip.in {
  opacity: 0.9;
  filter: alpha(opacity=90);
}
.tooltip.top {
  margin-top: -3px;
  padding: 5px 0;
}
.tooltip.right {
  margin-left: 3px;
  padding: 0 5px;
}
.tooltip.bottom {
  margin-top: 3px;
  padding: 5px 0;
}
.tooltip.left {
  margin-left: -3px;
  padding: 0 5px;
}
.tooltip-inner {
  max-width: 200px;
  padding: 3px 8px;
  color: #fff;
  text-align: center;
  background-color: #000;
  border-radius: 2px;
}
.tooltip-arrow {
  position: absolute;
  width: 0;
  height: 0;
  border-color: transparent;
  border-style: solid;
}
.tooltip.top .tooltip-arrow {
  bottom: 0;
  left: 50%;
  margin-left: -5px;
  border-width: 5px 5px 0;
  border-top-color: #000;
}
.tooltip.top-left .tooltip-arrow {
  bottom: 0;
  right: 5px;
  margin-bottom: -5px;
  border-width: 5px 5px 0;
  border-top-color: #000;
}
.tooltip.top-right .tooltip-arrow {
  bottom: 0;
  left: 5px;
  margin-bottom: -5px;
  border-width: 5px 5px 0;
  border-top-color: #000;
}
.tooltip.right .tooltip-arrow {
  top: 50%;
  left: 0;
  margin-top: -5px;
  border-width: 5px 5px 5px 0;
  border-right-color: #000;
}
.tooltip.left .tooltip-arrow {
  top: 50%;
  right: 0;
  margin-top: -5px;
  border-width: 5px 0 5px 5px;
  border-left-color: #000;
}
.tooltip.bottom .tooltip-arrow {
  top: 0;
  left: 50%;
  margin-left: -5px;
  border-width: 0 5px 5px;
  border-bottom-color: #000;
}
.tooltip.bottom-left .tooltip-arrow {
  top: 0;
  right: 5px;
  margin-top: -5px;
  border-width: 0 5px 5px;
  border-bottom-color: #000;
}
.tooltip.bottom-right .tooltip-arrow {
  top: 0;
  left: 5px;
  margin-top: -5px;
  border-width: 0 5px 5px;
  border-bottom-color: #000;
}
.popover {
  position: absolute;
  top: 0;
  left: 0;
  z-index: 1060;
  display: none;
  max-width: 276px;
  padding: 1px;
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
  font-style: normal;
  font-weight: normal;
  letter-spacing: normal;
  line-break: auto;
  line-height: 1.42857143;
  text-align: left;
  text-align: start;
  text-decoration: none;
  text-shadow: none;
  text-transform: none;
  white-space: normal;
  word-break: normal;
  word-spacing: normal;
  word-wrap: normal;
  font-size: 13px;
  background-color: #fff;
  background-clip: padding-box;
  border: 1px solid #ccc;
  border: 1px solid rgba(0, 0, 0, 0.2);
  border-radius: 3px;
  -webkit-box-shadow: 0 5px 10px rgba(0, 0, 0, 0.2);
  box-shadow: 0 5px 10px rgba(0, 0, 0, 0.2);
}
.popover.top {
  margin-top: -10px;
}
.popover.right {
  margin-left: 10px;
}
.popover.bottom {
  margin-top: 10px;
}
.popover.left {
  margin-left: -10px;
}
.popover-title {
  margin: 0;
  padding: 8px 14px;
  font-size: 13px;
  background-color: #f7f7f7;
  border-bottom: 1px solid #ebebeb;
  border-radius: 2px 2px 0 0;
}
.popover-content {
  padding: 9px 14px;
}
.popover > .arrow,
.popover > .arrow:after {
  position: absolute;
  display: block;
  width: 0;
  height: 0;
  border-color: transparent;
  border-style: solid;
}
.popover > .arrow {
  border-width: 11px;
}
.popover > .arrow:after {
  border-width: 10px;
  content: "";
}
.popover.top > .arrow {
  left: 50%;
  margin-left: -11px;
  border-bottom-width: 0;
  border-top-color: #999999;
  border-top-color: rgba(0, 0, 0, 0.25);
  bottom: -11px;
}
.popover.top > .arrow:after {
  content: " ";
  bottom: 1px;
  margin-left: -10px;
  border-bottom-width: 0;
  border-top-color: #fff;
}
.popover.right > .arrow {
  top: 50%;
  left: -11px;
  margin-top: -11px;
  border-left-width: 0;
  border-right-color: #999999;
  border-right-color: rgba(0, 0, 0, 0.25);
}
.popover.right > .arrow:after {
  content: " ";
  left: 1px;
  bottom: -10px;
  border-left-width: 0;
  border-right-color: #fff;
}
.popover.bottom > .arrow {
  left: 50%;
  margin-left: -11px;
  border-top-width: 0;
  border-bottom-color: #999999;
  border-bottom-color: rgba(0, 0, 0, 0.25);
  top: -11px;
}
.popover.bottom > .arrow:after {
  content: " ";
  top: 1px;
  margin-left: -10px;
  border-top-width: 0;
  border-bottom-color: #fff;
}
.popover.left > .arrow {
  top: 50%;
  right: -11px;
  margin-top: -11px;
  border-right-width: 0;
  border-left-color: #999999;
  border-left-color: rgba(0, 0, 0, 0.25);
}
.popover.left > .arrow:after {
  content: " ";
  right: 1px;
  border-right-width: 0;
  border-left-color: #fff;
  bottom: -10px;
}
.carousel {
  position: relative;
}
.carousel-inner {
  position: relative;
  overflow: hidden;
  width: 100%;
}
.carousel-inner > .item {
  display: none;
  position: relative;
  -webkit-transition: 0.6s ease-in-out left;
  -o-transition: 0.6s ease-in-out left;
  transition: 0.6s ease-in-out left;
}
.carousel-inner > .item > img,
.carousel-inner > .item > a > img {
  line-height: 1;
}
@media all and (transform-3d), (-webkit-transform-3d) {
  .carousel-inner > .item {
    -webkit-transition: -webkit-transform 0.6s ease-in-out;
    -moz-transition: -moz-transform 0.6s ease-in-out;
    -o-transition: -o-transform 0.6s ease-in-out;
    transition: transform 0.6s ease-in-out;
    -webkit-backface-visibility: hidden;
    -moz-backface-visibility: hidden;
    backface-visibility: hidden;
    -webkit-perspective: 1000px;
    -moz-perspective: 1000px;
    perspective: 1000px;
  }
  .carousel-inner > .item.next,
  .carousel-inner > .item.active.right {
    -webkit-transform: translate3d(100%, 0, 0);
    transform: translate3d(100%, 0, 0);
    left: 0;
  }
  .carousel-inner > .item.prev,
  .carousel-inner > .item.active.left {
    -webkit-transform: translate3d(-100%, 0, 0);
    transform: translate3d(-100%, 0, 0);
    left: 0;
  }
  .carousel-inner > .item.next.left,
  .carousel-inner > .item.prev.right,
  .carousel-inner > .item.active {
    -webkit-transform: translate3d(0, 0, 0);
    transform: translate3d(0, 0, 0);
    left: 0;
  }
}
.carousel-inner > .active,
.carousel-inner > .next,
.carousel-inner > .prev {
  display: block;
}
.carousel-inner > .active {
  left: 0;
}
.carousel-inner > .next,
.carousel-inner > .prev {
  position: absolute;
  top: 0;
  width: 100%;
}
.carousel-inner > .next {
  left: 100%;
}
.carousel-inner > .prev {
  left: -100%;
}
.carousel-inner > .next.left,
.carousel-inner > .prev.right {
  left: 0;
}
.carousel-inner > .active.left {
  left: -100%;
}
.carousel-inner > .active.right {
  left: 100%;
}
.carousel-control {
  position: absolute;
  top: 0;
  left: 0;
  bottom: 0;
  width: 15%;
  opacity: 0.5;
  filter: alpha(opacity=50);
  font-size: 20px;
  color: #fff;
  text-align: center;
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.6);
  background-color: rgba(0, 0, 0, 0);
}
.carousel-control.left {
  background-image: -webkit-linear-gradient(left, rgba(0, 0, 0, 0.5) 0%, rgba(0, 0, 0, 0.0001) 100%);
  background-image: -o-linear-gradient(left, rgba(0, 0, 0, 0.5) 0%, rgba(0, 0, 0, 0.0001) 100%);
  background-image: linear-gradient(to right, rgba(0, 0, 0, 0.5) 0%, rgba(0, 0, 0, 0.0001) 100%);
  background-repeat: repeat-x;
  filter: progid:DXImageTransform.Microsoft.gradient(startColorstr='#80000000', endColorstr='#00000000', GradientType=1);
}
.carousel-control.right {
  left: auto;
  right: 0;
  background-image: -webkit-linear-gradient(left, rgba(0, 0, 0, 0.0001) 0%, rgba(0, 0, 0, 0.5) 100%);
  background-image: -o-linear-gradient(left, rgba(0, 0, 0, 0.0001) 0%, rgba(0, 0, 0, 0.5) 100%);
  background-image: linear-gradient(to right, rgba(0, 0, 0, 0.0001) 0%, rgba(0, 0, 0, 0.5) 100%);
  background-repeat: repeat-x;
  filter: progid:DXImageTransform.Microsoft.gradient(startColorstr='#00000000', endColorstr='#80000000', GradientType=1);
}
.carousel-control:hover,
.carousel-control:focus {
  outline: 0;
  color: #fff;
  text-decoration: none;
  opacity: 0.9;
  filter: alpha(opacity=90);
}
.carousel-control .icon-prev,
.carousel-control .icon-next,
.carousel-control .glyphicon-chevron-left,
.carousel-control .glyphicon-chevron-right {
  position: absolute;
  top: 50%;
  margin-top: -10px;
  z-index: 5;
  display: inline-block;
}
.carousel-control .icon-prev,
.carousel-control .glyphicon-chevron-left {
  left: 50%;
  margin-left: -10px;
}
.carousel-control .icon-next,
.carousel-control .glyphicon-chevron-right {
  right: 50%;
  margin-right: -10px;
}
.carousel-control .icon-prev,
.carousel-control .icon-next {
  width: 20px;
  height: 20px;
  line-height: 1;
  font-family: serif;
}
.carousel-control .icon-prev:before {
  content: '\2039';
}
.carousel-control .icon-next:before {
  content: '\203a';
}
.carousel-indicators {
  position: absolute;
  bottom: 10px;
  left: 50%;
  z-index: 15;
  width: 60%;
  margin-left: -30%;
  padding-left: 0;
  list-style: none;
  text-align: center;
}
.carousel-indicators li {
  display: inline-block;
  width: 10px;
  height: 10px;
  margin: 1px;
  text-indent: -999px;
  border: 1px solid #fff;
  border-radius: 10px;
  cursor: pointer;
  background-color: #000 \9;
  background-color: rgba(0, 0, 0, 0);
}
.carousel-indicators .active {
  margin: 0;
  width: 12px;
  height: 12px;
  background-color: #fff;
}
.carousel-caption {
  position: absolute;
  left: 15%;
  right: 15%;
  bottom: 20px;
  z-index: 10;
  padding-top: 20px;
  padding-bottom: 20px;
  color: #fff;
  text-align: center;
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.6);
}
.carousel-caption .btn {
  text-shadow: none;
}
@media screen and (min-width: 768px) {
  .carousel-control .glyphicon-chevron-left,
  .carousel-control .glyphicon-chevron-right,
  .carousel-control .icon-prev,
  .carousel-control .icon-next {
    width: 30px;
    height: 30px;
    margin-top: -10px;
    font-size: 30px;
  }
  .carousel-control .glyphicon-chevron-left,
  .carousel-control .icon-prev {
    margin-left: -10px;
  }
  .carousel-control .glyphicon-chevron-right,
  .carousel-control .icon-next {
    margin-right: -10px;
  }
  .carousel-caption {
    left: 20%;
    right: 20%;
    padding-bottom: 30px;
  }
  .carousel-indicators {
    bottom: 20px;
  }
}
.clearfix:before,
.clearfix:after,
.dl-horizontal dd:before,
.dl-horizontal dd:after,
.container:before,
.container:after,
.container-fluid:before,
.container-fluid:after,
.row:before,
.row:after,
.form-horizontal .form-group:before,
.form-horizontal .form-group:after,
.btn-toolbar:before,
.btn-toolbar:after,
.btn-group-vertical > .btn-group:before,
.btn-group-vertical > .btn-group:after,
.nav:before,
.nav:after,
.navbar:before,
.navbar:after,
.navbar-header:before,
.navbar-header:after,
.navbar-collapse:before,
.navbar-collapse:after,
.pager:before,
.pager:after,
.panel-body:before,
.panel-body:after,
.modal-header:before,
.modal-header:after,
.modal-footer:before,
.modal-footer:after,
.item_buttons:before,
.item_buttons:after {
  content: " ";
  display: table;
}
.clearfix:after,
.dl-horizontal dd:after,
.container:after,
.container-fluid:after,
.row:after,
.form-horizontal .form-group:after,
.btn-toolbar:after,
.btn-group-vertical > .btn-group:after,
.nav:after,
.navbar:after,
.navbar-header:after,
.navbar-collapse:after,
.pager:after,
.panel-body:after,
.modal-header:after,
.modal-footer:after,
.item_buttons:after {
  clear: both;
}
.center-block {
  display: block;
  margin-left: auto;
  margin-right: auto;
}
.pull-right {
  float: right !important;
}
.pull-left {
  float: left !important;
}
.hide {
  display: none !important;
}
.show {
  display: block !important;
}
.invisible {
  visibility: hidden;
}
.text-hide {
  font: 0/0 a;
  color: transparent;
  text-shadow: none;
  background-color: transparent;
  border: 0;
}
.hidden {
  display: none !important;
}
.affix {
  position: fixed;
}
@-ms-viewport {
  width: device-width;
}
.visible-xs,
.visible-sm,
.visible-md,
.visible-lg {
  display: none !important;
}
.visible-xs-block,
.visible-xs-inline,
.visible-xs-inline-block,
.visible-sm-block,
.visible-sm-inline,
.visible-sm-inline-block,
.visible-md-block,
.visible-md-inline,
.visible-md-inline-block,
.visible-lg-block,
.visible-lg-inline,
.visible-lg-inline-block {
  display: none !important;
}
@media (max-width: 767px) {
  .visible-xs {
    display: block !important;
  }
  table.visible-xs {
    display: table !important;
  }
  tr.visible-xs {
    display: table-row !important;
  }
  th.visible-xs,
  td.visible-xs {
    display: table-cell !important;
  }
}
@media (max-width: 767px) {
  .visible-xs-block {
    display: block !important;
  }
}
@media (max-width: 767px) {
  .visible-xs-inline {
    display: inline !important;
  }
}
@media (max-width: 767px) {
  .visible-xs-inline-block {
    display: inline-block !important;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .visible-sm {
    display: block !important;
  }
  table.visible-sm {
    display: table !important;
  }
  tr.visible-sm {
    display: table-row !important;
  }
  th.visible-sm,
  td.visible-sm {
    display: table-cell !important;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .visible-sm-block {
    display: block !important;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .visible-sm-inline {
    display: inline !important;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .visible-sm-inline-block {
    display: inline-block !important;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .visible-md {
    display: block !important;
  }
  table.visible-md {
    display: table !important;
  }
  tr.visible-md {
    display: table-row !important;
  }
  th.visible-md,
  td.visible-md {
    display: table-cell !important;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .visible-md-block {
    display: block !important;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .visible-md-inline {
    display: inline !important;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .visible-md-inline-block {
    display: inline-block !important;
  }
}
@media (min-width: 1200px) {
  .visible-lg {
    display: block !important;
  }
  table.visible-lg {
    display: table !important;
  }
  tr.visible-lg {
    display: table-row !important;
  }
  th.visible-lg,
  td.visible-lg {
    display: table-cell !important;
  }
}
@media (min-width: 1200px) {
  .visible-lg-block {
    display: block !important;
  }
}
@media (min-width: 1200px) {
  .visible-lg-inline {
    display: inline !important;
  }
}
@media (min-width: 1200px) {
  .visible-lg-inline-block {
    display: inline-block !important;
  }
}
@media (max-width: 767px) {
  .hidden-xs {
    display: none !important;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  .hidden-sm {
    display: none !important;
  }
}
@media (min-width: 992px) and (max-width: 1199px) {
  .hidden-md {
    display: none !important;
  }
}
@media (min-width: 1200px) {
  .hidden-lg {
    display: none !important;
  }
}
.visible-print {
  display: none !important;
}
@media print {
  .visible-print {
    display: block !important;
  }
  table.visible-print {
    display: table !important;
  }
  tr.visible-print {
    display: table-row !important;
  }
  th.visible-print,
  td.visible-print {
    display: table-cell !important;
  }
}
.visible-print-block {
  display: none !important;
}
@media print {
  .visible-print-block {
    display: block !important;
  }
}
.visible-print-inline {
  display: none !important;
}
@media print {
  .visible-print-inline {
    display: inline !important;
  }
}
.visible-print-inline-block {
  display: none !important;
}
@media print {
  .visible-print-inline-block {
    display: inline-block !important;
  }
}
@media print {
  .hidden-print {
    display: none !important;
  }
}
/*!
*
* Font Awesome
*
*/
/*!
 *  Font Awesome 4.7.0 by @davegandy - http://fontawesome.io - @fontawesome
 *  License - http://fontawesome.io/license (Font: SIL OFL 1.1, CSS: MIT License)
 */
/* FONT PATH
 * -------------------------- */
@font-face {
  font-family: 'FontAwesome';
  src: url('../components/font-awesome/fonts/fontawesome-webfont.eot?v=4.7.0');
  src: url('../components/font-awesome/fonts/fontawesome-webfont.eot?#iefix&v=4.7.0') format('embedded-opentype'), url('../components/font-awesome/fonts/fontawesome-webfont.woff2?v=4.7.0') format('woff2'), url('../components/font-awesome/fonts/fontawesome-webfont.woff?v=4.7.0') format('woff'), url('../components/font-awesome/fonts/fontawesome-webfont.ttf?v=4.7.0') format('truetype'), url('../components/font-awesome/fonts/fontawesome-webfont.svg?v=4.7.0#fontawesomeregular') format('svg');
  font-weight: normal;
  font-style: normal;
}
.fa {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
/* makes the font 33% larger relative to the icon container */
.fa-lg {
  font-size: 1.33333333em;
  line-height: 0.75em;
  vertical-align: -15%;
}
.fa-2x {
  font-size: 2em;
}
.fa-3x {
  font-size: 3em;
}
.fa-4x {
  font-size: 4em;
}
.fa-5x {
  font-size: 5em;
}
.fa-fw {
  width: 1.28571429em;
  text-align: center;
}
.fa-ul {
  padding-left: 0;
  margin-left: 2.14285714em;
  list-style-type: none;
}
.fa-ul > li {
  position: relative;
}
.fa-li {
  position: absolute;
  left: -2.14285714em;
  width: 2.14285714em;
  top: 0.14285714em;
  text-align: center;
}
.fa-li.fa-lg {
  left: -1.85714286em;
}
.fa-border {
  padding: .2em .25em .15em;
  border: solid 0.08em #eee;
  border-radius: .1em;
}
.fa-pull-left {
  float: left;
}
.fa-pull-right {
  float: right;
}
.fa.fa-pull-left {
  margin-right: .3em;
}
.fa.fa-pull-right {
  margin-left: .3em;
}
/* Deprecated as of 4.4.0 */
.pull-right {
  float: right;
}
.pull-left {
  float: left;
}
.fa.pull-left {
  margin-right: .3em;
}
.fa.pull-right {
  margin-left: .3em;
}
.fa-spin {
  -webkit-animation: fa-spin 2s infinite linear;
  animation: fa-spin 2s infinite linear;
}
.fa-pulse {
  -webkit-animation: fa-spin 1s infinite steps(8);
  animation: fa-spin 1s infinite steps(8);
}
@-webkit-keyframes fa-spin {
  0% {
    -webkit-transform: rotate(0deg);
    transform: rotate(0deg);
  }
  100% {
    -webkit-transform: rotate(359deg);
    transform: rotate(359deg);
  }
}
@keyframes fa-spin {
  0% {
    -webkit-transform: rotate(0deg);
    transform: rotate(0deg);
  }
  100% {
    -webkit-transform: rotate(359deg);
    transform: rotate(359deg);
  }
}
.fa-rotate-90 {
  -ms-filter: "progid:DXImageTransform.Microsoft.BasicImage(rotation=1)";
  -webkit-transform: rotate(90deg);
  -ms-transform: rotate(90deg);
  transform: rotate(90deg);
}
.fa-rotate-180 {
  -ms-filter: "progid:DXImageTransform.Microsoft.BasicImage(rotation=2)";
  -webkit-transform: rotate(180deg);
  -ms-transform: rotate(180deg);
  transform: rotate(180deg);
}
.fa-rotate-270 {
  -ms-filter: "progid:DXImageTransform.Microsoft.BasicImage(rotation=3)";
  -webkit-transform: rotate(270deg);
  -ms-transform: rotate(270deg);
  transform: rotate(270deg);
}
.fa-flip-horizontal {
  -ms-filter: "progid:DXImageTransform.Microsoft.BasicImage(rotation=0, mirror=1)";
  -webkit-transform: scale(-1, 1);
  -ms-transform: scale(-1, 1);
  transform: scale(-1, 1);
}
.fa-flip-vertical {
  -ms-filter: "progid:DXImageTransform.Microsoft.BasicImage(rotation=2, mirror=1)";
  -webkit-transform: scale(1, -1);
  -ms-transform: scale(1, -1);
  transform: scale(1, -1);
}
:root .fa-rotate-90,
:root .fa-rotate-180,
:root .fa-rotate-270,
:root .fa-flip-horizontal,
:root .fa-flip-vertical {
  filter: none;
}
.fa-stack {
  position: relative;
  display: inline-block;
  width: 2em;
  height: 2em;
  line-height: 2em;
  vertical-align: middle;
}
.fa-stack-1x,
.fa-stack-2x {
  position: absolute;
  left: 0;
  width: 100%;
  text-align: center;
}
.fa-stack-1x {
  line-height: inherit;
}
.fa-stack-2x {
  font-size: 2em;
}
.fa-inverse {
  color: #fff;
}
/* Font Awesome uses the Unicode Private Use Area (PUA) to ensure screen
   readers do not read off random characters that represent icons */
.fa-glass:before {
  content: "\f000";
}
.fa-music:before {
  content: "\f001";
}
.fa-search:before {
  content: "\f002";
}
.fa-envelope-o:before {
  content: "\f003";
}
.fa-heart:before {
  content: "\f004";
}
.fa-star:before {
  content: "\f005";
}
.fa-star-o:before {
  content: "\f006";
}
.fa-user:before {
  content: "\f007";
}
.fa-film:before {
  content: "\f008";
}
.fa-th-large:before {
  content: "\f009";
}
.fa-th:before {
  content: "\f00a";
}
.fa-th-list:before {
  content: "\f00b";
}
.fa-check:before {
  content: "\f00c";
}
.fa-remove:before,
.fa-close:before,
.fa-times:before {
  content: "\f00d";
}
.fa-search-plus:before {
  content: "\f00e";
}
.fa-search-minus:before {
  content: "\f010";
}
.fa-power-off:before {
  content: "\f011";
}
.fa-signal:before {
  content: "\f012";
}
.fa-gear:before,
.fa-cog:before {
  content: "\f013";
}
.fa-trash-o:before {
  content: "\f014";
}
.fa-home:before {
  content: "\f015";
}
.fa-file-o:before {
  content: "\f016";
}
.fa-clock-o:before {
  content: "\f017";
}
.fa-road:before {
  content: "\f018";
}
.fa-download:before {
  content: "\f019";
}
.fa-arrow-circle-o-down:before {
  content: "\f01a";
}
.fa-arrow-circle-o-up:before {
  content: "\f01b";
}
.fa-inbox:before {
  content: "\f01c";
}
.fa-play-circle-o:before {
  content: "\f01d";
}
.fa-rotate-right:before,
.fa-repeat:before {
  content: "\f01e";
}
.fa-refresh:before {
  content: "\f021";
}
.fa-list-alt:before {
  content: "\f022";
}
.fa-lock:before {
  content: "\f023";
}
.fa-flag:before {
  content: "\f024";
}
.fa-headphones:before {
  content: "\f025";
}
.fa-volume-off:before {
  content: "\f026";
}
.fa-volume-down:before {
  content: "\f027";
}
.fa-volume-up:before {
  content: "\f028";
}
.fa-qrcode:before {
  content: "\f029";
}
.fa-barcode:before {
  content: "\f02a";
}
.fa-tag:before {
  content: "\f02b";
}
.fa-tags:before {
  content: "\f02c";
}
.fa-book:before {
  content: "\f02d";
}
.fa-bookmark:before {
  content: "\f02e";
}
.fa-print:before {
  content: "\f02f";
}
.fa-camera:before {
  content: "\f030";
}
.fa-font:before {
  content: "\f031";
}
.fa-bold:before {
  content: "\f032";
}
.fa-italic:before {
  content: "\f033";
}
.fa-text-height:before {
  content: "\f034";
}
.fa-text-width:before {
  content: "\f035";
}
.fa-align-left:before {
  content: "\f036";
}
.fa-align-center:before {
  content: "\f037";
}
.fa-align-right:before {
  content: "\f038";
}
.fa-align-justify:before {
  content: "\f039";
}
.fa-list:before {
  content: "\f03a";
}
.fa-dedent:before,
.fa-outdent:before {
  content: "\f03b";
}
.fa-indent:before {
  content: "\f03c";
}
.fa-video-camera:before {
  content: "\f03d";
}
.fa-photo:before,
.fa-image:before,
.fa-picture-o:before {
  content: "\f03e";
}
.fa-pencil:before {
  content: "\f040";
}
.fa-map-marker:before {
  content: "\f041";
}
.fa-adjust:before {
  content: "\f042";
}
.fa-tint:before {
  content: "\f043";
}
.fa-edit:before,
.fa-pencil-square-o:before {
  content: "\f044";
}
.fa-share-square-o:before {
  content: "\f045";
}
.fa-check-square-o:before {
  content: "\f046";
}
.fa-arrows:before {
  content: "\f047";
}
.fa-step-backward:before {
  content: "\f048";
}
.fa-fast-backward:before {
  content: "\f049";
}
.fa-backward:before {
  content: "\f04a";
}
.fa-play:before {
  content: "\f04b";
}
.fa-pause:before {
  content: "\f04c";
}
.fa-stop:before {
  content: "\f04d";
}
.fa-forward:before {
  content: "\f04e";
}
.fa-fast-forward:before {
  content: "\f050";
}
.fa-step-forward:before {
  content: "\f051";
}
.fa-eject:before {
  content: "\f052";
}
.fa-chevron-left:before {
  content: "\f053";
}
.fa-chevron-right:before {
  content: "\f054";
}
.fa-plus-circle:before {
  content: "\f055";
}
.fa-minus-circle:before {
  content: "\f056";
}
.fa-times-circle:before {
  content: "\f057";
}
.fa-check-circle:before {
  content: "\f058";
}
.fa-question-circle:before {
  content: "\f059";
}
.fa-info-circle:before {
  content: "\f05a";
}
.fa-crosshairs:before {
  content: "\f05b";
}
.fa-times-circle-o:before {
  content: "\f05c";
}
.fa-check-circle-o:before {
  content: "\f05d";
}
.fa-ban:before {
  content: "\f05e";
}
.fa-arrow-left:before {
  content: "\f060";
}
.fa-arrow-right:before {
  content: "\f061";
}
.fa-arrow-up:before {
  content: "\f062";
}
.fa-arrow-down:before {
  content: "\f063";
}
.fa-mail-forward:before,
.fa-share:before {
  content: "\f064";
}
.fa-expand:before {
  content: "\f065";
}
.fa-compress:before {
  content: "\f066";
}
.fa-plus:before {
  content: "\f067";
}
.fa-minus:before {
  content: "\f068";
}
.fa-asterisk:before {
  content: "\f069";
}
.fa-exclamation-circle:before {
  content: "\f06a";
}
.fa-gift:before {
  content: "\f06b";
}
.fa-leaf:before {
  content: "\f06c";
}
.fa-fire:before {
  content: "\f06d";
}
.fa-eye:before {
  content: "\f06e";
}
.fa-eye-slash:before {
  content: "\f070";
}
.fa-warning:before,
.fa-exclamation-triangle:before {
  content: "\f071";
}
.fa-plane:before {
  content: "\f072";
}
.fa-calendar:before {
  content: "\f073";
}
.fa-random:before {
  content: "\f074";
}
.fa-comment:before {
  content: "\f075";
}
.fa-magnet:before {
  content: "\f076";
}
.fa-chevron-up:before {
  content: "\f077";
}
.fa-chevron-down:before {
  content: "\f078";
}
.fa-retweet:before {
  content: "\f079";
}
.fa-shopping-cart:before {
  content: "\f07a";
}
.fa-folder:before {
  content: "\f07b";
}
.fa-folder-open:before {
  content: "\f07c";
}
.fa-arrows-v:before {
  content: "\f07d";
}
.fa-arrows-h:before {
  content: "\f07e";
}
.fa-bar-chart-o:before,
.fa-bar-chart:before {
  content: "\f080";
}
.fa-twitter-square:before {
  content: "\f081";
}
.fa-facebook-square:before {
  content: "\f082";
}
.fa-camera-retro:before {
  content: "\f083";
}
.fa-key:before {
  content: "\f084";
}
.fa-gears:before,
.fa-cogs:before {
  content: "\f085";
}
.fa-comments:before {
  content: "\f086";
}
.fa-thumbs-o-up:before {
  content: "\f087";
}
.fa-thumbs-o-down:before {
  content: "\f088";
}
.fa-star-half:before {
  content: "\f089";
}
.fa-heart-o:before {
  content: "\f08a";
}
.fa-sign-out:before {
  content: "\f08b";
}
.fa-linkedin-square:before {
  content: "\f08c";
}
.fa-thumb-tack:before {
  content: "\f08d";
}
.fa-external-link:before {
  content: "\f08e";
}
.fa-sign-in:before {
  content: "\f090";
}
.fa-trophy:before {
  content: "\f091";
}
.fa-github-square:before {
  content: "\f092";
}
.fa-upload:before {
  content: "\f093";
}
.fa-lemon-o:before {
  content: "\f094";
}
.fa-phone:before {
  content: "\f095";
}
.fa-square-o:before {
  content: "\f096";
}
.fa-bookmark-o:before {
  content: "\f097";
}
.fa-phone-square:before {
  content: "\f098";
}
.fa-twitter:before {
  content: "\f099";
}
.fa-facebook-f:before,
.fa-facebook:before {
  content: "\f09a";
}
.fa-github:before {
  content: "\f09b";
}
.fa-unlock:before {
  content: "\f09c";
}
.fa-credit-card:before {
  content: "\f09d";
}
.fa-feed:before,
.fa-rss:before {
  content: "\f09e";
}
.fa-hdd-o:before {
  content: "\f0a0";
}
.fa-bullhorn:before {
  content: "\f0a1";
}
.fa-bell:before {
  content: "\f0f3";
}
.fa-certificate:before {
  content: "\f0a3";
}
.fa-hand-o-right:before {
  content: "\f0a4";
}
.fa-hand-o-left:before {
  content: "\f0a5";
}
.fa-hand-o-up:before {
  content: "\f0a6";
}
.fa-hand-o-down:before {
  content: "\f0a7";
}
.fa-arrow-circle-left:before {
  content: "\f0a8";
}
.fa-arrow-circle-right:before {
  content: "\f0a9";
}
.fa-arrow-circle-up:before {
  content: "\f0aa";
}
.fa-arrow-circle-down:before {
  content: "\f0ab";
}
.fa-globe:before {
  content: "\f0ac";
}
.fa-wrench:before {
  content: "\f0ad";
}
.fa-tasks:before {
  content: "\f0ae";
}
.fa-filter:before {
  content: "\f0b0";
}
.fa-briefcase:before {
  content: "\f0b1";
}
.fa-arrows-alt:before {
  content: "\f0b2";
}
.fa-group:before,
.fa-users:before {
  content: "\f0c0";
}
.fa-chain:before,
.fa-link:before {
  content: "\f0c1";
}
.fa-cloud:before {
  content: "\f0c2";
}
.fa-flask:before {
  content: "\f0c3";
}
.fa-cut:before,
.fa-scissors:before {
  content: "\f0c4";
}
.fa-copy:before,
.fa-files-o:before {
  content: "\f0c5";
}
.fa-paperclip:before {
  content: "\f0c6";
}
.fa-save:before,
.fa-floppy-o:before {
  content: "\f0c7";
}
.fa-square:before {
  content: "\f0c8";
}
.fa-navicon:before,
.fa-reorder:before,
.fa-bars:before {
  content: "\f0c9";
}
.fa-list-ul:before {
  content: "\f0ca";
}
.fa-list-ol:before {
  content: "\f0cb";
}
.fa-strikethrough:before {
  content: "\f0cc";
}
.fa-underline:before {
  content: "\f0cd";
}
.fa-table:before {
  content: "\f0ce";
}
.fa-magic:before {
  content: "\f0d0";
}
.fa-truck:before {
  content: "\f0d1";
}
.fa-pinterest:before {
  content: "\f0d2";
}
.fa-pinterest-square:before {
  content: "\f0d3";
}
.fa-google-plus-square:before {
  content: "\f0d4";
}
.fa-google-plus:before {
  content: "\f0d5";
}
.fa-money:before {
  content: "\f0d6";
}
.fa-caret-down:before {
  content: "\f0d7";
}
.fa-caret-up:before {
  content: "\f0d8";
}
.fa-caret-left:before {
  content: "\f0d9";
}
.fa-caret-right:before {
  content: "\f0da";
}
.fa-columns:before {
  content: "\f0db";
}
.fa-unsorted:before,
.fa-sort:before {
  content: "\f0dc";
}
.fa-sort-down:before,
.fa-sort-desc:before {
  content: "\f0dd";
}
.fa-sort-up:before,
.fa-sort-asc:before {
  content: "\f0de";
}
.fa-envelope:before {
  content: "\f0e0";
}
.fa-linkedin:before {
  content: "\f0e1";
}
.fa-rotate-left:before,
.fa-undo:before {
  content: "\f0e2";
}
.fa-legal:before,
.fa-gavel:before {
  content: "\f0e3";
}
.fa-dashboard:before,
.fa-tachometer:before {
  content: "\f0e4";
}
.fa-comment-o:before {
  content: "\f0e5";
}
.fa-comments-o:before {
  content: "\f0e6";
}
.fa-flash:before,
.fa-bolt:before {
  content: "\f0e7";
}
.fa-sitemap:before {
  content: "\f0e8";
}
.fa-umbrella:before {
  content: "\f0e9";
}
.fa-paste:before,
.fa-clipboard:before {
  content: "\f0ea";
}
.fa-lightbulb-o:before {
  content: "\f0eb";
}
.fa-exchange:before {
  content: "\f0ec";
}
.fa-cloud-download:before {
  content: "\f0ed";
}
.fa-cloud-upload:before {
  content: "\f0ee";
}
.fa-user-md:before {
  content: "\f0f0";
}
.fa-stethoscope:before {
  content: "\f0f1";
}
.fa-suitcase:before {
  content: "\f0f2";
}
.fa-bell-o:before {
  content: "\f0a2";
}
.fa-coffee:before {
  content: "\f0f4";
}
.fa-cutlery:before {
  content: "\f0f5";
}
.fa-file-text-o:before {
  content: "\f0f6";
}
.fa-building-o:before {
  content: "\f0f7";
}
.fa-hospital-o:before {
  content: "\f0f8";
}
.fa-ambulance:before {
  content: "\f0f9";
}
.fa-medkit:before {
  content: "\f0fa";
}
.fa-fighter-jet:before {
  content: "\f0fb";
}
.fa-beer:before {
  content: "\f0fc";
}
.fa-h-square:before {
  content: "\f0fd";
}
.fa-plus-square:before {
  content: "\f0fe";
}
.fa-angle-double-left:before {
  content: "\f100";
}
.fa-angle-double-right:before {
  content: "\f101";
}
.fa-angle-double-up:before {
  content: "\f102";
}
.fa-angle-double-down:before {
  content: "\f103";
}
.fa-angle-left:before {
  content: "\f104";
}
.fa-angle-right:before {
  content: "\f105";
}
.fa-angle-up:before {
  content: "\f106";
}
.fa-angle-down:before {
  content: "\f107";
}
.fa-desktop:before {
  content: "\f108";
}
.fa-laptop:before {
  content: "\f109";
}
.fa-tablet:before {
  content: "\f10a";
}
.fa-mobile-phone:before,
.fa-mobile:before {
  content: "\f10b";
}
.fa-circle-o:before {
  content: "\f10c";
}
.fa-quote-left:before {
  content: "\f10d";
}
.fa-quote-right:before {
  content: "\f10e";
}
.fa-spinner:before {
  content: "\f110";
}
.fa-circle:before {
  content: "\f111";
}
.fa-mail-reply:before,
.fa-reply:before {
  content: "\f112";
}
.fa-github-alt:before {
  content: "\f113";
}
.fa-folder-o:before {
  content: "\f114";
}
.fa-folder-open-o:before {
  content: "\f115";
}
.fa-smile-o:before {
  content: "\f118";
}
.fa-frown-o:before {
  content: "\f119";
}
.fa-meh-o:before {
  content: "\f11a";
}
.fa-gamepad:before {
  content: "\f11b";
}
.fa-keyboard-o:before {
  content: "\f11c";
}
.fa-flag-o:before {
  content: "\f11d";
}
.fa-flag-checkered:before {
  content: "\f11e";
}
.fa-terminal:before {
  content: "\f120";
}
.fa-code:before {
  content: "\f121";
}
.fa-mail-reply-all:before,
.fa-reply-all:before {
  content: "\f122";
}
.fa-star-half-empty:before,
.fa-star-half-full:before,
.fa-star-half-o:before {
  content: "\f123";
}
.fa-location-arrow:before {
  content: "\f124";
}
.fa-crop:before {
  content: "\f125";
}
.fa-code-fork:before {
  content: "\f126";
}
.fa-unlink:before,
.fa-chain-broken:before {
  content: "\f127";
}
.fa-question:before {
  content: "\f128";
}
.fa-info:before {
  content: "\f129";
}
.fa-exclamation:before {
  content: "\f12a";
}
.fa-superscript:before {
  content: "\f12b";
}
.fa-subscript:before {
  content: "\f12c";
}
.fa-eraser:before {
  content: "\f12d";
}
.fa-puzzle-piece:before {
  content: "\f12e";
}
.fa-microphone:before {
  content: "\f130";
}
.fa-microphone-slash:before {
  content: "\f131";
}
.fa-shield:before {
  content: "\f132";
}
.fa-calendar-o:before {
  content: "\f133";
}
.fa-fire-extinguisher:before {
  content: "\f134";
}
.fa-rocket:before {
  content: "\f135";
}
.fa-maxcdn:before {
  content: "\f136";
}
.fa-chevron-circle-left:before {
  content: "\f137";
}
.fa-chevron-circle-right:before {
  content: "\f138";
}
.fa-chevron-circle-up:before {
  content: "\f139";
}
.fa-chevron-circle-down:before {
  content: "\f13a";
}
.fa-html5:before {
  content: "\f13b";
}
.fa-css3:before {
  content: "\f13c";
}
.fa-anchor:before {
  content: "\f13d";
}
.fa-unlock-alt:before {
  content: "\f13e";
}
.fa-bullseye:before {
  content: "\f140";
}
.fa-ellipsis-h:before {
  content: "\f141";
}
.fa-ellipsis-v:before {
  content: "\f142";
}
.fa-rss-square:before {
  content: "\f143";
}
.fa-play-circle:before {
  content: "\f144";
}
.fa-ticket:before {
  content: "\f145";
}
.fa-minus-square:before {
  content: "\f146";
}
.fa-minus-square-o:before {
  content: "\f147";
}
.fa-level-up:before {
  content: "\f148";
}
.fa-level-down:before {
  content: "\f149";
}
.fa-check-square:before {
  content: "\f14a";
}
.fa-pencil-square:before {
  content: "\f14b";
}
.fa-external-link-square:before {
  content: "\f14c";
}
.fa-share-square:before {
  content: "\f14d";
}
.fa-compass:before {
  content: "\f14e";
}
.fa-toggle-down:before,
.fa-caret-square-o-down:before {
  content: "\f150";
}
.fa-toggle-up:before,
.fa-caret-square-o-up:before {
  content: "\f151";
}
.fa-toggle-right:before,
.fa-caret-square-o-right:before {
  content: "\f152";
}
.fa-euro:before,
.fa-eur:before {
  content: "\f153";
}
.fa-gbp:before {
  content: "\f154";
}
.fa-dollar:before,
.fa-usd:before {
  content: "\f155";
}
.fa-rupee:before,
.fa-inr:before {
  content: "\f156";
}
.fa-cny:before,
.fa-rmb:before,
.fa-yen:before,
.fa-jpy:before {
  content: "\f157";
}
.fa-ruble:before,
.fa-rouble:before,
.fa-rub:before {
  content: "\f158";
}
.fa-won:before,
.fa-krw:before {
  content: "\f159";
}
.fa-bitcoin:before,
.fa-btc:before {
  content: "\f15a";
}
.fa-file:before {
  content: "\f15b";
}
.fa-file-text:before {
  content: "\f15c";
}
.fa-sort-alpha-asc:before {
  content: "\f15d";
}
.fa-sort-alpha-desc:before {
  content: "\f15e";
}
.fa-sort-amount-asc:before {
  content: "\f160";
}
.fa-sort-amount-desc:before {
  content: "\f161";
}
.fa-sort-numeric-asc:before {
  content: "\f162";
}
.fa-sort-numeric-desc:before {
  content: "\f163";
}
.fa-thumbs-up:before {
  content: "\f164";
}
.fa-thumbs-down:before {
  content: "\f165";
}
.fa-youtube-square:before {
  content: "\f166";
}
.fa-youtube:before {
  content: "\f167";
}
.fa-xing:before {
  content: "\f168";
}
.fa-xing-square:before {
  content: "\f169";
}
.fa-youtube-play:before {
  content: "\f16a";
}
.fa-dropbox:before {
  content: "\f16b";
}
.fa-stack-overflow:before {
  content: "\f16c";
}
.fa-instagram:before {
  content: "\f16d";
}
.fa-flickr:before {
  content: "\f16e";
}
.fa-adn:before {
  content: "\f170";
}
.fa-bitbucket:before {
  content: "\f171";
}
.fa-bitbucket-square:before {
  content: "\f172";
}
.fa-tumblr:before {
  content: "\f173";
}
.fa-tumblr-square:before {
  content: "\f174";
}
.fa-long-arrow-down:before {
  content: "\f175";
}
.fa-long-arrow-up:before {
  content: "\f176";
}
.fa-long-arrow-left:before {
  content: "\f177";
}
.fa-long-arrow-right:before {
  content: "\f178";
}
.fa-apple:before {
  content: "\f179";
}
.fa-windows:before {
  content: "\f17a";
}
.fa-android:before {
  content: "\f17b";
}
.fa-linux:before {
  content: "\f17c";
}
.fa-dribbble:before {
  content: "\f17d";
}
.fa-skype:before {
  content: "\f17e";
}
.fa-foursquare:before {
  content: "\f180";
}
.fa-trello:before {
  content: "\f181";
}
.fa-female:before {
  content: "\f182";
}
.fa-male:before {
  content: "\f183";
}
.fa-gittip:before,
.fa-gratipay:before {
  content: "\f184";
}
.fa-sun-o:before {
  content: "\f185";
}
.fa-moon-o:before {
  content: "\f186";
}
.fa-archive:before {
  content: "\f187";
}
.fa-bug:before {
  content: "\f188";
}
.fa-vk:before {
  content: "\f189";
}
.fa-weibo:before {
  content: "\f18a";
}
.fa-renren:before {
  content: "\f18b";
}
.fa-pagelines:before {
  content: "\f18c";
}
.fa-stack-exchange:before {
  content: "\f18d";
}
.fa-arrow-circle-o-right:before {
  content: "\f18e";
}
.fa-arrow-circle-o-left:before {
  content: "\f190";
}
.fa-toggle-left:before,
.fa-caret-square-o-left:before {
  content: "\f191";
}
.fa-dot-circle-o:before {
  content: "\f192";
}
.fa-wheelchair:before {
  content: "\f193";
}
.fa-vimeo-square:before {
  content: "\f194";
}
.fa-turkish-lira:before,
.fa-try:before {
  content: "\f195";
}
.fa-plus-square-o:before {
  content: "\f196";
}
.fa-space-shuttle:before {
  content: "\f197";
}
.fa-slack:before {
  content: "\f198";
}
.fa-envelope-square:before {
  content: "\f199";
}
.fa-wordpress:before {
  content: "\f19a";
}
.fa-openid:before {
  content: "\f19b";
}
.fa-institution:before,
.fa-bank:before,
.fa-university:before {
  content: "\f19c";
}
.fa-mortar-board:before,
.fa-graduation-cap:before {
  content: "\f19d";
}
.fa-yahoo:before {
  content: "\f19e";
}
.fa-google:before {
  content: "\f1a0";
}
.fa-reddit:before {
  content: "\f1a1";
}
.fa-reddit-square:before {
  content: "\f1a2";
}
.fa-stumbleupon-circle:before {
  content: "\f1a3";
}
.fa-stumbleupon:before {
  content: "\f1a4";
}
.fa-delicious:before {
  content: "\f1a5";
}
.fa-digg:before {
  content: "\f1a6";
}
.fa-pied-piper-pp:before {
  content: "\f1a7";
}
.fa-pied-piper-alt:before {
  content: "\f1a8";
}
.fa-drupal:before {
  content: "\f1a9";
}
.fa-joomla:before {
  content: "\f1aa";
}
.fa-language:before {
  content: "\f1ab";
}
.fa-fax:before {
  content: "\f1ac";
}
.fa-building:before {
  content: "\f1ad";
}
.fa-child:before {
  content: "\f1ae";
}
.fa-paw:before {
  content: "\f1b0";
}
.fa-spoon:before {
  content: "\f1b1";
}
.fa-cube:before {
  content: "\f1b2";
}
.fa-cubes:before {
  content: "\f1b3";
}
.fa-behance:before {
  content: "\f1b4";
}
.fa-behance-square:before {
  content: "\f1b5";
}
.fa-steam:before {
  content: "\f1b6";
}
.fa-steam-square:before {
  content: "\f1b7";
}
.fa-recycle:before {
  content: "\f1b8";
}
.fa-automobile:before,
.fa-car:before {
  content: "\f1b9";
}
.fa-cab:before,
.fa-taxi:before {
  content: "\f1ba";
}
.fa-tree:before {
  content: "\f1bb";
}
.fa-spotify:before {
  content: "\f1bc";
}
.fa-deviantart:before {
  content: "\f1bd";
}
.fa-soundcloud:before {
  content: "\f1be";
}
.fa-database:before {
  content: "\f1c0";
}
.fa-file-pdf-o:before {
  content: "\f1c1";
}
.fa-file-word-o:before {
  content: "\f1c2";
}
.fa-file-excel-o:before {
  content: "\f1c3";
}
.fa-file-powerpoint-o:before {
  content: "\f1c4";
}
.fa-file-photo-o:before,
.fa-file-picture-o:before,
.fa-file-image-o:before {
  content: "\f1c5";
}
.fa-file-zip-o:before,
.fa-file-archive-o:before {
  content: "\f1c6";
}
.fa-file-sound-o:before,
.fa-file-audio-o:before {
  content: "\f1c7";
}
.fa-file-movie-o:before,
.fa-file-video-o:before {
  content: "\f1c8";
}
.fa-file-code-o:before {
  content: "\f1c9";
}
.fa-vine:before {
  content: "\f1ca";
}
.fa-codepen:before {
  content: "\f1cb";
}
.fa-jsfiddle:before {
  content: "\f1cc";
}
.fa-life-bouy:before,
.fa-life-buoy:before,
.fa-life-saver:before,
.fa-support:before,
.fa-life-ring:before {
  content: "\f1cd";
}
.fa-circle-o-notch:before {
  content: "\f1ce";
}
.fa-ra:before,
.fa-resistance:before,
.fa-rebel:before {
  content: "\f1d0";
}
.fa-ge:before,
.fa-empire:before {
  content: "\f1d1";
}
.fa-git-square:before {
  content: "\f1d2";
}
.fa-git:before {
  content: "\f1d3";
}
.fa-y-combinator-square:before,
.fa-yc-square:before,
.fa-hacker-news:before {
  content: "\f1d4";
}
.fa-tencent-weibo:before {
  content: "\f1d5";
}
.fa-qq:before {
  content: "\f1d6";
}
.fa-wechat:before,
.fa-weixin:before {
  content: "\f1d7";
}
.fa-send:before,
.fa-paper-plane:before {
  content: "\f1d8";
}
.fa-send-o:before,
.fa-paper-plane-o:before {
  content: "\f1d9";
}
.fa-history:before {
  content: "\f1da";
}
.fa-circle-thin:before {
  content: "\f1db";
}
.fa-header:before {
  content: "\f1dc";
}
.fa-paragraph:before {
  content: "\f1dd";
}
.fa-sliders:before {
  content: "\f1de";
}
.fa-share-alt:before {
  content: "\f1e0";
}
.fa-share-alt-square:before {
  content: "\f1e1";
}
.fa-bomb:before {
  content: "\f1e2";
}
.fa-soccer-ball-o:before,
.fa-futbol-o:before {
  content: "\f1e3";
}
.fa-tty:before {
  content: "\f1e4";
}
.fa-binoculars:before {
  content: "\f1e5";
}
.fa-plug:before {
  content: "\f1e6";
}
.fa-slideshare:before {
  content: "\f1e7";
}
.fa-twitch:before {
  content: "\f1e8";
}
.fa-yelp:before {
  content: "\f1e9";
}
.fa-newspaper-o:before {
  content: "\f1ea";
}
.fa-wifi:before {
  content: "\f1eb";
}
.fa-calculator:before {
  content: "\f1ec";
}
.fa-paypal:before {
  content: "\f1ed";
}
.fa-google-wallet:before {
  content: "\f1ee";
}
.fa-cc-visa:before {
  content: "\f1f0";
}
.fa-cc-mastercard:before {
  content: "\f1f1";
}
.fa-cc-discover:before {
  content: "\f1f2";
}
.fa-cc-amex:before {
  content: "\f1f3";
}
.fa-cc-paypal:before {
  content: "\f1f4";
}
.fa-cc-stripe:before {
  content: "\f1f5";
}
.fa-bell-slash:before {
  content: "\f1f6";
}
.fa-bell-slash-o:before {
  content: "\f1f7";
}
.fa-trash:before {
  content: "\f1f8";
}
.fa-copyright:before {
  content: "\f1f9";
}
.fa-at:before {
  content: "\f1fa";
}
.fa-eyedropper:before {
  content: "\f1fb";
}
.fa-paint-brush:before {
  content: "\f1fc";
}
.fa-birthday-cake:before {
  content: "\f1fd";
}
.fa-area-chart:before {
  content: "\f1fe";
}
.fa-pie-chart:before {
  content: "\f200";
}
.fa-line-chart:before {
  content: "\f201";
}
.fa-lastfm:before {
  content: "\f202";
}
.fa-lastfm-square:before {
  content: "\f203";
}
.fa-toggle-off:before {
  content: "\f204";
}
.fa-toggle-on:before {
  content: "\f205";
}
.fa-bicycle:before {
  content: "\f206";
}
.fa-bus:before {
  content: "\f207";
}
.fa-ioxhost:before {
  content: "\f208";
}
.fa-angellist:before {
  content: "\f209";
}
.fa-cc:before {
  content: "\f20a";
}
.fa-shekel:before,
.fa-sheqel:before,
.fa-ils:before {
  content: "\f20b";
}
.fa-meanpath:before {
  content: "\f20c";
}
.fa-buysellads:before {
  content: "\f20d";
}
.fa-connectdevelop:before {
  content: "\f20e";
}
.fa-dashcube:before {
  content: "\f210";
}
.fa-forumbee:before {
  content: "\f211";
}
.fa-leanpub:before {
  content: "\f212";
}
.fa-sellsy:before {
  content: "\f213";
}
.fa-shirtsinbulk:before {
  content: "\f214";
}
.fa-simplybuilt:before {
  content: "\f215";
}
.fa-skyatlas:before {
  content: "\f216";
}
.fa-cart-plus:before {
  content: "\f217";
}
.fa-cart-arrow-down:before {
  content: "\f218";
}
.fa-diamond:before {
  content: "\f219";
}
.fa-ship:before {
  content: "\f21a";
}
.fa-user-secret:before {
  content: "\f21b";
}
.fa-motorcycle:before {
  content: "\f21c";
}
.fa-street-view:before {
  content: "\f21d";
}
.fa-heartbeat:before {
  content: "\f21e";
}
.fa-venus:before {
  content: "\f221";
}
.fa-mars:before {
  content: "\f222";
}
.fa-mercury:before {
  content: "\f223";
}
.fa-intersex:before,
.fa-transgender:before {
  content: "\f224";
}
.fa-transgender-alt:before {
  content: "\f225";
}
.fa-venus-double:before {
  content: "\f226";
}
.fa-mars-double:before {
  content: "\f227";
}
.fa-venus-mars:before {
  content: "\f228";
}
.fa-mars-stroke:before {
  content: "\f229";
}
.fa-mars-stroke-v:before {
  content: "\f22a";
}
.fa-mars-stroke-h:before {
  content: "\f22b";
}
.fa-neuter:before {
  content: "\f22c";
}
.fa-genderless:before {
  content: "\f22d";
}
.fa-facebook-official:before {
  content: "\f230";
}
.fa-pinterest-p:before {
  content: "\f231";
}
.fa-whatsapp:before {
  content: "\f232";
}
.fa-server:before {
  content: "\f233";
}
.fa-user-plus:before {
  content: "\f234";
}
.fa-user-times:before {
  content: "\f235";
}
.fa-hotel:before,
.fa-bed:before {
  content: "\f236";
}
.fa-viacoin:before {
  content: "\f237";
}
.fa-train:before {
  content: "\f238";
}
.fa-subway:before {
  content: "\f239";
}
.fa-medium:before {
  content: "\f23a";
}
.fa-yc:before,
.fa-y-combinator:before {
  content: "\f23b";
}
.fa-optin-monster:before {
  content: "\f23c";
}
.fa-opencart:before {
  content: "\f23d";
}
.fa-expeditedssl:before {
  content: "\f23e";
}
.fa-battery-4:before,
.fa-battery:before,
.fa-battery-full:before {
  content: "\f240";
}
.fa-battery-3:before,
.fa-battery-three-quarters:before {
  content: "\f241";
}
.fa-battery-2:before,
.fa-battery-half:before {
  content: "\f242";
}
.fa-battery-1:before,
.fa-battery-quarter:before {
  content: "\f243";
}
.fa-battery-0:before,
.fa-battery-empty:before {
  content: "\f244";
}
.fa-mouse-pointer:before {
  content: "\f245";
}
.fa-i-cursor:before {
  content: "\f246";
}
.fa-object-group:before {
  content: "\f247";
}
.fa-object-ungroup:before {
  content: "\f248";
}
.fa-sticky-note:before {
  content: "\f249";
}
.fa-sticky-note-o:before {
  content: "\f24a";
}
.fa-cc-jcb:before {
  content: "\f24b";
}
.fa-cc-diners-club:before {
  content: "\f24c";
}
.fa-clone:before {
  content: "\f24d";
}
.fa-balance-scale:before {
  content: "\f24e";
}
.fa-hourglass-o:before {
  content: "\f250";
}
.fa-hourglass-1:before,
.fa-hourglass-start:before {
  content: "\f251";
}
.fa-hourglass-2:before,
.fa-hourglass-half:before {
  content: "\f252";
}
.fa-hourglass-3:before,
.fa-hourglass-end:before {
  content: "\f253";
}
.fa-hourglass:before {
  content: "\f254";
}
.fa-hand-grab-o:before,
.fa-hand-rock-o:before {
  content: "\f255";
}
.fa-hand-stop-o:before,
.fa-hand-paper-o:before {
  content: "\f256";
}
.fa-hand-scissors-o:before {
  content: "\f257";
}
.fa-hand-lizard-o:before {
  content: "\f258";
}
.fa-hand-spock-o:before {
  content: "\f259";
}
.fa-hand-pointer-o:before {
  content: "\f25a";
}
.fa-hand-peace-o:before {
  content: "\f25b";
}
.fa-trademark:before {
  content: "\f25c";
}
.fa-registered:before {
  content: "\f25d";
}
.fa-creative-commons:before {
  content: "\f25e";
}
.fa-gg:before {
  content: "\f260";
}
.fa-gg-circle:before {
  content: "\f261";
}
.fa-tripadvisor:before {
  content: "\f262";
}
.fa-odnoklassniki:before {
  content: "\f263";
}
.fa-odnoklassniki-square:before {
  content: "\f264";
}
.fa-get-pocket:before {
  content: "\f265";
}
.fa-wikipedia-w:before {
  content: "\f266";
}
.fa-safari:before {
  content: "\f267";
}
.fa-chrome:before {
  content: "\f268";
}
.fa-firefox:before {
  content: "\f269";
}
.fa-opera:before {
  content: "\f26a";
}
.fa-internet-explorer:before {
  content: "\f26b";
}
.fa-tv:before,
.fa-television:before {
  content: "\f26c";
}
.fa-contao:before {
  content: "\f26d";
}
.fa-500px:before {
  content: "\f26e";
}
.fa-amazon:before {
  content: "\f270";
}
.fa-calendar-plus-o:before {
  content: "\f271";
}
.fa-calendar-minus-o:before {
  content: "\f272";
}
.fa-calendar-times-o:before {
  content: "\f273";
}
.fa-calendar-check-o:before {
  content: "\f274";
}
.fa-industry:before {
  content: "\f275";
}
.fa-map-pin:before {
  content: "\f276";
}
.fa-map-signs:before {
  content: "\f277";
}
.fa-map-o:before {
  content: "\f278";
}
.fa-map:before {
  content: "\f279";
}
.fa-commenting:before {
  content: "\f27a";
}
.fa-commenting-o:before {
  content: "\f27b";
}
.fa-houzz:before {
  content: "\f27c";
}
.fa-vimeo:before {
  content: "\f27d";
}
.fa-black-tie:before {
  content: "\f27e";
}
.fa-fonticons:before {
  content: "\f280";
}
.fa-reddit-alien:before {
  content: "\f281";
}
.fa-edge:before {
  content: "\f282";
}
.fa-credit-card-alt:before {
  content: "\f283";
}
.fa-codiepie:before {
  content: "\f284";
}
.fa-modx:before {
  content: "\f285";
}
.fa-fort-awesome:before {
  content: "\f286";
}
.fa-usb:before {
  content: "\f287";
}
.fa-product-hunt:before {
  content: "\f288";
}
.fa-mixcloud:before {
  content: "\f289";
}
.fa-scribd:before {
  content: "\f28a";
}
.fa-pause-circle:before {
  content: "\f28b";
}
.fa-pause-circle-o:before {
  content: "\f28c";
}
.fa-stop-circle:before {
  content: "\f28d";
}
.fa-stop-circle-o:before {
  content: "\f28e";
}
.fa-shopping-bag:before {
  content: "\f290";
}
.fa-shopping-basket:before {
  content: "\f291";
}
.fa-hashtag:before {
  content: "\f292";
}
.fa-bluetooth:before {
  content: "\f293";
}
.fa-bluetooth-b:before {
  content: "\f294";
}
.fa-percent:before {
  content: "\f295";
}
.fa-gitlab:before {
  content: "\f296";
}
.fa-wpbeginner:before {
  content: "\f297";
}
.fa-wpforms:before {
  content: "\f298";
}
.fa-envira:before {
  content: "\f299";
}
.fa-universal-access:before {
  content: "\f29a";
}
.fa-wheelchair-alt:before {
  content: "\f29b";
}
.fa-question-circle-o:before {
  content: "\f29c";
}
.fa-blind:before {
  content: "\f29d";
}
.fa-audio-description:before {
  content: "\f29e";
}
.fa-volume-control-phone:before {
  content: "\f2a0";
}
.fa-braille:before {
  content: "\f2a1";
}
.fa-assistive-listening-systems:before {
  content: "\f2a2";
}
.fa-asl-interpreting:before,
.fa-american-sign-language-interpreting:before {
  content: "\f2a3";
}
.fa-deafness:before,
.fa-hard-of-hearing:before,
.fa-deaf:before {
  content: "\f2a4";
}
.fa-glide:before {
  content: "\f2a5";
}
.fa-glide-g:before {
  content: "\f2a6";
}
.fa-signing:before,
.fa-sign-language:before {
  content: "\f2a7";
}
.fa-low-vision:before {
  content: "\f2a8";
}
.fa-viadeo:before {
  content: "\f2a9";
}
.fa-viadeo-square:before {
  content: "\f2aa";
}
.fa-snapchat:before {
  content: "\f2ab";
}
.fa-snapchat-ghost:before {
  content: "\f2ac";
}
.fa-snapchat-square:before {
  content: "\f2ad";
}
.fa-pied-piper:before {
  content: "\f2ae";
}
.fa-first-order:before {
  content: "\f2b0";
}
.fa-yoast:before {
  content: "\f2b1";
}
.fa-themeisle:before {
  content: "\f2b2";
}
.fa-google-plus-circle:before,
.fa-google-plus-official:before {
  content: "\f2b3";
}
.fa-fa:before,
.fa-font-awesome:before {
  content: "\f2b4";
}
.fa-handshake-o:before {
  content: "\f2b5";
}
.fa-envelope-open:before {
  content: "\f2b6";
}
.fa-envelope-open-o:before {
  content: "\f2b7";
}
.fa-linode:before {
  content: "\f2b8";
}
.fa-address-book:before {
  content: "\f2b9";
}
.fa-address-book-o:before {
  content: "\f2ba";
}
.fa-vcard:before,
.fa-address-card:before {
  content: "\f2bb";
}
.fa-vcard-o:before,
.fa-address-card-o:before {
  content: "\f2bc";
}
.fa-user-circle:before {
  content: "\f2bd";
}
.fa-user-circle-o:before {
  content: "\f2be";
}
.fa-user-o:before {
  content: "\f2c0";
}
.fa-id-badge:before {
  content: "\f2c1";
}
.fa-drivers-license:before,
.fa-id-card:before {
  content: "\f2c2";
}
.fa-drivers-license-o:before,
.fa-id-card-o:before {
  content: "\f2c3";
}
.fa-quora:before {
  content: "\f2c4";
}
.fa-free-code-camp:before {
  content: "\f2c5";
}
.fa-telegram:before {
  content: "\f2c6";
}
.fa-thermometer-4:before,
.fa-thermometer:before,
.fa-thermometer-full:before {
  content: "\f2c7";
}
.fa-thermometer-3:before,
.fa-thermometer-three-quarters:before {
  content: "\f2c8";
}
.fa-thermometer-2:before,
.fa-thermometer-half:before {
  content: "\f2c9";
}
.fa-thermometer-1:before,
.fa-thermometer-quarter:before {
  content: "\f2ca";
}
.fa-thermometer-0:before,
.fa-thermometer-empty:before {
  content: "\f2cb";
}
.fa-shower:before {
  content: "\f2cc";
}
.fa-bathtub:before,
.fa-s15:before,
.fa-bath:before {
  content: "\f2cd";
}
.fa-podcast:before {
  content: "\f2ce";
}
.fa-window-maximize:before {
  content: "\f2d0";
}
.fa-window-minimize:before {
  content: "\f2d1";
}
.fa-window-restore:before {
  content: "\f2d2";
}
.fa-times-rectangle:before,
.fa-window-close:before {
  content: "\f2d3";
}
.fa-times-rectangle-o:before,
.fa-window-close-o:before {
  content: "\f2d4";
}
.fa-bandcamp:before {
  content: "\f2d5";
}
.fa-grav:before {
  content: "\f2d6";
}
.fa-etsy:before {
  content: "\f2d7";
}
.fa-imdb:before {
  content: "\f2d8";
}
.fa-ravelry:before {
  content: "\f2d9";
}
.fa-eercast:before {
  content: "\f2da";
}
.fa-microchip:before {
  content: "\f2db";
}
.fa-snowflake-o:before {
  content: "\f2dc";
}
.fa-superpowers:before {
  content: "\f2dd";
}
.fa-wpexplorer:before {
  content: "\f2de";
}
.fa-meetup:before {
  content: "\f2e0";
}
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  border: 0;
}
.sr-only-focusable:active,
.sr-only-focusable:focus {
  position: static;
  width: auto;
  height: auto;
  margin: 0;
  overflow: visible;
  clip: auto;
}
.sr-only-focusable:active,
.sr-only-focusable:focus {
  position: static;
  width: auto;
  height: auto;
  margin: 0;
  overflow: visible;
  clip: auto;
}
/*!
*
* IPython base
*
*/
.modal.fade .modal-dialog {
  -webkit-transform: translate(0, 0);
  -ms-transform: translate(0, 0);
  -o-transform: translate(0, 0);
  transform: translate(0, 0);
}
code {
  color: #000;
}
pre {
  font-size: inherit;
  line-height: inherit;
}
label {
  font-weight: normal;
}
/* Make the page background atleast 100% the height of the view port */
/* Make the page itself atleast 70% the height of the view port */
.border-box-sizing {
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
.corner-all {
  border-radius: 2px;
}
.no-padding {
  padding: 0px;
}
/* Flexible box model classes */
/* Taken from Alex Russell http://infrequently.org/2009/08/css-3-progress/ */
/* This file is a compatability layer.  It allows the usage of flexible box 
model layouts accross multiple browsers, including older browsers.  The newest,
universal implementation of the flexible box model is used when available (see
`Modern browsers` comments below).  Browsers that are known to implement this 
new spec completely include:

    Firefox 28.0+
    Chrome 29.0+
    Internet Explorer 11+ 
    Opera 17.0+

Browsers not listed, including Safari, are supported via the styling under the
`Old browsers` comments below.
*/
.hbox {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
.hbox > * {
  /* Old browsers */
  -webkit-box-flex: 0;
  -moz-box-flex: 0;
  box-flex: 0;
  /* Modern browsers */
  flex: none;
}
.vbox {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
}
.vbox > * {
  /* Old browsers */
  -webkit-box-flex: 0;
  -moz-box-flex: 0;
  box-flex: 0;
  /* Modern browsers */
  flex: none;
}
.hbox.reverse,
.vbox.reverse,
.reverse {
  /* Old browsers */
  -webkit-box-direction: reverse;
  -moz-box-direction: reverse;
  box-direction: reverse;
  /* Modern browsers */
  flex-direction: row-reverse;
}
.hbox.box-flex0,
.vbox.box-flex0,
.box-flex0 {
  /* Old browsers */
  -webkit-box-flex: 0;
  -moz-box-flex: 0;
  box-flex: 0;
  /* Modern browsers */
  flex: none;
  width: auto;
}
.hbox.box-flex1,
.vbox.box-flex1,
.box-flex1 {
  /* Old browsers */
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  box-flex: 1;
  /* Modern browsers */
  flex: 1;
}
.hbox.box-flex,
.vbox.box-flex,
.box-flex {
  /* Old browsers */
  /* Old browsers */
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  box-flex: 1;
  /* Modern browsers */
  flex: 1;
}
.hbox.box-flex2,
.vbox.box-flex2,
.box-flex2 {
  /* Old browsers */
  -webkit-box-flex: 2;
  -moz-box-flex: 2;
  box-flex: 2;
  /* Modern browsers */
  flex: 2;
}
.box-group1 {
  /*  Deprecated */
  -webkit-box-flex-group: 1;
  -moz-box-flex-group: 1;
  box-flex-group: 1;
}
.box-group2 {
  /* Deprecated */
  -webkit-box-flex-group: 2;
  -moz-box-flex-group: 2;
  box-flex-group: 2;
}
.hbox.start,
.vbox.start,
.start {
  /* Old browsers */
  -webkit-box-pack: start;
  -moz-box-pack: start;
  box-pack: start;
  /* Modern browsers */
  justify-content: flex-start;
}
.hbox.end,
.vbox.end,
.end {
  /* Old browsers */
  -webkit-box-pack: end;
  -moz-box-pack: end;
  box-pack: end;
  /* Modern browsers */
  justify-content: flex-end;
}
.hbox.center,
.vbox.center,
.center {
  /* Old browsers */
  -webkit-box-pack: center;
  -moz-box-pack: center;
  box-pack: center;
  /* Modern browsers */
  justify-content: center;
}
.hbox.baseline,
.vbox.baseline,
.baseline {
  /* Old browsers */
  -webkit-box-pack: baseline;
  -moz-box-pack: baseline;
  box-pack: baseline;
  /* Modern browsers */
  justify-content: baseline;
}
.hbox.stretch,
.vbox.stretch,
.stretch {
  /* Old browsers */
  -webkit-box-pack: stretch;
  -moz-box-pack: stretch;
  box-pack: stretch;
  /* Modern browsers */
  justify-content: stretch;
}
.hbox.align-start,
.vbox.align-start,
.align-start {
  /* Old browsers */
  -webkit-box-align: start;
  -moz-box-align: start;
  box-align: start;
  /* Modern browsers */
  align-items: flex-start;
}
.hbox.align-end,
.vbox.align-end,
.align-end {
  /* Old browsers */
  -webkit-box-align: end;
  -moz-box-align: end;
  box-align: end;
  /* Modern browsers */
  align-items: flex-end;
}
.hbox.align-center,
.vbox.align-center,
.align-center {
  /* Old browsers */
  -webkit-box-align: center;
  -moz-box-align: center;
  box-align: center;
  /* Modern browsers */
  align-items: center;
}
.hbox.align-baseline,
.vbox.align-baseline,
.align-baseline {
  /* Old browsers */
  -webkit-box-align: baseline;
  -moz-box-align: baseline;
  box-align: baseline;
  /* Modern browsers */
  align-items: baseline;
}
.hbox.align-stretch,
.vbox.align-stretch,
.align-stretch {
  /* Old browsers */
  -webkit-box-align: stretch;
  -moz-box-align: stretch;
  box-align: stretch;
  /* Modern browsers */
  align-items: stretch;
}
div.error {
  margin: 2em;
  text-align: center;
}
div.error > h1 {
  font-size: 500%;
  line-height: normal;
}
div.error > p {
  font-size: 200%;
  line-height: normal;
}
div.traceback-wrapper {
  text-align: left;
  max-width: 800px;
  margin: auto;
}
div.traceback-wrapper pre.traceback {
  max-height: 600px;
  overflow: auto;
}
/**
 * Primary styles
 *
 * Author: Jupyter Development Team
 */
body {
  background-color: #fff;
  /* This makes sure that the body covers the entire window and needs to
       be in a different element than the display: box in wrapper below */
  position: absolute;
  left: 0px;
  right: 0px;
  top: 0px;
  bottom: 0px;
  overflow: visible;
}
body > #header {
  /* Initially hidden to prevent FLOUC */
  display: none;
  background-color: #fff;
  /* Display over codemirror */
  position: relative;
  z-index: 100;
}
body > #header #header-container {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  padding: 5px;
  padding-bottom: 5px;
  padding-top: 5px;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
body > #header .header-bar {
  width: 100%;
  height: 1px;
  background: #e7e7e7;
  margin-bottom: -1px;
}
@media print {
  body > #header {
    display: none !important;
  }
}
#header-spacer {
  width: 100%;
  visibility: hidden;
}
@media print {
  #header-spacer {
    display: none;
  }
}
#ipython_notebook {
  padding-left: 0px;
  padding-top: 1px;
  padding-bottom: 1px;
}
[dir="rtl"] #ipython_notebook {
  margin-right: 10px;
  margin-left: 0;
}
[dir="rtl"] #ipython_notebook.pull-left {
  float: right !important;
  float: right;
}
.flex-spacer {
  flex: 1;
}
#noscript {
  width: auto;
  padding-top: 16px;
  padding-bottom: 16px;
  text-align: center;
  font-size: 22px;
  color: red;
  font-weight: bold;
}
#ipython_notebook img {
  height: 28px;
}
#site {
  width: 100%;
  display: none;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  overflow: auto;
}
@media print {
  #site {
    height: auto !important;
  }
}
/* Smaller buttons */
.ui-button .ui-button-text {
  padding: 0.2em 0.8em;
  font-size: 77%;
}
input.ui-button {
  padding: 0.3em 0.9em;
}
span#kernel_logo_widget {
  margin: 0 10px;
}
span#login_widget {
  float: right;
}
[dir="rtl"] span#login_widget {
  float: left;
}
span#login_widget > .button,
#logout {
  color: #333;
  background-color: #fff;
  border-color: #ccc;
}
span#login_widget > .button:focus,
#logout:focus,
span#login_widget > .button.focus,
#logout.focus {
  color: #333;
  background-color: #e6e6e6;
  border-color: #8c8c8c;
}
span#login_widget > .button:hover,
#logout:hover {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
span#login_widget > .button:active,
#logout:active,
span#login_widget > .button.active,
#logout.active,
.open > .dropdown-togglespan#login_widget > .button,
.open > .dropdown-toggle#logout {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
span#login_widget > .button:active:hover,
#logout:active:hover,
span#login_widget > .button.active:hover,
#logout.active:hover,
.open > .dropdown-togglespan#login_widget > .button:hover,
.open > .dropdown-toggle#logout:hover,
span#login_widget > .button:active:focus,
#logout:active:focus,
span#login_widget > .button.active:focus,
#logout.active:focus,
.open > .dropdown-togglespan#login_widget > .button:focus,
.open > .dropdown-toggle#logout:focus,
span#login_widget > .button:active.focus,
#logout:active.focus,
span#login_widget > .button.active.focus,
#logout.active.focus,
.open > .dropdown-togglespan#login_widget > .button.focus,
.open > .dropdown-toggle#logout.focus {
  color: #333;
  background-color: #d4d4d4;
  border-color: #8c8c8c;
}
span#login_widget > .button:active,
#logout:active,
span#login_widget > .button.active,
#logout.active,
.open > .dropdown-togglespan#login_widget > .button,
.open > .dropdown-toggle#logout {
  background-image: none;
}
span#login_widget > .button.disabled:hover,
#logout.disabled:hover,
span#login_widget > .button[disabled]:hover,
#logout[disabled]:hover,
fieldset[disabled] span#login_widget > .button:hover,
fieldset[disabled] #logout:hover,
span#login_widget > .button.disabled:focus,
#logout.disabled:focus,
span#login_widget > .button[disabled]:focus,
#logout[disabled]:focus,
fieldset[disabled] span#login_widget > .button:focus,
fieldset[disabled] #logout:focus,
span#login_widget > .button.disabled.focus,
#logout.disabled.focus,
span#login_widget > .button[disabled].focus,
#logout[disabled].focus,
fieldset[disabled] span#login_widget > .button.focus,
fieldset[disabled] #logout.focus {
  background-color: #fff;
  border-color: #ccc;
}
span#login_widget > .button .badge,
#logout .badge {
  color: #fff;
  background-color: #333;
}
.nav-header {
  text-transform: none;
}
#header > span {
  margin-top: 10px;
}
.modal_stretch .modal-dialog {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
  min-height: 80vh;
}
.modal_stretch .modal-dialog .modal-body {
  max-height: calc(100vh - 200px);
  overflow: auto;
  flex: 1;
}
.modal-header {
  cursor: move;
}
@media (min-width: 768px) {
  .modal .modal-dialog {
    width: 700px;
  }
}
@media (min-width: 768px) {
  select.form-control {
    margin-left: 12px;
    margin-right: 12px;
  }
}
/*!
*
* IPython auth
*
*/
.center-nav {
  display: inline-block;
  margin-bottom: -4px;
}
[dir="rtl"] .center-nav form.pull-left {
  float: right !important;
  float: right;
}
[dir="rtl"] .center-nav .navbar-text {
  float: right;
}
[dir="rtl"] .navbar-inner {
  text-align: right;
}
[dir="rtl"] div.text-left {
  text-align: right;
}
/*!
*
* IPython tree view
*
*/
/* We need an invisible input field on top of the sentense*/
/* "Drag file onto the list ..." */
.alternate_upload {
  background-color: none;
  display: inline;
}
.alternate_upload.form {
  padding: 0;
  margin: 0;
}
.alternate_upload input.fileinput {
  position: absolute;
  display: block;
  width: 100%;
  height: 100%;
  overflow: hidden;
  cursor: pointer;
  opacity: 0;
  z-index: 2;
}
.alternate_upload .btn-xs > input.fileinput {
  margin: -1px -5px;
}
.alternate_upload .btn-upload {
  position: relative;
  height: 22px;
}
::-webkit-file-upload-button {
  cursor: pointer;
}
/**
 * Primary styles
 *
 * Author: Jupyter Development Team
 */
ul#tabs {
  margin-bottom: 4px;
}
ul#tabs a {
  padding-top: 6px;
  padding-bottom: 4px;
}
[dir="rtl"] ul#tabs.nav-tabs > li {
  float: right;
}
[dir="rtl"] ul#tabs.nav.nav-tabs {
  padding-right: 0;
}
ul.breadcrumb a:focus,
ul.breadcrumb a:hover {
  text-decoration: none;
}
ul.breadcrumb i.icon-home {
  font-size: 16px;
  margin-right: 4px;
}
ul.breadcrumb span {
  color: #5e5e5e;
}
.list_toolbar {
  padding: 4px 0 4px 0;
  vertical-align: middle;
}
.list_toolbar .tree-buttons {
  padding-top: 1px;
}
[dir="rtl"] .list_toolbar .tree-buttons .pull-right {
  float: left !important;
  float: left;
}
[dir="rtl"] .list_toolbar .col-sm-4,
[dir="rtl"] .list_toolbar .col-sm-8 {
  float: right;
}
.dynamic-buttons {
  padding-top: 3px;
  display: inline-block;
}
.list_toolbar [class*="span"] {
  min-height: 24px;
}
.list_header {
  font-weight: bold;
  background-color: #EEE;
}
.list_placeholder {
  font-weight: bold;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 7px;
  padding-right: 7px;
}
.list_container {
  margin-top: 4px;
  margin-bottom: 20px;
  border: 1px solid #ddd;
  border-radius: 2px;
}
.list_container > div {
  border-bottom: 1px solid #ddd;
}
.list_container > div:hover .list-item {
  background-color: red;
}
.list_container > div:last-child {
  border: none;
}
.list_item:hover .list_item {
  background-color: #ddd;
}
.list_item a {
  text-decoration: none;
}
.list_item:hover {
  background-color: #fafafa;
}
.list_header > div,
.list_item > div {
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 7px;
  padding-right: 7px;
  line-height: 22px;
}
.list_header > div input,
.list_item > div input {
  margin-right: 7px;
  margin-left: 14px;
  vertical-align: text-bottom;
  line-height: 22px;
  position: relative;
  top: -1px;
}
.list_header > div .item_link,
.list_item > div .item_link {
  margin-left: -1px;
  vertical-align: baseline;
  line-height: 22px;
}
[dir="rtl"] .list_item > div input {
  margin-right: 0;
}
.new-file input[type=checkbox] {
  visibility: hidden;
}
.item_name {
  line-height: 22px;
  height: 24px;
}
.item_icon {
  font-size: 14px;
  color: #5e5e5e;
  margin-right: 7px;
  margin-left: 7px;
  line-height: 22px;
  vertical-align: baseline;
}
.item_modified {
  margin-right: 7px;
  margin-left: 7px;
}
[dir="rtl"] .item_modified.pull-right {
  float: left !important;
  float: left;
}
.item_buttons {
  line-height: 1em;
  margin-left: -5px;
}
.item_buttons .btn,
.item_buttons .btn-group,
.item_buttons .input-group {
  float: left;
}
.item_buttons > .btn,
.item_buttons > .btn-group,
.item_buttons > .input-group {
  margin-left: 5px;
}
.item_buttons .btn {
  min-width: 13ex;
}
.item_buttons .running-indicator {
  padding-top: 4px;
  color: #5cb85c;
}
.item_buttons .kernel-name {
  padding-top: 4px;
  color: #5bc0de;
  margin-right: 7px;
  float: left;
}
[dir="rtl"] .item_buttons.pull-right {
  float: left !important;
  float: left;
}
[dir="rtl"] .item_buttons .kernel-name {
  margin-left: 7px;
  float: right;
}
.toolbar_info {
  height: 24px;
  line-height: 24px;
}
.list_item input:not([type=checkbox]) {
  padding-top: 3px;
  padding-bottom: 3px;
  height: 22px;
  line-height: 14px;
  margin: 0px;
}
.highlight_text {
  color: blue;
}
#project_name {
  display: inline-block;
  padding-left: 7px;
  margin-left: -2px;
}
#project_name > .breadcrumb {
  padding: 0px;
  margin-bottom: 0px;
  background-color: transparent;
  font-weight: bold;
}
.sort_button {
  display: inline-block;
  padding-left: 7px;
}
[dir="rtl"] .sort_button.pull-right {
  float: left !important;
  float: left;
}
#tree-selector {
  padding-right: 0px;
}
#button-select-all {
  min-width: 50px;
}
[dir="rtl"] #button-select-all.btn {
  float: right ;
}
#select-all {
  margin-left: 7px;
  margin-right: 2px;
  margin-top: 2px;
  height: 16px;
}
[dir="rtl"] #select-all.pull-left {
  float: right !important;
  float: right;
}
.menu_icon {
  margin-right: 2px;
}
.tab-content .row {
  margin-left: 0px;
  margin-right: 0px;
}
.folder_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f114";
}
.folder_icon:before.fa-pull-left {
  margin-right: .3em;
}
.folder_icon:before.fa-pull-right {
  margin-left: .3em;
}
.folder_icon:before.pull-left {
  margin-right: .3em;
}
.folder_icon:before.pull-right {
  margin-left: .3em;
}
.notebook_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f02d";
  position: relative;
  top: -1px;
}
.notebook_icon:before.fa-pull-left {
  margin-right: .3em;
}
.notebook_icon:before.fa-pull-right {
  margin-left: .3em;
}
.notebook_icon:before.pull-left {
  margin-right: .3em;
}
.notebook_icon:before.pull-right {
  margin-left: .3em;
}
.running_notebook_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f02d";
  position: relative;
  top: -1px;
  color: #5cb85c;
}
.running_notebook_icon:before.fa-pull-left {
  margin-right: .3em;
}
.running_notebook_icon:before.fa-pull-right {
  margin-left: .3em;
}
.running_notebook_icon:before.pull-left {
  margin-right: .3em;
}
.running_notebook_icon:before.pull-right {
  margin-left: .3em;
}
.file_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f016";
  position: relative;
  top: -2px;
}
.file_icon:before.fa-pull-left {
  margin-right: .3em;
}
.file_icon:before.fa-pull-right {
  margin-left: .3em;
}
.file_icon:before.pull-left {
  margin-right: .3em;
}
.file_icon:before.pull-right {
  margin-left: .3em;
}
#notebook_toolbar .pull-right {
  padding-top: 0px;
  margin-right: -1px;
}
ul#new-menu {
  left: auto;
  right: 0;
}
#new-menu .dropdown-header {
  font-size: 10px;
  border-bottom: 1px solid #e5e5e5;
  padding: 0 0 3px;
  margin: -3px 20px 0;
}
.kernel-menu-icon {
  padding-right: 12px;
  width: 24px;
  content: "\f096";
}
.kernel-menu-icon:before {
  content: "\f096";
}
.kernel-menu-icon-current:before {
  content: "\f00c";
}
#tab_content {
  padding-top: 20px;
}
#running .panel-group .panel {
  margin-top: 3px;
  margin-bottom: 1em;
}
#running .panel-group .panel .panel-heading {
  background-color: #EEE;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 7px;
  padding-right: 7px;
  line-height: 22px;
}
#running .panel-group .panel .panel-heading a:focus,
#running .panel-group .panel .panel-heading a:hover {
  text-decoration: none;
}
#running .panel-group .panel .panel-body {
  padding: 0px;
}
#running .panel-group .panel .panel-body .list_container {
  margin-top: 0px;
  margin-bottom: 0px;
  border: 0px;
  border-radius: 0px;
}
#running .panel-group .panel .panel-body .list_container .list_item {
  border-bottom: 1px solid #ddd;
}
#running .panel-group .panel .panel-body .list_container .list_item:last-child {
  border-bottom: 0px;
}
.delete-button {
  display: none;
}
.duplicate-button {
  display: none;
}
.rename-button {
  display: none;
}
.move-button {
  display: none;
}
.download-button {
  display: none;
}
.shutdown-button {
  display: none;
}
.dynamic-instructions {
  display: inline-block;
  padding-top: 4px;
}
/*!
*
* IPython text editor webapp
*
*/
.selected-keymap i.fa {
  padding: 0px 5px;
}
.selected-keymap i.fa:before {
  content: "\f00c";
}
#mode-menu {
  overflow: auto;
  max-height: 20em;
}
.edit_app #header {
  -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
}
.edit_app #menubar .navbar {
  /* Use a negative 1 bottom margin, so the border overlaps the border of the
    header */
  margin-bottom: -1px;
}
.dirty-indicator {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  width: 20px;
}
.dirty-indicator.fa-pull-left {
  margin-right: .3em;
}
.dirty-indicator.fa-pull-right {
  margin-left: .3em;
}
.dirty-indicator.pull-left {
  margin-right: .3em;
}
.dirty-indicator.pull-right {
  margin-left: .3em;
}
.dirty-indicator-dirty {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  width: 20px;
}
.dirty-indicator-dirty.fa-pull-left {
  margin-right: .3em;
}
.dirty-indicator-dirty.fa-pull-right {
  margin-left: .3em;
}
.dirty-indicator-dirty.pull-left {
  margin-right: .3em;
}
.dirty-indicator-dirty.pull-right {
  margin-left: .3em;
}
.dirty-indicator-clean {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  width: 20px;
}
.dirty-indicator-clean.fa-pull-left {
  margin-right: .3em;
}
.dirty-indicator-clean.fa-pull-right {
  margin-left: .3em;
}
.dirty-indicator-clean.pull-left {
  margin-right: .3em;
}
.dirty-indicator-clean.pull-right {
  margin-left: .3em;
}
.dirty-indicator-clean:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f00c";
}
.dirty-indicator-clean:before.fa-pull-left {
  margin-right: .3em;
}
.dirty-indicator-clean:before.fa-pull-right {
  margin-left: .3em;
}
.dirty-indicator-clean:before.pull-left {
  margin-right: .3em;
}
.dirty-indicator-clean:before.pull-right {
  margin-left: .3em;
}
#filename {
  font-size: 16pt;
  display: table;
  padding: 0px 5px;
}
#current-mode {
  padding-left: 5px;
  padding-right: 5px;
}
#texteditor-backdrop {
  padding-top: 20px;
  padding-bottom: 20px;
}
@media not print {
  #texteditor-backdrop {
    background-color: #EEE;
  }
}
@media print {
  #texteditor-backdrop #texteditor-container .CodeMirror-gutter,
  #texteditor-backdrop #texteditor-container .CodeMirror-gutters {
    background-color: #fff;
  }
}
@media not print {
  #texteditor-backdrop #texteditor-container .CodeMirror-gutter,
  #texteditor-backdrop #texteditor-container .CodeMirror-gutters {
    background-color: #fff;
  }
}
@media not print {
  #texteditor-backdrop #texteditor-container {
    padding: 0px;
    background-color: #fff;
    -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
    box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  }
}
.CodeMirror-dialog {
  background-color: #fff;
}
/*!
*
* IPython notebook
*
*/
/* CSS font colors for translated ANSI escape sequences */
/* The color values are a mix of
   http://www.xcolors.net/dl/baskerville-ivorylight and
   http://www.xcolors.net/dl/euphrasia */
.ansi-black-fg {
  color: #3E424D;
}
.ansi-black-bg {
  background-color: #3E424D;
}
.ansi-black-intense-fg {
  color: #282C36;
}
.ansi-black-intense-bg {
  background-color: #282C36;
}
.ansi-red-fg {
  color: #E75C58;
}
.ansi-red-bg {
  background-color: #E75C58;
}
.ansi-red-intense-fg {
  color: #B22B31;
}
.ansi-red-intense-bg {
  background-color: #B22B31;
}
.ansi-green-fg {
  color: #00A250;
}
.ansi-green-bg {
  background-color: #00A250;
}
.ansi-green-intense-fg {
  color: #007427;
}
.ansi-green-intense-bg {
  background-color: #007427;
}
.ansi-yellow-fg {
  color: #DDB62B;
}
.ansi-yellow-bg {
  background-color: #DDB62B;
}
.ansi-yellow-intense-fg {
  color: #B27D12;
}
.ansi-yellow-intense-bg {
  background-color: #B27D12;
}
.ansi-blue-fg {
  color: #208FFB;
}
.ansi-blue-bg {
  background-color: #208FFB;
}
.ansi-blue-intense-fg {
  color: #0065CA;
}
.ansi-blue-intense-bg {
  background-color: #0065CA;
}
.ansi-magenta-fg {
  color: #D160C4;
}
.ansi-magenta-bg {
  background-color: #D160C4;
}
.ansi-magenta-intense-fg {
  color: #A03196;
}
.ansi-magenta-intense-bg {
  background-color: #A03196;
}
.ansi-cyan-fg {
  color: #60C6C8;
}
.ansi-cyan-bg {
  background-color: #60C6C8;
}
.ansi-cyan-intense-fg {
  color: #258F8F;
}
.ansi-cyan-intense-bg {
  background-color: #258F8F;
}
.ansi-white-fg {
  color: #C5C1B4;
}
.ansi-white-bg {
  background-color: #C5C1B4;
}
.ansi-white-intense-fg {
  color: #A1A6B2;
}
.ansi-white-intense-bg {
  background-color: #A1A6B2;
}
.ansi-default-inverse-fg {
  color: #FFFFFF;
}
.ansi-default-inverse-bg {
  background-color: #000000;
}
.ansi-bold {
  font-weight: bold;
}
.ansi-underline {
  text-decoration: underline;
}
/* The following styles are deprecated an will be removed in a future version */
.ansibold {
  font-weight: bold;
}
.ansi-inverse {
  outline: 0.5px dotted;
}
/* use dark versions for foreground, to improve visibility */
.ansiblack {
  color: black;
}
.ansired {
  color: darkred;
}
.ansigreen {
  color: darkgreen;
}
.ansiyellow {
  color: #c4a000;
}
.ansiblue {
  color: darkblue;
}
.ansipurple {
  color: darkviolet;
}
.ansicyan {
  color: steelblue;
}
.ansigray {
  color: gray;
}
/* and light for background, for the same reason */
.ansibgblack {
  background-color: black;
}
.ansibgred {
  background-color: red;
}
.ansibggreen {
  background-color: green;
}
.ansibgyellow {
  background-color: yellow;
}
.ansibgblue {
  background-color: blue;
}
.ansibgpurple {
  background-color: magenta;
}
.ansibgcyan {
  background-color: cyan;
}
.ansibggray {
  background-color: gray;
}
div.cell {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
  border-radius: 2px;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  border-width: 1px;
  border-style: solid;
  border-color: transparent;
  width: 100%;
  padding: 5px;
  /* This acts as a spacer between cells, that is outside the border */
  margin: 0px;
  outline: none;
  position: relative;
  overflow: visible;
}
div.cell:before {
  position: absolute;
  display: block;
  top: -1px;
  left: -1px;
  width: 5px;
  height: calc(100% +  2px);
  content: '';
  background: transparent;
}
div.cell.jupyter-soft-selected {
  border-left-color: #E3F2FD;
  border-left-width: 1px;
  padding-left: 5px;
  border-right-color: #E3F2FD;
  border-right-width: 1px;
  background: #E3F2FD;
}
@media print {
  div.cell.jupyter-soft-selected {
    border-color: transparent;
  }
}
div.cell.selected,
div.cell.selected.jupyter-soft-selected {
  border-color: #ababab;
}
div.cell.selected:before,
div.cell.selected.jupyter-soft-selected:before {
  position: absolute;
  display: block;
  top: -1px;
  left: -1px;
  width: 5px;
  height: calc(100% +  2px);
  content: '';
  background: #42A5F5;
}
@media print {
  div.cell.selected,
  div.cell.selected.jupyter-soft-selected {
    border-color: transparent;
  }
}
.edit_mode div.cell.selected {
  border-color: #66BB6A;
}
.edit_mode div.cell.selected:before {
  position: absolute;
  display: block;
  top: -1px;
  left: -1px;
  width: 5px;
  height: calc(100% +  2px);
  content: '';
  background: #66BB6A;
}
@media print {
  .edit_mode div.cell.selected {
    border-color: transparent;
  }
}
.prompt {
  /* This needs to be wide enough for 3 digit prompt numbers: In[100]: */
  min-width: 14ex;
  /* This padding is tuned to match the padding on the CodeMirror editor. */
  padding: 0.4em;
  margin: 0px;
  font-family: monospace;
  text-align: right;
  /* This has to match that of the the CodeMirror class line-height below */
  line-height: 1.21429em;
  /* Don't highlight prompt number selection */
  -webkit-touch-callout: none;
  -webkit-user-select: none;
  -khtml-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
  /* Use default cursor */
  cursor: default;
}
@media (max-width: 540px) {
  .prompt {
    text-align: left;
  }
}
div.inner_cell {
  min-width: 0;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
  /* Old browsers */
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  box-flex: 1;
  /* Modern browsers */
  flex: 1;
}
/* input_area and input_prompt must match in top border and margin for alignment */
div.input_area {
  border: 1px solid #cfcfcf;
  border-radius: 2px;
  background: #f7f7f7;
  line-height: 1.21429em;
}
/* This is needed so that empty prompt areas can collapse to zero height when there
   is no content in the output_subarea and the prompt. The main purpose of this is
   to make sure that empty JavaScript output_subareas have no height. */
div.prompt:empty {
  padding-top: 0;
  padding-bottom: 0;
}
div.unrecognized_cell {
  padding: 5px 5px 5px 0px;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
div.unrecognized_cell .inner_cell {
  border-radius: 2px;
  padding: 5px;
  font-weight: bold;
  color: red;
  border: 1px solid #cfcfcf;
  background: #eaeaea;
}
div.unrecognized_cell .inner_cell a {
  color: inherit;
  text-decoration: none;
}
div.unrecognized_cell .inner_cell a:hover {
  color: inherit;
  text-decoration: none;
}
@media (max-width: 540px) {
  div.unrecognized_cell > div.prompt {
    display: none;
  }
}
div.code_cell {
  /* avoid page breaking on code cells when printing */
}
@media print {
  div.code_cell {
    page-break-inside: avoid;
  }
}
/* any special styling for code cells that are currently running goes here */
div.input {
  page-break-inside: avoid;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
@media (max-width: 540px) {
  div.input {
    /* Old browsers */
    display: -webkit-box;
    -webkit-box-orient: vertical;
    -webkit-box-align: stretch;
    display: -moz-box;
    -moz-box-orient: vertical;
    -moz-box-align: stretch;
    display: box;
    box-orient: vertical;
    box-align: stretch;
    /* Modern browsers */
    display: flex;
    flex-direction: column;
    align-items: stretch;
  }
}
/* input_area and input_prompt must match in top border and margin for alignment */
div.input_prompt {
  color: #303F9F;
  border-top: 1px solid transparent;
}
div.input_area > div.highlight {
  margin: 0.4em;
  border: none;
  padding: 0px;
  background-color: transparent;
}
div.input_area > div.highlight > pre {
  margin: 0px;
  border: none;
  padding: 0px;
  background-color: transparent;
}
/* The following gets added to the <head> if it is detected that the user has a
 * monospace font with inconsistent normal/bold/italic height.  See
 * notebookmain.js.  Such fonts will have keywords vertically offset with
 * respect to the rest of the text.  The user should select a better font.
 * See: https://github.com/ipython/ipython/issues/1503
 *
 * .CodeMirror span {
 *      vertical-align: bottom;
 * }
 */
.CodeMirror {
  line-height: 1.21429em;
  /* Changed from 1em to our global default */
  font-size: 14px;
  height: auto;
  /* Changed to auto to autogrow */
  background: none;
  /* Changed from white to allow our bg to show through */
}
.CodeMirror-scroll {
  /*  The CodeMirror docs are a bit fuzzy on if overflow-y should be hidden or visible.*/
  /*  We have found that if it is visible, vertical scrollbars appear with font size changes.*/
  overflow-y: hidden;
  overflow-x: auto;
}
.CodeMirror-lines {
  /* In CM2, this used to be 0.4em, but in CM3 it went to 4px. We need the em value because */
  /* we have set a different line-height and want this to scale with that. */
  /* Note that this should set vertical padding only, since CodeMirror assumes
       that horizontal padding will be set on CodeMirror pre */
  padding: 0.4em 0;
}
.CodeMirror-linenumber {
  padding: 0 8px 0 4px;
}
.CodeMirror-gutters {
  border-bottom-left-radius: 2px;
  border-top-left-radius: 2px;
}
.CodeMirror pre {
  /* In CM3 this went to 4px from 0 in CM2. This sets horizontal padding only,
    use .CodeMirror-lines for vertical */
  padding: 0 0.4em;
  border: 0;
  border-radius: 0;
}
.CodeMirror-cursor {
  border-left: 1.4px solid black;
}
@media screen and (min-width: 2138px) and (max-width: 4319px) {
  .CodeMirror-cursor {
    border-left: 2px solid black;
  }
}
@media screen and (min-width: 4320px) {
  .CodeMirror-cursor {
    border-left: 4px solid black;
  }
}
/*

Original style from softwaremaniacs.org (c) Ivan Sagalaev <Maniac@SoftwareManiacs.Org>
Adapted from GitHub theme

*/
.highlight-base {
  color: #000;
}
.highlight-variable {
  color: #000;
}
.highlight-variable-2 {
  color: #1a1a1a;
}
.highlight-variable-3 {
  color: #333333;
}
.highlight-string {
  color: #BA2121;
}
.highlight-comment {
  color: #408080;
  font-style: italic;
}
.highlight-number {
  color: #080;
}
.highlight-atom {
  color: #88F;
}
.highlight-keyword {
  color: #008000;
  font-weight: bold;
}
.highlight-builtin {
  color: #008000;
}
.highlight-error {
  color: #f00;
}
.highlight-operator {
  color: #AA22FF;
  font-weight: bold;
}
.highlight-meta {
  color: #AA22FF;
}
/* previously not defined, copying from default codemirror */
.highlight-def {
  color: #00f;
}
.highlight-string-2 {
  color: #f50;
}
.highlight-qualifier {
  color: #555;
}
.highlight-bracket {
  color: #997;
}
.highlight-tag {
  color: #170;
}
.highlight-attribute {
  color: #00c;
}
.highlight-header {
  color: blue;
}
.highlight-quote {
  color: #090;
}
.highlight-link {
  color: #00c;
}
/* apply the same style to codemirror */
.cm-s-ipython span.cm-keyword {
  color: #008000;
  font-weight: bold;
}
.cm-s-ipython span.cm-atom {
  color: #88F;
}
.cm-s-ipython span.cm-number {
  color: #080;
}
.cm-s-ipython span.cm-def {
  color: #00f;
}
.cm-s-ipython span.cm-variable {
  color: #000;
}
.cm-s-ipython span.cm-operator {
  color: #AA22FF;
  font-weight: bold;
}
.cm-s-ipython span.cm-variable-2 {
  color: #1a1a1a;
}
.cm-s-ipython span.cm-variable-3 {
  color: #333333;
}
.cm-s-ipython span.cm-comment {
  color: #408080;
  font-style: italic;
}
.cm-s-ipython span.cm-string {
  color: #BA2121;
}
.cm-s-ipython span.cm-string-2 {
  color: #f50;
}
.cm-s-ipython span.cm-meta {
  color: #AA22FF;
}
.cm-s-ipython span.cm-qualifier {
  color: #555;
}
.cm-s-ipython span.cm-builtin {
  color: #008000;
}
.cm-s-ipython span.cm-bracket {
  color: #997;
}
.cm-s-ipython span.cm-tag {
  color: #170;
}
.cm-s-ipython span.cm-attribute {
  color: #00c;
}
.cm-s-ipython span.cm-header {
  color: blue;
}
.cm-s-ipython span.cm-quote {
  color: #090;
}
.cm-s-ipython span.cm-link {
  color: #00c;
}
.cm-s-ipython span.cm-error {
  color: #f00;
}
.cm-s-ipython span.cm-tab {
  background: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADAAAAAMCAYAAAAkuj5RAAAAAXNSR0IArs4c6QAAAGFJREFUSMft1LsRQFAQheHPowAKoACx3IgEKtaEHujDjORSgWTH/ZOdnZOcM/sgk/kFFWY0qV8foQwS4MKBCS3qR6ixBJvElOobYAtivseIE120FaowJPN75GMu8j/LfMwNjh4HUpwg4LUAAAAASUVORK5CYII=);
  background-position: right;
  background-repeat: no-repeat;
}
div.output_wrapper {
  /* this position must be relative to enable descendents to be absolute within it */
  position: relative;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
  z-index: 1;
}
/* class for the output area when it should be height-limited */
div.output_scroll {
  /* ideally, this would be max-height, but FF barfs all over that */
  height: 24em;
  /* FF needs this *and the wrapper* to specify full width, or it will shrinkwrap */
  width: 100%;
  overflow: auto;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 2px 8px rgba(0, 0, 0, 0.8);
  box-shadow: inset 0 2px 8px rgba(0, 0, 0, 0.8);
  display: block;
}
/* output div while it is collapsed */
div.output_collapsed {
  margin: 0px;
  padding: 0px;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
}
div.out_prompt_overlay {
  height: 100%;
  padding: 0px 0.4em;
  position: absolute;
  border-radius: 2px;
}
div.out_prompt_overlay:hover {
  /* use inner shadow to get border that is computed the same on WebKit/FF */
  -webkit-box-shadow: inset 0 0 1px #000;
  box-shadow: inset 0 0 1px #000;
  background: rgba(240, 240, 240, 0.5);
}
div.output_prompt {
  color: #D84315;
}
/* This class is the outer container of all output sections. */
div.output_area {
  padding: 0px;
  page-break-inside: avoid;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
div.output_area .MathJax_Display {
  text-align: left !important;
}
div.output_area .rendered_html table {
  margin-left: 0;
  margin-right: 0;
}
div.output_area .rendered_html img {
  margin-left: 0;
  margin-right: 0;
}
div.output_area img,
div.output_area svg {
  max-width: 100%;
  height: auto;
}
div.output_area img.unconfined,
div.output_area svg.unconfined {
  max-width: none;
}
div.output_area .mglyph > img {
  max-width: none;
}
/* This is needed to protect the pre formating from global settings such
   as that of bootstrap */
.output {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: vertical;
  -moz-box-align: stretch;
  display: box;
  box-orient: vertical;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: column;
  align-items: stretch;
}
@media (max-width: 540px) {
  div.output_area {
    /* Old browsers */
    display: -webkit-box;
    -webkit-box-orient: vertical;
    -webkit-box-align: stretch;
    display: -moz-box;
    -moz-box-orient: vertical;
    -moz-box-align: stretch;
    display: box;
    box-orient: vertical;
    box-align: stretch;
    /* Modern browsers */
    display: flex;
    flex-direction: column;
    align-items: stretch;
  }
}
div.output_area pre {
  margin: 0;
  padding: 1px 0 1px 0;
  border: 0;
  vertical-align: baseline;
  color: black;
  background-color: transparent;
  border-radius: 0;
}
/* This class is for the output subarea inside the output_area and after
   the prompt div. */
div.output_subarea {
  overflow-x: auto;
  padding: 0.4em;
  /* Old browsers */
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  box-flex: 1;
  /* Modern browsers */
  flex: 1;
  max-width: calc(100% - 14ex);
}
div.output_scroll div.output_subarea {
  overflow-x: visible;
}
/* The rest of the output_* classes are for special styling of the different
   output types */
/* all text output has this class: */
div.output_text {
  text-align: left;
  color: #000;
  /* This has to match that of the the CodeMirror class line-height below */
  line-height: 1.21429em;
}
/* stdout/stderr are 'text' as well as 'stream', but execute_result/error are *not* streams */
div.output_stderr {
  background: #fdd;
  /* very light red background for stderr */
}
div.output_latex {
  text-align: left;
}
/* Empty output_javascript divs should have no height */
div.output_javascript:empty {
  padding: 0;
}
.js-error {
  color: darkred;
}
/* raw_input styles */
div.raw_input_container {
  line-height: 1.21429em;
  padding-top: 5px;
}
pre.raw_input_prompt {
  /* nothing needed here. */
}
input.raw_input {
  font-family: monospace;
  font-size: inherit;
  color: inherit;
  width: auto;
  /* make sure input baseline aligns with prompt */
  vertical-align: baseline;
  /* padding + margin = 0.5em between prompt and cursor */
  padding: 0em 0.25em;
  margin: 0em 0.25em;
}
input.raw_input:focus {
  box-shadow: none;
}
p.p-space {
  margin-bottom: 10px;
}
div.output_unrecognized {
  padding: 5px;
  font-weight: bold;
  color: red;
}
div.output_unrecognized a {
  color: inherit;
  text-decoration: none;
}
div.output_unrecognized a:hover {
  color: inherit;
  text-decoration: none;
}
.rendered_html {
  color: #000;
  /* any extras will just be numbers: */
}
.rendered_html em {
  font-style: italic;
}
.rendered_html strong {
  font-weight: bold;
}
.rendered_html u {
  text-decoration: underline;
}
.rendered_html :link {
  text-decoration: underline;
}
.rendered_html :visited {
  text-decoration: underline;
}
.rendered_html h1 {
  font-size: 185.7%;
  margin: 1.08em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
}
.rendered_html h2 {
  font-size: 157.1%;
  margin: 1.27em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
}
.rendered_html h3 {
  font-size: 128.6%;
  margin: 1.55em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
}
.rendered_html h4 {
  font-size: 100%;
  margin: 2em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
}
.rendered_html h5 {
  font-size: 100%;
  margin: 2em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
  font-style: italic;
}
.rendered_html h6 {
  font-size: 100%;
  margin: 2em 0 0 0;
  font-weight: bold;
  line-height: 1.0;
  font-style: italic;
}
.rendered_html h1:first-child {
  margin-top: 0.538em;
}
.rendered_html h2:first-child {
  margin-top: 0.636em;
}
.rendered_html h3:first-child {
  margin-top: 0.777em;
}
.rendered_html h4:first-child {
  margin-top: 1em;
}
.rendered_html h5:first-child {
  margin-top: 1em;
}
.rendered_html h6:first-child {
  margin-top: 1em;
}
.rendered_html ul:not(.list-inline),
.rendered_html ol:not(.list-inline) {
  padding-left: 2em;
}
.rendered_html ul {
  list-style: disc;
}
.rendered_html ul ul {
  list-style: square;
  margin-top: 0;
}
.rendered_html ul ul ul {
  list-style: circle;
}
.rendered_html ol {
  list-style: decimal;
}
.rendered_html ol ol {
  list-style: upper-alpha;
  margin-top: 0;
}
.rendered_html ol ol ol {
  list-style: lower-alpha;
}
.rendered_html ol ol ol ol {
  list-style: lower-roman;
}
.rendered_html ol ol ol ol ol {
  list-style: decimal;
}
.rendered_html * + ul {
  margin-top: 1em;
}
.rendered_html * + ol {
  margin-top: 1em;
}
.rendered_html hr {
  color: black;
  background-color: black;
}
.rendered_html pre {
  margin: 1em 2em;
  padding: 0px;
  background-color: #fff;
}
.rendered_html code {
  background-color: #eff0f1;
}
.rendered_html p code {
  padding: 1px 5px;
}
.rendered_html pre code {
  background-color: #fff;
}
.rendered_html pre,
.rendered_html code {
  border: 0;
  color: #000;
  font-size: 100%;
}
.rendered_html blockquote {
  margin: 1em 2em;
}
.rendered_html table {
  margin-left: auto;
  margin-right: auto;
  border: none;
  border-collapse: collapse;
  border-spacing: 0;
  color: black;
  font-size: 12px;
  table-layout: fixed;
}
.rendered_html thead {
  border-bottom: 1px solid black;
  vertical-align: bottom;
}
.rendered_html tr,
.rendered_html th,
.rendered_html td {
  text-align: right;
  vertical-align: middle;
  padding: 0.5em 0.5em;
  line-height: normal;
  white-space: normal;
  max-width: none;
  border: none;
}
.rendered_html th {
  font-weight: bold;
}
.rendered_html tbody tr:nth-child(odd) {
  background: #f5f5f5;
}
.rendered_html tbody tr:hover {
  background: rgba(66, 165, 245, 0.2);
}
.rendered_html * + table {
  margin-top: 1em;
}
.rendered_html p {
  text-align: left;
}
.rendered_html * + p {
  margin-top: 1em;
}
.rendered_html img {
  display: block;
  margin-left: auto;
  margin-right: auto;
}
.rendered_html * + img {
  margin-top: 1em;
}
.rendered_html img,
.rendered_html svg {
  max-width: 100%;
  height: auto;
}
.rendered_html img.unconfined,
.rendered_html svg.unconfined {
  max-width: none;
}
.rendered_html .alert {
  margin-bottom: initial;
}
.rendered_html * + .alert {
  margin-top: 1em;
}
[dir="rtl"] .rendered_html p {
  text-align: right;
}
div.text_cell {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
}
@media (max-width: 540px) {
  div.text_cell > div.prompt {
    display: none;
  }
}
div.text_cell_render {
  /*font-family: "Helvetica Neue", Arial, Helvetica, Geneva, sans-serif;*/
  outline: none;
  resize: none;
  width: inherit;
  border-style: none;
  padding: 0.5em 0.5em 0.5em 0.4em;
  color: #000;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
a.anchor-link:link {
  text-decoration: none;
  padding: 0px 20px;
  visibility: hidden;
}
h1:hover .anchor-link,
h2:hover .anchor-link,
h3:hover .anchor-link,
h4:hover .anchor-link,
h5:hover .anchor-link,
h6:hover .anchor-link {
  visibility: visible;
}
.text_cell.rendered .input_area {
  display: none;
}
.text_cell.rendered .rendered_html {
  overflow-x: auto;
  overflow-y: hidden;
}
.text_cell.rendered .rendered_html tr,
.text_cell.rendered .rendered_html th,
.text_cell.rendered .rendered_html td {
  max-width: none;
}
.text_cell.unrendered .text_cell_render {
  display: none;
}
.text_cell .dropzone .input_area {
  border: 2px dashed #bababa;
  margin: -1px;
}
.cm-header-1,
.cm-header-2,
.cm-header-3,
.cm-header-4,
.cm-header-5,
.cm-header-6 {
  font-weight: bold;
  font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
}
.cm-header-1 {
  font-size: 185.7%;
}
.cm-header-2 {
  font-size: 157.1%;
}
.cm-header-3 {
  font-size: 128.6%;
}
.cm-header-4 {
  font-size: 110%;
}
.cm-header-5 {
  font-size: 100%;
  font-style: italic;
}
.cm-header-6 {
  font-size: 100%;
  font-style: italic;
}
/*!
*
* IPython notebook webapp
*
*/
@media (max-width: 767px) {
  .notebook_app {
    padding-left: 0px;
    padding-right: 0px;
  }
}
#ipython-main-app {
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  height: 100%;
}
div#notebook_panel {
  margin: 0px;
  padding: 0px;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  height: 100%;
}
div#notebook {
  font-size: 14px;
  line-height: 20px;
  overflow-y: hidden;
  overflow-x: auto;
  width: 100%;
  /* This spaces the page away from the edge of the notebook area */
  padding-top: 20px;
  margin: 0px;
  outline: none;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  min-height: 100%;
}
@media not print {
  #notebook-container {
    padding: 15px;
    background-color: #fff;
    min-height: 0;
    -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
    box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  }
}
@media print {
  #notebook-container {
    width: 100%;
  }
}
div.ui-widget-content {
  border: 1px solid #ababab;
  outline: none;
}
pre.dialog {
  background-color: #f7f7f7;
  border: 1px solid #ddd;
  border-radius: 2px;
  padding: 0.4em;
  padding-left: 2em;
}
p.dialog {
  padding: 0.2em;
}
/* Word-wrap output correctly.  This is the CSS3 spelling, though Firefox seems
   to not honor it correctly.  Webkit browsers (Chrome, rekonq, Safari) do.
 */
pre,
code,
kbd,
samp {
  white-space: pre-wrap;
}
#fonttest {
  font-family: monospace;
}
p {
  margin-bottom: 0;
}
.end_space {
  min-height: 100px;
  transition: height .2s ease;
}
.notebook_app > #header {
  -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
}
@media not print {
  .notebook_app {
    background-color: #EEE;
  }
}
kbd {
  border-style: solid;
  border-width: 1px;
  box-shadow: none;
  margin: 2px;
  padding-left: 2px;
  padding-right: 2px;
  padding-top: 1px;
  padding-bottom: 1px;
}
.jupyter-keybindings {
  padding: 1px;
  line-height: 24px;
  border-bottom: 1px solid gray;
}
.jupyter-keybindings input {
  margin: 0;
  padding: 0;
  border: none;
}
.jupyter-keybindings i {
  padding: 6px;
}
.well code {
  background-color: #ffffff;
  border-color: #ababab;
  border-width: 1px;
  border-style: solid;
  padding: 2px;
  padding-top: 1px;
  padding-bottom: 1px;
}
/* CSS for the cell toolbar */
.celltoolbar {
  border: thin solid #CFCFCF;
  border-bottom: none;
  background: #EEE;
  border-radius: 2px 2px 0px 0px;
  width: 100%;
  height: 29px;
  padding-right: 4px;
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
  /* Old browsers */
  -webkit-box-pack: end;
  -moz-box-pack: end;
  box-pack: end;
  /* Modern browsers */
  justify-content: flex-end;
  display: -webkit-flex;
}
@media print {
  .celltoolbar {
    display: none;
  }
}
.ctb_hideshow {
  display: none;
  vertical-align: bottom;
}
/* ctb_show is added to the ctb_hideshow div to show the cell toolbar.
   Cell toolbars are only shown when the ctb_global_show class is also set.
*/
.ctb_global_show .ctb_show.ctb_hideshow {
  display: block;
}
.ctb_global_show .ctb_show + .input_area,
.ctb_global_show .ctb_show + div.text_cell_input,
.ctb_global_show .ctb_show ~ div.text_cell_render {
  border-top-right-radius: 0px;
  border-top-left-radius: 0px;
}
.ctb_global_show .ctb_show ~ div.text_cell_render {
  border: 1px solid #cfcfcf;
}
.celltoolbar {
  font-size: 87%;
  padding-top: 3px;
}
.celltoolbar select {
  display: block;
  width: 100%;
  height: 32px;
  padding: 6px 12px;
  font-size: 13px;
  line-height: 1.42857143;
  color: #555555;
  background-color: #fff;
  background-image: none;
  border: 1px solid #ccc;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  -webkit-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  -o-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  height: 30px;
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
  width: inherit;
  font-size: inherit;
  height: 22px;
  padding: 0px;
  display: inline-block;
}
.celltoolbar select:focus {
  border-color: #66afe9;
  outline: 0;
  -webkit-box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
  box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
}
.celltoolbar select::-moz-placeholder {
  color: #999;
  opacity: 1;
}
.celltoolbar select:-ms-input-placeholder {
  color: #999;
}
.celltoolbar select::-webkit-input-placeholder {
  color: #999;
}
.celltoolbar select::-ms-expand {
  border: 0;
  background-color: transparent;
}
.celltoolbar select[disabled],
.celltoolbar select[readonly],
fieldset[disabled] .celltoolbar select {
  background-color: #eeeeee;
  opacity: 1;
}
.celltoolbar select[disabled],
fieldset[disabled] .celltoolbar select {
  cursor: not-allowed;
}
textarea.celltoolbar select {
  height: auto;
}
select.celltoolbar select {
  height: 30px;
  line-height: 30px;
}
textarea.celltoolbar select,
select[multiple].celltoolbar select {
  height: auto;
}
.celltoolbar label {
  margin-left: 5px;
  margin-right: 5px;
}
.tags_button_container {
  width: 100%;
  display: flex;
}
.tag-container {
  display: flex;
  flex-direction: row;
  flex-grow: 1;
  overflow: hidden;
  position: relative;
}
.tag-container > * {
  margin: 0 4px;
}
.remove-tag-btn {
  margin-left: 4px;
}
.tags-input {
  display: flex;
}
.cell-tag:last-child:after {
  content: "";
  position: absolute;
  right: 0;
  width: 40px;
  height: 100%;
  /* Fade to background color of cell toolbar */
  background: linear-gradient(to right, rgba(0, 0, 0, 0), #EEE);
}
.tags-input > * {
  margin-left: 4px;
}
.cell-tag,
.tags-input input,
.tags-input button {
  display: block;
  width: 100%;
  height: 32px;
  padding: 6px 12px;
  font-size: 13px;
  line-height: 1.42857143;
  color: #555555;
  background-color: #fff;
  background-image: none;
  border: 1px solid #ccc;
  border-radius: 2px;
  -webkit-box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075);
  -webkit-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  -o-transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  transition: border-color ease-in-out .15s, box-shadow ease-in-out .15s;
  height: 30px;
  padding: 5px 10px;
  font-size: 12px;
  line-height: 1.5;
  border-radius: 1px;
  box-shadow: none;
  width: inherit;
  font-size: inherit;
  height: 22px;
  line-height: 22px;
  padding: 0px 4px;
  display: inline-block;
}
.cell-tag:focus,
.tags-input input:focus,
.tags-input button:focus {
  border-color: #66afe9;
  outline: 0;
  -webkit-box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
  box-shadow: inset 0 1px 1px rgba(0,0,0,.075), 0 0 8px rgba(102, 175, 233, 0.6);
}
.cell-tag::-moz-placeholder,
.tags-input input::-moz-placeholder,
.tags-input button::-moz-placeholder {
  color: #999;
  opacity: 1;
}
.cell-tag:-ms-input-placeholder,
.tags-input input:-ms-input-placeholder,
.tags-input button:-ms-input-placeholder {
  color: #999;
}
.cell-tag::-webkit-input-placeholder,
.tags-input input::-webkit-input-placeholder,
.tags-input button::-webkit-input-placeholder {
  color: #999;
}
.cell-tag::-ms-expand,
.tags-input input::-ms-expand,
.tags-input button::-ms-expand {
  border: 0;
  background-color: transparent;
}
.cell-tag[disabled],
.tags-input input[disabled],
.tags-input button[disabled],
.cell-tag[readonly],
.tags-input input[readonly],
.tags-input button[readonly],
fieldset[disabled] .cell-tag,
fieldset[disabled] .tags-input input,
fieldset[disabled] .tags-input button {
  background-color: #eeeeee;
  opacity: 1;
}
.cell-tag[disabled],
.tags-input input[disabled],
.tags-input button[disabled],
fieldset[disabled] .cell-tag,
fieldset[disabled] .tags-input input,
fieldset[disabled] .tags-input button {
  cursor: not-allowed;
}
textarea.cell-tag,
textarea.tags-input input,
textarea.tags-input button {
  height: auto;
}
select.cell-tag,
select.tags-input input,
select.tags-input button {
  height: 30px;
  line-height: 30px;
}
textarea.cell-tag,
textarea.tags-input input,
textarea.tags-input button,
select[multiple].cell-tag,
select[multiple].tags-input input,
select[multiple].tags-input button {
  height: auto;
}
.cell-tag,
.tags-input button {
  padding: 0px 4px;
}
.cell-tag {
  background-color: #fff;
  white-space: nowrap;
}
.tags-input input[type=text]:focus {
  outline: none;
  box-shadow: none;
  border-color: #ccc;
}
.completions {
  position: absolute;
  z-index: 110;
  overflow: hidden;
  border: 1px solid #ababab;
  border-radius: 2px;
  -webkit-box-shadow: 0px 6px 10px -1px #adadad;
  box-shadow: 0px 6px 10px -1px #adadad;
  line-height: 1;
}
.completions select {
  background: white;
  outline: none;
  border: none;
  padding: 0px;
  margin: 0px;
  overflow: auto;
  font-family: monospace;
  font-size: 110%;
  color: #000;
  width: auto;
}
.completions select option.context {
  color: #286090;
}
#kernel_logo_widget .current_kernel_logo {
  display: none;
  margin-top: -1px;
  margin-bottom: -1px;
  width: 32px;
  height: 32px;
}
[dir="rtl"] #kernel_logo_widget {
  float: left !important;
  float: left;
}
.modal .modal-body .move-path {
  display: flex;
  flex-direction: row;
  justify-content: space;
  align-items: center;
}
.modal .modal-body .move-path .server-root {
  padding-right: 20px;
}
.modal .modal-body .move-path .path-input {
  flex: 1;
}
#menubar {
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
  margin-top: 1px;
}
#menubar .navbar {
  border-top: 1px;
  border-radius: 0px 0px 2px 2px;
  margin-bottom: 0px;
}
#menubar .navbar-toggle {
  float: left;
  padding-top: 7px;
  padding-bottom: 7px;
  border: none;
}
#menubar .navbar-collapse {
  clear: left;
}
[dir="rtl"] #menubar .navbar-toggle {
  float: right;
}
[dir="rtl"] #menubar .navbar-collapse {
  clear: right;
}
[dir="rtl"] #menubar .navbar-nav {
  float: right;
}
[dir="rtl"] #menubar .nav {
  padding-right: 0px;
}
[dir="rtl"] #menubar .navbar-nav > li {
  float: right;
}
[dir="rtl"] #menubar .navbar-right {
  float: left !important;
}
[dir="rtl"] ul.dropdown-menu {
  text-align: right;
  left: auto;
}
[dir="rtl"] ul#new-menu.dropdown-menu {
  right: auto;
  left: 0;
}
.nav-wrapper {
  border-bottom: 1px solid #e7e7e7;
}
i.menu-icon {
  padding-top: 4px;
}
[dir="rtl"] i.menu-icon.pull-right {
  float: left !important;
  float: left;
}
ul#help_menu li a {
  overflow: hidden;
  padding-right: 2.2em;
}
ul#help_menu li a i {
  margin-right: -1.2em;
}
[dir="rtl"] ul#help_menu li a {
  padding-left: 2.2em;
}
[dir="rtl"] ul#help_menu li a i {
  margin-right: 0;
  margin-left: -1.2em;
}
[dir="rtl"] ul#help_menu li a i.pull-right {
  float: left !important;
  float: left;
}
.dropdown-submenu {
  position: relative;
}
.dropdown-submenu > .dropdown-menu {
  top: 0;
  left: 100%;
  margin-top: -6px;
  margin-left: -1px;
}
[dir="rtl"] .dropdown-submenu > .dropdown-menu {
  right: 100%;
  margin-right: -1px;
}
.dropdown-submenu:hover > .dropdown-menu {
  display: block;
}
.dropdown-submenu > a:after {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: block;
  content: "\f0da";
  float: right;
  color: #333333;
  margin-top: 2px;
  margin-right: -10px;
}
.dropdown-submenu > a:after.fa-pull-left {
  margin-right: .3em;
}
.dropdown-submenu > a:after.fa-pull-right {
  margin-left: .3em;
}
.dropdown-submenu > a:after.pull-left {
  margin-right: .3em;
}
.dropdown-submenu > a:after.pull-right {
  margin-left: .3em;
}
[dir="rtl"] .dropdown-submenu > a:after {
  float: left;
  content: "\f0d9";
  margin-right: 0;
  margin-left: -10px;
}
.dropdown-submenu:hover > a:after {
  color: #262626;
}
.dropdown-submenu.pull-left {
  float: none;
}
.dropdown-submenu.pull-left > .dropdown-menu {
  left: -100%;
  margin-left: 10px;
}
#notification_area {
  float: right !important;
  float: right;
  z-index: 10;
}
[dir="rtl"] #notification_area {
  float: left !important;
  float: left;
}
.indicator_area {
  float: right !important;
  float: right;
  color: #777;
  margin-left: 5px;
  margin-right: 5px;
  width: 11px;
  z-index: 10;
  text-align: center;
  width: auto;
}
[dir="rtl"] .indicator_area {
  float: left !important;
  float: left;
}
#kernel_indicator {
  float: right !important;
  float: right;
  color: #777;
  margin-left: 5px;
  margin-right: 5px;
  width: 11px;
  z-index: 10;
  text-align: center;
  width: auto;
  border-left: 1px solid;
}
#kernel_indicator .kernel_indicator_name {
  padding-left: 5px;
  padding-right: 5px;
}
[dir="rtl"] #kernel_indicator {
  float: left !important;
  float: left;
  border-left: 0;
  border-right: 1px solid;
}
#modal_indicator {
  float: right !important;
  float: right;
  color: #777;
  margin-left: 5px;
  margin-right: 5px;
  width: 11px;
  z-index: 10;
  text-align: center;
  width: auto;
}
[dir="rtl"] #modal_indicator {
  float: left !important;
  float: left;
}
#readonly-indicator {
  float: right !important;
  float: right;
  color: #777;
  margin-left: 5px;
  margin-right: 5px;
  width: 11px;
  z-index: 10;
  text-align: center;
  width: auto;
  margin-top: 2px;
  margin-bottom: 0px;
  margin-left: 0px;
  margin-right: 0px;
  display: none;
}
.modal_indicator:before {
  width: 1.28571429em;
  text-align: center;
}
.edit_mode .modal_indicator:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f040";
}
.edit_mode .modal_indicator:before.fa-pull-left {
  margin-right: .3em;
}
.edit_mode .modal_indicator:before.fa-pull-right {
  margin-left: .3em;
}
.edit_mode .modal_indicator:before.pull-left {
  margin-right: .3em;
}
.edit_mode .modal_indicator:before.pull-right {
  margin-left: .3em;
}
.command_mode .modal_indicator:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: ' ';
}
.command_mode .modal_indicator:before.fa-pull-left {
  margin-right: .3em;
}
.command_mode .modal_indicator:before.fa-pull-right {
  margin-left: .3em;
}
.command_mode .modal_indicator:before.pull-left {
  margin-right: .3em;
}
.command_mode .modal_indicator:before.pull-right {
  margin-left: .3em;
}
.kernel_idle_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f10c";
}
.kernel_idle_icon:before.fa-pull-left {
  margin-right: .3em;
}
.kernel_idle_icon:before.fa-pull-right {
  margin-left: .3em;
}
.kernel_idle_icon:before.pull-left {
  margin-right: .3em;
}
.kernel_idle_icon:before.pull-right {
  margin-left: .3em;
}
.kernel_busy_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f111";
}
.kernel_busy_icon:before.fa-pull-left {
  margin-right: .3em;
}
.kernel_busy_icon:before.fa-pull-right {
  margin-left: .3em;
}
.kernel_busy_icon:before.pull-left {
  margin-right: .3em;
}
.kernel_busy_icon:before.pull-right {
  margin-left: .3em;
}
.kernel_dead_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f1e2";
}
.kernel_dead_icon:before.fa-pull-left {
  margin-right: .3em;
}
.kernel_dead_icon:before.fa-pull-right {
  margin-left: .3em;
}
.kernel_dead_icon:before.pull-left {
  margin-right: .3em;
}
.kernel_dead_icon:before.pull-right {
  margin-left: .3em;
}
.kernel_disconnected_icon:before {
  display: inline-block;
  font: normal normal normal 14px/1 FontAwesome;
  font-size: inherit;
  text-rendering: auto;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  content: "\f127";
}
.kernel_disconnected_icon:before.fa-pull-left {
  margin-right: .3em;
}
.kernel_disconnected_icon:before.fa-pull-right {
  margin-left: .3em;
}
.kernel_disconnected_icon:before.pull-left {
  margin-right: .3em;
}
.kernel_disconnected_icon:before.pull-right {
  margin-left: .3em;
}
.notification_widget {
  color: #777;
  z-index: 10;
  background: rgba(240, 240, 240, 0.5);
  margin-right: 4px;
  color: #333;
  background-color: #fff;
  border-color: #ccc;
}
.notification_widget:focus,
.notification_widget.focus {
  color: #333;
  background-color: #e6e6e6;
  border-color: #8c8c8c;
}
.notification_widget:hover {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
.notification_widget:active,
.notification_widget.active,
.open > .dropdown-toggle.notification_widget {
  color: #333;
  background-color: #e6e6e6;
  border-color: #adadad;
}
.notification_widget:active:hover,
.notification_widget.active:hover,
.open > .dropdown-toggle.notification_widget:hover,
.notification_widget:active:focus,
.notification_widget.active:focus,
.open > .dropdown-toggle.notification_widget:focus,
.notification_widget:active.focus,
.notification_widget.active.focus,
.open > .dropdown-toggle.notification_widget.focus {
  color: #333;
  background-color: #d4d4d4;
  border-color: #8c8c8c;
}
.notification_widget:active,
.notification_widget.active,
.open > .dropdown-toggle.notification_widget {
  background-image: none;
}
.notification_widget.disabled:hover,
.notification_widget[disabled]:hover,
fieldset[disabled] .notification_widget:hover,
.notification_widget.disabled:focus,
.notification_widget[disabled]:focus,
fieldset[disabled] .notification_widget:focus,
.notification_widget.disabled.focus,
.notification_widget[disabled].focus,
fieldset[disabled] .notification_widget.focus {
  background-color: #fff;
  border-color: #ccc;
}
.notification_widget .badge {
  color: #fff;
  background-color: #333;
}
.notification_widget.warning {
  color: #fff;
  background-color: #f0ad4e;
  border-color: #eea236;
}
.notification_widget.warning:focus,
.notification_widget.warning.focus {
  color: #fff;
  background-color: #ec971f;
  border-color: #985f0d;
}
.notification_widget.warning:hover {
  color: #fff;
  background-color: #ec971f;
  border-color: #d58512;
}
.notification_widget.warning:active,
.notification_widget.warning.active,
.open > .dropdown-toggle.notification_widget.warning {
  color: #fff;
  background-color: #ec971f;
  border-color: #d58512;
}
.notification_widget.warning:active:hover,
.notification_widget.warning.active:hover,
.open > .dropdown-toggle.notification_widget.warning:hover,
.notification_widget.warning:active:focus,
.notification_widget.warning.active:focus,
.open > .dropdown-toggle.notification_widget.warning:focus,
.notification_widget.warning:active.focus,
.notification_widget.warning.active.focus,
.open > .dropdown-toggle.notification_widget.warning.focus {
  color: #fff;
  background-color: #d58512;
  border-color: #985f0d;
}
.notification_widget.warning:active,
.notification_widget.warning.active,
.open > .dropdown-toggle.notification_widget.warning {
  background-image: none;
}
.notification_widget.warning.disabled:hover,
.notification_widget.warning[disabled]:hover,
fieldset[disabled] .notification_widget.warning:hover,
.notification_widget.warning.disabled:focus,
.notification_widget.warning[disabled]:focus,
fieldset[disabled] .notification_widget.warning:focus,
.notification_widget.warning.disabled.focus,
.notification_widget.warning[disabled].focus,
fieldset[disabled] .notification_widget.warning.focus {
  background-color: #f0ad4e;
  border-color: #eea236;
}
.notification_widget.warning .badge {
  color: #f0ad4e;
  background-color: #fff;
}
.notification_widget.success {
  color: #fff;
  background-color: #5cb85c;
  border-color: #4cae4c;
}
.notification_widget.success:focus,
.notification_widget.success.focus {
  color: #fff;
  background-color: #449d44;
  border-color: #255625;
}
.notification_widget.success:hover {
  color: #fff;
  background-color: #449d44;
  border-color: #398439;
}
.notification_widget.success:active,
.notification_widget.success.active,
.open > .dropdown-toggle.notification_widget.success {
  color: #fff;
  background-color: #449d44;
  border-color: #398439;
}
.notification_widget.success:active:hover,
.notification_widget.success.active:hover,
.open > .dropdown-toggle.notification_widget.success:hover,
.notification_widget.success:active:focus,
.notification_widget.success.active:focus,
.open > .dropdown-toggle.notification_widget.success:focus,
.notification_widget.success:active.focus,
.notification_widget.success.active.focus,
.open > .dropdown-toggle.notification_widget.success.focus {
  color: #fff;
  background-color: #398439;
  border-color: #255625;
}
.notification_widget.success:active,
.notification_widget.success.active,
.open > .dropdown-toggle.notification_widget.success {
  background-image: none;
}
.notification_widget.success.disabled:hover,
.notification_widget.success[disabled]:hover,
fieldset[disabled] .notification_widget.success:hover,
.notification_widget.success.disabled:focus,
.notification_widget.success[disabled]:focus,
fieldset[disabled] .notification_widget.success:focus,
.notification_widget.success.disabled.focus,
.notification_widget.success[disabled].focus,
fieldset[disabled] .notification_widget.success.focus {
  background-color: #5cb85c;
  border-color: #4cae4c;
}
.notification_widget.success .badge {
  color: #5cb85c;
  background-color: #fff;
}
.notification_widget.info {
  color: #fff;
  background-color: #5bc0de;
  border-color: #46b8da;
}
.notification_widget.info:focus,
.notification_widget.info.focus {
  color: #fff;
  background-color: #31b0d5;
  border-color: #1b6d85;
}
.notification_widget.info:hover {
  color: #fff;
  background-color: #31b0d5;
  border-color: #269abc;
}
.notification_widget.info:active,
.notification_widget.info.active,
.open > .dropdown-toggle.notification_widget.info {
  color: #fff;
  background-color: #31b0d5;
  border-color: #269abc;
}
.notification_widget.info:active:hover,
.notification_widget.info.active:hover,
.open > .dropdown-toggle.notification_widget.info:hover,
.notification_widget.info:active:focus,
.notification_widget.info.active:focus,
.open > .dropdown-toggle.notification_widget.info:focus,
.notification_widget.info:active.focus,
.notification_widget.info.active.focus,
.open > .dropdown-toggle.notification_widget.info.focus {
  color: #fff;
  background-color: #269abc;
  border-color: #1b6d85;
}
.notification_widget.info:active,
.notification_widget.info.active,
.open > .dropdown-toggle.notification_widget.info {
  background-image: none;
}
.notification_widget.info.disabled:hover,
.notification_widget.info[disabled]:hover,
fieldset[disabled] .notification_widget.info:hover,
.notification_widget.info.disabled:focus,
.notification_widget.info[disabled]:focus,
fieldset[disabled] .notification_widget.info:focus,
.notification_widget.info.disabled.focus,
.notification_widget.info[disabled].focus,
fieldset[disabled] .notification_widget.info.focus {
  background-color: #5bc0de;
  border-color: #46b8da;
}
.notification_widget.info .badge {
  color: #5bc0de;
  background-color: #fff;
}
.notification_widget.danger {
  color: #fff;
  background-color: #d9534f;
  border-color: #d43f3a;
}
.notification_widget.danger:focus,
.notification_widget.danger.focus {
  color: #fff;
  background-color: #c9302c;
  border-color: #761c19;
}
.notification_widget.danger:hover {
  color: #fff;
  background-color: #c9302c;
  border-color: #ac2925;
}
.notification_widget.danger:active,
.notification_widget.danger.active,
.open > .dropdown-toggle.notification_widget.danger {
  color: #fff;
  background-color: #c9302c;
  border-color: #ac2925;
}
.notification_widget.danger:active:hover,
.notification_widget.danger.active:hover,
.open > .dropdown-toggle.notification_widget.danger:hover,
.notification_widget.danger:active:focus,
.notification_widget.danger.active:focus,
.open > .dropdown-toggle.notification_widget.danger:focus,
.notification_widget.danger:active.focus,
.notification_widget.danger.active.focus,
.open > .dropdown-toggle.notification_widget.danger.focus {
  color: #fff;
  background-color: #ac2925;
  border-color: #761c19;
}
.notification_widget.danger:active,
.notification_widget.danger.active,
.open > .dropdown-toggle.notification_widget.danger {
  background-image: none;
}
.notification_widget.danger.disabled:hover,
.notification_widget.danger[disabled]:hover,
fieldset[disabled] .notification_widget.danger:hover,
.notification_widget.danger.disabled:focus,
.notification_widget.danger[disabled]:focus,
fieldset[disabled] .notification_widget.danger:focus,
.notification_widget.danger.disabled.focus,
.notification_widget.danger[disabled].focus,
fieldset[disabled] .notification_widget.danger.focus {
  background-color: #d9534f;
  border-color: #d43f3a;
}
.notification_widget.danger .badge {
  color: #d9534f;
  background-color: #fff;
}
div#pager {
  background-color: #fff;
  font-size: 14px;
  line-height: 20px;
  overflow: hidden;
  display: none;
  position: fixed;
  bottom: 0px;
  width: 100%;
  max-height: 50%;
  padding-top: 8px;
  -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  /* Display over codemirror */
  z-index: 100;
  /* Hack which prevents jquery ui resizable from changing top. */
  top: auto !important;
}
div#pager pre {
  line-height: 1.21429em;
  color: #000;
  background-color: #f7f7f7;
  padding: 0.4em;
}
div#pager #pager-button-area {
  position: absolute;
  top: 8px;
  right: 20px;
}
div#pager #pager-contents {
  position: relative;
  overflow: auto;
  width: 100%;
  height: 100%;
}
div#pager #pager-contents #pager-container {
  position: relative;
  padding: 15px 0px;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
div#pager .ui-resizable-handle {
  top: 0px;
  height: 8px;
  background: #f7f7f7;
  border-top: 1px solid #cfcfcf;
  border-bottom: 1px solid #cfcfcf;
  /* This injects handle bars (a short, wide = symbol) for 
        the resize handle. */
}
div#pager .ui-resizable-handle::after {
  content: '';
  top: 2px;
  left: 50%;
  height: 3px;
  width: 30px;
  margin-left: -15px;
  position: absolute;
  border-top: 1px solid #cfcfcf;
}
.quickhelp {
  /* Old browsers */
  display: -webkit-box;
  -webkit-box-orient: horizontal;
  -webkit-box-align: stretch;
  display: -moz-box;
  -moz-box-orient: horizontal;
  -moz-box-align: stretch;
  display: box;
  box-orient: horizontal;
  box-align: stretch;
  /* Modern browsers */
  display: flex;
  flex-direction: row;
  align-items: stretch;
  line-height: 1.8em;
}
.shortcut_key {
  display: inline-block;
  width: 21ex;
  text-align: right;
  font-family: monospace;
}
.shortcut_descr {
  display: inline-block;
  /* Old browsers */
  -webkit-box-flex: 1;
  -moz-box-flex: 1;
  box-flex: 1;
  /* Modern browsers */
  flex: 1;
}
span.save_widget {
  height: 30px;
  margin-top: 4px;
  display: flex;
  justify-content: flex-start;
  align-items: baseline;
  width: 50%;
  flex: 1;
}
span.save_widget span.filename {
  height: 100%;
  line-height: 1em;
  margin-left: 16px;
  border: none;
  font-size: 146.5%;
  text-overflow: ellipsis;
  overflow: hidden;
  white-space: nowrap;
  border-radius: 2px;
}
span.save_widget span.filename:hover {
  background-color: #e6e6e6;
}
[dir="rtl"] span.save_widget.pull-left {
  float: right !important;
  float: right;
}
[dir="rtl"] span.save_widget span.filename {
  margin-left: 0;
  margin-right: 16px;
}
span.checkpoint_status,
span.autosave_status {
  font-size: small;
  white-space: nowrap;
  padding: 0 5px;
}
@media (max-width: 767px) {
  span.save_widget {
    font-size: small;
    padding: 0 0 0 5px;
  }
  span.checkpoint_status,
  span.autosave_status {
    display: none;
  }
}
@media (min-width: 768px) and (max-width: 991px) {
  span.checkpoint_status {
    display: none;
  }
  span.autosave_status {
    font-size: x-small;
  }
}
.toolbar {
  padding: 0px;
  margin-left: -5px;
  margin-top: 2px;
  margin-bottom: 5px;
  box-sizing: border-box;
  -moz-box-sizing: border-box;
  -webkit-box-sizing: border-box;
}
.toolbar select,
.toolbar label {
  width: auto;
  vertical-align: middle;
  margin-right: 2px;
  margin-bottom: 0px;
  display: inline;
  font-size: 92%;
  margin-left: 0.3em;
  margin-right: 0.3em;
  padding: 0px;
  padding-top: 3px;
}
.toolbar .btn {
  padding: 2px 8px;
}
.toolbar .btn-group {
  margin-top: 0px;
  margin-left: 5px;
}
.toolbar-btn-label {
  margin-left: 6px;
}
#maintoolbar {
  margin-bottom: -3px;
  margin-top: -8px;
  border: 0px;
  min-height: 27px;
  margin-left: 0px;
  padding-top: 11px;
  padding-bottom: 3px;
}
#maintoolbar .navbar-text {
  float: none;
  vertical-align: middle;
  text-align: right;
  margin-left: 5px;
  margin-right: 0px;
  margin-top: 0px;
}
.select-xs {
  height: 24px;
}
[dir="rtl"] .btn-group > .btn,
.btn-group-vertical > .btn {
  float: right;
}
.pulse,
.dropdown-menu > li > a.pulse,
li.pulse > a.dropdown-toggle,
li.pulse.open > a.dropdown-toggle {
  background-color: #F37626;
  color: white;
}
/**
 * Primary styles
 *
 * Author: Jupyter Development Team
 */
/** WARNING IF YOU ARE EDITTING THIS FILE, if this is a .css file, It has a lot
 * of chance of beeing generated from the ../less/[samename].less file, you can
 * try to get back the less file by reverting somme commit in history
 **/
/*
 * We'll try to get something pretty, so we
 * have some strange css to have the scroll bar on
 * the left with fix button on the top right of the tooltip
 */
@-moz-keyframes fadeOut {
  from {
    opacity: 1;
  }
  to {
    opacity: 0;
  }
}
@-webkit-keyframes fadeOut {
  from {
    opacity: 1;
  }
  to {
    opacity: 0;
  }
}
@-moz-keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
@-webkit-keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
/*properties of tooltip after "expand"*/
.bigtooltip {
  overflow: auto;
  height: 200px;
  -webkit-transition-property: height;
  -webkit-transition-duration: 500ms;
  -moz-transition-property: height;
  -moz-transition-duration: 500ms;
  transition-property: height;
  transition-duration: 500ms;
}
/*properties of tooltip before "expand"*/
.smalltooltip {
  -webkit-transition-property: height;
  -webkit-transition-duration: 500ms;
  -moz-transition-property: height;
  -moz-transition-duration: 500ms;
  transition-property: height;
  transition-duration: 500ms;
  text-overflow: ellipsis;
  overflow: hidden;
  height: 80px;
}
.tooltipbuttons {
  position: absolute;
  padding-right: 15px;
  top: 0px;
  right: 0px;
}
.tooltiptext {
  /*avoid the button to overlap on some docstring*/
  padding-right: 30px;
}
.ipython_tooltip {
  max-width: 700px;
  /*fade-in animation when inserted*/
  -webkit-animation: fadeOut 400ms;
  -moz-animation: fadeOut 400ms;
  animation: fadeOut 400ms;
  -webkit-animation: fadeIn 400ms;
  -moz-animation: fadeIn 400ms;
  animation: fadeIn 400ms;
  vertical-align: middle;
  background-color: #f7f7f7;
  overflow: visible;
  border: #ababab 1px solid;
  outline: none;
  padding: 3px;
  margin: 0px;
  padding-left: 7px;
  font-family: monospace;
  min-height: 50px;
  -moz-box-shadow: 0px 6px 10px -1px #adadad;
  -webkit-box-shadow: 0px 6px 10px -1px #adadad;
  box-shadow: 0px 6px 10px -1px #adadad;
  border-radius: 2px;
  position: absolute;
  z-index: 1000;
}
.ipython_tooltip a {
  float: right;
}
.ipython_tooltip .tooltiptext pre {
  border: 0;
  border-radius: 0;
  font-size: 100%;
  background-color: #f7f7f7;
}
.pretooltiparrow {
  left: 0px;
  margin: 0px;
  top: -16px;
  width: 40px;
  height: 16px;
  overflow: hidden;
  position: absolute;
}
.pretooltiparrow:before {
  background-color: #f7f7f7;
  border: 1px #ababab solid;
  z-index: 11;
  content: "";
  position: absolute;
  left: 15px;
  top: 10px;
  width: 25px;
  height: 25px;
  -webkit-transform: rotate(45deg);
  -moz-transform: rotate(45deg);
  -ms-transform: rotate(45deg);
  -o-transform: rotate(45deg);
}
ul.typeahead-list i {
  margin-left: -10px;
  width: 18px;
}
[dir="rtl"] ul.typeahead-list i {
  margin-left: 0;
  margin-right: -10px;
}
ul.typeahead-list {
  max-height: 80vh;
  overflow: auto;
}
ul.typeahead-list > li > a {
  /** Firefox bug **/
  /* see https://github.com/jupyter/notebook/issues/559 */
  white-space: normal;
}
ul.typeahead-list  > li > a.pull-right {
  float: left !important;
  float: left;
}
[dir="rtl"] .typeahead-list {
  text-align: right;
}
.cmd-palette .modal-body {
  padding: 7px;
}
.cmd-palette form {
  background: white;
}
.cmd-palette input {
  outline: none;
}
.no-shortcut {
  min-width: 20px;
  color: transparent;
}
[dir="rtl"] .no-shortcut.pull-right {
  float: left !important;
  float: left;
}
[dir="rtl"] .command-shortcut.pull-right {
  float: left !important;
  float: left;
}
.command-shortcut:before {
  content: "(command mode)";
  padding-right: 3px;
  color: #777777;
}
.edit-shortcut:before {
  content: "(edit)";
  padding-right: 3px;
  color: #777777;
}
[dir="rtl"] .edit-shortcut.pull-right {
  float: left !important;
  float: left;
}
#find-and-replace #replace-preview .match,
#find-and-replace #replace-preview .insert {
  background-color: #BBDEFB;
  border-color: #90CAF9;
  border-style: solid;
  border-width: 1px;
  border-radius: 0px;
}
[dir="ltr"] #find-and-replace .input-group-btn + .form-control {
  border-left: none;
}
[dir="rtl"] #find-and-replace .input-group-btn + .form-control {
  border-right: none;
}
#find-and-replace #replace-preview .replace .match {
  background-color: #FFCDD2;
  border-color: #EF9A9A;
  border-radius: 0px;
}
#find-and-replace #replace-preview .replace .insert {
  background-color: #C8E6C9;
  border-color: #A5D6A7;
  border-radius: 0px;
}
#find-and-replace #replace-preview {
  max-height: 60vh;
  overflow: auto;
}
#find-and-replace #replace-preview pre {
  padding: 5px 10px;
}
.terminal-app {
  background: #EEE;
}
.terminal-app #header {
  background: #fff;
  -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
  box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.2);
}
.terminal-app .terminal {
  width: 100%;
  float: left;
  font-family: monospace;
  color: white;
  background: black;
  padding: 0.4em;
  border-radius: 2px;
  -webkit-box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.4);
  box-shadow: 0px 0px 12px 1px rgba(87, 87, 87, 0.4);
}
.terminal-app .terminal,
.terminal-app .terminal dummy-screen {
  line-height: 1em;
  font-size: 14px;
}
.terminal-app .terminal .xterm-rows {
  padding: 10px;
}
.terminal-app .terminal-cursor {
  color: black;
  background: white;
}
.terminal-app #terminado-container {
  margin-top: 20px;
}
/*# sourceMappingURL=style.min.css.map */
    </style>
<style type="text/css">
    .highlight .hll { background-color: #ffffcc }
.highlight  { background: #f8f8f8; }
.highlight .c { color: #408080; font-style: italic } /* Comment */
.highlight .err { border: 1px solid #FF0000 } /* Error */
.highlight .k { color: #008000; font-weight: bold } /* Keyword */
.highlight .o { color: #666666 } /* Operator */
.highlight .ch { color: #408080; font-style: italic } /* Comment.Hashbang */
.highlight .cm { color: #408080; font-style: italic } /* Comment.Multiline */
.highlight .cp { color: #BC7A00 } /* Comment.Preproc */
.highlight .cpf { color: #408080; font-style: italic } /* Comment.PreprocFile */
.highlight .c1 { color: #408080; font-style: italic } /* Comment.Single */
.highlight .cs { color: #408080; font-style: italic } /* Comment.Special */
.highlight .gd { color: #A00000 } /* Generic.Deleted */
.highlight .ge { font-style: italic } /* Generic.Emph */
.highlight .gr { color: #FF0000 } /* Generic.Error */
.highlight .gh { color: #000080; font-weight: bold } /* Generic.Heading */
.highlight .gi { color: #00A000 } /* Generic.Inserted */
.highlight .go { color: #888888 } /* Generic.Output */
.highlight .gp { color: #000080; font-weight: bold } /* Generic.Prompt */
.highlight .gs { font-weight: bold } /* Generic.Strong */
.highlight .gu { color: #800080; font-weight: bold } /* Generic.Subheading */
.highlight .gt { color: #0044DD } /* Generic.Traceback */
.highlight .kc { color: #008000; font-weight: bold } /* Keyword.Constant */
.highlight .kd { color: #008000; font-weight: bold } /* Keyword.Declaration */
.highlight .kn { color: #008000; font-weight: bold } /* Keyword.Namespace */
.highlight .kp { color: #008000 } /* Keyword.Pseudo */
.highlight .kr { color: #008000; font-weight: bold } /* Keyword.Reserved */
.highlight .kt { color: #B00040 } /* Keyword.Type */
.highlight .m { color: #666666 } /* Literal.Number */
.highlight .s { color: #BA2121 } /* Literal.String */
.highlight .na { color: #7D9029 } /* Name.Attribute */
.highlight .nb { color: #008000 } /* Name.Builtin */
.highlight .nc { color: #0000FF; font-weight: bold } /* Name.Class */
.highlight .no { color: #880000 } /* Name.Constant */
.highlight .nd { color: #AA22FF } /* Name.Decorator */
.highlight .ni { color: #999999; font-weight: bold } /* Name.Entity */
.highlight .ne { color: #D2413A; font-weight: bold } /* Name.Exception */
.highlight .nf { color: #0000FF } /* Name.Function */
.highlight .nl { color: #A0A000 } /* Name.Label */
.highlight .nn { color: #0000FF; font-weight: bold } /* Name.Namespace */
.highlight .nt { color: #008000; font-weight: bold } /* Name.Tag */
.highlight .nv { color: #19177C } /* Name.Variable */
.highlight .ow { color: #AA22FF; font-weight: bold } /* Operator.Word */
.highlight .w { color: #bbbbbb } /* Text.Whitespace */
.highlight .mb { color: #666666 } /* Literal.Number.Bin */
.highlight .mf { color: #666666 } /* Literal.Number.Float */
.highlight .mh { color: #666666 } /* Literal.Number.Hex */
.highlight .mi { color: #666666 } /* Literal.Number.Integer */
.highlight .mo { color: #666666 } /* Literal.Number.Oct */
.highlight .sa { color: #BA2121 } /* Literal.String.Affix */
.highlight .sb { color: #BA2121 } /* Literal.String.Backtick */
.highlight .sc { color: #BA2121 } /* Literal.String.Char */
.highlight .dl { color: #BA2121 } /* Literal.String.Delimiter */
.highlight .sd { color: #BA2121; font-style: italic } /* Literal.String.Doc */
.highlight .s2 { color: #BA2121 } /* Literal.String.Double */
.highlight .se { color: #BB6622; font-weight: bold } /* Literal.String.Escape */
.highlight .sh { color: #BA2121 } /* Literal.String.Heredoc */
.highlight .si { color: #BB6688; font-weight: bold } /* Literal.String.Interpol */
.highlight .sx { color: #008000 } /* Literal.String.Other */
.highlight .sr { color: #BB6688 } /* Literal.String.Regex */
.highlight .s1 { color: #BA2121 } /* Literal.String.Single */
.highlight .ss { color: #19177C } /* Literal.String.Symbol */
.highlight .bp { color: #008000 } /* Name.Builtin.Pseudo */
.highlight .fm { color: #0000FF } /* Name.Function.Magic */
.highlight .vc { color: #19177C } /* Name.Variable.Class */
.highlight .vg { color: #19177C } /* Name.Variable.Global */
.highlight .vi { color: #19177C } /* Name.Variable.Instance */
.highlight .vm { color: #19177C } /* Name.Variable.Magic */
.highlight .il { color: #666666 } /* Literal.Number.Integer.Long */
    </style>
<style type="text/css">
    
/* Temporary definitions which will become obsolete with Notebook release 5.0 */
.ansi-black-fg { color: #3E424D; }
.ansi-black-bg { background-color: #3E424D; }
.ansi-black-intense-fg { color: #282C36; }
.ansi-black-intense-bg { background-color: #282C36; }
.ansi-red-fg { color: #E75C58; }
.ansi-red-bg { background-color: #E75C58; }
.ansi-red-intense-fg { color: #B22B31; }
.ansi-red-intense-bg { background-color: #B22B31; }
.ansi-green-fg { color: #00A250; }
.ansi-green-bg { background-color: #00A250; }
.ansi-green-intense-fg { color: #007427; }
.ansi-green-intense-bg { background-color: #007427; }
.ansi-yellow-fg { color: #DDB62B; }
.ansi-yellow-bg { background-color: #DDB62B; }
.ansi-yellow-intense-fg { color: #B27D12; }
.ansi-yellow-intense-bg { background-color: #B27D12; }
.ansi-blue-fg { color: #208FFB; }
.ansi-blue-bg { background-color: #208FFB; }
.ansi-blue-intense-fg { color: #0065CA; }
.ansi-blue-intense-bg { background-color: #0065CA; }
.ansi-magenta-fg { color: #D160C4; }
.ansi-magenta-bg { background-color: #D160C4; }
.ansi-magenta-intense-fg { color: #A03196; }
.ansi-magenta-intense-bg { background-color: #A03196; }
.ansi-cyan-fg { color: #60C6C8; }
.ansi-cyan-bg { background-color: #60C6C8; }
.ansi-cyan-intense-fg { color: #258F8F; }
.ansi-cyan-intense-bg { background-color: #258F8F; }
.ansi-white-fg { color: #C5C1B4; }
.ansi-white-bg { background-color: #C5C1B4; }
.ansi-white-intense-fg { color: #A1A6B2; }
.ansi-white-intense-bg { background-color: #A1A6B2; }

.ansi-bold { font-weight: bold; }

    </style>


<style type="text/css">
/* Overrides of notebook CSS for static HTML export */
body {
  overflow: visible;
  padding: 8px;
}

div#notebook {
  overflow: visible;
  border-top: none;
}@media print {
  div.cell {
    display: block;
    page-break-inside: avoid;
  } 
  div.output_wrapper { 
    display: block;
    page-break-inside: avoid; 
  }
  div.output { 
    display: block;
    page-break-inside: avoid; 
  }
}
</style>

<!-- Custom stylesheet, it must be in the same directory as the html file -->
<link rel="stylesheet" href="custom.css">

<!-- Loading mathjax macro -->
<!-- Load mathjax -->
    <script src="https://cdnjs.cloudflare.com/ajax/libs/mathjax/2.7.5/latest.js?config=TeX-AMS_HTML"></script>
    <!-- MathJax configuration -->
    <script type="text/x-mathjax-config">
    MathJax.Hub.Config({
        tex2jax: {
            inlineMath: [ ['$','$'], ["\\(","\\)"] ],
            displayMath: [ ['$$','$$'], ["\\[","\\]"] ],
            processEscapes: true,
            processEnvironments: true
        },
        // Center justify equations in code and markdown cells. Elsewhere
        // we use CSS to left justify single line equations in code cells.
        displayAlign: 'center',
        "HTML-CSS": {
            styles: {'.MathJax_Display': {"margin": 0}},
            linebreaks: { automatic: true }
        }
    });
    </script>
    <!-- End of mathjax configuration --></head>
<body>
  <div tabindex="-1" id="notebook" class="border-box-sizing">
    <div class="container" id="notebook-container">

<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Import Libraries Needed</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[1]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="o">!</span>pip install pyreadr
<span class="kn">import</span> <span class="nn">pyreadr</span>
<span class="kn">import</span> <span class="nn">numpy</span> <span class="k">as</span> <span class="nn">np</span>
<span class="kn">import</span> <span class="nn">matplotlib</span>
<span class="kn">import</span> <span class="nn">matplotlib.pyplot</span> <span class="k">as</span> <span class="nn">plt</span>
<span class="kn">import</span> <span class="nn">itertools</span> <span class="k">as</span> <span class="nn">it</span>
<span class="kn">import</span> <span class="nn">pandas</span> <span class="k">as</span> <span class="nn">pd</span>
<span class="kn">from</span> <span class="nn">pandas.plotting</span> <span class="k">import</span> <span class="n">scatter_matrix</span>
<span class="kn">import</span> <span class="nn">scipy</span>
<span class="kn">import</span> <span class="nn">numpy</span> <span class="k">as</span> <span class="nn">np</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Requirement already satisfied: pyreadr in /miniconda3/lib/python3.7/site-packages (0.2.1)
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Import Specific Functions</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[2]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">tensorflow.keras.models</span> <span class="k">import</span> <span class="n">Sequential</span>
<span class="kn">from</span> <span class="nn">tensorflow.keras.layers</span> <span class="k">import</span> <span class="n">Dense</span>
<span class="kn">from</span> <span class="nn">tensorflow.keras.layers</span> <span class="k">import</span> <span class="n">Embedding</span>
<span class="kn">from</span> <span class="nn">tensorflow.keras.layers</span> <span class="k">import</span> <span class="n">Flatten</span>
<span class="kn">from</span> <span class="nn">tensorflow.keras.layers</span> <span class="k">import</span> <span class="n">Dropout</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stderr output_text">
<pre>/miniconda3/lib/python3.7/site-packages/tensorflow/python/framework/dtypes.py:516: FutureWarning: Passing (type, 1) or &#39;1type&#39; as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / &#39;(1,)type&#39;.
  _np_qint8 = np.dtype([(&#34;qint8&#34;, np.int8, 1)])
/miniconda3/lib/python3.7/site-packages/tensorflow/python/framework/dtypes.py:517: FutureWarning: Passing (type, 1) or &#39;1type&#39; as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / &#39;(1,)type&#39;.
  _np_quint8 = np.dtype([(&#34;quint8&#34;, np.uint8, 1)])
/miniconda3/lib/python3.7/site-packages/tensorflow/python/framework/dtypes.py:518: FutureWarning: Passing (type, 1) or &#39;1type&#39; as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / &#39;(1,)type&#39;.
  _np_qint16 = np.dtype([(&#34;qint16&#34;, np.int16, 1)])
/miniconda3/lib/python3.7/site-packages/tensorflow/python/framework/dtypes.py:519: FutureWarning: Passing (type, 1) or &#39;1type&#39; as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / &#39;(1,)type&#39;.
  _np_quint16 = np.dtype([(&#34;quint16&#34;, np.uint16, 1)])
/miniconda3/lib/python3.7/site-packages/tensorflow/python/framework/dtypes.py:520: FutureWarning: Passing (type, 1) or &#39;1type&#39; as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / &#39;(1,)type&#39;.
  _np_qint32 = np.dtype([(&#34;qint32&#34;, np.int32, 1)])
/miniconda3/lib/python3.7/site-packages/tensorflow/python/framework/dtypes.py:525: FutureWarning: Passing (type, 1) or &#39;1type&#39; as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / &#39;(1,)type&#39;.
  np_resource = np.dtype([(&#34;resource&#34;, np.ubyte, 1)])
/miniconda3/lib/python3.7/site-packages/tensorboard/compat/tensorflow_stub/dtypes.py:541: FutureWarning: Passing (type, 1) or &#39;1type&#39; as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / &#39;(1,)type&#39;.
  _np_qint8 = np.dtype([(&#34;qint8&#34;, np.int8, 1)])
/miniconda3/lib/python3.7/site-packages/tensorboard/compat/tensorflow_stub/dtypes.py:542: FutureWarning: Passing (type, 1) or &#39;1type&#39; as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / &#39;(1,)type&#39;.
  _np_quint8 = np.dtype([(&#34;quint8&#34;, np.uint8, 1)])
/miniconda3/lib/python3.7/site-packages/tensorboard/compat/tensorflow_stub/dtypes.py:543: FutureWarning: Passing (type, 1) or &#39;1type&#39; as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / &#39;(1,)type&#39;.
  _np_qint16 = np.dtype([(&#34;qint16&#34;, np.int16, 1)])
/miniconda3/lib/python3.7/site-packages/tensorboard/compat/tensorflow_stub/dtypes.py:544: FutureWarning: Passing (type, 1) or &#39;1type&#39; as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / &#39;(1,)type&#39;.
  _np_quint16 = np.dtype([(&#34;quint16&#34;, np.uint16, 1)])
/miniconda3/lib/python3.7/site-packages/tensorboard/compat/tensorflow_stub/dtypes.py:545: FutureWarning: Passing (type, 1) or &#39;1type&#39; as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / &#39;(1,)type&#39;.
  _np_qint32 = np.dtype([(&#34;qint32&#34;, np.int32, 1)])
/miniconda3/lib/python3.7/site-packages/tensorboard/compat/tensorflow_stub/dtypes.py:550: FutureWarning: Passing (type, 1) or &#39;1type&#39; as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / &#39;(1,)type&#39;.
  np_resource = np.dtype([(&#34;resource&#34;, np.ubyte, 1)])
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Wide-Dataset">Wide Dataset<a class="anchor-link" href="#Wide-Dataset">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>In this example, I used two different datasets with different characteristics. The first is a "wide" dataset with more features but fewer cells. The second is a "Deep" dataset with fewer features and more cells. Below I will display results from each of them.</p>
<p>In the next cell, I load in the wide dataset and use .head() to verify that it is the correct file with the correct orientation.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[3]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">trainXdf</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">read_csv</span><span class="p">(</span><span class="s1">&#39;/Users/tjshruti/Downloads/PLN123_short.csv&#39;</span><span class="p">)</span>
<span class="c1">#trainXgenesDF = pd.read_csv(&#39;/Users/tjshruti/Downloads/GeneNamesPLN123.csv&#39;) </span>
<span class="n">trainXdf</span><span class="o">.</span><span class="n">head</span><span class="p">(),</span><span class="n">trainXdf</span><span class="o">.</span><span class="n">shape</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[3]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>(   Unnamed: 0              Row.names    V2.x        V5   V6        V7  \
 0           1  AAACCTGAGAGGGCTT_PLN2     CRP  0.728004  0.0  0.498859   
 1           2  AAACCTGAGCCGGTAA_PLN2    TrEC  1.155787  0.0  0.434530   
 2           3  AAACCTGAGCGCTTAT_PLN2    TrEC  0.987962  0.0  1.619479   
 3           4  AAACCTGAGCTGCCCA_PLN2  CapEC1  0.270323  0.0  0.448402   
 4           5  AAACCTGAGGCGCTCT_PLN2    TrEC  0.873254  0.0  0.374109   
 
          V8   V9       V10  V11   ...    V31046  V31047  V31048    V31049  \
 0  0.806498  0.0  1.630390  0.0   ...       0.0       0     0.0  0.000000   
 1  0.787668  0.0  1.474877  0.0   ...       0.0       0     0.0  0.766109   
 2  0.896746  0.0  1.733865  0.0   ...       0.0       0     0.0  0.000000   
 3  1.104601  0.0  1.905492  0.0   ...       0.0       0     0.0  0.000000   
 4  0.539635  0.0  1.324466  0.0   ...       0.0       0     0.0  0.000000   
 
      V31050    V31051  V31052    V31053  V31054  V31055  
 0  0.508397  0.115372       0  0.128194       0       0  
 1  0.180571  0.790527       0  0.000000       0       0  
 2  0.490711  0.803168       0  0.000000       0       0  
 3  0.607256  0.964530       0  0.165783       0       0  
 4  0.418944  0.194616       0  0.825784       0       0  
 
 [5 rows x 31054 columns], (7592, 31054))</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>set as array for further manipulation</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[4]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">trainXarr</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">asarray</span><span class="p">(</span><span class="n">trainXdf</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>In this example, I am selectively removing cells labeled as ambiguous. This is optional.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[5]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">drops</span> <span class="o">=</span> <span class="n">trainXarr</span><span class="p">[:,</span><span class="mi">2</span><span class="p">]</span><span class="o">==</span><span class="s1">&#39;ambig&#39;</span>
<span class="n">drops</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">transpose</span><span class="p">(</span><span class="n">drops</span><span class="p">)</span>
<span class="n">drops</span> <span class="o">=</span> <span class="p">[</span><span class="ow">not</span> <span class="n">y</span> <span class="k">for</span> <span class="n">y</span> <span class="ow">in</span> <span class="n">drops</span><span class="p">]</span>
<span class="n">trainXarr</span> <span class="o">=</span> <span class="n">trainXarr</span><span class="p">[</span><span class="n">drops</span><span class="p">]</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[6]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">trainXarr</span><span class="o">.</span><span class="n">shape</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[6]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>(7453, 31054)</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Separating data from labels</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[7]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">X</span> <span class="o">=</span> <span class="n">trainXarr</span><span class="p">[:,</span><span class="mi">3</span><span class="p">:</span><span class="mi">31055</span><span class="p">]</span>
<span class="n">Y_Arr</span> <span class="o">=</span> <span class="n">trainXarr</span><span class="p">[:,</span><span class="mi">2</span><span class="p">]</span>
<span class="n">Y_Arr</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[7]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>array([&#39;CRP&#39;, &#39;TrEC&#39;, &#39;TrEC&#39;, ..., &#39;CapEC2&#39;, &#39;CapEC2&#39;, &#39;HEV&#39;],
      dtype=object)</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Converting from string to int datatype, see labels below.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[8]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># TrEC = 0</span>
<span class="c1"># HEC / HEC late = 1</span>
<span class="c1"># CapEC1/2 = 2</span>
<span class="c1"># CRP / CRP Early = 3</span>
<span class="c1"># HEV = 1</span>
<span class="c1"># Pre-Art = 5</span>
<span class="c1"># Vn = 4</span>
<span class="c1"># Art = 5</span>
<span class="c1"># CapIfn = 6</span>


<span class="n">Y_Arr1</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">zeros</span><span class="p">((</span><span class="mi">7453</span><span class="p">,</span> <span class="mi">1</span><span class="p">))</span>
<span class="k">for</span> <span class="n">x</span> <span class="ow">in</span> <span class="nb">range</span><span class="p">(</span><span class="mi">7453</span><span class="p">):</span>
    <span class="k">if</span> <span class="p">(</span><span class="n">Y_Arr</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">==</span> <span class="s1">&#39;TrEC&#39;</span><span class="p">):</span>
        <span class="n">Y_Arr1</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">=</span> <span class="mi">0</span>
    <span class="k">elif</span> <span class="p">(</span><span class="n">Y_Arr</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">==</span> <span class="s1">&#39;HEC&#39;</span><span class="p">):</span>
        <span class="n">Y_Arr1</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">=</span> <span class="mi">1</span>
    <span class="k">elif</span> <span class="p">(</span><span class="n">Y_Arr</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">==</span> <span class="s1">&#39;HEC (late)&#39;</span><span class="p">):</span>
        <span class="n">Y_Arr1</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">=</span> <span class="mi">1</span>
    <span class="k">elif</span><span class="p">(</span><span class="n">Y_Arr</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">==</span> <span class="s1">&#39;CapEC1&#39;</span><span class="p">):</span>
        <span class="n">Y_Arr1</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">=</span> <span class="mi">2</span>
    <span class="k">elif</span> <span class="p">(</span><span class="n">Y_Arr</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">==</span> <span class="s1">&#39;CapEC2&#39;</span><span class="p">):</span>
        <span class="n">Y_Arr1</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">=</span> <span class="mi">2</span>
    <span class="k">elif</span> <span class="p">(</span><span class="n">Y_Arr</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">==</span> <span class="s1">&#39;CRP&#39;</span><span class="p">):</span>
        <span class="n">Y_Arr1</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">=</span> <span class="mi">3</span>
    <span class="k">elif</span> <span class="p">(</span><span class="n">Y_Arr</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">==</span> <span class="s1">&#39;HEV&#39;</span><span class="p">):</span>
        <span class="n">Y_Arr1</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">=</span> <span class="mi">1</span>
    <span class="k">elif</span> <span class="p">(</span><span class="n">Y_Arr</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">==</span> <span class="s1">&#39;Pre-Art&#39;</span><span class="p">):</span>
        <span class="n">Y_Arr1</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">=</span> <span class="mi">5</span>
    <span class="k">elif</span> <span class="p">(</span><span class="n">Y_Arr</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">==</span> <span class="s1">&#39;CRP (early)&#39;</span><span class="p">):</span>
        <span class="n">Y_Arr1</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">=</span> <span class="mi">3</span>
    <span class="k">elif</span><span class="p">(</span><span class="n">Y_Arr</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">==</span> <span class="s1">&#39;Vn&#39;</span><span class="p">):</span>
        <span class="n">Y_Arr1</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">=</span> <span class="mi">4</span>
    <span class="k">elif</span><span class="p">(</span><span class="n">Y_Arr</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">==</span> <span class="s1">&#39;Art&#39;</span><span class="p">):</span>
        <span class="n">Y_Arr1</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">=</span> <span class="mi">5</span>
    <span class="k">elif</span><span class="p">(</span><span class="n">Y_Arr</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">==</span> <span class="s1">&#39;CapIfn&#39;</span><span class="p">):</span>
        <span class="n">Y_Arr1</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">=</span> <span class="mi">6</span>
   
        
<span class="n">Y_Arr1</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[8]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>array([[3.],
       [0.],
       [0.],
       ...,
       [2.],
       [2.],
       [1.]])</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Create train test split where data and labels are mixed and separated into groups. This allows us to train our model and then verify with remaining data</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[9]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">sklearn.model_selection</span> <span class="k">import</span> <span class="n">train_test_split</span>

<span class="n">trainX</span><span class="p">,</span> <span class="n">testX</span><span class="p">,</span> <span class="n">trainY</span><span class="p">,</span> <span class="n">testY</span> <span class="o">=</span> <span class="n">train_test_split</span><span class="p">(</span><span class="n">X</span><span class="p">,</span> <span class="n">Y_Arr1</span><span class="p">,</span> <span class="n">train_size</span> <span class="o">=</span> <span class="mf">0.9</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[10]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">trainX</span><span class="o">.</span><span class="n">shape</span><span class="p">,</span> <span class="n">trainY</span><span class="o">.</span><span class="n">shape</span><span class="p">,</span> <span class="n">testX</span><span class="o">.</span><span class="n">shape</span><span class="p">,</span> <span class="n">testY</span><span class="o">.</span><span class="n">shape</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[10]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>((6707, 31051), (6707, 1), (746, 31051), (746, 1))</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Below we implement our classifier structure. In this example, there are four layers. The two internal layers can be manipulated for higher accuracy, but the input layer must match the number of features in the dataset, and the output layer must match the total number of classifications to be used.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[11]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">classifier</span> <span class="o">=</span> <span class="n">Sequential</span><span class="p">()</span>
<span class="n">classifier</span><span class="o">.</span><span class="n">add</span><span class="p">(</span><span class="n">Dense</span><span class="p">(</span><span class="mi">25</span><span class="p">,</span> <span class="n">activation</span><span class="o">=</span><span class="s1">&#39;relu&#39;</span><span class="p">,</span> <span class="n">input_dim</span><span class="o">=</span><span class="mi">31051</span><span class="p">,</span> <span class="n">kernel_initializer</span><span class="o">=</span><span class="s1">&#39;random_normal&#39;</span><span class="p">))</span>
<span class="n">classifier</span><span class="o">.</span><span class="n">add</span><span class="p">(</span><span class="n">Dense</span><span class="p">(</span><span class="mi">10</span><span class="p">,</span> <span class="n">activation</span><span class="o">=</span><span class="s1">&#39;relu&#39;</span><span class="p">,</span> <span class="n">kernel_initializer</span><span class="o">=</span><span class="s1">&#39;random_normal&#39;</span><span class="p">))</span>
<span class="n">classifier</span><span class="o">.</span><span class="n">add</span><span class="p">(</span><span class="n">Dense</span><span class="p">(</span><span class="mi">5</span><span class="p">,</span> <span class="n">activation</span><span class="o">=</span><span class="s1">&#39;relu&#39;</span><span class="p">,</span> <span class="n">kernel_initializer</span><span class="o">=</span><span class="s1">&#39;random_normal&#39;</span><span class="p">))</span>
<span class="n">classifier</span><span class="o">.</span><span class="n">add</span><span class="p">(</span><span class="n">Dense</span><span class="p">(</span><span class="mi">7</span><span class="p">,</span> <span class="n">activation</span><span class="o">=</span><span class="s1">&#39;sigmoid&#39;</span><span class="p">,</span> <span class="n">kernel_initializer</span><span class="o">=</span><span class="s1">&#39;random_normal&#39;</span><span class="p">))</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[12]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">classifier</span><span class="o">.</span><span class="n">compile</span><span class="p">(</span><span class="n">loss</span><span class="o">=</span><span class="s1">&#39;sparse_categorical_crossentropy&#39;</span><span class="p">,</span> <span class="n">optimizer</span><span class="o">=</span><span class="s1">&#39;adam&#39;</span><span class="p">,</span> <span class="n">metrics</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;accuracy&#39;</span><span class="p">])</span>
<span class="n">classifier</span><span class="o">.</span><span class="n">summary</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Model: &#34;sequential&#34;
_________________________________________________________________
Layer (type)                 Output Shape              Param #   
=================================================================
dense (Dense)                (None, 25)                776300    
_________________________________________________________________
dense_1 (Dense)              (None, 10)                260       
_________________________________________________________________
dense_2 (Dense)              (None, 5)                 55        
_________________________________________________________________
dense_3 (Dense)              (None, 7)                 42        
=================================================================
Total params: 776,657
Trainable params: 776,657
Non-trainable params: 0
_________________________________________________________________
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Now the model is trained on the training sets--which represent 90% of the data inputted. 16 epochs are used in this example, but this can be modified to save time or achieve greater accuracy.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[13]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">classifier</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">trainX</span><span class="p">,</span> <span class="n">trainY</span><span class="p">,</span> <span class="n">epochs</span> <span class="o">=</span> <span class="mi">16</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stderr output_text">
<pre>WARNING: Logging before flag parsing goes to stderr.
W1218 13:56:05.999615 4528575936 deprecation.py:323] From /miniconda3/lib/python3.7/site-packages/tensorflow/python/ops/math_grad.py:1250: add_dispatch_support.&lt;locals&gt;.wrapper (from tensorflow.python.ops.array_ops) is deprecated and will be removed in a future version.
Instructions for updating:
Use tf.where in 2.0, which has the same broadcast rule as np.where
</pre>
</div>
</div>

<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Train on 6707 samples
Epoch 1/16
6707/6707 [==============================] - 27s 4ms/sample - loss: 1.2626 - accuracy: 0.5728
Epoch 2/16
6707/6707 [==============================] - 27s 4ms/sample - loss: 0.5741 - accuracy: 0.7761
Epoch 3/16
6707/6707 [==============================] - 27s 4ms/sample - loss: 0.4152 - accuracy: 0.8299
Epoch 4/16
6707/6707 [==============================] - 26s 4ms/sample - loss: 0.3501 - accuracy: 0.8515
Epoch 5/16
6707/6707 [==============================] - 26s 4ms/sample - loss: 0.3000 - accuracy: 0.8622
Epoch 6/16
6707/6707 [==============================] - 26s 4ms/sample - loss: 0.2813 - accuracy: 0.8672
Epoch 7/16
6707/6707 [==============================] - 27s 4ms/sample - loss: 0.2361 - accuracy: 0.8771
Epoch 8/16
6707/6707 [==============================] - 26s 4ms/sample - loss: 0.2144 - accuracy: 0.8828
Epoch 9/16
6707/6707 [==============================] - 26s 4ms/sample - loss: 0.2132 - accuracy: 0.8783
Epoch 10/16
6707/6707 [==============================] - 27s 4ms/sample - loss: 0.1846 - accuracy: 0.8897
Epoch 11/16
6707/6707 [==============================] - 27s 4ms/sample - loss: 0.1715 - accuracy: 0.8921
Epoch 12/16
6707/6707 [==============================] - 27s 4ms/sample - loss: 0.1659 - accuracy: 0.8929
Epoch 13/16
6707/6707 [==============================] - 27s 4ms/sample - loss: 0.1498 - accuracy: 0.9016
Epoch 14/16
6707/6707 [==============================] - 27s 4ms/sample - loss: 0.1406 - accuracy: 0.9052
Epoch 15/16
6707/6707 [==============================] - 26s 4ms/sample - loss: 0.1467 - accuracy: 0.9034
Epoch 16/16
6707/6707 [==============================] - 26s 4ms/sample - loss: 0.1365 - accuracy: 0.9070
</pre>
</div>
</div>

<div class="output_area">

    <div class="prompt output_prompt">Out[13]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>&lt;tensorflow.python.keras.callbacks.History at 0x236fa2748&gt;</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[14]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Evaluate model accuracy on test data</span>
<span class="n">predictions</span> <span class="o">=</span> <span class="n">classifier</span><span class="o">.</span><span class="n">predict_classes</span><span class="p">(</span><span class="n">testX</span><span class="p">)</span>
<span class="n">preds</span> <span class="o">=</span> <span class="n">predictions</span><span class="o">.</span><span class="n">tolist</span><span class="p">()</span>

<span class="n">preds</span><span class="p">,</span> <span class="n">testY</span>
<span class="kn">from</span> <span class="nn">sklearn.metrics</span> <span class="k">import</span> <span class="n">accuracy_score</span>
<span class="nb">print</span><span class="p">(</span><span class="n">accuracy_score</span><span class="p">(</span><span class="n">preds</span><span class="p">,</span> <span class="n">testY</span><span class="p">)</span><span class="o">*</span><span class="mi">100</span><span class="p">)</span>
<span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">preds</span><span class="p">)</span><span class="o">.</span><span class="n">to_csv</span><span class="p">(</span><span class="s1">&#39;/Users/tjshruti/Downloads/PLN123_predictions_sept13.csv&#39;</span><span class="p">)</span>
<span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">testY</span><span class="p">)</span><span class="o">.</span><span class="n">to_csv</span><span class="p">(</span><span class="s1">&#39;/Users/tjshruti/Downloads/PLN123_actual_sept13.csv&#39;</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>86.59517426273459
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Set predictions and labels as variables for graphing</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[15]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">p</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">asarray</span><span class="p">(</span><span class="n">preds</span><span class="p">)</span>
<span class="n">t</span><span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">squeeze</span><span class="p">(</span><span class="n">testY</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="General-Histogram-for-PLN-TEST">General Histogram for PLN TEST<a class="anchor-link" href="#General-Histogram-for-PLN-TEST">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Now, we can graph our model's predictions into histograms. Below, I use matplotlib to put classifications into bins. The "general" histogram generated shows overall the actual amount of each cell type versus the prediction. This does not, however, show which classification bin each misclassified cell is moved into. More on that below.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[16]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">numpy</span> <span class="k">as</span> <span class="nn">np</span>
<span class="kn">import</span> <span class="nn">matplotlib.pyplot</span> <span class="k">as</span> <span class="nn">plt</span>

<span class="n">n_bins</span> <span class="o">=</span> <span class="p">[</span><span class="o">-</span><span class="mf">0.5</span><span class="p">,</span><span class="mf">0.5</span><span class="p">,</span><span class="mf">1.5</span><span class="p">,</span><span class="mf">2.5</span><span class="p">,</span><span class="mf">3.5</span><span class="p">,</span><span class="mf">4.5</span><span class="p">,</span><span class="mf">5.5</span><span class="p">,</span><span class="mf">6.5</span><span class="p">]</span>

<span class="n">colors</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;red&#39;</span><span class="p">,</span> <span class="s1">&#39;blue&#39;</span><span class="p">]</span>
<span class="n">labels</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;Predictions&#39;</span><span class="p">,</span><span class="s1">&#39;Actual&#39;</span><span class="p">]</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xticks</span><span class="p">(</span><span class="nb">range</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span> <span class="mi">7</span><span class="p">))</span>
<span class="n">plt</span><span class="o">.</span><span class="n">hist</span><span class="p">((</span><span class="n">p</span><span class="p">,</span><span class="n">t</span><span class="p">),</span> <span class="n">n_bins</span><span class="p">,</span> <span class="n">density</span><span class="o">=</span><span class="kc">False</span><span class="p">,</span> <span class="n">histtype</span><span class="o">=</span><span class="s1">&#39;bar&#39;</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="n">colors</span><span class="p">,</span> 
         <span class="n">label</span><span class="o">=</span><span class="n">labels</span><span class="p">,</span> <span class="n">align</span><span class="o">=</span><span class="s1">&#39;left&#39;</span><span class="p">,</span><span class="n">alpha</span><span class="o">=</span><span class="mf">0.7</span><span class="p">,</span> <span class="n">rwidth</span><span class="o">=</span><span class="mi">5</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">legend</span><span class="p">(</span><span class="n">prop</span><span class="o">=</span><span class="p">{</span><span class="s1">&#39;size&#39;</span><span class="p">:</span> <span class="mi">10</span><span class="p">})</span>
<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;PLN General Hist&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>

<span class="c1"># TrEC = 0</span>
<span class="c1"># HEC / HEC late = 1</span>
<span class="c1"># CapEC1/2 = 2</span>
<span class="c1"># CRP / CRP Early = 3</span>
<span class="c1"># HEV = 1</span>
<span class="c1"># Pre-Art = 5</span>
<span class="c1"># Vn = 4</span>
<span class="c1"># Art = 5</span>
<span class="c1"># CapIfn = 6</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,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
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Testing-MLN">Testing MLN<a class="anchor-link" href="#Testing-MLN">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>In the same way as above, I import a dataset and change it into an array. I then drop ambiguous cell types, and separate labels from data. This is an example of a slightly different dataset (MLN vs PLN) used for making predictions with our PLN trained model. IF our model is successful, this shows that it could be cross-tissue applicable.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[17]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">mln</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">read_csv</span><span class="p">(</span><span class="s1">&#39;/Users/tjshruti/Downloads/MLN_short.csv&#39;</span><span class="p">)</span>
<span class="n">mln</span><span class="o">.</span><span class="n">shape</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[17]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>(2128, 31054)</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[18]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">mln</span><span class="o">.</span><span class="n">head</span><span class="p">()</span>
<span class="n">mln_fit</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">asarray</span><span class="p">(</span><span class="n">mln</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[19]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">drops_mln</span> <span class="o">=</span> <span class="n">mln_fit</span><span class="p">[:,</span><span class="mi">2</span><span class="p">]</span><span class="o">==</span><span class="s1">&#39;ambig&#39;</span>
<span class="n">drops_mln</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">transpose</span><span class="p">(</span><span class="n">drops_mln</span><span class="p">)</span>
<span class="n">drops_mln</span> <span class="o">=</span> <span class="p">[</span><span class="ow">not</span> <span class="n">y</span> <span class="k">for</span> <span class="n">y</span> <span class="ow">in</span> <span class="n">drops_mln</span><span class="p">]</span>
<span class="n">mln_fit</span> <span class="o">=</span> <span class="n">mln_fit</span><span class="p">[</span><span class="n">drops_mln</span><span class="p">]</span>
<span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">mln_fit</span><span class="p">)</span><span class="o">.</span><span class="n">to_csv</span><span class="p">(</span><span class="s1">&#39;/Users/tjshruti/Downloads/MLN_short_no_Ambig.csv&#39;</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[20]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">Xarr</span> <span class="o">=</span> <span class="n">mln_fit</span><span class="p">[:,</span><span class="mi">3</span><span class="p">:</span><span class="mi">31055</span><span class="p">]</span>
<span class="n">Y_ArrMLN</span> <span class="o">=</span> <span class="n">mln_fit</span><span class="p">[:,</span><span class="mi">2</span><span class="p">]</span>
<span class="n">Y_ArrMLN</span><span class="o">.</span><span class="n">shape</span><span class="p">,</span> <span class="n">Xarr</span><span class="o">.</span><span class="n">shape</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[20]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>((1833,), (1833, 31051))</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[21]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">predictions</span> <span class="o">=</span> <span class="n">classifier</span><span class="o">.</span><span class="n">predict_classes</span><span class="p">(</span><span class="n">Xarr</span><span class="p">)</span>
<span class="n">predsMLN</span> <span class="o">=</span> <span class="n">predictions</span><span class="o">.</span><span class="n">tolist</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[22]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># TrEC = 0</span>
<span class="c1"># HEC / HEC late = 1</span>
<span class="c1"># CapEC1/2 = 2</span>
<span class="c1"># CRP / CRP Early = 3</span>
<span class="c1"># HEV = 1</span>
<span class="c1"># Pre-Art = 5</span>
<span class="c1"># Vn = 4</span>
<span class="c1"># Art = 5</span>
<span class="c1"># CapIfn = 6</span>


<span class="n">Y_ArrMLN1</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">zeros</span><span class="p">((</span><span class="mi">1833</span><span class="p">,</span> <span class="mi">1</span><span class="p">))</span>
<span class="k">for</span> <span class="n">x</span> <span class="ow">in</span> <span class="nb">range</span><span class="p">(</span><span class="mi">1833</span><span class="p">):</span>
    <span class="k">if</span> <span class="p">(</span><span class="n">Y_ArrMLN</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">==</span> <span class="s1">&#39;TrEC&#39;</span><span class="p">):</span>
        <span class="n">Y_ArrMLN1</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">=</span> <span class="mi">0</span>
    <span class="k">elif</span> <span class="p">(</span><span class="n">Y_ArrMLN</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">==</span> <span class="s1">&#39;HEC&#39;</span><span class="p">):</span>
        <span class="n">Y_ArrMLN1</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">=</span> <span class="mi">1</span>
    <span class="k">elif</span> <span class="p">(</span><span class="n">Y_ArrMLN</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">==</span> <span class="s1">&#39;HEC (late)&#39;</span><span class="p">):</span>
        <span class="n">Y_ArrMLN1</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">=</span> <span class="mi">1</span>
    <span class="k">elif</span><span class="p">(</span><span class="n">Y_ArrMLN</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">==</span> <span class="s1">&#39;CapEC1&#39;</span><span class="p">):</span>
        <span class="n">Y_ArrMLN1</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">=</span> <span class="mi">2</span>
    <span class="k">elif</span> <span class="p">(</span><span class="n">Y_ArrMLN</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">==</span> <span class="s1">&#39;CapEC2&#39;</span><span class="p">):</span>
        <span class="n">Y_ArrMLN1</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">=</span> <span class="mi">2</span>
    <span class="k">elif</span> <span class="p">(</span><span class="n">Y_ArrMLN</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">==</span> <span class="s1">&#39;CRP&#39;</span><span class="p">):</span>
        <span class="n">Y_ArrMLN1</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">=</span> <span class="mi">3</span>
    <span class="k">elif</span> <span class="p">(</span><span class="n">Y_ArrMLN</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">==</span> <span class="s1">&#39;HEV&#39;</span><span class="p">):</span>
        <span class="n">Y_ArrMLN1</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">=</span> <span class="mi">1</span>
    <span class="k">elif</span> <span class="p">(</span><span class="n">Y_ArrMLN</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">==</span> <span class="s1">&#39;Pre-Art&#39;</span><span class="p">):</span>
        <span class="n">Y_ArrMLN1</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">=</span> <span class="mi">5</span>
    <span class="k">elif</span> <span class="p">(</span><span class="n">Y_ArrMLN</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">==</span> <span class="s1">&#39;CRP (early)&#39;</span><span class="p">):</span>
        <span class="n">Y_ArrMLN1</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">=</span> <span class="mi">3</span>
    <span class="k">elif</span><span class="p">(</span><span class="n">Y_ArrMLN</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">==</span> <span class="s1">&#39;Vn&#39;</span><span class="p">):</span>
        <span class="n">Y_ArrMLN1</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">=</span> <span class="mi">4</span>
    <span class="k">elif</span><span class="p">(</span><span class="n">Y_ArrMLN</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">==</span> <span class="s1">&#39;Art&#39;</span><span class="p">):</span>
        <span class="n">Y_ArrMLN1</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">=</span> <span class="mi">5</span>
    <span class="k">elif</span><span class="p">(</span><span class="n">Y_ArrMLN</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">==</span> <span class="s1">&#39;CapIfn&#39;</span><span class="p">):</span>
        <span class="n">Y_ArrMLN1</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">=</span> <span class="mi">6</span>
   
        
<span class="n">Y_ArrMLN1</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[22]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>array([[2.],
       [2.],
       [2.],
       ...,
       [2.],
       [2.],
       [2.]])</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[23]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">pMLN</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">asarray</span><span class="p">(</span><span class="n">predsMLN</span><span class="p">)</span>
<span class="n">tMLN</span><span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">squeeze</span><span class="p">(</span><span class="n">Y_ArrMLN1</span><span class="p">)</span>
<span class="n">tMLN</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[23]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>array([2., 2., 2., ..., 2., 2., 2.])</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="General-Histogram-for-MLN-TEST">General Histogram for MLN TEST<a class="anchor-link" href="#General-Histogram-for-MLN-TEST">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[24]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">numpy</span> <span class="k">as</span> <span class="nn">np</span>
<span class="kn">import</span> <span class="nn">matplotlib.pyplot</span> <span class="k">as</span> <span class="nn">plt</span>

<span class="n">n_bins</span> <span class="o">=</span> <span class="p">[</span><span class="o">-</span><span class="mf">0.5</span><span class="p">,</span><span class="mf">0.5</span><span class="p">,</span><span class="mf">1.5</span><span class="p">,</span><span class="mf">2.5</span><span class="p">,</span><span class="mf">3.5</span><span class="p">,</span><span class="mf">4.5</span><span class="p">,</span><span class="mf">5.5</span><span class="p">,</span><span class="mf">6.5</span><span class="p">]</span>

<span class="n">colors</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;red&#39;</span><span class="p">,</span> <span class="s1">&#39;blue&#39;</span><span class="p">]</span>
<span class="n">labels</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;Predictions&#39;</span><span class="p">,</span><span class="s1">&#39;Actual&#39;</span><span class="p">]</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xticks</span><span class="p">(</span><span class="nb">range</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span> <span class="mi">9</span><span class="p">))</span>
<span class="n">plt</span><span class="o">.</span><span class="n">hist</span><span class="p">((</span><span class="n">pMLN</span><span class="p">,</span><span class="n">tMLN</span><span class="p">),</span> <span class="n">n_bins</span><span class="p">,</span> <span class="n">density</span><span class="o">=</span><span class="kc">False</span><span class="p">,</span> <span class="n">histtype</span><span class="o">=</span><span class="s1">&#39;bar&#39;</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="n">colors</span><span class="p">,</span> 
         <span class="n">label</span><span class="o">=</span><span class="n">labels</span><span class="p">,</span> <span class="n">align</span><span class="o">=</span><span class="s1">&#39;left&#39;</span><span class="p">,</span><span class="n">alpha</span><span class="o">=</span><span class="mf">0.7</span><span class="p">,</span> <span class="n">rwidth</span><span class="o">=</span><span class="mi">5</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">legend</span><span class="p">(</span><span class="n">prop</span><span class="o">=</span><span class="p">{</span><span class="s1">&#39;size&#39;</span><span class="p">:</span> <span class="mi">10</span><span class="p">})</span>
<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;MLN General Hist&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,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
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[25]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1">#Accuracy Score on MLN Tissue</span>
<span class="kn">from</span> <span class="nn">sklearn.metrics</span> <span class="k">import</span> <span class="n">accuracy_score</span>
<span class="nb">print</span><span class="p">(</span><span class="n">accuracy_score</span><span class="p">(</span><span class="n">predsMLN</span><span class="p">,</span> <span class="n">Y_ArrMLN1</span><span class="p">)</span><span class="o">*</span><span class="mi">100</span><span class="p">)</span>
<span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">predsMLN</span><span class="p">)</span><span class="o">.</span><span class="n">to_csv</span><span class="p">(</span><span class="s1">&#39;/Users/tjshruti/Downloads/MLN1_predictions_sept13.csv&#39;</span><span class="p">)</span>
<span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">Y_ArrMLN1</span><span class="p">)</span><span class="o">.</span><span class="n">to_csv</span><span class="p">(</span><span class="s1">&#39;/Users/tjshruti/Downloads/MLN1_actual_sept13.csv&#39;</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>80.03273322422258
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>The model displayed an 88% accuracy on a biologically different dataset. Based on the histogram, there are clear discrepancies. Let's see where the model had a hard time.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[26]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">probs</span> <span class="o">=</span> <span class="n">classifier</span><span class="o">.</span><span class="n">predict_proba</span><span class="p">(</span><span class="n">Xarr</span><span class="p">)</span>
<span class="n">pd</span><span class="o">.</span><span class="n">DataFrame</span><span class="p">(</span><span class="n">probs</span><span class="p">)</span><span class="o">.</span><span class="n">to_csv</span><span class="p">(</span><span class="s1">&#39;/Users/tjshruti/Downloads/MLN1_Classification_Probabilities1.csv&#39;</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>For the three cells below, I am creating a dataset where only predictions with a high (&gt;80%) level of accuracy are examined.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[27]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">probs_barcodes</span><span class="o">=</span><span class="n">pd</span><span class="o">.</span><span class="n">read_csv</span><span class="p">(</span><span class="s1">&#39;/Users/tjshruti/Downloads/MLN1_Classification_Probabilities_with_index.csv&#39;</span><span class="p">)</span>
<span class="n">probs_barcodes_arr</span><span class="o">=</span><span class="n">np</span><span class="o">.</span><span class="n">asarray</span><span class="p">(</span><span class="n">probs_barcodes</span><span class="p">)</span>
<span class="n">data</span><span class="o">=</span><span class="n">probs_barcodes_arr</span><span class="p">[:,</span><span class="mi">1</span><span class="p">:</span><span class="mi">8</span><span class="p">]</span>
<span class="n">data_answers</span><span class="o">=</span><span class="n">probs_barcodes_arr</span><span class="p">[:,</span><span class="mi">9</span><span class="p">:</span><span class="mi">10</span><span class="p">]</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[28]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">data_high_prob</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">zeros</span><span class="p">((</span><span class="mi">1833</span><span class="p">))</span>
                          
<span class="k">for</span> <span class="n">i</span> <span class="ow">in</span> <span class="nb">range</span><span class="p">(</span><span class="mi">1833</span><span class="p">):</span>
    <span class="k">for</span> <span class="n">j</span> <span class="ow">in</span> <span class="nb">range</span><span class="p">(</span><span class="mi">1</span><span class="p">,</span><span class="mi">7</span><span class="p">):</span>
        <span class="k">if</span> <span class="n">data</span><span class="p">[</span><span class="n">i</span><span class="p">,</span><span class="n">j</span><span class="p">]</span> <span class="o">&gt;</span> <span class="mf">0.8</span><span class="p">:</span>
            <span class="n">data_high_prob</span><span class="p">[</span><span class="n">i</span><span class="p">]</span><span class="o">=</span><span class="mi">1</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[29]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">data_bools</span> <span class="o">=</span> <span class="n">data_high_prob</span><span class="p">[:]</span><span class="o">==</span><span class="mi">1</span>
<span class="n">data_only_high_prob</span><span class="o">=</span> <span class="n">data</span><span class="p">[</span><span class="n">data_bools</span><span class="p">]</span>
<span class="n">data_answers_high_prob</span><span class="o">=</span><span class="n">data_answers</span><span class="p">[</span><span class="n">data_bools</span><span class="p">]</span>
<span class="n">data_only_high_prob_index</span><span class="o">=</span><span class="n">data_only_high_prob</span><span class="p">[:,</span><span class="mi">0</span><span class="p">]</span>


<span class="n">matches</span><span class="o">=</span><span class="n">probs_barcodes</span><span class="o">.</span><span class="n">loc</span><span class="p">[</span><span class="n">probs_barcodes</span><span class="p">[</span><span class="s1">&#39;Index&#39;</span><span class="p">]</span><span class="o">.</span><span class="n">isin</span><span class="p">(</span><span class="n">data_only_high_prob_index</span><span class="p">)]</span>
<span class="n">matches_arr</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">asarray</span><span class="p">(</span><span class="n">matches</span><span class="p">)</span>
<span class="n">matches_preds</span> <span class="o">=</span> <span class="n">matches_arr</span><span class="p">[:,</span><span class="mi">9</span><span class="p">]</span>
<span class="n">matches_true</span> <span class="o">=</span> <span class="n">matches_arr</span><span class="p">[:,</span><span class="mi">10</span><span class="p">]</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="High-Prob-&gt;80%-Histogram">High Prob &gt;80% Histogram<a class="anchor-link" href="#High-Prob-&gt;80%-Histogram">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[30]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">import</span> <span class="nn">numpy</span> <span class="k">as</span> <span class="nn">np</span>
<span class="kn">import</span> <span class="nn">matplotlib.pyplot</span> <span class="k">as</span> <span class="nn">plt</span>

<span class="n">n_bins</span> <span class="o">=</span> <span class="p">[</span><span class="o">-</span><span class="mf">0.5</span><span class="p">,</span><span class="mf">0.5</span><span class="p">,</span><span class="mf">1.5</span><span class="p">,</span><span class="mf">2.5</span><span class="p">,</span><span class="mf">3.5</span><span class="p">,</span><span class="mf">4.5</span><span class="p">,</span><span class="mf">5.5</span><span class="p">,</span><span class="mf">6.5</span><span class="p">]</span>

<span class="n">colors</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;red&#39;</span><span class="p">,</span> <span class="s1">&#39;blue&#39;</span><span class="p">]</span>
<span class="n">labels</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;Predictions&#39;</span><span class="p">,</span><span class="s1">&#39;Actual&#39;</span><span class="p">]</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xticks</span><span class="p">(</span><span class="nb">range</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span> <span class="mi">9</span><span class="p">))</span>
<span class="n">plt</span><span class="o">.</span><span class="n">hist</span><span class="p">((</span><span class="n">matches_preds</span><span class="p">,</span><span class="n">matches_true</span><span class="p">),</span> <span class="n">n_bins</span><span class="p">,</span> <span class="n">density</span><span class="o">=</span><span class="kc">False</span><span class="p">,</span> <span class="n">histtype</span><span class="o">=</span><span class="s1">&#39;bar&#39;</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="n">colors</span><span class="p">,</span> 
         <span class="n">label</span><span class="o">=</span><span class="n">labels</span><span class="p">,</span> <span class="n">align</span><span class="o">=</span><span class="s1">&#39;left&#39;</span><span class="p">,</span><span class="n">alpha</span><span class="o">=</span><span class="mf">0.7</span><span class="p">,</span> <span class="n">rwidth</span><span class="o">=</span><span class="mi">5</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">legend</span><span class="p">(</span><span class="n">prop</span><span class="o">=</span><span class="p">{</span><span class="s1">&#39;size&#39;</span><span class="p">:</span> <span class="mi">10</span><span class="p">})</span>
<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;High Probability Hist&#39;</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,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oqamhmHDhhW8XrPDMhFxZUSUREQpuZsuLY2Ic4DHga+lblPJXXkIuXtPT03TX0v9fWRulkHbt29n4MCBDvYiksTAgQNb/NtRWy5i+i5wuaQqcmPqu++mNx8YmNovB2a1YR9m1sU52IuvNZ9xiy5iiogngCfS9GvA0Q302Q6c0eJKzMys3XSJK1TNLCO+0s7P1r7//ma79OjRg9GjR7Nz506OPPJIKioq2HfffVu1uyeeeIIbbriBBx54gCVLlrB69WpmzWp48GHLli3ceeedXHhh7imTr7/+OpdeeimLFy9usH9Hc7h3tPb+y797szT/j6ClCvh3Zdbp+vTpw4oVKwA455xzuOWWW7j88sv3LI8IIoK99mrZKPTkyZOZPHlyo8u3bNnCz372sz3hfsghh3SZYAffOMzMMuTYY4+lqqqK6upqRowYwTe+8Q1GjRrFunXrePjhh5kwYQLjxo3jjDPOYNu2bQA89NBDjBw5knHjxnHPPR88cGvBggVcfHHuqZBvvvkmp512GmPGjGHMmDH84Q9/YNasWbz66quUlZVxxRVXUF1dzahRo4DcF83Tpk1j9OjRjB07lscff3zPNr/61a8yadIkhg8fzsyZMwHYtWsX559/PqNGjWL06NHMmTOnzZ+Fj9zNLBN27tzJb37zGyZNmgTAK6+8QkVFBePHj2fjxo3Mnj2bRx99lL59+3L99ddz4403MnPmTL75zW+ydOlSDj/8cL7+9a83uO1LL72UL3zhC9x7773s2rWLbdu28cMf/pBVq1bt+a2hurp6T/+bb74ZSaxcuZIXX3yRE088kZdffhmAFStW8Oc//5l99tmHESNGcMkll7BhwwZqa2tZtWoVkPutoK185G5m3dq7775LWVkZ5eXlfOITn2D69Nxtrg499FDGjx8PwFNPPcXq1as55phjKCsro6KigrVr1/Liiy8ybNgwhg8fjiTOPffcBvexdOlSLrjgAiA3xt+vX78ma1q2bNmebY0cOZJDDz10T7hPnDiRfv360bt3b4466ijWrl3LJz/5SV577TUuueQSHnroIQ444IA2fy4+cjezbi1/zD1f375990xHBCeccAILFy78UJ+G1iu2ffbZZ890jx492LlzJwceeCDPPfccv/3tb7nllltYtGgRt956a5v24yN3M8u88ePH8/vf/56qqioA/v73v/Pyyy8zcuRIqqurefXVVwE+Ev67TZw4kblz5wK58fGtW7ey//778/bbbzfY/9hjj+WOO+4A4OWXX+avf/0rI0aMaLS+jRs38v7773P66acze/Zsnn322Va/19185G5m7aeLnmI1aNAgFixYwNlnn82OHTsAmD17NkcccQTz5s3jlFNOYd999+XYY49tMLB/8pOfMGPGDObPn0+PHj2YO3cuEyZM4JhjjmHUqFGcdNJJXHTRRXv6X3jhhVxwwQWMHj2anj17smDBgg8dsddXW1vLtGnTeP/93L0Zf/CDH7T5PXeJZ6iWl5fHx+ZhHT4V0jJkzZo1HHnkkZ1dxsdCQ5+1pOURUd5Qfw/LmJllkMPdzCyDHO5mZhnkcDczyyCHu5lZBjnczcwyyOe5m1m76YQ7/gLw61//mtNOO401a9YwcuTIRvstWLCAE088kUMOOaRV9eTfErir85G7mXV7Cxcu5HOf+1yjV5jutmDBAl5//fUOqqpzNRvuknpLekbSc5JekPT91L5A0l8krUivstQuSTdJqpL0vKRxxX4TZvbxtW3bNpYtW8b8+fO566679rRff/31jB49mjFjxjBr1iwWL15MZWUl55xzDmVlZbz77ruUlpayceNGACorKznuuOMAeOaZZ5gwYQJjx47ls5/9LC+99FJnvLU2KWRYZgdwfERsk9QLWCbpN2nZFRFR/+70JwHD0+szwNz008ys3d13331MmjSJI444goEDB7J8+XI2bNjAfffdx9NPP82+++7L5s2bGTBgAD/96U+54YYbKC9v8KLOPUaOHMmTTz5Jz549efTRR7nqqqu4++67O+gdtY9mwz1y9yfYlmZ7pVdT9yyYAtye1ntKUn9JgyNifZurNTOrZ+HChVx22WUAnHXWWSxcuJCIYNq0aXsetzdgwIAWbXPr1q1MnTqVV155BUm899577V53sRX0haqkHsBy4HDg5oh4WtIFwLWS/ifwGDArInYAQ4B1eavXpDaHu5m1q82bN7N06VJWrlyJJHbt2oUkzjjjjILW79mz556bdW3fvn1P+9VXX80Xv/hF7r33Xqqrq/cM13QnBX2hGhG7IqIMKAGOljQKuBIYCXwaGAB8tyU7ljRDUqWkyrq6uhaWbWYGixcv5rzzzmPt2rVUV1ezbt06hg0bRr9+/bjtttt45513gNx/AsBHbtNbWlrK8uXLAT40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
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>The histogram above shows that when the model is confident in a prediction, it is almost always accurate. Clearly, there are features in certain cell types that are a dead giveaway marker for that cell type.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h1 id="Getting-Some-Cool-Histograms">Getting Some Cool Histograms<a class="anchor-link" href="#Getting-Some-Cool-Histograms">&#182;</a></h1>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Below, I dive into some specifics for each "general" histogram displayed above. Each class has a blue "actual" bar compared to one or more red "prediction" bars. This allows us to see where the model is going wrong with each specific cell type. The first set of histograms are for the PLN trained model's predictions on the MLN set, and the second set of histograms are for the PLN trained model's predictions on the PLN set (itself)</p>

</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="--MLN-Histograms">--MLN Histograms<a class="anchor-link" href="#--MLN-Histograms">&#182;</a></h2>
<pre><code># TrEC = 0
# HEC / HEC late / HEV = 1
# CapEC1/2 = 2
# CRP / CRP Early = 3
# Vn = 4
# Pre-Art / Art = 5
# CapIfn = 6</code></pre>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[31]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">comb</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">stack</span><span class="p">((</span><span class="n">tMLN</span><span class="p">,</span><span class="n">pMLN</span><span class="p">))</span>
<span class="n">comb</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">transpose</span><span class="p">(</span><span class="n">comb</span><span class="p">)</span>
<span class="nb">print</span><span class="p">(</span><span class="n">comb</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>[[2. 2.]
 [2. 2.]
 [2. 2.]
 ...
 [2. 2.]
 [2. 2.]
 [2. 2.]]
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[32]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">ones</span> <span class="o">=</span> <span class="n">comb</span><span class="p">[:,</span><span class="mi">0</span><span class="p">]</span><span class="o">==</span><span class="mi">0</span>
<span class="n">comb_ones</span> <span class="o">=</span> <span class="n">comb</span><span class="p">[</span><span class="n">ones</span><span class="p">]</span>
<span class="n">comb_ones_preds</span> <span class="o">=</span> <span class="n">comb_ones</span><span class="p">[:,</span><span class="mi">1</span><span class="p">]</span>
<span class="n">comb_ones_true</span> <span class="o">=</span> <span class="n">comb_ones</span><span class="p">[:,</span><span class="mi">0</span><span class="p">]</span>

<span class="n">n_bins</span> <span class="o">=</span> <span class="p">[</span><span class="o">-</span><span class="mf">0.5</span><span class="p">,</span><span class="mf">0.5</span><span class="p">,</span><span class="mf">1.5</span><span class="p">,</span><span class="mf">2.5</span><span class="p">,</span><span class="mf">3.5</span><span class="p">,</span><span class="mf">4.5</span><span class="p">,</span><span class="mf">5.5</span><span class="p">,</span><span class="mf">6.5</span><span class="p">]</span>

<span class="n">colors</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;red&#39;</span><span class="p">,</span> <span class="s1">&#39;blue&#39;</span><span class="p">]</span>
<span class="n">labels</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;Predictions&#39;</span><span class="p">,</span><span class="s1">&#39;Actual&#39;</span><span class="p">]</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xticks</span><span class="p">(</span><span class="nb">range</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span> <span class="mi">9</span><span class="p">))</span>
<span class="n">plt</span><span class="o">.</span><span class="n">hist</span><span class="p">((</span><span class="n">comb_ones_preds</span><span class="p">,</span><span class="n">comb_ones_true</span><span class="p">),</span> <span class="n">n_bins</span><span class="p">,</span> <span class="n">density</span><span class="o">=</span><span class="kc">False</span><span class="p">,</span> <span class="n">histtype</span><span class="o">=</span><span class="s1">&#39;bar&#39;</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="n">colors</span><span class="p">,</span> 
         <span class="n">label</span><span class="o">=</span><span class="n">labels</span><span class="p">,</span> <span class="n">align</span><span class="o">=</span><span class="s1">&#39;left&#39;</span><span class="p">,</span><span class="n">alpha</span><span class="o">=</span><span class="mf">0.7</span><span class="p">,</span> <span class="n">rwidth</span><span class="o">=</span><span class="mi">5</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">legend</span><span class="p">(</span><span class="n">prop</span><span class="o">=</span><span class="p">{</span><span class="s1">&#39;size&#39;</span><span class="p">:</span> <span class="mi">10</span><span class="p">})</span>
<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;TrEC Classification&#39;</span><span class="p">)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,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
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[33]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">ones</span> <span class="o">=</span> <span class="n">comb</span><span class="p">[:,</span><span class="mi">0</span><span class="p">]</span><span class="o">==</span><span class="mi">1</span>
<span class="n">comb_ones</span> <span class="o">=</span> <span class="n">comb</span><span class="p">[</span><span class="n">ones</span><span class="p">]</span>
<span class="n">comb_ones_preds</span> <span class="o">=</span> <span class="n">comb_ones</span><span class="p">[:,</span><span class="mi">1</span><span class="p">]</span>
<span class="n">comb_ones_true</span> <span class="o">=</span> <span class="n">comb_ones</span><span class="p">[:,</span><span class="mi">0</span><span class="p">]</span>

<span class="n">n_bins</span> <span class="o">=</span> <span class="p">[</span><span class="o">-</span><span class="mf">0.5</span><span class="p">,</span><span class="mf">0.5</span><span class="p">,</span><span class="mf">1.5</span><span class="p">,</span><span class="mf">2.5</span><span class="p">,</span><span class="mf">3.5</span><span class="p">,</span><span class="mf">4.5</span><span class="p">,</span><span class="mf">5.5</span><span class="p">,</span><span class="mf">6.5</span><span class="p">]</span>

<span class="n">colors</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;red&#39;</span><span class="p">,</span> <span class="s1">&#39;blue&#39;</span><span class="p">]</span>
<span class="n">labels</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;Predictions&#39;</span><span class="p">,</span><span class="s1">&#39;Actual&#39;</span><span class="p">]</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xticks</span><span class="p">(</span><span class="nb">range</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span> <span class="mi">9</span><span class="p">))</span>
<span class="n">plt</span><span class="o">.</span><span class="n">hist</span><span class="p">((</span><span class="n">comb_ones_preds</span><span class="p">,</span><span class="n">comb_ones_true</span><span class="p">),</span> <span class="n">n_bins</span><span class="p">,</span> <span class="n">density</span><span class="o">=</span><span class="kc">False</span><span class="p">,</span> <span class="n">histtype</span><span class="o">=</span><span class="s1">&#39;bar&#39;</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="n">colors</span><span class="p">,</span> 
         <span class="n">label</span><span class="o">=</span><span class="n">labels</span><span class="p">,</span> <span class="n">align</span><span class="o">=</span><span class="s1">&#39;left&#39;</span><span class="p">,</span><span class="n">alpha</span><span class="o">=</span><span class="mf">0.7</span><span class="p">,</span> <span class="n">rwidth</span><span class="o">=</span><span class="mi">5</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">legend</span><span class="p">(</span><span class="n">prop</span><span class="o">=</span><span class="p">{</span><span class="s1">&#39;size&#39;</span><span class="p">:</span> <span class="mi">10</span><span class="p">})</span>
<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;HEC / HEC late / HEV&#39;</span><span class="p">)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,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
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[34]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">ones</span> <span class="o">=</span> <span class="n">comb</span><span class="p">[:,</span><span class="mi">0</span><span class="p">]</span><span class="o">==</span><span class="mi">2</span>
<span class="n">comb_ones</span> <span class="o">=</span> <span class="n">comb</span><span class="p">[</span><span class="n">ones</span><span class="p">]</span>
<span class="n">comb_ones_preds</span> <span class="o">=</span> <span class="n">comb_ones</span><span class="p">[:,</span><span class="mi">1</span><span class="p">]</span>
<span class="n">comb_ones_true</span> <span class="o">=</span> <span class="n">comb_ones</span><span class="p">[:,</span><span class="mi">0</span><span class="p">]</span>

<span class="n">n_bins</span> <span class="o">=</span> <span class="p">[</span><span class="o">-</span><span class="mf">0.5</span><span class="p">,</span><span class="mf">0.5</span><span class="p">,</span><span class="mf">1.5</span><span class="p">,</span><span class="mf">2.5</span><span class="p">,</span><span class="mf">3.5</span><span class="p">,</span><span class="mf">4.5</span><span class="p">,</span><span class="mf">5.5</span><span class="p">,</span><span class="mf">6.5</span><span class="p">]</span>

<span class="n">colors</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;red&#39;</span><span class="p">,</span> <span class="s1">&#39;blue&#39;</span><span class="p">]</span>
<span class="n">labels</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;Predictions&#39;</span><span class="p">,</span><span class="s1">&#39;Actual&#39;</span><span class="p">]</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xticks</span><span class="p">(</span><span class="nb">range</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span> <span class="mi">9</span><span class="p">))</span>
<span class="n">plt</span><span class="o">.</span><span class="n">hist</span><span class="p">((</span><span class="n">comb_ones_preds</span><span class="p">,</span><span class="n">comb_ones_true</span><span class="p">),</span> <span class="n">n_bins</span><span class="p">,</span> <span class="n">density</span><span class="o">=</span><span class="kc">False</span><span class="p">,</span> <span class="n">histtype</span><span class="o">=</span><span class="s1">&#39;bar&#39;</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="n">colors</span><span class="p">,</span> 
         <span class="n">label</span><span class="o">=</span><span class="n">labels</span><span class="p">,</span> <span class="n">align</span><span class="o">=</span><span class="s1">&#39;left&#39;</span><span class="p">,</span><span class="n">alpha</span><span class="o">=</span><span class="mf">0.7</span><span class="p">,</span> <span class="n">rwidth</span><span class="o">=</span><span class="mi">5</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">legend</span><span class="p">(</span><span class="n">prop</span><span class="o">=</span><span class="p">{</span><span class="s1">&#39;size&#39;</span><span class="p">:</span> <span class="mi">10</span><span class="p">})</span>
<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;CapEC1/2&#39;</span><span class="p">)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,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
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[35]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">ones</span> <span class="o">=</span> <span class="n">comb</span><span class="p">[:,</span><span class="mi">0</span><span class="p">]</span><span class="o">==</span><span class="mi">3</span>
<span class="n">comb_ones</span> <span class="o">=</span> <span class="n">comb</span><span class="p">[</span><span class="n">ones</span><span class="p">]</span>
<span class="n">comb_ones_preds</span> <span class="o">=</span> <span class="n">comb_ones</span><span class="p">[:,</span><span class="mi">1</span><span class="p">]</span>
<span class="n">comb_ones_true</span> <span class="o">=</span> <span class="n">comb_ones</span><span class="p">[:,</span><span class="mi">0</span><span class="p">]</span>

<span class="n">n_bins</span> <span class="o">=</span> <span class="p">[</span><span class="o">-</span><span class="mf">0.5</span><span class="p">,</span><span class="mf">0.5</span><span class="p">,</span><span class="mf">1.5</span><span class="p">,</span><span class="mf">2.5</span><span class="p">,</span><span class="mf">3.5</span><span class="p">,</span><span class="mf">4.5</span><span class="p">,</span><span class="mf">5.5</span><span class="p">,</span><span class="mf">6.5</span><span class="p">]</span>

<span class="n">colors</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;red&#39;</span><span class="p">,</span> <span class="s1">&#39;blue&#39;</span><span class="p">]</span>
<span class="n">labels</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;Predictions&#39;</span><span class="p">,</span><span class="s1">&#39;Actual&#39;</span><span class="p">]</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xticks</span><span class="p">(</span><span class="nb">range</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span> <span class="mi">9</span><span class="p">))</span>
<span class="n">plt</span><span class="o">.</span><span class="n">hist</span><span class="p">((</span><span class="n">comb_ones_preds</span><span class="p">,</span><span class="n">comb_ones_true</span><span class="p">),</span> <span class="n">n_bins</span><span class="p">,</span> <span class="n">density</span><span class="o">=</span><span class="kc">False</span><span class="p">,</span> <span class="n">histtype</span><span class="o">=</span><span class="s1">&#39;bar&#39;</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="n">colors</span><span class="p">,</span> 
         <span class="n">label</span><span class="o">=</span><span class="n">labels</span><span class="p">,</span> <span class="n">align</span><span class="o">=</span><span class="s1">&#39;left&#39;</span><span class="p">,</span><span class="n">alpha</span><span class="o">=</span><span class="mf">0.7</span><span class="p">,</span> <span class="n">rwidth</span><span class="o">=</span><span class="mi">5</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">legend</span><span class="p">(</span><span class="n">prop</span><span class="o">=</span><span class="p">{</span><span class="s1">&#39;size&#39;</span><span class="p">:</span> <span class="mi">10</span><span class="p">})</span>
<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;CRP / CRP Early&#39;</span><span class="p">)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,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
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[36]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">ones</span> <span class="o">=</span> <span class="n">comb</span><span class="p">[:,</span><span class="mi">0</span><span class="p">]</span><span class="o">==</span><span class="mi">4</span>
<span class="n">comb_ones</span> <span class="o">=</span> <span class="n">comb</span><span class="p">[</span><span class="n">ones</span><span class="p">]</span>
<span class="n">comb_ones_preds</span> <span class="o">=</span> <span class="n">comb_ones</span><span class="p">[:,</span><span class="mi">1</span><span class="p">]</span>
<span class="n">comb_ones_true</span> <span class="o">=</span> <span class="n">comb_ones</span><span class="p">[:,</span><span class="mi">0</span><span class="p">]</span>

<span class="n">n_bins</span> <span class="o">=</span> <span class="p">[</span><span class="o">-</span><span class="mf">0.5</span><span class="p">,</span><span class="mf">0.5</span><span class="p">,</span><span class="mf">1.5</span><span class="p">,</span><span class="mf">2.5</span><span class="p">,</span><span class="mf">3.5</span><span class="p">,</span><span class="mf">4.5</span><span class="p">,</span><span class="mf">5.5</span><span class="p">,</span><span class="mf">6.5</span><span class="p">]</span>

<span class="n">colors</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;red&#39;</span><span class="p">,</span> <span class="s1">&#39;blue&#39;</span><span class="p">]</span>
<span class="n">labels</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;Predictions&#39;</span><span class="p">,</span><span class="s1">&#39;Actual&#39;</span><span class="p">]</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xticks</span><span class="p">(</span><span class="nb">range</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span> <span class="mi">9</span><span class="p">))</span>
<span class="n">plt</span><span class="o">.</span><span class="n">hist</span><span class="p">((</span><span class="n">comb_ones_preds</span><span class="p">,</span><span class="n">comb_ones_true</span><span class="p">),</span> <span class="n">n_bins</span><span class="p">,</span> <span class="n">density</span><span class="o">=</span><span class="kc">False</span><span class="p">,</span> <span class="n">histtype</span><span class="o">=</span><span class="s1">&#39;bar&#39;</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="n">colors</span><span class="p">,</span> 
         <span class="n">label</span><span class="o">=</span><span class="n">labels</span><span class="p">,</span> <span class="n">align</span><span class="o">=</span><span class="s1">&#39;left&#39;</span><span class="p">,</span><span class="n">alpha</span><span class="o">=</span><span class="mf">0.7</span><span class="p">,</span> <span class="n">rwidth</span><span class="o">=</span><span class="mi">5</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">legend</span><span class="p">(</span><span class="n">prop</span><span class="o">=</span><span class="p">{</span><span class="s1">&#39;size&#39;</span><span class="p">:</span> <span class="mi">10</span><span class="p">})</span>
<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;Vn&#39;</span><span class="p">)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAXcAAAEICAYAAACktLTqAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAALEgAACxIB0t1+/AAAADh0RVh0U29mdHdhcmUAbWF0cGxvdGxpYiB2ZXJzaW9uMy4xLjAsIGh0dHA6Ly9tYXRwbG90bGliLm9yZy+17YcXAAAU6ElEQVR4nO3dfYzV5Z338fe3oCJUUZEYldahtwgaCEgmFkptbdka1IJaa6u3D0hISdWqu94psibG7B3uVhOj66at3kQUmltxDWpRs9VW0Wztg+6guFpARHeQwQdAF1Z8aEW/9x9znB11eJg558yZuXy/EnJ+D9fv+n3PCfnMda7zO78TmYkkqSyfa3QBkqTaM9wlqUCGuyQVyHCXpAIZ7pJUIMNdkgpkuEtSgQx3feZFxIMR8b+72H5qRLwWEQMbUZdUDcNdgsXAuRERn9h+HnB7Zu5oQE1SVcJvqOqzLiL2BV4Dpmfmv1a2HQi8CnwZ+DvgbaAJ+BqwCvifmfliQwqW9oAjd33mZea7wF3A+Z02fw9Yk5nPVNbPAv4BOBBYB/yfXi1S6ibDXWq3GPhuRAyqrJ9f2faRezPzycoUze3AhN4uUOoOw10CMvNxYAtwWkT8D+A44I5OTV7rtPwO8PleLE/qNq8CkP7bL2kfsY8GHsrM1xtcj9Rjjtyl//ZL4G+AH/DxKRmp3zHcpYrMbAX+AAwB7mtsNVJ1vBRSkgrkyF2SCmS4S1KBDHdJKpDhLkkF6hPXuR988MHZ1NTU6DIkqV9ZsWLFlswc3tW+PhHuTU1NtLS0NLoMSepXImL9zvY5LSNJBTLcJalAhrskFahPzLlL6p/ef/992traeO+99xpdStEGDRrEiBEj2Guvvfb4GMNdUo+1tbWx33770dTUxKd/pVC1kJm88cYbtLW1MXLkyD0+zmkZST323nvvMWzYMIO9jiKCYcOGdfvdkeEuqSoGe/315DU23CWpQM65S6qd6dNr29/99+9y94ABAxg3bhw7duzg6KOPZvHixQwePLhHp3rssce47rrreOCBB7jvvvtYtWoV8+bN67Lt1q1bueOOO7jooosAeOWVV7j00ktZunRpj85dD4a7VJBaZ+tHdpOxDbPvvvuycuVKAM455xxuvvlmLr/88o79mUlm8rnPdW+SYsaMGcyYMWOn+7du3covfvGLjnA/7LDD+lSwg9Mykgpx/PHHs27dOlpbWxk9ejTnn38+Y8eOZcOGDfzmN79h8uTJTJw4kTPPPJPt27cD8OCDDzJmzBgmTpzIPffc09HXokWL+NGPfgTA66+/zumnn8748eMZP348f/jDH5g3bx4vvvgiEyZM4Mc//jGtra2MHTsWaP+QedasWYwbN45jjz2WRx99tKPP73znO0ybNo1Ro0Yxd+5cAD744AMuuOACxo4dy7hx47jhhhtq8no4cpfU7+3YsYNf//rXTJs2DYAXXniBxYsXM2nSJLZs2cL8+fN5+OGHGTJkCNdeey3XX389c+fO5Qc/+AHLly/nyCOP5Pvf/36XfV966aV8/etf59577+WDDz5g+/btXHPNNTz33HMd7xpaW1s72v/85z8nInj22WdZs2YNJ554ImvXrgVg5cqVPP300+yzzz6MHj2aSy65hE2bNrFx40aee+45oP1dQS04cpfUb7377rtMmDCB5uZmvvjFLzJ79mwAjjjiCCZNmgTAn/70J1atWsWUKVOYMGECixcvZv369axZs4aRI0cyatQoIoJzzz23y3MsX76cCy+8EGif4x86dOgua3r88cc7+hozZgxHHHFER7hPnTqVoUOHMmjQII455hjWr1/Pl770JV566SUuueQSHnzwQfbff/+avDaO3CX1W53n3DsbMmRIx3Jm8q1vfYslS5Z8rE1Xx9XbPvvs07E8YMAAduzYwYEHHsgzzzzDQw89xM0338xdd93FrbfeWvW5djtyj4hbI2JTRDzXadtBEfHbiHih8nhgZXtExD9FxLqI+PeImFh1hZJUhUmTJvH73/+edevWAfD222+zdu1axowZQ2trKy+++CLAp8L/I1OnTuWmm24C2ufHt23bxn777cdbb73VZfvjjz+e22+/HYC1a9fy8ssvM3r06J3Wt2XLFj788EPOOOMM5s+fz1NPPdXj59rZnozcFwE/A37Zads84JHMvCYi5lXWrwBOAkZV/n0ZuKnyKOmzoA9eVjN8+HAWLVrE2WefzV/+8hcA5s+fz1FHHcWCBQs45ZRTGDx4MMcff3yXgX3jjTcyZ84cFi5cyIABA7jpppuYPHkyU6ZMYezYsZx00klcfPHFHe0vuugiLrzwQsaNG8fAgQNZtGjRx0bsn7Rx40ZmzZrFhx9+CMBPf/rTmjzvyMzdN4po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
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[37]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">ones</span> <span class="o">=</span> <span class="n">comb</span><span class="p">[:,</span><span class="mi">0</span><span class="p">]</span><span class="o">==</span><span class="mi">5</span>
<span class="n">comb_ones</span> <span class="o">=</span> <span class="n">comb</span><span class="p">[</span><span class="n">ones</span><span class="p">]</span>
<span class="n">comb_ones_preds</span> <span class="o">=</span> <span class="n">comb_ones</span><span class="p">[:,</span><span class="mi">1</span><span class="p">]</span>
<span class="n">comb_ones_true</span> <span class="o">=</span> <span class="n">comb_ones</span><span class="p">[:,</span><span class="mi">0</span><span class="p">]</span>

<span class="n">n_bins</span> <span class="o">=</span> <span class="p">[</span><span class="o">-</span><span class="mf">0.5</span><span class="p">,</span><span class="mf">0.5</span><span class="p">,</span><span class="mf">1.5</span><span class="p">,</span><span class="mf">2.5</span><span class="p">,</span><span class="mf">3.5</span><span class="p">,</span><span class="mf">4.5</span><span class="p">,</span><span class="mf">5.5</span><span class="p">,</span><span class="mf">6.5</span><span class="p">]</span>

<span class="n">colors</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;red&#39;</span><span class="p">,</span> <span class="s1">&#39;blue&#39;</span><span class="p">]</span>
<span class="n">labels</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;Predictions&#39;</span><span class="p">,</span><span class="s1">&#39;Actual&#39;</span><span class="p">]</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xticks</span><span class="p">(</span><span class="nb">range</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span> <span class="mi">9</span><span class="p">))</span>
<span class="n">plt</span><span class="o">.</span><span class="n">hist</span><span class="p">((</span><span class="n">comb_ones_preds</span><span class="p">,</span><span class="n">comb_ones_true</span><span class="p">),</span> <span class="n">n_bins</span><span class="p">,</span> <span class="n">density</span><span class="o">=</span><span class="kc">False</span><span class="p">,</span> <span class="n">histtype</span><span class="o">=</span><span class="s1">&#39;bar&#39;</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="n">colors</span><span class="p">,</span> 
         <span class="n">label</span><span class="o">=</span><span class="n">labels</span><span class="p">,</span> <span class="n">align</span><span class="o">=</span><span class="s1">&#39;left&#39;</span><span class="p">,</span><span class="n">alpha</span><span class="o">=</span><span class="mf">0.7</span><span class="p">,</span> <span class="n">rwidth</span><span class="o">=</span><span class="mi">5</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">legend</span><span class="p">(</span><span class="n">prop</span><span class="o">=</span><span class="p">{</span><span class="s1">&#39;size&#39;</span><span class="p">:</span> <span class="mi">10</span><span class="p">})</span>
<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;Art/Pre-Art&#39;</span><span class="p">)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,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3oW3336byZMn09TUxMc//nHmzZsHwNFHH83UqVMBePTRR1m9ejXTp09n8uTJLFmyhPXr1/Pss88yduxYjj32WCKCr3/96x0eY8WKFVx00UVA2xz/yJEju6zpkUce2dXX+PHjOfroo3eF+8yZMxk5ciTDhg3jhBNOYP369XziE5/gxRdf5NJLL+X+++/noIMO6pPnRtLA5si9C+3n3NsbMWLErvuZyec//3mWLl36gTYd7dff9t9//133hwwZwo4dOzjkkEP44x//yC9/+UtuueUW7rzzTm677ba9XpukvWuPI/eIuC0iNkXE0+3WHRoRv4qI56vbQ6r1ERH/EBHrIuL/RsSU/ix+IJg6dSq//e1vWbduHQBvvfUWa9euZfz48bS0tPDCCy8AfCj83zdz5kxuvvlmoG1+fNu2bRx44IG8+eabHbafMWMGd9xxBwBr167lpZdeYty4cZ3Wt2XLFt577z3OPPNMFi5cyOOPP97rxypp8OjOyL2Ztl+Z/8d26xYAv87MayJiQbV8JXAKcGz19zfAzdVt7QboR+CjR4+mubmZc845h7/85S8ALFy4kOOOO45FixZx2mmnMXz4cGbMmNFhYN94441ceOGFLF68mCFDhnDzzTczbdo0pk+fzoQJEzjllFO45JJLdrW/+OKLueiii5g4cSINDQ00Nzd/YMS+u40bNzJ37lzee+89AL7//e/38TMgaSDq1m+oRkQjcF9mTqiWnwNOysxXIuII4OHMHBcRP6ruL929XVf9NzU15e4/1rFmzRqOP/74Xjwk9ZTPterBUyFrFxGrMrOpo229/UD18HaB/SpweHX/KGBDu3at1bqOirowIlZGxMrNmzf3sgxJUkdqPlsm24b+ex7+f3i/RZnZlJlNo0d3+BOAkqRe6m24v1ZNx1DdbqrWbwQ+1q7dmGqdJGkv6m243wvMqe7PAZa3W39+ddbMVGDbnubbJUl9b49ny0TEUuAk4LCIaAWuBq4B7oyIecB64KtV858DpwLrgD8Dc/uhZknSHuwx3DPznE42zeygbQKXdNBWkrQXDZpvqNbhir8A/PSnP+WMM85gzZo1jB8/vtN2zc3NnHzyyRx55JG9qqf9JYElqVZeW2YPli5dyqc//elOv2H6vubmZl5++eW9VJUkdc1w78L27dt55JFHWLx4MT/5yU92rb/22muZOHEikyZN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
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h1 id="Histograms-for-PLN-Test">Histograms for PLN Test<a class="anchor-link" href="#Histograms-for-PLN-Test">&#182;</a></h1>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">

<pre><code># TrEC = 0
# HEC / HEC late = 1
# CapEC1/2 = 2
# CRP / CRP Early = 3
# HEV = 4
# Pre-Art = 5
# Vn = 6
# Art = 7
# CapIfn = 8</code></pre>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[38]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">p</span><span class="p">,</span><span class="n">t</span>
<span class="n">plncomb</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">stack</span><span class="p">((</span><span class="n">t</span><span class="p">,</span><span class="n">p</span><span class="p">))</span>
<span class="n">plncomb</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">transpose</span><span class="p">(</span><span class="n">plncomb</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[39]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">plnones</span> <span class="o">=</span> <span class="n">plncomb</span><span class="p">[:,</span><span class="mi">0</span><span class="p">]</span><span class="o">==</span><span class="mi">0</span>
<span class="n">pln_ones</span> <span class="o">=</span> <span class="n">plncomb</span><span class="p">[</span><span class="n">plnones</span><span class="p">]</span>
<span class="n">pln_ones_preds</span> <span class="o">=</span> <span class="n">pln_ones</span><span class="p">[:,</span><span class="mi">1</span><span class="p">]</span>
<span class="n">pln_ones_true</span> <span class="o">=</span> <span class="n">pln_ones</span><span class="p">[:,</span><span class="mi">0</span><span class="p">]</span>

<span class="n">n_bins</span> <span class="o">=</span> <span class="p">[</span><span class="o">-</span><span class="mf">0.5</span><span class="p">,</span><span class="mf">0.5</span><span class="p">,</span><span class="mf">1.5</span><span class="p">,</span><span class="mf">2.5</span><span class="p">,</span><span class="mf">3.5</span><span class="p">,</span><span class="mf">4.5</span><span class="p">,</span><span class="mf">5.5</span><span class="p">,</span><span class="mf">6.5</span><span class="p">,</span><span class="mf">7.5</span><span class="p">,</span><span class="mf">8.5</span><span class="p">]</span>

<span class="n">colors</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;red&#39;</span><span class="p">,</span> <span class="s1">&#39;blue&#39;</span><span class="p">]</span>
<span class="n">labels</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;Predictions&#39;</span><span class="p">,</span><span class="s1">&#39;Actual&#39;</span><span class="p">]</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xticks</span><span class="p">(</span><span class="nb">range</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span> <span class="mi">9</span><span class="p">))</span>
<span class="n">plt</span><span class="o">.</span><span class="n">hist</span><span class="p">((</span><span class="n">pln_ones_preds</span><span class="p">,</span><span class="n">pln_ones_true</span><span class="p">),</span> <span class="n">n_bins</span><span class="p">,</span> <span class="n">density</span><span class="o">=</span><span class="kc">False</span><span class="p">,</span> <span class="n">histtype</span><span class="o">=</span><span class="s1">&#39;bar&#39;</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="n">colors</span><span class="p">,</span> 
         <span class="n">label</span><span class="o">=</span><span class="n">labels</span><span class="p">,</span> <span class="n">align</span><span class="o">=</span><span class="s1">&#39;left&#39;</span><span class="p">,</span><span class="n">alpha</span><span class="o">=</span><span class="mf">0.7</span><span class="p">,</span> <span class="n">rwidth</span><span class="o">=</span><span class="mi">5</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">legend</span><span class="p">(</span><span class="n">prop</span><span class="o">=</span><span class="p">{</span><span class="s1">&#39;size&#39;</span><span class="p">:</span> <span class="mi">10</span><span class="p">})</span>
<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;TrEC&#39;</span><span class="p">)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,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
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[40]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">plnones</span> <span class="o">=</span> <span class="n">plncomb</span><span class="p">[:,</span><span class="mi">0</span><span class="p">]</span><span class="o">==</span><span class="mi">1</span>
<span class="n">pln_ones</span> <span class="o">=</span> <span class="n">plncomb</span><span class="p">[</span><span class="n">plnones</span><span class="p">]</span>
<span class="n">pln_ones_preds</span> <span class="o">=</span> <span class="n">pln_ones</span><span class="p">[:,</span><span class="mi">1</span><span class="p">]</span>
<span class="n">pln_ones_true</span> <span class="o">=</span> <span class="n">pln_ones</span><span class="p">[:,</span><span class="mi">0</span><span class="p">]</span>

<span class="n">n_bins</span> <span class="o">=</span> <span class="p">[</span><span class="o">-</span><span class="mf">0.5</span><span class="p">,</span><span class="mf">0.5</span><span class="p">,</span><span class="mf">1.5</span><span class="p">,</span><span class="mf">2.5</span><span class="p">,</span><span class="mf">3.5</span><span class="p">,</span><span class="mf">4.5</span><span class="p">,</span><span class="mf">5.5</span><span class="p">,</span><span class="mf">6.5</span><span class="p">,</span><span class="mf">7.5</span><span class="p">,</span><span class="mf">8.5</span><span class="p">]</span>

<span class="n">colors</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;red&#39;</span><span class="p">,</span> <span class="s1">&#39;blue&#39;</span><span class="p">]</span>
<span class="n">labels</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;Predictions&#39;</span><span class="p">,</span><span class="s1">&#39;Actual&#39;</span><span class="p">]</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xticks</span><span class="p">(</span><span class="nb">range</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span> <span class="mi">9</span><span class="p">))</span>
<span class="n">plt</span><span class="o">.</span><span class="n">hist</span><span class="p">((</span><span class="n">pln_ones_preds</span><span class="p">,</span><span class="n">pln_ones_true</span><span class="p">),</span> <span class="n">n_bins</span><span class="p">,</span> <span class="n">density</span><span class="o">=</span><span class="kc">False</span><span class="p">,</span> <span class="n">histtype</span><span class="o">=</span><span class="s1">&#39;bar&#39;</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="n">colors</span><span class="p">,</span> 
         <span class="n">label</span><span class="o">=</span><span class="n">labels</span><span class="p">,</span> <span class="n">align</span><span class="o">=</span><span class="s1">&#39;left&#39;</span><span class="p">,</span><span class="n">alpha</span><span class="o">=</span><span class="mf">0.7</span><span class="p">,</span> <span class="n">rwidth</span><span class="o">=</span><span class="mi">5</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">legend</span><span class="p">(</span><span class="n">prop</span><span class="o">=</span><span class="p">{</span><span class="s1">&#39;size&#39;</span><span class="p">:</span> <span class="mi">10</span><span class="p">})</span>
<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;HEC / HEC Early&#39;</span><span class="p">)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,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
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[41]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">plnones</span> <span class="o">=</span> <span class="n">plncomb</span><span class="p">[:,</span><span class="mi">0</span><span class="p">]</span><span class="o">==</span><span class="mi">2</span>
<span class="n">pln_ones</span> <span class="o">=</span> <span class="n">plncomb</span><span class="p">[</span><span class="n">plnones</span><span class="p">]</span>
<span class="n">pln_ones_preds</span> <span class="o">=</span> <span class="n">pln_ones</span><span class="p">[:,</span><span class="mi">1</span><span class="p">]</span>
<span class="n">pln_ones_true</span> <span class="o">=</span> <span class="n">pln_ones</span><span class="p">[:,</span><span class="mi">0</span><span class="p">]</span>

<span class="n">n_bins</span> <span class="o">=</span> <span class="p">[</span><span class="o">-</span><span class="mf">0.5</span><span class="p">,</span><span class="mf">0.5</span><span class="p">,</span><span class="mf">1.5</span><span class="p">,</span><span class="mf">2.5</span><span class="p">,</span><span class="mf">3.5</span><span class="p">,</span><span class="mf">4.5</span><span class="p">,</span><span class="mf">5.5</span><span class="p">,</span><span class="mf">6.5</span><span class="p">,</span><span class="mf">7.5</span><span class="p">,</span><span class="mf">8.5</span><span class="p">]</span>

<span class="n">colors</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;red&#39;</span><span class="p">,</span> <span class="s1">&#39;blue&#39;</span><span class="p">]</span>
<span class="n">labels</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;Predictions&#39;</span><span class="p">,</span><span class="s1">&#39;Actual&#39;</span><span class="p">]</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xticks</span><span class="p">(</span><span class="nb">range</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span> <span class="mi">9</span><span class="p">))</span>
<span class="n">plt</span><span class="o">.</span><span class="n">hist</span><span class="p">((</span><span class="n">pln_ones_preds</span><span class="p">,</span><span class="n">pln_ones_true</span><span class="p">),</span> <span class="n">n_bins</span><span class="p">,</span> <span class="n">density</span><span class="o">=</span><span class="kc">False</span><span class="p">,</span> <span class="n">histtype</span><span class="o">=</span><span class="s1">&#39;bar&#39;</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="n">colors</span><span class="p">,</span> 
         <span class="n">label</span><span class="o">=</span><span class="n">labels</span><span class="p">,</span> <span class="n">align</span><span class="o">=</span><span class="s1">&#39;left&#39;</span><span class="p">,</span><span class="n">alpha</span><span class="o">=</span><span class="mf">0.7</span><span class="p">,</span> <span class="n">rwidth</span><span class="o">=</span><span class="mi">5</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">legend</span><span class="p">(</span><span class="n">prop</span><span class="o">=</span><span class="p">{</span><span class="s1">&#39;size&#39;</span><span class="p">:</span> <span class="mi">10</span><span class="p">})</span>
<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;CAPEC1 / 2&#39;</span><span class="p">)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,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
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[42]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">plnones</span> <span class="o">=</span> <span class="n">plncomb</span><span class="p">[:,</span><span class="mi">0</span><span class="p">]</span><span class="o">==</span><span class="mi">3</span>
<span class="n">pln_ones</span> <span class="o">=</span> <span class="n">plncomb</span><span class="p">[</span><span class="n">plnones</span><span class="p">]</span>
<span class="n">pln_ones_preds</span> <span class="o">=</span> <span class="n">pln_ones</span><span class="p">[:,</span><span class="mi">1</span><span class="p">]</span>
<span class="n">pln_ones_true</span> <span class="o">=</span> <span class="n">pln_ones</span><span class="p">[:,</span><span class="mi">0</span><span class="p">]</span>

<span class="n">n_bins</span> <span class="o">=</span> <span class="p">[</span><span class="o">-</span><span class="mf">0.5</span><span class="p">,</span><span class="mf">0.5</span><span class="p">,</span><span class="mf">1.5</span><span class="p">,</span><span class="mf">2.5</span><span class="p">,</span><span class="mf">3.5</span><span class="p">,</span><span class="mf">4.5</span><span class="p">,</span><span class="mf">5.5</span><span class="p">,</span><span class="mf">6.5</span><span class="p">,</span><span class="mf">7.5</span><span class="p">,</span><span class="mf">8.5</span><span class="p">]</span>

<span class="n">colors</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;red&#39;</span><span class="p">,</span> <span class="s1">&#39;blue&#39;</span><span class="p">]</span>
<span class="n">labels</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;Predictions&#39;</span><span class="p">,</span><span class="s1">&#39;Actual&#39;</span><span class="p">]</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xticks</span><span class="p">(</span><span class="nb">range</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span> <span class="mi">9</span><span class="p">))</span>
<span class="n">plt</span><span class="o">.</span><span class="n">hist</span><span class="p">((</span><span class="n">pln_ones_preds</span><span class="p">,</span><span class="n">pln_ones_true</span><span class="p">),</span> <span class="n">n_bins</span><span class="p">,</span> <span class="n">density</span><span class="o">=</span><span class="kc">False</span><span class="p">,</span> <span class="n">histtype</span><span class="o">=</span><span class="s1">&#39;bar&#39;</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="n">colors</span><span class="p">,</span> 
         <span class="n">label</span><span class="o">=</span><span class="n">labels</span><span class="p">,</span> <span class="n">align</span><span class="o">=</span><span class="s1">&#39;left&#39;</span><span class="p">,</span><span class="n">alpha</span><span class="o">=</span><span class="mf">0.7</span><span class="p">,</span> <span class="n">rwidth</span><span class="o">=</span><span class="mi">5</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">legend</span><span class="p">(</span><span class="n">prop</span><span class="o">=</span><span class="p">{</span><span class="s1">&#39;size&#39;</span><span class="p">:</span> <span class="mi">10</span><span class="p">})</span>
<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;CRP / CRP Early&#39;</span><span class="p">)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,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
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[43]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">plnones</span> <span class="o">=</span> <span class="n">plncomb</span><span class="p">[:,</span><span class="mi">0</span><span class="p">]</span><span class="o">==</span><span class="mi">4</span>
<span class="n">pln_ones</span> <span class="o">=</span> <span class="n">plncomb</span><span class="p">[</span><span class="n">plnones</span><span class="p">]</span>
<span class="n">pln_ones_preds</span> <span class="o">=</span> <span class="n">pln_ones</span><span class="p">[:,</span><span class="mi">1</span><span class="p">]</span>
<span class="n">pln_ones_true</span> <span class="o">=</span> <span class="n">pln_ones</span><span class="p">[:,</span><span class="mi">0</span><span class="p">]</span>

<span class="n">n_bins</span> <span class="o">=</span> <span class="p">[</span><span class="o">-</span><span class="mf">0.5</span><span class="p">,</span><span class="mf">0.5</span><span class="p">,</span><span class="mf">1.5</span><span class="p">,</span><span class="mf">2.5</span><span class="p">,</span><span class="mf">3.5</span><span class="p">,</span><span class="mf">4.5</span><span class="p">,</span><span class="mf">5.5</span><span class="p">,</span><span class="mf">6.5</span><span class="p">,</span><span class="mf">7.5</span><span class="p">,</span><span class="mf">8.5</span><span class="p">]</span>

<span class="n">colors</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;red&#39;</span><span class="p">,</span> <span class="s1">&#39;blue&#39;</span><span class="p">]</span>
<span class="n">labels</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;Predictions&#39;</span><span class="p">,</span><span class="s1">&#39;Actual&#39;</span><span class="p">]</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xticks</span><span class="p">(</span><span class="nb">range</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span> <span class="mi">9</span><span class="p">))</span>
<span class="n">plt</span><span class="o">.</span><span class="n">hist</span><span class="p">((</span><span class="n">pln_ones_preds</span><span class="p">,</span><span class="n">pln_ones_true</span><span class="p">),</span> <span class="n">n_bins</span><span class="p">,</span> <span class="n">density</span><span class="o">=</span><span class="kc">False</span><span class="p">,</span> <span class="n">histtype</span><span class="o">=</span><span class="s1">&#39;bar&#39;</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="n">colors</span><span class="p">,</span> 
         <span class="n">label</span><span class="o">=</span><span class="n">labels</span><span class="p">,</span> <span class="n">align</span><span class="o">=</span><span class="s1">&#39;left&#39;</span><span class="p">,</span><span class="n">alpha</span><span class="o">=</span><span class="mf">0.7</span><span class="p">,</span> <span class="n">rwidth</span><span class="o">=</span><span class="mi">5</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">legend</span><span class="p">(</span><span class="n">prop</span><span class="o">=</span><span class="p">{</span><span class="s1">&#39;size&#39;</span><span class="p">:</span> <span class="mi">10</span><span class="p">})</span>
<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;HEV&#39;</span><span class="p">)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,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CEXE5yNiTDYti4h5WcgTOVdExN9ExKiIqM9bf0FEHJtNd3WqWjOzTho/fjy//e1vaWhoAOCtt95iw4YNjBgxgsbGRl555RWAj3wQ7DV58mRuv/12IDeevmPHDo444gjefPPNNpc/5ZRTuPvuuwHYsGEDr776KsOHD2+3vq1bt/LBBx9w3nnnMXfuXJ577rmDfq97+RYIZtY1uunlRQMHDqS2tpbp06fz7rvvAjB37lyOO+445s+fz1lnnUXv3r055ZRT2gzvn//858yaNYs777yTiooKbr/9diZMmMDEiRMZOXIkZ5xxBldcccW+5S+//HIuu+wyRo0aRY8ePaitrf3QkXxrzc3NzJw5kw8++ACAH//4x51+z8pd+t69VFdXhx88YkXnyyu71Lp16zj++OPLXcYnQlu/a0mrIqK6reV9rxszs8Q56M3MEuegNzNLnIPezCxxDnozs8Q56M3MEufr6M2sS5ThLsUAPPDAA5x77rmsW7eOESNGtLtcbW0tU6ZM4eijjz6oevJvY9zd+YjezJJSV1fHySef3O43W/eqra3ltddeK1FV5eWgN7Nk7Ny5k6effpo777yTRYsW7Wu/6aabGDVqFKNHj2bOnDksXryY+vp6LrjgAsaMGcOuXbsYOnQoW7duBaC+vp5JkyYB8Pvf/54JEyYwduxYvvCFL7B+/fpyvLVO8dCNmSXjwQcfpKamhuOOO47+/fuzatUqtmzZwoMPPsizzz5L79692b59O0ceeSS33HILN998M9XVbX6ZdJ8RI0bwm9/8hh49evD444/z/e9/n/vuu69E76g4HPRmloy6ujquvvpqAKZNm0ZdXR0RwcyZM/c9UvDII488oG3u2LGDGTNm8PLLLyOJ999/v+h1dzUHvZklYfv27Sxfvpw1a9YgiT179iCJ888/v6D1e/Tose9GYu+8886+9uuvv57TTjuNJUuW0NjYuG9I5+PEY/RmloTFixdz0UUXsWnTJhobG9m8eTNVVVX07duXu+66i7fffhvIfSAAH7m18NChQ1m1ahXAh4ZmduzYwaBBuUdd19bWlujdFJeP6M2sS5T6Lp11dXV873vf+1Dbeeedx7p165g6dSrV1dUceuihnHnmmfzoRz/ikksu4dvf/jaHH344v/vd77jhhhu49NJLuf766z901H7ttdcyY8YM5s6dy1lnnVXaN1UkHd6mWNIC4CvAlogY2Ub/d4ELstkewPHAwOzpUo3Am8AeYHd7t9Bszbcpti7h2xR3Kd+muHS64jbFtUBNe50R8Y97nzwFXAf8n1aPCzwt6y8o5M3MrLgKeZTgU0Chz3mdDuz/WwpmZlZSRTsZK6k3uSP//AtMA3hU0ipJs4q1LzPrnrrjE+tSczC/42JedXM28NtWwzYnR8Q44AzgCklfbG9lSbMk1Uuqb2lpKWJZZlYKvXr1Ytu2bQ77LhQRbNu2jV69eh3QesW86mYarYZtIqI5+7lF0hLgROCptlaOiPnAfMidjC1iXWZWApWVlTQ1NeEDta7Vq1cvKisrD2idogS9pL7AqcCFeW19gEMi4s3s9RTgxmLsz8y6n549e1JVVVXuMqwNHQa9pDpgEjBAUhNwA9ATICLmZYudCzwaEW/lrfpZYImkvfu5JyIeLl7pZmZWiA6DPiKmF7BMLbnLMPPbNgKjD7YwMzMrDt8CwcwscQ56M7PEOejNzBLnoDczS5yD3swscQ56M7PEOejNzBLnoDczS5yD3swscQ56M7PEOejNzBLnoDczS5yD3swscQ56M7PEOejNzBLnoDczS5yD3swscR0GvaQFkrZIeqGd/kmSdkhanU0/yOurkbReUoOkOcUs3MzMClPIEX0tUNPBMr+JiDHZdCOApArgVuAM4ARguqQTOlOsmZkduA6DPiKeArYfxLZPBBoiYmNEvAcsAs45iO2YmVknFGuMfoKkP0h6SNLfZm2DgM15yzRlbW2SNEtSvaT6lpaWIpVlZmbFCPrngCERMRr478ADB7ORiJgfEdURUT1w4MAilGVmZlCEoI+Iv0bEzuz1MqCnpAFAMzA4b9HKrM3MzEqo00Ev6d9LUvb6xGyb24CVwDBJVZIOBaYBSzu7PzMzOzA9OlpAUh0wCRggqQm4AegJEBHzgK8Dl0naDewCpkVEALslzQYeASqABRHxYpe8CzMza1eHQR8R0zvovwW4pZ2+ZcCygyvNzMyKwd+MNTNLnIPezCxxDnozs8Q56M3MEuegNzNLnIPezCxxDnozs8Q56M3MEuegNzNLnIPezCxxDnozs8Q56M3MEuegNzNLnIPezCxxDnozs8Q56M3MEuegNzNLXIdBL2mBpC2SXmin/wJJf5S0RtIzkkbn9TVm7asl1RezcDMzK0whR/S1QM1++v8EnBoRo4AfAvNb9Z8WEWMiovrgSjQzs84o5JmxT0kaup/+Z/JmVwCVnS/LzMyKpdhj9JcCD+XNB/CopFWSZu1vRUmzJNVLqm9paSlyWWZmn1wdHtEXStJp5IL+5LzmkyOiWdK/Ax6T9FJEPNXW+hExn2zYp7q6OopVl5nZJ11RjuglfR64AzgnIrbtbY+I5uznFmAJcGIx9mdmZoXrdNBLOga4H7goIjbktfeRdMTe18AUoM0rd8zMrOt0OHQjqQ6YBAyQ1ATcAPQEiIh5wA+A/sBtkgB2Z1fYfBZYkrX1AO6JiIe74D2Ymdl+FHLVzfQO+r8JfLON9o3A6I+uYWZmpeRvxpqZJc5Bb2aWOAe9mVniHPRmZolz0JuZJc5Bb2aWOAe9mVniHPRmZolz0JuZJc5Bb2aWOAe9mVniHPRmZolz0JuZJc5Bb2aWOAe9mVniHPRmZolz0JuZJa6goJe0QNIWSW0+81U5/yypQdIfJY3L65sh6eVsmlGsws3MrDCFHtHXAjX76T8DGJZNs4DbASQdSe4ZsycBJwI3SOp3sMWamdmBKyjoI+IpYPt+FjkH+GXkrAA+I+ko4MvAYxGxPSL+AjzG/j8wzMysyIo1Rj8I2Jw335S1tdf+EZJmSaqXVN/S0lKksszMrNucjI2I+RFRHRHVAwcOLHc5ZmbJKFbQNwOD8+Yrs7b22s3MrESKFfRLgYuzq2/GAzsi4nXgEWCKpH7ZSdgpWZuZmZVIj0IWklQHTAIGSGoidyVNT4CImAcsA84EGoC3gZlZ33ZJPwRWZpu6MSL2d1LXzMyKrKCgj4jpHfQHcEU7fQuABQdempmZFUO3ORlrZmZdw0FvZpY4B72ZWeIc9GZmiXPQm5klzkFvZpY4B72ZWeIc9GZmiXPQm5klzkFvZpY4B72ZWeIc9GZmiXPQm5klzkFvZpY4B72ZWeIc9GZmiXPQm5klrqCgl1Qjab2kBklz2uj/maTV2bRB0ht5fXvy+pYWs3gzM+tYh48SlFQB3AqcDjQBKyUtjYi1e5eJiL/PW/5KYGzeJnZFxJjilWxmZgeikCP6E4GGiNgYEe8Bi4Bz9rP8dKCuGMWZmVnnFRL0g4DNefNNWdtHSBoCVAHL85p7SaqXtELSV9vbiaRZ2XL1LS0tBZRlZmaFKPbJ2GnA4ojYk9c2JCKqgb8D/knS37S1YkTMj4jqiKgeOHBgkcsyM/vkKiTom4HBefOVWVtbptFq2CYimrOfG4En+fD4vZmZdbFCgn4lMExSlaRDyYX5R66ekTQC6Af8Lq+tn6TDstcDgInA2tbrmplZ1+nwqpuI2C1pNvAIUAEsiIgXJd0I1EfE3tCfBiyKiMhb/XjgF5I+IPeh8pP8q3XMzKzrdRj0ABGxDFjWqu0Hreb/axvrPQOM6kR9ZmbWSf5mrJlZ4hz0ZmaJc9CbmSXOQW9mljgHvZlZ4hz0ZmaJc9CbmSXOQW9mljgHvZlZ4hz0ZmaJc9CbmSXOQW9mljgHvZlZ4hz0ZmaJc9CbmSXOQW9mljgHvZlZ4goKekk1ktZLapA0p43+SyS1SFqdTd/M65sh6eVsmlHM4s3MrGMdPkpQUgVwK3A60ASslLS0jWe//mtEzG617pHADUA1EMCqbN2/FKV6MzPrUCFH9CcCDRGxMSLeAxYB5xS4/S8Dj0XE9izcHwNqDq5UMzM7GIUE/SBgc958U9bW2nmS/ihpsaTBB7gukmZJqpdU39LSUkBZZmZWiGKdjP0VMDQiPk/uqH3hgW4gIuZHRHVEVA8cOLBIZZmZWSFB3wwMzpuvzNr2iYhtEfFuNnsH8B8KXdfMzLpWIUG/EhgmqUrSocA0YGn+ApKOypudCqzLXj8CTJHUT1I/YErWZmZmJdLhVTcRsVvSbHIBXQEsiIgXJd0I1EfEUuAqSVOB3cB24JJs3e2SfkjuwwLgxojY3gXvw8zM2tFh0ANExDJgWau2H+S9vg64rp11FwALOlGjmZl1gr8Za2aWOAe9mVniHPRmZolz0JuZJc5Bb2aWOAe9mVniHPRmZolz0JuZJc5Bb2aWOAe9mVniHPRmZolz0JuZJc5Bb2aWOAe9mVniHPRmZolz0JuZJc5Bb2aWuIKCXlKNpPWSGiTNaaP/GklrJf1R0v+WNCSvb4+k1dm0tPW6ZmbWtTp8lKCkCuBW4HSgCVgpaWlErM1b7HmgOiLelnQZ8A/AN7K+XRExpsh1m5lZgQo5oj8RaIiIjRHxHrAIOCd/gYh4IiLezmZXAJXFLdPMzA5WIUE/CNicN9+UtbXnUuChvPlekuolrZD01fZWkjQrW66+paWlgLLMzKwQHQ7dHAhJFwLVwKl5zUMiolnS54DlktZExCut142I+cB8gOrq6ihmXWZmn2SFHNE3A4Pz5iuztg+R9CXgvwBTI+Ldve0R0Zz93Ag8CYztRL1mZnaACgn6lcAwSVWSDgWmAR+6ekbSWOAX5EJ+S157P0mHZa8HABOB/JO4ZmbWxTocuomI3ZJmA48AFcCCiHhR0o1AfUQsBf4R+BTwb5IAXo2IqcDxwC8kfUDuQ+Unra7WMTOzLlbQGH1ELAOWtWr7Qd7rL7Wz3jPAqM4UaGZmneNvxpqZJc5Bb2aWOAe9mVniHPRmZolz0JuZJc5Bb2aWOAe9mVniHPRmZolz0JuZJc5Bb2aWOAe9mVniHPRmZolz0JuZJc5Bb2aWOAe9mVniHPRmZolz0JuZJa6goJdUI2m9pAZJc9roP0zSv2b9z0oamtd3Xda+XtKXi1e6mZkVosOgl1QB3AqcAZwATJd0QqvFLgX+EhHHAj8DbsrWPYHcw8T/FqgBbsu2Z2ZmJVLIEf2JQENEbIyI94BFwDmtljkHWJi9XgxMVu4p4ecAiyLi3Yj4E9CQbc/MzEqkkIeDDwI25803ASe1t0xE7Ja0A+ifta9ote6gtnYiaRYwK5vdKWl9AbV1ZwOAra4BSKoOdboIKaXfR1F0hzq6Qw3QuTqGtNdRSNCXRETMB+aXu45ikVQfEdWf9Bpch+v4ONTRHWroyjoKGbppBgbnzVdmbW0uI6kH0BfYVuC6ZmbWhQoJ+pXAMElVkg4ld3J1aatllgIzstdfB5ZHRGTt07KrcqqAYcDvi1O6mZkVosOhm2zMfTbwCFABLIiIFyXdCNRHxFLgTuBfJDUA28l9GJAtdy+wFtgNXBERe7rovXQ33WEYqjvUAK6jNdfxYd2hju5QA3RRHcodeJuZWar8zVgzs8Q56M3MEuegL7KObhdRohoWSNoi6YVy7D+vjsGSnpC0VtKLkq4uUx29JP1e0h+yOv5bOerIaqmQ9LykX5exhkZJayStllRfxjo+I2mxpJckrZM0oQw1DM9+D3unv0r6TqnryGr5++zf5wuS6iT1Ktq2PUZfPNntHTYAp5P7cthKYHpErC1xHV8EdgK/jIiRpdx3qzqOAo6KiOckHQGsAr5aht+HgD4RsVNST+Bp4OqIWNHBql1RyzVANfDpiPhKqfef1dAIVEdEWb8gJGkh8JuIuCO7oq93RLxRxnoqyF3+fVJEbCrxvgeR+3d5QkTsyi5iWRYRtcXYvo/oi6uQ20V0uYh4itzVT2UVEa9HxHPZ6zeBdbTzzeguriMiYmc22zObSn6EI6kSOAu4o9T77m4k9QW+SO6KPSLivXKGfGYy8EqpQz5PD+Dw7LtIvYHXirVhB31xtXW7iJIHW3eU3dF0LPBsmfZfIWk1sAV4LCLKUcc/AdcCH5Rh3/kCeFTSquzWI+VQBbQAd2VDWXdI6lOmWvaaBtSVY8cR0QzcDLwKvA7siIhHi7V9B711OUmfAu4DvhMRfy1HDRGxJyLGkPt29omSSjqkJekrwJaIWFXK/bbj5IgYR+6OtFdkQ32l1gMYB9weEWOBt4CynNMCyIaOpgL/Vqb99yP3138VcDTQR9KFxdq+g764fMuHVrIx8fuAuyPi/nLXkw0PPEHuttmlNBGYmo2PLwL+o6T/WeIagH1Hj0TEFmAJ5bmjbBPQlPeX1WJywV8uZwDPRcSfy7T/LwF/ioiWiHgfuB/4QrE27qAvrkJuF/GJkZ0EvRNYFxE/LWMdAyV9Jnt9OLmT5S+VsoaIuC4iKiNiKLl/F8sjomhHbIWS1Cc7MU42VDIFKPnVWRHxf4HNkoZnTZPJfYO+XKZTpmGbzKvAeEm9s/83k8md0yqKbnP3yhS0d7uIUtchqQ6YBAyQ1ATcEBF3lroOckexFwFrsvFxgO9HxLIS13EUsDC7quIQ4N6IKNvljWX2WWBJLkvoAdwTEQ+XqZYrgbuzg6KNwMxyFJF94J0O/Kdy7B8gIp6VtBh4jtztYp6niLdD8OWVZmaJ89CNmVniHPRmZolz0JuZJc5Bb2aWOAe9mVniHPRmZolz0JuZJe7/AcyRn0i4gLsoAAAAAElFTkSuQmCC
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[44]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">plnones</span> <span class="o">=</span> <span class="n">plncomb</span><span class="p">[:,</span><span class="mi">0</span><span class="p">]</span><span class="o">==</span><span class="mi">5</span>
<span class="n">pln_ones</span> <span class="o">=</span> <span class="n">plncomb</span><span class="p">[</span><span class="n">plnones</span><span class="p">]</span>
<span class="n">pln_ones_preds</span> <span class="o">=</span> <span class="n">pln_ones</span><span class="p">[:,</span><span class="mi">1</span><span class="p">]</span>
<span class="n">pln_ones_true</span> <span class="o">=</span> <span class="n">pln_ones</span><span class="p">[:,</span><span class="mi">0</span><span class="p">]</span>

<span class="n">n_bins</span> <span class="o">=</span> <span class="p">[</span><span class="o">-</span><span class="mf">0.5</span><span class="p">,</span><span class="mf">0.5</span><span class="p">,</span><span class="mf">1.5</span><span class="p">,</span><span class="mf">2.5</span><span class="p">,</span><span class="mf">3.5</span><span class="p">,</span><span class="mf">4.5</span><span class="p">,</span><span class="mf">5.5</span><span class="p">,</span><span class="mf">6.5</span><span class="p">,</span><span class="mf">7.5</span><span class="p">,</span><span class="mf">8.5</span><span class="p">]</span>

<span class="n">colors</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;red&#39;</span><span class="p">,</span> <span class="s1">&#39;blue&#39;</span><span class="p">]</span>
<span class="n">labels</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;Predictions&#39;</span><span class="p">,</span><span class="s1">&#39;Actual&#39;</span><span class="p">]</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xticks</span><span class="p">(</span><span class="nb">range</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span> <span class="mi">9</span><span class="p">))</span>
<span class="n">plt</span><span class="o">.</span><span class="n">hist</span><span class="p">((</span><span class="n">pln_ones_preds</span><span class="p">,</span><span class="n">pln_ones_true</span><span class="p">),</span> <span class="n">n_bins</span><span class="p">,</span> <span class="n">density</span><span class="o">=</span><span class="kc">False</span><span class="p">,</span> <span class="n">histtype</span><span class="o">=</span><span class="s1">&#39;bar&#39;</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="n">colors</span><span class="p">,</span> 
         <span class="n">label</span><span class="o">=</span><span class="n">labels</span><span class="p">,</span> <span class="n">align</span><span class="o">=</span><span class="s1">&#39;left&#39;</span><span class="p">,</span><span class="n">alpha</span><span class="o">=</span><span class="mf">0.7</span><span class="p">,</span> <span class="n">rwidth</span><span class="o">=</span><span class="mi">5</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">legend</span><span class="p">(</span><span class="n">prop</span><span class="o">=</span><span class="p">{</span><span class="s1">&#39;size&#39;</span><span class="p">:</span> <span class="mi">10</span><span class="p">})</span>
<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;Pre-Art&#39;</span><span class="p">)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAXAAAAEICAYAAABGaK+TAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAALEgAACxIB0t1+/AAAADh0RVh0U29mdHdhcmUAbWF0cGxvdGxpYiB2ZXJzaW9uMy4xLjAsIGh0dHA6Ly9tYXRwbG90bGliLm9yZy+17YcXAAAVN0lEQVR4nO3dfZDV1Z3n8fdXQBFUxgfWUlHBREEXiobqcSBIYobRQh1JjONGyihSbkh8dp0KYa21nK1iE60yOpky0WGCaWZG23JQgnGNMQazkTyYaZQMCIoP2whIeNBIxGgi+N0/+sK22E0/Xfr2Ie9X1a2+9/c793e+99p+OH3u73duZCaSpPIcUOsCJEndY4BLUqEMcEkqlAEuSYUywCWpUAa4JBXKAJekQhngKlZENEfEuxGxPSI2RURDRBxSxeNHRLwaEas62f4nEfFfq9W/1BEDXKU7PzMPAcYD9cD/aL2zEsLd/T3/JPCfgJMi4s/ba9TDPqRu85dO+4XM3AD8ABhdGQn/r4j4GfB7WgJ4SETMj4iNEbEhIuZGRL8ODjsDWAw8Vrm/Wxt9/AswGbir8hfBXdV+jdKe+te6AKkaIuJ44FzgYVqC9FLgHOBFIIAHgc3Ax4HBwKPAOuAf2zneIOBvgIuBg4F/jIgbM/OPrZrt2cdxwL9m5neq/fqktjgCV+m+FxFvAUuB/wN8rbK9ITOfz8wdwBG0hPsNmflOZm4G7qQlnNvzOeAPwBPA/wYGAOft0WZ3H5n5fvVektQ5jsBVus9m5pOtN0QEtIyudzmRlgDeWNkHLYOXdZX2z1faAJyTmU/TMmXyYOUfgB0R8VBl26JWx23dh9TrDHDtr1ovs7mOltH0UZVA/nDDzP/c+nFEDAP+Ejg9Ii6sbB4EDIyIozJzaxt9tPVY2qecQtF+LzM30jIV8o2IOCwiDoiIj0XEp9p5yqXAGmAkUFe5nQKsB6bvpatNwEnVq1zaOwNcfyouAw4EVgG/BRYCx7TTdgbw7cz8TesbcA97nI2yh28CfxMRv42If6hi7VKbwi90kKQyOQKXpEIZ4JJUKANckgplgEtSoXr1PPCjjjoqhw8f3ptdSlLxli1btjUzh+65vVcDfPjw4TQ1NfVml5JUvIhY29Z2p1AkqVAGuCQVygCXpEK5mJWkvXr//fdZv3497733Xq1L2e8NHDiQYcOGMWDAgE61N8Al7dX69es59NBDGT58OK2W41WVZSZvvPEG69evZ8SIEZ16jlMokvbqvffe48gjjzS897GI4Mgjj+zSXzoGuKQOGd69o6vvswEuSYVyDlxS15x/fnWP9/3vd9ikX79+jBkzhh07dnDqqaeyYMECBg0a1K3ufvKTn3D77bfz6KOP8sgjj7Bq1SrmzJnTZtu33nqL+++/n6uuugqA119/neuuu46FCxd2q+9qM8ClPqQa2diJPCzOwQcfzPLlywG45JJLuOeee7jxxht3789MMpMDDujapMK0adOYNm1au/vfeustvv3tb+8O8GOPPbbPhDc4hSKpMJMnT+bll1+mubmZkSNHctlllzF69GjWrVvHE088wcSJExk/fjwXXXQR27dvB+Dxxx9n1KhRjB8/nocffnj3sRoaGrjmmmsA2LRpExdccAFjx45l7Nix/PznP2fOnDm88sor1NXV8ZWvfIXm5mZGjx4NtHy4O3PmTMaMGcO4ceN46qmndh/zc5/7HFOnTuXkk09m9uzZAOzcuZPLL7+c0aNHM2bMGO68884evxeOwCUVY8eOHfzgBz9g6tSpALz00kssWLCACRMmsHXrVubOncuTTz7J4MGDue2227jjjjuYPXs2X/ziF1myZAkf//jH+fznP9/msa+77jo+9alPsWjRInbu3Mn27du59dZbWbly5e7Rf3Nz8+723/rWt4gIVqxYwQsvvMDZZ5/NmjVrAFi+fDnPPfccBx10ECNHjuTaa69l8+bNbNiwgZUrVwIto/uecgQuqc979913qauro76+nhNOOIErrrgCgBNPPJEJEyYA8Mtf/pJVq1YxadIk6urqWLBgAWvXruWFF15gxIgRnHzyyUQEX/jCF9rsY8mSJVx55ZVAy5z7kCFD9lrT0qVLdx9r1KhRnHjiibsDfMqUKQwZMoSBAwdy2mmnsXbtWk466SReffVVrr32Wh5//HEOO+ywHr8vjsAl9Xmt58BbGzx48O77mclZZ51FY2Pjh9q09bx97aCDDtp9v1+/fuzYsYPDDz+cX//61/zwhz/knnvu4cEHH+Tee+/tUT8djsAj4viIeCoiVkXE8xFxfWX730XEhohYXrmd26NKJKkHJkyYwM9+9jNefvllAN555x3WrFnDqFGjaG5u5pVXXgH4SMDvMmXKFO6+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
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[45]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">plnones</span> <span class="o">=</span> <span class="n">plncomb</span><span class="p">[:,</span><span class="mi">0</span><span class="p">]</span><span class="o">==</span><span class="mi">6</span>
<span class="n">pln_ones</span> <span class="o">=</span> <span class="n">plncomb</span><span class="p">[</span><span class="n">plnones</span><span class="p">]</span>
<span class="n">pln_ones_preds</span> <span class="o">=</span> <span class="n">pln_ones</span><span class="p">[:,</span><span class="mi">1</span><span class="p">]</span>
<span class="n">pln_ones_true</span> <span class="o">=</span> <span class="n">pln_ones</span><span class="p">[:,</span><span class="mi">0</span><span class="p">]</span>

<span class="n">n_bins</span> <span class="o">=</span> <span class="p">[</span><span class="o">-</span><span class="mf">0.5</span><span class="p">,</span><span class="mf">0.5</span><span class="p">,</span><span class="mf">1.5</span><span class="p">,</span><span class="mf">2.5</span><span class="p">,</span><span class="mf">3.5</span><span class="p">,</span><span class="mf">4.5</span><span class="p">,</span><span class="mf">5.5</span><span class="p">,</span><span class="mf">6.5</span><span class="p">,</span><span class="mf">7.5</span><span class="p">,</span><span class="mf">8.5</span><span class="p">]</span>

<span class="n">colors</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;red&#39;</span><span class="p">,</span> <span class="s1">&#39;blue&#39;</span><span class="p">]</span>
<span class="n">labels</span> <span class="o">=</span> <span class="p">[</span><span class="s1">&#39;Predictions&#39;</span><span class="p">,</span><span class="s1">&#39;Actual&#39;</span><span class="p">]</span>
<span class="n">plt</span><span class="o">.</span><span class="n">xticks</span><span class="p">(</span><span class="nb">range</span><span class="p">(</span><span class="mi">0</span><span class="p">,</span> <span class="mi">9</span><span class="p">))</span>
<span class="n">plt</span><span class="o">.</span><span class="n">hist</span><span class="p">((</span><span class="n">pln_ones_preds</span><span class="p">,</span><span class="n">pln_ones_true</span><span class="p">),</span> <span class="n">n_bins</span><span class="p">,</span> <span class="n">density</span><span class="o">=</span><span class="kc">False</span><span class="p">,</span> <span class="n">histtype</span><span class="o">=</span><span class="s1">&#39;bar&#39;</span><span class="p">,</span> <span class="n">color</span><span class="o">=</span><span class="n">colors</span><span class="p">,</span> 
         <span class="n">label</span><span class="o">=</span><span class="n">labels</span><span class="p">,</span> <span class="n">align</span><span class="o">=</span><span class="s1">&#39;left&#39;</span><span class="p">,</span><span class="n">alpha</span><span class="o">=</span><span class="mf">0.7</span><span class="p">,</span> <span class="n">rwidth</span><span class="o">=</span><span class="mi">5</span><span class="p">)</span>
<span class="n">plt</span><span class="o">.</span><span class="n">legend</span><span class="p">(</span><span class="n">prop</span><span class="o">=</span><span class="p">{</span><span class="s1">&#39;size&#39;</span><span class="p">:</span> <span class="mi">10</span><span class="p">})</span>
<span class="n">plt</span><span class="o">.</span><span class="n">title</span><span class="p">(</span><span class="s1">&#39;Vn&#39;</span><span class="p">)</span>

<span class="n">plt</span><span class="o">.</span><span class="n">show</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>




<div class="output_png output_subarea ">
<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAXAAAAEICAYAAABGaK+TAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAALEgAACxIB0t1+/AAAADh0RVh0U29mdHdhcmUAbWF0cGxvdGxpYiB2ZXJzaW9uMy4xLjAsIGh0dHA6Ly9tYXRwbG90bGliLm9yZy+17YcXAAAVOUlEQVR4nO3de4yV9b3v8fe3DMqllnqZ06hUh+4qaCACmbQgtbWlGqwVa62nerxyTDnVVm27U0o98Zh9wmlrjrG7SVsNEYVmI8aDUi/Z9bbRWFsve0A8UEC87EEHLwwaqXhpBb/nj1lyhhGZYdZirfnJ+5UQ1nrWs57nM8vh429+z2UiM5EkledjjQ4gSeofC1ySCmWBS1KhLHBJKpQFLkmFssAlqVAWuCQVygLXXiMi7o6I/7mT5adGxMsR0dSIXFJ/WeDamywAzomI6LH8XGBhZm5tQCap38IrMbW3iIihwMvAKZn5UGXZ/sBLwOeBHwJvAi3AF4HVwH/JzGcbEljqhSNw7TUy823gFuC8bov/M7A2M5+sPD8T+Cdgf+AZ4H/VNaS0Gyxw7W0WAN+KiCGV5+dVlr1vSWY+XplOWQiMr3dAqa8scO1VMvNhYBPwjYj4B+BzwE3dVnm52+O3gI/XMZ60Wzzqrr3R7+gaeY8G7snMVxqcR+oXR+DaG/0O+CrwHXacPpGKYoFrr5OZ7cCfgeHAHY1NI/WfpxFKUqEcgUtSoSxwSSqUBS5JhbLAJalQdT0P/KCDDsqWlpZ67lKSirds2bJNmdncc3ldC7ylpYW2trZ67lKSihcR63e23CkUSSqUBS5JhbLAJalQDb+Z1bvvvktHRwfvvPNOo6N8pA0ZMoSRI0cyePDgRkeRVCMNL/COjg72228/Wlpa+OBvulItZCavvvoqHR0djBo1qtFxJNVIw6dQ3nnnHQ488EDLew+KCA488EB/ypE+Ynot8Ii4ISI2RsSqnbz2jxGREXFQNSEs7z3Pz1j66OnLCHw+MK3nwoj4NHAi8HyNM0mS+qDXOfDMfCgiWnby0i+BWcDtNU10yik13Rx33tnrKoMGDWLcuHFs3bqVo446igULFjBs2LB+7e7BBx/k6quv5q677uKOO+5g9erVzJ49e6frvv7669x0001cfPHFALz44otceumlLF68uF/7lrR36ddBzIg4FdiQmU/29qN5RMwEZgIcdthh/dndHjd06FBWrFgBwNlnn811113Hj370o+2vZyaZycc+tnuHDKZPn8706dM/9PXXX3+d3/72t9sL/JBDDrG8NSDUYhzVh7GTqrTbBzEjYhhwOfA/+rJ+Zs7NzNbMbG1u/sCl/APOcccdxzPPPEN7ezujR4/mvPPOY+zYsbzwwgvce++9TJ48mYkTJ3LGGWewZcsWAO6++27GjBnDxIkTue2227Zva/78+Xz/+98H4JVXXuG0007jmGOO4ZhjjuHPf/4zs2fP5tlnn2X8+PH8+Mc/pr29nbFjxwJdB3dnzJjBuHHjmDBhAg888MD2bX7zm99k2rRpHHHEEcyaNQuAbdu2ccEFFzB27FjGjRvHL3/5y3p+bJIaoD8j8H8ARgHvj75HAssj4nOZ+fIu3znAbd26lT/84Q9Mm9Y15f/000+zYMECJk2axKZNm5gzZw73338/w4cP56qrruKaa65h1qxZfOc732Hp0qV89rOf5dvf/vZOt33ppZfypS99iSVLlrBt2za2bNnCL37xC1atWrV99N/e3r59/d/85jdEBCtXrmTt2rWceOKJrFu3DoAVK1bwxBNPsO+++zJ69GguueQSNm7cyIYNG1i1qutY8+uvv74HPylJA8Fuj8Azc2Vm/qfMbMnMFqADmFhyeb/99tuMHz+e1tZWDjvsMC688EIADj/8cCZNmgTAo48+yurVq5kyZQrjx49nwYIFrF+/nrVr1zJq1CiOOOIIIoJzzjlnp/tYunQpF110EdA15z5ixIhdZnr44Ye3b2vMmDEcfvjh2wt86tSpjBgxgiFDhnD00Uezfv16PvOZz/Dcc89xySWXcPfdd/OJT3yiJp+NpIGr1xF4RCwCjgcOiogO4MrMnLeng9VT9znw7oYPH779cWZywgknsGjRoh3W2dn79rR99913++NBgwaxdetW9t9/f5588knuuecerrvuOm655RZuuOGGumeTVD+9jsAz86zMPDgzB2fmyJ7lXRmJb9pzEQeGSZMm8ac//YlnnnkGgDfffJN169YxZswY2tvbefbZZwE+UPDvmzp1Ktdeey3QNV+9efNm9ttvP954442drn/cccexcOFCANatW8fzzz/P6NGjPzTfpk2beO+99zj99NOZM2cOy5cv7/fXKqkMDb+U/gMG6KHr5uZm5s+fz1ln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
"
>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<h2 id="Deep-Dataset">Deep Dataset<a class="anchor-link" href="#Deep-Dataset">&#182;</a></h2>
</div>
</div>
</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Below is an attempt to make a classifier for a different dataset with fewer features and more cells: the "deep" dataset. It was largely unsuccessful and needs further effort.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[46]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">trainXdf1</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">read_csv</span><span class="p">(</span><span class="s1">&#39;/Users/tjshruti/Downloads/PLN123.csv&#39;</span><span class="p">)</span>
<span class="n">trainXgenesDF</span> <span class="o">=</span> <span class="n">pd</span><span class="o">.</span><span class="n">read_csv</span><span class="p">(</span><span class="s1">&#39;/Users/tjshruti/Downloads/GeneNamesPLN123.csv&#39;</span><span class="p">)</span>                    
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[47]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">trainXarr1</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">asarray</span><span class="p">(</span><span class="n">trainXdf1</span><span class="p">)</span>
<span class="n">X1</span> <span class="o">=</span> <span class="n">trainXarr1</span><span class="p">[:,</span><span class="mi">7</span><span class="p">:</span><span class="mi">3087</span><span class="p">]</span>
<span class="n">Y_Arr1</span> <span class="o">=</span> <span class="n">trainXarr1</span><span class="p">[:,</span><span class="mi">3</span><span class="p">]</span>
<span class="n">Y_Arr1</span><span class="o">.</span><span class="n">shape</span><span class="p">,</span> <span class="n">X1</span><span class="o">.</span><span class="n">shape</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[47]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>((7592,), (7592, 3080))</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[48]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># TrEC(ontPC1_2 and tspUMAP) = 0</span>
<span class="c1"># HEC plus (temp) = 1</span>
<span class="c1"># CapEC2 = 2</span>
<span class="c1"># Vn = 3</span>
<span class="c1"># TrEC_Early = 4</span>
<span class="c1"># CRP = 5</span>
<span class="c1"># HEV(late_Sept1) = 6</span>
<span class="c1"># CapEC1 = 7</span>
<span class="c1"># CRP(eraly_Aug31)) = 8</span>
<span class="c1"># TrEC_Early = 9</span>
<span class="c1"># Art = 10</span>
<span class="c1">#</span>


<span class="n">Y_Arr2</span> <span class="o">=</span> <span class="n">np</span><span class="o">.</span><span class="n">zeros</span><span class="p">((</span><span class="mi">7592</span><span class="p">,</span> <span class="mi">1</span><span class="p">))</span>
<span class="k">for</span> <span class="n">x</span> <span class="ow">in</span> <span class="nb">range</span><span class="p">(</span><span class="mi">7592</span><span class="p">):</span>
    <span class="k">if</span> <span class="p">(</span><span class="n">Y_Arr1</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">==</span> <span class="s1">&#39;TrEC&#39;</span><span class="p">):</span>
        <span class="n">Y_Arr2</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">=</span> <span class="mi">0</span>
    <span class="k">elif</span> <span class="p">(</span><span class="n">Y_Arr1</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">==</span> <span class="s1">&#39;HEC&#39;</span><span class="p">):</span>
        <span class="n">Y_Arr2</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">=</span> <span class="mi">1</span>
    <span class="k">elif</span> <span class="p">(</span><span class="n">Y_Arr1</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">==</span> <span class="s1">&#39;HEC (late)&#39;</span><span class="p">):</span>
        <span class="n">Y_Arr2</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">=</span> <span class="mi">1</span>
    <span class="k">elif</span><span class="p">(</span><span class="n">Y_Arr1</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">==</span> <span class="s1">&#39;CapEC1&#39;</span><span class="p">):</span>
        <span class="n">Y_Arr2</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">=</span> <span class="mi">2</span>
    <span class="k">elif</span> <span class="p">(</span><span class="n">Y_Arr1</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">==</span> <span class="s1">&#39;CapEC2&#39;</span><span class="p">):</span>
        <span class="n">Y_Arr2</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">=</span> <span class="mi">2</span>
    <span class="k">elif</span> <span class="p">(</span><span class="n">Y_Arr1</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">==</span> <span class="s1">&#39;CRP&#39;</span><span class="p">):</span>
        <span class="n">Y_Arr2</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">=</span> <span class="mi">3</span>
    <span class="k">elif</span> <span class="p">(</span><span class="n">Y_Arr1</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">==</span> <span class="s1">&#39;Caplfn&#39;</span><span class="p">):</span>
        <span class="n">Y_Arr2</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">=</span> <span class="mi">4</span>
    <span class="k">elif</span> <span class="p">(</span><span class="n">Y_Arr1</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">==</span> <span class="s1">&#39;Pre-Art&#39;</span><span class="p">):</span>
        <span class="n">Y_Arr2</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">=</span> <span class="mi">5</span>
    <span class="k">elif</span> <span class="p">(</span><span class="n">Y_Arr1</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">==</span> <span class="s1">&#39;CRP (early)&#39;</span><span class="p">):</span>
        <span class="n">Y_Arr2</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">=</span> <span class="mi">3</span>
    <span class="k">elif</span><span class="p">(</span><span class="n">Y_Arr1</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">==</span> <span class="s1">&#39;Vn&#39;</span><span class="p">):</span>
        <span class="n">Y_Arr2</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">=</span> <span class="mi">6</span>
    <span class="k">elif</span><span class="p">(</span><span class="n">Y_Arr1</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">==</span> <span class="s1">&#39;Art&#39;</span><span class="p">):</span>
        <span class="n">Y_Arr2</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">=</span> <span class="mi">7</span>
    <span class="k">else</span><span class="p">:</span>
        <span class="n">Y_Arr2</span><span class="p">[</span><span class="n">x</span><span class="p">]</span> <span class="o">=</span> <span class="mi">8</span>
        
<span class="nb">print</span><span class="p">(</span><span class="n">Y_Arr2</span>
     <span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>[[0.]
 [1.]
 [2.]
 ...
 [2.]
 [2.]
 [2.]]
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[49]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="kn">from</span> <span class="nn">sklearn.model_selection</span> <span class="k">import</span> <span class="n">train_test_split</span>

<span class="n">trainX1</span><span class="p">,</span> <span class="n">testX1</span><span class="p">,</span> <span class="n">trainY1</span><span class="p">,</span> <span class="n">testY1</span> <span class="o">=</span> <span class="n">train_test_split</span><span class="p">(</span><span class="n">X1</span><span class="p">,</span> <span class="n">Y_Arr2</span><span class="p">,</span> <span class="n">train_size</span> <span class="o">=</span> <span class="mf">0.9</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[50]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">trainX1</span><span class="o">.</span><span class="n">shape</span><span class="p">,</span> <span class="n">trainY1</span><span class="o">.</span><span class="n">shape</span><span class="p">,</span> <span class="n">testX1</span><span class="o">.</span><span class="n">shape</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt output_prompt">Out[50]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>((6832, 3080), (6832, 1), (760, 3080))</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[51]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">classifier</span> <span class="o">=</span> <span class="n">Sequential</span><span class="p">()</span>
<span class="n">classifier</span><span class="o">.</span><span class="n">add</span><span class="p">(</span><span class="n">Dense</span><span class="p">(</span><span class="mi">25</span><span class="p">,</span> <span class="n">activation</span><span class="o">=</span><span class="s1">&#39;relu&#39;</span><span class="p">,</span> <span class="n">input_dim</span><span class="o">=</span><span class="mi">3080</span><span class="p">,</span> <span class="n">kernel_initializer</span><span class="o">=</span><span class="s1">&#39;random_normal&#39;</span><span class="p">))</span>
<span class="c1">#classifier.add(Dropout(rate = 0.5))</span>
<span class="c1">#classifier.add(Dropout(rate = 0.5))</span>
<span class="n">classifier</span><span class="o">.</span><span class="n">add</span><span class="p">(</span><span class="n">Dense</span><span class="p">(</span><span class="mi">9</span><span class="p">,</span> <span class="n">activation</span><span class="o">=</span><span class="s1">&#39;sigmoid&#39;</span><span class="p">,</span> <span class="n">kernel_initializer</span><span class="o">=</span><span class="s1">&#39;random_normal&#39;</span><span class="p">))</span>
</pre></div>

    </div>
</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[52]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">classifier</span><span class="o">.</span><span class="n">compile</span><span class="p">(</span><span class="n">loss</span><span class="o">=</span><span class="s1">&#39;sparse_categorical_crossentropy&#39;</span><span class="p">,</span> <span class="n">optimizer</span><span class="o">=</span><span class="s1">&#39;adam&#39;</span><span class="p">,</span> <span class="n">metrics</span><span class="o">=</span><span class="p">[</span><span class="s1">&#39;accuracy&#39;</span><span class="p">])</span>
<span class="n">classifier</span><span class="o">.</span><span class="n">summary</span><span class="p">()</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Model: &#34;sequential_1&#34;
_________________________________________________________________
Layer (type)                 Output Shape              Param #   
=================================================================
dense_4 (Dense)              (None, 25)                77025     
_________________________________________________________________
dense_5 (Dense)              (None, 9)                 234       
=================================================================
Total params: 77,259
Trainable params: 77,259
Non-trainable params: 0
_________________________________________________________________
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[53]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="n">classifier</span><span class="o">.</span><span class="n">fit</span><span class="p">(</span><span class="n">trainX1</span><span class="p">,</span> <span class="n">trainY1</span><span class="p">,</span> <span class="n">epochs</span> <span class="o">=</span> <span class="mi">25</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>Train on 6832 samples
Epoch 1/25
6832/6832 [==============================] - 3s 496us/sample - loss: 1.3458 - accuracy: 0.5231
Epoch 2/25
6832/6832 [==============================] - 3s 470us/sample - loss: 0.8382 - accuracy: 0.6734
Epoch 3/25
6832/6832 [==============================] - 3s 463us/sample - loss: 0.7309 - accuracy: 0.7286
Epoch 4/25
6832/6832 [==============================] - 3s 463us/sample - loss: 0.6886 - accuracy: 0.7321
Epoch 5/25
6832/6832 [==============================] - 3s 460us/sample - loss: 0.6775 - accuracy: 0.7373
Epoch 6/25
6832/6832 [==============================] - 3s 461us/sample - loss: 0.6651 - accuracy: 0.7357
Epoch 7/25
6832/6832 [==============================] - 3s 460us/sample - loss: 0.6565 - accuracy: 0.7411
Epoch 8/25
6832/6832 [==============================] - 3s 460us/sample - loss: 0.6586 - accuracy: 0.7425
Epoch 9/25
6832/6832 [==============================] - 3s 462us/sample - loss: 0.6595 - accuracy: 0.7406
Epoch 10/25
6832/6832 [==============================] - 3s 461us/sample - loss: 0.6526 - accuracy: 0.7411
Epoch 11/25
6832/6832 [==============================] - 3s 458us/sample - loss: 0.6517 - accuracy: 0.7395
Epoch 12/25
6832/6832 [==============================] - 3s 466us/sample - loss: 0.6421 - accuracy: 0.7421
Epoch 13/25
6832/6832 [==============================] - 3s 465us/sample - loss: 0.6466 - accuracy: 0.7472
Epoch 14/25
6832/6832 [==============================] - 3s 462us/sample - loss: 0.6455 - accuracy: 0.7387
Epoch 15/25
6832/6832 [==============================] - 3s 460us/sample - loss: 0.6430 - accuracy: 0.7441
Epoch 16/25
6832/6832 [==============================] - 3s 463us/sample - loss: 0.6361 - accuracy: 0.7417
Epoch 17/25
6832/6832 [==============================] - 3s 463us/sample - loss: 0.6380 - accuracy: 0.7395
Epoch 18/25
6832/6832 [==============================] - 3s 461us/sample - loss: 0.6313 - accuracy: 0.7458
Epoch 19/25
6832/6832 [==============================] - 3s 465us/sample - loss: 0.6347 - accuracy: 0.7430
Epoch 20/25
6832/6832 [==============================] - 3s 465us/sample - loss: 0.6325 - accuracy: 0.7466
Epoch 21/25
6832/6832 [==============================] - 3s 463us/sample - loss: 0.6302 - accuracy: 0.7452
Epoch 22/25
6832/6832 [==============================] - 3s 462us/sample - loss: 0.6289 - accuracy: 0.7484
Epoch 23/25
6832/6832 [==============================] - 3s 494us/sample - loss: 0.6306 - accuracy: 0.7500
Epoch 24/25
6832/6832 [==============================] - 3s 464us/sample - loss: 0.6281 - accuracy: 0.7463
Epoch 25/25
6832/6832 [==============================] - 3s 464us/sample - loss: 0.6263 - accuracy: 0.7468
</pre>
</div>
</div>

<div class="output_area">

    <div class="prompt output_prompt">Out[53]:</div>




<div class="output_text output_subarea output_execute_result">
<pre>&lt;tensorflow.python.keras.callbacks.History at 0x2bf0dfeb8&gt;</pre>
</div>

</div>

</div>
</div>

</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[54]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span><span class="c1"># Evaluate model accuracy on test data</span>
<span class="n">predictions1</span> <span class="o">=</span> <span class="n">classifier</span><span class="o">.</span><span class="n">predict_classes</span><span class="p">(</span><span class="n">testX1</span><span class="p">)</span>
<span class="n">preds1</span> <span class="o">=</span> <span class="n">predictions1</span><span class="o">.</span><span class="n">tolist</span><span class="p">()</span>
<span class="n">preds1</span><span class="p">,</span> <span class="n">testY1</span>
<span class="kn">from</span> <span class="nn">sklearn.metrics</span> <span class="k">import</span> <span class="n">accuracy_score</span>
<span class="nb">print</span><span class="p">(</span><span class="n">accuracy_score</span><span class="p">(</span><span class="n">preds1</span><span class="p">,</span> <span class="n">testY1</span><span class="p">)</span><span class="o">*</span><span class="mi">100</span><span class="p">)</span>
</pre></div>

    </div>
</div>
</div>

<div class="output_wrapper">
<div class="output">


<div class="output_area">

    <div class="prompt"></div>


<div class="output_subarea output_stream output_stdout output_text">
<pre>75.6578947368421
</pre>
</div>
</div>

</div>
</div>

</div>
<div class="cell border-box-sizing text_cell rendered"><div class="prompt input_prompt">
</div><div class="inner_cell">
<div class="text_cell_render border-box-sizing rendered_html">
<p>Moving forward, I would like to improve the "deep" dataset model and test the model on heart and lung datasets, as well as train seperate models for heart and lung datasets.</p>

</div>
</div>
</div>
<div class="cell border-box-sizing code_cell rendered">
<div class="input">
<div class="prompt input_prompt">In&nbsp;[&nbsp;]:</div>
<div class="inner_cell">
    <div class="input_area">
<div class=" highlight hl-ipython3"><pre><span></span> 
</pre></div>

    </div>
</div>
</div>

</div>
    </div>
  </div>
</body>

 


</html>
