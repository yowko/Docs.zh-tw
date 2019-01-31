---
title: <Directives> 項目 (.NET Native)
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 14eac92a2f3e5ed5d93f4e608f7d42b13849036e
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55254167"
---
# <a name="directives-element-net-native"></a><span data-ttu-id="ebf46-102">\<指示詞 > 項目 (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="ebf46-102">\<Directives> Element (.NET Native)</span></span>
<span data-ttu-id="ebf46-103">針對.NET 原生的每個執行階段指示詞檔案中的根項目。</span><span class="sxs-lookup"><span data-stu-id="ebf46-103">The root element in every runtime directives file for .NET Native.</span></span>  
  
 `<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">` 
  
## <a name="syntax"></a><span data-ttu-id="ebf46-104">語法</span><span class="sxs-lookup"><span data-stu-id="ebf46-104">Syntax</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->   
</Directives>  
```  
  
## <a name="attributes"></a><span data-ttu-id="ebf46-105">屬性</span><span class="sxs-lookup"><span data-stu-id="ebf46-105">Attributes</span></span>  
  
|<span data-ttu-id="ebf46-106">屬性</span><span class="sxs-lookup"><span data-stu-id="ebf46-106">Attribute</span></span>|<span data-ttu-id="ebf46-107">描述</span><span class="sxs-lookup"><span data-stu-id="ebf46-107">Description</span></span>|  
|---------------|-----------------|  
|`xmlns`|<span data-ttu-id="ebf46-108">XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="ebf46-108">The XML namespace.</span></span> <span data-ttu-id="ebf46-109">其值永遠是 **」 http://schemas.microsoft.com/netfx/2013/01/metadata"**。</span><span class="sxs-lookup"><span data-stu-id="ebf46-109">Its value is always **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="ebf46-110">子元素</span><span class="sxs-lookup"><span data-stu-id="ebf46-110">Child elements</span></span>  
  
|<span data-ttu-id="ebf46-111">項目</span><span class="sxs-lookup"><span data-stu-id="ebf46-111">Element</span></span>|<span data-ttu-id="ebf46-112">描述</span><span class="sxs-lookup"><span data-stu-id="ebf46-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ebf46-113">\<Application></span><span class="sxs-lookup"><span data-stu-id="ebf46-113">\<Application></span></span>](../../../docs/framework/net-native/application-element-net-native.md)|<span data-ttu-id="ebf46-114">做為容器，以包含整個應用程式中，可將中繼資料用於反映的類型和類型成員。</span><span class="sxs-lookup"><span data-stu-id="ebf46-114">Serves as a container for application-wide types and type members whose metadata is available for reflection.</span></span>|  
|[<span data-ttu-id="ebf46-115">\<程式庫></span><span class="sxs-lookup"><span data-stu-id="ebf46-115">\<Library></span></span>](../../../docs/framework/net-native/library-element-net-native.md)|<span data-ttu-id="ebf46-116">定義子類型和類型成員會在執行階段需要中繼資料的組件。</span><span class="sxs-lookup"><span data-stu-id="ebf46-116">Defines the assembly whose child types and type members require metadata at run time.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ebf46-117">備註</span><span class="sxs-lookup"><span data-stu-id="ebf46-117">Remarks</span></span>  
 <span data-ttu-id="ebf46-118">每個執行階段指示詞檔案都只能包含一個 `<Directives>` 元素。</span><span class="sxs-lookup"><span data-stu-id="ebf46-118">Each runtime directives file can contain only one `<Directives>` element.</span></span>  
  
 <span data-ttu-id="ebf46-119">`<Directives>` 項目可以包含零或一個 [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) 項目，以及零、一或多個 [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) 項目。</span><span class="sxs-lookup"><span data-stu-id="ebf46-119">The `<Directives>` element can contain zero or one [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) element, and zero, one, or more [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebf46-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ebf46-120">See also</span></span>
- [<span data-ttu-id="ebf46-121">執行階段指示詞 (rd.xml) 組態檔參考</span><span class="sxs-lookup"><span data-stu-id="ebf46-121">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="ebf46-122">執行階段指示詞項目</span><span class="sxs-lookup"><span data-stu-id="ebf46-122">Runtime Directive Elements</span></span>](../../../docs/framework/net-native/runtime-directive-elements.md)
