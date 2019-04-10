---
title: 無效的序數
ms.date: 07/20/2015
f1_keywords:
- vbrID452
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
ms.openlocfilehash: 28f78161e14604c1f59872801855ccc918faec58
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59299250"
---
# <a name="ordinal-is-not-valid"></a>無效的序數
您的動態連結程式庫 (DLL) 的呼叫表示使用的數字，而不是程序名稱，使用`#num`語法。 此錯誤有下列可能的原因：  
  
-   嘗試將轉換`#num`失敗為序數的運算式。  
  
-   `#num`指定 DLL 中未指定任何函式。  
  
-   類型程式庫有無效的宣告，因而導致無效的序數數字的內部使用。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 請確認運算式代表有效的數字，或呼叫程序的名稱。  
  
2. 請確定`#num`識別有效的函式在 DLL 中。  
  
3. 找出造成問題註解的程式碼的程序呼叫。 撰寫`Declare`陳述式的程序和報表類型程式庫的供應商的問題。  
  
## <a name="see-also"></a>另請參閱

- [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)
