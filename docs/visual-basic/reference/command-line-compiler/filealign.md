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
ms.openlocfilehash: 2893c1760a856a7d736e9c03ba33d9771722b5b2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929478"
---
# <a name="-filealign"></a>-filealign
指定要對齊輸出檔案區段的位置。  
  
## <a name="syntax"></a>語法  
  
```  
-filealign:number  
```  
  
## <a name="arguments"></a>引數  
 `number`  
 必要項。 值, 指定輸出檔案中區段的對齊方式。 有效值為 512、1024、2048、4096 和 8192。 這些值是以位元組為單位。  
  
## <a name="remarks"></a>備註  
 您可以使用`-filealign`選項來指定輸出檔案中區段的對齊方式。 區段是可移植執行檔 (PE) 中的連續記憶體區塊, 其中包含程式碼或資料。 `-filealign`選項可讓您以非標準的對齊方式編譯應用程式; 大部分的開發人員不需要使用此選項。  
  
 每個區段會對齊屬於`-filealign`值倍數的界限。 沒有固定預設值。 如果`-filealign`未指定, 編譯器會在編譯時期選取預設值。  
  
 藉由指定區段大小, 您可以變更輸出檔案的大小。 修改區段大小對執行於較小裝置上的程式而言可能很有用。  
  
> [!NOTE]
> 此`-filealign`選項無法從 Visual Studio 開發環境中使用; 只有在從命令列進行編譯時, 才能使用此選項。  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
