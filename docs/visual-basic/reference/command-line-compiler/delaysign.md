---
title: "/delaysign |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- delaysign compiler option [Visual Basic]
- /delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
caps.latest.revision: 19
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
ms.openlocfilehash: 59d4ec227286c20b2b4ecf749a91f0c4ee8d25ca
ms.lasthandoff: 03/13/2017

---
# <a name="delaysign"></a>/delaysign
指定將要完整簽署還是部分簽署組件。  
  
## <a name="syntax"></a>語法  
  
```  
/delaysign[+ | -]  
```  
  
## <a name="arguments"></a>引數  
 `+` &#124; `-`  
 選擇項。 如果要完整簽署組件，請使用 `/delaysign-`。 使用`/delaysign+`如果您想要的公開金鑰置於帶正負號的雜湊的組件和保留空間。 預設為 `/delaysign-`。  
  
## <a name="remarks"></a>備註  
 `/delaysign`選項沒有任何作用，除非搭配[/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)或[/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)。  
  
 當您要求完整簽署組件時，編譯器會雜湊包含資訊清單 （組件中繼資料），並使用私密金鑰簽署雜湊的檔案。 所產生的數位簽章會儲存在包含資訊清單的檔案中。 延遲簽署組件時，編譯器不會不會計算並儲存檔案中的簽章，但會保留空間，以便可以稍後再加入簽章。  
  
 例如，藉由使用`/delaysign+`，組織中的開發人員可以散發不帶正負號的測試組件版本的軟體測試人員可以向全域組件快取，並使用。 組件上的工作完成時，負責組織的私用金鑰的人員可以完整簽署組件。 此區隔化防止洩漏，同時允許使用組件的所有開發人員組織的私密金鑰。  
  
 請參閱[建立和使用強式名稱組件](https://msdn.microsoft.com/library/xwb8f617)如需有關簽署組件。  
  
### <a name="to-set-delaysign-in-the-visual-studio-integrated-development-environment"></a>在 Visual Studio 中設定 /delaysign 整合式開發環境  
  
1.  在 **方案總管**中選取專案。 在**專案**] 功能表上，按一下 [**屬性**。 如需詳細資訊，請參閱[專案設計工具簡介](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)。  
  
2.  按一下 [**簽署**] 索引標籤。  
  
3.  在設定的值**延遲簽署只**方塊。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)   
 [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)   
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
