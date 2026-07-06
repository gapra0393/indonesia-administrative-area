# Indonesia Administrative Areas (BPS) 2025

This repository contains Indonesia administrative area reference data sourced from **Badan Pusat Statistik (BPS)** through the SIG BPS REST API.

The dataset includes all administrative levels from **Province** to **Village/Subdistrict (Desa/Kelurahan)** and is exported into CSV format.

> **Data Source**
>
> https://sig.bps.go.id/rest-bridging/getwilayah

---

# Dataset Version

- **Source**: Badan Pusat Statistik (BPS)
- **Period**: `2025_2.2025`
- **Export Format**: CSV

---

# Files

| File | Description |
|------|-------------|
| `province.csv` | List of all provinces |
| `city.csv` | List of all regencies/cities (Kabupaten/Kota) |
| `district.csv` | List of all districts (Kecamatan) |
| `subdistrict.csv` | List of all villages/subdistricts (Desa/Kelurahan) |

---

# File Structure

## province.csv

Contains province-level administrative areas.

### Columns

| Column | Description |
|---------|-------------|
| `kode_bps` | Province code from BPS |
| `nama_bps` | Province name from BPS |
| `kode_dagri` | Province code from Kemendagri |
| `nama_dagri` | Province name from Kemendagri |

Example

| kode_bps | nama_bps | kode_dagri | nama_dagri |
|----------|-----------|------------|------------|
|11|ACEH|11|ACEH|

---

## city.csv

Contains all city/region.

Each record stores its province information.

### Columns

| Column | Description |
|---------|-------------|
| `prov_kode_bps` | Province BPS code |
| `prov_nama_bps` | Province BPS name |
| `prov_kode_dagri` | Province Kemendagri code |
| `prov_nama_dagri` | Province Kemendagri name |
| `kode_bps` | City/Region BPS code |
| `nama_bps` | City/Region BPS name |
| `kode_dagri` | City/Region Kemendagri code |
| `nama_dagri` | City/Region Kemendagri name |

Example

| prov_kode_bps | prov_nama_bps | prov_kode_dagri | prov_nama_dagri | kode_bps | nama_bps | kode_dagri | nama_dagri |
|-----------------|-----------------|-------------------|-------------------|-----------|-----------|-------------|-------------|
|11|ACEH|11|ACEH|1101|SIMEULUE|11.09|KABUPATEN SIMEULUE|

---

## district.csv

Contains all districts.

Each record stores its city/region information.

### Columns

| Column | Description |
|---------|-------------|
| `city_kode_bps` | City/Region BPS code |
| `city_nama_bps` | City/Region BPS name |
| `city_kode_dagri` | City/Region Kemendagri code |
| `city_nama_dagri` | City/Region Kemendagri name |
| `kode_bps` | District BPS code |
| `nama_bps` | District BPS name |
| `kode_dagri` | District Kemendagri code |
| `nama_dagri` | District Kemendagri name |

Example

| city_kode_bps | city_nama_bps | city_kode_dagri | city_nama_dagri | kode_bps | nama_bps | kode_dagri | nama_dagri |
|-----------------|-----------------|-------------------|-------------------|-----------|-----------|-------------|-------------|
|1101|SIMEULUE|11.09|KABUPATEN SIMEULUE|1101010|TEUPAH SELATAN|11.09.07|TEUPAH SELATAN|

---

## subdistrict.csv

Contains all subdistrict/village.

Each record stores its district information.

### Columns

| Column | Description |
|---------|-------------|
| `dist_kode_bps` | District BPS code |
| `dist_nama_bps` | District BPS name |
| `dist_kode_dagri` | District Kemendagri code |
| `dist_nama_dagri` | District Kemendagri name |
| `kode_bps` | Subdistrict/Village BPS code |
| `nama_bps` | Subdistrict/Village BPS name |
| `kode_dagri` | Subdistrict/Village Kemendagri code |
| `nama_dagri` | Subdistrict/Village Kemendagri name |

Example

| dist_kode_bps | dist_nama_bps | dist_kode_dagri | dist_nama_dagri | kode_bps | nama_bps | kode_dagri | nama_dagri |
|-----------------|-----------------|-------------------|-------------------|-----------|-----------|-------------|-------------|
|3174010|KEBON JERUK|31.73.08|KEBON JERUK|3174010001|JOGLO|31.73.08.1005|JOGLO|

---

# Parent-Child Relationship

The datasets are linked through the parent columns.

```
Province
    └── City/Regency
            └── District
                    └── Subdistrict/Village
```

Example:

```
Province
└── ACEH (11)
    └── SIMEULUE (1101)
        └── TEUPAH SELATAN (1101010)
            └── LATIUNG (1101010001)
```

This allows users to determine the hierarchy without performing additional joins.

---

# Data Source

The data is retrieved from the official BPS API.

```
GET https://sig.bps.go.id/rest-bridging/getwilayah
```

Parameters

| Parameter | Description |
|-----------|-------------|
| `level` | Administrative level (`provinsi`, `kabupaten`, `kecamatan`, `desa`) |
| `parent` | Parent BPS code |
| `periode_merge` | Data version |

Example

```
https://sig.bps.go.id/rest-bridging/getwilayah?level=provinsi&parent=0&periode_merge=2025_2.2025
```

---

# License

This repository republishes publicly accessible administrative reference data obtained from the official BPS API.

Users should refer to the official BPS website for the latest updates and any applicable terms of use.

---

# Disclaimer

This repository is **not affiliated with or maintained by Badan Pusat Statistik (BPS)**.

The data is provided for educational, development, and research purposes. While every effort has been made to preserve the original data accurately, users should verify critical information against the official BPS source before using it in production systems.
