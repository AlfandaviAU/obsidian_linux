| cut -dd
`dpkg -l | grep '^ii' | wc -l` -> search all package installed, seach prefix ii -> package, and count how many of it (wc -l)

`cat /etc/passwd | grep -v "false\|nologin"` -> search in /etc/passwd, and exclude whatever with false or nologin string

`cat /etc/passwd | grep -v "false\|nologin | cut -d":" -f1` -> search in /etc/passwd and exclude with false or nologin, and split it by : and get first occurence (using cut feature)

`cut -d<delimiter> -f<occurence>` : split text into by delimiter and select n occurence

`tr <string_to_replace> <string_replace>` : can be used for replace string with another string

`column -t` : remake display into table

`cat /etc/passwd | grep -v "false\|nologin" | tr ":" " " | column -t`
![[Pasted image 20250619183418.png]]

`awk '{args}'` : can be used for displaying desired fields
example : `awk '{print $1, $NF}'` display first `$1`, last details `$NF`
![[Pasted image 20250619183924.png]]

`sed 's/bin/HTP/g'` : can be used to switch string `bin` into `HTB` and `g` flag to replace all matches
![[Pasted image 20250619184335.png]]

[[Linux Filter Exercise]]
