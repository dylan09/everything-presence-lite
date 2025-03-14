---
layout: default
title: Updating and Connecting to WiFi
nav_order: 4
---

# Updating and Connecting To WiFi

{: .no_toc }

This page will help you to flash and update your Everything Presence Lite to the latest version and get it connected to WiFi!
{: .fs-6 .fw-300 }

## Everything Presence Lite ESPHome Firmware Install

Here you can install the latest [ESPHome](https://esphome.io) firmware on the Everything Presence Lite board for direct integration with [Home Assistant](https://home-assistant.io)

First, make sure you have the Lite connected to a USB port on your computer and select the platform you would like to install below. Hit the connect button, select the USB port from the list and then hit the install button to begin installing the latest software on your Everything Presence Lite.

Once the install has completed, you can then connect the Lite to your WiFi easily and securely.

{: .warning-title }
If you do not see a "Connect" button below, use a supported web browser like Google Chrome.

{: .warning-title }
After clicking the "Connect" button, if you do not see a "USB Serial" port listed, or you get the error "Failed to open serial port.", you may need to install the CH340 driver. The installer should give you links to the latest driver.

<div class="radios">
  <label>
    <input type="radio" name="type" value="everything-presence-lite-ha" checked/>
    <img src="images/everything-presence-one-ha-ble.png" alt="Everything Presence Lite Home Assistant" width="200" height="250"/>
  </label>
  <label class="beta">
    <input type="radio" name="type" value="everything-presence-lite-ha-no-ble" />
    <img src="images/everything-presence-one-ha.png" alt="Everything Presence Lite Home Assistant No BLE" width="200" height="250"/>
  </label>
</div>

<p class="button-row" align="left">
  <esp-web-install-button></esp-web-install-button>
</p>

<div class="hidden info everything-presence-lite-ha">
  <h3>Home Assistant</h3>
    <p>
      Installs the standard firmware on your Everything Presence Lite for <a href="https://home-assistant.io">Home Assistant</a>, with Bluetooth Proxy enabled. Once installed and connected to WiFi, follow the Home Assistant section to connect the Lite to your Home Assistant server.
    </p>
</div>

<div class="hidden info everything-presence-lite-ha-no-ble">
  <h3>Home Assistant (No Bluetooth Proxy)</h3>
    <p>
      Installs the standard firmware on your Everything Presence Lite for <a href="https://home-assistant.io">Home Assistant</a> but with Bluetooh Proxy disabled which can help with performance or intermittent connectivity issues. Once installed and connected to WiFi, follow the Home Assistant section to connect the Lite to your Home Assistant server.
    </p>
</div>

## Next Steps

With the Lite fully updated and connected to WiFi, the final step is to connect it to Home Assistant.

[Connecting to Home Assistant](./Home%20Assistant/connecting-home-assistant.html){: .btn .btn-blue } 


<script
  type="module"
  src="https://unpkg.com/esp-web-tools@9.0.3/dist/web/install-button.js?module"
></script>

<script>
const toggleDarkMode = document.querySelector('.js-toggle-dark-mode');

jtd.addEvent(toggleDarkMode, 'click', function(){
  if (jtd.getTheme() === 'dark') {
    jtd.setTheme('light');
    toggleDarkMode.textContent = 'Preview dark color scheme';
  } else {
    jtd.setTheme('dark');
    toggleDarkMode.textContent = 'Return to the light side';
  }
});
</script>

<script>
  document.querySelectorAll('input[name="type"]').forEach((radio) =>
    radio.addEventListener("change", () => {
      const button = document.querySelector("esp-web-install-button");
      button.manifest = `./${radio.value}-manifest.json`;

      document.querySelectorAll(".info").forEach((info) => {
        info.classList.add("hidden");
      });
      document
        .querySelector(`.info.${radio.value}`)
        .classList.remove("hidden");
    })
  );
  document
    .querySelector('input[name="type"]:checked')
    .dispatchEvent(new Event("change"));
  if (new URLSearchParams(document.location.search).has("beta")) {
    document.body.classList.add("show-beta");
  }
</script>
