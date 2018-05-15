---
title: '&lt;loadFromRemoteSources&gt;項目'
ms.date: 03/30/2017
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f0d442f71a0e2fc7deacd9aaa02cfba7b66f2349
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltloadfromremotesourcesgt-element"></a><span data-ttu-id="f6d59-102">&lt;loadFromRemoteSources&gt;項目</span><span class="sxs-lookup"><span data-stu-id="f6d59-102">&lt;loadFromRemoteSources&gt; Element</span></span>
<span data-ttu-id="f6d59-103">指定是否從遠端來源的組件應該被授與完全信任。</span><span class="sxs-lookup"><span data-stu-id="f6d59-103">Specifies whether assemblies from remote sources should be granted full trust.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f6d59-104">如果您已導向至本主題，因為 Visual Studio 專案錯誤清單或建置錯誤中的錯誤訊息，請參閱[How to： 使用 Visual Studio 中的 從 Web 組件](http://msdn.microsoft.com/library/d8635b63-89a0-41aa-90f4-f351b2111070)。</span><span class="sxs-lookup"><span data-stu-id="f6d59-104">If you were directed to this topic because of an error message in the Visual Studio project error list or a build error, see [How to: Use an Assembly from the Web in Visual Studio](http://msdn.microsoft.com/library/d8635b63-89a0-41aa-90f4-f351b2111070).</span></span>  
  
 <span data-ttu-id="f6d59-105">\<configuration></span><span class="sxs-lookup"><span data-stu-id="f6d59-105">\<configuration></span></span>  
<span data-ttu-id="f6d59-106">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="f6d59-106">\<runtime></span></span>  
<span data-ttu-id="f6d59-107">\<loadFromRemoteSources></span><span class="sxs-lookup"><span data-stu-id="f6d59-107">\<loadFromRemoteSources></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6d59-108">語法</span><span class="sxs-lookup"><span data-stu-id="f6d59-108">Syntax</span></span>  
  
