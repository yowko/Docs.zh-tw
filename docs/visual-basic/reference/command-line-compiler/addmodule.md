---
title: -addmodule
ms.date: 03/09/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c17d5541fe2d02ba88f4c5ef259b2248f371dfe5
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2018
---
# <a name="-addmodule"></a>-addmodule
讓編譯器將所指定檔案的類型資訊全部提供給您目前編譯的專案。  
  
## <a name="syntax"></a>語法  
  
```  
-addmodule:fileList  
```  
  
## <a name="arguments"></a>引數  
 `fileList`  
 必要。 包含中繼資料但不包含組件資訊清單檔案的逗號分隔清單。 應該以引號括住包含空格的檔案名稱 ("")。  
  
## <a name="remarks"></a>備註  
 所列出的檔案`fileList`參數必須以建立`-target:module`選項，或其他編譯器等同於`-target:module`。  
  
 使用新增的所有模組`-addmodule`必須位於執行階段的輸出檔相同的目錄。 也就是說，您可以在編譯時期，任一目錄中指定的模組，但該模組在執行階段時，必須在應用程式目錄。 如果不是，您會取得<xref:System.TypeLoadException>錯誤。  
  
 如果您指定 （隱含或明確） 任何[-目標 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)選項以外`-target:module`與`-addmodule`，您將傳遞至檔案`-addmodule`成為專案的組件的一部分。 組件，才能執行的輸出檔，具有一個或多個檔案加入`-addmodule`。  
  
 使用[/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)從包含組件檔案匯入中繼資料。  
  
> [!NOTE]
>  `-addmodule`選項不是從 Visual Studio 開發環境中使用; 其只有在從命令列編譯時。  
  
## <a name="example"></a>範例  
 下列程式碼會建立模組。  
  
 [!code-vb[VbVbalrCompiler#47](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_1.vb)]  
  
 下列程式碼會匯入模組的類型。  
  
 [!code-vb[VbVbalrCompiler#48](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_2.vb)]  
  
 當您執行`t1`，它會輸出`802`。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-目標 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [-參考 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
