---
title: 自訂類型和程式庫的 XAML 相關 CLR 屬性
ms.date: 03/30/2017
helpviewer_keywords:
- CLR attributes for custom types [XAML Services]
ms.assetid: 5dfb299a-b6e2-41b8-8694-e6ac987547f1
ms.openlocfilehash: a4b8a58ea2c7d9de2b59ed78dc37e4ce1c434b79
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90535393"
---
# <a name="xaml-related-clr-attributes-for-custom-types-and-libraries"></a><span data-ttu-id="ce6dc-102">自訂類型和程式庫的 XAML 相關 CLR 屬性</span><span class="sxs-lookup"><span data-stu-id="ce6dc-102">XAML-related CLR attributes for custom types and libraries</span></span>

<span data-ttu-id="ce6dc-103">本主題說明 .NET XAML 服務所定義 (CLR) 屬性的 common language runtime。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-103">This topic describes the common language runtime (CLR) attributes that are defined by .NET XAML Services.</span></span> <span data-ttu-id="ce6dc-104">此外，也會說明在 .NET 中定義的其他 CLR 屬性，這些屬性會針對應用程式的元件或類型，具有與 XAML 相關的案例。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-104">It also describes other CLR attributes that are defined in .NET that have a XAML-related scenario for application to assemblies or types.</span></span> <span data-ttu-id="ce6dc-105">使用這些 CLR 屬性（attribute）將元件、類型或成員的屬性（attribute）提供與類型相關的 XAML 類型系統資訊。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-105">Attributing assemblies, types, or members with these CLR attributes provides XAML type system information related to your types.</span></span> <span data-ttu-id="ce6dc-106">資訊會提供給任何使用 .NET XAML 服務的 XAML 取用者，以便直接或透過專用的 XAML 讀取器和 XAML 寫入器處理 XAML 節點資料流程。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-106">Information is provided to any XAML consumer that uses .NET XAML Services for processing the XAML node stream directly or through the dedicated XAML readers and XAML writers.</span></span>

## <a name="xaml-related-clr-attributes-for-custom-types-and-custom-members"></a><span data-ttu-id="ce6dc-107">自訂類型和自訂成員的 XAML 相關 CLR 屬性</span><span class="sxs-lookup"><span data-stu-id="ce6dc-107">XAML-Related CLR Attributes for Custom Types and Custom Members</span></span>

<span data-ttu-id="ce6dc-108">使用 CLR 屬性時，您必須使用整體 CLR 來定義您的類型，否則無法使用這類屬性。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-108">Using CLR attributes entails that you are using the overall CLR to define your types, otherwise such attributes are not available.</span></span> <span data-ttu-id="ce6dc-109">如果您使用 CLR 來定義型別支援，則 .NET XAML 服務 XAML 寫入器所使用的預設 XAML 架構內容，可以透過反映針對支援元件來讀取 CLR 屬性。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-109">If you use the CLR to define type backing, then the default XAML schema context used by .NET XAML Services XAML writers can read CLR attribution through reflection against backing assemblies.</span></span>

<span data-ttu-id="ce6dc-110">下列各節說明可套用至自訂類型或自訂成員的 XAML 相關屬性。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-110">The following sections describe the XAML-related attributes that you can apply to custom types or custom members.</span></span> <span data-ttu-id="ce6dc-111">每個 CLR 屬性都會傳達與 XAML 類型系統相關的資訊。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-111">Each CLR attribute communicates information that is relevant to a XAML type system.</span></span> <span data-ttu-id="ce6dc-112">在載入路徑中，屬性化資訊可協助 XAML 讀取器形成有效的 XAML 節點資料流程，或協助 XAML 寫入器產生有效的物件圖形。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-112">In the load path, the attributed information either helps the XAML reader form a valid XAML node stream, or it helps the XAML writer produce a valid object graph.</span></span> <span data-ttu-id="ce6dc-113">在儲存路徑中，屬性化資訊可協助 XAML 讀取器形成有效的 XAML 節點資料流程，以重組 XAML 類型系統資訊;或者，它會宣告 XAML 寫入器或其他 XAML 取用者的序列化提示或需求。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-113">In the save path, the attributed information either helps the XAML reader form a valid XAML node stream that reconstitutes XAML type system information; or it declares serialization hints or requirements for the XAML writer or other XAML consumers.</span></span>

### <a name="ambientattribute"></a><span data-ttu-id="ce6dc-114">AmbientAttribute</span><span class="sxs-lookup"><span data-stu-id="ce6dc-114">AmbientAttribute</span></span>

<span data-ttu-id="ce6dc-115">**參考檔：**<xref:System.Windows.Markup.AmbientAttribute></span><span class="sxs-lookup"><span data-stu-id="ce6dc-115">**Reference Documentation:** <xref:System.Windows.Markup.AmbientAttribute></span></span>

<span data-ttu-id="ce6dc-116">**適用于：**`get`支援可附加屬性的類別、屬性或存取子成員。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-116">**Applies to:** Class, property, or `get` accessor members that support attachable properties.</span></span>

<span data-ttu-id="ce6dc-117">**引數：** 沒有</span><span class="sxs-lookup"><span data-stu-id="ce6dc-117">**Arguments:** None</span></span>

<span data-ttu-id="ce6dc-118"><xref:System.Windows.Markup.AmbientAttribute> 指出屬性（property）或所有採用屬性化型別的屬性（property），都應該在 XAML 的環境屬性概念下解讀。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-118"><xref:System.Windows.Markup.AmbientAttribute> indicates that the property, or all properties that take the attributed type, should be interpreted under the ambient property concept in XAML.</span></span> <span data-ttu-id="ce6dc-119">環境概念與 XAML 處理器如何判斷成員類別擁有者有關。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-119">The ambient concept relates to how XAML processors determine type owners of members.</span></span> <span data-ttu-id="ce6dc-120">環境屬性是一種屬性，它會在建立物件圖形時，將值預期在剖析器內容中，但在這種情況下，會針對正在建立的立即 XAML 節點集暫停一般的型別成員查閱。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-120">An ambient property is a property where the value is expected to be available in the parser context when creating an object graph, but where typical type-member lookup is suspended for the immediate XAML node set being created.</span></span>

<span data-ttu-id="ce6dc-121">環境概念可以套用至可附加的成員，這些成員不會以 CLR 屬性定義的形式來表示 <xref:System.AttributeTargets> 。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-121">The ambient concept can be applied to attachable members, which are not represented as properties in terms of how CLR attribution defines <xref:System.AttributeTargets>.</span></span> <span data-ttu-id="ce6dc-122">方法屬性的使用方式應僅適用于 `get` 支援 XAML 可附加用法的存取子。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-122">The method attribution usage should be applied only for a `get` accessor that supports attachable usage for XAML.</span></span>

### <a name="constructorargumentattribute"></a><span data-ttu-id="ce6dc-123">ConstructorArgumentAttribute</span><span class="sxs-lookup"><span data-stu-id="ce6dc-123">ConstructorArgumentAttribute</span></span>

