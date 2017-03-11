---
title: "/debug (Visual Basic) | Microsoft Docs"
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
  - "debug compiler switches"
  - "/debug compiler option [Visual Basic]"
  - "-debug compiler option [Visual Basic]"
  - "debug compiler option [Visual Basic]"
ms.assetid: c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# /debug (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

讓編譯器產生偵錯資訊，並將其置於輸出檔。  
  
## 語法  
  
```  
/debug[+ | -]  
' -or-  
/debug:[full | pdbonly]  
```  
  
## 引數  
  
|||  
|-|-|  
|詞彙|定義|  
|`+`  &#124; `-`|選擇項。  指定 `+` 或 `/debug`，讓編譯器產生偵錯資訊，並將其置於 .pdb 檔案中。  指定 `-` 的效果與未指定 `/debug` 的效果相同。|  
|`full`  &#124; `pdbonly`|選擇項。  指定編譯器所產生的偵錯資訊類型。  若未指定 `/debug:pdbonly`，則預設值為 `full`，可讓您將偵錯工具附加至執行中的程式。  `pdbonly` 引數可以讓程式在偵錯工具中啟動時進行原始程式碼偵錯，但是只會在執行中的程式已附加到偵錯工具時，才會顯示組合語言程式碼。|  
  
## 備註  
 請使用這個選項來建立偵錯組建。  如果您沒有指定 `/debug`、`/debug+` 或 `/debug:full`，就無法偵錯程式的輸出檔。  
  
 在預設情況下，並不會發出偵錯資訊 \(`/debug-`\)。  若要發出偵錯資訊，請指定 `/debug` 或 `/debug+`。  
  
 如需如何設定應用程式偵錯效能的相關資訊，請參閱[使映像偵錯更容易](../Topic/Making%20an%20Image%20Easier%20to%20Debug.md)。  
  
||  
|-|  
|若要在 Visual Studio 整合式開發環境中設定 \/debug|  
|1.  在 \[**方案總管**\] 中選取專案之後，請在 \[**專案**\] 功能表上，按一下 \[**屬性**\]。  如需詳細資訊，請參閱[Introduction to the Project Designer](http://msdn.microsoft.com/zh-tw/898dd854-c98d-430c-ba1b-a913ce3c73d7)。<br />2.  按一下 \[**編譯**\] 索引標籤。<br />3.  按一下 \[**進階編譯選項**\]。<br />4.  修改 \[**產生偵錯資訊**\] 方塊中的值。|  
  
## 範例  
 下列範例會將偵錯資訊置於輸出檔 `App.exe` 中。  
  
```  
vbc /debug /out:app.exe test.vb  
```  
  
## 請參閱  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)