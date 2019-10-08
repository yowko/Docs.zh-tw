---
title: -keycontainer
ms.date: 03/10/2018
helpviewer_keywords:
- -keycontainer compiler option [Visual Basic]
- keycontainer compiler option [Visual Basic]
- /keycontainer compiler option [Visual Basic]
ms.assetid: 6a9bc861-1752-4db1-9f64-b5252f0482cc
ms.openlocfilehash: be2ad1416e801398fb513593c7f3828e5488bfaf
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005534"
---
# <a name="-keycontainer"></a>-keycontainer
指定金鑰組的金鑰容器名稱，為組件提供強式名稱。  
  
## <a name="syntax"></a>語法  
  
```console  
-keycontainer:container  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`container`|必要項。 包含金鑰的容器檔案。 如果名稱包含空格，請用引號（""）括住檔案名。|  
  
## <a name="remarks"></a>備註  
 編譯器會藉由將公開金鑰插入組件資訊清單中，並使用私密金鑰簽署最終元件，來建立可共用的元件。 若要產生金鑰檔，請在命令列中輸入 `sn -k file`。 @No__t-0 選項會將金鑰組安裝到容器中。 如需詳細資訊，請參閱[sn.exe （強式名稱工具）](../../../framework/tools/sn-exe-strong-name-tool.md)）。  
  
 如果您使用 `-target:module` 進行編譯，金鑰檔的名稱會保留在模組中，並併入當您使用[-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)編譯元件時所建立的元件中。  
  
 您也可以在任何 Microsoft 中繼語言 (MSIL) 模組的原始程式碼中，將這個選項指定為自訂屬性 (<xref:System.Reflection.AssemblyKeyNameAttribute>)。  
  
 您也可以使用 [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md) 將加密資訊傳遞給編譯器。 如需部分簽署的組件，請使用 [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md)。  
  
 如需簽署元件的詳細資訊，請參閱[建立和使用強式名稱的元件](../../../standard/assembly/create-use-strong-named.md)。  
  
> [!NOTE]
> @No__t-0 選項無法從 Visual Studio 開發環境中使用;只有在從命令列編譯時，才可以使用它。  
  
## <a name="example"></a>範例  
 下列程式碼會將來源檔案編譯 `Input.vb`，並指定金鑰容器。  
  
```console  
vbc -keycontainer:key1 input.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [.NET 中的組件](../../../standard/assembly/index.md)
- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