<span data-ttu-id="ce6dc-124">**參考檔：**  <xref:System.Windows.Markup.ConstructorArgumentAttribute></span><span class="sxs-lookup"><span data-stu-id="ce6dc-124">**Reference Documentation:**  <xref:System.Windows.Markup.ConstructorArgumentAttribute></span></span>

<span data-ttu-id="ce6dc-125">**適用于：** 類</span><span class="sxs-lookup"><span data-stu-id="ce6dc-125">**Applies to:** Class</span></span>

<span data-ttu-id="ce6dc-126">**引數：** 字串，指定符合單一函式引數的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-126">**Arguments:** A string that specifies the name of the property that matches a single constructor argument.</span></span>

<span data-ttu-id="ce6dc-127"><xref:System.Windows.Markup.ConstructorArgumentAttribute> 指定可以使用非參數化的函式語法來初始化物件，且指定之名稱的屬性會提供結構資訊。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-127"><xref:System.Windows.Markup.ConstructorArgumentAttribute> specifies that an object can be initialized by using a non-parameterless constructor syntax, and that a property of the specified name supplies construction information.</span></span> <span data-ttu-id="ce6dc-128">這項資訊主要供 XAML 序列化之用。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-128">This information is primarily for XAML serialization.</span></span> <span data-ttu-id="ce6dc-129">如需詳細資訊，請參閱<xref:System.Windows.Markup.ConstructorArgumentAttribute>。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-129">For more information, see <xref:System.Windows.Markup.ConstructorArgumentAttribute>.</span></span>

### <a name="contentpropertyattribute"></a><span data-ttu-id="ce6dc-130">ContentPropertyAttribute</span><span class="sxs-lookup"><span data-stu-id="ce6dc-130">ContentPropertyAttribute</span></span>

<span data-ttu-id="ce6dc-131">**參考檔：**  <xref:System.Windows.Markup.ContentPropertyAttribute></span><span class="sxs-lookup"><span data-stu-id="ce6dc-131">**Reference Documentation:**  <xref:System.Windows.Markup.ContentPropertyAttribute></span></span>

<span data-ttu-id="ce6dc-132">**適用于：** 類</span><span class="sxs-lookup"><span data-stu-id="ce6dc-132">**Applies to:** Class</span></span>

<span data-ttu-id="ce6dc-133">**引數：** 字串，指定屬性型別之成員的名稱。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-133">**Arguments:** A string that specifies the name of a member of the attributed type.</span></span>

<span data-ttu-id="ce6dc-134"><xref:System.Windows.Markup.ContentPropertyAttribute> 指出由引數命名的屬性應做為該類型的 XAML 內容屬性。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-134"><xref:System.Windows.Markup.ContentPropertyAttribute> indicates that the property as named by the argument should serve as the XAML content property for that type.</span></span> <span data-ttu-id="ce6dc-135">XAML 內容屬性定義會繼承到可指派給定義型別的所有衍生型別。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-135">The XAML content property definition inherits to all derived types that are assignable to the defining type.</span></span> <span data-ttu-id="ce6dc-136">您可以 <xref:System.Windows.Markup.ContentPropertyAttribute> 在特定的衍生型別上套用，藉以覆寫特定衍生型別的定義。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-136">You can override the definition on a specific derived type by applying <xref:System.Windows.Markup.ContentPropertyAttribute> on the specific derived type.</span></span>

<span data-ttu-id="ce6dc-137">針對做為 XAML 內容屬性的屬性，可以在 XAML 用法中省略屬性的屬性專案標記。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-137">For the property that serves as the XAML content property, property element tagging for the property can be omitted in the XAML usage.</span></span> <span data-ttu-id="ce6dc-138">通常，您會指定 XAML 內容屬性，以針對您的內容和內含專案模型升級簡化的 XAML 標記。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-138">Typically, you designate XAML content properties that promote a streamlined XAML markup for your content and containment models.</span></span> <span data-ttu-id="ce6dc-139">因為只有一個成員可以指定為 XAML 內容屬性，所以您有時會有設計選項，以決定應該將類型的數個容器屬性指定為 XAML 內容屬性。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-139">Because only one member can be designated as the XAML content property, you sometimes have design choices to make regarding which of several container properties of a type should be designated as the XAML content property.</span></span> <span data-ttu-id="ce6dc-140">其他容器屬性必須搭配明確的屬性元素使用。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-140">The other container properties must be used with explicit property elements.</span></span>

<span data-ttu-id="ce6dc-141">在 XAML 節點資料流程中，XAML 內容屬性仍會產生 `StartMember` 和 `EndMember` 節點，並使用的屬性名稱 <xref:System.Xaml.XamlMember> 。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-141">In the XAML node stream, XAML content properties still produce `StartMember` and `EndMember` nodes, using the name of the property for the <xref:System.Xaml.XamlMember>.</span></span> <span data-ttu-id="ce6dc-142">若要判斷成員是否為 XAML 內容屬性，請檢查 <xref:System.Xaml.XamlType> 位置的值 `StartObject` ，並取得的值 <xref:System.Xaml.XamlType.ContentProperty%2A> 。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-142">To determine whether a member is the XAML content property, examine the <xref:System.Xaml.XamlType> value from the `StartObject` position and obtain the value of <xref:System.Xaml.XamlType.ContentProperty%2A>.</span></span>

### <a name="contentwrapperattribute"></a><span data-ttu-id="ce6dc-143">ContentWrapperAttribute</span><span class="sxs-lookup"><span data-stu-id="ce6dc-143">ContentWrapperAttribute</span></span>

<span data-ttu-id="ce6dc-144">**參考檔：**  <xref:System.Windows.Markup.ContentWrapperAttribute></span><span class="sxs-lookup"><span data-stu-id="ce6dc-144">**Reference Documentation:**  <xref:System.Windows.Markup.ContentWrapperAttribute></span></span>

<span data-ttu-id="ce6dc-145">**適用于：** 類別，特別是集合類型。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-145">**Applies to:** Class, specifically collection types.</span></span>

<span data-ttu-id="ce6dc-146">**引數：**<xref:System.Type>，指定要做為外部內容之內容包裝函式類型的型別。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-146">**Arguments:** A <xref:System.Type> that specifies the type to use as the content wrapper type for foreign content.</span></span>

<span data-ttu-id="ce6dc-147"><xref:System.Windows.Markup.ContentWrapperAttribute> 指定將用來包裝外部內容之相關聯集合類型上的一或多個類型。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-147"><xref:System.Windows.Markup.ContentWrapperAttribute> specifies one or more types on the associated collection type that will be used to wrap foreign content.</span></span> <span data-ttu-id="ce6dc-148">外部內容是指 [內容] 屬性類型上的類型系統條件約束，不會捕捉擁有類型所支援之 XAML 使用方式的所有可能內容案例的案例。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-148">Foreign content refers to cases where the type system constraints on the type of the content property do not capture all of the possible content cases that XAML usage for the owning type would support.</span></span> <span data-ttu-id="ce6dc-149">例如，XAML 支援特定類型內容可能支援強型別泛型中的字串 <xref:System.Collections.ObjectModel.Collection%601> 。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-149">For example, XAML support for content of a particular type might support strings in a strongly typed generic <xref:System.Collections.ObjectModel.Collection%601>.</span></span> <span data-ttu-id="ce6dc-150">內容包裝函式適用于將預先存在的標記慣例遷移至 XAML 針對集合的可指派值概念，例如，遷移文字相關的內容模型。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-150">Content wrappers are useful for migrating pre-existing markup conventions into XAML's conception of assignable values for collections, such as migrating text-related content models.</span></span>

