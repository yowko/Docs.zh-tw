---
title: "Type Promotion (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "declared elements, scope"
  - "visibility, declared elements"
  - "Partial keyword, unexpected results with type promotion"
  - "scope, declared elements"
  - "scope, Visual Basic"
  - "type promotion"
  - "declared elements, visibility"
ms.assetid: 035eeb15-e4c5-4288-ab3c-6bd5d22f7051
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# Type Promotion (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

當您在模組中宣告一個程式設計項目時，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 會將其範圍提升至包含該模組的命名空間。  這個過程稱為「*型別提升*」\(Type Promotion\)。  
  
 下列範例說明模組的基本架構定義，以及該模組的兩個成員。  
  
 [!code-vb[VbVbalrDeclaredElements#1](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/visualbasic/type-promotion_1.vb)]  
  
 在 `projModule` 中，在模組層級宣告的程式設計項目會提升至 `projNamespace`。  在前述範例中，僅提升了 `basicEnum` 和 `innerClass`，卻沒有提升 `numberSub`，因為其並未在模組層級中宣告。  
  
## 型別提升的效用  
 型別提升的效用是在模組名稱中，不需加入限定性條件字串 \(String\)。  下列範例將會對前述範例中的程序呼叫兩次。  
  
 [!code-vb[VbVbalrDeclaredElements#2](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/visualbasic/type-promotion_2.vb)]  
  
 在前述範例中，第一次呼叫是使用完整的限定性條件字串。  但因為型別提升，其實並不需這麼做。  第二次呼叫也會存取模組成員，而不會在限定性條件字串中加入 `projModule`。  
  
## 型別提升失敗  
 如果命名空間中已經存在與模組成員名稱相同的成員，該模組成員的型別提升將無效。  下列範例說明列舉型別 \(Enumeration\) 及相同命名空間中模組的基本架構定義。  
  
 [!code-vb[VbVbalrDeclaredElements#3](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/visualbasic/type-promotion_3.vb)]  
  
 在前述範例中，[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 無法將類別 \(Class\) `abc` 提升至 `thisNameSpace`，因為命名空間層次中已經存在名稱相同的列舉型別。  若要存取 `abcSub`，您必須使用完整的限定性條件字串 `thisNamespace.thisModule.abc.abcSub`。  但是類別 `xyz` 仍會提升，而您可以使用較短的限定性條件字串 `thisNamespace.xyz.xyzSub` 來存取 `xyzSub`。  
  
### 部分型別的型別提升失敗  
 如果模組內的類別或結構使用 [Partial](../../../../visual-basic/language-reference/modifiers/partial.md) 關鍵字，無論命名空間中是否具有名稱相同的成員，該類別或結構的型別提升會自動失敗。  模組中的其他項目仍可進行型別提升。  
  
 **結果** ：部分定義的型別提升失敗可能導致無法預期的結果，甚至產生編譯器錯誤。  下列範例說明類別的基本架構部分定義，其中一項位於模組內。  
  
 [!code-vb[VbVbalrDeclaredElements#4](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/visualbasic/type-promotion_4.vb)]  
  
 在前述範例中，開發人員可能預期編譯器會合併 `sampleClass` 的兩個部分定義。  但是編譯器卻不會考慮提升 `sampleModule` 內的部分定義。  這使得編譯器嘗試編譯兩個獨立的不同類別，雖然名稱都是 `sampleClass`，但具備不同的完整路徑。  
  
 只有在完整路徑名稱 \(Fully Qualified Path\) 完全相同的情況下，編譯器才會合併部分定義。  
  
## 建議事項  
 下列建議表示良好的程式設計實務。  
  
-   **唯一名稱** ：當您能完全控制程式設計項目的命名方式時，在所有的地方都使用唯一的名稱是很好的作法。  相同的名稱需要額外的限定性條件，會因而增加閱讀程式碼的難度。  這也可能導致小錯誤和無法預期的結果。  
  
-   **完整路徑名稱** ：處理相同命名空間中的模組和其他項目時，最安全的方法是所有的程式設計項目永遠使用完整路徑名稱。  如果某個模組成員的型別提升失敗，而且您沒有提供該成員的完整路徑名稱，可能會無意間存取到不同的程式設計項目。  
  
## 請參閱  
 [Module Statement](../../../../visual-basic/language-reference/statements/module-statement.md)   
 [Namespace Statement](../../../../visual-basic/language-reference/statements/namespace-statement.md)   
 [Partial](../../../../visual-basic/language-reference/modifiers/partial.md)   
 [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)   
 [How to: Control the Scope of a Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)   
 [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)