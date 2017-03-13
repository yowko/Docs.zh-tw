---
title: "/optionexplicit | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "/optionexplicit"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "/optionexplicit compiler option [Visual Basic]"
  - "optionexplicit compiler option [Visual Basic]"
  - "-optionexplicit compiler option [Visual Basic]"
ms.assetid: 5d296ab3-bafe-4c4d-9887-78f162ed86c7
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# /optionexplicit
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

如果變數未在使用前宣告，編譯器則會報告錯誤。  
  
## 語法  
  
```  
/optionexplicit[+ | -]  
```  
  
## 引數  
 `+` &#124; `-`  
 選擇項。  指定 `/optionexplicit+` 需要明確宣告變數。  `/optionexplicit+` 選項是預設值，且與 `/optionexplicit` 相同。  `/optionexplicit-` 選項啟用隱含宣告變數。  
  
## 備註  
 如果原始程式碼檔包含 [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md)，則陳述式會覆寫 `/optionexplicit` 命令列編譯器設定。  
  
### 若要在 Visual Studio IDE 中設定 \/optionexplicit  
  
1.  在 \[**方案總管**\] 中選取專案。  在 \[**專案**\] 功能表上，按一下 \[**屬性**\]。  如需詳細資訊，請參閱[Introduction to the Project Designer](http://msdn.microsoft.com/zh-tw/898dd854-c98d-430c-ba1b-a913ce3c73d7)。  
  
2.  按一下 \[**編譯**\] 索引標籤。  
  
3.  修改 \[**Option Explicit**\] 方塊中的值。  
  
## 範例  
 使用 `/optionexplicit-` 時會編譯下列程式碼。  
  
 [!code-vb[VbVbalrCompiler#5](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/optionexplicit_1.vb)]  
  
## 請參閱  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)   
 [\/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)   
 [\/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md)   
 [選項對話方塊、專案、Visual Basic 預設值](/visual-studio/ide/reference/visual-basic-defaults-projects-options-dialog-box)