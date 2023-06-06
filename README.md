# Tomis

## Description

    Space board game

    Uses a standard chess board and backgammon pieces.

    Game pieces (per player):
    - 1 base (king)
    - 4 inactive gates (black backgammon pieces)
    - 4 active gates (white backgammon)
    - 4 jump gates
    - 8 frigates (pawns)
    - 2 sentry (towers)
    - 2 tower (bishops)
    - 1 flagship (queen)
  
## Scope/Story

    Two fleet commanders fight a space battle
    Use the available structures and ships to defeat the enemy
    Scope is to destroy the enemy base

## Initial placement

    - Base
      - Can be placed anywhere on the back row
    - Gates
      - The inactive gates are placed first
      - One per row, one per turn, start from back row
      - At least one step away from the base
    - Frigates, sentries, towers, flagship
      - Can be placed anywhere on the back row
      - Cannot be placed directly on a gate
    - Flagship
      - Only available after any piece arrives on the back row of the enemy

## Attacks

    Attack point = ap

    AttackPoints:
      - Base has no attack points
      - Frigate,Sentries,Towers ( 1 ap )
      - Flagship ( 2 ap )

    Attack effects:
      - A stalemate is when the attacker and defender have the same aps ( no effects ) 
      - An attack will be sucessfull if number of ap is larger then the target
      - After a succesfull attack a piece is removed from the board  
    
    Frigate attacks ( 1 step ):

      \ | /
        #

    Sentry attacks:

       \ /
        #
       / \

    Tower attacks:
        |
      - # -
        |
  
    Attack examples:
      - 1 frigate vs 1 frigate => stalemate (cannot destroy each other)
      - 2 frigates vs 1 frigate => succesfull attack (2ap vs 1p)

## Actions

    - Base
    - Gate
      - Place a marker to transform the active gate into a jump gate
    - Jump Gate
      - The default jump range is 2 (horizontal,vertical or diagonal movement)
      - Rotate the marker that tells the direction of the jump
      - On a jump where the target is a jump gate, you need 2 ap to destroy the jump gate
    - Frigates
      - Move 1 step forward or to the sides (no backward movement)
      - Can attack front, left, right
      - Each frigate has one attack point
      - To take a piece you need two attack points
      - Once on a gate can choose to activate/inactivate it (Replace the pieces accordingly)
      - Gate jump:
        - Jump to the next or previous active gate (only 1 step)
        - If target gate has an enemy frigate you need 2 attacks points to capture it by gate jump
        - If target gate is inactive no jump will be performed
      - Gate strike:
        - The unit is on an active gate
        - A unit on a gate can attack on the upper/lower active gate on this possitions: x G x
        - the attacking unit is destroyed as well as the enemy
      - Jump:
        - The unit is next to a jump gate
        - A piece will move 2 steps in the direction of the marker
        - A jump will not be performed if one of the passing rows has no gate
        - To modify the direction of the marker will take one turn
        - If the ship passes 2 or more consecutive jump gates it will jump 3 steps
    - Sentries
      - Bishop like movement
    - Towers
      - Tower like movement
    - Flagship
      - Queen like movement

## Win condition

    - Game is won when the enemy base is destroyed
    - A base is destroyed when under attack by 3 pieces
