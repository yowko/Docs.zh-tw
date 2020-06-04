---
title: -keyfile
ms.date: 03/10/2018
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
ms.openlocfilehash: 3f476f6b6db1a788002a938eb5ae4bbbed7a5dae
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408571"
---
# <a name="-keyfile"></a>-keyfile
指定一個檔案，其中包含可為組件提供強式名稱的金鑰或金鑰組。  
  
## <a name="syntax"></a>語法  
  
```console
-keyfile:file  
```  
  
## <a name="arguments"></a>引數  
 `file`  
 必要。 包含金鑰的檔案。 如果檔案名包含空格，請將名稱括在引號（""）中。  
  
## <a name="remarks"></a>備註  
 編譯器會將公開金鑰插入組件資訊清單中，然後使用私密金鑰簽署最終元件。 若要產生金鑰檔，請在命令列中輸入 `sn -k file`。 如需詳細資訊，請參閱[sn.exe （強式名稱工具）](../../../framework/tools/sn-exe-strong-name-tool.md)）。  
  
 如果您使用進行編譯 `-target:module` ，則金鑰檔的名稱會保留在模組中，並併入當您使用[-addmodule](addmodule.md)編譯元件時所建立的元件中。  
  
 您也可以使用 [-keycontainer](keycontainer.md) 將加密資訊傳遞給編譯器。 如需部分簽署的組件，請使用 [-delaysign](delaysign.md)。  
  
 您也可以 <xref:System.Reflection.AssemblyKeyFileAttribute> 在任何 Microsoft 中繼語言模組的原始程式碼中，將此選項指定為自訂屬性（）。  
  
 如果在 `-keyfile` 相同編譯中同時指定和[-keycontainer](keycontainer.md) （透過命令列選項或自訂屬性），編譯器會先嘗試使用金鑰容器。 如果這個動作成功，則會使用金鑰容器中的資訊來簽署組件。 如果編譯器找不到金鑰容器，則會嘗試使用指定的檔案 `-keyfile` 。 如果成功，則會使用金鑰檔中的資訊簽署元件，並將金鑰資訊安裝在金鑰容器中（類似于 `sn -i` ），如此一來，在下一次編譯時，金鑰容器將會是有效的。  
  
 請注意，金鑰檔可能只包含公開金鑰。  
  
 如需簽署元件的詳細資訊，請參閱[建立和使用強式名稱的元件](../../../standard/assembly/create-use-strong-named.md)。  
  
> [!NOTE]
> 此 `-keyfile` 選項無法從 Visual Studio 開發環境中使用; 只有在從命令列進行編譯時，才能使用此選項。

## <a name="example"></a>範例

下列程式碼會編譯原始程式檔 `Input.vb` ，並指定金鑰檔。

```console
vbc -keyfile:myfile.sn input.vb
```

## <a name="see-also"></a>另請參閱

- [.NET 中的組件](../../../standard/assembly/index.md)
- [Visual Basic 命令列編譯器](index.md)
- [-reference （Visual Basic）](reference.md)
- [編譯命令列的範例](sample-compilation-command-lines.md)
