---
title: "/optionstrict | Microsoft Docs"
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
  - "/optionstrict"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "-optionstrict compiler option [Visual Basic]"
  - "optionstrict compiler option [Visual Basic]"
  - "/optionstrict compiler option [Visual Basic]"
ms.assetid: c7b10086-0fa4-49db-b3c8-4ae0db5957da
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /optionstrict
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

使用嚴格型別語意來限制隱含型別轉換。  
  
## 語法  
  
```  
/optionstrict[+ | -]  
/optionstrict[:custom]  
```  
  
## 引數  
 `+` &#124; `-`  
 選擇項。  `/optionstrict+` 選項會限制隱含型別轉換。  此選項預設值為 `/optionstrict-`。  `/optionstrict+` 選項與 `/optionstrict` 相同。  您可以為寬鬆型別語意 \(Semantics\) 使用這兩個選項。  
  
 `custom`  
 必要項。  不適用嚴格的語意時發出警告。  
  
## 備註  
 當 `/optionstrict+` 生效時，只可隱含地進行擴展型別轉換。  隱含的縮小型別轉換則會視為錯誤而加以報告，例如將 `Decimal` 型別物件指派給整數型別物件。  
  
 若要產生隱含縮小型別轉換的警告，請使用 `/optionstrict:custom`。  使用 `/nowarn:numberlist` 可忽略特定警告，`/warnaserror:numberlist` 則會將特定警告視為錯誤。  
  
### 若要在 Visual Studio IDE 中設定 \/optionstrict  
  
1.  在 \[**方案總管**\] 中選取專案。  在 \[**專案**\] 功能表上，按一下 \[**屬性**\]。 如需詳細資訊，請參閱[Introduction to the Project Designer](http://msdn.microsoft.com/zh-tw/898dd854-c98d-430c-ba1b-a913ce3c73d7)。  
  
2.  按一下 \[**編譯**\] 索引標籤。  
  
3.  修改 \[**Option Strict**\] 方塊中的值。  
  
### 若要以程式設計方式設定 \/optionstrict  
  
-   請參閱 [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)。  
  
## 範例  
 下列程式碼會使用嚴格型別語意來編譯 `Test.vb`。  
  
```  
vbc /optionstrict+ test.vb  
```  
  
## 請參閱  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)   
 [\/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)   
 [\/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)   
 [\/nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)   
 [\/warnaserror](../../../visual-basic/reference/command-line-compiler/warnaserror.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [選項對話方塊、專案、Visual Basic 預設值](/visual-studio/ide/reference/visual-basic-defaults-projects-options-dialog-box)