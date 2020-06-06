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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "73117466"
---
# <a name="disablecommitthreadstack-element"></a><span data-ttu-id="8336a-102">\<disableCommitThreadStack> 項目</span><span class="sxs-lookup"><span data-stu-id="8336a-102">\<disableCommitThreadStack> Element</span></span>
<span data-ttu-id="8336a-103">指定是否在執行緒啟動時認可完整執行緒堆疊。</span><span class="sxs-lookup"><span data-stu-id="8336a-103">Specifies whether the full thread stack is committed when a thread is started.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<disableCommitThreadStack>**  
  
## <a name="syntax"></a><span data-ttu-id="8336a-104">語法</span><span class="sxs-lookup"><span data-stu-id="8336a-104">Syntax</span></span>  
  
```xml  
<disableCommitThreadStack enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8336a-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8336a-105">Attributes and Elements</span></span>  
 <span data-ttu-id="8336a-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="8336a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8336a-107">屬性</span><span class="sxs-lookup"><span data-stu-id="8336a-107">Attributes</span></span>  
  
|<span data-ttu-id="8336a-108">屬性</span><span class="sxs-lookup"><span data-stu-id="8336a-108">Attribute</span></span>|<span data-ttu-id="8336a-109">描述</span><span class="sxs-lookup"><span data-stu-id="8336a-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8336a-110">已啟用</span><span class="sxs-lookup"><span data-stu-id="8336a-110">enabled</span></span>|<span data-ttu-id="8336a-111">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="8336a-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="8336a-112">指定是否停用在執行緒啟動時認可完整執行緒堆疊 (預設行為)。</span><span class="sxs-lookup"><span data-stu-id="8336a-112">Specifies whether committing the full thread stack on thread startup (the default behavior) is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="8336a-113">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="8336a-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="8336a-114">值</span><span class="sxs-lookup"><span data-stu-id="8336a-114">Value</span></span>|<span data-ttu-id="8336a-115">描述</span><span class="sxs-lookup"><span data-stu-id="8336a-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8336a-116">0</span><span class="sxs-lookup"><span data-stu-id="8336a-116">0</span></span>|<span data-ttu-id="8336a-117">不停用 Common Language Runtime 的預設行為，也就是在執行緒啟動時認可完整執行緒堆疊。</span><span class="sxs-lookup"><span data-stu-id="8336a-117">Do not disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
|<span data-ttu-id="8336a-118">1</span><span class="sxs-lookup"><span data-stu-id="8336a-118">1</span></span>|<span data-ttu-id="8336a-119">不停用 Common Language Runtime 的預設行為，也就是在執行緒啟動時認可完整執行緒堆疊。</span><span class="sxs-lookup"><span data-stu-id="8336a-119">Disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8336a-120">子元素</span><span class="sxs-lookup"><span data-stu-id="8336a-120">Child Elements</span></span>  
 <span data-ttu-id="8336a-121">無。</span><span class="sxs-lookup"><span data-stu-id="8336a-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8336a-122">父項目</span><span class="sxs-lookup"><span data-stu-id="8336a-122">Parent Elements</span></span>  
  
|<span data-ttu-id="8336a-123">元素</span><span class="sxs-lookup"><span data-stu-id="8336a-123">Element</span></span>|<span data-ttu-id="8336a-124">描述</span><span class="sxs-lookup"><span data-stu-id="8336a-124">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="8336a-125">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="8336a-125">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="8336a-126">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="8336a-126">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8336a-127">備註</span><span class="sxs-lookup"><span data-stu-id="8336a-127">Remarks</span></span>  
 <span data-ttu-id="8336a-128">Common Language Runtime 的預設行為是在執行緒啟動時認可完整執行緒堆疊。</span><span class="sxs-lookup"><span data-stu-id="8336a-128">The default behavior of the common language runtime is to commit the full thread stack when a thread is started.</span></span> <span data-ttu-id="8336a-129">如果必須在具有有限記憶體的伺服器上建立大量執行緒，而且大部分的執行緒都會使用極小的堆疊空間，則 Common Language Runtime 不要在執行緒啟動時立即認可完整執行緒堆疊，伺服器的效能可能會較好。</span><span class="sxs-lookup"><span data-stu-id="8336a-129">If a large number of threads must be created on a server that has limited memory, and most of those threads will use very little stack space, the server might perform better if the common language runtime does not commit the full thread stack immediately when a thread is started.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8336a-130">未受管理的主機可以在 `STARTUP_DISABLE_COMMITTHREADSTACK` STARTUP_FLAGS [列舉中使用](../../../unmanaged-api/hosting/startup-flags-enumeration.md) 啟動旗標，來達到相同的結果。</span><span class="sxs-lookup"><span data-stu-id="8336a-130">Unmanaged hosts can use the `STARTUP_DISABLE_COMMITTHREADSTACK` startup flag in the [STARTUP_FLAGS](../../../unmanaged-api/hosting/startup-flags-enumeration.md) enumeration to accomplish the same result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8336a-131">範例</span><span class="sxs-lookup"><span data-stu-id="8336a-131">Example</span></span>  
 <span data-ttu-id="8336a-132">下列範例示範如何停用 Common Language Runtime 的預設行為，也就是在執行緒啟動時認可完整執行緒堆疊。</span><span class="sxs-lookup"><span data-stu-id="8336a-132">The following example shows how to disable the default behavior of the common language runtime, which is to commit the full thread stack on thread startup.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCommitThreadStack enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8336a-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8336a-133">See also</span></span>

- [<span data-ttu-id="8336a-134">執行時間設定架構</span><span class="sxs-lookup"><span data-stu-id="8336a-134">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="8336a-135">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="8336a-135">Configuration File Schema</span></span>](../index.md)
