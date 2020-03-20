---
title: .NET 框架中過時的內容
ms.custom: updateeachrelease
ms.date: 04/02/2019
helpviewer_keywords:
- obsolete [.NET Framework]
- what's obsolete [.NET Framework]
- deprecated [.NET Framework]
ms.assetid: d356a43a-73df-4ae2-a457-b9628074c7cd
ms.openlocfilehash: 7cfebfde859a95495e9d2d5e42bd034ad5d55e61
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79143131"
---
# <a name="whats-obsolete-in-the-net-framework-class-library"></a><span data-ttu-id="b4fdf-102">.NET Framework 類別庫中已淘汰的功能</span><span class="sxs-lookup"><span data-stu-id="b4fdf-102">What's obsolete in the .NET Framework class library</span></span>

<span data-ttu-id="b4fdf-103">.NET 會隨時間而變化。</span><span class="sxs-lookup"><span data-stu-id="b4fdf-103">.NET changes over time.</span></span> <span data-ttu-id="b4fdf-104">每個新版本都會加入一些提供新功能的新類型和類型成員。</span><span class="sxs-lookup"><span data-stu-id="b4fdf-104">Each new version adds new types and type members that provide new functionality.</span></span> <span data-ttu-id="b4fdf-105">現有的類型及其成員也會隨著時間改變。</span><span class="sxs-lookup"><span data-stu-id="b4fdf-105">Existing types and their members also change over time.</span></span> <span data-ttu-id="b4fdf-106">例如，某些類型變得不那麼重要，因為它們支援的技術被新技術所取代，並且某些方法被在某些方面優越的新方法所取代。</span><span class="sxs-lookup"><span data-stu-id="b4fdf-106">For example, some types become less important as the technology they support is replaced by a new technology, and some methods are superseded by newer methods that are superior in some way.</span></span>

<span data-ttu-id="b4fdf-107">.NET 框架和通用語言運行時努力支援向後相容性（允許使用一個版本 .NET Framework 開發的應用程式在下一版本的 .NET Framework 上運行）。</span><span class="sxs-lookup"><span data-stu-id="b4fdf-107">.NET Framework and the common language runtime strive to support backward compatibility (allowing applications that were developed with one version of .NET Framework to run on the next version of .NET Framework).</span></span> <span data-ttu-id="b4fdf-108">這點會讓您難以單純地移除類型或類型成員。</span><span class="sxs-lookup"><span data-stu-id="b4fdf-108">This makes it difficult to simply remove a type or a type member.</span></span> <span data-ttu-id="b4fdf-109">相反，.NET 指示不應再使用類型或類型成員將其標記為過時或棄用。</span><span class="sxs-lookup"><span data-stu-id="b4fdf-109">Instead, .NET indicates that a type or a type member should no longer be used by marking it as obsolete or deprecated.</span></span> <span data-ttu-id="b4fdf-110">取代類型或成員時需要為其加上標記，以便讓開發人員了解該類型或成員即將消失，而且有時間來回應其移除。</span><span class="sxs-lookup"><span data-stu-id="b4fdf-110">Deprecating a type or a member involves marking it so that developers are aware it will go away and have time to respond to its removal.</span></span> <span data-ttu-id="b4fdf-111">但是，使用類型或成員的現有代碼將繼續在新版本的 .NET 中運行。</span><span class="sxs-lookup"><span data-stu-id="b4fdf-111">However, existing code that uses the type or member continues to run in the new version of .NET.</span></span>

> [!NOTE]
> <span data-ttu-id="b4fdf-112">當應用於 .NET 類型和成員時，*已過時*和*棄用*的術語具有相同的含義。</span><span class="sxs-lookup"><span data-stu-id="b4fdf-112">The terms *obsolete* and *deprecated* have the same meaning when applied to .NET types and members.</span></span>

## <a name="the-obsoleteattribute-attribute"></a><span data-ttu-id="b4fdf-113">ObsoleteAttribute 屬性</span><span class="sxs-lookup"><span data-stu-id="b4fdf-113">The ObsoleteAttribute attribute</span></span>

