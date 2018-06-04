politicalP = []
users = []
tDistribution = []
line = ("===========================")
listPresi=[]
chosenlistlPresi=[]


# Variables that catch menu options are signed with an m at the start of the name, example: mAdmMenu
# "i" refers to index in lists
# "nCantons" "nDistritcs" refers to index of each zone in the list

#######################################################################################################################

#This method cointans main menu option, here the user can log in or register
def mainMenu():                                                                                              #Main Menu
    messMenu = ("1.Log in"+"\n"+"2.Sign up"+"\n")                                        #messMenu (Main Menu's message)
    print(line)
    mMenu = input(messMenu)
    while mMenu != "1" and mMenu != "2":
        print(line)
        mMenu = input("Invalid option"+"\n"+messMenu)
    if mMenu == "1":
        print(line)
        logIn()
    elif mMenu == "2":
        print(line)
        signUp()

#######################################################################################################################

#Users and adms can log in using its ID and password, if the user is an adm it shows adm´s menu and if is an user it
# shows consults section
def logIn():                                                                                                    #LOG IN
    userId = input("Id: ")
    userPass = input("Password: ")
    logInUser = userId+userPass
    i=0
    while i<len(users):
        if users[i]["password"] in logInUser and users[i]["adm"]=="1":
            print(line)
        elif users[i]["password"] in logInUser and users[i]["adm"]=="2":
            print(line)
            admMenu()
        i+=1
    if i == len(users):
        print("Sorry, we couldn't find that combination of ID and Password")
        mainMenu()

#######################################################################################################################

#Users register their account with this method, it ask for user's name, age, id, password and email, if some user's id
# is already signed it will show an warning and it will ask for another id. Also there are some validations like
#"IntValidation" , it only allows numbers, and "validation" it doesnt allow let fields empty

def signUp():                                                                                                   #Sign Up
    name = input("Name: ")
    name = validation(name,"Name: ")
    age = input("Age: ")
    age = validation(age,"Age: ")
    age = intValidation(age,"Age: ")
    id = input("Id: ")
    id = validation(id,"Id: ")
    for ids in users:
        while id == ids["id"]:
            id = input("Id already signed up" + "\n" + "Id: ")
    email = input("Email address: ")
    email = validation(email, "Email: ")
    for emails in users:
        while email == emails["email"]:
            email = input("Email already signed up" + "\n" + "Email: ")
    password = input("Password: ")
    password = validation(password, "Password: ")
    adm=input("1.Guest"+"\n"+"2.Admin"+"\n")
    while adm!=("1") and adm!=("2"):
        adm = input("Invalid option"+"\n"+"1.Guest"+"\n"+"2.Admin"+"\n")
    password=id+password
    newUser={"name":name,"age":age,"id":id,"email":email,"password":password,"adm":adm}
    users.append(newUser)
    mainMenu()

#######################################################################################################################


def admMenu():                                                                                              #Adm's Menu
    messAdmMenu=("1.Territorial Distribution"+"\n"+"2.Political parties"+"\n"+"3.Ballots"+"\n"+"4.Results"+"\n"+"5.Consults"+"\n"+"6.Log Out"+"\n")
    mAdmMenu=input(messAdmMenu)
    while mAdmMenu!=("1") and mAdmMenu!=("2") and mAdmMenu!=("3") and mAdmMenu!=("4") and mAdmMenu!=("5") and mAdmMenu!=("6"):
        mAdmMenu=input("Invalid Option"+"\n"+messAdmMenu)
    if mAdmMenu==("1"):
        print(line)
        territorialDistribution()
    elif mAdmMenu==("2"):
        print(line)
        politicalParties()
    elif mAdmMenu ==("3"):
        print(line)
        opcion = input("1.Presidential ballot" + "\n" + "2.Legislative ballot"+"\n")
        if opcion == "1":
            print(line)
            ballots()
        if opcion == "2":
            print(line)
            ballotsLegis(tDistribution)
        else:
            print(line)
            print("Invalid Option")
            print(line)
            admMenu()
    elif mAdmMenu == ("4"):
        results()
    elif mAdmMenu == ("5"):
        consults()
    elif mAdmMenu == ("6"):
        mainMenu()

    elif mAdmMenu ==("4"):
        print(line)
        results()
    elif mAdmMenu ==("5"):
        print(line)
    elif mAdmMenu ==("6"):
        mainMenu()

#######################################################################################################################

def politicalParties():                                                                         #POLITICAL PARTIES ADMIN
    mPoliticalParties = input("1.Create political party"+"\n"+"2.Delete political party"+"\n"+"3.Modify political party"+
                              "\n"+"4.See political parties"+"\n"+"5.Back"+"\n")
    if mPoliticalParties == "1":                                                                #ADD POLITICAL PARTY
        message1 = "added"
        addPoliticalParty(message1)
    elif mPoliticalParties == "2":                                                              #REMOVE POLITICAL PARTY
        message1 = "remove"
        message2 = "removed"
        removePoliticalParty(message1,message2)
    elif mPoliticalParties == "3":                                                              #MODIFY POLITICAL PARTY
        message1 = "modify"
        message2 = "modified"
        removePoliticalParty(message1,message2)
        addPoliticalParty(message2)
    elif mPoliticalParties == "4":
        print(line)
        print("Political Parties:")
        for politicalPartiesL in politicalP:
            print(politicalPartiesL["pName"])
        print(line)
    elif mPoliticalParties == "5":
        print(line)
        admMenu()
    else:
        print(line)
        print("Invalid Option"+"\n")
    politicalParties()


