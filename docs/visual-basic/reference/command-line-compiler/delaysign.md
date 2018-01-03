---
title: /delaysign
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- delaysign compiler option [Visual Basic]
- /delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b4d29f99d0c375eebee0f477720cb9a22172dddb
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="delaysign"></a>/delaysign
指定將要完整簽署還是部分簽署組件。  
  
## <a name="syntax"></a>語法  
  
```  
/delaysign[+ | -]  
```  
  
## <a name="arguments"></a>引數  
 `+` &#124; `-`  
 選擇性。 如果要完整簽署組件，請使用 `/delaysign-`。 使用`/delaysign+`如果您想要將公開金鑰放入帶正負號的雜湊的組件和保留空間。 預設為 `/delaysign-`。  
  
## <a name="remarks"></a>備註  
 `/delaysign`選項沒有任何作用，除非搭配[/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)或[/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)。  
  
 當您要求完整簽署的組件時，編譯器會雜湊包含資訊清單 (組件中繼資料) 的檔案，並使用私密金鑰簽署該雜湊。 所產生的數位簽章會儲存在包含資訊清單的檔案中。 延遲簽署組件時，編譯器不會不會計算並儲存檔案中的簽章，但保留空間，以便稍後再加入簽章。  
  
 例如，藉由使用`/delaysign+`，組織中的開發人員可以將不帶正負號的測試組件版本的測試人員可以向全域組件快取，並使用發佈。 組件上的工作完成時，負責組織的私用金鑰的人員可以完整簽署組件。 此劃分防止洩漏，同時允許使用組件的所有開發人員組織的私用金鑰。  
  
 請參閱[Creating and using strong-named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md)如需有關簽署組件。  
  
### <a name="to-set-delaysign-in-the-visual-studio-integrated-development-environment"></a>在 Visual Studio 中設定 /delaysign 整合式開發環境  
  
1.  在 **方案總管**中選取專案。 在 [專案] 功能表上，按一下 [屬性]。   
  
2.  按一下 [簽署]索引標籤。  
  
3.  設定中的值**延遲簽署只能**方塊。  
  
## <a name="see-also"></a>請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)  
 [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)  
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
