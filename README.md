# Windows10_Consolas

My first idea is to solve Chinese charactor display following the guideline:  
https://shajisoft.com/shajisoft_wp/fontlink-for-cjk-on-english-windows-10/ 

To conclusion, set up fontlink for consolas with one-line command:  
```
REG ADD "HKLM\Software\Microsoft\Windows NT\CurrentVersion\Fontlink\SystemLink" /v Consolas /t REG_MULTI_SZ /d "MSYH.TTC,Microsoft YaHei UI,128,96"\0"MSYH.TTC,Microsoft YaHei UI"\0"Arial.TTF,Arial"
pause
```

Furthermore, I think Consolas is also a good font for default Windows 10 GUI. So I reached lanceon on gist:   
https://gist.github.com/lanceon/57a5b03a7e12b0538277  

in short:  
Consolas.reg  
```
Windows Registry Editor Version 5.00

;Remove Segoe UI
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Fonts]

"Segoe UI (TrueType)"=""
"Segoe UI Bold (TrueType)"=""
"Segoe UI Italic (TrueType)"=""
"Segoe UI Bold Italic (TrueType)"=""
"Segoe UI Semibold (TrueType)"=""
"Segoe UI Light (TrueType)"=""

;Font Substitution
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\FontSubstitutes]

"Segoe UI"="Consolas"
```
NOTE1: No need to replace more register items. windows 10 failed to boot when I set every Segoe items into empty.   
NOTE2: Do not replace Segoe UI Symbol (TrueType), or num-pad for PIN code screen will display error on touchscreen.  

SegoeUI.reg
```
Windows Registry Editor Version 5.00

;Restore Segoe UI

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Fonts]

"Segoe UI (TrueType)"="segoeui.ttf"
"Segoe UI Bold (TrueType)"="segoeuib.ttf"
"Segoe UI Italic (TrueType)"="segoeuii.ttf"
"Segoe UI Bold Italic (TrueType)"="segoeuiz.ttf"
"Segoe UI Semibold (TrueType)"="seguisb.ttf"
"Segoe UI Light (TrueType)"="segoeuil.ttf"

;Remove Font Substitution
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\FontSubstitutes]

"Segoe UI"=-
```
