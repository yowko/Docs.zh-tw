---
title: "Service Contexts Available to Type Converters and Markup Extensions | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "XAML [XAML Services], type converter services how-to"
ms.assetid: b4dad00f-03da-4579-a4e9-d8d72d2ccbce
caps.latest.revision: 13
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 13
---
# Service Contexts Available to Type Converters and Markup Extensions
在撰寫類型來支援使用類型轉換子和標記延伸時，通常必須先知道會在標記或周圍物件圖形結構中的何處使用類型轉換子和標記延伸。 要有這些資訊，才能正確地具現化所提供的物件，或是在物件圖形中建立對現有物件的物件參考。 使用 .NET Framework XAML 服務時，可能需要的內容會以一系列服務介面的形式公開。 類型轉換子或標記延伸支援程式碼可以使用從 <xref:System.Xaml.IDestinationTypeProvider> 或相關類型傳來的可用服務提供者內容，來查詢服務。 XAML 結構描述內容可透過這類服務直接提供。 本主題說明如何透過值轉換器實作存取服務內容，並列出通常可用的服務及其角色。  
  
<a name="obtaining_services"></a>   
## 取得服務  
 身為值轉換器的實作者，您通常會需要存取套用值轉換器之特定類型的內容。 這個內容可能包含作用中的 XAML 結構描述內容、XAML 結構描述內容和 XAML 物件寫入器提供之類型對應系統的存取等資訊。 標記延伸或類型轉換子實作適用的可用服務，會透過每個虛擬方法之簽章中的內容參數來表示。 不論如何，您都會在內容中實作 <xref:System.Xaml.IDestinationTypeProvider>，並且可以呼叫 <xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A> 來要求服務。  
  
<a name="services_for_a_markup_extension"></a>   
## 標記延伸適用的服務  
 <xref:System.Xaml.IDestinationTypeProvider> 只有一種虛擬方法，那就是 <xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A>。 輸入 <xref:System.Xaml.IDestinationTypeProvider> 參數是在 XAML 處理器呼叫標記延伸時，用以向實作表示服務的方式。 下列虛擬程式碼示範標記延伸實作如何在其 <xref:System.Xaml.IDestinationTypeProvider> 中查詢服務：  
  
```  
public override object ProvideValue(IServiceProvider serviceProvider) { ... // Get the IXamlTypeResolver from the service provider if (serviceProvider == null) { throw new ArgumentNullException("serviceProvider"); } IXamlTypeResolver xamlTypeResolver = serviceProvider.GetService(typeof(IXamlTypeResolver)) as IXamlTypeResolver; if (xamlTypeResolver == null) { throw new ArgumentException("IXamlTypeResolver")); } ... }  
```  
  
<a name="services_for_a_type_converter"></a>   
## 類型轉換器適用的服務  
 <xref:System.Xaml.IDestinationTypeProvider> 有四個使用服務內容並支援使用 XAML 的虛擬方法。 每個方法都會傳遞輸入 <xref:System.Xaml.IDestinationTypeProvider> 參數。 這個參數屬於 <xref:System.Xaml.IDestinationTypeProvider> 類型，但該介面繼承自 <xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A>，因此類型轉換器實作會有 `x:Reference` 方法可以使用。  
  
 下列虛擬程式碼示範用於 XAML 的類型轉換子實作如何在其中一個覆寫 \(在本例中為 <xref:System.Xaml.IDestinationTypeProvider>\) 中查詢服務：  
  
```  
public override object ConvertFrom(ITypeDescriptorContext typeDescriptorContext, CultureInfo cultureInfo, object source) { IRootObjectProvider rootProvider = typeDescriptorContext.GetService(typeof(IRootObjectProvider)) as IRootObjectProvider; if (rootProvider != null && source is String) { //return something, else ... } throw GetConvertFromException(source); }  
```  
  