<span data-ttu-id="ce6dc-151">若要指定一個以上的內容包裝函式類型，請多次套用此屬性。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-151">To specify more than one content wrapper type, apply the attribute multiple times.</span></span>

### <a name="dependsonattribute"></a><span data-ttu-id="ce6dc-152">DependsOnAttribute</span><span class="sxs-lookup"><span data-stu-id="ce6dc-152">DependsOnAttribute</span></span>

<span data-ttu-id="ce6dc-153">**參考檔：**  <xref:System.Windows.Markup.DependsOnAttribute></span><span class="sxs-lookup"><span data-stu-id="ce6dc-153">**Reference Documentation:**  <xref:System.Windows.Markup.DependsOnAttribute></span></span>

<span data-ttu-id="ce6dc-154">**適用于：** 財產</span><span class="sxs-lookup"><span data-stu-id="ce6dc-154">**Applies to:** Property</span></span>

<span data-ttu-id="ce6dc-155">**引數：** 字串，指定屬性型別之另一個成員的名稱。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-155">**Arguments:** A string that specifies the name of another member of the attributed type.</span></span>

<span data-ttu-id="ce6dc-156"><xref:System.Windows.Markup.DependsOnAttribute> 指出屬性化屬性相依于另一個屬性的值。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-156"><xref:System.Windows.Markup.DependsOnAttribute> indicates that the attributed property depends on the value of another property.</span></span> <span data-ttu-id="ce6dc-157">將這個屬性套用至屬性定義，可確保相依屬性會先在撰寫的 XAML 物件中處理。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-157">Applying this attribute to a property definition ensures that the dependent properties are processed first in XAML object writing.</span></span> <span data-ttu-id="ce6dc-158">的使用方式 <xref:System.Windows.Markup.DependsOnAttribute> 會指定類型的例外狀況案例，在此類型上必須遵循特定的剖析順序，才能建立有效的物件。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-158">Usages of <xref:System.Windows.Markup.DependsOnAttribute> specify the exceptional cases of properties on types where a specific order of parsing must be followed for valid object creation.</span></span>

<span data-ttu-id="ce6dc-159">您可以將多個 <xref:System.Windows.Markup.DependsOnAttribute> 案例套用至屬性定義。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-159">You can apply multiple <xref:System.Windows.Markup.DependsOnAttribute> cases to a property definition.</span></span>

### <a name="markupextensionreturntypeattribute"></a><span data-ttu-id="ce6dc-160">MarkupExtensionReturnTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="ce6dc-160">MarkupExtensionReturnTypeAttribute</span></span>

<span data-ttu-id="ce6dc-161">**參考檔：**  <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute></span><span class="sxs-lookup"><span data-stu-id="ce6dc-161">**Reference Documentation:**  <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute></span></span>

<span data-ttu-id="ce6dc-162">**適用于：** 類別，它應該是 <xref:System.Windows.Markup.MarkupExtension> 衍生型別。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-162">**Applies to:** Class, which is expected to be a <xref:System.Windows.Markup.MarkupExtension> derived type.</span></span>

<span data-ttu-id="ce6dc-163">**引數：**<xref:System.Type>，指定預期為 `ProvideValue` 屬性化之結果的最精確型別 <xref:System.Windows.Markup.MarkupExtension> 。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-163">**Arguments:** A <xref:System.Type> that specifies the most precise type to expect as the `ProvideValue` result of the attributed <xref:System.Windows.Markup.MarkupExtension>.</span></span>

