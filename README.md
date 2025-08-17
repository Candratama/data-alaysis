# Loan Pivot (Excel)

Workbook Excel berisi:
- Sheet Data (table "Loans") dari CSV
- Sheet Pivot: Sum(loan_amnt) & Sum(funded_amnt) by home_ownership x term
- Sheet Summary: agregat by term + chart "Loan vs Funded by Term"

## Struktur yang disarankan
```
data/
  loan_data_summary.csv    # sumber data CSV (opsional disimpan di repo)
reports/
  loan_pivot.xlsx          # workbook Excel hasil akhir
scripts/
  build_loan_pivot.py      # pembuat Excel
requirements.txt
```

## Cara membangun di macOS
1) Python 3.8+ terpasang
2) Instal dependency:
```bash
pip3 install -r requirements.txt
```
3) Jalankan generator:
```bash
python3 scripts/build_loan_pivot.py --csv data/loan_data_summary.csv --out reports/loan_pivot.xlsx
```

## Membuka workbook
- Buka `reports/loan_pivot.xlsx` di Excel (Mac)
- Data > Refresh All (untuk memuat Pivot jika Excel menundanya)

## Catatan
- Pivot: Rows = home_ownership, Columns = term, Values = Sum(loan_amnt) & Sum(funded_amnt), grand totals aktif.
- Jika urutan term tidak 36 lalu 60, buat kolom bantu numerik (36/60) di data dan gunakan saat analisis lanjutan.
- Untuk Funding Ratio agregat (Total Funded / Total Loan) disarankan gunakan Data Model/Power Pivot (Excel 365).

## Re-run dengan data lebih besar
Jika Anda menambahkan/menimpa `data/loan_data_summary.csv`, jalankan ulang perintah di atas untuk meregenerasi Excel.
