---
title: 適用於類型轉換子和標記延伸的服務內容
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], type converter services how-to
ms.assetid: b4dad00f-03da-4579-a4e9-d8d72d2ccbce
ms.openlocfilehash: 850e266aed6fc2d69722ba6dac3baa3e115678a8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61953968"
---
# <a name="service-contexts-available-to-type-converters-and-markup-extensions"></a><span data-ttu-id="6bd21-102">適用於類型轉換子和標記延伸的服務內容</span><span class="sxs-lookup"><span data-stu-id="6bd21-102">Service Contexts Available to Type Converters and Markup Extensions</span></span>
<span data-ttu-id="6bd21-103">在撰寫類型來支援使用類型轉換子和標記延伸時，通常必須先知道會在標記或周圍物件圖形結構中的何處使用類型轉換子和標記延伸。</span><span class="sxs-lookup"><span data-stu-id="6bd21-103">Authors of the types that support type converter and markup extension usages must often have contextual information about where a usage is located in the markup, or in surrounding object graph structure.</span></span> <span data-ttu-id="6bd21-104">要有這些資訊，才能正確地具現化所提供的物件，或是在物件圖形中建立對現有物件的物件參考。</span><span class="sxs-lookup"><span data-stu-id="6bd21-104">Information might be needed so that the provided object is instantiated correctly or so that object references to existing objects in the object graph can be made.</span></span> <span data-ttu-id="6bd21-105">使用 .NET Framework XAML 服務時，可能需要的內容會以一系列服務介面的形式公開。</span><span class="sxs-lookup"><span data-stu-id="6bd21-105">When using .NET Framework XAML Services, the context that might be required is exposed as a series of service interfaces.</span></span> <span data-ttu-id="6bd21-106">類型轉換子或標記延伸支援程式碼可以使用從 <xref:System.Xaml.XamlObjectWriter> 或相關類型傳來的可用服務提供者內容，來查詢服務。</span><span class="sxs-lookup"><span data-stu-id="6bd21-106">Type converter or markup extension support code can query for a service by using a service provider context that is available and passed through from <xref:System.Xaml.XamlObjectWriter> or related types.</span></span> <span data-ttu-id="6bd21-107">XAML 結構描述內容可透過這類服務直接提供。</span><span class="sxs-lookup"><span data-stu-id="6bd21-107">The XAML schema context is directly available through one such service.</span></span> <span data-ttu-id="6bd21-108">本主題說明如何透過值轉換器實作存取服務內容，並列出通常可用的服務及其角色。</span><span class="sxs-lookup"><span data-stu-id="6bd21-108">This topic describes how to access service contexts from a value converter implementation, and lists typically available services and their roles.</span></span>  
  
<a name="obtaining_services"></a>   
## <a name="obtaining-services"></a><span data-ttu-id="6bd21-109">取得服務</span><span class="sxs-lookup"><span data-stu-id="6bd21-109">Obtaining Services</span></span>  
 <span data-ttu-id="6bd21-110">身為值轉換器的實作者，您通常會需要存取套用值轉換器之特定類型的內容。</span><span class="sxs-lookup"><span data-stu-id="6bd21-110">As an implementer of a value converter, you often need access to some type of context in which the value converter is applied.</span></span> <span data-ttu-id="6bd21-111">這個內容可能包含作用中的 XAML 結構描述內容、XAML 結構描述內容和 XAML 物件寫入器提供之類型對應系統的存取等資訊。</span><span class="sxs-lookup"><span data-stu-id="6bd21-111">This context might include information such as the active XAML schema context, access to the type mapping system that the XAML schema context and XAML object writer provide, and so on.</span></span> <span data-ttu-id="6bd21-112">標記延伸或類型轉換子實作適用的可用服務，會透過每個虛擬方法之簽章中的內容參數來表示。</span><span class="sxs-lookup"><span data-stu-id="6bd21-112">The services available for a markup extension or type converter implementation are communicated through the context parameters that are part of the signature of each virtual method.</span></span> <span data-ttu-id="6bd21-113">不論如何，您都會在內容中實作 <xref:System.IServiceProvider> ，並且可以呼叫 <xref:System.IServiceProvider.GetService%2A?displayProperty=nameWithType> 來要求服務。</span><span class="sxs-lookup"><span data-stu-id="6bd21-113">In every case, you have <xref:System.IServiceProvider> implemented in the context, and can call <xref:System.IServiceProvider.GetService%2A?displayProperty=nameWithType> to request a service.</span></span>  
  
<a name="services_for_a_markup_extension"></a>   
## <a name="services-for-a-markup-extension"></a><span data-ttu-id="6bd21-114">標記延伸適用的服務</span><span class="sxs-lookup"><span data-stu-id="6bd21-114">Services for a Markup Extension</span></span>  
 <span data-ttu-id="6bd21-115"><xref:System.Windows.Markup.MarkupExtension> 只有一種虛擬方法，那就是 <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>。</span><span class="sxs-lookup"><span data-stu-id="6bd21-115"><xref:System.Windows.Markup.MarkupExtension> has only one virtual method, <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>.</span></span> <span data-ttu-id="6bd21-116">輸入 `serviceProvider` 參數是在 XAML 處理器呼叫標記延伸時，用以向實作表示服務的方式。</span><span class="sxs-lookup"><span data-stu-id="6bd21-116">The input `serviceProvider` parameter is how the services are communicated to implementations when the markup extension is called by a XAML processor.</span></span> <span data-ttu-id="6bd21-117">下列虛擬程式碼示範標記延伸實作如何在其 <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>中查詢服務：</span><span class="sxs-lookup"><span data-stu-id="6bd21-117">The following pseudocode illustrates how a markup extension implementation might query for services in its <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>:</span></span>  
  
