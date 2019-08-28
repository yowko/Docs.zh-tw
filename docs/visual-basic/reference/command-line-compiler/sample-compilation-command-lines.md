---
title: 編譯命令列範例 (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- command line [Visual Basic], compilers
- compilation [Visual Basic], command-line
- command-line compilers
- compiling source code [Visual Basic], from command line
- Visual Basic compiler, sample command lines
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
ms.openlocfilehash: b7879c23bc64269c793c21b61b84d6f0fd4bdc24
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046285"
---
# <a name="sample-compilation-command-lines-visual-basic"></a>範例編譯命令列 (Visual Basic)

除了從 Visual Studio 內編譯 Visual Basic 程式以外, 您還可以從命令列進行編譯, 以產生可執行檔 (.exe) 或動態連結程式庫 (.dll) 檔案。

Visual Basic 命令列編譯器支援一組完整的選項, 可控制輸入和輸出檔案、元件和 debug 和預處理器選項。 每個選項都有兩種可交換`-option`的`/option`形式: 和。 本檔只`-option`會顯示表單。

下表列出您可以修改以供自己使用的一些範例命令列。

|以|使用|
|--------|---------|
|編譯 .vb 和 create File .exe|`vbc -reference:Microsoft.VisualBasic.dll File.vb`|
|編譯 .vb 和 create File .dll|`vbc -target:library File.vb`|
|編譯 .vb 並建立 My .exe|`vbc -out:My.exe File.vb`|
|編譯 .vb 並建立名為 File .dll 的程式庫和參考元件|`vbc -target:library -ref:.\debug\bin\ref\file.dll File.vb`|
|編譯目前目錄中的所有 Visual Basic 檔案, 並在其上進行`DEBUG`優化和定義的符號, 產生 File2 .exe|`vbc -define:DEBUG=1 -optimize -out:File2.exe *.vb`|
|編譯目前目錄中的所有 Visual Basic 檔案, 產生 File2 的 debug 版本, 而不顯示標誌或警告|`vbc -target:library -out:File2.dll -nowarn -nologo -debug *.vb`|
|將目前目錄中的所有 Visual Basic 檔案編譯為 .dll|`vbc -target:library -out:Something.dll *.vb`|

> [!TIP]
> 當您使用 Visual Studio IDE 來建立專案時, 您可以在 [輸出] 視窗中, 使用編譯器選項來顯示相關聯的**vbc**命令資訊。 若要顯示這項資訊, 請開啟 [[選項] 對話方塊、[專案和方案]、[建立並執行]](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), 然後將 [ **MSBuild 專案組建輸出詳細**資訊] 設定為 [**一般**] 或更高層級的詳細資訊。

## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [條件式編譯](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