<a name="services_for_a_value_serializer"></a>   
## 值序列化程式適用的服務  
 針對值序列化程式內容，您會使用 <xref:System.Xaml.IDestinationTypeProvider> 類別專屬的服務提供者類型 <xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A>。 該內容會傳遞給四個 <xref:System.Xaml.IDestinationTypeProvider> 虛擬方法的覆寫。 呼叫該內容中的 <xref:System.Xaml.IDestinationTypeProvider>，即可取得服務。  
  
<a name="using_the_xaml_service_provider_contexts"></a>   
## 使用 XAML 服務提供者內容  
 讓 <xref:System.Xaml.IDestinationTypeProvider> 得以存取可用之標記延伸或類型轉換器之 XAML 服務的服務提供者，會以內部類別的形式實作，而且僅會透過介面和在相關內容中用以傳遞服務提供者的管道來公開。 每當 .NET Framework XAML 服務預設實作之載入路徑或儲存路徑中的 XAML 處理作業，叫用需要服務內容的相關標記延伸或類型轉換器方法時，即會傳遞這個內部物件。 系統服務內容會根據當時的情況提供 <xref:System.Xaml.IDestinationTypeProvider> 或 <xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A>，但這兩個類別的內容則是內部資訊。 您與這些類別進行的互動，僅限於透過 <xref:System.Xaml.IDestinationTypeProvider> 向類別要求服務。  
  
<a name="available_systemxaml_services"></a>   
## .NET Framework XAML 服務內容提供的服務  
 .NET Framework XAML 服務定義標記延伸、類型轉換器、值序列化程式，以及其他可能適用的服務。 下列各節分別說明這些服務，並提供如何在實作中使用這些服務的相關指引。  
  
### IServiceProvider  
 參考文件<xref:System.Xaml.IDestinationTypeProvider>：<xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A>  
  
 適用於<xref:System.Xaml.IDestinationTypeProvider>：.NET Framework 中服務型基礎結構的基本作業，可讓您呼叫 <xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A>。  
  
### ITypeDescriptorContext  
 參考文件<xref:System.Xaml.IDestinationTypeProvider>：<xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A>  
  
 衍生自 <xref:System.Xaml.IDestinationTypeProvider>。 這個類別代表標準 <xref:System.Xaml.IDestinationTypeProvider> 簽章中的內容；<xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A> 是自 .NET Framework 1.0 開始便已存在的類別。 它比 XAML 和 XAML <xref:System.Xaml.IDestinationTypeProvider> 情節更早用於字串\-值類型轉換。 在 .NET Framework XAML 服務內容中，會明確實作 <xref:System.Xaml.IDestinationTypeProvider> 的方法。 這個明確實作的行為會讓呼叫端知道，<xref:System.Xaml.IDestinationTypeProvider> API 與 XAML 類型系統無關，或者與從 XAML 讀取或寫入物件無關。<xref:System.Xaml.IDestinationTypeProvider>、<xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A> 和 `x:Reference` 通常會從 .NET Framework XAML 服務內容傳回 `null`。  
  
### IValueSerializerContext  
 參考文件<xref:System.Xaml.IDestinationTypeProvider>：<xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A>  
  
 衍生自 <xref:System.Xaml.IDestinationTypeProvider>，也依賴明確實作來抑制與 XAML 類型系統有關的錯誤假設。 支援 <xref:System.Xaml.IDestinationTypeProvider> 上的靜態查閱協助方法。  
  
### IXamlTypeResolver  
 參考文件<xref:System.Xaml.IDestinationTypeProvider>：<xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A>  
  
 定義來源：<xref:System.Xaml.IDestinationTypeProvider><xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A> 命名空間、System.Xaml 組件  
  
 適用於：<xref:System.Xaml.IDestinationTypeProvider>載入路徑情節，以及與 XAML 結構描述內容的互動  
  
 **服務 API：**  <xref:System.Windows.Markup.IXamlTypeResolver.Resolve%2A>  
  
 可能會影響 XAML 寫入器在物件圖形中建構 CLR 物件時，需要進行的 XAML 對 CLR 類型對應。<xref:System.Xaml.IDestinationTypeProvider> 會處理與 XAML 類型名稱 \(<xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A>\) 對應的字串 \(這個字串可能含限定前置詞\)，然後傳回 CLR `x:Reference`。 解析類型的作業通常高度仰賴 XAML 結構描述內容。 只有 XAML 結構描述內容才可辨識已載入哪些組件，以及進行類型解析時可以或應該存取哪些組件。  
  