def addPoliticalParty(message1):
    print(line)
    partyName = input("Political Party's Name: ")
    partyName = validation(partyName, "Political Party's name: ")
    partyColors = input("Political Party's Colors: ")
    partyColors = validation(partyColors, "Political Party's colors: ")
    partyIdeology = input("Political Party's Ideology: ")
    partyIdeology = validation(partyIdeology, "Political Party's ideology: ")
    foundationYear = input("Political Party's Foundation Year: ")
    foundationYear = validation(foundationYear, "Foundation year: ")
    foundationYear = intValidation(foundationYear,"Foundation year: ")
    newParty = {"pName": partyName, "pColor": partyColors, "pIdeology": partyIdeology, "pYear": foundationYear,"votes":[]}
    print("======Political Party "+message1+"======")
    politicalP.append(newParty)


def removePoliticalParty(message1,message2):
    print(line)
    if len(politicalP) != 0:
        ppList = []
        x = 1
        print("Type the number of the political party that you want to "+message1)
        for politicalParty in politicalP:
            ppID = {"id": x, "name": politicalParty["pName"]}
            ppList.append(ppID)
            print(str(ppID["id"]) + "." + ppID["name"])
            x += 1
        mOption = input()
        mOption = int(intValidation(mOption," "))
        while mOption < 1 or mOption > x-1:
            mOption = input("Invalid option" + "\n")
            mOption = int(intValidation(mOption, " "))
        i = 0
        while i < len(ppList):
            if str(ppList[i]["id"]) == str(mOption):
                for ppOption in politicalP:
                    if ppOption["pName"] == ppList[i]["name"]:
                        politicalP.remove(politicalP[i])
            i += 1
        if message2 == "removed":
            print("======Political Party "+message2+"======")
    else:
        print("There is not political parties to "+message1)
        print(line)
        politicalParties()

#######################################################################################################################

def territorialDistribution():
    provincesList = []
    mTerritorialD = input("1.Add Province"+"\n"+"2.Manage Provinces"+"\n"+"3.See Provinces"+"\n"+"4.Back"+"\n")
    if mTerritorialD == "1": #Add Province
        TDAddZones("province","","")
        territorialDistribution()
    elif mTerritorialD == "2": #Manage Province
        if len(tDistribution)==0:
            print(line)
            print("There are not provinces to manage")
            print(line)
            territorialDistribution()
        else:
            id = 1                                                                          #assigns an id to each province to be managed
            print(line+"\n"+"Provinces:")
            for province in tDistribution:
                provinceID = {"id": id, "provinceName": province["province"]}
                provincesList.append(provinceID)
                print(str(provinceID["id"]) + " . " + provinceID["provinceName"])
                id += 1
            mProvince = input()
            mProvince = intValidation(mProvince," ")
            while mProvince < 1 or mProvince > len(tDistribution):
                mProvince = input("Invalid option" + "\n")
                mProvince = int(intValidation(mProvince, " "))
            i = 0
            while i < len(provincesList):
                if str(provincesList[i]["id"]) == str(mProvince):
                    TDProvinces(provincesList[i]["provinceName"])
                i += 1
    elif mTerritorialD == "3": #See provinces
        if len(tDistribution) == 0:
            print(line)
            print("There are not provinces to show")
            print(line)
            territorialDistribution()
        else:
            print(line+"\n"+"Provinces:")
            for province in tDistribution:
                print(province["province"])
            print(line)
            territorialDistribution()
    elif mTerritorialD == "4":
        print(line)
        admMenu()
    else:
        print("Invalid Option")
        territorialDistribution()

def TDAddZones(zone,selectedProvince,selectedCanton):
    print(line)
    if zone == "province":
        nameProvince = input("Province´s name: ")
        nameProvince = validation(nameProvince, "Province's name: ")
        deputies = input("Deputies: ")
        deputies = intValidation(deputies, "Deputies: ")
        nameProvince = nameProvince.capitalize()
        tDistribution.append({"province": nameProvince,"pBallot":[],"lBallot":[], "deputies": deputies, "cantons": []})
        print("======Province Added=======")
    elif zone == "canton":
        nameCanton = input("Canton´s name: ")
        nameCanton = validation(nameCanton, "Canton´s name: ")
        nameCanton = nameCanton.capitalize()
        newCanton = {"canton": nameCanton ,"pBallot":[],"lBallot":[],"district":[]}
        i = 0
        while len(tDistribution)>i:
            if tDistribution[i]["province"] == selectedProvince:
                tDistribution[i]["cantons"].append(newCanton)
                break
            i += 1
        print("======Canton Added=======")
    elif zone == "district":
        nameDistrict = input("District's name: ")
        nameDistrict = validation(nameDistrict,"District's name: ")
        nameDistrict = nameDistrict.capitalize()
        newDistrict = {"district":nameDistrict,"pBallot":[],"lBallot":[]}
        i = 0
        nCantons = 0
        while len(tDistribution) > i:
            if tDistribution[i]["province"] == selectedProvince:
                while len(tDistribution[i]["cantons"]) > nCantons:
                    if tDistribution[i]["cantons"][nCantons]["canton"] == selectedCanton:
                        tDistribution[i]["cantons"][nCantons]["district"].append(newDistrict)
                        break
                    nCantons += 1
            i += 1
        print("======District Added=======")

