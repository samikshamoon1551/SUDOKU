# SUDOKU
#SUDOKU PUZZLE
#To take input from user:


def userinput():
    row,col=input("Enter Row and Column: ").split()
    r=int(row)-1
    c=int(col)-1
   
   
   #User should no be able to modify clue cells...Thus accept only empty cell values:
    if ((r==0 and c==0) or (r==0 and c==1) or (r==0 and c==4) or (r==1and c==0) or (r==1 and c==3) or (r==1 and c==4)or (r==1 and c==5) or (r==2 and c==1) or (r==2 and c==2) or (r==2 and c==7)or (r==3 and c==0) or (r==3 and c==4) or (r==3 and c==8)or (r==4 and c==0) or (r==4 and c==3) or (r==4 and c==5) or (r==4 and c==8)or (r==5 and c==0)or (r==5 and c==4)or (r==5 and c==8) or (r==6 and c==1) or (r==6 and c==6) or (r==6 and c==7)or (r==7 and c==3) or (r==7 and c==4)or (r==7 and c==5)or (r==7 and c==8)or (r==8 and c==4) or (r==8 and c==7) or (r==8 and c==8)):
        print("Invalid! Enter Empty cell parameters ")
        userinput()   #GO back to take userinput for row and column
    else:
        e = int(input("Enter Element: "))
        checkrow(r, c, e)


#To check repeatition in row:


def checkrow(r,c,e):
    count1=0
    for x in range(9):
        if grid[r][x]==e:
            print("Invalid! Reapeation in Row!!!")
        else:
            count1=count1+1
    if count1>0:
        checkcol(r,c,e)
#To check repeatition in column:
def checkcol(r,c,e):
    count2=0
    for y in range(9):
        if grid[y][c]==e:
            print("Invalid! Reapeation in Column!!!")
        else:
            count2=count2+1
    if count2>0:
        checkblock(r,c,e)


#To check Repeatition in 3 X 3 blocks:


def checkblock(r,c,e):
    count3=0
    if r==0 or r==1 or r==2:
       if c==0 or c==1 or c==2:
          for x in range(0,3,1):
             for y in range(0,3,1):
                if grid[x][y]==e:
                   print("Invalid! Reapeation in Block1!!!")
                   count3+=1
                   userinput()    #Again take userinput

       elif c==3 or c==4 or c==5:
          for x in range(0, 3, 1):
              for y in range(3,6,1):
                  if grid[x][y] == e:
                      print("Invalid! Reapeation in Block2!!!")
                      count3 = count3 + 1
                      userinput()    #Again take userinput
       elif c==6 or c==7 or c==8:
          for x in range(0, 3, 1):
              for y in range(6,9,1):
                  if grid[x][y] == e:
                      print("Invalid! Reapeation in Block3!!!")
                      count3 = count3 + 1
                      userinput()    #Again take userinput
       if count3==0:
           execute(r,c,e)    #If the userentry(or the userinput) does not repeat in corresponding Row, Column or 3 X 3 Block, Print the modified grid:
       else:
           userinput()

    elif r==3 or r==4 or r==5:
        if c == 0 or c==1 or c==2:
            for x in range(3, 6, 1):
                for y in range(0, 3, 1):
                    if grid[x][y] == e:
                        print("Invalid! Reapeation in Block4!!!")
                        count3 = count3 + 1
                        userinput()   #Again take userinput
        elif c == 3 or c==4 or c==5:
            for x in range(3, 6, 1):
                for y in range(3, 6, 1):
                    if grid[x][y] == e:
                        print("Invalid! Reapeation in Block5!!!")
                        count3 = count3 + 1
                        userinput()    #Again take userinput
        elif c == 6 or c== 7 or c==8:
            for x in range(3, 6, 1):
                for y in range(6, 9, 1):
                    if grid[x][y] == e:
                        print("Invalid! Reapeation in Block6!!!")
                        count3 = count3 + 1
                        userinput()    #Again take userinput
        if count3 == 0:
            execute(r,c,e)   #If the userentry(or the userinput) does not repeat in corresponding Row, Column or 3 X 3 Block, Print the modified grid:
        else:
            userinput()
    elif r==6 or r==7 or r==8:
        if c == 0 or c==1 or c==2:
            for x in range(6, 9, 1):
                for y in range(0, 3, 1):
                    if grid[x][y] == e:
                        print("Invalid! Reapeation in Block7!!!")
                        count3 = count3 + 1
                        userinput()   #Again take userinput
        elif c == 3 or c==4 or c==5:
            for x in range(6, 9, 1):
                for y in range(3, 6, 1):
                    if grid[x][y] == e:
                        print("Invalid! Reapeation in Block8!!!")
                        count3 = count3 + 1
                        userinput()   #Again take userinput
        elif c == 6 or c==7 or c==8:
            for x in range(6, 9, 1):
                for y in range(6, 9, 1):
                    if grid[x][y] == e:
                        print("Invalid! Reapeation in Block9!!!")
                        count3 = count3 + 1
                        userinput()    #Again take userinput
        if count3 == 0:
            execute(r,c,e)  #If the userentry(or the userinput) does not repeat in corresponding Row, Column or 3 X 3 Block, Print the modified grid:
        else:
            userinput()   #Again take userinput


#If the userentry(or the userinput) does not repeat in corresponding Row, Column or 3 X 3 Block, Print the modified grid:


def execute(r,c,e):
    grid[r][c] = e
    for i in range(9):
        for j in range(9):
            print("|", grid[i][j], "|", end="  ")
        print()
    if grid==stdgrid:
        print("CONGRATULATIONS!!! YOU WIN!!!")   #If all the cells are filled correctly, Print the corresponding message
    else:
        userinput()   #If not, Again take the userinput


#Start from here:

#Define a standard grid as answer to Sudoku puzzle:

stdgrid=[[5,3,4,6,7,8,9,1,2],[6,7,2,1,9,5,3,4,8],[1,9,8,3,4,2,5,6,7],[8,5,9,7,6,1,4,2,3],[4,2,6,8,5,3,7,9,1],[7,1,3,9,2,4,8,5,6],[9,6,1,5,3,7,2,8,4],[2,8,7,4,1,9,6,3,5],[3,4,5,2,8,6,1,7,9]]
#Display Sudoku puzzle with clues and empty cells:
grid=[[5,3,"_","_",7,"_","_","_","_"],[6,"_","_",1,9,5,"_","_","_"],["_",9,8,"_","_","_","_",6,"_"],[8,"_","_","_",6,"_","_","_",3],[4,"_","_",8,"_",3,"_","_",1],[7,"_","_","_",2,"_","_","_",6],["_",6,"_","_","_","_",2,8,"_"],["_","_","_",4,1,9,"_","_",5],["_","_","_","_",8,"_","_",7,9]]

for i in range(9):
    for j in range(9):
        print("|",grid[i][j],"|",end="")
    print()
userinput()      #Go to userinput() function
