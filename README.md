from requests import post,get
from rich.console import Console
import requests,os,re,uuid
import time
import os
from colorist import Color
from colorist import red
from rich.text import Text
from datetime import datetime
import random
import webbrowser
url = "https://www.instagram.com/sir.ethin"
webbrowser.open(url)
from cfonts import render
B="\033[1;30m" # Black
R="\033[1;31m" # Red
G="\033[1;32m" # Green
Y="\033[1;33m" # Yellow
Bl="\033[1;34m" # Blue
P="\033[1;35m" # Purple
C="\033[1;36m" # Cyan
W="\033[1;37m" # White
H="\x1b[38;5;208m" #
M = '\x1b[1;37m'             
B="\033[1;30m"
R="\033[1;31m"
G="\033[1;32m"
Y="\033[1;33m"
Bl="\033[1;34m"
P="\033[1;35m"
C="\033[1;36m"
N="\033[1;37m"
A = '\033[2;34m'
C = '\033[1;34m'
E = '\033[1;33m'
J = "\033[1;31m"
I = '\033[1;32m'
G = '\033[1;97m'
H="\x1b[38;5;208m"

M = '\x1b[1;37m' 
b = random.randint(5,208)
bo = f'\x1b[38;5;{b}m'
j = random.randint(5,208)
jo = f'\x1b[38;5;{j}m'
cc = {
    'red': "\033[1m\033[31m",
    'green': "\033[1m\033[32m",
    'yellow': "\033[1m\033[33m",
    'blue': "\033[1m\033[34m",
    'cyan': "\033[1m\033[36m",
    'magenta': "\033[1m\033[35m",
    'white': "\033[1m\033[37m",
    'orange': "\033[1m\033[38;5;208m",
    'reset': "\033[0m"
}

def banner():
   

    print(f'''{C}┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓''')
    
    print(f'''{C}┃{E}{J}CH :{G} @KWFFX{C} ┃{J}Dev: {G} ETHAN {C} ┃{J}Ig:{G}@sir.ethin{C} ┃{J}Tele :{G}@RJJVJ''')
    
    print(f'''{C}┗{G}━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┛{G}''')
   
    print(f'''{C}━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━''')
    print('\033[1m' ,render('ETHAN' , font='block', colors=['white' , 'red'], align='center', space=True))
    print(f'''{G}━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━{G}''')
    
uid=str(uuid.uuid4())
console=Console()

def header():
    os.system("cls" if os.name=='nt' else "clear")
    banner()
class TextColor:
    HEADER = '\033[95m'  # Magenta
    OKBLUE = '\033[94m'  # Blue
    OKCYAN = '\033[96m'  # Red
    OKGREEN = '\033[92m' # Green
    WARNING = '\033[93m' # Yellow
    FAIL = '\033[91m'    # Red
    ENDC = '\033[0m'     # End of color
    
    
def Report_Instagram(target_id, sessionid, csrftoken):
    header()
    os.system('clear')
    banner()
    print('')
    
    print(f"{bo}Choose Reports ")
    report_options = [
        "1 : spam",
        "2 : self ",
        "3 : Drugs sell ",
        "4 : nudity",
        "5 : Violence",
    ]
    
    for option in report_options:
        print(f"  {TextColor.OKCYAN}{option}{TextColor.ENDC}")

    while True:
        try:
            reportType = int(input(f"{TextColor.OKGREEN}Choose: {TextColor.ENDC} "))
            if reportType in range(1, 6):
                print(f"{TextColor.OKGREEN}You selected: {reportType}{TextColor.ENDC}")
                break
            else:
                print(f"{TextColor.FAIL}Invalid input. Please choose a number between 1 and 6.{TextColor.ENDC}")
        except ValueError:
            print(f"{TextColor.FAIL}Invalid input. Please enter a valid number.{TextColor.ENDC}")


    while 1:
        try:
            r3 = post(
                "https://i.instagram.com/users/" + target_id + "/flag/",
                headers={
                    "User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:109.0) Gecko/20100101 Firefox/110.0",
                    "Host": "i.instagram.com",
                    'cookie': f"sessionid={sessionid}",
                    "X-CSRFToken": csrftoken,
                    "Content-Type": "application/x-www-form-urlencoded; charset=UTF-8"
                },
                data=f'source_name=&reason_id={reportType}&frx_context=',
                allow_redirects=False
            )         
            
            if r3.status_code==429:
                console.print(f"- Account Flagged [ {r3.status_code} ] ");exit()
            elif r3.status_code==500:
                console.print(f"- Target Not Found with status code [ {r3.status_code} ] ");exit()
            else:
                console.print(f"Reportd Done [bold green]successfully[/bold green]") 
                time.sleep(3)				
        except requests.exceptions.TooManyRedirects:
            console.print(f"Reportd Done [bold green]successfully[/bold green]")#;exit()
            time.sleep(3)
        except Exception as e:
            console.print(f"- Report Failed with status code [ {r3.status_code} ] ");exit()

