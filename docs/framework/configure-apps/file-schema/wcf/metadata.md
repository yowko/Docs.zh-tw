---
title: <metadata>
ms.date: 03/30/2017
ms.assetid: d09653eb-e355-4c73-b87b-28f93d56480d
ms.openlocfilehash: 028e4d3fbe7bce06caa7497c8f95f3b293a4b068
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855222"
---
# \<metadata>
<span data-ttu-id="aecc1-101">指定如何處理服務中繼資料。</span><span class="sxs-lookup"><span data-stu-id="aecc1-101">Specifies how service metadata can be processed.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<metadata>**  
  
## <a name="syntax"></a><span data-ttu-id="aecc1-102">語法</span><span class="sxs-lookup"><span data-stu-id="aecc1-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aecc1-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="aecc1-103">Attributes and Elements</span></span>  
 <span data-ttu-id="aecc1-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="aecc1-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aecc1-105">屬性</span><span class="sxs-lookup"><span data-stu-id="aecc1-105">Attributes</span></span>  
 <span data-ttu-id="aecc1-106">無。</span><span class="sxs-lookup"><span data-stu-id="aecc1-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="aecc1-107">子元素</span><span class="sxs-lookup"><span data-stu-id="aecc1-107">Child Elements</span></span>  
  
|<span data-ttu-id="aecc1-108">元素</span><span class="sxs-lookup"><span data-stu-id="aecc1-108">Element</span></span>|<span data-ttu-id="aecc1-109">描述</span><span class="sxs-lookup"><span data-stu-id="aecc1-109">Description</span></span>|  
|-------------|-----------------|  
|[\<policyImporters>](policyimporters.md)|<span data-ttu-id="aecc1-110">指定所有原則匯入工具，這些工具會控制匯入有關繫結的自訂原則判斷提示 (Assertion)。</span><span class="sxs-lookup"><span data-stu-id="aecc1-110">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span> <span data-ttu-id="aecc1-111">原則匯入工具是用來搜尋有關繫結功能的自訂原則判斷提示，以及附加可實作判斷提示所需要功能的自訂繫結項目。</span><span class="sxs-lookup"><span data-stu-id="aecc1-111">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>|  
|[\<wsdlImporters>](wsdlimporters.md)|<span data-ttu-id="aecc1-112">指定所有 WSDL 匯入工具，此工具會使用 WS-Policy 附件匯入 Web 服務描述語言 (WSDL) 1.1 中繼資料。</span><span class="sxs-lookup"><span data-stu-id="aecc1-112">Specifies all the WSDL importers that import Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span> <span data-ttu-id="aecc1-113">WSDL 匯入工具是用來匯入中繼資料，以及將該資訊轉換成表示合約和端點資訊的各種不同類別。</span><span class="sxs-lookup"><span data-stu-id="aecc1-113">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="aecc1-114">它可以選擇性地匯入合約和端點資訊，以及可公開 (Expose) 任何匯入錯誤並接受與匯入和轉換處理有關聯之型別資訊的屬性。</span><span class="sxs-lookup"><span data-stu-id="aecc1-114">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="aecc1-115">此外，它也支援匯入繫結資訊，以及可提供存取任何原則文件、WSDL 文件、WSDL 延伸和 XML 結構描述文件的屬性。</span><span class="sxs-lookup"><span data-stu-id="aecc1-115">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="aecc1-116">父項目</span><span class="sxs-lookup"><span data-stu-id="aecc1-116">Parent Elements</span></span>  
  
|<span data-ttu-id="aecc1-117">元素</span><span class="sxs-lookup"><span data-stu-id="aecc1-117">Element</span></span>|<span data-ttu-id="aecc1-118">描述</span><span class="sxs-lookup"><span data-stu-id="aecc1-118">Description</span></span>|  
|-------------|-----------------|  
|[\<client>](client.md)|<span data-ttu-id="aecc1-119">用戶端區段會定義用戶端可連線的端點清單。</span><span class="sxs-lookup"><span data-stu-id="aecc1-119">The client section defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aecc1-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aecc1-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="aecc1-121">WCF 用戶端組態</span><span class="sxs-lookup"><span data-stu-id="aecc1-121">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="aecc1-122">用戶端</span><span class="sxs-lookup"><span data-stu-id="aecc1-122">Clients</span></span>](../../../wcf/feature-details/clients.md)
