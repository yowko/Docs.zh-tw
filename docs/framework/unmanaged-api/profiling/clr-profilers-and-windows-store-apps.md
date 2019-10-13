---
title: CLR 分析工具和 Windows 市集應用程式
ms.date: 03/30/2017
dev_langs:
- csharp
applies_to:
- Windows 10
- Windows 8
helpviewer_keywords:
- profiling API
- profiling API [.NET Framework]
- profiling managed code
- profiling managed code [Windows Store Apps]
ms.assetid: 1c8eb2e7-f20a-42f9-a795-71503486a0f5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8368930e60210b0cb470700e9c9470c57d536c13
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291407"
---
# <a name="clr-profilers-and-windows-store-apps"></a><span data-ttu-id="5cfc4-102">CLR 分析工具和 Windows 市集應用程式</span><span class="sxs-lookup"><span data-stu-id="5cfc4-102">CLR Profilers and Windows Store Apps</span></span>

<span data-ttu-id="5cfc4-103">本主題討論在撰寫診斷工具來分析在 Windows Store 應用程式中執行的 managed 程式碼時，您必須考慮的事項。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-103">This topic discusses what you need to think about when writing diagnostic tools that analyze managed code running inside a Windows Store app.</span></span> <span data-ttu-id="5cfc4-104">它也提供修改現有開發工具的指導方針，讓它們在您對 Windows Store 應用程式執行時仍可繼續運作。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-104">It also provides guidelines to modify your existing development tools so they continue to work when you run them against Windows Store apps.</span></span> <span data-ttu-id="5cfc4-105">若要瞭解這項資訊，最好是您熟悉 Common Language Runtime 分析 API 時，您已經在可針對 Windows 桌面應用程式正確執行的診斷工具中使用此 API，而且您現在有興趣修改工具可針對 Windows Store 應用程式正確執行。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-105">To understand this information, it’s best if you're  familiar with the Common Language Runtime Profiling API, you’ve already used this API in a diagnostic tool that runs correctly against Windows desktop applications, and you’re now interested in modifying the tool to run correctly against Windows Store apps.</span></span>

## <a name="introduction"></a><span data-ttu-id="5cfc4-106">簡介</span><span class="sxs-lookup"><span data-stu-id="5cfc4-106">Introduction</span></span>

<span data-ttu-id="5cfc4-107">如果您已將它放在簡介段落之後，您就會熟悉 CLR 分析 API。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-107">If you made it past the introductory paragraph, then you’re familiar with the CLR Profiling API.</span></span> <span data-ttu-id="5cfc4-108">您已經撰寫一種診斷工具，適用于受管理的桌面應用程式。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-108">You’ve already written a diagnostic tool that works well against managed desktop applications.</span></span> <span data-ttu-id="5cfc4-109">現在您想知道該怎麼做，讓您的工具可與受控的 Windows Store 應用程式搭配使用。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-109">Now you’re curious what to do so that your tool works with a managed Windows Store app.</span></span> <span data-ttu-id="5cfc4-110">也許您已經試過這項工作，併發現它不是一項簡單的任務。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-110">Perhaps you’ve already tried to make this work, and have discovered that it’s not a straightforward task.</span></span> <span data-ttu-id="5cfc4-111">事實上，所有工具開發人員可能都不會對您有許多考慮。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-111">Indeed, there are a number of considerations that might not be obvious to all tools developers.</span></span> <span data-ttu-id="5cfc4-112">例如:</span><span class="sxs-lookup"><span data-stu-id="5cfc4-112">For example:</span></span>

- <span data-ttu-id="5cfc4-113">Windows Store 應用程式會在具有嚴重降低許可權的內容中執行。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-113">Windows Store apps run in a context with severely reduced permissions.</span></span>

- <span data-ttu-id="5cfc4-114">相較于傳統的受控模組，Windows 中繼資料檔案具有獨特的特性。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-114">Windows Metadata files have unique characteristics when compared to traditional managed modules.</span></span>

- <span data-ttu-id="5cfc4-115">當互動性中斷時，Windows Store 應用程式會習慣自行暫停。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-115">Windows Store apps have a habit of suspending themselves when interactivity goes down.</span></span>

- <span data-ttu-id="5cfc4-116">您的處理序間通訊機制可能因各種原因而無法再使用。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-116">Your inter-process communication mechanisms may no longer work for various reasons.</span></span>

<span data-ttu-id="5cfc4-117">本主題列出您需要注意的事項，以及如何正確處理它們。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-117">This topic lists the things you need to be aware of and how to deal with them properly.</span></span>

<span data-ttu-id="5cfc4-118">如果您不熟悉 CLR 分析 API，請跳到本主題結尾的資源，以尋找更好的簡介資訊。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-118">If you’re new to the CLR Profiling API, skip down to the Resources at the end of this topic to find better introductory information.</span></span>

<span data-ttu-id="5cfc4-119">提供有關特定 Windows Api 及其使用方式的詳細資料，也不在本主題的討論範圍內。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-119">Providing detail about specific Windows APIs and how they should be used is also outside the scope of this topic.</span></span> <span data-ttu-id="5cfc4-120">請考慮此主題的起點，並參閱 MSDN 以深入瞭解此處參考的任何 Windows Api。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-120">Consider this topic a starting point, and refer to MSDN to learn more about any Windows APIs referenced here.</span></span>

## <a name="architecture-and-terminology"></a><span data-ttu-id="5cfc4-121">架構與術語</span><span class="sxs-lookup"><span data-stu-id="5cfc4-121">Architecture and terminology</span></span>

<span data-ttu-id="5cfc4-122">通常，診斷工具具有如下圖所示的架構。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-122">Typically, a diagnostic tool has an architecture like the one shown in the following illustration.</span></span> <span data-ttu-id="5cfc4-123">它會使用「分析工具」一詞，但許多這類工具會超越一般的效能或記憶體分析，使其成為程式碼涵蓋範圍、模擬物件架構、時間差的偵錯工具、應用程式監視等方面。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-123">It uses the term "profiler," but many such tools go well beyond typical performance or memory profiling into areas such as code coverage, mock object frameworks, time-travel debugging, application monitoring, and so on.</span></span> <span data-ttu-id="5cfc4-124">為了簡單起見，本主題將繼續將所有這些工具當做分析工具來參考。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-124">For simplicity, this topic will continue to refer to all these tools as profilers.</span></span>

<span data-ttu-id="5cfc4-125">本主題中使用下列術語：</span><span class="sxs-lookup"><span data-stu-id="5cfc4-125">The following terminology is used throughout this topic:</span></span>

<span data-ttu-id="5cfc4-126">**應用程式**</span><span class="sxs-lookup"><span data-stu-id="5cfc4-126">**Application**</span></span>

<span data-ttu-id="5cfc4-127">這是 profiler 正在分析的應用程式。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-127">This is the application that the profiler is analyzing.</span></span> <span data-ttu-id="5cfc4-128">通常，此應用程式的開發人員現在會流量分析工具來協助診斷應用程式的問題。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-128">Typically, the developer of this application is now using the profiler to help diagnose issues with the application.</span></span> <span data-ttu-id="5cfc4-129">傳統上，此應用程式會是 Windows 桌面應用程式，但在本主題中，我們會查看 Windows Store 應用程式。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-129">Traditionally, this application would be a Windows desktop application, but in this topic, we’re looking at Windows Store apps.</span></span>

<span data-ttu-id="5cfc4-130">**Profiler DLL**</span><span class="sxs-lookup"><span data-stu-id="5cfc4-130">**Profiler DLL**</span></span>

<span data-ttu-id="5cfc4-131">這是載入所分析應用程式之進程空間的元件。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-131">This is the component that loads into the process space of the application being analyzed.</span></span> <span data-ttu-id="5cfc4-132">此元件（也稱為 profiler 「代理程式」）會執行[ICorProfilerCallback](icorprofilercallback-interface.md)[ICorProfilerCallback 介面](icorprofilercallback-interface.md)（2、3等）介面，並使用[ICorProfilerInfo](icorprofilerinfo-interface.md)（2，3，等）介面來收集有關的資料。分析的應用程式，並可能修改應用程式行為的各個層面。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-132">This component, also known as the profiler "agent," implements the [ICorProfilerCallback](icorprofilercallback-interface.md)[ICorProfilerCallback Interface](icorprofilercallback-interface.md)(2,3,etc.) interfaces and consumes the [ICorProfilerInfo](icorprofilerinfo-interface.md)(2,3,etc.) interfaces to collect data about the analyzed application and potentially modify aspects of the application’s behavior.</span></span>

<span data-ttu-id="5cfc4-133">**Profiler UI**</span><span class="sxs-lookup"><span data-stu-id="5cfc4-133">**Profiler UI**</span></span>

<span data-ttu-id="5cfc4-134">這是分析工具使用者所互動的桌面應用程式。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-134">This is a desktop application that the profiler user interacts with.</span></span> <span data-ttu-id="5cfc4-135">它會負責向使用者顯示應用程式狀態，並為使用者提供控制分析應用程式行為的方法。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-135">It’s responsible for displaying application status to the user and giving the user the means to control the behavior of the analyzed application.</span></span> <span data-ttu-id="5cfc4-136">這個元件一律會在自己的進程空間中執行，與所分析應用程式的進程空間不同。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-136">This component always runs in its own process space, separate from the process space of the application being profiled.</span></span> <span data-ttu-id="5cfc4-137">分析工具 UI 也可以做為「附加觸發程式」，也就是呼叫[ICLRProfiling：： AttachProfiler](iclrprofiling-attachprofiler-method.md)方法的進程，以便在剖析器 dll 未于啟動時載入的情況下，讓分析的應用程式載入分析工具 dll。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-137">The Profiler UI can also act as the "attach trigger," which is the process that calls the [ICLRProfiling::AttachProfiler](iclrprofiling-attachprofiler-method.md) method, to cause the analyzed application to load the Profiler DLL in those cases where the profiler DLL did not load on startup.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5cfc4-138">您的 Profiler UI 應該保留 Windows 桌面應用程式，即使是用來控制和報告 Windows Store 應用程式也一樣。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-138">Your Profiler UI should remain a Windows desktop application, even when it is used to control and report on a Windows Store app.</span></span> <span data-ttu-id="5cfc4-139">不希望能夠在 Windows 市集中封裝和運送您的診斷工具。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-139">Don’t expect to be able to package and ship your diagnostics tool in the Windows Store.</span></span> <span data-ttu-id="5cfc4-140">您的工具需要執行 Windows Store 應用程式無法執行的動作，而其中有許多專案都位於您的 Profiler UI 中。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-140">Your tool needs to do things that Windows Store apps cannot do, and many of those things reside inside your Profiler UI.</span></span>

