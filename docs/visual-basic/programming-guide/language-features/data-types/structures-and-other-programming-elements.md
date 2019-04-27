---
title: 結構和其他程式設計項目 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], arrays
- procedures [Visual Basic], structures as arguments to
- objects [Visual Basic], structure elements
- arrays [Visual Basic], structure elements
- nested structures [Visual Basic]
ms.assetid: 0f849313-ccd2-4c9a-acb9-69de6751c088
ms.openlocfilehash: a943bbdec617ba6c95685df3a4fcdb36b52def22
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61906447"
---
# <a name="structures-and-other-programming-elements-visual-basic"></a>結構和其他程式設計項目 (Visual Basic)
您可以使用結構搭配使用陣列、 物件和程序，以及彼此。 因為這些項目使用個別的互動會使用相同的語法。  
  
> [!NOTE]
>  您無法初始化任何在結構宣告中的結構項目。 您只能指派值給變數已宣告為結構類型的項目。  
  
## <a name="structures-and-arrays"></a>結構和陣列  
 結構包含一個或多個子項目陣列。 下列範例將說明這點。  
  
```vb  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As String  
    Public purchaseDate As Date  
End Structure   
```  
  
 存取陣列在結構中的值相同的方式存取物件的屬性。 下列範例將說明這點。  
  
```vb  
Dim mySystem As systemInfo  
ReDim mySystem.diskDrives(3)  
mySystem.diskDrives(0) = "1.44 MB"  
```  
  
 您也可以宣告結構的陣列。 下列範例將說明這點。  
  
```vb  
Dim allSystems(100) As systemInfo  
```  
  
 您遵循相同的規則，來存取此資料架構的元件。 下列範例將說明這點。  
  
```vb  
ReDim allSystems(5).diskDrives(3)  
allSystems(5).CPU = "386SX"  
allSystems(5).diskDrives(2) = "100M SCSI"  
```  
  
## <a name="structures-and-objects"></a>結構和物件  
 結構包含一個或多個子項目物件。 下列範例將說明這點。  
  
```vb  
Protected Structure userInput  
    Public userName As String  
    Public inputForm As System.Windows.Forms.Form  
    Public userFileNumber As Integer  
End Structure  
```  
  
 您應該使用特定的物件類別，在這類宣告中，而非`Object`。  
  
## <a name="structures-and-procedures"></a>結構和程序  
 您可以傳遞結構做為程序引數。 下列範例將說明這點。  
  
```vb  
Public currentCPUName As String = "700MHz Pentium compatible"  
Public currentMemorySize As Long = 256  
Public Sub fillSystem(ByRef someSystem As systemInfo)  
    someSystem.cPU = currentCPUName  
    someSystem.memory = currentMemorySize  
    someSystem.purchaseDate = Now  
End Sub  
```  
  
 上述範例中將結構傳遞*傳址*，可讓程序來修改其項目，讓呼叫端程式碼中所做的變更才會生效。 如果您想要保護對這類修改的結構，傳值方式傳遞。  
  
 您也可以傳回結構，以從`Function`程序。 下列範例將說明這點。  
  
```vb  
Dim allSystems(100) As systemInfo  
Function findByDate(ByVal searchDate As Date) As systemInfo  
    Dim i As Integer  
    For i = 1 To 100  
        If allSystems(i).purchaseDate = searchDate Then Return allSystems(i)  
    Next i  
   ' Process error: system with desired purchase date not found.  
End Function  
```  
  
## <a name="structures-within-structures"></a>結構內的結構  
 結構可以包含其他結構。 下列範例將說明這點。  
  
```vb  
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
  
```vb  
Dim allSystems(100) As systemInfo  
ReDim allSystems(1).diskDrives(3)  
allSystems(1).diskDrives(0).type = "Floppy"  
```  
  
 您也可以使用這項技術來封裝在不同的模組中定義的結構內的其中一個模組中定義的結構。  
  
 結構可以包含其他結構到任意深度。  
  
## <a name="see-also"></a>另請參閱

- [資料類型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [基礎資料類型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [複合資料類型](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [結構](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [資料類型的疑難排解](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [如何：宣告結構](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [結構變數](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)
- [結構和類別](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [Structure 陳述式](../../../../visual-basic/language-reference/statements/structure-statement.md)
