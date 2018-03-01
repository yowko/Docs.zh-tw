---
title: "自訂類型和程式庫的 XAML 相關 CLR 屬性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CLR attributes for custom types [XAML Services]
ms.assetid: 5dfb299a-b6e2-41b8-8694-e6ac987547f1
caps.latest.revision: 
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 25aac1d4478279561cbcdda6c1cf912c3c3b2cde
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="xaml-related-clr-attributes-for-custom-types-and-libraries"></a><span data-ttu-id="69fa1-102">自訂類型和程式庫的 XAML 相關 CLR 屬性</span><span class="sxs-lookup"><span data-stu-id="69fa1-102">XAML-Related CLR Attributes for Custom Types and Libraries</span></span>
<span data-ttu-id="69fa1-103">本主題會描述通用語言執行階段 (CLR) 屬性所定義的.NET Framework XAML 服務。</span><span class="sxs-lookup"><span data-stu-id="69fa1-103">This topic describes the common language runtime (CLR) attributes that are defined by .NET Framework XAML Services.</span></span> <span data-ttu-id="69fa1-104">它也會說明其他 CLR 具有的屬性定義在.NET Framework 組件或類型的應用程式的 XAML 相關案例。</span><span class="sxs-lookup"><span data-stu-id="69fa1-104">It also describes other CLR attributes that are defined in the .NET Framework that have a XAML-related scenario for application to assemblies or types.</span></span> <span data-ttu-id="69fa1-105">屬性的組件、 類型或成員設定這些 CLR 屬性提供 XAML 類型系統資訊與您的型別。</span><span class="sxs-lookup"><span data-stu-id="69fa1-105">Attributing assemblies, types, or members with these CLR attributes provides XAML type system information related to your types.</span></span> <span data-ttu-id="69fa1-106">任何直接處理 XAML 節點資料流，或透過專用的 XAML 讀取器和 XAML 寫入器會使用.NET Framework XAML 服務的 XAML 取用者會提供資訊。</span><span class="sxs-lookup"><span data-stu-id="69fa1-106">Information is provided to any XAML consumer that uses .NET Framework XAML Services for processing the XAML node stream directly or through the dedicated XAML readers and XAML writers.</span></span>  
  
## <a name="xaml-related-clr-attributes-for-custom-types-and-custom-members"></a><span data-ttu-id="69fa1-107">自訂型別和自訂成員的 XAML 相關 CLR 屬性</span><span class="sxs-lookup"><span data-stu-id="69fa1-107">XAML-Related CLR Attributes for Custom Types and Custom Members</span></span>  
 <span data-ttu-id="69fa1-108">使用 CLR 屬性牽涉到您用來定義您的型別整體的 CLR，否則不可以使用這類屬性。</span><span class="sxs-lookup"><span data-stu-id="69fa1-108">Using CLR attributes entails that you are using the overall CLR to define your types, otherwise such attributes are not available.</span></span> <span data-ttu-id="69fa1-109">如果您使用 CLR 定義支援的型別時，.NET Framework XAML 服務 XAML 寫入器所使用的預設 XAML 結構描述內容可以讀取透過反映來針對備份組件的 CLR 屬性。</span><span class="sxs-lookup"><span data-stu-id="69fa1-109">If you use the CLR to define type backing, then the default XAML schema context used by .NET  Framework XAML Services XAML writers can read CLR attribution through reflection against backing assemblies.</span></span>  
  
 <span data-ttu-id="69fa1-110">下列各節說明您可以套用至自訂類型或自訂成員的 XAML 相關屬性。</span><span class="sxs-lookup"><span data-stu-id="69fa1-110">The following sections describe the XAML-related attributes that you can apply to custom types or custom members.</span></span> <span data-ttu-id="69fa1-111">每個 CLR 屬性通訊與 XAML 類型系統有關的資訊。</span><span class="sxs-lookup"><span data-stu-id="69fa1-111">Each CLR attribute communicates information that is relevant to a XAML type system.</span></span> <span data-ttu-id="69fa1-112">在載入路徑中，屬性化的資訊可能有助於形成有效的 XAML 節點資料流，XAML 讀取器或它可協助產生有效的物件圖形的 XAML 寫入器。</span><span class="sxs-lookup"><span data-stu-id="69fa1-112">In the load path, the attributed information either helps the XAML reader form a valid XAML node stream, or it helps the XAML writer produce a valid object graph.</span></span> <span data-ttu-id="69fa1-113">在儲存路徑，是可幫助形成有效的 XAML 節點資料流，XAML 類型系統資訊，重新組成的 XAML 讀取器的屬性的資訊或其宣告序列化提示或 XAML 寫入器或其他 XAML 取用者的需求。</span><span class="sxs-lookup"><span data-stu-id="69fa1-113">In the save path, the attributed information either helps the XAML reader form a valid XAML node stream that reconstitutes XAML type system information; or it declares serialization hints or requirements for the XAML writer or other XAML consumers.</span></span>  
  
### <a name="ambientattribute"></a><span data-ttu-id="69fa1-114">AmbientAttribute</span><span class="sxs-lookup"><span data-stu-id="69fa1-114">AmbientAttribute</span></span>  
 <span data-ttu-id="69fa1-115">**參考文件：**  <xref:System.Windows.Markup.AmbientAttribute></span><span class="sxs-lookup"><span data-stu-id="69fa1-115">**Reference Documentation:**  <xref:System.Windows.Markup.AmbientAttribute></span></span>  
  
 <span data-ttu-id="69fa1-116">**適用於：**類別屬性，或`get`支援可附加屬性的存取子成員。</span><span class="sxs-lookup"><span data-stu-id="69fa1-116">**Applies to:** Class, property, or `get` accessor members that support attachable properties.</span></span>  
  
 <span data-ttu-id="69fa1-117">**引數：**無</span><span class="sxs-lookup"><span data-stu-id="69fa1-117">**Arguments:** None</span></span>  
  
 <span data-ttu-id="69fa1-118"><xref:System.Windows.Markup.AmbientAttribute>表示屬性或使用屬性化型別的所有屬性，應在 XAML 中的環境屬性概念解譯。</span><span class="sxs-lookup"><span data-stu-id="69fa1-118"><xref:System.Windows.Markup.AmbientAttribute> indicates that the property, or all properties that take the attributed type, should be interpreted under the ambient property concept in XAML.</span></span> <span data-ttu-id="69fa1-119">環境概念與 XAML 處理器如何判斷成員類別擁有者有關。</span><span class="sxs-lookup"><span data-stu-id="69fa1-119">The ambient concept relates to how XAML processors determine type owners of members.</span></span> <span data-ttu-id="69fa1-120">環境的屬性是屬性預期的可供使用的剖析器的內容中建立物件圖形，但在暫止立即的 XAML 節點集所建立的一般型別成員查閱值。</span><span class="sxs-lookup"><span data-stu-id="69fa1-120">An ambient property is a property where the value is expected to be available in the parser context when creating an object graph, but where typical type-member lookup is suspended for the immediate XAML node set being created.</span></span>  
  
 <span data-ttu-id="69fa1-121">環境概念可以套用到可附加成員，不會表示為 CLR 屬性會定義如何根據屬性<xref:System.AttributeTargets>。</span><span class="sxs-lookup"><span data-stu-id="69fa1-121">The ambient concept can be applied to attachable members, which are not represented as properties in terms of how CLR attribution defines <xref:System.AttributeTargets>.</span></span> <span data-ttu-id="69fa1-122">方法屬性使用方式應該只是套用`get`xaml 支援可附加的使用方式的存取子。</span><span class="sxs-lookup"><span data-stu-id="69fa1-122">The method attribution usage should be applied only in the case of a `get` accessor that supports attachable usage for XAML.</span></span>  
  
