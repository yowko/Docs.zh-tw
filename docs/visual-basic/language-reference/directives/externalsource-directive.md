---
title: '## ExternalSource 指示詞'
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
ms.openlocfilehash: 146ab41d74b45acc4063e2463baca26c7caa4652
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
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
  
 原始程式檔可能包含外部來源指示詞，指出特定的原始程式檔中的程式碼行與外部來源，例如.aspx 檔案的文字之間的對應。 如果在編譯期間指定之的來源的程式碼中發生錯誤，它們會被識別為來自外部來源。  
  
 外部來源指示詞不會影響在編譯時，不可為巢狀。 它們被供內部使用僅代表應用程式。  
  
## <a name="see-also"></a>另請參閱  
 [條件式編譯](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
