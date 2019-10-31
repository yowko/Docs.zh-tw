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
ms.openlocfilehash: 8aefb8a20d6a95c5b8062d0c03dcb28a3557ca3d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73117466"
---
# <a name="disablecommitthreadstack-element"></a><span data-ttu-id="3ce45-102">\<disableCommitThreadStack > 元素</span><span class="sxs-lookup"><span data-stu-id="3ce45-102">\<disableCommitThreadStack> Element</span></span>
<span data-ttu-id="3ce45-103">指定是否在執行緒啟動時認可完整執行緒堆疊。</span><span class="sxs-lookup"><span data-stu-id="3ce45-103">Specifies whether the full thread stack is committed when a thread is started.</span></span>  
  
<span data-ttu-id="3ce45-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3ce45-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3ce45-105">&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="3ce45-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="3ce45-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<disableCommitThreadStack >**</span><span class="sxs-lookup"><span data-stu-id="3ce45-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<disableCommitThreadStack>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ce45-107">語法</span><span class="sxs-lookup"><span data-stu-id="3ce45-107">Syntax</span></span>  
  
```xml  
<disableCommitThreadStack enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3ce45-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3ce45-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3ce45-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="3ce45-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3ce45-110">屬性</span><span class="sxs-lookup"><span data-stu-id="3ce45-110">Attributes</span></span>  
  
|<span data-ttu-id="3ce45-111">屬性</span><span class="sxs-lookup"><span data-stu-id="3ce45-111">Attribute</span></span>|<span data-ttu-id="3ce45-112">描述</span><span class="sxs-lookup"><span data-stu-id="3ce45-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3ce45-113">enabled</span><span class="sxs-lookup"><span data-stu-id="3ce45-113">enabled</span></span>|<span data-ttu-id="3ce45-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="3ce45-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="3ce45-115">指定是否停用在執行緒啟動時認可完整執行緒堆疊 (預設行為)。</span><span class="sxs-lookup"><span data-stu-id="3ce45-115">Specifies whether committing the full thread stack on thread startup (the default behavior) is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="3ce45-116">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="3ce45-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="3ce45-117">值</span><span class="sxs-lookup"><span data-stu-id="3ce45-117">Value</span></span>|<span data-ttu-id="3ce45-118">描述</span><span class="sxs-lookup"><span data-stu-id="3ce45-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3ce45-119">0</span><span class="sxs-lookup"><span data-stu-id="3ce45-119">0</span></span>|<span data-ttu-id="3ce45-120">不停用 Common Language Runtime 的預設行為，也就是在執行緒啟動時認可完整執行緒堆疊。</span><span class="sxs-lookup"><span data-stu-id="3ce45-120">Do not disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
|<span data-ttu-id="3ce45-121">1</span><span class="sxs-lookup"><span data-stu-id="3ce45-121">1</span></span>|<span data-ttu-id="3ce45-122">不停用 Common Language Runtime 的預設行為，也就是在執行緒啟動時認可完整執行緒堆疊。</span><span class="sxs-lookup"><span data-stu-id="3ce45-122">Disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3ce45-123">子項目</span><span class="sxs-lookup"><span data-stu-id="3ce45-123">Child Elements</span></span>  
 <span data-ttu-id="3ce45-124">無。</span><span class="sxs-lookup"><span data-stu-id="3ce45-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3ce45-125">父項目</span><span class="sxs-lookup"><span data-stu-id="3ce45-125">Parent Elements</span></span>  
  
|<span data-ttu-id="3ce45-126">項目</span><span class="sxs-lookup"><span data-stu-id="3ce45-126">Element</span></span>|<span data-ttu-id="3ce45-127">描述</span><span class="sxs-lookup"><span data-stu-id="3ce45-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3ce45-128">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="3ce45-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="3ce45-129">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="3ce45-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ce45-130">備註</span><span class="sxs-lookup"><span data-stu-id="3ce45-130">Remarks</span></span>  
 <span data-ttu-id="3ce45-131">Common Language Runtime 的預設行為是在執行緒啟動時認可完整執行緒堆疊。</span><span class="sxs-lookup"><span data-stu-id="3ce45-131">The default behavior of the common language runtime is to commit the full thread stack when a thread is started.</span></span> <span data-ttu-id="3ce45-132">如果必須在具有有限記憶體的伺服器上建立大量執行緒，而且大部分的執行緒都會使用極小的堆疊空間，則 Common Language Runtime 不要在執行緒啟動時立即認可完整執行緒堆疊，伺服器的效能可能會較好。</span><span class="sxs-lookup"><span data-stu-id="3ce45-132">If a large number of threads must be created on a server that has limited memory, and most of those threads will use very little stack space, the server might perform better if the common language runtime does not commit the full thread stack immediately when a thread is started.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3ce45-133">未受管理的主機可以在 `STARTUP_DISABLE_COMMITTHREADSTACK` STARTUP_FLAGS [列舉中使用](../../../unmanaged-api/hosting/startup-flags-enumeration.md) 啟動旗標，來達到相同的結果。</span><span class="sxs-lookup"><span data-stu-id="3ce45-133">Unmanaged hosts can use the `STARTUP_DISABLE_COMMITTHREADSTACK` startup flag in the [STARTUP_FLAGS](../../../unmanaged-api/hosting/startup-flags-enumeration.md) enumeration to accomplish the same result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ce45-134">範例</span><span class="sxs-lookup"><span data-stu-id="3ce45-134">Example</span></span>  
 <span data-ttu-id="3ce45-135">下列範例示範如何停用 Common Language Runtime 的預設行為，也就是在執行緒啟動時認可完整執行緒堆疊。</span><span class="sxs-lookup"><span data-stu-id="3ce45-135">The following example shows how to disable the default behavior of the common language runtime, which is to commit the full thread stack on thread startup.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCommitThreadStack enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3ce45-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="3ce45-136">See also</span></span>

- [<span data-ttu-id="3ce45-137">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="3ce45-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="3ce45-138">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="3ce45-138">Configuration File Schema</span></span>](../index.md)
