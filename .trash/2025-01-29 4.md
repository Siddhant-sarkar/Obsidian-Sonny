---
created:
  - <% tp.file.creation_date() %>
tags:
  - DailyNote
---


# <% moment(tp.file.title,'DD-dddd').format("dddd, MMMM DD, YYYY") %>

<< [[Purpose/Routine/Daily/<%fileDate = moment(tp.file.title, 'DD-dddd').subtract(1, 'd').format('YYYY/MM-MMMM') %>/<%fileDate = moment(tp.file.title, 'DD-dddd').subtract(1, 'd').format('DD-dddd') %>|Yesterday]] | [[Purpose/Routine/Daily/<% fileDate = moment(tp.file.title, 'DD-dddd').add(1, 'd').format('YYYY/MM-MMMM') %>/<% fileDate = moment(tp.file.title, 'DD-dddd').add(1, 'd').format('DD-dddd') %>|Tomorrow]] >>

---
### 📅 Daily Questions
##### 🌜 Last night, after work, I...
- 

##### 🙌 One thing I'm excited about right now is...
-  

##### 🚀 One+ thing I plan to accomplish today is...
- [ ] 

##### 👎 One thing I'm struggling with today is...
- 

---
# 📝 Notes
- <% tp.file.cursor() %>

---
### Notes created today
```dataview
List FROM "" WHERE file.cday = date("<% moment(tp.file.title,'DD-dddd').format("YYYY-MM-DD") %>") SORT file.ctime asc
```

### Notes last touched today
```dataview
List FROM "" WHERE file.mday = date("<% moment(tp.file.title,'DD-dddd').format("YYYY-MM-DD") %>") SORT file.mtime asc
```