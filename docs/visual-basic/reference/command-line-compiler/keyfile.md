---
title: -keyfile
ms.date: 03/10/2018
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
ms.openlocfilehash: cffc3c5f0ff3dd48ca2c74bde346a967b209dc5f
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266738"
---
# <a name="-keyfile"></a>-keyfile
指定一個檔案，其中包含可為組件提供強式名稱的金鑰或金鑰組。  
  
## <a name="syntax"></a>語法  
  
```console
-keyfile:file  
```  
  
## <a name="arguments"></a>引數  
 `file`  
 必要。 包含金鑰的檔。 如果檔案名包含空格，則用引號 （""） 括上名稱。  
  
## <a name="remarks"></a>備註  
 編譯器將公開金鑰插入組件資訊清單，然後使用私密金鑰對最終程式集進行簽名。 若要產生金鑰檔，請在命令列中輸入 `sn -k file`。 有關詳細資訊，請參閱[Sn.exe（強式名稱工具）。](../../../framework/tools/sn-exe-strong-name-tool.md)  
  
 如果使用 編譯，`-target:module`則金鑰檔的名稱將包含在模組中，併合並[到編譯器集](../../../visual-basic/reference/command-line-compiler/addmodule.md)時創建的程式集中，  
  
 您也可以使用 [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) 將加密資訊傳遞給編譯器。 如需部分簽署的組件，請使用 [-delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md)。  
  
 您還可以在任何 Microsoft 中間語言模組的原始程式碼中<xref:System.Reflection.AssemblyKeyFileAttribute>指定此選項為自訂屬性 （ ） 。  
  
 如果在同`-keyfile`一編譯中指定和[-key 容器](../../../visual-basic/reference/command-line-compiler/keycontainer.md)（通過命令列選項或自訂屬性），編譯器首先嘗試金鑰容器。 如果這個動作成功，則會使用金鑰容器中的資訊來簽署組件。 如果編譯器找不到金鑰容器，它將嘗試使用`-keyfile`指定的檔。 如果成功，程式集將使用金鑰檔中的資訊進行簽名，並且金鑰資訊安裝在金鑰容器中（類似于`sn -i`），以便在下一次編譯時金鑰容器將有效。  
  
 請注意，金鑰檔可能只包含公開金鑰。  
  
 有關對程式集進行簽名的詳細資訊，請參閱[創建和使用強式名稱程式集](../../../standard/assembly/create-use-strong-named.md)。  
  
> [!NOTE]
> 該`-keyfile`選項在視覺化工作室開發環境中不可用;因此，該選項在視覺化工作室開發環境中不可用。它僅在從命令列編譯時可用。

## <a name="example"></a>範例

以下代碼編譯原始檔案`Input.vb`並指定金鑰檔。

```console
vbc -keyfile:myfile.sn input.vb
```

## <a name="see-also"></a>另請參閱

- [.NET 中的組件](../../../standard/assembly/index.md)
- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [-參考（視覺基礎）](../../../visual-basic/reference/command-line-compiler/reference.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
