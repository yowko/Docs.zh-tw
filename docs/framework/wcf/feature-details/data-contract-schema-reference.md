---
title: 資料合約結構描述參考
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts [WCF], schema reference
ms.assetid: 9ebb0ebe-8166-4c93-980a-7c8f1f38f7c0
ms.openlocfilehash: 33661061e1a5db4f7826c1a8eca188f8c782b58f
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/08/2018
ms.locfileid: "48873715"
---
# <a name="data-contract-schema-reference"></a><span data-ttu-id="b3ad1-102">資料合約結構描述參考</span><span class="sxs-lookup"><span data-stu-id="b3ad1-102">Data Contract Schema Reference</span></span>
<span data-ttu-id="b3ad1-103">本主題說明 <xref:System.Runtime.Serialization.DataContractSerializer> 用來描述 XML 序列化之 Common Language Runtime (CLR) 型別的 XML 結構描述 (XSD) 子集。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-103">This topic describes the subset of the XML Schema (XSD) used by <xref:System.Runtime.Serialization.DataContractSerializer> to describe common language runtime (CLR) types for XML serialization.</span></span>  
  
## <a name="datacontractserializer-mappings"></a><span data-ttu-id="b3ad1-104">DataContractSerializer 對應</span><span class="sxs-lookup"><span data-stu-id="b3ad1-104">DataContractSerializer Mappings</span></span>  
 <span data-ttu-id="b3ad1-105">`DataContractSerializer`從 Windows Communication Foundation (WCF) 服務使用中繼資料端點匯出中繼資料時，將 CLR 型別對應至 XSD 或[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-105">The `DataContractSerializer` maps CLR types to XSD when metadata is exported from a Windows Communication Foundation (WCF) service using a metadata endpoint or the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="b3ad1-106">如需詳細資訊，請參閱 <<c0> [ 資料合約序列化程式](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md)。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-106">For more information, see [Data Contract Serializer](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md).</span></span>  
  
 <span data-ttu-id="b3ad1-107">當您使用 Svcutil.exe 來存取 Web 服務描述語言 (WSDL) 或 XSD 文件並產生服務或用戶端的資料合約時， `DataContractSerializer` 也會將 XSD 對應至 CLR 型別。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-107">The `DataContractSerializer` also maps XSD to CLR types when Svcutil.exe is used to access Web Services Description Language (WSDL) or XSD documents and generate data contracts for services or clients.</span></span>  
  
 <span data-ttu-id="b3ad1-108">只有符合本文件所述之需求的 XML 結構描述執行個體可以使用 `DataContractSerializer`對應至 CLR 型別。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-108">Only XML Schema instances that conform to requirements stated in this document can be mapped to CLR types using `DataContractSerializer`.</span></span>  
  
### <a name="support-levels"></a><span data-ttu-id="b3ad1-109">支援層級</span><span class="sxs-lookup"><span data-stu-id="b3ad1-109">Support Levels</span></span>  
 <span data-ttu-id="b3ad1-110">`DataContractSerializer` 針對特定 XML 結構描述功能提供下列支援層級：</span><span class="sxs-lookup"><span data-stu-id="b3ad1-110">The `DataContractSerializer` provides the following levels of support for a given XML Schema feature:</span></span>  
  
-   <span data-ttu-id="b3ad1-111">**支援**：</span><span class="sxs-lookup"><span data-stu-id="b3ad1-111">**Supported**.</span></span> <span data-ttu-id="b3ad1-112">使用 `DataContractSerializer`從這項功能明確對應至 CLR 型別或屬性 (或兩者)。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-112">There is explicit mapping from this feature to CLR types or attributes (or both) using `DataContractSerializer`.</span></span>  
  
-   <span data-ttu-id="b3ad1-113">**忽略**：</span><span class="sxs-lookup"><span data-stu-id="b3ad1-113">**Ignored**.</span></span> <span data-ttu-id="b3ad1-114">此功能可用在 `DataContractSerializer`所匯入的結構描述中，但是不會對產生程式碼有任何影響。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-114">The feature is allowed in schemas imported by the `DataContractSerializer`, but has no effect on code generation.</span></span>  
  
-   <span data-ttu-id="b3ad1-115">**禁止**：</span><span class="sxs-lookup"><span data-stu-id="b3ad1-115">**Forbidden**.</span></span> <span data-ttu-id="b3ad1-116">`DataContractSerializer` 不支援使用此功能來支援匯入結構描述。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-116">The `DataContractSerializer` does not support importing a schema using the feature.</span></span> <span data-ttu-id="b3ad1-117">例如，當使用結構描述 (運用此類功能) 來存取 WSDL 時，Svcutil.exe 就會改回使用 <xref:System.Xml.Serialization.XmlSerializer> 。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-117">For example, Svcutil.exe, when accessing a WSDL with a schema that uses such a feature, falls back to using the <xref:System.Xml.Serialization.XmlSerializer> instead.</span></span> <span data-ttu-id="b3ad1-118">這是預設的結果。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-118">This is by default.</span></span>  
  
## <a name="general-information"></a><span data-ttu-id="b3ad1-119">一般資訊</span><span class="sxs-lookup"><span data-stu-id="b3ad1-119">General Information</span></span>  
  
-   <span data-ttu-id="b3ad1-120">[XML 結構描述](https://go.microsoft.com/fwlink/?LinkId=95475)(英文) 將說明結構描述命名空間。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-120">The schema namespace is described at [XML Schema](https://go.microsoft.com/fwlink/?LinkId=95475).</span></span> <span data-ttu-id="b3ad1-121">本文使用 "xs" 前置詞。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-121">The prefix "xs" is used in this document.</span></span>  
  
-   <span data-ttu-id="b3ad1-122">任何包含非結構描述命名空間的屬性都會被忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-122">Any attributes with a non-schema namespace are ignored.</span></span>  
  
-   <span data-ttu-id="b3ad1-123">任何附註 (除了本文中所述的以外) 都會被忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-123">Any annotations (except for those described in this document) are ignored.</span></span>  
  
### <a name="xsschema-attributes"></a><span data-ttu-id="b3ad1-124">\<schema> >： 屬性</span><span class="sxs-lookup"><span data-stu-id="b3ad1-124">\<xs:schema>: attributes</span></span>  
  
|<span data-ttu-id="b3ad1-125">屬性</span><span class="sxs-lookup"><span data-stu-id="b3ad1-125">Attribute</span></span>|<span data-ttu-id="b3ad1-126">DataContract</span><span class="sxs-lookup"><span data-stu-id="b3ad1-126">DataContract</span></span>|  
|---------------|------------------|  
|`attributeFormDefault`|<span data-ttu-id="b3ad1-127">忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-127">Ignored.</span></span>|  
|`blockDefault`|<span data-ttu-id="b3ad1-128">忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-128">Ignored.</span></span>|  
|`elementFormDefault`|<span data-ttu-id="b3ad1-129">必須限定。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-129">Must be qualified.</span></span> <span data-ttu-id="b3ad1-130">所有項目必須限定，以便由 `DataContractSerializer`支援結構描述。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-130">All elements must be qualified for a schema to be supported by `DataContractSerializer`.</span></span> <span data-ttu-id="b3ad1-131">這可藉由設定任一xs:schema/@elementFormDefault為"qualified"或藉由設定xs:element/@form為"qualified"上每個個別的項目宣告。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-131">This can be accomplished by either setting xs:schema/@elementFormDefault to "qualified" or by setting xs:element/@form to "qualified" on each individual element declaration.</span></span>|  
|`finalDefault`|<span data-ttu-id="b3ad1-132">忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-132">Ignored.</span></span>|  
|`Id`|<span data-ttu-id="b3ad1-133">忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-133">Ignored.</span></span>|  
|`targetNamespace`|<span data-ttu-id="b3ad1-134">支援且對應至資料合約命名空間。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-134">Supported and mapped to the data contract namespace.</span></span> <span data-ttu-id="b3ad1-135">如果沒有指定此屬性，便會使用空白的命名空間。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-135">If this attribute is not specified, the blank namespace is used.</span></span> <span data-ttu-id="b3ad1-136">不能保留的命名空間 `http://schemas.microsoft.com/2003/10/Serialization/` 。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-136">Cannot be the reserved namespace `http://schemas.microsoft.com/2003/10/Serialization/`.</span></span>|  
|`version`|<span data-ttu-id="b3ad1-137">忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-137">Ignored.</span></span>|  
  
### <a name="xsschema-contents"></a><span data-ttu-id="b3ad1-138">\<schema> >： 內容</span><span class="sxs-lookup"><span data-stu-id="b3ad1-138">\<xs:schema>: contents</span></span>  
  
|<span data-ttu-id="b3ad1-139">內容</span><span class="sxs-lookup"><span data-stu-id="b3ad1-139">Contents</span></span>|<span data-ttu-id="b3ad1-140">結構描述</span><span class="sxs-lookup"><span data-stu-id="b3ad1-140">Schema</span></span>|  
|--------------|------------|  
|`include`|<span data-ttu-id="b3ad1-141">支援。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-141">Supported.</span></span> <span data-ttu-id="b3ad1-142">`DataContractSerializer` 支援 xs:include 和 xs:import。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-142">`DataContractSerializer` supports xs:include and xs:import.</span></span> <span data-ttu-id="b3ad1-143">但是，當您從本機檔案載入中繼資料時，Svcutil.exe 會限制下列 `xs:include/@schemaLocation` 和 `xs:import/@location` 參考。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-143">However, Svcutil.exe restricts following `xs:include/@schemaLocation` and `xs:import/@location` references when metadata is loaded from a local file.</span></span> <span data-ttu-id="b3ad1-144">在此情況下，結構描述檔案清單必須透過超出範圍之外的機制，而不是 `include` 來傳遞； `include`的結構描述文件會被忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-144">The list of schema files must be passed through an out-of-band mechanism and not through `include` in this case; `include`d schema documents are ignored.</span></span>|  
|`redefine`|<span data-ttu-id="b3ad1-145">禁止。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-145">Forbidden.</span></span> <span data-ttu-id="b3ad1-146">基於安全性的理由，禁止透過 `xs:redefine` 使用 `DataContractSerializer` ： `x:redefine` 要求必須遵循 `schemaLocation` 。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-146">The use of `xs:redefine` is forbidden by `DataContractSerializer` for security reasons: `x:redefine` requires `schemaLocation` to be followed.</span></span> <span data-ttu-id="b3ad1-147">在特定情況下，使用 DataContract 的 Svcutil.exe 會限制使用 `schemaLocation`。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-147">In certain circumstances, Svcutil.exe using DataContract restricts use of `schemaLocation`.</span></span>|  
|`import`|<span data-ttu-id="b3ad1-148">支援。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-148">Supported.</span></span> <span data-ttu-id="b3ad1-149">`DataContractSerializer` 支援 `xs:include` 和 `xs:import`。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-149">`DataContractSerializer` supports `xs:include` and `xs:import`.</span></span> <span data-ttu-id="b3ad1-150">但是，當您從本機檔案載入中繼資料時，Svcutil.exe 會限制下列 `xs:include/@schemaLocation` 和 `xs:import/@location` 參考。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-150">However, Svcutil.exe restricts following `xs:include/@schemaLocation` and `xs:import/@location` references when metadata is loaded from a local file.</span></span> <span data-ttu-id="b3ad1-151">在此情況下，結構描述檔案清單必須透過超出範圍之外的機制，而不是 `include` 來傳遞； `include` 的結構描述文件會被忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-151">The list of schema files must be passed through an out-of-band mechanism and not through `include` in this case; `include`d schema documents are ignored.</span></span>|  
|`simpleType`|<span data-ttu-id="b3ad1-152">支援。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-152">Supported.</span></span> <span data-ttu-id="b3ad1-153">請參閱 `xs:simpleType` 一節。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-153">See the `xs:simpleType` section.</span></span>|  
|`complexType`|<span data-ttu-id="b3ad1-154">支援，且對應至資料合約。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-154">Supported, maps to data contracts.</span></span> <span data-ttu-id="b3ad1-155">請參閱 `xs:complexType` 一節。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-155">See the `xs:complexType` section.</span></span>|  
|`group`|<span data-ttu-id="b3ad1-156">忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-156">Ignored.</span></span> <span data-ttu-id="b3ad1-157">`DataContractSerializer` 不支援使用 `xs:group`、 `xs:attributeGroup`和 `xs:attribute`。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-157">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="b3ad1-158">已忽略這些宣告並將其視為 `xs:schema` 的子項，但是無法從 `complexType` 或其他支援的建構內部參考這些宣告。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-158">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|  
|`attributeGroup`|<span data-ttu-id="b3ad1-159">忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-159">Ignored.</span></span> <span data-ttu-id="b3ad1-160">`DataContractSerializer` 不支援使用 `xs:group`、 `xs:attributeGroup`和 `xs:attribute`。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-160">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="b3ad1-161">已忽略這些宣告並將其視為 `xs:schema`的子項，但是無法從 `complexType` 或其他支援的建構內部參考這些宣告。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-161">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|  
|`element`|<span data-ttu-id="b3ad1-162">支援。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-162">Supported.</span></span> <span data-ttu-id="b3ad1-163">請參閱全域項目宣告 (GED)。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-163">See Global Element Declaration (GED).</span></span>|  
|`attribute`|<span data-ttu-id="b3ad1-164">忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-164">Ignored.</span></span> <span data-ttu-id="b3ad1-165">`DataContractSerializer` 不支援使用 `xs:group`、 `xs:attributeGroup`和 `xs:attribute`。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-165">`DataContractSerializer` does not support use of `xs:group`, `xs:attributeGroup`, and `xs:attribute`.</span></span> <span data-ttu-id="b3ad1-166">已忽略這些宣告並將其視為 `xs:schema` 的子項，但是無法從 `complexType` 或其他支援的建構內部參考這些宣告。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-166">These declarations are ignored as children of `xs:schema`, but cannot be referenced from within `complexType` or other supported constructs.</span></span>|  
|`notation`|<span data-ttu-id="b3ad1-167">忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-167">Ignored.</span></span>|  
  
## <a name="complex-types--xscomplextype"></a><span data-ttu-id="b3ad1-168">複雜型別 – \<complextype> ></span><span class="sxs-lookup"><span data-stu-id="b3ad1-168">Complex Types – \<xs:complexType></span></span>  
  
### <a name="general-information"></a><span data-ttu-id="b3ad1-169">一般資訊</span><span class="sxs-lookup"><span data-stu-id="b3ad1-169">General Information</span></span>  
 <span data-ttu-id="b3ad1-170">每個複雜型別\<complextype> > 對應至資料合約。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-170">Each complex type \<xs:complexType> maps to a data contract.</span></span>  
  
### <a name="xscomplextype-attributes"></a><span data-ttu-id="b3ad1-171">\<complextype> >： 屬性</span><span class="sxs-lookup"><span data-stu-id="b3ad1-171">\<xs:complexType>: attributes</span></span>  
  
|<span data-ttu-id="b3ad1-172">屬性</span><span class="sxs-lookup"><span data-stu-id="b3ad1-172">Attribute</span></span>|<span data-ttu-id="b3ad1-173">結構描述</span><span class="sxs-lookup"><span data-stu-id="b3ad1-173">Schema</span></span>|  
|---------------|------------|  
|`abstract`|<span data-ttu-id="b3ad1-174">必須為 false (預設)。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-174">Must be false (default).</span></span>|  
|`block`|<span data-ttu-id="b3ad1-175">禁止。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-175">Forbidden.</span></span>|  
|`final`|<span data-ttu-id="b3ad1-176">忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-176">Ignored.</span></span>|  
|`id`|<span data-ttu-id="b3ad1-177">忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-177">Ignored.</span></span>|  
|`mixed`|<span data-ttu-id="b3ad1-178">必須為 false (預設)。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-178">Must be false (default).</span></span>|  
|`name`|<span data-ttu-id="b3ad1-179">支援且對應至資料合約名稱。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-179">Supported and mapped to the data contract name.</span></span> <span data-ttu-id="b3ad1-180">如果名稱之間包含句點，就會嘗試將型別對應至內部型別。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-180">If there are periods in the name, an attempt is made to map the type to an inner type.</span></span> <span data-ttu-id="b3ad1-181">例如，名為 `A.B` 的複雜型別會對應至資料合約型別 (即包含資料合約名稱 `A`的內部型別)，但前提是必須存在此類資料合約型別。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-181">For example, a complex type named `A.B` maps to a data contract type that is an inner type of a type with the data contract name `A`, but only if such a data contract type exists.</span></span> <span data-ttu-id="b3ad1-182">有可能存在一個以上的巢狀層級：例如， `A.B.C` 可以是內部型別，但前提是 `A` 和 `A.B` 必須同時存在。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-182">More than one level of nesting is possible: for example, `A.B.C` can be an inner type, but only if `A` and `A.B` both exist.</span></span>|  
  
### <a name="xscomplextype-contents"></a><span data-ttu-id="b3ad1-183">\<complextype> >： 內容</span><span class="sxs-lookup"><span data-stu-id="b3ad1-183">\<xs:complexType>: contents</span></span>  
  
|<span data-ttu-id="b3ad1-184">內容</span><span class="sxs-lookup"><span data-stu-id="b3ad1-184">Contents</span></span>|<span data-ttu-id="b3ad1-185">結構描述</span><span class="sxs-lookup"><span data-stu-id="b3ad1-185">Schema</span></span>|  
|--------------|------------|  
|`simpleContent`|<span data-ttu-id="b3ad1-186">禁止使用副檔名。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-186">Extensions are forbidden.</span></span><br /><br /> <span data-ttu-id="b3ad1-187">只允許來自 `anySimpleType`的限制。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-187">Restriction is allowed only from `anySimpleType`.</span></span>|  
|`complexContent`|<span data-ttu-id="b3ad1-188">支援。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-188">Supported.</span></span> <span data-ttu-id="b3ad1-189">請參閱「繼承」。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-189">See "Inheritance".</span></span>|  
|`group`|<span data-ttu-id="b3ad1-190">禁止。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-190">Forbidden.</span></span>|  
|`all`|<span data-ttu-id="b3ad1-191">禁止。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-191">Forbidden.</span></span>|  
|`choice`|<span data-ttu-id="b3ad1-192">禁止</span><span class="sxs-lookup"><span data-stu-id="b3ad1-192">Forbidden</span></span>|  
|`sequence`|<span data-ttu-id="b3ad1-193">支援，且對應至資料合約的資料成員。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-193">Supported, maps to data members of a data contract.</span></span>|  
|`attribute`|<span data-ttu-id="b3ad1-194">已禁止，即使 use="prohibited" (有一個例外狀況) 亦然。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-194">Forbidden, even if use="prohibited" (with one exception).</span></span> <span data-ttu-id="b3ad1-195">僅支援來自標準序列化結構描述命名空間的選用屬性。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-195">Only optional attributes from the Standard Serialization Schema namespace are supported.</span></span> <span data-ttu-id="b3ad1-196">它們無法對應至資料合約程式設計模型中的資料成員。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-196">They do not map to data members in the data contract programming model.</span></span> <span data-ttu-id="b3ad1-197">目前，只有此類屬性具有意義，而且會在「ISerializable」一節中討論。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-197">Currently, only one such attribute has meaning and is discussed in the ISerializable section.</span></span> <span data-ttu-id="b3ad1-198">其他所有項目都會被忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-198">All others are ignored.</span></span>|  
|`attributeGroup`|<span data-ttu-id="b3ad1-199">禁止。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-199">Forbidden.</span></span> <span data-ttu-id="b3ad1-200">在 WCF v1 版本中，`DataContractSerializer`會忽略出現與否`attributeGroup`內`xs:complexType`。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-200">In the WCF v1 release, `DataContractSerializer` ignores the presence of `attributeGroup` inside `xs:complexType`.</span></span>|  
|`anyAttribute`|<span data-ttu-id="b3ad1-201">禁止。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-201">Forbidden.</span></span>|  
|<span data-ttu-id="b3ad1-202">(空白)</span><span class="sxs-lookup"><span data-stu-id="b3ad1-202">(empty)</span></span>|<span data-ttu-id="b3ad1-203">對應至不包含資料成員的資料合約。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-203">Maps to a data contract with no data members.</span></span>|  
  
### <a name="xssequence-in-a-complex-type-attributes"></a><span data-ttu-id="b3ad1-204">\<sequence > 複雜類型中： 屬性</span><span class="sxs-lookup"><span data-stu-id="b3ad1-204">\<xs:sequence> in a complex type: attributes</span></span>  
  
|<span data-ttu-id="b3ad1-205">屬性</span><span class="sxs-lookup"><span data-stu-id="b3ad1-205">Attribute</span></span>|<span data-ttu-id="b3ad1-206">結構描述</span><span class="sxs-lookup"><span data-stu-id="b3ad1-206">Schema</span></span>|  
|---------------|------------|  
|`id`|<span data-ttu-id="b3ad1-207">忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-207">Ignored.</span></span>|  
|`maxOccurs`|<span data-ttu-id="b3ad1-208">必須為 1 (預設)。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-208">Must be 1 (default).</span></span>|  
|`minOccurs`|<span data-ttu-id="b3ad1-209">必須為 1 (預設)。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-209">Must be 1 (default).</span></span>|  
  
### <a name="xssequence-in-a-complex-type-contents"></a><span data-ttu-id="b3ad1-210">\<sequence > 複雜類型中： 內容</span><span class="sxs-lookup"><span data-stu-id="b3ad1-210">\<xs:sequence> in a complex type: contents</span></span>  
  
|<span data-ttu-id="b3ad1-211">內容</span><span class="sxs-lookup"><span data-stu-id="b3ad1-211">Contents</span></span>|<span data-ttu-id="b3ad1-212">結構描述</span><span class="sxs-lookup"><span data-stu-id="b3ad1-212">Schema</span></span>|  
|--------------|------------|  
|`element`|<span data-ttu-id="b3ad1-213">每個執行個體都會對應至資料成員。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-213">Each instance maps to a data member.</span></span>|  
|`group`|<span data-ttu-id="b3ad1-214">禁止。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-214">Forbidden.</span></span>|  
|`choice`|<span data-ttu-id="b3ad1-215">禁止。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-215">Forbidden.</span></span>|  
|`sequence`|<span data-ttu-id="b3ad1-216">禁止。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-216">Forbidden.</span></span>|  
|`any`|<span data-ttu-id="b3ad1-217">禁止。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-217">Forbidden.</span></span>|  
|<span data-ttu-id="b3ad1-218">(空白)</span><span class="sxs-lookup"><span data-stu-id="b3ad1-218">(empty)</span></span>|<span data-ttu-id="b3ad1-219">對應至不包含資料成員的資料合約。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-219">Maps to a data contract with no data members.</span></span>|  
  
## <a name="elements--xselement"></a><span data-ttu-id="b3ad1-220">項目 – \<xs: element ></span><span class="sxs-lookup"><span data-stu-id="b3ad1-220">Elements – \<xs:element></span></span>  
  
### <a name="general-information"></a><span data-ttu-id="b3ad1-221">一般資訊</span><span class="sxs-lookup"><span data-stu-id="b3ad1-221">General Information</span></span>  
 <span data-ttu-id="b3ad1-222">`<xs:element>` 可能在下列情況發生：</span><span class="sxs-lookup"><span data-stu-id="b3ad1-222">`<xs:element>` can occur in the following contexts:</span></span>  
  
-   <span data-ttu-id="b3ad1-223">它會發生在用來描述一般 (非集合) 資料合約之資料成員的 `<xs:sequence>`中。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-223">It can occur within an `<xs:sequence>`, which describes a data member of a regular (non-collection) data contract.</span></span> <span data-ttu-id="b3ad1-224">在此情況下， `maxOccurs` 屬性必須為 1</span><span class="sxs-lookup"><span data-stu-id="b3ad1-224">In this case, the `maxOccurs` attribute must be 1.</span></span> <span data-ttu-id="b3ad1-225">(不允許 0 這個值)。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-225">(A value of 0 is not allowed).</span></span>  
  
-   <span data-ttu-id="b3ad1-226">它會發生在用來描述集合資料合約之資料成員的 `<xs:sequence>`中。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-226">It can occur within an `<xs:sequence>`, which describes a data member of a collection data contract.</span></span> <span data-ttu-id="b3ad1-227">在此情況下， `maxOccurs` 屬性必須為大於 1 或 "unbounded"。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-227">In this case, the `maxOccurs` attribute must be greater than 1 or "unbounded".</span></span>  
  
-   <span data-ttu-id="b3ad1-228">它會發生在 `<xs:schema>` 中，做為全域項目宣告 (GED)。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-228">It can occur within an `<xs:schema>` as a Global Element Declaration (GED).</span></span>  
  
### <a name="xselement-with-maxoccurs1-within-an-xssequence-data-members"></a><span data-ttu-id="b3ad1-229">\<xs: element > maxOccurs = 1 內\<xs > （資料成員）</span><span class="sxs-lookup"><span data-stu-id="b3ad1-229">\<xs:element> with maxOccurs=1 within an \<xs:sequence> (Data Members)</span></span>  
  
|<span data-ttu-id="b3ad1-230">屬性</span><span class="sxs-lookup"><span data-stu-id="b3ad1-230">Attribute</span></span>|<span data-ttu-id="b3ad1-231">結構描述</span><span class="sxs-lookup"><span data-stu-id="b3ad1-231">Schema</span></span>|  
|---------------|------------|  
|`ref`|<span data-ttu-id="b3ad1-232">禁止。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-232">Forbidden.</span></span>|  
|`name`|<span data-ttu-id="b3ad1-233">支援，且對應至資料成員名稱。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-233">Supported, maps to the data member name.</span></span>|  
|`type`|<span data-ttu-id="b3ad1-234">支援，且對應至資料成員型別。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-234">Supported, maps to the data member type.</span></span> <span data-ttu-id="b3ad1-235">如需詳細資訊，請參閱「型別/基本對應」。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-235">For more information, see Type/primitive mapping.</span></span> <span data-ttu-id="b3ad1-236">如果未指定 (而且項目不包含匿名型別)，則會假定為 `xs:anyType` 。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-236">If not specified (and the element does not contain an anonymous type), `xs:anyType` is assumed.</span></span>|  
|`block`|<span data-ttu-id="b3ad1-237">忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-237">Ignored.</span></span>|  
|`default`|<span data-ttu-id="b3ad1-238">禁止。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-238">Forbidden.</span></span>|  
|`fixed`|<span data-ttu-id="b3ad1-239">禁止。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-239">Forbidden.</span></span>|  
|`form`|<span data-ttu-id="b3ad1-240">必須限定。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-240">Must be qualified.</span></span> <span data-ttu-id="b3ad1-241">此屬性可以透過 `elementFormDefault` 上的 `xs:schema`來設定。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-241">This attribute can be set through `elementFormDefault` on `xs:schema`.</span></span>|  
|`id`|<span data-ttu-id="b3ad1-242">忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-242">Ignored.</span></span>|  
|`maxOccurs`|<span data-ttu-id="b3ad1-243">1</span><span class="sxs-lookup"><span data-stu-id="b3ad1-243">1</span></span>|  
|`minOccurs`|<span data-ttu-id="b3ad1-244">對應至資料成員的 <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> 屬性 (當`IsRequired` 為 1 時， `minOccurs` 為 true)。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-244">Maps to the <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> property of a data member (`IsRequired` is true when `minOccurs` is 1).</span></span>|  
|`nillable`|<span data-ttu-id="b3ad1-245">影響型別對應。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-245">Affects type mapping.</span></span> <span data-ttu-id="b3ad1-246">請參閱「型別/基本對應」。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-246">See Type/primitive mapping.</span></span>|  
  
### <a name="xselement-with-maxoccurs1-within-an-xssequence-collections"></a><span data-ttu-id="b3ad1-247">\<xs: element > maxoccurs > 1 內\<xs > （集合）</span><span class="sxs-lookup"><span data-stu-id="b3ad1-247">\<xs:element> with maxOccurs>1 within an \<xs:sequence> (Collections)</span></span>  
  
-   <span data-ttu-id="b3ad1-248">對應至 <xref:System.Runtime.Serialization.CollectionDataContractAttribute>。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-248">Maps to a <xref:System.Runtime.Serialization.CollectionDataContractAttribute>.</span></span>  
  
-   <span data-ttu-id="b3ad1-249">在集合型別中，xs:sequence 只允許使用一個 xs:element。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-249">In collection types, only one xs:element is allowed within an xs:sequence.</span></span>  
  
 <span data-ttu-id="b3ad1-250">集合可以是下列任何型別：</span><span class="sxs-lookup"><span data-stu-id="b3ad1-250">Collections can be of the following types:</span></span>  
  
-   <span data-ttu-id="b3ad1-251">一般集合 (例如，陣列)。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-251">Regular collections (for example, arrays).</span></span>  
  
-   <span data-ttu-id="b3ad1-252">字典集合 (將某值對應至另一個值；例如， <xref:System.Collections.Hashtable>)。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-252">Dictionary collections (mapping one value to another; for example, a <xref:System.Collections.Hashtable>).</span></span>  
  
-   <span data-ttu-id="b3ad1-253">字典與金鑰/值組型別的陣列之間的唯一差異，就在於產生的程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-253">The only difference between a dictionary and an array of a key/value pair type is in the generated programming model.</span></span> <span data-ttu-id="b3ad1-254">您可採用一種結構描述附註機制，將特定型別指定為字典集合。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-254">There is a schema annotation mechanism that can be used to indicate that a given type is a dictionary collection.</span></span>  
  
 <span data-ttu-id="b3ad1-255">`ref`、 `block`、 `default`、 `fixed`、 `form`和 `id` 屬性的規則與非集合案例的規則是一樣的。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-255">The rules for the `ref`, `block`, `default`, `fixed`, `form`, and `id` attributes are the same as for the non-collection case.</span></span> <span data-ttu-id="b3ad1-256">下表包含其他各項屬性。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-256">Other attributes include those in the following table.</span></span>  
  
|<span data-ttu-id="b3ad1-257">屬性</span><span class="sxs-lookup"><span data-stu-id="b3ad1-257">Attribute</span></span>|<span data-ttu-id="b3ad1-258">結構描述</span><span class="sxs-lookup"><span data-stu-id="b3ad1-258">Schema</span></span>|  
|---------------|------------|  
|`name`|<span data-ttu-id="b3ad1-259">支援，且對應至 <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> 屬性 (Attribute) 中的 `CollectionDataContractAttribute` 屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-259">Supported, maps to the <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> property in the `CollectionDataContractAttribute` attribute.</span></span>|  
|`type`|<span data-ttu-id="b3ad1-260">支援，且對應至存放在集合中的型別。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-260">Supported, maps to the type stored in the collection.</span></span>|  
|`maxOccurs`|<span data-ttu-id="b3ad1-261">大於 1 或 "unbounded"。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-261">Greater than 1 or "unbounded".</span></span> <span data-ttu-id="b3ad1-262">DC 結構描述應該使用 "unbounded"。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-262">The DC schema should use "unbounded".</span></span>|  
|`minOccurs`|<span data-ttu-id="b3ad1-263">忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-263">Ignored.</span></span>|  
|`nillable`|<span data-ttu-id="b3ad1-264">影響型別對應。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-264">Affects type mapping.</span></span> <span data-ttu-id="b3ad1-265">字典集合會忽略此屬性。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-265">This attribute is ignored for dictionary collections.</span></span>|  
  
### <a name="xselement-within-an-xsschema-global-element-declaration"></a><span data-ttu-id="b3ad1-266">\<xs: element > 內\<schema> > 元素的全域宣告</span><span class="sxs-lookup"><span data-stu-id="b3ad1-266">\<xs:element> within an \<xs:schema> Global Element Declaration</span></span>  
  
-   <span data-ttu-id="b3ad1-267">與結構描述中的型別具有相同名稱與命名空間的全域項目宣告 (GED)，或是可在本身內部定義匿名型別的項目，稱為與型別關聯。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-267">A Global Element Declaration (GED) that has the same name and namespace as a type in schema, or that defines an anonymous type inside itself, is said to be associated with the type.</span></span>  
  
-   <span data-ttu-id="b3ad1-268">結構描述匯出：每個產生的型別，不管是簡單還是複雜型別，都會產生關聯的 GED。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-268">Schema export: associated GEDs are generated for every generated type, both simple and complex.</span></span>  
  
-   <span data-ttu-id="b3ad1-269">還原序列化/序列化：關聯的 GED 可做為型別的根項目來使用。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-269">Deserialization/serialization: associated GEDs are used as root elements for the type.</span></span>  
  
-   <span data-ttu-id="b3ad1-270">結構描述匯入：如果關聯的 GED 遵循下列規則 (除非它們定義了型別)，則這些 GED 為非必要而且會被忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-270">Schema import: associated GEDs are not required and are ignored if they follow the following rules (unless they define types).</span></span>  
  
|<span data-ttu-id="b3ad1-271">屬性</span><span class="sxs-lookup"><span data-stu-id="b3ad1-271">Attribute</span></span>|<span data-ttu-id="b3ad1-272">結構描述</span><span class="sxs-lookup"><span data-stu-id="b3ad1-272">Schema</span></span>|  
|---------------|------------|  
|`abstract`|<span data-ttu-id="b3ad1-273">關聯的 GED 必須是 false。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-273">Must be false for associated GEDs.</span></span>|  
|`block`|<span data-ttu-id="b3ad1-274">禁止在關聯的 GED 中使用。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-274">Forbidden in associated GEDs.</span></span>|  
|`default`|<span data-ttu-id="b3ad1-275">禁止在關聯的 GED 中使用。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-275">Forbidden in associated GEDs.</span></span>|  
|`final`|<span data-ttu-id="b3ad1-276">關聯的 GED 必須是 false。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-276">Must be false for associated GEDs.</span></span>|  
|`fixed`|<span data-ttu-id="b3ad1-277">禁止在關聯的 GED 中使用。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-277">Forbidden in associated GEDs.</span></span>|  
|`id`|<span data-ttu-id="b3ad1-278">忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-278">Ignored.</span></span>|  
|`name`|<span data-ttu-id="b3ad1-279">支援。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-279">Supported.</span></span> <span data-ttu-id="b3ad1-280">請參閱關聯的 GED 定義。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-280">See the definition of associated GEDs.</span></span>|  
|`nillable`|<span data-ttu-id="b3ad1-281">關聯的 GED 必須是 true。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-281">Must be true for associated GEDs.</span></span>|  
|`substitutionGroup`|<span data-ttu-id="b3ad1-282">禁止在關聯的 GED 中使用。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-282">Forbidden in associated GEDs.</span></span>|  
|`type`|<span data-ttu-id="b3ad1-283">支援，且必須符合關聯 GED 的關聯型別 (除非項目包含匿名型別)。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-283">Supported, and must match the associated type for associated GEDs (unless the element contains an anonymous type).</span></span>|  
  
### <a name="xselement-contents"></a><span data-ttu-id="b3ad1-284">\<xs: element >： 內容</span><span class="sxs-lookup"><span data-stu-id="b3ad1-284">\<xs:element>: contents</span></span>  
  
|<span data-ttu-id="b3ad1-285">內容</span><span class="sxs-lookup"><span data-stu-id="b3ad1-285">Contents</span></span>|<span data-ttu-id="b3ad1-286">結構描述</span><span class="sxs-lookup"><span data-stu-id="b3ad1-286">Schema</span></span>|  
|--------------|------------|  
|`simpleType`|<span data-ttu-id="b3ad1-287">支援。\*</span><span class="sxs-lookup"><span data-stu-id="b3ad1-287">Supported.\*</span></span>|  
|`complexType`|<span data-ttu-id="b3ad1-288">支援。\*</span><span class="sxs-lookup"><span data-stu-id="b3ad1-288">Supported.\*</span></span>|  
|`unique`|<span data-ttu-id="b3ad1-289">忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-289">Ignored.</span></span>|  
|`key`|<span data-ttu-id="b3ad1-290">忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-290">Ignored.</span></span>|  
|`keyref`|<span data-ttu-id="b3ad1-291">忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-291">Ignored.</span></span>|  
|<span data-ttu-id="b3ad1-292">(空白)</span><span class="sxs-lookup"><span data-stu-id="b3ad1-292">(blank)</span></span>|<span data-ttu-id="b3ad1-293">支援。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-293">Supported.</span></span>|  
  
 <span data-ttu-id="b3ad1-294">\* 使用時`simpleType`和`complexType,`匿名型別對應是與非匿名型別相同，只不過沒有任何的匿名資料合約，因此建立具名的資料合約時，產生的名稱衍生自項目名稱。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-294">\* When using the `simpleType` and `complexType,` mapping for anonymous types is the same as for non-anonymous types, except that there is no anonymous data contracts, and so a named data contract is created, with a generated name derived from the element name.</span></span> <span data-ttu-id="b3ad1-295">下表為匿名型別的規則：</span><span class="sxs-lookup"><span data-stu-id="b3ad1-295">The rules for anonymous types are in the following list:</span></span>  
  
-   <span data-ttu-id="b3ad1-296">WCF 實作詳細資料： 如果`xs:element`名稱不包含句號，則匿名型別會對應至外部資料合約型別的內部型別。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-296">WCF implementation detail: If the `xs:element` name does not contain periods, the anonymous type maps to an inner type of the outer data contract type.</span></span> <span data-ttu-id="b3ad1-297">如果名稱包含句點，則結果的資料合約型別是獨立的 (不是內部型別)。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-297">If the name contains periods, the resulting data contract type is independent (not an inner type).</span></span>  
  
-   <span data-ttu-id="b3ad1-298">產生之內部型別的資料合約名稱為外部型別的資料合約名稱，後面並跟著句點、項目名稱，以及字串 "Type"。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-298">The generated data contract name of the inner type is the data contract name of the outer type followed by a period, the name of the element, and the string "Type".</span></span>  
  
-   <span data-ttu-id="b3ad1-299">如果此名稱的資料合約已經存在，則名稱後面會加上 "1"、"2"、"3" 等，直到將其建立為唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-299">If a data contract with such a name already exists, the name is made unique by appending "1", "2", "3", and so on until a unique name is created.</span></span>  
  
## <a name="simple-types---xssimpletype"></a><span data-ttu-id="b3ad1-300">簡單型別- \<simpletype> ></span><span class="sxs-lookup"><span data-stu-id="b3ad1-300">Simple Types - \<xs:simpleType></span></span>  
  
### <a name="xssimpletype-attributes"></a><span data-ttu-id="b3ad1-301">\<simpletype> >： 屬性</span><span class="sxs-lookup"><span data-stu-id="b3ad1-301">\<xs:simpleType>: attributes</span></span>  
  
|<span data-ttu-id="b3ad1-302">屬性</span><span class="sxs-lookup"><span data-stu-id="b3ad1-302">Attribute</span></span>|<span data-ttu-id="b3ad1-303">結構描述</span><span class="sxs-lookup"><span data-stu-id="b3ad1-303">Schema</span></span>|  
|---------------|------------|  
|`final`|<span data-ttu-id="b3ad1-304">忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-304">Ignored.</span></span>|  
|`id`|<span data-ttu-id="b3ad1-305">忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-305">Ignored.</span></span>|  
|`name`|<span data-ttu-id="b3ad1-306">支援，且對應至資料合約名稱。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-306">Supported, maps to the data contract name.</span></span>|  
  
### <a name="xssimpletype-contents"></a><span data-ttu-id="b3ad1-307">\<simpletype> >： 內容</span><span class="sxs-lookup"><span data-stu-id="b3ad1-307">\<xs:simpleType>: contents</span></span>  
  
|<span data-ttu-id="b3ad1-308">內容</span><span class="sxs-lookup"><span data-stu-id="b3ad1-308">Contents</span></span>|<span data-ttu-id="b3ad1-309">結構描述</span><span class="sxs-lookup"><span data-stu-id="b3ad1-309">Schema</span></span>|  
|--------------|------------|  
|`restriction`|<span data-ttu-id="b3ad1-310">支援。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-310">Supported.</span></span> <span data-ttu-id="b3ad1-311">對應至列舉資料合約。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-311">Maps to enumeration data contracts.</span></span> <span data-ttu-id="b3ad1-312">如果此屬性與列舉模式不符，就會被忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-312">This attribute is ignored if it does not match the enumeration pattern.</span></span> <span data-ttu-id="b3ad1-313">請參閱「 `xs:simpleType` 限制」一節。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-313">See the `xs:simpleType` restrictions section.</span></span>|  
|`list`|<span data-ttu-id="b3ad1-314">支援。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-314">Supported.</span></span> <span data-ttu-id="b3ad1-315">對應至旗標列舉資料合約。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-315">Maps to flag enumeration data contracts.</span></span> <span data-ttu-id="b3ad1-316">請參閱「 `xs:simpleType` 清單」一節。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-316">See the `xs:simpleType` lists section.</span></span>|  
|`union`|<span data-ttu-id="b3ad1-317">禁止。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-317">Forbidden.</span></span>|  
  
### <a name="xsrestriction"></a><span data-ttu-id="b3ad1-318">\<xs:restriction></span><span class="sxs-lookup"><span data-stu-id="b3ad1-318">\<xs:restriction></span></span>  
  
-   <span data-ttu-id="b3ad1-319">base="`xs:anyType`" 僅支援複雜型別限制。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-319">Complex type restrictions are supported only for base="`xs:anyType`".</span></span>  
  
-   <span data-ttu-id="b3ad1-320">只包含 `xs:string` 限制 Facet 的 `xs:enumeration` 簡單型別限制會對應至列舉資料合約。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-320">Simple type restrictions of `xs:string` that do not have any restriction facets other than `xs:enumeration` are mapped to enumeration data contracts.</span></span>  
  
-   <span data-ttu-id="b3ad1-321">其他所有簡單型別限制則會對應至所限制的型別上。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-321">All other simple type restrictions are mapped to the types they restrict.</span></span> <span data-ttu-id="b3ad1-322">例如， `xs:int` 的限制會對應至整數，就像 `xs:int` 本身一樣。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-322">For example, a restriction of `xs:int` maps to an integer, just as `xs:int` itself does.</span></span> <span data-ttu-id="b3ad1-323">如需有關基本類型對應的詳細資訊，請參閱型別/基本對應。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-323">For more information about primitive type mapping, see Type/primitive mapping.</span></span>  
  
### <a name="xsrestriction-attributes"></a><span data-ttu-id="b3ad1-324">\<xs: restriction >： 屬性</span><span class="sxs-lookup"><span data-stu-id="b3ad1-324">\<xs:restriction>: attributes</span></span>  
  
|<span data-ttu-id="b3ad1-325">屬性</span><span class="sxs-lookup"><span data-stu-id="b3ad1-325">Attribute</span></span>|<span data-ttu-id="b3ad1-326">結構描述</span><span class="sxs-lookup"><span data-stu-id="b3ad1-326">Schema</span></span>|  
|---------------|------------|  
|`base`|<span data-ttu-id="b3ad1-327">必須是支援的簡單型別或 `xs:anyType`。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-327">Must be a supported simple type or `xs:anyType`.</span></span>|  
|`id`|<span data-ttu-id="b3ad1-328">忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-328">Ignored.</span></span>|  
  
### <a name="xsrestriction-for-all-other-cases-contents"></a><span data-ttu-id="b3ad1-329">\<xs: restriction > 所有其他案例： 內容</span><span class="sxs-lookup"><span data-stu-id="b3ad1-329">\<xs:restriction> for all other cases: contents</span></span>  
  
|<span data-ttu-id="b3ad1-330">內容</span><span class="sxs-lookup"><span data-stu-id="b3ad1-330">Contents</span></span>|<span data-ttu-id="b3ad1-331">結構描述</span><span class="sxs-lookup"><span data-stu-id="b3ad1-331">Schema</span></span>|  
|--------------|------------|  
|`simpleType`|<span data-ttu-id="b3ad1-332">如果存在，必須衍生自支援的基本類型。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-332">If present, must be derived from a supported primitive type.</span></span>|  
|`minExclusive`|<span data-ttu-id="b3ad1-333">忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-333">Ignored.</span></span>|  
|`minInclusive`|<span data-ttu-id="b3ad1-334">忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-334">Ignored.</span></span>|  
|`maxExclusive`|<span data-ttu-id="b3ad1-335">忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-335">Ignored.</span></span>|  
|`maxInclusive`|<span data-ttu-id="b3ad1-336">忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-336">Ignored.</span></span>|  
|`totalDigits`|<span data-ttu-id="b3ad1-337">忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-337">Ignored.</span></span>|  
|`fractionDigits`|<span data-ttu-id="b3ad1-338">忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-338">Ignored.</span></span>|  
|`length`|<span data-ttu-id="b3ad1-339">忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-339">Ignored.</span></span>|  
|`minLength`|<span data-ttu-id="b3ad1-340">忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-340">Ignored.</span></span>|  
|`maxLength`|<span data-ttu-id="b3ad1-341">忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-341">Ignored.</span></span>|  
|`enumeration`|<span data-ttu-id="b3ad1-342">忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-342">Ignored.</span></span>|  
|`whiteSpace`|<span data-ttu-id="b3ad1-343">忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-343">Ignored.</span></span>|  
|`pattern`|<span data-ttu-id="b3ad1-344">忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-344">Ignored.</span></span>|  
|<span data-ttu-id="b3ad1-345">(空白)</span><span class="sxs-lookup"><span data-stu-id="b3ad1-345">(blank)</span></span>|<span data-ttu-id="b3ad1-346">支援。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-346">Supported.</span></span>|  
  
## <a name="enumeration"></a><span data-ttu-id="b3ad1-347">列舉</span><span class="sxs-lookup"><span data-stu-id="b3ad1-347">Enumeration</span></span>  
  
### <a name="xsrestriction-for-enumerations-attributes"></a><span data-ttu-id="b3ad1-348">\<xs: restriction > 列舉型別： 屬性</span><span class="sxs-lookup"><span data-stu-id="b3ad1-348">\<xs:restriction> for enumerations: attributes</span></span>  
  
|<span data-ttu-id="b3ad1-349">屬性</span><span class="sxs-lookup"><span data-stu-id="b3ad1-349">Attribute</span></span>|<span data-ttu-id="b3ad1-350">結構描述</span><span class="sxs-lookup"><span data-stu-id="b3ad1-350">Schema</span></span>|  
|---------------|------------|  
|`base`|<span data-ttu-id="b3ad1-351">如果存在的話，必須是 `xs:string`。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-351">If present, must be `xs:string`.</span></span>|  
|`id`|<span data-ttu-id="b3ad1-352">忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-352">Ignored.</span></span>|  
  
### <a name="xsrestriction-for-enumerations-contents"></a><span data-ttu-id="b3ad1-353">\<xs: restriction > 列舉： 內容</span><span class="sxs-lookup"><span data-stu-id="b3ad1-353">\<xs:restriction> for enumerations: contents</span></span>  
  
|<span data-ttu-id="b3ad1-354">內容</span><span class="sxs-lookup"><span data-stu-id="b3ad1-354">Contents</span></span>|<span data-ttu-id="b3ad1-355">結構描述</span><span class="sxs-lookup"><span data-stu-id="b3ad1-355">Schema</span></span>|  
|--------------|------------|  
|`simpleType`|<span data-ttu-id="b3ad1-356">如果存在，必須是資料合約所支援的列舉限制 (本節)。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-356">If present, must be an enumeration restriction supported by the data contract (this section).</span></span>|  
|`minExclusive`|<span data-ttu-id="b3ad1-357">忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-357">Ignored.</span></span>|  
|`minInclusive`|<span data-ttu-id="b3ad1-358">忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-358">Ignored.</span></span>|  
|`maxExclusive`|<span data-ttu-id="b3ad1-359">忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-359">Ignored.</span></span>|  
|`maxInclusive`|<span data-ttu-id="b3ad1-360">忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-360">Ignored.</span></span>|  
|`totalDigits`|<span data-ttu-id="b3ad1-361">忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-361">Ignored.</span></span>|  
|`fractionDigits`|<span data-ttu-id="b3ad1-362">忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-362">Ignored.</span></span>|  
|`length`|<span data-ttu-id="b3ad1-363">禁止。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-363">Forbidden.</span></span>|  
|`minLength`|<span data-ttu-id="b3ad1-364">禁止。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-364">Forbidden.</span></span>|  
|`maxLength`|<span data-ttu-id="b3ad1-365">禁止。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-365">Forbidden.</span></span>|  
|`enumeration`|<span data-ttu-id="b3ad1-366">支援。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-366">Supported.</span></span> <span data-ttu-id="b3ad1-367">會忽略列舉 "id"，並將 "value" 對應至列舉資料合約中的值名稱。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-367">Enumeration "id" is ignored, and "value" maps to the value name in the enumeration data contract.</span></span>|  
|`whiteSpace`|<span data-ttu-id="b3ad1-368">禁止。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-368">Forbidden.</span></span>|  
|`pattern`|<span data-ttu-id="b3ad1-369">禁止。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-369">Forbidden.</span></span>|  
|<span data-ttu-id="b3ad1-370">(空白)</span><span class="sxs-lookup"><span data-stu-id="b3ad1-370">(empty)</span></span>|<span data-ttu-id="b3ad1-371">支援，且對應至空的列舉型別。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-371">Supported, maps to empty enumeration type.</span></span>|  
  
 <span data-ttu-id="b3ad1-372">下列程式碼將示範 C# 列舉類別。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-372">The following code shows a C# enumeration class.</span></span>  
  
```  
public enum MyEnum  
{  
   first = 3,  
   second = 4,  
   third =5  
```  
  
 <span data-ttu-id="b3ad1-373">}</span><span class="sxs-lookup"><span data-stu-id="b3ad1-373">}</span></span>  
  
 <span data-ttu-id="b3ad1-374">此類別會透過 `DataContractSerializer`對應至下列結構描述。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-374">This class maps to the following schema by the `DataContractSerializer`.</span></span> <span data-ttu-id="b3ad1-375">如果列舉值從 1 開始，則不會產生 `xs:annotation` 區塊。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-375">If enumeration values start from 1, `xs:annotation` blocks are not generated.</span></span>  
  
