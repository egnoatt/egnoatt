# Personal Finance Operations — 2026-09-27

Status: operational record
Scope: personal administrative and financial obligations
Principle: record obligations, decisions and lifecycle state; do not store bank account numbers, IBANs, tax identifiers, or full payment receipts in GitHub.

## Status model

`OPEN -> PAYMENT_SCHEDULED -> PAID -> PAID_VERIFIED -> CLOSED`

`PAYMENT_SCHEDULED` means the payment instruction has been entered but execution has not yet been verified.
`PAID` means the payment was made/reported as paid; `PAID_VERIFIED` requires subsequent evidence of successful execution.

## FIN-ALB-2026 — Condominio Albicocca

Context: condominium ordinary 2026/2027 charges and extraordinary roof refurbishment charge for Unit 003.

| ID | Obligation | Amount | Due date | State as of 2026-09-27 |
|---|---|---:|---|---|
| FIN-ALB-01 | Extraordinary roof refurbishment — instalment 1 | EUR 6,926.99 | 2026-09-25 | PAYMENT_SCHEDULED |
| FIN-ALB-02 | Ordinary 2026/2027 — instalment 1 | EUR 144.39 | 2026-10-31 | PAYMENT_SCHEDULED |
| FIN-ALB-03 | Ordinary 2026/2027 — instalment 2 | EUR 191.15 | 2026-12-31 | PAYMENT_SCHEDULED |
| FIN-ALB-04 | Ordinary 2026/2027 — instalment 3 | EUR 191.15 | 2027-03-31 | PAYMENT_SCHEDULED |

Total condominium obligations scheduled: **EUR 7,453.68**, excluding bank fees.

Operational note: all four bank transfers were entered/scheduled on 2026-09-27. Do not mark them PAID/VERIFIED until execution is confirmed.

Administrative data-quality note: the correct personal name supplied by the owner is **SCATTOLA SABINA**. Condominium documents currently contain a different spelling; correction with the administrator is required.

## FIN-IMU-CIT-2026 — IMU Cittadella

Context: 2026 IMU for one building area in Comune di Cittadella.

- Municipality code: C743
- Tax code: 3916 (building areas)
- Reference year: 2026
- Late advance payment including ravvedimento: EUR 51.00
- Balance: EUR 49.00
- Total F24 paid: **EUR 100.00**
- Payment date: **2026-09-27**
- State: **PAID**
- Next state: PAID_VERIFIED after confirmation of successful debit/payment.

The F24 calculation used the payment date 2026-09-27. The record intentionally excludes personal tax code, bank-account data and payment credentials.

## Next operational checks

1. Verify execution of each scheduled condominium transfer at/after its execution date and move the corresponding item to `PAID_VERIFIED`.
2. Verify the successful IMU F24 debit and move FIN-IMU-CIT-2026 to `PAID_VERIFIED`.
3. Ask the condominium administrator to correct the owner name to SCATTOLA SABINA in future records.
4. Continue adding real cases before designing a larger Personal Finance / Personal Operations architecture.

## Architecture note

This operational layer is deliberately **not stored in wrip-radar**. WRIP Radar remains an observation/learning layer. Day-to-day obligations such as taxes, condominium charges, utilities, insurance, renewals and administrative deadlines belong to a Personal Operations domain. This first record is placed here as a lightweight seed; repository architecture can be reassessed after enough real cases exist.
