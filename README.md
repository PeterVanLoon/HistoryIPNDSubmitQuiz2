# IPNDSubmitQuiz2
Udacity IPND Quiz for Section Two
# List of words that designeate blanks to be filled in by the quiz taker 
blanks  = ["___1___" ,"___2___", "___3___" ,"___4___" ,"___5___"]

# Here is a simple quiz
easy_quiz = "The first person responsible for emergency management is ___1___.  \
Emergency management is not about buying things, but doing the valid ___2___ and \
vulnerability ___3___."
answer_easy=["AAAA","BBBB","CCCC"] 

medium_quiz = "The first person is total  ___1___.  \
Emergency management does the valid ___2___ and \
appropriate ___3___."
answer_medium=["DDDD","EEEE","FFFF"]

hard_quiz = "The first person eats   ___1___.  \
Emergency management sucks ___2___ and \
appropriately discharges ___3___."
answer_hard=["XXXX","YYYY","ZZZZ"]




# Checks if a word in quiz_string is a substring of the word passed in.
def word_in_blanks(word, quiz):
    for blank in quiz:
        if blank in word:
            print blank
            return blank
    return None
        
def quizchoice():
    quizrequest= raw_input("Choose a quiz; Easy, Medium, or Hard: ") #Gets a choice from the user
    #all below figures out which quiz to use based on what people input
    if quizrequest == "Easy":
        quizchosen=easy_quiz
        answer=answer_easy
    elif quizrequest=="Medium":
        quizchosen=medium_quiz
        answer=answer_medium
    elif quizrequest=="Hard":
        quizchosen=hard_quiz
        answer=answer_hard
    else:    
        print "Easy, Medium, or Hard are your choices"
        #I need to figure out a way to cycle back through the options if the right options are not used.
        #It works fine as long as people enter the exact option.  
    print quizchosen
    print answer#I get the right answer set assigned for the level chosen.  I can see it when this statement prints.
    return quizchosen# It goes to FITBQuiz because I can print it out as soon as it gets there
    return answer # I tried printing this just like 'quizchosen' from within
            #FITBQuiz, but it will not print.  that print rquest is errored out
            #below, and that keeps me from getting the Global name 'answer' is not
            #defined.  


# Goes through the quiz.  
def FITBQuiz(quizchosen,answer_blanks):
    print quizchosen#I get this from quizchoice() above with no problem
    #I print it out just to see that I am picking up the actual correct 
    #chosen quiz
    #print answer# I get quizchosen, but I cannot get the right 'answer'
    #I get that the global name 'answer' is not defined.  However, I got 
    #quizchosen just great.  
    replaced = [] #Initiates the string that will be the quiz
    quizchosen = quizchosen.split()#Takes the Quiz(First, Second, Third)
    for word in quizchosen:
        replacement = word_in_blanks(word, answer_blanks)
        if replacement != None:
            user_input = raw_input("Give an answer - what should be in  " + replacement + "? ")         
            #in here, I have to develeop a function that takes what is answered, and chekcs to see if
            #that answer, user_input, is the right answer.  If it is, I can let return user_input.
            #If it is not the right answer, I need to figure out how to get them to try again.
            #I will call this function: Check_Answer., and compare the user input to the answer list
            word = word.replace(replacement, user_input)
            replaced.append(word)
        else:
            replaced.append(word)
    replaced = " ".join(replaced)
    return replaced
