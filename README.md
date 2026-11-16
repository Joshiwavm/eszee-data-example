# eszee-data-example

Example data for the [eszee](https://github.com/lucadimascolo/eszee)
documentation: ALMA Band 1 observations of the galaxy cluster
ACT-CL J0459-4947 (SPT-CL J0459-4947, RA 74.927, Dec −49.787) from
[van Marrewijk et al. 2025, arXiv:2611.00132](https://arxiv.org/abs/2611.00132).
They serve the ALMA-only and the ALMA + ACT + Planck tutorials.

## Layout

```
data/
  output_band1_com12m.im.field-0.spw-{0,1,2,3}.data.npz    visibilities of one spectral window (12-m array, field 0)
  output_band1_com12m.im.field-0.spw-{0,1,2,3}.image.fits  dirty image of that window (Jy/beam, 1024 x 1024, 0.3")
  output_band1_com12m.im.field-0.spw-{0,1,2,3}.pbeam.fits  primary beam on the same grid
  output_band1_com12m.im.field-0.spw-{0,1,2,3}.psf.fits    dirty beam on the same grid
```

Each `.data.npz` holds one array of shape (6, nvis) in the format eszee's
`ALMA.add_visibilities` reads. The four spectral windows span ALMA
Band 1 (around 35–50 GHz).

## Use

```python
from eszee.data import ALMA

alma = ALMA()
for spw in range(4):
    alma.add_visibilities(f"data/output_band1_com12m.im.field-0.spw-{spw}.data.npz")
```