```xml  
<xs:simpleType name="MyEnum">  
<xs:restriction base="xs:string">  
 <xs:enumeration value="first">  
  <xs:annotation>  
   <xs:appinfo>  
    <EnumerationValue   
     xmlns="http://schemas.microsoft.com/2003/10/Serialization/">  
     3  
    </EnumerationValue>  
   </xs:appinfo>  
  </xs:annotation>  
 </xs:enumeration>  
 <xs:enumeration value="second">  
  <xs:annotation>  
   <xs:appinfo>  
    <EnumerationValue   
     xmlns="http://schemas.microsoft.com/2003/10/Serialization/">  
     4  
    </EnumerationValue>  
   </xs:appinfo>  
  </xs:annotation>  
 </xs:enumeration>  
</xs:restriction>  
</xs:simpleType>  
```  
  
### <a name="xslist"></a><span data-ttu-id="b3ad1-376">\<x: list> ></span><span class="sxs-lookup"><span data-stu-id="b3ad1-376">\<xs:list></span></span>  
 <span data-ttu-id="b3ad1-377">`DataContractSerializer` 會將標示為 `System.FlagsAttribute` 的列舉型別對應至衍生自 `xs:list` 的 `xs:string`。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-377">`DataContractSerializer` maps enumeration types marked with `System.FlagsAttribute` to `xs:list` derived from `xs:string`.</span></span> <span data-ttu-id="b3ad1-378">不支援其他任何 `xs:list` 變化。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-378">No other `xs:list` variations are supported.</span></span>  
  
