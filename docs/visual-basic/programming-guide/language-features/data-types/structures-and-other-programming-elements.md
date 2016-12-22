---
title: "Structures and Other Programming Elements (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "structures, arrays"
  - "procedures, structures as arguments to"
  - "objects [Visual Basic], structure elements"
  - "arrays [Visual Basic], structure elements"
  - "nested structures"
ms.assetid: 0f849313-ccd2-4c9a-acb9-69de6751c088
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Structures and Other Programming Elements (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

結構可與陣列、物件及程序彼此結合使用。  這些項目之間互動所使用的語法與其個別使用的語法相同。  
  
> [!NOTE]
>  您無法在結構宣告中初始化任何結構項目。  您只能將值指派給已宣告為結構型別 \(Structure Type\) 的變數項目。  
  
## 結構與陣列  
 結構可包含一個陣列做為其一個或多個元素。  下列範例將說明這點。  
  
```vb#  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As String  
    Public purchaseDate As Date  
End Structure   
```  
  
 存取結構中陣列的值，其方式與存取物件屬性的相同。  下列範例將說明這點。  
  
```vb#  
Dim mySystem As systemInfo  
ReDim mySystem.diskDrives(3)  
mySystem.diskDrives(0) = "1.44 MB"  
```  
  
 您也可以宣告結構的陣列。  下列範例將說明這點。  
  
```vb#  
Dim allSystems(100) As systemInfo  
```  
  
 您必須遵守相同的規則 \(Rule\) 以存取此資料架構的元件。  下列範例將說明這點。  
  
```vb#  
ReDim allSystems(5).diskDrives(3)  
allSystems(5).CPU = "386SX"  
allSystems(5).diskDrives(2) = "100M SCSI"  
```  
  
## 結構與物件  
 結構可包含一個物件做為一個或多個元素。  下列範例將說明這點。  
  
```vb#  
Protected Structure userInput  
    Public userName As String  
    Public inputForm As System.Windows.Forms.Form  
    Public userFileNumber As Integer  
End Structure  
```  
  
 在這類的宣告中，您應使用特定的物件類別，而非 `Object`。  
  
## 結構與程序  
 您可以將結構當做程序引數傳遞。  下列範例將說明這點。  
  
```vb#  
Public currentCPUName As String = "700MHz Pentium compatible"  
Public currentMemorySize As Long = 256  
Public Sub fillSystem(ByRef someSystem As systemInfo)  
    someSystem.cPU = currentCPUName  
    someSystem.memory = currentMemorySize  
    someSystem.purchaseDate = Now  
End Sub  
```  
  
 前述範例將結構以「*傳址方式*」\(By Reference\) 傳遞，讓程序能夠修改其元素，使變更在呼叫程式碼中產生效用。  若您不希望結構進行這類修改，則請以傳值 \(By Value\) 方式傳遞。  
  
 您也可以從 `Function` 程序傳回結構。  下列範例將說明這點。  
  
```vb#  
Dim allSystems(100) As systemInfo  
Function findByDate(ByVal searchDate As Date) As systemInfo  
    Dim i As Integer  
    For i = 1 To 100  
        If allSystems(i).purchaseDate = searchDate Then Return allSystems(i)  
    Next i  
   ' Process error: system with desired purchase date not found.  
End Function  
```  
  
## 包含在結構中的結構  
 結構中還可包含其他結構。  下列範例將說明這點。  
  
```vb#  
Public Structure driveInfo  
    Public type As String  
    Public size As Long  
End Structure  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As driveInfo  
    Public purchaseDate As Date  
End Structure  
```  
  
```vb#  
Dim allSystems(100) As systemInfo  
ReDim allSystems(1).diskDrives(3)  
allSystems(1).diskDrives(0).type = "Floppy"  
```  
  
 您也可以使用同樣的方法將一模組所定義的結構封裝到另一不同模組所定義的結構之中。  
  
 結構可以包含其他結構達任意多層。  
  
## 請參閱  
 [資料類型](../../../../visual-basic/reference/command-line-compiler/index.md)   
 [Elementary Data Types](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [How to: Declare a Structure](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)   
 [Structure Variables](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)   
 [Structures and Classes](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)   
 [Structure Statement](../../../../visual-basic/language-reference/statements/structure-statement.md)