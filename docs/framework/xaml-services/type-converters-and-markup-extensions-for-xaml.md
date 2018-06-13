---
title: XAML 的類型轉換子和標記延伸
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], type converter services
- XAML [XAML Services], value converters
- XAML [XAML Services], markup extension services
- value converters for XAML [XAML Services]
- XAML [XAML Services], service context
ms.assetid: db07a952-05ce-4aa4-b6f9-aac7397d0326
ms.openlocfilehash: 0c9cb7e87416860dda98df0da967ffbc070bc270
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565859"
---
# <a name="type-converters-and-markup-extensions-for-xaml"></a>XAML 的類型轉換子和標記延伸
類型轉換器和標記延伸是 XAML 類型系統和 XAML 寫入器用以產生物件圖形元件的兩項技術。 雖然兩者共用某些特性，但類型轉換器和標記延伸在 XAML 節點資料流中會以不同的方式表示。 在本文件集中，有時會將類型轉換器、標記延伸和類似的建構統稱為值轉換器。  
  
<a name="value_converters"></a>   
## <a name="value-converters"></a>值轉換器  
 在 XAML 中，值轉換器可用於多種情節。 下列清單顯示 XAML 中不同類型的值轉換器：  
  
-   類型轉換器  
  
-   標記延伸  
  
-   值序列化程式  
  
-   為 XAML 文字語法提供邏輯的相關類別或支援類別  
  
