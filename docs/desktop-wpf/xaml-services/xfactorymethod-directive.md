---
title: x:FactoryMethod 指示詞
ms.date: 03/30/2017
helpviewer_keywords:
- XAML. x:FactoryMethod directive [XAML Services]
- FactoryMethod directive in XAML [XAML Services]
- x:FactoryMethod directive [XAML Services]
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
ms.openlocfilehash: 5e864b6f5d664b079036a5d915e2f6f81b83639f
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071532"
---
# <a name="xfactorymethod-directive"></a>x:FactoryMethod 指示詞
指定 XAML 處理器應在解析物件支援類型後使用來初始化物件的構造函數以外的方法。  
  
## <a name="xaml-attribute-usage-no-xarguments"></a>XAML 屬性用法,無 x:參數  
  
```xaml  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-attribute-usage-xarguments-as-elements"></a>XAML 屬性用法,x:參數作為元素  
  
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
|`methodname`|XAML 處理器呼叫的方法的字串方法名稱,用於初始化指定為`object`的實例。 請參閱＜備註＞。|  
|`oneOrMoreObjectElements`|指定工廠方法參數的物件的一個或多個物件元素。 訂單很重要;它表示參數應傳遞給工廠方法的順序。|  
  
## <a name="remarks"></a>備註  
 如果是`methodname`實例方法,則無法限定它。  
  
 支持作為工廠方法的靜態方法。 如果是`methodname`靜態方法`methodname`,`typeName.methodName`則作為 組合`typeName`提供,其中 命名定義靜態工廠方法的類。 `typeName`如果引用映射的 xmlns 中的類型,則可以在前綴限定。 `typeName`可以是與`typeof(object)`不同的類型。  
  
 工廠方法必須是支持相關物件元素的類型聲明的公共方法。  
  
 工廠方法必須返回可分配給相關對象的實例。 工廠方法絕不應返回 null。  
  
 `x:Arguments`操作的原則是最佳匹配工廠方法的簽名。 匹配首先計算參數計數。 如果參數計數有多個可能的匹配項,則計算參數類型並確定最佳匹配。 如果在此評估階段之後仍有歧義,則未定義 XAML 處理器行為。  
  
 元素`x:FactoryMethod`用法在典型意義上不是屬性元素用法,因為指令標記不引用包含物件元素的類型。 預計元素使用比屬性用法少。 `x:Arguments`(屬性或元素用法)可以隨元素使用一`x:FactoryMethod`起使用,但"使用"部分沒有具體顯示。  
  
 `x:FactoryMethod`作為元素必須位於任何其他屬性元素之前,必須位於任何`x:Arguments`也作為元素提供的元素之前,並且必須位於任何內容/內部文本/初始化文本之前。  
  
## <a name="see-also"></a>另請參閱

- [x:Arguments 指示詞](xarguments-directive.md)
