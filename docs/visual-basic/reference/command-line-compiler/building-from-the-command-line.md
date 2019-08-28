---
title: 從命令列建置 (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 719ca45403ea56a655f06dbfea7c0fb7e32b34f7
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046434"
---
# <a name="building-from-the-command-line-visual-basic"></a>從命令列建置 (Visual Basic)

Visual Basic 專案是由一或多個不同的原始檔所組成。 在稱為編譯的程式期間, 這些檔案會結合成一個套件, 也就是可當做應用程式執行的單一可執行檔。

Visual Basic 提供命令列編譯器, 做為從 Visual Studio 整合式開發環境 (IDE) 中編譯器的替代方法。 命令列編譯器是針對您不需要 IDE 中完整功能集的情況所設計, 例如, 當您針對系統記憶體或儲存空間有限的電腦使用或寫入時。

若要從 Visual Studio IDE 內編譯來源檔案, 請從 [**組建**] 功能表選擇 [**組建**] 命令。

> [!TIP]
> 當您使用 Visual Studio IDE 來建立專案檔時, 可以在 [輸出] 視窗中顯示相關聯的**vbc**命令及其參數的相關資訊。 若要顯示這項資訊, 請開啟 [[選項] 對話方塊、[專案和方案]、[建立並執行]](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), 然後將 [ **MSBuild 專案組建輸出詳細**資訊] 設定為 [**一般**] 或更高層級的詳細資訊。 如需詳細資訊，請參閱[如何：查看、儲存和設定組建記錄](/visualstudio/ide/how-to-view-save-and-configure-build-log-files)檔。

您可以在命令提示字元中使用 MSBuild 來編譯專案 (. vbproj) 檔案。 如需詳細資訊, 請參閱[命令列參考](/visualstudio/msbuild/msbuild-command-line-reference)和[逐步解說:使用 MSBuild](/visualstudio/msbuild/walkthrough-using-msbuild)。

## <a name="in-this-section"></a>本節內容

[如何：叫用命令列編譯器](../../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) \
描述如何在 MS-DOS 提示字元或從特定子目錄叫用命令列編譯器。

[範例編譯命令列](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) \
提供範例命令列清單, 您可以針對自己的用途加以修改。

## <a name="related-sections"></a>相關章節

[Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md) \
提供編譯器選項清單, 以字母順序或依目的組織。

[條件式編譯](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md) \
描述如何編譯器代碼的特定區段。

[在 Visual Studio 中建置和清除專案與方案](/visualstudio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio) \
描述如何組織將包含在不同組建中的內容、選擇專案屬性, 並確保專案以正確的順序建立。