def TDRemoveZones(zone,selectedProvince,selectedCanton,selectedDistrict):
    if zone == "province":
        i = 0
        while i < len(tDistribution):
            if tDistribution[i]["province"] == selectedProvince:
                tDistribution.remove(tDistribution[i])
            i += 1
        print("======Province Removed=======")
    elif zone == "canton":
        i = 0
        nCantons = 0
        while i < len(tDistribution):
            if tDistribution[i]["province"] == selectedProvince:
                while len(tDistribution[i]["cantons"]) > nCantons:
                    if tDistribution[i]["cantons"][nCantons]["canton"] == selectedCanton:
                        del tDistribution[i]["cantons"][nCantons]
                    nCantons += 1
            i += 1
        print("=====Canton Removed======")
    elif zone == "district":
        i = 0
        nCantons = 0
        nDistricts = 0
        while len(tDistribution) > i:
            if tDistribution[i]["province"] == selectedProvince:
                while len(tDistribution[i]["cantons"]) > nCantons:
                    if tDistribution[i]["cantons"][nCantons]["canton"] == selectedCanton:
                        while len(tDistribution[i]["cantons"][nCantons]["district"]) > nDistricts:
                            if tDistribution[i]["cantons"][nCantons]["district"][nDistricts]["district"] == selectedDistrict:
                                    del tDistribution[i]["cantons"][nCantons]["district"][nDistricts]
                            nDistricts += 1
                    nCantons += 1
            i += 1
        print("=====District Removed======")

def TDModifyZones(zone,selectedProvince,selectedCanton,selectedDistrict):
    print(line)
    if zone == "province":
        nameProvince = input("New province's name: ")
        nameProvince = validation(nameProvince, "New province´s name: ")
        deputies = input("Deputies: ")
        deputies = intValidation(deputies, "Deputies: ")
        nameProvince = nameProvince.capitalize()
        i = 0
        while i<len(tDistribution):
            if tDistribution[i]["province"] == selectedProvince:
                tDistribution[i]["province"] = nameProvince
                tDistribution[i]["deputies"] = deputies
                break
            i += 1
        selectedProvince=nameProvince
        print("======Province Modified=======")
        TDProvinces(selectedProvince)
    elif zone == "canton":
        nameCanton = input("New canton´s name: ")
        nameCanton = validation(nameCanton, "New canton´s name: ")
        nameCanton = nameCanton.capitalize()
        i = 0
        nCanton = 0
        while i < len(tDistribution):
            if tDistribution[i]["province"] == selectedProvince:
                while len(tDistribution[i]["cantons"])>nCanton:
                    if tDistribution[i]["cantons"][nCanton]["canton"] == selectedCanton:
                        tDistribution[i]["cantons"][nCanton]["canton"] = nameCanton
                        break
                    nCanton+=1
            i += 1
        selectedCanton=nameCanton
        print("======Canton Modified=======")
        TDCantons(selectedProvince, selectedCanton)
    elif zone == "district":
        nameDistrict = input("New district´s name: ")
        nameDistrict = validation(nameDistrict, "New district´s name: ")
        nameDistrict = nameDistrict.capitalize()
        i= 0
        nCantons = 0
        nDistricts = 0
        while len(tDistribution) > i:
            if tDistribution[i]["province"] == selectedProvince:
                while len(tDistribution[i]["cantons"]) > nCantons:
                    if tDistribution[i]["cantons"][nCantons]["canton"] == selectedCanton:
                        while len(tDistribution[i]["cantons"][nCantons]["district"]) > nDistricts:
                            if tDistribution[i]["cantons"][nCantons]["district"][nDistricts]["district"] == selectedDistrict:
                                tDistribution[i]["cantons"][nCantons]["district"][nDistricts]["district"] = nameDistrict
                            nDistricts += 1
                    nCantons += 1
            i += 1
        selectedDistrict=nameDistrict
        print("======Canton Modified=======")
        TDDistricts(selectedProvince, selectedCanton,selectedDistrict)

def TDProvinces(selectedProvince):
    print("========="+selectedProvince+"==========")
    mTDProvinces = input("1.Modify provice"+"\n"+"2.Delete this province"+"\n"+"3.Manage "+selectedProvince+"'s cantons"+"\n"+"4.Back"+"\n")
    if mTDProvinces == "1":                                                                                             # Modify Province
        TDModifyZones("province",selectedProvince,"","")
    elif mTDProvinces == "2":                                                                                            # Delete this province
        removeOption=input("Are you sure you want to remove "+selectedProvince+"\n"+"1.Yes"+"\n"+"2.No"+"\n")
        if removeOption == "1":
            TDRemoveZones("province",selectedProvince,"","")
            territorialDistribution()
        elif removeOption == "2":
            TDProvinces(selectedProvince)
    elif mTDProvinces == "3":                                                                                           # Manage Cantons
        print("========="+selectedProvince+"==========")
        mTDCantons = input("1.Add Canton"+"\n"+"2.Manage Cantons"+"\n"+"3.See Cantons"+"\n"+"4.Back"+"\n")
        if mTDCantons == "1":                                                                                           #Add Canton
            TDAddZones("canton",selectedProvince,"")
            TDProvinces(selectedProvince)
        elif mTDCantons == "2":                                                                                         #Manage Cantons
            i = 0
            nCantons = 0
            print(line+"\n"+selectedProvince+"'s cantons:")
            while len(tDistribution) > i:
                if tDistribution[i]["province"] == selectedProvince:
                    if len(tDistribution[i]["cantons"]) == 0:
                        print(line)
                        print("There are not cantons to manage")
                        TDProvinces(selectedProvince)
                    else:
                        while len(tDistribution[i]["cantons"]) > nCantons:
                            print(str(nCantons+1)+"."+tDistribution[i]["cantons"][nCantons]["canton"])
                            nCantons += 1
                        break
                i += 1
            optionCanton = input()
            optionCanton = intValidation(optionCanton,"")
            while optionCanton<1 or optionCanton>nCantons:
                optionCanton = input("Invalid Option"+"\n")
                optionCanton = intValidation(optionCanton,"")
            selectedCanton = tDistribution[i]["cantons"][optionCanton-1]["canton"]
            TDCantons(selectedProvince,selectedCanton)
        elif mTDCantons == "3":
            i = 0
            nCantons = 0
            print("==="+selectedProvince+"'s"+" cantons===")
            while len(tDistribution)>i:
                if tDistribution[i]["province"] == selectedProvince:
                    while len(tDistribution[i]["cantons"]) > nCantons:
                        print(tDistribution[i]["cantons"][nCantons]["canton"])
                        nCantons+=1
                i+=1
            TDProvinces(selectedProvince)
        elif mTDCantons == "4":
            TDProvinces(selectedProvince)
        else:
            print(line)
            print("Invalid Option")
            TDProvinces(selectedProvince)
    elif mTDProvinces == "4":
        print(line)
        territorialDistribution()
    else:
        print(line)
        print("Invalid Option")
        TDProvinces(selectedProvince)