<span data-ttu-id="b4fdf-114">.NET Framework 會使用 <xref:System.ObsoleteAttribute> 屬性來標記某個類型或類型成員，表示該類型或類型成員已過時。</span><span class="sxs-lookup"><span data-stu-id="b4fdf-114">The .NET Framework indicates that a type or type member is obsolete by marking it with the <xref:System.ObsoleteAttribute> attribute.</span></span> <span data-ttu-id="b4fdf-115">如果將這個屬性套用至某個類型或成員，就表示未來的某個 .NET Framework 版本將移除該類型或成員，但不會破壞使用該成員的已編譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="b4fdf-115">Applying the attribute to a type or member indicates that type or member will be removed in some future version of the .NET Framework without breaking compiled code that uses that member.</span></span>

<span data-ttu-id="b4fdf-116">除了表示某個類型或類型成員已過時之外，<xref:System.ObsoleteAttribute> 也會定義編譯器如何處理包含該類型或成員的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="b4fdf-116">In addition to indicating that a type or a type member is obsolete, <xref:System.ObsoleteAttribute> defines how the compiler handles source code that includes that type or member.</span></span> <span data-ttu-id="b4fdf-117">編譯器可能會編譯程式碼但發出警告訊息，也可能會將類型或成員的使用視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="b4fdf-117">The compiler can compile the code but emit a warning message, or it can treat the use of the type or member as an error.</span></span> <span data-ttu-id="b4fdf-118">在第一種情況下，雖然程式碼可以成功編譯，但是警告訊息會指出類型或成員已過時。</span><span class="sxs-lookup"><span data-stu-id="b4fdf-118">In the first case, the code can successfully compile, but a warning message indicates that the type or member is obsolete.</span></span> <span data-ttu-id="b4fdf-119">在第二種情況下，編譯會失敗。</span><span class="sxs-lookup"><span data-stu-id="b4fdf-119">In the second case, compilation fails.</span></span>

<span data-ttu-id="b4fdf-120">即使編譯產生錯誤而非警告訊息，<xref:System.ObsoleteAttribute> 並不會影響執行階段行為。</span><span class="sxs-lookup"><span data-stu-id="b4fdf-120">Even if compilation produces an error instead of a warning message, <xref:System.ObsoleteAttribute> does not affect run-time behavior.</span></span> <span data-ttu-id="b4fdf-121">也就是說，使用該類型或成員而且已成功編譯的應用程式一定會順利執行。</span><span class="sxs-lookup"><span data-stu-id="b4fdf-121">That is, applications that use the type or member and that have compiled successfully will always run successfully.</span></span> <span data-ttu-id="b4fdf-122">只有嘗試重新編譯使用該類型或成員之應用程式的作業會失敗。</span><span class="sxs-lookup"><span data-stu-id="b4fdf-122">Only the attempt to recompile an application that uses the type or member fails.</span></span>

## <a name="how-to-handle-obsolete-types-and-members"></a><span data-ttu-id="b4fdf-123">如何處理已淘汰的類型和成員</span><span class="sxs-lookup"><span data-stu-id="b4fdf-123">How to handle obsolete types and members</span></span>

<span data-ttu-id="b4fdf-124">當您升級和重新編譯現有的程式碼時，使用在應用程式中產生編譯器警告的過時類型或成員是完全可接受的作法。</span><span class="sxs-lookup"><span data-stu-id="b4fdf-124">When you upgrade and recompile existing code, using an obsolete type or member that produces a compiler warning in your application is perfectly acceptable.</span></span> <span data-ttu-id="b4fdf-125">不過，您應該檢閱編譯器警告訊息，以便判斷是否應該變更應用程式程式碼。</span><span class="sxs-lookup"><span data-stu-id="b4fdf-125">However, you should review the compiler warning message to determine whether you should change your application code.</span></span> <span data-ttu-id="b4fdf-126">如果訊息沒有指向適當的替代方案，您就應該進行下列其中一項步驟：</span><span class="sxs-lookup"><span data-stu-id="b4fdf-126">If the message does not point to a suitable alternative, you should do either of the following:</span></span>

- <span data-ttu-id="b4fdf-127">變更程式碼，不使用類型或成員 (如果可能的話)。</span><span class="sxs-lookup"><span data-stu-id="b4fdf-127">Change your code by removing the use of the type or member, if possible.</span></span>

     <span data-ttu-id="b4fdf-128">-或-</span><span class="sxs-lookup"><span data-stu-id="b4fdf-128">-or-</span></span>

