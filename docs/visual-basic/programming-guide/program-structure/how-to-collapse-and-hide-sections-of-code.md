---
title: "How to: Collapse and Hide Sections of Code (Visual Basic) | Microsoft Docs"
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
  - "Visual Basic, code collapsing"
  - "Visual Basic, code hiding"
  - "Visual Basic code, collapsing and hiding"
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# How to: Collapse and Hide Sections of Code (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

`#Region` 指示詞可供您摺疊和隱藏 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 檔案中的程式碼區段。  `#Region` 指示詞可供您指定在使用 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] 程式碼編輯器時，您可展開或摺疊的程式碼區塊。  可選擇性地隱藏程式碼可讓您的檔案更易於管理與閱讀。  如需詳細資訊，請參閱 [大綱](/visual-studio/ide/outlining)。  
  
 `#Region` 指示詞可支援程式碼區塊語意 \(Semantics\)，例如 `#If...#End If`。  這表示它們不能在某個區塊開始而在另一個區塊結束，必須在同一個區塊中開始與結束。  函式中不支援 `#Region` 指示詞。  
  
### 若要摺疊與隱藏程式碼區段  
  
-   將程式碼區段放在 `#Region` 和 `#End Region` 陳述式 \(Statement\) 之間，如下列範例所示：  
  
     [!code-vb[VbVbalrConditionalComp#6](../../../visual-basic/language-reference/directives/codesnippet/visualbasic/how-to-collapse-and-hide_1.vb)]  
  
     `#Region` 區塊可在一個程式碼檔案中使用多次，因此使用者可以自行定義可依序摺疊的程序與類別區塊，  也可以將 `#Region` 區塊巢狀於另一個 `#Region` 區塊中。  
  
    > [!NOTE]
    >  隱藏程式碼並不會使它無法進行編譯，而且也不會影響 `#If...#End If` 陳述式。  
  
## 請參閱  
 [Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)   
 [\#Region Directive](../../../visual-basic/language-reference/directives/region-directive.md)   
 [\#If...Then...\#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md)   
 [大綱](/visual-studio/ide/outlining)