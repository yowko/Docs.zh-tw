---
title: <loadFromRemoteSources> 項目
ms.date: 05/24/2018
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7568129f30267b212737ec8aa688cf882e19bbff
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "55675305"
---
# <a name="loadfromremotesources-element"></a><span data-ttu-id="5d45a-102">\<loadFromRemoteSources > 項目</span><span class="sxs-lookup"><span data-stu-id="5d45a-102">\<loadFromRemoteSources> element</span></span>
<span data-ttu-id="5d45a-103">指定是否從遠端來源載入的組件，應該就會具有完全信任，在.NET Framework 4 和更新版本。</span><span class="sxs-lookup"><span data-stu-id="5d45a-103">Specifies whether assemblies loaded from remote sources should be granted full trust in .NET Framework 4 and later.</span></span>
  
> [!NOTE]
>  <span data-ttu-id="5d45a-104">如果您因為 Visual Studio 專案的錯誤清單或建置錯誤中的錯誤訊息導向這篇文章，請參閱[How to:使用 Visual Studio 中的 從 Web 組件](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="5d45a-104">If you were directed to this article because of an error message in the Visual Studio project error list or a build error, see [How to: Use an Assembly from the Web in Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100)).</span></span>  
  
 <span data-ttu-id="5d45a-105">\<configuration></span><span class="sxs-lookup"><span data-stu-id="5d45a-105">\<configuration></span></span>  
<span data-ttu-id="5d45a-106">\<執行階段 ></span><span class="sxs-lookup"><span data-stu-id="5d45a-106">\<runtime></span></span>  
<span data-ttu-id="5d45a-107">\<loadFromRemoteSources></span><span class="sxs-lookup"><span data-stu-id="5d45a-107">\<loadFromRemoteSources></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d45a-108">語法</span><span class="sxs-lookup"><span data-stu-id="5d45a-108">Syntax</span></span>  
  
