linkedin_wordlist
=================

Loads of dumps acequiared via various cracking on the linkedin hashset. 

Various techniques listed below were used to retrieve these details and create subsequent .pot file.  


hashcat commands
=================

To crack lower chars up to 8 long:

/tmp/hashcat-cli64.bin --hash-mode 100 -n 32 -a 3 /tmp/linkedin.hashes ?l?l?l?l?l?l?l?l -o /home/linkedin_lower.out

To crack upper chars up to 8 long:

/tmp/hashcat-cli64.bin --hash-mode 100 -n 32 -a 3 /tmp/linkedin.hashes ?u?u?u?u?u?u?u?u -o /home/linkedin_upper.out

To crack upper+lower+special up to 8 long:

/tmp/hashcat-cli64.bin --hash-mode 100 -n 32 -a 3 /tmp/linkedin.hashes -1 ?l?u?s?d ?1?l?l?l?l?l?l?l -o /home/linkedin_upper_lower_special.out

To crack upper+lower+special up to 8 long:

/tmp/hashcat-cli64.bin --hash-mode 100 -n 32 -a 3 /tmp/linkedin.hashes -1 ?l?u?s?d ?1?l?l?l?l?l?l?d -o /home/linkedin_upper_lower_special_digit_last.out

To crack upper+lower+special up to 8 long with string last:

/tmp/hashcat-cli64.bin --hash-mode 100 -n 32 -a 3 /tmp/linkedin.hashes -1 ?l?u?s?d ?1?l?l?l?l?l?l?s -o /home/linkedin_upper_lower_special_string_last.out

To use your GPU for cracking all the characters in the passwords (1-15 long), you will have to download hashcat that supports it and run it as follows :

./cudaHashcat-plus64.bin -m 100 -a 3 -n 160 --gpu-async --gpu-loops 1024 ../../combo_not.txt -1 ?l?d?s?u ?1?1?1?1?1?1?1?1?1? --outfile=/home/output_crack

Also there is possibility to use dictionary combination on the passwords to recover longer passwords such as ohmygod123456. This attack relays on good dictionary so make sure you have one at hand. It will combine the words in specific order, generating a large number of combined passwords that can be up to any length.

./hashcat-cli64.bin -a 1 /tmp/linkedin.hashes --output-file=/home/linkedin_combination.out -m 100 1_combined_passwords_all.txt

or use GPU to help you with the process:

./oclHashcat-plus64.bin -m 100 -a 1 /tmp/linkedin.hashes --outfile=/home/linkedin