def TDCantons(selectedProvince,selectedCanton):
    print("=========" + selectedCanton + "==========")
    mTDCantons = input("1.Modify canton" + "\n" + "2.Delete this canton" + "\n" + "3.Manage " + selectedCanton + "'s districts" + "\n" + "4.Back" + "\n")
    if mTDCantons == "1":
        TDModifyZones("canton",selectedProvince,selectedCanton,"")
    elif mTDCantons == "2":
        TDRemoveZones("canton" , selectedProvince , selectedCanton,"")
        TDProvinces(selectedProvince)
    elif mTDCantons == "3":
        print("=== "+selectedCanton+" ===")
        mTDDistrics = input("1.Add District"+"\n"+"2.Manage Districts"+"\n"+"3.See "+selectedCanton+"'s Districts"+"\n"+"4.Back"+"\n")
        if mTDDistrics == "1":                                                                                            # Add district
            TDAddZones("district",selectedProvince,selectedCanton)
            TDCantons(selectedProvince, selectedCanton)
        elif mTDDistrics == "2":                                                                                          #Manage district
            i = 0
            nCantons = 0
            nDistricts = 0
            print(line + "\n" + selectedCanton + "'s districts:")
            while len(tDistribution) > i:
                if tDistribution[i]["province"] == selectedProvince:
                        while len(tDistribution[i]["cantons"]) > nCantons:
                            if tDistribution[i]["cantons"][nCantons]["canton"] == selectedCanton:
                                if len(tDistribution[i]["cantons"][nCantons]["district"]) == 0:
                                    print(line)
                                    print("There are not districts to manage")
                                    TDCantons(selectedProvince,selectedCanton)
                                else:
                                    while len(tDistribution[i]["cantons"][nCantons]["district"]) > nDistricts:
                                        print(str(nDistricts + 1) + "." + tDistribution[i]["cantons"][nCantons]["district"][nDistricts]["district"])
                                        nDistricts += 1
                                    break
                            nCantons += 1
                        break
                i += 1
            optionDistrict = input()
            optionDistrict = intValidation(optionDistrict, "")
            while optionDistrict < 1 or optionDistrict > nDistricts:
                optionDistrict = input("Invalid Option" + "\n")
                optionDistrict = intValidation(optionDistrict, "")
            selectedDistrict = tDistribution[i]["cantons"][nCantons]["district"][optionDistrict - 1]["district"]
            TDDistricts(selectedProvince,selectedCanton,selectedDistrict)
        elif mTDDistrics == "3":                                                                                         #See districts
            i = 0
            nCantons = 0
            nDistricts = 0
            print(line + "\n" + selectedCanton + "'s districts:")
            while len(tDistribution) > i:
                if tDistribution[i]["province"] == selectedProvince:
                    while len(tDistribution[i]["cantons"]) > nCantons:
                        if tDistribution[i]["cantons"][nCantons]["canton"] == selectedCanton:
                            if len(tDistribution[i]["cantons"][nCantons]["district"]) == 0:
                                print(line)
                                print("There are not districts to show")
                                mTDCantons
                            else:
                                while len(tDistribution[i]["cantons"][nCantons]["district"]) > nDistricts:
                                    print(tDistribution[i]["cantons"][nCantons]["district"][nDistricts]["district"])
                                    nDistricts += 1
                        nCantons += 1
                i += 1
            TDCantons(selectedProvince,selectedCanton)
        elif mTDDistrics == "4":
            TDCantons(selectedProvince, selectedCanton)
        else:
            print("Invalid Option")
            TDCantons(selectedProvince, selectedCanton)
    elif mTDCantons == "4":
        TDProvinces(selectedProvince)
    else:
        print("Invalid Option")
        TDCantons(selectedProvince,selectedCanton)

def TDDistricts(selectedProvince,selectedCanton,selectedDistrict):
    print("==== "+selectedDistrict+" =====")
    mTDDistricts = input("1. Modify district"+"\n"+"2. Delete this district"+"\n"+"3. Back"+"\n")
    if mTDDistricts == "1":
        TDModifyZones("district",selectedProvince,selectedCanton,selectedDistrict)
    elif mTDDistricts == "2":
        TDRemoveZones("district",selectedProvince,selectedCanton,selectedDistrict)
        TDCantons(selectedProvince,selectedCanton)
    elif mTDDistricts == "3":
        TDCantons(selectedProvince,selectedCanton)

#######################################################################################################################

def results():
    print("================= RESULTS ========================")
    i = 0
    while len(tDistribution) > i:
        nCantons = 0
        while len(tDistribution[i]["cantons"]) > nCantons:
            if len(tDistribution[i]["cantons"][nCantons]["district"]) == 0:
                print("Please add at least 1 district to " + tDistribution[i]["cantons"][nCantons]["canton"])        #verify if in any canton there is not an district
                admMenu()
            nCantons += 1
        i += 1
        if len(tDistribution[0]["pBallot"]) == 0:
            print("Presidential ballot have not been created")
            print(line + "========================")
            admMenu()
        mResults = input("1. Add presidential elections results" + "\n" + "2. Add legislative elections results"+"\n"+"3. Back"+"\n")
        if mResults == "1" :
            presidentialResults()
        elif mResults == "2" :
            legislativeResults()
        elif mResults == "3" :
            print(line)
            admMenu()
        else:
            print(line+"========================")
            print("Invalid Option")
            results()