### <a name="xslist-attributes"></a><span data-ttu-id="b3ad1-379">\<x: list> >： 屬性</span><span class="sxs-lookup"><span data-stu-id="b3ad1-379">\<xs:list>: attributes</span></span>  
  
|<span data-ttu-id="b3ad1-380">屬性</span><span class="sxs-lookup"><span data-stu-id="b3ad1-380">Attribute</span></span>|<span data-ttu-id="b3ad1-381">結構描述</span><span class="sxs-lookup"><span data-stu-id="b3ad1-381">Schema</span></span>|  
|---------------|------------|  
|`itemType`|<span data-ttu-id="b3ad1-382">禁止。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-382">Forbidden.</span></span>|  
|`id`|<span data-ttu-id="b3ad1-383">忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-383">Ignored.</span></span>|  
  
### <a name="xslist-contents"></a><span data-ttu-id="b3ad1-384">\<x: list> >： 內容</span><span class="sxs-lookup"><span data-stu-id="b3ad1-384">\<xs:list>: contents</span></span>  
  
|<span data-ttu-id="b3ad1-385">內容</span><span class="sxs-lookup"><span data-stu-id="b3ad1-385">Contents</span></span>|<span data-ttu-id="b3ad1-386">結構描述</span><span class="sxs-lookup"><span data-stu-id="b3ad1-386">Schema</span></span>|  
|--------------|------------|  
|`simpleType`|<span data-ttu-id="b3ad1-387">必須使用 `xs:string` Facet 從 `xs:enumeration` 限制。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-387">Must be restriction from `xs:string` using `xs:enumeration` facet.</span></span>|  
  
 <span data-ttu-id="b3ad1-388">如果列舉值並未遵循 2 次方的級數 (旗標的預設值)，則會將值儲存在 `xs:annotation/xs:appInfo/ser:EnumerationValue` 項目中。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-388">If enumeration value does not follow a power of 2 progression (default for Flags), the value is stored in the `xs:annotation/xs:appInfo/ser:EnumerationValue` element.</span></span>  
  
 <span data-ttu-id="b3ad1-389">例如，下列程式碼會為列舉型別加上旗標。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-389">For example, the following code flags an enumeration type.</span></span>  
  
