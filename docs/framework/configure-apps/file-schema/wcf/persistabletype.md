---
title: <persistableType>
ms.date: 03/30/2017
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
ms.openlocfilehash: 328caaefe0cc24da45b460cab0a672dc8a6ccce1
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855077"
---
# <a name="persistabletype"></a><span data-ttu-id="5528f-101">\<persistableType></span><span class="sxs-lookup"><span data-stu-id="5528f-101">\<persistableType></span></span>
<span data-ttu-id="5528f-102">指定所有永久性型別。</span><span class="sxs-lookup"><span data-stu-id="5528f-102">Specifies all the persistable types.</span></span>  
  
<span data-ttu-id="5528f-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5528f-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5528f-104">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="5528f-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="5528f-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comContracts >** ](comcontracts.md)</span><span class="sxs-lookup"><span data-stu-id="5528f-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)</span></span>\
<span data-ttu-id="5528f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comContract >** ](comcontract.md)</span><span class="sxs-lookup"><span data-stu-id="5528f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContract>**](comcontract.md)</span></span>\
<span data-ttu-id="5528f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<persistableTypes >** ](persistabletypes.md)</span><span class="sxs-lookup"><span data-stu-id="5528f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<persistableTypes>**](persistabletypes.md)</span></span>\
<span data-ttu-id="5528f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<persistableType >**</span><span class="sxs-lookup"><span data-stu-id="5528f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<persistableType>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5528f-109">語法</span><span class="sxs-lookup"><span data-stu-id="5528f-109">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="5528f-110">類型</span><span class="sxs-lookup"><span data-stu-id="5528f-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5528f-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5528f-111">Attributes and Elements</span></span>  
 <span data-ttu-id="5528f-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="5528f-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5528f-113">屬性</span><span class="sxs-lookup"><span data-stu-id="5528f-113">Attributes</span></span>  
  
|<span data-ttu-id="5528f-114">屬性</span><span class="sxs-lookup"><span data-stu-id="5528f-114">Attribute</span></span>|<span data-ttu-id="5528f-115">說明</span><span class="sxs-lookup"><span data-stu-id="5528f-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5528f-116">id</span><span class="sxs-lookup"><span data-stu-id="5528f-116">id</span></span>|<span data-ttu-id="5528f-117">必要屬性，其中包含的字串可指定永久性類別的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="5528f-117">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="5528f-118">NAME</span><span class="sxs-lookup"><span data-stu-id="5528f-118">name</span></span>|<span data-ttu-id="5528f-119">選擇性屬性，其中包含的字串可指定永久性類別的名稱。</span><span class="sxs-lookup"><span data-stu-id="5528f-119">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5528f-120">子元素</span><span class="sxs-lookup"><span data-stu-id="5528f-120">Child Elements</span></span>  
 <span data-ttu-id="5528f-121">None</span><span class="sxs-lookup"><span data-stu-id="5528f-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5528f-122">父項目</span><span class="sxs-lookup"><span data-stu-id="5528f-122">Parent Elements</span></span>  
  
|<span data-ttu-id="5528f-123">項目</span><span class="sxs-lookup"><span data-stu-id="5528f-123">Element</span></span>|<span data-ttu-id="5528f-124">描述</span><span class="sxs-lookup"><span data-stu-id="5528f-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5528f-125">\<persistableTypes></span><span class="sxs-lookup"><span data-stu-id="5528f-125">\<persistableTypes></span></span>](persistabletypes.md)|<span data-ttu-id="5528f-126">`persistableType` 項目的集合。</span><span class="sxs-lookup"><span data-stu-id="5528f-126">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5528f-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5528f-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>
- [<span data-ttu-id="5528f-128">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="5528f-128">\<comContracts></span></span>](comcontracts.md)
- [<span data-ttu-id="5528f-129">整合 COM 應用程式</span><span class="sxs-lookup"><span data-stu-id="5528f-129">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="5528f-130">如何：設定 COM + 服務設定</span><span class="sxs-lookup"><span data-stu-id="5528f-130">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