### <a name="constructorargumentattribute"></a><span data-ttu-id="69fa1-123">ConstructorArgumentAttribute</span><span class="sxs-lookup"><span data-stu-id="69fa1-123">ConstructorArgumentAttribute</span></span>  
 <span data-ttu-id="69fa1-124">**參考文件：**  <xref:System.Windows.Markup.ConstructorArgumentAttribute></span><span class="sxs-lookup"><span data-stu-id="69fa1-124">**Reference Documentation:**  <xref:System.Windows.Markup.ConstructorArgumentAttribute></span></span>  
  
 <span data-ttu-id="69fa1-125">**適用於：**類別</span><span class="sxs-lookup"><span data-stu-id="69fa1-125">**Applies to:** Class</span></span>  
  
 <span data-ttu-id="69fa1-126">**引數：**指定比對單一建構函式引數的屬性名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="69fa1-126">**Arguments:** A string that specifies the name of the property that matches a single constructor argument.</span></span>  
  
 <span data-ttu-id="69fa1-127"><xref:System.Windows.Markup.ConstructorArgumentAttribute>指定可以使用非預設建構函式語法中初始化物件，並指定名稱的屬性提供建構資訊。</span><span class="sxs-lookup"><span data-stu-id="69fa1-127"><xref:System.Windows.Markup.ConstructorArgumentAttribute> specifies that an object can be initialized by using a non-default constructor syntax, and that a property of the specified name supplies construction information.</span></span> <span data-ttu-id="69fa1-128">這項資訊主要供 XAML 序列化之用。</span><span class="sxs-lookup"><span data-stu-id="69fa1-128">This information is primarily for XAML serialization.</span></span> <span data-ttu-id="69fa1-129">如需詳細資訊，請參閱<xref:System.Windows.Markup.ConstructorArgumentAttribute>。</span><span class="sxs-lookup"><span data-stu-id="69fa1-129">For more information, see <xref:System.Windows.Markup.ConstructorArgumentAttribute>.</span></span>  
  
### <a name="contentpropertyattribute"></a><span data-ttu-id="69fa1-130">ContentPropertyAttribute</span><span class="sxs-lookup"><span data-stu-id="69fa1-130">ContentPropertyAttribute</span></span>  
 <span data-ttu-id="69fa1-131">**參考文件：**  <xref:System.Windows.Markup.ContentPropertyAttribute></span><span class="sxs-lookup"><span data-stu-id="69fa1-131">**Reference Documentation:**  <xref:System.Windows.Markup.ContentPropertyAttribute></span></span>  
  
 <span data-ttu-id="69fa1-132">**適用於：**類別</span><span class="sxs-lookup"><span data-stu-id="69fa1-132">**Applies to:** Class</span></span>  
  
 <span data-ttu-id="69fa1-133">**引數：**指定成員的屬性化型別名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="69fa1-133">**Arguments:** A string that specifies the name of a member of the attributed type.</span></span>  
  
 <span data-ttu-id="69fa1-134"><xref:System.Windows.Markup.ContentPropertyAttribute>表示引數所命名的屬性應該做為該類型的 XAML 內容屬性。</span><span class="sxs-lookup"><span data-stu-id="69fa1-134"><xref:System.Windows.Markup.ContentPropertyAttribute> indicates that the property as named by the argument should serve as the XAML content property for that type.</span></span> <span data-ttu-id="69fa1-135">XAML 內容屬性定義會繼承所有可指派給定義類型的衍生型別。</span><span class="sxs-lookup"><span data-stu-id="69fa1-135">The XAML content property definition inherits to all derived types that are assignable to the defining type.</span></span> <span data-ttu-id="69fa1-136">您可以藉由套用覆寫特定衍生類型上的定義<xref:System.Windows.Markup.ContentPropertyAttribute>特定衍生型別。</span><span class="sxs-lookup"><span data-stu-id="69fa1-136">You can override the definition on a specific derived type by applying <xref:System.Windows.Markup.ContentPropertyAttribute> on the specific derived type.</span></span>  
  
 <span data-ttu-id="69fa1-137">做為 XAML 內容屬性的屬性，可以省略屬性標記的屬性項目中 XAML 用法。</span><span class="sxs-lookup"><span data-stu-id="69fa1-137">For the property that serves as the XAML content property, property element tagging for the property can be omitted in the XAML usage.</span></span> <span data-ttu-id="69fa1-138">一般而言，您會指定升級的內容和內含項目模型簡化的 XAML 標記的 XAML 內容屬性。</span><span class="sxs-lookup"><span data-stu-id="69fa1-138">Typically, you designate XAML content properties that promote a streamlined XAML markup for your content and containment models.</span></span> <span data-ttu-id="69fa1-139">因為只有一個成員可以指定為 XAML 內容屬性中，您有時候必須設計選擇，可以讓數個容器的哪些類型的屬性應該指定為 XAML 內容屬性。</span><span class="sxs-lookup"><span data-stu-id="69fa1-139">Because only one member can be designated as the XAML content property, you sometimes have design choices to make regarding which of several container properties of a type should be designated as the XAML content property.</span></span> <span data-ttu-id="69fa1-140">其他容器屬性必須使用具有明確的屬性項目。</span><span class="sxs-lookup"><span data-stu-id="69fa1-140">The other container properties must be used with explicit property elements.</span></span>  
  
 <span data-ttu-id="69fa1-141">在 XAML 節點資料流，XAML 內容屬性，仍可能產生`StartMember`和`EndMember`使用的屬性名稱的節點<xref:System.Xaml.XamlMember>。</span><span class="sxs-lookup"><span data-stu-id="69fa1-141">In the XAML node stream, XAML content properties still produce `StartMember` and `EndMember` nodes, using the name of the property for the <xref:System.Xaml.XamlMember>.</span></span> <span data-ttu-id="69fa1-142">若要判斷成員是否為 XAML 內容屬性，檢查<xref:System.Xaml.XamlType>值`StartObject`定位和取得的值， <xref:System.Xaml.XamlType.ContentProperty%2A>。</span><span class="sxs-lookup"><span data-stu-id="69fa1-142">To determine whether a member is the XAML content property, examine the <xref:System.Xaml.XamlType> value from the `StartObject` position and obtain the value of <xref:System.Xaml.XamlType.ContentProperty%2A>.</span></span>  
  
### <a name="contentwrapperattribute"></a><span data-ttu-id="69fa1-143">ContentWrapperAttribute</span><span class="sxs-lookup"><span data-stu-id="69fa1-143">ContentWrapperAttribute</span></span>  
 <span data-ttu-id="69fa1-144">**參考文件：**  <xref:System.Windows.Markup.ContentWrapperAttribute></span><span class="sxs-lookup"><span data-stu-id="69fa1-144">**Reference Documentation:**  <xref:System.Windows.Markup.ContentWrapperAttribute></span></span>  
  
 <span data-ttu-id="69fa1-145">**適用於：**類別，尤其是集合型別。</span><span class="sxs-lookup"><span data-stu-id="69fa1-145">**Applies to:** Class, specifically collection types.</span></span>  
  
 <span data-ttu-id="69fa1-146">**引數：** A <xref:System.Type> ，指定要使用的內容包裝函式類型做為外部內容類型。</span><span class="sxs-lookup"><span data-stu-id="69fa1-146">**Arguments:** A <xref:System.Type> that specifies the type to use as the content wrapper type for foreign content.</span></span>  
  
 <span data-ttu-id="69fa1-147"><xref:System.Windows.Markup.ContentWrapperAttribute>將用來包裝外部內容的相關聯的集合型別上指定一個或多個類型。</span><span class="sxs-lookup"><span data-stu-id="69fa1-147"><xref:System.Windows.Markup.ContentWrapperAttribute> specifies one or more types on the associated collection type that will be used to wrap foreign content.</span></span> <span data-ttu-id="69fa1-148">外部內容是指其中內容屬性的型別上的型別系統條件約束沒有擷取所有可能的擁有者類型的 XAML 用法原本支援的內容案例的情況下。</span><span class="sxs-lookup"><span data-stu-id="69fa1-148">Foreign content refers to cases where the type system constraints on the type of the content property do not capture all of the possible content cases that XAML usage for the owning type would support.</span></span> <span data-ttu-id="69fa1-149">比方說，XAML 支援特定類型的內容可能會支援字串中的強型別的泛型<xref:System.Collections.ObjectModel.Collection%601>。</span><span class="sxs-lookup"><span data-stu-id="69fa1-149">For example, XAML support for content of a particular type might support strings in a strongly typed generic <xref:System.Collections.ObjectModel.Collection%601>.</span></span> <span data-ttu-id="69fa1-150">內容包裝函式可用於為 XAML 的概念，可指派值的集合，例如移轉相關的文字內容模型的移轉預先存在的標記慣例。</span><span class="sxs-lookup"><span data-stu-id="69fa1-150">Content wrappers are useful for migrating preexisting markup conventions into XAML's conception of assignable values for collections, such as migrating text-related content models.</span></span>  
  
 <span data-ttu-id="69fa1-151">若要指定多個內容包裝函式類型，將屬性套用多次。</span><span class="sxs-lookup"><span data-stu-id="69fa1-151">To specify more than one content wrapper type, apply the attribute multiple times.</span></span>  
  
