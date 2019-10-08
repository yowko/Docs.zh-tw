---
title: '@ (指定回應檔) (Visual Basic)'
ms.date: 03/13/2018
helpviewer_keywords:
- '@ (Specify Response File) compiler option [Visual Basic]'
ms.assetid: a6847eaa-e5f9-4303-9421-45b55484b9ca
ms.openlocfilehash: deab111cc669941a1cd7dc143dd699b6521221bb
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004987"
---
# <a name="-specify-response-file-visual-basic"></a>@ (指定回應檔) (Visual Basic)
指定檔案，其中包含要編譯的編譯器選項和原始程式碼檔。  
  
## <a name="syntax"></a>語法  
  
```console  
@response_file  
```  
  
## <a name="arguments"></a>引數  
 `response_file`  
 必要項。 列出要編譯之編譯器選項或原始程式碼檔案的檔案。 將檔案名括在引號（""）中（如果它包含空格）。  
  
## <a name="remarks"></a>備註  
 編譯器會處理在回應檔中指定的編譯器選項和原始程式碼檔，如同已在命令列上指定。  
  
 若要在編譯中指定一個以上的回應檔，請指定多個回應檔案選項，如下所示。  
  
```console  
@file1.rsp @file2.rsp  
```  
  
 在回應檔中，多個編譯器選項和原始程式碼檔可能會出現在一行上。 單一編譯器選項規格必須出現在一行（不能跨越多行）。 回應檔可以有以 `#` 符號開頭的批註。  
  
 您可以結合在命令列上指定的選項與一個或多個回應檔中指定的選項。 編譯器會在遇到命令選項時進行處理。 因此，命令列引數可以覆寫回應檔中先前列出的選項。 相反地，回應檔中的選項會覆寫先前在命令列或其他回應檔中列出的選項。  
  
 Visual Basic 提供 Vbc .rsp 檔案，該檔案位於與 Vbc 檔案相同的目錄中。 除非使用了 `-noconfig` 選項，否則預設會包含 Vbc 檔案。 如需詳細資訊，請參閱[-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)。  
  
> [!NOTE]
> @No__t-0 選項無法從 Visual Studio 開發環境中使用;只有在從命令列編譯時，才可以使用它。  
  
## <a name="example"></a>範例  
 下列幾行來自範例回應檔。  
  
```console
# build the first output file  
-target:exe   
-out:MyExe.exe  
source1.vb   
source2.vb  
```  
  
## <a name="example"></a>範例  
 下列範例示範如何使用 `@` 選項搭配名為 `File1.rsp` 的回應檔。  
  
```console
vbc @file1.rsp  
```  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
