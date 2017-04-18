---
title: "/optionstrict |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /optionstrict
dev_langs:
- VB
helpviewer_keywords:
- -optionstrict compiler option [Visual Basic]
- optionstrict compiler option [Visual Basic]
- /optionstrict compiler option [Visual Basic]
ms.assetid: c7b10086-0fa4-49db-b3c8-4ae0db5957da
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 0394d9c1f4c082271316829ef1d226bd97d136c9
ms.lasthandoff: 03/13/2017

---
# <a name="optionstrict"></a>/optionstrict
會強制執行嚴格的型別語意來限制隱含型別轉換。  
  
## <a name="syntax"></a>語法  
  
```  
/optionstrict[+ | -]  
/optionstrict[:custom]  
```  
  
## <a name="arguments"></a>引數  
 `+` &#124; `-`  
 選擇項。 `/optionstrict+`選項會限制隱含類型轉換。 此選項的預設值是`/optionstrict-`。 `/optionstrict+`選項等同於`/optionstrict`。 您可以使用適用於寬鬆的型別語意 （semantics）。  
  
 `custom`  
 必要項。 未遵守嚴格的語意時發出警告。  
  
## <a name="remarks"></a>備註  
 當`/optionstrict+`有作用，只有擴大的類型轉換可以隱含地進行。 隱含縮小型別轉換，例如指派`Decimal`輸入整數型別物件的物件，會回報為錯誤。  
  
 若要產生隱含縮小型別轉換的警告，請使用`/optionstrict:custom`。 使用`/nowarn:numberlist`略過特定的警告和`/warnaserror:numberlist`將特定的警告視為錯誤。  
  
### <a name="to-set-optionstrict-in-the-visual-studio-ide"></a>在 Visual Studio IDE 中設定 /optionstrict  
  
1.  在 **方案總管**中選取專案。 在**專案** 功能表上，按一下**屬性。** 如需詳細資訊，請參閱[專案設計工具簡介](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)。  
  
2.  按一下 [編譯]**** 索引標籤。  
  
3.  修改中的值**Option Strict**方塊。  
  
### <a name="to-set-optionstrict-programmatically"></a>以程式設計方式設定 /optionstrict  
  
-   請參閱[Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)。  
  
## <a name="example"></a>範例  
 下列程式碼編譯`Test.vb`使用嚴格的型別語意 （semantics）。  
  
```  
vbc /optionstrict+ test.vb  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)   
 [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)   
 [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)   
 [/nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)   
 [/warnaserror (Visual Basic)](../../../visual-basic/reference/command-line-compiler/warnaserror.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Option Strict 陳述式](../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [選項對話方塊、專案、Visual Basic 預設值](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