```xml  
<loadFromRemoteSources    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f6d59-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f6d59-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f6d59-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="f6d59-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f6d59-111">屬性</span><span class="sxs-lookup"><span data-stu-id="f6d59-111">Attributes</span></span>  
  
|<span data-ttu-id="f6d59-112">屬性</span><span class="sxs-lookup"><span data-stu-id="f6d59-112">Attribute</span></span>|<span data-ttu-id="f6d59-113">描述</span><span class="sxs-lookup"><span data-stu-id="f6d59-113">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="f6d59-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="f6d59-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="f6d59-115">指定是否會從遠端來源載入的組件應該被授與完全信任。</span><span class="sxs-lookup"><span data-stu-id="f6d59-115">Specifies whether an assembly that is loaded from remote sources should be granted full trust.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="f6d59-116">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="f6d59-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="f6d59-117">值</span><span class="sxs-lookup"><span data-stu-id="f6d59-117">Value</span></span>|<span data-ttu-id="f6d59-118">描述</span><span class="sxs-lookup"><span data-stu-id="f6d59-118">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="f6d59-119">請勿授與完全信任的應用程式從遠端來源。</span><span class="sxs-lookup"><span data-stu-id="f6d59-119">Do not grant full trust to applications from remote sources.</span></span> <span data-ttu-id="f6d59-120">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="f6d59-120">This is the default.</span></span>|  
|`true`|<span data-ttu-id="f6d59-121">授與完全信任應用程式從遠端來源。</span><span class="sxs-lookup"><span data-stu-id="f6d59-121">Grant full trust to applications from remote sources.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f6d59-122">子項目</span><span class="sxs-lookup"><span data-stu-id="f6d59-122">Child Elements</span></span>  
 <span data-ttu-id="f6d59-123">無。</span><span class="sxs-lookup"><span data-stu-id="f6d59-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f6d59-124">父項目</span><span class="sxs-lookup"><span data-stu-id="f6d59-124">Parent Elements</span></span>  
  
|<span data-ttu-id="f6d59-125">項目</span><span class="sxs-lookup"><span data-stu-id="f6d59-125">Element</span></span>|<span data-ttu-id="f6d59-126">描述</span><span class="sxs-lookup"><span data-stu-id="f6d59-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="f6d59-127">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="f6d59-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="f6d59-128">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="f6d59-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f6d59-129">備註</span><span class="sxs-lookup"><span data-stu-id="f6d59-129">Remarks</span></span>  
 <span data-ttu-id="f6d59-130">在.NET Framework 3.5 版和更早版本中，如果您從遠端位置，載入組件的組件就會執行部分信任使用取決於它已載入該區域的授權集。</span><span class="sxs-lookup"><span data-stu-id="f6d59-130">In the .NET Framework version 3.5 and earlier versions, if you loaded an assembly from a remote location, the assembly would run partially trusted with a grant set that depended on the zone in which it was loaded.</span></span> <span data-ttu-id="f6d59-131">例如，如果您從網站載入組件，該組件就會載入至網際網路區域，並取得網際網路權限集。</span><span class="sxs-lookup"><span data-stu-id="f6d59-131">For example, if you loaded an assembly from a website, it was loaded into the Internet zone and granted the Internet permission set.</span></span> <span data-ttu-id="f6d59-132">換句話說，它在網際網路沙箱中執行。</span><span class="sxs-lookup"><span data-stu-id="f6d59-132">In other words, it executed in an Internet sandbox.</span></span> <span data-ttu-id="f6d59-133">如果您嘗試在執行該組件[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]和更新版本中，會擲回例外狀況，則您必須明確地建立沙箱組件 (請參閱[如何： 執行部分信任程式碼在沙箱中](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md))，或在完全信任中執行。</span><span class="sxs-lookup"><span data-stu-id="f6d59-133">If you try to run that assembly in the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] and later versions, an exception is thrown; you must either explicitly create a sandbox for the assembly (see [How to: Run Partially Trusted Code in a Sandbox](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)), or run it in full trust.</span></span>  
  
 <span data-ttu-id="f6d59-134">`<loadFromRemoteSources>` 項目可讓您指定在 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] (含) 以後版本中，以完全信任方式執行先前在舊版 .NET Framework 中以部分信任方式執行的組件。</span><span class="sxs-lookup"><span data-stu-id="f6d59-134">The `<loadFromRemoteSources>` element lets you specify that the assemblies that would have run partially trusted in earlier versions of the .NET Framework are to be run fully trusted in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] and later versions.</span></span> <span data-ttu-id="f6d59-135">根據預設，遠端組件不會在 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] (含) 以後版本中執行。</span><span class="sxs-lookup"><span data-stu-id="f6d59-135">By default, remote assemblies do not run in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] and later.</span></span> <span data-ttu-id="f6d59-136">若要執行遠端組件，您必須以完全信任方式執行該組件，或是建立要在其中執行該組件的沙箱 <xref:System.AppDomain>。</span><span class="sxs-lookup"><span data-stu-id="f6d59-136">To run a remote assembly, you must either run it as fully trusted or create a sandboxed <xref:System.AppDomain> in which to run it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f6d59-137">在 [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)] 中，區域網路共用上的組件預設會以完全信任方式執行，因此您不需要啟用 `<loadFromRemoteSources>` 項目。</span><span class="sxs-lookup"><span data-stu-id="f6d59-137">In the [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)], assemblies on local network shares are run as full trust by default; you do not have to enable the `<loadFromRemoteSources>` element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f6d59-138">如果已從網路複製應用程式，即使該應用程式位於本機電腦上，Windows 仍會將它標示為 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="f6d59-138">If an application has been copied from the web, it is flagged by Windows as being a web application, even if it resides on the local computer.</span></span> <span data-ttu-id="f6d59-139">您可以變更該指定變更檔案屬性，或者您可以使用`<loadFromRemoteSources>`授與組件的項目完全信任。</span><span class="sxs-lookup"><span data-stu-id="f6d59-139">You can change that designation by changing the file properties, or you can use the `<loadFromRemoteSources>` element to grant the assembly full trust.</span></span> <span data-ttu-id="f6d59-140">或者，您可以使用 <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> 方法載入作業系統標示為從 Web 載入的本機組件。</span><span class="sxs-lookup"><span data-stu-id="f6d59-140">As an alternative, you can use the <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> method to load a local assembly that the operating system has flagged as having been loaded from the web.</span></span>  
  
 <span data-ttu-id="f6d59-141">`enabled`屬性只有在程式碼存取安全性 (CAS) 已停用時，才這個項目才有效。</span><span class="sxs-lookup"><span data-stu-id="f6d59-141">The `enabled` attribute for this element is effective only when code access security (CAS) is disabled.</span></span> <span data-ttu-id="f6d59-142">根據預設，CAS 原則中已停用[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]和更新版本。</span><span class="sxs-lookup"><span data-stu-id="f6d59-142">By default, CAS policy is disabled in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] and later versions.</span></span> <span data-ttu-id="f6d59-143">如果您設定`enabled`至`true`，遠端應用程式會授與完全信任。</span><span class="sxs-lookup"><span data-stu-id="f6d59-143">If you set `enabled` to `true`, remote applications are granted full trust.</span></span>  
  
 <span data-ttu-id="f6d59-144">如果`<loadFromRemoteSources>``enabled`未設定為`true`，在下列情況下擲回例外狀況：</span><span class="sxs-lookup"><span data-stu-id="f6d59-144">If `<loadFromRemoteSources>``enabled` is not set to `true`, an exception is thrown under the following conditions:</span></span>  
  
-   <span data-ttu-id="f6d59-145">目前網域的沙箱化處理行為是在其行為與不同[!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f6d59-145">The sandboxing behavior of the current domain is different from its behavior in the [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)].</span></span> <span data-ttu-id="f6d59-146">這需要停用時，CAS 原則和目前的網域為沙箱化。</span><span class="sxs-lookup"><span data-stu-id="f6d59-146">This requires CAS policy to be disabled, and the current domain not to be sandboxed.</span></span>  
  
-   <span data-ttu-id="f6d59-147">正在載入的組件不是來自`MyComputer`區域。</span><span class="sxs-lookup"><span data-stu-id="f6d59-147">The assembly being loaded is not from the `MyComputer` zone.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f6d59-148">您可能會收到<xref:System.IO.FileLoadException>Windows Virtual PC 應用程式，當您嘗試載入的檔案從主機服務電腦上的連結資料夾中。</span><span class="sxs-lookup"><span data-stu-id="f6d59-148">You may get a <xref:System.IO.FileLoadException> in a Windows Virtual PC application when you try to load a file from linked folders on the hosting computer.</span></span> <span data-ttu-id="f6d59-149">當您嘗試從透過連結的資料夾載入檔案時，也可能發生此錯誤[遠端桌面服務](http://go.microsoft.com/fwlink/?LinkId=182775)（終端機服務）。</span><span class="sxs-lookup"><span data-stu-id="f6d59-149">This error may also occur when you try to load a file from a folder linked over [Remote Desktop Services](http://go.microsoft.com/fwlink/?LinkId=182775) (Terminal Services).</span></span> <span data-ttu-id="f6d59-150">若要避免此例外狀況，將`enabled`至`true`。</span><span class="sxs-lookup"><span data-stu-id="f6d59-150">To avoid the exception, set `enabled` to `true`.</span></span>  
  
 <span data-ttu-id="f6d59-151">設定`<loadFromRemoteSources>`元素`true`可避免擲回這個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f6d59-151">Setting the `<loadFromRemoteSources>` element to `true` prevents this exception from being thrown.</span></span> <span data-ttu-id="f6d59-152">它可讓您指定，您不依賴沙箱 common language runtime 載入的組件的安全性，和它們可以允許將當做執行完全信任。</span><span class="sxs-lookup"><span data-stu-id="f6d59-152">It enables you to specify that you are not relying on the common language runtime to sandbox the loaded assemblies for security, and that they can be allowed to execute as full trust.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f6d59-153">如果組件不在完全信任執行，請勿設定這個組態項目。</span><span class="sxs-lookup"><span data-stu-id="f6d59-153">If the assembly should not run in full trust, do not set this configuration element.</span></span> <span data-ttu-id="f6d59-154">請改為建立的沙箱<xref:System.AppDomain>要載入的組件。</span><span class="sxs-lookup"><span data-stu-id="f6d59-154">Instead, create a sandboxed <xref:System.AppDomain> in which to load the assembly.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="f6d59-155">組態檔</span><span class="sxs-lookup"><span data-stu-id="f6d59-155">Configuration File</span></span>  
 <span data-ttu-id="f6d59-156">此項目通常用於應用程式組態檔，不過可以根據內容用於其他組態檔。</span><span class="sxs-lookup"><span data-stu-id="f6d59-156">This element is typically used in the application configuration file, but can be used in other configuration files depending upon the context.</span></span> <span data-ttu-id="f6d59-157">如需詳細資訊，請參閱文章[詳細隱含使用 CAS 原則： loadFromRemoteSources](http://go.microsoft.com/fwlink/p/?LinkId=266839) .NET 安全性部落格。</span><span class="sxs-lookup"><span data-stu-id="f6d59-157">For more information, see the article [More Implicit Uses of CAS Policy: loadFromRemoteSources](http://go.microsoft.com/fwlink/p/?LinkId=266839) in the .NET Security blog.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6d59-158">範例</span><span class="sxs-lookup"><span data-stu-id="f6d59-158">Example</span></span>  
 <span data-ttu-id="f6d59-159">下列範例會示範如何從遠端來源授與完全信任的應用程式。</span><span class="sxs-lookup"><span data-stu-id="f6d59-159">The following example shows how to grant full trust to applications from remote sources.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f6d59-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f6d59-160">See Also</span></span>  
 [<span data-ttu-id="f6d59-161">更隱含使用了 CAS 原則： loadFromRemoteSources</span><span class="sxs-lookup"><span data-stu-id="f6d59-161">More Implicit Uses of CAS Policy: loadFromRemoteSources</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=266839)  
 [<span data-ttu-id="f6d59-162">如何：在沙箱中執行部分信任的程式碼</span><span class="sxs-lookup"><span data-stu-id="f6d59-162">How to: Run Partially Trusted Code in a Sandbox</span></span>](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)  
 [<span data-ttu-id="f6d59-163">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="f6d59-163">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="f6d59-164">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="f6d59-164">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