- <span data-ttu-id="b4fdf-129">檢閱適用於這個技術領域的文件，以便判斷如何回應取代。</span><span class="sxs-lookup"><span data-stu-id="b4fdf-129">Review the documentation for this technology area to determine how to respond to the deprecation.</span></span>

<span data-ttu-id="b4fdf-130">您可以選擇不要針對更新的 .NET Framework 版本重新編譯現有的程式碼，</span><span class="sxs-lookup"><span data-stu-id="b4fdf-130">You may choose not to recompile existing code against a later version of the .NET Framework.</span></span> <span data-ttu-id="b4fdf-131">而改為指定現有已編譯程式碼所執行的目標 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="b4fdf-131">Instead, you can specify the version of the .NET Framework against which your existing compiled code runs.</span></span> <span data-ttu-id="b4fdf-132">例如，假設您有一個名為 app1.exe 且已針對 .NET Framework 3.5 編譯的應用程式，但是您想要讓這個應用程式針對 .NET Framework 4.5 執行。</span><span class="sxs-lookup"><span data-stu-id="b4fdf-132">For example, suppose that you have an application named app1.exe that was compiled against the .NET Framework 3.5, but you want the application to run against the .NET Framework 4.5.</span></span> <span data-ttu-id="b4fdf-133">此時，您需要進行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="b4fdf-133">This requires the following steps:</span></span>

1. <span data-ttu-id="b4fdf-134">建立主要可執行檔的組態檔，並將它命名為 *appName*.exe.config，其中 *appName* 是應用程式可執行檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="b4fdf-134">Create a configuration file for your main executable and name it *appName*.exe.config, where *appName* is the name of the application executable.</span></span> <span data-ttu-id="b4fdf-135">對於我們示例中名為*app1.exe*的應用程式，您將創建名為*app1.exe.config 的*設定檔。</span><span class="sxs-lookup"><span data-stu-id="b4fdf-135">For the application named *app1.exe* in our example, you would create a configuration file named *app1.exe.config*.</span></span>

2. <span data-ttu-id="b4fdf-136">將下列內容加入組態檔。</span><span class="sxs-lookup"><span data-stu-id="b4fdf-136">Add the following to the configuration file.</span></span>

    ```xml
    <configuration>
       <startup>
          <supportedRuntime version="v4.0" />
       </startup>
    </configuration>
    ```

<span data-ttu-id="b4fdf-137">要定位 .NET Framework 的特定版本，請為`version`屬性分配以下字串值之一：</span><span class="sxs-lookup"><span data-stu-id="b4fdf-137">To target a specific version of .NET Framework, assign one of the following string values to the `version` attribute:</span></span>

