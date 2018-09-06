---
title: '&lt;Directives&gt; 項目 (.NET Native)'
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8921d2841f9a7b4228ae3b8735d7047453f71bcb
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43800189"
---
# <a name="ltdirectivesgt-element-net-native"></a><span data-ttu-id="208d4-102">&lt;Directives&gt; 項目 (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="208d4-102">&lt;Directives&gt; Element (.NET Native)</span></span>
<span data-ttu-id="208d4-103">針對.NET 原生的每個執行階段指示詞檔案中的根項目。</span><span class="sxs-lookup"><span data-stu-id="208d4-103">The root element in every runtime directives file for .NET Native.</span></span>  
  
 `<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">` 
  
## <a name="syntax"></a><span data-ttu-id="208d4-104">語法</span><span class="sxs-lookup"><span data-stu-id="208d4-104">Syntax</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->   
</Directives>  
```  
  
## <a name="attributes"></a><span data-ttu-id="208d4-105">屬性</span><span class="sxs-lookup"><span data-stu-id="208d4-105">Attributes</span></span>  
  
|<span data-ttu-id="208d4-106">屬性</span><span class="sxs-lookup"><span data-stu-id="208d4-106">Attribute</span></span>|<span data-ttu-id="208d4-107">描述</span><span class="sxs-lookup"><span data-stu-id="208d4-107">Description</span></span>|  
|---------------|-----------------|  
|`xmlns`|<span data-ttu-id="208d4-108">XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="208d4-108">The XML namespace.</span></span> <span data-ttu-id="208d4-109">其值永遠是 **」 http://schemas.microsoft.com/netfx/2013/01/metadata"**。</span><span class="sxs-lookup"><span data-stu-id="208d4-109">Its value is always **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="208d4-110">子元素</span><span class="sxs-lookup"><span data-stu-id="208d4-110">Child elements</span></span>  
  
|<span data-ttu-id="208d4-111">項目</span><span class="sxs-lookup"><span data-stu-id="208d4-111">Element</span></span>|<span data-ttu-id="208d4-112">描述</span><span class="sxs-lookup"><span data-stu-id="208d4-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="208d4-113">\<Application></span><span class="sxs-lookup"><span data-stu-id="208d4-113">\<Application></span></span>](../../../docs/framework/net-native/application-element-net-native.md)|<span data-ttu-id="208d4-114">做為容器，以包含整個應用程式中，可將中繼資料用於反映的類型和類型成員。</span><span class="sxs-lookup"><span data-stu-id="208d4-114">Serves as a container for application-wide types and type members whose metadata is available for reflection.</span></span>|  
|[<span data-ttu-id="208d4-115">\<程式庫></span><span class="sxs-lookup"><span data-stu-id="208d4-115">\<Library></span></span>](../../../docs/framework/net-native/library-element-net-native.md)|<span data-ttu-id="208d4-116">定義子類型和類型成員會在執行階段需要中繼資料的組件。</span><span class="sxs-lookup"><span data-stu-id="208d4-116">Defines the assembly whose child types and type members require metadata at run time.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="208d4-117">備註</span><span class="sxs-lookup"><span data-stu-id="208d4-117">Remarks</span></span>  
 <span data-ttu-id="208d4-118">每個執行階段指示詞檔案都只能包含一個 `<Directives>` 元素。</span><span class="sxs-lookup"><span data-stu-id="208d4-118">Each runtime directives file can contain only one `<Directives>` element.</span></span>  
  
 <span data-ttu-id="208d4-119">`<Directives>` 項目可以包含零或一個 [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) 項目，以及零、一或多個 [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) 項目。</span><span class="sxs-lookup"><span data-stu-id="208d4-119">The `<Directives>` element can contain zero or one [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) element, and zero, one, or more [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="208d4-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="208d4-120">See Also</span></span>  
 [<span data-ttu-id="208d4-121">執行階段指示詞 (rd.xml) 組態檔參考</span><span class="sxs-lookup"><span data-stu-id="208d4-121">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="208d4-122">執行階段指示詞項目</span><span class="sxs-lookup"><span data-stu-id="208d4-122">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
