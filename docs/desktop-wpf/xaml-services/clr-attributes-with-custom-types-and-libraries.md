---
title: 自訂類型和程式庫的 XAML 相關 CLR 屬性
ms.date: 03/30/2017
helpviewer_keywords:
- CLR attributes for custom types [XAML Services]
ms.assetid: 5dfb299a-b6e2-41b8-8694-e6ac987547f1
ms.openlocfilehash: 5481d02e4d393312fa0f0dd13b45c54acc567e13
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071763"
---
# <a name="xaml-related-clr-attributes-for-custom-types-and-libraries"></a><span data-ttu-id="05afc-102">自訂型態與函式庫的與 XAML 相關的 CLR 屬性</span><span class="sxs-lookup"><span data-stu-id="05afc-102">XAML-related CLR attributes for custom types and libraries</span></span>

<span data-ttu-id="05afc-103">本主題介紹由 .NET XAML 服務定義的通用語言運行時 (CLR) 屬性。</span><span class="sxs-lookup"><span data-stu-id="05afc-103">This topic describes the common language runtime (CLR) attributes that are defined by .NET XAML Services.</span></span> <span data-ttu-id="05afc-104">它還描述了在 .NET 中定義的其他 CLR 屬性,這些屬性具有與 XAML 相關的方案,用於應用程式到程式集或類型。</span><span class="sxs-lookup"><span data-stu-id="05afc-104">It also describes other CLR attributes that are defined in .NET that have a XAML-related scenario for application to assemblies or types.</span></span> <span data-ttu-id="05afc-105">將這些 CLR 屬性的程式集、類型或成員歸為具有 XAML 類型系統資訊,這些資訊與您的類型相關。</span><span class="sxs-lookup"><span data-stu-id="05afc-105">Attributing assemblies, types, or members with these CLR attributes provides XAML type system information related to your types.</span></span> <span data-ttu-id="05afc-106">資訊提供給使用 .NET XAML 服務直接或透過專用 XAML 讀取器和 XAML 編寫器處理 XAML 節點串流的任何 XAML 消費者。</span><span class="sxs-lookup"><span data-stu-id="05afc-106">Information is provided to any XAML consumer that uses .NET XAML Services for processing the XAML node stream directly or through the dedicated XAML readers and XAML writers.</span></span>

## <a name="xaml-related-clr-attributes-for-custom-types-and-custom-members"></a><span data-ttu-id="05afc-107">自訂型態與自訂成員的 XAML 相關 CLR 屬性</span><span class="sxs-lookup"><span data-stu-id="05afc-107">XAML-Related CLR Attributes for Custom Types and Custom Members</span></span>

<span data-ttu-id="05afc-108">使用 CLR 屬性意味著您使用整個 CLR 來定義類型,否則此類屬性不可用。</span><span class="sxs-lookup"><span data-stu-id="05afc-108">Using CLR attributes entails that you are using the overall CLR to define your types, otherwise such attributes are not available.</span></span> <span data-ttu-id="05afc-109">如果使用 CLR 定義類型備份,則 .NET XAML 服務 XAML 編寫器使用的預設 XAML 架構上下文可以通過反射來讀取 CLR 歸因。</span><span class="sxs-lookup"><span data-stu-id="05afc-109">If you use the CLR to define type backing, then the default XAML schema context used by .NET XAML Services XAML writers can read CLR attribution through reflection against backing assemblies.</span></span>

<span data-ttu-id="05afc-110">以下各節介紹可應用於自定義類型或自定義成員的與 XAML 相關的屬性。</span><span class="sxs-lookup"><span data-stu-id="05afc-110">The following sections describe the XAML-related attributes that you can apply to custom types or custom members.</span></span> <span data-ttu-id="05afc-111">每個 CLR 屬性都傳達與 XAML 類型系統相關的資訊。</span><span class="sxs-lookup"><span data-stu-id="05afc-111">Each CLR attribute communicates information that is relevant to a XAML type system.</span></span> <span data-ttu-id="05afc-112">在載入路徑中,屬性化資訊要麼説明 XAML 讀取器形成有效的 XAML 節點流,要麼説明 XAML 編寫器生成有效的物件圖。</span><span class="sxs-lookup"><span data-stu-id="05afc-112">In the load path, the attributed information either helps the XAML reader form a valid XAML node stream, or it helps the XAML writer produce a valid object graph.</span></span> <span data-ttu-id="05afc-113">在保存路徑中,屬性化資訊要麼説明 XAML 讀取器形成有效的 XAML 節點流,從而重新構成 XAML 類型系統資訊;或者聲明 XAML 編寫器或其他 XAML 消費者的序列化提示或要求。</span><span class="sxs-lookup"><span data-stu-id="05afc-113">In the save path, the attributed information either helps the XAML reader form a valid XAML node stream that reconstitutes XAML type system information; or it declares serialization hints or requirements for the XAML writer or other XAML consumers.</span></span>

### <a name="ambientattribute"></a><span data-ttu-id="05afc-114">環境屬性</span><span class="sxs-lookup"><span data-stu-id="05afc-114">AmbientAttribute</span></span>

<span data-ttu-id="05afc-115">**參考文件:**<xref:System.Windows.Markup.AmbientAttribute></span><span class="sxs-lookup"><span data-stu-id="05afc-115">**Reference Documentation:** <xref:System.Windows.Markup.AmbientAttribute></span></span>

<span data-ttu-id="05afc-116">**適用於:** 支援可附加屬性的`get`類、屬性或訪問器成員。</span><span class="sxs-lookup"><span data-stu-id="05afc-116">**Applies to:** Class, property, or `get` accessor members that support attachable properties.</span></span>

<span data-ttu-id="05afc-117">**參數:** 沒有</span><span class="sxs-lookup"><span data-stu-id="05afc-117">**Arguments:** None</span></span>

<span data-ttu-id="05afc-118"><xref:System.Windows.Markup.AmbientAttribute>指示屬性或採用屬性類型的所有屬性應在 XAML 中的環境屬性概念下解釋。</span><span class="sxs-lookup"><span data-stu-id="05afc-118"><xref:System.Windows.Markup.AmbientAttribute> indicates that the property, or all properties that take the attributed type, should be interpreted under the ambient property concept in XAML.</span></span> <span data-ttu-id="05afc-119">環境概念與 XAML 處理器如何判斷成員類別擁有者有關。</span><span class="sxs-lookup"><span data-stu-id="05afc-119">The ambient concept relates to how XAML processors determine type owners of members.</span></span> <span data-ttu-id="05afc-120">環境屬性是一個屬性,在創建物件圖時,該值在解析器上下文中可用,但在創建的直接 XAML 節點集時暫停典型的類型成員查找的屬性。</span><span class="sxs-lookup"><span data-stu-id="05afc-120">An ambient property is a property where the value is expected to be available in the parser context when creating an object graph, but where typical type-member lookup is suspended for the immediate XAML node set being created.</span></span>

<span data-ttu-id="05afc-121">環境概念可以應用於可附加成員,這些成員在 CLR 屬性定義方面不表示<xref:System.AttributeTargets>為屬性 。</span><span class="sxs-lookup"><span data-stu-id="05afc-121">The ambient concept can be applied to attachable members, which are not represented as properties in terms of how CLR attribution defines <xref:System.AttributeTargets>.</span></span> <span data-ttu-id="05afc-122">方法歸因用應僅適用於支援 XAML 可附加用`get`法的 訪問者。</span><span class="sxs-lookup"><span data-stu-id="05afc-122">The method attribution usage should be applied only for a `get` accessor that supports attachable usage for XAML.</span></span>

### <a name="constructorargumentattribute"></a><span data-ttu-id="05afc-123">建構函數參數屬性</span><span class="sxs-lookup"><span data-stu-id="05afc-123">ConstructorArgumentAttribute</span></span>

