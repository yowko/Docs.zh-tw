---
title: '&lt;persistableType&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c77bdf8ef02edf682ded95ab16b4d56dbf60b4ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltpersistabletypegt"></a><span data-ttu-id="d1508-102">&lt;persistableType&gt;</span><span class="sxs-lookup"><span data-stu-id="d1508-102">&lt;persistableType&gt;</span></span>
<span data-ttu-id="d1508-103">指定所有永久性型別。</span><span class="sxs-lookup"><span data-stu-id="d1508-103">Specifies all the persistable types.</span></span>  
  
 <span data-ttu-id="d1508-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="d1508-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d1508-105">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="d1508-105">\<comContracts></span></span>  
<span data-ttu-id="d1508-106">\<comContract ></span><span class="sxs-lookup"><span data-stu-id="d1508-106">\<comContract></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1508-107">語法</span><span class="sxs-lookup"><span data-stu-id="d1508-107">Syntax</span></span>  
  
```xml  
<comContracts>  
  <comContract>  
      <persistableTypes>  
         <persistableType id="string"  
            name="string">  
         </persistableType>  
      </persistableTypes>  
  </comContract>  
</comContracts>  
```  
  
## <a name="type"></a><span data-ttu-id="d1508-108">類型</span><span class="sxs-lookup"><span data-stu-id="d1508-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d1508-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d1508-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d1508-110">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d1508-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d1508-111">屬性</span><span class="sxs-lookup"><span data-stu-id="d1508-111">Attributes</span></span>  
  
|<span data-ttu-id="d1508-112">屬性</span><span class="sxs-lookup"><span data-stu-id="d1508-112">Attribute</span></span>|<span data-ttu-id="d1508-113">描述</span><span class="sxs-lookup"><span data-stu-id="d1508-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d1508-114">id</span><span class="sxs-lookup"><span data-stu-id="d1508-114">id</span></span>|<span data-ttu-id="d1508-115">必要屬性，其中包含的字串可指定永久性類別的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="d1508-115">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="d1508-116">name</span><span class="sxs-lookup"><span data-stu-id="d1508-116">name</span></span>|<span data-ttu-id="d1508-117">選擇性屬性，其中包含的字串可指定永久性類別的名稱。</span><span class="sxs-lookup"><span data-stu-id="d1508-117">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d1508-118">子元素</span><span class="sxs-lookup"><span data-stu-id="d1508-118">Child Elements</span></span>  
 <span data-ttu-id="d1508-119">無</span><span class="sxs-lookup"><span data-stu-id="d1508-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d1508-120">父項目</span><span class="sxs-lookup"><span data-stu-id="d1508-120">Parent Elements</span></span>  
  
|<span data-ttu-id="d1508-121">項目</span><span class="sxs-lookup"><span data-stu-id="d1508-121">Element</span></span>|<span data-ttu-id="d1508-122">說明</span><span class="sxs-lookup"><span data-stu-id="d1508-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d1508-123">\<persistableTypes ></span><span class="sxs-lookup"><span data-stu-id="d1508-123">\<persistableTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)|<span data-ttu-id="d1508-124">`persistableType` 項目的集合。</span><span class="sxs-lookup"><span data-stu-id="d1508-124">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d1508-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1508-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>  
 [<span data-ttu-id="d1508-126">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="d1508-126">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [<span data-ttu-id="d1508-127">整合 COM + 應用程式</span><span class="sxs-lookup"><span data-stu-id="d1508-127">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="d1508-128">如何： 設定 COM + 服務設定</span><span class="sxs-lookup"><span data-stu-id="d1508-128">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
