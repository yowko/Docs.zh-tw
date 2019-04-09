---
title: 自訂類型和程式庫的 XAML 相關 CLR 屬性
ms.date: 03/30/2017
helpviewer_keywords:
- CLR attributes for custom types [XAML Services]
ms.assetid: 5dfb299a-b6e2-41b8-8694-e6ac987547f1
ms.openlocfilehash: ace1b40b25bd12ff7092459e468a90f382434bf4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59086204"
---
# <a name="xaml-related-clr-attributes-for-custom-types-and-libraries"></a><span data-ttu-id="9bf7b-102">自訂類型和程式庫的 XAML 相關 CLR 屬性</span><span class="sxs-lookup"><span data-stu-id="9bf7b-102">XAML-Related CLR Attributes for Custom Types and Libraries</span></span>
<span data-ttu-id="9bf7b-103">本主題描述由.NET Framework XAML 服務所定義的通用語言執行平台 (CLR) 屬性。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-103">This topic describes the common language runtime (CLR) attributes that are defined by .NET Framework XAML Services.</span></span> <span data-ttu-id="9bf7b-104">它也會說明其他 CLR 屬性定義在.NET Framework 組件或類型的應用程式的 XAML 相關案例。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-104">It also describes other CLR attributes that are defined in the .NET Framework that have a XAML-related scenario for application to assemblies or types.</span></span> <span data-ttu-id="9bf7b-105">屬性的組件、 類型或成員設定這些 CLR 屬性提供 XAML 類型系統資訊與您的型別。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-105">Attributing assemblies, types, or members with these CLR attributes provides XAML type system information related to your types.</span></span> <span data-ttu-id="9bf7b-106">處理 XAML 節點資料流直接或透過專用的 XAML 讀取器和 XAML 寫入器會使用.NET Framework XAML 服務任何 XAML 取用者會提供資訊。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-106">Information is provided to any XAML consumer that uses .NET Framework XAML Services for processing the XAML node stream directly or through the dedicated XAML readers and XAML writers.</span></span>  
  
## <a name="xaml-related-clr-attributes-for-custom-types-and-custom-members"></a><span data-ttu-id="9bf7b-107">自訂型別和自訂成員的 XAML 相關 CLR 屬性</span><span class="sxs-lookup"><span data-stu-id="9bf7b-107">XAML-Related CLR Attributes for Custom Types and Custom Members</span></span>  
 <span data-ttu-id="9bf7b-108">使用 CLR 屬性需要，您用來定義您的型別整體的 CLR，否則不提供這類屬性。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-108">Using CLR attributes entails that you are using the overall CLR to define your types, otherwise such attributes are not available.</span></span> <span data-ttu-id="9bf7b-109">如果您使用 CLR 定義的類型支援時，.NET Framework XAML 服務 XAML 寫入器所使用的預設 XAML 結構描述內容可以讀取透過反映對備份組件的 CLR 屬性。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-109">If you use the CLR to define type backing, then the default XAML schema context used by .NET  Framework XAML Services XAML writers can read CLR attribution through reflection against backing assemblies.</span></span>  
  
 <span data-ttu-id="9bf7b-110">下列各節說明您可以套用至自訂類型或自訂的成員的 XAML 相關屬性。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-110">The following sections describe the XAML-related attributes that you can apply to custom types or custom members.</span></span> <span data-ttu-id="9bf7b-111">每個 CLR 屬性會將 XAML 類型系統的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-111">Each CLR attribute communicates information that is relevant to a XAML type system.</span></span> <span data-ttu-id="9bf7b-112">在載入路徑中，屬性化的資訊可能有助於形成有效的 XAML 節點資料流，XAML 讀取器，或最好讓產生有效的物件圖形的 XAML 寫入器。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-112">In the load path, the attributed information either helps the XAML reader form a valid XAML node stream, or it helps the XAML writer produce a valid object graph.</span></span> <span data-ttu-id="9bf7b-113">在儲存路徑，是協助構成有效的 XAML 節點資料流，重組 XAML 類型系統資訊，XAML 讀取器的屬性的資訊或者，它會宣告序列化提示或 XAML 寫入器或其他 XAML 取用者需求。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-113">In the save path, the attributed information either helps the XAML reader form a valid XAML node stream that reconstitutes XAML type system information; or it declares serialization hints or requirements for the XAML writer or other XAML consumers.</span></span>  
  
### <a name="ambientattribute"></a><span data-ttu-id="9bf7b-114">AmbientAttribute</span><span class="sxs-lookup"><span data-stu-id="9bf7b-114">AmbientAttribute</span></span>  
 **<span data-ttu-id="9bf7b-115">參考文件：</span><span class="sxs-lookup"><span data-stu-id="9bf7b-115">Reference Documentation:</span></span>**  <xref:System.Windows.Markup.AmbientAttribute>  
  
 <span data-ttu-id="9bf7b-116">**適用於：** 類別、 屬性或`get`支援可附加屬性的存取子成員。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-116">**Applies to:** Class, property, or `get` accessor members that support attachable properties.</span></span>  
  
 <span data-ttu-id="9bf7b-117">**引數：** None</span><span class="sxs-lookup"><span data-stu-id="9bf7b-117">**Arguments:** None</span></span>  
  
 <xref:System.Windows.Markup.AmbientAttribute> <span data-ttu-id="9bf7b-118">指出應該解譯屬性或所有屬性的屬性化類型中，在 XAML 中的環境屬性概念。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-118">indicates that the property, or all properties that take the attributed type, should be interpreted under the ambient property concept in XAML.</span></span> <span data-ttu-id="9bf7b-119">環境概念與 XAML 處理器如何判斷成員類別擁有者有關。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-119">The ambient concept relates to how XAML processors determine type owners of members.</span></span> <span data-ttu-id="9bf7b-120">環境屬性是屬性的值，必須是可用於剖析器內容時建立物件圖形，但典型的型別成員查閱已暫止立即設定所建立的 XAML 節點。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-120">An ambient property is a property where the value is expected to be available in the parser context when creating an object graph, but where typical type-member lookup is suspended for the immediate XAML node set being created.</span></span>  
  
 <span data-ttu-id="9bf7b-121">環境概念可以套用至不會表示為方面如何定義 CLR 屬性的屬性中的可附加成員<xref:System.AttributeTargets>。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-121">The ambient concept can be applied to attachable members, which are not represented as properties in terms of how CLR attribution defines <xref:System.AttributeTargets>.</span></span> <span data-ttu-id="9bf7b-122">方法屬性使用方式應該只是套用`get`XAML 支援可附加的使用方式的存取子。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-122">The method attribution usage should be applied only in the case of a `get` accessor that supports attachable usage for XAML.</span></span>  
  
