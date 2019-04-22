---
title: -noconfig
ms.date: 03/13/2018
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
ms.openlocfilehash: 44bc619c489fdff36f0b595f7d8934689b859adb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58819426"
---
# <a name="-noconfig"></a>-noconfig
指定的編譯器應該不會自動參考常用[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]組件或匯入`System`和`Microsoft.VisualBasic`命名空間。  
  
## <a name="syntax"></a>語法  
  
```  
-noconfig  
```  
  
## <a name="remarks"></a>備註  
 `-noconfig`選項會指示編譯器不要使用 Vbc.rsp 檔案，位於與 Vbc.exe 檔案相同的目錄中的檔案。 Vbc.rsp 檔案參考常用[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]組件和匯入`System`和`Microsoft.VisualBasic`命名空間。 編譯器會隱含參考之 System.dll 組件，除非`-nostdlib`指定選項。 `-nostdlib`選項會指示編譯器不要使用 vbc.rsp 進行編譯，或自動參考 System.dll 組件。  
  
> [!NOTE]
>  一律會參考 Mscorlib.dll 和 Microsoft.VisualBasic.dll 的組件。  
  
 您可以修改 Vbc.rsp 檔案來指定應包含在每次 Vbc.exe 編譯的其他編譯器選項 (指定時，除非`-noconfig`選項)。 如需詳細資訊，請參閱 [@ (指定回應檔)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)。  
  
 編譯器會處理傳遞給選項`vbc`最後一個命令。 因此，在命令列上的任何選項會覆寫在 Vbc.rsp 檔案中的相同選項的設定。  
  
> [!NOTE]
>  `-noconfig`選項不是從 Visual Studio 開發環境中使用; 只有在從命令列編譯時均可使用。  
  
## <a name="see-also"></a>另請參閱

- [-nostdlib (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nostdlib.md)
- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [@ (指定回應檔)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)
- [-參考 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