```  
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
  
<a name="services_for_a_type_converter"></a>   
## <a name="services-for-a-type-converter"></a><span data-ttu-id="6bd21-118">類型轉換器適用的服務</span><span class="sxs-lookup"><span data-stu-id="6bd21-118">Services for a Type Converter</span></span>  
 <span data-ttu-id="6bd21-119"><xref:System.ComponentModel.TypeConverter> 有四個使用服務內容並支援使用 XAML 的虛擬方法。</span><span class="sxs-lookup"><span data-stu-id="6bd21-119"><xref:System.ComponentModel.TypeConverter> has four virtual methods that use a service context and that support XAML usages.</span></span> <span data-ttu-id="6bd21-120">每個方法都會傳遞輸入 `context` 參數。</span><span class="sxs-lookup"><span data-stu-id="6bd21-120">Each of these methods passes an input `context` parameter.</span></span> <span data-ttu-id="6bd21-121">這個參數屬於 <xref:System.ComponentModel.ITypeDescriptorContext>類型，但該介面繼承自 <xref:System.IServiceProvider>，因此類型轉換器實作會有 <xref:System.IServiceProvider.GetService%2A> 方法可以使用。</span><span class="sxs-lookup"><span data-stu-id="6bd21-121">This parameter is of type <xref:System.ComponentModel.ITypeDescriptorContext>, but that interface inherits <xref:System.IServiceProvider>, and therefore, there is a <xref:System.IServiceProvider.GetService%2A> method available to type converter implementations.</span></span>  
  
 <span data-ttu-id="6bd21-122">下列虛擬程式碼示範用於 XAML 的類型轉換子實作如何在其中一個覆寫 (在本例中為 <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>) 中查詢服務：</span><span class="sxs-lookup"><span data-stu-id="6bd21-122">The following pseudocode illustrates how a type converter implementation for XAML usages might query for services in one of its overrides, in this case <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>:</span></span>  
  
```  
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
  
<a name="services_for_a_value_serializer"></a>   
## <a name="services-for-a-value-serializer"></a><span data-ttu-id="6bd21-123">值序列化程式適用的服務</span><span class="sxs-lookup"><span data-stu-id="6bd21-123">Services for a Value Serializer</span></span>  
 <span data-ttu-id="6bd21-124">針對值序列化程式內容，您會使用 <xref:System.Windows.Markup.ValueSerializer> 類別專屬的服務提供者類型 <xref:System.Windows.Markup.IValueSerializerContext>。</span><span class="sxs-lookup"><span data-stu-id="6bd21-124">For value serializer context, you use a service provider type that is specific to the <xref:System.Windows.Markup.ValueSerializer> class, <xref:System.Windows.Markup.IValueSerializerContext>.</span></span> <span data-ttu-id="6bd21-125">該內容會傳遞給四個 <xref:System.Windows.Markup.ValueSerializer> 虛擬方法的覆寫。</span><span class="sxs-lookup"><span data-stu-id="6bd21-125">That context is passed to overrides of the four <xref:System.Windows.Markup.ValueSerializer> virtual methods.</span></span> <span data-ttu-id="6bd21-126">呼叫該內容中的 <xref:System.IServiceProvider.GetService%2A> ，即可取得服務。</span><span class="sxs-lookup"><span data-stu-id="6bd21-126">Call <xref:System.IServiceProvider.GetService%2A> from the context to obtain services.</span></span>  
  
<a name="using_the_xaml_service_provider_contexts"></a>   
## <a name="using-the-xaml-service-provider-contexts"></a><span data-ttu-id="6bd21-127">使用 XAML 服務提供者內容</span><span class="sxs-lookup"><span data-stu-id="6bd21-127">Using the XAML Service Provider Contexts</span></span>  
 <span data-ttu-id="6bd21-128">讓 <xref:System.IServiceProvider.GetService%2A> 得以存取可用之標記延伸或類型轉換器之 XAML 服務的服務提供者，會以內部類別的形式實作，而且僅會透過介面和在相關內容中用以傳遞服務提供者的管道來公開。</span><span class="sxs-lookup"><span data-stu-id="6bd21-128">The service provider for <xref:System.IServiceProvider.GetService%2A> access to XAML services available to markup extensions or type converters is implemented as an internal class, with exposure only through the interface and how it is passed into the relevant context .</span></span> <span data-ttu-id="6bd21-129">每當 .NET Framework XAML 服務預設實作之載入路徑或儲存路徑中的 XAML 處理作業，叫用需要服務內容的相關標記延伸或類型轉換器方法時，即會傳遞這個內部物件。</span><span class="sxs-lookup"><span data-stu-id="6bd21-129">Whenever a XAML processing operation in the default .NET Framework XAML Services implementations of load path or save path invokes the relevant markup extension or type converter methods that require a service context, this internal object is passed.</span></span> <span data-ttu-id="6bd21-130">系統服務內容會根據當時的情況提供 `MarkupExtensionContext` 或 `TextSyntaxContext`，但這兩個類別的內容則是內部資訊。</span><span class="sxs-lookup"><span data-stu-id="6bd21-130">Depending on the circumstance, the system service context provides either `MarkupExtensionContext` or `TextSyntaxContext`, but the specifics of both of these classes are internal.</span></span> <span data-ttu-id="6bd21-131">您與這些類別進行的互動，僅限於透過 <xref:System.IServiceProvider.GetService%2A>向類別要求服務。</span><span class="sxs-lookup"><span data-stu-id="6bd21-131">Your interaction with these classes is limited to requesting services from them, through <xref:System.IServiceProvider.GetService%2A>.</span></span>  
  
