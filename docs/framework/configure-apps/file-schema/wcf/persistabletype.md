---
title: <persistableType>
ms.date: 03/30/2017
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
ms.openlocfilehash: 3ea99d360ceb1e3fe6e97cbf9c8827dd7c853f63
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55256520"
---
# <a name="persistabletype"></a><span data-ttu-id="0d8cf-101">\<persistableType></span><span class="sxs-lookup"><span data-stu-id="0d8cf-101">\<persistableType></span></span>
<span data-ttu-id="0d8cf-102">指定所有永久性型別。</span><span class="sxs-lookup"><span data-stu-id="0d8cf-102">Specifies all the persistable types.</span></span>  
  
 <span data-ttu-id="0d8cf-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0d8cf-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="0d8cf-104">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="0d8cf-104">\<comContracts></span></span>  
<span data-ttu-id="0d8cf-105">\<comContract></span><span class="sxs-lookup"><span data-stu-id="0d8cf-105">\<comContract></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d8cf-106">語法</span><span class="sxs-lookup"><span data-stu-id="0d8cf-106">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="0d8cf-107">類型</span><span class="sxs-lookup"><span data-stu-id="0d8cf-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0d8cf-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0d8cf-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0d8cf-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="0d8cf-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0d8cf-110">屬性</span><span class="sxs-lookup"><span data-stu-id="0d8cf-110">Attributes</span></span>  
  
|<span data-ttu-id="0d8cf-111">屬性</span><span class="sxs-lookup"><span data-stu-id="0d8cf-111">Attribute</span></span>|<span data-ttu-id="0d8cf-112">描述</span><span class="sxs-lookup"><span data-stu-id="0d8cf-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0d8cf-113">id</span><span class="sxs-lookup"><span data-stu-id="0d8cf-113">id</span></span>|<span data-ttu-id="0d8cf-114">必要屬性，其中包含的字串可指定永久性類別的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="0d8cf-114">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="0d8cf-115">name</span><span class="sxs-lookup"><span data-stu-id="0d8cf-115">name</span></span>|<span data-ttu-id="0d8cf-116">選擇性屬性，其中包含的字串可指定永久性類別的名稱。</span><span class="sxs-lookup"><span data-stu-id="0d8cf-116">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0d8cf-117">子元素</span><span class="sxs-lookup"><span data-stu-id="0d8cf-117">Child Elements</span></span>  
 <span data-ttu-id="0d8cf-118">無</span><span class="sxs-lookup"><span data-stu-id="0d8cf-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0d8cf-119">父項目</span><span class="sxs-lookup"><span data-stu-id="0d8cf-119">Parent Elements</span></span>  
  
|<span data-ttu-id="0d8cf-120">項目</span><span class="sxs-lookup"><span data-stu-id="0d8cf-120">Element</span></span>|<span data-ttu-id="0d8cf-121">描述</span><span class="sxs-lookup"><span data-stu-id="0d8cf-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0d8cf-122">\<persistableTypes></span><span class="sxs-lookup"><span data-stu-id="0d8cf-122">\<persistableTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)|<span data-ttu-id="0d8cf-123">`persistableType` 項目的集合。</span><span class="sxs-lookup"><span data-stu-id="0d8cf-123">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0d8cf-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d8cf-124">See also</span></span>
- <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>
- [<span data-ttu-id="0d8cf-125">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="0d8cf-125">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)
- [<span data-ttu-id="0d8cf-126">整合 COM 應用程式</span><span class="sxs-lookup"><span data-stu-id="0d8cf-126">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="0d8cf-127">如何：設定 COM + 服務設定</span><span class="sxs-lookup"><span data-stu-id="0d8cf-127">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
