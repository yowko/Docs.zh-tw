---
title: <useLegacyJit> 項目
ms.date: 04/26/2017
ms.assetid: c2cf97f0-9262-4f1f-a754-5568b51110ad
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a467599084f01b1a48c95c5e25fb1f869156dffa
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55278755"
---
# <a name="uselegacyjit-element"></a><span data-ttu-id="c2caf-102">\<Uselegacyjit> > 項目</span><span class="sxs-lookup"><span data-stu-id="c2caf-102">\<useLegacyJit> Element</span></span>

<span data-ttu-id="c2caf-103">決定通用語言執行平台是否針對 Just-In-Time 編譯使用舊版 64 位元 JIT 編譯器。</span><span class="sxs-lookup"><span data-stu-id="c2caf-103">Determines whether the common language runtime uses the legacy 64-bit JIT compiler for just-in-time compilation.</span></span>  
  
<span data-ttu-id="c2caf-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="c2caf-104">\<configuration></span></span>  
<span data-ttu-id="c2caf-105">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="c2caf-105">\<runtime></span></span>  
<span data-ttu-id="c2caf-106">\<useLegacyJit></span><span class="sxs-lookup"><span data-stu-id="c2caf-106">\<useLegacyJit></span></span>
  
## <a name="syntax"></a><span data-ttu-id="c2caf-107">語法</span><span class="sxs-lookup"><span data-stu-id="c2caf-107">Syntax</span></span>  
  
```xml
<useLegacyJit enabled=0|1 />
```

<span data-ttu-id="c2caf-108">項目名稱`useLegacyJit`會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="c2caf-108">The element name `useLegacyJit` is case-sensitive.</span></span>
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c2caf-109">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="c2caf-109">Attributes and elements</span></span>

<span data-ttu-id="c2caf-110">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c2caf-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c2caf-111">屬性</span><span class="sxs-lookup"><span data-stu-id="c2caf-111">Attributes</span></span>  
  
| <span data-ttu-id="c2caf-112">屬性</span><span class="sxs-lookup"><span data-stu-id="c2caf-112">Attribute</span></span> | <span data-ttu-id="c2caf-113">描述</span><span class="sxs-lookup"><span data-stu-id="c2caf-113">Description</span></span>                                                                                   |  
| --------- | --------------------------------------------------------------------------------------------- |  
| `enabled` | <span data-ttu-id="c2caf-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="c2caf-114">Required attribute.</span></span><br><br><span data-ttu-id="c2caf-115">指定執行階段是否使用舊版 64 位元 JIT 編譯器。</span><span class="sxs-lookup"><span data-stu-id="c2caf-115">Specifies whether the runtime uses the legacy 64-bit JIT compiler.</span></span> |  
  
### <a name="enabled-attribute"></a><span data-ttu-id="c2caf-116">啟用的屬性</span><span class="sxs-lookup"><span data-stu-id="c2caf-116">enabled attribute</span></span>  
  
| <span data-ttu-id="c2caf-117">值</span><span class="sxs-lookup"><span data-stu-id="c2caf-117">Value</span></span> | <span data-ttu-id="c2caf-118">描述</span><span class="sxs-lookup"><span data-stu-id="c2caf-118">Description</span></span>                                                                                                         |  
| ----- | ------------------------------------------------------------------------------------------------------------------- |  
| <span data-ttu-id="c2caf-119">0</span><span class="sxs-lookup"><span data-stu-id="c2caf-119">0</span></span>     | <span data-ttu-id="c2caf-120">Common language runtime 會使用.NET Framework 4.6 和更新版本中所包含的新 64 位元 JIT 編譯器。</span><span class="sxs-lookup"><span data-stu-id="c2caf-120">The common language runtime uses the new 64-bit JIT compiler included in the .NET Framework 4.6 and later versions.</span></span> |  
| <span data-ttu-id="c2caf-121">1</span><span class="sxs-lookup"><span data-stu-id="c2caf-121">1</span></span>     | <span data-ttu-id="c2caf-122">Common language runtime 會使用舊版 64 位元 JIT 編譯器。</span><span class="sxs-lookup"><span data-stu-id="c2caf-122">The common language runtime uses the older 64-bit JIT compiler.</span></span>                                                     |  
  
