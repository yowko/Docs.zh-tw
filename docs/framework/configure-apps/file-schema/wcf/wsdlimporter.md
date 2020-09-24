---
title: <wsdlImporter>
ms.date: 03/30/2017
ms.assetid: 986b2165-8430-4dba-b1b8-00396841bb96
ms.openlocfilehash: 82704aa40b508f1b1e2237c9768a7b7599c5c87e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158587"
---
# \<wsdlImporter>

<span data-ttu-id="6c02a-101">指定所有 WSDL 匯入工具，此工具會使用 WS-Policy 附件匯入 Web 服務描述語言 (WSDL) 1.1 中繼資料。</span><span class="sxs-lookup"><span data-stu-id="6c02a-101">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<metadata>**](metadata.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsdlImporters>**](wsdlimporters.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsdlImporter>**  
  
## <a name="syntax"></a><span data-ttu-id="6c02a-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="6c02a-102">Syntax</span></span>  
  
```xml  
<metadata>
  <wsdlImporters>
    <wsdlImporter type="string" />
  </wsdlImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6c02a-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6c02a-103">Attributes and Elements</span></span>  

 <span data-ttu-id="6c02a-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="6c02a-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6c02a-105">屬性</span><span class="sxs-lookup"><span data-stu-id="6c02a-105">Attributes</span></span>  
  
|<span data-ttu-id="6c02a-106">屬性</span><span class="sxs-lookup"><span data-stu-id="6c02a-106">Attribute</span></span>|<span data-ttu-id="6c02a-107">描述</span><span class="sxs-lookup"><span data-stu-id="6c02a-107">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="6c02a-108">此項目的型別。</span><span class="sxs-lookup"><span data-stu-id="6c02a-108">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6c02a-109">子元素</span><span class="sxs-lookup"><span data-stu-id="6c02a-109">Child Elements</span></span>  

 <span data-ttu-id="6c02a-110">無。</span><span class="sxs-lookup"><span data-stu-id="6c02a-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6c02a-111">父項目</span><span class="sxs-lookup"><span data-stu-id="6c02a-111">Parent Elements</span></span>  
  
|<span data-ttu-id="6c02a-112">項目</span><span class="sxs-lookup"><span data-stu-id="6c02a-112">Element</span></span>|<span data-ttu-id="6c02a-113">描述</span><span class="sxs-lookup"><span data-stu-id="6c02a-113">Description</span></span>|  
|-------------|-----------------|  
|[\<wsdlImporters>](wsdlimporters.md)|<span data-ttu-id="6c02a-114">指定所有 WSDL 匯入工具，此工具會使用 WS-Policy 附件匯入 Web 服務描述語言 (WSDL) 1.1 中繼資料。</span><span class="sxs-lookup"><span data-stu-id="6c02a-114">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c02a-115">備註</span><span class="sxs-lookup"><span data-stu-id="6c02a-115">Remarks</span></span>  

 <span data-ttu-id="6c02a-116">WSDL 匯入工具是用來匯入中繼資料，以及將該資訊轉換成表示合約和端點資訊的各種不同類別。</span><span class="sxs-lookup"><span data-stu-id="6c02a-116">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="6c02a-117">它可以選擇性地匯入合約和端點資訊，以及可公開 (Expose) 任何匯入錯誤並接受與匯入和轉換處理有關聯之型別資訊的屬性。</span><span class="sxs-lookup"><span data-stu-id="6c02a-117">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="6c02a-118">此外，它也支援匯入繫結資訊，以及可提供存取任何原則文件、WSDL 文件、WSDL 延伸和 XML 結構描述文件的屬性。</span><span class="sxs-lookup"><span data-stu-id="6c02a-118">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c02a-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c02a-119">See also</span></span>

- <xref:System.ServiceModel.Configuration.WsdlImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="6c02a-120">WCF 用戶端組態</span><span class="sxs-lookup"><span data-stu-id="6c02a-120">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="6c02a-121">用戶端</span><span class="sxs-lookup"><span data-stu-id="6c02a-121">Clients</span></span>](../../../wcf/feature-details/clients.md)
