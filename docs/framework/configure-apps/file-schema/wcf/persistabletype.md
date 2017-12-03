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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 56443902885e191d93897096e55742f7665ba00a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltpersistabletypegt"></a><span data-ttu-id="aa4ba-102">&lt;persistableType&gt;</span><span class="sxs-lookup"><span data-stu-id="aa4ba-102">&lt;persistableType&gt;</span></span>
<span data-ttu-id="aa4ba-103">指定所有永久性型別。</span><span class="sxs-lookup"><span data-stu-id="aa4ba-103">Specifies all the persistable types.</span></span>  
  
 <span data-ttu-id="aa4ba-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="aa4ba-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="aa4ba-105">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="aa4ba-105">\<comContracts></span></span>  
<span data-ttu-id="aa4ba-106">\<comContract ></span><span class="sxs-lookup"><span data-stu-id="aa4ba-106">\<comContract></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa4ba-107">語法</span><span class="sxs-lookup"><span data-stu-id="aa4ba-107">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="aa4ba-108">類型</span><span class="sxs-lookup"><span data-stu-id="aa4ba-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aa4ba-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="aa4ba-109">Attributes and Elements</span></span>  
 <span data-ttu-id="aa4ba-110">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="aa4ba-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aa4ba-111">屬性</span><span class="sxs-lookup"><span data-stu-id="aa4ba-111">Attributes</span></span>  
  
|<span data-ttu-id="aa4ba-112">屬性</span><span class="sxs-lookup"><span data-stu-id="aa4ba-112">Attribute</span></span>|<span data-ttu-id="aa4ba-113">描述</span><span class="sxs-lookup"><span data-stu-id="aa4ba-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="aa4ba-114">id</span><span class="sxs-lookup"><span data-stu-id="aa4ba-114">id</span></span>|<span data-ttu-id="aa4ba-115">必要屬性，其中包含的字串可指定永久性類別的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="aa4ba-115">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="aa4ba-116">name</span><span class="sxs-lookup"><span data-stu-id="aa4ba-116">name</span></span>|<span data-ttu-id="aa4ba-117">選擇性屬性，其中包含的字串可指定永久性類別的名稱。</span><span class="sxs-lookup"><span data-stu-id="aa4ba-117">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="aa4ba-118">子元素</span><span class="sxs-lookup"><span data-stu-id="aa4ba-118">Child Elements</span></span>  
 <span data-ttu-id="aa4ba-119">無</span><span class="sxs-lookup"><span data-stu-id="aa4ba-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="aa4ba-120">父項目</span><span class="sxs-lookup"><span data-stu-id="aa4ba-120">Parent Elements</span></span>  
  
|<span data-ttu-id="aa4ba-121">項目</span><span class="sxs-lookup"><span data-stu-id="aa4ba-121">Element</span></span>|<span data-ttu-id="aa4ba-122">說明</span><span class="sxs-lookup"><span data-stu-id="aa4ba-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="aa4ba-123">\<persistableTypes ></span><span class="sxs-lookup"><span data-stu-id="aa4ba-123">\<persistableTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)|<span data-ttu-id="aa4ba-124">`persistableType` 項目的集合。</span><span class="sxs-lookup"><span data-stu-id="aa4ba-124">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aa4ba-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aa4ba-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>  
 [<span data-ttu-id="aa4ba-126">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="aa4ba-126">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [<span data-ttu-id="aa4ba-127">整合 COM + 應用程式</span><span class="sxs-lookup"><span data-stu-id="aa4ba-127">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="aa4ba-128">如何： 設定 COM + 服務設定</span><span class="sxs-lookup"><span data-stu-id="aa4ba-128">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
