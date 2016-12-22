---
title: "/rootnamespace | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/rootnamespace"
  - "rootnamespace"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "/rootnamespace compiler option [Visual Basic]"
  - "-rootnamespace compiler option [Visual Basic]"
  - "rootnamespace compiler option [Visual Basic]"
ms.assetid: e9245edf-6bef-420d-a7c7-324117752783
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /rootnamespace
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

為所有型別宣告指定命名空間。  
  
## 語法  
  
```  
/rootnamespace:namespace  
```  
  
## 引數  
  
|||  
|-|-|  
|詞彙|定義|  
|`namespace`|括住目前專案所有型別宣告的命名空間名稱。|  
  
## 備註  
 如果使用 Visual Studio 可執行檔 \(Devenv.exe\) 來編譯 Visual Studio 整合開發環境中建立的專案，請使用 `/rootnamespace` 來指定 <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> 屬性值。  如需詳細資訊，請參閱 [Devenv 命令列參數](/visual-studio/ide/reference/devenv-command-line-switches)。  
  
 請使用 Common Language Runtime MSIL 反組譯工具 \(I`ldasm.exe`\) 來檢視您輸出檔中的命名空間名稱。  
  
||  
|-|  
|若要在 Visual Studio 整合式開發環境中設定 \/rootnamespace|  
|1.  在 \[**方案總管**\] 中選取專案。  在 \[**專案**\] 功能表上，按一下 \[**屬性**\]。  如需詳細資訊，請參閱[Introduction to the Project Designer](http://msdn.microsoft.com/zh-tw/898dd854-c98d-430c-ba1b-a913ce3c73d7)。<br />2.  按一下 \[**應用程式**\] 索引標籤。<br />3.  修改 \[**根命名空間**\] 方塊中的值。|  
  
## 範例  
 下列程式碼會編譯 `In.vb`，並將所有型別宣告 \(Type Declaration\) 括在 `mynamespace` 命名空間中。  
  
```  
vbc /rootnamespace:mynamespace in.vb  
```  
  
## 請參閱  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Ildasm.exe \(IL Disassembler\)](../Topic/Ildasm.exe%20\(IL%20Disassembler\).md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)