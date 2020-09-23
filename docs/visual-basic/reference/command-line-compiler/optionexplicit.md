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
ms.openlocfilehash: 65cc3fb1b2fa9daa04013caa2b93a3949d0a15b9
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91098932"
---
# <a name="-optionexplicit"></a>-optionexplicit

如果變數在使用之前未宣告，則會導致編譯器報告錯誤。  
  
## <a name="syntax"></a>語法  
  
```console  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a>引數  

 `+` &#124; `-`  
 選擇性。 指定 `-optionexplicit+` 需要明確宣告變數。 此 `-optionexplicit+` 選項是預設值，而且與相同 `-optionexplicit` 。 `-optionexplicit-`選項會啟用變數的隱含宣告。  
  
## <a name="remarks"></a>備註  

 如果原始程式碼檔包含 [Option Explicit 語句](../../language-reference/statements/option-explicit-statement.md)，則語句會覆寫 `-optionexplicit` 命令列編譯器設定。  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a>若要在 Visual Studio IDE 中設定-optionexplicit  
  
1. 在 **方案總管**中選取專案。 按一下 [專案] 功能表上的 [屬性]。
  
2. 按一下 [編譯]**** 索引標籤。  
  
3. 修改 [ **選項明確** ] 方塊中的值。  
  
## <a name="example"></a>範例  

 使用時，下列 `-optionexplicit-` 程式碼會進行編譯。  
  
 [!code-vb[VbVbalrCompiler#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionExplicitOff.vb#5)]  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](index.md)
- [-optioncompare](optioncompare.md)
- [-optionstrict](optionstrict.md)
- [-optioninfer](optioninfer.md)
- [編譯命令列的範例](sample-compilation-command-lines.md)
- [Option Explicit 陳述式](../../language-reference/statements/option-explicit-statement.md)
- [選項對話方塊、專案、Visual Basic 預設值](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
