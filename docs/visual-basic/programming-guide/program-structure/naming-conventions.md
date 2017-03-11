---
title: "Visual Basic Naming Conventions | Microsoft Docs"
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
  - "names, Visual Basic rules"
  - "naming conventions"
  - "naming conventions, Visual Basic"
  - "Visual Basic code, naming conventions"
  - "conventions, Visual Basic coding"
  - "names, naming conventions"
  - "naming conventions, classes"
ms.assetid: 164949a4-2a7c-4736-9d82-9c3078e2e56c
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# Visual Basic Naming Conventions
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

當您在 Visual Basic 應用程式中為項目命名時，該名稱的第一個字元必須是字母字元或底線。  但請注意，以底線開頭的名稱不符合 [語言獨立性以及與語言無關的元件](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\) 標準。  
  
 以下為適用於命名的建議。  
  
-   名稱中的每一個單字以大寫字母做為開頭，例如 `FindLastRecord` 與 `RedrawMyForm`。  
  
-   函式與方法名稱以動詞做為開頭，例如 `InitNameArray` 或 `CloseDialog`。  
  
-   類別 \(Class\)、結構、模組和屬性 \(Property\) 名稱會以名詞做為開頭，例如 `EmployeeName` 或 `CarAccessory`。  
  
-   介面名稱以 "I" 前置字元做為開頭，之後並接著一個名詞或名詞片語 \(例如 `IComponent`\)，或是接著可描述介面行為的形容詞 \(例如 `IPersistable`\)。  不要使用底線，並且盡量不要使用縮寫，因為縮寫可能導致混淆。  
  
-   事件處理常式名稱以名詞為開頭，以描述其後跟隨 "`EventHandler`" 後置詞的事件類型，例如 "`MouseEventHandler`"。  
  
-   在事件引數類別的名稱中，包含 "`EventArgs`" 後置詞。  
  
-   如果事件擁有「之前」、「之後」的概念，請使用現在式或過去式的後置字元，例如在 "`ControlAdd`" 或 "`ControlAdded`" 中。  
  
-   對於冗長或常用的詞彙，可使用縮寫以使名稱保持合理的長度，例如使用 "HTML"，而不使用 "Hypertext Markup Language"。  一般來說，變數名稱大於 32 個字元者將會難以在低解析度的螢幕上閱讀。  此外，確認您的縮寫名稱在整個應用軟體中維持一致。  在專案中隨意變換 "HTML" 與 "Hypertext Markup Language" 會造成混淆。  
  
-   避免在內部範圍使用與外部範圍相同的名稱。  存取不正確的變數會導致錯誤發生。  若名稱相同的變數與關鍵字產生衝突，則您必須以適當的型別程式庫前置關鍵字來識別之。  例如，如果有一個名為 `Date` 的變數，則您只能藉由呼叫 <xref:System.DateTime.Date%2A?displayProperty=fullName> 的方式，使用內建的 `Date` 函式。  
  
## 請參閱  
 [Keywords as Element Names in Code](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)   
 [Me, My, MyBase, and MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)   
 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [程式結構和程式碼慣例](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)   
 [Visual Basic Language Reference](../../../visual-basic/language-reference/index.md)