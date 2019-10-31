---
title: <Directives> 元素（.NET Native）
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
ms.openlocfilehash: abe2e7221e0afb984a6178b12fabc36ea24deb35
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128463"
---
# <a name="directives-element-net-native"></a><span data-ttu-id="ce8ed-102">\<指示詞 > 元素（.NET Native）</span><span class="sxs-lookup"><span data-stu-id="ce8ed-102">\<Directives> Element (.NET Native)</span></span>
<span data-ttu-id="ce8ed-103">.NET Native 的每個執行時間指示詞檔案中的根項目。</span><span class="sxs-lookup"><span data-stu-id="ce8ed-103">The root element in every runtime directives file for .NET Native.</span></span>  
  
 `<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">` 
  
## <a name="syntax"></a><span data-ttu-id="ce8ed-104">語法</span><span class="sxs-lookup"><span data-stu-id="ce8ed-104">Syntax</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->   
</Directives>  
```  
  
## <a name="attributes"></a><span data-ttu-id="ce8ed-105">屬性</span><span class="sxs-lookup"><span data-stu-id="ce8ed-105">Attributes</span></span>  
  
|<span data-ttu-id="ce8ed-106">屬性</span><span class="sxs-lookup"><span data-stu-id="ce8ed-106">Attribute</span></span>|<span data-ttu-id="ce8ed-107">描述</span><span class="sxs-lookup"><span data-stu-id="ce8ed-107">Description</span></span>|  
|---------------|-----------------|  
|`xmlns`|<span data-ttu-id="ce8ed-108">XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="ce8ed-108">The XML namespace.</span></span> <span data-ttu-id="ce8ed-109">其值永遠是**http://schemas.microsoft.com/netfx/2013/01/metadata"** 。</span><span class="sxs-lookup"><span data-stu-id="ce8ed-109">Its value is always **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="ce8ed-110">子元素</span><span class="sxs-lookup"><span data-stu-id="ce8ed-110">Child elements</span></span>  
  
|<span data-ttu-id="ce8ed-111">項目</span><span class="sxs-lookup"><span data-stu-id="ce8ed-111">Element</span></span>|<span data-ttu-id="ce8ed-112">描述</span><span class="sxs-lookup"><span data-stu-id="ce8ed-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ce8ed-113">\<Application></span><span class="sxs-lookup"><span data-stu-id="ce8ed-113">\<Application></span></span>](application-element-net-native.md)|<span data-ttu-id="ce8ed-114">做為容器，以包含整個應用程式中，可將中繼資料用於反映的類型和類型成員。</span><span class="sxs-lookup"><span data-stu-id="ce8ed-114">Serves as a container for application-wide types and type members whose metadata is available for reflection.</span></span>|  
|[<span data-ttu-id="ce8ed-115">\<Library></span><span class="sxs-lookup"><span data-stu-id="ce8ed-115">\<Library></span></span>](library-element-net-native.md)|<span data-ttu-id="ce8ed-116">定義子類型和類型成員會在執行階段需要中繼資料的組件。</span><span class="sxs-lookup"><span data-stu-id="ce8ed-116">Defines the assembly whose child types and type members require metadata at run time.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ce8ed-117">備註</span><span class="sxs-lookup"><span data-stu-id="ce8ed-117">Remarks</span></span>  
 <span data-ttu-id="ce8ed-118">每個執行階段指示詞檔案都只能包含一個 `<Directives>` 元素。</span><span class="sxs-lookup"><span data-stu-id="ce8ed-118">Each runtime directives file can contain only one `<Directives>` element.</span></span>  
  
 <span data-ttu-id="ce8ed-119">`<Directives>` 項目可以包含零或一個 [\<Application>](application-element-net-native.md) 項目，以及零、一或多個 [\<Library>](library-element-net-native.md) 項目。</span><span class="sxs-lookup"><span data-stu-id="ce8ed-119">The `<Directives>` element can contain zero or one [\<Application>](application-element-net-native.md) element, and zero, one, or more [\<Library>](library-element-net-native.md) elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce8ed-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="ce8ed-120">See also</span></span>

- [<span data-ttu-id="ce8ed-121">執行階段指示詞 (rd.xml) 組態檔參考</span><span class="sxs-lookup"><span data-stu-id="ce8ed-121">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="ce8ed-122">執行階段指示詞項目</span><span class="sxs-lookup"><span data-stu-id="ce8ed-122">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