```  
[Flags]  
public enum AuthFlags  
{    
  AuthAnonymous = 1,  
  AuthBasic = 2,  
  AuthNTLM = 4,  
  AuthMD5 = 16,  
  AuthWindowsLiveID = 64,  
}  
```  
  
 <span data-ttu-id="b3ad1-390">此型別會對應至下列結構描述。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-390">This type maps to the following schema.</span></span>  
  
```xml  
<xs:simpleType name="AuthFlags">  
    <xs:list>  
      <xs:simpleType>  
        <xs:restriction base="xs:string">  
          <xs:enumeration value="AuthAnonymous" />  
          <xs:enumeration value="AuthBasic" />  
          <xs:enumeration value="AuthNTLM" />  
          <xs:enumeration value="AuthMD5">  
            <xs:annotation>  
              <xs:appinfo>  
                <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Se  
rialization/">16</EnumerationValue>  
              </xs:appinfo>  
            </xs:annotation>  
          </xs:enumeration>  
          <xs:enumeration value="AuthWindowsLiveID">  
            <xs:annotation>  
              <xs:appinfo>  
                <EnumerationValue xmlns="http://schemas.microsoft.com/2003/10/Se  
rialization/">64</EnumerationValue>  
              </xs:appinfo>  
            </xs:annotation>  
          </xs:enumeration>  
        </xs:restriction>  
      </xs:simpleType>  
    </xs:list>  
  </xs:simpleType>  
```  
  
