---
title: 適用於類型轉換子和標記延伸的服務內容
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], type converter services how-to
ms.assetid: b4dad00f-03da-4579-a4e9-d8d72d2ccbce
ms.openlocfilehash: 59c4385eb4df8c622be6164cdb0a1a911c445ca8
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071658"
---
# <a name="service-contexts-available-to-type-converters-and-markup-extensions"></a>適用於類型轉換子和標記延伸的服務內容
在撰寫類型來支援使用類型轉換子和標記延伸時，通常必須先知道會在標記或周圍物件圖形結構中的何處使用類型轉換子和標記延伸。 要有這些資訊，才能正確地具現化所提供的物件，或是在物件圖形中建立對現有物件的物件參考。 使用 .NET XAML 服務時,可能需要的上下文將作為一系列服務介面公開。 類型轉換子或標記延伸支援程式碼可以使用從 <xref:System.Xaml.XamlObjectWriter> 或相關類型傳來的可用服務提供者內容，來查詢服務。 XAML 結構描述內容可透過這類服務直接提供。 本主題說明如何透過值轉換器實作存取服務內容，並列出通常可用的服務及其角色。

## <a name="obtaining-services"></a>取得服務

身為值轉換器的實作者，您通常會需要存取套用值轉換器之特定類型的內容。 此上下文可能包括諸如活動 XAML 架構上下文、訪問 XAML 架構上下文和 XAML 物件編寫器提供的類型映射系統等資訊。 標記延伸或類型轉換子實作適用的可用服務，會透過每個虛擬方法之簽章中的內容參數來表示。 不論如何，您都會在內容中實作 <xref:System.IServiceProvider> ，並且可以呼叫 <xref:System.IServiceProvider.GetService%2A?displayProperty=nameWithType> 來要求服務。

## <a name="services-for-a-markup-extension"></a>標記延伸適用的服務

<xref:System.Windows.Markup.MarkupExtension> 只有一種虛擬方法，那就是 <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>。 輸入 `serviceProvider` 參數是在 XAML 處理器呼叫標記延伸時，用以向實作表示服務的方式。 下列虛擬程式碼示範標記延伸實作如何在其 <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>中查詢服務：

```csharp
public override object ProvideValue(IServiceProvider serviceProvider)
{
...
    // Get the IXamlTypeResolver from the service provider
    if (serviceProvider == null)
    {
        throw new ArgumentNullException("serviceProvider");
    }
    IXamlTypeResolver xamlTypeResolver = serviceProvider.GetService(typeof(IXamlTypeResolver)) as IXamlTypeResolver;
    if (xamlTypeResolver == null)
   {
        throw new ArgumentException("IXamlTypeResolver"));
    }
...
}
```

## <a name="services-for-a-type-converter"></a>類型轉換器適用的服務

<xref:System.ComponentModel.TypeConverter> 有四個使用服務內容並支援使用 XAML 的虛擬方法。 每個方法都會傳遞輸入 `context` 參數。 這個參數屬於 <xref:System.ComponentModel.ITypeDescriptorContext>類型，但該介面繼承自 <xref:System.IServiceProvider>，因此類型轉換器實作會有 <xref:System.IServiceProvider.GetService%2A> 方法可以使用。

下列虛擬程式碼示範用於 XAML 的類型轉換子實作如何在其中一個覆寫 (在本例中為 <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>) 中查詢服務：

```csharp
public override object ConvertFrom(ITypeDescriptorContext typeDescriptorContext,
  CultureInfo cultureInfo,
  object source)
{
    IRootObjectProvider rootProvider = typeDescriptorContext.GetService(typeof(IRootObjectProvider)) as IRootObjectProvider;
    if (rootProvider != null && source is String)
    {
        //return something, else ...
    }
    throw GetConvertFromException(source);
}
```

## <a name="services-for-a-value-serializer"></a>值序列化程式適用的服務

