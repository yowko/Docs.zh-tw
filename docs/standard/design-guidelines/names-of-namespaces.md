---
title: 命名空間的名稱
description: 使用這些指導方針，將命名空間命名為設計程式庫以延伸和與 .NET 程式庫互動的指導方針。
ms.date: 10/22/2008
helpviewer_keywords:
- names [.NET Framework], conflicts
- names [.NET Framework], namespaces
- type names, conflicts
- namespaces [.NET Framework], names
- names [.NET Framework], type names
ms.assetid: a49058d2-0276-43a7-9502-04adddf857b2
ms.openlocfilehash: 561a6e4ed1abf82fc1412123a4558a63e7176b2f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706485"
---
# <a name="names-of-namespaces"></a>命名空間的名稱

如同其他命名指導方針，命名命名空間的目標是為程式設計人員建立足夠的清楚清楚，讓程式設計人員使用架構立即知道命名空間的內容可能是什麼。 下列範本會指定命名空間的一般規則：

 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`

 範例如下：

 `Fabrikam.Math` `Litware.Security`

 ✔️使用公司名稱來做為命名空間名稱的前置詞，以防止來自不同公司的命名空間具有相同的名稱。

 ✔️在命名空間名稱的第二個層級使用穩定且與版本無關的產品名稱。

 ❌ 請勿使用組織階層作為命名空間階層中名稱的基礎，因為公司內的組名通常會很短。 組織相關技術群組的命名空間階層。

 ✔️請使用 PascalCasing，並以句點分隔命名空間元件 (例如 `Microsoft.Office.PowerPoint`) 。 如果您的品牌採用非傳統大小寫，您應該遵循品牌所定義的大小寫，即使它偏離正常的命名空間大小寫也一樣。

 ✔️在適當的情況下，請考慮使用複數命名空間名稱。

 例如，請使用 `System.Collections`，而不要使用 `System.Collection`。 但品牌名稱和縮寫是此規則的例外狀況。 例如，請使用 `System.IO`，而不要使用 `System.IOs`。

 ❌ 請勿在命名空間和該命名空間中的類型使用相同的名稱。

 例如，請勿使用做 `Debug` 為命名空間名稱，然後 `Debug` 在相同的命名空間中提供名為的類別。 數個編譯器需要這類類型才能完整限定。

### <a name="namespaces-and-type-name-conflicts"></a>命名空間和類型名稱衝突

 ❌ 請勿引進泛型型別名稱 `Element` ，例如、 `Node` 、 `Log` 和 `Message` 。

 在常見案例中，這麼做會導致類型名稱衝突的機率很高。 您應限定泛型型別名稱， (`FormElement` 、 `XmlNode` 、 `EventLog` `SoapMessage`) 。

 針對不同類別的命名空間，避免類型名稱衝突的特定指導方針。

- **應用程式模型命名空間**

     屬於單一應用程式模型的命名空間通常會一起使用，但幾乎不會與其他應用程式模型的命名空間搭配使用。 例如， <xref:System.Windows.Forms?displayProperty=nameWithType> 命名空間很少與 <xref:System.Web.UI?displayProperty=nameWithType> 命名空間一起使用。 以下是知名的應用程式模型命名空間群組清單：

     `System.Windows*` `System.Web.UI*`

     ❌ 請勿在單一應用程式模型內的命名空間中，將相同的名稱提供給類型。

     例如， `Page` <xref:System.Web.UI.Adapters?displayProperty=nameWithType> 由於 <xref:System.Web.UI?displayProperty=nameWithType> 命名空間已包含名為的型別，因此請勿將名為的型別加入命名空間 `Page` 。

- **基礎結構命名空間**

     此群組包含在開發一般應用程式期間很少匯入的命名空間。 例如， `.Design` 命名空間主要用於開發程式設計工具。 避免與這些命名空間中的類型發生衝突並不重要。

- **核心命名空間**

     核心命名空間包含所有 `System` 命名空間，但不包括應用程式模型和基礎結構命名空間的命名空間。 核心命名空間包括、、、 `System` `System.IO` 和等 `System.Xml` `System.Net` 。

     ❌ 請勿提供會與核心命名空間中的任何類型衝突的類型名稱。

     例如，絕對不要使用 `Stream` 做為類型名稱。 它會與 <xref:System.IO.Stream?displayProperty=nameWithType> 通常使用的型別相衝突。

- **技術命名空間群組**

     此類別包含具有相同前兩個命名空間節點的所有命名空間 `(<Company>.<Technology>*`) ，例如 `Microsoft.Build.Utilities` 和 `Microsoft.Build.Tasks` 。 很重要的是，屬於單一技術的型別不會彼此衝突。

     ❌ 請勿指派與單一技術內的其他類型相衝突的類型名稱。

     ❌ 請勿在技術命名空間中的類型和應用程式模型命名空間之間導入類型名稱衝突 (除非該技術不適合用于應用程式模型) 。

 *部分©2005、2009 Microsoft Corporation。保留的擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。

## <a name="see-also"></a>另請參閱

- [架構設計指導方針](index.md)
- [命名指導方針](naming-guidelines.md)
