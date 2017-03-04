import json
import requests
import time
import datetime

user = 'jkms'

def UrlJson(url):
	json_result = requests.get(url).json()
	time.sleep(1) #required by API
	return json_result

def ReturnResults(games):
	if not games:
		print "no games in progress"
	for g in games:
		#print(datetime.datetime.fromtimestamp(g["lastMoveAt"]/1000))
		#print time.time()
		if g["players"]["white"]["userId"] == user:
			my_color = "white"
			if g["color"] == "white":
				my_move = True
			else:
				my_move = False
		else:
			my_color = "black"
			if g["color"] == "black":
				my_move = True
			else:
				my_move = False
		
		if (my_move and my_color == "white"):
			print("[x]%s(%s) vs [ ]%s(%s): %s" % \
			(g["players"]["white"]["userId"], \
			g["players"]["white"]["rating"], \
			g["players"]["black"]["userId"], \
			g["players"]["black"]["rating"], \
			g["moves"].split()[-1]))
		elif(my_move and my_color == "black"): 
			print("[ ]%s(%s) vs [x]%s(%s): %s" % \
			(g["players"]["white"]["userId"], \
			g["players"]["white"]["rating"], \
			g["players"]["black"]["userId"], \
			g["players"]["black"]["rating"], \
			g["moves"].split()[-1]))
		elif (not my_move and my_color == "white"): 
			print("[ ]%s(%s) vs [x]%s(%s): %s" % \
			(g["players"]["white"]["userId"], \
			g["players"]["white"]["rating"], \
			g["players"]["black"]["userId"], \
			g["players"]["black"]["rating"], \
			g["moves"].split()[-1]))
		elif (not my_move and my_color == "black"): 
			print("[x]%s(%s) vs [ ]%s(%s): %s" % \
			(g["players"]["white"]["userId"], \
			g["players"]["white"]["rating"], \
			g["players"]["black"]["userId"], \
			g["players"]["black"]["rating"], \
			g["moves"].split()[-1]))
		
	
games = UrlJson("http://en.lichess.org/api/user/%s/games?playing=1&with_moves=1" % (user))["currentPageResults"]
ReturnResults(games)