## <a name="inheritance"></a><span data-ttu-id="b3ad1-391">繼承</span><span class="sxs-lookup"><span data-stu-id="b3ad1-391">Inheritance</span></span>  
  
### <a name="general-rules"></a><span data-ttu-id="b3ad1-392">一般規則</span><span class="sxs-lookup"><span data-stu-id="b3ad1-392">General rules</span></span>  
 <span data-ttu-id="b3ad1-393">資料合約可以繼承自其他資料合約。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-393">A data contract can inherit from another data contract.</span></span> <span data-ttu-id="b3ad1-394">此類資料合約會對應至基底型別，而且會使用 `<xs:extension>` XML 結構描述建構並由延伸型別衍生。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-394">Such data contracts map to a base and are derived by extension types using the `<xs:extension>` XML Schema construct.</span></span>  
  
 <span data-ttu-id="b3ad1-395">資料合約無法繼承自集合資料合約。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-395">A data contract cannot inherit from a collection data contract.</span></span>  
  
 <span data-ttu-id="b3ad1-396">例如，下列程式碼為資料合約。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-396">For example, the following code is a data contract.</span></span>  
  
```  
[DataContract]  
public class Person  
{  
  [DataMember]  
  public string Name;  
}  
[DataContract]  
public class Employee : Person   
{      
  [DataMember]  
  public int ID;  
}  
```  
  
 <span data-ttu-id="b3ad1-397">此資料合約會對應至下列 XML 結構描述型別宣告。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-397">This data contract maps to the following XML Schema type declaration.</span></span>  
  
