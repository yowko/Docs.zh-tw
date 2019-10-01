---
title: '#ExternalSource 指示詞（Visual Basic）'
ms.date: 07/20/2015
f1_keywords:
- '#Externalsource'
- '#ExternalSource'
- vb.ExternalSource
- Externalsource
- vb.#ExternalSource
- ExternalSource
helpviewer_keywords:
- ExternalSource directive (#ExternalSource)
- '#ExternalSource directive'
ms.assetid: 243bc6a2-34c3-4eeb-a776-9fd2bf988149
ms.openlocfilehash: ac7096e998dd8d2a416dc739e1d7625e1abff7a6
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696830"
---
# <a name="externalsource-directive"></a>#ExternalSource 指示詞
表示原始程式程式碼與來源外部文字之間的對應。  
  
## <a name="syntax"></a>語法  
  
```vb  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a>組件  
 `StringLiteral`  
 外部來源的路徑。  
  
 `IntLiteral`  
 外部來源第一行的行號。  
  
 `LogicalLine`  
 外部來源中發生錯誤的行。  
  
 `#End ExternalSource`  
 終止 `#ExternalSource` 區塊。  
  
## <a name="remarks"></a>備註  
 這個指示詞僅供編譯器和偵錯工具使用。  
  
 原始程式檔可能包含外部來源指示詞，這表示原始程式檔中的特定程式程式碼與來源外部的文字之間的對應，例如 .aspx 檔案。 如果在編譯期間于指定的原始程式碼中遇到錯誤，則會將它們識別為來自外部來源。  
  
 外部來源指示詞不會影響編譯，而且無法加以嵌套。 它們僅供應用程式內部使用。  
  
## <a name="see-also"></a>另請參閱

- [條件式編譯](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
