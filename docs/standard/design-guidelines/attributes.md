---
title: 屬性
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- attributes [.NET Framework], about
- class library design guidelines [.NET Framework], attributes
ms.assetid: ee0038ef-b247-4747-a650-3c5c5cd58d8b
ms.openlocfilehash: 3c0e1b8c20042c085d4ace996a084cbd464d3b21
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617557"
---
# <a name="attributes"></a>屬性
<xref:System.Attribute?displayProperty=nameWithType>是用來定義自訂屬性的基類。

 屬性（attribute）是可以新增至程式設計專案（例如元件、類型、成員和參數）的批註。 它們會儲存在元件的中繼資料中，而且可以在執行時間使用反映 Api 來存取。 例如，架構 <xref:System.ObsoleteAttribute> 會定義，它可以套用至類型或成員，以表示類型或成員已被取代。

 屬性可以有一或多個屬性，其中包含與屬性相關的其他資料。 例如， `ObsoleteAttribute` 可能會包含有關發行的其他資訊，其中類型或成員已被取代，而新 api 的描述則取代過時的 api。

 套用屬性時，必須指定屬性的某些屬性。 這些稱為必要的屬性或必要的引數，因為它們是以位置函式參數表示。 例如，的 <xref:System.Diagnostics.ConditionalAttribute.ConditionString%2A> 屬性 <xref:System.Diagnostics.ConditionalAttribute> 是必要的屬性。

 套用屬性時，不一定要指定的屬性稱為選擇性屬性（或選擇性引數）。 它們是以可設定的屬性來表示。 當套用屬性時，編譯器會提供特殊語法來設定這些屬性。 例如， <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> 屬性代表一個選擇性引數。

 ✔️ DO 使用後置詞 "Attribute" 來命名自訂屬性類別。

 ✔️，請將套用 <xref:System.AttributeUsageAttribute> 至自訂屬性。

 ✔️提供選擇性引數的可設定屬性。

 ✔️提供必要引數的僅限取得屬性。

 ✔️確實提供了用來初始化對應于必要引數之屬性的參數化參數。 每個參數都應該具有相同的名稱（但大小寫不同）做為對應的屬性。

 ❌請避免提供函數參數來初始化對應于選擇性引數的屬性。

 換句話說，沒有可同時使用「函式」和「setter」設定的屬性。 這項指導方針非常明確地說，哪些引數是選擇性的，而且是必要的，而且可以避免有兩種方式來執行相同的動作。

 ❌避免多載自訂屬性的函式。

 只有一個函式會清楚地與使用者通訊，而這些引數是必要的，哪些是選擇性的。

 ✔️在可能的情況下密封自訂屬性類別。 這會讓屬性的查詢速度更快。

 *部分 &copy; 2005，2009 Microsoft Corporation。已保留擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。**

## <a name="see-also"></a>另請參閱

- [架構設計方針](index.md)
- [使用指導方針](usage-guidelines.md)