<a name="type_converters"></a>   
## <a name="type-converters"></a>類型轉換器  
 在 .NET Framework XAML 服務定義中，類型轉換器是衍生自 CLR <xref:System.ComponentModel.TypeConverter> 類別的類別。 <xref:System.ComponentModel.TypeConverter> 是之前的 Microsoft.NET Framework XAML 才會存在的類別。 其原始用途是為了支援 [!INCLUDE[TLA2#tla_ide](../../../includes/tla2sharptla-ide-md.md)] 屬性的屬性視窗和類似的文字編輯表示。 .NET Framework 中引進的 XAML 使用 <xref:System.ComponentModel.TypeConverter> ，將文字語法 (如屬性值或 XAML 值節點中的文字語法) 轉換成物件。 <xref:System.ComponentModel.TypeConverter> 也可用來將物件值序列化為文字語法。 <xref:System.ComponentModel.TypeConverter> 也在 Windows Presentation Foundation (WPF) 和 Windows Communication Foundation (WCF) 和先前的架構特定 XAML 實作中使用。 如需在 XAML 中 <xref:System.ComponentModel.TypeConverter> 的詳細資訊，請參閱 [Type Converters for XAML Overview](../../../docs/framework/xaml-services/type-converters-for-xaml-overview.md)。  
  
<a name="markup_extensions"></a>   
## <a name="markup-extensions"></a>標記延伸  
 在 .NET Framework XAML 服務實作中，標記延伸是衍生自 <xref:System.Windows.Markup.MarkupExtension> 類別的類別。 標記延伸是一種概念，在這種形式下的標記都是源自 XAML 語言。 您可以將標記延伸視為類似可延伸的逸出序列，這個序列會呼叫服務類別來提供其邏輯。 就標記而言，XAML 處理器普遍會將文字字串中以左大括號 ({) 開頭的文字序列視為標記延伸。  
  
 標記延伸與類型轉換器不同。 類型轉換器通常與類型或成員相關聯。 當物件圖形建立或序列化作業遇到與這些實體關聯的文字語法時，即會叫用類型轉換器。  
  
 標記延伸與單一支援服務類別相關聯，但可套用至任何成員值。 (不過，您可以透過服務內容實作標記延伸，刻意限制只有特定成員或目的類型才能使用)。標記延伸可覆寫類型轉換器關聯。 或者，您可以使用標記延伸，為原本不支援文字語法的成員指定屬性值。  
  
 如需 XAML 之標記延伸實作模式的詳細資訊，請參閱 [Markup Extensions for XAML Overview](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md)。  
  
> [!NOTE]
>  <xref:System.Windows.Markup.MarkupExtension> 和 <xref:System.Windows.Markup.ValueSerializer> 類型都在 <xref:System.Windows.Markup> 命名空間中，而不在 <xref:System.Xaml> 命名空間中。 這不表示這些類型專屬於否則填入包含字串的 CLR 命名空間的 WPF 或 Windows Form 技術`Windows`。 <xref:System.Windows.Markup.MarkupExtension> 和 <xref:System.Windows.Markup.ValueSerializer> 位於 System.Xaml 組件中，並且沒有特定架構相依性。 這些類型在 [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)] 存在於 CLR 命名空間中，到了 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 仍存在於 CLR 命名空間中，這是為了避免破壞現有 WPF 專案中的參考。 如需詳細資訊，請參閱 [Types Migrated from WPF to System.Xaml](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)。  
  
<a name="value_serializers"></a>   
## <a name="value-serializers"></a>值序列化程式  
 <xref:System.Windows.Markup.ValueSerializer> 是為了以最佳方式將物件轉換成字串而特製化的類型轉換器。 XAML 的 <xref:System.Windows.Markup.ValueSerializer> 可能完全無法實作 `ConvertFrom` 方法。 <xref:System.Windows.Markup.ValueSerializer> 實作取得服務的方式與 <xref:System.ComponentModel.TypeConverter> 實作類似。 虛擬方法會提供輸入 `context` 參數。 `context` 參數屬於 <xref:System.Windows.Markup.IValueSerializerContext>類型，該類型繼承自 <xref:System.IServiceProvider> 介面並具有 <xref:System.IServiceProvider.GetService%2A> 方法。  
  
 在 XAML 類型系統中，以及針對使用 XAML 節點迴圈處理序列化的 XAML 寫入器實作，與類型或成員關聯的值轉換器會由其專屬的 <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> 屬性來報告。 這對執行序列化的 XAML 寫入器所代表的意義是，如果有 <xref:System.Xaml.XamlType.TypeConverter%2A?displayProperty=nameWithType> 和 <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType>，則應針對載入路徑使用類型轉換器，並應針對儲存路徑使用值序列化程式。 如果有 <xref:System.Xaml.XamlType.TypeConverter%2A?displayProperty=nameWithType> 但 <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> 為 `null`，也應針對儲存路徑使用類型轉換器。  
  
<a name="other_value_converters"></a>   
## <a name="other-value-converters"></a>其他值轉換器  
 值轉換器可延伸至超出類型轉換器或標記延伸的特定模式。 但若要進行這項自訂，還必須重新定義 .NET Framework XAML 服務所提供的 XAML 類型系統。 現有 XAML 類型系統具有適用於類型轉換子、標記延伸和值序列化程式的表示和報告系統，但沒有適用於自訂形式之值轉換的表示和報告系統。 如果您想要建立自訂值轉換器，請使用 <xref:System.Xaml.Schema.XamlValueConverter%601> 類型。  
  
<a name="type_converters_and_markup_extensions_in_combination"></a>   
## <a name="type-converters-and-markup-extensions-in-combination"></a>類型轉換器和標記延伸的組合  
 標記延伸和類型轉換器會用於 XAML 中的不同情況。 儘管有適合標記延伸使用的內容，但標記延伸負責提供值的屬性類型轉換行為在標記延伸實作中通常不會遭到檢查。 換句話說，即使標記延伸傳回文字字串做為其 `ProvideValue` 輸出，也不會在該字串上，叫用套用至特定屬性或屬性值類型的類型轉換行為。 一般來說，標記延伸的目的是在未涉及任何類型轉換器的情況下，處理字串及傳回物件。  
  
<a name="service_context_for_a_value_converter"></a>   
## <a name="service-context-for-a-value-converter"></a>值轉換器的服務內容  
 當您實作值轉換器時，您通常會需要存取套用值轉換器的內容。 這個內容稱為服務內容。 服務內容可能包含作用中的 XAML 結構描述內容、XAML 結構描述內容和 XAML 物件寫入器提供之類型對應系統的存取等資訊。 如需值轉換器的可用服務內容，以及如何存取服務內容可能提供之服務的詳細資訊，請參閱 [Service Contexts Available to Type Converters and Markup Extensions](../../../docs/framework/xaml-services/service-contexts-available-to-type-converters-and-markup-extensions.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Markup.MarkupExtension>  
 <xref:System.Xaml.XamlObjectWriter>  
 [XAML 標記延伸概觀](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md)  
 [XAML 類型轉換子概觀](../../../docs/framework/xaml-services/type-converters-for-xaml-overview.md)  
 [適用於類型轉換子和標記延伸的服務內容](../../../docs/framework/xaml-services/service-contexts-available-to-type-converters-and-markup-extensions.md)
