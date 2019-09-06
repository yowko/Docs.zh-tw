---
title: <loadFromRemoteSources> 項目
ms.date: 05/24/2018
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 83980d315c83aa5cc23944dbd271c29e0ed83206
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252472"
---
# <a name="loadfromremotesources-element"></a><span data-ttu-id="b14b6-102">\<loadFromRemoteSources > 元素</span><span class="sxs-lookup"><span data-stu-id="b14b6-102">\<loadFromRemoteSources> element</span></span>
<span data-ttu-id="b14b6-103">指定是否應將 .NET Framework 4 和更新版本中的完全信任授與從遠端來源載入的元件。</span><span class="sxs-lookup"><span data-stu-id="b14b6-103">Specifies whether assemblies loaded from remote sources should be granted full trust in .NET Framework 4 and later.</span></span>
  
> [!NOTE]
> <span data-ttu-id="b14b6-104">如果您因為 Visual Studio 專案錯誤清單中的錯誤訊息或組建錯誤而被導向本文，請參閱[如何：在 Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100))中使用來自 Web 的元件。</span><span class="sxs-lookup"><span data-stu-id="b14b6-104">If you were directed to this article because of an error message in the Visual Studio project error list or a build error, see [How to: Use an Assembly from the Web in Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100)).</span></span>  
  
