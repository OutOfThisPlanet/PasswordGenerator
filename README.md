# PasswordGenerator
Generates a password, then outputs it, or a reversed version of it. 
```
Function GeneratePassword
{
    cls
    $MinimumPasswordLength = 12
    $MaximumPasswordLength = 16
    $PasswordLength = Get-Random -InputObject ($MinimumPasswordLength..$MaximumPasswordLength)
    $AllowedPasswordCharacters = [char[]]'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789!?@#£$%^&'
    $Regex = "(?=.*\d)(?=.*[a-z])(?=.*[A-Z])(?=.*\W)"

    do {
            $Password = ([string]($AllowedPasswordCharacters | 
            Get-Random -Count $PasswordLength) -replace ' ')
       }    until ($Password -cmatch $Regex)

    Get-Random -InputObject ($Password, ($Password[-1..-($Password.length)] -join ""))

}

GeneratePassword
```
