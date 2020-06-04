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
ms.openlocfilehash: b004acb0c1c7d145c59a1e3a88ef7f1d405a91c6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400551"
---
# <a name="-optionexplicit"></a>-optionexplicit
如果變數在使用之前未宣告，則會導致編譯器報告錯誤。  
  
## <a name="syntax"></a>語法  
  
```console  
-optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a>引數  
 `+` &#124; `-`  
 選擇性。 指定 `-optionexplicit+` ，以要求明確宣告變數。 `-optionexplicit+`選項是預設值，而且與相同 `-optionexplicit` 。 `-optionexplicit-`選項會啟用變數的隱含宣告。  
  
## <a name="remarks"></a>備註  
 如果原始程式碼檔案包含[Option Explicit 語句](../../language-reference/statements/option-explicit-statement.md)，則語句會覆寫 `-optionexplicit` 命令列編譯器設定。  
  
### <a name="to-set--optionexplicit-in-the-visual-studio-ide"></a>若要在 Visual Studio IDE 中設定-optionexplicit  
  
1. 在 **方案總管**中選取專案。 按一下 [專案]**** 功能表上的 [屬性]****。
  
2. 按一下 [編譯]**** 索引標籤。  
  
3. 修改 [選項] [**明確**] 方塊中的值。  
  
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