def presidentialResults():  # Presidential Results
    print("===============Presidential Results===============")
    votePList = chosenlistlPresi
    i = 0
    while len(tDistribution) > i:
        nCantons = 0
        while len(tDistribution[i]["cantons"]) > nCantons:
            nDistricts = 0
            while len(tDistribution[i]["cantons"][nCantons]["district"]) > nDistricts:
                print("===Votes from " + tDistribution[i]["cantons"][nCantons]["district"][nDistricts][
                    "district"] + "===")
                for ballot in votePList:
                    votes = input(ballot["pName"] + ":    ")
                    votes = validation(votes, ballot["pName"] + ":    ")
                    votes = intValidation(votes, ballot["pName"] + ":    ")
                    votesRegister = {"pName": ballot["pName"], "votes": votes}
                    tDistribution[i]["cantons"][nCantons]["district"][nDistricts]["pBallot"].append(votesRegister)
                nDistricts += 1
            nCantons += 1
        i += 1
    results()

def legislativeResults():
    voteLList = []
    i = 0
    while len(tDistribution) > i:
        voteLList.clear()
        voteLList = tDistribution[i]["lBallot"]
        nCantons = 0
        while len(tDistribution[i]["cantons"]) > nCantons:
            nDistricts = 0
            while len(tDistribution[i]["cantons"][nCantons]["district"]) > nDistricts:
                print("===Votes from " + tDistribution[i]["cantons"][nCantons]["district"][nDistricts][
                    "district"] + "===")
                for ballot in voteLList:
                    votes = input(ballot["pName"] + ":    ")
                    votes = validation(votes, ballot["pName"] + ":    ")
                    votes = intValidation(votes, ballot["pName"] + ":    ")
                    votesRegister = {"pName": ballot["pName"], "votes": votes}
                    tDistribution[i]["cantons"][nCantons]["district"][nDistricts]["lBallot"] = votesRegister
                nDistricts += 1
            nCantons += 1
        i += 1
    print(tDistribution)

#######################################################################################################################

def createPballot(politicalP):
    option=0
    while option!="4":
        option = input("Presidential ballot paper" + "\n" +
                       "1.Create a new ballot paper" + "\n" +
                       "2.Modify ballot paper" + "\n" +
                       "3.Delete ballot paper" + "\n" +
                       "4.See the ballot"+ "\n" +
                       "5.Exit "+ "\n")
        if option == "1":  # CREATE NEW BALLOT#
            if len(chosenlistlPresi)<=0:
                createPballotS(politicalP,listPresi)
            else:
                print("Already Exist")
                createPballot(politicalP)
        elif option=="2":
            modifyPballot(chosenlistlPresi,listPresi)
        elif option=="3":
            deletePballot(chosenlistlPresi,listPresi)
        elif option=="4":
            print(line)
            print("President Ballot")
            if len(chosenlistlPresi)>0:

                for x in chosenlistlPresi:
                    print (x["pName"])
                print(line)
            else:
                print(line)
                print("Without ballot")
                print(line)
            ballots()
        elif option=="5":
            print(line)
            admMenu()
        else:
            print(line)
            print("Invalid option")
            print(line)
    admMenu()

def createPballotS(politicalP,listPresi):
    if len(tDistribution) > 0:
        listPresi.clear()
        for list in politicalP:
            listPresi.append(list)
        finish = "1"
        while finish == "1":
            if len(listPresi) > 0:
                i = 0
                ppballot = []
                x = 1
                for ppoliticalballo in listPresi:
                    partyID = {"id": x, "name": ppoliticalballo["pName"]}
                    ppballot.append(partyID)
                    x += 1
                print(line)
                print("The options are:")

                for parties in ppballot:
                    print(str(parties["id"]) + "." + parties["name"])
                try:
                    optionb = int(input("Choose the party you want to add: "))

                except ValueError:
                    print("Invalid Option")
                    print(line)
                    createPballotS(politicalP,listPresi)
                if optionb>len(ppballot):
                    print("Invalid Option")

                finish = input("Do you add another party "+"\n"+
                               "1-YES"+"\n"+
                               "2-NO"+"\n")
                print(line)

                for party in ppballot:
                    if str(optionb) == str(party["id"]):
                        chosenlistlPresi.append(listPresi[i])
                        listPresi.remove(listPresi[i])
                    i += 1
            else:
                print(line)
                print("No more politcal parties")
                print(line)
                print("Presidential ballot paper:")
                for party in chosenlistlPresi:
                    print(party["pName"])
                print(line)
                for y in tDistribution:
                    y["pBallot"] = (chosenlistlPresi)
                ballots()
        for y in tDistribution:
            y["pBallot"].append(chosenlistlPresi)
        print(line)
        print("Presidential ballot paper:")
        for party in chosenlistlPresi:
                print(party["pName"])
        print(line)
        createPballot(politicalP)
    else:
        print(line)
        print("Please, first create province")
        print(line)
        admMenu()

