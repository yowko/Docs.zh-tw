---
title: <disableCommitThreadStack> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCommitThreadStack
- http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCommitThreadStack
helpviewer_keywords:
- <disableCommitThreadStack> element
- disableCommitThreadStack element
ms.assetid: 3559d46a-7640-4c72-9a11-7e980768929e
ms.openlocfilehash: f717f57fe8670b126ed1468713a2114aaa772762
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198986"
---
# <a name="disablecommitthreadstack-element"></a><span data-ttu-id="447b4-102">\<disableCommitThreadStack> 項目</span><span class="sxs-lookup"><span data-stu-id="447b4-102">\<disableCommitThreadStack> Element</span></span>

<span data-ttu-id="447b4-103">指定是否在執行緒啟動時認可完整執行緒堆疊。</span><span class="sxs-lookup"><span data-stu-id="447b4-103">Specifies whether the full thread stack is committed when a thread is started.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<disableCommitThreadStack>**  
  
## <a name="syntax"></a><span data-ttu-id="447b4-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="447b4-104">Syntax</span></span>  
  
```xml  
<disableCommitThreadStack enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="447b4-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="447b4-105">Attributes and Elements</span></span>  

 <span data-ttu-id="447b4-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="447b4-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="447b4-107">屬性</span><span class="sxs-lookup"><span data-stu-id="447b4-107">Attributes</span></span>  
  
|<span data-ttu-id="447b4-108">屬性</span><span class="sxs-lookup"><span data-stu-id="447b4-108">Attribute</span></span>|<span data-ttu-id="447b4-109">描述</span><span class="sxs-lookup"><span data-stu-id="447b4-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="447b4-110">已啟用</span><span class="sxs-lookup"><span data-stu-id="447b4-110">enabled</span></span>|<span data-ttu-id="447b4-111">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="447b4-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="447b4-112">指定是否停用在執行緒啟動時認可完整執行緒堆疊 (預設行為)。</span><span class="sxs-lookup"><span data-stu-id="447b4-112">Specifies whether committing the full thread stack on thread startup (the default behavior) is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="447b4-113">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="447b4-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="447b4-114">值</span><span class="sxs-lookup"><span data-stu-id="447b4-114">Value</span></span>|<span data-ttu-id="447b4-115">描述</span><span class="sxs-lookup"><span data-stu-id="447b4-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="447b4-116">0</span><span class="sxs-lookup"><span data-stu-id="447b4-116">0</span></span>|<span data-ttu-id="447b4-117">不停用 Common Language Runtime 的預設行為，也就是在執行緒啟動時認可完整執行緒堆疊。</span><span class="sxs-lookup"><span data-stu-id="447b4-117">Do not disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
|<span data-ttu-id="447b4-118">1</span><span class="sxs-lookup"><span data-stu-id="447b4-118">1</span></span>|<span data-ttu-id="447b4-119">不停用 Common Language Runtime 的預設行為，也就是在執行緒啟動時認可完整執行緒堆疊。</span><span class="sxs-lookup"><span data-stu-id="447b4-119">Disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="447b4-120">子元素</span><span class="sxs-lookup"><span data-stu-id="447b4-120">Child Elements</span></span>  

 <span data-ttu-id="447b4-121">無。</span><span class="sxs-lookup"><span data-stu-id="447b4-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="447b4-122">父項目</span><span class="sxs-lookup"><span data-stu-id="447b4-122">Parent Elements</span></span>  
  
|<span data-ttu-id="447b4-123">項目</span><span class="sxs-lookup"><span data-stu-id="447b4-123">Element</span></span>|<span data-ttu-id="447b4-124">描述</span><span class="sxs-lookup"><span data-stu-id="447b4-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="447b4-125">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="447b4-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="447b4-126">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="447b4-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="447b4-127">備註</span><span class="sxs-lookup"><span data-stu-id="447b4-127">Remarks</span></span>  

 <span data-ttu-id="447b4-128">Common Language Runtime 的預設行為是在執行緒啟動時認可完整執行緒堆疊。</span><span class="sxs-lookup"><span data-stu-id="447b4-128">The default behavior of the common language runtime is to commit the full thread stack when a thread is started.</span></span> <span data-ttu-id="447b4-129">如果必須在具有有限記憶體的伺服器上建立大量執行緒，而且大部分的執行緒都會使用極小的堆疊空間，則 Common Language Runtime 不要在執行緒啟動時立即認可完整執行緒堆疊，伺服器的效能可能會較好。</span><span class="sxs-lookup"><span data-stu-id="447b4-129">If a large number of threads must be created on a server that has limited memory, and most of those threads will use very little stack space, the server might perform better if the common language runtime does not commit the full thread stack immediately when a thread is started.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="447b4-130">未受管理的主機可以在 `STARTUP_DISABLE_COMMITTHREADSTACK` STARTUP_FLAGS [列舉中使用](../../../unmanaged-api/hosting/startup-flags-enumeration.md) 啟動旗標，來達到相同的結果。</span><span class="sxs-lookup"><span data-stu-id="447b4-130">Unmanaged hosts can use the `STARTUP_DISABLE_COMMITTHREADSTACK` startup flag in the [STARTUP_FLAGS](../../../unmanaged-api/hosting/startup-flags-enumeration.md) enumeration to accomplish the same result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="447b4-131">範例</span><span class="sxs-lookup"><span data-stu-id="447b4-131">Example</span></span>  

 <span data-ttu-id="447b4-132">下列範例示範如何停用 Common Language Runtime 的預設行為，也就是在執行緒啟動時認可完整執行緒堆疊。</span><span class="sxs-lookup"><span data-stu-id="447b4-132">The following example shows how to disable the default behavior of the common language runtime, which is to commit the full thread stack on thread startup.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCommitThreadStack enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="447b4-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="447b4-133">See also</span></span>

- [<span data-ttu-id="447b4-134">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="447b4-134">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="447b4-135">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="447b4-135">Configuration File Schema</span></span>](../index.md)
