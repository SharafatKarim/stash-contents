---
Owner: Sharafat Karim
Last edited time: 2022-11-25T21:12
---
**copyright**

> [!info] @ahmubashshir's blog  
> Evidence of my terrible writing skills.  
> [https://ahmubashshir.github.io/](https://ahmubashshir.github.io/)  

---

`${<name>%<pattern>}`  
matches and replaces it from the right once  
  
`${<name>#<pattern>}`  
same, but from left  
  
`${<name>##<pattern>}`  
replace all, from left  
  
`${<name>%%<pattern>}`  
replace all from right  

<pattern> can contain alphanumeric characters and [posix character classes]* and normal shell globs (?/*)

- depends on implementation(eg. sh provided by dash doesn't support them)

  

**eg.**

`test=a.b.c.d/e.f/g-h/i.j.k echo ${test%.` `_} echo ${test%%._` `} echo ${test#` `_.} echo ${test##_` `.} echo ${test%e.f/` `_} echo ${test#_` `/e.f} echo ${test%i.j.?}`

  

snap:

![[/Untitled 10.png|Untitled 10.png]]