### <a name="child-elements"></a><span data-ttu-id="c2caf-123">子元素</span><span class="sxs-lookup"><span data-stu-id="c2caf-123">Child elements</span></span>

<span data-ttu-id="c2caf-124">無</span><span class="sxs-lookup"><span data-stu-id="c2caf-124">None</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="c2caf-125">父元素</span><span class="sxs-lookup"><span data-stu-id="c2caf-125">Parent elements</span></span>  
  
| <span data-ttu-id="c2caf-126">元素</span><span class="sxs-lookup"><span data-stu-id="c2caf-126">Element</span></span>         | <span data-ttu-id="c2caf-127">描述</span><span class="sxs-lookup"><span data-stu-id="c2caf-127">Description</span></span>                                                                                                       |  
| --------------- | ----------------------------------------------------------------------------------------------------------------- |  
| `configuration` | <span data-ttu-id="c2caf-128">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="c2caf-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span> |  
| `runtime`       | <span data-ttu-id="c2caf-129">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="c2caf-129">Contains information about runtime initialization options.</span></span>                                                        |  
  
## <a name="remarks"></a><span data-ttu-id="c2caf-130">備註</span><span class="sxs-lookup"><span data-stu-id="c2caf-130">Remarks</span></span>  

<span data-ttu-id="c2caf-131">從.NET Framework 4.6 開始，common language runtime 預設會使用新的 64 位元編譯器進行 Just-In-Time (JIT) 編譯。</span><span class="sxs-lookup"><span data-stu-id="c2caf-131">Starting with the .NET Framework 4.6, the common language runtime uses a new 64-bit compiler for Just-In-Time (JIT) compilation by default.</span></span> <span data-ttu-id="c2caf-132">在某些情況下，這可能會導致從應用程式是由舊版 64 位元 JIT 編譯器的 JIT 編譯的程式碼的行為差異。</span><span class="sxs-lookup"><span data-stu-id="c2caf-132">In some cases, this may result in a difference in behavior from application code that was JIT-compiled by the previous version of the 64-bit JIT compiler.</span></span> <span data-ttu-id="c2caf-133">藉由設定`enabled`的屬性`<useLegacyJit>`項目`1`，您可以停用新的 64 位元 JIT 編譯器，並改為編譯您的應用程式使用舊版 64 位元 JIT 編譯器。</span><span class="sxs-lookup"><span data-stu-id="c2caf-133">By setting the `enabled` attribute of the `<useLegacyJit>` element to `1`, you can disable the new 64-bit JIT compiler and instead compile your app using the legacy 64-bit JIT compiler.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c2caf-134">`<useLegacyJit>`項目會影響僅 64 位元 JIT 編譯。</span><span class="sxs-lookup"><span data-stu-id="c2caf-134">The `<useLegacyJit>` element affects 64-bit JIT compilation only.</span></span> <span data-ttu-id="c2caf-135">使用 32 位元 JIT 編譯器的編譯不受影響。</span><span class="sxs-lookup"><span data-stu-id="c2caf-135">Compilation with the 32-bit JIT compiler is unaffected.</span></span>  
  
<span data-ttu-id="c2caf-136">而不是使用組態檔設定，您可以啟用舊版 64 位元 JIT 編譯器，另外兩種方式：</span><span class="sxs-lookup"><span data-stu-id="c2caf-136">Instead of using a configuration file setting, you can enable the legacy 64-bit JIT compiler in two other ways:</span></span>  
  
- <span data-ttu-id="c2caf-137">設定環境變數</span><span class="sxs-lookup"><span data-stu-id="c2caf-137">Setting an environment variable</span></span>

  <span data-ttu-id="c2caf-138">設定`COMPLUS_useLegacyJit`環境變數設為`0`（使用新的 64 位元 JIT 編譯器） 或`1`（使用舊版 64 位元 JIT 編譯器）：</span><span class="sxs-lookup"><span data-stu-id="c2caf-138">Set the `COMPLUS_useLegacyJit` environment variable to either `0` (use the new 64-bit JIT compiler) or `1` (use the older 64-bit JIT compiler):</span></span>
  
  ```  
  COMPLUS_useLegacyJit=0|1  
  ```  
  
  <span data-ttu-id="c2caf-139">環境變數*全域範圍*，也就是說，它會影響所有應用程式的電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="c2caf-139">The environment variable has *global scope*, which means that it affects all applications run on the machine.</span></span> <span data-ttu-id="c2caf-140">如果設定，它會覆寫應用程式組態檔的設定。</span><span class="sxs-lookup"><span data-stu-id="c2caf-140">If set, it can be overridden by the application configuration file setting.</span></span> <span data-ttu-id="c2caf-141">環境變數名稱不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="c2caf-141">The environment variable name is not case-sensitive.</span></span>
  
