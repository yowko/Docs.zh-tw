---
title: <Directives>元素（.NET Native）
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
ms.openlocfilehash: 0c6ebb8954e80f3f6dc6733f0e9d76094477689b
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202376"
---
# <a name="directives-element-net-native"></a><span data-ttu-id="778d9-102">\<Directives>元素（.NET Native）</span><span class="sxs-lookup"><span data-stu-id="778d9-102">\<Directives> Element (.NET Native)</span></span>
<span data-ttu-id="778d9-103">.NET Native 的每個執行時間指示詞檔案中的根項目。</span><span class="sxs-lookup"><span data-stu-id="778d9-103">The root element in every runtime directives file for .NET Native.</span></span>  
  
 `<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">`
  
## <a name="syntax"></a><span data-ttu-id="778d9-104">語法</span><span class="sxs-lookup"><span data-stu-id="778d9-104">Syntax</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->
</Directives>  
```  
  
## <a name="attributes"></a><span data-ttu-id="778d9-105">屬性</span><span class="sxs-lookup"><span data-stu-id="778d9-105">Attributes</span></span>  
  
|<span data-ttu-id="778d9-106">屬性</span><span class="sxs-lookup"><span data-stu-id="778d9-106">Attribute</span></span>|<span data-ttu-id="778d9-107">描述</span><span class="sxs-lookup"><span data-stu-id="778d9-107">Description</span></span>|  
|---------------|-----------------|  
|`xmlns`|<span data-ttu-id="778d9-108">XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="778d9-108">The XML namespace.</span></span> <span data-ttu-id="778d9-109">其值一律為 `http://schemas.microsoft.com/netfx/2013/01/metadata` 。</span><span class="sxs-lookup"><span data-stu-id="778d9-109">Its value is always `http://schemas.microsoft.com/netfx/2013/01/metadata`.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="778d9-110">子元素</span><span class="sxs-lookup"><span data-stu-id="778d9-110">Child elements</span></span>  
  
|<span data-ttu-id="778d9-111">元素</span><span class="sxs-lookup"><span data-stu-id="778d9-111">Element</span></span>|<span data-ttu-id="778d9-112">描述</span><span class="sxs-lookup"><span data-stu-id="778d9-112">Description</span></span>|  
|-------------|-----------------|  
|[\<Application>](application-element-net-native.md)|<span data-ttu-id="778d9-113">做為容器，以包含整個應用程式中，可將中繼資料用於反映的類型和類型成員。</span><span class="sxs-lookup"><span data-stu-id="778d9-113">Serves as a container for application-wide types and type members whose metadata is available for reflection.</span></span>|  
|[\<Library>](library-element-net-native.md)|<span data-ttu-id="778d9-114">定義子類型和類型成員會在執行階段需要中繼資料的組件。</span><span class="sxs-lookup"><span data-stu-id="778d9-114">Defines the assembly whose child types and type members require metadata at run time.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="778d9-115">備註</span><span class="sxs-lookup"><span data-stu-id="778d9-115">Remarks</span></span>  
 <span data-ttu-id="778d9-116">每個執行階段指示詞檔案都只能包含一個 `<Directives>` 元素。</span><span class="sxs-lookup"><span data-stu-id="778d9-116">Each runtime directives file can contain only one `<Directives>` element.</span></span>  
  
 <span data-ttu-id="778d9-117">`<Directives>`元素可以包含零個或一個專案 [\<Application>](application-element-net-native.md) ，以及零個、一個或多個 [\<Library>](library-element-net-native.md) 元素。</span><span class="sxs-lookup"><span data-stu-id="778d9-117">The `<Directives>` element can contain zero or one [\<Application>](application-element-net-native.md) element, and zero, one, or more [\<Library>](library-element-net-native.md) elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="778d9-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="778d9-118">See also</span></span>

- [<span data-ttu-id="778d9-119">執行階段指示詞 (rd.xml) 組態檔參考</span><span class="sxs-lookup"><span data-stu-id="778d9-119">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="778d9-120">執行階段指示詞項目</span><span class="sxs-lookup"><span data-stu-id="778d9-120">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
