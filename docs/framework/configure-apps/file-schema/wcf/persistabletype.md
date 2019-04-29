---
title: <persistableType>
ms.date: 03/30/2017
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
ms.openlocfilehash: 939a29e90ee21e94ccb78842d6f7224e9a6288d0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783314"
---
# <a name="persistabletype"></a><span data-ttu-id="f786c-101">\<persistableType></span><span class="sxs-lookup"><span data-stu-id="f786c-101">\<persistableType></span></span>
<span data-ttu-id="f786c-102">指定所有永久性型別。</span><span class="sxs-lookup"><span data-stu-id="f786c-102">Specifies all the persistable types.</span></span>  
  
 <span data-ttu-id="f786c-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f786c-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="f786c-104">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="f786c-104">\<comContracts></span></span>  
<span data-ttu-id="f786c-105">\<comContract></span><span class="sxs-lookup"><span data-stu-id="f786c-105">\<comContract></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f786c-106">語法</span><span class="sxs-lookup"><span data-stu-id="f786c-106">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="f786c-107">類型</span><span class="sxs-lookup"><span data-stu-id="f786c-107">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f786c-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f786c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f786c-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="f786c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f786c-110">屬性</span><span class="sxs-lookup"><span data-stu-id="f786c-110">Attributes</span></span>  
  
|<span data-ttu-id="f786c-111">屬性</span><span class="sxs-lookup"><span data-stu-id="f786c-111">Attribute</span></span>|<span data-ttu-id="f786c-112">描述</span><span class="sxs-lookup"><span data-stu-id="f786c-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f786c-113">id</span><span class="sxs-lookup"><span data-stu-id="f786c-113">id</span></span>|<span data-ttu-id="f786c-114">必要屬性，其中包含的字串可指定永久性類別的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="f786c-114">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="f786c-115">名稱</span><span class="sxs-lookup"><span data-stu-id="f786c-115">name</span></span>|<span data-ttu-id="f786c-116">選擇性屬性，其中包含的字串可指定永久性類別的名稱。</span><span class="sxs-lookup"><span data-stu-id="f786c-116">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f786c-117">子元素</span><span class="sxs-lookup"><span data-stu-id="f786c-117">Child Elements</span></span>  
 <span data-ttu-id="f786c-118">None</span><span class="sxs-lookup"><span data-stu-id="f786c-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f786c-119">父項目</span><span class="sxs-lookup"><span data-stu-id="f786c-119">Parent Elements</span></span>  
  
|<span data-ttu-id="f786c-120">項目</span><span class="sxs-lookup"><span data-stu-id="f786c-120">Element</span></span>|<span data-ttu-id="f786c-121">描述</span><span class="sxs-lookup"><span data-stu-id="f786c-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f786c-122">\<persistableTypes></span><span class="sxs-lookup"><span data-stu-id="f786c-122">\<persistableTypes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)|<span data-ttu-id="f786c-123">`persistableType` 項目的集合。</span><span class="sxs-lookup"><span data-stu-id="f786c-123">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f786c-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f786c-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>
- [<span data-ttu-id="f786c-125">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="f786c-125">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)
- [<span data-ttu-id="f786c-126">整合 COM 應用程式</span><span class="sxs-lookup"><span data-stu-id="f786c-126">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="f786c-127">如何：設定 COM + 服務設定</span><span class="sxs-lookup"><span data-stu-id="f786c-127">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
