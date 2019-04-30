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
ms.openlocfilehash: 4a3ef3a8254153fa8695ffacd9829ca9316d77a5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61959974"
---
# <a name="object-variable-declaration-visual-basic"></a>物件變數宣告 (Visual Basic)
您可以使用一般的宣告陳述式來宣告物件變數。 資料類型，針對您指定下列其中一個`Object`(也就是[Object 資料型別](../../../../visual-basic/language-reference/data-types/object-data-type.md)) 或更特定的類別來源物件的建立。  
  
 宣告一個變數`Object`等同於它宣告為<xref:System.Object?displayProperty=nameWithType>。  
  
 當您宣告變數與特定物件類別時，它可以存取所有的方法和該類別和它所繼承的類別所公開的屬性。 如果您宣告變數<xref:System.Object>，它可以存取的成員<xref:System.Object>類別，除非您開啟`Option Strict Off`允許晚期繫結。  
  
## <a name="declaration-syntax"></a>宣告語法  
 您可以使用下列語法來宣告物件變數：  
  
```vb  
Dim variablename As [New] { objectclass | Object }  
```  
  
 您也可以指定[公開金鑰](../../../../visual-basic/language-reference/modifiers/public.md)，[受保護](../../../../visual-basic/language-reference/modifiers/protected.md)， [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)， `Protected Friend`，[私人](../../../../visual-basic/language-reference/modifiers/private.md)，[共用](../../../../visual-basic/language-reference/modifiers/shared.md)，或[靜態](../../../../visual-basic/language-reference/modifiers/static.md)宣告中。 下列範例宣告是有效的：  
  
```vb  
Private objA As Object  
Static objB As System.Windows.Forms.Label  
Dim objC As System.OperatingSystem  
```  
  
## <a name="late-binding-and-early-binding"></a>晚期繫結，以及早期繫結  
 有時候特定的類別是未知的程式碼執行之前。 在此情況下，您必須宣告物件變數`Object`資料型別。 這會建立任何類型的物件，一般參考，並在執行階段指派特定的類別。 這就叫做*晚期繫結*。 晚期繫結需要額外的執行時間。 它也會限制您的程式碼的方法和您最近已指派給它之類別的屬性。 如果您的程式碼嘗試存取不同類別的成員，這可能會導致執行階段錯誤。  
  
 當您知道的特定類別在編譯時期時，您應該宣告為該類別的物件變數。 這稱為「早期繫結」。 早期繫結可以改善效能，並保證您的程式碼存取所有的方法和屬性的特定類別。 在上述範例宣告中，如果變數`objA`使用的類別的物件<xref:System.Windows.Forms.Label?displayProperty=nameWithType>，您應該指定`As System.Windows.Forms.Label`在其宣告中。  
  
### <a name="advantages-of-early-binding"></a>早期繫結的優點  
 物件變數宣告為特定的類別會提供數個優點：  
  
- 自動類型檢查  
  
- 保證特定類別的所有成員存取  
  
- Microsoft IntelliSense 支援在程式碼編輯器  
  
- 您的程式碼更容易閱讀  
  
- 在您的程式碼中的錯誤更少  
  
- 在攔截到的錯誤編譯時間，而非執行階段  
  
- 更快的程式碼執行  
  
## <a name="access-to-object-variable-members"></a>物件變數成員的存取  
 當`Option Strict`已開啟`On`，物件變數可以存取的方法和與您用以宣告之類別的屬性。 下列範例將說明這點。  
  
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
 當使用繼承階層架構中的物件，您必須選擇要用於宣告物件變數的類別。 在進行這項選擇，您必須平衡對類別成員的存取權的物件指派的彈性。 例如，請考慮繼承階層架構，會導致<xref:System.Windows.Forms.Form?displayProperty=nameWithType>類別：  
  
 <xref:System.Object>  
  
 &nbsp;&nbsp;<xref:System.MarshalByRefObject>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;<xref:System.ComponentModel.Component>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Control>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ScrollableControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ContainerControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Form>  
  
 假設您的應用程式定義表單類別，稱為`specialForm`，該項則繼承自類別<xref:System.Windows.Forms.Form>。 您可以宣告物件變數，指的是專為`specialForm`，如下列範例所示。  
  
```vb  
Public Class specialForm  
    Inherits System.Windows.Forms.Form  
    ' Insert code defining methods and properties of specialForm.  
End Class  
Dim nextForm As New specialForm  
```  
  
 在上述範例中宣告限制變數`nextForm`類別的物件`specialForm`，但它也會使得所有方法和屬性`specialForm`能夠`nextForm`，以及從它的所有類別的所有成員`specialForm`繼承。  
  
 您可以讓較一般的物件變數宣告為類型<xref:System.Windows.Forms.Form>，如下列範例所示。  
  
```vb  
Dim anyForm As System.Windows.Forms.Form  
```  
  
 在上述範例中宣告可讓您指派您的應用程式中的任何表單`anyForm`。 不過，雖然`anyForm`可以存取類別的所有成員<xref:System.Windows.Forms.Form>，它不能使用的任何其他的方法或屬性，例如定義特定表單`specialForm`。  
  
 基底類別的所有成員都都可以使用衍生的類別，但在衍生類別的其他成員都則無法使用的基底類別。  
  
## <a name="see-also"></a>另請參閱

- [物件變數](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [物件變數指派](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [物件變數值](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [如何：宣告物件變數，並在 Visual Basic 中將物件指派給它](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [如何：存取物件的成員](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)
- [New 運算子](../../../../visual-basic/language-reference/operators/new-operator.md)
- [Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [區域類型推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
