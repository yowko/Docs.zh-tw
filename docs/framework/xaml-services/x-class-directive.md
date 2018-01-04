---
title: "x:Class 指示詞"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- x:Class
- xClass
- Class
helpviewer_keywords:
- Class attribute in XAML [XAML Services]
- XAML [XAML Services], x:Class attribute
- x:Class attribute [XAML Services]
ms.assetid: bc4a3d8e-76e2-423e-a5d1-159a023e82ec
caps.latest.revision: "27"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b894a56caa3644bae140e7ec37cf5b55ab093a59
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="xclass-directive"></a>x:Class 指示詞
設定要加入標記和程式碼後置的部分類別的 XAML 標記編譯。 在不同的程式碼檔案中定義的程式碼的部分類別[!INCLUDE[TLA#tla_cls](../../../includes/tlasharptla-cls-md.md)]語言，而標記的部分類別通常在 XAML 編譯期間產生的程式碼來建立。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```  
<object x:Class="namespace.classname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`namespace`|選擇性。 指定[!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)]包含所識別的部分類別的命名空間`classname`。 如果`namespace`指定，則句點 （.） 分隔`namespace`和`classname`。 請參閱＜備註＞。|  
|`classname`|必要。 指定[!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)]的部分類別載入的 XAML 和程式碼後置該 XAML 的連接名稱。|  
  
## <a name="dependencies"></a>相依性  
 `x:Class`只有在 XAML 生產的根項目上指定。 `x:Class`具有父代在 XAML 生產環境中的任何物件上無效。 如需詳細資訊，請參閱[ \[MS-XAML\]區段 4.3.1.6](http://go.microsoft.com/fwlink/?LinkId=114525)。  
  
## <a name="remarks"></a>備註  
 `namespace`值可能包含相關的命名空間組織成名稱階層，這是在.NET Framework 程式設計中的常用技術的其他點。 只有在字串中的最後一個點`x:Class`值會被解譯為分隔`namespace`和`classname.`類別用來當做`x:Class`不可為巢狀的類別。 不允許巢狀的類別，因為判斷點的意義`x:Class`字串模稜兩可，如果允許巢狀的類別。  
  
 以現有的程式設計模型使用`x:Class`，`x:Class`是選擇性的它是否有 XAML 頁面，其中包含任何程式碼後置完全有效。 不過，這項功能互動的建置動作由使用 XAML 的架構實作。 `x:Class`功能也會受到角色的 XAML 指定內容的各種分類應用程式模型中，並在對應的建置動作。 如果您的 XAML 宣告事件處理屬性值或定義類別所在的程式碼後置類別中的自訂項目會具現化，您必須提供`x:Class`指示詞參考 (或[X:subclass](../../../docs/framework/xaml-services/x-subclass-directive.md)) 至程式碼後置的適當類別。  
  
 值`x:Class`指示詞必須是指定的類別，但不含任何組件資訊的完整限定的名稱的字串 (相當於<xref:System.Type.FullName%2A?displayProperty=nameWithType>)。 簡單的應用程式，您可以省略 CLR 命名空間資訊，如果程式碼後置也結構化的方式 （在類別層級程式碼定義開始）。  
  
 在頁面或應用程式定義的程式碼後置檔案必須是專案的會產生編譯的應用程式牽涉到標記編譯中包含的程式碼檔案內。 您必須遵循的 CLR 類別名稱的規則。 如需詳細資訊，請參閱[Framework 設計方針](../../../docs/standard/design-guidelines/index.md)。 根據預設，程式碼後置類別必須是`public`; 不過，定義在不同的存取層級使用[X:classmodifier 指示詞](../../../docs/framework/xaml-services/x-classmodifier-directive.md)。  
  
 此解譯`x:Class`屬性只適用於以 CLR 為基礎的 XAML 實作中，特別是.NET Framework XAML 服務。 其他 XAML 實作中，不以 CLR 為基礎，而且，不會使用.NET Framework XAML 服務可能會使用不同的解析度公式來連接 XAML 標記，並支援執行階段程式碼。 如需有關的一般解譯`x:Class`，請參閱[ \[MS-XAML\]](http://go.microsoft.com/fwlink/?LinkId=114525)。  
  
 在特定層級的架構的意義`x:Class`未定義在.NET Framework XAML 服務中。 這是因為.NET Framework XAML 服務未指定的 xaml 標記和支援的程式碼已連線的程式設計模型。 其他用法`x:Class`指示詞可能會實作所使用的程式設計模型或應用程式模型來定義如何連接 XAML 標記和 clr 程式碼後置的特定架構。 每個架構可以有它自己建置動作以啟用部分必須包含在建置環境的特定元件或行為。 在架構中，建置動作也會有所不同用於程式碼後置特定 CLR 語言。  
  
## <a name="xclass-in-the-wpf-programming-model"></a>WPF 程式設計模型中的 x： 類別  
 WPF 應用程式和 WPF 應用程式模型中，`x:Class`可以宣告為屬性，是為 XAML 檔案的根，以及編譯任何項目 (其中包含 XAML WPF 應用程式專案中，使用`Page`建置動作)，或 <c4 > <xref:System.Windows.Application> 應用程式定義中的已編譯的 WPF 應用程式的根。 宣告`x:Class`頁面根或應用程式根目錄以外的項目上或在未編譯 WPF XAML 檔案中，會導致編譯時間錯誤下的[!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)]和[!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)]WPF XAML 編譯器。 如需有關其他方面的資訊`x:Class`處理在 WPF 中，請參閱[程式碼後置中和 XAML WPF](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)。  
  
## <a name="xclass-for-windows-workflow-foundation"></a>X:class for Windows Workflow Foundation  
 針對 Windows Workflow Foundation，`x:Class`名稱完全以 XAML 撰寫之自訂活動的類別或 XAML 頁面的部分類別名稱與程式碼後置活動設計工具。  
  
## <a name="silverlight-usage-notes"></a>Silverlight 的使用方式附註  
 `x:Class`silverlight 被說明文件。 如需詳細資訊，請參閱[XAML 命名空間 （x:）語言功能 (Silverlight)](http://go.microsoft.com/fwlink/?LinkId=199081)。  
  
## <a name="see-also"></a>請參閱  
 [x:Subclass 指示詞](../../../docs/framework/xaml-services/x-subclass-directive.md)  
 [WPF 的 XAML 和自訂類別](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)  
 [x:ClassModifier 指示詞](../../../docs/framework/xaml-services/x-classmodifier-directive.md)  
 [從 WPF 移轉至 System.Xaml 的類型](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)
