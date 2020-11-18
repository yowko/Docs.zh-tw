---
title: 抽象 (抽象類型和介面)
ms.date: 10/22/2008
helpviewer_keywords:
- interfaces [.NET Framework], abstract
- abstract interfaces [.NET Framework]
- abstract types [.NET Framework]
- types [.NET Framework], abstract
ms.assetid: 0a632bc7-9b03-44ee-8842-c82f88672a45
ms.openlocfilehash: 6acefa2d4a2aed8fca5d0b7db634d393baac6b58
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821628"
---
# <a name="abstractions-abstract-types-and-interfaces"></a>抽象 (抽象類型和介面)
抽象概念是一種描述合約的類型，但不會提供完整的合約執行。 抽象概念通常會實作為抽象類別或介面，並隨附一組定義完善的參考檔，說明實作為合約的型別所需的語法。 .NET Framework 中最重要的抽象概念包括 <xref:System.IO.Stream> 、 <xref:System.Collections.Generic.IEnumerable%601> 和 <xref:System.Object> 。

 您可以藉由執行可支援抽象概念的具象型別，以及使用此具象型別搭配使用 (在) 抽象概念上運作的架構 Api，來擴充架構。

 有意義且有用的抽象概念，能夠承受時間的測試，是很難設計的。 主要的困難是取得一組正確的成員，而不是更多。 如果抽象概念的成員太多，就會變得很難或甚至根本無法執行。 如果該功能的成員太少，在許多有趣的情況下就會變得無用。

 架構中有太多抽象概念也會對架構的可用性造成負面影響。 您通常很難瞭解抽象概念，而不需要瞭解如何將它放入具體的實體，以及在抽象上操作之 Api 的較大圖片。 此外，抽象概念和其成員的名稱一定是抽象的，這通常會讓它們變得更清楚且 unapproachable，而不需要先瞭解其使用方式的廣泛內容。

 不過，抽象層提供了功能強大的擴充性，而其他擴充性機制通常不能相符。 它們是許多架構模式的核心，例如外掛程式、控制反轉 (IoC) 、管線等等。 它們對於架構的可測試性也非常重要。 良好的抽象概念可讓您針對單元測試的目的，將繁重的相依性存根。 總而言之，抽象概念負責最豐富的新式物件導向架構。

 ❌ 除非透過開發數個具象的實作為測試，以及使用抽象概念的 Api，否則請勿提供抽象。

 設計抽象概念時，✔️務必仔細選擇抽象類別和介面。

 ✔️考慮提供抽象概念的參考測試。 這類測試應可讓使用者測試其執行是否正確地實行合約。

 *部分©2005、2009 Microsoft Corporation。保留的擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。

## <a name="see-also"></a>請參閱

- [架構設計指導方針](index.md)
- [擴充性設計](designing-for-extensibility.md)
