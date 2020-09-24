---
title: <legacyCorruptedStateExceptionsPolicy> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
ms.openlocfilehash: f36e27a1b85cff2ba8c7e838bace37890a5aa760
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151203"
---
# <a name="legacycorruptedstateexceptionspolicy-element"></a><span data-ttu-id="18a37-102">\<legacyCorruptedStateExceptionsPolicy> 項目</span><span class="sxs-lookup"><span data-stu-id="18a37-102">\<legacyCorruptedStateExceptionsPolicy> Element</span></span>

<span data-ttu-id="18a37-103">指定 common language runtime 是否允許 managed 程式碼攔截存取違規和其他損毀狀態例外狀況。</span><span class="sxs-lookup"><span data-stu-id="18a37-103">Specifies whether the common language runtime allows managed code to catch access violations and other corrupted state exceptions.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<legacyCorruptedStateExceptionsPolicy>**  
  
## <a name="syntax"></a><span data-ttu-id="18a37-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="18a37-104">Syntax</span></span>  
  
```xml  
<legacyCorruptedStateExceptionsPolicy enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="18a37-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="18a37-105">Attributes and Elements</span></span>  

 <span data-ttu-id="18a37-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="18a37-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="18a37-107">屬性</span><span class="sxs-lookup"><span data-stu-id="18a37-107">Attributes</span></span>  
  
|<span data-ttu-id="18a37-108">屬性</span><span class="sxs-lookup"><span data-stu-id="18a37-108">Attribute</span></span>|<span data-ttu-id="18a37-109">描述</span><span class="sxs-lookup"><span data-stu-id="18a37-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="18a37-110">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="18a37-110">Required attribute.</span></span><br /><br /> <span data-ttu-id="18a37-111">指定應用程式將會攔截損毀狀態例外狀況失敗，例如存取違規。</span><span class="sxs-lookup"><span data-stu-id="18a37-111">Specifies that the application will catch corrupting state exception failures such as access violations.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="18a37-112">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="18a37-112">enabled Attribute</span></span>  
  
|<span data-ttu-id="18a37-113">值</span><span class="sxs-lookup"><span data-stu-id="18a37-113">Value</span></span>|<span data-ttu-id="18a37-114">描述</span><span class="sxs-lookup"><span data-stu-id="18a37-114">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="18a37-115">應用程式不會攔截損毀狀態例外狀況失敗，例如存取違規。</span><span class="sxs-lookup"><span data-stu-id="18a37-115">The application will not catch corrupting state exception failures such as access violations.</span></span> <span data-ttu-id="18a37-116">此為預設值。</span><span class="sxs-lookup"><span data-stu-id="18a37-116">This is the default.</span></span>|  
|`true`|<span data-ttu-id="18a37-117">應用程式將會攔截損毀狀態例外狀況失敗，例如存取違規。</span><span class="sxs-lookup"><span data-stu-id="18a37-117">The application will catch corrupting state exception failures such as access violations.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="18a37-118">子元素</span><span class="sxs-lookup"><span data-stu-id="18a37-118">Child Elements</span></span>  

 <span data-ttu-id="18a37-119">無。</span><span class="sxs-lookup"><span data-stu-id="18a37-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="18a37-120">父項目</span><span class="sxs-lookup"><span data-stu-id="18a37-120">Parent Elements</span></span>  
  
|<span data-ttu-id="18a37-121">項目</span><span class="sxs-lookup"><span data-stu-id="18a37-121">Element</span></span>|<span data-ttu-id="18a37-122">描述</span><span class="sxs-lookup"><span data-stu-id="18a37-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="18a37-123">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="18a37-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="18a37-124">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="18a37-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18a37-125">備註</span><span class="sxs-lookup"><span data-stu-id="18a37-125">Remarks</span></span>  

 <span data-ttu-id="18a37-126">在 .NET Framework 3.5 版和更舊版本中，common language runtime 允許 managed 程式碼攔截因進程狀態損毀而引發的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="18a37-126">In the .NET Framework version 3.5 and earlier, the common language runtime allowed managed code to catch exceptions that were raised by corrupted process states.</span></span> <span data-ttu-id="18a37-127">存取違規是這種例外狀況類型的範例。</span><span class="sxs-lookup"><span data-stu-id="18a37-127">An access violation is an example of this type of exception.</span></span>  
  
 <span data-ttu-id="18a37-128">從 .NET Framework 4 開始，managed 程式碼不會再于區塊中攔截這些例外狀況類型 `catch` 。</span><span class="sxs-lookup"><span data-stu-id="18a37-128">Starting with the .NET Framework 4, managed code no longer catches these types of exceptions in `catch` blocks.</span></span> <span data-ttu-id="18a37-129">不過，您可以覆寫這項變更，並以兩種方式維護損毀狀態例外狀況的處理：</span><span class="sxs-lookup"><span data-stu-id="18a37-129">However, you can override this change and maintain the handling of corrupted state exceptions in two ways:</span></span>  
  
- <span data-ttu-id="18a37-130">將 `<legacyCorruptedStateExceptionsPolicy>` 元素的 `enabled` 屬性設定為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="18a37-130">Set the `<legacyCorruptedStateExceptionsPolicy>` element's `enabled` attribute to `true`.</span></span> <span data-ttu-id="18a37-131">這項設定會套用 processwide 並影響所有方法。</span><span class="sxs-lookup"><span data-stu-id="18a37-131">This configuration setting is applied processwide and affects all methods.</span></span>  
  
 <span data-ttu-id="18a37-132">-或-</span><span class="sxs-lookup"><span data-stu-id="18a37-132">-or-</span></span>  
  
- <span data-ttu-id="18a37-133">將 <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> 屬性套用至包含例外狀況區塊的方法 `catch` 。</span><span class="sxs-lookup"><span data-stu-id="18a37-133">Apply the <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> attribute to the method that contains the exceptions `catch` block.</span></span>  
  
 <span data-ttu-id="18a37-134">只有 .NET Framework 4 和更新版本才提供此設定元素。</span><span class="sxs-lookup"><span data-stu-id="18a37-134">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18a37-135">範例</span><span class="sxs-lookup"><span data-stu-id="18a37-135">Example</span></span>  

 <span data-ttu-id="18a37-136">下列範例示範如何指定應用程式應該在 .NET Framework 4 之前還原為行為，並攔截所有損毀狀態例外狀況失敗。</span><span class="sxs-lookup"><span data-stu-id="18a37-136">The following example shows how to specify that the application should revert to the behavior before the .NET Framework 4, and catch all corrupting state exception failures.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="18a37-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18a37-137">See also</span></span>

- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>
- [<span data-ttu-id="18a37-138">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="18a37-138">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="18a37-139">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="18a37-139">Configuration File Schema</span></span>](../index.md)
