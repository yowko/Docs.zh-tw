---
title: 從命令列建置 (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- builds [Visual Basic], command-line
- Visual Basic compiler, about Visual Basic compiler
- command line [Visual Basic], compilers
- command line [Visual Basic], building from
- command line [Visual Basic], builds
- compilers [Visual Basic], invoking from command line
- command-line builds
- compiling source code
- command-line compilers [Visual Basic], Visual Basic
- command line [Visual Basic], Visual Basic
ms.assetid: e61947e9-a42e-4717-a699-5f70a98cdd03
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1fd4054838925267647986a5166fd88037b17fae
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="building-from-the-command-line-visual-basic"></a>從命令列建置 (Visual Basic)
Visual Basic 專案是由一或多個不同的來源檔案所組成。 在稱為編譯過程中，這些檔案會回到一起成單一套件，可以為應用程式執行單一可執行檔。  
  
 Visual Basic 提供命令列編譯器編譯程式從替代[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]整合式的開發環境 (IDE)。 命令列編譯器可供您在不需要完整的 IDE 功能的情況 — 例如，當您使用或撰寫具有有限的系統記憶體或儲存空間的電腦。  
  
  若要編譯原始程式檔從[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]IDE 中，選擇**建置**命令**建置**功能表。  
  
> [!TIP]
>  當您使用 Visual Studio IDE 建置專案檔時，您可以顯示相關聯的相關資訊**vbc**命令，並在 [輸出] 視窗中的其參數。 若要顯示這項資訊，請開啟[選項對話方塊、 專案和方案、 建置和執行](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)，然後設定**MSBuild 專案組建輸出詳細等級**至**一般**或更高的層級的詳細資訊。 如需詳細資訊，請參閱[如何：檢閱、儲存和設定建置記錄檔](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7)。  
  
 您可以使用 MSBuild 編譯專案 (.vbproj) 檔案，在命令提示字元。 如需詳細資訊，請參閱[命令列參照](/visualstudio/msbuild/msbuild-command-line-reference)和[逐步解說： 使用 MSBuild](/visualstudio/msbuild/walkthrough-using-msbuild)。  
  
## <a name="in-this-section"></a>本節內容  
 [操作說明：叫用命令列編譯器](../../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)  
 描述如何叫用命令列編譯器在 MS-DOS 提示，或從特定的子目錄。  
  
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 提供命令列範例，您可以修改供自己使用的清單。  
  
## <a name="related-sections"></a>相關章節  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)  
 提供編譯器選項，依字母順序或依目的的清單。  
  
 [條件式編譯](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 說明如何編譯的程式碼的特定區段。  
  
 [在 Visual Studio 中建置和清除專案與方案](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)  
 描述如何組織將會包含在不同的組建，選擇 專案屬性，以及確保以正確的順序建置專案。
