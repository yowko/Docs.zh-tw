---
title: -filealign
ms.date: 03/10/2018
helpviewer_keywords:
- sections compiler option [Visual Basic]
- alignment compiler option [Visual Basic]
- -filealign compiler option [Visual Basic]
- section alignment
- /filealign compiler option [Visual Basic]
- filealign compiler option [Visual Basic]
ms.assetid: cc61ec3d-ad38-4b28-9659-099d73cad099
ms.openlocfilehash: 9a844515a4596064937762ac05b850463f1b5e14
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819173"
---
# <a name="-filealign"></a>-filealign
指定要對齊輸出檔案區段的位置。  
  
## <a name="syntax"></a>語法  
  
```  
-filealign:number  
```  
  
## <a name="arguments"></a>引數  
 `number`  
 必要項。 值，指定輸出檔中的區段的對齊方式。 有效值為 512、1024、2048、4096 和 8192。 這些值是以位元組為單位。  
  
## <a name="remarks"></a>備註  
 您可以使用`-filealign`選項來指定輸出檔案區段的對齊方式。 在可攜式執行檔 (PE) 檔案包含程式碼或資料的連續記憶體區塊的區段。 `-filealign`選項可讓您編譯您的應用程式，使用標準的對齊方式，不需要使用此選項大部分的開發人員。  
  
 每個區段都會對齊界限的倍數`-filealign`值。 沒有固定預設值。 如果`-filealign`未指定，則編譯器會在編譯時期選取預設值。  
  
 藉由指定區段大小，您可以變更輸出檔案的大小。 修改區段大小對執行於較小裝置上的程式而言可能很有用。  
  
> [!NOTE]
>  `-filealign`選項不是從 Visual Studio 開發環境中使用; 只有在從命令列編譯時均可使用。  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
