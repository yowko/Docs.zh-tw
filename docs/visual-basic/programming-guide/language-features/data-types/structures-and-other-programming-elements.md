---
title: 結構與其他程式設計項目
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], arrays
- procedures [Visual Basic], structures as arguments to
- objects [Visual Basic], structure elements
- arrays [Visual Basic], structure elements
- nested structures [Visual Basic]
ms.assetid: 0f849313-ccd2-4c9a-acb9-69de6751c088
ms.openlocfilehash: 73d3f999e95c484dff3f5409f2cdb9032b64fe38
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266855"
---
# <a name="structures-and-other-programming-elements-visual-basic"></a>結構和其他程式設計項目 (Visual Basic)
您可以將結構與陣列、物件和過程結合使用，也可以彼此結合使用。 交互使用與這些元素單獨使用的語法相同。  
  
> [!NOTE]
> 不能初始化結構聲明中的任何結構元素。 只能將值分配給已聲明為結構類型的變數的元素。  
  
## <a name="structures-and-arrays"></a>結構和陣列  
 結構可以包含陣列作為其一個或多個元素。 下列範例將說明這點。  
  
```vb  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As String  
    Public purchaseDate As Date  
End Structure
```  
  
 訪問結構中陣列的值的方式與訪問物件的屬性的方式相同。 下列範例將說明這點。  
  
```vb  
Dim mySystem As systemInfo  
ReDim mySystem.diskDrives(3)  
mySystem.diskDrives(0) = "1.44 MB"  
```  
  
 您還可以聲明結構陣列。 下列範例將說明這點。  
  
```vb  
Dim allSystems(100) As systemInfo  
```  
  
 您可以遵循相同的規則來訪問此資料體系結構的元件。 下列範例將說明這點。  
  
```vb  
ReDim allSystems(5).diskDrives(3)  
allSystems(5).CPU = "386SX"  
allSystems(5).diskDrives(2) = "100M SCSI"  
```  
  
## <a name="structures-and-objects"></a>結構和物件  
 結構可以包含物件作為其一個或多個元素。 下列範例將說明這點。  
  
```vb  
Protected Structure userInput  
    Public userName As String  
    Public inputForm As System.Windows.Forms.Form  
    Public userFileNumber As Integer  
End Structure  
```  
  
 應在此類聲明中使用特定物件類，而不是`Object`。  
  
## <a name="structures-and-procedures"></a>結構和程式  
 可以將結構作為過程參數傳遞。 下列範例將說明這點。  
  
```vb  
Public currentCPUName As String = "700MHz Pentium compatible"  
Public currentMemorySize As Long = 256  
Public Sub fillSystem(ByRef someSystem As systemInfo)  
    someSystem.cPU = currentCPUName  
    someSystem.memory = currentMemorySize  
    someSystem.purchaseDate = Now  
End Sub  
```  
  
 前面的示例*通過 引用*傳遞結構，這允許過程修改其元素，以便更改在調用代碼中生效。 如果要保護結構免受此類修改，則按值傳遞它。  
  
 您還可以從`Function`過程返回結構。 下列範例將說明這點。  
  
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
  
## <a name="structures-within-structures"></a>結構內部的結構  
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
  
 您還可以使用此技術封裝在不同模組中定義的結構中一個模組中定義的結構。  
  
 結構可以包含任意深度的其他結構。  
  
## <a name="see-also"></a>另請參閱

- [資料類型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [基礎資料類型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [複合資料類型](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [值類型和參考類型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [結構](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [資料類型的疑難排解](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [如何：宣告結構](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [結構變數](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)
- [結構和類別](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [Structure 陳述式](../../../../visual-basic/language-reference/statements/structure-statement.md)
