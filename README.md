This repository contains Indonesia administrative area reference data obtained from the Badan Pusat Statistik (BPS) REST API.

The dataset is intended for developers, data engineers, analysts, and system integrators who need a hierarchical reference of Indonesian administrative regions.

Data Source

Source:

https://sig.bps.go.id/rest-bridging/getwilayah

Reference period:

2025_2.2025

Data provider:

Badan Pusat Statistik (BPS), Republic of Indonesia
Dataset

The repository contains four CSV files.

File	Administrative Level
province.csv	Province
city.csv	Regency / City (Kabupaten / Kota)
district.csv	District (Kecamatan)
subdistrict.csv	Village / Urban Village (Desa / Kelurahan)
CSV Structure
province.csv

Contains all provinces in Indonesia.

Column	Description
kode_bps	Province code issued by BPS
nama_bps	Province name according to BPS
kode_dagri	Province code issued by Ministry of Home Affairs (Kemendagri)
nama_dagri	Province name according to Kemendagri

Example:

kode_bps	nama_bps	kode_dagri	nama_dagri
11	ACEH	11	ACEH
city.csv

Contains all regencies and cities.

Each record includes its parent province.

Column	Description
parent_kode_bps	Parent province BPS code
parent_nama_bps	Parent province name
parent_kode_dagri	Parent province Kemendagri code
parent_nama_dagri	Parent province name according to Kemendagri
kode_bps	Regency/City BPS code
nama_bps	Regency/City name according to BPS
kode_dagri	Regency/City Kemendagri code
nama_dagri	Regency/City name according to Kemendagri
district.csv

Contains all districts (Kecamatan).

Each record includes its parent regency/city.

Column	Description
parent_kode_bps	Parent Regency/City BPS code
parent_nama_bps	Parent Regency/City name
parent_kode_dagri	Parent Regency/City Kemendagri code
parent_nama_dagri	Parent Regency/City name according to Kemendagri
kode_bps	District BPS code
nama_bps	District name according to BPS
kode_dagri	District Kemendagri code
nama_dagri	District name according to Kemendagri
subdistrict.csv

Contains all villages (Desa/Kelurahan).

Each record includes its parent district.

Column	Description
parent_kode_bps	Parent District BPS code
parent_nama_bps	Parent District name
parent_kode_dagri	Parent District Kemendagri code
parent_nama_dagri	Parent District name according to Kemendagri
kode_bps	Village BPS code
nama_bps	Village name according to BPS
kode_dagri	Village Kemendagri code
nama_dagri	Village name according to Kemendagri
Hierarchical Relationship
Province
└── Regency / City
    └── District
        └── Village (Desa / Kelurahan)

The parent columns are included to make the relationship explicit, allowing users to identify the parent administrative area without performing additional joins.

Character Encoding

All CSV files are encoded using UTF-8 with BOM (utf-8-sig) for compatibility with:

Microsoft Excel
LibreOffice Calc
Google Sheets
PostgreSQL
MySQL
SQL Server
Most modern programming languages
Intended Use

This dataset can be used for:

Master/reference data
ERP systems
Government information systems
Geographic Information Systems (GIS)
Customer address normalization
ETL pipelines
Data warehousing
Analytics and reporting
Form dropdowns for Indonesian administrative areas
Disclaimer

This repository redistributes administrative reference data retrieved from the public BPS API. The original data remains the property of Badan Pusat Statistik (BPS).

Users should refer to the official BPS website for the latest updates and authoritative information.

License

This repository does not claim ownership of the administrative data.

Please comply with the terms and conditions of the original data provider (BPS) when using or redistributing this dataset.
