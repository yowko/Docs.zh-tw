---
title: "/langversion (Visual Basic) | Microsoft Docs"
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
  - "/langversion compiler option [Visual Basic]"
  - "langversion compiler option [Visual Basic]"
  - "-langversion compiler option [Visual Basic]"
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# /langversion (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

讓編譯器只能接受指定之 Visual Basic 語言版本中所包含的語法。  
  
## 語法  
  
```  
/langversion:version  
```  
  
## 引數  
 `version`  
 必要項。  編譯期間要使用的語言版本。  可接受的值為 `9`、`9.0`、`10` 和 `10.0`。  
  
## 備註  
 `/langversion` 選項會指定編譯器接受的語法。  例如，如果您指定語言版本為 9.0，則編譯器會對只在 10.0 \(含\) 以後版本中有效的語法產生錯誤。  
  
 當您開發以不同 .NET Framework 版本為目標的應用程式時，可以使用這個選項。  例如，如果以 .NET Framework 3.5 為目標，就可以使用這個選項來確保不會使用語言版本 10.0 的語法。  
  
 您只能使用命令列直接設定 `/langversion`。  如需詳細資訊，請參閱[以特定的 .NET Framework 版本為目標](/visual-studio/ide/targeting-a-specific-dotnet-framework-version)。  
  
## 範例  
 下列程式碼會以 Visual Basic 9.0 為目標來編譯 `sample.vb`。  
  
```  
vbc /langversion:9.0 sample.vb  
```  
  
## 請參閱  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [以特定的 .NET Framework 版本為目標](/visual-studio/ide/targeting-a-specific-dotnet-framework-version)