<span data-ttu-id="5cfc4-141">在本檔中，範例程式碼假設：</span><span class="sxs-lookup"><span data-stu-id="5cfc4-141">Throughout this document, the sample code assumes that:</span></span>

- <span data-ttu-id="5cfc4-142">您的 Profiler DLL 是以C++撰寫，因為它必須是原生 DLL，視 CLR 分析 API 的需求而成。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-142">Your Profiler DLL is written in C++, because it must be a native DLL, as per the requirements of the CLR Profiling API.</span></span>

- <span data-ttu-id="5cfc4-143">您的 Profiler UI 是以C#撰寫。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-143">Your Profiler UI is written in C#.</span></span> <span data-ttu-id="5cfc4-144">這並不是必要的，但因為您分析工具 UI 進程的語言沒有任何需求，所以為什麼不選擇簡潔且簡單的語言？</span><span class="sxs-lookup"><span data-stu-id="5cfc4-144">This isn’t necessary, but because there are no requirements on the language for your Profiler UI’s process, why not pick a language that’s concise and simple?</span></span>

### <a name="windows-rt-devices"></a><span data-ttu-id="5cfc4-145">Windows RT 裝置</span><span class="sxs-lookup"><span data-stu-id="5cfc4-145">Windows RT devices</span></span>

<span data-ttu-id="5cfc4-146">Windows RT 裝置已完全鎖定。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-146">Windows RT devices are quite locked down.</span></span> <span data-ttu-id="5cfc4-147">協力廠商分析工具只是無法在這類裝置上載入。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-147">Third-party profilers simply cannot be loaded on such devices.</span></span> <span data-ttu-id="5cfc4-148">本檔著重于 Windows 8 電腦。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-148">This document focuses on Windows 8 PCs.</span></span>

## <a name="consuming-windows-runtime-apis"></a><span data-ttu-id="5cfc4-149">使用 Windows 執行階段 Api</span><span class="sxs-lookup"><span data-stu-id="5cfc4-149">Consuming Windows Runtime APIs</span></span>

<span data-ttu-id="5cfc4-150">在下列各節中討論的幾個案例中，您的 Profiler UI 桌面應用程式必須使用一些新的 Windows 執行階段 Api。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-150">In a number of scenarios discussed in the following sections, your Profiler UI desktop application needs to consume some new Windows Runtime APIs.</span></span> <span data-ttu-id="5cfc4-151">您會想要參考檔，以瞭解哪些 Windows 執行階段 Api 可以從桌面應用程式使用，以及從桌面應用程式和 Windows Store 應用程式呼叫時，其行為是否不同。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-151">You’ll want to consult the documentation to understand which Windows Runtime APIs can be used from desktop applications, and whether their behavior is different when called from desktop applications and Windows Store apps.</span></span>

