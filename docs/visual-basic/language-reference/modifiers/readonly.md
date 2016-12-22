---
title: "ReadOnly (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ReadOnly"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "ReadOnly keyword"
  - "variables [Visual Basic], read-only"
  - "ReadOnly property"
  - "properties [Visual Basic], read-only"
  - "read-only variables"
ms.assetid: e868185d-6142-4359-a2fd-a7965cadfce8
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# ReadOnly (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

指定變數或屬性可以讀取但不可寫入。  
  
## 備註  
  
## 規則  
  
-   **宣告內容：** 只能在模組層級使用 `ReadOnly`。  這表示 `ReadOnly` 元素的宣告內容必須是類別、結構或模組，且不能是原始程式檔、命名空間或程序。  
  
-   **組合的修飾詞：** 您無法在同一個宣告中同時指定 `ReadOnly` 和 `Static`。  
  
-   **指派值** 使用 `ReadOnly` 屬性的程式碼無法設定其值。  但擁有基礎儲存體存取權限的程式碼可隨時指派或變更值。  
  
     您只能在 `ReadOnly` 變數的宣告中，或在定義了該變數的類別或結構的建構函式 \(Constructor\) 中，將值指派給該變數。  
  
## ReadOnly 變數的使用時機  
 在某些情況下，可能無法使用 [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md) 來宣告和指派常數值。  例如，`Const` 陳述式可能不接受您想指派的資料型別，或您可能無法在編譯時期，以常數運算式計算值。  您甚至無法在編譯時期確認值為何。  在這些情況下，可使用 `ReadOnly` 變數來保留常數值。  
  
> [!IMPORTANT]
>  如果變數的資料型別是參考型別 \(例如陣列或類別執行個體\)，則即使變數本身是 `ReadOnly`，您也能變更其成員。  下列範例將說明這點。  
  
 `ReadOnly characterArray() As Char = {"x"c, "y"c, "z"c}`  
  
 `Sub changeArrayElement()`  
  
 `characterArray(1) = "M"c`  
  
 `End Sub`  
  
 初始化時，`characterArray()` 所指向的陣列將存放 "x"、"y" 和 "z"。  由於變數 `characterArray` 是 `ReadOnly`，所以您無法變更其初始化後的值，也就是說無法指派給它新陣列。  然而，您可以變更一或多個陣列成員的值。  接下來呼叫程序 `changeArrayElement`，`characterArray()` 指向的陣列會存放 "x"、"M" 和 "z"。  
  
 請注意，這類似於將程序參數宣告為 [ByVal](../../../visual-basic/language-reference/modifiers/byval.md)，防止程序變更呼叫引數本身，但允許它變更其成員。  
  
## 範例  
 下列範例針對員工的雇用日期定義 `ReadOnly` 屬性。  類別會在內部將屬性值儲存為 `Private` 變數，且只有類別的內部程式碼可變更該值。  然而，屬性是 `Public`，且可存取類別的所有程式碼都能讀取該屬性。  
  
 [!CODE [VbVbalrKeywords#4](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrKeywords#4)]  
  
 `ReadOnly` 修飾詞可用於以下內容中：  
  
 [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## 請參閱  
 [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)   
 [關鍵字](../../../visual-basic/reference/command-line-compiler/index.md)