---
title: "&lt;useLegacyJit&gt;項目"
ms.custom: 
ms.date: 04/26/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c2cf97f0-9262-4f1f-a754-5568b51110ad
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9d2a71e44db2d6e85ae730f4603bf191f54525c2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltuselegacyjitgt-element"></a><span data-ttu-id="2f919-102">&lt;useLegacyJit&gt;項目</span><span class="sxs-lookup"><span data-stu-id="2f919-102">&lt;useLegacyJit&gt; Element</span></span>

<span data-ttu-id="2f919-103">決定通用語言執行平台是否針對 Just-In-Time 編譯使用舊版 64 位元 JIT 編譯器。</span><span class="sxs-lookup"><span data-stu-id="2f919-103">Determines whether the common language runtime uses the legacy 64-bit JIT compiler for just-in-time compilation.</span></span>  
  
<span data-ttu-id="2f919-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="2f919-104">\<configuration></span></span>  
<span data-ttu-id="2f919-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="2f919-105">\<runtime></span></span>  
<span data-ttu-id="2f919-106">\<useLegacyJit ></span><span class="sxs-lookup"><span data-stu-id="2f919-106">\<useLegacyJit></span></span>
  
## <a name="syntax"></a><span data-ttu-id="2f919-107">語法</span><span class="sxs-lookup"><span data-stu-id="2f919-107">Syntax</span></span>  
  
```xml
<useLegacyJit enabled=0|1 />
```

<span data-ttu-id="2f919-108">項目名稱`useLegacyJit`會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="2f919-108">The element name `useLegacyJit` is case-sensitive.</span></span>
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2f919-109">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="2f919-109">Attributes and elements</span></span>

<span data-ttu-id="2f919-110">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="2f919-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2f919-111">屬性</span><span class="sxs-lookup"><span data-stu-id="2f919-111">Attributes</span></span>  
  
| <span data-ttu-id="2f919-112">屬性</span><span class="sxs-lookup"><span data-stu-id="2f919-112">Attribute</span></span> | <span data-ttu-id="2f919-113">描述</span><span class="sxs-lookup"><span data-stu-id="2f919-113">Description</span></span>                                                                                   |  
| --------- | --------------------------------------------------------------------------------------------- |  
| `enabled` | <span data-ttu-id="2f919-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="2f919-114">Required attribute.</span></span><br><br><span data-ttu-id="2f919-115">指定執行階段是否使用傳統的 64 位元 JIT 編譯器。</span><span class="sxs-lookup"><span data-stu-id="2f919-115">Specifies whether the runtime uses the legacy 64-bit JIT compiler.</span></span> |  
  
### <a name="enabled-attribute"></a><span data-ttu-id="2f919-116">啟用的屬性</span><span class="sxs-lookup"><span data-stu-id="2f919-116">enabled attribute</span></span>  
  
| <span data-ttu-id="2f919-117">值</span><span class="sxs-lookup"><span data-stu-id="2f919-117">Value</span></span> | <span data-ttu-id="2f919-118">描述</span><span class="sxs-lookup"><span data-stu-id="2f919-118">Description</span></span>                                                                                                         |  
| ----- | ------------------------------------------------------------------------------------------------------------------- |  
| <span data-ttu-id="2f919-119">0</span><span class="sxs-lookup"><span data-stu-id="2f919-119">0</span></span>     | <span data-ttu-id="2f919-120">Common language runtime 會使用新的 64 位元 JIT 編譯器包含在.NET Framework 4.6 和更新版本。</span><span class="sxs-lookup"><span data-stu-id="2f919-120">The common language runtime uses the new 64-bit JIT compiler included in the .NET Framework 4.6 and later versions.</span></span> |  
| <span data-ttu-id="2f919-121">1</span><span class="sxs-lookup"><span data-stu-id="2f919-121">1</span></span>     | <span data-ttu-id="2f919-122">Common language runtime 會使用較舊的 64 位元 JIT 編譯器。</span><span class="sxs-lookup"><span data-stu-id="2f919-122">The common language runtime uses the older 64-bit JIT compiler.</span></span>                                                     |  
  
