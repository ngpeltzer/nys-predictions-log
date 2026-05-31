# Registro público de predicciones · Nuestra Señal

Log **append-only** y **auditable** de las predicciones del Oráculo de [nys.com.ar](https://nys.com.ar).

Cada predicción del Oráculo se registra acá con el **hash SHA-256** de su contenido canónico, en el momento en que se publica — *antes* de saber el resultado. Esto prueba que la predicción existió en esa fecha y **no se editó después**.

## Formato

`predictions.log` — una línea por predicción, separada por tabs:

```
fecha    hash_sha256    ticker
```

## Cómo verificar una predicción

1. En el detalle de la predicción en nys.com.ar vas a ver el **JSON canónico exacto** y su hash.
2. Calculá el SHA-256 de ese JSON canónico (bytes UTF-8). Debe coincidir con el `hash_sha256` de este log:
   ```
   printf '%s' '<json canónico>' | sha256sum
   ```
3. Cada hash está además **anclado a la blockchain de Bitcoin** vía [OpenTimestamps](https://opentimestamps.org) — prueba criptográfica de que existía en esa fecha, sin tener que confiar en nosotros ni en GitHub.

**No nos creas: verificá.**

---
*Mantenido automáticamente por el pipeline de Nuestra Señal. Este repo es solo el registro público; el sitio es [nys.com.ar](https://nys.com.ar).*