### <a name="constructorargumentattribute"></a><span data-ttu-id="9bf7b-123">ConstructorArgumentAttribute</span><span class="sxs-lookup"><span data-stu-id="9bf7b-123">ConstructorArgumentAttribute</span></span>  
 **<span data-ttu-id="9bf7b-124">參考文件：</span><span class="sxs-lookup"><span data-stu-id="9bf7b-124">Reference Documentation:</span></span>**  <xref:System.Windows.Markup.ConstructorArgumentAttribute>  
  
 <span data-ttu-id="9bf7b-125">**適用於：** 類別</span><span class="sxs-lookup"><span data-stu-id="9bf7b-125">**Applies to:** Class</span></span>  
  
 <span data-ttu-id="9bf7b-126">**引數：** 指定符合的單一建構函式引數的屬性名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-126">**Arguments:** A string that specifies the name of the property that matches a single constructor argument.</span></span>  
  
 <xref:System.Windows.Markup.ConstructorArgumentAttribute> <span data-ttu-id="9bf7b-127">指定可以使用非預設建構函式語法中初始化物件，並指定名稱的屬性提供建構資訊。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-127">specifies that an object can be initialized by using a non-default constructor syntax, and that a property of the specified name supplies construction information.</span></span> <span data-ttu-id="9bf7b-128">這項資訊主要供 XAML 序列化之用。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-128">This information is primarily for XAML serialization.</span></span> <span data-ttu-id="9bf7b-129">如需詳細資訊，請參閱<xref:System.Windows.Markup.ConstructorArgumentAttribute>。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-129">For more information, see <xref:System.Windows.Markup.ConstructorArgumentAttribute>.</span></span>  
  
### <a name="contentpropertyattribute"></a><span data-ttu-id="9bf7b-130">ContentPropertyAttribute</span><span class="sxs-lookup"><span data-stu-id="9bf7b-130">ContentPropertyAttribute</span></span>  
 **<span data-ttu-id="9bf7b-131">參考文件：</span><span class="sxs-lookup"><span data-stu-id="9bf7b-131">Reference Documentation:</span></span>**  <xref:System.Windows.Markup.ContentPropertyAttribute>  
  
 <span data-ttu-id="9bf7b-132">**適用於：** 類別</span><span class="sxs-lookup"><span data-stu-id="9bf7b-132">**Applies to:** Class</span></span>  
  
 <span data-ttu-id="9bf7b-133">**引數：** 字串，指定名稱的屬性化型別的成員。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-133">**Arguments:** A string that specifies the name of a member of the attributed type.</span></span>  
  
 <xref:System.Windows.Markup.ContentPropertyAttribute> <span data-ttu-id="9bf7b-134">表示引數所命名的屬性，應該做為該類型的 XAML 內容屬性。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-134">indicates that the property as named by the argument should serve as the XAML content property for that type.</span></span> <span data-ttu-id="9bf7b-135">XAML 內容屬性定義會繼承所有可指派給定義類型的衍生型別。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-135">The XAML content property definition inherits to all derived types that are assignable to the defining type.</span></span> <span data-ttu-id="9bf7b-136">您可以藉由套用覆寫特定的衍生型別上定義<xref:System.Windows.Markup.ContentPropertyAttribute>特定衍生型別。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-136">You can override the definition on a specific derived type by applying <xref:System.Windows.Markup.ContentPropertyAttribute> on the specific derived type.</span></span>  
  
 <span data-ttu-id="9bf7b-137">做為 XAML 內容屬性的屬性，屬性標記的屬性項目可以在 XAML 用法中省略。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-137">For the property that serves as the XAML content property, property element tagging for the property can be omitted in the XAML usage.</span></span> <span data-ttu-id="9bf7b-138">一般而言，您會指定升級您的內容和內含項目模型簡化的 XAML 標記的 XAML 內容屬性。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-138">Typically, you designate XAML content properties that promote a streamlined XAML markup for your content and containment models.</span></span> <span data-ttu-id="9bf7b-139">因為只有一個成員可以指定為 XAML 內容屬性中，有時會有數個容器的哪些類型的屬性應該指定為 XAML 內容屬性進行的設計選擇。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-139">Because only one member can be designated as the XAML content property, you sometimes have design choices to make regarding which of several container properties of a type should be designated as the XAML content property.</span></span> <span data-ttu-id="9bf7b-140">使用明確的屬性項目，必須使用其他容器屬性。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-140">The other container properties must be used with explicit property elements.</span></span>  
  
 <span data-ttu-id="9bf7b-141">在 XAML 節點資料流，XAML 內容屬性仍會產生`StartMember`並`EndMember`使用的屬性名稱的節點<xref:System.Xaml.XamlMember>。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-141">In the XAML node stream, XAML content properties still produce `StartMember` and `EndMember` nodes, using the name of the property for the <xref:System.Xaml.XamlMember>.</span></span> <span data-ttu-id="9bf7b-142">若要判斷成員是否為 XAML 內容屬性，檢查<xref:System.Xaml.XamlType>值從`StartObject`位置，並取得的值<xref:System.Xaml.XamlType.ContentProperty%2A>。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-142">To determine whether a member is the XAML content property, examine the <xref:System.Xaml.XamlType> value from the `StartObject` position and obtain the value of <xref:System.Xaml.XamlType.ContentProperty%2A>.</span></span>  
  
### <a name="contentwrapperattribute"></a><span data-ttu-id="9bf7b-143">ContentWrapperAttribute</span><span class="sxs-lookup"><span data-stu-id="9bf7b-143">ContentWrapperAttribute</span></span>  
 **<span data-ttu-id="9bf7b-144">參考文件：</span><span class="sxs-lookup"><span data-stu-id="9bf7b-144">Reference Documentation:</span></span>**  <xref:System.Windows.Markup.ContentWrapperAttribute>  
  
 <span data-ttu-id="9bf7b-145">**適用於：** 類別，尤其是集合型別。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-145">**Applies to:** Class, specifically collection types.</span></span>  
  
 <span data-ttu-id="9bf7b-146">**引數：** A <xref:System.Type> ，指定要使用的內容包裝函式型別做為外部索引內容的型別。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-146">**Arguments:** A <xref:System.Type> that specifies the type to use as the content wrapper type for foreign content.</span></span>  
  
 <xref:System.Windows.Markup.ContentWrapperAttribute> <span data-ttu-id="9bf7b-147">指定將用來包裝外部內容的相關聯的集合型別上的一個或多個類型。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-147">specifies one or more types on the associated collection type that will be used to wrap foreign content.</span></span> <span data-ttu-id="9bf7b-148">外部內容是指，型別系統條件約束，內容屬性的型別上沒有擷取所有可能內容的情況下，可支援擁有類型的 XAML 用法的案例。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-148">Foreign content refers to cases where the type system constraints on the type of the content property do not capture all of the possible content cases that XAML usage for the owning type would support.</span></span> <span data-ttu-id="9bf7b-149">比方說，XAML 支援特定類型的內容可能會在強型別泛型支援字串<xref:System.Collections.ObjectModel.Collection%601>。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-149">For example, XAML support for content of a particular type might support strings in a strongly typed generic <xref:System.Collections.ObjectModel.Collection%601>.</span></span> <span data-ttu-id="9bf7b-150">內容包裝函式可用於為 XAML 的一輩子的指派值的集合，例如移轉文字相關的內容模型移轉現有的標記慣例。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-150">Content wrappers are useful for migrating preexisting markup conventions into XAML's conception of assignable values for collections, such as migrating text-related content models.</span></span>  
  
 <span data-ttu-id="9bf7b-151">若要指定多個內容包裝函式類型，請套用屬性多次。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-151">To specify more than one content wrapper type, apply the attribute multiple times.</span></span>  
  