<a name="available_systemxaml_services"></a>   
## <a name="available-services-from-the-net-framework-xaml-service-context"></a><span data-ttu-id="6bd21-132">.NET Framework XAML 服務內容提供的服務</span><span class="sxs-lookup"><span data-stu-id="6bd21-132">Available Services from the .NET Framework XAML Service Context</span></span>  
 <span data-ttu-id="6bd21-133">.NET Framework XAML 服務定義標記延伸、類型轉換器、值序列化程式，以及其他可能適用的服務。</span><span class="sxs-lookup"><span data-stu-id="6bd21-133">.NET Framework XAML Services defines services for markup extensions, type converters, value serializers, and potentially other usages.</span></span> <span data-ttu-id="6bd21-134">下列各節分別說明這些服務，並提供如何在實作中使用這些服務的相關指引。</span><span class="sxs-lookup"><span data-stu-id="6bd21-134">The following sections describe each of these services and provide guidance about how the service might be used in an implementation.</span></span>  
  
### <a name="iserviceprovider"></a><span data-ttu-id="6bd21-135">IServiceProvider</span><span class="sxs-lookup"><span data-stu-id="6bd21-135">IServiceProvider</span></span>  
 <span data-ttu-id="6bd21-136">**T:System.Xaml.IDestinationTypeProvider**中查詢服務： <xref:System.IServiceProvider></span><span class="sxs-lookup"><span data-stu-id="6bd21-136">**Reference documentation**: <xref:System.IServiceProvider></span></span>  
  
 <span data-ttu-id="6bd21-137">**與：**.NET Framework 中服務基礎結構的基本作業，以便讓您可以呼叫<xref:System.IServiceProvider.GetService%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="6bd21-137">**Relevant to:** Basic operation of a service-based infrastructure in the .NET Framework so that you can call <xref:System.IServiceProvider.GetService%2A?displayProperty=nameWithType>.</span></span>  
  
### <a name="itypedescriptorcontext"></a><span data-ttu-id="6bd21-138">ITypeDescriptorContext</span><span class="sxs-lookup"><span data-stu-id="6bd21-138">ITypeDescriptorContext</span></span>  
 <span data-ttu-id="6bd21-139">**T:System.Xaml.IDestinationTypeProvider**中查詢服務： <xref:System.ComponentModel.ITypeDescriptorContext></span><span class="sxs-lookup"><span data-stu-id="6bd21-139">**Reference documentation**: <xref:System.ComponentModel.ITypeDescriptorContext></span></span>  
  
 <span data-ttu-id="6bd21-140">衍生自 <xref:System.IServiceProvider>。</span><span class="sxs-lookup"><span data-stu-id="6bd21-140">Derives from <xref:System.IServiceProvider>.</span></span> <span data-ttu-id="6bd21-141">這個類別代表標準 <xref:System.ComponentModel.TypeConverter> 簽章中的內容； <xref:System.ComponentModel.TypeConverter> 是自 .NET Framework 1.0 開始便已存在的類別。</span><span class="sxs-lookup"><span data-stu-id="6bd21-141">This class represents context in the standard <xref:System.ComponentModel.TypeConverter> signatures; <xref:System.ComponentModel.TypeConverter> is a class that has existed since .NET Framework 1.0.</span></span> <span data-ttu-id="6bd21-142">它比 XAML 和 XAML <xref:System.ComponentModel.TypeConverter> 情節更早用於字串-值類型轉換。</span><span class="sxs-lookup"><span data-stu-id="6bd21-142">It predates XAML and the XAML <xref:System.ComponentModel.TypeConverter> scenario for string-value type conversion.</span></span> <span data-ttu-id="6bd21-143">在 .NET Framework XAML 服務內容中，會明確實作 <xref:System.ComponentModel.TypeConverter> 的方法。</span><span class="sxs-lookup"><span data-stu-id="6bd21-143">In the .NET Framework XAML Services context, methods of <xref:System.ComponentModel.TypeConverter> are implemented explicitly.</span></span> <span data-ttu-id="6bd21-144">這個明確實作的行為會讓呼叫端知道， <xref:System.ComponentModel.ITypeDescriptorContext> API 與 XAML 類型系統無關，或者與從 XAML 讀取或寫入物件無關。</span><span class="sxs-lookup"><span data-stu-id="6bd21-144">The explicit implementation's behavior indicates to callers that the <xref:System.ComponentModel.ITypeDescriptorContext> API is not relevant for XAML type systems, or for reading or writing objects from XAML.</span></span> <span data-ttu-id="6bd21-145"><xref:System.ComponentModel.ITypeDescriptorContext.Container%2A>、 <xref:System.ComponentModel.ITypeDescriptorContext.Instance%2A>和 <xref:System.ComponentModel.ITypeDescriptorContext.PropertyDescriptor%2A> 通常會從 .NET Framework XAML 服務內容傳回 `null` 。</span><span class="sxs-lookup"><span data-stu-id="6bd21-145"><xref:System.ComponentModel.ITypeDescriptorContext.Container%2A>, <xref:System.ComponentModel.ITypeDescriptorContext.Instance%2A>, and <xref:System.ComponentModel.ITypeDescriptorContext.PropertyDescriptor%2A> generally return `null` from .NET Framework XAML Services contexts.</span></span>  
  
