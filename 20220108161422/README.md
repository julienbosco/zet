# How to remove single quote (') in Powershell

    "Test'." -replace [char]0x0027,''

Trim() doesn't work. 0x0027 is Unicode for single quote.

    #powershell #regex

