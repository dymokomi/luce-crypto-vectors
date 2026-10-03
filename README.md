# luce-crypto-vectors

Test data for [luce-crypto](https://github.com/dymokomi/luce-crypto): known
answers and edge cases from public, MIT- or Apache-licensed and government
sources, converted to simple line files. It is test data only, not a registry
package, and nothing here is needed at run time.

luce-crypto's tests read this checkout from `../luce-crypto-vectors` beside
luce-crypto, or from the path in `LUCE_CRYPTO_VECTORS`. luce-crypto pins the
revision it was validated with in `bootstrap/PACKAGES`, and its CI checks out
that revision.

| Path | Source | Converter (in luce-crypto) |
|---|---|---|
| `*.rsp`, `SHA256SUMS` | NIST CAVP SHA-2 byte vectors, unmodified | none (original files) |
| `argon2id.json` | Argon2 reference via argon2-cffi | `tests/argon_oracle.py --write` |
| `bearssl/` | BearSSL `test/test_crypto.c` | `tools/bearssl_vectors.py` |
| `wycheproof/` | Project Wycheproof | `tools/wycheproof.py` |
| `openssl/` | OpenSSL `test/recipes/30-test_evp_data` | `tools/openssl_vectors.py` |
| `rfc/` | RFC 8439, RFC 7748 | `tools/rfc_vectors.py` |
| `cavp/` | NIST CAVP GCM and ECDSA SigVer | `tools/cavp_vectors.py` |

Each directory's `SOURCE-SHA256SUMS` records the checksums of the source files
it was converted from. The file formats are described in each converter's
header. Provenance and licenses: [NOTICE.md](NOTICE.md).

To regenerate after changing a converter, run it from a luce-crypto checkout
(it writes into this checkout, or into `LUCE_CRYPTO_VECTORS`), commit here,
then update the pin in luce-crypto's `bootstrap/PACKAGES`.
