---
title: 無效的序數
ms.date: 07/20/2015
f1_keywords:
- vbrID452
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
ms.openlocfilehash: 12d73b33e3c025b40c98d84e3507af7be1e1e91a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593599"
---
# <a name="ordinal-is-not-valid"></a>無效的序數
使用數字，而不是程序名稱，指示您動態連結程式庫 (DLL) 的呼叫使用`#num`語法。 此錯誤有下列可能原因：  
  
-   嘗試將轉換`#num`無法為序數的運算式。  
  
-   `#num`指定 DLL 中未指定任何函式。  
  
-   類型程式庫有無效的宣告導致無效的序數數字的內部使用。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  請確定運算式代表有效的數字，或呼叫程序的名稱。  
  
2.  請確定`#num`識別 DLL 中是有效的函數。  
  
3.  找出造成問題，註解的程式碼的程序呼叫。 寫入`Declare`程序，並回報問題類型程式庫的供應商的陳述式。  
  
## <a name="see-also"></a>另請參閱  
 [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)
