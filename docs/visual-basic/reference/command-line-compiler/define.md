---
title: "/define (Visual Basic) | Microsoft Docs"
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
  - "-d compiler option [Visual Basic]"
  - "/d compiler option [Visual Basic]"
  - "-define compiler option [Visual Basic]"
  - "d compiler option [Visual Basic]"
  - "/define compiler option [Visual Basic]"
  - "define compiler option [Visual Basic]"
ms.assetid: f735c57d-1cf9-4f2f-a26f-0de630fd4077
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# /define (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

定義條件式編譯器常數。  
  
## 語法  
  
```  
/define:["]symbol[=value][,symbol[=value]]["] ' -or- /d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## 引數  
  
|||  
|-|-|  
|詞彙|定義|  
|`symbol`|必要項。  要定義的符號。|  
|`value`|選擇項。  要指派 `symbol` 的值。  如果 `value` 是字串，則必須以反斜線\/引號的順序 \(\\"\) 括住，而不能使用引號。  如果未指定值，則會認為是 True。|  
  
## 備註  
 `/define` 選項有一個類似在原始程式檔中使用 `#Const` 前置處理器指示詞的效果，除了以 `/define` 定義的常數是公開的，且適用於專案中的所有檔案。  
  
 您可以使用此選項建立的符號，搭配 `#If`...`Then`...`#Else` 指示詞，有條件地編譯原始程式檔。  
  
 `/d` 是 `/define` 的簡短形式。  
  
 您可以使用逗號分隔符號定義，以 `/define` 定義多個符號。  
  
||  
|-|  
|在 Visual Studio 整合式開發環境中設定 \/ 定義|  
|1.  在 \[方案總管\] 中選取專案。  在 \[專案\] 功能表上，按一下 \[屬性\]。  如需詳細資訊，請參閱[Introduction to the Project Designer](http://msdn.microsoft.com/zh-tw/898dd854-c98d-430c-ba1b-a913ce3c73d7)。<br />2.  按一下 \[編譯\] 索引標籤。<br />3.  按一下 \[**進階**\]。<br />4.  修改 \[自訂常數\] 方塊中的值。|  
  
## 範例  
 下列程式碼會定義然後使用兩個條件式編譯器常數。  
  
 [!code-vb[VbVbalrCompiler#45](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/define_1.vb)]  
  
## 請參閱  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\#If...Then...\#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md)   
 [\#Const Directive](../../../visual-basic/language-reference/directives/const-directive.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)