|<span data-ttu-id="b4fdf-138">.NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="b4fdf-138">.NET Framework version</span></span>|<span data-ttu-id="b4fdf-139">`version` 字串</span><span class="sxs-lookup"><span data-stu-id="b4fdf-139">`version` string</span></span>|
|-|-|
|<span data-ttu-id="b4fdf-140">4.8</span><span class="sxs-lookup"><span data-stu-id="b4fdf-140">4.8</span></span>|<span data-ttu-id="b4fdf-141">4.0 版起</span><span class="sxs-lookup"><span data-stu-id="b4fdf-141">v4.0</span></span>|
|<span data-ttu-id="b4fdf-142">4.7 (包括 4.7.1 和 4.7.2)</span><span class="sxs-lookup"><span data-stu-id="b4fdf-142">4.7 (including 4.7.1 and 4.7.2)</span></span>|<span data-ttu-id="b4fdf-143">4.0 版起</span><span class="sxs-lookup"><span data-stu-id="b4fdf-143">v4.0</span></span>|
|<span data-ttu-id="b4fdf-144">4.6 (包括 4.6.1 和 4.6.2)</span><span class="sxs-lookup"><span data-stu-id="b4fdf-144">4.6 (including 4.6.1 and 4.6.2)</span></span>|<span data-ttu-id="b4fdf-145">4.0 版起</span><span class="sxs-lookup"><span data-stu-id="b4fdf-145">v4.0</span></span>|
|<span data-ttu-id="b4fdf-146">4.5 (包括 4.5.1 和 4.5.2)</span><span class="sxs-lookup"><span data-stu-id="b4fdf-146">4.5 (including 4.5.1 and 4.5.2)</span></span>|<span data-ttu-id="b4fdf-147">4.0 版起</span><span class="sxs-lookup"><span data-stu-id="b4fdf-147">v4.0</span></span>|
|<span data-ttu-id="b4fdf-148">4</span><span class="sxs-lookup"><span data-stu-id="b4fdf-148">4</span></span>|<span data-ttu-id="b4fdf-149">4.0 版起</span><span class="sxs-lookup"><span data-stu-id="b4fdf-149">v4.0</span></span>|
|<span data-ttu-id="b4fdf-150">3.5</span><span class="sxs-lookup"><span data-stu-id="b4fdf-150">3.5</span></span>|<span data-ttu-id="b4fdf-151">v2.0.50727</span><span class="sxs-lookup"><span data-stu-id="b4fdf-151">v2.0.50727</span></span>|
|<span data-ttu-id="b4fdf-152">2.0</span><span class="sxs-lookup"><span data-stu-id="b4fdf-152">2.0</span></span>|<span data-ttu-id="b4fdf-153">v2.0.50727</span><span class="sxs-lookup"><span data-stu-id="b4fdf-153">v2.0.50727</span></span>|
|<span data-ttu-id="b4fdf-154">1.1</span><span class="sxs-lookup"><span data-stu-id="b4fdf-154">1.1</span></span>|<span data-ttu-id="b4fdf-155">v1.1.4322</span><span class="sxs-lookup"><span data-stu-id="b4fdf-155">v1.1.4322</span></span>|
|<span data-ttu-id="b4fdf-156">1.0</span><span class="sxs-lookup"><span data-stu-id="b4fdf-156">1.0</span></span>|<span data-ttu-id="b4fdf-157">v1.0.3705</span><span class="sxs-lookup"><span data-stu-id="b4fdf-157">v1.0.3705</span></span>|

## <a name="obsolete-apis-for-net-framework-45-and-later-versions"></a><span data-ttu-id="b4fdf-158">.NET 框架 4.5 和更高版本的過時 API</span><span class="sxs-lookup"><span data-stu-id="b4fdf-158">Obsolete APIs for .NET Framework 4.5 and later versions</span></span>

- [<span data-ttu-id="b4fdf-159">已淘汰的類型</span><span class="sxs-lookup"><span data-stu-id="b4fdf-159">Obsolete Types</span></span>](obsolete-types.md)
- [<span data-ttu-id="b4fdf-160">已淘汰的成員</span><span class="sxs-lookup"><span data-stu-id="b4fdf-160">Obsolete Members</span></span>](obsolete-members.md)

## <a name="obsolete-apis-for-previous-versions"></a><span data-ttu-id="b4fdf-161">早期版本的過時 API</span><span class="sxs-lookup"><span data-stu-id="b4fdf-161">Obsolete APIs for previous versions</span></span>

- <span data-ttu-id="b4fdf-162">[.NET 框架 4 中的過時類型](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee461503(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b4fdf-162">[Obsolete Types in .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee461503(v=vs.100))</span></span>
- <span data-ttu-id="b4fdf-163">[.NET 框架 4 中的過時成員](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee471421(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b4fdf-163">[Obsolete Members in .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee471421(v=vs.100))</span></span>
- <span data-ttu-id="b4fdf-164">[.NET Framework 3.5 的過時清單](https://docs.microsoft.com/previous-versions/cc835481(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="b4fdf-164">[.NET Framework 3.5 Obsolete List](https://docs.microsoft.com/previous-versions/cc835481(v=msdn.10))</span></span>
- <span data-ttu-id="b4fdf-165">[.NET Framework 2.0 的過時清單](https://docs.microsoft.com/previous-versions/aa497286(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="b4fdf-165">[.NET Framework 2.0 Obsolete List](https://docs.microsoft.com/previous-versions/aa497286(v=msdn.10))</span></span>

## <a name="see-also"></a><span data-ttu-id="b4fdf-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4fdf-166">See also</span></span>

- [<span data-ttu-id="b4fdf-167">\<支援的運行時>元素</span><span class="sxs-lookup"><span data-stu-id="b4fdf-167">\<supportedRuntime> Element</span></span>](../configure-apps/file-schema/startup/supportedruntime-element.md)
