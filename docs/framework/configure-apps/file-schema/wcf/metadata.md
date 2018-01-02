---
title: "&lt;中繼資料&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d09653eb-e355-4c73-b87b-28f93d56480d
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e1da05ebd48a3fff7c35510db4093d56831a8fcd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltmetadatagt"></a><span data-ttu-id="afed3-102">&lt;中繼資料&gt;</span><span class="sxs-lookup"><span data-stu-id="afed3-102">&lt;metadata&gt;</span></span>
<span data-ttu-id="afed3-103">指定如何處理服務中繼資料。</span><span class="sxs-lookup"><span data-stu-id="afed3-103">Specifies how service metadata can be processed.</span></span>  
  
 <span data-ttu-id="afed3-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="afed3-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="afed3-105">\<用戶端 ></span><span class="sxs-lookup"><span data-stu-id="afed3-105">\<client></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afed3-106">語法</span><span class="sxs-lookup"><span data-stu-id="afed3-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
    <client>  
        <metadata>  
                   <policyImporters>  
                          <policyImporter type="string" />  
                   </policyImporters  
                 <wsdlImporters>  
                      <wsdlImporter type="string" />  
                 </wsdlImporters>  
        </metadata>  
    </client>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="afed3-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="afed3-107">Attributes and Elements</span></span>  
 <span data-ttu-id="afed3-108">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="afed3-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="afed3-109">屬性</span><span class="sxs-lookup"><span data-stu-id="afed3-109">Attributes</span></span>  
 <span data-ttu-id="afed3-110">無。</span><span class="sxs-lookup"><span data-stu-id="afed3-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="afed3-111">子元素</span><span class="sxs-lookup"><span data-stu-id="afed3-111">Child Elements</span></span>  
  
|<span data-ttu-id="afed3-112">項目</span><span class="sxs-lookup"><span data-stu-id="afed3-112">Element</span></span>|<span data-ttu-id="afed3-113">描述</span><span class="sxs-lookup"><span data-stu-id="afed3-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="afed3-114">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="afed3-114">\<policyImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|<span data-ttu-id="afed3-115">指定所有原則匯入工具，這些工具會控制匯入有關繫結的自訂原則判斷提示 (Assertion)。</span><span class="sxs-lookup"><span data-stu-id="afed3-115">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span> <span data-ttu-id="afed3-116">原則匯入工具是用來搜尋有關繫結功能的自訂原則判斷提示，以及附加可實作判斷提示所需要功能的自訂繫結項目。</span><span class="sxs-lookup"><span data-stu-id="afed3-116">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>|  
|[<span data-ttu-id="afed3-117">\<wsdlImporters ></span><span class="sxs-lookup"><span data-stu-id="afed3-117">\<wsdlImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/wsdlimporters.md)|<span data-ttu-id="afed3-118">指定所有 WSDL 匯入工具，此工具會使用 WS-Policy 附件匯入 Web 服務描述語言 (WSDL) 1.1 中繼資料。</span><span class="sxs-lookup"><span data-stu-id="afed3-118">Specifies all the WSDL importers that import Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span> <span data-ttu-id="afed3-119">WSDL 匯入工具是用來匯入中繼資料，以及將該資訊轉換成表示合約和端點資訊的各種不同類別。</span><span class="sxs-lookup"><span data-stu-id="afed3-119">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="afed3-120">它可以選擇性地匯入合約和端點資訊，以及可公開 (Expose) 任何匯入錯誤並接受與匯入和轉換處理有關聯之型別資訊的屬性。</span><span class="sxs-lookup"><span data-stu-id="afed3-120">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="afed3-121">此外，它也支援匯入繫結資訊，以及可提供存取任何原則文件、WSDL 文件、WSDL 延伸和 XML 結構描述文件的屬性。</span><span class="sxs-lookup"><span data-stu-id="afed3-121">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="afed3-122">父項目</span><span class="sxs-lookup"><span data-stu-id="afed3-122">Parent Elements</span></span>  
  
|<span data-ttu-id="afed3-123">項目</span><span class="sxs-lookup"><span data-stu-id="afed3-123">Element</span></span>|<span data-ttu-id="afed3-124">描述</span><span class="sxs-lookup"><span data-stu-id="afed3-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="afed3-125">\<用戶端 ></span><span class="sxs-lookup"><span data-stu-id="afed3-125">\<client></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|<span data-ttu-id="afed3-126">用戶端區段會定義用戶端可連線的端點清單。</span><span class="sxs-lookup"><span data-stu-id="afed3-126">The client section defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="afed3-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="afed3-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>  
 <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>  
 <xref:System.ServiceModel.Description.MetadataImporter>  
 <xref:System.ServiceModel.Description.WsdlImporter>  
 [<span data-ttu-id="afed3-128">WCF 用戶端組態</span><span class="sxs-lookup"><span data-stu-id="afed3-128">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="afed3-129">用戶端</span><span class="sxs-lookup"><span data-stu-id="afed3-129">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
