---
title: <wsdlImporter>
ms.date: 03/30/2017
ms.assetid: 986b2165-8430-4dba-b1b8-00396841bb96
ms.openlocfilehash: bd6c8661f94610d932ffee631aee7ad060f04c6b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55269311"
---
# <a name="wsdlimporter"></a><span data-ttu-id="c0204-101">\<wsdlImporter></span><span class="sxs-lookup"><span data-stu-id="c0204-101">\<wsdlImporter></span></span>
<span data-ttu-id="c0204-102">指定所有 WSDL 匯入工具，此工具會使用 WS-Policy 附件匯入 Web 服務描述語言 (WSDL) 1.1 中繼資料。</span><span class="sxs-lookup"><span data-stu-id="c0204-102">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>  
  
<span data-ttu-id="c0204-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c0204-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="c0204-104">\<client></span><span class="sxs-lookup"><span data-stu-id="c0204-104">\<client></span></span>  
<span data-ttu-id="c0204-105">\<metadata></span><span class="sxs-lookup"><span data-stu-id="c0204-105">\<metadata></span></span>  
<span data-ttu-id="c0204-106">\<wsdlImporters></span><span class="sxs-lookup"><span data-stu-id="c0204-106">\<wsdlImporters></span></span>  
<span data-ttu-id="c0204-107">\<wsdlImporter></span><span class="sxs-lookup"><span data-stu-id="c0204-107">\<wsdlImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0204-108">語法</span><span class="sxs-lookup"><span data-stu-id="c0204-108">Syntax</span></span>  
  
```xml  
<metadata>
  <wsdlImporters>
    <wsdlImporter type="string" />
  </wsdlImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c0204-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c0204-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c0204-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c0204-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c0204-111">屬性</span><span class="sxs-lookup"><span data-stu-id="c0204-111">Attributes</span></span>  
  
|<span data-ttu-id="c0204-112">屬性</span><span class="sxs-lookup"><span data-stu-id="c0204-112">Attribute</span></span>|<span data-ttu-id="c0204-113">描述</span><span class="sxs-lookup"><span data-stu-id="c0204-113">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="c0204-114">此項目的型別。</span><span class="sxs-lookup"><span data-stu-id="c0204-114">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c0204-115">子元素</span><span class="sxs-lookup"><span data-stu-id="c0204-115">Child Elements</span></span>  
 <span data-ttu-id="c0204-116">無。</span><span class="sxs-lookup"><span data-stu-id="c0204-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c0204-117">父項目</span><span class="sxs-lookup"><span data-stu-id="c0204-117">Parent Elements</span></span>  
  
|<span data-ttu-id="c0204-118">項目</span><span class="sxs-lookup"><span data-stu-id="c0204-118">Element</span></span>|<span data-ttu-id="c0204-119">描述</span><span class="sxs-lookup"><span data-stu-id="c0204-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c0204-120">\<wsdlImporters></span><span class="sxs-lookup"><span data-stu-id="c0204-120">\<wsdlImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdlimporters.md)|<span data-ttu-id="c0204-121">指定所有 WSDL 匯入工具，此工具會使用 WS-Policy 附件匯入 Web 服務描述語言 (WSDL) 1.1 中繼資料。</span><span class="sxs-lookup"><span data-stu-id="c0204-121">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0204-122">備註</span><span class="sxs-lookup"><span data-stu-id="c0204-122">Remarks</span></span>  
 <span data-ttu-id="c0204-123">WSDL 匯入工具是用來匯入中繼資料，以及將該資訊轉換成表示合約和端點資訊的各種不同類別。</span><span class="sxs-lookup"><span data-stu-id="c0204-123">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="c0204-124">它可以選擇性地匯入合約和端點資訊，以及可公開 (Expose) 任何匯入錯誤並接受與匯入和轉換處理有關聯之型別資訊的屬性。</span><span class="sxs-lookup"><span data-stu-id="c0204-124">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="c0204-125">此外，它也支援匯入繫結資訊，以及可提供存取任何原則文件、WSDL 文件、WSDL 延伸和 XML 結構描述文件的屬性。</span><span class="sxs-lookup"><span data-stu-id="c0204-125">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0204-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0204-126">See also</span></span>
- <xref:System.ServiceModel.Configuration.WsdlImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="c0204-127">WCF 用戶端組態</span><span class="sxs-lookup"><span data-stu-id="c0204-127">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="c0204-128">用戶端</span><span class="sxs-lookup"><span data-stu-id="c0204-128">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
