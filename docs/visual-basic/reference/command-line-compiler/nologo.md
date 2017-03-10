---
title: "/nologo (Visual Basic) | Microsoft Docs"
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
  - "-nologo compiler option [Visual Basic]"
  - "banners, suppressing startup"
  - "nologo compiler option [Visual Basic]"
  - "/nologo compiler option [Visual Basic]"
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# /nologo (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

隱藏在編譯期間顯示的著作權橫幅和資訊訊息。  
  
## 語法  
  
```  
/nologo  
```  
  
## 備註  
 如果您指定 `/nologo`，編譯器 \(Compiler\) 不會顯示著作權橫幅。  `/nologo` 預設為不作用。  
  
> [!NOTE]
>  `/nologo` 選項無法在 Visual Studio 開發環境內使用，只有在命令列編譯時才能使用。  
  
## 範例  
 下列程式碼會編譯 `T2.vb`，而且不會顯示著作權橫幅。  
  
```  
vbc /nologo t2.vb  
```  
  
## 請參閱  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)