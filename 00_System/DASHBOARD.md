#index
> [!abstract] Summary
> A central place for the ideas, knowledge, projects, and work that make up this vault. The dashboard is only a starting point — the actual content lives in the notes linked below.

## Master Notes

The main entry points into the vault.
- [[Math]]
- [[Robotics]]
- [[Control]]
- [[Programming]]
- [[Electronics]]
- [[Computer Hardware]]
- [[Embedded Systems]]
- [[AI]]
- [[Tools]]
- [[Guides]]

## Recently Added
```dataview
TABLE WITHOUT ID
  file.link AS "Note",
  dateformat(file.ctime, "dd MMM yyyy") AS "Added On"
FROM ""
WHERE !contains(file.tags, "#index")
  AND file.path != this.file.path
  AND file.name != "README"
  AND !startswith(file.path, "97_Attachments/")
  AND !startswith(file.path, "98_Inbox/")
  AND !startswith(file.path, "99_Archives/")
SORT file.ctime DESC
LIMIT 5
```
    
> [!Note] Keep it simple  
> Use Master Notes to organize knowledge and keep only master note links.