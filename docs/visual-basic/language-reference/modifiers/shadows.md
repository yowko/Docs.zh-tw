---
title: "Shadows (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Shadows"
  - "shadows"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "shadowing"
  - "duplicate names"
  - "scope, shadowing"
  - "Shadows keyword"
  - "names, shadowing"
ms.assetid: 6bf687cd-0544-4797-b51b-911125ec57c6
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# Shadows (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

指定宣告的程式設計項目會重新宣告並隱藏基底類別中相同名稱的項目，或多載項目集。  
  
## 備註  
 遮蔽 \(也稱為「*依名稱隱藏*」\) 的主要目的是保留類別成員的定義。  基底類別可能會經歷變更，該變更會使用與已定義的相同名稱來建立項目。  若有上述情形發生，`Shadows` 修飾詞 \(Modifier\) 會透過類別，強制參考解析為您所定義的成員，而非解析為新的基底類別項目。  
  
 遮蔽和覆寫都會重新定義繼承的項目，但這兩個方法之間有顯著的差異。  如需詳細資訊，請參閱 [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)。  
  
## 規則  
  
-   **宣告內容：** 您只能在類別層級使用 `Shadows`。  這表示 `Shadows` 項目的宣告內容必須是類別，而不可以是原始程式檔 \(Source File\)、命名空間 \(Namespace\)、介面、模組、結構或程序。  
  
     在單一宣告陳述式 \(Declaration Statement\) 中只可宣告一個主導遮蔽項目 \(Shadowing Element\)。  
  
-   **組合的修飾詞：** 您無法在同一個宣告中同時指定 `Shadows` 與 `Overloads`、`Overrides` 或 `Static`。  
  
-   **元素型別**： 您可以用任意一種宣告項目遮蔽其他宣告項目。  若以其他屬性或程序遮蔽屬性或程序，參數和傳回型別就不必符合基底類別屬性或程序中的參數和傳回型別。  
  
-   **存取** 基底類別中的受遮蔽項目 \(Shadowed Element\) 通常無法從遮蔽它的衍生類別中取得。  但需考量下列情形。  
  
    -   如果主導遮蔽項目無法從參考它的程式碼中存取，則參考會解析為受遮蔽項目。  例如，如果 `Private` 項目會遮蔽基底類別項目，則無權存取 `Private` 項目的程式碼會改為存取基底類別項目。  
  
    -   若有遮蔽項目，則仍可透過以基底類別型別宣告的物件，存取遮蔽的項目。  您也可透過 `MyBase` 進行存取。  
  
 `Shadows` 修飾詞可用於以下內容中：  
  
 [Class 陳述式](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Const 陳述式](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Delegate 陳述式](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Enum 陳述式](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface 陳述式](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## 請參閱  
 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)   
 [Static](../../../visual-basic/language-reference/modifiers/static.md)   
 [Private](../../../visual-basic/language-reference/modifiers/private.md)   
 [Me, My, MyBase, and MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)   
 [Inheritance Basics](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)   
 [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)   
 [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)   
 [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md)   
 [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)   
 [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)   
 [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)