### <a name="ivalueserializercontext"></a><span data-ttu-id="6bd21-146">IValueSerializerContext</span><span class="sxs-lookup"><span data-stu-id="6bd21-146">IValueSerializerContext</span></span>  
 <span data-ttu-id="6bd21-147">**T:System.Xaml.IDestinationTypeProvider**中查詢服務： <xref:System.Windows.Markup.IValueSerializerContext></span><span class="sxs-lookup"><span data-stu-id="6bd21-147">**Reference documentation**: <xref:System.Windows.Markup.IValueSerializerContext></span></span>  
  
 <span data-ttu-id="6bd21-148">衍生自 <xref:System.ComponentModel.ITypeDescriptorContext> ，也依賴明確實作來抑制與 XAML 類型系統有關的錯誤假設。</span><span class="sxs-lookup"><span data-stu-id="6bd21-148">Derives from <xref:System.ComponentModel.ITypeDescriptorContext> and also relies on explicit implementations to suppress false implications about the XAML type system.</span></span> <span data-ttu-id="6bd21-149">支援 <xref:System.Windows.Markup.ValueSerializer>上的靜態查閱協助方法。</span><span class="sxs-lookup"><span data-stu-id="6bd21-149">Supports the static lookup helper methods on <xref:System.Windows.Markup.ValueSerializer>.</span></span>  
  
### <a name="ixamltyperesolver"></a><span data-ttu-id="6bd21-150">IXamlTypeResolver</span><span class="sxs-lookup"><span data-stu-id="6bd21-150">IXamlTypeResolver</span></span>  
 <span data-ttu-id="6bd21-151">**T:System.Xaml.IDestinationTypeProvider**中查詢服務： <xref:System.Windows.Markup.IXamlTypeResolver></span><span class="sxs-lookup"><span data-stu-id="6bd21-151">**Reference documentation**: <xref:System.Windows.Markup.IXamlTypeResolver></span></span>  
  
 <span data-ttu-id="6bd21-152">**T:System.Xaml.IDestinationTypeProvider**  <xref:System.Windows.Markup> 命名空間、System.Xaml 組件</span><span class="sxs-lookup"><span data-stu-id="6bd21-152">**Defined by:**  <xref:System.Windows.Markup> namespace, System.Xaml assembly</span></span>  
  
 <span data-ttu-id="6bd21-153">**與：** 載入路徑情節，以及與 XAML 結構描述內容的互動</span><span class="sxs-lookup"><span data-stu-id="6bd21-153">**Relevant to:** Load path scenarios, and interaction with XAML schema context</span></span>  
  
 <span data-ttu-id="6bd21-154">**服務 API：**  <xref:System.Windows.Markup.IXamlTypeResolver.Resolve%2A></span><span class="sxs-lookup"><span data-stu-id="6bd21-154">**Service API:**  <xref:System.Windows.Markup.IXamlTypeResolver.Resolve%2A></span></span>  
  
 <span data-ttu-id="6bd21-155">可能會影響 XAML 寫入器在物件圖形中建構 CLR 物件時，需要進行的 XAML 對 CLR 類型對應。</span><span class="sxs-lookup"><span data-stu-id="6bd21-155">Can influence the XAML-to-CLR type mapping that is necessary when the XAML writer constructs a CLR object in an object graph.</span></span> <span data-ttu-id="6bd21-156"><xref:System.Windows.Markup.IXamlTypeResolver.Resolve%2A> 會處理與 XAML 類型名稱 (<xref:System.Xaml.XamlType.Name%2A?displayProperty=nameWithType>) 對應的字串 (這個字串可能含限定前置詞)，然後傳回 CLR <xref:System.Type>。</span><span class="sxs-lookup"><span data-stu-id="6bd21-156"><xref:System.Windows.Markup.IXamlTypeResolver.Resolve%2A> processes a potentially prefix-qualified string that corresponds to a XAML type name (<xref:System.Xaml.XamlType.Name%2A?displayProperty=nameWithType>), and returns a CLR <xref:System.Type>.</span></span> <span data-ttu-id="6bd21-157">解析類型的作業通常高度仰賴 XAML 結構描述內容。</span><span class="sxs-lookup"><span data-stu-id="6bd21-157">Resolving types is typically heavily dependent on XAML schema context.</span></span> <span data-ttu-id="6bd21-158">只有 XAML 結構描述內容才可辨識已載入哪些組件，以及進行類型解析時可以或應該存取哪些組件。</span><span class="sxs-lookup"><span data-stu-id="6bd21-158">Only the XAML schema context is aware of considerations such as which assemblies are loaded, and which of these assemblies can or should be accessed for type resolution.</span></span>  
  
