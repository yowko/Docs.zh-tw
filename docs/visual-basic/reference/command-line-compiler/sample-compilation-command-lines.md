---
title: "編譯命令列範例 (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "命令列，編譯器"
  - "編譯，命令列"
  - "命令列編譯器"
  - "編譯原始程式碼，從命令列"
  - "Visual Basic 編譯器，範例命令列"
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 編譯命令列範例 (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

在 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 中編譯 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] 程式的替代用法，就是您可以從命令列進行編譯，以產生可執行 \(.exe\) 檔或動態連結程式庫 \(.dll\) 檔。  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 命令列編譯器 \(Compiler\) 支援一組完整的選項，可控制輸入和輸出檔、組件 \(Assembly\)、偵錯和前置處理器 \(Preprocessor\) 選項。  每個選項都有兩種可交換的形式：`-``option` 和 `/``option`。  這份文件只顯示 `/``option` 形式。  
  
 下表列出一些您可自行修改使用的命令列範例。  
  
|若要|使用|  
|--------|--------|  
|編譯 File.vb 和建立 File.exe|`vbc /reference:Microsoft.VisualBasic.dll File.vb`|  
|編譯 File.vb 和建立 File.dll|`vbc /target:library File.vb`|  
|編譯 File.vb 和建立 My.exe|`vbc /out:My.exe File.vb`|  
|開啟最佳化並定義 `DEBUG` 符號，在目前的目錄中編譯所有的 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 檔，產生 File2.exe|`vbc /define:DEBUG=1 /optimize /out:File2.exe *.vb`|  
|在目前的目錄中編譯所有的 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 檔案，產生 File2.dll 的偵錯版本，但不顯示標誌或警告|`vbc /target:library /out:File2.dll /nowarn /nologo /debug *.vb`|  
|將目前目錄中所有的 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 檔案編譯為 Something.dll|`vbc /target:library /out:Something.dll *.vb`|  
  
 從命令列編譯時，必須透過 `/reference` 編譯器選項，明確參考 Microsoft [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 執行階段程式庫。  
  
> [!TIP]
>  使用 Visual Studio IDE 中，當您建立專案，您可以顯示有關相關聯的 **vbc** 命令的資訊與其在輸出視窗中的編譯器選項。  若要顯示這項資訊，請開啟 [選項對話方塊, 專案和方案, 建置和執行](/visual-studio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)，然後將 \[**MSBuild 專案建置輸出詳細等級**\] 設定為 \[**一般**\] 或較高層級的詳細等級。  如需詳細資訊，請參閱[如何：檢閱、儲存和設定建置記錄檔](../Topic/How%20to:%20View,%20Save,%20and%20Configure%20Build%20Log%20Files.md)。  
  
## 請參閱  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)