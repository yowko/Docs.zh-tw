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
ms.openlocfilehash: b6de52cf738a56a42c82978b54cef31574ab0bcb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410357"
---
# <a name="object-variable-declaration-visual-basic"></a>物件變數宣告 (Visual Basic)
您可以使用一般宣告語句來宣告物件變數。 針對資料類型，您可以指定 `Object` （也就是[物件資料類型](../../../language-reference/data-types/object-data-type.md)）或更特定的類別，以從中建立物件。  
  
 將變數宣告為，如同 `Object` 將它宣告為 <xref:System.Object?displayProperty=nameWithType> 。  
  
 當您宣告具有特定物件類別的變數時，它可以存取該類別所公開的所有方法和屬性，以及它所繼承的類別。 如果您使用宣告變數 <xref:System.Object> ，它只能存取類別的成員 <xref:System.Object> ，除非您轉換 `Option Strict Off` 成允許晚期繫結。  
  
## <a name="declaration-syntax"></a>宣告語法  
 使用下列語法宣告物件變數：  
  
```vb  
Dim variablename As [New] { objectclass | Object }  
```  
  
 您也可以在宣告中指定[Public](../../../language-reference/modifiers/public.md)、 [Protected](../../../language-reference/modifiers/protected.md)、 [Friend](../../../language-reference/modifiers/friend.md)、 `Protected Friend` 、 [Private](../../../language-reference/modifiers/private.md)、 [Shared](../../../language-reference/modifiers/shared.md)或[Static](../../../language-reference/modifiers/static.md) 。 下列是有效的範例宣告：  
  
```vb  
Private objA As Object  
Static objB As System.Windows.Forms.Label  
Dim objC As System.OperatingSystem  
```  
  
## <a name="late-binding-and-early-binding"></a>晚期繫結和早期繫結  
 有時候，在您的程式碼執行之前，特定類別是未知的。 在此情況下，您必須宣告具有資料類型的物件變數 `Object` 。 這會建立任何物件類型的一般參考，並在執行時間指派特定的類別。 這稱為*晚期繫結*。 晚期繫結需要額外的執行時間。 它也會將您的程式碼限制為您最近指派給它的類別的方法和屬性。 如果您的程式碼嘗試存取不同類別的成員，這可能會造成執行階段錯誤。  
  
 當您在編譯時期知道特定類別時，您應該將物件變數宣告為該類別的。 這稱為「早期繫結」**。 早期繫結會改善效能，並保證您的程式碼可以存取特定類別的所有方法和屬性。 在上述範例宣告中，如果變數 `objA` 只使用類別的物件 <xref:System.Windows.Forms.Label?displayProperty=nameWithType> ，您應該 `As System.Windows.Forms.Label` 在其宣告中指定。  
  
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
 當 `Option Strict` 開啟時 `On` ，物件變數只能存取您用以宣告之類別的方法和屬性。 下列範例將說明這點。  
  
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
 在繼承階層架構中使用物件時，您可以選擇要用來宣告物件變數的類別。 進行這項選擇時，您必須平衡物件指派的彈性，使其無法存取類別的成員。 例如，請考慮導致類別的繼承階層架構 <xref:System.Windows.Forms.Form?displayProperty=nameWithType> ：  
  
 <xref:System.Object>  
  
 &nbsp;&nbsp;<xref:System.MarshalByRefObject>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;<xref:System.ComponentModel.Component>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Control>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ScrollableControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.ContainerControl>  
  
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<xref:System.Windows.Forms.Form>  
  
 假設您的應用程式定義了名為的表單類別 `specialForm` ，它會繼承自類別 <xref:System.Windows.Forms.Form> 。 您可以宣告特別參考的物件變數 `specialForm` ，如下列範例所示。  
  
```vb  
Public Class specialForm  
    Inherits System.Windows.Forms.Form  
    ' Insert code defining methods and properties of specialForm.  
End Class  
Dim nextForm As New specialForm  
```  
  
 上述範例中的宣告會將變數限制 `nextForm` 為類別的物件 `specialForm` ，但它也會讓的所有方法和屬性都可 `specialForm` 供使用 `nextForm` ，以及繼承之所有類別的所有成員 `specialForm` 。  
  
 您可以將物件變數宣告為類型，使其更通用 <xref:System.Windows.Forms.Form> ，如下列範例所示。  
  
```vb  
Dim anyForm As System.Windows.Forms.Form  
```  
  
 上述範例中的宣告可讓您將應用程式中的任何表單指派給 `anyForm` 。 不過，雖然 `anyForm` 可以存取類別的所有成員 <xref:System.Windows.Forms.Form> ，但它無法使用針對特定表單（例如）所定義的任何額外方法或屬性 `specialForm` 。  
  
 基類的所有成員都可供衍生類別使用，但衍生類別的其他成員無法供基類使用。  
  
## <a name="see-also"></a>另請參閱

- [物件變數](object-variables.md)
- [物件變數指派](object-variable-assignment.md)
- [物件變數值](object-variable-values.md)
- [如何：在 Visual Basic 中宣告物件變數，並指派物件給它](how-to-declare-an-object-variable-and-assign-an-object-to-it.md)
- [如何：存取物件的成員](how-to-access-members-of-an-object.md)
- [New 運算子](../../../language-reference/operators/new-operator.md)
- [Long](../../../language-reference/statements/option-strict-statement.md)
- [區域型別推斷](local-type-inference.md)
