---
title: -addmodule
ms.date: 03/09/2018
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
ms.openlocfilehash: 2db122acc03056a9cb6f355119d4c4e6da6ed175
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097783"
---
# <a name="-addmodule"></a>-addmodule

讓編譯器將所指定檔案的類型資訊全部提供給您目前編譯的專案。  
  
## <a name="syntax"></a>語法  
  
```console  
-addmodule:fileList  
```  
  
## <a name="arguments"></a>引數  

 `fileList`  
 必要。 包含中繼資料但不包含組件資訊清單的檔案清單（以逗號分隔）。 包含空格的檔案名應以引號括住 ( "" ) 。  
  
## <a name="remarks"></a>備註  

 參數所列出的檔案 `fileList` 必須以 `-target:module` 選項建立，或與另一個編譯器的相等 `-target:module` 。  
  
 所有新增的模組都 `-addmodule` 必須與執行時間的輸出檔案位於相同的目錄中。 也就是說，您可以在編譯時期指定任何目錄中的模組，但模組在執行時間必須在應用程式目錄中。 如果不是，您會收到 <xref:System.TypeLoadException> 錯誤訊息。  
  
 如果您指定 (以隱含或明確的方式) 任何[目標 (Visual Basic) ](target.md) 選項 `-target:module` `-addmodule` ，則您傳遞給的檔案 `-addmodule` 會成為專案元件的一部分。 需要元件，才能執行包含一或多個新增之檔案的輸出檔 `-addmodule` 。  
  
 使用 [-reference (Visual Basic) ](reference.md) 從包含元件的檔案匯入中繼資料。  
  
> [!NOTE]
> `-addmodule`選項無法在 Visual Studio 開發環境中使用; 只有在從命令列編譯時，才能使用此選項。  
  
## <a name="example"></a>範例  

 下列程式碼會建立模組。  
  
 [!code-vb[VbVbalrCompiler#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#47)]  
  
 下列程式碼會匯入模組的類型。  
  
 [!code-vb[VbVbalrCompiler#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#48)]  
  
 當您執行時 `t1` ，它會輸出 `802` 。  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](index.md)
- [-目標 (Visual Basic) ](target.md)
- [-reference (Visual Basic) ](reference.md)
- [編譯命令列的範例](sample-compilation-command-lines.md)
