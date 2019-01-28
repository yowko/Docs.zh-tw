---
title: .NET Framework 類別庫中的過時功能
ms.custom: updateeachrelease
ms.date: 04/10/2018
helpviewer_keywords:
- obsolete [.NET Framework]
- what's obsolete [.NET Framework]
- deprecated [.NET Framework]
ms.assetid: d356a43a-73df-4ae2-a457-b9628074c7cd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8af9d0f3c31e9178e815dc8fb00f192b8da3e5de
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54541257"
---
# <a name="what39s-obsolete-in-the-net-framework-class-library"></a><span data-ttu-id="decd9-102">.NET Framework 類別庫中的過時功能</span><span class="sxs-lookup"><span data-stu-id="decd9-102">What&#39;s Obsolete in the .NET Framework Class Library</span></span>
<span data-ttu-id="decd9-103">.NET Framework 會隨著時間改變。</span><span class="sxs-lookup"><span data-stu-id="decd9-103">The .NET Framework changes over time.</span></span> <span data-ttu-id="decd9-104">每個新版本都會加入一些提供新功能的新類型和類型成員。</span><span class="sxs-lookup"><span data-stu-id="decd9-104">Each new version adds new types and type members that provide new functionality.</span></span> <span data-ttu-id="decd9-105">現有的類型及其成員也會隨著時間改變。</span><span class="sxs-lookup"><span data-stu-id="decd9-105">Existing types and their members also change over time.</span></span> <span data-ttu-id="decd9-106">例如，當某些類型所支援的技術由新技術取代時，這些類型的重要性會降低，而且某些方法會由更方便或功能更完整的新方法取代。</span><span class="sxs-lookup"><span data-stu-id="decd9-106">For example, some types become less important as the technology they support is replaced by a new technology, and some methods are superseded by newer methods that are either more convenient or more full-featured.</span></span>  
  
 <span data-ttu-id="decd9-107">.NET Framework 和 Common Language Runtime 致力於支援回溯相容性 (讓使用某個 .NET Framework 版本所開發的應用程式能夠在下一個 .NET Framework 版本上執行)。</span><span class="sxs-lookup"><span data-stu-id="decd9-107">The .NET Framework and the common language runtime strive to support backward compatibility (allowing applications that were developed with one version of the .NET Framework to run on the next version of the .NET Framework).</span></span> <span data-ttu-id="decd9-108">這點會讓您難以單純地移除類型或類型成員。</span><span class="sxs-lookup"><span data-stu-id="decd9-108">This makes it difficult to simply remove a type or a type member.</span></span> <span data-ttu-id="decd9-109">相反地，.NET Framework 會將某個類型或類型成員標記為過時或已被取代，表示不應該再使用該類型或類型成員。</span><span class="sxs-lookup"><span data-stu-id="decd9-109">Instead, the .NET Framework indicates that a type or a type member should no longer be used by marking it as obsolete or deprecated.</span></span> <span data-ttu-id="decd9-110">取代類型或成員時需要為其加上標記，以便讓開發人員了解該類型或成員即將消失，而且有時間來回應其移除。</span><span class="sxs-lookup"><span data-stu-id="decd9-110">Deprecating a type or a member involves marking it so that developers are aware it will go away and have time to respond to its removal.</span></span> <span data-ttu-id="decd9-111">不過，使用該類型或成員的現有程式碼仍然可繼續在新的 .NET Framework 版本中執行。</span><span class="sxs-lookup"><span data-stu-id="decd9-111">However, existing code that uses the type or member continues to run in the new version of the .NET Framework.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="decd9-112">就 .NET Framework 的類型和成員而言，「過時」和「已被取代」具有相同的意義。</span><span class="sxs-lookup"><span data-stu-id="decd9-112">The terms *obsolete* and *deprecated* have the same meaning when applied to the types and members of the .NET Framework.</span></span>  
  