<span data-ttu-id="05afc-124">**參考文件:**  <xref:System.Windows.Markup.ConstructorArgumentAttribute></span><span class="sxs-lookup"><span data-stu-id="05afc-124">**Reference Documentation:**  <xref:System.Windows.Markup.ConstructorArgumentAttribute></span></span>

<span data-ttu-id="05afc-125">**適用於:** 類別</span><span class="sxs-lookup"><span data-stu-id="05afc-125">**Applies to:** Class</span></span>

<span data-ttu-id="05afc-126">**參數:** 指定與單個建構函數參數匹配的屬性名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="05afc-126">**Arguments:** A string that specifies the name of the property that matches a single constructor argument.</span></span>

<span data-ttu-id="05afc-127"><xref:System.Windows.Markup.ConstructorArgumentAttribute>指定可以使用非參數建構函數語法初始化物件,並且指定名稱的屬性提供構造資訊。</span><span class="sxs-lookup"><span data-stu-id="05afc-127"><xref:System.Windows.Markup.ConstructorArgumentAttribute> specifies that an object can be initialized by using a non-parameterless constructor syntax, and that a property of the specified name supplies construction information.</span></span> <span data-ttu-id="05afc-128">這項資訊主要供 XAML 序列化之用。</span><span class="sxs-lookup"><span data-stu-id="05afc-128">This information is primarily for XAML serialization.</span></span> <span data-ttu-id="05afc-129">如需詳細資訊，請參閱 <xref:System.Windows.Markup.ConstructorArgumentAttribute>。</span><span class="sxs-lookup"><span data-stu-id="05afc-129">For more information, see <xref:System.Windows.Markup.ConstructorArgumentAttribute>.</span></span>

### <a name="contentpropertyattribute"></a><span data-ttu-id="05afc-130">內容屬性屬性</span><span class="sxs-lookup"><span data-stu-id="05afc-130">ContentPropertyAttribute</span></span>

<span data-ttu-id="05afc-131">**參考文件:**  <xref:System.Windows.Markup.ContentPropertyAttribute></span><span class="sxs-lookup"><span data-stu-id="05afc-131">**Reference Documentation:**  <xref:System.Windows.Markup.ContentPropertyAttribute></span></span>

<span data-ttu-id="05afc-132">**適用於:** 類別</span><span class="sxs-lookup"><span data-stu-id="05afc-132">**Applies to:** Class</span></span>

<span data-ttu-id="05afc-133">**參數:** 指定屬性類型成員名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="05afc-133">**Arguments:** A string that specifies the name of a member of the attributed type.</span></span>

<span data-ttu-id="05afc-134"><xref:System.Windows.Markup.ContentPropertyAttribute>指示參數命名的屬性應用作該類型的 XAML 內容屬性。</span><span class="sxs-lookup"><span data-stu-id="05afc-134"><xref:System.Windows.Markup.ContentPropertyAttribute> indicates that the property as named by the argument should serve as the XAML content property for that type.</span></span> <span data-ttu-id="05afc-135">XAML 內容屬性定義將繼承到可分配給定義類型的所有派生類型。</span><span class="sxs-lookup"><span data-stu-id="05afc-135">The XAML content property definition inherits to all derived types that are assignable to the defining type.</span></span> <span data-ttu-id="05afc-136">可以通過應用<xref:System.Windows.Markup.ContentPropertyAttribute>於 特定派生類型來覆蓋特定派生類型上的定義。</span><span class="sxs-lookup"><span data-stu-id="05afc-136">You can override the definition on a specific derived type by applying <xref:System.Windows.Markup.ContentPropertyAttribute> on the specific derived type.</span></span>

<span data-ttu-id="05afc-137">對於用作 XAML 內容屬性的屬性,可以在 XAML 用法中省略該屬性的屬性元素標記。</span><span class="sxs-lookup"><span data-stu-id="05afc-137">For the property that serves as the XAML content property, property element tagging for the property can be omitted in the XAML usage.</span></span> <span data-ttu-id="05afc-138">通常,您指定 XAML 內容屬性,這些屬性可為您的內容和包含模型推廣簡化的 XAML 標記。</span><span class="sxs-lookup"><span data-stu-id="05afc-138">Typically, you designate XAML content properties that promote a streamlined XAML markup for your content and containment models.</span></span> <span data-ttu-id="05afc-139">由於只能將一個成員指定為 XAML 內容屬性,因此您有時可以選擇將某種類型的多個容器屬性中的哪一個指定為 XAML 內容屬性。</span><span class="sxs-lookup"><span data-stu-id="05afc-139">Because only one member can be designated as the XAML content property, you sometimes have design choices to make regarding which of several container properties of a type should be designated as the XAML content property.</span></span> <span data-ttu-id="05afc-140">其他容器屬性必須與顯式屬性元素一起使用。</span><span class="sxs-lookup"><span data-stu-id="05afc-140">The other container properties must be used with explicit property elements.</span></span>

<span data-ttu-id="05afc-141">在 XAML 節點串流中,XAML 內容`StartMember`屬性`EndMember`, 使用的屬性<xref:System.Xaml.XamlMember>的名稱產生和節點 。</span><span class="sxs-lookup"><span data-stu-id="05afc-141">In the XAML node stream, XAML content properties still produce `StartMember` and `EndMember` nodes, using the name of the property for the <xref:System.Xaml.XamlMember>.</span></span> <span data-ttu-id="05afc-142">要決定成員是否為 XAML 內容屬性,<xref:System.Xaml.XamlType>`StartObject`請從 位置檢查值並<xref:System.Xaml.XamlType.ContentProperty%2A>取得的值 。</span><span class="sxs-lookup"><span data-stu-id="05afc-142">To determine whether a member is the XAML content property, examine the <xref:System.Xaml.XamlType> value from the `StartObject` position and obtain the value of <xref:System.Xaml.XamlType.ContentProperty%2A>.</span></span>

### <a name="contentwrapperattribute"></a><span data-ttu-id="05afc-143">內容包裝屬性</span><span class="sxs-lookup"><span data-stu-id="05afc-143">ContentWrapperAttribute</span></span>

<span data-ttu-id="05afc-144">**參考文件:**  <xref:System.Windows.Markup.ContentWrapperAttribute></span><span class="sxs-lookup"><span data-stu-id="05afc-144">**Reference Documentation:**  <xref:System.Windows.Markup.ContentWrapperAttribute></span></span>

<span data-ttu-id="05afc-145">**適用於:** 類,特別是集合類型。</span><span class="sxs-lookup"><span data-stu-id="05afc-145">**Applies to:** Class, specifically collection types.</span></span>

<span data-ttu-id="05afc-146">**參數:** 指定<xref:System.Type>用作外國內容內容包裝類型的類型的類型。</span><span class="sxs-lookup"><span data-stu-id="05afc-146">**Arguments:** A <xref:System.Type> that specifies the type to use as the content wrapper type for foreign content.</span></span>

<span data-ttu-id="05afc-147"><xref:System.Windows.Markup.ContentWrapperAttribute>指定將用於包裝外來內容的關聯集合類型的一個或多個類型。</span><span class="sxs-lookup"><span data-stu-id="05afc-147"><xref:System.Windows.Markup.ContentWrapperAttribute> specifies one or more types on the associated collection type that will be used to wrap foreign content.</span></span> <span data-ttu-id="05afc-148">外國內容是指內容屬性類型的類型系統約束未捕獲擁有類型的 XAML 使用的所有可能內容情形的情況。</span><span class="sxs-lookup"><span data-stu-id="05afc-148">Foreign content refers to cases where the type system constraints on the type of the content property do not capture all of the possible content cases that XAML usage for the owning type would support.</span></span> <span data-ttu-id="05afc-149">例如,對特定類型內容的 XAML 支援可能支援強類型<xref:System.Collections.ObjectModel.Collection%601>泛型 中的字串。</span><span class="sxs-lookup"><span data-stu-id="05afc-149">For example, XAML support for content of a particular type might support strings in a strongly typed generic <xref:System.Collections.ObjectModel.Collection%601>.</span></span> <span data-ttu-id="05afc-150">內容包裝器可用於將預先存在的標記約定遷移到 XAML 的集合可分配值的概念中,例如遷移與文本相關的內容模型。</span><span class="sxs-lookup"><span data-stu-id="05afc-150">Content wrappers are useful for migrating pre-existing markup conventions into XAML's conception of assignable values for collections, such as migrating text-related content models.</span></span>

