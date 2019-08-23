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
ms.openlocfilehash: ec65c75fcfd907097f1cd1e0d3092a547272a782
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933239"
---
# <a name="structures-and-other-programming-elements-visual-basic"></a>結構和其他程式設計項目 (Visual Basic)
您可以搭配使用結構與陣列、物件和程式, 以及彼此結合。 互動會使用與這些元素個別使用相同的語法。  
  
> [!NOTE]
> 您無法初始化結構宣告中的任何結構元素。 您只能將值指派給已宣告為結構類型之變數的元素。  
  
## <a name="structures-and-arrays"></a>結構和陣列  
 結構可以包含陣列做為它的一個或多個元素。 下列範例將說明這點。  
  
```vb  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As String  
    Public purchaseDate As Date  
End Structure   
```  
  
 在結構中存取陣列的值, 與存取物件上屬性的方式相同。 下列範例將說明這點。  
  
```vb  
Dim mySystem As systemInfo  
ReDim mySystem.diskDrives(3)  
mySystem.diskDrives(0) = "1.44 MB"  
```  
  
 您也可以宣告結構的陣列。 下列範例將說明這點。  
  
```vb  
Dim allSystems(100) As systemInfo  
```  
  
 您會遵循相同的規則來存取此資料結構的元件。 下列範例將說明這點。  
  
```vb  
ReDim allSystems(5).diskDrives(3)  
allSystems(5).CPU = "386SX"  
allSystems(5).diskDrives(2) = "100M SCSI"  
```  
  
## <a name="structures-and-objects"></a>結構和物件  
 結構可以包含物件做為其一個或多個元素。 下列範例將說明這點。  
  
```vb  
Protected Structure userInput  
    Public userName As String  
    Public inputForm As System.Windows.Forms.Form  
    Public userFileNumber As Integer  
End Structure  
```  
  
 您應該在這類宣告中使用特定的物件類別, 而`Object`不是。  
  
## <a name="structures-and-procedures"></a>結構和程式  
 您可以將結構當做程式引數來傳遞。 下列範例將說明這點。  
  
```vb  
Public currentCPUName As String = "700MHz Pentium compatible"  
Public currentMemorySize As Long = 256  
Public Sub fillSystem(ByRef someSystem As systemInfo)  
    someSystem.cPU = currentCPUName  
    someSystem.memory = currentMemorySize  
    someSystem.purchaseDate = Now  
End Sub  
```  
  
 上述範例會以傳*址方式*傳遞結構, 讓程式可以修改其專案, 讓變更在呼叫程式碼中生效。 如果您想要針對這類修改來保護結構, 請以傳值方式傳遞。  
  
 您也可以從`Function`程式傳回結構。 下列範例將說明這點。  
  
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
  
 您也可以使用這項技術, 將一個模組中定義的結構封裝在不同模組中定義的結構內。  
  
 結構可以包含任意深度的其他結構。  
  
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