### <a name="dependsonattribute"></a><span data-ttu-id="69fa1-152">DependsOnAttribute</span><span class="sxs-lookup"><span data-stu-id="69fa1-152">DependsOnAttribute</span></span>  
 <span data-ttu-id="69fa1-153">**參考文件：**  <xref:System.Windows.Markup.DependsOnAttribute></span><span class="sxs-lookup"><span data-stu-id="69fa1-153">**Reference Documentation:**  <xref:System.Windows.Markup.DependsOnAttribute></span></span>  
  
 <span data-ttu-id="69fa1-154">**適用於：**屬性</span><span class="sxs-lookup"><span data-stu-id="69fa1-154">**Applies to:** Property</span></span>  
  
 <span data-ttu-id="69fa1-155">**引數：**字串，指定的屬性化類型的另一個成員的名稱。</span><span class="sxs-lookup"><span data-stu-id="69fa1-155">**Arguments:** A string that specifies the name of another member of the attributed type.</span></span>  
  
 <span data-ttu-id="69fa1-156"><xref:System.Windows.Markup.DependsOnAttribute>表示屬性化的屬性，取決於另一個屬性的值。</span><span class="sxs-lookup"><span data-stu-id="69fa1-156"><xref:System.Windows.Markup.DependsOnAttribute> indicates that the attributed property depends on the value of another property.</span></span> <span data-ttu-id="69fa1-157">將此屬性套用至屬性定義，可確保相依的屬性，會先處理 XAML 物件寫入。</span><span class="sxs-lookup"><span data-stu-id="69fa1-157">Applying this attribute to a property definition ensures that the dependent properties are processed first in XAML object writing.</span></span> <span data-ttu-id="69fa1-158">使用方式的<xref:System.Windows.Markup.DependsOnAttribute>建立有效的物件必須遵循剖析特定順序的型別上指定例外的情況下的屬性。</span><span class="sxs-lookup"><span data-stu-id="69fa1-158">Usages of <xref:System.Windows.Markup.DependsOnAttribute> specify the exceptional cases of properties on types where a specific order of parsing must be followed for valid object creation.</span></span>  
  
 <span data-ttu-id="69fa1-159">您可以套用多個<xref:System.Windows.Markup.DependsOnAttribute>至屬性定義的情況。</span><span class="sxs-lookup"><span data-stu-id="69fa1-159">You can apply multiple <xref:System.Windows.Markup.DependsOnAttribute> cases to a property definition.</span></span>  
  