```xml  
<loadFromRemoteSources    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5d45a-109">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="5d45a-109">Attributes and elements</span></span>
 <span data-ttu-id="5d45a-110">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="5d45a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5d45a-111">屬性</span><span class="sxs-lookup"><span data-stu-id="5d45a-111">Attributes</span></span>  
  
|<span data-ttu-id="5d45a-112">屬性</span><span class="sxs-lookup"><span data-stu-id="5d45a-112">Attribute</span></span>|<span data-ttu-id="5d45a-113">描述</span><span class="sxs-lookup"><span data-stu-id="5d45a-113">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="5d45a-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="5d45a-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="5d45a-115">指定是否會從遠端來源載入的組件，應該就會具有完全信任。</span><span class="sxs-lookup"><span data-stu-id="5d45a-115">Specifies whether an assembly that is loaded from a remote source should be granted full trust.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="5d45a-116">啟用的屬性</span><span class="sxs-lookup"><span data-stu-id="5d45a-116">enabled attribute</span></span>  
  
|<span data-ttu-id="5d45a-117">值</span><span class="sxs-lookup"><span data-stu-id="5d45a-117">Value</span></span>|<span data-ttu-id="5d45a-118">描述</span><span class="sxs-lookup"><span data-stu-id="5d45a-118">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="5d45a-119">請勿授與完全信任應用程式從遠端來源。</span><span class="sxs-lookup"><span data-stu-id="5d45a-119">Do not grant full trust to applications from remote sources.</span></span> <span data-ttu-id="5d45a-120">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="5d45a-120">This is the default.</span></span>|  
|`true`|<span data-ttu-id="5d45a-121">授與完全信任應用程式從遠端來源。</span><span class="sxs-lookup"><span data-stu-id="5d45a-121">Grant full trust to applications from remote sources.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5d45a-122">子元素</span><span class="sxs-lookup"><span data-stu-id="5d45a-122">Child elements</span></span>  
 <span data-ttu-id="5d45a-123">無。</span><span class="sxs-lookup"><span data-stu-id="5d45a-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5d45a-124">父元素</span><span class="sxs-lookup"><span data-stu-id="5d45a-124">Parent elements</span></span>  
  
|<span data-ttu-id="5d45a-125">元素</span><span class="sxs-lookup"><span data-stu-id="5d45a-125">Element</span></span>|<span data-ttu-id="5d45a-126">描述</span><span class="sxs-lookup"><span data-stu-id="5d45a-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5d45a-127">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="5d45a-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="5d45a-128">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="5d45a-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d45a-129">備註</span><span class="sxs-lookup"><span data-stu-id="5d45a-129">Remarks</span></span>

<span data-ttu-id="5d45a-130">在.NET Framework 3.5 和更早版本中，如果您從遠端位置，載入組件的組件中的程式碼將取決於從其載入該區域的授權集的部分信任中執行。</span><span class="sxs-lookup"><span data-stu-id="5d45a-130">In the .NET Framework 3.5 and earlier versions, if you load an assembly from a remote location, code in the assembly runs in partial trust with a grant set that depends on the zone from which it is loaded.</span></span> <span data-ttu-id="5d45a-131">比方說，如果您從網站載入組件，它會載入 [網際網路] 區域，並授與網際網路權限集合。</span><span class="sxs-lookup"><span data-stu-id="5d45a-131">For example, if you load an assembly from a website, it is loaded into the Internet zone and granted the Internet permission set.</span></span> <span data-ttu-id="5d45a-132">換句話說，它在網際網路沙箱中執行。</span><span class="sxs-lookup"><span data-stu-id="5d45a-132">In other words, it executes in an Internet sandbox.</span></span>

<span data-ttu-id="5d45a-133">從.NET Framework 4 開始，程式碼存取安全性 (CAS) 原則已停用，並已載入以完全信任組件。</span><span class="sxs-lookup"><span data-stu-id="5d45a-133">Starting with the .NET Framework 4, code access security (CAS) policy is disabled and assemblies are loaded in full trust.</span></span> <span data-ttu-id="5d45a-134">一般情況下，這會授與完全信任組件載入<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>先前已沙箱化的方法。</span><span class="sxs-lookup"><span data-stu-id="5d45a-134">Ordinarily, this would grant full trust to assemblies loaded with the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> method that previously had been sandboxed.</span></span> <span data-ttu-id="5d45a-135">若要避免這個問題，預設會停用從遠端來源載入的組件中執行程式碼的能力。</span><span class="sxs-lookup"><span data-stu-id="5d45a-135">To prevent this, the ability to run code in assemblies loaded from a remote source is disabled by default.</span></span> <span data-ttu-id="5d45a-136">根據預設，如果您嘗試載入遠端組件，<xref:System.IO.FileLoadException>像就會擲回下列例外狀況訊息：</span><span class="sxs-lookup"><span data-stu-id="5d45a-136">By default, if you attempt to load a remote assembly, a <xref:System.IO.FileLoadException> with an exception message like the following is thrown:</span></span>

```text
System.IO.FileNotFoundException: Could not load file or assembly 'file:assem.dll' or one of its dependencies. Operation is not supported. 
(Exception from HRESULT: 0x80131515)
File name: 'file:assem.dll' ---> 
System.NotSupportedException: An attempt was made to load an assembly from a network location which would have caused the assembly 
to be sandboxed in previous versions of the .NET Framework. This release of the .NET Framework does not enable CAS policy by default, 
so this load may be dangerous. If this load is not intended to sandbox the assembly, please enable the loadFromRemoteSources switch. 
```

<span data-ttu-id="5d45a-137">若要載入的組件，並執行其程式碼，您必須使用下列其中一個：</span><span class="sxs-lookup"><span data-stu-id="5d45a-137">To load the assembly and execute its code, you must either:</span></span>

- <span data-ttu-id="5d45a-138">組件明確建立沙箱 (請參閱[How to:在沙箱中執行部分信任程式碼](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md))。</span><span class="sxs-lookup"><span data-stu-id="5d45a-138">Explicitly create a sandbox for the assembly (see [How to: Run Partially Trusted Code in a Sandbox](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)).</span></span>

- <span data-ttu-id="5d45a-139">以完全信任執行組件的程式碼。</span><span class="sxs-lookup"><span data-stu-id="5d45a-139">Run the assembly's code in full trust.</span></span> <span data-ttu-id="5d45a-140">您可以設定`<loadFromRemoteSources>`項目。</span><span class="sxs-lookup"><span data-stu-id="5d45a-140">You do this by configuring the `<loadFromRemoteSources>` element.</span></span> <span data-ttu-id="5d45a-141">它可讓您指定在舊版.NET Framework 中的部分信任中執行的組件現在在.NET Framework 4 及更新版本中的完全信任中執行。</span><span class="sxs-lookup"><span data-stu-id="5d45a-141">It lets you specify that the assemblies that run in partial trust in earlier versions of the .NET Framework now run in full trust in the .NET Framework 4 and later versions.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5d45a-142">如果組件不應在完全信任中執行，不會設定這個組態項目。</span><span class="sxs-lookup"><span data-stu-id="5d45a-142">If the assembly should not run in full trust, do not set this configuration element.</span></span> <span data-ttu-id="5d45a-143">反而是建立沙箱<xref:System.AppDomain>要載入的組件。</span><span class="sxs-lookup"><span data-stu-id="5d45a-143">Instead, create a sandboxed <xref:System.AppDomain> in which to load the assembly.</span></span>

<span data-ttu-id="5d45a-144">`enabled`屬性`<loadFromRemoteSources>`項目是有效僅當程式碼存取安全性 (CAS) 已停用。</span><span class="sxs-lookup"><span data-stu-id="5d45a-144">The `enabled` attribute for the `<loadFromRemoteSources>` element is effective only when code access security (CAS) is disabled.</span></span> <span data-ttu-id="5d45a-145">根據預設，已停用在.NET Framework 4 和更新版本的 CAS 原則。</span><span class="sxs-lookup"><span data-stu-id="5d45a-145">By default, CAS policy is disabled in the .NET Framework 4 and later versions.</span></span> <span data-ttu-id="5d45a-146">如果您設定`enabled`至`true`，遠端組件都會授予完全信任。</span><span class="sxs-lookup"><span data-stu-id="5d45a-146">If you set `enabled` to `true`, remote assemblies are granted full trust.</span></span>

<span data-ttu-id="5d45a-147">如果`enabled`未設為`true`、<xref:System.IO.FileLoadException>在任一個下列條件時會擲回：</span><span class="sxs-lookup"><span data-stu-id="5d45a-147">If `enabled` is not set to `true`, a <xref:System.IO.FileLoadException> is thrown under the either of the following conditions:</span></span>

- <span data-ttu-id="5d45a-148">目前的沙箱行為是網域的不同於其行為在.NET Framework 3.5。</span><span class="sxs-lookup"><span data-stu-id="5d45a-148">The sandboxing behavior of the current domain is different from its behavior in the .NET Framework 3.5.</span></span> <span data-ttu-id="5d45a-149">這需要停用時，CAS 原則和目前網域不受限於沙箱。</span><span class="sxs-lookup"><span data-stu-id="5d45a-149">This requires CAS policy to be disabled, and the current domain not to be sandboxed.</span></span>

- <span data-ttu-id="5d45a-150">正在載入的組件不是來自`MyComputer`區域。</span><span class="sxs-lookup"><span data-stu-id="5d45a-150">The assembly being loaded is not from the `MyComputer` zone.</span></span>

<span data-ttu-id="5d45a-151">設定`<loadFromRemoteSources>`項目`true`可避免擲回這個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="5d45a-151">Setting the `<loadFromRemoteSources>` element to `true` prevents this exception from being thrown.</span></span> <span data-ttu-id="5d45a-152">它可讓您指定，您可以不依賴沙箱的 common language runtime 載入的組件的安全性，以及它們可以允許在執行完全信任。</span><span class="sxs-lookup"><span data-stu-id="5d45a-152">It enables you to specify that you are not relying on the common language runtime to sandbox the loaded assemblies for security, and that they can be allowed to execute in full trust.</span></span>

## <a name="notes"></a><span data-ttu-id="5d45a-153">注意</span><span class="sxs-lookup"><span data-stu-id="5d45a-153">Notes</span></span>

- <span data-ttu-id="5d45a-154">在.NET Framework 4.5 和更新版本中，區域網路共用上的組件以完全信任執行的預設值;您沒有啟用`<loadFromRemoteSources>`項目。</span><span class="sxs-lookup"><span data-stu-id="5d45a-154">In the .NET Framework 4.5 and later versions, assemblies on local network shares run in full trust by default; you do not have to enable the `<loadFromRemoteSources>` element.</span></span>

- <span data-ttu-id="5d45a-155">如果已從網路複製應用程式，即使該應用程式位於本機電腦上，Windows 仍會將它標示為 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="5d45a-155">If an application has been copied from the web, it is flagged by Windows as being a web application, even if it resides on the local computer.</span></span> <span data-ttu-id="5d45a-156">您可以藉由變更其檔案屬性，變更該名稱，或者您可以使用`<loadFromRemoteSources>`授與組件的項目完全信任。</span><span class="sxs-lookup"><span data-stu-id="5d45a-156">You can change that designation by changing its file properties, or you can use the `<loadFromRemoteSources>` element to grant the assembly full trust.</span></span> <span data-ttu-id="5d45a-157">或者，您可以使用 <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> 方法載入作業系統標示為從 Web 載入的本機組件。</span><span class="sxs-lookup"><span data-stu-id="5d45a-157">As an alternative, you can use the <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> method to load a local assembly that the operating system has flagged as having been loaded from the web.</span></span>

- <span data-ttu-id="5d45a-158">您可能會收到<xref:System.IO.FileLoadException>Windows Virtual PC 應用程式中執行的應用程式中。</span><span class="sxs-lookup"><span data-stu-id="5d45a-158">You may get a <xref:System.IO.FileLoadException> in an application that is running in a Windows Virtual PC application.</span></span> <span data-ttu-id="5d45a-159">當您嘗試從主機服務電腦上的連結資料夾載入檔案時，也可會發生。</span><span class="sxs-lookup"><span data-stu-id="5d45a-159">This can happen when you try to load a file from linked folders on the hosting computer.</span></span> <span data-ttu-id="5d45a-160">它也可能發生於您嘗試從透過連結的資料夾載入檔案[Remote Desktop Services](https://go.microsoft.com/fwlink/?LinkId=182775) (Terminal Services)。</span><span class="sxs-lookup"><span data-stu-id="5d45a-160">It can also occur when you try to load a file from a folder linked over [Remote Desktop Services](https://go.microsoft.com/fwlink/?LinkId=182775) (Terminal Services).</span></span> <span data-ttu-id="5d45a-161">若要避免例外狀況，請設定`enabled`至`true`。</span><span class="sxs-lookup"><span data-stu-id="5d45a-161">To avoid the exception, set `enabled` to `true`.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="5d45a-162">組態檔</span><span class="sxs-lookup"><span data-stu-id="5d45a-162">Configuration file</span></span>

<span data-ttu-id="5d45a-163">此項目通常用於應用程式組態檔，不過可以根據內容用於其他組態檔。</span><span class="sxs-lookup"><span data-stu-id="5d45a-163">This element is typically used in the application configuration file, but can be used in other configuration files depending upon the context.</span></span> <span data-ttu-id="5d45a-164">如需詳細資訊，請參閱文章[更多隱含的 CAS 原則用法： loadFromRemoteSources](https://go.microsoft.com/fwlink/p/?LinkId=266839) .NET Security 部落格中。</span><span class="sxs-lookup"><span data-stu-id="5d45a-164">For more information, see the article [More Implicit Uses of CAS Policy: loadFromRemoteSources](https://go.microsoft.com/fwlink/p/?LinkId=266839) in the .NET Security blog.</span></span>  

## <a name="example"></a><span data-ttu-id="5d45a-165">範例</span><span class="sxs-lookup"><span data-stu-id="5d45a-165">Example</span></span>

<span data-ttu-id="5d45a-166">下列範例示範如何從遠端來源載入的組件授與完全信任。</span><span class="sxs-lookup"><span data-stu-id="5d45a-166">The following example shows how to grant full trust to assemblies loaded from remote sources.</span></span>

```xml
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```

## <a name="see-also"></a><span data-ttu-id="5d45a-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5d45a-167">See also</span></span>

- [<span data-ttu-id="5d45a-168">更為隱含的 CAS 原則用法： loadFromRemoteSources</span><span class="sxs-lookup"><span data-stu-id="5d45a-168">More Implicit Uses of CAS Policy: loadFromRemoteSources</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=266839)
- [<span data-ttu-id="5d45a-169">如何：在沙箱中執行部分信任的程式碼</span><span class="sxs-lookup"><span data-stu-id="5d45a-169">How to: Run Partially Trusted Code in a Sandbox</span></span>](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
- [<span data-ttu-id="5d45a-170">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="5d45a-170">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="5d45a-171">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="5d45a-171">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>
