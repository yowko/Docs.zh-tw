---
title: <policyImporter>
ms.date: 03/30/2017
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
ms.openlocfilehash: 4ef5890d52c3f2af42322f023b9a2a23cb583035
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855057"
---
# \<policyImporter>
<span data-ttu-id="e151b-101">指定原則匯入工具，此工具會控制匯入有關繫結的自訂原則判斷提示 (Assertion)。</span><span class="sxs-lookup"><span data-stu-id="e151b-101">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<metadata>**](metadata.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<policyImporters>**](policyimporters.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<policyImporter>**  
  
## <a name="syntax"></a><span data-ttu-id="e151b-102">語法</span><span class="sxs-lookup"><span data-stu-id="e151b-102">Syntax</span></span>  
  
```xml  
<metadata>
  <policyImporters>
    <policyImporter type="String" />
  </policyImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e151b-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e151b-103">Attributes and Elements</span></span>  
 <span data-ttu-id="e151b-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e151b-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e151b-105">屬性</span><span class="sxs-lookup"><span data-stu-id="e151b-105">Attributes</span></span>  
  
|<span data-ttu-id="e151b-106">屬性</span><span class="sxs-lookup"><span data-stu-id="e151b-106">Attribute</span></span>|<span data-ttu-id="e151b-107">描述</span><span class="sxs-lookup"><span data-stu-id="e151b-107">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="e151b-108">此項目的型別。</span><span class="sxs-lookup"><span data-stu-id="e151b-108">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e151b-109">子元素</span><span class="sxs-lookup"><span data-stu-id="e151b-109">Child Elements</span></span>  
 <span data-ttu-id="e151b-110">無</span><span class="sxs-lookup"><span data-stu-id="e151b-110">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e151b-111">父項目</span><span class="sxs-lookup"><span data-stu-id="e151b-111">Parent Elements</span></span>  
  
|<span data-ttu-id="e151b-112">元素</span><span class="sxs-lookup"><span data-stu-id="e151b-112">Element</span></span>|<span data-ttu-id="e151b-113">描述</span><span class="sxs-lookup"><span data-stu-id="e151b-113">Description</span></span>|  
|-------------|-----------------|  
|[\<policyImporters>](policyimporters.md)|<span data-ttu-id="e151b-114">指定所有原則匯入工具，這些工具會控制匯入有關繫結的自訂原則判斷提示 (Assertion)。</span><span class="sxs-lookup"><span data-stu-id="e151b-114">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e151b-115">備註</span><span class="sxs-lookup"><span data-stu-id="e151b-115">Remarks</span></span>  
 <span data-ttu-id="e151b-116">原則匯入工具是用來搜尋有關繫結功能的自訂原則判斷提示，以及附加可實作判斷提示所需要功能的自訂繫結項目。</span><span class="sxs-lookup"><span data-stu-id="e151b-116">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e151b-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e151b-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.PolicyImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Description.MetadataImporter>
- [<span data-ttu-id="e151b-118">WCF 用戶端組態</span><span class="sxs-lookup"><span data-stu-id="e151b-118">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="e151b-119">用戶端</span><span class="sxs-lookup"><span data-stu-id="e151b-119">Clients</span></span>](../../../wcf/feature-details/clients.md)
