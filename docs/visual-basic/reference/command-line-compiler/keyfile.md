---
title: -keyfile
ms.date: 03/10/2018
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
ms.openlocfilehash: c13f34c23cad9c909c2c5bd3447f1a8fa53f9b4d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793953"
---
# <a name="-keyfile"></a>-keyfile
指定一個檔案，其中包含可為組件提供強式名稱的金鑰或金鑰組。  
  
## <a name="syntax"></a>語法  
  
``` 
-keyfile:file  
```  
  
## <a name="arguments"></a>引數  
 `file`  
 必要項。 包含索引鍵的檔案。 如果檔案名稱包含空格，將名稱括在引號 ("")。  
  
## <a name="remarks"></a>備註  
 編譯器會將公開金鑰插入到組件資訊清單，然後使用私密金鑰簽署最終組件。 若要產生金鑰檔，請在命令列中輸入 `sn -k file`。 如需詳細資訊，請參閱 < [Sn.exe （強式名稱工具）](../../../framework/tools/sn-exe-strong-name-tool.md))。  
  
 如果您使用編譯`-target:module`，金鑰檔的名稱會保留在模組中並併入編譯的組件時所建立的組件[/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)。  
  
 您也可以使用 [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) 將加密資訊傳遞給編譯器。 如需部分簽署的組件，請使用 [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md)。  
  
 您也可以指定此選項為自訂屬性 (<xref:System.Reflection.AssemblyKeyFileAttribute>) 在任何 Microsoft 中繼語言模組的原始程式碼。  
  
 在案例中都`-keyfile`並[-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) （藉由命令列選項或是自訂屬性） 中指定相同編譯中，編譯器會先嘗試使用金鑰容器。 如果這個動作成功，則會使用金鑰容器中的資訊來簽署組件。 如果編譯器找不到金鑰容器，它會嘗試使用指定的檔案`-keyfile`。 如果這個作業會成功，金鑰檔中的資訊簽署組件的金鑰資訊安裝在金鑰容器 (類似於`sn -i`)，以便在下次編譯時，金鑰容器才有效。  
  
 請注意，金鑰檔可能只包含公開金鑰。  
  
 請參閱[建立和使用強式名稱組件](../../../framework/app-domains/create-and-use-strong-named-assemblies.md)如需有關簽署組件。  
  
> [!NOTE]
>  `-keyfile`選項不是從 Visual Studio 開發環境中使用; 只有在從命令列編譯時均可使用。  
  
## <a name="example"></a>範例  
 下列程式碼會編譯原始程式檔`Input.vb`和指定的金鑰檔。  
  
```console  
vbc -keyfile:myfile.sn input.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [.NET 中的組件](../../../standard/assembly/index.md)
- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [-參考 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
