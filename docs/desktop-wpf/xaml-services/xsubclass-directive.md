---
title: x:Subclass 指示詞
ms.date: 03/30/2017
f1_keywords:
- Subclass
- xSubclass
- x:Subclass
helpviewer_keywords:
- x:Subclass attribute [XAML Services]
- XAML [XAML Services], x:Subclass attribute
- Subclass attribute in XAML [XAML Services]
ms.assetid: 99f66072-8107-4362-ab99-8171dc83b469
ms.openlocfilehash: b888ef73d1678fd37c984e4bb223f24e5b65d2cc
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90540715"
---
# <a name="xsubclass-directive"></a>x:Subclass 指示詞

當也提供時，修改 XAML 標記編譯行為 `x:Class` 。 所提供的會以中繼類別的形式建立，而不是建立以中繼類別為基礎的部分類別 `x:Class` `x:Class` ，然後您所提供的衍生類別應該以作為基礎 `x:Class` 。

## <a name="xaml-attribute-usage"></a>XAML Attribute Usage

```xaml
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">
   ...
</object>
```

## <a name="xaml-values"></a>XAML 值

|||
|-|-|
|`namespace`|選擇性。 指定包含的 CLR 命名空間 `classname` 。 如果 `namespace` 指定了，就會以點 (。 ) 分隔 `namespace` 和 `classname` 。|
|`classname`|必要。 指定部分類別的 CLR 名稱，以連接載入的 XAML 和該 XAML 的程式碼後端。 請參閱＜備註＞。|
|`subclassNamespace`|選擇性。 `namespace`如果每個命名空間可以解析另一個命名空間，則可以不同。 指定包含的 CLR 命名空間 `subclassName` 。 如果 `subclassName` 指定了，就會以點 (。 ) 分隔 `subclassNamespace` 和 `subclassName` 。|
|`subclassName`|必要。 指定子類別的 CLR 名稱。|

## <a name="dependencies"></a>相依性

您也必須在相同的物件上提供[x：Class](xclass-directive.md)指示詞，且該物件必須是 XAML 生產的根項目。

## <a name="remarks"></a>備註

`x:Subclass` 使用方式主要適用于不支援部分類別宣告的語言。

用作的類別 `x:Subclass` 不能是嵌套類別，而且 `x:Subclass` 必須參考根物件，如「相依性」一節中所述。

否則， `x:Subclass` .NET XAML 服務執行會未定義的概念意義。 這是因為 .NET XAML 服務的行為不會指定 XAML 標記和支援的程式碼所連接的整體程式設計模型。 與和相關的進一步概念 `x:Class` 的 `x:Subclass` 執行是由使用程式設計模型或應用程式模型的特定架構所執行，以定義如何連接 XAML 標記、編譯的標記和 CLR 程式碼後端。 每個架構都可能有自己的組建動作，可啟用某些行為，或是必須包含在組建環境中的特定元件。 在架構中，組建動作也會根據用於程式碼後端的特定 CLR 語言而有所不同。

## <a name="wpf-usage-notes"></a>WPF 使用注意事項

`x:Subclass` 可以位於頁面根目錄或 <xref:System.Windows.Application> 應用程式定義的根目錄中，也就是已有的應用程式定義 `x:Class` 。 `x:Subclass`在頁面或應用程式根目錄以外的任何專案上宣告，或指定不存在的專案 `x:Class` ，會導致編譯時期錯誤。

建立適用于此案例的衍生類別 `x:Subclass` 相當複雜。 您可能需要檢查中繼檔案， (專案的 obj 資料夾中所產生的. g 檔案，其名稱包含) 的 .xaml 檔案名。 這些中繼檔案可協助您在已編譯的應用程式中，于聯結的部分類別中判斷特定程式設計結構的來源。

衍生類別中的事件處理常式必須 `internal override` `Friend Overrides` 在 Microsoft Visual Basic) 中 (，才能覆寫在編譯期間于中繼類別中建立之處理常式的存根。 否則，衍生類別實 (會隱藏中繼類別實) 陰影，而不會叫用中繼類別處理常式。

當您同時定義 `x:Class` 和時 `x:Subclass` ，您不需要為所參考的類別提供任何實作為 `x:Class` 。 您只需要透過屬性提供它的名稱， `x:Class` 編譯器就會在中繼檔案中建立類別的指引， (編譯器不會在此情況下選取預設名稱) 。 您可以為 `x:Class` 類別提供實值; 不過，這不是使用和的一般案例 `x:Class` `x:Subclass` 。

## <a name="see-also"></a>另請參閱

- [x:Class 指示詞](xclass-directive.md)
- [WPF 的 XAML 和自訂類別](/dotnet/desktop/wpf/advanced/xaml-and-custom-classes-for-wpf)
