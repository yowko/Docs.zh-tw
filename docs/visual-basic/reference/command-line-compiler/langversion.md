---
title: -langversion
ms.date: 03/10/2018
helpviewer_keywords:
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.custom: updateeachrelease
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
ms.openlocfilehash: 9921df0b8bb1a4808528b58a5a38d75e5e3fbdd2
ms.sourcegitcommit: ae2e8a61a93c5cf3f0035c59e6b064fa2f812d14
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "89359255"
---
# <a name="-langversion-visual-basic"></a>-langversion (Visual Basic) 

使編譯器只接受指定 Visual Basic 語言版本中包含的語法。  
  
## <a name="syntax"></a>語法  
  
```console  
-langversion:version  
```  
  
## <a name="arguments"></a>引數

 `version`\
 必要。 要在編譯期間使用的語言版本。 接受的值為 `9` 、 `10` 、、、、、、、 `11` `12` `14` `15` `15.3` `15.5` `16` `default` 和 `latest` 。

 您也可以使用 `.0` 做為次要版本來指定任何整數，例如， `11.0` 。

 您可以 `-langversion:?` 在命令列上指定，以查看所有可能值的清單。

## <a name="remarks"></a>備註

`-langversion`選項會指定編譯器接受的語法。 例如，如果您將語言版本指定為9.0，則編譯器會針對只有10.0 版和更新版本中有效的語法產生錯誤。

當您開發以不同 .NET Framework 版本為目標的應用程式時，可以使用這個選項。 例如，如果您的目標是 .NET Framework 3.5，您可以使用此選項，以確保您不會使用語言10.0 版中的語法。

您只能 `-langversion` 使用命令列來直接設定。 如需詳細資訊，請參閱[以特定的 .NET Framework 版本為目標](/visualstudio/ide/visual-studio-multi-targeting-overview)。

## <a name="example"></a>範例

下列程式碼會 `sample.vb` 針對 Visual Basic 9.0 進行編譯。

```console
vbc -langversion:9.0 sample.vb
```

## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](index.md)
- [編譯命令列的範例](sample-compilation-command-lines.md)