<span data-ttu-id="5cfc4-152">如果您的分析工具 UI 是以 managed 程式碼撰寫的，您將需要執行幾個步驟，才能輕鬆地使用這些 Windows 執行階段 Api。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-152">If your Profiler UI is written in managed code, there will be a few steps you’ll need to do to make consuming those Windows Runtime APIs easy.</span></span> <span data-ttu-id="5cfc4-153">如需詳細資訊，請參閱[受管理的桌面應用程式和 Windows 執行階段](https://go.microsoft.com/fwlink/?LinkID=271858)一文。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-153">See the [Managed desktop apps and Windows Runtime](https://go.microsoft.com/fwlink/?LinkID=271858) article for more information.</span></span>

## <a name="loading-the-profiler-dll"></a><span data-ttu-id="5cfc4-154">載入 Profiler DLL</span><span class="sxs-lookup"><span data-stu-id="5cfc4-154">Loading the Profiler DLL</span></span>

<span data-ttu-id="5cfc4-155">本節說明 Profiler UI 如何讓 Windows Store 應用程式載入您的分析工具 DLL。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-155">This section describes how your Profiler UI causes the Windows Store app to load your Profiler DLL.</span></span> <span data-ttu-id="5cfc4-156">本節中所討論的程式碼屬於您的分析工具 UI 桌面應用程式，因此牽涉到使用適用于傳統型應用程式的 Windows Api，但不一定是 Windows Store 應用程式的安全。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-156">The code discussed in this section belongs in your Profiler UI desktop app, and therefore involves using Windows APIs that are safe for desktop apps but not necessarily safe for Windows Store apps.</span></span>

<span data-ttu-id="5cfc4-157">您的 Profiler UI 可能會以兩種方式，將 Profiler DLL 載入應用程式的進程空間：</span><span class="sxs-lookup"><span data-stu-id="5cfc4-157">Your Profiler UI can cause your Profiler DLL to be loaded into the application’s process space in two ways:</span></span>

- <span data-ttu-id="5cfc4-158">在應用程式啟動時，由環境變數所控制。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-158">At application startup, as controlled by environment variables.</span></span>

- <span data-ttu-id="5cfc4-159">藉由呼叫[ICLRProfiling：： AttachProfiler](iclrprofiling-attachprofiler-method.md)方法，在啟動完成後附加至應用程式。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-159">By attaching to the application after startup is complete by calling the [ICLRProfiling::AttachProfiler](iclrprofiling-attachprofiler-method.md) method.</span></span>

<span data-ttu-id="5cfc4-160">您的第一個障礙就是取得啟動載入和附加程式碼剖析工具 DLL，以便與 Windows Store 應用程式正常搭配運作。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-160">One of your first roadblocks will be getting startup-load and attach-load of your Profiler DLL to work properly with Windows Store apps.</span></span> <span data-ttu-id="5cfc4-161">這兩種形式的載入都共用一些特殊考慮，因此讓我們開始使用。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-161">Both forms of loading share some special considerations in common, so let’s start with them.</span></span>

### <a name="common-considerations-for-startup-and-attach-loads"></a><span data-ttu-id="5cfc4-162">啟動和附加負載的一般考慮</span><span class="sxs-lookup"><span data-stu-id="5cfc4-162">Common considerations for startup and attach loads</span></span>

<span data-ttu-id="5cfc4-163">**簽署 Profiler DLL**</span><span class="sxs-lookup"><span data-stu-id="5cfc4-163">**Signing your Profiler DLL**</span></span>

<span data-ttu-id="5cfc4-164">當 Windows 嘗試載入分析工具 DLL 時，它會驗證您的 Profiler DLL 是否已正確簽署。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-164">When Windows attempts to load your Profiler DLL, it verifies that your Profiler DLL is properly signed.</span></span> <span data-ttu-id="5cfc4-165">如果不是，則預設載入會失敗。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-165">If not, the load fails by default.</span></span> <span data-ttu-id="5cfc4-166">執行此作業的方法有兩種：</span><span class="sxs-lookup"><span data-stu-id="5cfc4-166">There are two ways to do this:</span></span>

- <span data-ttu-id="5cfc4-167">請確定您的 Profiler DLL 已簽署。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-167">Ensure that your Profiler DLL is signed.</span></span>

- <span data-ttu-id="5cfc4-168">告訴您的使用者，他們必須先在他們的 Windows 8 電腦上安裝開發人員授權，才能使用您的工具。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-168">Tell your user that they must install a developer license on their Windows 8 machine before using your tool.</span></span> <span data-ttu-id="5cfc4-169">這可以從 Visual Studio 自動完成，或從命令提示字元手動執行。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-169">This can be done automatically from Visual Studio or manually from a command prompt.</span></span> <span data-ttu-id="5cfc4-170">如需詳細資訊，請參閱[取得開發人員授權](https://docs.microsoft.com/previous-versions/windows/apps/hh974578(v=win.10))。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-170">For more information, see [Get a developer license](https://docs.microsoft.com/previous-versions/windows/apps/hh974578(v=win.10)).</span></span>

<span data-ttu-id="5cfc4-171">**檔案系統許可權**</span><span class="sxs-lookup"><span data-stu-id="5cfc4-171">**File system permissions**</span></span>

<span data-ttu-id="5cfc4-172">Windows Store 應用程式必須具有從檔案系統上的位置載入和執行 Profiler DLL 的許可權，而此檔案是 residesBy 預設的，Windows Store 應用程式在大部分目錄上沒有這類許可權，而且嘗試載入 Profiler DLL 失敗會在 Windows 應用程式事件記錄檔中產生專案，如下所示：</span><span class="sxs-lookup"><span data-stu-id="5cfc4-172">The Windows Store app must have permission to load and execute your Profiler DLL from the location on the file system in which it residesBy default, the Windows Store app doesn’t have such permission on most directories, and any failed attempt to load your Profiler DLL will produce an entry in the Windows Application event log that looks something like this:</span></span>

```output
NET Runtime version 4.0.30319.17929 - Loading profiler failed during CoCreateInstance.  Profiler CLSID: '{xxxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx}'.  HRESULT: 0x80070005.  Process ID (decimal): 4688.  Message ID: [0x2504].
```

<span data-ttu-id="5cfc4-173">一般來說，Windows Store 應用程式只允許存取磁片上一組有限的位置。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-173">Generally, Windows Store apps are only allowed to access a limited set of locations on the disk.</span></span> <span data-ttu-id="5cfc4-174">每個 Windows Store 應用程式都可以存取自己的應用程式資料檔案夾，以及在檔案系統中，為所有 Windows Store 應用程式授與存取權的一些其他區域。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-174">Each Windows Store app can access its own application data folders, as well as a few other areas in the file system for which all Windows Store apps are granted access.</span></span> <span data-ttu-id="5cfc4-175">最佳做法是將您的 Profiler DLL 及其相依性安裝在 Program Files 或 Program Files （x86）底下，因為所有的 Windows Store 應用程式在預設情況下都有讀取和執行許可權。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-175">It's best to install your Profiler DLL and its dependencies somewhere under Program Files or Program Files (x86), because all Windows Store apps have read and execute permissions there by default.</span></span>

### <a name="startup-load"></a><span data-ttu-id="5cfc4-176">啟動載入</span><span class="sxs-lookup"><span data-stu-id="5cfc4-176">Startup load</span></span>

<span data-ttu-id="5cfc4-177">一般來說，在傳統型應用程式中，分析工具 UI 會藉由初始化包含必要 CLR 分析 API 環境變數（也就是 `COR_PROFILER`、`COR_ENABLE_PROFILING` 和 `COR_PROFILER_PATH`）的環境區塊，來提示您分析工具 DLL 的啟動負載，然後建立新的使用該環境區塊的處理常式。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-177">Typically, in a desktop app, your Profiler UI prompts a startup load of your Profiler DLL by initializing an environment block that contains the required CLR Profiling API environment variables (i.e., `COR_PROFILER`, `COR_ENABLE_PROFILING`, and `COR_PROFILER_PATH`), and then creating a new process with that environment block.</span></span> <span data-ttu-id="5cfc4-178">Windows Store 應用程式也是如此，但機制不同。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-178">The same holds true for Windows Store apps, but the mechanisms are different.</span></span>

<span data-ttu-id="5cfc4-179">**不要以提高許可權執行**</span><span class="sxs-lookup"><span data-stu-id="5cfc4-179">**Don’t run elevated**</span></span>

<span data-ttu-id="5cfc4-180">如果進程嘗試產生 Windows Store 應用程式進程 B，則應該以中度完整性層級執行進程，而不是在高完整性層級（也就是未提高許可權）。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-180">If Process A attempts to spawn Windows Store app Process B, Process A should be run at medium integrity level, not at high integrity level (that is, not elevated).</span></span> <span data-ttu-id="5cfc4-181">這表示您的分析工具 UI 應該以「中」完整性層級執行，或者必須產生「中」整合層級的另一個桌面進程，以處理啟動 Windows Store 應用程式。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-181">This means that either your Profiler UI should be running at medium integrity level, or it must spawn another desktop process at medium integrity level to take care of launching the Windows Store app.</span></span>

<span data-ttu-id="5cfc4-182">**選擇要分析的 Windows Store 應用程式**</span><span class="sxs-lookup"><span data-stu-id="5cfc4-182">**Choosing a Windows Store App to profile**</span></span>

<span data-ttu-id="5cfc4-183">首先，您會想要要求 profiler 使用者要啟動哪個 Windows Store 應用程式。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-183">First, you’ll want to ask your profiler user which Windows Store app to launch.</span></span> <span data-ttu-id="5cfc4-184">針對桌面應用程式，您可能會顯示 [檔案] [流覽] 對話方塊，而使用者會尋找並選取 .exe 檔案。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-184">For desktop apps, perhaps you’d show a file Browse dialog, and the user would find and select an .exe file.</span></span> <span data-ttu-id="5cfc4-185">但是，Windows Store 應用程式不同，而且使用 [流覽] 對話方塊沒有意義。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-185">But Windows Store apps are different, and using a Browse dialog doesn’t make sense.</span></span> <span data-ttu-id="5cfc4-186">相反地，最好是向使用者顯示已安裝的 Windows Store 應用程式清單，以供該使用者選取。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-186">Instead, it’s better to show the user a list of Windows Store apps installed for that user to select from.</span></span>

<span data-ttu-id="5cfc4-187">您可以使用 <xref:Windows.Management.Deployment.PackageManager> 類別來產生這份清單。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-187">You can use the <xref:Windows.Management.Deployment.PackageManager> class to generate this list.</span></span> <span data-ttu-id="5cfc4-188">`PackageManager` 是適用于桌面應用程式的 Windows 執行階段類別，事實上，它*僅*適用于桌面應用程式。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-188">`PackageManager` is a Windows Runtime class that is available to desktop apps, and in fact it is *only* available to desktop apps.</span></span>

<span data-ttu-id="5cfc4-189">下列來自以中C#的桌面應用程式撰寫的假設分析工具 UI 的程式碼範例會使用 `PackageManager` 來產生 Windows 應用程式的清單：</span><span class="sxs-lookup"><span data-stu-id="5cfc4-189">The following code example from a hypothetical Profiler UI written as a desktop app in C# uses the `PackageManager` to generate a list of Windows apps:</span></span>

```csharp
string currentUserSID = WindowsIdentity.GetCurrent().User.ToString();
IAppxFactory appxFactory = (IAppxFactory) new AppxFactory();
PackageManager packageManager = new PackageManager();
IEnumerable<Package> packages = packageManager.FindPackagesForUser(currentUserSID);
```

<span data-ttu-id="5cfc4-190">**指定自訂環境區塊**</span><span class="sxs-lookup"><span data-stu-id="5cfc4-190">**Specifying the custom environment block**</span></span>

<span data-ttu-id="5cfc4-191">新的 COM 介面[IPackageDebugSettings](/windows/desktop/api/shobjidl_core/nn-shobjidl_core-ipackagedebugsettings)可讓您自訂 Windows Store 應用程式的執行行為，讓某些形式的診斷變得更容易。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-191">A new COM interface, [IPackageDebugSettings](/windows/desktop/api/shobjidl_core/nn-shobjidl_core-ipackagedebugsettings), allows you to customize the execution behavior of a Windows Store app to make some forms of diagnostics easier.</span></span> <span data-ttu-id="5cfc4-192">它的其中一個方法[EnableDebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-enabledebugging)，可讓您在啟動時將環境區塊傳遞至 Windows Store 應用程式，以及其他實用的效果，例如停用自動進程暫止。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-192">One of its methods, [EnableDebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-enabledebugging), lets you pass an environment block to the Windows Store app when it’s launched, along with other useful effects like disabling automatic process suspension.</span></span> <span data-ttu-id="5cfc4-193">環境區塊很重要，因為您必須在此指定 CLR 用來載入分析工具 DLL 的環境變數（`COR_PROFILER`、`COR_ENABLE_PROFILING` 和 `COR_PROFILER_PATH)`）。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-193">The environment block is important because that’s where you need to specify the environment variables (`COR_PROFILER`, `COR_ENABLE_PROFILING`, and `COR_PROFILER_PATH)`) used by the CLR to load your Profiler DLL .</span></span>

<span data-ttu-id="5cfc4-194">請考慮下列程式碼片段：</span><span class="sxs-lookup"><span data-stu-id="5cfc4-194">Consider the following code snippet:</span></span>

```csharp
IPackageDebugSettings pkgDebugSettings = new PackageDebugSettings();
pkgDebugSettings.EnableDebugging(packageFullName, debuggerCommandLine,
                                                                 (IntPtr)fixedEnvironmentPzz);
```

<span data-ttu-id="5cfc4-195">您必須先取得幾個專案：</span><span class="sxs-lookup"><span data-stu-id="5cfc4-195">There are a couple of items you'll need to get right:</span></span>

- <span data-ttu-id="5cfc4-196">在逐一查看封裝並抓取 `package.Id.FullName` 時，可以判斷 `packageFullName`。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-196">`packageFullName` can be determined while iterating over the packages and grabbing `package.Id.FullName`.</span></span>

- <span data-ttu-id="5cfc4-197">`debuggerCommandLine` 更有趣。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-197">`debuggerCommandLine` is a bit more interesting.</span></span> <span data-ttu-id="5cfc4-198">若要將自訂環境區塊傳遞至 Windows Store 應用程式，您需要撰寫您自己、簡單的虛擬偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-198">In order to pass the custom environment block to the Windows Store app, you need to write your own, simplistic dummy debugger.</span></span> <span data-ttu-id="5cfc4-199">Windows 會產生已暫停的 Windows Store 應用程式，然後使用命令列啟動偵錯工具（如下列範例所示）來附加偵錯工具：</span><span class="sxs-lookup"><span data-stu-id="5cfc4-199">Windows spawns the Windows Store app suspended and then attaches your debugger by launching your debugger with a command line like in this example:</span></span>

    ```console
    MyDummyDebugger.exe -p 1336 -tid 1424
    ```

     <span data-ttu-id="5cfc4-200">其中 `-p 1336` 表示 Windows Store 應用程式具有處理序識別碼1336，而 `-tid 1424` 表示執行緒識別碼1424是已暫停的執行緒。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-200">where `-p 1336` means the Windows Store app has Process ID 1336, and `-tid 1424` means Thread ID 1424 is the thread that is suspended.</span></span> <span data-ttu-id="5cfc4-201">您的虛擬偵錯工具會從命令列剖析 ThreadID，繼續該執行緒，然後結束。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-201">Your dummy debugger would parse the ThreadID from the command-line, resume that thread, and then exit.</span></span>

     <span data-ttu-id="5cfc4-202">以下是一些執行C++此動作的範例程式碼（請務必新增錯誤檢查！）：</span><span class="sxs-lookup"><span data-stu-id="5cfc4-202">Here’s some example C++ code to do this (be sure to add error checking!):</span></span>

    ```cpp
    int wmain(int argc, wchar_t* argv[])
    {
        // …
        // Parse command line here
        // …

        HANDLE hThread = OpenThread(THREAD_SUSPEND_RESUME,
                                                                  FALSE /* bInheritHandle */, nThreadID);
        ResumeThread(hThread);
        CloseHandle(hThread);
        return 0;
    }
    ```

     <span data-ttu-id="5cfc4-203">您必須將此虛擬偵錯工具部署為診斷工具安裝的一部分，然後在 `debuggerCommandLine` 參數中指定此偵錯工具的路徑。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-203">You’ll need to deploy this dummy debugger as part of your diagnostics tool installation, and then specify the path to this debugger in the `debuggerCommandLine` parameter.</span></span>

<span data-ttu-id="5cfc4-204">**啟動 Windows Store 應用程式**</span><span class="sxs-lookup"><span data-stu-id="5cfc4-204">**Launching the Windows Store app**</span></span>

<span data-ttu-id="5cfc4-205">Windows Store 應用程式的啟動時間終於到達。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-205">The moment to launch the Windows Store app has finally arrived.</span></span> <span data-ttu-id="5cfc4-206">如果您已自行嘗試這麼做，您可能已注意到[CreateProcess](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createprocessa)並不是您建立 Windows Store 應用程式進程的方式。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-206">If you’ve already tried doing this yourself, you may have noticed that [CreateProcess](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createprocessa) is not how you create a Windows Store app process.</span></span> <span data-ttu-id="5cfc4-207">相反地，您必須使用[IApplicationActivationManager：： ActivateApplication](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-iapplicationactivationmanager-activateapplication)方法。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-207">Instead, you’ll need to use the [IApplicationActivationManager::ActivateApplication](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-iapplicationactivationmanager-activateapplication) method.</span></span> <span data-ttu-id="5cfc4-208">若要這麼做，您必須取得您要啟動之 Windows Store 應用程式的應用程式使用者模型識別碼。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-208">To do that, you’ll need to get the App User Model ID of the Windows Store app that you’re launching.</span></span> <span data-ttu-id="5cfc4-209">這表示您必須透過資訊清單執行一些深入探討。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-209">And that means you’ll need to do a little digging through the manifest.</span></span>

<span data-ttu-id="5cfc4-210">在反復執行封裝時（請參閱稍早[啟動載入](#startup-load)區段中的「選擇要分析的 Windows Store 應用程式」），您會想要抓取目前套件資訊清單中所包含的應用程式集合：</span><span class="sxs-lookup"><span data-stu-id="5cfc4-210">While iterating over your packages (see "Choosing a Windows Store App to Profile" in the [Startup load](#startup-load) section earlier), you’ll want to grab the set of applications contained in the current package’s manifest:</span></span>

```csharp
string manifestPath = package.InstalledLocation.Path + "\\AppxManifest.xml";

AppxPackaging.IStream manifestStream;
SHCreateStreamOnFileEx(
                    manifestPath,
                    0x00000040,     // STGM_READ | STGM_SHARE_DENY_NONE
                    0,              // file creation attributes
                    false,          // fCreate
                    null,           // reserved
                    out manifestStream);

IAppxManifestReader manifestReader = appxFactory.CreateManifestReader(manifestStream);

IAppxManifestApplicationsEnumerator appsEnum = manifestReader.GetApplications();
```

<span data-ttu-id="5cfc4-211">是，一個封裝可以有多個應用程式，而且每個應用程式都有自己的應用程式使用者模型識別碼。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-211">Yes, one package can have multiple applications, and each application has its own Application User Model ID.</span></span> <span data-ttu-id="5cfc4-212">因此，您會想要向使用者要求要分析的應用程式，並從該特定應用程式抓取應用程式使用者模型識別碼：</span><span class="sxs-lookup"><span data-stu-id="5cfc4-212">So you’ll want to ask your user which application to profile, and grab the Application User Model ID from that particular application:</span></span>

```csharp
while (appsEnum.GetHasCurrent() != 0)
{
    IAppxManifestApplication app = appsEnum.GetCurrent();
    string appUserModelId = app.GetAppUserModelId();
    //...
}
```

<span data-ttu-id="5cfc4-213">最後，您現在已具備啟動 Windows Store 應用程式所需的功能：</span><span class="sxs-lookup"><span data-stu-id="5cfc4-213">Finally, you now have what you need to launch the Windows Store app:</span></span>

```csharp
IApplicationActivationManager appActivationMgr = new ApplicationActivationManager();
appActivationMgr.ActivateApplication(appUserModelId, appArgs, ACTIVATEOPTIONS.AO_NONE, out pid);
```

<span data-ttu-id="5cfc4-214">**請記得呼叫 DisableDebugging**</span><span class="sxs-lookup"><span data-stu-id="5cfc4-214">**Remember to call DisableDebugging**</span></span>

<span data-ttu-id="5cfc4-215">當您呼叫[IPackageDebugSettings：： EnableDebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-enabledebugging)時，您所做出的承諾是藉由呼叫[IPackageDebugSettings：:D isabledebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-disabledebugging)方法來自行清除，因此當分析會話結束時，請務必這麼做。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-215">When you called [IPackageDebugSettings::EnableDebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-enabledebugging), you made a promise that you would clean up after yourself by calling the [IPackageDebugSettings::DisableDebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-disabledebugging) method, so be sure to do that when the profiling session is over.</span></span>

### <a name="attach-load"></a><span data-ttu-id="5cfc4-216">附加負載</span><span class="sxs-lookup"><span data-stu-id="5cfc4-216">Attach load</span></span>

<span data-ttu-id="5cfc4-217">當您的 Profiler UI 想要將其 Profiler DLL 附加至已經開始執行的應用程式時，它會使用[ICLRProfiling：： AttachProfiler](iclrprofiling-attachprofiler-method.md)。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-217">When your Profiler UI wants to attach its Profiler DLL to an application that has already started running, it uses [ICLRProfiling::AttachProfiler](iclrprofiling-attachprofiler-method.md).</span></span> <span data-ttu-id="5cfc4-218">Windows Store 應用程式也是如此。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-218">The same holds true with Windows Store apps.</span></span> <span data-ttu-id="5cfc4-219">但是除了先前所列的一般考慮之外，請確定目標 Windows 儲存區應用程式未暫停。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-219">But in addition to the common considerations listed earlier, make sure the that the target Windows Store app is not suspended.</span></span>

<span data-ttu-id="5cfc4-220">**EnableDebugging**</span><span class="sxs-lookup"><span data-stu-id="5cfc4-220">**EnableDebugging**</span></span>

<span data-ttu-id="5cfc4-221">如同啟動載入，請呼叫[IPackageDebugSettings：： EnableDebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-enabledebugging)方法。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-221">As with startup load, call the [IPackageDebugSettings::EnableDebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-enabledebugging) method.</span></span> <span data-ttu-id="5cfc4-222">您不需要它來傳遞環境區塊，但您需要其中一個其他功能：停用自動處理常式擱置。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-222">You don’t need it for passing an environment block, but you need one of its other features: disabling automatic process suspension.</span></span> <span data-ttu-id="5cfc4-223">否則，當您的 Profiler UI 呼叫[AttachProfiler](iclrprofiling-attachprofiler-method.md)時，目標 Windows Store 應用程式可能會暫停。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-223">Otherwise, when your Profiler UI calls [AttachProfiler](iclrprofiling-attachprofiler-method.md), the target Windows Store app may be suspended.</span></span> <span data-ttu-id="5cfc4-224">事實上，如果使用者現在與您的分析工具 UI 互動，而 Windows Store 應用程式在任何使用者畫面上都不是作用中，這就很有可能。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-224">In fact, this is likely if the user is now interacting with your Profiler UI, and the Windows Store app is not active on any of the user’s screens.</span></span> <span data-ttu-id="5cfc4-225">而且，如果 Windows 儲存區應用程式已暫止，它將無法回應 CLR 傳送給它的任何信號，以附加您的分析工具 DLL。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-225">And if the Windows Store app is suspended, it won’t be able to respond to any signal that the CLR sends to it to attach your Profiler DLL.</span></span>

<span data-ttu-id="5cfc4-226">因此，您會想要執行如下的動作：</span><span class="sxs-lookup"><span data-stu-id="5cfc4-226">So you’ll want to do something like this:</span></span>

```csharp
IPackageDebugSettings pkgDebugSettings = new PackageDebugSettings();
pkgDebugSettings.EnableDebugging(packageFullName, null /* debuggerCommandLine */,
                                                                 IntPtr.Zero /* environment */);
```

<span data-ttu-id="5cfc4-227">這是您針對啟動載入案例所做的相同呼叫，但您不需要指定偵錯工具命令列或環境區塊。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-227">This is the same call you’d make for the startup load case, except you don’t specify a debugger command line or an environment block.</span></span>

<span data-ttu-id="5cfc4-228">**DisableDebugging**</span><span class="sxs-lookup"><span data-stu-id="5cfc4-228">**DisableDebugging**</span></span>

<span data-ttu-id="5cfc4-229">一如往常，當您的分析會話完成時，別忘了呼叫[IPackageDebugSettings：:D isabledebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-disabledebugging) 。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-229">As always, don’t forget to call [IPackageDebugSettings::DisableDebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-disabledebugging) when your profiling session is completed.</span></span>

## <a name="running-inside-the-windows-store-app"></a><span data-ttu-id="5cfc4-230">在 Windows Store 應用程式中執行</span><span class="sxs-lookup"><span data-stu-id="5cfc4-230">Running inside the Windows Store app</span></span>

<span data-ttu-id="5cfc4-231">因此，Windows Store 應用程式終於已載入您的 Profiler DLL。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-231">So the Windows Store app has finally loaded your Profiler DLL.</span></span> <span data-ttu-id="5cfc4-232">現在，您的分析工具 DLL 必須教您如何透過 Windows Store 應用程式所需的不同規則來播放，包括允許哪些 Api，以及如何以降低的許可權執行。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-232">Now your Profiler DLL must be taught how to play by the different rules required by Windows Store apps, including which APIs are allowable and how to run with reduced permissions.</span></span>

### <a name="stick-to-the-windows-store-app-apis"></a><span data-ttu-id="5cfc4-233">堅持 Windows Store 應用程式 Api</span><span class="sxs-lookup"><span data-stu-id="5cfc4-233">Stick to the Windows Store app APIs</span></span>

<span data-ttu-id="5cfc4-234">當您流覽 Windows API 時，您會注意到每個 API 都記載為適用于桌面應用程式、Windows Store 應用程式或兩者。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-234">As you browse the Windows API, you’ll notice that every API is documented as being applicable to desktop apps, Windows Store apps, or both.</span></span> <span data-ttu-id="5cfc4-235">例如， [InitializeCriticalSectionAndSpinCount](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionandspincount)函式檔的 [**需求**] 區段指出函式僅適用于桌面應用程式。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-235">For example, the **Requirements** section of the documentation for the [InitializeCriticalSectionAndSpinCount](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionandspincount) function indicates that the function applies to desktop apps only.</span></span> <span data-ttu-id="5cfc4-236">相反地，桌面應用程式和 Windows Store 應用程式都有提供[InitializeCriticalSectionEx](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionex)函式。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-236">In contrast, the [InitializeCriticalSectionEx](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionex) function is available for both desktop apps and Windows Store apps.</span></span>

<span data-ttu-id="5cfc4-237">開發分析工具 DLL 時，請將它視為 Windows Store 應用程式，並只使用已記載為可供 Windows Store 應用程式使用的 Api。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-237">When developing your Profiler DLL, treat it as if it’s a Windows Store app and only use APIs that are documented as available to Windows Store apps.</span></span> <span data-ttu-id="5cfc4-238">分析您的相依性（例如，您可以針對分析工具 DLL 執行 `link /dump /imports` 來進行審核），然後搜尋檔以查看哪些相依性是正常的，哪些不是。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-238">Analyze your dependencies (for example, you can run `link /dump /imports` against your Profiler DLL to audit), and then search the docs to see which of your dependencies are ok and which aren’t.</span></span> <span data-ttu-id="5cfc4-239">在大部分的情況下，您只要以較新的 API 形式（也就是將[InitializeCriticalSectionAndSpinCount](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionandspincount)取代為[InitializeCriticalSectionEx](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionex)）取代，就可以修正您的違規。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-239">In most cases, your violations can be fixed by simply replacing them with a newer form of the API that is documented as safe (for example, replacing [InitializeCriticalSectionAndSpinCount](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionandspincount) with [InitializeCriticalSectionEx](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionex)).</span></span>

<span data-ttu-id="5cfc4-240">您可能會注意到您的分析工具 DLL 會呼叫一些僅適用于桌面應用程式的 Api，但即使您的分析工具 DLL 載入 Windows Store 應用程式中，它們還是看起來很有作用。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-240">You might notice that your Profiler DLL calls some APIs that apply to desktop apps only, and yet they seem to work even when your Profiler DLL is loaded inside a Windows Store app.</span></span> <span data-ttu-id="5cfc4-241">請注意，當您載入 Windows Store 應用程式進程時，流量分析工具 DLL 中的 Windows Store 應用程式未記載的任何 API，會有風險：</span><span class="sxs-lookup"><span data-stu-id="5cfc4-241">Be aware that it’s risky to use any API not documented for use with Windows Store apps in your Profiler DLL when loaded into a Windows Store app process:</span></span>

- <span data-ttu-id="5cfc4-242">在 Windows Store 應用程式執行所在的唯一內容中呼叫這類 Api 時，並不保證會運作。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-242">Such APIs are not guaranteed to work when called in the unique context that Windows Store apps run in.</span></span>

- <span data-ttu-id="5cfc4-243">從不同的 Windows Store 應用程式進程中呼叫時，這類 Api 可能無法一致地工作。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-243">Such APIs might not work consistently when called from within different Windows Store app processes.</span></span>

- <span data-ttu-id="5cfc4-244">這類 Api 在目前 Windows 版本的 Windows Store 應用程式中看起來可能很正常，但在未來的 Windows 版本中可能會中斷或停用。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-244">Such APIs might seem to work fine from Windows Store apps in the current version of Windows, but may break or be disabled in future releases of Windows.</span></span>

<span data-ttu-id="5cfc4-245">最佳建議是修正您所有的違規，並避免風險。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-245">The best advice is to fix all your violations and avoid the risk.</span></span>

<span data-ttu-id="5cfc4-246">您可能會發現，在沒有特定 API 的情況下，您絕對無法執行，而且找不到適用于 Windows Store 應用程式的取代。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-246">You might find that you absolutely cannot do without a particular API and cannot find a replacement suitable for Windows Store apps.</span></span> <span data-ttu-id="5cfc4-247">在這種情況下，至少：</span><span class="sxs-lookup"><span data-stu-id="5cfc4-247">In such a case, at a minimum:</span></span>

- <span data-ttu-id="5cfc4-248">測試、測試、測試您在使用該 API 時的生活 daylights。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-248">Test, test, test the living daylights out of your usage of that API.</span></span>

- <span data-ttu-id="5cfc4-249">瞭解在未來的 Windows 版本中，如果從 Windows Store 應用程式中呼叫，API 可能突然中斷或消失。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-249">Understand that the API might suddenly break or disappear if called from inside Windows Store apps in future releases of Windows.</span></span> <span data-ttu-id="5cfc4-250">這不會被視為 Microsoft 的相容性問題，而且支援您的使用方式將不會是優先考慮。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-250">This won’t be considered a compatibility concern by Microsoft, and supporting your usage of it will not be a priority.</span></span>

### <a name="reduced-permissions"></a><span data-ttu-id="5cfc4-251">降低許可權</span><span class="sxs-lookup"><span data-stu-id="5cfc4-251">Reduced permissions</span></span>

<span data-ttu-id="5cfc4-252">這不在本主題的討論範圍內，以列出 Windows Store 應用程式許可權與桌面應用程式不同的所有方式。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-252">It’s outside the scope of this topic to list all the ways that Windows Store app permissions differ from desktop apps.</span></span> <span data-ttu-id="5cfc4-253">但當然，每當您的分析工具 DLL （載入至 Windows Store 應用程式時，相較于桌面應用程式）嘗試存取任何資源時，行為會有所不同。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-253">But certainly the behavior will be different every time your Profiler DLL (when loaded into a Windows Store app as compared to a desktop app) tries to access any resources.</span></span> <span data-ttu-id="5cfc4-254">檔案系統是最常見的範例。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-254">The file system is the most common example.</span></span> <span data-ttu-id="5cfc4-255">在磁片上，有幾個位置可供指定的 Windows Store 應用程式存取（請參閱檔案[存取和許可權（Windows 執行階段應用程式](https://docs.microsoft.com/previous-versions/windows/apps/hh967755(v=win.10))），而您的分析工具 DLL 會受到相同的限制。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-255">There are but a few places on disk that a given Windows Store app is allowed to access (see [File access and permissions (Windows Runtime apps](https://docs.microsoft.com/previous-versions/windows/apps/hh967755(v=win.10))), and your Profiler DLL will be under the same restrictions.</span></span> <span data-ttu-id="5cfc4-256">徹底測試您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-256">Test your code thoroughly.</span></span>

### <a name="inter-process-communication"></a><span data-ttu-id="5cfc4-257">處理序間通訊</span><span class="sxs-lookup"><span data-stu-id="5cfc4-257">Inter-process communication</span></span>

<span data-ttu-id="5cfc4-258">如本文開頭的圖表所示，您的分析工具 DLL （載入至 Windows Store 應用程式進程空間）可能需要透過您自己的自訂進程間，與您的分析工具 UI 通訊（在不同的桌面應用程式進程空間中執行）通訊（IPC）通道。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-258">As shown in the diagram at the beginning of this paper, your Profiler DLL (loaded into the Windows Store app process space) will likely need to communicate with your Profiler UI (running in a separate desktop app process space) through your own custom inter-process communication (IPC) channel.</span></span> <span data-ttu-id="5cfc4-259">分析工具 UI 會將信號傳送至 Profiler DLL 以修改其行為，而 Profiler DLL 會將資料從分析的 Windows Store 應用程式傳送回 Profiler UI，以進行後置處理，並向 profiler 使用者顯示。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-259">The Profiler UI sends signals to the Profiler DLL to modify its behavior, and the Profiler DLL sends data from the analyzed Windows Store app back to the Profiler UI for post-processing and displaying to the profiler user.</span></span>

<span data-ttu-id="5cfc4-260">大部分的分析工具都需要以這種方式來工作，但當您的分析工具 DLL 載入至 Windows Store 應用程式時，您對 IPC 機制的選擇會更有限制。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-260">Most profilers need to work this way, but your choices for IPC mechanisms are more limited when your Profiler DLL is loaded into a Windows Store app.</span></span> <span data-ttu-id="5cfc4-261">例如，具名管道不是 Windows Store 應用程式 SDK 的一部分，因此您無法使用它們。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-261">For example, named pipes are not part of the Windows Store app SDK, so you cannot use them.</span></span>

<span data-ttu-id="5cfc4-262">但當然，檔案仍在中，雖然是以較有限的方式提供。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-262">But of course, files are still in, albeit in a more limited fashion.</span></span> <span data-ttu-id="5cfc4-263">事件也可供使用。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-263">Events are also available.</span></span>

<span data-ttu-id="5cfc4-264">**透過檔案通訊**</span><span class="sxs-lookup"><span data-stu-id="5cfc4-264">**Communicating via files**</span></span>

<span data-ttu-id="5cfc4-265">大部分的資料可能會透過檔案在分析工具 DLL 和 Profiler UI 之間通過。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-265">Most of your data will likely pass between the Profiler DLL and Profiler UI via files.</span></span> <span data-ttu-id="5cfc4-266">關鍵在於選擇檔案位置，讓您的分析工具 DLL （在 Windows Store 應用程式的內容中）和 Profiler UI 具有的讀取和寫入權限。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-266">The key is to pick a file location that both your Profiler DLL (in the context of a Windows Store app) and Profiler UI have read and write access to.</span></span> <span data-ttu-id="5cfc4-267">例如，暫存資料夾路徑是分析工具 DLL 和分析工具 UI 可以存取的位置，但是沒有其他 Windows 儲存區應用程式套件可以存取（因而防護您從其他 Windows Store 應用程式套件記錄的任何資訊）。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-267">For example, the Temporary Folder path is a location that both your Profiler DLL and Profiler UI can access, but no other Windows Store app package can access (thus shielding any information you log from other Windows Store app packages).</span></span>

<span data-ttu-id="5cfc4-268">您的 Profiler UI 和 Profiler DLL 都可以獨立判斷此路徑。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-268">Both your Profiler UI and Profiler DLL can determine this path independently.</span></span> <span data-ttu-id="5cfc4-269">分析工具 UI，當它逐一查看所有為目前使用者安裝的封裝（請參閱稍早的範例程式碼）時，會取得 `PackageId` 類別的存取權，其中暫存資料夾路徑可以使用類似于此程式碼片段的程式碼來衍生。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-269">Your Profiler UI, when it iterates through all packages installed for the current user (see the sample code earlier), gets access to the `PackageId` class, from which the Temporary Folder path can be derived with code similar to this snippet.</span></span> <span data-ttu-id="5cfc4-270">（一如往常，為了簡潔起見，會省略錯誤檢查）。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-270">(As always, error checking is omitted for brevity.)</span></span>

```csharp
// C# code for the Profiler UI.
ApplicationData appData =
    ApplicationDataManager.CreateForPackageFamily(
        packageId.FamilyName);

tempDir = appData.TemporaryFolder.Path;
```

<span data-ttu-id="5cfc4-271">同時，您的分析工具 DLL 基本上可以執行相同的動作，不過使用[ApplicationData](xref:Windows.Storage.ApplicationData.Current%2A)屬性可以更輕鬆地取得 @no__t 0 類別。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-271">Meanwhile, your Profiler DLL can do basically the same thing, though it can more easily get to the <xref:Windows.Storage.ApplicationData> class by using the [ApplicationData.Current](xref:Windows.Storage.ApplicationData.Current%2A) property.</span></span>

<span data-ttu-id="5cfc4-272">**透過事件通訊**</span><span class="sxs-lookup"><span data-stu-id="5cfc4-272">**Communicating via events**</span></span>

<span data-ttu-id="5cfc4-273">如果您想要讓分析工具 UI 與 Profiler DLL 之間有簡單的信號，您可以在 Windows Store 應用程式和桌面應用程式中使用事件。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-273">If you want simple signaling semantics between your Profiler UI and Profiler DLL, you can use events inside Windows Store apps as well as desktop apps.</span></span>

<span data-ttu-id="5cfc4-274">從您的分析工具 DLL，您可以直接呼叫[CreateEventEx](/windows/desktop/api/synchapi/nf-synchapi-createeventexa)函式，以您喜歡的任何名稱來建立名為的事件。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-274">From your Profiler DLL, you can simply call the [CreateEventEx](/windows/desktop/api/synchapi/nf-synchapi-createeventexa) function to create a named event with any name you like.</span></span> <span data-ttu-id="5cfc4-275">例如:</span><span class="sxs-lookup"><span data-stu-id="5cfc4-275">For example:</span></span>

```cpp
// Profiler DLL in Windows Store app (C++).
CreateEventEx(
    NULL,  // Not inherited
    "MyNamedEvent"
    CREATE_EVENT_MANUAL_RESET, /* explicit ResetEvent() required; leave initial state unsignaled */
    EVENT_ALL_ACCESS);
```

<span data-ttu-id="5cfc4-276">接著，您的分析工具 UI 就必須在 Windows Store 應用程式的命名空間下尋找該命名事件。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-276">Your Profiler UI then needs to find that named event under the Windows Store app’s namespace.</span></span> <span data-ttu-id="5cfc4-277">例如，您的 Profiler UI 可以呼叫[CreateEventEx](/windows/desktop/api/synchapi/nf-synchapi-createeventexa)，並將事件名稱指定為</span><span class="sxs-lookup"><span data-stu-id="5cfc4-277">For example, your Profiler UI could call [CreateEventEx](/windows/desktop/api/synchapi/nf-synchapi-createeventexa), specifying the event name as</span></span>

`AppContainerNamedObjects\<acSid>\MyNamedEvent`

<span data-ttu-id="5cfc4-278">`<acSid>` 是 Windows Store 應用程式的 AppContainer SID。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-278">`<acSid>` is the Windows Store app’s AppContainer SID.</span></span> <span data-ttu-id="5cfc4-279">本主題稍早的章節示範如何逐一查看針對目前使用者所安裝的套件。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-279">An earlier section of this topic showed how to iterate over the packages installed for the current user.</span></span> <span data-ttu-id="5cfc4-280">從該範例程式碼中，您可以取得 packageId。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-280">From that sample code, you can obtain the packageId.</span></span> <span data-ttu-id="5cfc4-281">而從 packageId，您可以使用與下列類似的程式碼取得 `<acSid>`：</span><span class="sxs-lookup"><span data-stu-id="5cfc4-281">And from the packageId, you can obtain the `<acSid>` with code similar to the following:</span></span>

```csharp
IntPtr acPSID;
DeriveAppContainerSidFromAppContainerName(packageId.FamilyName, out acPSID);

string acSid;
ConvertSidToStringSid(acPSID, out acSid);

string acDir;
GetAppContainerFolderPath(acSid, out acDir);
```

### <a name="no-shutdown-notifications"></a><span data-ttu-id="5cfc4-282">沒有關機通知</span><span class="sxs-lookup"><span data-stu-id="5cfc4-282">No shutdown notifications</span></span>

<span data-ttu-id="5cfc4-283">在 Windows Store 應用程式中執行時，您的分析工具 DLL 不應依賴[ICorProfilerCallback：： Shutdown](icorprofilercallback-shutdown-method.md) ，[或甚至是](/windows/desktop/Dlls/dllmain)使用 `DLL_PROCESS_DETACH`）來通知分析工具 dll，Windows Store 應用程式即將結束。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-283">When running inside a Windows Store app, your Profiler DLL should not rely on either [ICorProfilerCallback::Shutdown](icorprofilercallback-shutdown-method.md) or even [DllMain](/windows/desktop/Dlls/dllmain) (with `DLL_PROCESS_DETACH`) being called to notify your Profiler DLL that the Windows Store app is exiting.</span></span> <span data-ttu-id="5cfc4-284">事實上，您應該預期它們永遠不會被呼叫。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-284">In fact, you should expect they will never be called.</span></span> <span data-ttu-id="5cfc4-285">在過去，許多 Profiler Dll 已使用這些通知做為方便的位置，可將快取快取到磁片、關閉檔案、將通知傳送回分析工具 UI 等等。但現在您的 Profiler DLL 必須以不同的方式組織。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-285">Historically, many Profiler DLLs have used those notifications as convenient places to flush caches to disk, close files, send notifications back to the Profiler UI, etc. But now your Profiler DLL needs to be organized a little differently.</span></span>

<span data-ttu-id="5cfc4-286">分析工具 DLL 應記錄資訊。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-286">Your Profiler DLL should be logging information as it goes.</span></span> <span data-ttu-id="5cfc4-287">基於效能的考慮，您可能會想要在記憶體中批次處理資訊，並在批次大小超過某個臨界值時將資料排清到磁片。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-287">For performance reasons, you may want to batch information in memory and flush it to disk as the batch grows in size past some threshold.</span></span> <span data-ttu-id="5cfc4-288">但假設尚未排清到磁片的任何資訊都可能遺失。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-288">But assume that any information not yet flushed to disk can be lost.</span></span> <span data-ttu-id="5cfc4-289">這表示您會想要明智地挑選您的臨界值，而且您的分析工具 UI 必須強化，才能處理 Profiler DLL 所寫入的不完整資訊。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-289">This means you’ll want to pick your threshold wisely, and that your Profiler UI needs to be hardened to deal with incomplete information written by the Profiler DLL.</span></span>

## <a name="windows-runtime-metadata-files"></a><span data-ttu-id="5cfc4-290">Windows 執行階段中繼資料檔案</span><span class="sxs-lookup"><span data-stu-id="5cfc4-290">Windows Runtime metadata files</span></span>

<span data-ttu-id="5cfc4-291">本檔不在本文的討論範圍內，以詳細瞭解 Windows 執行階段中繼資料（WinMD）檔案。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-291">It is outside the scope of this document to go into detail on what Windows Runtime metadata (WinMD) files are.</span></span> <span data-ttu-id="5cfc4-292">本節僅限於當 WinMD 檔案是由 Profiler DLL 正在分析的 Windows Store 應用程式載入時，CLR 分析 API 的回應方式。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-292">This section is limited to how the CLR Profiling API reacts when WinMD files are loaded by the Windows Store app your Profiler DLL is analyzing.</span></span>

### <a name="managed-and-non-managed-winmds"></a><span data-ttu-id="5cfc4-293">受控和非受控 Winmd</span><span class="sxs-lookup"><span data-stu-id="5cfc4-293">Managed and non-managed WinMDs</span></span>

<span data-ttu-id="5cfc4-294">如果開發人員使用 Visual Studio 建立新的 Windows 執行階段元件專案，則該專案的組建會產生 WinMD 檔案，以描述開發人員所撰寫的中繼資料（類別、介面等的類型描述）。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-294">If a developer uses Visual Studio to create a new Windows Runtime Component project, a build of that project produces a WinMD file that describes the metadata (the type descriptions of classes, interfaces, etc.) authored by the developer.</span></span> <span data-ttu-id="5cfc4-295">如果此專案是以C#或 VB 撰寫的 managed 語言專案，則相同的 WinMD 檔案也會包含這些類型的實作為（表示它包含從開發人員的原始程式碼所編譯的所有 IL）。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-295">If this project is a managed language project written in C# or VB, that same WinMD file also contains the implementation of those types (meaning that it contains all the IL compiled from the developer’s source code).</span></span> <span data-ttu-id="5cfc4-296">這類檔案稱為受控 WinMD 檔案。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-296">Such files are known as managed WinMD files.</span></span> <span data-ttu-id="5cfc4-297">它們很有趣，因為它們同時包含 Windows 執行階段中繼資料和基礎執行。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-297">They're interesting in that they contain both Windows Runtime metadata and the underlying implementation.</span></span>

<span data-ttu-id="5cfc4-298">相反地，如果開發人員建立的 Windows 執行階段元件專案C++，則該專案的組建會產生僅包含中繼資料的 WinMD 檔案，並將此實編譯成個別的原生 DLL。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-298">In contrast, if a developer creates a Windows Runtime Component project for C++, a build of that project produces a WinMD file that contains only metadata, and the implementation is compiled into a separate native DLL.</span></span> <span data-ttu-id="5cfc4-299">同樣地，隨附于 Windows SDK 中的 WinMD 檔案只包含中繼資料，並編譯成個別的原生 Dll，並隨附于 Windows 中。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-299">Similarly, the WinMD files that ship in the Windows SDK contain only metadata, with the implementation compiled into separate native DLLs that ship as part of Windows.</span></span>

<span data-ttu-id="5cfc4-300">下列資訊適用于 managed Winmd，其中包含中繼資料和實作為，以及僅包含中繼資料的非受控 Winmd。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-300">The information below applies to both managed WinMDs, which contain metadata and implementation, and to non-managed WinMDs, which contain only metadata.</span></span>

### <a name="winmd-files-look-like-clr-modules"></a><span data-ttu-id="5cfc4-301">WinMD 檔案看起來像 CLR 模組</span><span class="sxs-lookup"><span data-stu-id="5cfc4-301">WinMD files look like CLR modules</span></span>

<span data-ttu-id="5cfc4-302">就 CLR 的顧慮而言，所有 WinMD 檔案都是模組。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-302">As far as the CLR is concerned, all WinMD files are modules.</span></span> <span data-ttu-id="5cfc4-303">因此，CLR 分析 API 會在 WinMD 檔案載入及其 ModuleIDs 時，告訴您的 Profiler DLL，其方式與其他受控模組相同。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-303">The CLR Profiling API therefore tells your Profiler DLL when WinMD files load and what their ModuleIDs are, in the same way as for other managed modules.</span></span>

<span data-ttu-id="5cfc4-304">您的分析工具 DLL 可以藉由呼叫[ICorProfilerInfo3：： GetModuleInfo2](icorprofilerinfo3-getmoduleinfo2-method.md)方法，並檢查[COR_PRF_MODULE_WINDOWS_RUNTIME](cor-prf-module-flags-enumeration.md)旗標的 `pdwModuleFlags` 輸出參數，來區分 WinMD 檔案與其他模組。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-304">Your Profiler DLL can distinguish WinMD files from other modules by calling the [ICorProfilerInfo3::GetModuleInfo2](icorprofilerinfo3-getmoduleinfo2-method.md) method and inspecting the `pdwModuleFlags` output parameter for the [COR_PRF_MODULE_WINDOWS_RUNTIME](cor-prf-module-flags-enumeration.md) flag.</span></span> <span data-ttu-id="5cfc4-305">（只有在 ModuleID 代表 WinMD 時才會設定）。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-305">(It’s set if and only if the ModuleID represents a WinMD.)</span></span>

### <a name="reading-metadata-from-winmds"></a><span data-ttu-id="5cfc4-306">從 Winmd 讀取中繼資料</span><span class="sxs-lookup"><span data-stu-id="5cfc4-306">Reading metadata from WinMDs</span></span>

<span data-ttu-id="5cfc4-307">WinMD 檔案（例如一般模組）包含可以透過[中繼資料 api](../../../../docs/framework/unmanaged-api/metadata/index.md)讀取的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-307">WinMD files, like regular modules, contain metadata that can be read via the [Metadata APIs](../../../../docs/framework/unmanaged-api/metadata/index.md).</span></span> <span data-ttu-id="5cfc4-308">不過，CLR 會在讀取 WinMD 檔案時，將 Windows 執行階段型別對應到 .NET Framework 型別，以便在 managed 程式碼中設計和取用 WinMD 檔案的開發人員可以擁有更自然的程式設計經驗。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-308">However, the CLR maps Windows Runtime types to .NET Framework types when it reads WinMD files so that developers who program in managed code and consume the WinMD file can have a more natural programming experience.</span></span> <span data-ttu-id="5cfc4-309">如需這些對應的一些範例，請參閱[.NET Framework 支援 Windows Store 應用程式和 Windows 執行階段](../../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-309">For some examples of these mappings, see [.NET Framework Support for Windows Store Apps and Windows Runtime](../../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md).</span></span>

<span data-ttu-id="5cfc4-310">當 profiler 使用中繼資料 Api 時，您的分析工具會取得哪一個視圖：原始 Windows 執行階段視圖或對應的 .NET Framework 視圖？</span><span class="sxs-lookup"><span data-stu-id="5cfc4-310">So which view will your profiler get when it uses the metadata APIs: the raw Windows Runtime view, or the mapped .NET Framework view?</span></span>  <span data-ttu-id="5cfc4-311">答：這是由您自行來。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-311">The answer: it’s up to you.</span></span>

<span data-ttu-id="5cfc4-312">當您在 WinMD 上呼叫[ICorProfilerInfo：： GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md)方法來取得中繼資料介面（例如[IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)）時，您可以選擇在 `dwOpenFlags` 參數中設定[ofNoTransform](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) ，以關閉這個對應。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-312">When you call the [ICorProfilerInfo::GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) method on a WinMD to obtain a metadata interface, such as [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md),  you can choose to set [ofNoTransform](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) in the `dwOpenFlags` parameter to turn off this mapping.</span></span> <span data-ttu-id="5cfc4-313">否則，根據預設，將會啟用對應。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-313">Otherwise, by default, the mapping will be enabled.</span></span> <span data-ttu-id="5cfc4-314">一般來說，分析工具會讓對應保持啟用狀態，讓分析工具 DLL 從 WinMD 中繼資料（例如，類型的名稱）取得的字串看起來會對分析工具使用者感到熟悉且自然。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-314">Typically, a profiler will keep the mapping enabled, so that the strings that the Profiler DLL obtains from the WinMD metadata (for example, names of types) will look familiar and natural to the profiler user.</span></span>

### <a name="modifying-metadata-from-winmds"></a><span data-ttu-id="5cfc4-315">修改 Winmd 的中繼資料</span><span class="sxs-lookup"><span data-stu-id="5cfc4-315">Modifying metadata from WinMDs</span></span>

<span data-ttu-id="5cfc4-316">不支援在 Winmd 中修改中繼資料。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-316">Modifying metadata in WinMDs is not supported.</span></span> <span data-ttu-id="5cfc4-317">如果您針對 WinMD 檔案呼叫[ICorProfilerInfo：： GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md)方法，並在 `dwOpenFlags` 參數中指定[ofWrite](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) ，或要求可寫入的中繼資料介面（例如[IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)）， [GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md)將會失敗。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-317">If you call the [ICorProfilerInfo::GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) method for a WinMD file and specify [ofWrite](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) in the `dwOpenFlags` parameter or ask for a writeable metadata interface such as [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md), [GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) will fail.</span></span> <span data-ttu-id="5cfc4-318">這對於 IL 重寫分析工具而言特別重要，這需要修改中繼資料以支援其檢測（例如，新增 AssemblyRefs 或新方法）。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-318">This is of particular importance to IL-rewriting profilers, which need to modify metadata to support their instrumentation (for example, to add AssemblyRefs or new methods).</span></span> <span data-ttu-id="5cfc4-319">因此，您應該先檢查[COR_PRF_MODULE_WINDOWS_RUNTIME](cor-prf-module-flags-enumeration.md) （如上一節所述），並避免在這類別模組上要求可寫入的中繼資料介面。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-319">So you should check for [COR_PRF_MODULE_WINDOWS_RUNTIME](cor-prf-module-flags-enumeration.md) first (as discussed in the previous section) and refrain from asking for writeable metadata interfaces on such modules.</span></span>

### <a name="resolving-assembly-references-with-winmds"></a><span data-ttu-id="5cfc4-320">使用 Winmd 解析元件參考</span><span class="sxs-lookup"><span data-stu-id="5cfc4-320">Resolving assembly references with WinMDs</span></span>

<span data-ttu-id="5cfc4-321">許多分析工具必須以手動方式解析中繼資料參考，以協助檢測或型別檢查。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-321">Many profilers need to resolve metadata references manually to aid with instrumentation or type inspection.</span></span> <span data-ttu-id="5cfc4-322">這類分析工具必須知道 CLR 如何解析指向 Winmd 的元件參考，因為這些參考是以與標準元件參考完全不同的方式來解析。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-322">Such profilers need to be aware of how the CLR resolves assembly references that point to WinMDs, because those references are resolved in a completely different way than standard assembly references.</span></span>

## <a name="memory-profilers"></a><span data-ttu-id="5cfc4-323">記憶體分析工具</span><span class="sxs-lookup"><span data-stu-id="5cfc4-323">Memory profilers</span></span>

<span data-ttu-id="5cfc4-324">在 Windows Store 應用程式和傳統型應用程式中，垃圾收集行程和受控堆積的本質並不相同。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-324">The garbage collector and managed heap are not fundamentally different in a Windows Store app and a desktop app.</span></span> <span data-ttu-id="5cfc4-325">不過，profiler 作者必須注意一些細微的差異。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-325">However, there are some subtle differences that profiler authors need to be aware of.</span></span>

### <a name="forcegc-creates-a-managed-thread"></a><span data-ttu-id="5cfc4-326">ForceGC 會建立受控執行緒</span><span class="sxs-lookup"><span data-stu-id="5cfc4-326">ForceGC creates a managed thread</span></span>

<span data-ttu-id="5cfc4-327">進行記憶體分析時，您的 Profiler DLL 通常會建立另一個執行緒，以呼叫[ForceGC 方法](icorprofilerinfo-forcegc-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-327">When doing memory profiling, your Profiler DLL typically creates a separate thread from which to call the [ForceGC Method](icorprofilerinfo-forcegc-method.md) method.</span></span> <span data-ttu-id="5cfc4-328">這不是新的內容。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-328">This is nothing new.</span></span> <span data-ttu-id="5cfc4-329">但可能會令人驚訝的是，在 Windows Store 應用程式中執行垃圾收集的動作可能會將您的執行緒轉換成受控執行緒（例如，將會為該執行緒建立分析 API ThreadID）。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-329">But what might be surprising is that the act of doing a garbage collection inside a Windows Store app may transform your thread into a managed thread (for example, a Profiling API ThreadID will be created for that thread).</span></span>

<span data-ttu-id="5cfc4-330">若要瞭解這項功能的結果，請務必瞭解 CLR 分析 API 所定義的同步和非同步呼叫之間的差異。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-330">To understand the consequences of this, it’s important to understand the differences between synchronous and asynchronous calls as defined by the CLR Profiling API.</span></span> <span data-ttu-id="5cfc4-331">請注意，這與 Windows Store 應用程式中非同步呼叫的概念非常不同。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-331">Note that this is very different from the concept of asynchronous calls in Windows Store apps.</span></span> <span data-ttu-id="5cfc4-332">如需詳細資訊，請參閱 blog 文章[為什麼會 CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](https://blogs.msdn.microsoft.com/davbr/2008/12/23/why-we-have-corprof_e_unsupported_call_sequence/) 。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-332">See the blog post [Why we have CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](https://blogs.msdn.microsoft.com/davbr/2008/12/23/why-we-have-corprof_e_unsupported_call_sequence/) for more information.</span></span>

<span data-ttu-id="5cfc4-333">相關的重點是，您的分析工具所建立之執行緒上的呼叫一律會視為同步，即使這些呼叫是從您的其中一個 Profiler DLL 的[ICorProfilerCallback](icorprofilercallback-interface.md)方法以外的地方進行。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-333">The relevant point is that calls made on threads created by your profiler are always considered synchronous, even if those calls are made from outside an implementation of one of your Profiler DLL’s [ICorProfilerCallback](icorprofilercallback-interface.md) methods.</span></span> <span data-ttu-id="5cfc4-334">至少，這是用來做為案例的情況。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-334">At least, that used to be the case.</span></span> <span data-ttu-id="5cfc4-335">既然 CLR 已將分析工具的執行緒轉換成 managed 執行緒，因為您呼叫[ForceGC 方法](icorprofilerinfo-forcegc-method.md)，該執行緒就不再被視為分析工具的執行緒。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-335">Now that the CLR has turned your profiler’s thread into a managed thread because of your call to [ForceGC Method](icorprofilerinfo-forcegc-method.md), that thread is no longer considered your profiler’s thread.</span></span> <span data-ttu-id="5cfc4-336">因此，CLR 會針對該執行緒強制執行更嚴格的定義，亦即呼叫必須源自其中一個分析工具 DLL 的[ICorProfilerCallback](icorprofilercallback-interface.md)方法，才能限定為同步。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-336">As such, the CLR enforces a more stringent definition of what qualifies as synchronous for that thread—namely that a call must originate from inside one of your Profiler DLL’s [ICorProfilerCallback](icorprofilercallback-interface.md) methods to qualify as synchronous.</span></span>

<span data-ttu-id="5cfc4-337">這在實務上的意義為何？</span><span class="sxs-lookup"><span data-stu-id="5cfc4-337">What does this mean in practice?</span></span> <span data-ttu-id="5cfc4-338">大部分的[ICorProfilerInfo](icorprofilerinfo-interface.md)方法都只能以同步方式呼叫，否則會立即失敗。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-338">Most [ICorProfilerInfo](icorprofilerinfo-interface.md) methods are only safe to be called synchronously, and will immediately fail otherwise.</span></span> <span data-ttu-id="5cfc4-339">因此，如果您的分析工具 DLL 重複使用[ForceGC 方法](icorprofilerinfo-forcegc-method.md)執行緒，以進行通常在分析工具建立的執行緒上進行的其他呼叫（例如， [RequestProfilerDetach](icorprofilerinfo3-requestprofilerdetach-method.md)、 [RequestReJIT](icorprofilerinfo4-requestrejit-method.md)或[RequestRevert](icorprofilerinfo4-requestrevert-method.md)），您就會遇到問題.</span><span class="sxs-lookup"><span data-stu-id="5cfc4-339">So if your Profiler DLL reuses your [ForceGC Method](icorprofilerinfo-forcegc-method.md) thread for other calls typically made on profiler-created threads (for example, to [RequestProfilerDetach](icorprofilerinfo3-requestprofilerdetach-method.md), [RequestReJIT](icorprofilerinfo4-requestrejit-method.md), or [RequestRevert](icorprofilerinfo4-requestrevert-method.md)), you’re going to have trouble.</span></span> <span data-ttu-id="5cfc4-340">即使是非同步安全的函式（例如[DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) ），從 managed 執行緒呼叫時也有特殊的規則。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-340">Even an asynchronous-safe function such as [DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) has special rules when called from managed threads.</span></span> <span data-ttu-id="5cfc4-341">（請參閱 @no__t 0Profiler 堆疊演練的 blog 文章：除了 @ no__t-0 以外的基本知識，以取得詳細資訊）。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-341">(See the blog post [Profiler stack walking: Basics and beyond](https://blogs.msdn.microsoft.com/davbr/2005/10/06/profiler-stack-walking-basics-and-beyond/) for more information.)</span></span>

<span data-ttu-id="5cfc4-342">因此，我們建議您 Profiler DLL 所建立的任何執行緒呼叫[ForceGC 方法](icorprofilerinfo-forcegc-method.md)，都應該*僅*用於觸發 GC，然後回應 gc 回呼的目的。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-342">Therefore, we recommend that any thread your Profiler DLL creates to call [ForceGC Method](icorprofilerinfo-forcegc-method.md) should be used *only* for the purpose of triggering GCs and then responding to the GC callbacks.</span></span> <span data-ttu-id="5cfc4-343">它不應該呼叫分析 API 來執行其他工作，例如堆疊取樣或卸離。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-343">It should not call into the Profiling API to perform other tasks like stack sampling or detaching.</span></span>

### <a name="conditionalweaktablereferences"></a><span data-ttu-id="5cfc4-344">ConditionalWeakTableReferences</span><span class="sxs-lookup"><span data-stu-id="5cfc4-344">ConditionalWeakTableReferences</span></span>

<span data-ttu-id="5cfc4-345">從 .NET Framework 4.5 開始，有新的 GC 回呼[ConditionalWeakTableElementReferences](icorprofilercallback5-conditionalweaktableelementreferences-method.md)，可讓分析工具更完整地取得*相依控制碼*的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-345">Starting with the .NET Framework 4.5, there is a new GC callback, [ConditionalWeakTableElementReferences](icorprofilercallback5-conditionalweaktableelementreferences-method.md), which gives the profiler more complete information about *dependent handles*.</span></span> <span data-ttu-id="5cfc4-346">這些控制碼可有效地將來源物件的參考新增至目標物件，以進行 GC 存留期管理。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-346">These handles effectively add a reference from a source object to a target object for the purpose of GC lifetime management.</span></span> <span data-ttu-id="5cfc4-347">相依控制碼並不是新的，而且以 managed 程式碼撰寫程式的開發人員也能夠在 Windows 8 和 .NET Framework 4.5 之前，使用 <xref:System.Runtime.CompilerServices.ConditionalWeakTable%602?displayProperty=nameWithType> 類別來建立自己的相依控制碼。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-347">Dependent handles are nothing new, and developers who program in managed code have been able to create their own dependent handles by using the <xref:System.Runtime.CompilerServices.ConditionalWeakTable%602?displayProperty=nameWithType> class even before Windows 8 and the .NET Framework 4.5.</span></span>

<span data-ttu-id="5cfc4-348">不過，受控 XAML Windows Store 應用程式現在會大量使用相依的控制碼。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-348">However, managed XAML Windows Store apps now make heavy use of dependent handles.</span></span> <span data-ttu-id="5cfc4-349">特別是，CLR 會使用它們來協助管理 managed 物件與非受控 Windows 執行階段物件之間的參考迴圈。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-349">In particular, the CLR uses them to aid with managing reference cycles between managed objects and unmanaged Windows Runtime objects.</span></span> <span data-ttu-id="5cfc4-350">這表示，比以往更重要的是，要知道這些相依控制碼的記憶體分析工具，讓它們可以與堆積圖形中的其餘邊緣進行視覺化。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-350">This means that it’s more important now than ever for memory profilers to be informed of these dependent handles so that they can be visualized along with the rest of the edges in the heap graph.</span></span> <span data-ttu-id="5cfc4-351">您的分析工具 DLL 應該一起使用[RootReferences2](icorprofilercallback2-rootreferences2-method.md)、 [ObjectReferences](icorprofilercallback-objectreferences-method.md)和[ConditionalWeakTableElementReferences](icorprofilercallback5-conditionalweaktableelementreferences-method.md)來形成堆積圖表的完整視圖。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-351">Your Profiler DLL should use [RootReferences2](icorprofilercallback2-rootreferences2-method.md), [ObjectReferences](icorprofilercallback-objectreferences-method.md), and [ConditionalWeakTableElementReferences](icorprofilercallback5-conditionalweaktableelementreferences-method.md) together to form a complete view of the heap graph.</span></span>

## <a name="conclusion"></a><span data-ttu-id="5cfc4-352">結論</span><span class="sxs-lookup"><span data-stu-id="5cfc4-352">Conclusion</span></span>

<span data-ttu-id="5cfc4-353">您可以使用 CLR 分析 API 來分析在 Windows Store 應用程式中執行的受控碼。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-353">It is possible to use the CLR Profiling API to analyze managed code running inside Windows Store apps.</span></span> <span data-ttu-id="5cfc4-354">事實上，您可以採用您正在開發的現有 profiler，並進行一些特定的變更，讓它能夠以 Windows Store 應用程式為目標。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-354">In fact, you can take an existing profiler that you’re developing and make some specific changes so that it can target Windows Store apps.</span></span> <span data-ttu-id="5cfc4-355">您的 Profiler UI 應使用新的 Api，以在偵錯工具模式中啟用 Windows Store 應用程式。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-355">Your Profiler UI should use the new APIs for activating the Windows Store app in debugging mode.</span></span> <span data-ttu-id="5cfc4-356">請確定您的 Profiler DLL 只會使用適用于 Windows Store 應用程式的 Api。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-356">Make sure that your Profiler DLL consumes only those APIs applicable for Windows Store apps.</span></span> <span data-ttu-id="5cfc4-357">分析工具 DLL 和分析工具 UI 之間的通訊機制，應以 Windows Store 應用程式 API 限制來撰寫，並留意適用于 Windows Store 應用程式的限制許可權。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-357">The communication mechanism between your Profiler DLL and Profiler UI should be written with the Windows Store app API restrictions in mind and with awareness of the restricted permissions in place for Windows Store apps.</span></span> <span data-ttu-id="5cfc4-358">您的分析工具 DLL 應該知道 CLR 如何處理 Winmd，以及垃圾收集行程的行為與 managed 執行緒的不同之處。</span><span class="sxs-lookup"><span data-stu-id="5cfc4-358">Your Profiler DLL should be aware of how the CLR treats WinMDs, and how the Garbage Collector’s behavior is different with respect to managed threads.</span></span>

## <a name="resources"></a><span data-ttu-id="5cfc4-359">資源</span><span class="sxs-lookup"><span data-stu-id="5cfc4-359">Resources</span></span>

<span data-ttu-id="5cfc4-360">**Common Language Runtime**</span><span class="sxs-lookup"><span data-stu-id="5cfc4-360">**The Common Language Runtime**</span></span>

- [<span data-ttu-id="5cfc4-361">分析（非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="5cfc4-361">Profiling (Unmanaged API Reference)</span></span>](index.md)

- [<span data-ttu-id="5cfc4-362">中繼資料（非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="5cfc4-362">Metadata (Unmanaged API Reference)</span></span>](../metadata/index.md)

<span data-ttu-id="5cfc4-363">**CLR 與 Windows 執行階段的互動**</span><span class="sxs-lookup"><span data-stu-id="5cfc4-363">**The CLR's interaction with the Windows Runtime**</span></span>

- [<span data-ttu-id="5cfc4-364">Windows 市集應用程式和 Windows 執行階段的 .NET Framework 支援</span><span class="sxs-lookup"><span data-stu-id="5cfc4-364">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](../../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)

<span data-ttu-id="5cfc4-365">**Windows 市集應用程式**</span><span class="sxs-lookup"><span data-stu-id="5cfc4-365">**Windows Store apps**</span></span>

- [<span data-ttu-id="5cfc4-366">檔案存取和許可權（Windows 執行階段應用程式</span><span class="sxs-lookup"><span data-stu-id="5cfc4-366">File access and permissions (Windows Runtime apps</span></span>](https://docs.microsoft.com/previous-versions/windows/apps/hh967755%28v=win.10%29)

- [<span data-ttu-id="5cfc4-367">取得開發人員授權</span><span class="sxs-lookup"><span data-stu-id="5cfc4-367">Get a developer license</span></span>](https://docs.microsoft.com/previous-versions/windows/apps/hh974578%28v=win.10%29)

- [<span data-ttu-id="5cfc4-368">IPackageDebugSettings 介面</span><span class="sxs-lookup"><span data-stu-id="5cfc4-368">IPackageDebugSettings Interface</span></span>](/windows/desktop/api/shobjidl_core/nn-shobjidl_core-ipackagedebugsettings)