- <span data-ttu-id="c2caf-142">新增登錄機碼</span><span class="sxs-lookup"><span data-stu-id="c2caf-142">Adding a registry key</span></span>

  <span data-ttu-id="c2caf-143">您可以藉由新增啟用舊版 64 位元 JIT 編譯器`REG_DWORD`值設為`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework`或`HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework`金鑰在登錄中。</span><span class="sxs-lookup"><span data-stu-id="c2caf-143">You can enable the legacy 64-bit JIT compiler by adding a `REG_DWORD` value to either the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` or `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key in the registry.</span></span> <span data-ttu-id="c2caf-144">值為`useLegacyJit`。</span><span class="sxs-lookup"><span data-stu-id="c2caf-144">The value is named `useLegacyJit`.</span></span> <span data-ttu-id="c2caf-145">如果值為 0，則會使用新的編譯器。</span><span class="sxs-lookup"><span data-stu-id="c2caf-145">If the value is 0, the new compiler is used.</span></span> <span data-ttu-id="c2caf-146">如果值為 1，則會啟用舊版 64 位元 JIT 編譯器。</span><span class="sxs-lookup"><span data-stu-id="c2caf-146">If the value is 1, the legacy 64-bit JIT compiler is enabled.</span></span> <span data-ttu-id="c2caf-147">登錄值名稱不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="c2caf-147">The registry value name is not case-sensitive.</span></span>
  
  <span data-ttu-id="c2caf-148">值來加入`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework`金鑰會影響電腦上執行的所有應用程式。</span><span class="sxs-lookup"><span data-stu-id="c2caf-148">Adding the value to the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` key affects all apps running on the machine.</span></span> <span data-ttu-id="c2caf-149">值來加入`HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework`金鑰會影響目前使用者所執行的所有應用程式。</span><span class="sxs-lookup"><span data-stu-id="c2caf-149">Adding the value to the `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` key affects all apps run by the current user.</span></span> <span data-ttu-id="c2caf-150">如果機器已使用多個使用者帳戶，只有目前使用者所執行的應用程式會受到影響，除非此值會加入至其他使用者的登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="c2caf-150">If a machine is configured with multiple user accounts, only apps run by the current user are affected, unless the value is added to the registry keys for other users as well.</span></span> <span data-ttu-id="c2caf-151">新增`<useLegacyJit>`組態檔的項目覆寫登錄設定中，如果它們存在。</span><span class="sxs-lookup"><span data-stu-id="c2caf-151">Adding the `<useLegacyJit>` element to a configuration file overrides the registry settings, if they're present.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2caf-152">範例</span><span class="sxs-lookup"><span data-stu-id="c2caf-152">Example</span></span>  

<span data-ttu-id="c2caf-153">下列組態檔會停用新的 64 位元 JIT 編譯器的編譯，並改為使用舊版 64 位元 JIT 編譯器。</span><span class="sxs-lookup"><span data-stu-id="c2caf-153">The following configuration file disables compilation with the new 64-bit JIT compiler and instead uses the legacy 64-bit JIT compiler.</span></span>  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
  <runtime>  
    <useLegacyJit enabled="1" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c2caf-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2caf-154">See also</span></span>

- [<span data-ttu-id="c2caf-155">\<執行階段 > 項目</span><span class="sxs-lookup"><span data-stu-id="c2caf-155">\<runtime> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)
- [<span data-ttu-id="c2caf-156">\<configuration> 項目</span><span class="sxs-lookup"><span data-stu-id="c2caf-156">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)
- [<span data-ttu-id="c2caf-157">風險降低：新的 64 位元 JIT 編譯器</span><span class="sxs-lookup"><span data-stu-id="c2caf-157">Mitigation: New 64-bit JIT Compiler</span></span>](../../../../../docs/framework/migration-guide/mitigation-new-64-bit-jit-compiler.md)
