---
title: -moduleassemblyname
ms.date: 03/13/2018
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
ms.openlocfilehash: 9fb9287f9472d4b33eff4cb601aff5eed370b2c0
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91065563"
---
# <a name="-moduleassemblyname"></a>-moduleassemblyname

指定將包含此模組的組件名稱。  
  
## <a name="syntax"></a>語法  
  
```console  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`assembly_name`|此模組所屬的組件名稱。|  
  
## <a name="remarks"></a>備註  

 `-moduleassemblyname`只有在已指定選項時，編譯器才會處理選項 `-target:module` 。 這會導致編譯器建立模組。 編譯器所建立的模組，只對使用選項指定的元件有效 `-moduleassemblyname` 。 如果您將模組放在不同的元件中，則會發生執行階段錯誤。  
  
 `-moduleassemblyname`只有當下列條件成立時，才需要此選項：  
  
- 模組中的資料類型需要存取 `Friend` 參考元件中的類型。  
  
- 參考的元件已將 friend 元件存取權授與將在其中建立模組的元件。  
  
 如需有關建立模組的詳細資訊，請參閱 [-目標 (Visual Basic) ](target.md)。 如需 friend 元件的詳細資訊，請參閱 [Friend 元件](../../../standard/assembly/friend.md)。  
  
> [!NOTE]
> `-moduleassemblyname`選項無法在 Visual Studio 開發環境中使用; 只有當您從命令提示字元進行編譯時，才能使用此選項。  
  
## <a name="see-also"></a>另請參閱

- [如何：建立多檔案元件](../../../framework/app-domains/build-multifile-assembly.md)
- [Visual Basic 命令列編譯器](index.md)
- [-目標 (Visual Basic) ](target.md)
- [-main](main.md)
- [-reference (Visual Basic) ](reference.md)
- [-addmodule](addmodule.md)
- [.NET 中的組件](../../../standard/assembly/index.md)
- [編譯命令列的範例](sample-compilation-command-lines.md)
- [Friend 元件](../../../standard/assembly/friend.md)
