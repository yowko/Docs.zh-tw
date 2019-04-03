---
title: -參考 (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /reference compiler option [Visual Basic]
- r compiler option [Visual Basic]
- -reference compiler option [Visual Basic]
- /r compiler option [Visual Basic]
- reference compiler option [Visual Basic]
- -r compiler option [Visual Basic]
ms.assetid: 66bdfced-bbf6-43d1-a554-bc0990315737
ms.openlocfilehash: 21efca701eb16898dd291d73bf0431641ba75d12
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826115"
---
# <a name="-reference-visual-basic"></a>-參考 (Visual Basic)
可讓編譯器進行指定的組件中的類型資訊提供給您目前編譯的專案。  
  
## <a name="syntax"></a>語法  
  
```  
-reference:fileList  
' -or-  
-r:fileList  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`fileList`|必要項。 以逗號分隔的組件檔案名稱清單。 如果檔案名稱包含空格，請用引號括住名稱。|  
  
## <a name="remarks"></a>備註  
 您匯入的檔案必須包含組件中繼資料。 只有公用型別是組件外部可見的。 [/Addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)選項，從模組匯入中繼資料。  
  
 如果您參考的組件 （組件 A） 本身參考另一個組件 (組件 B)，如果您需要參考 B 組件：  
  
-   組件 A 的類型繼承自組件 B 的類型，或是實作組件 B 的介面。  
  
-   所叫用的欄位、屬性、事件或方法具有組件 B 的傳回型別或參數類型。  
  
 使用[-libpath](../../../visual-basic/reference/command-line-compiler/libpath.md)指定一或多個組件參考所在的目錄。  
  
 編譯器無法辨識的組件 （而非模組） 中的型別，它必須強制執行解析的型別。 執行這其中一個範例是定義類型的執行個體。 其他方式可解決編譯器的組件中的型別名稱。 比方說，如果您繼承自組件中的類型，類型名稱就會知道給編譯器。  
  
 參考常用的 Vbc.rsp 回應檔[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]組件，預設會使用。 使用`-noconfig`若不想讓編譯器使用 Vbc.rsp。  
  
 `-reference` 的簡短形式為 `/r`。  
  
## <a name="example"></a>範例  
 下列命令會編譯原始程式檔`Input.vb`，並參考來自組件`Metad1.dll`並`Metad2.dll`產生`Out.exe`。  
  
```console
vbc -reference:metad1.dll,metad2.dll -out:out.exe input.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [編譯命令列範例](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