<span data-ttu-id="ce6dc-164">如需詳細資訊，請參閱 [XAML 的標記延伸總覽](markup-extensions-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-164">For more information, see [Markup Extensions for XAML Overview](markup-extensions-overview.md).</span></span>

### <a name="namescopepropertyattribute"></a><span data-ttu-id="ce6dc-165">NameScopePropertyAttribute</span><span class="sxs-lookup"><span data-stu-id="ce6dc-165">NameScopePropertyAttribute</span></span>

<span data-ttu-id="ce6dc-166">**參考檔：**  <xref:System.Windows.Markup.NameScopePropertyAttribute></span><span class="sxs-lookup"><span data-stu-id="ce6dc-166">**Reference Documentation:**  <xref:System.Windows.Markup.NameScopePropertyAttribute></span></span>

<span data-ttu-id="ce6dc-167">**適用于：** 類</span><span class="sxs-lookup"><span data-stu-id="ce6dc-167">**Applies to:** Class</span></span>

<span data-ttu-id="ce6dc-168">**引數：** 支援兩種形式的屬性：</span><span class="sxs-lookup"><span data-stu-id="ce6dc-168">**Arguments:** Supports two forms of attribution:</span></span>

- <span data-ttu-id="ce6dc-169">字串，指定屬性化型別上的屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-169">A string that specifies the name of a property on the attributed type.</span></span>

- <span data-ttu-id="ce6dc-170">字串，指定屬性的名稱，以及 <xref:System.Type> 定義已命名屬性之類型的。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-170">A string that specifies the name of a property, and a <xref:System.Type> for the type that defines the named property.</span></span> <span data-ttu-id="ce6dc-171">此形式適用于將可附加的成員指定為 XAML 名稱範圍屬性。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-171">This form is for specifying an attachable member as the XAML namescope property.</span></span>

<span data-ttu-id="ce6dc-172"><xref:System.Windows.Markup.NameScopePropertyAttribute> 指定可為屬性化類別提供 XAML 名稱範圍值的屬性。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-172"><xref:System.Windows.Markup.NameScopePropertyAttribute> specifies a property that provides the XAML namescope value for the attributed class.</span></span> <span data-ttu-id="ce6dc-173">XAML 名稱範圍屬性必須參考物件，該物件會執行 <xref:System.Windows.Markup.INameScope> 並保存實際的 XAML 名稱範圍、其存放區和其行為。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-173">The XAML namescope property is expected to reference an object that implements <xref:System.Windows.Markup.INameScope> and holds the actual XAML namescope, its store, and its behavior.</span></span>

### <a name="runtimenamepropertyattribute"></a><span data-ttu-id="ce6dc-174">RuntimeNamePropertyAttribute</span><span class="sxs-lookup"><span data-stu-id="ce6dc-174">RuntimeNamePropertyAttribute</span></span>

<span data-ttu-id="ce6dc-175">**參考檔：**  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute></span><span class="sxs-lookup"><span data-stu-id="ce6dc-175">**Reference Documentation:**  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute></span></span>

<span data-ttu-id="ce6dc-176">**適用于：** 類</span><span class="sxs-lookup"><span data-stu-id="ce6dc-176">**Applies to:** Class</span></span>

<span data-ttu-id="ce6dc-177">**引數：** 字串，指定屬性化型別上執行時間名稱屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-177">**Arguments:** A string that specifies the name of the run-time name property on the attributed type.</span></span>

<span data-ttu-id="ce6dc-178"><xref:System.Windows.Markup.RuntimeNamePropertyAttribute> 報告對應至 XAML [x：Name](xname-directive.md)指示詞之屬性化型別的屬性（property）。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-178"><xref:System.Windows.Markup.RuntimeNamePropertyAttribute> reports a property of the attributed type that maps to the XAML [x:Name Directive](xname-directive.md).</span></span> <span data-ttu-id="ce6dc-179">屬性必須是型別 <xref:System.String> ，而且必須是讀取/寫入。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-179">The property must be of type <xref:System.String> and must be read/write.</span></span>

<span data-ttu-id="ce6dc-180">定義會繼承到可指派給定義型別的所有衍生型別。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-180">The definition inherits to all derived types that are assignable to the defining type.</span></span> <span data-ttu-id="ce6dc-181">您可以 <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> 在特定的衍生型別上套用，藉以覆寫特定衍生型別的定義。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-181">You can override the definition on a specific derived type by applying <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> on the specific derived type.</span></span>

### <a name="trimsurroundingwhitespaceattribute"></a><span data-ttu-id="ce6dc-182">TrimSurroundingWhitespaceAttribute</span><span class="sxs-lookup"><span data-stu-id="ce6dc-182">TrimSurroundingWhitespaceAttribute</span></span>

<span data-ttu-id="ce6dc-183">**參考檔：**  <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute></span><span class="sxs-lookup"><span data-stu-id="ce6dc-183">**Reference Documentation:**  <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute></span></span>

<span data-ttu-id="ce6dc-184">**適用于：** 類型</span><span class="sxs-lookup"><span data-stu-id="ce6dc-184">**Applies to:** Types</span></span>

<span data-ttu-id="ce6dc-185">**引數：** 沒有。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-185">**Arguments:** None.</span></span>

<span data-ttu-id="ce6dc-186"><xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute> 會套用至特定類型，而這些類型可能會顯示為泛空白字元內的子項目， (內容由具有) 之集合所持有的內容 <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-186"><xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute> is applied to specific types that might appear as child elements within white-space significant content (content held by a collection that has <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>).</span></span> <span data-ttu-id="ce6dc-187"><xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute> 主要與儲存路徑相關，但在 XAML 型別系統中，可透過檢查來提供給載入路徑 <xref:System.Xaml.XamlType.TrimSurroundingWhitespace%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-187"><xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute> is mainly relevant to the save path, but is available in the XAML type system in the load path by examining <xref:System.Xaml.XamlType.TrimSurroundingWhitespace%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ce6dc-188">如需詳細資訊，請參閱 [XAML 中](white-space-processing.md)的空白字元處理。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-188">For more information, see [White-space processing in XAML](white-space-processing.md).</span></span>

### <a name="typeconverterattribute"></a><span data-ttu-id="ce6dc-189">TypeConverterAttribute</span><span class="sxs-lookup"><span data-stu-id="ce6dc-189">TypeConverterAttribute</span></span>

<span data-ttu-id="ce6dc-190">**參考檔：**  <xref:System.ComponentModel.TypeConverterAttribute></span><span class="sxs-lookup"><span data-stu-id="ce6dc-190">**Reference Documentation:**  <xref:System.ComponentModel.TypeConverterAttribute></span></span>

<span data-ttu-id="ce6dc-191">**適用于：** 類別、屬性、方法 (唯一的 XAML 有效方法案例，是 `get` 支援可附加成員) 的存取子。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-191">**Applies to:** Class, property, method (the only XAML-valid method case is a `get` accessor that supports an attachable member).</span></span>

<span data-ttu-id="ce6dc-192">**引數：** 的 <xref:System.Type> <xref:System.ComponentModel.TypeConverter> 。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-192">**Arguments:** The <xref:System.Type> of the <xref:System.ComponentModel.TypeConverter>.</span></span>

<span data-ttu-id="ce6dc-193"><xref:System.ComponentModel.TypeConverterAttribute> 在 XAML 內容中，會參考自訂 <xref:System.ComponentModel.TypeConverter> 。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-193"><xref:System.ComponentModel.TypeConverterAttribute> in a XAML context references a custom <xref:System.ComponentModel.TypeConverter>.</span></span> <span data-ttu-id="ce6dc-194">這 <xref:System.ComponentModel.TypeConverter> 會提供自訂類型的類型轉換行為，或該類型的成員。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-194">This <xref:System.ComponentModel.TypeConverter> provides type conversion behavior for custom types, or members of that type.</span></span>

<span data-ttu-id="ce6dc-195">將 <xref:System.ComponentModel.TypeConverterAttribute> 屬性套用至您的類型，並參考您的類型轉換子執行。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-195">Apply the <xref:System.ComponentModel.TypeConverterAttribute> attribute to your type, referencing your type converter implementation.</span></span> <span data-ttu-id="ce6dc-196">您可以在類別、結構或介面上定義 XAML 的類型轉換器。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-196">You can define type converters for XAML on classes, structures, or interfaces.</span></span> <span data-ttu-id="ce6dc-197">您不需要提供列舉的型別轉換，就會以原生方式啟用轉換。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-197">You do not need to provide type conversion for enumerations, that conversion is enabled natively.</span></span>

<span data-ttu-id="ce6dc-198">您的類型轉換器應該能夠從用於標記之屬性或初始化文字的字串轉換成您想要的目的地類型。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-198">Your type converter should be able to convert from a string that is used for attributes or initialization text in markup, into your intended destination type.</span></span> <span data-ttu-id="ce6dc-199">如需詳細資訊，請參閱 [typeconverter 和 XAML](/dotnet/desktop/wpf/advanced/typeconverters-and-xaml)。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-199">For more information, see [TypeConverters and XAML](/dotnet/desktop/wpf/advanced/typeconverters-and-xaml).</span></span>

<span data-ttu-id="ce6dc-200">XAML 的類型轉換子行為也可以在特定屬性上建立，而不是套用至類型的所有值。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-200">Rather than applying to all values of a type, a type converter behavior for XAML can also be established on a specific property.</span></span> <span data-ttu-id="ce6dc-201">在此情況下，您會將 <xref:System.ComponentModel.TypeConverterAttribute> 屬性定義套用 (外部定義，而不是特定 `get` 和 `set` 定義) 。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-201">In this case, you apply <xref:System.ComponentModel.TypeConverterAttribute> to the property definition (the outer definition, not the specific `get` and `set` definitions).</span></span>

<span data-ttu-id="ce6dc-202">您可以套用 <xref:System.ComponentModel.TypeConverterAttribute> 至 `get` 支援 xaml 使用方式的方法存取子，藉以指派自訂可附加成員的 XAML 使用類型轉換器行為。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-202">A type converter behavior for XAML usage of a custom attachable member can be assigned by applying <xref:System.ComponentModel.TypeConverterAttribute> to the `get` method accessor that supports the XAML usage.</span></span>

<span data-ttu-id="ce6dc-203">類似于 <xref:System.ComponentModel.TypeConverter> ， <xref:System.ComponentModel.TypeConverterAttribute> .net 存在於 XAML 之前，以及型別轉換子模型為其他用途提供服務。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-203">Similar to <xref:System.ComponentModel.TypeConverter>, <xref:System.ComponentModel.TypeConverterAttribute> existed in .NET prior to the existence of XAML, and the type converter model served other purposes.</span></span> <span data-ttu-id="ce6dc-204"><xref:System.ComponentModel.TypeConverterAttribute>您必須完整限定或提供的語句，才能參考和使用 `using` <xref:System.ComponentModel> 。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-204">In order to reference and use <xref:System.ComponentModel.TypeConverterAttribute>, you must fully qualify it or provide a `using` statement for <xref:System.ComponentModel>.</span></span> <span data-ttu-id="ce6dc-205">也請在您的專案中包含系統元件。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-205">Also include the System assembly in your project.</span></span>

### <a name="uidpropertyattribute"></a><span data-ttu-id="ce6dc-206">UidPropertyAttribute</span><span class="sxs-lookup"><span data-stu-id="ce6dc-206">UidPropertyAttribute</span></span>

<span data-ttu-id="ce6dc-207">**參考檔：**  <xref:System.Windows.Markup.UidPropertyAttribute></span><span class="sxs-lookup"><span data-stu-id="ce6dc-207">**Reference Documentation:**  <xref:System.Windows.Markup.UidPropertyAttribute></span></span>

<span data-ttu-id="ce6dc-208">**適用于：** 類</span><span class="sxs-lookup"><span data-stu-id="ce6dc-208">**Applies to:** Class</span></span>

<span data-ttu-id="ce6dc-209">**引數：** 依名稱參考相關屬性的字串。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-209">**Arguments:** A string that references the relevant property by name.</span></span>

<span data-ttu-id="ce6dc-210">指出類別的 CLR 屬性，該類別會為 [x：Uid](xuid-directive.md)指示詞進行別名。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-210">Indicates the CLR property of a class that aliases the [x:Uid Directive](xuid-directive.md).</span></span>

### <a name="usableduringinitializationattribute"></a><span data-ttu-id="ce6dc-211">UsableDuringInitializationAttribute</span><span class="sxs-lookup"><span data-stu-id="ce6dc-211">UsableDuringInitializationAttribute</span></span>

<span data-ttu-id="ce6dc-212">**參考檔：**  <xref:System.Windows.Markup.UsableDuringInitializationAttribute></span><span class="sxs-lookup"><span data-stu-id="ce6dc-212">**Reference Documentation:**  <xref:System.Windows.Markup.UsableDuringInitializationAttribute></span></span>

<span data-ttu-id="ce6dc-213">**適用于：** 類</span><span class="sxs-lookup"><span data-stu-id="ce6dc-213">**Applies to:** Class</span></span>

<span data-ttu-id="ce6dc-214">**引數：** 布林值。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-214">**Arguments:** A Boolean.</span></span> <span data-ttu-id="ce6dc-215">如果用於屬性的預期用途，此值應該設定為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-215">If used for the attribute's intended purpose, the value should be set to `true`.</span></span>

<span data-ttu-id="ce6dc-216">指出型別是否在建立 XAML 物件圖形期間由上而下建立。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-216">Indicates whether the type is built top-down during XAML object graph creation.</span></span> <span data-ttu-id="ce6dc-217">這是一個很好的概念，可能與您的程式設計模型定義密切相關。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-217">This is an advanced concept, which is probably closely related to the definition of your programming model.</span></span> <span data-ttu-id="ce6dc-218">如需詳細資訊，請參閱<xref:System.Windows.Markup.UsableDuringInitializationAttribute>。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-218">For more information, see <xref:System.Windows.Markup.UsableDuringInitializationAttribute>.</span></span>

### <a name="valueserializerattribute"></a><span data-ttu-id="ce6dc-219">ValueSerializerAttribute</span><span class="sxs-lookup"><span data-stu-id="ce6dc-219">ValueSerializerAttribute</span></span>

<span data-ttu-id="ce6dc-220">**參考檔：**  <xref:System.Windows.Markup.ValueSerializerAttribute></span><span class="sxs-lookup"><span data-stu-id="ce6dc-220">**Reference Documentation:**  <xref:System.Windows.Markup.ValueSerializerAttribute></span></span>

<span data-ttu-id="ce6dc-221">**適用于：** 類別、屬性、方法 (唯一的 XAML 有效方法案例，是 `get` 支援可附加成員) 的存取子。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-221">**Applies to:** Class, property, method (the only XAML-valid method case is a `get` accessor that supports an attachable member).</span></span>

<span data-ttu-id="ce6dc-222">**引數：**<xref:System.Type>，指定序列化屬性化類型的所有屬性或特定屬性化屬性時所要使用的值序列化程式支援類別。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-222">**Arguments:** A <xref:System.Type> that specifies the value serializer support class to use when serializing all properties of the attributed type, or the specific attributed property.</span></span>

<span data-ttu-id="ce6dc-223"><xref:System.Windows.Markup.ValueSerializer> 指定需要更多狀態和內容的值序列化類別 <xref:System.ComponentModel.TypeConverter> 。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-223"><xref:System.Windows.Markup.ValueSerializer> specifies a value serialization class that requires more state and context than a <xref:System.ComponentModel.TypeConverter> does.</span></span> <span data-ttu-id="ce6dc-224"><xref:System.Windows.Markup.ValueSerializer> 可以在可 <xref:System.Windows.Markup.ValueSerializerAttribute> 附加成員的靜態存取子方法上套用屬性，以便與可附加的成員建立關聯 `get` 。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-224"><xref:System.Windows.Markup.ValueSerializer> can be associated with an attachable member by applying the <xref:System.Windows.Markup.ValueSerializerAttribute> attribute on the static `get` accessor method for the attachable member.</span></span> <span data-ttu-id="ce6dc-225">值序列化也適用于列舉、介面和結構，但不適用於委派。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-225">Value serialization is also applicable for enumerations, interfaces, and structures, but not for delegates.</span></span>

### <a name="whitespacesignificantcollectionattribute"></a><span data-ttu-id="ce6dc-226">WhitespaceSignificantCollectionAttribute</span><span class="sxs-lookup"><span data-stu-id="ce6dc-226">WhitespaceSignificantCollectionAttribute</span></span>

<span data-ttu-id="ce6dc-227">**參考檔：**  <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute></span><span class="sxs-lookup"><span data-stu-id="ce6dc-227">**Reference Documentation:**  <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute></span></span>

<span data-ttu-id="ce6dc-228">**適用于：** 類別，特別是預期會裝載混合內容的集合型別，其中物件專案周圍的空白字元對於 UI 表示而言可能很重要。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-228">**Applies to:** Class, specifically collection types that are expected to host mixed content, where white space around object elements might be significant for UI representation.</span></span>

<span data-ttu-id="ce6dc-229">**引數：** 沒有。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-229">**Arguments:** None.</span></span>

<span data-ttu-id="ce6dc-230"><xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> 表示集合類型應該以泛空白字元的方式處理，由 XAML 處理器所影響，而這會影響集合內 XAML 節點資料流程的值節點的結構。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-230"><xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> indicates that a collection type should be processed as white-space significant by a XAML processor, which influences the construction of the XAML node stream's value nodes within the collection.</span></span> <span data-ttu-id="ce6dc-231">如需詳細資訊，請參閱 [XAML 中](white-space-processing.md)的空白字元處理。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-231">For more information, see [White-space processing in XAML](white-space-processing.md).</span></span>

### <a name="xamldeferloadattribute"></a><span data-ttu-id="ce6dc-232">XamlDeferLoadAttribute</span><span class="sxs-lookup"><span data-stu-id="ce6dc-232">XamlDeferLoadAttribute</span></span>

<span data-ttu-id="ce6dc-233">**參考檔：**  <xref:System.Windows.Markup.XamlDeferLoadAttribute></span><span class="sxs-lookup"><span data-stu-id="ce6dc-233">**Reference Documentation:**  <xref:System.Windows.Markup.XamlDeferLoadAttribute></span></span>

<span data-ttu-id="ce6dc-234">**適用于：** 類別、屬性。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-234">**Applies to:** Class, property.</span></span>

<span data-ttu-id="ce6dc-235">**引數：** 支援兩種屬性形式的類型做為字串或類型 <xref:System.Type> 。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-235">**Arguments:** Supports two attribution forms types as strings, or types as <xref:System.Type>.</span></span> <span data-ttu-id="ce6dc-236">請參閱 <xref:System.Windows.Markup.XamlDeferLoadAttribute>。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-236">See <xref:System.Windows.Markup.XamlDeferLoadAttribute>.</span></span>

<span data-ttu-id="ce6dc-237">表示類別或屬性具有 XAML 的延後載入使用方式 (例如，範本行為)，並報告啟用延後行為的類別及其目的型別/內容型別。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-237">Indicates that a class or property has a deferred load usage for XAML (such as a template behavior), and reports the class that enables the deferring behavior and its destination/content type.</span></span>

### <a name="xamlsetmarkupextensionattribute"></a><span data-ttu-id="ce6dc-238">System.windows.markup.xamlsetmarkupextensionattribute</span><span class="sxs-lookup"><span data-stu-id="ce6dc-238">XamlSetMarkupExtensionAttribute</span></span>

<span data-ttu-id="ce6dc-239">**參考檔：**  <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute></span><span class="sxs-lookup"><span data-stu-id="ce6dc-239">**Reference Documentation:**  <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute></span></span>

<span data-ttu-id="ce6dc-240">**適用于：** 類</span><span class="sxs-lookup"><span data-stu-id="ce6dc-240">**Applies to:** Class</span></span>

<span data-ttu-id="ce6dc-241">**引數：** 為回呼命名。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-241">**Arguments:** Names the callback.</span></span>

<span data-ttu-id="ce6dc-242">指出類別可使用標記延伸來提供其一或多個屬性的值，並參考 XAML 寫入器在針對類別的任何屬性執行標記延伸集作業之前，應該呼叫的處理常式。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-242">Indicates that a class can use a markup extension to provide a value for one or more of its properties, and references a handler that a XAML writer should call before performing a markup extension set operation on any property of the class.</span></span>

### <a name="xamlsettypeconverterattribute"></a><span data-ttu-id="ce6dc-243">XamlSetTypeConverterAttribute</span><span class="sxs-lookup"><span data-stu-id="ce6dc-243">XamlSetTypeConverterAttribute</span></span>

<span data-ttu-id="ce6dc-244">**參考檔：**  <xref:System.Windows.Markup.XamlSetTypeConverterAttribute></span><span class="sxs-lookup"><span data-stu-id="ce6dc-244">**Reference Documentation:**  <xref:System.Windows.Markup.XamlSetTypeConverterAttribute></span></span>

<span data-ttu-id="ce6dc-245">**適用于：** 類</span><span class="sxs-lookup"><span data-stu-id="ce6dc-245">**Applies to:** Class</span></span>

<span data-ttu-id="ce6dc-246">**引數：** 為回呼命名。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-246">**Arguments:** Names the callback.</span></span>

<span data-ttu-id="ce6dc-247">指出類別可以使用類型轉換器來提供其一或多個屬性的值，並參考 XAML 寫入器在類別的任何屬性上執行類型轉換器設定作業之前，應該呼叫的處理常式。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-247">Indicates that a class can use a type converter to provide a value for one or more of its properties, and references a handler that a XAML writer should call before performing a type converter set operation on any property of the class.</span></span>

### <a name="xmllangpropertyattribute"></a><span data-ttu-id="ce6dc-248">XmlLangPropertyAttribute</span><span class="sxs-lookup"><span data-stu-id="ce6dc-248">XmlLangPropertyAttribute</span></span>

<span data-ttu-id="ce6dc-249">**參考檔：**  <xref:System.Windows.Markup.XmlLangPropertyAttribute></span><span class="sxs-lookup"><span data-stu-id="ce6dc-249">**Reference Documentation:**  <xref:System.Windows.Markup.XmlLangPropertyAttribute></span></span>

<span data-ttu-id="ce6dc-250">**適用于：** 類</span><span class="sxs-lookup"><span data-stu-id="ce6dc-250">**Applies to:** Class</span></span>

<span data-ttu-id="ce6dc-251">**引數：** 字串，指定屬性化類型上要別名的屬性名稱 `xml:lang` 。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-251">**Arguments:** A string that specifies the name of the property to alias to `xml:lang` on the attributed type.</span></span>

<span data-ttu-id="ce6dc-252"><xref:System.Windows.Markup.XmlLangPropertyAttribute> 報告與 XML 指示詞對應之屬性化型別的屬性（property） `lang` 。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-252"><xref:System.Windows.Markup.XmlLangPropertyAttribute> reports a property of the attributed type that maps to the XML `lang` directive.</span></span> <span data-ttu-id="ce6dc-253">屬性不一定是型別， <xref:System.String> 但必須可以從字串指派 (指派，方法是將型別轉換器與屬性的型別或特定屬性) 產生關聯。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-253">The property is not necessarily of type <xref:System.String> but must be assignable from a string (assignment could be accomplished by associating a type converter with the property's type or with the specific property).</span></span> <span data-ttu-id="ce6dc-254">屬性必須是讀取/寫入。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-254">The property must be read/write.</span></span>

<span data-ttu-id="ce6dc-255">對應的案例 `xml:lang` 是，執行時間物件模型可以存取 XML 指定的語言資訊，而不需要特別處理 XMLDOM。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-255">The scenario for mapping `xml:lang` is so that a runtime object model has access to XML-specified language information without specifically processing with an XMLDOM.</span></span>

<span data-ttu-id="ce6dc-256">定義會繼承到可指派給定義型別的所有衍生型別。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-256">The definition inherits to all derived types that are assignable to the defining type.</span></span> <span data-ttu-id="ce6dc-257">您可以在特定的衍生型別上套用，以覆寫特定衍生型別的定義 <xref:System.Windows.Markup.XmlLangPropertyAttribute> ，雖然這是不常見的情況。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-257">You can override the definition on a specific derived type by applying <xref:System.Windows.Markup.XmlLangPropertyAttribute> on the specific derived type, although that is an uncommon scenario.</span></span>

## <a name="xaml-related-clr-attributes-at-the-assembly-level"></a><span data-ttu-id="ce6dc-258">元件層級的 XAML 相關 CLR 屬性</span><span class="sxs-lookup"><span data-stu-id="ce6dc-258">XAML-Related CLR Attributes at the Assembly Level</span></span>

<span data-ttu-id="ce6dc-259">下列各節描述未套用至類型或成員定義，但改為套用至元件的 XAML 相關屬性。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-259">The following sections describe the XAML-related attributes that are not applied to types or member definitions, but are instead applied to assemblies.</span></span> <span data-ttu-id="ce6dc-260">這些屬性與定義程式庫（其中包含要在 XAML 中使用的自訂類型）的整體目標有關。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-260">These attributes are pertinent to the overall goal of defining a library that contains custom types to use in XAML.</span></span> <span data-ttu-id="ce6dc-261">某些屬性不一定會直接影響 XAML 節點資料流程，但會在節點資料流程中傳遞給其他取用者使用。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-261">Some of the attributes do not necessarily influence the XAML node stream directly, but are passed on in the node stream for other consumers to use.</span></span> <span data-ttu-id="ce6dc-262">資訊的取用者包括設計環境或需要 XAML 命名空間資訊的序列化程式，以及相關聯的前置詞資訊。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-262">Consumers for the information include design environments or serialization processes that need XAML namespace information and associated prefix information.</span></span> <span data-ttu-id="ce6dc-263">XAML 架構內容 (包括 .NET XAML 服務預設) 也會使用此資訊。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-263">A XAML schema context (including the .NET XAML Services default) also uses this information.</span></span>

### <a name="xmlnscompatiblewithattribute"></a><span data-ttu-id="ce6dc-264">XmlnsCompatibleWithAttribute</span><span class="sxs-lookup"><span data-stu-id="ce6dc-264">XmlnsCompatibleWithAttribute</span></span>

<span data-ttu-id="ce6dc-265">**參考檔：**  <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute></span><span class="sxs-lookup"><span data-stu-id="ce6dc-265">**Reference Documentation:**  <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute></span></span>

<span data-ttu-id="ce6dc-266">**引數:**</span><span class="sxs-lookup"><span data-stu-id="ce6dc-266">**Arguments:**</span></span>

- <span data-ttu-id="ce6dc-267">字串，指定要包含的 XAML 命名空間識別碼。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-267">A string that specifies the identifier of the XAML namespace to subsume.</span></span>

- <span data-ttu-id="ce6dc-268">字串，指定可從上一個引數包含 XAML 命名空間的 XAML 命名空間識別碼。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-268">A string that specifies the identifier of the XAML namespace that can subsume the XAML namespace from the previous argument.</span></span>

  <span data-ttu-id="ce6dc-269"><xref:System.Windows.Markup.XmlnsCompatibleWithAttribute> 指定 XAML 命名空間可由另一個 XAML 命名空間建立小計。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-269"><xref:System.Windows.Markup.XmlnsCompatibleWithAttribute> specifies that a XAML namespace can be subsumed by another XAML namespace.</span></span> <span data-ttu-id="ce6dc-270">一般會在預先定義的 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> 中指出建立小計的 XAML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-270">Typically, the subsuming XAML namespace is indicated in a previously defined <xref:System.Windows.Markup.XmlnsDefinitionAttribute>.</span></span> <span data-ttu-id="ce6dc-271">這項技術可以用來在程式庫中設定 XAML 詞彙的版本，並使其與先前已建立版本之詞彙的先前定義標記相容。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-271">This technique can be used for versioning a XAML vocabulary in a library and to make it compatible with previously defined markup against the earlier versioned vocabulary.</span></span>

### <a name="xmlnsdefinitionattribute"></a><span data-ttu-id="ce6dc-272">XmlnsDefinitionAttribute</span><span class="sxs-lookup"><span data-stu-id="ce6dc-272">XmlnsDefinitionAttribute</span></span>

<span data-ttu-id="ce6dc-273">**參考檔：**  <xref:System.Windows.Markup.XmlnsDefinitionAttribute></span><span class="sxs-lookup"><span data-stu-id="ce6dc-273">**Reference Documentation:**  <xref:System.Windows.Markup.XmlnsDefinitionAttribute></span></span>

<span data-ttu-id="ce6dc-274">**引數:**</span><span class="sxs-lookup"><span data-stu-id="ce6dc-274">**Arguments:**</span></span>

- <span data-ttu-id="ce6dc-275">字串，指定要定義的 XAML 命名空間識別碼。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-275">A string that specifies the identifier of the XAML namespace to define.</span></span>

- <span data-ttu-id="ce6dc-276">命名 CLR 命名空間的字串。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-276">A string that names a CLR namespace.</span></span> <span data-ttu-id="ce6dc-277">CLR 命名空間應該在您的元件中定義公用類型，而且至少要有一個 CLR 命名空間類型適用于 XAML 用法。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-277">The CLR namespace should define public types in your assembly, and at least one of the CLR namespace types should be intended for XAML usage.</span></span>

  <span data-ttu-id="ce6dc-278"><xref:System.Windows.Markup.XmlnsDefinitionAttribute> 指定 XAML 命名空間和 CLR 命名空間之間每個元件的對應，然後由 XAML 物件寫入器或 XAML 架構內容用於類型解析。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-278"><xref:System.Windows.Markup.XmlnsDefinitionAttribute> specifies a mapping on a per-assembly basis between a XAML namespace and a CLR namespace, which is then used for type resolution by a XAML object writer or XAML schema context.</span></span>

  <span data-ttu-id="ce6dc-279">您可以將一個以上 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> 的應用程式套用至元件。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-279">More than one <xref:System.Windows.Markup.XmlnsDefinitionAttribute> can be applied to an assembly.</span></span> <span data-ttu-id="ce6dc-280">這可能會因為下列任何組合而完成：</span><span class="sxs-lookup"><span data-stu-id="ce6dc-280">This might be done for any combination of the following reasons:</span></span>

- <span data-ttu-id="ce6dc-281">程式庫設計包含多個 CLR 命名空間，適用于執行時間 API 存取的邏輯組織;不過，您想要透過參考相同的 XAML 命名空間，讓這些命名空間中的所有型別都可以使用 XAML。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-281">The library design contains multiple CLR namespaces for logical organization of run-time API access; however, you want all types in those namespaces to be XAML-usable by referencing the same XAML namespace.</span></span> <span data-ttu-id="ce6dc-282">在此情況下，您會 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> 使用相同的 <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> 值，但不同的值來套用數個屬性 <xref:System.Windows.Markup.XmlnsDefinitionAttribute.ClrNamespace%2A> 。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-282">In this case, you apply several <xref:System.Windows.Markup.XmlnsDefinitionAttribute> attributes using the same <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> value but different <xref:System.Windows.Markup.XmlnsDefinitionAttribute.ClrNamespace%2A> values.</span></span> <span data-ttu-id="ce6dc-283">如果您要定義 XAML 命名空間的對應，架構或應用程式想要成為一般使用方式的預設 XAML 命名空間，這會特別有用。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-283">This is especially useful if you are defining mappings for the XAML namespace that your framework or application intends to be the default XAML namespace in common usage.</span></span>

- <span data-ttu-id="ce6dc-284">程式庫設計包含多個 CLR 命名空間，而您想要在這些 CLR 命名空間中的型別使用方式之間區隔刻意的 XAML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-284">The library design contains multiple CLR namespaces, and you want a deliberate XAML namespace separation between the usages of types in those CLR namespaces.</span></span>

- <span data-ttu-id="ce6dc-285">您可以在元件中定義 CLR 命名空間，而且想要透過多個 XAML 命名空間來存取它。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-285">You define a CLR namespace in the assembly, and you want it to be accessible through more than one XAML namespace.</span></span> <span data-ttu-id="ce6dc-286">當您使用相同的程式碼基底來支援多個詞彙時，就會發生此情況。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-286">This scenario occurs when you are supporting multiple vocabularies with the same codebase.</span></span>

- <span data-ttu-id="ce6dc-287">您可以在一或多個 CLR 命名空間中定義 XAML 語言支援。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-287">You define XAML language support in one or more CLR namespaces.</span></span> <span data-ttu-id="ce6dc-288">在此情況下，此 <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> 值應為 `http://schemas.microsoft.com/winfx/2006/xaml` 。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-288">In this case, the <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> value should be `http://schemas.microsoft.com/winfx/2006/xaml`.</span></span>

### <a name="xmlnsprefixattribute"></a><span data-ttu-id="ce6dc-289">XmlnsPrefixAttribute</span><span class="sxs-lookup"><span data-stu-id="ce6dc-289">XmlnsPrefixAttribute</span></span>

<span data-ttu-id="ce6dc-290">**參考檔：**  <xref:System.Windows.Markup.XmlnsPrefixAttribute></span><span class="sxs-lookup"><span data-stu-id="ce6dc-290">**Reference Documentation:**  <xref:System.Windows.Markup.XmlnsPrefixAttribute></span></span>

<span data-ttu-id="ce6dc-291">**引數:**</span><span class="sxs-lookup"><span data-stu-id="ce6dc-291">**Arguments:**</span></span>

- <span data-ttu-id="ce6dc-292">指定 XAML 命名空間識別碼的字串。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-292">A string that specifies the identifier of a XAML namespace.</span></span>

- <span data-ttu-id="ce6dc-293">指定建議前置詞的字串。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-293">A string that specifies a recommended prefix.</span></span>

  <span data-ttu-id="ce6dc-294"><xref:System.Windows.Markup.XmlnsDefinitionAttribute> 指定要用於 XAML 命名空間的建議前置詞。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-294"><xref:System.Windows.Markup.XmlnsDefinitionAttribute> specifies a recommended prefix to use for a XAML namespace.</span></span> <span data-ttu-id="ce6dc-295">當您在 .NET XAML 服務所序列化的 XAML 檔案中撰寫專案和屬性時 <xref:System.Xaml.XamlXmlWriter> ，或 xaml 執行程式庫與具有 XAML 編輯功能的設計環境互動時，前置詞會很有用。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-295">The prefix is useful when writing elements and attributes in a XAML file that is serialized by .NET XAML Services <xref:System.Xaml.XamlXmlWriter>, or when a XAML-implementing library interacts with a design environment that has XAML editing features.</span></span>

  <span data-ttu-id="ce6dc-296">您可以將一個以上 <xref:System.Windows.Markup.XmlnsPrefixAttribute> 的應用程式套用至元件。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-296">More than one <xref:System.Windows.Markup.XmlnsPrefixAttribute> can be applied to an assembly.</span></span> <span data-ttu-id="ce6dc-297">這可能會因為下列任何組合而完成：</span><span class="sxs-lookup"><span data-stu-id="ce6dc-297">This might be done for any combination of the following reasons:</span></span>

- <span data-ttu-id="ce6dc-298">您的元件會定義一個以上的 XAML 命名空間類型。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-298">Your assembly defines types for more than one XAML namespace.</span></span> <span data-ttu-id="ce6dc-299">在此情況下，請為每個 XAML 命名空間定義不同的前置詞值。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-299">In this case, define different prefix values for each XAML namespace.</span></span>

- <span data-ttu-id="ce6dc-300">您支援多個詞彙，且每個詞彙和 XAML 命名空間使用不同的首碼。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-300">You are supporting multiple vocabularies, and you use different prefixes for each vocabulary and XAML namespace.</span></span>

- <span data-ttu-id="ce6dc-301">您可以在元件中定義 XAML 語言支援，並 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> 為指定 `http://schemas.microsoft.com/winfx/2006/xaml` 。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-301">You define XAML language support in the assembly and have a <xref:System.Windows.Markup.XmlnsDefinitionAttribute> for `http://schemas.microsoft.com/winfx/2006/xaml`.</span></span> <span data-ttu-id="ce6dc-302">在此情況下，您通常應該升級前置詞 `x` 。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-302">In this case, you typically should promote the prefix `x`.</span></span>

> [!NOTE]
> <span data-ttu-id="ce6dc-303">.NET XAML 服務也會定義與 XAML 相關的屬性 <xref:System.Windows.Markup.RootNamespaceAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-303">.NET XAML Services also defines the XAML-related attribute <xref:System.Windows.Markup.RootNamespaceAttribute>.</span></span> <span data-ttu-id="ce6dc-304">這個屬性是專案系統支援的元件層級屬性，與 XAML 自訂類型無關。</span><span class="sxs-lookup"><span data-stu-id="ce6dc-304">This attribute is an assembly-level attribute for project system support, and it is not relevant for XAML custom types.</span></span>

## <a name="see-also"></a><span data-ttu-id="ce6dc-305">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce6dc-305">See also</span></span>

- <xref:System.Attribute>
- [<span data-ttu-id="ce6dc-306">定義可搭配 .NET XAML 服務使用的自訂類型</span><span class="sxs-lookup"><span data-stu-id="ce6dc-306">Defining Custom Types for Use with .NET XAML Services</span></span>](define-custom-types.md)