def modifyPballot(chosenlistlPresi, listPresi):
    if len(chosenlistlPresi) > 0:
        finish = "1"
        listPresi.clear()
        for a in politicalP:
            if a not in chosenlistlPresi:
                listPresi.append(a)
        try:
            print(line)
            modify = int(input("1-Delete party" + "\n" + "2-Add party"))  # DELETE THE PARTY IN THE BALLOT
        except ValueError:
            print(line)
            print("Invalid Option")
            print(line)
            modifyPballot(chosenlistlPresi, listPresi)
        if modify == 1:
            while finish == "1":
                if len(chosenlistlPresi)>0:
                    ppchosen = []
                    x = 1
                    for ppBCH in chosenlistlPresi:
                        partyID = {"id": x, "name": ppBCH["pName"]}
                        ppchosen.append(partyID)
                        x += 1
                    print(line)
                    print("Political parties")
                    for x in ppchosen:
                        print(str(x["id"]) + "." + x["name"])
                    try:
                        delete = int(input("Type the number of the political party that you want to delete"))
                        print(line)
                    except ValueError:
                        print("Invalid Option")
                        modifyPballot(chosenlistlPresi, listPresi)

                    if len(chosenlistlPresi)<delete:

                        print("Invalid Option")
                        print(line)
                    finish = input("Do you want to delete another?"+"\n"+
                            "1-YES"+"\n"+
                            "2-NO")
                    i = 0
                    for partydelete in ppchosen:
                        if str(delete) == str(partydelete["id"]):
                            listPresi.append(chosenlistlPresi[i])
                            chosenlistlPresi.remove(chosenlistlPresi[i])
                        i = i + 1
                    print(line)
                else:
                    print(line)
                    print("Without available parties")
                    break
            for y in tDistribution:
                y["pBallot"].clear()
                y["pBallot"].append(chosenlistlPresi)
            print("The modify president ballot paper:")
            for x in chosenlistlPresi:
                print(x["pName"])
            print(line)

        elif modify == 2:  # ADD A NEW PARTY IN THE BALLOT
            finish="1"
            while finish == "1":
                if len(listPresi) > 0:
                    x = 1
                    ppballot = []
                    for party in listPresi:
                        partyID = {"id": x, "name": party["pName"]}
                        ppballot.append(partyID)
                        x += 1
                    print(line)
                    print("Type the number of the political party that you want to add")
                    for parties in ppballot:
                        print(str(parties["id"]) + "." + parties["name"])
                    try:
                        add = int(input())
                    except ValueError:
                        print(line)
                        print("Invalid Option")
                        print(line)
                        modifyPballot(chosenlistlPresi, listPresi)
                    if add>len(listPresi):
                        print(line)
                        print("Invalid Option")
                        print(line)

                    finish = input("Do you want to add other"+"\n"+
                            "1-YES"+"\n"+
                            "2-NO")
                    i = 0
                    for x in ppballot:
                        if str(add) == str(x["id"]):
                            chosenlistlPresi.append(listPresi[i])
                            listPresi.remove(listPresi[i])

                        i = i + 1
                    print(line)
                else:
                    print(line)
                    print("Without available political partys ")
                    print(line)
                    break
            for y in tDistribution:
                y["pBallot"].clear()
                y["pBallot"].append(chosenlistlPresi)
            print("The modify president ballot paper:")
            for x in chosenlistlPresi:
                print(x["pName"])
            print(line)
        else:
            print(line)
            print("Invalid Option")
            print(line)
            modifyPballot(chosenlistlPresi,listPresi)


    else:
        print(line)
        print("Without available ballot paper")

def deletePballot(chosenlistlPresi,listPresi):
    if len(chosenlistlPresi) > 0:
        print(line)
        deleteChosenPoliticalParties = input("Do you want to delete de ballot paper?"+"\n"+
                           "1-YES"+"\n"+
                           "2-NO")
        if deleteChosenPoliticalParties == "1":
            for x in chosenlistlPresi:
                listPresi.append(x)
            chosenlistlPresi.clear()
            for y in tDistribution:
                y["pBallot"].clear()
            print(line)
            print("Successfully deleted")
            print(line)
        elif deleteChosenPoliticalParties=="2":
            print(line)
            print("it was not deleted")
            print(line)
        else:
            print(line)
            print("Invalid option")
            print(line)
    else:
        print(line)
        print("Without available ballot paper")
        print(line)

def ballots():
    createPballot(politicalP)
    print("Ballots")
    ballots()

def ballotsLegis(tDistribution):
    if len(tDistribution)>0:
        print("Select the province")
        x=1
        prList=[]
        for Pl in tDistribution:
            idProvi={"id":x,"name":Pl["province"]}
            prList.append(idProvi)
            x+=1
        for partido in prList:
            print(str(partido["id"])+"."+partido["name"])
        x=0
        x=len(prList)+1
        print(str(x)+"."+"Exit")
        try:
            province=int(input())
            print(line)
        except ValueError:
            print(line)
            print("Invalid Option")
            print(line)
        if len(prList)+1<province:
            print(line)
            print("Invalid Option")
            print(line)
            ballotsLegis(tDistribution)
        if province==len(prList)+1:
            admMenu()
        i=0
        for cont in prList:
            if str(province) == str(cont["id"]):

                while i < len(prList):
                    option = input("Legislative ballot paper" + "\n" +
                                   "1.Create a new ballot paper" + "\n" +
                                   "2.Modify ballot paper" + "\n" +
                                   "3.Delete ballot paper" + "\n" +
                                   "4.See the ballot" + "\n" +
                                   "5.Exit "+ "\n")
                    if option == "1":  # CREATE NEW BALLOT#
                        if len(tDistribution[i]["lBallot"]) <= 0:
                            createLballots(politicalP,i)
                        else:
                            print("Already exist")
                    elif option=="2":
                        if len(tDistribution[i]["lBallot"]) > 0:
                            modifyLballots(tDistribution,i)
                        else:
                            print(line)
                            print("Without ballot")
                            print(line)
                            del tDistribution[i]["lBallot"]

                    elif option=="3":
                        print(line)
                        if len(tDistribution[i]["lBallot"]) > 0:
                            deleteLballot(tDistribution,i)
                        else:
                            print("Without ballot")
                            print(line)
                    elif option=="4":
                        print(line)
                        if len(tDistribution[i]["lBallot"]) > 0:

                            for x in tDistribution[i]["lBallot"]:
                                print(x["pName"])
                            print(line)
                        else:
                            print("Without ballot")
                            print(line)

                    ballotsLegis(tDistribution)
                else:
                    admMenu()
            i+=1
        admMenu()
    else:
        print("Without province")
        print(line)
        admMenu()

