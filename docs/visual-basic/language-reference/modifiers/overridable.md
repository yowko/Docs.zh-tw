---
title: "Overridable (Visual Basic) | Microsoft Docs"
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
  - "Overridable"
  - "vb.Overridable"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "elements, concrete"
  - "properties [Visual Basic], redefining"
  - "overriding, Overridable keyword"
  - "elements, virtual"
  - "virtual elements"
  - "procedures, overriding"
  - "concrete elements"
  - "procedures, redefining"
  - "Overridable keyword"
  - "properties [Visual Basic], overriding"
ms.assetid: 612581e7-8a4c-4a5d-beff-3402fffa6f35
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Overridable (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

指定可以衍生類別中名稱完全相同的屬性 \(Property\) 或程序來覆寫屬性或程序。  
  
## 備註  
 `Overridable`修飾詞讓衍生類別中覆寫類別中的屬性或方法。  [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)修飾詞可防止屬性或方法在衍生類別中覆寫。  如需詳細資訊，請參閱 [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)。  
  
 如果`Overridable`或`NotOverridable`修飾詞不指定，則預設設定，取決於是否屬性或方法會覆寫基底類別的屬性或方法。  如果該屬性或方法覆寫基底類別的屬性或方法，預設值會是`Overridable`。 否則，它就是`NotOverridable`。  
  
 您可以遮蔽或覆寫來重新定義繼承的項目，但這兩種方法間有顯著的差異。  如需詳細資訊，請參閱 [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)。  
  
 可覆寫的項目有時稱為「*虛擬*」\(Virtual\) 項目。  如果項目可予以覆寫，但並不一定要進行覆寫，有時也稱為「*實體*」項目。  
  
 只有在屬性或程序宣告陳述式 \(Declaration Statement\) 中，才能使用 `Overridable`。  
  
## 組合的修飾詞  
 您不能指定`Overridable`或`NotOverridable`的`Private`方法。  
  
 您無法在同一個宣告中同時指定 `Overridable` 與 `MustOverride`、`NotOverridable` 或 `Shared`。  
  
 因為覆寫項目可隱含覆寫，所以您無法將 `Overridable` 與 `Overrides` 合併。  
  
## 使用方式  
 `Overridable` 修飾詞可用於以下內容中：  
  
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## 請參閱  
 [Modifiers](../../../visual-basic/language-reference/modifiers/index.md)   
 [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)   
 [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)   
 [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)   
 [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)   
 [關鍵字](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)