### <a name="dependsonattribute"></a><span data-ttu-id="9bf7b-152">DependsOnAttribute</span><span class="sxs-lookup"><span data-stu-id="9bf7b-152">DependsOnAttribute</span></span>  
 **<span data-ttu-id="9bf7b-153">參考文件：</span><span class="sxs-lookup"><span data-stu-id="9bf7b-153">Reference Documentation:</span></span>**  <xref:System.Windows.Markup.DependsOnAttribute>  
  
 <span data-ttu-id="9bf7b-154">**適用於：** 屬性</span><span class="sxs-lookup"><span data-stu-id="9bf7b-154">**Applies to:** Property</span></span>  
  
 <span data-ttu-id="9bf7b-155">**引數：** 字串，指定的屬性化類型的另一個成員的名稱。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-155">**Arguments:** A string that specifies the name of another member of the attributed type.</span></span>  
  
 <xref:System.Windows.Markup.DependsOnAttribute> <span data-ttu-id="9bf7b-156">指出屬性化的屬性相依於另一個屬性的值。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-156">indicates that the attributed property depends on the value of another property.</span></span> <span data-ttu-id="9bf7b-157">將這個屬性套用至屬性定義，可確保相依的屬性，會先處理中 XAML 物件寫入。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-157">Applying this attribute to a property definition ensures that the dependent properties are processed first in XAML object writing.</span></span> <span data-ttu-id="9bf7b-158">使用方式的<xref:System.Windows.Markup.DependsOnAttribute>其中剖析的特定順序必須遵循有效的物件建立的類型上指定屬性例外狀況。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-158">Usages of <xref:System.Windows.Markup.DependsOnAttribute> specify the exceptional cases of properties on types where a specific order of parsing must be followed for valid object creation.</span></span>  
  
 <span data-ttu-id="9bf7b-159">您可以套用多個<xref:System.Windows.Markup.DependsOnAttribute>至屬性定義的情況。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-159">You can apply multiple <xref:System.Windows.Markup.DependsOnAttribute> cases to a property definition.</span></span>  
  
