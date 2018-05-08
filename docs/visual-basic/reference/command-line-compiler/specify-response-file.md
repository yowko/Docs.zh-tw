---
title: '@ (指定回應檔) (Visual Basic)'
ms.date: 03/13/2018
helpviewer_keywords:
- '@ (Specify Response File) compiler option [Visual Basic]'
ms.assetid: a6847eaa-e5f9-4303-9421-45b55484b9ca
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4ad4201dcc094364899984e13c85f2f43a6467ff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="-specify-response-file-visual-basic"></a>@ (指定回應檔) (Visual Basic)
指定包含編譯器選項的檔案和要編譯的原始程式碼檔案。  
  
## <a name="syntax"></a>語法  
  
```  
@response_file  
```  
  
## <a name="arguments"></a>引數  
 `response_file`  
 必要。 列出編譯器選項或原始程式碼檔案編譯的檔案。 將檔案名稱括在引號 ("") 如果包含空格。  
  
## <a name="remarks"></a>備註  
 編譯器處理編譯器選項和如同已指定命令列上，指定回應檔中的原始程式碼檔。  
  
 若要指定多個回應檔編譯中，指定多個回應檔選項，如下所示。  
  
```  
@file1.rsp @file2.rsp  
```  
  
 在回應檔案、 多個編譯器選項和原始程式檔可以出現在一行上。 單一的編譯器選項規格必須出現在一行 （無法跨越多行）。 回應檔案可以有開頭的註解`#`符號。  
  
 您可以結合一或多個回應檔中指定選項在命令列上指定的選項。 當它遇到它們，編譯器會處理命令選項。 因此，命令列引數可以覆寫先前列出的選項，在回應檔案中。 相反地，在回應檔中的選項會覆寫在命令列或其他回應檔中先前所列的選項。  
  
 Visual Basic 提供 Vbc.rsp 檔案，位於與 Vbc.exe 檔案相同的目錄中。 除非預設包含 Vbc.rsp 檔案進行`-noconfig`選項使用。 如需詳細資訊，請參閱[-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)。  
  
> [!NOTE]
>  `@`選項不是從 Visual Studio 開發環境中使用; 其只有在從命令列編譯時。  
  
## <a name="example"></a>範例  
 下列幾行是從範例回應檔案。  
  
```console
# build the first output file  
-target:exe   
-out:MyExe.exe  
source1.vb   
source2.vb  
```  
  
## <a name="example"></a>範例  
 下列範例示範如何使用`@`選項名為的回應檔案搭配`File1.rsp`。  
  
```console
vbc @file1.rsp  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)  
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