## <a name="the-obsoleteattribute-attribute"></a><span data-ttu-id="decd9-113">ObsoleteAttribute 屬性</span><span class="sxs-lookup"><span data-stu-id="decd9-113">The ObsoleteAttribute Attribute</span></span>  
 <span data-ttu-id="decd9-114">.NET Framework 會使用 <xref:System.ObsoleteAttribute> 屬性來標記某個類型或類型成員，表示該類型或類型成員已過時。</span><span class="sxs-lookup"><span data-stu-id="decd9-114">The .NET Framework indicates that a type or type member is obsolete by marking it with the <xref:System.ObsoleteAttribute> attribute.</span></span> <span data-ttu-id="decd9-115">如果將這個屬性套用至某個類型或成員，就表示未來的某個 .NET Framework 版本將移除該類型或成員，但不會破壞使用該成員的已編譯程式碼。</span><span class="sxs-lookup"><span data-stu-id="decd9-115">Applying the attribute to a type or member indicates that type or member will be removed in some future version of the .NET Framework without breaking compiled code that uses that member.</span></span>  
  
 <span data-ttu-id="decd9-116">除了表示某個類型或類型成員已過時之外，<xref:System.ObsoleteAttribute> 也會定義編譯器如何處理包含該類型或成員的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="decd9-116">In addition to indicating that a type or a type member is obsolete, <xref:System.ObsoleteAttribute> defines how the compiler handles source code that includes that type or member.</span></span> <span data-ttu-id="decd9-117">編譯器可能會編譯程式碼但發出警告訊息，也可能會將類型或成員的使用視為錯誤。</span><span class="sxs-lookup"><span data-stu-id="decd9-117">The compiler can compile the code but emit a warning message, or it can treat the use of the type or member as an error.</span></span> <span data-ttu-id="decd9-118">在第一種情況下，雖然程式碼可以成功編譯，但是警告訊息會指出類型或成員已過時。</span><span class="sxs-lookup"><span data-stu-id="decd9-118">In the first case, the code can successfully compile, but a warning message indicates that the type or member is obsolete.</span></span> <span data-ttu-id="decd9-119">在第二種情況下，編譯會失敗。</span><span class="sxs-lookup"><span data-stu-id="decd9-119">In the second case, compilation fails.</span></span>  
  
 <span data-ttu-id="decd9-120">即使編譯產生錯誤而非警告訊息，<xref:System.ObsoleteAttribute> 並不會影響執行階段行為。</span><span class="sxs-lookup"><span data-stu-id="decd9-120">Even if compilation produces an error instead of a warning message, <xref:System.ObsoleteAttribute> does not affect run-time behavior.</span></span> <span data-ttu-id="decd9-121">也就是說，使用該類型或成員而且已成功編譯的應用程式一定會順利執行。</span><span class="sxs-lookup"><span data-stu-id="decd9-121">That is, applications that use the type or member and that have compiled successfully will always run successfully.</span></span> <span data-ttu-id="decd9-122">只有嘗試重新編譯使用該類型或成員之應用程式的作業會失敗。</span><span class="sxs-lookup"><span data-stu-id="decd9-122">Only the attempt to recompile an application that uses the type or member fails.</span></span>  
  
## <a name="how-to-handle-obsolete-types-and-members"></a><span data-ttu-id="decd9-123">如何處理過時的類型和成員</span><span class="sxs-lookup"><span data-stu-id="decd9-123">How to Handle Obsolete Types and Members</span></span>  
 <span data-ttu-id="decd9-124">當您升級和重新編譯現有的程式碼時，使用在應用程式中產生編譯器警告的過時類型或成員是完全可接受的作法。</span><span class="sxs-lookup"><span data-stu-id="decd9-124">When you upgrade and recompile existing code, using an obsolete type or member that produces a compiler warning in your application is perfectly acceptable.</span></span> <span data-ttu-id="decd9-125">不過，您應該檢閱編譯器警告訊息，以便判斷是否應該變更應用程式程式碼。</span><span class="sxs-lookup"><span data-stu-id="decd9-125">However, you should review the compiler warning message to determine whether you should change your application code.</span></span> <span data-ttu-id="decd9-126">如果訊息沒有指向適當的替代方案，您就應該進行下列其中一項步驟：</span><span class="sxs-lookup"><span data-stu-id="decd9-126">If the message does not point to a suitable alternative, you should do either of the following:</span></span>  
  
