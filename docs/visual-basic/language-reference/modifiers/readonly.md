---
title: ReadOnly (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ReadOnly
helpviewer_keywords:
- ReadOnly keyword [Visual Basic]
- variables [Visual Basic], read-only
- ReadOnly property
- properties [Visual Basic], read-only
- read-only variables
ms.assetid: e868185d-6142-4359-a2fd-a7965cadfce8
ms.openlocfilehash: 6e361cbe89f4c51f28199b008de817c2d48ef326
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58825387"
---
# <a name="readonly-visual-basic"></a>ReadOnly (Visual Basic)
指定的變數或屬性可讀取但不是會寫入。  
  
## <a name="remarks"></a>備註  
  
## <a name="rules"></a>規則  
  
-   **宣告內容。** 您只能在模組層級使用 `ReadOnly`。 這表示的宣告內容`ReadOnly`項目必須是類別、 結構或模組，並不能是原始程式檔、 命名空間或程序。  
  
-   **結合的修飾詞。** 您無法指定`ReadOnly`搭配`Static`相同宣告中。  
  
-   **指派的值。** 程式碼使用`ReadOnly`屬性無法設定其值。 但是，具有存取權的基礎儲存體的程式碼可以指派，或隨時變更此值。  
  
     您可以指派值給`ReadOnly`變數只在其宣告或類別或結構中定義的建構函式中。  
  
## <a name="when-to-use-a-readonly-variable"></a>何時使用唯讀變數  
 您無法使用的情況下[Const 陳述式](../../../visual-basic/language-reference/statements/const-statement.md)來宣告和指派常數值。 比方說，`Const`陳述式可能不會接受您想要指派，資料類型，或您可能無法在編譯時期常數的運算式與計算的值。 然後，您甚至可能不知道值在編譯時期。 在這些情況下，您可以使用`ReadOnly`儲存常數值的變數。  
  
> [!IMPORTANT]
>  即使變數本身是，如果變數的資料型別是參考類型，例如陣列或類別執行個體，可以變更其成員`ReadOnly`。 下列範例將說明這點。  
  
 `ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}`  
  
 `Sub changeArrayElement()`  
  
 `characterArray(1) = "M"c`  
  
 `End Sub`  
  
 當初始化時，陣列指向`characterArray()`保留"x"，"y"，"z"。 因為變數`characterArray`是`ReadOnly`一旦初始化; 也就是說，您無法變更其值，您無法將新的陣列指派給它。 不過，您可以變更一個或多個陣列成員的值。 下列程序呼叫`changeArrayElement`，所指陣列`characterArray()`保留"x"，"M"、"z"。  
  
 請注意，這類似於宣告的程序參數[ByVal](../../../visual-basic/language-reference/modifiers/byval.md)，防止程序呼叫中引數本身的變更，但是可讓它來變更其成員。  
  
## <a name="example"></a>範例  
 下列範例會定義`ReadOnly`雇用員工的日期屬性。 屬性的值在內部類別會儲存`Private`變數，並只在類別內的程式碼可以變更該值。 不過，屬性是`Public`，並可存取該類別的任何程式碼可以讀取屬性。  
  
 [!code-vb[VbVbalrKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#4)]  
  
 `ReadOnly` 修飾詞可用於以下內容：  
  
 [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>另請參閱

- [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)
- [關鍵字](../../../visual-basic/language-reference/keywords/index.md)
