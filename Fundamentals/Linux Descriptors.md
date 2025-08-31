File Descriptors used for manage I/O operations
1. `STDIN` - 0 : Data Stream for Input
2. `STDOUT` - 1 : Data Strean for Output
3. `STDERR` - 2 : Data Strean for Output that includes Error

`find /etc/ -name -shadow 2>/dev/null` -> find shadow but supress error

`find /etc/ -name shadow 2>/dev/null > results.txt` -> find shadow supress error but result will return on results.txt

`find /etc/ -name shadow 2> stderr.txt 1> stdout.txt` -> find shadow, handle error to stderr.txt and handle output to stdout.txt 

`find /etc/ -name passwd >> stdout.txt 2>/dev/null` -> find anything named passwd and return that in stdout.txt and supress error

`cat << EOF > stream.txt` -> take input, until EOF, then save on stream.txt

`find /etc/ -name *.conf 2>/dev/null | grep systemd | wc -l` -> find on etc config file, supress error, find systemd string, then count how many file (wc -l)
