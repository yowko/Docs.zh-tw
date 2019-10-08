---
title: -optioncompare
ms.date: 07/20/2015
f1_keywords:
- /optioncompare
- -optioncompare
helpviewer_keywords:
- optioncompare compiler option [Visual Basic]
- -optioncompare compiler option [Visual Basic]
- /optioncompare compiler option [Visual Basic]
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
ms.openlocfilehash: ee130073b95dfbab5616a54c188b09fa92ccc930
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005358"
---
# <a name="-optioncompare"></a>-optioncompare
指定如何進行字串比較。  
  
## <a name="syntax"></a>語法  
  
```console  
-optioncompare:{binary | text}  
```  
  
## <a name="remarks"></a>備註  
 您可以使用下列兩種形式的其中一種來指定 `-optioncompare`： `-optioncompare:binary` 表示使用二進位字串比較，而 `-optioncompare:text` 則使用文字字串比較。 根據預設，編譯器會使用 `-optioncompare:binary`。  
  
 在 Microsoft Windows 中，目前的字碼頁會決定二進位排序次序。 典型的二進位排序次序如下所示：  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 以文字為基礎的字串比較是以您系統的地區設定所決定的不區分大小寫文字排序次序為基礎。 一般文字排序次序如下所示：  
  
 `(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
### <a name="to-set--optioncompare-in-the-visual-studio-ide"></a>若要在 Visual Studio IDE 中設定-optioncompare  
  
1. 在 **方案總管**中選取專案。 在 [專案] 功能表上，按一下 [屬性]。   
  
2. 按一下 [編譯] 索引標籤。  
  
3. 修改 [**選項比較**] 方塊中的值。  
  
### <a name="to-set--optioncompare-programmatically"></a>以程式設計方式設定-optioncompare  
  
- 請參閱[Option Compare 語句](../../../visual-basic/language-reference/statements/option-compare-statement.md)。  
  
## <a name="example"></a>範例  
 下列程式碼會編譯 `ProjFile.vb`，並使用二進位字串比較。  
  
```console
vbc -optioncompare:binary projFile.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Option Compare 陳述式](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [選項對話方塊、專案、Visual Basic 預設值](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
