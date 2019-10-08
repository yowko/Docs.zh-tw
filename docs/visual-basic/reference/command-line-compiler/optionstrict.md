---
title: -optionstrict
ms.date: 07/20/2015
f1_keywords:
- -optionstrict
helpviewer_keywords:
- -optionstrict compiler option [Visual Basic]
- optionstrict compiler option [Visual Basic]
- /optionstrict compiler option [Visual Basic]
ms.assetid: c7b10086-0fa4-49db-b3c8-4ae0db5957da
ms.openlocfilehash: 6d281fe07754f0471f8d6c0e31cf3ea890060504
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005344"
---
# <a name="-optionstrict"></a>-optionstrict
強制執行嚴格的類型語義來限制隱含類型轉換。  
  
## <a name="syntax"></a>語法  
  
```console  
-optionstrict[+ | -]  
-optionstrict[:custom]  
```  
  
## <a name="arguments"></a>引數  
 `+` &#124; `-`  
 選擇性。 @No__t-0 選項會限制隱含類型轉換。 此選項的預設值為 `-optionstrict-`。 @No__t-0 選項與 `-optionstrict` 相同。 您可以針對寬鬆類型的語義使用這兩者。  
  
 `custom`  
 必要項。 不遵守嚴格語言語義時發出警告。  
  
## <a name="remarks"></a>備註  
 當 `-optionstrict+` 生效時，只有擴展型別轉換可以隱含地進行。 隱含的縮小類型轉換（例如將 @no__t 0 的類型物件指派給整數類型物件）會回報為錯誤。  
  
 若要產生隱含縮小類型轉換的警告，請使用 `-optionstrict:custom`。 使用 `-nowarn:numberlist` 來忽略特定的警告，並 `-warnaserror:numberlist` 將特定警告視為錯誤。  
  
### <a name="to-set--optionstrict-in-the-visual-studio-ide"></a>若要在 Visual Studio IDE 中設定-optionstrict  
  
1. 在 **方案總管**中選取專案。 在 [**專案**] 功能表上，按一下 [**屬性]。**   
  
2. 按一下 [編譯] 索引標籤。  
  
3. 修改 [**選項 Strict** ] 方塊中的值。  
  
### <a name="to-set--optionstrict-programmatically"></a>以程式設計方式設定-optionstrict  
  
- 請參閱[Option Strict 語句](../../../visual-basic/language-reference/statements/option-strict-statement.md)。  
  
## <a name="example"></a>範例  
 下列程式碼會使用 strict 類型的語義來編譯 @no__t 0。  
  
```console
vbc -optionstrict+ test.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)
- [-warnaserror （Visual Basic）](../../../visual-basic/reference/command-line-compiler/warnaserror.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [選項對話方塊、專案、Visual Basic 預設值](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
