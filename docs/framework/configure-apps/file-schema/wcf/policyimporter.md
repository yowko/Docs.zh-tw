---
title: <policyImporter>
ms.date: 03/30/2017
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
ms.openlocfilehash: 4ef5890d52c3f2af42322f023b9a2a23cb583035
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855057"
---
# <a name="policyimporter"></a><span data-ttu-id="5485f-101">\<policyImporter></span><span class="sxs-lookup"><span data-stu-id="5485f-101">\<policyImporter></span></span>
<span data-ttu-id="5485f-102">指定原則匯入工具，此工具會控制匯入有關繫結的自訂原則判斷提示 (Assertion)。</span><span class="sxs-lookup"><span data-stu-id="5485f-102">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
<span data-ttu-id="5485f-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5485f-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5485f-104">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="5485f-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="5485f-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<用戶端 >** ](client.md)</span><span class="sxs-lookup"><span data-stu-id="5485f-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="5485f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<中繼資料 >** ](metadata.md)</span><span class="sxs-lookup"><span data-stu-id="5485f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<metadata>**](metadata.md)</span></span>\
<span data-ttu-id="5485f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<policyImporters >** ](policyimporters.md)</span><span class="sxs-lookup"><span data-stu-id="5485f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<policyImporters>**](policyimporters.md)</span></span>  
<span data-ttu-id="5485f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<policyImporter >**</span><span class="sxs-lookup"><span data-stu-id="5485f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<policyImporter>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5485f-109">語法</span><span class="sxs-lookup"><span data-stu-id="5485f-109">Syntax</span></span>  
  
```xml  
<metadata>
  <policyImporters>
    <policyImporter type="String" />
  </policyImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5485f-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5485f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5485f-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="5485f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5485f-112">屬性</span><span class="sxs-lookup"><span data-stu-id="5485f-112">Attributes</span></span>  
  
|<span data-ttu-id="5485f-113">屬性</span><span class="sxs-lookup"><span data-stu-id="5485f-113">Attribute</span></span>|<span data-ttu-id="5485f-114">描述</span><span class="sxs-lookup"><span data-stu-id="5485f-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="5485f-115">此項目的型別。</span><span class="sxs-lookup"><span data-stu-id="5485f-115">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5485f-116">子元素</span><span class="sxs-lookup"><span data-stu-id="5485f-116">Child Elements</span></span>  
 <span data-ttu-id="5485f-117">無</span><span class="sxs-lookup"><span data-stu-id="5485f-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5485f-118">父項目</span><span class="sxs-lookup"><span data-stu-id="5485f-118">Parent Elements</span></span>  
  
|<span data-ttu-id="5485f-119">項目</span><span class="sxs-lookup"><span data-stu-id="5485f-119">Element</span></span>|<span data-ttu-id="5485f-120">描述</span><span class="sxs-lookup"><span data-stu-id="5485f-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5485f-121">\<policyImporters></span><span class="sxs-lookup"><span data-stu-id="5485f-121">\<policyImporters></span></span>](policyimporters.md)|<span data-ttu-id="5485f-122">指定所有原則匯入工具，這些工具會控制匯入有關繫結的自訂原則判斷提示 (Assertion)。</span><span class="sxs-lookup"><span data-stu-id="5485f-122">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5485f-123">備註</span><span class="sxs-lookup"><span data-stu-id="5485f-123">Remarks</span></span>  
 <span data-ttu-id="5485f-124">原則匯入工具是用來搜尋有關繫結功能的自訂原則判斷提示，以及附加可實作判斷提示所需要功能的自訂繫結項目。</span><span class="sxs-lookup"><span data-stu-id="5485f-124">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5485f-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5485f-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.PolicyImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Description.MetadataImporter>
- [<span data-ttu-id="5485f-126">WCF 用戶端組態</span><span class="sxs-lookup"><span data-stu-id="5485f-126">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="5485f-127">用戶端</span><span class="sxs-lookup"><span data-stu-id="5485f-127">Clients</span></span>](../../../wcf/feature-details/clients.md)