針對值序列化程式內容，您會使用 <xref:System.Windows.Markup.ValueSerializer> 類別專屬的服務提供者類型 <xref:System.Windows.Markup.IValueSerializerContext>。 該內容會傳遞給四個 <xref:System.Windows.Markup.ValueSerializer> 虛擬方法的覆寫。 呼叫該內容中的 <xref:System.IServiceProvider.GetService%2A> ，即可取得服務。

## <a name="using-the-xaml-service-provider-contexts"></a>使用 XAML 服務提供者內容

訪問<xref:System.IServiceProvider.GetService%2A>可用於標記擴展或類型轉換器的 XAML 服務的服務提供者作為內部類實現,僅透過介面進行曝光,以及如何將其傳遞到相關上下文中。 每當預設的 .NET XAML 服務中的 XAML 處理操作載入路徑或儲存路徑的實現呼叫需要服務上下文的相關標記擴展或類型轉換器方法時,都會傳遞此內部物件。 系統服務內容會根據當時的情況提供 `MarkupExtensionContext` 或 `TextSyntaxContext`，但這兩個類別的內容則是內部資訊。 您與這些類別進行的互動，僅限於透過 <xref:System.IServiceProvider.GetService%2A>向類別要求服務。

## <a name="available-services-from-the-net-xaml-service-context"></a>來自 .NET XAML 服務內容的服務

.NET XAML 服務為標記擴展、類型轉換器、值序列化器和可能的其他用途定義服務。 下列各節分別說明這些服務，並提供如何在實作中使用這些服務的相關指引。

### <a name="iserviceprovider"></a>IServiceProvider

**參考文件**:<xref:System.IServiceProvider>

**與:**.NET 中基於服務的基礎結構的基本操作,以便您可以呼<xref:System.IServiceProvider.GetService%2A?displayProperty=nameWithType>叫 。

### <a name="itypedescriptorcontext"></a>ITypeDescriptorContext

**參考文件**:<xref:System.ComponentModel.ITypeDescriptorContext>

衍生自 <xref:System.IServiceProvider>。 這個類別代表標準 <xref:System.ComponentModel.TypeConverter> 簽章中的內容； <xref:System.ComponentModel.TypeConverter> 是自 .NET Framework 1.0 開始便已存在的類別。 它比 XAML 和 XAML <xref:System.ComponentModel.TypeConverter> 情節更早用於字串-值類型轉換。 在 .NET XAML 服務<xref:System.ComponentModel.TypeConverter>上下文中 ,將顯式實現 這個明確實作的行為會讓呼叫端知道， <xref:System.ComponentModel.ITypeDescriptorContext> API 與 XAML 類型系統無關，或者與從 XAML 讀取或寫入物件無關。 <xref:System.ComponentModel.ITypeDescriptorContext.Container%2A><xref:System.ComponentModel.ITypeDescriptorContext.Instance%2A>,通常<xref:System.ComponentModel.ITypeDescriptorContext.PropertyDescriptor%2A>從 .NET XAML 服務`null`上下文返回 。

### <a name="ivalueserializercontext"></a>IValueSerializerContext

**參考文件**:<xref:System.Windows.Markup.IValueSerializerContext>

衍生自 <xref:System.ComponentModel.ITypeDescriptorContext> ，也依賴明確實作來抑制與 XAML 類型系統有關的錯誤假設。 支援 <xref:System.Windows.Markup.ValueSerializer>上的靜態查閱協助方法。

### <a name="ixamltyperesolver"></a>IXamlTypeResolver

**參考文件**:<xref:System.Windows.Markup.IXamlTypeResolver>

**T:System.Xaml.IDestinationTypeProvider**  <xref:System.Windows.Markup> 命名空間、System.Xaml 組件

適用於：**T:System.Xaml.IDestinationTypeProvider** 載入路徑情節，以及與 XAML 結構描述內容的互動

**服務 API：**  <xref:System.Windows.Markup.IXamlTypeResolver.Resolve%2A>