### IUriContext  
 參考文件<xref:System.Xaml.IDestinationTypeProvider>：<xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A>  
  
 定義來源：<xref:System.Xaml.IDestinationTypeProvider><xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A> 命名空間、System.Xaml 組件  
  
 適用於：<xref:System.Xaml.IDestinationTypeProvider>成員值 \(URI 或 <xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A> 值\) 的載入路徑和儲存路徑處理。  
  
 **服務 API：**  <xref:System.Windows.Markup.IUriContext.BaseUri%2A>  
  
 這項服務會報告全域可用的根 URI \(如果有的話\)。 根 URI 可用來將相對 URI 解析成絕對 URI，或將絕對 URI 解析成相對 URI。 這個情節主要與由特定架構，或由架構中常用根項目類別的功能所公開的應用程式服務有關。 基底 URI 可建立為 XAML 讀取器設定，接著傳遞至 XAML 物件寫入器，再由這項服務報告。  
  
### IAmbientProvider  
 參考文件<xref:System.Xaml.IDestinationTypeProvider>：<xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A>  
  
 定義來源：<xref:System.Xaml.IDestinationTypeProvider><xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A> 命名空間、System.Xaml 組件  
  
 適用於：<xref:System.Xaml.IDestinationTypeProvider>載入路徑處理和類型查閱的延後或最佳化。  
  
 服務 API：<xref:System.Xaml.IDestinationTypeProvider><xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A>、其他 3 項。  
  
 XAML 中的環境概念是一種將類型的特定成員標記為環境成員的技術。 或者，您也可以將類型設為環境類型，使所有包含該類型之執行個體的屬性值都被視為環境屬性。 在物件圖形中 XAML 節點資料流更深層和做為子系的標記延伸或類型轉換器，可以在載入時存取環境屬性或類型執行個體，或是在儲存時使用環境結構的資訊。 這可能會影響其他服務 \(例如 <xref:System.Xaml.IDestinationTypeProvider> 或 <xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A>\) 的類型解析作業所需的限定程度。 請參閱<xref:System.Xaml.IDestinationTypeProvider>。  
  
### IXamlSchemaContextProvider  
 參考文件<xref:System.Xaml.IDestinationTypeProvider>：<xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A>  
  
 定義來源：<xref:System.Xaml.IDestinationTypeProvider><xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A> 命名空間、System.Xaml 組件  
  
 適用於：<xref:System.Xaml.IDestinationTypeProvider>載入路徑，以及任何必須將 XAML 類型解析成支援類型的作業。  
  
 **服務 API：**  <xref:System.Xaml.IXamlSchemaContextProvider.SchemaContext%2A>  
  
 所有延後載入作業都需要 XAML 結構描述內容，因為相同的結構描述內容必須套用至延後的區域，才能整合延後的內容。 如需 XAML 結構描述內容所扮演角色的詳細資訊，請參閱 <xref:System.Xaml.IDestinationTypeProvider>。  
  
### IRootObjectProvider  
 參考文件<xref:System.Xaml.IDestinationTypeProvider>：<xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A>  
  
 定義來源：<xref:System.Xaml.IDestinationTypeProvider><xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A> 命名空間、System.Xaml 組件  
  
 適用於：<xref:System.Xaml.IDestinationTypeProvider>載入路徑。  
  
 **服務 API：**  <xref:System.Xaml.IRootObjectProvider.RootObject%2A>  
  
 這項服務與由特定架構，或由架構中常用根項目類別的功能所公開的應用程式服務有關。 連接程式碼後置和事件連接，就是一種需要取得根物件的情節。 例如，<xref:System.Xaml.IDestinationTypeProvider> 的 WPF 實作可用來編譯標記，以及連接在 XAML 標記中的任何其他位置找到的任何事件處理常式屬性。 進行標記編譯時，標記和程式碼後置定義部分類別的連接點是在根項目。  
  