```xml  
<xs:complexType name="Employee">  
 <xs:complexContent mixed="false">  
  <xs:extension base="tns:Person">  
   <xs:sequence>  
    <xs:element minOccurs="0" name="ID" type="xs:int"/>  
   </xs:sequence>  
  </xs:extension>  
 </xs:complexContent>  
</xs:complexType>  
<xs:complexType name="Person">  
 <xs:sequence>  
  <xs:element minOccurs="0" name="Name"   
    nillable="true" type="xs:string"/>  
 </xs:sequence>  
</xs:complexType>  
```  
  
### <a name="xscomplexcontent-attributes"></a><span data-ttu-id="b3ad1-398">\<complexcontent> >： 屬性</span><span class="sxs-lookup"><span data-stu-id="b3ad1-398">\<xs:complexContent>: attributes</span></span>  
  
|<span data-ttu-id="b3ad1-399">屬性</span><span class="sxs-lookup"><span data-stu-id="b3ad1-399">Attribute</span></span>|<span data-ttu-id="b3ad1-400">結構描述</span><span class="sxs-lookup"><span data-stu-id="b3ad1-400">Schema</span></span>|  
|---------------|------------|  
|`id`|<span data-ttu-id="b3ad1-401">忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-401">Ignored.</span></span>|  
|`mixed`|<span data-ttu-id="b3ad1-402">必須為 false。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-402">Must be false.</span></span>|  
  
### <a name="xscomplexcontent-contents"></a><span data-ttu-id="b3ad1-403">\<complexcontent> >： 內容</span><span class="sxs-lookup"><span data-stu-id="b3ad1-403">\<xs:complexContent>: contents</span></span>  
  
|<span data-ttu-id="b3ad1-404">內容</span><span class="sxs-lookup"><span data-stu-id="b3ad1-404">Contents</span></span>|<span data-ttu-id="b3ad1-405">結構描述</span><span class="sxs-lookup"><span data-stu-id="b3ad1-405">Schema</span></span>|  
|--------------|------------|  
|`restriction`|<span data-ttu-id="b3ad1-406">禁止，除了當 base="`xs:anyType`" 以外。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-406">Forbidden, except when base="`xs:anyType`".</span></span> <span data-ttu-id="b3ad1-407">後者等同於將 `xs:restriction` 的內容直接放在 `xs:complexContent`容器底下。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-407">The latter is equivalent to placing the content of the `xs:restriction` directly under the container of the `xs:complexContent`.</span></span>|  
|`extension`|<span data-ttu-id="b3ad1-408">支援。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-408">Supported.</span></span> <span data-ttu-id="b3ad1-409">對應至資料合約繼承。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-409">Maps to data contract inheritance.</span></span>|  
  
### <a name="xsextension-in-xscomplexcontent-attributes"></a><span data-ttu-id="b3ad1-410">\<xs: extension > 在\<complexcontent> >： 屬性</span><span class="sxs-lookup"><span data-stu-id="b3ad1-410">\<xs:extension> in \<xs:complexContent>: attributes</span></span>  
  
|<span data-ttu-id="b3ad1-411">屬性</span><span class="sxs-lookup"><span data-stu-id="b3ad1-411">Attribute</span></span>|<span data-ttu-id="b3ad1-412">結構描述</span><span class="sxs-lookup"><span data-stu-id="b3ad1-412">Schema</span></span>|  
|---------------|------------|  
|`id`|<span data-ttu-id="b3ad1-413">忽略。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-413">Ignored.</span></span>|  
|`base`|<span data-ttu-id="b3ad1-414">支援。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-414">Supported.</span></span> <span data-ttu-id="b3ad1-415">對應至此型別所繼承的基底資料合約型別。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-415">Maps to the base data contract type that this type inherits from.</span></span>|  
  
### <a name="xsextension-in-xscomplexcontent-contents"></a><span data-ttu-id="b3ad1-416">\<xs: extension > 在\<complexcontent> >： 內容</span><span class="sxs-lookup"><span data-stu-id="b3ad1-416">\<xs:extension> in \<xs:complexContent>: contents</span></span>  
 <span data-ttu-id="b3ad1-417">其規則與 `<xs:complexType>` 內容的規則一樣。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-417">The rules are the same as for `<xs:complexType>` contents.</span></span>  
  
 <span data-ttu-id="b3ad1-418">如果提供了 `<xs:sequence>` ，則其成員項目會對應至額外資料成員 (存在衍生的資料合約中)。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-418">If an `<xs:sequence>` is provided, its member elements map to additional data members that are present in the derived data contract.</span></span>  
  
 <span data-ttu-id="b3ad1-419">如果衍生型別內含的項目與基底型別中的項目擁有相同的名稱，則重複的項目宣告會對應至已產生唯一名稱的資料成員。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-419">If a derived type contains an element with the same name as an element in a base type, the duplicate element declaration maps to a data member with a name that is generated to be unique.</span></span> <span data-ttu-id="b3ad1-420">正整數會新增至資料成員名稱 ("member1"、"member2" 等等)，直到找到唯一名稱為止。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-420">Positive integer numbers are added to the data member name ("member1", "member2", and so on) until a unique name is found.</span></span> <span data-ttu-id="b3ad1-421">相反地：</span><span class="sxs-lookup"><span data-stu-id="b3ad1-421">Conversely:</span></span>  
  
-   <span data-ttu-id="b3ad1-422">如果衍生資料合約的資料成員與基底資料合約中的資料成員具有相同的名稱與型別，則 `DataContractSerializer` 會在衍生型別中產生這個對應的項目。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-422">If a derived data contract has a data member with the same name and type as a data member in a base data contract, `DataContractSerializer` generates this corresponding element in the derived type.</span></span>  
  
-   <span data-ttu-id="b3ad1-423">如果衍生資料合約的資料成員與基底資料合約中的資料成員具有相同的名稱 (但型別不同)，則 `DataContractSerializer` 會將包含型別 `xs:anyType` 之項目的結構描述匯入基底型別與衍生型別宣告中。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-423">If a derived data contract has a data member with the same name as a data member in a base data contract but a different type, the `DataContractSerializer` imports a schema with an element of the type `xs:anyType` in both base type and derived type declarations.</span></span> <span data-ttu-id="b3ad1-424">原始型別名稱會保留在 `xs:annotations/xs:appInfo/ser:ActualType/@Name`中。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-424">The original type name is preserved in `xs:annotations/xs:appInfo/ser:ActualType/@Name`.</span></span>  
  
 <span data-ttu-id="b3ad1-425">兩種變化視各自的資料成員的順序而定，都可能會導致結構描述內含模糊的內容模型。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-425">Both variations may lead to a schema with an ambiguous content model, which depends on the order of the respective data members.</span></span>  
  
