##### Grouping Operators

| Operators | Description                  |
| --------- | ---------------------------- |
| `(a)`     | Group parts of regex         |
| `[a-z]`   | List of characters to search |
| `{1,10}`  | Quantifiers, for range       |
| `\|`      | OR operator                  |
| `.*`      | AND operator (both present)  |
example usage : `grep -E "(my|false)" /etc/passwd`
search on /etc/passwd whatever include `my` or `false`

`grep -E "(my.*false)" /etc/passwd`
search on /etc/passwd whatever start with my and end with false

##### Practice
`/etc/ssh/sshd_config` directory

|                                                                        |     |
| ---------------------------------------------------------------------- | --- |
| Search for all lines that contain a word that starts with `Permit`.    |     |
| Search for all lines that contain a word ending with `Authentication`. |     |
| Search for all lines containing the word `Key`.                        |     |
| Search for all lines beginning with `Password` and containing `yes`.   |     |
| Search for all lines that end with `yes`.                              |     |
1. Show all lines that do not contain the `#` character. 
	1. <mark style="background: #FF5582A6;">grep -Ev "#" /etc/ssh/sshd_config</mark>
2. Search for all lines that contain a word that starts with `Permit`.
	1. <mark style="background: #FF5582A6;">grep -E 'Permit.*' /etc/ssh/sshd_config</mark>
3. Search for all lines that contain a word ending with Authentication.
	1. <mark style="background: #FF5582A6;">grep -E 'Authentication$' /etc/ssh/sshd_config</mark>
4. Search for all lines containing the word Key.
	1. <mark style="background: #FF5582A6;">grep -E 'Key' /etc/ssh/sshd_config
</mark>
5. Search for all lines beginning with `Password` and containing `yes`.
	1. <mark style="background: #FF5582A6;">grep -E '^Password.*yes' /etc/ssh/sshd_config</mark>
6. Search for all lines that end with yes.
	1. <mark style="background: #FF5582A6;">grep -E 'yes$' /etc/ssh/sshd_config</mark>