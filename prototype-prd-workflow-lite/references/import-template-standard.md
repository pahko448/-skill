# Import Template Standard

Before generating an import/export template, read or confirm:

- Real backend behavior.
- Current import endpoints or frontend import logic if available.
- Database tables and sample records if credentials are provided.
- Existing import logs and failure reasons if available.
- Required file types and asset handling rules.

## Generic Template Order

1. Basic information.
2. Core configuration modules.
3. Content/data rows.
4. Options/enums/scoring/rules when relevant.
5. Display/report/output modules when relevant.
6. Asset/file list when relevant.
7. Validation rules.
8. Failure and fallback rules.

## Markdown Image Import

Prefer normal Markdown image paths:

```md
![image alt](./images/example.png)
```

Expected behavior:

1. Resolve image path relative to MD file or package root.
2. Upload image to backend/file service.
3. Replace Markdown image syntax with uploaded URL for rich-text fields.
4. Attach image to the module where it appears.
5. If upload fails, keep text importable and mark image as needing repair unless image is required for core flow.

## Validation

Templates should define:

- Required fields.
- Unique fields or codes.
- Enum validity.
- Referenced data existence.
- Asset/file existence.
- Score/range overlap or gaps when relevant.
- Partial success behavior.
- Downloadable failure log.
