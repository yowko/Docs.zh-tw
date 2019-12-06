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
ms.openlocfilehash: 2e64c716ee85934bf02c016ee408b8e5f612a819
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837190"
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
|`object`|XAML 類型的物件元素宣告，由 CLR 泛型型別支援。 如果 `object` 參考的 XAML 型別不是來自預設的 XAML 命名空間，`object` 需要前置詞來表示 `object` 存在的 XAML 命名空間。|  
|`typeString`|將一個或多個 XAML 類型名稱宣告為字串的字串，可提供 CLR 泛型型別的類型引數。 如需其他語法注意事項，請參閱備註。|  
  
## <a name="remarks"></a>備註  
 在大部分情況下，做為 `typeString` 字串中的資訊專案使用的 XAML 型別會加上前置詞。 典型的 CLR 泛型條件約束類型（例如，<xref:System.Int32> 和 <xref:System.String>）來自 CLR 基類庫。 這些程式庫不會對應到一般架構特定的預設 XAML 命名空間，因此需要 XAML 用法的前置詞對應。  
  
 您可以使用逗號分隔符號來指定一個以上的 XAML 類型名稱。  
  
 如果泛型條件約束本身使用泛型型別，則嵌套的條件約束類型引數可以包含在括弧（）內。  
  
 請注意，這項 `x:TypeArguments` 定義是 .NET Framework XAML 服務和使用 CLR 支援所特有。 您可以在[\[MS-XAML\] 區段 5.3.11](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))中找到語言層級定義。  
  
## <a name="usage-examples"></a>使用方式範例  
 在這些範例中，假設已宣告下列 XAML 命名空間定義：  
  
```xaml  
xmlns:sys="clr-namespace:System;assembly=mscorlib"  
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
```  
  
### <a name="liststring"></a>列出\<字串 >  
 `<scg:List x:TypeArguments="sys:String" ...>` 使用 <xref:System.String> 型別引數具現化新的 <xref:System.Collections.Generic.List%601>。  
  
### <a name="dictionarystringstring"></a>字典\<字串，字串 >  
 `<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` 使用兩個 <xref:System.String> 型別引數具現化新的 <xref:System.Collections.Generic.Dictionary%602>。  
  
### <a name="queuekeyvaluepairstringstring"></a>佇列 < KeyValuePair\<字串，字串 > >  
 `<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` 具現化具有內部條件約束類型引數 <xref:System.String> 和 <xref:System.String>之 <xref:System.Collections.Generic.KeyValuePair%602> 條件約束的新 <xref:System.Collections.Generic.Queue%601>。  
  
## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a>XAML 2006 和 WPF 一般 XAML 用法  
 針對 XAML 2006 用法和 WPF 應用程式所使用的 XAML，一般會有下列限制： XAML 中的 `x:TypeArguments` 和一般類型使用方式。  
  
- 只有 XAML 檔案的根項目可以支援參考泛型型別的泛型 XAML 用法。  
  
- 根項目必須對應至具有至少一個型別引數的泛型型別。 例如 <xref:System.Windows.Navigation.PageFunction%601>。 頁面函式是 WPF 中 XAML 一般使用方式支援的主要案例。  
  
- 泛型的根項目 XAML 物件元素也必須使用 `x:Class`宣告部分類別。 即使定義 WPF 組建動作也是如此。  
  
- `x:TypeArguments` 無法參考嵌套的泛型條件約束。  
  
## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a>不含 WPF 3.0 或 WPF 3.5 相依性的 XAML 2009 或 XAML 2006  
 在 XAML 2006 或 XAML 2009 .NET Framework XAML 服務中，泛型 XAML 使用方式的 WPF 相關限制是寬鬆的。 您可以在 XAML 標記中，將泛型物件專案具現化，以支援型別系統和物件模型。  
  
 如果您使用 XAML 2009，而不是對應 CLR 基底型別來取得通用語言基本類型的 XAML 型別，您可以使用[通用 XAML 語言基本類型的內建型](built-in-types-for-common-xaml-language-primitives.md)別做為 `typeString`中的資訊專案。 例如，您可以宣告下列（未顯示前置詞對應，但 x 是 xaml 2009 的 xaml 語言 XAML 命名空間）：  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
 在 WPF 中，以 .NET Framework 4 為目標時，您可以搭配 `x:TypeArguments` 使用 XAML 2009 功能，但僅適用于鬆散的 XAML （不是以標記編譯的 XAML）。 WPF 之編譯標記的 XAML 和 BAML 形式的 XAML 目前不支援 XAML 2009 關鍵字和功能。 如果您需要標記編譯 XAML，您必須在「XAML 2006 和 WPF 一般 XAML 使用方式」一節中所述的限制下操作。  
  
## <a name="see-also"></a>請參閱

- [x:Class 指示詞](x-class-directive.md)
- [x:Type 標記延伸模組](x-type-markup-extension.md)
- [通用 XAML 語言基本類型的內建類型](built-in-types-for-common-xaml-language-primitives.md)
- [XAML 中的泛型](generics-in-xaml.md)
