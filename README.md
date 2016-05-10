# Authenticon prototype Web client #

*Authenticon* is a project proposed by [Martus](http://www.martus.org). Briefly, Martus is used by people in hostile environments to transmit evidence of human rights abuses. Their transmissions are encrypted. To detect interception, a 40-digit fingerprint is provided that can be verified out of band (eg, by phone call). Because it is difficult to check a 40-digit number over a phone the fingerprint is rarely checked. The project proposes to provide a more visual view of the fingerprint that is easier to work with.

This repository contains a simple Web client to test the prototype API initially developed at the [CHI 2016](http://chi2016.acm.org) day of service. A brief video run-through is [here](https://youtu.be/5LxcUCHlwkI).

* How to install the client
* How to use it
* How it works
* Considerations for further development

## How to install the client ##

Clone the repository into a Web server. It may not work when opened as *file://*. It will happily co-exist with the [prototype API](https://bitbucket.org/lorenzowood/authenticon-api/overview).

## How to use it ##

See the [run-through](https://youtu.be/5LxcUCHlwkI).

## How it works ##

It is a one-page site that uses [bootstrap.js](http://getbootstrap.com/) for responsive layout with virtually no customisation. Along with [jQuery](http://jquery.com) it uses [the jQuery Validation plug-in](https://jqueryvalidation.org/) to provide automatic validation of the entry field for fingerprints. Bootstrap is copied into the project; jQuery and jQuery Validation are loaded from a CDN.

The URL for the API is hard-wired near the top of the file. The current section is:
```
  <script>
      var apiRoot = 'http://52.48.1.222/api/visualise-fingerprint.php';
  </script>
```

When it loads (using jQuery’s *ready()* call) it calls the API end point to retrieve an array of encoding methods. It uses these to populate the drop-down in the nav bar that allows the user to change methods.

The main page either shows a form to enter a fingerprint (validated for exactly 40 digits) or shows the result of encoding. The type of the encoding method (*image* or *text*) is used to determine how to render the result of calling the API. For text, *<pre>* is used to allow line breaks to work. The only styling override in the file is to boost the size of *<pre>* text.

## Considerations for further development ##

This is meant to be a mechanism to test the API only. Presumably the idea is to build the approach into other software using the APi.