### <a name="markupextensionreturntypeattribute"></a><span data-ttu-id="9bf7b-160">MarkupExtensionReturnTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="9bf7b-160">MarkupExtensionReturnTypeAttribute</span></span>  
 **<span data-ttu-id="9bf7b-161">參考文件：</span><span class="sxs-lookup"><span data-stu-id="9bf7b-161">Reference Documentation:</span></span>**  <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>  
  
 <span data-ttu-id="9bf7b-162">**適用於：** 類別，應該要<xref:System.Windows.Markup.MarkupExtension>衍生型別。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-162">**Applies to:** Class, which is expected to be a <xref:System.Windows.Markup.MarkupExtension> derived type.</span></span>  
  
 <span data-ttu-id="9bf7b-163">**引數：** A <xref:System.Type> ，指定最精確的類型為預期`ProvideValue`結果的屬性化<xref:System.Windows.Markup.MarkupExtension>。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-163">**Arguments:** A <xref:System.Type> that specifies the most precise type to expect as the `ProvideValue` result of the attributed <xref:System.Windows.Markup.MarkupExtension>.</span></span>  
  
 <span data-ttu-id="9bf7b-164">如需詳細資訊，請參閱 < [Markup Extensions for XAML Overview](markup-extensions-for-xaml-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-164">For more information, see [Markup Extensions for XAML Overview](markup-extensions-for-xaml-overview.md).</span></span>  
  
### <a name="namescopepropertyattribute"></a><span data-ttu-id="9bf7b-165">NameScopePropertyAttribute</span><span class="sxs-lookup"><span data-stu-id="9bf7b-165">NameScopePropertyAttribute</span></span>  
 **<span data-ttu-id="9bf7b-166">參考文件：</span><span class="sxs-lookup"><span data-stu-id="9bf7b-166">Reference Documentation:</span></span>**  <xref:System.Windows.Markup.NameScopePropertyAttribute>  
  
 <span data-ttu-id="9bf7b-167">**適用於：** 類別</span><span class="sxs-lookup"><span data-stu-id="9bf7b-167">**Applies to:** Class</span></span>  
  
 <span data-ttu-id="9bf7b-168">**引數：** 支援兩種形式的屬性：</span><span class="sxs-lookup"><span data-stu-id="9bf7b-168">**Arguments:** Supports two forms of attribution:</span></span>  
  
-   <span data-ttu-id="9bf7b-169">屬性化類型指定的屬性名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-169">A string that specifies the name of a property on the attributed type.</span></span>  
  
-   <span data-ttu-id="9bf7b-170">字串，指定名稱的屬性，以及<xref:System.Type>用於定義具名的屬性的型別。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-170">A string that specifies the name of a property, and a <xref:System.Type> for the type that defines the named property.</span></span> <span data-ttu-id="9bf7b-171">此表單是用來指定可附加成員的 XAML 名稱範圍屬性。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-171">This form is for specifying an attachable member as the XAML namescope property.</span></span>  
  
 <xref:System.Windows.Markup.NameScopePropertyAttribute> <span data-ttu-id="9bf7b-172">指定提供 XAML namescope 值屬性化類別的屬性。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-172">specifies a property that provides the XAML namescope value for the attributed class.</span></span> <span data-ttu-id="9bf7b-173">XAML 名稱範圍屬性應參考該物件會實作<xref:System.Windows.Markup.INameScope>並保留實際 XAML 名稱範圍，其存放區，其行為。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-173">The XAML namescope property is expected to reference an object that implements <xref:System.Windows.Markup.INameScope> and holds the actual XAML namescope, its store, and its behavior.</span></span>  
  
### <a name="runtimenamepropertyattribute"></a><span data-ttu-id="9bf7b-174">RuntimeNamePropertyAttribute</span><span class="sxs-lookup"><span data-stu-id="9bf7b-174">RuntimeNamePropertyAttribute</span></span>  
 **<span data-ttu-id="9bf7b-175">參考文件：</span><span class="sxs-lookup"><span data-stu-id="9bf7b-175">Reference Documentation:</span></span>**  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>  
  
 <span data-ttu-id="9bf7b-176">**適用於：** 類別</span><span class="sxs-lookup"><span data-stu-id="9bf7b-176">**Applies to:** Class</span></span>  
  
 <span data-ttu-id="9bf7b-177">**引數：** 字串，指定屬性化型別上的執行階段名稱屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-177">**Arguments:** A string that specifies the name of the run-time name property on the attributed type.</span></span>  
  
 <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> <span data-ttu-id="9bf7b-178">報告的屬性對應到 XAML 的屬性化型別[X:name 指示詞](x-name-directive.md)。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-178">reports a property of the attributed type that maps to the XAML [x:Name Directive](x-name-directive.md).</span></span> <span data-ttu-id="9bf7b-179">屬性必須是型別<xref:System.String>，而且必須是讀取/寫入。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-179">The property must be of type <xref:System.String> and must be read/write.</span></span>  
  
 <span data-ttu-id="9bf7b-180">定義繼承可指派給定義類型的所有衍生類型。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-180">The definition inherits to all derived types that are assignable to the defining type.</span></span> <span data-ttu-id="9bf7b-181">您可以藉由套用覆寫特定的衍生型別上定義<xref:System.Windows.Markup.RuntimeNamePropertyAttribute>特定衍生型別。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-181">You can override the definition on a specific derived type by applying <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> on the specific derived type.</span></span>  
  
### <a name="trimsurroundingwhitespaceattribute"></a><span data-ttu-id="9bf7b-182">TrimSurroundingWhitespaceAttribute</span><span class="sxs-lookup"><span data-stu-id="9bf7b-182">TrimSurroundingWhitespaceAttribute</span></span>  
 **<span data-ttu-id="9bf7b-183">參考文件：</span><span class="sxs-lookup"><span data-stu-id="9bf7b-183">Reference Documentation:</span></span>**  <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>  
  
 <span data-ttu-id="9bf7b-184">**適用於：** 型別</span><span class="sxs-lookup"><span data-stu-id="9bf7b-184">**Applies to:** Types</span></span>  
  
 <span data-ttu-id="9bf7b-185">**引數：** 無。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-185">**Arguments:** None.</span></span>  
  
 <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute> <span data-ttu-id="9bf7b-186">會套用至特定可能顯示為顯著泛空白字元的內容中的子元素的類型 (內容持有的集合，其中具有<xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>)。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-186">is applied to specific types that might appear as child elements within white-space significant content (content held by a collection that has <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>).</span></span> <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute> <span data-ttu-id="9bf7b-187">主要是與儲存的路徑，但可在載入路徑 XAML 類型系統中藉由檢查<xref:System.Xaml.XamlType.TrimSurroundingWhitespace%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-187">is mainly relevant to the save path, but is available in the XAML type system in the load path by examining <xref:System.Xaml.XamlType.TrimSurroundingWhitespace%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9bf7b-188">如需詳細資訊，請參閱 <<c0> [ 泛空白字元處理中 XAML](whitespace-processing-in-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-188">For more information, see [White-space processing in XAML](whitespace-processing-in-xaml.md).</span></span>  
  
### <a name="typeconverterattribute"></a><span data-ttu-id="9bf7b-189">TypeConverterAttribute</span><span class="sxs-lookup"><span data-stu-id="9bf7b-189">TypeConverterAttribute</span></span>  
 **<span data-ttu-id="9bf7b-190">參考文件：</span><span class="sxs-lookup"><span data-stu-id="9bf7b-190">Reference Documentation:</span></span>**  <xref:System.ComponentModel.TypeConverterAttribute>  
  
 <span data-ttu-id="9bf7b-191">**適用於：** 類別、 屬性、 方法 (唯一 XAML 有效的方法案例是`get`支援可附加成員的存取子)。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-191">**Applies to:** Class, property, method (the only XAML-valid method case is a `get` accessor that supports an attachable member).</span></span>  
  
 <span data-ttu-id="9bf7b-192">**引數：**<xref:System.Type> 的 <xref:System.ComponentModel.TypeConverter>。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-192">**Arguments:** The <xref:System.Type> of the <xref:System.ComponentModel.TypeConverter>.</span></span>  
  
 <xref:System.ComponentModel.TypeConverterAttribute> <span data-ttu-id="9bf7b-193">在 XAML 內容參考自訂<xref:System.ComponentModel.TypeConverter>。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-193">in a XAML context references a custom <xref:System.ComponentModel.TypeConverter>.</span></span> <span data-ttu-id="9bf7b-194">這<xref:System.ComponentModel.TypeConverter>提供自訂型別，或該類型的成員的型別轉換行為。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-194">This <xref:System.ComponentModel.TypeConverter> provides type conversion behavior for custom types, or members of that type.</span></span>  
  
 <span data-ttu-id="9bf7b-195">您套用<xref:System.ComponentModel.TypeConverterAttribute>屬性設定為您的型別，參考型別轉換子實作。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-195">You apply the <xref:System.ComponentModel.TypeConverterAttribute> attribute to your type, referencing your type converter implementation.</span></span> <span data-ttu-id="9bf7b-196">您可以定義為 XAML 型別轉換子類別、 結構或介面。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-196">You can define type converters for XAML on classes, structures, or interfaces.</span></span> <span data-ttu-id="9bf7b-197">您不需要提供的列舉型別轉換，轉換會以原生方式啟用。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-197">You do not need to provide type conversion for enumerations, that conversion is enabled natively.</span></span>  
  
 <span data-ttu-id="9bf7b-198">您的型別轉換子，應該能夠從或所用的屬性初始設定文字在標記中，為您想要的目的地類型的字串轉換。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-198">Your type converter should be able to convert from a string that is used for attributes or initialization text in markup, into your intended destination type.</span></span> <span data-ttu-id="9bf7b-199">如需詳細資訊，請參閱 < [TypeConverters 和 XAML](../wpf/advanced/typeconverters-and-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-199">For more information, see [TypeConverters and XAML](../wpf/advanced/typeconverters-and-xaml.md).</span></span>  
  
 <span data-ttu-id="9bf7b-200">而不是套用至類型的所有值，XAML 類型轉換器行為可以建立特定的屬性。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-200">Rather than applying to all values of a type, a type converter behavior for XAML can also be established on a specific property.</span></span> <span data-ttu-id="9bf7b-201">在此情況下，您套用<xref:System.ComponentModel.TypeConverterAttribute>屬性定義 (外部定義、 非特定`get`和`set`定義)。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-201">In this case, you apply <xref:System.ComponentModel.TypeConverterAttribute> to the property definition (the outer definition, not the specific `get` and `set` definitions).</span></span>  
  
 <span data-ttu-id="9bf7b-202">可以指派自訂的可附加成員的 XAML 用法型別轉換子行為，藉由套用<xref:System.ComponentModel.TypeConverterAttribute>至`get`支援 XAML 用法的方法存取子。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-202">A type converter behavior for XAML usage of a custom attachable member can be assigned by applying <xref:System.ComponentModel.TypeConverterAttribute> to the `get` method accessor that supports the XAML usage.</span></span>  
  
 <span data-ttu-id="9bf7b-203">類似於<xref:System.ComponentModel.TypeConverter>，<xref:System.ComponentModel.TypeConverterAttribute>存在於 XAML，面市之前的.NET Framework 中，而且型別轉換子模型提供的其他用途。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-203">Similar to <xref:System.ComponentModel.TypeConverter>, <xref:System.ComponentModel.TypeConverterAttribute> existed in the .NET Framework prior to the existence of XAML, and the type converter model served other purposes.</span></span> <span data-ttu-id="9bf7b-204">若要參考及使用<xref:System.ComponentModel.TypeConverterAttribute>，您必須完整限定它，或提供`using`陳述式<xref:System.ComponentModel>。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-204">In order to reference and use <xref:System.ComponentModel.TypeConverterAttribute>, you must fully qualify it or provide a `using` statement for <xref:System.ComponentModel>.</span></span> <span data-ttu-id="9bf7b-205">您也必須在專案中包含系統組件。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-205">You must also include the System assembly in your project.</span></span>  
  
### <a name="uidpropertyattribute"></a><span data-ttu-id="9bf7b-206">UidPropertyAttribute</span><span class="sxs-lookup"><span data-stu-id="9bf7b-206">UidPropertyAttribute</span></span>  
 **<span data-ttu-id="9bf7b-207">參考文件：</span><span class="sxs-lookup"><span data-stu-id="9bf7b-207">Reference Documentation:</span></span>**  <xref:System.Windows.Markup.UidPropertyAttribute>  
  
 <span data-ttu-id="9bf7b-208">**適用於：** 類別</span><span class="sxs-lookup"><span data-stu-id="9bf7b-208">**Applies to:** Class</span></span>  
  
 <span data-ttu-id="9bf7b-209">**引數：** 依名稱參考相關屬性的字串。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-209">**Arguments:** A string that references the relevant property by name.</span></span>  
  
 <span data-ttu-id="9bf7b-210">表示類別的 CLR 屬性別名[X:uid 指示詞](x-uid-directive.md)。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-210">Indicates the CLR property of a class that aliases the [x:Uid Directive](x-uid-directive.md).</span></span>  
  
### <a name="usableduringinitializationattribute"></a><span data-ttu-id="9bf7b-211">UsableDuringInitializationAttribute</span><span class="sxs-lookup"><span data-stu-id="9bf7b-211">UsableDuringInitializationAttribute</span></span>  
 **<span data-ttu-id="9bf7b-212">參考文件：</span><span class="sxs-lookup"><span data-stu-id="9bf7b-212">Reference Documentation:</span></span>**  <xref:System.Windows.Markup.UsableDuringInitializationAttribute>  
  
 <span data-ttu-id="9bf7b-213">**適用於：** 類別</span><span class="sxs-lookup"><span data-stu-id="9bf7b-213">**Applies to:** Class</span></span>  
  
 <span data-ttu-id="9bf7b-214">**引數：** 布林值。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-214">**Arguments:** A Boolean.</span></span> <span data-ttu-id="9bf7b-215">如果使用屬性的目的，這應該一律指定為`true`。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-215">If used for the attribute's intended purpose, this should always be specified as `true`.</span></span>  
  
 <span data-ttu-id="9bf7b-216">表示這個類型是否在 XAML 物件圖形建立期間由上而下建置。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-216">Indicates whether this type is built top-down during XAML object graph creation.</span></span> <span data-ttu-id="9bf7b-217">這是進階的概念，與您的程式設計模型的定義可能密切相關。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-217">This is an advanced concept, which is probably closely related to the definition of your programming model.</span></span> <span data-ttu-id="9bf7b-218">如需詳細資訊，請參閱<xref:System.Windows.Markup.UsableDuringInitializationAttribute>。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-218">For more information, see <xref:System.Windows.Markup.UsableDuringInitializationAttribute>.</span></span>  
  
### <a name="valueserializerattribute"></a><span data-ttu-id="9bf7b-219">ValueSerializerAttribute</span><span class="sxs-lookup"><span data-stu-id="9bf7b-219">ValueSerializerAttribute</span></span>  
 **<span data-ttu-id="9bf7b-220">參考文件：</span><span class="sxs-lookup"><span data-stu-id="9bf7b-220">Reference Documentation:</span></span>**  <xref:System.Windows.Markup.ValueSerializerAttribute>  
  
 <span data-ttu-id="9bf7b-221">**適用於：** 類別、 屬性、 方法 (唯一 XAML 有效的方法案例是`get`支援可附加成員的存取子)。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-221">**Applies to:** Class, property, method (the only XAML-valid method case is a `get` accessor that supports an attachable member).</span></span>  
  
 <span data-ttu-id="9bf7b-222">**引數：** A <xref:System.Type> ，指定用於在序列化的屬性化類型中，所有屬性的值序列化程式支援類別或特定屬性的屬性。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-222">**Arguments:** A <xref:System.Type> that specifies the value serializer support class to use when serializing all properties of the attributed type, or the specific attributed property.</span></span>  
  
 <xref:System.Windows.Markup.ValueSerializer> <span data-ttu-id="9bf7b-223">指定需要更多的狀態和內容的值序列化類別<xref:System.ComponentModel.TypeConverter>沒有。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-223">specifies a value serialization class that requires more state and context than a <xref:System.ComponentModel.TypeConverter> does.</span></span> <xref:System.Windows.Markup.ValueSerializer> <span data-ttu-id="9bf7b-224">可以藉由套用可附加成員與相關聯<xref:System.Windows.Markup.ValueSerializerAttribute>上的靜態屬性`get`之可附加成員的存取子方法。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-224">can be associated with an attachable member by applying the <xref:System.Windows.Markup.ValueSerializerAttribute> attribute on the static `get` accessor method for the attachable member.</span></span> <span data-ttu-id="9bf7b-225">值序列化也適用於列舉、 介面和結構，但不適用於委派。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-225">Value serialization is also applicable for enumerations, interfaces and structures, but not for delegates.</span></span>  
  
### <a name="whitespacesignificantcollectionattribute"></a><span data-ttu-id="9bf7b-226">WhitespaceSignificantCollectionAttribute</span><span class="sxs-lookup"><span data-stu-id="9bf7b-226">WhitespaceSignificantCollectionAttribute</span></span>  
 **<span data-ttu-id="9bf7b-227">參考文件：</span><span class="sxs-lookup"><span data-stu-id="9bf7b-227">Reference Documentation:</span></span>**  <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>  
  
 <span data-ttu-id="9bf7b-228">**適用於：** 類別，特別是裝載混合的內容，其中物件項目周圍的空白字元可能會造成很大 UI 表示法預期集合型別。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-228">**Applies to:** Class, specifically collection types that are expected to host mixed content, where white space around object elements might be significant for UI representation.</span></span>  
  
 <span data-ttu-id="9bf7b-229">**引數：** 無。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-229">**Arguments:** None.</span></span>  
  
 <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> <span data-ttu-id="9bf7b-230">表示集合型別應該處理為泛空白字元顯著，XAML 處理器，這會影響建構的 XAML 節點資料流的值集合中的節點。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-230">indicates that a collection type should be processed as white-space significant by a XAML processor, which influences the construction of the XAML node stream's value nodes within the collection.</span></span> <span data-ttu-id="9bf7b-231">如需詳細資訊，請參閱 <<c0> [ 泛空白字元處理中 XAML](whitespace-processing-in-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-231">For more information, see [White-space processing in XAML](whitespace-processing-in-xaml.md).</span></span>  
  
### <a name="xamldeferloadattribute"></a><span data-ttu-id="9bf7b-232">XamlDeferLoadAttribute</span><span class="sxs-lookup"><span data-stu-id="9bf7b-232">XamlDeferLoadAttribute</span></span>  
 **<span data-ttu-id="9bf7b-233">參考文件：</span><span class="sxs-lookup"><span data-stu-id="9bf7b-233">Reference Documentation:</span></span>**  <xref:System.Windows.Markup.XamlDeferLoadAttribute>  
  
 <span data-ttu-id="9bf7b-234">**適用於：** 類別屬性。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-234">**Applies to:** Class, property.</span></span>  
  
 <span data-ttu-id="9bf7b-235">**引數：** 支援兩個屬性形成類型視為字串，或為<xref:System.Type>。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-235">**Arguments:** Supports two attribution forms types as strings, or types as <xref:System.Type>.</span></span> <span data-ttu-id="9bf7b-236">請參閱 <xref:System.Windows.Markup.XamlDeferLoadAttribute>。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-236">See <xref:System.Windows.Markup.XamlDeferLoadAttribute>.</span></span>  
  
 <span data-ttu-id="9bf7b-237">表示類別或屬性具有 XAML 的延後的載入使用方式 （例如，範本行為），並報告啟用延後的行為和其目的地/內容型別類別。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-237">Indicates that a class or property has a deferred load usage for XAML (such as a template behavior), and reports the class that enables the deferring behavior and its destination/content type.</span></span>  
  
### <a name="xamlsetmarkupextensionattribute"></a><span data-ttu-id="9bf7b-238">XamlSetMarkupExtensionAttribute</span><span class="sxs-lookup"><span data-stu-id="9bf7b-238">XamlSetMarkupExtensionAttribute</span></span>  
 **<span data-ttu-id="9bf7b-239">參考文件：</span><span class="sxs-lookup"><span data-stu-id="9bf7b-239">Reference Documentation:</span></span>**  <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute>  
  
 <span data-ttu-id="9bf7b-240">**適用於：** 類別</span><span class="sxs-lookup"><span data-stu-id="9bf7b-240">**Applies to:** Class</span></span>  
  
 <span data-ttu-id="9bf7b-241">**引數：** 命名的回呼。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-241">**Arguments:** Names the callback.</span></span>  
  
 <span data-ttu-id="9bf7b-242">表示類別可以使用標記延伸的一個或多個屬性，提供的值，以及參考的 XAML 寫入器應該呼叫在執行類別的任何屬性上的標記延伸設定作業之前的處理常式。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-242">Indicates that a class can use a markup extension to provide a value for one or more of its properties, and references a handler that a XAML writer should call before performing a markup extension set operation on any property of the class.</span></span>  
  
### <a name="xamlsettypeconverterattribute"></a><span data-ttu-id="9bf7b-243">XamlSetTypeConverterAttribute</span><span class="sxs-lookup"><span data-stu-id="9bf7b-243">XamlSetTypeConverterAttribute</span></span>  
 **<span data-ttu-id="9bf7b-244">參考文件：</span><span class="sxs-lookup"><span data-stu-id="9bf7b-244">Reference Documentation:</span></span>**  <xref:System.Windows.Markup.XamlSetTypeConverterAttribute>  
  
 <span data-ttu-id="9bf7b-245">**適用於：** 類別</span><span class="sxs-lookup"><span data-stu-id="9bf7b-245">**Applies to:** Class</span></span>  
  
 <span data-ttu-id="9bf7b-246">**引數：** 命名的回呼。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-246">**Arguments:** Names the callback.</span></span>  
  
 <span data-ttu-id="9bf7b-247">表示類別可以使用型別轉換子的一個或多個屬性，提供的值，以及參考的 XAML 寫入器應該呼叫在執行類別的任何屬性的型別轉換子設定作業之前的處理常式。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-247">Indicates that a class can use a type converter to provide a value for one or more of its properties, and references a handler that a XAML writer should call before performing a type converter set operation on any property of the class.</span></span>  
  
### <a name="xmllangpropertyattribute"></a><span data-ttu-id="9bf7b-248">XmlLangPropertyAttribute</span><span class="sxs-lookup"><span data-stu-id="9bf7b-248">XmlLangPropertyAttribute</span></span>  
 **<span data-ttu-id="9bf7b-249">參考文件：</span><span class="sxs-lookup"><span data-stu-id="9bf7b-249">Reference Documentation:</span></span>**  <xref:System.Windows.Markup.XmlLangPropertyAttribute>  
  
 <span data-ttu-id="9bf7b-250">**適用於：** 類別</span><span class="sxs-lookup"><span data-stu-id="9bf7b-250">**Applies to:** Class</span></span>  
  
 <span data-ttu-id="9bf7b-251">**引數：** 字串，指定別名的屬性名稱`xml:lang`屬性化型別上。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-251">**Arguments:** A string that specifies the name of the property to alias to `xml:lang` on the attributed type.</span></span>  
  
 <xref:System.Windows.Markup.XmlLangPropertyAttribute> <span data-ttu-id="9bf7b-252">報告的屬性化型別對應至 XML 屬性`lang`指示詞。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-252">reports a property of the attributed type that maps to the XML `lang` directive.</span></span> <span data-ttu-id="9bf7b-253">屬性不是一定的型別<xref:System.String>，但必須可從字串 （這可藉由建立關聯型別轉換子，屬性的類型或特定的屬性）。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-253">The property is not necessarily of type <xref:System.String>, but must be assignable from a string (this could be accomplished by associating a type converter with the property's type, or with the specific property).</span></span> <span data-ttu-id="9bf7b-254">屬性必須是讀取/寫入。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-254">The property must be read/write.</span></span>  
  
 <span data-ttu-id="9bf7b-255">對應的案例`xml:lang`會使執行階段物件模型而不需特別處理使用 XMLDOM 具有 XML 指定的語言資訊的存取權。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-255">The scenario for mapping `xml:lang` is so that a runtime object model has access to XML-specified language information without specifically processing with an XMLDOM.</span></span>  
  
 <span data-ttu-id="9bf7b-256">定義繼承可指派給定義類型的所有衍生類型。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-256">The definition inherits to all derived types that are assignable to the defining type.</span></span> <span data-ttu-id="9bf7b-257">您可以藉由套用覆寫特定的衍生型別上定義<xref:System.Windows.Markup.XmlLangPropertyAttribute>特定衍生型別，雖然這是常見的案例。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-257">You can override the definition on a specific derived type by applying <xref:System.Windows.Markup.XmlLangPropertyAttribute> on the specific derived type, although that is an uncommon scenario.</span></span>  
  
## <a name="xaml-related-clr-attributes-at-the-assembly-level"></a><span data-ttu-id="9bf7b-258">組件層級的 XAML 相關 CLR 屬性</span><span class="sxs-lookup"><span data-stu-id="9bf7b-258">XAML-Related CLR Attributes at the Assembly Level</span></span>  
 <span data-ttu-id="9bf7b-259">下列各節描述的 XAML 相關的屬性不會套用至類型或成員的定義，但會改為套用至組件。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-259">The following sections describe the XAML-related attributes that are not applied to types or member definitions, but are instead applied to assemblies.</span></span> <span data-ttu-id="9bf7b-260">這些屬性是與整體目標是要定義包含在 XAML 中使用的自訂型別程式庫相關。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-260">These attributes are pertinent to the overall goal of defining a library that contains custom types to use in XAML.</span></span> <span data-ttu-id="9bf7b-261">有些屬性不一定影響 XAML 節點資料流直接，但會傳遞其他取用者使用的節點資料流中。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-261">Some of the attributes do not necessarily influence the XAML node stream directly, but are passed on in the node stream for other consumers to use.</span></span> <span data-ttu-id="9bf7b-262">如需資訊的取用者包括設計環境或序列化程序，需要 XAML 命名空間的資訊和相關聯的前置詞資訊。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-262">Consumers for the information include design environments or serialization processes that need XAML namespace information and associated prefix information.</span></span> <span data-ttu-id="9bf7b-263">XAML 結構描述內容 （包括.NET Framework XAML 服務預設值） 也會使用這項資訊。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-263">A XAML schema context (including the .NET Framework XAML Services default) also uses this information.</span></span>  
  
### <a name="xmlnscompatiblewithattribute"></a><span data-ttu-id="9bf7b-264">XmlnsCompatibleWithAttribute</span><span class="sxs-lookup"><span data-stu-id="9bf7b-264">XmlnsCompatibleWithAttribute</span></span>  
 **<span data-ttu-id="9bf7b-265">參考文件：</span><span class="sxs-lookup"><span data-stu-id="9bf7b-265">Reference Documentation:</span></span>**  <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>  
  
 **<span data-ttu-id="9bf7b-266">引數：</span><span class="sxs-lookup"><span data-stu-id="9bf7b-266">Arguments:</span></span>**  
  
-   <span data-ttu-id="9bf7b-267">字串，指定要包含的 XAML 命名空間的識別項。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-267">A string that specifies the identifier of the XAML namespace to subsume.</span></span>  
  
-   <span data-ttu-id="9bf7b-268">字串，指定可以包含從先前的引數的 XAML 命名空間的 XAML 命名空間的識別碼。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-268">A string that specifies the identifier of the XAML namespace that can subsume the XAML namespace from the previous argument.</span></span>  
  
 <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute> <span data-ttu-id="9bf7b-269">指定可以在另一個 XAML 命名空間建立小計的 XAML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-269">specifies that a XAML namespace can be subsumed by another XAML namespace.</span></span> <span data-ttu-id="9bf7b-270">一般會在預先定義的 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> 中指出建立小計的 XAML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-270">Typically, the subsuming XAML namespace is indicated in a previously defined <xref:System.Windows.Markup.XmlnsDefinitionAttribute>.</span></span> <span data-ttu-id="9bf7b-271">這種方式可用於版本控制 XAML 詞彙的文件庫中，並讓它與先前定義的標記，針對稍早的版本控制詞彙相容。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-271">This technique can be used for versioning a XAML vocabulary in a library and to make it compatible with previously defined markup against the earlier versioned vocabulary.</span></span>  
  
### <a name="xmlnsdefinitionattribute"></a><span data-ttu-id="9bf7b-272">XmlnsDefinitionAttribute</span><span class="sxs-lookup"><span data-stu-id="9bf7b-272">XmlnsDefinitionAttribute</span></span>  
 **<span data-ttu-id="9bf7b-273">參考文件：</span><span class="sxs-lookup"><span data-stu-id="9bf7b-273">Reference Documentation:</span></span>**  <xref:System.Windows.Markup.XmlnsDefinitionAttribute>  
  
 **<span data-ttu-id="9bf7b-274">引數：</span><span class="sxs-lookup"><span data-stu-id="9bf7b-274">Arguments:</span></span>**  
  
-   <span data-ttu-id="9bf7b-275">字串，指定定義的 XAML 命名空間的識別碼。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-275">A string that specifies the identifier of the XAML namespace to define.</span></span>  
  
-   <span data-ttu-id="9bf7b-276">字串，可命名 CLR 命名空間。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-276">A string that names a CLR namespace.</span></span> <span data-ttu-id="9bf7b-277">CLR 命名空間應該在您的組件中定義公用型別，並至少一個 CLR 命名空間型別應該適合 XAML 用法。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-277">The CLR namespace should define public types in your assembly, and at least one of the CLR namespace types should be intended for XAML usage.</span></span>  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> <span data-ttu-id="9bf7b-278">指定 XAML 命名空間與 CLR 命名空間，然後用於類型解析的 XAML 物件寫入器或 XAML 結構描述內容之間以每個組件為基礎的對應。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-278">specifies a mapping on a per-assembly basis between a XAML namespace and a CLR namespace, which is then used for type resolution by a XAML object writer or XAML schema context.</span></span>  
  
 <span data-ttu-id="9bf7b-279">多個<xref:System.Windows.Markup.XmlnsDefinitionAttribute>可以套用至組件。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-279">More than one <xref:System.Windows.Markup.XmlnsDefinitionAttribute> can be applied to an assembly.</span></span> <span data-ttu-id="9bf7b-280">達成此目的任何組合的原因如下：</span><span class="sxs-lookup"><span data-stu-id="9bf7b-280">This might be done for any combination of the following reasons:</span></span>  
  
-   <span data-ttu-id="9bf7b-281">程式庫設計包含多個 CLR 命名空間，針對邏輯組織的執行階段 API 存取權限;不過，您會想要由 XAML 可參考相同的 XAML 命名空間在這些命名空間中的所有型別。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-281">The library design contains multiple CLR namespaces for logical organization of run-time API access; however, you want all types in those namespaces to be XAML-usable by referencing the same XAML namespace.</span></span> <span data-ttu-id="9bf7b-282">在此情況下，套用數個<xref:System.Windows.Markup.XmlnsDefinitionAttribute>屬性使用相同<xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A>值但不同<xref:System.Windows.Markup.XmlnsDefinitionAttribute.ClrNamespace%2A>值。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-282">In this case, you apply several <xref:System.Windows.Markup.XmlnsDefinitionAttribute> attributes using the same <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> value but different <xref:System.Windows.Markup.XmlnsDefinitionAttribute.ClrNamespace%2A> values.</span></span> <span data-ttu-id="9bf7b-283">這是特別有用，如果您要定義 framework 或應用程式想要預設 XAML 命名空間中常見的用法的 XAML 命名空間的對應。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-283">This is especially useful if you are defining mappings for the XAML namespace that your framework or application intends to be the default XAML namespace in common usage.</span></span>  
  
-   <span data-ttu-id="9bf7b-284">程式庫設計包含多個 CLR 命名空間，而且您想在審慎 XAML 命名空間之間的分隔的這些 CLR 命名空間中類型的使用方式。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-284">The library design contains multiple CLR namespaces, and you want a deliberate XAML namespace separation between the usages of types in those CLR namespaces.</span></span>  
  
-   <span data-ttu-id="9bf7b-285">您定義的 CLR 命名空間的組件，而您希望它可透過一個以上的 XAML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-285">You define a CLR namespace in the assembly, and you want it to be accessible through more than one XAML namespace.</span></span> <span data-ttu-id="9bf7b-286">若要支援具有相同的程式碼基底的多個詞彙，就會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-286">This scenario occurs when you are supporting multiple vocabularies with the same codebase.</span></span>  
  
-   <span data-ttu-id="9bf7b-287">您可以定義 XAML 語言支援一或多個 CLR 命名空間中。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-287">You define XAML language support in one or more CLR namespaces.</span></span> <span data-ttu-id="9bf7b-288">對於這些<xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A>值應該是`http://schemas.microsoft.com/winfx/2006/xaml`。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-288">For these, the <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> value should be `http://schemas.microsoft.com/winfx/2006/xaml`.</span></span>  
  
### <a name="xmlnsprefixattribute"></a><span data-ttu-id="9bf7b-289">XmlnsPrefixAttribute</span><span class="sxs-lookup"><span data-stu-id="9bf7b-289">XmlnsPrefixAttribute</span></span>  
 **<span data-ttu-id="9bf7b-290">參考文件：</span><span class="sxs-lookup"><span data-stu-id="9bf7b-290">Reference Documentation:</span></span>**  <xref:System.Windows.Markup.XmlnsPrefixAttribute>  
  
 **<span data-ttu-id="9bf7b-291">引數：</span><span class="sxs-lookup"><span data-stu-id="9bf7b-291">Arguments:</span></span>**  
  
-   <span data-ttu-id="9bf7b-292">字串，指定的 XAML 命名空間識別項。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-292">A string that specifies the identifier of a XAML namespace.</span></span>  
  
-   <span data-ttu-id="9bf7b-293">字串，指定建議的前置詞。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-293">A string that specifies a recommended prefix.</span></span>  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> <span data-ttu-id="9bf7b-294">指定要用於 XAML 命名空間的建議前置詞。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-294">specifies a recommended prefix to use for a XAML namespace.</span></span> <span data-ttu-id="9bf7b-295">寫入項目和屬性的 XAML 檔案中，序列化的.NET Framework XAML 服務時很有用的前置詞，是<xref:System.Xaml.XamlXmlWriter>，或當 XAML 實作的程式庫互動的設計環境具有 XAML 編輯功能。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-295">The prefix is useful when writing elements and attributes in a XAML file that is serialized by the .NET Framework XAML Services <xref:System.Xaml.XamlXmlWriter>, or when a XAML-implementing library interacts with a design environment that has XAML editing features.</span></span>  
  
 <span data-ttu-id="9bf7b-296">多個<xref:System.Windows.Markup.XmlnsPrefixAttribute>可以套用至組件。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-296">More than one <xref:System.Windows.Markup.XmlnsPrefixAttribute> can be applied to an assembly.</span></span> <span data-ttu-id="9bf7b-297">達成此目的任何組合的原因如下：</span><span class="sxs-lookup"><span data-stu-id="9bf7b-297">This might be done for any combination of the following reasons:</span></span>  
  
-   <span data-ttu-id="9bf7b-298">您的組件會定義一個以上的 XAML 命名空間的類型。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-298">Your assembly defines types for more than one XAML namespace.</span></span> <span data-ttu-id="9bf7b-299">在此情況下，您應該定義每個 XAML 命名空間的不同前置詞值。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-299">In this case you should define different prefix values for each XAML namespace.</span></span>  
  
-   <span data-ttu-id="9bf7b-300">您要支援多個詞彙，而且您使用不同的前置詞為每個詞彙和 XAML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-300">You are supporting multiple vocabularies, and you use different prefixes for each vocabulary and XAML namespace.</span></span>  
  
-   <span data-ttu-id="9bf7b-301">您定義組件中的 XAML 語言支援，並讓<xref:System.Windows.Markup.XmlnsDefinitionAttribute>針對`http://schemas.microsoft.com/winfx/2006/xaml`。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-301">You define XAML language support in the assembly and have a <xref:System.Windows.Markup.XmlnsDefinitionAttribute> for `http://schemas.microsoft.com/winfx/2006/xaml`.</span></span> <span data-ttu-id="9bf7b-302">在此情況下，您通常應該升級前置詞`x`。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-302">In this case, you typically should promote the prefix `x`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9bf7b-303">.NET framework XAML 服務也會定義的 XAML 相關屬性<xref:System.Windows.Markup.RootNamespaceAttribute>。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-303">.NET Framework XAML Services also defines the XAML-related attribute <xref:System.Windows.Markup.RootNamespaceAttribute>.</span></span> <span data-ttu-id="9bf7b-304">這個屬性是專案系統支援的組件層級屬性，並不是與 XAML 自訂型別相關。</span><span class="sxs-lookup"><span data-stu-id="9bf7b-304">This attribute is an assembly-level attribute for project system support, and it is not relevant for XAML custom types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bf7b-305">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9bf7b-305">See also</span></span>

- <xref:System.Attribute>
- [<span data-ttu-id="9bf7b-306">定義可搭配 .NET Framework XAML 服務使用的自訂類型</span><span class="sxs-lookup"><span data-stu-id="9bf7b-306">Defining Custom Types for Use with .NET Framework XAML Services</span></span>](defining-custom-types-for-use-with-net-framework-xaml-services.md)
