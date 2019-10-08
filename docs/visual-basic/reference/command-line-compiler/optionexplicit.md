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
ms.openlocfilehash: 5c0946b94bfe02d797d1a484088869375703eb6a
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005313"
---
# <a name="-optionexplicit"></a>-optionexplicit
如果變數在使用之前未宣告，則會導致編譯器報告錯誤。  
  
## <a name="syntax"></a>語法  
  
```console  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a>引數  
 `+` &#124; `-`  
 選擇性。 指定 `-optionexplicit+` 則需要明確宣告變數。 @No__t-0 選項是預設值，而且與 `-optionexplicit` 相同。 @No__t-0 選項可啟用變數的隱含宣告。  
  
## <a name="remarks"></a>備註  
 如果原始程式碼檔包含[Option Explicit 語句](../../../visual-basic/language-reference/statements/option-explicit-statement.md)，則語句會覆寫 `-optionexplicit` 命令列編譯器設定。  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a>若要在 Visual Studio IDE 中設定-optionexplicit  
  
1. 在 **方案總管**中選取專案。 在 [專案] 功能表上，按一下 [屬性]。   
  
2. 按一下 [編譯] 索引標籤。  
  
3. 修改 [選項] [**明確**] 方塊中的值。  
  
## <a name="example"></a>範例  
 當使用 `-optionexplicit-` 時，下列程式碼會進行編譯。  
  
 [!code-vb[VbVbalrCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionExplicitOff.vb#5)]  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Option Explicit 陳述式](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [選項對話方塊、專案、Visual Basic 預設值](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
