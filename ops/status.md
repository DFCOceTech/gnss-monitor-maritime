# Operational Status

**Updated**: 2026-05-09

## What's Working

- Dashboard live at http://192.168.178.84:5000 — all panels populated, E2E verified (2026-05-09)
- 3D fix, 21–22 SVs at current anchor location
- **Vessel State card**: speed (kn) + course (°) displaying — confirmed 0.0 kn / 0.0° at rest ✓
- **Position Track chart**: rendering, 40+ points populated from in-memory ring buffer ✓
- Velocity fields in DB: speed_mps, course_deg, vel_n_mps, vel_e_mps, vel_d_mps writing correctly ✓
- RF bands, SEC-SIG, OSNMA panels all present (inherited from static version)
- Dead-reckoning position-jump detection armed (will fire when speed ≥ 0.5 m/s)
- Velocity-gated baseline: only updates at anchor (speed < 0.5 m/s) ✓
- SQLite writing — 7 tables including new velocity columns in gnss_samples

## What's Next / Underway Verification

1. **Verify velocity scaling** — confirm `speed_kn` tracks actual speed underway (gSpeed assumed mm/s → m/s → kn; verify against ship's log)
2. **Verify headMot** — confirm `course_deg` tracks actual heading at speed > 0.5 m/s
3. **Tune DR threshold** — 100 m default may need adjustment based on observed GPS wander at sea
4. **Let baseline establish** — run at anchor for ≥ 4 h before getting underway for valid baseline calibration
5. **Firmware update** — OSNMA requires firmware update (KI-007)
6. **Test position-jump detection** — verify it triggers (and resolves) on a known GNSS outage/recovery

## Known Issues

See `ops/known-issues.md` (inherited from gnss-monitor static)

## Known Issues

See `ops/known-issues.md`