## <a name="typeprimitive-mapping"></a><span data-ttu-id="b3ad1-426">型別/基本對應</span><span class="sxs-lookup"><span data-stu-id="b3ad1-426">Type/primitive mapping</span></span>  
 <span data-ttu-id="b3ad1-427">`DataContractSerializer` 針對 XML 結構描述基本型別使用下列對應。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-427">The `DataContractSerializer` uses the following mapping for XML Schema primitive types.</span></span>  
  
|<span data-ttu-id="b3ad1-428">XSD 類型</span><span class="sxs-lookup"><span data-stu-id="b3ad1-428">XSD type</span></span>|<span data-ttu-id="b3ad1-429">.NET 型別</span><span class="sxs-lookup"><span data-stu-id="b3ad1-429">.NET type</span></span>|  
|--------------|---------------|  
|`anyType`|<span data-ttu-id="b3ad1-430"><xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="b3ad1-430"><xref:System.Object>.</span></span>|  
|`anySimpleType`|<span data-ttu-id="b3ad1-431"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b3ad1-431"><xref:System.String>.</span></span>|  
|`duration`|<span data-ttu-id="b3ad1-432"><xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="b3ad1-432"><xref:System.TimeSpan>.</span></span>|  
|`dateTime`|<span data-ttu-id="b3ad1-433"><xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="b3ad1-433"><xref:System.DateTime>.</span></span>|  
|`dateTimeOffset`|<span data-ttu-id="b3ad1-434">用於位移的<xref:System.DateTime> 和 <xref:System.TimeSpan> 。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-434"><xref:System.DateTime> and <xref:System.TimeSpan> for the offset.</span></span> <span data-ttu-id="b3ad1-435">請參閱下面的＜DateTimeOffset 序列化＞。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-435">See DateTimeOffset Serialization below.</span></span>|  
|`time`|<span data-ttu-id="b3ad1-436"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b3ad1-436"><xref:System.String>.</span></span>|  
|`date`|<span data-ttu-id="b3ad1-437"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b3ad1-437"><xref:System.String>.</span></span>|  
|`gYearMonth`|<span data-ttu-id="b3ad1-438"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b3ad1-438"><xref:System.String>.</span></span>|  
|`gYear`|<span data-ttu-id="b3ad1-439"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b3ad1-439"><xref:System.String>.</span></span>|  
|`gMonthDay`|<span data-ttu-id="b3ad1-440"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b3ad1-440"><xref:System.String>.</span></span>|  
|`gDay`|<span data-ttu-id="b3ad1-441"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b3ad1-441"><xref:System.String>.</span></span>|  
|`gMonth`|<span data-ttu-id="b3ad1-442"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b3ad1-442"><xref:System.String>.</span></span>|  
|`boolean`|<xref:System.Boolean>|  
|`base64Binary`|<span data-ttu-id="b3ad1-443"><xref:System.Byte> 陣列。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-443"><xref:System.Byte> array.</span></span>|  
|`hexBinary`|<span data-ttu-id="b3ad1-444"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b3ad1-444"><xref:System.String>.</span></span>|  
|`float`|<span data-ttu-id="b3ad1-445"><xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="b3ad1-445"><xref:System.Single>.</span></span>|  
|`double`|<span data-ttu-id="b3ad1-446"><xref:System.Double>.</span><span class="sxs-lookup"><span data-stu-id="b3ad1-446"><xref:System.Double>.</span></span>|  
|`anyURI`|<span data-ttu-id="b3ad1-447"><xref:System.Uri>.</span><span class="sxs-lookup"><span data-stu-id="b3ad1-447"><xref:System.Uri>.</span></span>|  
|`QName`|<span data-ttu-id="b3ad1-448"><xref:System.Xml.XmlQualifiedName>.</span><span class="sxs-lookup"><span data-stu-id="b3ad1-448"><xref:System.Xml.XmlQualifiedName>.</span></span>|  
|`string`|<span data-ttu-id="b3ad1-449"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b3ad1-449"><xref:System.String>.</span></span>|  
|`normalizedString`|<span data-ttu-id="b3ad1-450"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b3ad1-450"><xref:System.String>.</span></span>|  
|`token`|<span data-ttu-id="b3ad1-451"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b3ad1-451"><xref:System.String>.</span></span>|  
|`language`|<span data-ttu-id="b3ad1-452"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b3ad1-452"><xref:System.String>.</span></span>|  
|`Name`|<span data-ttu-id="b3ad1-453"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b3ad1-453"><xref:System.String>.</span></span>|  
|`NCName`|<span data-ttu-id="b3ad1-454"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b3ad1-454"><xref:System.String>.</span></span>|  
|`ID`|<span data-ttu-id="b3ad1-455"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b3ad1-455"><xref:System.String>.</span></span>|  
|`IDREF`|<span data-ttu-id="b3ad1-456"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b3ad1-456"><xref:System.String>.</span></span>|  
|`IDREFS`|<span data-ttu-id="b3ad1-457"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b3ad1-457"><xref:System.String>.</span></span>|  
|`ENTITY`|<span data-ttu-id="b3ad1-458"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b3ad1-458"><xref:System.String>.</span></span>|  
|`ENTITIES`|<span data-ttu-id="b3ad1-459"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b3ad1-459"><xref:System.String>.</span></span>|  
|`NMTOKEN`|<span data-ttu-id="b3ad1-460"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b3ad1-460"><xref:System.String>.</span></span>|  
|`NMTOKENS`|<span data-ttu-id="b3ad1-461"><xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="b3ad1-461"><xref:System.String>.</span></span>|  
|`decimal`|<span data-ttu-id="b3ad1-462"><xref:System.Decimal>.</span><span class="sxs-lookup"><span data-stu-id="b3ad1-462"><xref:System.Decimal>.</span></span>|  
|`integer`|<span data-ttu-id="b3ad1-463"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="b3ad1-463"><xref:System.Int64>.</span></span>|  
|`nonPositiveInteger`|<span data-ttu-id="b3ad1-464"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="b3ad1-464"><xref:System.Int64>.</span></span>|  
|`negativeInteger`|<span data-ttu-id="b3ad1-465"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="b3ad1-465"><xref:System.Int64>.</span></span>|  
|`long`|<span data-ttu-id="b3ad1-466"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="b3ad1-466"><xref:System.Int64>.</span></span>|  
|`int`|<span data-ttu-id="b3ad1-467"><xref:System.Int32>.</span><span class="sxs-lookup"><span data-stu-id="b3ad1-467"><xref:System.Int32>.</span></span>|  
|`short`|<span data-ttu-id="b3ad1-468"><xref:System.Int16>.</span><span class="sxs-lookup"><span data-stu-id="b3ad1-468"><xref:System.Int16>.</span></span>|  
|`Byte`|<span data-ttu-id="b3ad1-469"><xref:System.SByte>.</span><span class="sxs-lookup"><span data-stu-id="b3ad1-469"><xref:System.SByte>.</span></span>|  
|`nonNegativeInteger`|<span data-ttu-id="b3ad1-470"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="b3ad1-470"><xref:System.Int64>.</span></span>|  
|`unsignedLong`|<span data-ttu-id="b3ad1-471"><xref:System.UInt64>.</span><span class="sxs-lookup"><span data-stu-id="b3ad1-471"><xref:System.UInt64>.</span></span>|  
|`unsignedInt`|<span data-ttu-id="b3ad1-472"><xref:System.UInt32>.</span><span class="sxs-lookup"><span data-stu-id="b3ad1-472"><xref:System.UInt32>.</span></span>|  
|`unsignedShort`|<span data-ttu-id="b3ad1-473"><xref:System.UInt16>.</span><span class="sxs-lookup"><span data-stu-id="b3ad1-473"><xref:System.UInt16>.</span></span>|  
|`unsignedByte`|<span data-ttu-id="b3ad1-474"><xref:System.Byte>.</span><span class="sxs-lookup"><span data-stu-id="b3ad1-474"><xref:System.Byte>.</span></span>|  
|`positiveInteger`|<span data-ttu-id="b3ad1-475"><xref:System.Int64>.</span><span class="sxs-lookup"><span data-stu-id="b3ad1-475"><xref:System.Int64>.</span></span>|  
  
## <a name="iserializable-types-mapping"></a><span data-ttu-id="b3ad1-476">ISerializable 型別對應</span><span class="sxs-lookup"><span data-stu-id="b3ad1-476">ISerializable types mapping</span></span>  
 <span data-ttu-id="b3ad1-477">在 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 1.0 版中，已將 `ISerializable` 引入為用來序列化物件以便保存或做為資料傳輸用途的一般機制。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-477">In [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] version 1.0, `ISerializable` was introduced as a general mechanism to serialize objects for persistence or data transfer.</span></span> <span data-ttu-id="b3ad1-478">有許多 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 型別都會實作 `ISerializable` ，而且可以在應用程式之間傳遞。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-478">There are many [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] types that implement `ISerializable` and that can be passed between applications.</span></span> <span data-ttu-id="b3ad1-479">`DataContractSerializer` 自然會為 `ISerializable` 類別提供支援。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-479">`DataContractSerializer` naturally provides support for `ISerializable` classes.</span></span> <span data-ttu-id="b3ad1-480">`DataContractSerializer` 會對應至 `ISerializable` 實作結構描述型別 (其中只有型別的 QName 限定名稱不同)，而且是有效的屬性集合。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-480">The `DataContractSerializer` maps `ISerializable` implementation schema types that differ only by the QName (qualified name) of the type and are effectively property collections.</span></span> <span data-ttu-id="b3ad1-481">例如， `DataContractSerializer` 對應 <xref:System.Exception> 至下列 XSD 型別中 `http://schemas.datacontract.org/2004/07/System` 命名空間。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-481">For example, the `DataContractSerializer` maps <xref:System.Exception> to the following XSD type in the `http://schemas.datacontract.org/2004/07/System` namespace.</span></span>  
  