### IXamlNamespaceResolver  
 參考文件<xref:System.Xaml.IDestinationTypeProvider>：<xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A>  
  
 定義來源：<xref:System.Xaml.IDestinationTypeProvider><xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A> 命名空間、System.Xaml 組件  
  
 適用於：<xref:System.Xaml.IDestinationTypeProvider>載入路徑、儲存路徑。  
  
 服務 API：<xref:System.Xaml.IDestinationTypeProvider><xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A> \(適用於載入路徑\)、`x:Reference` \(適用於儲存路徑\)。  
  
 <xref:System.Xaml.IDestinationTypeProvider> 是一項服務，可根據 XAML 命名空間的前置詞，傳回 XAML 命名空間在起始 XAML 標記中的識別項 \/ URI。  
  
### IProvideValueTarget  
 參考文件<xref:System.Xaml.IDestinationTypeProvider>：<xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A>  
  
 定義來源：<xref:System.Xaml.IDestinationTypeProvider><xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A> 命名空間、System.Xaml 組件  
  
 適用於：<xref:System.Xaml.IDestinationTypeProvider>載入路徑和儲存路徑。  
  
 服務 API：<xref:System.Xaml.IDestinationTypeProvider><xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A>、`x:Reference`。  
  
 <xref:System.Xaml.IDestinationTypeProvider> 可讓類型轉換器或標記延伸取得有關其在載入時之作用位置的內容。 實作可以使用這個內容讓某個使用方式無效。 例如，WPF 在其某些標記延伸 \(例如 <xref:System.Xaml.IDestinationTypeProvider>\) 內具有邏輯。 這個邏輯會檢查 <xref:System.Xaml.IDestinationTypeProvider>，以確定該延伸只會用來設定相依性屬性 \(或其他非相依性屬性的簡短清單\)。  
  
### IXamlNameResolver  
 參考文件<xref:System.Xaml.IDestinationTypeProvider>：<xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A>  
  
 定義來源：<xref:System.Xaml.IDestinationTypeProvider><xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A> 命名空間、System.Xaml 組件  
  
 適用於：<xref:System.Xaml.IDestinationTypeProvider>載入路徑物件圖形定義，並解析由 <xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A>、`x:Reference` 或架構特定技術所識別的物件。  
  
 服務 API：<xref:System.Xaml.IDestinationTypeProvider><xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A>；其他適用於進階情節 \(例如處理向前參考\) 的 API。  
  
 .NET Framework XAML 服務所實作的 <xref:System.Xaml.IDestinationTypeProvider> 處理依賴這項服務。 特定架構或是支援該架構的工具，會使用這項服務來處理 <xref:System.Xaml.IDestinationTypeProvider> 或是已用 <xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A> 屬性化\(Attributed\) 的對等屬性 \(Property\)。  
  
### IDestinationTypeProvider  
 參考文件<xref:System.Xaml.IDestinationTypeProvider>：<xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A>  
  
 定義來源：<xref:System.Xaml.IDestinationTypeProvider><xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A> 命名空間、System.Xaml 組件  
  
 適用於：<xref:System.Xaml.IDestinationTypeProvider>間接 CLR 類型資訊的載入路徑解析。  
  
 服務 API：<xref:System.Xaml.IDestinationTypeProvider> <xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A>  
  
 如需詳細資訊，請參閱<xref:System.Xaml.IDestinationTypeProvider>。  
  
## 請參閱  
 <xref:System.Windows.Markup.MarkupExtension>   
 <xref:System.Xaml.XamlObjectWriter>   
 [Markup Extensions for XAML Overview](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md)   
 [Type Converters for XAML Overview](../../../docs/framework/xaml-services/type-converters-for-xaml-overview.md)