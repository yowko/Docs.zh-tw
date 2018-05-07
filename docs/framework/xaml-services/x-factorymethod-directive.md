---
title: x:FactoryMethod 指示詞
ms.date: 03/30/2017
helpviewer_keywords:
- XAML. x:FactoryMethod directive [XAML Services]
- FactoryMethod directive in XAML [XAML Services]
- x:FactoryMethod directive [XAML Services]
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
ms.openlocfilehash: 75225e624abdd3dc0862a04fae409da48b3f0d1e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="xfactorymethod-directive"></a>x:FactoryMethod 指示詞
指定 XAML 處理器必須用來解決它支援的型別之後初始化物件的建構函式以外的方法。  
  
## <a name="xaml-attribute-usage-no-xarguments"></a>XAML 屬性使用方式，不使用 x： 引數  
  
```  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-attribute-usage-xarguments-as-elements"></a>XAML 屬性使用方式，為元素的 x： 引數  
  
```  
<object x:FactoryMethod="methodname"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`methodname`|XAML 處理器呼叫初始化為指定的執行個體方法的字串方法名稱`object`。 請參閱＜備註＞。|  
|`oneOrMoreObjectElements`|一或多個物件項目指定處理站方法參數的物件。 順序是很重要。它表示在其中引數應該傳遞給的 factory 方法的順序。|  
  
## <a name="remarks"></a>備註  
 如果`methodname`是執行個體方法，無法加以限定。  
  
 支援的 factory 方法為靜態方法。 如果`methodname`是靜態方法，`methodname`依現狀*typeName*。*methodName*組合，其中*typeName*名稱定義的靜態 factory 方法的類別。 *typeName*可以是如果參考類型中對應的 xmlns 前置詞限定。 *typeName*可以是類型不同於`typeof(``object``)`。  
  
 Factory 方法，必須是宣告的公用方法的型別之備份的相關物件項目。  
  
 處理站方法必須傳回可指派至相關物件執行個體。 Factory 方法，應該永遠不會傳回 null。  
  
 `x:Arguments` 最符合的 factory 方法的簽章的原則上運作。 比對參數計數會先評估。 如果有多個可能的相符項目參數計數的參數類型為則取決於評估及最佳的相符項目。 如果此評估階段之後仍有模稜兩可，XAML 處理器的行為是未定義的。  
  
 `x:FactoryMethod`項目使用方式不是屬性項目用法中的一般意義，因為指示詞標記未參考包含物件項目類型。 預期的項目用法是較不常見，比屬性使用方式。 `x:Arguments` 可以使用 （屬性或項目使用方式），連同`x:FactoryMethod`項目使用方式，但這不特別會顯示在使用方式區段。  
  
 `x:FactoryMethod` 當項目必須在任何其他屬性項目之前，必須優先於任何`x:Arguments`也提供做為項目，而且必須在前面的任何內容/內部文字/初始化文字。  
  
## <a name="see-also"></a>另請參閱  
 [x:Arguments 指示詞](../../../docs/framework/xaml-services/x-arguments-directive.md)
