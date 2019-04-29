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
ms.openlocfilehash: 39e6963c97340daab3f0ab7ad6860695f1f6c135
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61747033"
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

- [條件式編譯](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
