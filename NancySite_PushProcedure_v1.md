# NancySite — Staging → Production Push Procedure
**Last updated:** 2026-05-07  
**Proven by:** Practice push, Session 5  
**Live site:** https://nancy.boycan.com/  
**Staging site:** https://nancy.boycan.com/nancy-site-stagi/  
**Database:** canate5_wp644 (cPanel → phpMyAdmin)  
**Live table prefix:** `wp9f_`  
**Staging table prefix:** `wpstg0_`

---

## Pre-Push Checklist
- [ ] All build work for this session is complete on staging
- [ ] Staging site visually verified in browser
- [ ] cPanel session is active (re-login at canateo.com:2083 if needed)
- [ ] phpMyAdmin is open on canate5_wp644

---

## Step 1 — Export Full Database Backup
In phpMyAdmin → select `canate5_wp644` → Export tab  
- Method: Quick  
- Format: SQL  
- Click **Export** → save file locally as `canate5_wp644_YYYY-MM-DD.sql`

✅ Do not proceed without a confirmed backup download.

---

## Step 2 — Rename Live Tables to Backup
Open phpMyAdmin SQL editor and run each statement individually.  
> ⚠️ MariaDB does not support DDL in PREPARE/EXECUTE.  
> ⚠️ Use individual statements — a batch fails entirely if any one table is missing.

```sql
RENAME TABLE wp9f_aiowps_events TO wp9f_aiowps_events_bak;
RENAME TABLE wp9f_aiowps_failed_logins TO wp9f_aiowps_failed_logins_bak;
RENAME TABLE wp9f_aiowps_login_activity TO wp9f_aiowps_login_activity_bak;
RENAME TABLE wp9f_aiowps_login_lockout TO wp9f_aiowps_login_lockout_bak;
RENAME TABLE wp9f_aiowps_perm_block TO wp9f_aiowps_perm_block_bak;
RENAME TABLE wp9f_commentmeta TO wp9f_commentmeta_bak;
RENAME TABLE wp9f_comments TO wp9f_comments_bak;
RENAME TABLE wp9f_links TO wp9f_links_bak;
RENAME TABLE wp9f_mailpoet_custom_fields TO wp9f_mailpoet_custom_fields_bak;
RENAME TABLE wp9f_mailpoet_dynamic_segment_filters TO wp9f_mailpoet_dynamic_segment_filters_bak;
RENAME TABLE wp9f_mailpoet_feature_flags TO wp9f_mailpoet_feature_flags_bak;
RENAME TABLE wp9f_mailpoet_forms TO wp9f_mailpoet_forms_bak;
RENAME TABLE wp9f_mailpoet_log TO wp9f_mailpoet_log_bak;
RENAME TABLE wp9f_mailpoet_newsletters TO wp9f_mailpoet_newsletters_bak;
RENAME TABLE wp9f_mailpoet_newsletter_links TO wp9f_mailpoet_newsletter_links_bak;
RENAME TABLE wp9f_mailpoet_newsletter_option TO wp9f_mailpoet_newsletter_option_bak;
RENAME TABLE wp9f_mailpoet_newsletter_option_fields TO wp9f_mailpoet_newsletter_option_fields_bak;
RENAME TABLE wp9f_mailpoet_newsletter_posts TO wp9f_mailpoet_newsletter_posts_bak;
RENAME TABLE wp9f_mailpoet_newsletter_segment_statistics TO wp9f_mailpoet_newsletter_segment_statistics_bak;
RENAME TABLE wp9f_mailpoet_newsletter_statistics TO wp9f_mailpoet_newsletter_statistics_bak;
RENAME TABLE wp9f_mailpoet_scheduled_tasks TO wp9f_mailpoet_scheduled_tasks_bak;
RENAME TABLE wp9f_mailpoet_scheduled_task_subscribers TO wp9f_mailpoet_scheduled_task_subscribers_bak;
RENAME TABLE wp9f_mailpoet_segments TO wp9f_mailpoet_segments_bak;
RENAME TABLE wp9f_mailpoet_sending_queues TO wp9f_mailpoet_sending_queues_bak;
RENAME TABLE wp9f_mailpoet_statistics_bounces TO wp9f_mailpoet_statistics_bounces_bak;
RENAME TABLE wp9f_mailpoet_statistics_clicks TO wp9f_mailpoet_statistics_clicks_bak;
RENAME TABLE wp9f_mailpoet_statistics_forms TO wp9f_mailpoet_statistics_forms_bak;
RENAME TABLE wp9f_mailpoet_statistics_opens TO wp9f_mailpoet_statistics_opens_bak;
RENAME TABLE wp9f_mailpoet_statistics_unsubscribes TO wp9f_mailpoet_statistics_unsubscribes_bak;
RENAME TABLE wp9f_mailpoet_statistics_woocommerce_purchases TO wp9f_mailpoet_statistics_woocommerce_purchases_bak;
RENAME TABLE wp9f_mailpoet_subscriber_ips TO wp9f_mailpoet_subscriber_ips_bak;
RENAME TABLE wp9f_mailpoet_subscriber_segment TO wp9f_mailpoet_subscriber_segment_bak;
RENAME TABLE wp9f_mailpoet_subscribers TO wp9f_mailpoet_subscribers_bak;
RENAME TABLE wp9f_mailpoet_subscriber_tag TO wp9f_mailpoet_subscriber_tag_bak;
RENAME TABLE wp9f_mailpoet_tags TO wp9f_mailpoet_tags_bak;
RENAME TABLE wp9f_mailpoet_user_flags TO wp9f_mailpoet_user_flags_bak;
RENAME TABLE wp9f_mailpoet_webhooks TO wp9f_mailpoet_webhooks_bak;
RENAME TABLE wp9f_ms_snippets TO wp9f_ms_snippets_bak;
RENAME TABLE wp9f_options TO wp9f_options_bak;
RENAME TABLE wp9f_postmeta TO wp9f_postmeta_bak;
RENAME TABLE wp9f_posts TO wp9f_posts_bak;
RENAME TABLE wp9f_signups TO wp9f_signups_bak;
RENAME TABLE wp9f_snippets TO wp9f_snippets_bak;
RENAME TABLE wp9f_termmeta TO wp9f_termmeta_bak;
RENAME TABLE wp9f_terms TO wp9f_terms_bak;
RENAME TABLE wp9f_term_relationships TO wp9f_term_relationships_bak;
RENAME TABLE wp9f_term_taxonomy TO wp9f_term_taxonomy_bak;
RENAME TABLE wp9f_usermeta TO wp9f_usermeta_bak;
RENAME TABLE wp9f_users TO wp9f_users_bak;
RENAME TABLE wp9f_wpforms_entries TO wp9f_wpforms_entries_bak;
RENAME TABLE wp9f_wpforms_entry_fields TO wp9f_wpforms_entry_fields_bak;
RENAME TABLE wp9f_wpforms_entry_meta TO wp9f_wpforms_entry_meta_bak;
RENAME TABLE wp9f_wpforms_logs TO wp9f_wpforms_logs_bak;
RENAME TABLE wp9f_wpforms_payments TO wp9f_wpforms_payments_bak;
RENAME TABLE wp9f_wpforms_payment_meta TO wp9f_wpforms_payment_meta_bak;
RENAME TABLE wp9f_wpmailsmtp_debug_events TO wp9f_wpmailsmtp_debug_events_bak;
RENAME TABLE wp9f_wpmailsmtp_tasks_meta TO wp9f_wpmailsmtp_tasks_meta_bak;
```

