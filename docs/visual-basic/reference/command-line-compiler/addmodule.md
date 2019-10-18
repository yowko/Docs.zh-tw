---
title: -addmodule
ms.date: 03/09/2018
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
ms.openlocfilehash: dd98b45d75ff421dc81666ed47695132a49bfa3a
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524475"
---
# <a name="-addmodule"></a>-addmodule
讓編譯器將所指定檔案的類型資訊全部提供給您目前編譯的專案。  
  
## <a name="syntax"></a>語法  
  
```console  
-addmodule:fileList  
```  
  
## <a name="arguments"></a>引數  
 `fileList`  
 必要項。 包含中繼資料但不包含組件資訊清單的檔案清單（以逗號分隔）。 包含空格的檔案名應該以引號（""）括住。  
  
## <a name="remarks"></a>備註  
 @No__t_0 參數所列出的檔案必須使用 [`-target:module`] 選項來建立，或與另一個編譯器相當於 [`-target:module`]。  
  
 使用 `-addmodule` 新增的所有模組，都必須位於與執行時間輸出檔案相同的目錄中。 也就是說，您可以在編譯時期指定任何目錄中的模組，但模組必須在執行時間的應用程式目錄中。 如果不是，您會收到 <xref:System.TypeLoadException> 錯誤。  
  
 如果您指定（隱含或明確）具有 `-addmodule` `-target:module` 以外的任何[目標（Visual Basic）](../../../visual-basic/reference/command-line-compiler/target.md)選項，您傳遞至 `-addmodule` 的檔案就會成為專案元件的一部分。 需要元件才能執行包含一或多個以 `-addmodule` 新增之檔案的輸出檔。  
  
 使用[-reference （Visual Basic）](../../../visual-basic/reference/command-line-compiler/reference.md)從包含元件的檔案匯入中繼資料。  
  
> [!NOTE]
> Visual Studio 開發環境中無法使用 [`-addmodule`] 選項;只有在從命令列編譯時，才可以使用它。  
  
## <a name="example"></a>範例  
 下列程式碼會建立模組。  
  
 [!code-vb[VbVbalrCompiler#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#47)]  
  
 下列程式碼會匯入模組的類型。  
  
 [!code-vb[VbVbalrCompiler#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#48)]  
  
 當您執行 `t1` 時，它會輸出 `802`。  
  
## <a name="see-also"></a>請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [-target （Visual Basic）](../../../visual-basic/reference/command-line-compiler/target.md)
- [-reference （Visual Basic）](../../../visual-basic/reference/command-line-compiler/reference.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
