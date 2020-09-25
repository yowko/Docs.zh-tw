---
title: <policyImporter>
ms.date: 03/30/2017
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
ms.openlocfilehash: 72778ce0070d853f8b081a4889ead9524bafd0e8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181345"
---
# \<policyImporter>

<span data-ttu-id="260fd-101">指定原則匯入工具，此工具會控制匯入有關繫結的自訂原則判斷提示 (Assertion)。</span><span class="sxs-lookup"><span data-stu-id="260fd-101">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<metadata>**](metadata.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<policyImporters>**](policyimporters.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<policyImporter>**  
  
## <a name="syntax"></a><span data-ttu-id="260fd-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="260fd-102">Syntax</span></span>  
  
```xml  
<metadata>
  <policyImporters>
    <policyImporter type="String" />
  </policyImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="260fd-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="260fd-103">Attributes and Elements</span></span>  

 <span data-ttu-id="260fd-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="260fd-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="260fd-105">屬性</span><span class="sxs-lookup"><span data-stu-id="260fd-105">Attributes</span></span>  
  
|<span data-ttu-id="260fd-106">屬性</span><span class="sxs-lookup"><span data-stu-id="260fd-106">Attribute</span></span>|<span data-ttu-id="260fd-107">描述</span><span class="sxs-lookup"><span data-stu-id="260fd-107">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="260fd-108">此項目的型別。</span><span class="sxs-lookup"><span data-stu-id="260fd-108">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="260fd-109">子元素</span><span class="sxs-lookup"><span data-stu-id="260fd-109">Child Elements</span></span>  

 <span data-ttu-id="260fd-110">無</span><span class="sxs-lookup"><span data-stu-id="260fd-110">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="260fd-111">父項目</span><span class="sxs-lookup"><span data-stu-id="260fd-111">Parent Elements</span></span>  
  
|<span data-ttu-id="260fd-112">項目</span><span class="sxs-lookup"><span data-stu-id="260fd-112">Element</span></span>|<span data-ttu-id="260fd-113">描述</span><span class="sxs-lookup"><span data-stu-id="260fd-113">Description</span></span>|  
|-------------|-----------------|  
|[\<policyImporters>](policyimporters.md)|<span data-ttu-id="260fd-114">指定所有原則匯入工具，這些工具會控制匯入有關繫結的自訂原則判斷提示 (Assertion)。</span><span class="sxs-lookup"><span data-stu-id="260fd-114">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="260fd-115">備註</span><span class="sxs-lookup"><span data-stu-id="260fd-115">Remarks</span></span>  

 <span data-ttu-id="260fd-116">原則匯入工具是用來搜尋有關繫結功能的自訂原則判斷提示，以及附加可實作判斷提示所需要功能的自訂繫結項目。</span><span class="sxs-lookup"><span data-stu-id="260fd-116">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="260fd-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="260fd-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.PolicyImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Description.MetadataImporter>
- [<span data-ttu-id="260fd-118">WCF 用戶端組態</span><span class="sxs-lookup"><span data-stu-id="260fd-118">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="260fd-119">用戶端</span><span class="sxs-lookup"><span data-stu-id="260fd-119">Clients</span></span>](../../../wcf/feature-details/clients.md)
