---
title: 抽象類別設計
ms.date: 10/22/2008
helpviewer_keywords:
- type design guidelines, abstract classes
- abstract classes, design guidelines
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], abstract
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d3646e6d-5c1f-4922-8fb0-ec5effb30d60
ms.openlocfilehash: 6903e10c8695376d8ac5961461796c5413307f90
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821641"
---
# <a name="abstract-class-design"></a>抽象類別設計

❌ 請勿在抽象類別型中定義公用或受保護的內部函式。

 只有當使用者需要建立型別的實例時，才應為公用的。 因為您無法建立抽象類別型的實例，所以具有公用函式的抽象型別設計不正確，而且會誤導使用者。

 ✔️在抽象類別中定義了受保護的或內部的函式。

 受保護的函式更為常見，只要在建立子類型時，基類就能自行進行初始化。

 內部的函式可以用來將抽象類別的具體執行限制為定義類別的元件。

 ✔️請提供至少一個繼承自您所送出之抽象類別的具象型別。

 這樣做有助於驗證抽象類別的設計。 例如，  <xref:System.IO.FileStream?displayProperty=nameWithType> 是抽象類別的實作為 <xref:System.IO.Stream?displayProperty=nameWithType> 。

 *部分©2005、2009 Microsoft Corporation。保留的擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。

## <a name="see-also"></a>請參閱

- [型別設計方針](type.md)
- [架構設計指導方針](index.md)