```xml  
<xs:complexType name="Exception">  
 <xs:sequence>  
  <xs:any minOccurs="0" maxOccurs="unbounded"   
      namespace="##local" processContents="skip"/>  
 </xs:sequence>  
 <xs:attribute ref="ser:FactoryType"/>  
</xs:complexType>  
```  
  
 <span data-ttu-id="b3ad1-482">在資料合約序列化結構描述中宣告的選用屬性 `ser:FactoryType` 會參考可以還原序列化型別的處理站類別。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-482">The optional attribute `ser:FactoryType` declared in the Data Contract Serialization schema references a factory class that can deserialize the type.</span></span> <span data-ttu-id="b3ad1-483">處理站類別必須是正在使用之 `DataContractSerializer` 執行個體的已知型別集合的一部分。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-483">The factory class must be part of the known types collection of the `DataContractSerializer` instance being used.</span></span> <span data-ttu-id="b3ad1-484">如需已知型別的詳細資訊，請參閱[Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-484">For more information about known types, see [Data Contract Known Types](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).</span></span>  
  
## <a name="datacontract-serialization-schema"></a><span data-ttu-id="b3ad1-485">DataContract 序列化結構描述</span><span class="sxs-lookup"><span data-stu-id="b3ad1-485">DataContract Serialization Schema</span></span>  
 <span data-ttu-id="b3ad1-486">由 `DataContractSerializer` 匯出的一些結構描述使用來自特殊資料合約序列化命名空間的型別、項目和屬性：</span><span class="sxs-lookup"><span data-stu-id="b3ad1-486">A number of schemas exported by the `DataContractSerializer` use types, elements, and attributes from a special Data Contract Serialization namespace:</span></span>  
  
 `http://schemas.microsoft.com/2003/10/Serialization`
  
 <span data-ttu-id="b3ad1-487">下列為完整的資料合約序列化結構描述宣告。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-487">The following is a complete Data Contract Serialization schema declaration.</span></span>  
  
```xml  
<xs:schema attributeFormDefault="qualified"          
   elementFormDefault="qualified"        
   targetNamespace =   
    "http://schemas.microsoft.com/2003/10/Serialization/"   
   xmlns:xs="http://www.w3.org/2001/XMLSchema"        
   xmlns:tns="http://schemas.microsoft.com/2003/10/Serialization/">  
  
 <!-- Top-level elements for primitive types. -->  
 <xs:element name="anyType" nillable="true" type="xs:anyType"/>  
 <xs:element name="anyURI" nillable="true" type="xs:anyURI"/>  
 <xs:element name="base64Binary"  
       nillable="true" type="xs:base64Binary"/>  
 <xs:element name="boolean" nillable="true" type="xs:boolean"/>  
 <xs:element name="byte" nillable="true" type="xs:byte"/>  
 <xs:element name="dateTime" nillable="true" type="xs:dateTime"/>  
 <xs:element name="decimal" nillable="true" type="xs:decimal"/>  
 <xs:element name="double" nillable="true" type="xs:double"/>  
 <xs:element name="float" nillable="true" type="xs:float"/>  
 <xs:element name="int" nillable="true" type="xs:int"/>  
 <xs:element name="long" nillable="true" type="xs:long"/>  
 <xs:element name="QName" nillable="true" type="xs:QName"/>  
 <xs:element name="short" nillable="true" type="xs:short"/>  
 <xs:element name="string" nillable="true" type="xs:string"/>  
 <xs:element name="unsignedByte"  
       nillable="true" type="xs:unsignedByte"/>  
 <xs:element name="unsignedInt"  
       nillable="true" type="xs:unsignedInt"/>  
 <xs:element name="unsignedLong"  
       nillable="true" type="xs:unsignedLong"/>  
 <xs:element name="unsignedShort"  
       nillable="true" type="xs:unsignedShort"/>  
  
 <!-- Primitive types introduced for certain .NET simple types. -->  
 <xs:element name="char" nillable="true" type="tns:char"/>  
 <xs:simpleType name="char">  
  <xs:restriction base="xs:int"/>  
 </xs:simpleType>  
  
 <!-- xs:duration is restricted to an ordered value space,  
    to map to System.TimeSpan -->  
 <xs:element name="duration" nillable="true" type="tns:duration"/>  
 <xs:simpleType name="duration">  
  <xs:restriction base="xs:duration">  
   <xs:pattern   
     value="\-?P(\d*D)?(T(\d*H)?(\d*M)?(\d*(\.\d*)?S)?)?"/>  
   <xs:minInclusive value="-P10675199DT2H48M5.4775808S"/>  
   <xs:maxInclusive value="P10675199DT2H48M5.4775807S"/>  
  </xs:restriction>  
 </xs:simpleType>  
  
 <xs:element name="guid" nillable="true" type="tns:guid"/>  
 <xs:simpleType name="guid">  
  <xs:restriction base="xs:string">  
   <xs:pattern value="[\da-fA-F]{8}-[\da-fA-F]{4}-[\da-fA-F]{4}-[\da-fA-F]{4}-[\da-fA-F]{12}"/>  
  </xs:restriction>  
 </xs:simpleType>  
  
 <!-- This is used for schemas exported from ISerializable type. -->  
 <xs:attribute name="FactoryType" type="xs:QName"/>  
</xs:schema>  
```  
  
 <span data-ttu-id="b3ad1-488">請注意下列各項：</span><span class="sxs-lookup"><span data-stu-id="b3ad1-488">The following should be noted:</span></span>  
  
-   <span data-ttu-id="b3ad1-489">`ser:char` 已引入來代表型別 <xref:System.Char>的 Unicode 字元。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-489">`ser:char` is introduced to represent Unicode characters of type <xref:System.Char>.</span></span>  
  
-   <span data-ttu-id="b3ad1-490">`valuespace` 的 `xs:duration` 已縮減為排序的組合，以對應至 <xref:System.TimeSpan>。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-490">The `valuespace` of `xs:duration` is reduced to an ordered set so that it can be mapped to a <xref:System.TimeSpan>.</span></span>  
  
-   <span data-ttu-id="b3ad1-491">`FactoryType` 會用在衍生自 <xref:System.Runtime.Serialization.ISerializable>之型別所匯出的結構描述中。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-491">`FactoryType` is used in schemas exported from types that are derived from <xref:System.Runtime.Serialization.ISerializable>.</span></span>  
  
## <a name="importing-non-datacontract-schemas"></a><span data-ttu-id="b3ad1-492">匯入非 DataContract 結構描述</span><span class="sxs-lookup"><span data-stu-id="b3ad1-492">Importing non-DataContract schemas</span></span>  
 <span data-ttu-id="b3ad1-493">`DataContractSerializer` 具有 `ImportXmlTypes` 選項，可允許匯入不符合 `DataContractSerializer` XSD 設定檔的結構描述 (請參閱 <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> 屬性)。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-493">`DataContractSerializer` has the `ImportXmlTypes` option to allow import of schemas that do not conform to the `DataContractSerializer` XSD profile (see the <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> property).</span></span> <span data-ttu-id="b3ad1-494">將此選項設為 `true` 可允許接受不符的結構描述型別，並將之對應至下列實作： <xref:System.Xml.Serialization.IXmlSerializable> 包裝 <xref:System.Xml.XmlNode> 的陣列 (只有類別名稱不同)。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-494">Setting this option to `true` enables acceptance of non-conforming schema types and mapping them to the following implementation, <xref:System.Xml.Serialization.IXmlSerializable> wrapping an array of <xref:System.Xml.XmlNode> (only the class name differs).</span></span>  
  
```  
[GeneratedCodeAttribute("System.Runtime.Serialization", "3.0.0.0")]  
[System.Xml.Serialization.XmlSchemaProviderAttribute("ExportSchema")]  
[System.Xml.Serialization.XmlRootAttribute(IsNullable=false)]  
public partial class Person : object, IXmlSerializable  
{    
  private XmlNode[] nodesField;    
  private static XmlQualifiedName typeName =   
new XmlQualifiedName("Person","http://Microsoft.ServiceModel.Samples");    
  public XmlNode[] Nodes  
  {  
    get {return this.nodesField;}  
    set {this.nodesField = value;}  
  }    
  public void ReadXml(XmlReader reader)  
  {  
    this.nodesField = XmlSerializableServices.ReadNodes(reader);  
  }    
  public void WriteXml(XmlWriter writer)  
  {  
    XmlSerializableServices.WriteNodes(writer, this.Nodes);  
  }    
  public System.Xml.Schema.XmlSchema GetSchema()  
  {  
    return null;  
  }    
  public static XmlQualifiedName ExportSchema(XmlSchemaSet schemas)  
  {  
    XmlSerializableServices.AddDefaultSchema(schemas, typeName);  
    return typeName;  
  }  
}  
```  
  
## <a name="datetimeoffset-serialization"></a><span data-ttu-id="b3ad1-495">DateTimeOffset 序列化</span><span class="sxs-lookup"><span data-stu-id="b3ad1-495">DateTimeOffset Serialization</span></span>  
 <span data-ttu-id="b3ad1-496"><xref:System.DateTimeOffset> 不會被視為基本型別。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-496">The <xref:System.DateTimeOffset> is not treated as a primitive type.</span></span> <span data-ttu-id="b3ad1-497">反之，它會被序列化為包含兩個部分的複雜項目。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-497">Instead, it is serialized as a complex element with two parts.</span></span> <span data-ttu-id="b3ad1-498">第一個部分代表日期時間，而第二個部分則代表日期時間的位移。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-498">The first part represents the date time, and the second part represents the offset from the date time.</span></span> <span data-ttu-id="b3ad1-499">下列程式碼提供序列化的 DateTimeOffset 值範例。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-499">An example of a serialized DateTimeOffset value is shown in the following code.</span></span>  
  
```xml  
<OffSet xmlns:a="http://schemas.datacontract.org/2004/07/System">  
  <DateTime i:type="b:dateTime" xmlns=""   
    xmlns:b="http://www.w3.org/2001/XMLSchema">2008-08-28T08:00:00    
  </DateTime>   
  <OffsetMinutes i:type="b:short" xmlns=""   
   xmlns:b="http://www.w3.org/2001/XMLSchema">-480  
   </OffsetMinutes>   
</OffSet>  
```  
  
 <span data-ttu-id="b3ad1-500">結構描述如下列所示。</span><span class="sxs-lookup"><span data-stu-id="b3ad1-500">The schema is as follows.</span></span>  
  
```xml  
<xs:schema targetNamespace="http://schemas.datacontract.org/2004/07/System">  
   <xs:complexType name="DateTimeOffset">  
      <xs:sequence minOccurs="1" maxOccurs="1">  
         <xs:element name="DateTime" type="xs:dateTime"  
         minOccurs="1" maxOccurs="1" />  
         <xs:elementname="OffsetMinutes" type="xs:short"  
         minOccurs="1" maxOccurs="1" />  
      </xs:sequence>  
   </xs:complexType>  
</xs:schema>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b3ad1-501">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b3ad1-501">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 <xref:System.Runtime.Serialization.XsdDataContractImporter>  
 [<span data-ttu-id="b3ad1-502">使用資料合約</span><span class="sxs-lookup"><span data-stu-id="b3ad1-502">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
