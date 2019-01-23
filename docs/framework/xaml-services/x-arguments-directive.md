---
title: x:Arguments 指示詞
ms.date: 03/30/2017
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
ms.openlocfilehash: d4cff4c2f95d1418371921a3ac992a3b243d1c07
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54490813"
---
# <a name="xarguments-directive"></a>x:Arguments 指示詞
針對 XAML，非預設建構函式物件的項目宣告或 factory 方法的物件宣告，封裝建構引數。  
  
## <a name="xaml-element-usage-nondefault-constructor"></a>XAML 項目使用方式 （非預設建構函式）  
  
```  
<object ...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-element-usage-factory-method"></a>XAML 項目使用方式 （處理站方法）  
  
```  
<object x:FactoryMethod="methodName"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`oneOrMoreObjectElements`|指定要傳遞至支援非預設建構函式或 factory 方法的引數的一個或多個物件元素。<br /><br /> 通常是用來使用物件元素內的初始設定文字，以指定的實質引數的值。 請參閱 < 範例 > 一節。<br /><br /> 項目的順序很重要。 在順序中的 XAML 型別必須符合類型，然後輸入備份建構函式或 factory 方法多載的順序。|  
|`methodName`|應該處理任何的 factory 方法的名稱`x:Arguments`引數。|  
  
## <a name="dependencies"></a>相依性  
 `x:FactoryMethod` 範圍和行為可以修改其中`x:Arguments`套用。  
  
 如果沒有`x:FactoryMethod`未指定，`x:Arguments`適用於支援建構函式的替代 （非預設值） 簽章。  
  
 如果`x:FactoryMethod`未指定，`x:Arguments`適用於具名方法的多載。  
  
## <a name="remarks"></a>備註  
 XAML 2006 可支援透過初始設定文字的非預設值初始化。 不過，實際的應用程式的初始設定文字建構是技巧的有限。 初始設定文字會被視為單一文字字串;因此，它只會新增功能的單一參數初始化除非定義型別轉換子可以剖析自訂的資訊項目和自訂的分隔符號，從字串建構行為。 此外，物件邏輯的文字字串可能是處理基本項目，則為 true 的字串以外的給定的 XAML 剖析器的原生的預設型別轉換子。  
  
 `x:Arguments` XAML 用法不是屬性項目使用方式的一般意義，因為指示詞的標記不會參考包含物件項目類型。 它就是這類比較類似於其他指示詞`x:Code`元素 demarks 中應該標記解譯以外子內容的預設值為一個範圍的位置。 在此情況下，每個物件項目的 XAML 型別會由 XAML 剖析器用來決定哪一個特定的建構函式 factory 方法簽章引數類型的相關資訊的通訊`x:Arguments`使用量嘗試參考。  
  
 `x:Arguments` 物件項目建構應優先於任何其他屬性的項目、 內容、 內部文字或初始化字串的物件項目。 中的物件項目`x:Arguments`可以包括屬性和初始化字串，所允許的 XAML 型別和其支援的建構函式或 factory 方法。 物件或引數中，您可以指定自訂的 XAML 型別或 XAML 型別，否則以外的預設 XAML 命名空間的參考已建立的前置詞對應。  
  
 XAML 處理器會使用下列指導方針來判斷如何在中指定的引數`x:Arguments`應該用來建構物件。 如果`x:FactoryMethod`指定，則資訊進行比較來指定`x:FactoryMethod`(請注意，值`x:FactoryMethod`是方法名稱，而具名的方法的多載。 如果`x:FactoryMethod`未指定，資訊進行比較之物件的所有公用建構函式多載的集合。 XAML 處理邏輯然後比較的參數數目，並選取使用相符的引數數目的多載。 如果有多個相符項目，則 XAML 處理器應該比較根據提供的物件項目的 XAML 型別參數的類型。 如果仍然超過一個符合項目，XAML 處理器行為是未定義。 如果`x:FactoryMethod`指定但方法不能解析，XAML 處理器應該擲回例外狀況。  
  
 XAML 屬性使用方式`<x:Arguments>string</x:Arguments>`是可行的。 不過，這提供什麼無法透過否則初始化文字和類型轉換器，沒有功能，並使用此語法不是 XAML 2009 的 factory 方法功能的設計目的。  
  
## <a name="examples"></a>範例  
 下列範例會顯示非預設建構函式簽章，則 XAML 使用`x:Arguments`，用來存取該簽章。  
  
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
  
 下列範例顯示目標處理站方法簽章，則 XAML 使用`x:Arguments`，用來存取該簽章。  
  
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
- [定義可搭配 .NET Framework XAML 服務使用的自訂類型](../../../docs/framework/xaml-services/defining-custom-types-for-use-with-net-framework-xaml-services.md)
- [XAML 概觀 (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
