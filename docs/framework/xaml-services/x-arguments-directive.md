---
title: x:Arguments 指示詞
ms.date: 03/30/2017
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
ms.openlocfilehash: a18de9a07839f5b01620311832b85667680c12ad
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053825"
---
# <a name="xarguments-directive"></a>x:Arguments 指示詞
封裝 XAML 或 factory 方法物件宣告中非無參數之函式物件專案宣告的結構引數。  
  
## <a name="xaml-element-usage-nonparameterless-constructor"></a>XAML 元素使用方式 (Nonparameterless 的函式)  
  
```xaml  
<object ...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-element-usage-factory-method"></a>XAML 元素使用方式 (factory 方法)  
  
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
|`oneOrMoreObjectElements`|一或多個物件專案, 指定要傳遞給支援非參數的函式或 factory 方法的引數。<br /><br /> 一般用法是在物件元素內使用初始化文字, 以指定實際的引數值。 請參閱範例一節。<br /><br /> 元素的順序很重要。 順序中的 XAML 類型必須符合支援的函式或 factory 方法多載的類型和類型順序。|  
|`methodName`|應該處理任何`x:Arguments`引數的 factory 方法名稱。|  
  
## <a name="dependencies"></a>相依性  
 `x:FactoryMethod`可以修改`x:Arguments`套用的範圍和行為。  
  
 如果未`x:FactoryMethod`指定, `x:Arguments`則會套用至支援之函式的替代 (非預設) 簽章。  
  
 如果`x:FactoryMethod`指定, `x:Arguments`則會套用至已命名方法的多載。  
  
## <a name="remarks"></a>備註  
 XAML 2006 可以透過初始化文字支援非預設初始化。 不過, 初始化文字結構化技術的實際應用會受到限制。 初始化文字會被視為單一文字字串;因此, 它只會加入單一參數初始化的功能, 除非已針對可從字串剖析自訂資訊專案和自訂分隔符號的結構行為定義類型轉換器。 此外, 文字字串至物件邏輯可能是指定的 XAML 剖析器的原生預設類型轉換器, 用於處理 true 字串以外的基本專案。  
  
 `x:Arguments` XAML 用法不是一般意義的屬性專案使用方式, 因為指示詞標記不會參考包含物件專案的類型。 它更類似于其他指示詞, 例如`x:Code` , 專案 demarks 的範圍, 其中的標記應解讀為子系內容的預設值。 在此情況下, 每個物件專案的 XAML 類型都會傳達引數類型的相關資訊, 而 xaml 剖析器會使用這些參數來判斷`x:Arguments`使用方式嘗試參考的特定「處理站」 factory 方法簽章。  
  
 `x:Arguments`針對所要建立的物件專案, 必須在物件元素的任何其他屬性專案、內容、內部文字或初始化字串之前。 內`x:Arguments`的物件元素可以包含屬性和初始化字串, 如該 XAML 類型和其支援的函數或 factory 方法所允許。 針對物件或引數, 您可以藉由參考已建立的前置詞對應, 指定預設 XAML 命名空間以外的自訂 XAML 類型或 XAML 類型。  
  
 XAML 處理器會使用下列指導方針來決定應該如何使用中`x:Arguments`指定的引數來建立物件。 如果`x:FactoryMethod`指定了, 就會將資訊與指定`x:FactoryMethod`的 ( `x:FactoryMethod`請注意, 的值是方法名稱, 而命名的方法可以有多載。 如果`x:FactoryMethod`未指定, 則會將資訊與物件之所有公用函式多載的集合進行比較。 然後, XAML 處理邏輯會比較參數數目, 並選取具有相符 arity 的多載。 如果有多個相符專案, XAML 處理器應該根據所提供之物件元素的 XAML 類型來比較參數的類型。 如果仍然有一個以上的相符項, XAML 處理器行為會是未定義的。 `x:FactoryMethod`如果指定了, 但無法解析方法, XAML 處理器應該會擲回例外狀況。  
  
 在技術上, `<x:Arguments>string</x:Arguments>` XAML 屬性使用方式是可行的。 不過, 這不會提供除了透過初始化文字和類型轉換器以外的其他功能, 而且使用此語法並不是 XAML 2009 factory 方法功能的設計意圖。  
  
## <a name="examples"></a>範例  
 下列範例`x:Arguments`會顯示非參數的函式簽章, 然後是存取該簽章的 XAML 使用方式。  
  
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
  
 下列範例示範目標 factory 方法簽章, 然後是`x:Arguments`會存取該簽章的 XAML 使用方式。  
  
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

- [定義可搭配 .NET Framework XAML 服務使用的自訂類型](defining-custom-types-for-use-with-net-framework-xaml-services.md)
- [XAML 概觀 (WPF)](../wpf/advanced/xaml-overview-wpf.md)
