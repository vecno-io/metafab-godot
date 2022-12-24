# Godot API client for MetaFab

An add-on for the Godot engine that wraps the MetaFab API into simple HTTPRequest nodes while providing a static interface with callbacks that behave like one-off signals.

## Overview

* Godot Engine: 3.5.1 (4.x)
* MetaFab API version: 1.3.0

## Usage Guide

The UI Example is set up so that you can follow along with the official getting started guide. (see links below)

In short, you register your development account on Metafab to get your API credentials and then follow along to create players, currencies, items, shops, and so on.

To get the addon into your Godot project just drop the 'addons/metafab-api' folder into the root folder of your project. And then reload the project so that it sets up the global variable needed to start using the API in other scripts.

Basic usage example that gets all registered players (admin only)
```GDScript
func _on_action_request():
  var res = MetaFab.get_players(self, "_on_action_request_result", secret_key_string)
  # Error can happen if servers are down or the device is not connected
  if res != MetaFabRequest.Ok: print("[%s] Error: %s" % [name, res])

func _on_action_request_result(code: int, result: String):
  var json = JSON.parse(result)
  # Anything but 200 means something went wrong on the server
  if code == 200: print("[%s] Result: %s" % [name, json.result])
  else: print("[%s] Code: %s / Error: %s" % [name, code, json.result])
```

If you have questions or find bugs drop us a line on discord or open an issue here.

---

A demo project can be found at: [github.com/vecno-io/metafab-godot-ui](https://github.com/vecno-io/metafab-godot-ui)

The complete MetaFab API references and guides can be found at: [trymetafab.com](https://trymetafab.com)
