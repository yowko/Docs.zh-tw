---
title: -addmodule
ms.date: 03/09/2018
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
ms.openlocfilehash: 3e5c94cce8b16649854050855800ac1bf2fc6572
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580573"
---
# <a name="-addmodule"></a>-addmodule
讓編譯器將所指定檔案的類型資訊全部提供給您目前編譯的專案。  
  
## <a name="syntax"></a>語法  
  
```  
-addmodule:fileList  
```  
  
## <a name="arguments"></a>引數  
 `fileList`  
 必要項。 檔案所含的中繼資料，但不是包含組件資訊清單的逗號分隔清單。 應該以引號括住包含空格的檔案名稱 ("")。  
  
## <a name="remarks"></a>備註  
 依列出的檔案`fileList`參數必須以建立`-target:module`選項，或使用其他編譯器相當於`-target:module`。  
  
 加上的所有模組`-addmodule`必須位於執行階段的輸出檔相同的目錄。 也就是您可以在任何目錄中指定模組，在編譯時期，但該模組在執行階段時，必須在應用程式目錄中。 如果不是，您會取得<xref:System.TypeLoadException>時發生錯誤。  
  
 如果您指定 （隱含或明確） 任何[-目標 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)以外的其他選項`-target:module`與`-addmodule`，您將傳遞至檔案`-addmodule`成為專案的組件的一部分。 組件，才能執行輸出檔案，其中具有一個或多個檔案加`-addmodule`。  
  
 使用[/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)從包含的組件檔案匯入中繼資料。  
  
> [!NOTE]
>  `-addmodule`選項不是從 Visual Studio 開發環境中使用; 只有在從命令列編譯時均可使用。  
  
## <a name="example"></a>範例  
 下列程式碼會建立模組。  
  
 [!code-vb[VbVbalrCompiler#47](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_1.vb)]  
  
 下列程式碼匯入模組的類型。  
  
 [!code-vb[VbVbalrCompiler#48](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/addmodule_2.vb)]  
  
 當您執行`t1`，它會輸出`802`。  
  
## <a name="see-also"></a>另請參閱
- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [-參考 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
