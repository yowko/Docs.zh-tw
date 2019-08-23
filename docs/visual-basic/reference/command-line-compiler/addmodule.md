---
title: -addmodule
ms.date: 03/09/2018
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
ms.openlocfilehash: 0e0915a2534f950cec074632a59750c3f96b679d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962451"
---
# <a name="-addmodule"></a>-addmodule
讓編譯器將所指定檔案的類型資訊全部提供給您目前編譯的專案。  
  
## <a name="syntax"></a>語法  
  
```  
-addmodule:fileList  
```  
  
## <a name="arguments"></a>引數  
 `fileList`  
 必要項。 包含中繼資料但不包含組件資訊清單的檔案清單 (以逗號分隔)。 包含空格的檔案名應該以引號 ("") 括住。  
  
## <a name="remarks"></a>備註  
 `fileList`參數所列出的檔案必須`-target:module`使用選項來建立, 或與另一個編譯器的相當於`-target:module`。  
  
 使用新增的`-addmodule`所有模組, 都必須位於與執行時間輸出檔案相同的目錄中。 也就是說, 您可以在編譯時期指定任何目錄中的模組, 但模組必須在執行時間的應用程式目錄中。 如果不是, 您會收到<xref:System.TypeLoadException>錯誤。  
  
 如果您指定 [(隱含或明確)] 以外`-target:module` `-addmodule`的任何[目標 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)選項, 則您傳遞給`-addmodule`的檔案會成為專案元件的一部分。 需要元件才能執行包含一或多個已加入`-addmodule`之檔案的輸出檔。  
  
 使用[/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)從包含元件的檔案匯入中繼資料。  
  
> [!NOTE]
> 此`-addmodule`選項無法從 Visual Studio 開發環境中使用; 只有在從命令列進行編譯時, 才能使用此選項。  
  
## <a name="example"></a>範例  
 下列程式碼會建立模組。  
  
 [!code-vb[VbVbalrCompiler#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#47)]  
  
 下列程式碼會匯入模組的類型。  
  
 [!code-vb[VbVbalrCompiler#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#48)]  
  
 當您執行`t1`時, 它`802`會輸出。  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [-reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
