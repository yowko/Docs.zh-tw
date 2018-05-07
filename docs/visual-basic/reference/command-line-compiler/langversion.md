---
title: -langversion (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
ms.openlocfilehash: 82a7114027451d1342e6dc0846799933ce44d968
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="-langversion-visual-basic"></a>-langversion (Visual Basic)
可讓編譯器接受包含在指定的 Visual Basic 語言版本的語法。  
  
## <a name="syntax"></a>語法  
  
```  
-langversion:version  
```  
  
## <a name="arguments"></a>引數  
 `version`  
 必要。 要在編譯期間使用的語言版本。 接受的值為`9`， `9.0`， `10`，和`10.0`。  
  
## <a name="remarks"></a>備註  
 `-langversion`選項指定何種編譯器接受的語法。 例如，如果您指定的語言版本是 9.0，編譯器會產生只適用於 10.0 版及更新版本的語法錯誤。  
  
 當您開發該目標的不同版本的.NET framework 應用程式時，您可以使用此選項。 例如，如果您的目標.NET Framework 3.5，您可以使用此選項以確保不會使用從 10.0 版的語言語法。  
  
 您可以設定`-langversion`直接只能藉由使用命令列。 如需詳細資訊，請參閱[以特定的 .NET Framework 版本為目標](/visualstudio/ide/targeting-a-specific-dotnet-framework-version)。  
  
## <a name="example"></a>範例  
 下列程式碼編譯`sample.vb`的 Visual Basic 9.0。  
  
```console  
vbc -langversion:9.0 sample.vb  
```  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)  
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [以特定的 .NET Framework 版本為目標](/visualstudio/ide/targeting-a-specific-dotnet-framework-version)
