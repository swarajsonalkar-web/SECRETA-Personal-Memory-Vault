# SECRETA — Private Vault

A local-first personal vault for private notes and saved logins.

## Run
1. Extract the ZIP.
2. Open `index.html` using a modern browser.
3. For WebAuthn device verification, run on `https://` or `http://localhost` (not a `file://` URL). A local server is recommended:
   - `python3 -m http.server 8000`
   - Visit `http://localhost:8000`

## Features
- First-run passcode setup and vault lock/unlock
- AES-GCM encryption with a key derived using PBKDF2 (310,000 iterations)
- Private notes and password-manager entries
- Search, edit, delete, copy, and random password generation
- Optional WebAuthn platform-authenticator registration
- Export/import of encrypted vault backups

## Important security notes
- This is a browser-only prototype. Data is stored in this browser's local storage; it does not sync between devices.
- Your passcode is not recoverable. If forgotten, the encrypted vault cannot be decrypted.
- Device verification uses WebAuthn platform authentication. The device may use fingerprint, face recognition, or its PIN/password; a website cannot guarantee fingerprint-only authentication.
- In this prototype, device verification is an additional identity check but does **not** replace the vault passcode or unlock/decrypt the vault by itself.
- Anyone with access to your unlocked browser session may view vault entries. Lock the vault when stepping away.
- Exported backups are encrypted, but protect the backup file and remember the passcode.
- For real-world production use, add security review, stronger session controls, CSP, secure deployment, and testing. Do not treat this prototype as a substitute for a professionally audited password manager.
