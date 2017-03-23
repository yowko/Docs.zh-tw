---
title: "/optionexplicit |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /optionexplicit
dev_langs:
- VB
helpviewer_keywords:
- /optionexplicit compiler option [Visual Basic]
- optionexplicit compiler option [Visual Basic]
- -optionexplicit compiler option [Visual Basic]
ms.assetid: 5d296ab3-bafe-4c4d-9887-78f162ed86c7
caps.latest.revision: 16
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: cfdad72c21b7886f9ea8a2d46e7c457087e7049d
ms.lasthandoff: 03/13/2017

---
# <a name="optionexplicit"></a>/optionexplicit
如果變數不在使用前宣告，請讓編譯器將報告錯誤。  
  
## <a name="syntax"></a>語法  
  
```  
/optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a>引數  
 `+` &#124; `-`  
 選擇項。 指定`/optionexplicit+`需要明確宣告變數。 `/optionexplicit+`選項的預設值，而且相同`/optionexplicit`。 `/optionexplicit-`選項可讓隱含宣告的變數。  
  
## <a name="remarks"></a>備註  
 如果原始程式碼檔案包含[Option Explicit 陳述式](../../../visual-basic/language-reference/statements/option-explicit-statement.md)，陳述式會覆寫`/optionexplicit`命令列編譯器設定。  
  
### <a name="to-set-optionexplicit-in-the-visual-studio-ide"></a>在 Visual Studio IDE 中設定 /optionexplicit  
  
1.  在 **方案總管**中選取專案。 在**專案**] 功能表上，按一下 [**屬性**。 如需詳細資訊，請參閱[專案設計工具簡介](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)。  
  
2.  按一下 [編譯]**** 索引標籤。  
  
3.  修改中的值**Option Explicit**方塊。  
  
## <a name="example"></a>範例  
 下列程式碼編譯時`/optionexplicit-`用。  
  
 [!code-vb[VbVbalrCompiler #&5;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/optionexplicit_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)   
 [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)   
 [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Option Explicit 陳述式](../../../visual-basic/language-reference/statements/option-explicit-statement.md)   
 [選項對話方塊、專案、Visual Basic 預設值](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
