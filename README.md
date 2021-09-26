# Instabot-in-python
import os
import glob
cookie_del = glob.glob("config/*cookie.json")
os.remove(cookie_del[0])
from instabot import Bot
import os
import glob

from tqdm.std import tqdm

bot = Bot(max_follows_per_day=150, follow_delay=0, filter_previously_followed=True, filter_verified_accounts=True, filter_private_users=True, filter_business_accounts=True)



bot.login(username="singhnagar046", password="Deo@9837")

user_list = ["deepikapadukone", "priyankachopra",
 "urvashirautela", "dishapatani", "kiaraaliaadvani", "norafatehi", "aliaabhatt",
             "cristiano" , "virat.kohli" , "avneetkaur_13","jannatzubair29"]


for user in user_list:
    medias = bot.get_user_medias(user, filtration=False)
    print (medias)
    post1 = medias[0]
    post2 = medias[1]

    likers = bot.get_media_likers(post1)

    cnt = 0

    for liker in tqdm(likers):
        if cnt < 10:
            print (bot.get_username_from_user_id(liker))
            bot.follow(liker)
            cnt += 1

    likers = bot.get_media_likers(post2)

    cnt = 0

    for liker in tqdm(likers):
        if cnt < 10:
            print (bot.get_username_from_user_id(liker))
            bot.follow(liker)
            cnt += 1