### <a name="child-elements"></a><span data-ttu-id="2f919-123">子元素</span><span class="sxs-lookup"><span data-stu-id="2f919-123">Child elements</span></span>

<span data-ttu-id="2f919-124">無</span><span class="sxs-lookup"><span data-stu-id="2f919-124">None</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="2f919-125">父元素</span><span class="sxs-lookup"><span data-stu-id="2f919-125">Parent elements</span></span>  
  
| <span data-ttu-id="2f919-126">元素</span><span class="sxs-lookup"><span data-stu-id="2f919-126">Element</span></span>         | <span data-ttu-id="2f919-127">描述</span><span class="sxs-lookup"><span data-stu-id="2f919-127">Description</span></span>                                                                                                       |  
| --------------- | ----------------------------------------------------------------------------------------------------------------- |  
| `configuration` | <span data-ttu-id="2f919-128">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="2f919-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |  
| `runtime`       | <span data-ttu-id="2f919-129">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="2f919-129">Contains information about runtime initialization options.</span></span>                                                        |  
  
## <a name="remarks"></a><span data-ttu-id="2f919-130">備註</span><span class="sxs-lookup"><span data-stu-id="2f919-130">Remarks</span></span>  

<span data-ttu-id="2f919-131">從.NET Framework 4.6 開始，通用語言執行平台預設會使用新的 64 位元編譯器 Just-In-Time (JIT) 編譯的。</span><span class="sxs-lookup"><span data-stu-id="2f919-131">Starting with the .NET Framework 4.6, the common language runtime uses a new 64-bit compiler for Just-In-Time (JIT) compilation by default.</span></span> <span data-ttu-id="2f919-132">在某些情況下，這可能會導致從已由舊版的 64 位元 JIT 編譯器的 JIT 編譯的應用程式程式碼的行為差異。</span><span class="sxs-lookup"><span data-stu-id="2f919-132">In some cases, this may result in a difference in behavior from application code that was JIT-compiled by the previous version of the 64-bit JIT compiler.</span></span> <span data-ttu-id="2f919-133">藉由設定`enabled`屬性`<useLegacyJit>`元素`1`，您可以停用新的 64 位元 JIT 編譯器，而是在編譯應用程式使用舊版的 64 位元 JIT 編譯器。</span><span class="sxs-lookup"><span data-stu-id="2f919-133">By setting the `enabled` attribute of the `<useLegacyJit>` element to `1`, you can disable the new 64-bit JIT compiler and instead compile your app using the legacy 64-bit JIT compiler.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2f919-134">`<useLegacyJit>`項目會影響只有 64 位元 JIT 編譯。</span><span class="sxs-lookup"><span data-stu-id="2f919-134">The `<useLegacyJit>` element affects 64-bit JIT compilation only.</span></span> <span data-ttu-id="2f919-135">32 位元 JIT 編譯器的編譯不受影響。</span><span class="sxs-lookup"><span data-stu-id="2f919-135">Compilation with the 32-bit JIT compiler is unaffected.</span></span>  
  
<span data-ttu-id="2f919-136">不使用組態檔設定，您可以啟用舊版的 64 位元 JIT 編譯器，另外兩種方式：</span><span class="sxs-lookup"><span data-stu-id="2f919-136">Instead of using a configuration file setting, you can enable the legacy 64-bit JIT compiler in two other ways:</span></span>  
  
- <span data-ttu-id="2f919-137">設定環境變數</span><span class="sxs-lookup"><span data-stu-id="2f919-137">Setting an environment variable</span></span>

  <span data-ttu-id="2f919-138">設定`COMPLUS_useLegacyJit`環境變數設為  `0` （使用新的 64 位元 JIT 編譯器） 或`1`（使用較舊的 64 位元 JIT 編譯器）：</span><span class="sxs-lookup"><span data-stu-id="2f919-138">Set the `COMPLUS_useLegacyJit` environment variable to either `0` (use the new 64-bit JIT compiler) or `1` (use the older 64-bit JIT compiler):</span></span>
  
  ```  
  COMPLUS_useLegacyJit=0|1  
  ```  
  
  <span data-ttu-id="2f919-139">環境變數具有*全域範圍*，也就是說，它會影響的電腦上執行的所有應用程式。</span><span class="sxs-lookup"><span data-stu-id="2f919-139">The environment variable has *global scope*, which means that it affects all applications run on the machine.</span></span> <span data-ttu-id="2f919-140">如果設定，它可覆寫應用程式組態檔設定。</span><span class="sxs-lookup"><span data-stu-id="2f919-140">If set, it can be overridden by the application configuration file setting.</span></span> <span data-ttu-id="2f919-141">環境變數名稱不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="2f919-141">The environment variable name is not case-sensitive.</span></span>
  
