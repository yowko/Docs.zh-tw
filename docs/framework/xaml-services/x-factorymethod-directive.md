---
title: x:FactoryMethod 指示詞
ms.date: 03/30/2017
helpviewer_keywords:
- XAML. x:FactoryMethod directive [XAML Services]
- FactoryMethod directive in XAML [XAML Services]
- x:FactoryMethod directive [XAML Services]
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
ms.openlocfilehash: 586965dd4094e81fd830a09b64604cf33f195630
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053782"
---
# <a name="xfactorymethod-directive"></a>x:FactoryMethod 指示詞
指定 XAML 處理器在解析其支援型別之後，要用來初始化物件的函式以外的方法。  
  
## <a name="xaml-attribute-usage-no-xarguments"></a>XAML 屬性使用方式，無 x:Arguments  
  
```xaml  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-attribute-usage-xarguments-as-elements"></a>XAML 屬性使用方式，x:Arguments 為元素  
  
```xaml  
<object x:FactoryMethod="methodname"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`methodname`|XAML 處理器呼叫來初始化指定為`object`之實例的方法的字串方法名稱。 請參閱＜備註＞。|  
|`oneOrMoreObjectElements`|指定 factory 方法參數之物件的一或多個物件元素。 順序很重要;它表示引數傳遞至 factory 方法的順序。|  
  
## <a name="remarks"></a>備註  
 如果`methodname`是實例方法，則不能是限定的。  
  
 可支援靜態方法做為 factory 方法。 如果`methodname`是靜態方法， `methodname`則會以*typeName*的形式提供。*方法*名稱組合，其中*typeName*會將定義靜態 factory 方法的類別命名為。 如果在對應的 xmlns 中參考型別，則*typeName*可以是前置詞限定的。 *typeName*可以是與`typeof(object)`不同的類型。  
  
 Factory 方法必須是可支援相關物件元素之類型的已宣告公用方法。  
  
 Factory 方法必須傳回可指派給相關物件的實例。 Factory 方法絕對不應傳回 null。  
  
 `x:Arguments`會針對 factory 方法的簽章，操作最符合的原則。 比對會先評估參數計數。 如果有一個以上的參數計數可能相符，則會評估參數類型，並決定最符合的值。 如果在這個評估階段之後仍有不明確的情況，XAML 處理器行為會是未定義的。  
  
 `x:FactoryMethod`由於指示詞標記不會參考包含物件專案的類型，因此專案使用方式不是一般意義中的屬性元素用法。 預期元素的使用方式不如屬性使用方式一般。 `x:Arguments`（屬性或專案使用方式）可與`x:FactoryMethod`專案使用方法一起使用，但不會特別顯示在 [使用方式] 區段中。  
  
 `x:FactoryMethod`當專案必須在任何其他屬性專案之前，必須在任何`x:Arguments`也提供作為元素的前面，而且必須在任何內容/內部文字/初始化文字之前。  
  
## <a name="see-also"></a>另請參閱

- [x:Arguments 指示詞](x-arguments-directive.md)
