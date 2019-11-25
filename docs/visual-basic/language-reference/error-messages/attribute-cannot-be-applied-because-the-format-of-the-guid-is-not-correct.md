---
title: 無法套用 '<attribute>'，因為 GUID '<number>' 的格式不正確
ms.date: 07/20/2015
f1_keywords:
- vbc32500
- bc32500
helpviewer_keywords:
- BC32500
ms.assetid: 6fa34c55-368e-4d7d-b488-07a3fffe045f
ms.openlocfilehash: f7b6e42480075666ce9f7e8fc6966bd4bb6b888a
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73977321"
---
# <a name="attribute-cannot-be-applied-because-the-format-of-the-guid-number-is-not-correct"></a>'\<屬性 > ' 無法套用，因為 GUID '\<號碼 > ' 的格式不正確

`COMClassAttribute` 屬性區塊會指定不符合 GUID 適當格式的全域唯一識別碼（GUID）。 `COMClassAttribute` 使用 Guid 來唯一識別類別、介面和建立事件。  
  
 GUID 由 16 個位元組組成，前八位是數字，後八位是二進位。 它是由 Microsoft 公用程式（例如 uuidgen）所產生，並保證在空間和時間中是唯一的。  
  
 **錯誤識別碼：** BC32500  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 判斷識別 COM 物件所需的正確 GUID 或 Guid。  
  
2. 請確定正確複製要呈現給 `COMClassAttribute` 屬性區塊的 GUID 字串。  
  
## <a name="see-also"></a>請參閱

- <xref:System.Guid>
- [屬性概觀](../../../visual-basic/programming-guide/concepts/attributes/index.md)
