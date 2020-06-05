---
title: -noconfig
ms.date: 03/13/2018
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
ms.openlocfilehash: ee7cd1b8039a8d9312a8b058cc85c41ca536ed2b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401936"
---
# <a name="-noconfig"></a>-noconfig
指定編譯器不應自動參考常用的 .NET Framework 元件，或匯入 `System` 和 `Microsoft.VisualBasic` 命名空間。  
  
## <a name="syntax"></a>語法  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a>備註  
 `-noconfig`選項會指示編譯器不要以 vbc 檔案進行編譯，此檔案位於與 vbc 檔案相同的目錄中。 Vbc 檔案會參考常用的 .NET Framework 元件，並匯入 `System` 和 `Microsoft.VisualBasic` 命名空間。 除非指定選項，否則編譯器會隱含地參考 System.web 元件 `-nostdlib` 。 `-nostdlib`選項會指示編譯器不要使用 Vbc .rsp 進行編譯，或自動參考 system.string 元件。  
  
> [!NOTE]
> 我們一律會參考 Mscorlib.dll 和 Microsoft。  
  
 您可以修改 Vbc .rsp 檔案，以指定應包含在每個 Vbc 編譯中的其他編譯器選項（除非指定 `-noconfig` 選項）。 如需詳細資訊，請參閱[@ （指定回應檔）](specify-response-file.md)。  
  
 編譯器會處理過去傳遞給命令的選項 `vbc` 。 因此，命令列上的任何選項都會覆寫 Vbc .rsp 檔案中相同選項的設定。  
  
> [!NOTE]
> 此 `-noconfig` 選項無法從 Visual Studio 開發環境中使用; 只有在從命令列進行編譯時，才能使用此選項。  
  
## <a name="see-also"></a>另請參閱

- [-nostdlib （Visual Basic）](nostdlib.md)
- [Visual Basic 命令列編譯器](index.md)
- [@ (指定回應檔)](specify-response-file.md)
- [-reference （Visual Basic）](reference.md)