- <span data-ttu-id="2f919-142">新增登錄機碼</span><span class="sxs-lookup"><span data-stu-id="2f919-142">Adding a registry key</span></span>

  <span data-ttu-id="2f919-143">您可以藉由新增啟用舊版的 64 位元 JIT 編譯器`REG_DWORD`值設為 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework`或`HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework`登錄中的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="2f919-143">You can enable the legacy 64-bit JIT compiler by adding a `REG_DWORD` value to either the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` or `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key in the registry.</span></span> <span data-ttu-id="2f919-144">值為`useLegacyJit`。</span><span class="sxs-lookup"><span data-stu-id="2f919-144">The value is named `useLegacyJit`.</span></span> <span data-ttu-id="2f919-145">如果值為 0，則會使用新的編譯器。</span><span class="sxs-lookup"><span data-stu-id="2f919-145">If the value is 0, the new compiler is used.</span></span> <span data-ttu-id="2f919-146">如果值為 1，會啟用舊版的 64 位元 JIT 編譯器。</span><span class="sxs-lookup"><span data-stu-id="2f919-146">If the value is 1, the legacy 64-bit JIT compiler is enabled.</span></span> <span data-ttu-id="2f919-147">登錄值名稱不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="2f919-147">The registry value name is not case-sensitive.</span></span>
  
  <span data-ttu-id="2f919-148">值來加入`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework`金鑰會影響電腦上執行的所有應用程式。</span><span class="sxs-lookup"><span data-stu-id="2f919-148">Adding the value to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` key affects all apps running on the machine.</span></span> <span data-ttu-id="2f919-149">值來加入`HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework`金鑰會影響目前使用者所執行的所有應用程式。</span><span class="sxs-lookup"><span data-stu-id="2f919-149">Adding the value to the `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key affects all apps run by the current user.</span></span> <span data-ttu-id="2f919-150">如果電腦透過多個使用者帳戶設定，只有目前使用者所執行的應用程式會受到影響，除非此值會加入至其他使用者的登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="2f919-150">If a machine is configured with multiple user accounts, only apps run by the current user are affected, unless the value is added to the registry keys for other users as well.</span></span> <span data-ttu-id="2f919-151">加入`<useLegacyJit>`項目至組態檔覆寫登錄設定，如果它們存在。</span><span class="sxs-lookup"><span data-stu-id="2f919-151">Adding the `<useLegacyJit>` element to a configuration file overrides the registry settings, if they're present.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f919-152">範例</span><span class="sxs-lookup"><span data-stu-id="2f919-152">Example</span></span>  

<span data-ttu-id="2f919-153">下列組態檔停用與新的 64 位元 JIT 編譯器編譯，而是使用舊版的 64 位元 JIT 編譯器。</span><span class="sxs-lookup"><span data-stu-id="2f919-153">The following configuration file disables compilation with the new 64-bit JIT compiler and instead uses the legacy 64-bit JIT compiler.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
  <runtime>  
    <useLegacyJit enabled="1" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2f919-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2f919-154">See also</span></span>

<span data-ttu-id="2f919-155">[\<runtime > 項目](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="2f919-155">[\<runtime> Element](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) </span></span>  
<span data-ttu-id="2f919-156">[\<設定 > 項目](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="2f919-156">[\<configuration> Element](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
[<span data-ttu-id="2f919-157">風險降低：新的 64 位元 JIT 編譯器</span><span class="sxs-lookup"><span data-stu-id="2f919-157">Mitigation: New 64-bit JIT Compiler</span></span>](../../../../../docs/framework/migration-guide/mitigation-new-64-bit-jit-compiler.md)
