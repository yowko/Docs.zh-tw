---
title: 抽象 (抽象類型和介面)
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- interfaces [.NET Framework], abstract
- abstract interfaces [.NET Framework]
- abstract types [.NET Framework]
- types [.NET Framework], abstract
ms.assetid: 0a632bc7-9b03-44ee-8842-c82f88672a45
ms.openlocfilehash: fd5b8fe10d0dcca5da3a2093f7be37f6d88b382a
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280610"
---
# <a name="abstractions-abstract-types-and-interfaces"></a>抽象 (抽象類型和介面)
抽象概念是描述合約，但不提供合約完整執行的類型。 抽象概念通常會實作為抽象類別或介面，而且會隨附一組定義完善的參考檔，說明實作為合約的型別所需的語法。 .NET Framework 中一些最重要的抽象概念包括 <xref:System.IO.Stream> 、 <xref:System.Collections.Generic.IEnumerable%601> 和 <xref:System.Object> 。

 您可以藉由實作為支援抽象概念的具象型別，並使用此具體型別搭配耗用（操作）抽象概念的架構 Api，來擴充架構。

 有意義且有用的抽象概念，能夠承受時間測試，並不容易設計。 主要的難題是取得正確的成員集合，而不是更少。 如果抽象概念有太多成員，就會變得很難或甚至無法執行。 如果其承諾的功能有太少的成員，則在許多有趣的案例中會變得毫無用處。

 架構中有太多抽象概念也會對架構的可用性造成負面影響。 您通常很難瞭解抽象概念，而不需要瞭解它如何融入具體的執行，以及在抽象概念上操作的 Api。 此外，抽象和其成員的名稱一定是抽象的，這通常會使它們變得更不容易 unapproachable，而不需要先瞭解其使用方式的更廣泛內容。

 不過，抽象層提供非常強大的擴充性，其他擴充性機制通常不會符合。 它們是許多架構模式的核心，例如外掛程式、控制反轉（IoC）、管線等等。 它們對於架構的可測試性也非常重要。 良好的抽象概念可讓您針對單元測試的目的，將繁重的相依性 stub。 總而言之，抽象概念會負責各種現代化物件導向架構的豐富功能。

 ❌除非藉由開發數個具體的執行和使用抽象概念的 Api 進行測試，否則請不要提供抽象概念。

 在設計抽象概念時，✔️請在抽象類別和介面之間謹慎選擇。

 ✔️考慮為抽象的具體執行提供參考測試。 這類測試應允許使用者測試其執行是否正確地實作為合約。

 *部分©2005、2009 Microsoft Corporation。已保留擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。**

## <a name="see-also"></a>另請參閱

- [架構設計方針](index.md)
- [擴充性設計](designing-for-extensibility.md)
