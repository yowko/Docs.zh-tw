---
title: "/verbose | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "verbose compiler option [Visual Basic]"
  - "-verbose compiler option [Visual Basic]"
  - "/verbose compiler option [Visual Basic]"
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /verbose
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

讓編譯器產生詳細資訊狀態和錯誤訊息。  
  
## 語法  
  
```  
/verbose[+ | -]  
```  
  
## 引數  
 `+` &#124; `-`  
 選擇項。  指定 `/verbose` 和指定 `/verbose+` 相同，會使編譯器發出詳細訊息。  此選項預設值為 `/verbose-`。  
  
## 備註  
 `/verbose` 選項會顯示有關編譯器所發出錯誤總數的資訊，報告模組正在載入的組件，以及顯示目前正在進行編譯的檔案。  
  
> [!NOTE]
>  `/verbose` 選項無法在 Visual Studio 開發環境內使用；只有在命令列編譯時才能使用。  
  
## 範例  
 下列程式碼會編譯 `In.vb`，並指示編譯器顯示詳細的狀態資訊。  
  
```  
vbc /verbose in.vb  
```  
  
## 請參閱  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)