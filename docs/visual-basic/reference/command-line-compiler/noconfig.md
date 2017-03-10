---
title: "/noconfig | Microsoft Docs"
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
  - "noconfig compiler option [Visual Basic]"
  - "-noconfig compiler option [Visual Basic]"
  - "/noconfig compiler option [Visual Basic]"
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# /noconfig
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

指定編譯器 \(Compiler\) 不應該自動參考常用的 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 組件 \(Assembly\) 或匯入 `System` 和 `Microsoft.VisualBasic` 命名空間。  
  
## 語法  
  
```  
/noconfig  
```  
  
## 備註  
 `/noconfig` 選項會告訴編譯器，不要使用與 Vbc.exe 檔位在相同目錄的 Vbc.rsp 檔來進行編譯。  Vbc.rsp 檔會參考常用的 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] 組件並匯入 `System` 和 `Microsoft.VisualBasic` 命名空間。  除非已指定 `/nostdlib` 選項，否則編譯器會隱含參考 System.dll 組件。  `/nostdlib` 選項會告訴編譯器，不要使用 Vbc.rsp 進行編譯或自動參考 System.dll 組件。  
  
> [!NOTE]
>  一定會參考 Mscorlib.dll 和 Microsoft.VisualBasic.dll 組件。  
  
 您可修改 Vbc.rsp 檔，以指定每個 Vbc.exe 編譯應該包含的其他編譯器選項 \(不適用指定 `/noconfig` 選項時\)。  如需詳細資訊，請參閱 [@ \(Specify Response File\)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)。  
  
 編譯器最後才會處理傳遞至 `vbc` 命令的選項。  因此，命令列中的任何選項都會覆寫 Vbc.rsp 檔中相同選項的設定。  
  
> [!NOTE]
>  `/noconfig` 選項無法在 Visual Studio 開發環境內使用；只有在命令列編譯時才能使用。  
  
## 請參閱  
 [\/nostdlib](../../../visual-basic/reference/command-line-compiler/nostdlib.md)   
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [@ \(Specify Response File\)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)   
 [\/reference](../../../visual-basic/reference/command-line-compiler/reference.md)