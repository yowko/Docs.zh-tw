---
title: -最佳化
ms.date: 07/20/2015
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
ms.openlocfilehash: 2f066835c5f864538f281d4c58772e0e60c132f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="-optimize"></a>-最佳化
啟用或停用編譯器最佳化。  
  
## <a name="syntax"></a>語法  
  
```  
-optimize[ + | - ]  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`+` &#124; `-`|選擇性。 `-optimize-`選項會停用編譯器最佳化。 `-optimize+`選項啟用最佳化。 根據預設，會停用最佳化。|  
  
## <a name="remarks"></a>備註  
 編譯器最佳化可讓您的輸出檔案變得更小、更快、更有效率。 不過，因為最佳化導致輸出檔中的程式碼重新排列`-optimize+`可能會造成偵錯困難。  
  
 使用產生的所有模組`-target:module`組件必須使用相同`-optimize`設定與組件。 如需詳細資訊，請參閱[-目標 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)。  
  
 您可以結合`-optimize`和`-debug`選項。  
  
|若要設定的最佳化 Visual Studio 整合式的開發環境中|  
|---|  
|1.在 **方案總管**中選取專案。 在 [專案] 功能表上，按一下 [屬性]。<br />     <br />2.按一下 [編譯] 索引標籤。<br />3.按一下 [ **進階** ] 按鈕。<br />4.修改**啟用最佳化**核取方塊。|  
  
## <a name="example"></a>範例  
 下列程式碼編譯`T2.vb`並啟用編譯器最佳化。  
  
```console
vbc t2.vb -optimize  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-偵錯 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md)  
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [-目標 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