<span data-ttu-id="05afc-151">要指定多個內容包裝類型,請多次應用該屬性。</span><span class="sxs-lookup"><span data-stu-id="05afc-151">To specify more than one content wrapper type, apply the attribute multiple times.</span></span>

### <a name="dependsonattribute"></a><span data-ttu-id="05afc-152">相依屬性</span><span class="sxs-lookup"><span data-stu-id="05afc-152">DependsOnAttribute</span></span>

<span data-ttu-id="05afc-153">**參考文件:**  <xref:System.Windows.Markup.DependsOnAttribute></span><span class="sxs-lookup"><span data-stu-id="05afc-153">**Reference Documentation:**  <xref:System.Windows.Markup.DependsOnAttribute></span></span>

<span data-ttu-id="05afc-154">**適用於:** 財產</span><span class="sxs-lookup"><span data-stu-id="05afc-154">**Applies to:** Property</span></span>

<span data-ttu-id="05afc-155">**參數:** 指定屬性類型另一個成員名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="05afc-155">**Arguments:** A string that specifies the name of another member of the attributed type.</span></span>

<span data-ttu-id="05afc-156"><xref:System.Windows.Markup.DependsOnAttribute>指示屬性屬性取決於另一個屬性的值。</span><span class="sxs-lookup"><span data-stu-id="05afc-156"><xref:System.Windows.Markup.DependsOnAttribute> indicates that the attributed property depends on the value of another property.</span></span> <span data-ttu-id="05afc-157">將此屬性應用於屬性定義可確保在 XAML 物件寫入中首先處理從屬屬性。</span><span class="sxs-lookup"><span data-stu-id="05afc-157">Applying this attribute to a property definition ensures that the dependent properties are processed first in XAML object writing.</span></span> <span data-ttu-id="05afc-158">的<xref:System.Windows.Markup.DependsOnAttribute>用法指定屬性的特殊情況,這些類型對於有效物件創建必須遵循特定的分析順序。</span><span class="sxs-lookup"><span data-stu-id="05afc-158">Usages of <xref:System.Windows.Markup.DependsOnAttribute> specify the exceptional cases of properties on types where a specific order of parsing must be followed for valid object creation.</span></span>

<span data-ttu-id="05afc-159">您可以將多個<xref:System.Windows.Markup.DependsOnAttribute>案例應用於屬性定義。</span><span class="sxs-lookup"><span data-stu-id="05afc-159">You can apply multiple <xref:System.Windows.Markup.DependsOnAttribute> cases to a property definition.</span></span>

### <a name="markupextensionreturntypeattribute"></a><span data-ttu-id="05afc-160">標記延伸傳回類型屬性</span><span class="sxs-lookup"><span data-stu-id="05afc-160">MarkupExtensionReturnTypeAttribute</span></span>

<span data-ttu-id="05afc-161">**參考文件:**  <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute></span><span class="sxs-lookup"><span data-stu-id="05afc-161">**Reference Documentation:**  <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute></span></span>

<span data-ttu-id="05afc-162">**適用於:** 類,應為<xref:System.Windows.Markup.MarkupExtension>派生類型。</span><span class="sxs-lookup"><span data-stu-id="05afc-162">**Applies to:** Class, which is expected to be a <xref:System.Windows.Markup.MarkupExtension> derived type.</span></span>

<span data-ttu-id="05afc-163">**參數:**<xref:System.Type>指定作為`ProvideValue`<xref:System.Windows.Markup.MarkupExtension>屬性的結果預期的最精確類型。</span><span class="sxs-lookup"><span data-stu-id="05afc-163">**Arguments:** A <xref:System.Type> that specifies the most precise type to expect as the `ProvideValue` result of the attributed <xref:System.Windows.Markup.MarkupExtension>.</span></span>

