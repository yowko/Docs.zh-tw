---
title: -keycontainer
ms.date: 03/10/2018
helpviewer_keywords:
- -keycontainer compiler option [Visual Basic]
- keycontainer compiler option [Visual Basic]
- /keycontainer compiler option [Visual Basic]
ms.assetid: 6a9bc861-1752-4db1-9f64-b5252f0482cc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dc6453dc188e7621444b6f44b805aab9354d81f0
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43854680"
---
# <a name="-keycontainer"></a>-keycontainer
指定金鑰組的金鑰容器名稱，為組件提供強式名稱。  
  
## <a name="syntax"></a>語法  
  
```  
-keycontainer:container  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`container`|必要。 包含索引鍵的容器檔案。 將檔案名稱括在引號 ("") 如果名稱包含空格。|  
  
## <a name="remarks"></a>備註  
 藉由將公開金鑰插入組件資訊清單，並使用私密金鑰簽署最終組件，編譯器會建立可共用的元件。 若要產生金鑰檔，請在命令列中輸入 `sn -k file`。 `-i`選項會安裝至容器的金鑰組。 如需詳細資訊，請參閱 [Sn.exe （強式名稱工具）][Sn.exe （強式名稱工具）](../../../framework/tools/sn-exe-strong-name-tool.md))。  
  
 如果您使用編譯`-target:module`，金鑰檔的名稱會保留在模組中並併入編譯的組件時所建立的組件[-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)。  
  
 您也可以在任何 Microsoft 中繼語言 (MSIL) 模組的原始程式碼中，將這個選項指定為自訂屬性 (<xref:System.Reflection.AssemblyKeyNameAttribute>)。  
  
 您也可以使用 [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) 將加密資訊傳遞給編譯器。 如需部分簽署的組件，請使用 [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md)。  
  
 請參閱[建立和使用強式名稱組件](../../../framework/app-domains/create-and-use-strong-named-assemblies.md)如需有關簽署組件。  
  
> [!NOTE]
>  `-keycontainer`選項不是從 Visual Studio 開發環境中使用; 只有在從命令列編譯時均可使用。  
  
## <a name="example"></a>範例  
 下列程式碼會編譯原始程式檔`Input.vb`和指定的金鑰容器。  
  
```  
vbc -keycontainer:key1 input.vb  
```  
  
## <a name="see-also"></a>另請參閱  
 [組件和全域組件快取](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)  
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
