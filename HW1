#by Wei Qiang
#Missionary-Cannibal Problem
'''
In the missionaries and cannibals problem, three missionaries and three cannibals must cross a river using a boat which can carry at most two people,
under the constraint that, for both banks, if there are missionaries present on the bank,
they cannot be outnumbered by cannibals (if they were, the cannibals would eat the missionaries).
The boat cannot cross the river by itself with no people on board.
'''


#State = {Cannibals, Missionaries, Side}

illegalState = 0
repeatedState = 0
other = 0
state = [3,3,"L"]
stateArray = []
stateArray.append(state)


#tell if the state is a dead state, a dead state inclues when the cannibals eat the missionaries
def ifDead(state):
    if state[0] > state[1] and state[1] > 0:
        return True
    elif 3 - state[0] > 3 - state[1] and 3 - state[1] > 0:
        return True
    else:
        return False


#tell if the state is an repeated state, a repeted state will not count as a new solution.
def ifRepeat(state):
    global stateArray
    for s in stateArray:
        if state[0] == s[0] and state[1] == s[1] and state[2] == s[2]:
            return True
    return False


'''
change of the state{Cannibals, Missionaries, Side}
type of change
1-<1,0>
2-<2,0>
3-<0,1>
4-<0,2>
5-<1,1>
'''
def change(state,type):
    if(state[2] == "L"):
        state[2] = "R"
        if type == 1:
            state[0] -= 1
        elif type == 2:
            state[0] -= 2
        elif type == 3:
            state[1] -= 1
        elif type == 4:
            state[1] -= 2
        elif type == 5:
            state[1] -= 1
            state[0] -= 1
    elif state[2] == "R":
        state[2] = "L"
        if type == 1:
            state[0] += 1
        elif type == 2:
            state[0] += 2
        elif type == 3:
            state[1] += 1
        elif type == 4:
            state[1] += 2
        elif type == 5:
            state[1] += 1
            state[0] += 1







#explore the  with current state and the track of the state
def solve(state,statearray):
    global illegalState
    global other
    global repeatedState

    if state == [0,0,"R"]:  #no people left
        for s in statearray:
            print "(" + str(s[0]) + "," + str(s[1]) +  "," + str(s[2]) +")",

        print

    else:
        for i in range(1,6):
            newstate = list(state)
            change(newstate,i)
            if(newstate[0] >= 0 and newstate[1] >= 0 and newstate[0] <= 3 and newstate[1] <= 3):
                if(not ifDead(newstate)):
                    if ifRepeat(newstate):
                        repeatedState += 1
                    else:
                        other += 1
                        statearray.append(newstate)
                        solve(newstate,statearray)
                        del statearray[len(statearray) - 1]
                else:
                    illegalState += 1




solve(state,stateArray)
print("Dead state " + str(illegalState))
print("Repeated state " + str(repeatedState))
print("normal state " + str(other))






