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
ms.openlocfilehash: e85e0fb5a0e1a865ed84a93767f8152a115bbe5f
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071364"
---
# <a name="xsubclass-directive"></a>x:Subclass 指示詞

在提供時`x:Class`修改 XAML 標記編譯行為。 提供的派生類應基於`x:Class``x:Class``x:Class`,而不是創建基於 的部分類。

## <a name="xaml-attribute-usage"></a>XAML Attribute Usage

```xaml
<object x:Class="namespace.classname" x:Subclass="subclassNamespace.subclassName">
   ...
</object>
```

## <a name="xaml-values"></a>XAML 值

|||
|-|-|
|`namespace`|選擇性。 指定包含的`classname`CLR 命名空間。 如果`namespace`指定,點 (.) 會`namespace`分`classname`隔與 。|
|`classname`|必要。 指定連接載入的 XAML 和該 XAML 的代碼後面的部分類的 CLR 名稱。 請參閱＜備註＞。|
|`subclassNamespace`|選擇性。 可以不同於`namespace`如果每個命名空間可以解析另一個。 指定包含的`subclassName`CLR 命名空間。 如果`subclassName`指定,點 (.) 會`subclassNamespace`分`subclassName`隔與 。|
|`subclassName`|必要。 指定子類的 CLR 名稱。|

## <a name="dependencies"></a>相依性

[x:類指令](xclass-directive.md)也必須在同一物件上提供,並且該物件必須是 XAML 生產的根元素。

## <a name="remarks"></a>備註

`x:Subclass`主要用於不支援部分類聲明的語言。

用作`x:Subclass`的 類不能是嵌套類,`x:Subclass`並且必須引用根物件,如"依賴"部分中所述。

否則,.NET XAML 服務實現未`x:Subclass`定義 其概念含義。 這是因為 .NET XAML 服務行為未指定連接 XAML 標記和背碼的總體程式設計模型。 與`x:Class`和`x:Subclass`相關的其他概念的實現由使用程式設計模型或應用程式模型來定義如何連接 XAML 標記、編譯標記和基於 CLR 的代碼後面的特定框架執行。 每個框架可能都有自己的生成操作,這些操作啟用某些行為或必須包含在生成環境中的特定元件。 在框架中,生成操作還可以根據用於代碼後面的特定 CLR 語言而變化。

## <a name="wpf-usage-notes"></a>WPF 使用注意事項

`x:Subclass`可以位於頁面根上或應用程式定義的<xref:System.Windows.Application>根上,該定義已`x:Class`具有 。 在`x:Subclass`頁面或應用程式根以外的任何元素上聲明,或在`x:Class`不存在 時指定它,會導致編譯時錯誤。

創建正確適用於該方案的`x:Subclass`派生類相當複雜。 您可能需要檢查中間檔(通過標記編譯專案 obj 資料夾中生成的 .g 檔,以及包含 .xaml 檔名的名稱)。 這些中間檔可以説明您確定編譯應用程式中聯接部分類中某些程式設計構造的來源。

派生類中的事件處理程式必須`internal override``Friend Overrides`( 在 Microsoft Visual Basic 中)才能覆蓋在編譯過程中中間類中創建的處理程式的存根。 否則,派生類實現將隱藏(陰影)中間類實現,並且不會調用中間類處理程式。

定義`x:Class``x:Subclass`和 時,不需要`x:Class`為引用的類提供任何實現。 您只需透過`x:Class`屬性為其指定名稱,以便編譯器對它在中間檔中創建的類具有一些指導(在這種情況下,編譯器不會選擇預設名稱)。 您可以為`x:Class`類提供一個實現;但是,這不是使用和`x:Class``x:Subclass`的典型方案。

## <a name="see-also"></a>另請參閱

- [x:Class 指示詞](xclass-directive.md)
- [WPF 的 XAML 和自訂類別](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
