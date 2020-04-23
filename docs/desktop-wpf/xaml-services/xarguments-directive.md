---
title: x:Arguments 指示詞
ms.date: 03/30/2017
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
ms.openlocfilehash: 5ec6e192688e1065ea847db6c175ad9da0e743fe
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071588"
---
# <a name="xarguments-directive"></a>x:Arguments 指示詞

在 XAML 或工廠方法物件聲明中為非無參數構造函數物件元素聲明打包構造參數。

## <a name="xaml-element-usage-nonparameterless-constructor"></a>XAML 元素使用(無參數建構函數)

```xaml
<object ...>
  <x:Arguments>
    oneOrMoreObjectElements
  </x:Arguments>
</object>
```

## <a name="xaml-element-usage-factory-method"></a>XAML 元素用法(工廠方法)

```xaml
<object x:FactoryMethod="methodName"...>
  <x:Arguments>
    oneOrMoreObjectElements
  </x:Arguments>
</object>
```

## <a name="xaml-values"></a>XAML 值

|||
|-|-|
|`oneOrMoreObjectElements`|指定要傳遞給支援的非無參數建構函數或工廠方法的參數的一個或多個物件元素。<br /><br /> 典型用法是使用物件元素中的初始化文本來指定實際參數值。 請參閱示例部分。<br /><br /> 元素的順序很重要。 XAML 類型順序必須與後備構造函數或工廠方法重載的類型和類型順序匹配。|
|`methodName`|應處理任何`x:Arguments`參數的工廠方法的名稱。|

## <a name="dependencies"></a>相依性

`x:FactoryMethod`可以修改`x:Arguments`適用的範圍和行為。

如果未`x:FactoryMethod`指定`x:Arguments`, 則應用於支援建構函數的備用(非預設)簽名。

如果`x:FactoryMethod`指定,`x:Arguments`則應用於命名方法的重載。

## <a name="remarks"></a>備註

XAML 2006 可通過初始化文本支援非預設初始化。 然而,初始化文本構造技術的實際應用有限。 初始化文字被視為單個文字字串;因此,它僅添加單個參數初始化的功能,除非為構造行為定義類型轉換器,該構造行為可以從字串解析自定義資訊項和自定義分隔符。 此外,到物件邏輯的文本字串可能是給定的 XAML 解析器的本機預設類型轉換器,用於處理真字串以外的基元。

`x:Arguments` XAML 用法在典型意義上不是屬性元素用法,因為指令標記不引用包含物件元素的類型。 它更類似於其他指令,例如`x:Code`元素將標記的範圍解釋為子內容的預設值以外的範圍。 在這種情況下,每個物件元素的 XAML 類型傳達有關參數類型的資訊,XAML 解析器`x:Arguments`使用該類型來確定 使用方法嘗試引用的特定構造函數工廠方法簽名。

`x:Arguments`對於正在建構的物件元素,必須位於物件元素的任何其他屬性元素、內容、內部文本或初始化字串之前。 中`x:Arguments`的物件元素可以包括屬性和初始化字串,這是 XAML 類型及其支援構造函數或工廠方法所允許的。 對於物件或參數,可以通過引用已建立的首碼映射來指定自定義 XAML 類型或 XAML 類型,這些類型在預設 XAML 命名空間之外。

XAML 處理器使用以下準則來確定如何在`x:Arguments`中 指定的參數用於構造物件。 如果`x:FactoryMethod`指定,則將資訊與指定`x:FactoryMethod`的 (請注意`x:FactoryMethod`,值 是方法名稱,並且命名方法可以具有重載。 如果未`x:FactoryMethod`指定,則將資訊與物件的所有公共構造函數重載集進行比較。 然後,XAML 處理邏輯比較參數數,並選擇具有匹配的參數的重載。 如果有多個匹配項,XAML 處理器應根據提供的物件元素的 XAML 類型比較參數類型。 如果仍然有多個匹配項,則未定義 XAML 處理器行為。 如果指定`x:FactoryMethod`了 ,但方法無法解決,XAML 處理器應引發異常。

從技術上講,XAML`<x:Arguments>string</x:Arguments>`屬性使用是可能的。 但是,除了通過初始化文本和類型轉換器可以執行哪些功能之外,這沒有任何功能,使用此語法不是 XAML 2009 工廠方法功能的設計意圖。

## <a name="examples"></a>範例

下面的範例顯示一個非無參數構造函數簽名,然後是該簽名的`x:Arguments`XAML 用法。

```csharp
public class Food {
  private string _name;
  private Int32 _calories;
  public Food(string name, Int32 calories) {
      _name=name;
      _calories=calories;
  }
}
```

```xaml
<my:Food>
  <x:Arguments>
      <x:String>Apple</x:String>
      <x:Int32>150</x:Int32>
  </x:Arguments>
</my:Food>
```

下面的範例顯示目標工廠方法簽名,然後顯示該簽名的`x:Arguments`XAML 用法。

```csharp
public Food TryLookupFood(string name)
{
switch (name) {
  case "Apple": return new Food("Apple",150);
  case "Chocolate": return new Food("Chocolate",200);
  case "Cheese": return new Food("Cheese", 450);
  default: {return new Food(name,0);
}
}
```

```xaml
<my:Food x:FactoryMethod="TryLookupFood">
  <x:Arguments>
      <x:String>Apple</x:String>
  </x:Arguments>
</my:Food>
```

## <a name="see-also"></a>另請參閱

- [定義可搭配 .NET XAML 服務使用的自訂類型](define-custom-types.md)
- [XAML 概觀 (WPF)](../fundamentals/xaml.md)
