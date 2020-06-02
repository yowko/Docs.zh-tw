---
title: 欄位設計
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- fields, design guidelines
- read-only fields
- member design guidelines, fields
ms.assetid: 7cb4b0f3-7a10-4c93-b84d-733f7134fcf8
ms.openlocfilehash: 3a5ae985ab161899fbb5e96f9b0ef0cfa90b957c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289742"
---
# <a name="field-design"></a>欄位設計
封裝的原則是物件導向設計中最重要的概念之一。 此原則指出，儲存在物件內的資料應該只能供該物件存取。

 解讀原則的一個實用方法是說，型別應該設計成讓該類型的欄位變更（名稱或類型變更），而不需要中斷程式碼，而不是針對該類型的成員進行。 這種轉譯會立即暗示所有欄位都必須是私用的。

 我們會從這項嚴格的限制排除常數和靜態唯讀欄位，因為這類欄位幾乎是定義的，因此永遠不需要變更。

 ❌請勿提供公用或受保護的實例欄位。

 您應該提供屬性來存取欄位，而不是將它們設為公用或保護。

 ✔️對於永遠不會變更的常數，請使用常數位段。

 編譯器會將 const 欄位的值直接帶到呼叫程式碼中。 因此，如果沒有中斷相容性的風險，就永遠不會變更 const 值。

 ✔️ `readonly` 針對預先定義的物件實例使用公用靜態欄位。

 如果有預先定義的類型實例，請將其宣告為類型本身的公用唯讀靜態欄位。

 ❌請勿將可變類型的實例指派給 `readonly` 欄位。

 可變型別是具有實例的型別，可在具現化之後加以修改。 例如，陣列、大部分的集合和資料流程都是可變動的類型，但 <xref:System.Int32?displayProperty=nameWithType> 、 <xref:System.Uri?displayProperty=nameWithType> 和 <xref:System.String?displayProperty=nameWithType> 都是不可變的。 [參考型別] 欄位上的唯讀修飾詞會防止儲存在欄位中的實例被取代，但它不會藉由呼叫變更實例的成員來防止修改欄位的實例資料。

 *部分©2005、2009 Microsoft Corporation。已保留擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。**

## <a name="see-also"></a>另請參閱

- [成員設計方針](member.md)
- [架構設計方針](index.md)
