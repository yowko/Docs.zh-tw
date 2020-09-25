---
title: <persistableType>
ms.date: 03/30/2017
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
ms.openlocfilehash: 6425b21fe50865beb7bb2876ea478b415fbe3944
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181514"
---
# \<persistableType>

<span data-ttu-id="435c0-101">指定所有永久性型別。</span><span class="sxs-lookup"><span data-stu-id="435c0-101">Specifies all the persistable types.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContract>**](comcontract.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<persistableTypes>**](persistabletypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<persistableType>**  
  
## <a name="syntax"></a><span data-ttu-id="435c0-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="435c0-102">Syntax</span></span>  
  
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
  
## <a name="type"></a><span data-ttu-id="435c0-103">類型</span><span class="sxs-lookup"><span data-stu-id="435c0-103">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="435c0-104">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="435c0-104">Attributes and Elements</span></span>  

 <span data-ttu-id="435c0-105">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="435c0-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="435c0-106">屬性</span><span class="sxs-lookup"><span data-stu-id="435c0-106">Attributes</span></span>  
  
|<span data-ttu-id="435c0-107">屬性</span><span class="sxs-lookup"><span data-stu-id="435c0-107">Attribute</span></span>|<span data-ttu-id="435c0-108">描述</span><span class="sxs-lookup"><span data-stu-id="435c0-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="435c0-109">id</span><span class="sxs-lookup"><span data-stu-id="435c0-109">id</span></span>|<span data-ttu-id="435c0-110">必要屬性，其中包含的字串可指定永久性類別的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="435c0-110">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="435c0-111">NAME</span><span class="sxs-lookup"><span data-stu-id="435c0-111">name</span></span>|<span data-ttu-id="435c0-112">選擇性屬性，其中包含的字串可指定永久性類別的名稱。</span><span class="sxs-lookup"><span data-stu-id="435c0-112">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="435c0-113">子元素</span><span class="sxs-lookup"><span data-stu-id="435c0-113">Child Elements</span></span>  

 <span data-ttu-id="435c0-114">無</span><span class="sxs-lookup"><span data-stu-id="435c0-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="435c0-115">父項目</span><span class="sxs-lookup"><span data-stu-id="435c0-115">Parent Elements</span></span>  
  
|<span data-ttu-id="435c0-116">項目</span><span class="sxs-lookup"><span data-stu-id="435c0-116">Element</span></span>|<span data-ttu-id="435c0-117">描述</span><span class="sxs-lookup"><span data-stu-id="435c0-117">Description</span></span>|  
|-------------|-----------------|  
|[\<persistableTypes>](persistabletypes.md)|<span data-ttu-id="435c0-118">`persistableType` 項目的集合。</span><span class="sxs-lookup"><span data-stu-id="435c0-118">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="435c0-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="435c0-119">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>
- [\<comContracts>](comcontracts.md)
- [<span data-ttu-id="435c0-120">與 COM + 應用程式整合</span><span class="sxs-lookup"><span data-stu-id="435c0-120">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="435c0-121">作法：設定 COM+ 服務設定</span><span class="sxs-lookup"><span data-stu-id="435c0-121">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
