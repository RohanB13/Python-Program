Python-Program
==============

This python program uses different statements and loops to change the input into an output

J = 1
OLIST=[] #list for the outputs

#following section prepares the output list
OLIST.append(" ")
OLIST.append("----------------------------RESULTS----------------------------")
OLIST.append(" ")
OLIST.append("TEST INPUT                                        " + "TEST OUTPUT          ")
OLIST.append(" ")

#following section gets the inputs and performs operations
for J in (1, 2, 3, 4, 5): #loop to get inputs and perform operations
    INPUT_LINE = raw_input("Please Enter Input Line "+ str(J) +" (with a comma in between): ") #asks for input from the user
   
    K = INPUT_LINE
    K = K.replace(" ","") #replaces spaces with no space
    IP1 = K[:K.rfind(",")] #gets the first part of the input
    IP2 = K[K.rfind(",")+1:] #gets the second part of the input

    if IP1.find(",") == -1 and IP1.find("$") == -1 and IP1.find("*") == -1 and IP1.find("-") == -1 :
       #print "contains only &"
       OP = IP2.rjust(len(IP1),'*')
    else:
        if IP1.find(",") <> -1 and IP1.find("$") == -1 and IP1.find("*") == -1 and IP1.find("-") == -1 :
           #print "contains ,";
           OP = IP2.rjust(len(IP1.replace(",","")),'*')
           Q = len(IP2)/3 #gets quotient
           R = len(IP2)%3 #gets remainder
           if R == 0: #if evenly divisible by 3 then reduce the quotient by 1
              Q = Q - 1
           T = -3
           while Q <> 0 :
                 OP = OP[:T] + "," + OP[T:]
                 Q = Q - 1
                 T = T - 4
        else:
            if IP1.find("$") <> -1 and IP1.find(",") == -1 and IP1.find("*") == -1 and IP1.find("-") == -1 :
               #print "contains $";
               OP = "$" + IP2
            else:
               if IP1.find("*") <> -1 and IP1.find("$") <> -1 and IP1.find(",") == -1 and IP1.find("-") == -1 :
                   #print "contains *$";
                   OP = "$" + IP2
                   N = IP1.replace("*","")
                   OP = OP.rjust(len(N.replace("$",""))+1,'*')
               else:
                   if IP1.find("-") <> -1 and IP1.find("*") == -1 and IP1.find("$") == -1 and IP1.find(",") == -1 :
                      #print "contains -";
                      if IP2.find("-") <> -1 :
                        #print "value contains -"
                        N = IP2.replace("-","")
                        OP = N.rjust(len(IP1)-1,'*') +"-"
                      else:
                        #print "value does not contain -"
                        OP = IP2.rjust(len(IP1)-1,'*') +"*"
       
    OLIST.append((str(J)+". "+INPUT_LINE).ljust(50, ' ') + str(J)+". "+OP) #adds the input and output to the output list
    OLIST.append(" ") #adds an empty line in the output list


#following section prints the output list containing the results
for item in OLIST:
    print item

raw_input()
