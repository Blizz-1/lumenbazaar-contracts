# Policy Wallet Examples

These examples are mirrored by executable tests in `src/test.rs`.

Spending policy validity boundaries are inclusive: a policy is active for ledger sequences satisfying `valid_from_ledger <= ledger_sequence <= valid_until_ledger`.

| Scenario | Test name | Expected result |
| --- | --- | --- |
| Allowed payment | `documentation_allowed_payment_example_authorizes` | The agent-authorized payment succeeds and increments daily spend. |
| Blocked payment | `documentation_blocked_payment_example_reports_amount_cap` | A payment over the per-payment cap returns `AmountExceedsPaymentCap`. |
| Pre-activation policy | `documentation_pre_activation_policy_example_reports_not_active` | A payment checked before `valid_from_ledger` returns `PolicyNotActive` and leaves spend unchanged. |
| Expired policy | `documentation_expired_policy_example_reports_expired` | A payment checked after `valid_until_ledger` returns `PolicyExpired`. |
| Wrong seller | `documentation_wrong_seller_example_reports_seller_error` | A seller outside the allowlist returns `SellerNotAllowed`. |
| Wrong asset | `documentation_wrong_asset_example_reports_asset_error` | An asset outside the allowlist returns `AssetNotAllowed`. |
