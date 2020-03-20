---
title: <loadFromRemoteSources> 項目
ms.date: 05/24/2018
helpviewer_keywords:
- loadFromRemoteSources element
- <loadFromRemoteSources> element
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
ms.openlocfilehash: a0dcffe378cdd09de0fbd8f0a6ef0635c033fd9c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154058"
---
# <a name="loadfromremotesources-element"></a><span data-ttu-id="2abef-102">\<負載從遠端源>元素</span><span class="sxs-lookup"><span data-stu-id="2abef-102">\<loadFromRemoteSources> element</span></span>
<span data-ttu-id="2abef-103">指定是否應授予從遠端源載入的程式集對 .NET 框架 4 和更高版本完全信任。</span><span class="sxs-lookup"><span data-stu-id="2abef-103">Specifies whether assemblies loaded from remote sources should be granted full trust in .NET Framework 4 and later.</span></span>
  
> [!NOTE]
> <span data-ttu-id="2abef-104">如果您因為 Visual Studio 專案錯誤清單中的錯誤訊息或建置錯誤而被定向到本文，請參閱["如何：在視覺化工作室中的 Web 中使用程式集](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100))"。</span><span class="sxs-lookup"><span data-stu-id="2abef-104">If you were directed to this article because of an error message in the Visual Studio project error list or a build error, see [How to: Use an Assembly from the Web in Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ee890038(v=vs.100)).</span></span>  
  
<span data-ttu-id="2abef-105">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2abef-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2abef-106">&nbsp;&nbsp;[**\<運行時>**](runtime-element.md)</span><span class="sxs-lookup"><span data-stu-id="2abef-106">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="2abef-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<負載從遠端源>**</span><span class="sxs-lookup"><span data-stu-id="2abef-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<loadFromRemoteSources>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2abef-108">語法</span><span class="sxs-lookup"><span data-stu-id="2abef-108">Syntax</span></span>  
  
```xml  
<loadFromRemoteSources
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2abef-109">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="2abef-109">Attributes and elements</span></span>
 <span data-ttu-id="2abef-110">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="2abef-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2abef-111">屬性</span><span class="sxs-lookup"><span data-stu-id="2abef-111">Attributes</span></span>  
  
|<span data-ttu-id="2abef-112">屬性</span><span class="sxs-lookup"><span data-stu-id="2abef-112">Attribute</span></span>|<span data-ttu-id="2abef-113">描述</span><span class="sxs-lookup"><span data-stu-id="2abef-113">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="2abef-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="2abef-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="2abef-115">指定是否應授予從遠端源載入的程式集完全信任。</span><span class="sxs-lookup"><span data-stu-id="2abef-115">Specifies whether an assembly that is loaded from a remote source should be granted full trust.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="2abef-116">啟用的屬性</span><span class="sxs-lookup"><span data-stu-id="2abef-116">enabled attribute</span></span>  
  
|<span data-ttu-id="2abef-117">值</span><span class="sxs-lookup"><span data-stu-id="2abef-117">Value</span></span>|<span data-ttu-id="2abef-118">描述</span><span class="sxs-lookup"><span data-stu-id="2abef-118">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="2abef-119">不要對來自遠端源的應用程式授予完全信任。</span><span class="sxs-lookup"><span data-stu-id="2abef-119">Do not grant full trust to applications from remote sources.</span></span> <span data-ttu-id="2abef-120">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="2abef-120">This is the default.</span></span>|  
|`true`|<span data-ttu-id="2abef-121">完全信任來自遠端源的應用程式。</span><span class="sxs-lookup"><span data-stu-id="2abef-121">Grant full trust to applications from remote sources.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2abef-122">子元素</span><span class="sxs-lookup"><span data-stu-id="2abef-122">Child elements</span></span>  
 <span data-ttu-id="2abef-123">無。</span><span class="sxs-lookup"><span data-stu-id="2abef-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2abef-124">父元素</span><span class="sxs-lookup"><span data-stu-id="2abef-124">Parent elements</span></span>  
  
|<span data-ttu-id="2abef-125">元素</span><span class="sxs-lookup"><span data-stu-id="2abef-125">Element</span></span>|<span data-ttu-id="2abef-126">描述</span><span class="sxs-lookup"><span data-stu-id="2abef-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="2abef-127">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="2abef-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="2abef-128">包含有關執行階段初始化選項的資訊。</span><span class="sxs-lookup"><span data-stu-id="2abef-128">Contains information about runtime initialization options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2abef-129">備註</span><span class="sxs-lookup"><span data-stu-id="2abef-129">Remarks</span></span>

<span data-ttu-id="2abef-130">在 .NET Framework 3.5 和早期版本中，如果從遠端位置載入程式集，則程式集中的代碼將部分信任地運行，授予集取決於載入該程式集的區域。</span><span class="sxs-lookup"><span data-stu-id="2abef-130">In the .NET Framework 3.5 and earlier versions, if you load an assembly from a remote location, code in the assembly runs in partial trust with a grant set that depends on the zone from which it is loaded.</span></span> <span data-ttu-id="2abef-131">例如，如果從網站載入程式集，則程式集將載入到 Internet 區域並授予 Internet 許可權集。</span><span class="sxs-lookup"><span data-stu-id="2abef-131">For example, if you load an assembly from a website, it is loaded into the Internet zone and granted the Internet permission set.</span></span> <span data-ttu-id="2abef-132">換句話說，它在一個互聯網沙箱中執行。</span><span class="sxs-lookup"><span data-stu-id="2abef-132">In other words, it executes in an Internet sandbox.</span></span>

<span data-ttu-id="2abef-133">從 .NET 框架 4 開始，代碼訪問安全 （CAS） 策略被禁用，程式集完全信任地載入。</span><span class="sxs-lookup"><span data-stu-id="2abef-133">Starting with the .NET Framework 4, code access security (CAS) policy is disabled and assemblies are loaded in full trust.</span></span> <span data-ttu-id="2abef-134">通常，這將完全信任載入以前已沙箱<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>的方法的程式集。</span><span class="sxs-lookup"><span data-stu-id="2abef-134">Ordinarily, this would grant full trust to assemblies loaded with the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> method that previously had been sandboxed.</span></span> <span data-ttu-id="2abef-135">為了防止這種情況，預設情況下禁用在從遠端源載入的程式集中運行代碼的能力。</span><span class="sxs-lookup"><span data-stu-id="2abef-135">To prevent this, the ability to run code in assemblies loaded from a remote source is disabled by default.</span></span> <span data-ttu-id="2abef-136">預設情況下，如果嘗試載入遠端程式集，則會引發如下所示的<xref:System.IO.FileLoadException>異常消息：</span><span class="sxs-lookup"><span data-stu-id="2abef-136">By default, if you attempt to load a remote assembly, a <xref:System.IO.FileLoadException> with an exception message like the following is thrown:</span></span>

```text
System.IO.FileNotFoundException: Could not load file or assembly 'file:assem.dll' or one of its dependencies. Operation is not supported.
(Exception from HRESULT: 0x80131515)
File name: 'file:assem.dll' --->
System.NotSupportedException: An attempt was made to load an assembly from a network location which would have caused the assembly
to be sandboxed in previous versions of the .NET Framework. This release of the .NET Framework does not enable CAS policy by default,
so this load may be dangerous. If this load is not intended to sandbox the assembly, please enable the loadFromRemoteSources switch.
```

<span data-ttu-id="2abef-137">要載入程式集並執行其代碼，必須：</span><span class="sxs-lookup"><span data-stu-id="2abef-137">To load the assembly and execute its code, you must either:</span></span>

- <span data-ttu-id="2abef-138">顯式為程式集創建沙箱（[請參閱如何：在沙箱中運行部分受信任的代碼](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)）。</span><span class="sxs-lookup"><span data-stu-id="2abef-138">Explicitly create a sandbox for the assembly (see [How to: Run Partially Trusted Code in a Sandbox](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)).</span></span>

- <span data-ttu-id="2abef-139">完全信任運行程式集的代碼。</span><span class="sxs-lookup"><span data-stu-id="2abef-139">Run the assembly's code in full trust.</span></span> <span data-ttu-id="2abef-140">通過配置元素來`<loadFromRemoteSources>`執行此操作。</span><span class="sxs-lookup"><span data-stu-id="2abef-140">You do this by configuring the `<loadFromRemoteSources>` element.</span></span> <span data-ttu-id="2abef-141">它允許您指定在 .NET Framework 的早期版本中以部分信任方式運行的程式集現在完全信任 .NET 框架 4 和更高版本。</span><span class="sxs-lookup"><span data-stu-id="2abef-141">It lets you specify that the assemblies that run in partial trust in earlier versions of the .NET Framework now run in full trust in the .NET Framework 4 and later versions.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2abef-142">如果程式集不應完全信任地運行，請不要設置此配置元素。</span><span class="sxs-lookup"><span data-stu-id="2abef-142">If the assembly should not run in full trust, do not set this configuration element.</span></span> <span data-ttu-id="2abef-143">相反，請創建一個裝沙<xref:System.AppDomain>盒以載入程式集。</span><span class="sxs-lookup"><span data-stu-id="2abef-143">Instead, create a sandboxed <xref:System.AppDomain> in which to load the assembly.</span></span>

<span data-ttu-id="2abef-144">僅當`enabled`禁用代碼訪問`<loadFromRemoteSources>`安全性 （CAS） 時，元素的屬性才有效。</span><span class="sxs-lookup"><span data-stu-id="2abef-144">The `enabled` attribute for the `<loadFromRemoteSources>` element is effective only when code access security (CAS) is disabled.</span></span> <span data-ttu-id="2abef-145">預設情況下，在 .NET 框架 4 和更高版本中禁用 CAS 策略。</span><span class="sxs-lookup"><span data-stu-id="2abef-145">By default, CAS policy is disabled in the .NET Framework 4 and later versions.</span></span> <span data-ttu-id="2abef-146">如果設置為`enabled``true`，則遠端程式集將被授予完全信任。</span><span class="sxs-lookup"><span data-stu-id="2abef-146">If you set `enabled` to `true`, remote assemblies are granted full trust.</span></span>

<span data-ttu-id="2abef-147">如果未`enabled`設置為`true`，<xref:System.IO.FileLoadException>則 在以下任一條件下引發 ：</span><span class="sxs-lookup"><span data-stu-id="2abef-147">If `enabled` is not set to `true`, a <xref:System.IO.FileLoadException> is thrown under the either of the following conditions:</span></span>

- <span data-ttu-id="2abef-148">當前域的沙箱行為不同于其在 .NET 框架 3.5 中的行為。</span><span class="sxs-lookup"><span data-stu-id="2abef-148">The sandboxing behavior of the current domain is different from its behavior in the .NET Framework 3.5.</span></span> <span data-ttu-id="2abef-149">這要求禁用 CAS 策略，並且當前域不得沙箱化。</span><span class="sxs-lookup"><span data-stu-id="2abef-149">This requires CAS policy to be disabled, and the current domain not to be sandboxed.</span></span>

- <span data-ttu-id="2abef-150">正在載入的程式集不來自`MyComputer`區域。</span><span class="sxs-lookup"><span data-stu-id="2abef-150">The assembly being loaded is not from the `MyComputer` zone.</span></span>

<span data-ttu-id="2abef-151">設置元素`<loadFromRemoteSources>`以防止`true`引發此異常。</span><span class="sxs-lookup"><span data-stu-id="2abef-151">Setting the `<loadFromRemoteSources>` element to `true` prevents this exception from being thrown.</span></span> <span data-ttu-id="2abef-152">它使您能夠指定您不依賴通用語言運行時來對載入的程式集進行沙箱，以確保安全性，並且可以允許它們完全信任地執行。</span><span class="sxs-lookup"><span data-stu-id="2abef-152">It enables you to specify that you are not relying on the common language runtime to sandbox the loaded assemblies for security, and that they can be allowed to execute in full trust.</span></span>

## <a name="notes"></a><span data-ttu-id="2abef-153">注意</span><span class="sxs-lookup"><span data-stu-id="2abef-153">Notes</span></span>

- <span data-ttu-id="2abef-154">在 .NET 框架 4.5 和更高版本中，本地網路共用上的程式集預設完全信任運行;您不必啟用該`<loadFromRemoteSources>`元素。</span><span class="sxs-lookup"><span data-stu-id="2abef-154">In the .NET Framework 4.5 and later versions, assemblies on local network shares run in full trust by default; you do not have to enable the `<loadFromRemoteSources>` element.</span></span>

- <span data-ttu-id="2abef-155">如果已從網路複製應用程式，即使該應用程式位於本機電腦上，Windows 仍會將它標示為 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="2abef-155">If an application has been copied from the web, it is flagged by Windows as being a web application, even if it resides on the local computer.</span></span> <span data-ttu-id="2abef-156">您可以通過更改其檔案屬性來更改該名稱，也可以使用 元素`<loadFromRemoteSources>`授予程式集完全信任。</span><span class="sxs-lookup"><span data-stu-id="2abef-156">You can change that designation by changing its file properties, or you can use the `<loadFromRemoteSources>` element to grant the assembly full trust.</span></span> <span data-ttu-id="2abef-157">或者，您可以使用 <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> 方法載入作業系統標示為從 Web 載入的本機組件。</span><span class="sxs-lookup"><span data-stu-id="2abef-157">As an alternative, you can use the <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> method to load a local assembly that the operating system has flagged as having been loaded from the web.</span></span>

- <span data-ttu-id="2abef-158">您可以在 Windows<xref:System.IO.FileLoadException>虛擬 PC 應用程式中運行的 應用程式中獲取 。</span><span class="sxs-lookup"><span data-stu-id="2abef-158">You may get a <xref:System.IO.FileLoadException> in an application that is running in a Windows Virtual PC application.</span></span> <span data-ttu-id="2abef-159">當您嘗試從託管電腦上的連結資料夾中載入檔時，可能會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="2abef-159">This can happen when you try to load a file from linked folders on the hosting computer.</span></span> <span data-ttu-id="2abef-160">當您嘗試從通過[遠端桌面服務](/windows/win32/termserv/terminal-services-portal)（終端服務）連結的資料夾中載入檔時，也會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="2abef-160">It can also occur when you try to load a file from a folder linked over [Remote Desktop Services](/windows/win32/termserv/terminal-services-portal) (Terminal Services).</span></span> <span data-ttu-id="2abef-161">為了避免異常，請設置為`enabled``true`。</span><span class="sxs-lookup"><span data-stu-id="2abef-161">To avoid the exception, set `enabled` to `true`.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="2abef-162">組態檔</span><span class="sxs-lookup"><span data-stu-id="2abef-162">Configuration file</span></span>

<span data-ttu-id="2abef-163">此項目通常用於應用程式組態檔，不過可以根據內容用於其他組態檔。</span><span class="sxs-lookup"><span data-stu-id="2abef-163">This element is typically used in the application configuration file, but can be used in other configuration files depending upon the context.</span></span> <span data-ttu-id="2abef-164">有關詳細資訊，請參閱文章["CAS 策略的更多隱式使用：在](https://docs.microsoft.com/archive/blogs/shawnfa/more-implicit-uses-of-cas-policy-loadfromremotesources).NET 安全博客中載入從遠端資源"。</span><span class="sxs-lookup"><span data-stu-id="2abef-164">For more information, see the article [More Implicit Uses of CAS Policy: loadFromRemoteSources](https://docs.microsoft.com/archive/blogs/shawnfa/more-implicit-uses-of-cas-policy-loadfromremotesources) in the .NET Security blog.</span></span>  

## <a name="example"></a><span data-ttu-id="2abef-165">範例</span><span class="sxs-lookup"><span data-stu-id="2abef-165">Example</span></span>

<span data-ttu-id="2abef-166">下面的示例演示如何對從遠端源載入的程式集授予完全信任。</span><span class="sxs-lookup"><span data-stu-id="2abef-166">The following example shows how to grant full trust to assemblies loaded from remote sources.</span></span>

```xml
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```

## <a name="see-also"></a><span data-ttu-id="2abef-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2abef-167">See also</span></span>

- [<span data-ttu-id="2abef-168">CAS 策略的更多隱式使用：從遠端源載入</span><span class="sxs-lookup"><span data-stu-id="2abef-168">More Implicit Uses of CAS Policy: loadFromRemoteSources</span></span>](https://docs.microsoft.com/archive/blogs/shawnfa/more-implicit-uses-of-cas-policy-loadfromremotesources)
- [<span data-ttu-id="2abef-169">如何：在沙箱中執行部分信任的程式碼</span><span class="sxs-lookup"><span data-stu-id="2abef-169">How to: Run Partially Trusted Code in a Sandbox</span></span>](../../../misc/how-to-run-partially-trusted-code-in-a-sandbox.md)
- [<span data-ttu-id="2abef-170">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="2abef-170">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="2abef-171">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="2abef-171">Configuration File Schema</span></span>](../index.md)
- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>
