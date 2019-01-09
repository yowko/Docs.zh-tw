---
title: '&lt;wsdlImporter&gt;'
ms.date: 03/30/2017
ms.assetid: 986b2165-8430-4dba-b1b8-00396841bb96
ms.openlocfilehash: 43c1a50c740cd9c75ee641e4ac4d0fa8ea3ca36b
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54144986"
---
# <a name="ltwsdlimportergt"></a><span data-ttu-id="528c9-102">&lt;wsdlImporter&gt;</span><span class="sxs-lookup"><span data-stu-id="528c9-102">&lt;wsdlImporter&gt;</span></span>
<span data-ttu-id="528c9-103">指定所有 WSDL 匯入工具，此工具會使用 WS-Policy 附件匯入 Web 服務描述語言 (WSDL) 1.1 中繼資料。</span><span class="sxs-lookup"><span data-stu-id="528c9-103">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>  
  
<span data-ttu-id="528c9-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="528c9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="528c9-105">\<用戶端 ></span><span class="sxs-lookup"><span data-stu-id="528c9-105">\<client></span></span>  
<span data-ttu-id="528c9-106">\<中繼資料 ></span><span class="sxs-lookup"><span data-stu-id="528c9-106">\<metadata></span></span>  
<span data-ttu-id="528c9-107">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="528c9-107">\<wsdlImporters></span></span>  
<span data-ttu-id="528c9-108">\<wsdlImporter ></span><span class="sxs-lookup"><span data-stu-id="528c9-108">\<wsdlImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="528c9-109">語法</span><span class="sxs-lookup"><span data-stu-id="528c9-109">Syntax</span></span>  
  
```xml  
<metadata>
  <wsdlImporters>
    <wsdlImporter type="string" />
  </wsdlImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="528c9-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="528c9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="528c9-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="528c9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="528c9-112">屬性</span><span class="sxs-lookup"><span data-stu-id="528c9-112">Attributes</span></span>  
  
|<span data-ttu-id="528c9-113">屬性</span><span class="sxs-lookup"><span data-stu-id="528c9-113">Attribute</span></span>|<span data-ttu-id="528c9-114">描述</span><span class="sxs-lookup"><span data-stu-id="528c9-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="528c9-115">此項目的型別。</span><span class="sxs-lookup"><span data-stu-id="528c9-115">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="528c9-116">子元素</span><span class="sxs-lookup"><span data-stu-id="528c9-116">Child Elements</span></span>  
 <span data-ttu-id="528c9-117">無。</span><span class="sxs-lookup"><span data-stu-id="528c9-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="528c9-118">父項目</span><span class="sxs-lookup"><span data-stu-id="528c9-118">Parent Elements</span></span>  
  
|<span data-ttu-id="528c9-119">項目</span><span class="sxs-lookup"><span data-stu-id="528c9-119">Element</span></span>|<span data-ttu-id="528c9-120">描述</span><span class="sxs-lookup"><span data-stu-id="528c9-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="528c9-121">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="528c9-121">\<wsdlImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdlimporters.md)|<span data-ttu-id="528c9-122">指定所有 WSDL 匯入工具，此工具會使用 WS-Policy 附件匯入 Web 服務描述語言 (WSDL) 1.1 中繼資料。</span><span class="sxs-lookup"><span data-stu-id="528c9-122">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="528c9-123">備註</span><span class="sxs-lookup"><span data-stu-id="528c9-123">Remarks</span></span>  
 <span data-ttu-id="528c9-124">WSDL 匯入工具是用來匯入中繼資料，以及將該資訊轉換成表示合約和端點資訊的各種不同類別。</span><span class="sxs-lookup"><span data-stu-id="528c9-124">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="528c9-125">它可以選擇性地匯入合約和端點資訊，以及可公開 (Expose) 任何匯入錯誤並接受與匯入和轉換處理有關聯之型別資訊的屬性。</span><span class="sxs-lookup"><span data-stu-id="528c9-125">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="528c9-126">此外，它也支援匯入繫結資訊，以及可提供存取任何原則文件、WSDL 文件、WSDL 延伸和 XML 結構描述文件的屬性。</span><span class="sxs-lookup"><span data-stu-id="528c9-126">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="528c9-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="528c9-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WsdlImporterElement>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>  
 <xref:System.ServiceModel.Description.MetadataImporter>  
 <xref:System.ServiceModel.Description.WsdlImporter>  
 [<span data-ttu-id="528c9-128">WCF 用戶端組態</span><span class="sxs-lookup"><span data-stu-id="528c9-128">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="528c9-129">用戶端</span><span class="sxs-lookup"><span data-stu-id="528c9-129">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
