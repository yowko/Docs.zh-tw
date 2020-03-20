---
title: <Directives>元素（.NET 本機）
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
ms.openlocfilehash: 49c1aaf005b80a6c1c1fa382eebc2cb0dbfa4be7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181049"
---
# <a name="directives-element-net-native"></a><span data-ttu-id="85823-102">\<指令>元素（.NET 本機）</span><span class="sxs-lookup"><span data-stu-id="85823-102">\<Directives> Element (.NET Native)</span></span>
<span data-ttu-id="85823-103">每個運行時指令檔中的根項目為 .NET 本機。</span><span class="sxs-lookup"><span data-stu-id="85823-103">The root element in every runtime directives file for .NET Native.</span></span>  
  
 `<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">`
  
## <a name="syntax"></a><span data-ttu-id="85823-104">語法</span><span class="sxs-lookup"><span data-stu-id="85823-104">Syntax</span></span>  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->
</Directives>  
```  
  
## <a name="attributes"></a><span data-ttu-id="85823-105">屬性</span><span class="sxs-lookup"><span data-stu-id="85823-105">Attributes</span></span>  
  
|<span data-ttu-id="85823-106">屬性</span><span class="sxs-lookup"><span data-stu-id="85823-106">Attribute</span></span>|<span data-ttu-id="85823-107">描述</span><span class="sxs-lookup"><span data-stu-id="85823-107">Description</span></span>|  
|---------------|-----------------|  
|`xmlns`|<span data-ttu-id="85823-108">XML 命名空間。</span><span class="sxs-lookup"><span data-stu-id="85823-108">The XML namespace.</span></span> <span data-ttu-id="85823-109">它的價值總是 \*\*""。http://schemas.microsoft.com/netfx/2013/01/metadata \*\*</span><span class="sxs-lookup"><span data-stu-id="85823-109">Its value is always **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.</span></span>|  
  
## <a name="child-elements"></a><span data-ttu-id="85823-110">子元素</span><span class="sxs-lookup"><span data-stu-id="85823-110">Child elements</span></span>  
  
|<span data-ttu-id="85823-111">元素</span><span class="sxs-lookup"><span data-stu-id="85823-111">Element</span></span>|<span data-ttu-id="85823-112">描述</span><span class="sxs-lookup"><span data-stu-id="85823-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="85823-113">\<應用></span><span class="sxs-lookup"><span data-stu-id="85823-113">\<Application></span></span>](application-element-net-native.md)|<span data-ttu-id="85823-114">做為容器，以包含整個應用程式中，可將中繼資料用於反映的類型和類型成員。</span><span class="sxs-lookup"><span data-stu-id="85823-114">Serves as a container for application-wide types and type members whose metadata is available for reflection.</span></span>|  
|[<span data-ttu-id="85823-115">\<圖書館></span><span class="sxs-lookup"><span data-stu-id="85823-115">\<Library></span></span>](library-element-net-native.md)|<span data-ttu-id="85823-116">定義子類型和類型成員會在執行階段需要中繼資料的組件。</span><span class="sxs-lookup"><span data-stu-id="85823-116">Defines the assembly whose child types and type members require metadata at run time.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85823-117">備註</span><span class="sxs-lookup"><span data-stu-id="85823-117">Remarks</span></span>  
 <span data-ttu-id="85823-118">每個執行階段指示詞檔案都只能包含一個 `<Directives>` 元素。</span><span class="sxs-lookup"><span data-stu-id="85823-118">Each runtime directives file can contain only one `<Directives>` element.</span></span>  
  
 <span data-ttu-id="85823-119">該`<Directives>`元素可以包含零或一個[\<應用程式>](application-element-net-native.md)元素，以及零、一個或多個[\<庫>](library-element-net-native.md)元素。</span><span class="sxs-lookup"><span data-stu-id="85823-119">The `<Directives>` element can contain zero or one [\<Application>](application-element-net-native.md) element, and zero, one, or more [\<Library>](library-element-net-native.md) elements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85823-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85823-120">See also</span></span>

- [<span data-ttu-id="85823-121">執行階段指示詞 (rd.xml) 組態檔參考</span><span class="sxs-lookup"><span data-stu-id="85823-121">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="85823-122">執行階段指示詞項目</span><span class="sxs-lookup"><span data-stu-id="85823-122">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
