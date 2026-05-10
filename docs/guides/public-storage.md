# Public Storage Review Notes

Public storage is useful for assets that should be visible to everyone, but it can become risky when uploads contain private documents, screenshots, exports, or customer files.

## Common risks

- Uploaded documents are publicly reachable.
- File URLs are guessable or listed.
- Private screenshots are stored in public buckets.
- Signed URL expiration is not used when private access is expected.
- File type and file size limits are missing.

## Review checklist

- [ ] Public buckets are intentionally public.
- [ ] Private uploads require authentication.
- [ ] Sensitive files use signed URLs or equivalent access control.
- [ ] File names do not expose private information.
- [ ] Uploads have type and size limits.
- [ ] Old files can be deleted when users request deletion.

## Safe report wording

```text
Public storage or upload paths were detected. Manual review is recommended to confirm whether uploaded files are intended to be public.
```
