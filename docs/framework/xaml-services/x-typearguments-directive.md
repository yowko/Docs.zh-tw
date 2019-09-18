---
title: x:TypeArguments 指示詞
ms.date: 03/30/2017
f1_keywords:
- x:TypeArguments
- xTypeArguments
- TypeArguments
helpviewer_keywords:
- x:TypeArguments attribute [XAML Services]
- TypeArguments attribute in XAML [XAML Services]
- XAML [XAML Services], x:TypeArguments attribute
ms.assetid: 86561058-d393-4a44-b5c3-993a4513ea74
ms.openlocfilehash: a2a960870d368e57272b3368e69eb38ebbe2ba5d
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053708"
---
# <a name="xtypearguments-directive"></a>x:TypeArguments 指示詞
將泛型的條件約束類型引數傳遞至泛型型別的處理函式。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```xaml  
<object x:TypeArguments="typeString" .../>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`object`|XAML 類型的物件元素宣告，由 CLR 泛型型別支援。 如果`object`參考的 xaml 類型不是來自預設的 xaml 命名空間， `object`則需要前置詞來`object`表示存在的 xaml 命名空間。|  
|`typeString`|將一個或多個 XAML 類型名稱宣告為字串的字串，可提供 CLR 泛型型別的類型引數。 如需其他語法注意事項，請參閱備註。|  
  
## <a name="remarks"></a>備註  
 在大部分情況下，做為`typeString`字串中的資訊專案使用的 XAML 型別會加上前置詞。 一般的 clr 泛型條件約束類型（ <xref:System.Int32>例如和<xref:System.String>）來自 clr 基類庫。 這些程式庫不會對應到一般架構特定的預設 XAML 命名空間，因此需要 XAML 用法的前置詞對應。  
  
 您可以使用逗號分隔符號來指定一個以上的 XAML 類型名稱。  
  
 如果泛型條件約束本身使用泛型型別，則嵌套的條件約束類型引數可以包含在括弧（）內。  
  
 請注意，的`x:TypeArguments`這個定義是 .NET Framework XAML 服務和使用 CLR 支援所特有。 您可以在[ \[5.3.11\] ](https://go.microsoft.com/fwlink/?LinkId=114525)中找到語言層級的定義。  
  
## <a name="usage-examples"></a>使用範例  
 在這些範例中，假設已宣告下列 XAML 命名空間定義：  
  
```xaml  
xmlns:sys="clr-namespace:System;assembly=mscorlib"  
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
```  
  
### <a name="liststring"></a>清單\<字串 >  
 `<scg:List x:TypeArguments="sys:String" ...>`使用型別<xref:System.Collections.Generic.List%601>引數具現化新的。 <xref:System.String>  
  
### <a name="dictionarystringstring"></a>字典\<字串，字串 >  
 `<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>`使用兩個<xref:System.Collections.Generic.Dictionary%602> <xref:System.String>型別引數具現化新的。  
  
### <a name="queuekeyvaluepairstringstring"></a>佇列 < KeyValuePair\<字串，字串 > >  
 `<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>`具現化<xref:System.Collections.Generic.Queue%601>具有內部條件約束類型<xref:System.Collections.Generic.KeyValuePair%602>引數<xref:System.String>和<xref:System.String>之條件約束的新。  
  
## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a>XAML 2006 和 WPF 一般 XAML 用法  
 針對 xaml 2006 用法和 WPF 應用程式所使用的 xaml，一般會針對`x:TypeArguments`和 xaml 中的泛型型別使用方式存在下列限制：  
  
- 只有 XAML 檔案的根項目可以支援參考泛型型別的泛型 XAML 用法。  
  
- 根項目必須對應至具有至少一個型別引數的泛型型別。 例如 <xref:System.Windows.Navigation.PageFunction%601>。 頁面函式是 WPF 中 XAML 一般使用方式支援的主要案例。  
  
- 泛型的根項目 XAML 物件元素也必須使用`x:Class`宣告部分類別。 即使定義 WPF 組建動作也是如此。  
  
- `x:TypeArguments`無法參考嵌套的泛型條件約束。  
  
## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a>不含 WPF 3.0 或 WPF 3.5 相依性的 XAML 2009 或 XAML 2006  
 在 XAML 2006 或 XAML 2009 .NET Framework XAML 服務中，泛型 XAML 使用方式的 WPF 相關限制是寬鬆的。 您可以在 XAML 標記中，將泛型物件專案具現化，以支援型別系統和物件模型。  
  
 如果您使用 XAML 2009，而不是對應 CLR 基底型別來取得通用語言基本類型的 XAML 型別，您可以使用[通用 XAML 語言基本類型的內建型](built-in-types-for-common-xaml-language-primitives.md)別做為中`typeString`的資訊專案。 例如，您可以宣告下列（未顯示前置詞對應，但 x 是 xaml 2009 的 xaml 語言 XAML 命名空間）：  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
 在 WPF 中，以 .NET Framework 4 為`x:TypeArguments`目標時，您可以使用 XAML 2009 功能搭配，但僅適用于鬆散的 xaml （不是以標記編譯的 xaml）。 WPF 之編譯標記的 XAML 和 BAML 形式的 XAML 目前不支援 XAML 2009 關鍵字和功能。 如果您需要標記編譯 XAML，您必須在「XAML 2006 和 WPF 一般 XAML 使用方式」一節中所述的限制下操作。  
  
## <a name="see-also"></a>另請參閱

- [x:Class 指示詞](x-class-directive.md)
- [x:Type 標記延伸模組](x-type-markup-extension.md)
- [通用 XAML 語言基本類型的內建類型](built-in-types-for-common-xaml-language-primitives.md)
- [XAML 中的泛型](generics-in-xaml.md)