-   <span data-ttu-id="decd9-127">變更程式碼，不使用類型或成員 (如果可能的話)。</span><span class="sxs-lookup"><span data-stu-id="decd9-127">Change your code by removing the use of the type or member, if possible.</span></span>  
  
     <span data-ttu-id="decd9-128">-或-</span><span class="sxs-lookup"><span data-stu-id="decd9-128">-or-</span></span>  
  
-   <span data-ttu-id="decd9-129">檢閱適用於這個技術領域的文件，以便判斷如何回應取代。</span><span class="sxs-lookup"><span data-stu-id="decd9-129">Review the documentation for this technology area to determine how to respond to the deprecation.</span></span>  
  
 <span data-ttu-id="decd9-130">您可以選擇不要針對更新的 .NET Framework 版本重新編譯現有的程式碼，</span><span class="sxs-lookup"><span data-stu-id="decd9-130">You may choose not to recompile existing code against a later version of the .NET Framework.</span></span> <span data-ttu-id="decd9-131">而改為指定現有已編譯程式碼所執行的目標 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="decd9-131">Instead, you can specify the version of the .NET Framework against which your existing compiled code runs.</span></span> <span data-ttu-id="decd9-132">例如，假設您有一個名為 app1.exe 而且已針對 [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] 編譯的應用程式，但是您想要讓這個應用程式針對 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 執行。</span><span class="sxs-lookup"><span data-stu-id="decd9-132">For example, suppose that you have an application named app1.exe that was compiled against the [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)], but you want the application to run against the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span> <span data-ttu-id="decd9-133">此時，您需要進行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="decd9-133">This requires the following steps:</span></span>  
  
1.  <span data-ttu-id="decd9-134">建立主要可執行檔的組態檔，並將它命名為 *appName*.exe.config，其中 *appName* 是應用程式可執行檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="decd9-134">Create a configuration file for your main executable and name it *appName*.exe.config, where *appName* is the name of the application executable.</span></span> <span data-ttu-id="decd9-135">對於範例中名為 app1.exe 的應用程式而言，您要建立名為 app1.exe.config 的組態檔。</span><span class="sxs-lookup"><span data-stu-id="decd9-135">For the application named app1.exe in our example, you would create a configuration file named app1.exe.config.</span></span>  
  
2.  <span data-ttu-id="decd9-136">將下列內容加入組態檔。</span><span class="sxs-lookup"><span data-stu-id="decd9-136">Add the following to the configuration file.</span></span>  
  
    ```xml  
    <configuration>  
       <startup>   
          <supportedRuntime version="v4.0" />  
       </startup>  
    </configuration>  
    ```  
  
 <span data-ttu-id="decd9-137">下表列出您可以指派給 `version` 屬性的字串值，以便將目標設定為特定 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="decd9-137">The following table lists the string values that you can assign to the `version` attribute to target a specific version of the .NET Framework.</span></span>  
  
