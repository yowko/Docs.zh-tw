---
title: /moduleassemblyname
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0d9a5307970ac745b4f102d0008e64b985c00e52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="moduleassemblyname"></a>/moduleassemblyname
指定將包含此模組的組件名稱。  
  
## <a name="syntax"></a>語法  
  
```  
/moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`assembly_name`|此模組將成為一部分的組件名稱。|  
  
## <a name="remarks"></a>備註  
 編譯器處理序`/moduleassemblyname`選項才`/target:module`已指定選項。 這會導致編譯器建立的模組。 由編譯器所建立的模組是僅適用於具有指定的組件`/moduleassemblyname`選項。 如果您將模組放在不同的組件時，會發生執行階段錯誤。  
  
 `/moduleassemblyname`選項只有在下列條件成立時，才需要：  
  
-   模組中的資料類型需要存取`Friend`參考的組件的類型。  
  
-   參考的組件有 friend 組件存取權限授與模組將會建置到其中的組件。  
  
 如需有關建立模組的詳細資訊，請參閱[/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)。 如需 friend 組件的詳細資訊，請參閱[Friend 組件](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055)。  
  
> [!NOTE]
>  `/moduleassemblyname`選項不是從 Visual Studio 開發環境中使用，則可以使用只有當您編譯的命令提示字元。  
  
## <a name="see-also"></a>另請參閱  
 [操作說明：建置多檔案組件](../../../framework/app-domains/how-to-build-a-multifile-assembly.md)  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [/main](../../../visual-basic/reference/command-line-compiler/main.md)  
 [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)  
 [組件和全域組件快取](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Friend 組件](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055)
