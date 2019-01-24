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
ms.openlocfilehash: fdea071f8c41f2e707d10c96c8b6ab1fbb44bad0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54733307"
---
# <a name="-optionstrict"></a>-optionstrict
會強制執行嚴格類型語意來限制隱含類型轉換。  
  
## <a name="syntax"></a>語法  
  
```  
-optionstrict[+ | -]  
-optionstrict[:custom]  
```  
  
## <a name="arguments"></a>引數  
 `+` &#124; `-`  
 選擇性。 `-optionstrict+`選項會限制隱含類型轉換。 此選項的預設值是`-optionstrict-`。 `-optionstrict+`選項相當於`-optionstrict`。 您可以使用的寬鬆的型別語意。  
  
 `custom`  
 必要項。 未遵守嚴格的語意時，就發出警告。  
  
## <a name="remarks"></a>備註  
 當`-optionstrict+`處於作用中，只有擴大的類型轉換可以隱含進行。 隱含縮小類型轉換，例如指派`Decimal`類型為整數型別物件的物件，會回報為錯誤。  
  
 若要產生隱含縮小類型轉換的警告，請使用`-optionstrict:custom`。 使用`-nowarn:numberlist`略過特定的警告和`-warnaserror:numberlist`將特定警告視為錯誤。  
  
### <a name="to-set--optionstrict-in-the-visual-studio-ide"></a>若要在 Visual Studio IDE 中設定-optionstrict  
  
1.  在 **方案總管**中選取專案。 在 **專案**功能表上，按一下 **屬性。**   
  
2.  按一下 [編譯] 索引標籤。  
  
3.  修改中的值**Option Strict**  方塊中。  
  
### <a name="to-set--optionstrict-programmatically"></a>以程式設計方式設定-optionstrict  
  
-   請參閱[Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)。  
  
## <a name="example"></a>範例  
 下列程式碼編譯`Test.vb`使用嚴格的類型語意。  
  
```console
vbc -optionstrict+ test.vb  
```  
  
## <a name="see-also"></a>另請參閱
- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)
- [-warnaserror (Visual Basic)](../../../visual-basic/reference/command-line-compiler/warnaserror.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [選項對話方塊、專案、Visual Basic 預設值](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
