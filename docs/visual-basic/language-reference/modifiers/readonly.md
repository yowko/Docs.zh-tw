---
title: ReadOnly (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.ReadOnly
helpviewer_keywords:
- ReadOnly keyword [Visual Basic]
- variables [Visual Basic], read-only
- ReadOnly property
- properties [Visual Basic], read-only
- read-only variables
ms.assetid: e868185d-6142-4359-a2fd-a7965cadfce8
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9ca1d2e4eddb3b88073d6fcd46b0de5c627ba809
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="readonly-visual-basic"></a>ReadOnly (Visual Basic)
指定的變數或屬性可以讀取但不是會寫入。  
  
## <a name="remarks"></a>備註  
  
## <a name="rules"></a>規則  
  
-   **宣告內容。** 您只能在模組層級使用 `ReadOnly`。 這表示宣告內容`ReadOnly`項目必須是類別、 結構或模組，並不能是原始程式檔、 命名空間或程序。  
  
-   **結合的修飾詞。** 您無法指定`ReadOnly`搭配`Static`相同宣告中。  
  
-   **指派值。** 程式碼使用`ReadOnly`屬性無法設定其值。 但可以存取的基礎儲存體的程式碼可以指派或在任何時間變更的值。  
  
     您可以指派值給`ReadOnly`變數只有在其宣告或類別或結構定義所在的建構函式中。  
  
## <a name="when-to-use-a-readonly-variable"></a>何時使用唯讀變數  
 您無法使用的情況有[Const 陳述式](../../../visual-basic/language-reference/statements/const-statement.md)宣告並指派常數值。 例如，`Const`陳述式可能無法接受的資料類型，您想要指派，或您可能無法在編譯時期常數的運算式與計算值。 然後，您甚至可能不知道此值在編譯時間。 在這些情況下，您可以使用`ReadOnly`儲存常數值的變數。  
  
> [!IMPORTANT]
>  即使變數本身是如果變數的資料類型是參考類型，例如陣列或類別執行個體，可變更其成員`ReadOnly`。 下列範例將說明這點。  
  
 `ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}`  
  
 `Sub changeArrayElement()`  
  
 `characterArray(1) = "M"c`  
  
 `End Sub`  
  
 當初始化時，陣列所指`characterArray()`保留"x"、"y"和"z"。 因為變數`characterArray`是`ReadOnly`一旦初始化; 也就是說，無法變更其值，您無法將新的陣列指派給它。 不過，您可以變更的一或多個陣列成員的值。 下列程序呼叫`changeArrayElement`，所指陣列`characterArray()`保留"x"，"M"、"z"。  
  
 請注意，這類似於宣告的程序參數[ByVal](../../../visual-basic/language-reference/modifiers/byval.md)，這可防止程序變更呼叫的引數本身但會允許它變更其成員。  
  
## <a name="example"></a>範例  
 下列範例會定義`ReadOnly`雇用員工的日期屬性。 類別會將屬性值在內部以`Private`變數，而且只在類別內的程式碼可以變更這個值。 不過，屬性是`Public`，以及任何可以存取該類別的程式碼可以讀取屬性。  
  
 [!code-vb[VbVbalrKeywords#4](../../../visual-basic/language-reference/codesnippet/VisualBasic/readonly_1.vb)]  
  
 `ReadOnly` 修飾詞可用於以下內容：  
  
 [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>另請參閱  
 [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)  
 [關鍵字](../../../visual-basic/language-reference/keywords/index.md)
