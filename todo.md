1. Download full dataset langsung dari broker MT5 yang akan dipakai live.

2. Gunakan hanya 1 source data:

   * jangan campur HistData
   * jangan campur Kaggle
   * jangan campur broker lain.

3. Buat master dataset final:

   ```text
   EURUSD_MT5_MASTER_M15.csv
   ```

4. Audit dataset:

   * missing candle
   * duplicate candle
   * DST/session mismatch
   * spread distribution
   * abnormal spike
   * holiday gap.

5. Freeze timezone dan session handling.

6. Freeze feature engineering pipeline:

   * jangan rewrite ulang
   * jangan beda notebook
   * jangan beda logic.

7. Tambahkan spread-aware feature:

   * spread_pips
   * spread_regime
   * spread filter.

8. Tambahkan volatility regime feature:

   * ATR regime
   * volatility percentile.

9. Audit target generation:

   * no leakage
   * no future bias
   * no overlap issue.

10. Pastikan execution logic realistis:

    * next candle open entry
    * spread included
    * no hindsight TP/SL
    * no overlap trade.

11. Retrain model menggunakan MT5 dataset saja.

12. Lakukan walk-forward validation:

    * train → future test
    * bukan random split.

13. Jalankan Monte Carlo ulang menggunakan dataset MT5 baru.

14. Cari threshold baru:

    * 0.54 mungkin sudah tidak optimal.

15. Bangun 1 validation engine final:

    * research
    * replay
    * forward test
    * live
      semua harus memakai engine yang sama.

16. Replay hanya sebagai playback visualization:

    * jangan hitung ulang signal.

17. Jalankan replay forward simulation candle-by-candle.

18. Jalankan paper trading minimal 1–2 bulan.

19. Buat logging system:

    * signal
    * y_prob
    * spread
    * ATR
    * entry
    * exit
    * outcome.

20. Evaluasi:

    * PF
    * expectancy
    * drawdown
    * stability per regime.

21. Setelah stabil baru deploy VPS/live.

22. Tambahkan live safety system:

    * spread spike filter
    * reconnect handling
    * duplicate order prevention
    * max DD protection.

23. Jangan tweak replay engine lagi sebelum retrain selesai.

24. Fokus utama sekarang:

    ```text
    feed consistency
    ```

    karena ini akar masalah terbesar yang sudah ditemukan.
