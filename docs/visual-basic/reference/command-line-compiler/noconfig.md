---
title: -noconfig
ms.date: 03/13/2018
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
ms.openlocfilehash: c57ed1699d110959e9faf3dc3d43bcc200851c1c
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005442"
---
# <a name="-noconfig"></a>-noconfig
指定編譯器不應自動參考常用的 .NET Framework 元件，或匯入 `System` 和 @no__t 1 命名空間。  
  
## <a name="syntax"></a>語法  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a>備註  
 @No__t-0 選項會指示編譯器不要以 Vbc 檔案進行編譯，此檔案位於與 Vbc 檔案相同的目錄中。 Vbc 檔案會參考常用的 .NET Framework 元件，並匯入 `System` 和 @no__t 1 命名空間。 除非指定了 `-nostdlib` 選項，否則編譯器會隱含地參考 System.web 元件。 @No__t-0 選項會指示編譯器不要使用 Vbc 或自動參考 system.string 元件來編譯。  
  
> [!NOTE]
> 我們一律會參考 Mscorlib.dll 和 Microsoft。  
  
 您可以修改 Vbc .rsp 檔案，以指定應包含在每個 Vbc 編譯中的其他編譯器選項（除非指定 `-noconfig` 選項時除外）。 如需詳細資訊，請參閱 [@ (指定回應檔)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)。  
  
 編譯器會處理過去傳遞給 `vbc` 命令的選項。 因此，命令列上的任何選項都會覆寫 Vbc .rsp 檔案中相同選項的設定。  
  
> [!NOTE]
> @No__t-0 選項無法從 Visual Studio 開發環境中使用;只有在從命令列編譯時，才可以使用它。  
  
## <a name="see-also"></a>另請參閱

- [-nostdlib （Visual Basic）](../../../visual-basic/reference/command-line-compiler/nostdlib.md)
- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
- [@ (指定回應檔)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)
- [-reference （Visual Basic）](../../../visual-basic/reference/command-line-compiler/reference.md)