### <a name="iuricontext"></a><span data-ttu-id="6bd21-159">IUriContext</span><span class="sxs-lookup"><span data-stu-id="6bd21-159">IUriContext</span></span>  
 <span data-ttu-id="6bd21-160">**T:System.Xaml.IDestinationTypeProvider**中查詢服務： <xref:System.Windows.Markup.IUriContext></span><span class="sxs-lookup"><span data-stu-id="6bd21-160">**Reference documentation**: <xref:System.Windows.Markup.IUriContext></span></span>  
  
 <span data-ttu-id="6bd21-161">**T:System.Xaml.IDestinationTypeProvider**  <xref:System.Windows.Markup> 命名空間、System.Xaml 組件</span><span class="sxs-lookup"><span data-stu-id="6bd21-161">**Defined by:**  <xref:System.Windows.Markup> namespace, System.Xaml assembly</span></span>  
  
 <span data-ttu-id="6bd21-162">**與：** 載入路徑和儲存路徑處理是一種 Uri 的成員值或`x:Uri`值。</span><span class="sxs-lookup"><span data-stu-id="6bd21-162">**Relevant to:** Load path and save path handling of member values that are URIs or `x:Uri` values.</span></span>  
  
 <span data-ttu-id="6bd21-163">**服務 API：**  <xref:System.Windows.Markup.IUriContext.BaseUri%2A></span><span class="sxs-lookup"><span data-stu-id="6bd21-163">**Service API:**  <xref:System.Windows.Markup.IUriContext.BaseUri%2A></span></span>  
  
 <span data-ttu-id="6bd21-164">這項服務會報告全域可用的根 URI (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="6bd21-164">This service reports a globally available URI root, if any.</span></span> <span data-ttu-id="6bd21-165">根 URI 可用來將相對 URI 解析成絕對 URI，或將絕對 URI 解析成相對 URI。</span><span class="sxs-lookup"><span data-stu-id="6bd21-165">The URI root can be used to resolve relative URIs to absolute URIs or vice versa.</span></span> <span data-ttu-id="6bd21-166">這個情節主要與由特定架構，或由架構中常用根項目類別的功能所公開的應用程式服務有關。</span><span class="sxs-lookup"><span data-stu-id="6bd21-166">This scenario is mainly relevant to application services that are exposed by a particular framework, or capabilities of a frequently used root element class in a framework.</span></span> <span data-ttu-id="6bd21-167">基底 URI 可建立為 XAML 讀取器設定，接著傳遞至 XAML 物件寫入器，再由這項服務報告。</span><span class="sxs-lookup"><span data-stu-id="6bd21-167">The base URI can be established as a XAML reader setting, which is then passed through to the XAML object writer and reported by this service.</span></span>  
  
### <a name="iambientprovider"></a><span data-ttu-id="6bd21-168">IAmbientProvider</span><span class="sxs-lookup"><span data-stu-id="6bd21-168">IAmbientProvider</span></span>  
 <span data-ttu-id="6bd21-169">**T:System.Xaml.IDestinationTypeProvider**中查詢服務： <xref:System.Xaml.IAmbientProvider></span><span class="sxs-lookup"><span data-stu-id="6bd21-169">**Reference documentation**: <xref:System.Xaml.IAmbientProvider></span></span>  
  
 <span data-ttu-id="6bd21-170">**T:System.Xaml.IDestinationTypeProvider**  <xref:System.Xaml> 命名空間、System.Xaml 組件</span><span class="sxs-lookup"><span data-stu-id="6bd21-170">**Defined by:**  <xref:System.Xaml> namespace, System.Xaml assembly</span></span>  
  
 <span data-ttu-id="6bd21-171">**與：** 載入路徑處理和類型查閱的延後或最佳化。</span><span class="sxs-lookup"><span data-stu-id="6bd21-171">**Relevant to:** Load path handling and type lookup deferrals or optimizations.</span></span>  
  
 <span data-ttu-id="6bd21-172">**T:System.Xaml.IDestinationTypeProvider**  <xref:System.Xaml.IAmbientProvider.GetAllAmbientValues%2A>、其他 3 項。</span><span class="sxs-lookup"><span data-stu-id="6bd21-172">**Service APIs:**  <xref:System.Xaml.IAmbientProvider.GetAllAmbientValues%2A>, 3 others.</span></span>  
  
 <span data-ttu-id="6bd21-173">XAML 中的環境概念是一種將類型的特定成員標記為環境成員的技術。</span><span class="sxs-lookup"><span data-stu-id="6bd21-173">The ambience concept in XAML is a technique for marking a particular member of a type as ambient.</span></span> <span data-ttu-id="6bd21-174">或者，您也可以將類型設為環境類型，使所有包含該類型之執行個體的屬性值都被視為環境屬性。</span><span class="sxs-lookup"><span data-stu-id="6bd21-174">Alternatively, a type can be ambient so that all property values that hold an instance of the type should be considered ambient properties.</span></span> <span data-ttu-id="6bd21-175">在物件圖形中 XAML 節點資料流更深層和做為子系的標記延伸或類型轉換器，可以在載入時存取環境屬性或類型執行個體，或是在儲存時使用環境結構的資訊。</span><span class="sxs-lookup"><span data-stu-id="6bd21-175">Markup extensions or type converters that are further along the XAML node stream and that are descendants in the object graph can access the ambient property or type instance at load time; or they can use knowledge of the ambient structure at save time.</span></span> <span data-ttu-id="6bd21-176">這可能會影響其他服務 (例如 <xref:System.Windows.Markup.IXamlTypeResolver> 或 `x:Type`) 的類型解析作業所需的限定程度。</span><span class="sxs-lookup"><span data-stu-id="6bd21-176">This can affect the degree of qualification that is needed to resolve types for other services, such as for <xref:System.Windows.Markup.IXamlTypeResolver> or for `x:Type`.</span></span> <span data-ttu-id="6bd21-177">請參閱 <xref:System.Xaml.AmbientPropertyValue>。</span><span class="sxs-lookup"><span data-stu-id="6bd21-177">See also <xref:System.Xaml.AmbientPropertyValue>.</span></span>  
  
### <a name="ixamlschemacontextprovider"></a><span data-ttu-id="6bd21-178">IXamlSchemaContextProvider</span><span class="sxs-lookup"><span data-stu-id="6bd21-178">IXamlSchemaContextProvider</span></span>  
 <span data-ttu-id="6bd21-179">**T:System.Xaml.IDestinationTypeProvider**中查詢服務： <xref:System.Xaml.IXamlSchemaContextProvider></span><span class="sxs-lookup"><span data-stu-id="6bd21-179">**Reference documentation**: <xref:System.Xaml.IXamlSchemaContextProvider></span></span>  
  
 <span data-ttu-id="6bd21-180">**T:System.Xaml.IDestinationTypeProvider**  <xref:System.Xaml> 命名空間、System.Xaml 組件</span><span class="sxs-lookup"><span data-stu-id="6bd21-180">**Defined by:**  <xref:System.Xaml> namespace, System.Xaml assembly</span></span>  
  
 <span data-ttu-id="6bd21-181">**與：** 載入路徑，以及任何必須將 XAML 類型解析成支援類型的作業。</span><span class="sxs-lookup"><span data-stu-id="6bd21-181">**Relevant to:** Load path, and any operation that must resolve a XAML type to a backing type.</span></span>  
  
 <span data-ttu-id="6bd21-182">**服務 API：**  <xref:System.Xaml.IXamlSchemaContextProvider.SchemaContext%2A></span><span class="sxs-lookup"><span data-stu-id="6bd21-182">**Service API:**  <xref:System.Xaml.IXamlSchemaContextProvider.SchemaContext%2A></span></span>  
  
 <span data-ttu-id="6bd21-183">所有延後載入作業都需要 XAML 結構描述內容，因為相同的結構描述內容必須套用至延後的區域，才能整合延後的內容。</span><span class="sxs-lookup"><span data-stu-id="6bd21-183">XAML schema context is necessary for any defer load operations, because the same schema context must act on the deferred area in order to integrate the deferred content.</span></span> <span data-ttu-id="6bd21-184">如需 XAML 結構描述內容所扮演角色的詳細資訊，請參閱 [T:System.Xaml.IDestinationTypeProvider](index.md)。</span><span class="sxs-lookup"><span data-stu-id="6bd21-184">For more information about the role of the XAML schema context, see [XAML Services](index.md).</span></span>  
  
### <a name="irootobjectprovider"></a><span data-ttu-id="6bd21-185">IRootObjectProvider</span><span class="sxs-lookup"><span data-stu-id="6bd21-185">IRootObjectProvider</span></span>  
 <span data-ttu-id="6bd21-186">**T:System.Xaml.IDestinationTypeProvider**中查詢服務： <xref:System.Xaml.IRootObjectProvider></span><span class="sxs-lookup"><span data-stu-id="6bd21-186">**Reference documentation**: <xref:System.Xaml.IRootObjectProvider></span></span>  
  
 <span data-ttu-id="6bd21-187">**T:System.Xaml.IDestinationTypeProvider**  <xref:System.Xaml> 命名空間、System.Xaml 組件</span><span class="sxs-lookup"><span data-stu-id="6bd21-187">**Defined by:**  <xref:System.Xaml> namespace, System.Xaml assembly</span></span>  
  
 <span data-ttu-id="6bd21-188">**與：** 載入路徑。</span><span class="sxs-lookup"><span data-stu-id="6bd21-188">**Relevant to:** Load path.</span></span>  
  
 <span data-ttu-id="6bd21-189">**服務 API：**  <xref:System.Xaml.IRootObjectProvider.RootObject%2A></span><span class="sxs-lookup"><span data-stu-id="6bd21-189">**Service API:**  <xref:System.Xaml.IRootObjectProvider.RootObject%2A></span></span>  
  
 <span data-ttu-id="6bd21-190">這項服務與由特定架構，或由架構中常用根項目類別的功能所公開的應用程式服務有關。</span><span class="sxs-lookup"><span data-stu-id="6bd21-190">The service is relevant to application services that are exposed by a particular framework or by capabilities of a frequently used root element class in a framework.</span></span> <span data-ttu-id="6bd21-191">連接程式碼後置和事件連接，就是一種需要取得根物件的情節。</span><span class="sxs-lookup"><span data-stu-id="6bd21-191">One scenario for obtaining the root object is connecting code-behind and event wiring.</span></span> <span data-ttu-id="6bd21-192">例如， `x:Class` 的 WPF 實作可用來編譯標記，以及連接在 XAML 標記中的任何其他位置找到的任何事件處理常式屬性。</span><span class="sxs-lookup"><span data-stu-id="6bd21-192">For example, the WPF implementation of `x:Class` is used for markup compile and wiring of any event handler attribute that is found at any other position in the XAML markup.</span></span> <span data-ttu-id="6bd21-193">進行標記編譯時，標記和程式碼後置定義部分類別的連接點是在根項目。</span><span class="sxs-lookup"><span data-stu-id="6bd21-193">The connection point of markup and code-behind defined partial classes for markup compile is at the root element.</span></span>  
  
### <a name="ixamlnamespaceresolver"></a><span data-ttu-id="6bd21-194">IXamlNamespaceResolver</span><span class="sxs-lookup"><span data-stu-id="6bd21-194">IXamlNamespaceResolver</span></span>  
 <span data-ttu-id="6bd21-195">**T:System.Xaml.IDestinationTypeProvider**中查詢服務： <xref:System.Xaml.IXamlNamespaceResolver></span><span class="sxs-lookup"><span data-stu-id="6bd21-195">**Reference documentation**: <xref:System.Xaml.IXamlNamespaceResolver></span></span>  
  
 <span data-ttu-id="6bd21-196">**T:System.Xaml.IDestinationTypeProvider**  <xref:System.Xaml> 命名空間、System.Xaml 組件</span><span class="sxs-lookup"><span data-stu-id="6bd21-196">**Defined by:**  <xref:System.Xaml> namespace, System.Xaml assembly</span></span>  
  
 <span data-ttu-id="6bd21-197">**與：** 載入路徑、 儲存路徑。</span><span class="sxs-lookup"><span data-stu-id="6bd21-197">**Relevant to:** Load path, save path.</span></span>  
  
 <span data-ttu-id="6bd21-198">**服務 API:** <xref:System.Xaml.IXamlNamespaceResolver.GetNamespace%2A>適用於載入路徑<xref:System.Xaml.IXamlNamespaceResolver.GetNamespacePrefixes%2A>針對儲存路徑。</span><span class="sxs-lookup"><span data-stu-id="6bd21-198">**Service API:** <xref:System.Xaml.IXamlNamespaceResolver.GetNamespace%2A> for load path, <xref:System.Xaml.IXamlNamespaceResolver.GetNamespacePrefixes%2A> for save path.</span></span>  
  
 <span data-ttu-id="6bd21-199"><xref:System.Xaml.IXamlNamespaceResolver> 是一項服務，可根據 XAML 命名空間的前置詞，傳回 XAML 命名空間在起始 XAML 標記中的識別項 / URI。</span><span class="sxs-lookup"><span data-stu-id="6bd21-199"><xref:System.Xaml.IXamlNamespaceResolver> is a service that can return a XAML namespace identifier / URI based on its prefix as mapped in the originating XAML markup.</span></span>  
  
### <a name="iprovidevaluetarget"></a><span data-ttu-id="6bd21-200">IProvideValueTarget</span><span class="sxs-lookup"><span data-stu-id="6bd21-200">IProvideValueTarget</span></span>  
 <span data-ttu-id="6bd21-201">**T:System.Xaml.IDestinationTypeProvider**中查詢服務： <xref:System.Windows.Markup.IProvideValueTarget></span><span class="sxs-lookup"><span data-stu-id="6bd21-201">**Reference documentation**: <xref:System.Windows.Markup.IProvideValueTarget></span></span>  
  
 <span data-ttu-id="6bd21-202">**T:System.Xaml.IDestinationTypeProvider**  <xref:System.Windows.Markup> 命名空間、System.Xaml 組件</span><span class="sxs-lookup"><span data-stu-id="6bd21-202">**Defined by:**  <xref:System.Windows.Markup> namespace, System.Xaml assembly</span></span>  
  
 <span data-ttu-id="6bd21-203">**與：** 載入路徑和儲存路徑。</span><span class="sxs-lookup"><span data-stu-id="6bd21-203">**Relevant to:** Load path and save path.</span></span>  
  
 <span data-ttu-id="6bd21-204">**T:System.Xaml.IDestinationTypeProvider**  <xref:System.Windows.Markup.IProvideValueTarget.TargetObject%2A>、 <xref:System.Windows.Markup.IProvideValueTarget.TargetProperty%2A>。</span><span class="sxs-lookup"><span data-stu-id="6bd21-204">**Service APIs:**  <xref:System.Windows.Markup.IProvideValueTarget.TargetObject%2A>, <xref:System.Windows.Markup.IProvideValueTarget.TargetProperty%2A>.</span></span>  
  
 <span data-ttu-id="6bd21-205"><xref:System.Windows.Markup.IProvideValueTarget> 可讓類型轉換器或標記延伸取得有關其在載入時之作用位置的內容。</span><span class="sxs-lookup"><span data-stu-id="6bd21-205"><xref:System.Windows.Markup.IProvideValueTarget> enables a type converter or markup extension to obtain context about where it is acting at load time.</span></span> <span data-ttu-id="6bd21-206">實作可以使用這個內容讓某個使用方式無效。</span><span class="sxs-lookup"><span data-stu-id="6bd21-206">Implementations might use this context to invalidate a usage.</span></span> <span data-ttu-id="6bd21-207">例如，WPF 在其某些標記延伸 (例如 <xref:System.Windows.DynamicResourceExtension>) 內具有邏輯。</span><span class="sxs-lookup"><span data-stu-id="6bd21-207">For example, WPF has logic inside some of its markup extensions such as <xref:System.Windows.DynamicResourceExtension>.</span></span> <span data-ttu-id="6bd21-208">這個邏輯會檢查 <xref:System.Windows.Markup.IProvideValueTarget.TargetProperty%2A> ，以確定該延伸只會用來設定相依性屬性 (或其他非相依性屬性的簡短清單)。</span><span class="sxs-lookup"><span data-stu-id="6bd21-208">The logic checks the <xref:System.Windows.Markup.IProvideValueTarget.TargetProperty%2A> to make sure that the extension is only used to set dependency properties (or a short list of other non-dependency properties).</span></span>  
  
### <a name="ixamlnameresolver"></a><span data-ttu-id="6bd21-209">IXamlNameResolver</span><span class="sxs-lookup"><span data-stu-id="6bd21-209">IXamlNameResolver</span></span>  
 <span data-ttu-id="6bd21-210">**T:System.Xaml.IDestinationTypeProvider**中查詢服務： <xref:System.Xaml.IXamlNameResolver></span><span class="sxs-lookup"><span data-stu-id="6bd21-210">**Reference documentation**: <xref:System.Xaml.IXamlNameResolver></span></span>  
  
 <span data-ttu-id="6bd21-211">**T:System.Xaml.IDestinationTypeProvider**  <xref:System.Xaml> 命名空間、System.Xaml 組件</span><span class="sxs-lookup"><span data-stu-id="6bd21-211">**Defined by:**  <xref:System.Xaml> namespace, System.Xaml assembly</span></span>  
  
 <span data-ttu-id="6bd21-212">**與：** 載入路徑物件圖形定義，並解決所識別的物件`x:Name`， `x:Reference`，或架構特定技術。</span><span class="sxs-lookup"><span data-stu-id="6bd21-212">**Relevant to:** Load path object graph definition, resolving objects identified by `x:Name`, `x:Reference`, or framework-specific techniques.</span></span>  
  
 <span data-ttu-id="6bd21-213">**T:System.Xaml.IDestinationTypeProvider**  <xref:System.Xaml.IXamlNameResolver.Resolve%2A>；其他適用於進階情節 (例如處理向前參考) 的 API。</span><span class="sxs-lookup"><span data-stu-id="6bd21-213">**Service APIs:**  <xref:System.Xaml.IXamlNameResolver.Resolve%2A>; other APIs for more advanced scenarios such as dealing with forward references.</span></span>  
  
 <span data-ttu-id="6bd21-214">.NET Framework XAML 服務所實作的 `x:Reference` 處理依賴這項服務。</span><span class="sxs-lookup"><span data-stu-id="6bd21-214">The .NET Framework XAML Services implementation of `x:Reference` handling relies on this service.</span></span> <span data-ttu-id="6bd21-215">特定架構或是支援該架構的工具，會使用這項服務來處理 `x:Name` 或是已用<xref:System.Windows.Markup.RuntimeNamePropertyAttribute> 屬性化(Attributed) 的對等屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="6bd21-215">Specific frameworks or tools that support the framework use this service for `x:Name` handling or equivalent (<xref:System.Windows.Markup.RuntimeNamePropertyAttribute> attributed) property handling.</span></span>  
  
### <a name="idestinationtypeprovider"></a><span data-ttu-id="6bd21-216">IDestinationTypeProvider</span><span class="sxs-lookup"><span data-stu-id="6bd21-216">IDestinationTypeProvider</span></span>  
 <span data-ttu-id="6bd21-217">**T:System.Xaml.IDestinationTypeProvider**中查詢服務： <xref:System.Xaml.IDestinationTypeProvider></span><span class="sxs-lookup"><span data-stu-id="6bd21-217">**Reference documentation**: <xref:System.Xaml.IDestinationTypeProvider></span></span>  
  
 <span data-ttu-id="6bd21-218">**T:System.Xaml.IDestinationTypeProvider**  <xref:System.Xaml> 命名空間、System.Xaml 組件</span><span class="sxs-lookup"><span data-stu-id="6bd21-218">**Defined by:**  <xref:System.Xaml> namespace, System.Xaml assembly</span></span>  
  
 <span data-ttu-id="6bd21-219">**與：** 載入路徑解析間接 CLR 類型資訊。</span><span class="sxs-lookup"><span data-stu-id="6bd21-219">**Relevant to:** Load path resolution of indirect CLR type information.</span></span>  
  
 <span data-ttu-id="6bd21-220">**服務 API：** <xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A></span><span class="sxs-lookup"><span data-stu-id="6bd21-220">**Service API:** <xref:System.Xaml.IDestinationTypeProvider.GetDestinationType%2A></span></span>  
  
 <span data-ttu-id="6bd21-221">如需詳細資訊，請參閱<xref:System.Xaml.IDestinationTypeProvider>。</span><span class="sxs-lookup"><span data-stu-id="6bd21-221">For more information, see <xref:System.Xaml.IDestinationTypeProvider>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bd21-222">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6bd21-222">See also</span></span>

- <xref:System.Windows.Markup.MarkupExtension>
- <xref:System.Xaml.XamlObjectWriter>
- [<span data-ttu-id="6bd21-223">XAML 標記延伸概觀</span><span class="sxs-lookup"><span data-stu-id="6bd21-223">Markup Extensions for XAML Overview</span></span>](markup-extensions-for-xaml-overview.md)
- [<span data-ttu-id="6bd21-224">XAML 類型轉換子概觀</span><span class="sxs-lookup"><span data-stu-id="6bd21-224">Type Converters for XAML Overview</span></span>](type-converters-for-xaml-overview.md)
