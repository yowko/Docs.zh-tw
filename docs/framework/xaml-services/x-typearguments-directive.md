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
ms.openlocfilehash: 94f09bdd3b6ee0b180e30bab0993f0b4e41730ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566856"
---
# <a name="xtypearguments-directive"></a>x:TypeArguments 指示詞
將型別引數的泛型型別建構函式的泛型條件約束的傳遞。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```xaml  
<object x:TypeArguments="typeString" .../>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`object`|屬於 XAML 型別，由 CLR 泛型型別所支援物件項目宣告。 如果`object`指的不是是來自預設 XAML 命名空間中，將 XAML 類型`object`需要指出 XAML 命名空間的前置詞其中`object`存在。|  
|`typeString`|字串，其中會宣告一個或多個 XAML 類型名稱為字串，其中提供 CLR 泛型類型的型別引數。 如需其他的語法資訊，請參閱 < 備註 >。|  
  
## <a name="remarks"></a>備註  
 在大部分情況下，XAML 類型做為中的資訊項目`typeString`前置詞字串。 一般類型的 CLR 泛型條件約束 (例如，<xref:System.Int32>和<xref:System.String>) 來自 CLR 基底類別程式庫。 這些程式庫無法對應到一般架構特定的預設 XAML 命名空間，而且因此，需要 XAML 用法的前置詞對應。  
  
 您可以使用逗號分隔符號來指定一個以上的 XAML 型別名稱。  
  
 泛型條件約束本身會使用泛型型別，如果巢狀的條件約束的型別引數可以包含括號 （）。  
  
 請注意，此定義`x:TypeArguments`專屬於.NET Framework XAML 服務，使用 CLR 支援。 可以在中找到的語言層級定義[ \[MS-XAML\]區段 5.3.11](http://go.microsoft.com/fwlink/?LinkId=114525)。  
  
## <a name="usage-examples"></a>使用範例  
 這些範例中，假設宣告 XAML 命名空間定義如下：  
  
```  
xmlns:sys="clr-namespace:System;assembly=mscorlib"  
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
```  
  
### <a name="liststring"></a>清單\<字串 >  
 `<scg:List x:TypeArguments="sys:String" ...>` 具現化新<xref:System.Collections.Generic.List%601>與<xref:System.String>型別引數。  
  
### <a name="dictionarystringstring"></a>字典\<字串、 字串 >  
 `<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` 具現化新<xref:System.Collections.Generic.Dictionary%602>具有兩個<xref:System.String>型別引數。  
  
### <a name="queuekeyvaluepairstringstring"></a>佇列 < KeyValuePair\<String，String >>  
 `<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` 具現化新<xref:System.Collections.Generic.Queue%601>，有條件約束的<xref:System.Collections.Generic.KeyValuePair%602>內部條件約束的型別引數<xref:System.String>和<xref:System.String>。  
  
## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a>XAML 2006 和 WPF XAML 一般使用方式  
 如需 XAML 2006 使用量和使用 WPF 應用程式的 XAML，有下列限制`x:TypeArguments`以及從 XAML 中一般的泛型型別使用方式：  
  
-   只有 XAML 檔案的根項目可以支援一般的 XAML 用法參考泛型型別。  
  
-   根項目必須具有至少一個型別引數的泛型型別對應。 範例是<xref:System.Windows.Navigation.PageFunction%601>。 頁面函式會針對 XAML 泛型使用量支援 WPF 中的主要案例。  
  
-   泛型的根項目 XAML 物件項目也必須宣告部分類別，使用`x:Class`。 即使定義 WPF 建置動作，也是如此。  
  
-   `x:TypeArguments` 無法參考巢狀泛型條件約束。  
  
## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a>XAML 2009 或不含 WPF 3.0 或 3.5 WPF XAML 2006 相依性  
 在.NET Framework XAML 服務 XAML 2006 或 XAML 2009 被放寬泛型的 XAML 用法的 WPF 相關限制。 您可以具現化的支援類型系統和物件模型可支援的 XAML 標記中的任何位置的泛用的物件項目。  
  
 如果您使用 XAML 2009 而不是將 CLR 對應基底類型，以取得通用語言基本類型的 XAML 型別，您可以使用[通用 XAML 語言基本類型的內建類型](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md)為中的資訊項目`typeString`。 例如，您可以宣告下列 （前置詞對應不會顯示，而 x 是 XAML 語言 XAML 命名空間，XAML 2009）：  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
 在 WPF 中，並為目標時[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]，您可以使用 XAML 2009 功能與搭配`x:TypeArguments`但僅針對鬆散的 XAML (未標記編譯 XAML)。 WPF 之編譯標記的 XAML 和 BAML 形式的 XAML 目前不支援 XAML 2009 關鍵字和功能。 如果您需要以標記編譯 XAML，您必須以"XAML 2006 and WPF 泛型 XAML 使用方法 」 一節所述的限制來運作。  
  
## <a name="see-also"></a>另請參閱  
 [x:Class 指示詞](../../../docs/framework/xaml-services/x-class-directive.md)  
 [x:Type 標記延伸模組](../../../docs/framework/xaml-services/x-type-markup-extension.md)  
 [通用 XAML 語言基本類型的內建類型](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md)  
 [XAML 中的泛型](../../../docs/framework/xaml-services/generics-in-xaml.md)
