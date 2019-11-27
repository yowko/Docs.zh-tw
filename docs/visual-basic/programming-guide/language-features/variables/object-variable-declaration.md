---
title: 物件變數宣告
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
ms.openlocfilehash: d1964e3768124dde1deeabfada9006ff5a59def0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351808"
---
# <a name="object-variable-declaration-visual-basic"></a>物件變數宣告 (Visual Basic)
您可以使用一般宣告語句來宣告物件變數。 針對資料類型，您可以指定 `Object` （也就是[物件資料類型](../../../../visual-basic/language-reference/data-types/object-data-type.md)）或更特定的類別，以從中建立物件。  
  
 將變數宣告為 `Object` 與將它宣告為 <xref:System.Object?displayProperty=nameWithType>相同。  
  
 當您宣告具有特定物件類別的變數時，它可以存取該類別所公開的所有方法和屬性，以及它所繼承的類別。 如果您使用 <xref:System.Object>宣告變數，它只能存取 <xref:System.Object> 類別的成員，除非您關閉 `Option Strict Off` 以允許晚期繫結。  
  
## <a name="declaration-syntax"></a>宣告語法  
 使用下列語法宣告物件變數：  
  
```vb  
Dim variablename As [New] { objectclass | Object }  
```  
  
 您也可以在宣告中指定[Public](../../../../visual-basic/language-reference/modifiers/public.md)、 [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)、 [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)、`Protected Friend`、 [Private](../../../../visual-basic/language-reference/modifiers/private.md)、 [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)或[Static](../../../../visual-basic/language-reference/modifiers/static.md) 。 下列是有效的範例宣告：  
  
```vb  
Private objA As Object  
Static objB As System.Windows.Forms.Label  
Dim objC As System.OperatingSystem  
```  
  
## <a name="late-binding-and-early-binding"></a>晚期繫結和早期繫結  
 有時候，在您的程式碼執行之前，特定類別是未知的。 在此情況下，您必須宣告具有 `Object` 資料類型的物件變數。 這會建立任何物件類型的一般參考，並在執行時間指派特定的類別。 這稱為*晚期繫結*。 晚期繫結需要額外的執行時間。 它也會將您的程式碼限制為您最近指派給它的類別的方法和屬性。 如果您的程式碼嘗試存取不同類別的成員，這可能會造成執行階段錯誤。  
  
 當您在編譯時期知道特定類別時，您應該將物件變數宣告為該類別的。 這稱為「早期繫結」。 早期繫結會改善效能，並保證您的程式碼可以存取特定類別的所有方法和屬性。 在上述範例宣告中，如果變數 `objA` 只使用 <xref:System.Windows.Forms.Label?displayProperty=nameWithType>類別的物件，您應該在其宣告中指定 `As System.Windows.Forms.Label`。  
  
### <a name="advantages-of-early-binding"></a>早期繫結的優點  
 將物件變數宣告為特定類別，可提供您幾個優點：  
  
- 自動類型檢查  
  
- 保證能夠存取特定類別的所有成員  
  
- 程式碼編輯器中的 Microsoft IntelliSense 支援  
  
- 改善程式碼的可讀性  
  
- 程式碼中的錯誤較少  
  
- 在編譯時期（而非執行時間）攔截到的錯誤  
  
- 更快速的程式碼執行  
  
## <a name="access-to-object-variable-members"></a>物件變數成員的存取權  
 當 `Option Strict` 開啟 `On`時，物件變數只能存取您用來宣告之類別的方法和屬性。 下列範例將說明這點。  
  
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
 在繼承階層架構中使用物件時，您可以選擇要用來宣告物件變數的類別。 進行這項選擇時，您必須平衡物件指派的彈性，使其無法存取類別的成員。 例如，請考慮導致 <xref:System.Windows.Forms.Form?displayProperty=nameWithType> 類別的繼承階層架構：  
  
 <xref:System.Object>  
  
 &nbsp;&nbsp;<xref:System.MarshalByRefObject>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;<xref:System.ComponentModel.Component>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Control>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ScrollableControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ContainerControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Form>  
  
 假設您的應用程式定義名為 `specialForm`的表單類別，其繼承自類別 <xref:System.Windows.Forms.Form>。 您可以宣告特別參考 `specialForm`的物件變數，如下列範例所示。  
  
```vb  
Public Class specialForm  
    Inherits System.Windows.Forms.Form  
    ' Insert code defining methods and properties of specialForm.  
End Class  
Dim nextForm As New specialForm  
```  
  
 前述範例中的宣告會將變數 `nextForm` 限制為 `specialForm`類別的物件，但它也會將 `specialForm` 的所有方法和屬性提供給 `nextForm`，以及 `specialForm` 繼承之所有類別的所有成員。  
  
 您可以將物件變數宣告為類型 <xref:System.Windows.Forms.Form>，讓它更通用，如下列範例所示。  
  
```vb  
Dim anyForm As System.Windows.Forms.Form  
```  
  
 上述範例中的宣告可讓您將應用程式中的任何表單指派給 `anyForm`。 不過，雖然 `anyForm` 可以存取 <xref:System.Windows.Forms.Form>類別的所有成員，但它無法使用針對特定表單（例如 `specialForm`）所定義的任何額外方法或屬性。  
  
 基類的所有成員都可供衍生類別使用，但衍生類別的其他成員無法供基類使用。  
  
## <a name="see-also"></a>請參閱

- [物件變數](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [物件變數指派](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [物件變數值](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [如何：在 Visual Basic 中宣告物件變數並指派物件給它](../../../../visual-basic/programming-guide/language-features/variables/how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [如何：存取物件的成員](../../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)
- [New 運算子](../../../../visual-basic/language-reference/operators/new-operator.md)
- [Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [區域類型推斷](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
