---
title: '## ExternalSource 指示詞 (Visual Basic)'
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
ms.openlocfilehash: dcde8507eb033d0a47d5c5d3fa36176cd63b0856
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43861779"
---
# <a name="externalsource-directive"></a>#ExternalSource 指示詞
表示特定的原始程式碼行和來源外部文字之間的對應。  
  
## <a name="syntax"></a>語法  
  
```  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a>組件  
 `StringLiteral`  
 外部來源的路徑。  
  
 `IntLiteral`  
 外部來源的第一行的行號。  
  
 `LogicalLine`  
 外部來源中發生錯誤的行。  
  
 `#End ExternalSource`  
 終止 `#ExternalSource` 區塊。  
  
## <a name="remarks"></a>備註  
 這個指示詞僅供編譯器和偵錯工具。  
  
 原始程式檔可能包含外部來源指示詞，可指出特定程式碼中的原始程式檔行與外部來源，例如.aspx 檔案的文字之間的對應。 如果在編譯期間指定的原始程式碼中遇到錯誤，它們會識別為來自外部來源。  
  
 外部來源指示詞有對於編譯沒有作用，而且不能巢狀。 它們被供內部使用僅限應用程式。  
  
## <a name="see-also"></a>另請參閱  
 [條件式編譯](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