可能會影響 XAML 寫入器在物件圖形中建構 CLR 物件時，需要進行的 XAML 對 CLR 類型對應。 <xref:System.Windows.Markup.IXamlTypeResolver.Resolve%2A> 會處理與 XAML 類型名稱 (<xref:System.Xaml.XamlType.Name%2A?displayProperty=nameWithType>) 對應的字串 (這個字串可能含限定前置詞)，然後傳回 CLR <xref:System.Type>。 解析類型的作業通常高度仰賴 XAML 結構描述內容。 只有 XAML 結構描述內容才可辨識已載入哪些組件，以及進行類型解析時可以或應該存取哪些組件。

### <a name="iuricontext"></a>IUriContext

**參考文件**:<xref:System.Windows.Markup.IUriContext>

**T:System.Xaml.IDestinationTypeProvider**  <xref:System.Windows.Markup> 命名空間、System.Xaml 組件

**T:System.Xaml.IDestinationTypeProvider** 成員值 (URI 或 `x:Uri` 值) 的載入路徑和儲存路徑處理。

**服務 API：**  <xref:System.Windows.Markup.IUriContext.BaseUri%2A>

這項服務會報告全域可用的根 URI (如果有的話)。 根 URI 可用來將相對 URI 解析成絕對 URI，或將絕對 URI 解析成相對 URI。 這個情節主要與由特定架構，或由架構中常用根項目類別的功能所公開的應用程式服務有關。 基底 URI 可建立為 XAML 讀取器設定，接著傳遞至 XAML 物件寫入器，再由這項服務報告。

### <a name="iambientprovider"></a>IAmbientProvider

**參考文件**:<xref:System.Xaml.IAmbientProvider>

**T:System.Xaml.IDestinationTypeProvider**  <xref:System.Xaml> 命名空間、System.Xaml 組件

適用於：**T:System.Xaml.IDestinationTypeProvider** 載入路徑處理和類型查閱的延後或最佳化。

**服務 API:**  <xref:System.Xaml.IAmbientProvider.GetAllAmbientValues%2A>, 其他三個。

XAML 中的環境概念是一種將類型的特定成員標記為環境成員的技術。 或者，您也可以將類型設為環境類型，使所有包含該類型之執行個體的屬性值都被視為環境屬性。 在物件圖形中 XAML 節點資料流更深層和做為子系的標記延伸或類型轉換器，可以在載入時存取環境屬性或類型執行個體，或是在儲存時使用環境結構的資訊。 這可能會影響其他服務 (例如 <xref:System.Windows.Markup.IXamlTypeResolver> 或 `x:Type`) 的類型解析作業所需的限定程度。 另請參閱 <xref:System.Xaml.AmbientPropertyValue>。

### <a name="ixamlschemacontextprovider"></a>IXamlSchemaContextProvider

**參考文件**:<xref:System.Xaml.IXamlSchemaContextProvider>

**T:System.Xaml.IDestinationTypeProvider**  <xref:System.Xaml> 命名空間、System.Xaml 組件

適用於：**T:System.Xaml.IDestinationTypeProvider** 載入路徑，以及任何必須將 XAML 類型解析成支援類型的作業。

**服務 API：**  <xref:System.Xaml.IXamlSchemaContextProvider.SchemaContext%2A>

所有延後載入作業都需要 XAML 結構描述內容，因為相同的結構描述內容必須套用至延後的區域，才能整合延後的內容。 如需 XAML 結構描述內容所扮演角色的詳細資訊，請參閱 [T:System.Xaml.IDestinationTypeProvider](../../../api/index.md)。

### <a name="irootobjectprovider"></a>IRootObjectProvider

**參考文件**:<xref:System.Xaml.IRootObjectProvider>

**T:System.Xaml.IDestinationTypeProvider**  <xref:System.Xaml> 命名空間、System.Xaml 組件

適用於：**T:System.Xaml.IDestinationTypeProvider** 載入路徑。

**服務 API：**  <xref:System.Xaml.IRootObjectProvider.RootObject%2A>

