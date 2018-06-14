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
ms.openlocfilehash: 072a816f189a772543fbbd63e7202441469c0177
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653594"
---
# <a name="-optionexplicit"></a>-optionexplicit
如果變數不宣告在使用前，會導致編譯器錯誤報告。  
  
## <a name="syntax"></a>語法  
  
```  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a>引數  
 `+` &#124; `-`  
 選擇性。 指定`-optionexplicit+`表示需要明確宣告變數。 `-optionexplicit+`選項是預設值，並與相同`-optionexplicit`。 `-optionexplicit-`選項可讓隱含宣告的變數。  
  
## <a name="remarks"></a>備註  
 如果原始程式碼檔內含[Option Explicit 陳述式](../../../visual-basic/language-reference/statements/option-explicit-statement.md)，陳述式會覆寫`-optionexplicit`命令列編譯器設定。  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a>在 Visual Studio IDE 中設定-optionexplicit  
  
1.  在 **方案總管**中選取專案。 在 [專案] 功能表上，按一下 [屬性]。   
  
2.  按一下 [編譯] 索引標籤。  
  
3.  修改中的值**Option Explicit**方塊。  
  
## <a name="example"></a>範例  
 下列程式碼會編譯時`-optionexplicit-`用。  
  
 [!code-vb[VbVbalrCompiler#5](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/optionexplicit_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Option Explicit 陳述式](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [選項對話方塊、專案、Visual Basic 預設值](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
