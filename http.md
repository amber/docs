# HTTP



## Assets

### GetAsset

* __Method__: GET
* __URL__: /api/assets/`hash`/
* __Parameters__: `hash` — a SHA-256 hash
* __Returns__: the contents of the asset with the given hash

### AddAsset

* __Method__: POST
* __URL__: /api/assets/
* __Request Body__: the asset
* __Returns__: the hash of the given asset
