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
ms.openlocfilehash: 8f7ca5fdb170411aba24d34b8bf4d6c4f5776cc4
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555142"
---
# <a name="xclass-directive"></a>x:Class 指示詞
設定 XAML 標記編譯以聯結標記和程式碼後端之間的部分類別。 程式碼部分類別是在 Common Language Specification (CLS) 語言中的不同程式碼檔案中定義，而標記部分類別通常是在 XAML 編譯期間由程式碼產生所建立。

## <a name="xaml-attribute-usage"></a>XAML Attribute Usage

```xaml
<object x:Class="namespace.classname"...>
  ...
</object>
```

## <a name="xaml-values"></a>XAML 值

|||
|-|-|
|`namespace`|選擇性。 指定包含所識別之部分類別的 CLR 命名空間 `classname` 。 如果 `namespace` 指定了，就會以點 (。 ) 分隔 `namespace` 和 `classname` 。 請參閱＜備註＞。|
|`classname`|必要。 指定部分類別的 CLR 名稱，以連接載入的 XAML 和該 XAML 的程式碼後端。|

## <a name="dependencies"></a>相依性

`x:Class` 只能在 XAML 生產的根項目上指定。 `x:Class` 在 XAML 生產中具有父系的任何物件上無效。 如需詳細資訊，請參閱[ \[ MS-XAML \] 區段 4.3.1.6](/previous-versions/msp-n-p/ff650760(v=pandp.10))。

## <a name="remarks"></a>備註

此 `namespace` 值可能包含額外的點，以便將相關的命名空間組織成名稱階層，這是 .net 程式設計中的常見技術。 只有值字串中的最後一個點 `x:Class` 會被解釋為分開 `namespace` ，而且 `classname.` 用來做為的類別 `x:Class` 不能是嵌套類別。 不允許使用嵌套類別，因為 `x:Class` 如果允許嵌套類別，判斷字串的點意義就不明確。

在使用的現有程式設計模型中 `x:Class` ， `x:Class` 是選擇性的，因為它完全有效，讓沒有程式碼後端的 XAML 頁面。 不過，這項功能與使用 XAML 的架構所執行的組建動作互動。 `x:Class` 功能也會受到 XAML 指定內容的各種分類在應用程式模型和對應的組建動作中的角色所影響。 如果您的 XAML 宣告事件處理屬性值，或是具現化定義類別位於程式碼後端類別中的自訂專案，您就必須為程式碼後端提供適當類別的指示詞 `x:Class` 參考 (或 [x:Subclass](xsubclass-directive.md)) 。

指示詞的值 `x:Class` 必須是字串，這個字串會指定類別的完整名稱，但不含任何元件資訊 (相當於 <xref:System.Type.FullName%2A?displayProperty=nameWithType>) 。 針對簡單的應用程式，如果程式碼後端也是以這種方式結構化，則您可以省略 CLR 命名空間資訊， (程式碼定義會從類別層級開始) 。

頁面或應用程式定義的程式碼後端檔案必須位於程式碼檔案中，該檔案包含做為產生已編譯應用程式之專案的一部分，並且牽涉到標記編譯。 您必須遵循 CLR 類別的名稱規則。 如需詳細資訊，請參閱 [架構設計指導方針](../../../api/index.md)。 根據預設，程式碼後端類別必須是 `public` ; 不過，您可以使用 [x:ClassModifier](xclassmodifier-directive.md)指示詞，在不同的存取層級定義它。

這項屬性的解讀 `x:Class` 只適用于以 CLR 為基礎的 xaml 實作為 .NET Xaml 服務。 其他不是以 CLR 為基礎且不使用 .NET XAML 服務的 XAML 執行，可能會使用不同的解析公式來連接 XAML 標記和支援執行時間程式碼。 如需更多一般解釋的詳細資訊 `x:Class` ，請參閱[ \[ MS \] XAML](/previous-versions/msp-n-p/ff650760(v=pandp.10))。

在特定的架構層級上，的意義 `x:Class` 在 .NET XAML 服務中是未定義的。 這是因為 .NET XAML 服務不會指定 XAML 標記和支援的程式碼所連接的程式設計模型。 指示詞的其他用法 `x:Class` 可能會由使用程式設計模型或應用程式模型的特定架構來執行，以定義如何連接 XAML 標記和 CLR 程式碼後端。 每個架構都可以有自己的組建動作，以啟用必須包含在組建環境中的某些行為或特定元件。 在架構中，組建動作也會根據程式碼後端所使用的特定 CLR 語言而有所不同。

## <a name="xclass-in-the-wpf-programming-model"></a>WPF 程式設計模型中的 X：Class

在 WPF 應用程式和 WPF 應用程式模型中， `x:Class` 可以將任何專案的屬性（也就是 xaml 檔案的根）宣告為屬性，並將其編譯 (其中 xaml 包含在具有組建動作) 的 WPF 應用程式專案中 `Page` ，或在 <xref:System.Windows.Application> 已編譯之 WPF 應用程式的應用程式定義中包含根項目。 在 `x:Class` 頁面根或應用程式根目錄以外的專案上宣告，或在未編譯的 WPF XAML 檔案上宣告，會導致 .NET Framework 3.0 和 .NET Framework 3.5 WPF XAML 編譯器下發生編譯時期錯誤。 如需有關在 WPF 中處理其他方面的詳細資訊 `x:Class` ，請參閱 [wpf 中的程式碼後端和 XAML](/dotnet/desktop/wpf/advanced/code-behind-and-xaml-in-wpf)。

## <a name="xclass-for-windows-workflow-foundation"></a>Windows Workflow Foundation 的 X：Class
針對 Windows Workflow Foundation，會 `x:Class` 命名完全以 XAML 撰寫的自訂活動類別，或為具有程式碼後端的活動設計工具命名 XAML 頁面的部分類別。

## <a name="silverlight-usage-notes"></a>Silverlight 使用注意事項

`x:Class` Silverlight 會另外記載。 如需詳細資訊，請參閱 [XAML 命名空間 (x： ) 語言功能 (Silverlight) ](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95))。

## <a name="see-also"></a>另請參閱

- [x:Subclass 指示詞](xsubclass-directive.md)
- [WPF 的 XAML 和自訂類別](/dotnet/desktop/wpf/advanced/xaml-and-custom-classes-for-wpf)
- [x:ClassModifier 指示詞](xclassmodifier-directive.md)
- [從 WPF 移轉至 System.Xaml 的類型](/dotnet/desktop/wpf/advanced/types-migrated-from-wpf-to-system)
