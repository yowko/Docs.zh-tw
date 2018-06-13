---
title: '&lt;persistableType&gt;'
ms.date: 03/30/2017
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
ms.openlocfilehash: 23724957398ed1ade2c81a3932e9773d7cf4c642
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747069"
---
# <a name="ltpersistabletypegt"></a><span data-ttu-id="7f176-102">&lt;persistableType&gt;</span><span class="sxs-lookup"><span data-stu-id="7f176-102">&lt;persistableType&gt;</span></span>
<span data-ttu-id="7f176-103">指定所有永久性型別。</span><span class="sxs-lookup"><span data-stu-id="7f176-103">Specifies all the persistable types.</span></span>  
  
 <span data-ttu-id="7f176-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7f176-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7f176-105">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="7f176-105">\<comContracts></span></span>  
<span data-ttu-id="7f176-106">\<comContract ></span><span class="sxs-lookup"><span data-stu-id="7f176-106">\<comContract></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f176-107">語法</span><span class="sxs-lookup"><span data-stu-id="7f176-107">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="7f176-108">類型</span><span class="sxs-lookup"><span data-stu-id="7f176-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7f176-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7f176-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7f176-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="7f176-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7f176-111">屬性</span><span class="sxs-lookup"><span data-stu-id="7f176-111">Attributes</span></span>  
  
|<span data-ttu-id="7f176-112">屬性</span><span class="sxs-lookup"><span data-stu-id="7f176-112">Attribute</span></span>|<span data-ttu-id="7f176-113">描述</span><span class="sxs-lookup"><span data-stu-id="7f176-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7f176-114">id</span><span class="sxs-lookup"><span data-stu-id="7f176-114">id</span></span>|<span data-ttu-id="7f176-115">必要屬性，其中包含的字串可指定永久性類別的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="7f176-115">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="7f176-116">name</span><span class="sxs-lookup"><span data-stu-id="7f176-116">name</span></span>|<span data-ttu-id="7f176-117">選擇性屬性，其中包含的字串可指定永久性類別的名稱。</span><span class="sxs-lookup"><span data-stu-id="7f176-117">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7f176-118">子項目</span><span class="sxs-lookup"><span data-stu-id="7f176-118">Child Elements</span></span>  
 <span data-ttu-id="7f176-119">無</span><span class="sxs-lookup"><span data-stu-id="7f176-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7f176-120">父項目</span><span class="sxs-lookup"><span data-stu-id="7f176-120">Parent Elements</span></span>  
  
|<span data-ttu-id="7f176-121">項目</span><span class="sxs-lookup"><span data-stu-id="7f176-121">Element</span></span>|<span data-ttu-id="7f176-122">描述</span><span class="sxs-lookup"><span data-stu-id="7f176-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7f176-123">\<persistableTypes></span><span class="sxs-lookup"><span data-stu-id="7f176-123">\<persistableTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)|<span data-ttu-id="7f176-124">`persistableType` 項目的集合。</span><span class="sxs-lookup"><span data-stu-id="7f176-124">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7f176-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7f176-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>  
 [<span data-ttu-id="7f176-126">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="7f176-126">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [<span data-ttu-id="7f176-127">整合 COM 應用程式</span><span class="sxs-lookup"><span data-stu-id="7f176-127">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [<span data-ttu-id="7f176-128">如何：設定 COM+ 服務設定</span><span class="sxs-lookup"><span data-stu-id="7f176-128">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
