---
title: -optionexplicit
ms.date: 07/20/2015
f1_keywords:
- /optionexplicit
- -optionexplicit
helpviewer_keywords:
- /optionexplicit compiler option [Visual Basic]
- optionexplicit compiler option [Visual Basic]
- -optionexplicit compiler option [Visual Basic]
ms.assetid: 5d296ab3-bafe-4c4d-9887-78f162ed86c7
ms.openlocfilehash: 1de1b3a816739fc5f8ba1d1251b673c0b708d106
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56969488"
---
# <a name="-optionexplicit"></a>-optionexplicit
如果變數未宣告在使用前，會導致編譯器報告錯誤。  
  
## <a name="syntax"></a>語法  
  
```  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a>引數  
 `+` &#124; `-`  
 選擇性。 指定`-optionexplicit+`表示需要明確宣告變數。 `-optionexplicit+`選項是預設值，並與相同`-optionexplicit`。 `-optionexplicit-`選項可讓隱含宣告的變數。  
  
## <a name="remarks"></a>備註  
 如果原始程式碼檔中包含[Option Explicit 陳述式](../../../visual-basic/language-reference/statements/option-explicit-statement.md)，此陳述式會覆寫`-optionexplicit`命令列編譯器設定。  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a>若要在 Visual Studio IDE 中設定-optionexplicit  
  
1.  在 **方案總管**中選取專案。 在 [專案] 功能表上，按一下 [屬性]。   
  
2.  按一下 [編譯] 索引標籤。  
  
3.  修改中的值**Option Explicit**  方塊中。  
  
## <a name="example"></a>範例  
 下列程式碼會編譯時`-optionexplicit-`用。  
  
 [!code-vb[VbVbalrCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionExplicitOff.vb#5)]  
  
## <a name="see-also"></a>另請參閱
- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Option Explicit 陳述式](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [選項對話方塊、專案、Visual Basic 預設值](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
