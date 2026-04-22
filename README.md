# author mikusuzi
import requests
import re

print('WARNING!!! This only applies to BV number parsing!!! Not for commercial use, for personal use only.')
print('Please do not use this API maliciously. This API can only be used 108 times per day.')
print('API source author address->>>         {https://github.com/injahow/bilibili-parse/tree/master}        ')
header = {

    'user-agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/147.0.0.0 Safari/537.36 Edg/147.0.0.0'
}

while 1:
    bv=input('Enter bv or the current URL\n->>>')
    try:
        bv = re.findall(r"BV[0-9a-zA-Z]{10}", bv)[0]
    except:
        print('Input error: No BV symbol found!\n')
        continue
    op=input('Enter the total number of pages.\n>>>')

    urlbv = 'https://api.injahow.cn/bparse/?'

    while not op.isdigit():
        print('This is not a number, please re-enter.')
        op = input('Please re-enter the page number.\n>>>')

    for p in range(int(op)):
        params ={
            'bv':bv,
            'q':80,
            'otype':'url',
            'p':p
        }
        response = requests.get(urlbv, headers=header, params =params)
        print('Download("Download using software similar to IDM.")->>>',response.content.decode('utf-8'))











