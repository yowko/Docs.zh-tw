---
title: "{} 逸出序列標記延伸"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- '{}'
helpviewer_keywords:
- XAML [XAML Services], quotation mark (")
- '{} escape sequence [XAML Services]'
- XAML [XAML Services], {} escape sequence
- XAML [XAML Services], escape sequence
- quotation mark (") [XAML Services]
- escape sequence [XAML Services]
ms.assetid: 3ce3e2ad-a868-43f9-9c98-b29561cb146e
caps.latest.revision: 
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8419a1e89d5e94b9868b0fd1fb81540253efca5d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="-escape-sequence--markup-extension"></a>{} 逸出序列 / 標記延伸
提供 XAML 逸出序列的屬性值。 逸出序列必須解譯成常值屬性中讓後續的值。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```xml  
<object property="{} literalValue" .../>  
```  
  
## <a name="xaml-property-element-usage"></a>XAML 屬性項目用法  
  
```  
<object>  
  <object.property>  
    {} literalValue  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|*literalValue*|常值字串的逸出序列。 這個字串通常包含開啟或關閉括號 （{或}）。|  
  
## <a name="remarks"></a>備註  
 使用逸出序列 （{}），因此可以當做常值字元，在 XAML 中使用左大括弧 （{}）。  
  
 XAML 讀取器通常會使用左大括號 （{}） 來代表標記延伸的進入點; 不過，他們第一次檢查以判斷它是否右大括號 （}） 的下一個字元。 只有當兩個大括號 （{） 相鄰，則會視為逸出序列。  
  
 如果遇到逸出序列時，XAML 讀取器應該處理字串的其餘部分做為字串。 不過，如果逸出序列套用至具有型別轉換子的成員，字串可能進行類型轉換時將它解譯 XAML 寫入器。  
  
 逸出序列不是標記延伸，而且不受類別。 不過，它是 （包括自訂 XAML 讀取器） 的 XAML 讀取器應該遵循的慣例。  
  
 引號 （"） 不能以這種方式的逸出序列。 如果您需要設定為非屬性的屬性值的引號，使用屬性項目語法，將引號字串內的屬性項目，或使用 XML 字元實體。 內容屬性，引號可以是完整的內容。  
  
 指定必須在 XAML 標記延伸位置可能會出現的位置中包含命名空間限定詞的 XML 類型時，就經常需要逸出序列 （{}）。 這包括開頭的 XAML 屬性值，並在標記延伸、 等號 （=） 後面。 下列範例會顯示在 XAML 屬性值的開頭的 XML 命名空間的逸出序列。  
  
 [!code-xaml[XLINQExample#StackPanelResources](../../../samples/snippets/csharp/VS_Snippets_Wpf/XLinqExample/CSharp/Window1.xaml#stackpanelresources)]  
  
## <a name="see-also"></a>請參閱  
 [XAML 的類型轉換子和標記延伸](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md)  
 [XML 字元實體和 XAML](../../../docs/framework/xaml-services/xml-character-entities-and-xaml.md)
