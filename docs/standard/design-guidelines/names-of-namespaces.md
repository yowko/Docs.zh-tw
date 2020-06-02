---
title: 命名空間的名稱
description: 使用這些指導方針來命名命名空間，做為設計程式庫以擴充和與 .NET 程式庫互動的指導方針。
ms.date: 10/22/2008
helpviewer_keywords:
- names [.NET Framework], conflicts
- names [.NET Framework], namespaces
- type names, conflicts
- namespaces [.NET Framework], names
- names [.NET Framework], type names
ms.assetid: a49058d2-0276-43a7-9502-04adddf857b2
ms.openlocfilehash: e435e0281165b4a9f12bbccbeb10401b57375dcb
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290197"
---
# <a name="names-of-namespaces"></a>命名空間的名稱
就像其他命名指導方針一樣，命名命名空間的目標是要讓程式設計人員能夠使用架構來立即知道命名空間的內容有何可能。 下列範本會指定命名空間的一般規則：

 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`

 範例如下：

 `Fabrikam.Math` `Litware.Security`

 ✔️會在命名空間名稱前面加上公司名稱，以防止來自不同公司的命名空間具有相同的名稱。

 ✔️確實會在命名空間名稱的第二個層級上使用穩定、版本無關的產品名稱。

 ❌請勿使用組織階層做為命名空間階層中的名稱基礎，因為公司內的組名通常會短期。 依據相關技術群組來組織命名空間的階層。

 ✔️確實使用 PascalCasing，並以句號分隔命名空間元件（例如 `Microsoft.Office.PowerPoint` ）。 如果您的品牌採用生命的大小寫，則應該遵循您的品牌所定義的大小寫，即使它與一般的命名空間大小寫不一樣。

 ✔️在適當的情況下，請考慮使用複數命名空間名稱。

 例如，請使用 `System.Collections`，而不要使用 `System.Collection`。 不過，品牌名稱和縮寫是此規則的例外狀況。 例如，請使用 `System.IO`，而不要使用 `System.IOs`。

 ❌命名空間和該命名空間中的類型，請勿使用相同的名稱。

 例如，請勿使用做 `Debug` 為命名空間名稱，然後 `Debug` 在相同的命名空間中提供名為的類別。 數個編譯器要求這類類型必須是完整的。

### <a name="namespaces-and-type-name-conflicts"></a>命名空間和類型名稱衝突
 ❌請勿引進泛型型別名稱 `Element` ，例如、 `Node` 、 `Log` 和 `Message` 。

 這麼做的機率很高，會導致常見案例中的型別名稱衝突。 您應該限定泛型型別名稱（ `FormElement` 、 `XmlNode` 、 `EventLog` 、 `SoapMessage` ）。

 有一些特定的指導方針可避免不同分類命名空間的類型名稱衝突。

- **應用程式模型命名空間**

     屬於單一應用程式模型的命名空間通常會一起使用，但它們幾乎不會與其他應用程式模型的命名空間搭配使用。 例如， <xref:System.Windows.Forms?displayProperty=nameWithType> 命名空間非常少搭配 <xref:System.Web.UI?displayProperty=nameWithType> 命名空間使用。 以下是知名的應用程式模型命名空間群組清單：

     `System.Windows*` `System.Web.UI*`

     ❌請不要在單一應用程式模型中，為命名空間中的類型提供相同的名稱。

     例如，請勿將名為的型別加入 `Page` <xref:System.Web.UI.Adapters?displayProperty=nameWithType> 命名空間，因為 <xref:System.Web.UI?displayProperty=nameWithType> 命名空間已經包含名為的型別 `Page` 。

- **基礎結構命名空間**

     此群組包含在開發一般應用程式期間很少匯入的命名空間。 例如， `.Design` 在開發程式設計工具時，主要會使用命名空間。 避免與這些命名空間中的類型發生衝突並不重要。

- **核心命名空間**

     核心命名空間包含所有 `System` 命名空間，但不包括應用程式模型的命名空間和基礎結構命名空間。 核心命名空間包括其他、、 `System` 、 `System.IO` `System.Xml` 和 `System.Net` 。

     ❌請不要提供與核心命名空間中任何類型衝突的類型名稱。

     例如，絕對不要使用 `Stream` 做為型別名稱。 它會與 <xref:System.IO.Stream?displayProperty=nameWithType> 非常常用的類型相衝突。

- **技術命名空間群組**

     此類別包括具有相同前兩個命名空間節點的所有命名空間 `(<Company>.<Technology>*` ，例如 `Microsoft.Build.Utilities` 和 `Microsoft.Build.Tasks` 。 屬於單一技術的型別不會互相衝突，這點很重要。

     ❌請勿指派與單一技術內其他類型衝突的類型名稱。

     ❌請勿在技術命名空間中的類型與應用程式模型命名空間之間導入類型名稱衝突（除非此技術不適合用于應用程式模型）。

 *部分©2005、2009 Microsoft Corporation。已保留擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。**

## <a name="see-also"></a>另請參閱

- [架構設計方針](index.md)
- [命名方針](naming-guidelines.md)
