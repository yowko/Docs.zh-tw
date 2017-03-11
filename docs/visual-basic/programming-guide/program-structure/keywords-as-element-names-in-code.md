---
title: "Keywords as Element Names in Code (Visual Basic) | Microsoft Docs"
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
  - "Visual Basic code, naming conventions"
  - "keywords [Visual Basic], in code"
  - "name conflicts"
  - "element names, in code"
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# Keywords as Element Names in Code (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

任何程式項目，例如變數、類別或成員，可以和限制的關鍵字具有相同的名稱。  例如，您可以建立一個名為 `Loop` 的變數。  然而，若要參考您自己版本的變數 \(它會與限制的 `Loop` 關鍵字擁有相同名稱\)，則必須在該變數前加上完整的限定字串，或者以方括弧 \(`[ ]`\) 括住它，如下列範例所示：  
  
 [!code-vb[VbVbcnConventions#8](../../../visual-basic/programming-guide/language-features/codesnippet/visualbasic/keywords-as-element-name_1.vb)]  
  
 如果您未做上述的任一項動作，則 Visual Basic 將假設為使用內建的 `Loop` 關鍵字並產生錯誤，如下列範例所示：  
  
 `' The following statement causes a compiler error.`  
  
 `Loop.Visible = True`  
  
 當參考表單和控制項，或是使用與限制關鍵字相同之名稱宣告變數或定義程序時，您可以使用方括弧。  通常人們很容易忘記檢查名稱或者使用方括弧，而如此將會在您的程式碼中產生錯誤並使它更難以閱讀。  基於這個理由，我們建議您不要使用限制關鍵字做為程式項目的名稱。  然而，如果未來的 Visual Basic 版本定義與現有表單或控制項名稱相衝突的新關鍵字，則當您更新程式碼以使用新的版本執行時，便可以使用這個技巧。  
  
> [!NOTE]
>  您的程式可能也會包含由其他參考之組件 \(Assembly\) 所提供的項目名稱。  如果這些名稱會與限制的關鍵字相衝突，則可在前後放置方括弧以使 Visual Basic 將它們解譯為您所定義的項目。  
  
## 請參閱  
 [Visual Basic Naming Conventions](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)   
 [程式結構和程式碼慣例](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)   
 [關鍵字](../../../visual-basic/language-reference/keywords/index.md)