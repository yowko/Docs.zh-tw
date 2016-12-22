---
title: "從命令列建置 (Visual Basic) | Microsoft Docs"
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
  - "組建 [Visual Basic]，命令列"
  - "Visual Basic 編譯器，關於 Visual Basic 編譯器"
  - "命令列 [Visual Basic]，編譯器"
  - "命令列 [Visual Basic]，建置"
  - "命令列 [Visual Basic]，組建"
  - "編譯器，從命令列叫用"
  - "命令列組建"
  - "編譯原始程式碼"
  - "命令列編譯器，Visual Basic"
  - "命令列 [Visual Basic]，Visual Basic"
ms.assetid: e61947e9-a42e-4717-a699-5f70a98cdd03
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 從命令列建置 (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 專案是由一或數個個別的原始程式檔 \(Source File\) 所組成。  在稱為編譯 \(Compilation\) 的處理序 \(Process\) 中，這些檔案將匯集成為一個套件 \(Package\)，即像應用程式般執行的單一可執行檔。  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 提供了命令列編譯器，做為從 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] 整合開發環境 \(IDE\) 內編譯程式的替代方案。  命令列編譯器是設計成供您在不需要完整的 IDE 功能時使用，例如，當您在使用或寫入系統記憶體或存放空間有限的電腦時。  
  
 從命令列編譯時，必須透過 `/reference` 編譯器選項，明確參考 Microsoft [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 執行階段程式庫。  
  
 若要從 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] IDE 中編譯原始程式檔，請選擇 \[**建置**\] 功能表的 \[**建置**\] 命令。  
  
> [!TIP]
>  使用 Visual Studio IDE 時，就會在專案檔中，您可以顯示有關相關聯的 **vbc** 命令的詳細資訊和其在輸出視窗中的參數。  若要顯示這項資訊，請開啟 [選項對話方塊, 專案和方案, 建置和執行](/visual-studio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)，然後將 \[**MSBuild 專案建置輸出詳細等級**\] 設定為 \[**一般**\] 或較高層級的詳細等級。  如需詳細資訊，請參閱[如何：檢閱、儲存和設定建置記錄檔](../Topic/How%20to:%20View,%20Save,%20and%20Configure%20Build%20Log%20Files.md)。  
  
 您可以編譯專案 \(.vbproj\) 使用 MSBuild，檔案會在命令提示字元。  如需詳細資訊，請參閱[Command\-Line Reference](/visual-studio/msbuild/msbuild-command-line-reference)與[逐步解說：使用 MSBuild](../Topic/Walkthrough:%20Using%20MSBuild.md)。  
  
## 在本節中  
 [How to: Invoke the Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)  
 描述如何在 MS\-DOS 命令提示字元或從特定的子目錄中叫用 \(Invoke\) 命令列編譯器。  
  
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 提供可自行修改使用的命令列範例清單。  
  
## 相關章節  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)  
 提供依字母順序或用途來排列的編譯器選項清單。  
  
 [Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 描述如何編譯程式碼的特定區段。  
  
 [在 Visual Studio 中建置和清除專案與方案](/visual-studio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)  
 描述如何組織包含在不同組建 \(Build\) 中的內容、選擇專案屬性和確保按正確的順序建置 \(Build\) 專案。