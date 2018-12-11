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
author: KrzysztofCwalina
ms.openlocfilehash: 64efdc46583a0931df9f57c32424ca4233bf2b82
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53143437"
---
# <a name="names-of-namespaces"></a>命名空間的名稱
做為其他命名指導方針，命名的命名空間時的目標建立足夠的清晰度給程式設計人員立即知道命名空間的內容可能是使用架構。 下列範本指定為命名空間進行的一般規則：  
  
 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`  
  
 以下是範例：  
  
 `Fabrikam.Math`  
 `Litware.Security`  
  
 **✓ DO** 命名空間名稱前面加上的公司名稱，以避免不同公司的具有相同名稱的命名空間。  
  
 **✓ DO** 第二個層級的命名空間名稱使用的穩定、 版本無關的產品名稱。  
  
 **X DO NOT** 使用組織階層做為基礎，名稱在命名空間階層中，因為公司內的群組名稱大多數為暫時性。 組織相關技術的群組周圍的命名空間階層的架構。  
  
 **✓ DO** 期間，使用 PascalCasing，與不同的命名空間的元件 (例如 `Microsoft.Office.PowerPoint`)。 如果您的品牌採用非傳統任務為大小寫，則您應該遵循您的品牌所定義的大小寫，即使它是衍生自標準的命名空間的大小寫。  
  
 **✓ CONSIDER** 適時使用複數命名空間名稱。  
  
 例如，使用`System.Collections`而不是`System.Collection`。 品牌名稱與縮寫不過是這項規則的例外狀況。 例如，使用`System.IO`而不是`System.IOs`。  
  
 **X DO NOT** 該命名空間中使用相同名稱的命名空間和類型。  
  
 例如，請勿使用`Debug`的命名空間名稱，並也提供類別，名為`Debug`相同的命名空間中。 有好幾種編譯器需要這類的類型是完整名稱。  
  
### <a name="namespaces-and-type-name-conflicts"></a>命名空間和類型名稱衝突  
 **X DO NOT** 引入泛型型別名稱，例如 `Element`， `Node`， `Log`，和 `Message`。  
  
 沒有極高的可能這樣做會導致輸入名稱衝突在一般案例。 您應該符合資格的泛型型別名稱 (`FormElement`， `XmlNode`， `EventLog`， `SoapMessage`)。  
  
 有避免不同類別的命名空間的型別名稱衝突的特定方針。  
  
-   **應用程式模型命名空間**  
  
     屬於單一應用程式模型的命名空間會經常一起使用，但幾乎不會搭配其他應用程式模型的命名空間。 例如，<xref:System.Windows.Forms?displayProperty=nameWithType>命名空間很少可搭配使用<xref:System.Web.UI?displayProperty=nameWithType>命名空間。 以下是已知的應用程式模型命名空間群組的清單：  
  
     `System.Windows*`   
     `System.Web.UI*`  
  
     **X DO NOT** 讓具有相同名稱的單一應用程式模型中的命名空間中的型別。  
  
     比方說，不會將名為的型別`Page`要<xref:System.Web.UI.Adapters?displayProperty=nameWithType>命名空間，因為<xref:System.Web.UI?displayProperty=nameWithType>命名空間已經包含名為的型別`Page`。  
  
-   **基礎結構命名空間**  
  
     此群組包含很少的常見的應用程式開發期間匯入的命名空間。 比方說，`.Design`命名空間主要是用來開發程式工具。 避免衝突，這些命名空間中的類型並不重要。  
  
-   **核心命名空間**  
  
     核心命名空間包含所有`System`命名空間，但不包括應用程式模型的命名空間和基礎結構命名空間。 包含核心命名空間，其中， `System`， `System.IO`， `System.Xml`，和`System.Net`。  
  
     **X DO NOT** 授與類型的核心命名空間中的任何類型，會發生衝突的名稱。  
  
     比方說，永遠不會使用`Stream`做為型別名稱。 它會和衝突<xref:System.IO.Stream?displayProperty=nameWithType>、 相當常用的型別。  
  
-   **技術命名空間群組**  
  
     這個分類包括具有相同的前兩個命名空間節點的所有命名空間`(<Company>.<Technology>*`)，例如`Microsoft.Build.Utilities`和`Microsoft.Build.Tasks`。 很重要，彼此不衝突類型屬於單一技術。  
  
     **X DO NOT** 指派內單一技術的其他類型的型別名稱，以免造成衝突。  
  
     **X DO NOT** （除非該技術不是用於與應用程式模型） 導入技術的命名空間中的型別和應用程式模型命名空間之間的類型名稱衝突。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *皮耳森教育，inc.的權限所印製[Framework 設計方針：慣例、 慣用句和可重複使用的.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 和 Brad Abrams，2008 年 10 月 22 日由 Addison-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## <a name="see-also"></a>另請參閱

- [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)  
- [命名方針](../../../docs/standard/design-guidelines/naming-guidelines.md)
