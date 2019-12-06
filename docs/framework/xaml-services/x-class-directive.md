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
ms.openlocfilehash: d6baa6d8eb3a6d3520fb1549e2182f27ca52c36a
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837242"
---
# <a name="xclass-directive"></a>x:Class 指示詞
設定 XAML 標記編譯以聯結標記和程式碼後置之間的部分類別。 程式碼部分類別是以 Common Language Specification （CLS）語言在不同的程式碼檔案中定義，而標記部分類別通常是在 XAML 編譯期間由程式碼產生所建立。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```xaml  
<object x:Class="namespace.classname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`namespace`|選擇項。 指定 CLR 命名空間，其中包含 `classname`所識別的部分類別。 如果指定 `namespace`，則句點（.）會分隔 `namespace` 和 `classname`。 請參閱＜備註＞。|  
|`classname`|必要項。 指定部分類別的 CLR 名稱，此元件會連接已載入的 XAML 和該 XAML 的程式碼後置。|  
  
## <a name="dependencies"></a>相依性  
 `x:Class` 只能在 XAML 生產的根項目上指定。 `x:Class` 在 XAML 生產中具有父系的任何物件上無效。 如需詳細資訊，請參閱[\[MS-XAML\] 區段 4.3.1.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))。  
  
## <a name="remarks"></a>備註  
 `namespace` 值可能包含用來將相關命名空間組織成名稱階層的其他點，這是 .NET Framework 程式設計的常見技巧。 只有 `x:Class` 值字串中的最後一個點會被解讀為分隔 `namespace`，而 `classname.` 做為 `x:Class` 的類別則不能是嵌套類別。 不允許使用嵌套的類別，因為如果允許嵌套的類別，判斷 `x:Class` 字串的點意義是不明確的。  
  
 在使用 `x:Class`的現有程式設計模型中，`x:Class` 是選擇性的，因為具有不具有程式碼後置的 XAML 頁面是完全有效的。 不過，這項功能會與使用 XAML 的架構所執行的組建動作互動。 `x:Class` 功能也會受到 XAML 指定內容的各種分類在應用程式模型和對應的組建動作中的角色所影響。 如果您的 XAML 宣告事件處理屬性值或具現化自訂專案，其中定義的類別位於程式碼後置類別中，您必須提供 `x:Class` 指示詞參考（或[x:Subclass](x-subclass-directive.md)）給程式碼後置的適當類別。  
  
 `x:Class` 指示詞的值必須是指定類別之完整名稱的字串，但不含任何元件資訊（相當於 <xref:System.Type.FullName%2A?displayProperty=nameWithType>）。 對於簡單的應用程式，如果程式碼後置也以該方式結構化，您就可以省略 CLR 命名空間資訊（在類別層級開始程式碼定義）。  
  
 頁面或應用程式定義的程式碼後置檔案必須位於程式碼檔案中，此檔案包含在產生已編譯應用程式的專案中，並牽涉到標記編譯。 您必須遵循 CLR 類別的名稱規則。 如需詳細資訊，請參閱[架構設計方針](../../standard/design-guidelines/index.md)。 根據預設，程式碼後置類別必須 `public`。不過，您可以使用[x:ClassModifier](x-classmodifier-directive.md)指示詞，在不同的存取層級定義它。  
  
 這項 `x:Class` 屬性的解讀僅適用于以 CLR 為基礎的 XAML 執行，特別是 .NET Framework XAML 服務。 其他不是以 CLR 為基礎且未使用 .NET Framework XAML 服務的 XAML 執行，可能會使用不同的解析公式來連接 XAML 標記和支援執行時間程式碼。 如需更多 `x:Class`一般解讀的詳細資訊，請參閱[\[MS-XAML\]](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))。  
  
 在特定層級的架構中，`x:Class` 的意義在 .NET Framework XAML 服務中未定義。 這是因為 .NET Framework XAML 服務並不會指定 XAML 標記和支援的程式碼所連接的程式設計模型。 `x:Class` 指示詞的其他用法可能會由使用程式設計模型或應用程式模型的特定架構來執行，以定義如何連接 XAML 標記和以 CLR 為基礎的程式碼後置。 每個架構都可以有自己的組建動作，以啟用某些必須包含在組建環境中的行為或特定元件。 在架構中，組建動作也會根據程式碼後置所使用的特定 CLR 語言而有所不同。  
  
## <a name="xclass-in-the-wpf-programming-model"></a>WPF 程式設計模型中的 X：Class  
 在 WPF 應用程式和 WPF 應用程式模型中，`x:Class` 可以宣告為 XAML 檔案根目錄的任何元素的屬性（其中 XAML 包含在具有 `Page` 組建動作的 WPF 應用程式專案中），或針對已編譯 WPF 應用程式之應用程式定義中的 <xref:System.Windows.Application> 根目錄。 在頁面根目錄或應用程式根目錄以外的專案上宣告 `x:Class`，或是在未編譯的 WPF XAML 檔案上，會導致 .NET Framework 3.0 和 .NET Framework 3.5 WPF XAML 編譯器下發生編譯時期錯誤。 如需 WPF 中 `x:Class` 處理其他方面的詳細資訊，請參閱[wpf 中的程式碼後置和 XAML](../wpf/advanced/code-behind-and-xaml-in-wpf.md)。  
  
## <a name="xclass-for-windows-workflow-foundation"></a>適用于 Windows Workflow Foundation 的 X：Class  
 針對 Windows Workflow Foundation，`x:Class` 會將自訂活動的類別命名為完全以 XAML 撰寫，或以程式碼後置的方式命名活動設計工具的 XAML 頁面的部分類別。  
  
## <a name="silverlight-usage-notes"></a>Silverlight 使用方式備註  
 Silverlight 的 `x:Class` 會在其他篇幅中做說明。 如需詳細資訊，請參閱[XAML 命名空間（x：）語言功能（Silverlight）](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95))。  
  
## <a name="see-also"></a>請參閱

- [x:Subclass 指示詞](x-subclass-directive.md)
- [WPF 的 XAML 和自訂類別](../wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [x:ClassModifier 指示詞](x-classmodifier-directive.md)
- [從 WPF 移轉至 System.Xaml 的類型](types-migrated-from-wpf-to-system-xaml.md)
