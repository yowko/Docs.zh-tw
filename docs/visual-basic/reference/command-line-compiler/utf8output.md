---
title: "/utf8output (Visual Basic) | Microsoft Docs"
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
  - "-utf8output compiler option [Visual Basic]"
  - "utf8output compiler option [Visual Basic]"
  - "/utf8output compiler option [Visual Basic]"
ms.assetid: 8ab36b1e-027a-49ac-85b4-f48997d9e4d6
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /utf8output (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

使用 UTF\-8 編碼方式顯示編譯器輸出。  
  
## 語法  
  
```  
/utf8output[+ | -]  
```  
  
## 引數  
 `+` &#124; `-`  
 選擇項。  這個選項的預設值為 `/utf8output-`，這表示編譯器輸出不會使用 UTF\-8 編碼。  指定 `/utf8output` 就相當於指定 `/utf8output+`。  
  
## 備註  
 在某些國際組態中，編譯器的輸出無法正確地顯示在主控台中。  在這類情況下，請使用 `/utf8output`，並將編譯器輸出重新導向至檔案。  
  
> [!NOTE]
>  `/utf8output` 選項無法在 Visual Studio 開發環境內使用；只有在命令列編譯時才能使用。  
  
## 範例  
 下列程式碼會編譯 `In.vb`，並指示編譯器使用 UTF\-8 編碼來顯示輸出。  
  
```  
vbc /utf8output in.vb  
```  
  
## 請參閱  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)