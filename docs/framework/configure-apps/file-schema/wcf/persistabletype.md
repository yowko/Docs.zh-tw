---
title: <persistableType>
ms.date: 03/30/2017
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
ms.openlocfilehash: 328caaefe0cc24da45b460cab0a672dc8a6ccce1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855077"
---
# \<persistableType>
<span data-ttu-id="1f7c8-101">指定所有永久性型別。</span><span class="sxs-lookup"><span data-stu-id="1f7c8-101">Specifies all the persistable types.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContract>**](comcontract.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<persistableTypes>**](persistabletypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<persistableType>**  
  
## <a name="syntax"></a><span data-ttu-id="1f7c8-102">語法</span><span class="sxs-lookup"><span data-stu-id="1f7c8-102">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="1f7c8-103">類型</span><span class="sxs-lookup"><span data-stu-id="1f7c8-103">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1f7c8-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1f7c8-104">Attributes and Elements</span></span>  
 <span data-ttu-id="1f7c8-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="1f7c8-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1f7c8-106">屬性</span><span class="sxs-lookup"><span data-stu-id="1f7c8-106">Attributes</span></span>  
  
|<span data-ttu-id="1f7c8-107">屬性</span><span class="sxs-lookup"><span data-stu-id="1f7c8-107">Attribute</span></span>|<span data-ttu-id="1f7c8-108">描述</span><span class="sxs-lookup"><span data-stu-id="1f7c8-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1f7c8-109">id</span><span class="sxs-lookup"><span data-stu-id="1f7c8-109">id</span></span>|<span data-ttu-id="1f7c8-110">必要屬性，其中包含的字串可指定永久性類別的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="1f7c8-110">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="1f7c8-111">NAME</span><span class="sxs-lookup"><span data-stu-id="1f7c8-111">name</span></span>|<span data-ttu-id="1f7c8-112">選擇性屬性，其中包含的字串可指定永久性類別的名稱。</span><span class="sxs-lookup"><span data-stu-id="1f7c8-112">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1f7c8-113">子元素</span><span class="sxs-lookup"><span data-stu-id="1f7c8-113">Child Elements</span></span>  
 <span data-ttu-id="1f7c8-114">無</span><span class="sxs-lookup"><span data-stu-id="1f7c8-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1f7c8-115">父項目</span><span class="sxs-lookup"><span data-stu-id="1f7c8-115">Parent Elements</span></span>  
  
|<span data-ttu-id="1f7c8-116">元素</span><span class="sxs-lookup"><span data-stu-id="1f7c8-116">Element</span></span>|<span data-ttu-id="1f7c8-117">描述</span><span class="sxs-lookup"><span data-stu-id="1f7c8-117">Description</span></span>|  
|-------------|-----------------|  
|[\<persistableTypes>](persistabletypes.md)|<span data-ttu-id="1f7c8-118">`persistableType` 項目的集合。</span><span class="sxs-lookup"><span data-stu-id="1f7c8-118">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1f7c8-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f7c8-119">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>
- [\<comContracts>](comcontracts.md)
- [<span data-ttu-id="1f7c8-120">與 COM + 應用程式整合</span><span class="sxs-lookup"><span data-stu-id="1f7c8-120">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="1f7c8-121">HOW TO：設定 COM+ 服務設定</span><span class="sxs-lookup"><span data-stu-id="1f7c8-121">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
