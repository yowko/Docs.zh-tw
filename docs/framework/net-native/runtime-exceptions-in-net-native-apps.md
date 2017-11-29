---
title: ".NET 原生 App 中的執行階段例外狀況"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5f050181-8fdd-4a4e-9d16-f84c22a88a97
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9d4f5787faa2fdf5f5450d8ddce285919a658645
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="runtime-exceptions-in-net-native-apps"></a><span data-ttu-id="0acf2-102">.NET 原生 App 中的執行階段例外狀況</span><span class="sxs-lookup"><span data-stu-id="0acf2-102">Runtime Exceptions in .NET Native Apps</span></span>
<span data-ttu-id="0acf2-103">因為偵錯和發行組態完全不同，所以請務必在目標平台上測試通用 Windows 平台 App 的發行組建。</span><span class="sxs-lookup"><span data-stu-id="0acf2-103">It is important to test the release builds of your Universal Windows Platform app on their target platforms because the debug and release configurations are completely different.</span></span> <span data-ttu-id="0acf2-104">根據預設，偵錯組態會使用 .NET 核心執行階段來編譯 App，但此發行組態會使用 .NET 原生將 App 編譯為原生程式碼。</span><span class="sxs-lookup"><span data-stu-id="0acf2-104">By default, the debug configuration uses the .NET Core runtime to compile your app, but the release configuration uses .NET Native to compile your app to native code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0acf2-105">如需處理 [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)、[MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md) 和 [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) 這三項您在測試應用程式發行版本時可能遇到之例外狀況的資訊，請參閱[使用者入門](../../../docs/framework/net-native/getting-started-with-net-native.md)主題中的「步驟 4：手動解決遺失的中繼資料」，以及 [反映和 .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md) 和[執行階段指示詞 (rd.xml) 組態檔參考](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="0acf2-105">For information on dealing with the [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md), and [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) exceptions that you may encounter when testing the release versions of your app, see  "Step 4: Manually resolve missing metadata: in the [Getting Started](../../../docs/framework/net-native/getting-started-with-net-native.md) topic, as well as [Reflection and .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md) and [Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span></span>  
  
## <a name="debug-and-release-builds"></a><span data-ttu-id="0acf2-106">偵錯與發行組建</span><span class="sxs-lookup"><span data-stu-id="0acf2-106">Debug and release builds</span></span>  
 <span data-ttu-id="0acf2-107">當偵錯組建針對 .NET 核心執行階段執行時，它尚未被編譯為原生程式碼。</span><span class="sxs-lookup"><span data-stu-id="0acf2-107">When the debug build executes against the .NET Core runtime, it has not been compiled to native code.</span></span> <span data-ttu-id="0acf2-108">這使得此執行階段平常提供的所有服務可用於您的 App。</span><span class="sxs-lookup"><span data-stu-id="0acf2-108">This makes all of the services ordinarily provided by the runtime available to your app.</span></span>  
  
 <span data-ttu-id="0acf2-109">相反地，發行組建會編譯為其目標平台的原生程式碼、移除大部分外部執行階段和程式庫的相依性，以及徹底最佳化程式碼，以追求最大效能。</span><span class="sxs-lookup"><span data-stu-id="0acf2-109">On the other hand, the release build compiles to native code for its target platforms, removes most dependencies on external runtimes and libraries, and heavily optimizes code for maximum performance.</span></span>  
  
 <span data-ttu-id="0acf2-110">當您偵錯使用 .NET 原生編譯的發行組建：</span><span class="sxs-lookup"><span data-stu-id="0acf2-110">When you debug release builds that are compiled by using .NET Native:</span></span>  
  
-   <span data-ttu-id="0acf2-111">您會使用不同於一般 .NET 偵錯工具的 .NET 原生偵錯引擎。</span><span class="sxs-lookup"><span data-stu-id="0acf2-111">You use the .NET Native debug engine, which is different from the normal .NET debugging tools.</span></span>  
  
-   <span data-ttu-id="0acf2-112">會盡可能減少可執行檔的大小。</span><span class="sxs-lookup"><span data-stu-id="0acf2-112">The size of your executable is reduced as much as possible.</span></span> <span data-ttu-id="0acf2-113">.NET 原生降低可執行檔大小的其中一種方式，是大幅修剪執行階段例外狀況訊息，這也是在 [Runtime exception messages](#Messages) 一節中更詳細討論的主題。</span><span class="sxs-lookup"><span data-stu-id="0acf2-113">One of the ways that .NET Native reduces the size of an executable is by significantly trimming runtime exception messages, a topic discussed in greater detail in the [Runtime exception messages](#Messages) section.</span></span>  
  
-   <span data-ttu-id="0acf2-114">您的程式碼已徹底最佳化。</span><span class="sxs-lookup"><span data-stu-id="0acf2-114">Your code is heavily optimized.</span></span> <span data-ttu-id="0acf2-115">這代表會盡可能使用內嵌。</span><span class="sxs-lookup"><span data-stu-id="0acf2-115">This means that inlining is used whenever possible.</span></span> <span data-ttu-id="0acf2-116">(內嵌將程式碼從外部常式移動至呼叫常式。) .NET 原生提供特製化執行階段並實作主動內嵌的事實，會影響在偵錯時顯示的呼叫堆疊。</span><span class="sxs-lookup"><span data-stu-id="0acf2-116">(Inlining moves code from external routines into the calling routine.)   The fact that .NET Native provides a specialized runtime and implements aggressive inlining  affects the call stack that is displayed when debugging.</span></span>  <span data-ttu-id="0acf2-117">如需詳細資訊，請參閱 [Runtime call stack](#CallStack) 一節。</span><span class="sxs-lookup"><span data-stu-id="0acf2-117">For more information, see the [Runtime call stack](#CallStack) section.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0acf2-118">您可以控制偵錯和發行組建是否以 .NET 原生工具鏈編譯，方法是選取或取消選取 [使用 .NET 原生工具鏈編譯]  方塊。</span><span class="sxs-lookup"><span data-stu-id="0acf2-118">You can control whether the debug and release builds are compiled with the .NET Native tool chain by checking or unchecking the **Compile with .NET Native tool chain** box.</span></span>   <span data-ttu-id="0acf2-119">不過請注意，Windows 市集一律會編譯 App 的 .NET 原生工具鏈生產環境版本。</span><span class="sxs-lookup"><span data-stu-id="0acf2-119">Note, however, that the Windows Store will always compile the production version of your app with the .NET Native tool chain.</span></span>  
  
<a name="Messages"></a>   
## <a name="runtime-exception-messages"></a><span data-ttu-id="0acf2-120">Runtime exception messages</span><span class="sxs-lookup"><span data-stu-id="0acf2-120">Runtime exception messages</span></span>  
 <span data-ttu-id="0acf2-121">為了將應用程式可執行檔大小降到最低，.NET 原生不包含例外狀況訊息的完整文字。</span><span class="sxs-lookup"><span data-stu-id="0acf2-121">To minimize application executable size, .NET Native does not include the full text of exception messages.</span></span> <span data-ttu-id="0acf2-122">如此一來，在發行組建中擲回的執行階段例外狀況，可能無法顯示完整的例外狀況訊息文字。</span><span class="sxs-lookup"><span data-stu-id="0acf2-122">As a result, runtime exceptions thrown in release builds may not display the full text of exception messages.</span></span> <span data-ttu-id="0acf2-123">相反地，此文字可能會包含子字串，以及應遵循的詳細資訊連結。</span><span class="sxs-lookup"><span data-stu-id="0acf2-123">Instead, the text may consist of a substring along with a link to follow for more information.</span></span> <span data-ttu-id="0acf2-124">例如，例外狀況資訊可能會如下所示：</span><span class="sxs-lookup"><span data-stu-id="0acf2-124">For example, the exception information may appear as:</span></span>  
  
```  
Exception thrown: '$16_System.AggregateException' in Unknown Module.  
  
Additional information: AggregateException_ctor_DefaultMessage  
  
If there is a handler for this exception, the program may be safely continued.  
```  
  
 <span data-ttu-id="0acf2-125">如果您需要完整的例外狀況訊息，請改為執行偵錯組建。</span><span class="sxs-lookup"><span data-stu-id="0acf2-125">If you need the complete exception message,  run the debug build instead.</span></span> <span data-ttu-id="0acf2-126">例如，來自發行組建的前一筆例外狀況資訊可能會在偵錯組建中出現，如下所示：</span><span class="sxs-lookup"><span data-stu-id="0acf2-126">For example, the previous exception information  from the release build might appear as follows in the debug build:</span></span>  
  
```  
Exception thrown: 'System.AggregateException' in NativeApp.exe.  
  
Additional information: Value does not fall within the expected range.  
```  
  
<a name="CallStack"></a>   
## <a name="runtime-call-stack"></a><span data-ttu-id="0acf2-127">Runtime call stack</span><span class="sxs-lookup"><span data-stu-id="0acf2-127">Runtime call stack</span></span>  
 <span data-ttu-id="0acf2-128">因為內嵌和其他最佳化的關係，由 .NET 原生工具鏈結編譯之 App 所顯示的呼叫堆疊，可能也無法幫助您清楚識別執行階段例外狀況的路徑。</span><span class="sxs-lookup"><span data-stu-id="0acf2-128">Because of inlining and other optimizations, the call stack displayed by an app compiled by the .NET Native tool chain may not help you to  clearly identify the path to a runtime exception.</span></span>  
  
 <span data-ttu-id="0acf2-129">若要取得完整的堆疊，請改為執行偵錯組建。</span><span class="sxs-lookup"><span data-stu-id="0acf2-129">To get the full stack, run the debug build instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0acf2-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0acf2-130">See Also</span></span>  
 [<span data-ttu-id="0acf2-131">偵錯.NET 原生 Windows 通用應用程式</span><span class="sxs-lookup"><span data-stu-id="0acf2-131">Debugging .NET Native Windows Universal Apps</span></span>](http://blogs.msdn.com/b/visualstudioalm/archive/2015/07/29/debugging-net-native-windows-universal-apps.aspx)  
 [<span data-ttu-id="0acf2-132">快速入門</span><span class="sxs-lookup"><span data-stu-id="0acf2-132">Getting Started</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)
