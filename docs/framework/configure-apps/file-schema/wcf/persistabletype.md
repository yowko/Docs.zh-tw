---
title: <persistableType>
ms.date: 03/30/2017
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
ms.openlocfilehash: 939a29e90ee21e94ccb78842d6f7224e9a6288d0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083734"
---
# <a name="persistabletype"></a><span data-ttu-id="0111f-101">\<persistableType></span><span class="sxs-lookup"><span data-stu-id="0111f-101">\<persistableType></span></span>
<span data-ttu-id="0111f-102">指定所有永久性型別。</span><span class="sxs-lookup"><span data-stu-id="0111f-102">Specifies all the persistable types.</span></span>  
  
 <span data-ttu-id="0111f-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0111f-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="0111f-104">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="0111f-104">\<comContracts></span></span>  
<span data-ttu-id="0111f-105">\<comContract></span><span class="sxs-lookup"><span data-stu-id="0111f-105">\<comContract></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0111f-106">語法</span><span class="sxs-lookup"><span data-stu-id="0111f-106">Syntax</span></span>  
  
```xml  
<comContracts>
  <comContract>
    <persistableTypes>
      <persistableType id="String"
                       name="String">
      </persistableType>
    </persistableTypes>
  </comContract>
</comContracts>
```  
  
## <a name="type"></a><span data-ttu-id="0111f-107">類型</span><span class="sxs-lookup"><span data-stu-id="0111f-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0111f-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0111f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0111f-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="0111f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0111f-110">屬性</span><span class="sxs-lookup"><span data-stu-id="0111f-110">Attributes</span></span>  
  
|<span data-ttu-id="0111f-111">屬性</span><span class="sxs-lookup"><span data-stu-id="0111f-111">Attribute</span></span>|<span data-ttu-id="0111f-112">描述</span><span class="sxs-lookup"><span data-stu-id="0111f-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0111f-113">id</span><span class="sxs-lookup"><span data-stu-id="0111f-113">id</span></span>|<span data-ttu-id="0111f-114">必要屬性，其中包含的字串可指定永久性類別的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="0111f-114">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="0111f-115">名稱</span><span class="sxs-lookup"><span data-stu-id="0111f-115">name</span></span>|<span data-ttu-id="0111f-116">選擇性屬性，其中包含的字串可指定永久性類別的名稱。</span><span class="sxs-lookup"><span data-stu-id="0111f-116">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0111f-117">子元素</span><span class="sxs-lookup"><span data-stu-id="0111f-117">Child Elements</span></span>  
 <span data-ttu-id="0111f-118">None</span><span class="sxs-lookup"><span data-stu-id="0111f-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0111f-119">父項目</span><span class="sxs-lookup"><span data-stu-id="0111f-119">Parent Elements</span></span>  
  
|<span data-ttu-id="0111f-120">項目</span><span class="sxs-lookup"><span data-stu-id="0111f-120">Element</span></span>|<span data-ttu-id="0111f-121">描述</span><span class="sxs-lookup"><span data-stu-id="0111f-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0111f-122">\<persistableTypes></span><span class="sxs-lookup"><span data-stu-id="0111f-122">\<persistableTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)|<span data-ttu-id="0111f-123">`persistableType` 項目的集合。</span><span class="sxs-lookup"><span data-stu-id="0111f-123">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0111f-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0111f-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>
- [<span data-ttu-id="0111f-125">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="0111f-125">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)
- [<span data-ttu-id="0111f-126">整合 COM+ 應用程式</span><span class="sxs-lookup"><span data-stu-id="0111f-126">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="0111f-127">HOW TO：設定 COM+ 服務設定</span><span class="sxs-lookup"><span data-stu-id="0111f-127">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
