---
title: -moduleassemblyname
ms.date: 03/13/2018
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
ms.openlocfilehash: dc4c0336c8a67a1b4e70f71ba5f5406da1fbb2ff
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972381"
---
# <a name="-moduleassemblyname"></a>-moduleassemblyname
指定將包含此模組的組件名稱。  
  
## <a name="syntax"></a>語法  
  
```  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`assembly_name`|此模組將成為其一部分的元件名稱。|  
  
## <a name="remarks"></a>備註  
 只有在`-moduleassemblyname` `-target:module`已指定選項時，編譯器才會處理選項。 這會導致編譯器建立模組。 編譯器所建立的模組只對使用`-moduleassemblyname`選項指定的元件有效。 如果您將模組放在不同的元件中，就會發生執行階段錯誤。  
  
 只有在下列條件成立時，才需要選項：`-moduleassemblyname`  
  
- 模組中的資料類型需要存取參考元件中`Friend`的類型。  
  
- 參考的元件已將 friend 元件存取權授與要在其中建立模組的元件。  
  
 如需有關建立模組的詳細資訊，請參閱[/target （Visual Basic）](../../../visual-basic/reference/command-line-compiler/target.md)。 如需 friend 元件的詳細資訊，請參閱[Friend 元件](../../../standard/assembly/friend.md)。  
  
> [!NOTE]
> 此`-moduleassemblyname`選項無法從 Visual Studio 開發環境中使用; 只有當您從命令提示字元進行編譯時，才能使用此選項。  
  
## <a name="see-also"></a>另請參閱

- [如何：建置多檔案組件](../../../framework/app-domains/build-multifile-assembly.md)
- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [-target （Visual Basic）](../../../visual-basic/reference/command-line-compiler/target.md)
- [-main](../../../visual-basic/reference/command-line-compiler/main.md)
- [-reference （Visual Basic）](../../../visual-basic/reference/command-line-compiler/reference.md)
- [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)
- [.NET 中的組件](../../../standard/assembly/index.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Friend 組件](../../../standard/assembly/friend.md)
