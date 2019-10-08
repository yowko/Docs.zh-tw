---
title: -optimize
ms.date: 07/20/2015
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
ms.openlocfilehash: e8daf4a49123623b6470bc3c6281869f1b9b3d0f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005379"
---
# <a name="-optimize"></a>-optimize
啟用或停用編譯器優化。  
  
## <a name="syntax"></a>語法  
  
```console  
-optimize[ + | - ]  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`+` &#124; `-`|選擇性。 @No__t-0 選項會停用編譯器優化。 @No__t-0 選項會啟用優化。 根據預設，會停用最佳化。|  
  
## <a name="remarks"></a>備註  
 編譯器最佳化可讓您的輸出檔案變得更小、更快、更有效率。 不過，由於優化會導致輸出檔中的程式碼重新排列，`-optimize+` 會使偵錯工具變得很棘手。  
  
 為元件產生的所有模組 `-target:module`，都必須使用與元件相同的 @no__t 1 設定。 如需詳細資訊，請參閱[-target （Visual Basic）](../../../visual-basic/reference/command-line-compiler/target.md)。  
  
 您可以結合 `-optimize` 和 `-debug` 選項。  
  
|在 Visual Studio 的整合式開發環境中設定-optimize|  
|---|  
|1.在 **方案總管**中選取專案。 在 [專案] 功能表上，按一下 [屬性]。<br />     <br />2.按一下 [編譯] 索引標籤。<br />3.按一下 [ **進階** ] 按鈕。<br />4.修改 [**啟用優化**] 核取方塊。|  
  
## <a name="example"></a>範例  
 下列程式碼會編譯 `T2.vb`，並啟用編譯器優化。  
  
```console
vbc t2.vb -optimize  
```  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [-debug （Visual Basic）](../../../visual-basic/reference/command-line-compiler/debug.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-target （Visual Basic）](../../../visual-basic/reference/command-line-compiler/target.md)