<span data-ttu-id="b14b6-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b14b6-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b14b6-106">&nbsp;&nbsp;[ **\<執行時間 >** ](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="b14b6-106">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="b14b6-107">&nbsp;&nbsp;&nbsp;&nbsp; **\<loadFromRemoteSources >**</span><span class="sxs-lookup"><span data-stu-id="b14b6-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<loadFromRemoteSources>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b14b6-108">語法</span><span class="sxs-lookup"><span data-stu-id="b14b6-108">Syntax</span></span>  
  
```xml  
<loadFromRemoteSources    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b14b6-109">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="b14b6-109">Attributes and elements</span></span>
 <span data-ttu-id="b14b6-110">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="b14b6-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b14b6-111">屬性</span><span class="sxs-lookup"><span data-stu-id="b14b6-111">Attributes</span></span>  
  
|<span data-ttu-id="b14b6-112">屬性</span><span class="sxs-lookup"><span data-stu-id="b14b6-112">Attribute</span></span>|<span data-ttu-id="b14b6-113">描述</span><span class="sxs-lookup"><span data-stu-id="b14b6-113">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="b14b6-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="b14b6-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="b14b6-115">指定是否應授與從遠端來源載入的元件完全信任。</span><span class="sxs-lookup"><span data-stu-id="b14b6-115">Specifies whether an assembly that is loaded from a remote source should be granted full trust.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="b14b6-116">enabled 屬性</span><span class="sxs-lookup"><span data-stu-id="b14b6-116">enabled attribute</span></span>  
  
|<span data-ttu-id="b14b6-117">值</span><span class="sxs-lookup"><span data-stu-id="b14b6-117">Value</span></span>|<span data-ttu-id="b14b6-118">說明</span><span class="sxs-lookup"><span data-stu-id="b14b6-118">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="b14b6-119">請勿將完全信任授與遠端來源的應用程式。</span><span class="sxs-lookup"><span data-stu-id="b14b6-119">Do not grant full trust to applications from remote sources.</span></span> <span data-ttu-id="b14b6-120">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="b14b6-120">This is the default.</span></span>|  
|`true`|<span data-ttu-id="b14b6-121">授與從遠端來源對應用程式的完全信任。</span><span class="sxs-lookup"><span data-stu-id="b14b6-121">Grant full trust to applications from remote sources.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b14b6-122">子元素</span><span class="sxs-lookup"><span data-stu-id="b14b6-122">Child elements</span></span>  
 <span data-ttu-id="b14b6-123">無。</span><span class="sxs-lookup"><span data-stu-id="b14b6-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b14b6-124">父元素</span><span class="sxs-lookup"><span data-stu-id="b14b6-124">Parent elements</span></span>  
  
|<span data-ttu-id="b14b6-125">元素</span><span class="sxs-lookup"><span data-stu-id="b14b6-125">Element</span></span>|<span data-ttu-id="b14b6-126">描述</span><span class="sxs-lookup"><span data-stu-id="b14b6-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b14b6-127">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="b14b6-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="b14b6-128">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="b14b6-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b14b6-129">備註</span><span class="sxs-lookup"><span data-stu-id="b14b6-129">Remarks</span></span>

<span data-ttu-id="b14b6-130">在 .NET Framework 3.5 和更早版本中，如果您從遠端位置載入元件，則元件中的程式碼會以部分信任的方式執行，而該授權集是根據載入它的區域而定。</span><span class="sxs-lookup"><span data-stu-id="b14b6-130">In the .NET Framework 3.5 and earlier versions, if you load an assembly from a remote location, code in the assembly runs in partial trust with a grant set that depends on the zone from which it is loaded.</span></span> <span data-ttu-id="b14b6-131">例如，如果您從網站載入元件，則會將它載入至網際網路區域並授與網際網路許可權集合。</span><span class="sxs-lookup"><span data-stu-id="b14b6-131">For example, if you load an assembly from a website, it is loaded into the Internet zone and granted the Internet permission set.</span></span> <span data-ttu-id="b14b6-132">換句話說，它會在網際網路沙箱中執行。</span><span class="sxs-lookup"><span data-stu-id="b14b6-132">In other words, it executes in an Internet sandbox.</span></span>

<span data-ttu-id="b14b6-133">從 .NET Framework 4 開始，會停用代碼啟用安全性（CAS）原則，並以完全信任的方式載入元件。</span><span class="sxs-lookup"><span data-stu-id="b14b6-133">Starting with the .NET Framework 4, code access security (CAS) policy is disabled and assemblies are loaded in full trust.</span></span> <span data-ttu-id="b14b6-134">一般來說，這會授與完全信任給以先前已<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>沙箱化的方法所載入的元件。</span><span class="sxs-lookup"><span data-stu-id="b14b6-134">Ordinarily, this would grant full trust to assemblies loaded with the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> method that previously had been sandboxed.</span></span> <span data-ttu-id="b14b6-135">為了避免這種情況，預設會停用在從遠端來源載入的元件中執行程式碼的功能。</span><span class="sxs-lookup"><span data-stu-id="b14b6-135">To prevent this, the ability to run code in assemblies loaded from a remote source is disabled by default.</span></span> <span data-ttu-id="b14b6-136">根據預設，如果您嘗試載入遠端元件， <xref:System.IO.FileLoadException>則會擲回具有類似如下的例外狀況訊息：</span><span class="sxs-lookup"><span data-stu-id="b14b6-136">By default, if you attempt to load a remote assembly, a <xref:System.IO.FileLoadException> with an exception message like the following is thrown:</span></span>

```text
System.IO.FileNotFoundException: Could not load file or assembly 'file:assem.dll' or one of its dependencies. Operation is not supported. 
(Exception from HRESULT: 0x80131515)
File name: 'file:assem.dll' ---> 
System.NotSupportedException: An attempt was made to load an assembly from a network location which would have caused the assembly 
to be sandboxed in previous versions of the .NET Framework. This release of the .NET Framework does not enable CAS policy by default, 
so this load may be dangerous. If this load is not intended to sandbox the assembly, please enable the loadFromRemoteSources switch. 
```

<span data-ttu-id="b14b6-137">若要載入元件並執行其程式碼，您必須執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="b14b6-137">To load the assembly and execute its code, you must either:</span></span>

- <span data-ttu-id="b14b6-138">明確建立元件的沙箱（請參閱[如何：在沙箱](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)中執行部分信任的程式碼）。</span><span class="sxs-lookup"><span data-stu-id="b14b6-138">Explicitly create a sandbox for the assembly (see [How to: Run Partially Trusted Code in a Sandbox](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)).</span></span>

- <span data-ttu-id="b14b6-139">以完全信任的方式執行元件的程式碼。</span><span class="sxs-lookup"><span data-stu-id="b14b6-139">Run the assembly's code in full trust.</span></span> <span data-ttu-id="b14b6-140">您可以藉由設定`<loadFromRemoteSources>`元素來完成此動作。</span><span class="sxs-lookup"><span data-stu-id="b14b6-140">You do this by configuring the `<loadFromRemoteSources>` element.</span></span> <span data-ttu-id="b14b6-141">它可讓您指定在舊版 .NET Framework 中以部分信任方式執行的元件，現在會在 .NET Framework 4 和更新版本中以完全信任的方式執行。</span><span class="sxs-lookup"><span data-stu-id="b14b6-141">It lets you specify that the assemblies that run in partial trust in earlier versions of the .NET Framework now run in full trust in the .NET Framework 4 and later versions.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b14b6-142">如果元件不應在完全信任中執行，請不要設定此 configuration 元素。</span><span class="sxs-lookup"><span data-stu-id="b14b6-142">If the assembly should not run in full trust, do not set this configuration element.</span></span> <span data-ttu-id="b14b6-143">相反地，請建立<xref:System.AppDomain>用來載入元件的沙箱。</span><span class="sxs-lookup"><span data-stu-id="b14b6-143">Instead, create a sandboxed <xref:System.AppDomain> in which to load the assembly.</span></span>

<span data-ttu-id="b14b6-144">只有`enabled`在停用`<loadFromRemoteSources>`代碼啟用安全性（CAS）時，元素的屬性才有效。</span><span class="sxs-lookup"><span data-stu-id="b14b6-144">The `enabled` attribute for the `<loadFromRemoteSources>` element is effective only when code access security (CAS) is disabled.</span></span> <span data-ttu-id="b14b6-145">預設會停用 .NET Framework 4 和更新版本中的 CAS 原則。</span><span class="sxs-lookup"><span data-stu-id="b14b6-145">By default, CAS policy is disabled in the .NET Framework 4 and later versions.</span></span> <span data-ttu-id="b14b6-146">如果您將`enabled`設定`true`為，遠端元件會被授與完全信任。</span><span class="sxs-lookup"><span data-stu-id="b14b6-146">If you set `enabled` to `true`, remote assemblies are granted full trust.</span></span>

<span data-ttu-id="b14b6-147">如果`enabled`未設定為`true`， <xref:System.IO.FileLoadException>則會在下列任一情況下擲回：</span><span class="sxs-lookup"><span data-stu-id="b14b6-147">If `enabled` is not set to `true`, a <xref:System.IO.FileLoadException> is thrown under the either of the following conditions:</span></span>

- <span data-ttu-id="b14b6-148">目前網域的沙箱行為與其在 .NET Framework 3.5 中的行為不同。</span><span class="sxs-lookup"><span data-stu-id="b14b6-148">The sandboxing behavior of the current domain is different from its behavior in the .NET Framework 3.5.</span></span> <span data-ttu-id="b14b6-149">這需要停用 CAS 原則，而目前的網域則不會進行沙箱處理。</span><span class="sxs-lookup"><span data-stu-id="b14b6-149">This requires CAS policy to be disabled, and the current domain not to be sandboxed.</span></span>

- <span data-ttu-id="b14b6-150">正在載入的元件不是來自`MyComputer`區域。</span><span class="sxs-lookup"><span data-stu-id="b14b6-150">The assembly being loaded is not from the `MyComputer` zone.</span></span>

<span data-ttu-id="b14b6-151">設定元素以`true`防止擲回這個例外狀況。 `<loadFromRemoteSources>`</span><span class="sxs-lookup"><span data-stu-id="b14b6-151">Setting the `<loadFromRemoteSources>` element to `true` prevents this exception from being thrown.</span></span> <span data-ttu-id="b14b6-152">它可讓您指定您不依賴 common language runtime 將載入的元件沙箱處理為安全性，而且可以允許在完全信任的情況下執行。</span><span class="sxs-lookup"><span data-stu-id="b14b6-152">It enables you to specify that you are not relying on the common language runtime to sandbox the loaded assemblies for security, and that they can be allowed to execute in full trust.</span></span>

## <a name="notes"></a><span data-ttu-id="b14b6-153">注意</span><span class="sxs-lookup"><span data-stu-id="b14b6-153">Notes</span></span>

- <span data-ttu-id="b14b6-154">在 .NET Framework 4.5 和更新版本中，本機網路共用上的元件預設會以完全信任的方式執行;您不需要啟用`<loadFromRemoteSources>`元素。</span><span class="sxs-lookup"><span data-stu-id="b14b6-154">In the .NET Framework 4.5 and later versions, assemblies on local network shares run in full trust by default; you do not have to enable the `<loadFromRemoteSources>` element.</span></span>

- <span data-ttu-id="b14b6-155">如果已從網路複製應用程式，即使該應用程式位於本機電腦上，Windows 仍會將它標示為 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="b14b6-155">If an application has been copied from the web, it is flagged by Windows as being a web application, even if it resides on the local computer.</span></span> <span data-ttu-id="b14b6-156">您可以藉由變更其檔案屬性來變更該指定，也可以使用`<loadFromRemoteSources>`元素來授與元件完全信任。</span><span class="sxs-lookup"><span data-stu-id="b14b6-156">You can change that designation by changing its file properties, or you can use the `<loadFromRemoteSources>` element to grant the assembly full trust.</span></span> <span data-ttu-id="b14b6-157">或者，您可以使用 <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> 方法載入作業系統標示為從 Web 載入的本機組件。</span><span class="sxs-lookup"><span data-stu-id="b14b6-157">As an alternative, you can use the <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> method to load a local assembly that the operating system has flagged as having been loaded from the web.</span></span>

- <span data-ttu-id="b14b6-158">您可能會<xref:System.IO.FileLoadException>在 Windows 虛擬 PC 應用程式中執行的應用程式中取得。</span><span class="sxs-lookup"><span data-stu-id="b14b6-158">You may get a <xref:System.IO.FileLoadException> in an application that is running in a Windows Virtual PC application.</span></span> <span data-ttu-id="b14b6-159">當您嘗試從主控電腦上的連結資料夾載入檔案時，就會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="b14b6-159">This can happen when you try to load a file from linked folders on the hosting computer.</span></span> <span data-ttu-id="b14b6-160">當您嘗試從連結于[遠端桌面服務](https://go.microsoft.com/fwlink/?LinkId=182775)（終端機服務）的資料夾載入檔案時，也可能會發生此問題。</span><span class="sxs-lookup"><span data-stu-id="b14b6-160">It can also occur when you try to load a file from a folder linked over [Remote Desktop Services](https://go.microsoft.com/fwlink/?LinkId=182775) (Terminal Services).</span></span> <span data-ttu-id="b14b6-161">若要避免例外狀況， `enabled`請`true`將設定為。</span><span class="sxs-lookup"><span data-stu-id="b14b6-161">To avoid the exception, set `enabled` to `true`.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="b14b6-162">組態檔</span><span class="sxs-lookup"><span data-stu-id="b14b6-162">Configuration file</span></span>

<span data-ttu-id="b14b6-163">此項目通常用於應用程式組態檔，不過可以根據內容用於其他組態檔。</span><span class="sxs-lookup"><span data-stu-id="b14b6-163">This element is typically used in the application configuration file, but can be used in other configuration files depending upon the context.</span></span> <span data-ttu-id="b14b6-164">如需詳細資訊，請參閱 .NET 安全性 blog 中的 < [CAS 原則的更多隱含用法： loadFromRemoteSources 一](https://go.microsoft.com/fwlink/p/?LinkId=266839)文。</span><span class="sxs-lookup"><span data-stu-id="b14b6-164">For more information, see the article [More Implicit Uses of CAS Policy: loadFromRemoteSources](https://go.microsoft.com/fwlink/p/?LinkId=266839) in the .NET Security blog.</span></span>  

## <a name="example"></a><span data-ttu-id="b14b6-165">範例</span><span class="sxs-lookup"><span data-stu-id="b14b6-165">Example</span></span>

<span data-ttu-id="b14b6-166">下列範例顯示如何將完全信任授與從遠端來源載入的元件。</span><span class="sxs-lookup"><span data-stu-id="b14b6-166">The following example shows how to grant full trust to assemblies loaded from remote sources.</span></span>

```xml
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```

## <a name="see-also"></a><span data-ttu-id="b14b6-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b14b6-167">See also</span></span>

- [<span data-ttu-id="b14b6-168">CAS 原則的更多隱含用法： loadFromRemoteSources</span><span class="sxs-lookup"><span data-stu-id="b14b6-168">More Implicit Uses of CAS Policy: loadFromRemoteSources</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=266839)
- [<span data-ttu-id="b14b6-169">如何：在沙箱中執行部分信任的程式碼</span><span class="sxs-lookup"><span data-stu-id="b14b6-169">How to: Run Partially Trusted Code in a Sandbox</span></span>](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
- [<span data-ttu-id="b14b6-170">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="b14b6-170">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="b14b6-171">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="b14b6-171">Configuration File Schema</span></span>](../index.md)
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>
