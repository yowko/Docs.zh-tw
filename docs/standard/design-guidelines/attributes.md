---
title: 屬性
ms.date: 10/22/2008
helpviewer_keywords:
- attributes [.NET Framework], about
- class library design guidelines [.NET Framework], attributes
ms.assetid: ee0038ef-b247-4747-a650-3c5c5cd58d8b
ms.openlocfilehash: c02c41244fa74b686277c2f3c3940405fe2d95ba
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95701363"
---
# <a name="attributes"></a>屬性

<xref:System.Attribute?displayProperty=nameWithType> 是用來定義自訂屬性的基類。

 屬性是可以加入至程式設計專案（例如元件、類型、成員和參數）的附注。 它們會儲存在元件的中繼資料中，並可在執行時間使用反映 Api 來存取。 例如，架構會定義可套用 <xref:System.ObsoleteAttribute> 至類型或成員的，以表示類型或成員已被取代。

 屬性可以有一或多個屬性包含與屬性相關的其他資料。 例如， `ObsoleteAttribute` 可能會包含類型或成員已被取代之版本的其他相關資訊，以及取代淘汰的 api 之新 api 的描述。

 套用屬性時，必須指定屬性的某些屬性。 這些是必要的屬性或必要的引數，因為它們是以位置的函式參數來表示。 例如，的 <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> 屬性 <xref:System.Diagnostics.ConditionalAttribute> 是必要屬性。

 套用屬性時，不一定要指定的屬性稱為選用屬性 (或) 選擇性引數。 它們是由可設定的屬性工作表示。 當套用屬性時，編譯器會提供特殊的語法來設定這些屬性。 例如， <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> 屬性代表選擇性引數。

 ✔️使用尾碼 "Attribute" 來命名自訂屬性類別。

 ✔️請將套用 <xref:System.AttributeUsageAttribute> 至自訂屬性。

 ✔️確實提供選擇性引數的可設定屬性。

 ✔️確實提供必要引數的 get 屬性。

 ✔️確實提供了函式參數，以初始化對應到必要引數的屬性。 每個參數都應該有相同的名稱 (但使用不同的大小寫) 作為對應的屬性。

 ❌ 避免提供函式參數來初始化對應至選擇性引數的屬性。

 換句話說，沒有可同時以函式和 setter 設定的屬性。 這項指導方針很明確地明確指出哪些引數是選擇性的，哪些是必要的，而且可以避免有兩種方法來執行相同的工作。

 ❌ 避免多載自訂屬性的函式。

 只有一個函式會清楚地與使用者傳達需要哪些引數，哪些是選擇性的。

 ✔️盡可能密封自訂屬性類別。 這樣就能更快地查閱屬性。

 *部分 &copy; 2005、2009 Microsoft Corporation。保留的擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。

## <a name="see-also"></a>另請參閱

- [架構設計指導方針](index.md)
- [使用指導方針](usage-guidelines.md)
