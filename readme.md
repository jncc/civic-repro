
Civic cookie control bug reproduction
=====================================

Reproduces either (i) incomprehensible behavour or (ii) a critical bug in the Civic cookie control.

    npm install
    npm run dev

[If you don't use Node, just open `index.html` in some other local web server.]

- Open `http://127.0.0.1:8080/`
- Open the browser developer tools to see the console.
- The cookie control dialogue appears. Note that 'Analytical cookies' are 'OFF'.
- Click 'I accept'.
- `Analytics accepted!` is written to the console.

I do not expect to see this, because I have not accepted analytics. The "accepted" callback should not have been invoked.

The code is copied from the example code at https://www.civicuk.com/cookie-control/documentation. Additional cookie groups have been removed and a `console.log` line in each of the two callbacks instead of the Google Analytics initialisation and removal.

Additionally, the callbacks appear to be invoked every time a checkbox button is toggled. This breaks any normal UI convention and any reasonableness test for granting consent. I haven't consented to receive cookies until I click on the big 'I accept' button. I do not expect that toggling a checkbox would cause *any* immediate action to happen, let alone when there is a large form submission button unambiguously presented for that purpose.

Note I used the CDN code distribution as in the example, so this reproduction is not deterministic.