def createLballots(politicalP,i):
    listLegist=[]
    chosenlistLegist=[]
    for list in politicalP:
        listLegist.append(list)
    finish = "1"
    while finish == "1":
        if len(listLegist) > 0:
            plballot = []
            x = 1
            for ppoliticalballo in listLegist:
                partyID = {"id": x, "name": ppoliticalballo["pName"]}
                plballot.append(partyID)
                x += 1
            print(line)
            print("The options are:")
            for parties in plballot:
                print(str(parties["id"]) + "." + parties["name"])

            try:
                print(line)
                optionb = int(input("Choose the party you want to add: "))

            except ValueError:
                print("Invalid Option")
                print(line)
                createPballotS(politicalP,listLegist)
            if optionb>len(plballot):
                print("Invalid Option")

            finish = input("Do you add another party "+"\n"+
                           "1-YES"+"\n"+
                           "2-NO"+"\n")

            a=0
            for party in plballot:
                if str(optionb) == str(party["id"]):
                    chosenlistLegist.append(listLegist[a])
                    listLegist.remove(listLegist[a])
                a += 1
        else:
            print(line)
            print("Without available parties")
            tDistribution[i]["lBallot"].clear()
            break

    print(line)

    print("Legislative ballot paper:")
    for party in chosenlistLegist:
        tDistribution[i]["lBallot"].append(party)
        print(party["pName"])
    print(line)
    ballotsLegis(tDistribution)

def modifyLballots(tDistribution,i):
    listLegist=[]
    chosenlistLegist=[]
    for x in tDistribution[i]["lBallot"]:
        chosenlistLegist.append(x)
    if len(tDistribution[i]["lBallot"]) > 0:
        print(line)
        try:
            print(line)
            modify = input("1.Delete party" + "\n" + "2.Add party")  # DELETE THE PARTY IN THE BALLOT
        except ValueError:
            print("Invalid Option")
            modifyLballots(tDistribution, i)
        finish = "1"
        if modify == "1":
            while finish == "1":
                if len(chosenlistLegist) > 0:
                    x=1
                    casa=[]
                    a=0
                    for pl in chosenlistLegist:
                        part={"id":x,"name":pl["pName"]}
                        casa.append(part)
                        x+=1
                        a+=1
                    for c in casa:
                        print(str(c["id"]) + "." + c["name"])

                    try:
                        delete = int(input("Type the number of the political party that you want to delete"))
                    except ValueError:
                        print("Invalid Option")
                        modifyLballots(tDistribution, i)
                    print(line)
                    finish = input("Do you want to delete another?" + "\n" +
                                   "1-YES" + "\n" +
                                   "2-NO"+ "\n")
                    print(line)
                    a=0
                    for partydelete in casa:
                        if str(delete) == str(partydelete["id"]):
                            chosenlistLegist.remove(chosenlistLegist[a])
                        a = a + 1
                        tDistribution[i]["lBallot"].clear()
                        for x in chosenlistLegist:
                            tDistribution[i]["lBallot"].append(x)
                else:
                    chosenlistLegist.clear()
                    tDistribution[i]["lBallot"].clear()
                    print(line)
                    print("Whitout available ballot")
                    break
            print("The modify Legislative ballot paper:")

            for x in chosenlistLegist:
                print(x["pName"])
            print(line)

        elif modify=="2":
            listLegist=[]

            for a in politicalP:
                if a not in chosenlistLegist:
                    listLegist.append(a)
            finish="1"
            while finish == "1":
                print("Select the party")
                plch=[]
                x=1
                for y in listLegist:
                    part = {"id": x, "name": y["pName"]}
                    plch.append(part)
                    x+=1
                for c in plch:
                    print(str(c["id"])+"."+c["name"])
                try:
                    add=int(input())
                except ValueError:
                    print("Invalid Option")
                    modifyLballots(tDistribution, i)

                a=0
                for party in plch:
                    if str(party["id"])==str(add):
                        chosenlistLegist.append(listLegist[a])
                        listLegist.remove(listLegist[a])
                    a+=1

                finish = input("Do you want add other 1-Yes/2-No")
            print(line)
            print("The modify ballot")
            for x in chosenlistLegist:
                print(x["pName"])
            tDistribution[i]["lBallot"].clear()
            tDistribution[i]["lBallot"].append(chosenlistLegist)

def deleteLballot(tDistribution,i):
    delete=input("Do you want delete Legislaive ballot? 1-Yes/2-No")
    if delete=="1":
        tDistribution[i]["lBallot"].clear()

#######################################################################################################################

def consults ():
# (This method counts the total of votes of the presidential ballot in all provinces)##############################
    totalVotes = 0
    i=0
    while len(tDistribution) > i:
        nCantons = 0
        while len(tDistribution[i]["cantons"]) > nCantons:
            nDistricts = 0
            while len(tDistribution[i]["cantons"][nCantons]["district"]) > nDistricts:
                ballot = 0
                votes = 0
                while len(tDistribution[i]["cantons"][nCantons]["district"][nDistricts]["pBallot"])> ballot:
                    totalVotes+=tDistribution[i]["cantons"][nCantons]["district"][nDistricts]["pBallot"][votes]["votes"]
                    ballot+=1
                    votes +=1
                nDistricts+=1
            nCantons+=1
        i+=1
    print(line)
    print("TOTAL VOTES = "+str(totalVotes))
    print(line)
    mConsults = input("1. Consult National Elections Results"+"\n"+
                        "2. Consult Natinoal Election Results By Province"+"\n"+
                        "3. Consult Natinoal Election Results By Cantons"+"\n"+
                        "4. Consult Natinoal Election Results By Districts"+"\n"+
                        "5. Back"+"\n" )
    if mConsults == "1":
        consultNational(totalVotes)
    elif mConsults == "2":
        print("Provinces")
        consults()
    elif mConsults == "3":
        print("Cantons")
    elif mConsults == "4":
        consultDistrict()
    elif mConsults == "5":
        admMenu()