|<span data-ttu-id="decd9-138">.NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="decd9-138">.NET Framework version</span></span>|<span data-ttu-id="decd9-139">`version` 字串</span><span class="sxs-lookup"><span data-stu-id="decd9-139">`version` string</span></span>|
|-|-|  
|<span data-ttu-id="decd9-140">4.7 (包括 4.7.1 和 4.7.2)</span><span class="sxs-lookup"><span data-stu-id="decd9-140">4.7 (including 4.7.1 and 4.7.2)</span></span>|<span data-ttu-id="decd9-141">4.0 版起</span><span class="sxs-lookup"><span data-stu-id="decd9-141">v4.0</span></span>|  
|<span data-ttu-id="decd9-142">4.6 (包括 4.6.1 和 4.6.2)</span><span class="sxs-lookup"><span data-stu-id="decd9-142">4.6 (including 4.6.1 and 4.6.2)</span></span>|<span data-ttu-id="decd9-143">4.0 版起</span><span class="sxs-lookup"><span data-stu-id="decd9-143">v4.0</span></span>|  
|<span data-ttu-id="decd9-144">4.5 (包括 4.5.1 和 4.5.2)</span><span class="sxs-lookup"><span data-stu-id="decd9-144">4.5 (including 4.5.1 and 4.5.2)</span></span>|<span data-ttu-id="decd9-145">4.0 版起</span><span class="sxs-lookup"><span data-stu-id="decd9-145">v4.0</span></span>|  
|<span data-ttu-id="decd9-146">4</span><span class="sxs-lookup"><span data-stu-id="decd9-146">4</span></span>|<span data-ttu-id="decd9-147">4.0 版起</span><span class="sxs-lookup"><span data-stu-id="decd9-147">v4.0</span></span>|  
|<span data-ttu-id="decd9-148">3.5</span><span class="sxs-lookup"><span data-stu-id="decd9-148">3.5</span></span>|<span data-ttu-id="decd9-149">v2.0.50727</span><span class="sxs-lookup"><span data-stu-id="decd9-149">v2.0.50727</span></span>|  
|<span data-ttu-id="decd9-150">2.0</span><span class="sxs-lookup"><span data-stu-id="decd9-150">2.0</span></span>|<span data-ttu-id="decd9-151">v2.0.50727</span><span class="sxs-lookup"><span data-stu-id="decd9-151">v2.0.50727</span></span>|  
|<span data-ttu-id="decd9-152">1.1</span><span class="sxs-lookup"><span data-stu-id="decd9-152">1.1</span></span>|<span data-ttu-id="decd9-153">v1.1.4322</span><span class="sxs-lookup"><span data-stu-id="decd9-153">v1.1.4322</span></span>|  
|<span data-ttu-id="decd9-154">1.0</span><span class="sxs-lookup"><span data-stu-id="decd9-154">1.0</span></span>|<span data-ttu-id="decd9-155">v1.0.3705</span><span class="sxs-lookup"><span data-stu-id="decd9-155">v1.0.3705</span></span>|  
  
## <a name="obsolete-lists-for-the-net-framework-45-and-later-versions"></a><span data-ttu-id="decd9-156">.NET Framework 4.5 和更新版本的已淘汰清單</span><span class="sxs-lookup"><span data-stu-id="decd9-156">Obsolete Lists for the .NET Framework 4.5 and later versions</span></span>  
 [<span data-ttu-id="decd9-157">過時的類型</span><span class="sxs-lookup"><span data-stu-id="decd9-157">Obsolete Types</span></span>](../../../docs/framework/whats-new/obsolete-types.md)  
  
 [<span data-ttu-id="decd9-158">過時的成員</span><span class="sxs-lookup"><span data-stu-id="decd9-158">Obsolete Members</span></span>](../../../docs/framework/whats-new/obsolete-members.md)  
  
## <a name="obsolete-lists-for-previous-versions"></a><span data-ttu-id="decd9-159">舊版的過時清單</span><span class="sxs-lookup"><span data-stu-id="decd9-159">Obsolete Lists for Previous Versions</span></span>  
 [<span data-ttu-id="decd9-160">.NET Framework 4 中過時的類型</span><span class="sxs-lookup"><span data-stu-id="decd9-160">Obsolete Types in the .NET Framework 4</span></span>](https://go.microsoft.com/fwlink/?LinkId=224224)  
  
 [<span data-ttu-id="decd9-161">.NET Framework 4 中過時的成員</span><span class="sxs-lookup"><span data-stu-id="decd9-161">Obsolete Members in the .NET Framework 4</span></span>](https://go.microsoft.com/fwlink/?LinkId=224227)  
  
 [<span data-ttu-id="decd9-162">.NET Framework 3.5 的過時清單</span><span class="sxs-lookup"><span data-stu-id="decd9-162">.NET Framework 3.5 Obsolete List</span></span>](https://go.microsoft.com/fwlink/?LinkId=163710)  
  
 [<span data-ttu-id="decd9-163">.NET Framework 2.0 的過時清單</span><span class="sxs-lookup"><span data-stu-id="decd9-163">.NET Framework 2.0 Obsolete List</span></span>](https://go.microsoft.com/fwlink/?LinkID=125264)  
  
## <a name="see-also"></a><span data-ttu-id="decd9-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="decd9-164">See also</span></span>
- [<span data-ttu-id="decd9-165">\<supportedRuntime> 項目</span><span class="sxs-lookup"><span data-stu-id="decd9-165">\<supportedRuntime> Element</span></span>](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)