def starter():
    
    user = input("\033[1;32m username : \033[0m")
    os.system('clear')
    banner()
    if user=="":console.print("[!] You must write The user");exit()
    pess = input("\033[1;32m password : \033[0m")
    os.system('clear')
    banner()
    if pess=="":console.print("[!] You must write The password");exit()
    r1=post('https://i.instagram.com/api/v1/accounts/login/',headers={'User-Agent': 'Instagram 114.0.0.38.120 Android (30/3.0; 216dpi; 1080x2340; huawei/google; Nexus 6P; angler; angler; en_US)',"Accept": "*/*","Accept-Encoding": "gzip, deflate","Accept-Language": "en-US","X-IG-Capabilities": "3brTvw==","X-IG-Connection-Type": "WIFI","Content-Type": "application/x-www-form-urlencoded; charset=UTF-8",'Host': 'i.instagram.com'},data={'_uuid': uid,'password': pess,'username': user,'device_id': uid,'from_reg': 'false','_csrftoken': 'missing','login_attempt_count': '0'},allow_redirects=True)
    if 'logged_in_user' in r1.text:
        console.print("Logged in [bold green]successfully[/bold green] ")
        sessionid=r1.cookies['sessionid']
        csrftoken=r1.cookies['csrftoken']
        target=input(f"\033[1;36m Target : \033[0m ") 

        r2=post('https://i.instagram.com:443/api/v1/users/lookup/',headers={"Connection": "close", "X-IG-Connection-Type": "WIFI","mid":"XOSINgABAAG1IDmaral3noOozrK0rrNSbPuSbzHq","X-IG-Capabilities": "3R4=","Accept-Language": "ar-sa","Content-Type": "application/x-www-form-urlencoded; charset=UTF-8","User-Agent": "Instagram 99.4.0 TweakPY_vv1ck (TweakPY_vv1ck)","Accept-Encoding": "gzip, deflate"},data={"signed_body": "35a2d547d3b6ff400f713948cdffe0b789a903f86117eb6e2f3e573079b2f038.{\"q\":\"%s\"}" % target})
        if 'No users found' in r2.text:
            adv_search=get(f'https://www.instagram.com/{target}',headers={'Host': 'www.instagram.com','User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:109.0) Gecko/20100101 Firefox/110.0','Accept': 'text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8','Accept-Language': 'ar,en-US;q=0.7,en;q=0.3','Accept-Encoding': 'gzip, deflate, br','Connection': 'keep-alive','Cookie': f'csrftoken={csrftoken}','Upgrade-Insecure-Requests': '1','Sec-Fetch-Dest': 'document','Sec-Fetch-Mode': 'navigate','Sec-Fetch-Site': 'none','Sec-Fetch-User': '?1','TE': 'trailers'})
            try:
                target_id=re.findall('"profile_id":"(.*?)"',adv_search.text)[0]
                Report_Instagram(target_id,sessionid,csrftoken)
            except IndexError:
                try:
                    target_id=re.findall('"page_id":"profilePage_(.*?)"',adv_search.text)[0]
                    Report_Instagram(target_id,sessionid,csrftoken)
                except IndexError:
                    try:
                        adv_search2=get(f'https://www.instagram.com/api/v1/users/web_profile_info/?username={target}',headers={'Host': 'www.instagram.com','User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:109.0) Gecko/20100101 Firefox/110.0','Accept': '*/*','Accept-Language': 'ar,en-US;q=0.7,en;q=0.3','Accept-Encoding': 'gzip, deflate, br','X-CSRFToken': csrftoken,'X-IG-App-ID': '936619743392459','X-ASBD-ID': '198387','X-IG-WWW-Claim': 'hmac.AR3KPEPoXkWYhwtoCUKyUHK80GsE1g2PJI1uPtDlCyo4PHKn','X-Requested-With': 'XMLHttpRequest','Alt-Used': 'www.instagram.com','Connection': 'keep-alive','Referer': f'https://www.instagram.com/{target}/','Cookie':  f'sessionid={sessionid}','Sec-Fetch-Dest': 'empty','Sec-Fetch-Mode': 'cors','Sec-Fetch-Site': 'same-origin','TE': 'trailers'})
                        target_id=adv_search2.json()['data']['user']['id']
                        Report_Instagram(target_id,sessionid,csrftoken)
                    except KeyError:
                        console.print('\n- [bold red]Failed[/bold red] to get target username, Try entering the Target ID manually .\n')
                        target_id=input('- Enter The Target ID : ')
                        Report_Instagram(target_id,sessionid,csrftoken)
        elif '"spam":true' in r2.text:
            console.print("- Try again Later !");exit()
        else:
            try:
                target_id=str(r2.json()['user_id'])
                Report_Instagram(target_id,sessionid,csrftoken)
            except KeyError:
                console.print('- General [bold red]Error[/bold red] ...');exit() 
    elif 'ip_block' in r1.text:
        console.print("- You Have [bold red]banned[/bold red] from Instagram ( [bold red]ip block[/bold red] ) !");exit()
    elif 'The password you entered is incorrect' in r1.text:
        console.print("- Please check Your Password !");exit()
    elif "Please check your username and try again." in r1.text:
        console.print("- username Not Found !");exit()
    elif 'two_factor_required' in r1.text:
        console.print("- [bold orange3]Two Factor[/bold orange3] ! ...");exit()
    elif 'challenge_required' in r1.text:
        console.print("- [bold orange3]Secure[/bold orange3] Account ! ...");exit()
    elif 'inactive user' in r1.text:
        console.print('- This user is [bold red]banned[/bold red] from Instagram ...');exit()
    elif "We're working on it and we'll get it fixed as soon as we can." in r1.text:
        console.print("- Try again in a minute !");exit()
    elif 'Please wait a few minutes before you try again' in r1.text:
        console.print("- Try again in a minute !");exit()
    elif 'Bad request' in r1.text:
        console.print("- [bold red]Error[/bold red] in instagram, try again in 15 minutes ...");exit()
    elif 'Invalid Parameters' in r1.text:
        console.print("- [bold red]Error[/bold red] Please Reinstall The Tool From The original Source ... ");exit()
    else:
        console.print('- General [bold red]Error[/bold red] ...');exit()    



header();starter()
