---
title: <legacyCorruptedStateExceptionsPolicy> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6191ee2169a85725f0367763874e60c0ceb1d7a4
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489427"
---
# <a name="legacycorruptedstateexceptionspolicy-element"></a><span data-ttu-id="9bf27-102">\<legacyCorruptedStateExceptionsPolicy > 項目</span><span class="sxs-lookup"><span data-stu-id="9bf27-102">\<legacyCorruptedStateExceptionsPolicy> Element</span></span>
<span data-ttu-id="9bf27-103">指定 common language runtime 是否允許 managed 程式碼攔截存取違規和其他損毀的狀態例外狀況。</span><span class="sxs-lookup"><span data-stu-id="9bf27-103">Specifies whether the common language runtime allows managed code to catch access violations and other corrupted state exceptions.</span></span>  
  
 <span data-ttu-id="9bf27-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="9bf27-104">\<configuration></span></span>  
<span data-ttu-id="9bf27-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="9bf27-105">\<runtime></span></span>  
<span data-ttu-id="9bf27-106">\<legacyCorruptedStateExceptionsPolicy></span><span class="sxs-lookup"><span data-stu-id="9bf27-106">\<legacyCorruptedStateExceptionsPolicy></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bf27-107">語法</span><span class="sxs-lookup"><span data-stu-id="9bf27-107">Syntax</span></span>  
  
```xml  
<legacyCorruptedStateExceptionsPolicy enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9bf27-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9bf27-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9bf27-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="9bf27-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9bf27-110">屬性</span><span class="sxs-lookup"><span data-stu-id="9bf27-110">Attributes</span></span>  
  
|<span data-ttu-id="9bf27-111">屬性</span><span class="sxs-lookup"><span data-stu-id="9bf27-111">Attribute</span></span>|<span data-ttu-id="9bf27-112">描述</span><span class="sxs-lookup"><span data-stu-id="9bf27-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="9bf27-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="9bf27-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="9bf27-114">指定應用程式會攔截損毀狀態例外狀況失敗，例如存取違規。</span><span class="sxs-lookup"><span data-stu-id="9bf27-114">Specifies that the application will catch corrupting state exception failures such as access violations.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="9bf27-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="9bf27-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="9bf27-116">值</span><span class="sxs-lookup"><span data-stu-id="9bf27-116">Value</span></span>|<span data-ttu-id="9bf27-117">描述</span><span class="sxs-lookup"><span data-stu-id="9bf27-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="9bf27-118">應用程式不會攔截損毀狀態例外狀況失敗，例如存取違規。</span><span class="sxs-lookup"><span data-stu-id="9bf27-118">The application will not catch corrupting state exception failures such as access violations.</span></span> <span data-ttu-id="9bf27-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="9bf27-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="9bf27-120">應用程式會攔截損毀狀態例外狀況失敗，例如存取違規。</span><span class="sxs-lookup"><span data-stu-id="9bf27-120">The application will catch corrupting state exception failures such as access violations.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9bf27-121">子元素</span><span class="sxs-lookup"><span data-stu-id="9bf27-121">Child Elements</span></span>  
 <span data-ttu-id="9bf27-122">無。</span><span class="sxs-lookup"><span data-stu-id="9bf27-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9bf27-123">父項目</span><span class="sxs-lookup"><span data-stu-id="9bf27-123">Parent Elements</span></span>  
  
|<span data-ttu-id="9bf27-124">項目</span><span class="sxs-lookup"><span data-stu-id="9bf27-124">Element</span></span>|<span data-ttu-id="9bf27-125">描述</span><span class="sxs-lookup"><span data-stu-id="9bf27-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="9bf27-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="9bf27-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="9bf27-127">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="9bf27-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9bf27-128">備註</span><span class="sxs-lookup"><span data-stu-id="9bf27-128">Remarks</span></span>  
 <span data-ttu-id="9bf27-129">在.NET Framework 3.5 和更早版本中，通用語言執行平台允許受管理的程式碼，以擷取損毀處理序狀態已引發的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="9bf27-129">In the .NET Framework version 3.5 and earlier, the common language runtime allowed managed code to catch exceptions that were raised by corrupted process states.</span></span> <span data-ttu-id="9bf27-130">存取違規是這種類型的例外狀況的範例。</span><span class="sxs-lookup"><span data-stu-id="9bf27-130">An access violation is an example of this type of exception.</span></span>  
  
 <span data-ttu-id="9bf27-131">從.NET Framework 4 開始，managed 程式碼不會再會攔截這些類型中的例外狀況的`catch`區塊。</span><span class="sxs-lookup"><span data-stu-id="9bf27-131">Starting with the .NET Framework 4, managed code no longer catches these types of exceptions in `catch` blocks.</span></span> <span data-ttu-id="9bf27-132">不過，您可以覆寫這項變更，並維護兩種方式中的損毀的狀態例外狀況的處理：</span><span class="sxs-lookup"><span data-stu-id="9bf27-132">However, you can override this change and maintain the handling of corrupted state exceptions in two ways:</span></span>  
  
- <span data-ttu-id="9bf27-133">設定`<legacyCorruptedStateExceptionsPolicy>`項目的`enabled`屬性設定為`true`。</span><span class="sxs-lookup"><span data-stu-id="9bf27-133">Set the `<legacyCorruptedStateExceptionsPolicy>` element's `enabled` attribute to `true`.</span></span> <span data-ttu-id="9bf27-134">此組態設定會套用的 processwide，而且會影響所有方法。</span><span class="sxs-lookup"><span data-stu-id="9bf27-134">This configuration setting is applied processwide and affects all methods.</span></span>  
  
 <span data-ttu-id="9bf27-135">-或-</span><span class="sxs-lookup"><span data-stu-id="9bf27-135">-or-</span></span>  
  
- <span data-ttu-id="9bf27-136">適用於<xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType>屬性設定為包含例外狀況的方法`catch`區塊。</span><span class="sxs-lookup"><span data-stu-id="9bf27-136">Apply the <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> attribute to the method that contains the exceptions `catch` block.</span></span>  
  
 <span data-ttu-id="9bf27-137">這個組態項目是僅適用於.NET Framework 4 及更新版本。</span><span class="sxs-lookup"><span data-stu-id="9bf27-137">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9bf27-138">範例</span><span class="sxs-lookup"><span data-stu-id="9bf27-138">Example</span></span>  
 <span data-ttu-id="9bf27-139">下列範例示範如何指定應用程式應該還原為.NET Framework 4 之前的行為，並擷取所有損毀狀態例外狀況失敗。</span><span class="sxs-lookup"><span data-stu-id="9bf27-139">The following example shows how to specify that the application should revert to the behavior before the .NET Framework 4, and catch all corrupting state exception failures.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9bf27-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9bf27-140">See also</span></span>

- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>
- [<span data-ttu-id="9bf27-141">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="9bf27-141">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="9bf27-142">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="9bf27-142">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
