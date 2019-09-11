---
title: <metadata>
ms.date: 03/30/2017
ms.assetid: d09653eb-e355-4c73-b87b-28f93d56480d
ms.openlocfilehash: 028e4d3fbe7bce06caa7497c8f95f3b293a4b068
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855222"
---
# <a name="metadata"></a><span data-ttu-id="2f9e7-101">\<中繼資料 ></span><span class="sxs-lookup"><span data-stu-id="2f9e7-101">\<metadata></span></span>
<span data-ttu-id="2f9e7-102">指定如何處理服務中繼資料。</span><span class="sxs-lookup"><span data-stu-id="2f9e7-102">Specifies how service metadata can be processed.</span></span>  
  
<span data-ttu-id="2f9e7-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2f9e7-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2f9e7-104">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="2f9e7-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="2f9e7-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<用戶端 >** ](client.md)</span><span class="sxs-lookup"><span data-stu-id="2f9e7-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="2f9e7-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<中繼資料 >**</span><span class="sxs-lookup"><span data-stu-id="2f9e7-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<metadata>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f9e7-107">語法</span><span class="sxs-lookup"><span data-stu-id="2f9e7-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <client>
    <metadata>
      <policyImporters>
        <policyImporter type="string" />
      </policyImporters>
      <wsdlImporters>
        <wsdlImporter type="string" />
      </wsdlImporters>
    </metadata>
  </client>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2f9e7-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2f9e7-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2f9e7-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="2f9e7-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2f9e7-110">屬性</span><span class="sxs-lookup"><span data-stu-id="2f9e7-110">Attributes</span></span>  
 <span data-ttu-id="2f9e7-111">無。</span><span class="sxs-lookup"><span data-stu-id="2f9e7-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2f9e7-112">子元素</span><span class="sxs-lookup"><span data-stu-id="2f9e7-112">Child Elements</span></span>  
  
|<span data-ttu-id="2f9e7-113">項目</span><span class="sxs-lookup"><span data-stu-id="2f9e7-113">Element</span></span>|<span data-ttu-id="2f9e7-114">說明</span><span class="sxs-lookup"><span data-stu-id="2f9e7-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2f9e7-115">\<policyImporters></span><span class="sxs-lookup"><span data-stu-id="2f9e7-115">\<policyImporters></span></span>](policyimporters.md)|<span data-ttu-id="2f9e7-116">指定所有原則匯入工具，這些工具會控制匯入有關繫結的自訂原則判斷提示 (Assertion)。</span><span class="sxs-lookup"><span data-stu-id="2f9e7-116">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span> <span data-ttu-id="2f9e7-117">原則匯入工具是用來搜尋有關繫結功能的自訂原則判斷提示，以及附加可實作判斷提示所需要功能的自訂繫結項目。</span><span class="sxs-lookup"><span data-stu-id="2f9e7-117">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>|  
|[<span data-ttu-id="2f9e7-118">\<wsdlImporters></span><span class="sxs-lookup"><span data-stu-id="2f9e7-118">\<wsdlImporters></span></span>](wsdlimporters.md)|<span data-ttu-id="2f9e7-119">指定所有 WSDL 匯入工具，此工具會使用 WS-Policy 附件匯入 Web 服務描述語言 (WSDL) 1.1 中繼資料。</span><span class="sxs-lookup"><span data-stu-id="2f9e7-119">Specifies all the WSDL importers that import Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span> <span data-ttu-id="2f9e7-120">WSDL 匯入工具是用來匯入中繼資料，以及將該資訊轉換成表示合約和端點資訊的各種不同類別。</span><span class="sxs-lookup"><span data-stu-id="2f9e7-120">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="2f9e7-121">它可以選擇性地匯入合約和端點資訊，以及可公開 (Expose) 任何匯入錯誤並接受與匯入和轉換處理有關聯之型別資訊的屬性。</span><span class="sxs-lookup"><span data-stu-id="2f9e7-121">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="2f9e7-122">此外，它也支援匯入繫結資訊，以及可提供存取任何原則文件、WSDL 文件、WSDL 延伸和 XML 結構描述文件的屬性。</span><span class="sxs-lookup"><span data-stu-id="2f9e7-122">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2f9e7-123">父項目</span><span class="sxs-lookup"><span data-stu-id="2f9e7-123">Parent Elements</span></span>  
  
|<span data-ttu-id="2f9e7-124">項目</span><span class="sxs-lookup"><span data-stu-id="2f9e7-124">Element</span></span>|<span data-ttu-id="2f9e7-125">說明</span><span class="sxs-lookup"><span data-stu-id="2f9e7-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2f9e7-126">\<client></span><span class="sxs-lookup"><span data-stu-id="2f9e7-126">\<client></span></span>](client.md)|<span data-ttu-id="2f9e7-127">用戶端區段會定義用戶端可連線的端點清單。</span><span class="sxs-lookup"><span data-stu-id="2f9e7-127">The client section defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2f9e7-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f9e7-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="2f9e7-129">WCF 用戶端組態</span><span class="sxs-lookup"><span data-stu-id="2f9e7-129">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="2f9e7-130">用戶端</span><span class="sxs-lookup"><span data-stu-id="2f9e7-130">Clients</span></span>](../../../wcf/feature-details/clients.md)
