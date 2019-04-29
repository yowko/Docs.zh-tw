---
title: -delaysign
ms.date: 03/10/2018
helpviewer_keywords:
- delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
ms.openlocfilehash: 770dcad385c522a548a0c6fd3b6ef02dfbac82f5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61649708"
---
# <a name="-delaysign"></a>-delaysign
指定將要完整簽署還是部分簽署組件。  
  
## <a name="syntax"></a>語法  
  
```  
-delaysign[+ | -]  
```  
  
## <a name="arguments"></a>引數  
 `+` &#124; `-`  
 選擇性。 如果要完整簽署組件，請使用 `-delaysign-`。 使用`-delaysign+`如果您想要將公開金鑰放在帶正負號的雜湊的組件和保留空間。 預設為 `-delaysign-`。  
  
## <a name="remarks"></a>備註  
 `-delaysign`選項沒有任何作用，除非搭配[-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)或是[-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)。  
  
 當您要求完整簽署的組件時，編譯器會雜湊包含資訊清單 (組件中繼資料) 的檔案，並使用私密金鑰簽署該雜湊。 所產生的數位簽章會儲存在包含資訊清單的檔案中。 延遲簽署組件時，編譯器不會計算和儲存檔案中的簽章，但保留空間，以便可以稍後再加入簽章。  
  
 例如，藉由使用`-delaysign+`，組織的開發人員可以將測試人員可向全域組件快取註冊及使用組件的不帶正負號的測試版本散發。 組件上的工作完成時，負責組織的私用金鑰的人員可以完整簽署組件。 此區隔化防止洩漏，同時讓所有開發人員使用的組件之組織的私用金鑰。  
  
 請參閱[建立和使用強式名稱組件](../../../framework/app-domains/create-and-use-strong-named-assemblies.md)如需有關簽署組件。  
  
### <a name="to-set--delaysign-in-the-visual-studio-integrated-development-environment"></a>若要在 Visual Studio 整合式的開發環境中設定-delaysign  
  
1. 在 **方案總管**中選取專案。 在 [專案] 功能表上，按一下 [屬性]。   
  
2. 按一下 [簽署]索引標籤。  
  
3. 在設定的值**僅延遲簽署** 方塊中。  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)
- [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