> **Known missing tables** (will throw an error — safe to ignore, they don't exist in live):  
> - `wp9f_mailpoet_newsletter_segment_statistics` ← skip if error  
> - `wp9f_mailpoet_newsletter_statistics` ← skip if error

---

## Step 3 — Rename Staging Tables to Live
```sql
RENAME TABLE wpstg0_aiowps_events TO wp9f_aiowps_events;
RENAME TABLE wpstg0_aiowps_failed_logins TO wp9f_aiowps_failed_logins;
RENAME TABLE wpstg0_aiowps_login_activity TO wp9f_aiowps_login_activity;
RENAME TABLE wpstg0_aiowps_login_lockout TO wp9f_aiowps_login_lockout;
RENAME TABLE wpstg0_aiowps_perm_block TO wp9f_aiowps_perm_block;
RENAME TABLE wpstg0_commentmeta TO wp9f_commentmeta;
RENAME TABLE wpstg0_comments TO wp9f_comments;
RENAME TABLE wpstg0_links TO wp9f_links;
RENAME TABLE wpstg0_mailpoet_custom_fields TO wp9f_mailpoet_custom_fields;
RENAME TABLE wpstg0_mailpoet_dynamic_segment_filters TO wp9f_mailpoet_dynamic_segment_filters;
RENAME TABLE wpstg0_mailpoet_feature_flags TO wp9f_mailpoet_feature_flags;
RENAME TABLE wpstg0_mailpoet_forms TO wp9f_mailpoet_forms;
RENAME TABLE wpstg0_mailpoet_log TO wp9f_mailpoet_log;
RENAME TABLE wpstg0_mailpoet_newsletters TO wp9f_mailpoet_newsletters;
RENAME TABLE wpstg0_mailpoet_newsletter_links TO wp9f_mailpoet_newsletter_links;
RENAME TABLE wpstg0_mailpoet_newsletter_option TO wp9f_mailpoet_newsletter_option;
RENAME TABLE wpstg0_mailpoet_newsletter_option_fields TO wp9f_mailpoet_newsletter_option_fields;
RENAME TABLE wpstg0_mailpoet_newsletter_posts TO wp9f_mailpoet_newsletter_posts;
RENAME TABLE wpstg0_mailpoet_scheduled_tasks TO wp9f_mailpoet_scheduled_tasks;
RENAME TABLE wpstg0_mailpoet_scheduled_task_subscribers TO wp9f_mailpoet_scheduled_task_subscribers;
RENAME TABLE wpstg0_mailpoet_segments TO wp9f_mailpoet_segments;
RENAME TABLE wpstg0_mailpoet_sending_queues TO wp9f_mailpoet_sending_queues;
RENAME TABLE wpstg0_mailpoet_statistics_bounces TO wp9f_mailpoet_statistics_bounces;
RENAME TABLE wpstg0_mailpoet_statistics_clicks TO wp9f_mailpoet_statistics_clicks;
RENAME TABLE wpstg0_mailpoet_statistics_forms TO wp9f_mailpoet_statistics_forms;
RENAME TABLE wpstg0_mailpoet_statistics_opens TO wp9f_mailpoet_statistics_opens;
RENAME TABLE wpstg0_mailpoet_statistics_unsubscribes TO wp9f_mailpoet_statistics_unsubscribes;
RENAME TABLE wpstg0_mailpoet_statistics_woocommerce_purchases TO wp9f_mailpoet_statistics_woocommerce_purchases;
RENAME TABLE wpstg0_mailpoet_subscriber_ips TO wp9f_mailpoet_subscriber_ips;
RENAME TABLE wpstg0_mailpoet_subscriber_segment TO wp9f_mailpoet_subscriber_segment;
RENAME TABLE wpstg0_mailpoet_subscribers TO wp9f_mailpoet_subscribers;
RENAME TABLE wpstg0_mailpoet_subscriber_tag TO wp9f_mailpoet_subscriber_tag;
RENAME TABLE wpstg0_mailpoet_tags TO wp9f_mailpoet_tags;
RENAME TABLE wpstg0_mailpoet_user_flags TO wp9f_mailpoet_user_flags;
RENAME TABLE wpstg0_mailpoet_webhooks TO wp9f_mailpoet_webhooks;
RENAME TABLE wpstg0_ms_snippets TO wp9f_ms_snippets;
RENAME TABLE wpstg0_options TO wp9f_options;
RENAME TABLE wpstg0_postmeta TO wp9f_postmeta;
RENAME TABLE wpstg0_posts TO wp9f_posts;
RENAME TABLE wpstg0_signups TO wp9f_signups;
RENAME TABLE wpstg0_snippets TO wp9f_snippets;
RENAME TABLE wpstg0_termmeta TO wp9f_termmeta;
RENAME TABLE wpstg0_terms TO wp9f_terms;
RENAME TABLE wpstg0_term_relationships TO wp9f_term_relationships;
RENAME TABLE wpstg0_term_taxonomy TO wp9f_term_taxonomy;
RENAME TABLE wpstg0_usermeta TO wp9f_usermeta;
RENAME TABLE wpstg0_users TO wp9f_users;
RENAME TABLE wpstg0_wpforms_entries TO wp9f_wpforms_entries;
RENAME TABLE wpstg0_wpforms_entry_fields TO wp9f_wpforms_entry_fields;
RENAME TABLE wpstg0_wpforms_entry_meta TO wp9f_wpforms_entry_meta;
RENAME TABLE wpstg0_wpforms_logs TO wp9f_wpforms_logs;
RENAME TABLE wpstg0_wpforms_payments TO wp9f_wpforms_payments;
RENAME TABLE wpstg0_wpforms_payment_meta TO wp9f_wpforms_payment_meta;
RENAME TABLE wpstg0_wpmailsmtp_debug_events TO wp9f_wpmailsmtp_debug_events;
RENAME TABLE wpstg0_wpmailsmtp_tasks_meta TO wp9f_wpmailsmtp_tasks_meta;
```

---

## Step 4 — URL Search and Replace
```sql
-- Fix siteurl and home
UPDATE wp9f_options 
SET option_value = REPLACE(option_value, 'nancy.boycan.com/nancy-site-stagi', 'nancy.boycan.com') 
WHERE option_name IN ('siteurl', 'home');

-- Fix any other options containing staging URL
UPDATE wp9f_options 
SET option_value = REPLACE(option_value, 'nancy.boycan.com/nancy-site-stagi', 'nancy.boycan.com') 
WHERE option_value LIKE '%nancy-site-stagi%';

-- Fix post GUIDs
UPDATE wp9f_posts 
SET guid = REPLACE(guid, 'nancy.boycan.com/nancy-site-stagi', 'nancy.boycan.com') 
WHERE guid LIKE '%nancy-site-stagi%';

-- Fix post content
UPDATE wp9f_posts 
SET post_content = REPLACE(post_content, 'nancy.boycan.com/nancy-site-stagi', 'nancy.boycan.com') 
WHERE post_content LIKE '%nancy-site-stagi%';

-- Fix postmeta
UPDATE wp9f_postmeta 
SET meta_value = REPLACE(meta_value, 'nancy.boycan.com/nancy-site-stagi', 'nancy.boycan.com') 
WHERE meta_value LIKE '%nancy-site-stagi%';
```

---

## Step 5 — Fix Usermeta Prefix ⚠️ NEW — Required
> This was missed in the original procedure. Staging copies usermeta keys with the `wpstg0_` prefix.  
> WordPress looks for `wp9f_capabilities` — if it finds only `wpstg0_capabilities`, all users appear to have no role and are locked out of wp-admin.

```sql
UPDATE wp9f_usermeta 
SET meta_key = REPLACE(meta_key, 'wpstg0_', 'wp9f_') 
WHERE meta_key LIKE 'wpstg0_%';
```

Expected: ~7 rows affected (capabilities, user_level, dashboard prefs, etc.)

---

## Step 6 — Disable WP Staging Auth Overlay
Via **cPanel → File Manager** → navigate to:  
`/home/canate5/public_html/nancy.boycan.com/wp-content/plugins/`

Rename: `wp-staging` → `wp-staging-disabled`

> This deactivates the plugin at the filesystem level, bypassing the admin auth overlay that blocks the live site after a push.

---

## Step 7 — Verify Live Site
1. Navigate to `https://nancy.boycan.com/` — confirm memorial site loads
2. Navigate to `https://nancy.boycan.com/wp-login.php` — log in as `sboycan`
3. Go to **Plugins** → rename `wp-staging-disabled` back to `wp-staging` (or do via File Manager)
4. In WP Admin → **WP Staging** settings → turn OFF "Enable admin authorization" toggle
5. Confirm live site still loads after re-enabling plugin

---

## Rollback Procedure (if needed)
Run these to restore the backup tables as live:
```sql
-- Drop the promoted staging tables (now wp9f_*)
-- Then restore from _bak tables:
RENAME TABLE wp9f_options_bak TO wp9f_options;
RENAME TABLE wp9f_posts_bak TO wp9f_posts;
RENAME TABLE wp9f_postmeta_bak TO wp9f_postmeta;
RENAME TABLE wp9f_users_bak TO wp9f_users;
RENAME TABLE wp9f_usermeta_bak TO wp9f_usermeta;
-- ... (repeat for all _bak tables)
```
Then rename the `wp-staging-disabled` folder back to `wp-staging`.

---

## Database Reference
| Item | Value |
|---|---|
| Database | canate5_wp644 |
| Live prefix | wp9f_ |
| Staging prefix | wpstg0_ |
| Unrelated DB | canate5_wrdp1 (canateo.com/web — ignore) |
| Total tables at time of practice push | 130 (99 live + 31 staging) |

## Known Table Discrepancies
These tables exist in staging but NOT in the original live DB — they will be created fresh on push:
- `wp9f_mailpoet_newsletter_segment_statistics`
- `wp9f_mailpoet_newsletter_statistics`

---

## Lessons Learned (Practice Push — Session 5)
1. **MariaDB won't run DDL in PREPARE/EXECUTE** — use individual RENAME TABLE statements only
2. **Batch RENAME TABLE fails if any table missing** — comma-separated list halts on first error; individual statements continue past errors
3. **WP Staging auth overlay is file-based** — renaming the plugin folder is the fastest fix; no DB manipulation needed
4. **Usermeta prefix must be updated** — `wpstg0_capabilities` → `wp9f_capabilities` or all users are locked out of wp-admin (Step 5 above)
5. **cPanel sessions expire** — if phpMyAdmin throws auth errors mid-session, re-login at canateo.com:2083 to get a new session token
6. **CodeMirror in phpMyAdmin** — click in the editor area first before trying to type or inject SQL; the JS `cm.setValue()` approach works but requires clicking the visible Go button afterward
