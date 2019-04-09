---
title: <wsdlImporter>
ms.date: 03/30/2017
ms.assetid: 986b2165-8430-4dba-b1b8-00396841bb96
ms.openlocfilehash: 1f34486296465b3ea0b5b05bd9492062c85ad8c8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134429"
---
# <a name="wsdlimporter"></a><span data-ttu-id="44513-101">\<wsdlImporter></span><span class="sxs-lookup"><span data-stu-id="44513-101">\<wsdlImporter></span></span>
<span data-ttu-id="44513-102">指定所有 WSDL 匯入工具，此工具會使用 WS-Policy 附件匯入 Web 服務描述語言 (WSDL) 1.1 中繼資料。</span><span class="sxs-lookup"><span data-stu-id="44513-102">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>  
  
<span data-ttu-id="44513-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="44513-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="44513-104">\<client></span><span class="sxs-lookup"><span data-stu-id="44513-104">\<client></span></span>  
<span data-ttu-id="44513-105">\<metadata></span><span class="sxs-lookup"><span data-stu-id="44513-105">\<metadata></span></span>  
<span data-ttu-id="44513-106">\<wsdlImporters></span><span class="sxs-lookup"><span data-stu-id="44513-106">\<wsdlImporters></span></span>  
<span data-ttu-id="44513-107">\<wsdlImporter></span><span class="sxs-lookup"><span data-stu-id="44513-107">\<wsdlImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44513-108">語法</span><span class="sxs-lookup"><span data-stu-id="44513-108">Syntax</span></span>  
  
```xml  
<metadata>
  <wsdlImporters>
    <wsdlImporter type="string" />
  </wsdlImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44513-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="44513-109">Attributes and Elements</span></span>  
 <span data-ttu-id="44513-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="44513-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44513-111">屬性</span><span class="sxs-lookup"><span data-stu-id="44513-111">Attributes</span></span>  
  
|<span data-ttu-id="44513-112">屬性</span><span class="sxs-lookup"><span data-stu-id="44513-112">Attribute</span></span>|<span data-ttu-id="44513-113">描述</span><span class="sxs-lookup"><span data-stu-id="44513-113">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="44513-114">此項目的型別。</span><span class="sxs-lookup"><span data-stu-id="44513-114">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="44513-115">子元素</span><span class="sxs-lookup"><span data-stu-id="44513-115">Child Elements</span></span>  
 <span data-ttu-id="44513-116">無。</span><span class="sxs-lookup"><span data-stu-id="44513-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="44513-117">父項目</span><span class="sxs-lookup"><span data-stu-id="44513-117">Parent Elements</span></span>  
  
|<span data-ttu-id="44513-118">項目</span><span class="sxs-lookup"><span data-stu-id="44513-118">Element</span></span>|<span data-ttu-id="44513-119">描述</span><span class="sxs-lookup"><span data-stu-id="44513-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="44513-120">\<wsdlImporters></span><span class="sxs-lookup"><span data-stu-id="44513-120">\<wsdlImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdlimporters.md)|<span data-ttu-id="44513-121">指定所有 WSDL 匯入工具，此工具會使用 WS-Policy 附件匯入 Web 服務描述語言 (WSDL) 1.1 中繼資料。</span><span class="sxs-lookup"><span data-stu-id="44513-121">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44513-122">備註</span><span class="sxs-lookup"><span data-stu-id="44513-122">Remarks</span></span>  
 <span data-ttu-id="44513-123">WSDL 匯入工具是用來匯入中繼資料，以及將該資訊轉換成表示合約和端點資訊的各種不同類別。</span><span class="sxs-lookup"><span data-stu-id="44513-123">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="44513-124">它可以選擇性地匯入合約和端點資訊，以及可公開 (Expose) 任何匯入錯誤並接受與匯入和轉換處理有關聯之型別資訊的屬性。</span><span class="sxs-lookup"><span data-stu-id="44513-124">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="44513-125">此外，它也支援匯入繫結資訊，以及可提供存取任何原則文件、WSDL 文件、WSDL 延伸和 XML 結構描述文件的屬性。</span><span class="sxs-lookup"><span data-stu-id="44513-125">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44513-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44513-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.WsdlImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="44513-127">WCF 用戶端組態</span><span class="sxs-lookup"><span data-stu-id="44513-127">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="44513-128">用戶端</span><span class="sxs-lookup"><span data-stu-id="44513-128">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
