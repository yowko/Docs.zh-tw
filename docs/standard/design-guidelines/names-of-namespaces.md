---
title: 命名空間的名稱
ms.date: 10/22/2008
helpviewer_keywords:
- names [.NET Framework], conflicts
- names [.NET Framework], namespaces
- type names, conflicts
- namespaces [.NET Framework], names
- names [.NET Framework], type names
ms.assetid: a49058d2-0276-43a7-9502-04adddf857b2
ms.openlocfilehash: 52fee0dfaff284c2c1a6afcb8aa7530c28a60d65
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744147"
---
# <a name="names-of-namespaces"></a>命名空間的名稱
就像其他命名指導方針一樣，命名命名空間的目標是要讓程式設計人員能夠使用架構來立即知道命名空間的內容有何可能。 下列範本會指定命名空間的一般規則：

 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`

 範例如下：

 `Fabrikam.Math` `Litware.Security`

 ✔️會在命名空間名稱前面加上公司名稱，以防止來自不同公司的命名空間具有相同的名稱。

 ✔️確實會在命名空間名稱的第二個層級上使用穩定、版本無關的產品名稱。

 ❌ 不使用組織階層做為命名空間階層中的名稱基礎，因為公司內的組名通常會短期。 依據相關技術群組來組織命名空間的階層。

 ✔️確實使用 PascalCasing，並將命名空間元件與句號（例如 `Microsoft.Office.PowerPoint`）分開。 如果您的品牌採用生命的大小寫，則應該遵循您的品牌所定義的大小寫，即使它與一般的命名空間大小寫不一樣。

 ✔️在適當的情況下，請考慮使用複數命名空間名稱。

 例如，使用 `System.Collections` 而不是 `System.Collection`。 不過，品牌名稱和縮寫是此規則的例外狀況。 例如，使用 `System.IO` 而不是 `System.IOs`。

 ❌ 不會針對命名空間和該命名空間中的類型使用相同的名稱。

 例如，請勿使用 `Debug` 做為命名空間名稱，然後在相同的命名空間中提供名為 `Debug` 的類別。 數個編譯器要求這類類型必須是完整的。

### <a name="namespaces-and-type-name-conflicts"></a>命名空間和類型名稱衝突
 ❌ 不會引進泛型型別名稱，例如 `Element`、`Node`、`Log`和 `Message`。

 這麼做的機率很高，會導致常見案例中的型別名稱衝突。 您應該限定泛型型別名稱（`FormElement`、`XmlNode`、`EventLog`、`SoapMessage`）。

 有一些特定的指導方針可避免不同分類命名空間的類型名稱衝突。

- **應用程式模型命名空間**

     屬於單一應用程式模型的命名空間通常會一起使用，但它們幾乎不會與其他應用程式模型的命名空間搭配使用。 例如，<xref:System.Windows.Forms?displayProperty=nameWithType> 命名空間很少與 <xref:System.Web.UI?displayProperty=nameWithType> 命名空間搭配使用。 以下是知名的應用程式模型命名空間群組清單：

     `System.Windows*` `System.Web.UI*`

     ❌ 不會在單一應用程式模型中，為命名空間中的類型提供相同的名稱。

     例如，請勿將名為 `Page` 的類型加入 <xref:System.Web.UI.Adapters?displayProperty=nameWithType> 命名空間，因為 <xref:System.Web.UI?displayProperty=nameWithType> 命名空間已經包含名為 `Page`的類型。

- **基礎結構命名空間**

     此群組包含在開發一般應用程式期間很少匯入的命名空間。 例如，在開發程式設計工具時，主要會使用 `.Design` 命名空間。 避免與這些命名空間中的類型發生衝突並不重要。

- **核心命名空間**

     核心命名空間包含所有 `System` 的命名空間，但不包括應用程式模型的命名空間和基礎結構命名空間。 核心命名空間包括其他 `System`、`System.IO`、`System.Xml`和 `System.Net`。

     ❌ 不提供會與核心命名空間中任何類型衝突的類型名稱。

     例如，絕對不要使用 `Stream` 做為類型名稱。 它會與 <xref:System.IO.Stream?displayProperty=nameWithType>（非常常用的類型）相衝突。

- **技術命名空間群組**

     此類別包含前兩個命名空間節點 `(<Company>.<Technology>*`）的所有命名空間，例如 `Microsoft.Build.Utilities` 和 `Microsoft.Build.Tasks`。 屬於單一技術的型別不會互相衝突，這點很重要。

     ❌ 不會指派與單一技術內其他類型衝突的類型名稱。

     ❌ 不會在技術命名空間中的類型與應用程式模型命名空間之間導入類型名稱衝突（除非該技術不適合用于應用程式模型）。

 *部分©2005、2009 Microsoft Corporation。已保留擁有權限。*

 獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。

## <a name="see-also"></a>請參閱

- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)
- [命名方針](../../../docs/standard/design-guidelines/naming-guidelines.md)
