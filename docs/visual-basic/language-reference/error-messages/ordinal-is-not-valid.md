---
title: 無效的序數
ms.date: 07/20/2015
f1_keywords:
- vbrID452
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
ms.openlocfilehash: 7b9bd8435b56dd5e33d14eb35d76aacc7d60c8b5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413049"
---
# <a name="ordinal-is-not-valid"></a>無效的序數
您對動態連結程式庫（DLL）的呼叫會使用語法，而不是使用程式名稱 `#num` 。 此錯誤的可能原因如下：  
  
- 嘗試將 `#num` 運算式轉換成序數失敗。  
  
- 指定的未 `#num` 指定 DLL 中的任何函式。  
  
- 類型程式庫具有不正確宣告，導致內部使用不正確序數。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 請確定運算式代表有效的數位，或依名稱呼叫程式。  
  
2. 請確定在 `#num` DLL 中識別有效的函式。  
  
3. 藉由將程式碼批註化，來隔離造成問題的程序呼叫。 撰寫 `Declare` 程式的語句，並向類型程式庫廠商報告問題。  
  
## <a name="see-also"></a>另請參閱

- [Declare Statement](../statements/declare-statement.md)
