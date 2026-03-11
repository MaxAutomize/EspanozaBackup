# Account Assessment Skill

Assess, authenticate, and manage Microsoft & GitHub account workflows.

## Summary

**Maxwell's Accounts:**
- **Microsoft:** max.rippley22@outlook.com (primary email for Office 365, Canvas, CU Denver integration)
- **GitHub:** max.rippley22@outlook.com (dev work, repos, gists)

Both use the same email but may have separate auth flows depending on 2FA/OAuth setup.

## Quick Reference

### Microsoft Account

**Purpose:** Outlook, OneDrive, Canvas LMS (via SSO), Office 365, CU Denver institutional access

**Check:**
- Security info, sign-in options, connected apps
- 2FA status, recovery email/phone, active sessions
- Canvas SSO connection
- OneDrive storage (linked to Outlook quota)

---

### GitHub Account

**Purpose:** Version control, repos, gists, Actions, code collaboration

**Check:**
- SSH keys active & not expired
- PAT (Personal Access Token) valid & not revoked
- Security log for suspicious activity
- No unauthorized OAuth apps connected
- 2FA enabled

---

## Login & Access Workflow

**Before any assessment or task:**

1. **Get credentials** from TOOLS.md (max.rippley22@outlook.com + password)
2. **Choose channel:**
   - Microsoft: Use browser (account.microsoft.com or via Canvas)
   - GitHub: Use browser (github.com) OR git CLI with SSH/PAT
3. **Verify access:**
   - Can sign in? ✓
   - 2FA prompt? (Have recovery codes ready if locked out)
   - Session active? (Check device list to confirm)
4. **Proceed with task** (assessment, repo work, account management, etc.)

**Credentials location:** TOOLS.md (never hardcode in skills or commit to repos)

---

## Assessment Workflow

Use this checklist before starting any work that touches these accounts:

### Pre-Work Checklist

- [ ] **Microsoft Account Status**
  - [ ] Can log in (no password reset needed)
  - [ ] 2FA working (if enabled)
  - [ ] Canvas SSO connecting properly
  - [ ] No security warnings/alerts
  
- [ ] **GitHub Account Status**
  - [ ] Can log in via web
  - [ ] SSH key configured & tested (if using git clone)
  - [ ] PAT valid & not expired (if using HTTPS auth)
  - [ ] No security alerts or unauthorized OAuth apps

- [ ] **Cross-Account Checks**
  - [ ] Email verified on both platforms
  - [ ] No account lockouts or suspicious activity
  - [ ] Recovery options (backup email/phone) up to date

### Troubleshooting Decision Tree

**"I can't log in"**
→ Password reset? → 2FA issue? → Account locked? → Contact support

**"Git push/pull fails"**
→ SSH key expired? → Wrong permissions? → PAT revoked? → Network issue?

**"Canvas won't load"**
→ Microsoft SSO failing? → Cookies/cache? → Institutional account not linked? → Try incognito

**"Security alert on account"**
→ Check recent sign-ins (geo-suspicious?) → Review connected apps → Enable 2FA if not active

---

## Key Notes

- Both accounts use: max.rippley22@outlook.com
- 2FA may require recovery codes if locked out
- SSH keys expire — check expiry dates regularly
- PATs must be regenerated periodically for security
- Never hardcode credentials in repos or skills
