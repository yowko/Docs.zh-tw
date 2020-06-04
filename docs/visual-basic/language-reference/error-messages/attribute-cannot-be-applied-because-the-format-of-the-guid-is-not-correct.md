---
title: 無法套用 '<attribute>'，因為 GUID '<number>' 的格式不正確
ms.date: 07/20/2015
f1_keywords:
- vbc32500
- bc32500
helpviewer_keywords:
- BC32500
ms.assetid: 6fa34c55-368e-4d7d-b488-07a3fffe045f
ms.openlocfilehash: 554c38c8f44999feba4cfa04d58ce2f07e955eb1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409916"
---
# <a name="attribute-cannot-be-applied-because-the-format-of-the-guid-number-is-not-correct"></a>無法套用 '\<attribute>'，因為 GUID '\<number>' 的格式不正確

`COMClassAttribute`屬性區塊會指定不符合 GUID 適當格式的全域唯一識別碼（guid）。 `COMClassAttribute`使用 Guid 來唯一識別類別、介面和建立事件。  
  
 GUID 由 16 個位元組組成，前八位是數字，後八位是二進位。 它是由 Microsoft 公用程式（例如 uuidgen）所產生，並保證在空間和時間中是唯一的。  
  
 **錯誤識別碼：** BC32500  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. 判斷識別 COM 物件所需的正確 GUID 或 Guid。  
  
2. 請確定正確複製要呈現給 `COMClassAttribute` 屬性區塊的 GUID 字串。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Guid>
- [屬性概觀](../../programming-guide/concepts/attributes/index.md)
