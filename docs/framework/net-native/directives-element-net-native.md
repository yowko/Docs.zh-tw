---
title: "&lt;Directives&gt; 項目 (.NET Native)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4ca27422889fd33071a02c3a4b6fea0a6ba7eb0b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltdirectivesgt-element-net-native"></a><span data-ttu-id="3f9f0-102">&lt;Directives&gt; 項目 (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="3f9f0-102">&lt;Directives&gt; Element (.NET Native)</span></span>
<span data-ttu-id="3f9f0-103">[!INCLUDE[net_native](../../../includes/net-native-md.md)] 每個執行階段指示詞檔案中的根元素。</span><span class="sxs-lookup"><span data-stu-id="3f9f0-103">The root element in every runtime directives file for [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span>  
  
 <span data-ttu-id="3f9f0-104">**\<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">**</span><span class="sxs-lookup"><span data-stu-id="3f9f0-104">**\<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f9f0-105">語法</span><span class="sxs-lookup"><span data-stu-id="3f9f0-105">Syntax</span></span>  
  
```xml  
      <Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->   
</Directives>  
```  
  
## <a name="attributes"></a><span data-ttu-id="3f9f0-106">屬性</span><span class="sxs-lookup"><span data-stu-id="3f9f0-106">Attributes</span></span>  
  
|<span data-ttu-id="3f9f0-107">屬性</span><span class="sxs-lookup"><span data-stu-id="3f9f0-107">Attribute</span></span>|<span data-ttu-id="3f9f0-108">描述</span><span class="sxs-lookup"><span data-stu-id="3f9f0-108">Description</span></span>|  
|---------------|-----------------|  
|`xmlns`|<span data-ttu-id="3f9f0-109">XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="3f9f0-109">The XML namespace.</span></span> <span data-ttu-id="3f9f0-110">其值一律為 **"http://schemas.microsoft.com/netfx/2013/01/metadata"**。</span><span class="sxs-lookup"><span data-stu-id="3f9f0-110">Its value is always **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="3f9f0-111">子元素</span><span class="sxs-lookup"><span data-stu-id="3f9f0-111">Child elements</span></span>  
  
|<span data-ttu-id="3f9f0-112">項目</span><span class="sxs-lookup"><span data-stu-id="3f9f0-112">Element</span></span>|<span data-ttu-id="3f9f0-113">描述</span><span class="sxs-lookup"><span data-stu-id="3f9f0-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3f9f0-114">\<Application></span><span class="sxs-lookup"><span data-stu-id="3f9f0-114">\<Application></span></span>](../../../docs/framework/net-native/application-element-net-native.md)|<span data-ttu-id="3f9f0-115">做為容器，以包含整個應用程式中，可將中繼資料用於反映的類型和類型成員。</span><span class="sxs-lookup"><span data-stu-id="3f9f0-115">Serves as a container for application-wide types and type members whose metadata is available for reflection.</span></span>|  
|[<span data-ttu-id="3f9f0-116">\<程式庫></span><span class="sxs-lookup"><span data-stu-id="3f9f0-116">\<Library></span></span>](../../../docs/framework/net-native/library-element-net-native.md)|<span data-ttu-id="3f9f0-117">定義子類型和類型成員會在執行階段需要中繼資料的組件。</span><span class="sxs-lookup"><span data-stu-id="3f9f0-117">Defines the assembly whose child types and type members require metadata at run time.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f9f0-118">備註</span><span class="sxs-lookup"><span data-stu-id="3f9f0-118">Remarks</span></span>  
 <span data-ttu-id="3f9f0-119">每個執行階段指示詞檔案都只能包含一個 `<Directives>` 元素。</span><span class="sxs-lookup"><span data-stu-id="3f9f0-119">Each runtime directives file can contain only one `<Directives>` element.</span></span>  
  
 <span data-ttu-id="3f9f0-120">`<Directives>` 項目可以包含零或一個 [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) 項目，以及零、一或多個 [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) 項目。</span><span class="sxs-lookup"><span data-stu-id="3f9f0-120">The `<Directives>` element can contain zero or one [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) element, and zero, one, or more [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f9f0-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="3f9f0-121">See Also</span></span>  
 [<span data-ttu-id="3f9f0-122">執行階段指示詞 (rd.xml) 組態檔參考</span><span class="sxs-lookup"><span data-stu-id="3f9f0-122">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="3f9f0-123">執行階段指示詞項目</span><span class="sxs-lookup"><span data-stu-id="3f9f0-123">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
