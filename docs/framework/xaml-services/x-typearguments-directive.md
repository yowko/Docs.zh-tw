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
ms.openlocfilehash: 28eda94914125f2c5849a471671c8e283475c82c
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2018
ms.locfileid: "44268821"
---
# <a name="xtypearguments-directive"></a>x:TypeArguments 指示詞
限制的傳遞類型泛型型別之建構函式的泛型引的數。  
  
## <a name="xaml-attribute-usage"></a>XAML Attribute Usage  
  
```xaml  
<object x:TypeArguments="typeString" .../>  
```  
  
## <a name="xaml-values"></a>XAML 值  
  
|||  
|-|-|  
|`object`|物件項目宣告的 XAML 型別，而由 CLR 的泛型型別。 如果`object`不是來自預設 XAML 命名空間中，XAML 型別是指`object`需要指出 XAML 命名空間的前置詞其中`object`存在。|  
|`typeString`|字串，其中會宣告一個或多個 XAML 類型名稱為字串，提供 CLR 的泛型類型的類型引數。 如需其他的語法資訊，請參閱 < 備註 >。|  
  
## <a name="remarks"></a>備註  
 在大部分情況下，XAML 類型做為中的資訊項目`typeString`前置詞字串。 一般類型的 CLR 的泛型條件約束 (例如<xref:System.Int32>和<xref:System.String>) 來自 CLR 基底類別庫。 這些程式庫不對應至典型架構專屬的預設 XAML 命名空間，且因此，如果需要前置詞對應的 XAML 用法。  
  
 您可以使用逗號分隔符號來指定一個以上的 XAML 型別名稱。  
  
 如果泛型條件約束本身會使用泛型型別，可以包含巢狀條件約束的型別引數的括號 （）。  
  
 請注意，此定義`x:TypeArguments`專屬於.NET Framework XAML 服務，使用 CLR 支援。 語言層級定義可在[ \[MS XAML\]一節 5.3.11](https://go.microsoft.com/fwlink/?LinkId=114525)。  
  
## <a name="usage-examples"></a>使用範例  
 如需這些範例中，假設宣告 XAML 命名空間定義如下：  
  
```  
xmlns:sys="clr-namespace:System;assembly=mscorlib"  
xmlns:scg="clr-namespace:System.Collections.Generic;assembly=mscorlib"  
```  
  
### <a name="liststring"></a>清單\<字串 >  
 `<scg:List x:TypeArguments="sys:String" ...>` 新具現化<xref:System.Collections.Generic.List%601>與<xref:System.String>型別引數。  
  
### <a name="dictionarystringstring"></a>字典\<字串，字串 >  
 `<scg:Dictionary x:TypeArguments="sys:String,sys:String" ...>` 新具現化<xref:System.Collections.Generic.Dictionary%602>具有兩個<xref:System.String>型別引數。  
  
### <a name="queuekeyvaluepairstringstring"></a>佇列 < KeyValuePair\<String，String >>  
 `<scg:Queue x:TypeArguments="scg:KeyValuePair(sys:String,sys:String)" ...>` 新具現化<xref:System.Collections.Generic.Queue%601>具有條件約束<xref:System.Collections.Generic.KeyValuePair%602>使用內部條件約束的型別引數<xref:System.String>和<xref:System.String>。  
  
## <a name="xaml-2006-and-wpf-generic-xaml-usages"></a>XAML 2006 和 WPF XAML 的一般使用方式  
 如需 XAML 2006 使用量和用於 WPF 應用程式的 XAML，有下列限制`x:TypeArguments`以及從 XAML 中一般的泛型型別使用方式：  
  
-   只有 XAML 檔案的根項目可以支援一般的 XAML 用途，參考泛型型別。  
  
-   根項目必須對應到至少一個類型引數的泛型型別。 例如， <xref:System.Windows.Navigation.PageFunction%601>。 頁面函式會將一般用途支援 XAML 在 WPF 中的主要案例。  
  
-   泛型的根項目的 XAML 物件項目也必須宣告部分類別，使用`x:Class`。 這是 true，即使定義 WPF 建置動作。  
  
-   `x:TypeArguments` 不能參考巢狀的泛型條件約束。  
  
## <a name="xaml-2009-or-xaml-2006-with-no-wpf-30-or-wpf-35-dependency"></a>XAML 2009 或不含 WPF 3.0 或 3.5 WPF 的 XAML 2006 相依性  
 在.NET Framework XAML 服務 XAML 2006 或 XAML 2009，一般 XAML 用途的 WPF 相關限制比較不嚴謹。 您可以具現化的支援型別系統和物件模型可支援 XAML 標記中的任何位置的一般物件項目。  
  
 如果您使用 XAML 2009 而不是將 CLR 對應基底型別，以取得通用語言基本類型的 XAML 型別，您可以使用[通用 XAML 語言基本類型的內建型別](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md)中的資訊項目`typeString`。 例如，您可以宣告下列 （前置詞對應不會顯示，而 x 是 XAML 2009 的 XAML 語言 XAML 命名空間）：  
  
```xaml  
<my:BusinessObject x:TypeArguments="x:String,x:Int32"/>  
```  
  
 在 WPF 中，並為目標時[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]，您可以使用 XAML 2009 功能，並搭配`x:TypeArguments`但只在鬆散的 XAML (未標記編譯的 XAML)。 WPF 之編譯標記的 XAML 和 BAML 形式的 XAML 目前不支援 XAML 2009 關鍵字和功能。 如果您需要以標記編譯 XAML，您必須在 「 XAML 2006 和 WPF 泛型 XAML 使用方式 」 一節所述的限制下進行操作。  
  
## <a name="see-also"></a>另請參閱  
 [x:Class 指示詞](../../../docs/framework/xaml-services/x-class-directive.md)  
 [x:Type 標記延伸模組](../../../docs/framework/xaml-services/x-type-markup-extension.md)  
 [通用 XAML 語言基本類型的內建類型](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md)  
 [XAML 中的泛型](../../../docs/framework/xaml-services/generics-in-xaml.md)
