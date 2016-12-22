---
title: "/filealign | Microsoft Docs"
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
  - "sections compiler option [Visual Basic]"
  - "alignment compiler option [Visual Basic]"
  - "-filealign compiler option [Visual Basic]"
  - "section alignment"
  - "/filealign compiler option [Visual Basic]"
  - "filealign compiler option [Visual Basic]"
ms.assetid: cc61ec3d-ad38-4b28-9659-099d73cad099
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /filealign
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

指定要對齊輸出檔案區段的位置。  
  
## 語法  
  
```  
/filealign:number  
```  
  
## 引數  
 `number`  
 必要項。  用來指定在輸出檔的區段對齊之值。  有效值為 512、1024、2048、4096 和 8192。  這些值是以位元組為單位。  
  
## 備註  
 您可以使用 `/filealign` 選項來指定輸出檔中的區段對齊。  區段是「可攜式執行檔 \(PE\)」檔案中的連續記憶體區塊，包含程式碼或資料。  `/filealign` 選項可讓您利用非標準的對齊方式來編譯應用程式，大多數開發人員不需要使用這個選項。  
  
 每個區段是在多個 `/filealign` 值的界限上對齊。  沒有固定預設值。  如果沒有指定 `/filealign`，編譯器會在編譯時期選取一個預設值。  
  
 您可藉著指定區段大小來變更輸出檔的大小。  修改區段大小對將執行於較小裝置上的程式很有幫助。  
  
> [!NOTE]
>  `/filealign` 選項無法在 Visual Studio 開發環境內使用，只有在命令列編譯時才能使用。  
  
## 請參閱  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)