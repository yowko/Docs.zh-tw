---
title: -langversion
ms.date: 03/10/2018
helpviewer_keywords:
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
ms.openlocfilehash: 271606ac021e6afcb28fdac3e1bc86e1aaba7d2b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408534"
---
# <a name="-langversion-visual-basic"></a>-langversion （Visual Basic）
使編譯器只接受指定的 Visual Basic 語言版本中所包含的語法。  
  
## <a name="syntax"></a>語法  
  
```console  
-langversion:version  
```  
  
## <a name="arguments"></a>引數  
 `version`  
 必要。 要在編譯期間使用的語言版本。 接受的值為 `9` 、 `10` 、 `11` 、、、、、 `12` `14` `15` `15.3` `15.5` `default` 和 `latest` 。

 您也可以使用將任何整數指定 `.0` 為次要版本，例如 `11.0` 。

 您可以 `-langversion:?` 在命令列上指定，以查看所有可能值的清單。  
  
## <a name="remarks"></a>備註  
 `-langversion`選項會指定編譯器接受的語法。 例如，如果您指定語言版本是9.0，則編譯器會針對只有10.0 版和更新版本中有效的語法產生錯誤。  
  
 當您開發以不同 .NET Framework 版本為目標的應用程式時，可以使用此選項。 例如，如果您的目標是 .NET Framework 3.5，您可以使用此選項來確保不會使用語言版本10.0 中的語法。  
  
 您只能 `-langversion` 使用命令列來直接設定。 如需詳細資訊，請參閱[以特定的 .NET Framework 版本為目標](/visualstudio/ide/visual-studio-multi-targeting-overview)。  
  
## <a name="example"></a>範例  
 下列程式碼會 `sample.vb` 針對 Visual Basic 9.0 進行編譯。  
  
```console  
vbc -langversion:9.0 sample.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](index.md)
- [編譯命令列的範例](sample-compilation-command-lines.md)
- [以特定的 .NET Framework 版本為目標](/visualstudio/ide/visual-studio-multi-targeting-overview)
