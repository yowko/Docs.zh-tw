---
title: <legacyCorruptedStateExceptionsPolicy> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6566437d899b768cda1bab74bb1310deb7aa74db
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252508"
---
# <a name="legacycorruptedstateexceptionspolicy-element"></a><span data-ttu-id="beffe-102">\<legacyCorruptedStateExceptionsPolicy > 元素</span><span class="sxs-lookup"><span data-stu-id="beffe-102">\<legacyCorruptedStateExceptionsPolicy> Element</span></span>
<span data-ttu-id="beffe-103">指定通用語言執行時間是否允許 managed 程式碼攔截存取違規和其他損毀狀態例外狀況。</span><span class="sxs-lookup"><span data-stu-id="beffe-103">Specifies whether the common language runtime allows managed code to catch access violations and other corrupted state exceptions.</span></span>  
  
<span data-ttu-id="beffe-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="beffe-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="beffe-105">&nbsp;&nbsp;[ **\<執行時間 >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="beffe-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="beffe-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<legacyCorruptedStateExceptionsPolicy>**</span><span class="sxs-lookup"><span data-stu-id="beffe-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<legacyCorruptedStateExceptionsPolicy>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="beffe-107">語法</span><span class="sxs-lookup"><span data-stu-id="beffe-107">Syntax</span></span>  
  
```xml  
<legacyCorruptedStateExceptionsPolicy enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="beffe-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="beffe-108">Attributes and Elements</span></span>  
 <span data-ttu-id="beffe-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="beffe-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="beffe-110">屬性</span><span class="sxs-lookup"><span data-stu-id="beffe-110">Attributes</span></span>  
  
|<span data-ttu-id="beffe-111">屬性</span><span class="sxs-lookup"><span data-stu-id="beffe-111">Attribute</span></span>|<span data-ttu-id="beffe-112">描述</span><span class="sxs-lookup"><span data-stu-id="beffe-112">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="beffe-113">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="beffe-113">Required attribute.</span></span><br /><br /> <span data-ttu-id="beffe-114">指定應用程式將會攔截損毀狀態例外狀況失敗, 例如存取違規。</span><span class="sxs-lookup"><span data-stu-id="beffe-114">Specifies that the application will catch corrupting state exception failures such as access violations.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="beffe-115">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="beffe-115">enabled Attribute</span></span>  
  
|<span data-ttu-id="beffe-116">值</span><span class="sxs-lookup"><span data-stu-id="beffe-116">Value</span></span>|<span data-ttu-id="beffe-117">描述</span><span class="sxs-lookup"><span data-stu-id="beffe-117">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="beffe-118">應用程式將不會攔截損毀狀態例外狀況失敗, 例如存取違規。</span><span class="sxs-lookup"><span data-stu-id="beffe-118">The application will not catch corrupting state exception failures such as access violations.</span></span> <span data-ttu-id="beffe-119">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="beffe-119">This is the default.</span></span>|  
|`true`|<span data-ttu-id="beffe-120">應用程式將會攔截損毀狀態例外狀況失敗, 例如存取違規。</span><span class="sxs-lookup"><span data-stu-id="beffe-120">The application will catch corrupting state exception failures such as access violations.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="beffe-121">子元素</span><span class="sxs-lookup"><span data-stu-id="beffe-121">Child Elements</span></span>  
 <span data-ttu-id="beffe-122">無。</span><span class="sxs-lookup"><span data-stu-id="beffe-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="beffe-123">父項目</span><span class="sxs-lookup"><span data-stu-id="beffe-123">Parent Elements</span></span>  
  
|<span data-ttu-id="beffe-124">項目</span><span class="sxs-lookup"><span data-stu-id="beffe-124">Element</span></span>|<span data-ttu-id="beffe-125">說明</span><span class="sxs-lookup"><span data-stu-id="beffe-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="beffe-126">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="beffe-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="beffe-127">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="beffe-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="beffe-128">備註</span><span class="sxs-lookup"><span data-stu-id="beffe-128">Remarks</span></span>  
 <span data-ttu-id="beffe-129">在 .NET Framework 版本3.5 和舊版中, 通用語言執行平臺允許 managed 程式碼攔截因進程狀態損毀而引發的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="beffe-129">In the .NET Framework version 3.5 and earlier, the common language runtime allowed managed code to catch exceptions that were raised by corrupted process states.</span></span> <span data-ttu-id="beffe-130">存取違規是這類例外狀況的範例。</span><span class="sxs-lookup"><span data-stu-id="beffe-130">An access violation is an example of this type of exception.</span></span>  
  
 <span data-ttu-id="beffe-131">從 .NET Framework 4 開始, managed 程式碼不會再于區塊中`catch`捕捉這些類型的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="beffe-131">Starting with the .NET Framework 4, managed code no longer catches these types of exceptions in `catch` blocks.</span></span> <span data-ttu-id="beffe-132">不過, 您可以透過兩種方式來覆寫此變更並維護損毀狀態例外狀況的處理:</span><span class="sxs-lookup"><span data-stu-id="beffe-132">However, you can override this change and maintain the handling of corrupted state exceptions in two ways:</span></span>  
  
- <span data-ttu-id="beffe-133">將元素的`enabled`屬性設定為`true`。 `<legacyCorruptedStateExceptionsPolicy>`</span><span class="sxs-lookup"><span data-stu-id="beffe-133">Set the `<legacyCorruptedStateExceptionsPolicy>` element's `enabled` attribute to `true`.</span></span> <span data-ttu-id="beffe-134">此設定會套用 processwide, 並會影響所有方法。</span><span class="sxs-lookup"><span data-stu-id="beffe-134">This configuration setting is applied processwide and affects all methods.</span></span>  
  
 <span data-ttu-id="beffe-135">-或-</span><span class="sxs-lookup"><span data-stu-id="beffe-135">-or-</span></span>  
  
- <span data-ttu-id="beffe-136">將屬性套用至包含例外`catch`狀況區塊的方法。 <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="beffe-136">Apply the <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> attribute to the method that contains the exceptions `catch` block.</span></span>  
  
 <span data-ttu-id="beffe-137">此 configuration 元素僅適用于 .NET Framework 4 和更新版本。</span><span class="sxs-lookup"><span data-stu-id="beffe-137">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="beffe-138">範例</span><span class="sxs-lookup"><span data-stu-id="beffe-138">Example</span></span>  
 <span data-ttu-id="beffe-139">下列範例顯示如何指定應用程式應該還原為 .NET Framework 4 之前的行為, 並攔截所有損毀狀態例外狀況失敗。</span><span class="sxs-lookup"><span data-stu-id="beffe-139">The following example shows how to specify that the application should revert to the behavior before the .NET Framework 4, and catch all corrupting state exception failures.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="beffe-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="beffe-140">See also</span></span>

- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>
- [<span data-ttu-id="beffe-141">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="beffe-141">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="beffe-142">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="beffe-142">Configuration File Schema</span></span>](../index.md)
