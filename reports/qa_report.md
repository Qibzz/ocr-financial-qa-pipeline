
# OCR Parsing QA Report

## Ringkasan
- Total dokumen direview: 20
- Akurasi field 'vendor': 20.0%
- Akurasi field 'date': 35.0%
- Akurasi field 'total': 5.0%

## Pola Error Paling Umum
error_type
wrong_field_source + missed_field                     6
garbled_text                                          3
wrong_field_source (vendor) + missed_field (total)    2
partial_read (vendor) + missed_field (total)          2
correct                                               2
correct (total)                                       1
wrong_field_source                                    1
missed_field                                          1
partial_read (vendor) + missed_field (date, total)    1
garbled_text (vendor) + missed_field (date)           1

## Rekomendasi Perbaikan
- (isi manual berdasarkan temuan: misal "regex total gagal baca kalau ada simbol mata uang custom")