<span data-ttu-id="05afc-164">有關詳細資訊,請參閱[XAML 概述的標記延伸](markup-extensions-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="05afc-164">For more information, see [Markup Extensions for XAML Overview](markup-extensions-overview.md).</span></span>

### <a name="namescopepropertyattribute"></a><span data-ttu-id="05afc-165">名稱範圍屬性</span><span class="sxs-lookup"><span data-stu-id="05afc-165">NameScopePropertyAttribute</span></span>

<span data-ttu-id="05afc-166">**參考文件:**  <xref:System.Windows.Markup.NameScopePropertyAttribute></span><span class="sxs-lookup"><span data-stu-id="05afc-166">**Reference Documentation:**  <xref:System.Windows.Markup.NameScopePropertyAttribute></span></span>

<span data-ttu-id="05afc-167">**適用於:** 類別</span><span class="sxs-lookup"><span data-stu-id="05afc-167">**Applies to:** Class</span></span>

<span data-ttu-id="05afc-168">**參數:** 支援兩種歸因形式:</span><span class="sxs-lookup"><span data-stu-id="05afc-168">**Arguments:** Supports two forms of attribution:</span></span>

- <span data-ttu-id="05afc-169">指定屬性類型上屬性名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="05afc-169">A string that specifies the name of a property on the attributed type.</span></span>

- <span data-ttu-id="05afc-170">指定屬性名稱的字串,以及定義命名屬性的類型的<xref:System.Type>字串。</span><span class="sxs-lookup"><span data-stu-id="05afc-170">A string that specifies the name of a property, and a <xref:System.Type> for the type that defines the named property.</span></span> <span data-ttu-id="05afc-171">此表單用於將可附加成員指定為 XAML 命名範圍屬性。</span><span class="sxs-lookup"><span data-stu-id="05afc-171">This form is for specifying an attachable member as the XAML namescope property.</span></span>

<span data-ttu-id="05afc-172"><xref:System.Windows.Markup.NameScopePropertyAttribute>指定為屬性類提供 XAML 命名範圍值的屬性。</span><span class="sxs-lookup"><span data-stu-id="05afc-172"><xref:System.Windows.Markup.NameScopePropertyAttribute> specifies a property that provides the XAML namescope value for the attributed class.</span></span> <span data-ttu-id="05afc-173">XAML 命名範圍屬性應參考<xref:System.Windows.Markup.INameScope>實現 並保存實際 XAML 名稱範圍、其存儲及其行為的物件。</span><span class="sxs-lookup"><span data-stu-id="05afc-173">The XAML namescope property is expected to reference an object that implements <xref:System.Windows.Markup.INameScope> and holds the actual XAML namescope, its store, and its behavior.</span></span>

### <a name="runtimenamepropertyattribute"></a><span data-ttu-id="05afc-174">執行時名稱屬性屬性</span><span class="sxs-lookup"><span data-stu-id="05afc-174">RuntimeNamePropertyAttribute</span></span>

<span data-ttu-id="05afc-175">**參考文件:**  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute></span><span class="sxs-lookup"><span data-stu-id="05afc-175">**Reference Documentation:**  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute></span></span>

<span data-ttu-id="05afc-176">**適用於:** 類別</span><span class="sxs-lookup"><span data-stu-id="05afc-176">**Applies to:** Class</span></span>

<span data-ttu-id="05afc-177">**參數:** 指定屬性化類型上的執行時名稱屬性名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="05afc-177">**Arguments:** A string that specifies the name of the run-time name property on the attributed type.</span></span>

<span data-ttu-id="05afc-178"><xref:System.Windows.Markup.RuntimeNamePropertyAttribute>報告對應到 XAML [x:Name 指令](xname-directive.md)的屬性類型。</span><span class="sxs-lookup"><span data-stu-id="05afc-178"><xref:System.Windows.Markup.RuntimeNamePropertyAttribute> reports a property of the attributed type that maps to the XAML [x:Name Directive](xname-directive.md).</span></span> <span data-ttu-id="05afc-179">屬性必須為類型<xref:System.String>,並且必須讀取/寫入。</span><span class="sxs-lookup"><span data-stu-id="05afc-179">The property must be of type <xref:System.String> and must be read/write.</span></span>

<span data-ttu-id="05afc-180">定義將繼承到可分配給定義類型的所有派生類型。</span><span class="sxs-lookup"><span data-stu-id="05afc-180">The definition inherits to all derived types that are assignable to the defining type.</span></span> <span data-ttu-id="05afc-181">可以通過應用<xref:System.Windows.Markup.RuntimeNamePropertyAttribute>於 特定派生類型來覆蓋特定派生類型上的定義。</span><span class="sxs-lookup"><span data-stu-id="05afc-181">You can override the definition on a specific derived type by applying <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> on the specific derived type.</span></span>

### <a name="trimsurroundingwhitespaceattribute"></a><span data-ttu-id="05afc-182">修剪包圍空白屬性</span><span class="sxs-lookup"><span data-stu-id="05afc-182">TrimSurroundingWhitespaceAttribute</span></span>

<span data-ttu-id="05afc-183">**參考文件:**  <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute></span><span class="sxs-lookup"><span data-stu-id="05afc-183">**Reference Documentation:**  <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute></span></span>

<span data-ttu-id="05afc-184">**適用於:** 類型</span><span class="sxs-lookup"><span data-stu-id="05afc-184">**Applies to:** Types</span></span>

<span data-ttu-id="05afc-185">**參數:** 沒有。</span><span class="sxs-lookup"><span data-stu-id="05afc-185">**Arguments:** None.</span></span>

<span data-ttu-id="05afc-186"><xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>應用於可能顯示為空白重要內容中的子元素的特定類型(由<xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>具有的集合持有的內容)。</span><span class="sxs-lookup"><span data-stu-id="05afc-186"><xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute> is applied to specific types that might appear as child elements within white-space significant content (content held by a collection that has <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>).</span></span> <span data-ttu-id="05afc-187"><xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>主要與保存路徑相關,但通過檢查<xref:System.Xaml.XamlType.TrimSurroundingWhitespace%2A?displayProperty=nameWithType>在負載路徑中的 XAML 類型系統中可用。</span><span class="sxs-lookup"><span data-stu-id="05afc-187"><xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute> is mainly relevant to the save path, but is available in the XAML type system in the load path by examining <xref:System.Xaml.XamlType.TrimSurroundingWhitespace%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="05afc-188">有關詳細資訊,請參閱[XAML 中的空白處理](white-space-processing.md)。</span><span class="sxs-lookup"><span data-stu-id="05afc-188">For more information, see [White-space processing in XAML](white-space-processing.md).</span></span>

### <a name="typeconverterattribute"></a><span data-ttu-id="05afc-189">TypeConverterAttribute</span><span class="sxs-lookup"><span data-stu-id="05afc-189">TypeConverterAttribute</span></span>

<span data-ttu-id="05afc-190">**參考文件:**  <xref:System.ComponentModel.TypeConverterAttribute></span><span class="sxs-lookup"><span data-stu-id="05afc-190">**Reference Documentation:**  <xref:System.ComponentModel.TypeConverterAttribute></span></span>

<span data-ttu-id="05afc-191">**適用於:** 類、屬性、方法(唯一`get`的 XAML 有效方法大小寫是支援可連接成員的存取器)。</span><span class="sxs-lookup"><span data-stu-id="05afc-191">**Applies to:** Class, property, method (the only XAML-valid method case is a `get` accessor that supports an attachable member).</span></span>

<span data-ttu-id="05afc-192">**參數:** 的<xref:System.Type><xref:System.ComponentModel.TypeConverter>。</span><span class="sxs-lookup"><span data-stu-id="05afc-192">**Arguments:** The <xref:System.Type> of the <xref:System.ComponentModel.TypeConverter>.</span></span>

<span data-ttu-id="05afc-193"><xref:System.ComponentModel.TypeConverterAttribute>在 XAML 內文中引用<xref:System.ComponentModel.TypeConverter>自訂 。</span><span class="sxs-lookup"><span data-stu-id="05afc-193"><xref:System.ComponentModel.TypeConverterAttribute> in a XAML context references a custom <xref:System.ComponentModel.TypeConverter>.</span></span> <span data-ttu-id="05afc-194">這為<xref:System.ComponentModel.TypeConverter>自定義類型或該類型的成員提供類型轉換行為。</span><span class="sxs-lookup"><span data-stu-id="05afc-194">This <xref:System.ComponentModel.TypeConverter> provides type conversion behavior for custom types, or members of that type.</span></span>

<span data-ttu-id="05afc-195">將<xref:System.ComponentModel.TypeConverterAttribute>該屬性應用於類型,引用類型轉換器實現。</span><span class="sxs-lookup"><span data-stu-id="05afc-195">Apply the <xref:System.ComponentModel.TypeConverterAttribute> attribute to your type, referencing your type converter implementation.</span></span> <span data-ttu-id="05afc-196">您可以在類、結構或介面上為 XAML 定義類型轉換器。</span><span class="sxs-lookup"><span data-stu-id="05afc-196">You can define type converters for XAML on classes, structures, or interfaces.</span></span> <span data-ttu-id="05afc-197">您無需為枚舉提供類型轉換,該轉換是本機啟用的。</span><span class="sxs-lookup"><span data-stu-id="05afc-197">You do not need to provide type conversion for enumerations, that conversion is enabled natively.</span></span>

<span data-ttu-id="05afc-198">類型轉換器應該能夠從用於標記中的屬性或初始化文本的字串轉換為預期的目標類型。</span><span class="sxs-lookup"><span data-stu-id="05afc-198">Your type converter should be able to convert from a string that is used for attributes or initialization text in markup, into your intended destination type.</span></span> <span data-ttu-id="05afc-199">有關詳細資訊,請參考[類型轉換器與 XAML](../../framework/wpf/advanced/typeconverters-and-xaml.md)。</span><span class="sxs-lookup"><span data-stu-id="05afc-199">For more information, see [TypeConverters and XAML](../../framework/wpf/advanced/typeconverters-and-xaml.md).</span></span>

<span data-ttu-id="05afc-200">也可以在特定屬性上建立 XAML 的類型轉換器行為,而不是應用於類型的所有值。</span><span class="sxs-lookup"><span data-stu-id="05afc-200">Rather than applying to all values of a type, a type converter behavior for XAML can also be established on a specific property.</span></span> <span data-ttu-id="05afc-201">在這種情況下,您將應用於<xref:System.ComponentModel.TypeConverterAttribute>屬性定義(外部定義,而不是`get`特定定義`set`和定義)。</span><span class="sxs-lookup"><span data-stu-id="05afc-201">In this case, you apply <xref:System.ComponentModel.TypeConverterAttribute> to the property definition (the outer definition, not the specific `get` and `set` definitions).</span></span>

<span data-ttu-id="05afc-202">可以通過應用<xref:System.ComponentModel.TypeConverterAttribute>於支援 XAML`get`用法 的方法存取器來分配自訂可連接成員的 XAML 使用的類型轉換器行為。</span><span class="sxs-lookup"><span data-stu-id="05afc-202">A type converter behavior for XAML usage of a custom attachable member can be assigned by applying <xref:System.ComponentModel.TypeConverterAttribute> to the `get` method accessor that supports the XAML usage.</span></span>

<span data-ttu-id="05afc-203">與<xref:System.ComponentModel.TypeConverter>類似<xref:System.ComponentModel.TypeConverterAttribute>,在 XAML 存在之前存在於 .NET 中,類型轉換器模型具有其他用途。</span><span class="sxs-lookup"><span data-stu-id="05afc-203">Similar to <xref:System.ComponentModel.TypeConverter>, <xref:System.ComponentModel.TypeConverterAttribute> existed in .NET prior to the existence of XAML, and the type converter model served other purposes.</span></span> <span data-ttu-id="05afc-204">為了引用和使用<xref:System.ComponentModel.TypeConverterAttribute>,您必須完全限定它或`using`提供 語<xref:System.ComponentModel>句。</span><span class="sxs-lookup"><span data-stu-id="05afc-204">In order to reference and use <xref:System.ComponentModel.TypeConverterAttribute>, you must fully qualify it or provide a `using` statement for <xref:System.ComponentModel>.</span></span> <span data-ttu-id="05afc-205">還在專案中包括系統程式集。</span><span class="sxs-lookup"><span data-stu-id="05afc-205">Also include the System assembly in your project.</span></span>

### <a name="uidpropertyattribute"></a><span data-ttu-id="05afc-206">烏德屬性</span><span class="sxs-lookup"><span data-stu-id="05afc-206">UidPropertyAttribute</span></span>

<span data-ttu-id="05afc-207">**參考文件:**  <xref:System.Windows.Markup.UidPropertyAttribute></span><span class="sxs-lookup"><span data-stu-id="05afc-207">**Reference Documentation:**  <xref:System.Windows.Markup.UidPropertyAttribute></span></span>

<span data-ttu-id="05afc-208">**適用於:** 類別</span><span class="sxs-lookup"><span data-stu-id="05afc-208">**Applies to:** Class</span></span>

<span data-ttu-id="05afc-209">**參數:** 依名稱引用相關屬性的字串。</span><span class="sxs-lookup"><span data-stu-id="05afc-209">**Arguments:** A string that references the relevant property by name.</span></span>

<span data-ttu-id="05afc-210">指示別名[x:Uid 指令](xuid-directive.md)的類的 CLR 屬性。</span><span class="sxs-lookup"><span data-stu-id="05afc-210">Indicates the CLR property of a class that aliases the [x:Uid Directive](xuid-directive.md).</span></span>

### <a name="usableduringinitializationattribute"></a><span data-ttu-id="05afc-211">初始化期間可用屬性</span><span class="sxs-lookup"><span data-stu-id="05afc-211">UsableDuringInitializationAttribute</span></span>

<span data-ttu-id="05afc-212">**參考文件:**  <xref:System.Windows.Markup.UsableDuringInitializationAttribute></span><span class="sxs-lookup"><span data-stu-id="05afc-212">**Reference Documentation:**  <xref:System.Windows.Markup.UsableDuringInitializationAttribute></span></span>

<span data-ttu-id="05afc-213">**適用於:** 類別</span><span class="sxs-lookup"><span data-stu-id="05afc-213">**Applies to:** Class</span></span>

<span data-ttu-id="05afc-214">**參數:** 一個布爾。</span><span class="sxs-lookup"><span data-stu-id="05afc-214">**Arguments:** A Boolean.</span></span> <span data-ttu-id="05afc-215">如果用於屬性的預期用途,則該值應設定為`true`。</span><span class="sxs-lookup"><span data-stu-id="05afc-215">If used for the attribute's intended purpose, the value should be set to `true`.</span></span>

<span data-ttu-id="05afc-216">指示類型在 XAML 物件圖形創建期間是否自上而下生成。</span><span class="sxs-lookup"><span data-stu-id="05afc-216">Indicates whether the type is built top-down during XAML object graph creation.</span></span> <span data-ttu-id="05afc-217">這是一個高級概念,可能與程式設計模型的定義密切相關。</span><span class="sxs-lookup"><span data-stu-id="05afc-217">This is an advanced concept, which is probably closely related to the definition of your programming model.</span></span> <span data-ttu-id="05afc-218">如需詳細資訊，請參閱 <xref:System.Windows.Markup.UsableDuringInitializationAttribute>。</span><span class="sxs-lookup"><span data-stu-id="05afc-218">For more information, see <xref:System.Windows.Markup.UsableDuringInitializationAttribute>.</span></span>

### <a name="valueserializerattribute"></a><span data-ttu-id="05afc-219">值序列器屬性</span><span class="sxs-lookup"><span data-stu-id="05afc-219">ValueSerializerAttribute</span></span>

<span data-ttu-id="05afc-220">**參考文件:**  <xref:System.Windows.Markup.ValueSerializerAttribute></span><span class="sxs-lookup"><span data-stu-id="05afc-220">**Reference Documentation:**  <xref:System.Windows.Markup.ValueSerializerAttribute></span></span>

<span data-ttu-id="05afc-221">**適用於:** 類、屬性、方法(唯一`get`的 XAML 有效方法大小寫是支援可連接成員的存取器)。</span><span class="sxs-lookup"><span data-stu-id="05afc-221">**Applies to:** Class, property, method (the only XAML-valid method case is a `get` accessor that supports an attachable member).</span></span>

<span data-ttu-id="05afc-222">**參數:** 指定<xref:System.Type>在序列化屬性類型或特定屬性屬性的所有屬性時要使用的值序列化器支援類。</span><span class="sxs-lookup"><span data-stu-id="05afc-222">**Arguments:** A <xref:System.Type> that specifies the value serializer support class to use when serializing all properties of the attributed type, or the specific attributed property.</span></span>

<span data-ttu-id="05afc-223"><xref:System.Windows.Markup.ValueSerializer>指定值序列化類,該類需要比 更多的<xref:System.ComponentModel.TypeConverter>狀態和上下文。</span><span class="sxs-lookup"><span data-stu-id="05afc-223"><xref:System.Windows.Markup.ValueSerializer> specifies a value serialization class that requires more state and context than a <xref:System.ComponentModel.TypeConverter> does.</span></span> <span data-ttu-id="05afc-224"><xref:System.Windows.Markup.ValueSerializer>通過將屬性應用於可附加成員的靜態<xref:System.Windows.Markup.ValueSerializerAttribute>`get`訪問器方法,可以與可連接成員關聯。</span><span class="sxs-lookup"><span data-stu-id="05afc-224"><xref:System.Windows.Markup.ValueSerializer> can be associated with an attachable member by applying the <xref:System.Windows.Markup.ValueSerializerAttribute> attribute on the static `get` accessor method for the attachable member.</span></span> <span data-ttu-id="05afc-225">值序列化也適用於枚舉、介面和結構,但不適用於委託。</span><span class="sxs-lookup"><span data-stu-id="05afc-225">Value serialization is also applicable for enumerations, interfaces, and structures, but not for delegates.</span></span>

### <a name="whitespacesignificantcollectionattribute"></a><span data-ttu-id="05afc-226">空白顯著集合屬性</span><span class="sxs-lookup"><span data-stu-id="05afc-226">WhitespaceSignificantCollectionAttribute</span></span>

<span data-ttu-id="05afc-227">**參考文件:**  <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute></span><span class="sxs-lookup"><span data-stu-id="05afc-227">**Reference Documentation:**  <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute></span></span>

<span data-ttu-id="05afc-228">**適用於:** 類,特別是預期承載混合內容的集合類型,其中物件元素周圍的空白對於UI表示可能很重要。</span><span class="sxs-lookup"><span data-stu-id="05afc-228">**Applies to:** Class, specifically collection types that are expected to host mixed content, where white space around object elements might be significant for UI representation.</span></span>

<span data-ttu-id="05afc-229">**參數:** 沒有。</span><span class="sxs-lookup"><span data-stu-id="05afc-229">**Arguments:** None.</span></span>

<span data-ttu-id="05afc-230"><xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>指示集合類型應被 XAML 處理器處理為具有顯著意義的空格,這會影響集合中 XAML 節點流的值節點的構造。</span><span class="sxs-lookup"><span data-stu-id="05afc-230"><xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> indicates that a collection type should be processed as white-space significant by a XAML processor, which influences the construction of the XAML node stream's value nodes within the collection.</span></span> <span data-ttu-id="05afc-231">有關詳細資訊,請參閱[XAML 中的空白處理](white-space-processing.md)。</span><span class="sxs-lookup"><span data-stu-id="05afc-231">For more information, see [White-space processing in XAML](white-space-processing.md).</span></span>

### <a name="xamldeferloadattribute"></a><span data-ttu-id="05afc-232">XamlDeferLoad 屬性</span><span class="sxs-lookup"><span data-stu-id="05afc-232">XamlDeferLoadAttribute</span></span>

<span data-ttu-id="05afc-233">**參考文件:**  <xref:System.Windows.Markup.XamlDeferLoadAttribute></span><span class="sxs-lookup"><span data-stu-id="05afc-233">**Reference Documentation:**  <xref:System.Windows.Markup.XamlDeferLoadAttribute></span></span>

<span data-ttu-id="05afc-234">**適用於:** 類,屬性。</span><span class="sxs-lookup"><span data-stu-id="05afc-234">**Applies to:** Class, property.</span></span>

<span data-ttu-id="05afc-235">**參數:** 支援兩個歸因表單型態為字串,或<xref:System.Type>類型為 。</span><span class="sxs-lookup"><span data-stu-id="05afc-235">**Arguments:** Supports two attribution forms types as strings, or types as <xref:System.Type>.</span></span> <span data-ttu-id="05afc-236">請參閱＜<xref:System.Windows.Markup.XamlDeferLoadAttribute>＞。</span><span class="sxs-lookup"><span data-stu-id="05afc-236">See <xref:System.Windows.Markup.XamlDeferLoadAttribute>.</span></span>

<span data-ttu-id="05afc-237">表示類別或屬性具有 XAML 的延後載入使用方式 (例如，範本行為)，並報告啟用延後行為的類別及其目的型別/內容型別。</span><span class="sxs-lookup"><span data-stu-id="05afc-237">Indicates that a class or property has a deferred load usage for XAML (such as a template behavior), and reports the class that enables the deferring behavior and its destination/content type.</span></span>

### <a name="xamlsetmarkupextensionattribute"></a><span data-ttu-id="05afc-238">XamlSetMarkup 擴充屬性</span><span class="sxs-lookup"><span data-stu-id="05afc-238">XamlSetMarkupExtensionAttribute</span></span>

<span data-ttu-id="05afc-239">**參考文件:**  <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute></span><span class="sxs-lookup"><span data-stu-id="05afc-239">**Reference Documentation:**  <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute></span></span>

<span data-ttu-id="05afc-240">**適用於:** 類別</span><span class="sxs-lookup"><span data-stu-id="05afc-240">**Applies to:** Class</span></span>

<span data-ttu-id="05afc-241">**參數:** 命名回調。</span><span class="sxs-lookup"><span data-stu-id="05afc-241">**Arguments:** Names the callback.</span></span>

<span data-ttu-id="05afc-242">指示類可以使用標記擴展為一個或多個屬性提供值,並引用 XAML 編寫器在對類的任何屬性執行標記擴展集操作之前應調用的處理程式。</span><span class="sxs-lookup"><span data-stu-id="05afc-242">Indicates that a class can use a markup extension to provide a value for one or more of its properties, and references a handler that a XAML writer should call before performing a markup extension set operation on any property of the class.</span></span>

### <a name="xamlsettypeconverterattribute"></a><span data-ttu-id="05afc-243">XamlSet 類型轉換器屬性</span><span class="sxs-lookup"><span data-stu-id="05afc-243">XamlSetTypeConverterAttribute</span></span>

<span data-ttu-id="05afc-244">**參考文件:**  <xref:System.Windows.Markup.XamlSetTypeConverterAttribute></span><span class="sxs-lookup"><span data-stu-id="05afc-244">**Reference Documentation:**  <xref:System.Windows.Markup.XamlSetTypeConverterAttribute></span></span>

<span data-ttu-id="05afc-245">**適用於:** 類別</span><span class="sxs-lookup"><span data-stu-id="05afc-245">**Applies to:** Class</span></span>

<span data-ttu-id="05afc-246">**參數:** 命名回調。</span><span class="sxs-lookup"><span data-stu-id="05afc-246">**Arguments:** Names the callback.</span></span>

<span data-ttu-id="05afc-247">指示類可以使用類型轉換器為其一個或多個屬性提供值,並引用 XAML 編寫器在對類的任何屬性執行類型轉換器集操作之前應調用的處理程式。</span><span class="sxs-lookup"><span data-stu-id="05afc-247">Indicates that a class can use a type converter to provide a value for one or more of its properties, and references a handler that a XAML writer should call before performing a type converter set operation on any property of the class.</span></span>

### <a name="xmllangpropertyattribute"></a><span data-ttu-id="05afc-248">XmlLang屬性</span><span class="sxs-lookup"><span data-stu-id="05afc-248">XmlLangPropertyAttribute</span></span>

<span data-ttu-id="05afc-249">**參考文件:**  <xref:System.Windows.Markup.XmlLangPropertyAttribute></span><span class="sxs-lookup"><span data-stu-id="05afc-249">**Reference Documentation:**  <xref:System.Windows.Markup.XmlLangPropertyAttribute></span></span>

<span data-ttu-id="05afc-250">**適用於:** 類別</span><span class="sxs-lookup"><span data-stu-id="05afc-250">**Applies to:** Class</span></span>

<span data-ttu-id="05afc-251">**參數:** 一個字串,用於在屬性類型上指定屬性的名稱`xml:lang`到別名。</span><span class="sxs-lookup"><span data-stu-id="05afc-251">**Arguments:** A string that specifies the name of the property to alias to `xml:lang` on the attributed type.</span></span>

<span data-ttu-id="05afc-252"><xref:System.Windows.Markup.XmlLangPropertyAttribute>報告對應到 XML`lang`指令屬性類型的屬性。</span><span class="sxs-lookup"><span data-stu-id="05afc-252"><xref:System.Windows.Markup.XmlLangPropertyAttribute> reports a property of the attributed type that maps to the XML `lang` directive.</span></span> <span data-ttu-id="05afc-253">屬性不一定是類型<xref:System.String>,但必須從字串中分配(可以通過將類型轉換器與屬性的類型或特定屬性相關聯來實現)。</span><span class="sxs-lookup"><span data-stu-id="05afc-253">The property is not necessarily of type <xref:System.String> but must be assignable from a string (assignment could be accomplished by associating a type converter with the property's type or with the specific property).</span></span> <span data-ttu-id="05afc-254">屬性必須讀/寫。</span><span class="sxs-lookup"><span data-stu-id="05afc-254">The property must be read/write.</span></span>

<span data-ttu-id="05afc-255">映射`xml:lang`方案是,執行時物件模型可以訪問 XML 指定的語言資訊,而無需專門使用 XMLDOM 進行處理。</span><span class="sxs-lookup"><span data-stu-id="05afc-255">The scenario for mapping `xml:lang` is so that a runtime object model has access to XML-specified language information without specifically processing with an XMLDOM.</span></span>

<span data-ttu-id="05afc-256">定義將繼承到可分配給定義類型的所有派生類型。</span><span class="sxs-lookup"><span data-stu-id="05afc-256">The definition inherits to all derived types that are assignable to the defining type.</span></span> <span data-ttu-id="05afc-257">可以通過應用<xref:System.Windows.Markup.XmlLangPropertyAttribute>於 特定派生類型來覆蓋特定派生類型上的定義,儘管這種情況並不常見。</span><span class="sxs-lookup"><span data-stu-id="05afc-257">You can override the definition on a specific derived type by applying <xref:System.Windows.Markup.XmlLangPropertyAttribute> on the specific derived type, although that is an uncommon scenario.</span></span>

## <a name="xaml-related-clr-attributes-at-the-assembly-level"></a><span data-ttu-id="05afc-258">裝配層級的 XAML 相關 CLR 屬性</span><span class="sxs-lookup"><span data-stu-id="05afc-258">XAML-Related CLR Attributes at the Assembly Level</span></span>

<span data-ttu-id="05afc-259">以下各節介紹不應用於類型或成員定義但應用於程式集的與 XAML 相關的屬性。</span><span class="sxs-lookup"><span data-stu-id="05afc-259">The following sections describe the XAML-related attributes that are not applied to types or member definitions, but are instead applied to assemblies.</span></span> <span data-ttu-id="05afc-260">這些屬性與定義包含要在 XAML 中使用的自定義類型的庫的總體目標相關。</span><span class="sxs-lookup"><span data-stu-id="05afc-260">These attributes are pertinent to the overall goal of defining a library that contains custom types to use in XAML.</span></span> <span data-ttu-id="05afc-261">某些屬性不一定直接影響 XAML 節點流,而是在節點流中傳遞,供其他消費者使用。</span><span class="sxs-lookup"><span data-stu-id="05afc-261">Some of the attributes do not necessarily influence the XAML node stream directly, but are passed on in the node stream for other consumers to use.</span></span> <span data-ttu-id="05afc-262">資訊的消費者包括需要 XAML 命名空間資訊和關聯的前置資訊的設計環境或序列化過程。</span><span class="sxs-lookup"><span data-stu-id="05afc-262">Consumers for the information include design environments or serialization processes that need XAML namespace information and associated prefix information.</span></span> <span data-ttu-id="05afc-263">XAML 架構上下文(包括 .NET XAML 服務預設值)也使用此資訊。</span><span class="sxs-lookup"><span data-stu-id="05afc-263">A XAML schema context (including the .NET XAML Services default) also uses this information.</span></span>

### <a name="xmlnscompatiblewithattribute"></a><span data-ttu-id="05afc-264">與屬性相容的 Xmlns</span><span class="sxs-lookup"><span data-stu-id="05afc-264">XmlnsCompatibleWithAttribute</span></span>

<span data-ttu-id="05afc-265">**參考文件:**  <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute></span><span class="sxs-lookup"><span data-stu-id="05afc-265">**Reference Documentation:**  <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute></span></span>

<span data-ttu-id="05afc-266">**引數:**</span><span class="sxs-lookup"><span data-stu-id="05afc-266">**Arguments:**</span></span>

- <span data-ttu-id="05afc-267">指定要歸納的 XAML 命名空間的識別碼的字串。</span><span class="sxs-lookup"><span data-stu-id="05afc-267">A string that specifies the identifier of the XAML namespace to subsume.</span></span>

- <span data-ttu-id="05afc-268">指定 XAML 命名空間的識別碼的字串,該名稱空間可以從上一個參數中歸入 XAML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="05afc-268">A string that specifies the identifier of the XAML namespace that can subsume the XAML namespace from the previous argument.</span></span>

  <span data-ttu-id="05afc-269"><xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>指定 XAML 命名空間可以由另一個 XAML 命名空間進行歸用。</span><span class="sxs-lookup"><span data-stu-id="05afc-269"><xref:System.Windows.Markup.XmlnsCompatibleWithAttribute> specifies that a XAML namespace can be subsumed by another XAML namespace.</span></span> <span data-ttu-id="05afc-270">一般會在預先定義的 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> 中指出建立小計的 XAML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="05afc-270">Typically, the subsuming XAML namespace is indicated in a previously defined <xref:System.Windows.Markup.XmlnsDefinitionAttribute>.</span></span> <span data-ttu-id="05afc-271">此技術可用於在庫中對 XAML 詞彙進行版本控制,並使之與以前定義的標記(針對早期版本化的詞彙表)相容。</span><span class="sxs-lookup"><span data-stu-id="05afc-271">This technique can be used for versioning a XAML vocabulary in a library and to make it compatible with previously defined markup against the earlier versioned vocabulary.</span></span>

### <a name="xmlnsdefinitionattribute"></a><span data-ttu-id="05afc-272">Xmlns 定義屬性</span><span class="sxs-lookup"><span data-stu-id="05afc-272">XmlnsDefinitionAttribute</span></span>

<span data-ttu-id="05afc-273">**參考文件:**  <xref:System.Windows.Markup.XmlnsDefinitionAttribute></span><span class="sxs-lookup"><span data-stu-id="05afc-273">**Reference Documentation:**  <xref:System.Windows.Markup.XmlnsDefinitionAttribute></span></span>

<span data-ttu-id="05afc-274">**引數:**</span><span class="sxs-lookup"><span data-stu-id="05afc-274">**Arguments:**</span></span>

- <span data-ttu-id="05afc-275">指定要定義的 XAML 命名空間的識別碼的字串。</span><span class="sxs-lookup"><span data-stu-id="05afc-275">A string that specifies the identifier of the XAML namespace to define.</span></span>

- <span data-ttu-id="05afc-276">命名 CLR 命名空間的字串。</span><span class="sxs-lookup"><span data-stu-id="05afc-276">A string that names a CLR namespace.</span></span> <span data-ttu-id="05afc-277">CLR 命名空間應在程式集中定義公共類型,並且至少應使用一種 CLR 命名空間類型來使用 XAML。</span><span class="sxs-lookup"><span data-stu-id="05afc-277">The CLR namespace should define public types in your assembly, and at least one of the CLR namespace types should be intended for XAML usage.</span></span>

  <span data-ttu-id="05afc-278"><xref:System.Windows.Markup.XmlnsDefinitionAttribute>指定 XAML 命名空間和 CLR 命名空間之間的每個程式集映射,然後 XAML 物件編寫器或 XAML 架構上下文用於類型解析。</span><span class="sxs-lookup"><span data-stu-id="05afc-278"><xref:System.Windows.Markup.XmlnsDefinitionAttribute> specifies a mapping on a per-assembly basis between a XAML namespace and a CLR namespace, which is then used for type resolution by a XAML object writer or XAML schema context.</span></span>

  <span data-ttu-id="05afc-279">可以有多個<xref:System.Windows.Markup.XmlnsDefinitionAttribute>元件。</span><span class="sxs-lookup"><span data-stu-id="05afc-279">More than one <xref:System.Windows.Markup.XmlnsDefinitionAttribute> can be applied to an assembly.</span></span> <span data-ttu-id="05afc-280">這可能是出於以下任何原因的組合:</span><span class="sxs-lookup"><span data-stu-id="05afc-280">This might be done for any combination of the following reasons:</span></span>

- <span data-ttu-id="05afc-281">庫設計包含多個 CLR 命名空間,用於運行時 API 訪問的邏輯組織;但是,您希望這些命名空間中的所有類型都可用於 XAML,透過引用相同的 XAML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="05afc-281">The library design contains multiple CLR namespaces for logical organization of run-time API access; however, you want all types in those namespaces to be XAML-usable by referencing the same XAML namespace.</span></span> <span data-ttu-id="05afc-282">在這種情況下,使用相同的<xref:System.Windows.Markup.XmlnsDefinitionAttribute><xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A>值但不同的<xref:System.Windows.Markup.XmlnsDefinitionAttribute.ClrNamespace%2A>值應用多個屬性。</span><span class="sxs-lookup"><span data-stu-id="05afc-282">In this case, you apply several <xref:System.Windows.Markup.XmlnsDefinitionAttribute> attributes using the same <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> value but different <xref:System.Windows.Markup.XmlnsDefinitionAttribute.ClrNamespace%2A> values.</span></span> <span data-ttu-id="05afc-283">如果要定義框架或應用程式打算成為常用的預設 XAML 命名空間的 XAML 命名空間的映射,則此功能尤其有用。</span><span class="sxs-lookup"><span data-stu-id="05afc-283">This is especially useful if you are defining mappings for the XAML namespace that your framework or application intends to be the default XAML namespace in common usage.</span></span>

- <span data-ttu-id="05afc-284">庫設計包含多個 CLR 命名空間,您希望在這些 CLR 命名空間中類型的用法之間進行深思熟慮的 XAML 命名空間分離。</span><span class="sxs-lookup"><span data-stu-id="05afc-284">The library design contains multiple CLR namespaces, and you want a deliberate XAML namespace separation between the usages of types in those CLR namespaces.</span></span>

- <span data-ttu-id="05afc-285">在程式集中定義 CLR 命名空間,並希望它可以通過多個 XAML 命名空間進行訪問。</span><span class="sxs-lookup"><span data-stu-id="05afc-285">You define a CLR namespace in the assembly, and you want it to be accessible through more than one XAML namespace.</span></span> <span data-ttu-id="05afc-286">當您支援具有相同代碼庫的多個詞彙庫時,將發生此情況。</span><span class="sxs-lookup"><span data-stu-id="05afc-286">This scenario occurs when you are supporting multiple vocabularies with the same codebase.</span></span>

- <span data-ttu-id="05afc-287">在一個或多個 CLR 命名空間中定義 XAML 語言支援。</span><span class="sxs-lookup"><span data-stu-id="05afc-287">You define XAML language support in one or more CLR namespaces.</span></span> <span data-ttu-id="05afc-288">在這種情況下,<xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A>值應`http://schemas.microsoft.com/winfx/2006/xaml`為 。</span><span class="sxs-lookup"><span data-stu-id="05afc-288">In this case, the <xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A> value should be `http://schemas.microsoft.com/winfx/2006/xaml`.</span></span>

### <a name="xmlnsprefixattribute"></a><span data-ttu-id="05afc-289">Xmlns前置字串屬性</span><span class="sxs-lookup"><span data-stu-id="05afc-289">XmlnsPrefixAttribute</span></span>

<span data-ttu-id="05afc-290">**參考文件:**  <xref:System.Windows.Markup.XmlnsPrefixAttribute></span><span class="sxs-lookup"><span data-stu-id="05afc-290">**Reference Documentation:**  <xref:System.Windows.Markup.XmlnsPrefixAttribute></span></span>

<span data-ttu-id="05afc-291">**引數:**</span><span class="sxs-lookup"><span data-stu-id="05afc-291">**Arguments:**</span></span>

- <span data-ttu-id="05afc-292">指定 XAML 命名空間識別碼的字串。</span><span class="sxs-lookup"><span data-stu-id="05afc-292">A string that specifies the identifier of a XAML namespace.</span></span>

- <span data-ttu-id="05afc-293">指定建議前置字串。</span><span class="sxs-lookup"><span data-stu-id="05afc-293">A string that specifies a recommended prefix.</span></span>

  <span data-ttu-id="05afc-294"><xref:System.Windows.Markup.XmlnsDefinitionAttribute>指定用於 XAML 命名空間的建議前置碼。</span><span class="sxs-lookup"><span data-stu-id="05afc-294"><xref:System.Windows.Markup.XmlnsDefinitionAttribute> specifies a recommended prefix to use for a XAML namespace.</span></span> <span data-ttu-id="05afc-295">在由 .NET XAML 服務<xref:System.Xaml.XamlXmlWriter>序列化的 XAML 檔中編寫元素和屬性時,或者當 XAML 實現庫與具有 XAML 編輯功能的設計環境互動時,前置碼非常有用。</span><span class="sxs-lookup"><span data-stu-id="05afc-295">The prefix is useful when writing elements and attributes in a XAML file that is serialized by .NET XAML Services <xref:System.Xaml.XamlXmlWriter>, or when a XAML-implementing library interacts with a design environment that has XAML editing features.</span></span>

  <span data-ttu-id="05afc-296">可以有多個<xref:System.Windows.Markup.XmlnsPrefixAttribute>元件。</span><span class="sxs-lookup"><span data-stu-id="05afc-296">More than one <xref:System.Windows.Markup.XmlnsPrefixAttribute> can be applied to an assembly.</span></span> <span data-ttu-id="05afc-297">這可能是出於以下任何原因的組合:</span><span class="sxs-lookup"><span data-stu-id="05afc-297">This might be done for any combination of the following reasons:</span></span>

- <span data-ttu-id="05afc-298">程式集定義多個 XAML 命名空間的類型。</span><span class="sxs-lookup"><span data-stu-id="05afc-298">Your assembly defines types for more than one XAML namespace.</span></span> <span data-ttu-id="05afc-299">在這種情況下,為每個 XAML 命名空間定義不同的前置值。</span><span class="sxs-lookup"><span data-stu-id="05afc-299">In this case, define different prefix values for each XAML namespace.</span></span>

- <span data-ttu-id="05afc-300">您支援多個詞彙,並且對每個詞彙表和 XAML 命名空間使用不同的前置碼。</span><span class="sxs-lookup"><span data-stu-id="05afc-300">You are supporting multiple vocabularies, and you use different prefixes for each vocabulary and XAML namespace.</span></span>

- <span data-ttu-id="05afc-301">在程式集中定義 XAML 語言支援,<xref:System.Windows.Markup.XmlnsDefinitionAttribute>`http://schemas.microsoft.com/winfx/2006/xaml`並為</span><span class="sxs-lookup"><span data-stu-id="05afc-301">You define XAML language support in the assembly and have a <xref:System.Windows.Markup.XmlnsDefinitionAttribute> for `http://schemas.microsoft.com/winfx/2006/xaml`.</span></span> <span data-ttu-id="05afc-302">在這種情況下,通常應升級前置字`x`串 。</span><span class="sxs-lookup"><span data-stu-id="05afc-302">In this case, you typically should promote the prefix `x`.</span></span>

> [!NOTE]
> <span data-ttu-id="05afc-303">.NET XAML 服務還定義了與<xref:System.Windows.Markup.RootNamespaceAttribute>XAML 相關的屬性 。</span><span class="sxs-lookup"><span data-stu-id="05afc-303">.NET XAML Services also defines the XAML-related attribute <xref:System.Windows.Markup.RootNamespaceAttribute>.</span></span> <span data-ttu-id="05afc-304">此屬性是專案系統支援的程式集級屬性,與 XAML 自定義類型無關。</span><span class="sxs-lookup"><span data-stu-id="05afc-304">This attribute is an assembly-level attribute for project system support, and it is not relevant for XAML custom types.</span></span>

## <a name="see-also"></a><span data-ttu-id="05afc-305">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05afc-305">See also</span></span>

- <xref:System.Attribute>
- [<span data-ttu-id="05afc-306">定義可搭配 .NET XAML 服務使用的自訂類型</span><span class="sxs-lookup"><span data-stu-id="05afc-306">Defining Custom Types for Use with .NET XAML Services</span></span>](define-custom-types.md)
