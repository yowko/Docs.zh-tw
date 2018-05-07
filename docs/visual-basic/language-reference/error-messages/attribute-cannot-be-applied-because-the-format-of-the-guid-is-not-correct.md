---
title: '&#39;&lt;屬性&gt;&#39;無法套用，因為 GUID 的格式&#39;&lt;數目&gt;&#39;不正確'
ms.date: 07/20/2015
f1_keywords:
- vbc32500
- bc32500
helpviewer_keywords:
- BC32500
ms.assetid: 6fa34c55-368e-4d7d-b488-07a3fffe045f
ms.openlocfilehash: 93b208b2119942f939a3af223c2f562c6097f7a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="39ltattributegt39-cannot-be-applied-because-the-format-of-the-guid-39ltnumbergt39-is-not-correct"></a>&#39;&lt;屬性&gt;&#39;無法套用，因為 GUID 的格式&#39;&lt;數目&gt;&#39;不正確
A`COMClassAttribute`屬性區塊指定全域唯一識別碼 (GUID) 的 guid 不符合為適當格式。 `COMClassAttribute` 使用 Guid 來唯一識別類別、 介面和建立事件。  
  
 GUID 由 16 個位元組組成，前八位是數字，後八位是二進位。 它由 Microsoft 公用程式，例如 uuidgen.exe 所產生，並保證是唯一的時間和空間內。  
  
 **錯誤 ID:** BC32500  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  判斷正確的 GUID 或需要識別之 COM 物件的 Guid。  
  
2.  請確定正確複製要呈現給 `COMClassAttribute` 屬性區塊的 GUID 字串。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Guid>  
[屬性概觀](../../../visual-basic/programming-guide/concepts/attributes/index.md)

