---
title: 物件變數宣告 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- early binding [Visual Basic]
- declarations [Visual Basic], class
- classes [Visual Basic], declaring
- binding [Visual Basic], late and early
- object variables [Visual Basic], declaring
- variables [Visual Basic], object
- declaring variables [Visual Basic], object variables
- declaring classes [Visual Basic]
- late binding [Visual Basic]
ms.assetid: 2a5a41a3-1aa8-4236-b1f0-2382af7bf715
ms.openlocfilehash: f5f77b81380d997e078a9f52ac4aae6f6e975575
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656278"
---
# <a name="object-variable-declaration-visual-basic"></a>物件變數宣告 (Visual Basic)
您可以使用一般宣告陳述式來宣告物件變數。 資料類型，您指定`Object`(也就是[物件資料類型](../../../../visual-basic/language-reference/data-types/object-data-type.md)) 或更特定類別的物件是要建立的。  
  
 變數宣告為`Object`等同於它宣告為<xref:System.Object?displayProperty=nameWithType>。  
  
 當您宣告具有特定的物件類別的變數時，它可以存取所有的方法和該類別和它所繼承的類別所公開的屬性。 如果您宣告變數和<xref:System.Object>，它可以存取的成員<xref:System.Object>類別，除非您開啟`Option Strict Off`允許晚期繫結。  
  
## <a name="declaration-syntax"></a>宣告語法  
 使用下列語法來宣告物件變數：  
  
```vb  
Dim variablename As [New] { objectclass | Object }  
```  
  
 您也可以指定[公用](../../../../visual-basic/language-reference/modifiers/public.md)，[保護](../../../../visual-basic/language-reference/modifiers/protected.md)， [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)， `Protected Friend`，[私人](../../../../visual-basic/language-reference/modifiers/private.md)，[共用](../../../../visual-basic/language-reference/modifiers/shared.md)，或[靜態](../../../../visual-basic/language-reference/modifiers/static.md)宣告中。 下列範例宣告是有效值：  
  
```vb  
Private objA As Object  
Static objB As System.Windows.Forms.Label  
Dim objC As System.OperatingSystem  
```  
  
## <a name="late-binding-and-early-binding"></a>晚期繫結與早期繫結  
 有時特定類別是未知的程式碼執行之前。 在此情況下，您必須宣告物件變數`Object`資料型別。 這會建立任何類型的物件，以一般參考，並在執行階段指派特定的類別。 這稱為*晚期繫結*。 晚期繫結需要額外的執行時間。 它也會限制您的程式碼的方法和屬性，您最近已指派給它的類別。 如果您的程式碼嘗試存取不同類別的成員，這會造成執行階段錯誤。  
  
 當您在編譯時間知道特定類別時，您應該宣告為該類別的物件變數。 這稱為「早期繫結」。 早期繫結可改善效能，而且不保證您的程式碼存取的所有方法和特定類別的屬性。 在上述範例宣告中，如果變數`objA`使用物件類別<xref:System.Windows.Forms.Label?displayProperty=nameWithType>，您應該指定`As System.Windows.Forms.Label`在其宣告中。  
  
### <a name="advantages-of-early-binding"></a>早期繫結的優點  
 物件變數宣告為特定的類別有數個優點：  
  
-   自動類型檢查  
  
-   保證特定類別的所有成員存取  
  
-   Microsoft IntelliSense 支援在程式碼編輯器  
  
-   您的程式碼更容易閱讀  
  
-   減少程式碼中的錯誤  
  
-   錯誤攔截在編譯時期而不是執行階段  
  
-   更快速執行的程式碼  
  
## <a name="access-to-object-variable-members"></a>物件變數成員存取  
 當`Option Strict`開啟`On`，物件變數只能存取方法和您用以宣告它之類別的屬性。 下列範例將說明這點。  
  
```vb  
' Option statements must precede all other source file lines.  
Option Strict On  
' Imports statement must precede all declarations in the source file.  
Imports System.Windows.Forms  
Public Sub accessMembers()  
    Dim p As Object  
    Dim q As System.Windows.Forms.Label  
    p = New System.Windows.Forms.Label  
    q = New System.Windows.Forms.Label  
    Dim j, k As Integer  
    ' The following statement generates a compiler ERROR.  
    j = p.Left  
    ' The following statement retrieves the left edge of the label in pixels.  
    k = q.Left  
End Sub  
```  
  
 在此範例中， `p` 只能使用 <xref:System.Object> 類別本身的成員，其並未包含 `Left` 屬性。 另一方面，已宣告 `q` 屬於 <xref:System.Windows.Forms.Label>類型，因此它可以使用 <xref:System.Windows.Forms.Label> 命名空間中 <xref:System.Windows.Forms> 類別的所有方法和屬性。  
  
## <a name="flexibility-of-object-variables"></a>物件變數的彈性  
 當使用繼承階層架構中的物件，您必須選擇要用於宣告物件變數的類別。 在選擇時，您必須平衡對類別成員存取的物件指派的彈性。 例如，請考慮繼承階層架構，會導致<xref:System.Windows.Forms.Form?displayProperty=nameWithType>類別：  
  
 <xref:System.Object>  
  
 &nbsp;&nbsp;<xref:System.MarshalByRefObject>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;<xref:System.ComponentModel.Component>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Control>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ScrollableControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ContainerControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Form>  
  
 假設您的應用程式定義表單類別，稱為`specialForm`，後者繼承自類別<xref:System.Windows.Forms.Form>。 您可以宣告物件變數，指的是專為`specialForm`，如下列範例所示。  
  
```vb  
Public Class specialForm  
    Inherits System.Windows.Forms.Form  
    ' Insert code defining methods and properties of specialForm.  
End Class  
Dim nextForm As New specialForm  
```  
  
 在上述範例中宣告限制變數`nextForm`類別的物件`specialForm`，但同時也讓所有方法和屬性`specialForm`可`nextForm`，以及從中的所有類別的所有成員`specialForm`繼承。  
  
 您可以藉由宣告它是型別進行更一般的物件變數<xref:System.Windows.Forms.Form>，如下列範例所示。  
  
```vb  
Dim anyForm As System.Windows.Forms.Form  
```  
  
 在上述範例中宣告可讓您指定您的應用程式中的任何表單`anyForm`。 不過，雖然`anyForm`可以存取類別的所有成員<xref:System.Windows.Forms.Form>，它不能使用任何其他方法或屬性，例如定義特定形式`specialForm`。  
  
 基底類別的所有成員都都可以使用衍生的類別，但在衍生類別的其他成員都則無法使用的基底類別。  
  
## <a name="see-also"></a>另請參閱  
 [物件變數](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [物件變數指派](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [物件變數值](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [如何： 宣告物件變數，並在 Visual Basic 中為其指派物件](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)  
 [如何：存取物件的成員](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)  
 [New 運算子](../../../../visual-basic/language-reference/operators/new-operator.md)  
 [Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [區域類型推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
