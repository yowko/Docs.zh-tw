---
title: "命名空間的名稱 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "名稱 [.NET Framework] 衝突"
  - "名稱 [.NET Framework] 命名空間"
  - "型別名稱衝突"
  - "命名空間 [.NET Framework] 名稱"
  - "名稱 [.NET Framework] 的型別名稱"
ms.assetid: a49058d2-0276-43a7-9502-04adddf857b2
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# 命名空間的名稱
做為其他命名指導方針，命名的命名空間時的目標建立足夠的清晰度對程式設計師能夠立即知道命名空間的內容可能是使用架構。 下列範本指定為命名空間進行的一般規則︰  
  
 `<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]`  
  
 以下是範例︰  
  
 `Fabrikam.Math`   
 `Litware.Security`  
  
 **✓ 執行** 命名空間名稱前面加上公司名稱，以避免不同公司的具有相同名稱的命名空間。  
  
 **✓ 執行** 命名空間名稱的第二個層級使用穩定且與版本無關的產品名稱。  
  
 **X 不** 作為組織階層基準名稱在命名空間階層中，因為公司內的群組名稱通常是很短暫。 組織相關技術的群組周圍的命名空間階層的架構。  
  
 **✓ 執行** 期間，使用 PascalCasing，與不同的命名空間的元件 \(例如 `Microsoft.Office.PowerPoint`\)。 如果您的品牌使用社會大小寫，則應遵循您的品牌所定義的大小寫，即使偏離標準的命名空間的大小寫。  
  
 **✓ 考慮** 適當使用複數命名空間名稱。  
  
 例如，使用 `System.Collections` 而不是 `System.Collection`。 品牌名稱與縮寫，不過是這項規則的例外狀況。 例如，使用 `System.IO` 而不是 `System.IOs`。  
  
 **X 不** 該命名空間中使用相同名稱的命名空間和型別。  
  
 例如，請勿使用 `Debug` 為命名空間名稱，然後也提供類別，名為 `Debug` 相同的命名空間中。 有好幾種編譯器需要完整的這種型別。  
  
### 命名空間和型別名稱衝突  
 **X 不** 導入泛型型別名稱時，例如 `Element`, ，`Node`, ，`Log`, ，和 `Message`。  
  
 沒有這樣做會導致輸入名稱衝突在一般案例的機率相當高。 您應該限定的泛型型別名稱 \(`FormElement`, ，`XmlNode`, ，`EventLog`, ，`SoapMessage`\)。  
  
 有特定的指導方針，可以避免不同類別的命名空間的型別名稱衝突。  
  
-   **應用程式模型命名空間**  
  
     屬於單一應用程式模型的命名空間會經常一起使用，但幾乎無法搭配其他應用程式模型的命名空間。 例如， <xref:System.Windows.Forms?displayProperty=fullName> 搭配很少使用命名空間 <xref:System.Web.UI?displayProperty=fullName> 的命名空間。 下列是已知的應用程式模型命名空間群組的清單︰  
  
     `System.Windows*`   
     `System.Web.UI*`  
  
     **X 不** 單一應用程式模型中的命名空間中的型別提供相同的名稱。  
  
     例如，不會加入名為型別 `Page` 到 <xref:System.Web.UI.Adapters?displayProperty=fullName> 命名空間，因為 <xref:System.Web.UI?displayProperty=fullName> 命名空間已經包含名為型別 `Page`。  
  
-   **基礎結構的命名空間**  
  
     此群組包含常用的應用程式開發期間很少匯入的命名空間。 例如， `.Design` 程式設計的開發工具時，主要用於命名空間。 這些命名空間中型別的避免衝突並不重要。  
  
-   **核心命名空間**  
  
     核心命名空間包含所有 `System` 命名空間，不包括應用程式模型的命名空間和基礎結構的命名空間。 和其他核心命名空間包含 `System`, ，`System.IO`, ，`System.Xml`, ，和 `System.Net`。  
  
     **X 不** 提供類型的核心命名空間中的任何類型，會發生衝突的名稱。  
  
     例如，絕對不要使用 `Stream` 做為型別名稱。 它會和衝突 <xref:System.IO.Stream?displayProperty=fullName>, 、 相當常用的型別。  
  
-   **技術命名空間群組**  
  
     此類別包含具有相同的前兩個命名空間節點的所有命名空間 `(<Company>.<Technology>*`\)，例如 `Microsoft.Build.Utilities` 和 `Microsoft.Build.Tasks`。 請務必彼此並不衝突類型屬於單一技術。  
  
     **X 不** 指派單一技術內其他型別的型別名稱，以免造成衝突。  
  
     **X 不** （除非技術並不打算使用與應用程式模型） 導入技術命名空間中的型別和應用程式模型命名空間之間的型別名稱衝突。  
  
 *部分 © 2005年、 2009 Microsoft Corporation。 著作權所有，並保留一切權利。*  
  
 *皮耳森教育，從 Inc.的權限所印製 [Framework 設計方針︰ 慣例、 慣用句和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina 並 Brad Abrams，2008 年 10 月 22 日由 Addison\-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*  
  
## 請參閱  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)   
 [命名方針](../../../docs/standard/design-guidelines/naming-guidelines.md)