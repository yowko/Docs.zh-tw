---
title: 無法套用 '<attribute>'，因為 GUID '<number>' 的格式不正確
ms.date: 07/20/2015
f1_keywords:
- vbc32500
- bc32500
helpviewer_keywords:
- BC32500
ms.assetid: 6fa34c55-368e-4d7d-b488-07a3fffe045f
ms.openlocfilehash: 1e92c77e6138bbd546d9b837e095e41d5dfaf30c
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55279860"
---
# <a name="attribute-cannot-be-applied-because-the-format-of-the-guid-number-is-not-correct"></a>'\<屬性 >' 無法套用，因為 GUID 的格式'\<編號 >' 不正確
A`COMClassAttribute`屬性區塊指定全域唯一識別碼 (GUID) guid 不符合為適當格式。 `COMClassAttribute` 使用 Guid 來唯一識別類別、 介面，以及建立事件。  
  
 GUID 由 16 個位元組組成，前八位是數字，後八位是二進位。 它由 Microsoft 公用程式，例如 uuidgen.exe 所產生，而且保證是唯一的時間和空間內。  
  
 **錯誤 ID:** BC32500  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  判斷正確的 GUID 或需要識別 COM 物件的 Guid。  
  
2.  請確定正確複製要呈現給 `COMClassAttribute` 屬性區塊的 GUID 字串。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Guid>
- [屬性概觀](../../../visual-basic/programming-guide/concepts/attributes/index.md)

