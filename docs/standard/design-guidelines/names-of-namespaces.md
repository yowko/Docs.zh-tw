---
title: "命名空間的名稱"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- names [.NET Framework], conflicts
- names [.NET Framework], namespaces
- type names, conflicts
- namespaces [.NET Framework], names
- names [.NET Framework], type names
ms.assetid: a49058d2-0276-43a7-9502-04adddf857b2
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: bc298ad41884bfda84771a729990ebb4e6f776b7
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="names-of-namespaces"></a>命名空間的名稱
做為與其他命名指導方針，命名的命名空間時的目標建立足夠的清楚起見使用 framework 立即知道命名空間的內容可能是程式設計人員。 下列範本會指定為命名空間進行的一般規則：  
  
 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`  
  
 範例如下：  
  
 `Fabrikam.Math`  
 `Litware.Security`  
  
 **✓ 不要**命名空間名稱前面加上的公司名稱，以避免不同公司的具有相同名稱的命名空間。  
  
 **✓ 不要**第二個層級的命名空間名稱使用的穩定、 版本無關的產品名稱。  
  
 **X 不**使用組織階層做為基礎，名稱在命名空間階層中，因為公司內的群組名稱大多數為暫時性。 組織相關技術的群組周圍的命名空間階層的架構。  
  
 **✓ 不要**期間，使用 PascalCasing，與不同的命名空間的元件 (例如`Microsoft.Office.PowerPoint`)。 如果您的品牌使用社會大小寫，您應該遵循您的品牌所定義的大小寫，即使偏離標準的命名空間的大小寫。  
  
 **✓ 考慮**適時使用複數命名空間名稱。  
  
 例如，使用`System.Collections`而不是`System.Collection`。 品牌名稱與縮寫，不過是這項規則的例外狀況。 例如，使用`System.IO`而不是`System.IOs`。  
  
 **X 不**該命名空間中使用相同名稱的命名空間和類型。  
  
 例如，請勿使用`Debug`為命名空間名稱，然後也提供類別，名為`Debug`相同的命名空間中。 有好幾種編譯器需要這類必須是完整的類型。  
  
### <a name="namespaces-and-type-name-conflicts"></a>命名空間和類型名稱衝突  
 **X 不**引入泛型型別名稱，例如`Element`， `Node`， `Log`，和`Message`。  
  
 沒有這樣做會導致輸入名稱衝突在一般案例的機率相當高。 您應該限定的泛型型別名稱 (`FormElement`， `XmlNode`， `EventLog`， `SoapMessage`)。  
  
 有避免不同類別的命名空間的型別名稱衝突的特定指導方針。  
  
-   **應用程式模型命名空間**  
  
     屬於單一應用程式模型的命名空間通常會同時使用，但是幾乎永遠不會使用與其他應用程式模型的命名空間。 例如，<xref:System.Windows.Forms?displayProperty=nameWithType>搭配很少使用命名空間<xref:System.Web.UI?displayProperty=nameWithType>命名空間。 以下是已知的應用程式模型命名空間群組的清單：  
  
     `System.Windows*`   
     `System.Web.UI*`  
  
     **X 不**讓具有相同名稱的單一應用程式模型中的命名空間中的型別。  
  
     例如，不會加入名為型別`Page`至<xref:System.Web.UI.Adapters?displayProperty=nameWithType>命名空間，因為<xref:System.Web.UI?displayProperty=nameWithType>命名空間已經包含名為型別`Page`。  
  
-   **基礎結構的命名空間**  
  
     此群組包含一般的應用程式開發期間很少匯入的命名空間。 例如，`.Design`開發程式設計工具時，主要會使用命名空間。 避免衝突，這些命名空間中的類型並不重要。  
  
-   **核心命名空間**  
  
     核心命名空間包含所有`System`命名空間，但排除的應用程式模型的命名空間和基礎結構命名空間。 和其他項目，核心命名空間包含`System`， `System.IO`， `System.Xml`，和`System.Net`。  
  
     **X 不**授與類型的核心命名空間中的任何類型，會發生衝突的名稱。  
  
     例如，絕對不要使用`Stream`做為型別名稱。 它會和衝突<xref:System.IO.Stream?displayProperty=nameWithType>的非常常用的型別。  
  
-   **技術命名空間群組**  
  
     此類別包含所有具有相同的前兩個命名空間節點的命名空間`(<Company>.<Technology>*`)，例如`Microsoft.Build.Utilities`和`Microsoft.Build.Tasks`。 請務必確認屬於單一技術類型未與彼此衝突。  
  
     **X 不**指派內單一技術的其他類型的型別名稱，以免造成衝突。  
  
     **X 不**（除非該技術不是用於與應用程式模型） 導入技術的命名空間中的型別和應用程式模型命名空間之間的類型名稱衝突。  
  
 *部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*  
  
 *皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*  
  
## <a name="see-also"></a>請參閱  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)  
 [命名方針](../../../docs/standard/design-guidelines/naming-guidelines.md)
