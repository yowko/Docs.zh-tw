---
title: x:Class 指示詞
ms.date: 03/30/2017
f1_keywords:
- x:Class
- xClass
- Class
helpviewer_keywords:
- Class attribute in XAML [XAML Services]
- XAML [XAML Services], x:Class attribute
- x:Class attribute [XAML Services]
ms.assetid: bc4a3d8e-76e2-423e-a5d1-159a023e82ec
ms.openlocfilehash: 5f7b072e90e92070dd7fda2f0ad44814009268b9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59199449"
---
# <a name="xclass-directive"></a>x:Class 指示詞
設定要加入標記和程式碼後置的部分類別的 XAML 標記編譯。 在不同的程式碼檔案中定義的程式碼的部分類別[!INCLUDE[TLA#tla_cls](../../../includes/tlasharptla-cls-md.md)]語言，而標記的部分類別通常是由 XAML 編譯期間產生的程式碼。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```  
<object x:Class="namespace.classname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`namespace`|選擇性。 指定[!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)]命名空間，其中包含所識別的部分類別`classname`。 如果`namespace`指定，則句點 （.） 分隔`namespace`和`classname`。 請參閱＜備註＞。|  
|`classname`|必要項。 指定[!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)]連接載入的 XAML 和您程式碼後置的 XAML 的部分類別的名稱。|  
  
## <a name="dependencies"></a>相依性  
 `x:Class` 只有在 XAML 生產的根項目上指定。 `x:Class` 已有父代 XAML 生產環境中任何物件上無效。 如需詳細資訊，請參閱 < [ \[MS XAML\]一節 4.3.1.6](https://go.microsoft.com/fwlink/?LinkId=114525)。  
  
## <a name="remarks"></a>備註  
 `namespace`值可能包含相關的命名空間組織成名稱的階層，這是常用的技巧，在.NET Framework 程式設計中的其他點。 只有字串中的最後一個點`x:Class`值會被解譯為分隔`namespace`並`classname.`做為類別`x:Class`不可為巢狀的類別。 判斷點表示的意義，因為不允許巢狀的類別`x:Class`字串模稜兩可，如果允許巢狀的類別。  
  
 在現有的程式設計，使用模型`x:Class`，`x:Class`是選擇性的它是否有任何程式碼後置的 XAML 頁面完全有效。 不過，這項功能與互動，建置動作藉由使用 XAML 的架構。 `x:Class` XAML 指定內容的各種分類中的應用程式模型，以及中對應的建置動作的角色也會影響功能。 如果您的 XAML 宣告事件處理屬性值或定義類別所在的程式碼後置類別中的自訂項目具現化，您必須提供`x:Class`指示詞參考 (或[X:subclass](x-subclass-directive.md)) 至程式碼後置的適當類別。  
  
 值`x:Class`指示詞必須是字串，指定的類別，但不含任何組件資訊的完整格式的名稱 (相當於<xref:System.Type.FullName%2A?displayProperty=nameWithType>)。 對於簡單的應用程式，您可以省略 CLR 命名空間資訊，如果程式碼後置也結構化的方式 （在類別層級程式碼定義從開始）。  
  
 會產生編譯的應用程式，並牽涉到標記編譯的專案隨附的程式碼檔案內必須是頁面或應用程式定義的程式碼後置檔案。 您必須遵循的 CLR 類別名稱的規則。 如需詳細資訊，請參閱 < [Framework 設計方針](../../standard/design-guidelines/index.md)。 根據預設，程式碼後置類別必須是`public`; 不過，您可以在不同的存取層級中定義它，藉由使用[X:classmodifier 指示詞](x-classmodifier-directive.md)。  
  
 此解譯`x:Class`屬性只適用於以 CLR 為基礎的 XAML 實作中，特別是以.NET Framework XAML 服務。 其他 XAML 實作中，不以 CLR 為基礎，而且，不會使用.NET Framework XAML 服務可能會使用不同的解析度公式來連接 XAML 標記，並支援執行階段程式碼。 如需更多一般解譯的詳細資訊`x:Class`，請參閱 < [ \[MS XAML\]](https://go.microsoft.com/fwlink/?LinkId=114525)。  
  
 在特定層級的架構的意義`x:Class`.NET Framework XAML 服務中未定義。 這是因為.NET Framework XAML 服務不會指定哪一個 XAML 的標記和備份程式碼會連接程式撰寫模型。 其他用法`x:Class`指示詞可能會使用程式設計模型或應用程式模型來定義如何連接 XAML 標記和 CLR 為基礎的程式碼後置的特定架構實作。 每個架構可以有自己的建置動作可讓部分必須包含在建置環境的特定元件或行為。 在架構中，也可能有所不同用於程式碼後置的特定 CLR 語言的建置動作。  
  
## <a name="xclass-in-the-wpf-programming-model"></a>WPF 程式設計模型中的 x： 類別  
 WPF 應用程式和 WPF 應用程式模型中，`x:Class`可以宣告為屬性是 XAML 檔案的根目錄，並在編譯任何項目 (其中包含 XAML 在 WPF 應用程式專案中，使用`Page`建置動作)，或如 <c4 > <xref:System.Windows.Application> 編譯的 WPF 應用程式的應用程式定義中的根。 宣告`x:Class`頁面根或應用程式根目錄以外的項目或在未編譯 WPF XAML 檔案，會造成在編譯時期錯誤[!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)]和[!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)]WPF XAML 編譯器。 如需其他層面`x:Class`WPF 中的處理，請參閱[程式碼後置和 XAML 在 WPF 中的](../wpf/advanced/code-behind-and-xaml-in-wpf.md)。  
  
## <a name="xclass-for-windows-workflow-foundation"></a>X:class for Windows Workflow Foundation  
 對於 Windows Workflow Foundation，`x:Class`名稱全部以 XAML，撰寫之自訂活動的類別或命名活動設計工具與程式碼後置的 XAML 頁面的部分類別。  
  
## <a name="silverlight-usage-notes"></a>Silverlight 使用方式附註  
 `x:Class` silverlight 會另外記載。 如需詳細資訊，請參閱[XAML 命名空間 （x:）語言功能 (Silverlight)](https://go.microsoft.com/fwlink/?LinkId=199081)。  
  
## <a name="see-also"></a>另請參閱

- [x:Subclass 指示詞](x-subclass-directive.md)
- [WPF 的 XAML 和自訂類別](../wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [x:ClassModifier 指示詞](x-classmodifier-directive.md)
- [從 WPF 移轉至 System.Xaml 的類型](types-migrated-from-wpf-to-system-xaml.md)
