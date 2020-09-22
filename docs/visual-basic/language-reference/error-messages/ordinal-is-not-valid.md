---
title: 無效的序數
ms.date: 07/20/2015
f1_keywords:
- vbrID452
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
ms.openlocfilehash: 64f56b2ecace0ceafb310a175ea605e6959b7256
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871393"
---
# <a name="ordinal-is-not-valid"></a>無效的序數

您對動態連結程式庫的呼叫 (DLL) 指出要使用數位，而不是程式名稱（使用語法） `#num` 。 此錯誤有下列可能的原因：  
  
- 嘗試將 `#num` 運算式轉換成序數失敗。  
  
- `#num`指定的不會指定 DLL 中的任何函數。  
  
- 類型程式庫有不正確宣告，導致內部使用不正確序數。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 請確定運算式代表有效的數位，或依名稱呼叫程式。  
  
2. 請確定 `#num` 在 DLL 中找出有效的函式。  
  
3. 將程式碼批註化，以找出造成問題的程序呼叫。 撰寫 `Declare` 程式的語句，並將問題回報給類型程式庫廠商。  
  
## <a name="see-also"></a>另請參閱

- [Declare Statement](../statements/declare-statement.md)