這項服務與由特定架構，或由架構中常用根項目類別的功能所公開的應用程式服務有關。 連接程式碼後置和事件連接，就是一種需要取得根物件的情節。 例如， `x:Class` 的 WPF 實作可用來編譯標記，以及連接在 XAML 標記中的任何其他位置找到的任何事件處理常式屬性。 進行標記編譯時，標記和程式碼後置定義部分類別的連接點是在根項目。

### <a name="ixamlnamespaceresolver"></a>IXamlNamespaceResolver

**參考文件**:<xref:System.Xaml.IXamlNamespaceResolver>

**T:System.Xaml.IDestinationTypeProvider**  <xref:System.Xaml> 命名空間、System.Xaml 組件

適用於：**T:System.Xaml.IDestinationTypeProvider** 載入路徑、儲存路徑。

**服務 API:**<xref:System.Xaml.IXamlNamespaceResolver.GetNamespace%2A>用於載<xref:System.Xaml.IXamlNamespaceResolver.GetNamespacePrefixes%2A>入路徑 ,用於保存路徑。

<xref:System.Xaml.IXamlNamespaceResolver> 是一項服務，可根據 XAML 命名空間的前置詞，傳回 XAML 命名空間在起始 XAML 標記中的識別項 / URI。

### <a name="iprovidevaluetarget"></a>IProvideValueTarget

**參考文件**:<xref:System.Windows.Markup.IProvideValueTarget>

**T:System.Xaml.IDestinationTypeProvider**  <xref:System.Windows.Markup> 命名空間、System.Xaml 組件

適用於：**T:System.Xaml.IDestinationTypeProvider** 載入路徑和儲存路徑。

**服務 API:** <xref:System.Windows.Markup.IProvideValueTarget.TargetObject%2A> <xref:System.Windows.Markup.IProvideValueTarget.TargetProperty%2A>.  

<xref:System.Windows.Markup.IProvideValueTarget> 可讓類型轉換器或標記延伸取得有關其在載入時之作用位置的內容。 實作可以使用這個內容讓某個使用方式無效。 例如，WPF 在其某些標記延伸 (例如 <xref:System.Windows.DynamicResourceExtension>) 內具有邏輯。 這個邏輯會檢查 <xref:System.Windows.Markup.IProvideValueTarget.TargetProperty%2A> ，以確定該延伸只會用來設定相依性屬性 (或其他非相依性屬性的簡短清單)。

### <a name="ixamlnameresolver"></a>IXamlNameResolver

**參考文件**:<xref:System.Xaml.IXamlNameResolver>

**T:System.Xaml.IDestinationTypeProvider**  <xref:System.Xaml> 命名空間、System.Xaml 組件

**與:** 載入路徑物件圖定義,解析由`x:Name``x:Reference`或特定於框架的技術標識的物件。

**T:System.Xaml.IDestinationTypeProvider**  <xref:System.Xaml.IXamlNameResolver.Resolve%2A>；其他適用於進階情節 (例如處理向前參考) 的 API。

.NET XAML`x:Reference`服務的處理實現依賴於此服務。 特定架構或是支援該架構的工具，會使用這項服務來處理 `x:Name` 或是已用<xref:System.Windows.Markup.RuntimeNamePropertyAttribute> 屬性化(Attributed) 的對等屬性 (Property)。

### <a name="idestinationtypeprovider"></a>IDestinationTypeProvider

**參考文件**:<xref:System.Xaml.IDestinationTypeProvider>

**T:System.Xaml.IDestinationTypeProvider**  <xref:System.Xaml> 命名空間、System.Xaml 組件

適用於：**T:System.Xaml.IDestinationTypeProvider** 間接 CLR 類型資訊的載入路徑解析。

**服務 API：** <xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A>

如需詳細資訊，請參閱 <xref:System.Xaml.IDestinationTypeProvider>。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Markup.MarkupExtension>
- <xref:System.Xaml.XamlObjectWriter>
- [XAML 標記延伸概觀](markup-extensions-overview.md)
- [XAML 類型轉換子概觀](type-converters-overview.md)
