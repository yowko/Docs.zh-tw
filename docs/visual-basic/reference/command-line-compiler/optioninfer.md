---
title: "/optioninfer | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "/optioninfer"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "-optioninfer compiler option [Visual Basic]"
  - "/optioninfer compiler option [Visual Basic]"
  - "optioninfer compiler option [Visual Basic]"
ms.assetid: f6c09db1-0553-464a-abe3-d4510c61d6ed
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# /optioninfer
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

可讓您在變數宣告中使用區域類型推斷。  
  
## 語法  
  
```  
/optioninfer[+ | -]  
```  
  
## 引數  
  
|||  
|-|-|  
|詞彙|定義|  
|`+`  &#124; `-`|選擇項。  指定 `/optioninfer+` 以啟用區域類型推斷，或是指定 `/optioninfer-` 以封鎖它。  未指定值的 `/optioninfer` 選項與 `/optioninfer+` 相同。  不存在 `/optioninfer` 參數時的預設值也是 `/optioninfer+`。  預設值是在 Vbc.rsp 回應檔中設定。|  
  
> [!NOTE]
>  您可以使用 `/noconfig` 選項來保留編譯器的內部預設值而不是 vbc.rsp 中所指定的預設值。  這個選項的編譯器預設值是 `/optioninfer-`。  
  
## 備註  
 如果原始程式碼檔包含 [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md)，陳述式會覆寫 `/optioninfer` 命令列編譯器設定。  
  
### 在 Visual Studio IDE 中設定 \/optioninfer  
  
1.  在 \[方案總管\] 中選取專案。  在 \[專案\] 功能表上，按一下 \[屬性\]。  如需詳細資訊，請參閱[NIB: Managing Project Properties with the Project Designer](http://msdn.microsoft.com/zh-tw/983f3c18-832f-4666-afec-74b716ff3e0e)。  
  
2.  在 \[編譯\] 索引標籤上，修改 \[選項推斷\] 方塊中的值。  
  
## 範例  
 下列程式碼會在已啟用區域類型推斷下編譯 `test.vb`。  
  
```  
vbc /optioninfer+ test.vb  
```  
  
## 請參閱  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)   
 [\/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)   
 [\/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md)   
 [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [選項對話方塊、專案、Visual Basic 預設值](/visual-studio/ide/reference/visual-basic-defaults-projects-options-dialog-box)   
 [專案設計工具、編譯頁 \(Visual Basic\)](/visual-studio/ide/reference/compile-page-project-designer-visual-basic)   
 [\/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)   
 [從命令列建置](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)