def consultDistrict():                                     # Consult N4 Sort by Districts
    totalsVotes = []
    partyVotes = []
    disVotes = 0
    i = 0
    while len(tDistribution) > i:
        nCantons = 0
        while len(tDistribution[i]["cantons"]) > nCantons:
            nDistricts = 0
            while len(tDistribution[i]["cantons"][nCantons]["district"]) > nDistricts:
                ballot = 0
                while len(tDistribution[i]["cantons"][nCantons]["district"][nDistricts]["pBallot"]) > ballot:
                    x = len(tDistribution[i]["cantons"][nCantons]["district"][nDistricts]["pBallot"]) - 1                            #this method adds the total of votes
                    while x >= 0:                                                                                                     #in each district to a list
                        disVotes += tDistribution[i]["cantons"][nCantons]["district"][nDistricts]["pBallot"][x]["votes"]
                        x -= 1
                        ballot += 1
                    totalsVotes.append(disVotes)
                    disVotes = 0
                nDistricts += 1
            nCantons += 1
        i += 1
    i = 0
    while len(tDistribution) > i:
        nCantons = 0
        while len(tDistribution[i]["cantons"]) > nCantons:
            nDistricts = 0
            while len(tDistribution[i]["cantons"][nCantons]["district"]) > nDistricts:
                ballot = 0                                                                                                                 #this method adds the results of eachs
                while len(tDistribution[i]["cantons"][nCantons]["district"][nDistricts]["pBallot"]) > ballot:                                 #district to a list
                    parties = len(tDistribution[i]["cantons"][nCantons]["district"][nDistricts]["pBallot"])
                    x = 0
                    while parties > x:
                        partyVotes.append(tDistribution[i]["cantons"][nCantons]["district"][nDistricts]["pBallot"][x])
                        x += 1
                        ballot += 1
                nDistricts += 1
            nCantons += 1
        i += 1
    i = 0
    totalVotesIndex = 0
    partiesVotesIndex = 0
    while len(tDistribution) > i:
        nCantons = 0
        print(line)
        print(tDistribution[i]["province"])
        while len(tDistribution[i]["cantons"]) > nCantons:
            nDistricts = 0
            print("   " + tDistribution[i]["cantons"][nCantons]["canton"])
            while len(tDistribution[i]["cantons"][nCantons]["district"]) > nDistricts:
                x = 0
                print("      " + tDistribution[i]["cantons"][nCantons]["district"][nDistricts]["district"])
                parties = len(tDistribution[i]["cantons"][nCantons]["district"][nDistricts]["pBallot"])
                while parties > x:
                    nBallots = len(tDistribution[i]["cantons"][nCantons]["district"][nDistricts]["pBallot"])
                    while nBallots > 0:
                        tVotesDis = (round(partyVotes[partiesVotesIndex]["votes"] * 100 / totalsVotes[totalVotesIndex]))
                        nBallots-=1
                    print("             " + partyVotes[partiesVotesIndex]["pName"] + " votes: " + str(partyVotes[partiesVotesIndex]["votes"])+" = "+str(tVotesDis)+"%")
                    partiesVotesIndex += 1
                    x += 1
                nDistricts += 1
                totalVotesIndex += 1
            nCantons += 1
        i += 1
    print(line)
    consults()

def consultNational(totalVotes):
    print("=NATIONAL ELECTION RESULTS=")
    partyVotes=[]
    nationalElectionsParties =[]
    votesReceived = []
    i = 0
    while len (chosenlistlPresi)>i:
        nationalElectionsParties.append(chosenlistlPresi[i]["pName"])
        i+=1
    i = 0
    while len(tDistribution) > i:
        nCantons = 0
        while len(tDistribution[i]["cantons"]) > nCantons:
            nDistricts = 0
            while len(tDistribution[i]["cantons"][nCantons]["district"]) > nDistricts:
                ballot = 0
                while len(tDistribution[i]["cantons"][nCantons]["district"][nDistricts]["pBallot"]) > ballot:
                    parties = len(tDistribution[i]["cantons"][nCantons]["district"][nDistricts]["pBallot"])
                    x = 0
                    while parties > x:
                        partyVotes.append(tDistribution[i]["cantons"][nCantons]["district"][nDistricts]["pBallot"][x])
                        x += 1
                        ballot += 1
                nDistricts += 1
            nCantons += 1
        i += 1
    nVotes = 0
    while nVotes  < len(nationalElectionsParties):
        votesReceived.append(0)
        nVotes+=1
    i+=1
    i = 0
    z = 0
    while (len(partyVotes)/len(nationalElectionsParties))> i:
        nVotes = 0
        while nVotes < len(nationalElectionsParties):
            votesReceived[nVotes]+=partyVotes[z]["votes"]
            nVotes += 1
            z+=1
        i += 1
    i = 0
    while parties > i:
        print(nationalElectionsParties[i]+" votes: "+str(votesReceived[i])+" = "+str((votesReceived[i]*100)/totalVotes)+"%")
        i+=1
    print(line)
    consults()


#######################################################################################################################

def validation(x,y):                                                         #This method verify if any field is empty
    while len(x) == 0:
        x = input("This field is required "+"\n"+y)
    return (x)

def intValidation(num,message):
    try:
        num = int(num)
    except ValueError:
        num = input("Only numbers"+"\n"+message)
        num = intValidation(num,message)
    return int(num)


mainMenu()
