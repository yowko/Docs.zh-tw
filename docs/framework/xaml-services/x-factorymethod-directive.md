---
title: x:FactoryMethod 指示詞
ms.date: 03/30/2017
helpviewer_keywords:
- XAML. x:FactoryMethod directive [XAML Services]
- FactoryMethod directive in XAML [XAML Services]
- x:FactoryMethod directive [XAML Services]
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
ms.openlocfilehash: 436caa9b93467dcf2a0763bcc0962a2beb722315
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2018
ms.locfileid: "45527866"
---
# <a name="xfactorymethod-directive"></a>x:FactoryMethod 指示詞
指定的 XAML 處理器應該用來解決它的支援型別之後初始化物件的建構函式以外的方法。  
  
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
|`methodname`|XAML 處理器呼叫來初始化為指定的執行個體方法的字串方法名稱`object`。 請參閱＜備註＞。|  
|`oneOrMoreObjectElements`|一或多個物件項目指定 factory 方法參數的物件。 順序很重要;它表示在其中的引數應該傳遞至 factory 方法的順序。|  
  
## <a name="remarks"></a>備註  
 如果`methodname`是執行個體方法，它不限定。  
  
 支援靜態方法，做為 factory 方法。 如果`methodname`是一種靜態方法，`methodname`依現狀*typeName*。*methodName*組合，其中*typeName*名稱定義的靜態 factory 方法的類別。 *typeName*可以是如果參考類型中對應的 xmlns 前置詞限定。 *typeName*可以是類型不同於`typeof(object)`。  
  
 Factory 方法必須宣告的公用方法之類型的備份相關的物件項目。  
  
 Factory 方法必須傳回指派給相關的物件執行個體。 Factory 方法永遠不會傳回 null。  
  
 `x:Arguments` 最符合的 factory 方法的簽章的原則上運作。 比對參數計數會先評估。 如果有多個可能的相符項目參數計數，則取決於評估且最佳的相符項目，也會是參數型別。 如果在這個階段之後仍有模稜兩可，XAML 處理器行為是評估的未定義。  
  
 `x:FactoryMethod`項目使用方式不是屬性項目用法的一般意義，因為指示詞的標記不會參考包含物件項目類型。 預期的項目使用方式是較不常見比屬性使用方式。 `x:Arguments` 可以使用 （屬性或項目使用方式），連同`x:FactoryMethod`項目使用方式，但這中未特意顯示使用方式區段。  
  
 `x:FactoryMethod` 當項目必須位於任何其他的屬性元素之前，前面必須加上任何`x:Arguments`也提供做為項目，而且前面必須加上任何內容/內部文字/初始化文字。  
  
## <a name="see-also"></a>另請參閱  
 [x:Arguments 指示詞](../../../docs/framework/xaml-services/x-arguments-directive.md)
