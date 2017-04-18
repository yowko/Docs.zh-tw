---
title: "從命令列 (Visual Basic) 建置 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- builds [Visual Basic], command-line
- Visual Basic compiler, about Visual Basic compiler
- command line [Visual Basic], compilers
- command line [Visual Basic], building from
- command line [Visual Basic], builds
- compilers, invoking from command line
- command-line builds
- compiling source code
- command-line compilers, Visual Basic
- command line [Visual Basic], Visual Basic
ms.assetid: e61947e9-a42e-4717-a699-5f70a98cdd03
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 49f84c221e18457ab46534ca46da7c4764a8ee40
ms.lasthandoff: 03/13/2017

---
# <a name="building-from-the-command-line-visual-basic"></a>從命令列建置 (Visual Basic)
A[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]專案由一或多個不同的原始程式檔所組成。 在稱為編譯過程中，這些檔案組成成一個套件，可以為應用程式執行單一可執行檔。  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]提供命令列編譯器編譯程式從替代[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]整合式的開發環境 (IDE)。 命令列編譯器設計成供您在不需要完整的 IDE 功能 — 例如，當您要使用還是寫入電腦具有有限的系統記憶體或儲存體空間。  
  
 當從命令列進行編譯，您必須明確參考 Microsoft[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]透過執行階段程式庫`/reference`編譯器選項。  
  
 若要編譯原始程式檔內[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]IDE 中，選擇 **建置**命令**建置**功能表。  
  
> [!TIP]
>  當您使用 Visual Studio IDE 建置專案檔時，您可以顯示相關聯的相關資訊**vbc**命令，並在 [輸出] 視窗中的，其參數。 若要顯示這項資訊，請開啟[選項對話方塊、 專案和方案、 建置和執行](https://docs.microsoft.com/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run)，然後設定**MSBuild 專案建置輸出詳細程度**至**正常**或更高的層級的詳細資訊。 如需詳細資訊，請參閱[如何：檢閱、儲存和設定建置記錄檔](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7)。  
  
 您可以使用 MSBuild 編譯專案 (.vbproj) 檔案，在命令提示字元。 如需詳細資訊，請參閱[命令列參考](https://docs.microsoft.com/visualstudio/msbuild/msbuild-command-line-reference)和[逐步解說︰ 使用 MSBuild](http://msdn.microsoft.com/library/b8a8b866-bb07-4abf-b9ec-0b40d281c310)。  
  
## <a name="in-this-section"></a>本章節內容  
 [如何：叫用命令列編譯器](../../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)  
 說明如何叫用命令列編譯器在 MS-DOS 命令提示字元，或從特定的子目錄。  
  
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 提供命令列範例，您可以修改供自己使用的清單。  
  
## <a name="related-sections"></a>相關章節  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)  
 提供依字母順序或依用途的編譯器選項的清單。  
  
 [條件式編譯](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 描述如何編譯程式碼的特定區段。  
  
 [在 Visual Studio 中建置和清除專案與方案](https://docs.microsoft.com/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)  
 描述如何組織將會包含在不同的組建，選擇 專案屬性，以及確保以正確的順序建置專案。