### <a name="markupextensionreturntypeattribute"></a><span data-ttu-id="69fa1-160">MarkupExtensionReturnTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="69fa1-160">MarkupExtensionReturnTypeAttribute</span></span>  
 <span data-ttu-id="69fa1-161">**參考文件：**  <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute></span><span class="sxs-lookup"><span data-stu-id="69fa1-161">**Reference Documentation:**  <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute></span></span>  
  
 <span data-ttu-id="69fa1-162">**適用於：**類別，應該是<xref:System.Windows.Markup.MarkupExtension>衍生型別。</span><span class="sxs-lookup"><span data-stu-id="69fa1-162">**Applies to:** Class, which is expected to be a <xref:System.Windows.Markup.MarkupExtension> derived type.</span></span>  
  
 <span data-ttu-id="69fa1-163">**引數：** A <xref:System.Type> ，指定最精確的類型，預期為`ProvideValue`結果的屬性化<xref:System.Windows.Markup.MarkupExtension>。</span><span class="sxs-lookup"><span data-stu-id="69fa1-163">**Arguments:** A <xref:System.Type> that specifies the most precise type to expect as the `ProvideValue` result of the attributed <xref:System.Windows.Markup.MarkupExtension>.</span></span>  
  
 <span data-ttu-id="69fa1-164">如需詳細資訊，請參閱[標記延伸 XAML 概觀](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="69fa1-164">For more information, see [Markup Extensions for XAML Overview](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).</span></span>  
  
### <a name="namescopepropertyattribute"></a><span data-ttu-id="69fa1-165">NameScopePropertyAttribute</span><span class="sxs-lookup"><span data-stu-id="69fa1-165">NameScopePropertyAttribute</span></span>  
 <span data-ttu-id="69fa1-166">**參考文件：**  <xref:System.Windows.Markup.NameScopePropertyAttribute></span><span class="sxs-lookup"><span data-stu-id="69fa1-166">**Reference Documentation:**  <xref:System.Windows.Markup.NameScopePropertyAttribute></span></span>  
  
 <span data-ttu-id="69fa1-167">**適用於：**類別</span><span class="sxs-lookup"><span data-stu-id="69fa1-167">**Applies to:** Class</span></span>  
  
 <span data-ttu-id="69fa1-168">**引數：**支援兩種屬性：</span><span class="sxs-lookup"><span data-stu-id="69fa1-168">**Arguments:** Supports two forms of attribution:</span></span>  
  
-   <span data-ttu-id="69fa1-169">屬性化型別指定的屬性名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="69fa1-169">A string that specifies the name of a property on the attributed type.</span></span>  
  
-   <span data-ttu-id="69fa1-170">字串，指定屬性的名稱，以及<xref:System.Type>所定義之具名的屬性的類型。</span><span class="sxs-lookup"><span data-stu-id="69fa1-170">A string that specifies the name of a property, and a <xref:System.Type> for the type that defines the named property.</span></span> <span data-ttu-id="69fa1-171">這種形式是為 XAML namescope 屬性指定可附加的成員。</span><span class="sxs-lookup"><span data-stu-id="69fa1-171">This form is for specifying an attachable member as the XAML namescope property.</span></span>  
  
 <span data-ttu-id="69fa1-172"><xref:System.Windows.Markup.NameScopePropertyAttribute>指定提供 XAML namescope 值屬性化類別的屬性。</span><span class="sxs-lookup"><span data-stu-id="69fa1-172"><xref:System.Windows.Markup.NameScopePropertyAttribute> specifies a property that provides the XAML namescope value for the attributed class.</span></span> <span data-ttu-id="69fa1-173">XAML namescope 屬性應參考該物件會實作<xref:System.Windows.Markup.INameScope>和保存實際的 XAML 名稱範圍，其存放區，其行為。</span><span class="sxs-lookup"><span data-stu-id="69fa1-173">The XAML namescope property is expected to reference an object that implements <xref:System.Windows.Markup.INameScope> and holds the actual XAML namescope, its store, and its behavior.</span></span>  
  
### <a name="runtimenamepropertyattribute"></a><span data-ttu-id="69fa1-174">RuntimeNamePropertyAttribute</span><span class="sxs-lookup"><span data-stu-id="69fa1-174">RuntimeNamePropertyAttribute</span></span>  
 <span data-ttu-id="69fa1-175">**參考文件：**  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute></span><span class="sxs-lookup"><span data-stu-id="69fa1-175">**Reference Documentation:**  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute></span></span>  
  
 <span data-ttu-id="69fa1-176">**適用於：**類別</span><span class="sxs-lookup"><span data-stu-id="69fa1-176">**Applies to:** Class</span></span>  
  
 <span data-ttu-id="69fa1-177">**引數：**屬性化型別指定執行階段名稱屬性名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="69fa1-177">**Arguments:** A string that specifies the name of the run-time name property on the attributed type.</span></span>  
  
 <span data-ttu-id="69fa1-178"><xref:System.Windows.Markup.RuntimeNamePropertyAttribute>報告的屬性化類型對應至 XAML 屬性[X:name 指示詞](../../../docs/framework/xaml-services/x-name-directive.md)。</span><span class="sxs-lookup"><span data-stu-id="69fa1-178"><xref:System.Windows.Markup.RuntimeNamePropertyAttribute> reports a property of the attributed type that maps to the XAML [x:Name Directive](../../../docs/framework/xaml-services/x-name-directive.md).</span></span> <span data-ttu-id="69fa1-179">屬性必須是型別<xref:System.String>，而且必須是讀取/寫入。</span><span class="sxs-lookup"><span data-stu-id="69fa1-179">The property must be of type <xref:System.String> and must be read/write.</span></span>  
  
 <span data-ttu-id="69fa1-180">定義繼承所有可指派給定義類型的衍生型別。</span><span class="sxs-lookup"><span data-stu-id="69fa1-180">The definition inherits to all derived types that are assignable to the defining type.</span></span> <span data-ttu-id="69fa1-181">您可以藉由套用覆寫特定衍生類型上的定義<xref:System.Windows.Markup.RuntimeNamePropertyAttribute>特定衍生型別。</span><span class="sxs-lookup"><span data-stu-id="69fa1-181">You can override the definition on a specific derived type by applying <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> on the specific derived type.</span></span>  
  
### <a name="trimsurroundingwhitespaceattribute"></a><span data-ttu-id="69fa1-182">TrimSurroundingWhitespaceAttribute</span><span class="sxs-lookup"><span data-stu-id="69fa1-182">TrimSurroundingWhitespaceAttribute</span></span>  
 <span data-ttu-id="69fa1-183">**參考文件：**  <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute></span><span class="sxs-lookup"><span data-stu-id="69fa1-183">**Reference Documentation:**  <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute></span></span>  
  
 <span data-ttu-id="69fa1-184">**適用於：**類型</span><span class="sxs-lookup"><span data-stu-id="69fa1-184">**Applies to:** Types</span></span>  
  
 <span data-ttu-id="69fa1-185">**引數：** None。</span><span class="sxs-lookup"><span data-stu-id="69fa1-185">**Arguments:** None.</span></span>  
  
 <span data-ttu-id="69fa1-186"><xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>會套用至可能會以空白字元重要內容中的子項目出現的特定類型 (內容持有的集合，其中具有<xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>)。</span><span class="sxs-lookup"><span data-stu-id="69fa1-186"><xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute> is applied to specific types that might appear as child elements within whitespace significant content (content held by a collection that has <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>).</span></span> <span data-ttu-id="69fa1-187"><xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>大致上是相關的儲存路徑，但卻是在載入路徑 XAML 類型系統所提供藉由檢查<xref:System.Xaml.XamlType.TrimSurroundingWhitespace%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="69fa1-187"><xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute> is mainly relevant to the save path, but is available in the XAML type system in the load path by examining <xref:System.Xaml.XamlType.TrimSurroundingWhitespace%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="69fa1-188">如需詳細資訊，請參閱[XAML 中的空白字元處理](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="69fa1-188">For more information, see [Whitespace Processing in XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).</span></span>  
  
### <a name="typeconverterattribute"></a><span data-ttu-id="69fa1-189">TypeConverterAttribute</span><span class="sxs-lookup"><span data-stu-id="69fa1-189">TypeConverterAttribute</span></span>  
 <span data-ttu-id="69fa1-190">**參考文件：**  <xref:System.ComponentModel.TypeConverterAttribute></span><span class="sxs-lookup"><span data-stu-id="69fa1-190">**Reference Documentation:**  <xref:System.ComponentModel.TypeConverterAttribute></span></span>  
  
 <span data-ttu-id="69fa1-191">**適用於：**類別、 屬性、 方法 (唯一 XAML 有效的方法則是`get`存取子，支援可附加的成員)。</span><span class="sxs-lookup"><span data-stu-id="69fa1-191">**Applies to:** Class, property, method (the only XAML-valid method case is a `get` accessor that supports an attachable member).</span></span>  
  
 <span data-ttu-id="69fa1-192">**引數：** <xref:System.Type>的<xref:System.ComponentModel.TypeConverter>。</span><span class="sxs-lookup"><span data-stu-id="69fa1-192">**Arguments:** The <xref:System.Type> of the <xref:System.ComponentModel.TypeConverter>.</span></span>  
  
 <span data-ttu-id="69fa1-193"><xref:System.ComponentModel.TypeConverterAttribute>在 XAML 內容參考自訂<xref:System.ComponentModel.TypeConverter>。</span><span class="sxs-lookup"><span data-stu-id="69fa1-193"><xref:System.ComponentModel.TypeConverterAttribute> in a XAML context references a custom <xref:System.ComponentModel.TypeConverter>.</span></span> <span data-ttu-id="69fa1-194">這<xref:System.ComponentModel.TypeConverter>提供自訂型別或該類型的成員的類型轉換行為。</span><span class="sxs-lookup"><span data-stu-id="69fa1-194">This <xref:System.ComponentModel.TypeConverter> provides type conversion behavior for custom types, or members of that type.</span></span>  
  
 <span data-ttu-id="69fa1-195">您套用<xref:System.ComponentModel.TypeConverterAttribute>屬性設定為您的型別，請參考您的型別轉換子實作。</span><span class="sxs-lookup"><span data-stu-id="69fa1-195">You apply the <xref:System.ComponentModel.TypeConverterAttribute> attribute to your type, referencing your type converter implementation.</span></span> <span data-ttu-id="69fa1-196">您可以定義 XAML 的類型轉換器類別、 結構或介面。</span><span class="sxs-lookup"><span data-stu-id="69fa1-196">You can define type converters for XAML on classes, structures, or interfaces.</span></span> <span data-ttu-id="69fa1-197">您不需要提供型別轉換為列舉型別轉換已啟用原生。</span><span class="sxs-lookup"><span data-stu-id="69fa1-197">You do not need to provide type conversion for enumerations, that conversion is enabled natively.</span></span>  
  
 <span data-ttu-id="69fa1-198">類型轉換器應該能夠從字串用於屬性或在標記中，初始文字轉換預定的目的地類型轉換。</span><span class="sxs-lookup"><span data-stu-id="69fa1-198">Your type converter should be able to convert from a string that is used for attributes or initialization text in markup, into your intended destination type.</span></span> <span data-ttu-id="69fa1-199">如需詳細資訊，請參閱[TypeConverters 和 XAML](../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="69fa1-199">For more information, see [TypeConverters and XAML](../../../docs/framework/wpf/advanced/typeconverters-and-xaml.md).</span></span>  
  
 <span data-ttu-id="69fa1-200">而不是套用至所有值的類型，xaml 的類型轉換器行為可建立在特定的屬性。</span><span class="sxs-lookup"><span data-stu-id="69fa1-200">Rather than applying to all values of a type, a type converter behavior for XAML can also be established on a specific property.</span></span> <span data-ttu-id="69fa1-201">在此情況下，您將套用<xref:System.ComponentModel.TypeConverterAttribute>至 property 定義 (外部定義、 非特有`get`和`set`定義)。</span><span class="sxs-lookup"><span data-stu-id="69fa1-201">In this case, you apply <xref:System.ComponentModel.TypeConverterAttribute> to the property definition (the outer definition, not the specific `get` and `set` definitions).</span></span>  
  
 <span data-ttu-id="69fa1-202">自訂的可附加成員的 XAML 用法的類型轉換器行為可以藉由套用指派<xref:System.ComponentModel.TypeConverterAttribute>至`get`支援 XAML 用法的方法存取子。</span><span class="sxs-lookup"><span data-stu-id="69fa1-202">A type converter behavior for XAML usage of a custom attachable member can be assigned by applying <xref:System.ComponentModel.TypeConverterAttribute> to the `get` method accessor that supports the XAML usage.</span></span>  
  
 <span data-ttu-id="69fa1-203">類似於<xref:System.ComponentModel.TypeConverter>，<xref:System.ComponentModel.TypeConverterAttribute>存在於 XAML，面市之前的.NET Framework 中，而類型轉換器模型提供的其他用途。</span><span class="sxs-lookup"><span data-stu-id="69fa1-203">Similar to <xref:System.ComponentModel.TypeConverter>, <xref:System.ComponentModel.TypeConverterAttribute> existed in the .NET Framework prior to the existence of XAML, and the type converter model served other purposes.</span></span> <span data-ttu-id="69fa1-204">若要參考及使用<xref:System.ComponentModel.TypeConverterAttribute>，您必須完整限定它，或提供`using`陳述式<xref:System.ComponentModel>。</span><span class="sxs-lookup"><span data-stu-id="69fa1-204">In order to reference and use <xref:System.ComponentModel.TypeConverterAttribute>, you must fully qualify it or provide a `using` statement for <xref:System.ComponentModel>.</span></span> <span data-ttu-id="69fa1-205">您也必須包含在專案中的系統組件。</span><span class="sxs-lookup"><span data-stu-id="69fa1-205">You must also include the System assembly in your project.</span></span>  
  
### <a name="uidpropertyattribute"></a><span data-ttu-id="69fa1-206">UidPropertyAttribute</span><span class="sxs-lookup"><span data-stu-id="69fa1-206">UidPropertyAttribute</span></span>  
 <span data-ttu-id="69fa1-207">**參考文件：**  <xref:System.Windows.Markup.UidPropertyAttribute></span><span class="sxs-lookup"><span data-stu-id="69fa1-207">**Reference Documentation:**  <xref:System.Windows.Markup.UidPropertyAttribute></span></span>  
  
 <span data-ttu-id="69fa1-208">**適用於：**類別</span><span class="sxs-lookup"><span data-stu-id="69fa1-208">**Applies to:** Class</span></span>  
  
 <span data-ttu-id="69fa1-209">**引數：**參考相關的屬性名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="69fa1-209">**Arguments:** A string that references the relevant property by name.</span></span>  
  
 <span data-ttu-id="69fa1-210">表示的 CLR 屬性的類別別名[X:uid 指示詞](../../../docs/framework/xaml-services/x-uid-directive.md)。</span><span class="sxs-lookup"><span data-stu-id="69fa1-210">Indicates the CLR property of a class that aliases the [x:Uid Directive](../../../docs/framework/xaml-services/x-uid-directive.md).</span></span>  
  
### <a name="usableduringinitializationattribute"></a><span data-ttu-id="69fa1-211">UsableDuringInitializationAttribute</span><span class="sxs-lookup"><span data-stu-id="69fa1-211">UsableDuringInitializationAttribute</span></span>  
 <span data-ttu-id="69fa1-212">**參考文件：**  <xref:System.Windows.Markup.UsableDuringInitializationAttribute></span><span class="sxs-lookup"><span data-stu-id="69fa1-212">**Reference Documentation:**  <xref:System.Windows.Markup.UsableDuringInitializationAttribute></span></span>  
  
 <span data-ttu-id="69fa1-213">**適用於：**類別</span><span class="sxs-lookup"><span data-stu-id="69fa1-213">**Applies to:** Class</span></span>  
  
 <span data-ttu-id="69fa1-214">**引數：**布林值。</span><span class="sxs-lookup"><span data-stu-id="69fa1-214">**Arguments:** A Boolean.</span></span> <span data-ttu-id="69fa1-215">如果用於屬性的使用目的，這應該一律指定為`true`。</span><span class="sxs-lookup"><span data-stu-id="69fa1-215">If used for the attribute's intended purpose, this should always be specified as `true`.</span></span>  
  
 <span data-ttu-id="69fa1-216">表示這個類型是否在 XAML 物件圖形建立期間由上而下建置。</span><span class="sxs-lookup"><span data-stu-id="69fa1-216">Indicates whether this type is built top-down during XAML object graph creation.</span></span> <span data-ttu-id="69fa1-217">這是進階的概念，與您的程式設計模型的定義可能密切相關。</span><span class="sxs-lookup"><span data-stu-id="69fa1-217">This is an advanced concept, which is probably closely related to the definition of your programming model.</span></span> <span data-ttu-id="69fa1-218">如需詳細資訊，請參閱<xref:System.Windows.Markup.UsableDuringInitializationAttribute>。</span><span class="sxs-lookup"><span data-stu-id="69fa1-218">For more information, see <xref:System.Windows.Markup.UsableDuringInitializationAttribute>.</span></span>  
  
### <a name="valueserializerattribute"></a><span data-ttu-id="69fa1-219">ValueSerializerAttribute</span><span class="sxs-lookup"><span data-stu-id="69fa1-219">ValueSerializerAttribute</span></span>  
 <span data-ttu-id="69fa1-220">**參考文件：**  <xref:System.Windows.Markup.ValueSerializerAttribute></span><span class="sxs-lookup"><span data-stu-id="69fa1-220">**Reference Documentation:**  <xref:System.Windows.Markup.ValueSerializerAttribute></span></span>  
  
 <span data-ttu-id="69fa1-221">**適用於：**類別、 屬性、 方法 (唯一 XAML 有效的方法則是`get`存取子，支援可附加的成員)。</span><span class="sxs-lookup"><span data-stu-id="69fa1-221">**Applies to:** Class, property, method (the only XAML-valid method case is a `get` accessor that supports an attachable member).</span></span>  
  
 <span data-ttu-id="69fa1-222">**引數：** A<xref:System.Type>指定值序列化程式支援類別，用於在序列化的屬性化類型中，所有屬性，或是特定屬性的屬性。</span><span class="sxs-lookup"><span data-stu-id="69fa1-222">**Arguments:** A <xref:System.Type> that specifies the value serializer support class to use when serializing all properties of the attributed type, or the specific attributed property.</span></span>  
  
 <span data-ttu-id="69fa1-223"><xref:System.Windows.Markup.ValueSerializer>指定需要更多的狀態和內容的值序列化類別<xref:System.ComponentModel.TypeConverter>沒有。</span><span class="sxs-lookup"><span data-stu-id="69fa1-223"><xref:System.Windows.Markup.ValueSerializer> specifies a value serialization class that requires more state and context than a <xref:System.ComponentModel.TypeConverter> does.</span></span> <span data-ttu-id="69fa1-224"><xref:System.Windows.Markup.ValueSerializer>可以藉由套用可附加成員與相關聯<xref:System.Windows.Markup.ValueSerializerAttribute>上靜態屬性`get`可附加成員的存取子方法。</span><span class="sxs-lookup"><span data-stu-id="69fa1-224"><xref:System.Windows.Markup.ValueSerializer> can be associated with an attachable member by applying the <xref:System.Windows.Markup.ValueSerializerAttribute> attribute on the static `get` accessor method for the attachable member.</span></span> <span data-ttu-id="69fa1-225">值序列化也適用於列舉型別、 介面和結構，但不適用於委派。</span><span class="sxs-lookup"><span data-stu-id="69fa1-225">Value serialization is also applicable for enumerations, interfaces and structures, but not for delegates.</span></span>  
  
### <a name="whitespacesignificantcollectionattribute"></a><span data-ttu-id="69fa1-226">WhitespaceSignificantCollectionAttribute</span><span class="sxs-lookup"><span data-stu-id="69fa1-226">WhitespaceSignificantCollectionAttribute</span></span>  
 <span data-ttu-id="69fa1-227">**參考文件：**  <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute></span><span class="sxs-lookup"><span data-stu-id="69fa1-227">**Reference Documentation:**  <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute></span></span>  
  
 <span data-ttu-id="69fa1-228">**適用於：**類別，特別是預期的混合的內容，裝載在物件項目周圍的空白字元可能會顯著 UI 表示法的集合型別。</span><span class="sxs-lookup"><span data-stu-id="69fa1-228">**Applies to:** Class, specifically collection types that are expected to host mixed content, where white space around object elements might be significant for UI representation.</span></span>  
  
 <span data-ttu-id="69fa1-229">**引數：** None。</span><span class="sxs-lookup"><span data-stu-id="69fa1-229">**Arguments:** None.</span></span>  
  
 <span data-ttu-id="69fa1-230"><xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>表示集合型別應該處理為空白字元，XAML 處理器，會影響集合內的 XAML 節點資料流值節點建構。</span><span class="sxs-lookup"><span data-stu-id="69fa1-230"><xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> indicates that a collection type should be processed as whitespace significant by a XAML processor, which influences the construction of the XAML node stream's value nodes within the collection.</span></span> <span data-ttu-id="69fa1-231">如需詳細資訊，請參閱[XAML 中的空白字元處理](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="69fa1-231">For more information, see [Whitespace Processing in XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).</span></span>  
  
### <a name="xamldeferloadattribute"></a><span data-ttu-id="69fa1-232">XamlDeferLoadAttribute</span><span class="sxs-lookup"><span data-stu-id="69fa1-232">XamlDeferLoadAttribute</span></span>  
 <span data-ttu-id="69fa1-233">**參考文件：**  <xref:System.Windows.Markup.XamlDeferLoadAttribute></span><span class="sxs-lookup"><span data-stu-id="69fa1-233">**Reference Documentation:**  <xref:System.Windows.Markup.XamlDeferLoadAttribute></span></span>  
  
 <span data-ttu-id="69fa1-234">**適用於：**類別屬性。</span><span class="sxs-lookup"><span data-stu-id="69fa1-234">**Applies to:** Class, property.</span></span>  
  
 <span data-ttu-id="69fa1-235">**引數：**支援兩個屬性會形成類型為字串，或類型為<xref:System.Type>。</span><span class="sxs-lookup"><span data-stu-id="69fa1-235">**Arguments:** Supports two attribution forms types as strings, or types as <xref:System.Type>.</span></span> <span data-ttu-id="69fa1-236">請參閱 <xref:System.Windows.Markup.XamlDeferLoadAttribute>。</span><span class="sxs-lookup"><span data-stu-id="69fa1-236">See <xref:System.Windows.Markup.XamlDeferLoadAttribute>.</span></span>  
  
 <span data-ttu-id="69fa1-237">表示類別或屬性具有 XAML 延後的載入使用量 （例如範本行為），並報告類別，可讓延後的行為和目的地/內容型別。</span><span class="sxs-lookup"><span data-stu-id="69fa1-237">Indicates that a class or property has a deferred load usage for XAML (such as a template behavior), and reports the class that enables the deferring behavior and its destination/content type.</span></span>  
  
### <a name="xamlsetmarkupextensionattribute"></a><span data-ttu-id="69fa1-238">XamlSetMarkupExtensionAttribute</span><span class="sxs-lookup"><span data-stu-id="69fa1-238">XamlSetMarkupExtensionAttribute</span></span>  
 <span data-ttu-id="69fa1-239">**參考文件：**  <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute></span><span class="sxs-lookup"><span data-stu-id="69fa1-239">**Reference Documentation:**  <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute></span></span>  
  
 <span data-ttu-id="69fa1-240">**適用於：**類別</span><span class="sxs-lookup"><span data-stu-id="69fa1-240">**Applies to:** Class</span></span>  
  
 <span data-ttu-id="69fa1-241">**引數：**命名回呼。</span><span class="sxs-lookup"><span data-stu-id="69fa1-241">**Arguments:** Names the callback.</span></span>  
  
 <span data-ttu-id="69fa1-242">表示類別可以使用標記延伸的一個或多個屬性，提供的值，而且參考的 XAML 寫入器應該在之前執行任何屬性的類別上的標記延伸模組組作業呼叫的處理常式。</span><span class="sxs-lookup"><span data-stu-id="69fa1-242">Indicates that a class can use a markup extension to provide a value for one or more of its properties, and references a handler that a XAML writer should call before performing a markup extension set operation on any property of the class.</span></span>  
  
### <a name="xamlsettypeconverterattribute"></a><span data-ttu-id="69fa1-243">XamlSetTypeConverterAttribute</span><span class="sxs-lookup"><span data-stu-id="69fa1-243">XamlSetTypeConverterAttribute</span></span>  
 <span data-ttu-id="69fa1-244">**參考文件：**  <xref:System.Windows.Markup.XamlSetTypeConverterAttribute></span><span class="sxs-lookup"><span data-stu-id="69fa1-244">**Reference Documentation:**  <xref:System.Windows.Markup.XamlSetTypeConverterAttribute></span></span>  
  
 <span data-ttu-id="69fa1-245">**適用於：**類別</span><span class="sxs-lookup"><span data-stu-id="69fa1-245">**Applies to:** Class</span></span>  
  
 <span data-ttu-id="69fa1-246">**引數：**命名回呼。</span><span class="sxs-lookup"><span data-stu-id="69fa1-246">**Arguments:** Names the callback.</span></span>  
  
 <span data-ttu-id="69fa1-247">表示類別可以使用類型轉換器，來提供值的一個或多個屬性，而且參考的 XAML 寫入器應該在之前執行上類別的任何屬性的型別轉換子組作業呼叫的處理常式。</span><span class="sxs-lookup"><span data-stu-id="69fa1-247">Indicates that a class can use a type converter to provide a value for one or more of its properties, and references a handler that a XAML writer should call before performing a type converter set operation on any property of the class.</span></span>  
  
### <a name="xmllangpropertyattribute"></a><span data-ttu-id="69fa1-248">XmlLangPropertyAttribute</span><span class="sxs-lookup"><span data-stu-id="69fa1-248">XmlLangPropertyAttribute</span></span>  
 <span data-ttu-id="69fa1-249">**參考文件：**  <xref:System.Windows.Markup.XmlLangPropertyAttribute></span><span class="sxs-lookup"><span data-stu-id="69fa1-249">**Reference Documentation:**  <xref:System.Windows.Markup.XmlLangPropertyAttribute></span></span>  
  
 <span data-ttu-id="69fa1-250">**適用於：**類別</span><span class="sxs-lookup"><span data-stu-id="69fa1-250">**Applies to:** Class</span></span>  
  
 <span data-ttu-id="69fa1-251">**引數：**指定別名的屬性名稱的字串`xml:lang`屬性化型別上。</span><span class="sxs-lookup"><span data-stu-id="69fa1-251">**Arguments:** A string that specifies the name of the property to alias to `xml:lang` on the attributed type.</span></span>  
  
 <span data-ttu-id="69fa1-252"><xref:System.Windows.Markup.XmlLangPropertyAttribute>報告的屬性化類型對應至 XML 屬性`lang`指示詞。</span><span class="sxs-lookup"><span data-stu-id="69fa1-252"><xref:System.Windows.Markup.XmlLangPropertyAttribute> reports a property of the attributed type that maps to the XML `lang` directive.</span></span> <span data-ttu-id="69fa1-253">屬性不是一定的型別<xref:System.String>，但必須是可從 （做到這一點無法關聯型別轉換子，屬性的型別，或特定的屬性） 的字串。</span><span class="sxs-lookup"><span data-stu-id="69fa1-253">The property is not necessarily of type <xref:System.String>, but must be assignable from a string (this could be accomplished by associating a type converter with the property's type, or with the specific property).</span></span> <span data-ttu-id="69fa1-254">屬性必須是讀取/寫入。</span><span class="sxs-lookup"><span data-stu-id="69fa1-254">The property must be read/write.</span></span>  
  
 <span data-ttu-id="69fa1-255">對應的實例`xml:lang`會使執行階段物件模型而不需特別處理 XMLDOM 與已指定 XML 語言資訊的存取權。</span><span class="sxs-lookup"><span data-stu-id="69fa1-255">The scenario for mapping `xml:lang` is so that a runtime object model has access to XML-specified language information without specifically processing with an XMLDOM.</span></span>  
  
 <span data-ttu-id="69fa1-256">定義繼承所有可指派給定義類型的衍生型別。</span><span class="sxs-lookup"><span data-stu-id="69fa1-256">The definition inherits to all derived types that are assignable to the defining type.</span></span> <span data-ttu-id="69fa1-257">您可以藉由套用覆寫特定衍生類型上的定義<xref:System.Windows.Markup.XmlLangPropertyAttribute>特定衍生型別，但不常見的案例。</span><span class="sxs-lookup"><span data-stu-id="69fa1-257">You can override the definition on a specific derived type by applying <xref:System.Windows.Markup.XmlLangPropertyAttribute> on the specific derived type, although that is an uncommon scenario.</span></span>  
  
## <a name="xaml-related-clr-attributes-at-the-assembly-level"></a><span data-ttu-id="69fa1-258">組件層級的 XAML 相關 CLR 屬性</span><span class="sxs-lookup"><span data-stu-id="69fa1-258">XAML-Related CLR Attributes at the Assembly Level</span></span>  
 <span data-ttu-id="69fa1-259">下列章節說明的 XAML 相關的屬性不會套用至類型或成員定義中，但會改為套用至組件。</span><span class="sxs-lookup"><span data-stu-id="69fa1-259">The following sections describe the XAML-related attributes that are not applied to types or member definitions, but are instead applied to assemblies.</span></span> <span data-ttu-id="69fa1-260">這些屬性所相關的定義包含在 XAML 中使用的自訂型別程式庫的整體目標。</span><span class="sxs-lookup"><span data-stu-id="69fa1-260">These attributes are pertinent to the overall goal of defining a library that contains custom types to use in XAML.</span></span> <span data-ttu-id="69fa1-261">有些屬性不一定影響 XAML 節點資料流直接，但是會傳遞為使用其他取用者在節點資料流。</span><span class="sxs-lookup"><span data-stu-id="69fa1-261">Some of the attributes do not necessarily influence the XAML node stream directly, but are passed on in the node stream for other consumers to use.</span></span> <span data-ttu-id="69fa1-262">取用者的資訊包括設計環境或序列化程序需要 XAML 命名空間資訊及相關聯的前置詞資訊。</span><span class="sxs-lookup"><span data-stu-id="69fa1-262">Consumers for the information include design environments or serialization processes that need XAML namespace information and associated prefix information.</span></span> <span data-ttu-id="69fa1-263">XAML 結構描述內容 （包括.NET Framework XAML 服務預設值） 也會使用這項資訊。</span><span class="sxs-lookup"><span data-stu-id="69fa1-263">A XAML schema context (including the .NET Framework XAML Services default) also uses this information.</span></span>  
  
### <a name="xmlnscompatiblewithattribute"></a><span data-ttu-id="69fa1-264">XmlnsCompatibleWithAttribute</span><span class="sxs-lookup"><span data-stu-id="69fa1-264">XmlnsCompatibleWithAttribute</span></span>  
 <span data-ttu-id="69fa1-265">**參考文件：**  <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute></span><span class="sxs-lookup"><span data-stu-id="69fa1-265">**Reference Documentation:**  <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute></span></span>  
  
 <span data-ttu-id="69fa1-266">**引數：**</span><span class="sxs-lookup"><span data-stu-id="69fa1-266">**Arguments:**</span></span>  
  
-   <span data-ttu-id="69fa1-267">字串，指定而已 XAML 命名空間識別項。</span><span class="sxs-lookup"><span data-stu-id="69fa1-267">A string that specifies the identifier of the XAML namespace to subsume.</span></span>  
  
-   <span data-ttu-id="69fa1-268">字串，指定可以而已 XAML 命名空間，從先前的引數的 XAML 命名空間識別項。</span><span class="sxs-lookup"><span data-stu-id="69fa1-268">A string that specifies the identifier of the XAML namespace that can subsume the XAML namespace from the previous argument.</span></span>  
  
 <span data-ttu-id="69fa1-269"><xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>指定可以在另一個 XAML 命名空間建立小計的 XAML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="69fa1-269"><xref:System.Windows.Markup.XmlnsCompatibleWithAttribute> specifies that a XAML namespace can be subsumed by another XAML namespace.</span></span> <span data-ttu-id="69fa1-270">一般而言，會指出歸類 XAML 命名空間中預先定義<xref:System.Windows.Markup.XmlnsDefinitionAttribute>。</span><span class="sxs-lookup"><span data-stu-id="69fa1-270">Typically, the subsuming XAML namespace is indicated in a previously defined <xref:System.Windows.Markup.XmlnsDefinitionAttribute>.</span></span> <span data-ttu-id="69fa1-271">這項技術可用於 XAML 詞彙的文件庫中，並讓它與先前定義的標記，針對稍早的版本設定詞彙相容版本。</span><span class="sxs-lookup"><span data-stu-id="69fa1-271">This technique can be used for versioning a XAML vocabulary in a library and to make it compatible with previously defined markup against the earlier versioned vocabulary.</span></span>  
  
### <a name="xmlnsdefinitionattribute"></a><span data-ttu-id="69fa1-272">XmlnsDefinitionAttribute</span><span class="sxs-lookup"><span data-stu-id="69fa1-272">XmlnsDefinitionAttribute</span></span>  
 <span data-ttu-id="69fa1-273">**參考文件：**  <xref:System.Windows.Markup.XmlnsDefinitionAttribute></span><span class="sxs-lookup"><span data-stu-id="69fa1-273">**Reference Documentation:**  <xref:System.Windows.Markup.XmlnsDefinitionAttribute></span></span>  
  
 <span data-ttu-id="69fa1-274">**引數：**</span><span class="sxs-lookup"><span data-stu-id="69fa1-274">**Arguments:**</span></span>  
  
-   <span data-ttu-id="69fa1-275">字串，指定 XAML 命名空間定義的識別項。</span><span class="sxs-lookup"><span data-stu-id="69fa1-275">A string that specifies the identifier of the XAML namespace to define.</span></span>  
  
-   <span data-ttu-id="69fa1-276">命名的 CLR 命名空間的字串。</span><span class="sxs-lookup"><span data-stu-id="69fa1-276">A string that names a CLR namespace.</span></span> <span data-ttu-id="69fa1-277">CLR 命名空間應該組件中定義的公用型別，至少一個 CLR 命名空間類型應該用於 XAML 用法。</span><span class="sxs-lookup"><span data-stu-id="69fa1-277">The CLR namespace should define public types in your assembly, and at least one of the CLR namespace types should be intended for XAML usage.</span></span>  
  
 <span data-ttu-id="69fa1-278"><xref:System.Windows.Markup.XmlnsDefinitionAttribute>每個組件為基礎的 XAML 命名空間與 CLR 命名空間，然後使用型別解析 XAML 物件寫入器或 XAML 結構描述內容所指定的對應。</span><span class="sxs-lookup"><span data-stu-id="69fa1-278"><xref:System.Windows.Markup.XmlnsDefinitionAttribute> specifies a mapping on a per-assembly basis between a XAML namespace and a CLR namespace, which is then used for type resolution by a XAML object writer or XAML schema context.</span></span>  
  
 <span data-ttu-id="69fa1-279">多個<xref:System.Windows.Markup.XmlnsDefinitionAttribute>可以套用至組件。</span><span class="sxs-lookup"><span data-stu-id="69fa1-279">More than one <xref:System.Windows.Markup.XmlnsDefinitionAttribute> can be applied to an assembly.</span></span> <span data-ttu-id="69fa1-280">這可能會基於下列原因所造成的任何組合：</span><span class="sxs-lookup"><span data-stu-id="69fa1-280">This might be done for any combination of the following reasons:</span></span>  
  
-   <span data-ttu-id="69fa1-281">程式庫設計包含多個 CLR 命名空間的執行階段應用程式開發介面存取; 的邏輯組織不過，您會想要由 XAML 可參考相同的 XAML 命名空間在這些命名空間中的所有型別。</span><span class="sxs-lookup"><span data-stu-id="69fa1-281">The library design contains multiple CLR namespaces for logical organization of run-time API access; however, you want all types in those namespaces to be XAML-usable by referencing the same XAML namespace.</span></span> <span data-ttu-id="69fa1-282">在此情況下，套用數個<xref:System.Windows.Markup.XmlnsDefinitionAttribute>屬性使用相同<xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A>值但不同<xref:System.Windows.Markup.XmlnsDefinitionAttribute.ClrNamespace%2A>值。</span><span class="sxs-lookup"><span data-stu-id="69fa1-282">In this case, you apply several <xref:System.Windows.Markup.XmlnsDefinitionAttribute> attributes using the same <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> value but different <xref:System.Windows.Markup.XmlnsDefinitionAttribute.ClrNamespace%2A> values.</span></span> <span data-ttu-id="69fa1-283">這是特別有用，如果您要定義 framework 或應用程式想要預設 XAML 命名空間中常見的用法的 XAML 命名空間的對應。</span><span class="sxs-lookup"><span data-stu-id="69fa1-283">This is especially useful if you are defining mappings for the XAML namespace that your framework or application intends to be the default XAML namespace in common usage.</span></span>  
  
-   <span data-ttu-id="69fa1-284">程式庫設計包含多個 CLR 命名空間，而且您想刻意 XAML 命名空間的區隔這些 CLR 命名空間中類型的用法。</span><span class="sxs-lookup"><span data-stu-id="69fa1-284">The library design contains multiple CLR namespaces, and you want a deliberate XAML namespace separation between the usages of types in those CLR namespaces.</span></span>  
  
-   <span data-ttu-id="69fa1-285">您定義的 CLR 命名空間的組件，而且希望能夠透過一個以上的 XAML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="69fa1-285">You define a CLR namespace in the assembly, and you want it to be accessible through more than one XAML namespace.</span></span> <span data-ttu-id="69fa1-286">若要支援具有相同的程式碼基底的多個詞彙，就會發生此情況。</span><span class="sxs-lookup"><span data-stu-id="69fa1-286">This scenario occurs when you are supporting multiple vocabularies with the same codebase.</span></span>  
  
-   <span data-ttu-id="69fa1-287">您可以定義 XAML 語言支援一或多個 CLR 命名空間中。</span><span class="sxs-lookup"><span data-stu-id="69fa1-287">You define XAML language support in one or more CLR namespaces.</span></span> <span data-ttu-id="69fa1-288">對於這些<xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A>值應該是`http://schemas.microsoft.com/winfx/2006/xaml`。</span><span class="sxs-lookup"><span data-stu-id="69fa1-288">For these, the <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> value should be `http://schemas.microsoft.com/winfx/2006/xaml`.</span></span>  
  
### <a name="xmlnsprefixattribute"></a><span data-ttu-id="69fa1-289">XmlnsPrefixAttribute</span><span class="sxs-lookup"><span data-stu-id="69fa1-289">XmlnsPrefixAttribute</span></span>  
 <span data-ttu-id="69fa1-290">**參考文件：**  <xref:System.Windows.Markup.XmlnsPrefixAttribute></span><span class="sxs-lookup"><span data-stu-id="69fa1-290">**Reference Documentation:**  <xref:System.Windows.Markup.XmlnsPrefixAttribute></span></span>  
  
 <span data-ttu-id="69fa1-291">**引數：**</span><span class="sxs-lookup"><span data-stu-id="69fa1-291">**Arguments:**</span></span>  
  
-   <span data-ttu-id="69fa1-292">指定的 XAML 命名空間識別項的字串。</span><span class="sxs-lookup"><span data-stu-id="69fa1-292">A string that specifies the identifier of a XAML namespace.</span></span>  
  
-   <span data-ttu-id="69fa1-293">指定的建議前置詞的字串。</span><span class="sxs-lookup"><span data-stu-id="69fa1-293">A string that specifies a recommended prefix.</span></span>  
  
 <span data-ttu-id="69fa1-294"><xref:System.Windows.Markup.XmlnsDefinitionAttribute>指定要用於 XAML 命名空間的建議前置詞。</span><span class="sxs-lookup"><span data-stu-id="69fa1-294"><xref:System.Windows.Markup.XmlnsDefinitionAttribute> specifies a recommended prefix to use for a XAML namespace.</span></span> <span data-ttu-id="69fa1-295">前置詞時，寫入序列化的.NET Framework XAML 服務 XAML 檔案中的項目和屬性<xref:System.Xaml.XamlXmlWriter>，或實作 XAML 的程式庫互動設計環境具有 XAML 編輯功能。</span><span class="sxs-lookup"><span data-stu-id="69fa1-295">The prefix is useful when writing elements and attributes in a XAML file that is serialized by the .NET Framework XAML Services <xref:System.Xaml.XamlXmlWriter>, or when a XAML-implementing library interacts with a design environment that has XAML editing features.</span></span>  
  
 <span data-ttu-id="69fa1-296">多個<xref:System.Windows.Markup.XmlnsPrefixAttribute>可以套用至組件。</span><span class="sxs-lookup"><span data-stu-id="69fa1-296">More than one <xref:System.Windows.Markup.XmlnsPrefixAttribute> can be applied to an assembly.</span></span> <span data-ttu-id="69fa1-297">這可能會基於下列原因所造成的任何組合：</span><span class="sxs-lookup"><span data-stu-id="69fa1-297">This might be done for any combination of the following reasons:</span></span>  
  
-   <span data-ttu-id="69fa1-298">您的組件會定義一個以上的 XAML 命名空間的類型。</span><span class="sxs-lookup"><span data-stu-id="69fa1-298">Your assembly defines types for more than one XAML namespace.</span></span> <span data-ttu-id="69fa1-299">在此情況下，您應該定義每個 XAML 命名空間的不同前置詞值。</span><span class="sxs-lookup"><span data-stu-id="69fa1-299">In this case you should define different prefix values for each XAML namespace.</span></span>  
  
-   <span data-ttu-id="69fa1-300">您要支援多個詞彙，而且您使用不同的前置詞為每個詞彙和 XAML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="69fa1-300">You are supporting multiple vocabularies, and you use different prefixes for each vocabulary and XAML namespace.</span></span>  
  
-   <span data-ttu-id="69fa1-301">您的組件中定義 XAML 語言支援，且有<xref:System.Windows.Markup.XmlnsDefinitionAttribute>如`http://schemas.microsoft.com/winfx/2006/xaml`。</span><span class="sxs-lookup"><span data-stu-id="69fa1-301">You define XAML language support in the assembly and have a <xref:System.Windows.Markup.XmlnsDefinitionAttribute> for `http://schemas.microsoft.com/winfx/2006/xaml`.</span></span> <span data-ttu-id="69fa1-302">在此情況下，您通常應該將升級的前置詞`x`。</span><span class="sxs-lookup"><span data-stu-id="69fa1-302">In this case, you typically should promote the prefix `x`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="69fa1-303">.NET framework XAML 服務也會定義 XAML 相關屬性<xref:System.Windows.Markup.RootNamespaceAttribute>。</span><span class="sxs-lookup"><span data-stu-id="69fa1-303">.NET Framework XAML Services also defines the XAML-related attribute <xref:System.Windows.Markup.RootNamespaceAttribute>.</span></span> <span data-ttu-id="69fa1-304">這個屬性是專案系統支援，組件層級屬性，並不是與 XAML 自訂型別相關。</span><span class="sxs-lookup"><span data-stu-id="69fa1-304">This attribute is an assembly-level attribute for project system support, and it is not relevant for XAML custom types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69fa1-305">請參閱</span><span class="sxs-lookup"><span data-stu-id="69fa1-305">See Also</span></span>  
 <xref:System.Attribute>  
 [<span data-ttu-id="69fa1-306">定義可搭配 .NET Framework XAML 服務使用的自訂類型</span><span class="sxs-lookup"><span data-stu-id="69fa1-306">Defining Custom Types for Use with .NET Framework XAML Services</span></span>](../../../docs/framework/xaml-services/defining-custom-types-for-use-with-net-framework-xaml-services.md)
