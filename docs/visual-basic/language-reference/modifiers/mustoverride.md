---
title: "MustOverride (Visual Basic) | Microsoft Docs"
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
  - "vb.MustOverride"
  - "MustOverride"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "virtual elements, pure"
  - "elements, pure virtual"
  - "properties [Visual Basic], redefining"
  - "procedures, overriding"
  - "overriding, MustOverride keyword"
  - "procedures, redefining"
  - "pure virtual elements"
  - "MustOverride keyword"
  - "properties [Visual Basic], overriding"
ms.assetid: 6e9d9ad6-bb64-433f-b32b-3ef84293bf96
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# MustOverride (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

指定屬性 \(Property\) 或程序未在此類別 \(Class\) 中進行實作，而且必須先在衍生類別中予以覆寫，才可加以使用。  
  
## 備註  
 只有在屬性或程序宣告陳述式 \(Declaration Statement\) 中，才能使用 `MustOverride`。  指定 `MustOverride` 的屬性或程序必須是類別的成員，而且該類別必須標記為 [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)。  
  
## 規則  
  
-   **不完整的宣告。** 指定 `MustOverride` 時，未提供屬性或程序的任何其他程式碼行，甚至也未提供 `End Function`、`End Property` 或 `End Sub` 陳述式。  
  
-   **組合的修飾詞：** 您無法在同一個宣告中同時指定 `MustOverride` 與 `NotOverridable`、`Overridable` 或 `Shared`。  
  
-   **遮蔽和覆寫** 遮蔽和覆寫都會重新定義繼承的項目，但這兩個方法之間有顯著的差異。  如需詳細資訊，請參閱 [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)。  
  
-   **替代用詞。** 不可使用的項目 \(但在覆寫中除外\) 有時稱為「*純虛擬*」\(Pure Virtual\) 項目。  
  
 `MustOverride` 修飾詞可用於以下內容中：  
  
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## 請參閱  
 [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)   
 [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)   
 [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)   
 [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)   
 [關鍵字](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)