---
title: x:Arguments 指示詞
ms.date: 03/30/2017
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
ms.openlocfilehash: e0e7f380ec176e80d2422878a2e676d64985d660
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="xarguments-directive"></a>x:Arguments 指示詞
在 XAML 中、 非預設建構函式物件項目宣告或 factory 方法物件宣告，封裝建構引數。  
  
## <a name="xaml-element-usage-nondefault-constructor"></a>（非預設建構函式） 的 XAML 項目用法  
  
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
|`oneOrMoreObjectElements`|一或多個物件項目指定要傳遞至支援非預設建構函式或 factory 方法的引數。<br /><br /> 一般用法是，使用指定的實際引數的值的物件項目內的初始文字。 請參閱範例 > 一節。<br /><br /> 項目的順序很重要。 在順序中的 XAML 型別必須符合類型，然後輸入備份建構函式或 factory 方法多載的順序。|  
|`methodName`|應該處理任何的 factory 方法的名稱`x:Arguments`引數。|  
  
## <a name="dependencies"></a>相依性  
 `x:FactoryMethod` 範圍和行為可以修改其中`x:Arguments`套用。  
  
 如果沒有`x:FactoryMethod`指定，則`x:Arguments`適用於支援建構函式的替代 （非預設值） 簽章。  
  
 如果`x:FactoryMethod`指定，則`x:Arguments`適用於具名方法的多載。  
  
## <a name="remarks"></a>備註  
 XAML 2006 可支援透過初始文字的非預設值初始化。 不過，實際的應用程式的初始化文字建構項技術是限制。 初始文字會被視為單一文字字串;因此，它只會將單一參數初始設定的功能，除非建構行為可以剖析自訂的資訊項目以及從字串的自訂分隔符號定義型別轉換子。 此外，邏輯物件的文字字串可能會處理原始物件，則為 true 的字串以外的給定的 XAML 剖析器的原生的預設型別轉換子。  
  
 `x:Arguments` XAML 用法不是屬性項目用法中的一般意義，因為指示詞標記未參考包含物件項目類型。 例如，它是比較類似於其他指示詞`x:Code`其中的項目 demarks 所在標記應該解譯為以外子內容的預設值的範圍。 在此情況下，XAML 類型的每個物件項目傳達資訊引數類型的 XAML 剖析器用來判斷哪一個特定的建構函式的 factory 方法簽章`x:Arguments`使用量嘗試參考。  
  
 `x:Arguments` 物件項目所建構應優先於其他任何屬性項目、 內容、 內部文字或初始化字串的物件項目。 中的物件項目`x:Arguments`可以包括屬性和初始化字串所允許的該 XAML 類型和其支援的建構函式或 factory 方法。 物件或引數，您可以指定自訂的 XAML 型別或 XAML 類型，否則預設 XAML 命名空間外部參考已建立的前置詞對應。  
  
 XAML 處理器會使用下列指導方針來判斷如何在中指定的引數`x:Arguments`應該用來建構物件。 如果`x:FactoryMethod`指定，則資訊進行比較的指定`x:FactoryMethod`(請注意，值`x:FactoryMethod`是方法名稱，而具名的方法的多載。 如果`x:FactoryMethod`未指定，資訊進行比較的物件的所有公用建構函式多載的集合。 然後，XAML 處理邏輯會比較的參數數目，並選取具有相符引數數目的多載。 如果有多個相符項目，XAML 處理器應該比較根據提供的物件項目的 XAML 型別參數的類型。 如果沒有仍然超過一個符合項目，XAML 處理器的行為未定義。 如果`x:FactoryMethod`指定，但此方法無法解決，XAML 處理器應該擲回例外狀況。  
  
 XAML 屬性使用方式`<x:Arguments>string</x:Arguments>`是可行的。 不過，這會提供任何功能什麼無法透過否則初始化文字和類型轉換器，並使用此語法不是 XAML 2009 的 factory 方法功能的設計目的。  
  
## <a name="examples"></a>範例  
 下列範例顯示的非預設建構函式簽章，則的 XAML 用法`x:Arguments`，用來存取該簽章。  
  
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
  
 下列範例顯示目標的 factory 方法簽章然後的 XAML 用法`x:Arguments`，用來存取該簽章。  
  
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
 [定義可搭配 .NET Framework XAML 服務使用的自訂類型](../../../docs/framework/xaml-services/defining-custom-types-for-use-with-net-framework-xaml-services.md)  
 [XAML 概觀 (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)
