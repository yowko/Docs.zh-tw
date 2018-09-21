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
ms.openlocfilehash: 27e1433415bdc6303555ab9ae04a20e097248535
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/21/2018
ms.locfileid: "46538004"
---
# <a name="clr-profilers-and-windows-store-apps"></a><span data-ttu-id="c2714-102">CLR 分析工具和 Windows 市集應用程式</span><span class="sxs-lookup"><span data-stu-id="c2714-102">CLR Profilers and Windows Store Apps</span></span>

<span data-ttu-id="c2714-103">本主題討論您需要思考寫入分析的診斷工具管理的 Windows 市集應用程式內執行的程式碼時。</span><span class="sxs-lookup"><span data-stu-id="c2714-103">This topic discusses what you need to think about when writing diagnostic tools that analyze managed code running inside a Windows Store app.</span></span> <span data-ttu-id="c2714-104">它也會提供指導方針來修改現有的開發工具，讓它們繼續運作，當您執行 Windows 市集應用程式。</span><span class="sxs-lookup"><span data-stu-id="c2714-104">It also provides guidelines to modify your existing development tools so they continue to work when you run them against Windows Store apps.</span></span> <span data-ttu-id="c2714-105">若要了解這項資訊，最好是如果您已熟悉使用通用語言執行階段設定檔 API，您已經使用此 API 中正確地針對 Windows 桌面應用程式，而且您的執行現在想要在修改工具的診斷工具若要針對 Windows 市集應用程式正確執行。</span><span class="sxs-lookup"><span data-stu-id="c2714-105">To understand this information, it’s best if you're  familiar with the Common Language Runtime Profiling API, you’ve already used this API in a diagnostic tool that runs correctly against Windows desktop applications, and you’re now interested in modifying the tool to run correctly against Windows Store apps.</span></span>

## <a name="introduction"></a><span data-ttu-id="c2714-106">簡介</span><span class="sxs-lookup"><span data-stu-id="c2714-106">Introduction</span></span>

<span data-ttu-id="c2714-107">如果您進行過簡介段落，然後您熟悉 CLR Profiling API。</span><span class="sxs-lookup"><span data-stu-id="c2714-107">If you made it past the introductory paragraph, then you’re familiar with the CLR Profiling API.</span></span> <span data-ttu-id="c2714-108">您已撰寫也針對受管理的桌面應用程式的運作方式的一種診斷工具。</span><span class="sxs-lookup"><span data-stu-id="c2714-108">You’ve already written a diagnostic tool that works well against managed desktop applications.</span></span> <span data-ttu-id="c2714-109">現在您想知道該如何使您的工具可與受管理的 Windows 市集應用程式。</span><span class="sxs-lookup"><span data-stu-id="c2714-109">Now you’re curious what to do so that your tool works with a managed Windows Store app.</span></span> <span data-ttu-id="c2714-110">或許您已經嘗試進行這項工作，並發現不是簡單的工作。</span><span class="sxs-lookup"><span data-stu-id="c2714-110">Perhaps you’ve already tried to make this work, and have discovered that it’s not a straightforward task.</span></span> <span data-ttu-id="c2714-111">事實上，有許多可能不明顯所有的工具開發人員的考量。</span><span class="sxs-lookup"><span data-stu-id="c2714-111">Indeed, there are a number of considerations that might not be obvious to all tools developers.</span></span> <span data-ttu-id="c2714-112">例如: </span><span class="sxs-lookup"><span data-stu-id="c2714-112">For example:</span></span>

- <span data-ttu-id="c2714-113">嚴重降低權限的內容中，執行 Windows 市集應用程式。</span><span class="sxs-lookup"><span data-stu-id="c2714-113">Windows Store apps run in a context with severely reduced permissions.</span></span>

- <span data-ttu-id="c2714-114">Windows 中繼資料檔案具有獨特的特性，相較於傳統的受管理模組。</span><span class="sxs-lookup"><span data-stu-id="c2714-114">Windows Metadata files have unique characteristics when compared to traditional managed modules.</span></span>

- <span data-ttu-id="c2714-115">Windows 市集應用程式已習慣在暫止自行關閉而發生的互動性。</span><span class="sxs-lookup"><span data-stu-id="c2714-115">Windows Store apps have a habit of suspending themselves when interactivity goes down.</span></span>

- <span data-ttu-id="c2714-116">基於各種原因，可能無法再運作您的處理序間通訊機制。</span><span class="sxs-lookup"><span data-stu-id="c2714-116">Your inter-process communication mechanisms may no longer work for various reasons.</span></span>

<span data-ttu-id="c2714-117">本主題列出您要注意的事項，以及如何正確處理它們。</span><span class="sxs-lookup"><span data-stu-id="c2714-117">This topic lists the things you need to be aware of and how to deal with them properly.</span></span>

<span data-ttu-id="c2714-118">如果您熟悉 CLR 設定檔 API，直接跳到本主題結尾處的資源，以尋找更好的入門資訊。</span><span class="sxs-lookup"><span data-stu-id="c2714-118">If you’re new to the CLR Profiling API, skip down to the Resources at the end of this topic to find better introductory information.</span></span>

<span data-ttu-id="c2714-119">提供關於特定 Windows Api 和它們的使用方式的詳細資料也已超出本主題的範圍。</span><span class="sxs-lookup"><span data-stu-id="c2714-119">Providing detail about specific Windows APIs and how they should be used is also outside the scope of this topic.</span></span> <span data-ttu-id="c2714-120">請考慮本主題的起點，並參考 MSDN，若要深入了解此處參考的任何 Windows Api。</span><span class="sxs-lookup"><span data-stu-id="c2714-120">Consider this topic a starting point, and refer to MSDN to learn more about any Windows APIs referenced here.</span></span>

## <a name="architecture-and-terminology"></a><span data-ttu-id="c2714-121">架構和術語</span><span class="sxs-lookup"><span data-stu-id="c2714-121">Architecture and terminology</span></span>

<span data-ttu-id="c2714-122">一般而言，一種診斷工具的架構，在下圖所示。</span><span class="sxs-lookup"><span data-stu-id="c2714-122">Typically, a diagnostic tool has an architecture like the one shown in the following illustration.</span></span> <span data-ttu-id="c2714-123">它會使用詞彙 「 程式碼剖析工具 」，但是許多這類工具遠超過一般的效能或記憶體剖析成區域，例如程式碼涵蓋範圍，模擬物件架構、 時間移動的偵錯、 監視、 等等的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c2714-123">It uses the term "profiler," but many such tools go well beyond typical performance or memory profiling into areas such as code coverage, mock object frameworks, time-travel debugging, application monitoring, and so on.</span></span> <span data-ttu-id="c2714-124">為了簡單起見，本主題將繼續參考程式碼剖析工具為所有這些工具。</span><span class="sxs-lookup"><span data-stu-id="c2714-124">For simplicity, this topic will continue to refer to all these tools as profilers.</span></span>

<span data-ttu-id="c2714-125">在本主題中使用下列術語：</span><span class="sxs-lookup"><span data-stu-id="c2714-125">The following terminology is used throughout this topic:</span></span>

<span data-ttu-id="c2714-126">**應用程式**</span><span class="sxs-lookup"><span data-stu-id="c2714-126">**Application**</span></span>

<span data-ttu-id="c2714-127">這是分析工具分析應用程式。</span><span class="sxs-lookup"><span data-stu-id="c2714-127">This is the application that the profiler is analyzing.</span></span> <span data-ttu-id="c2714-128">一般而言，此應用程式的開發人員正在使用的程式碼剖析工具以協助診斷應用程式的問題。</span><span class="sxs-lookup"><span data-stu-id="c2714-128">Typically, the developer of this application is now using the profiler to help diagnose issues with the application.</span></span> <span data-ttu-id="c2714-129">傳統上，此應用程式是 Windows 桌面應用程式，但在本主題中，我們將探討 Windows 市集應用程式。</span><span class="sxs-lookup"><span data-stu-id="c2714-129">Traditionally, this application would be a Windows desktop application, but in this topic, we’re looking at Windows Store apps.</span></span>

<span data-ttu-id="c2714-130">**Profiler DLL**</span><span class="sxs-lookup"><span data-stu-id="c2714-130">**Profiler DLL**</span></span>

<span data-ttu-id="c2714-131">這是載入應用程式會被分析的處理序空間的元件。</span><span class="sxs-lookup"><span data-stu-id="c2714-131">This is the component that loads into the process space of the application being analyzed.</span></span> <span data-ttu-id="c2714-132">此元件，也就是程式碼剖析工具 「 代理程式 」 會實作[ICorProfilerCallback](icorprofilercallback-interface.md)[ICorProfilerCallback 介面](icorprofilercallback-interface.md)(2，3，等等) 介面，並取用[ICorProfilerInfo](icorprofilerinfo-interface.md)(2，3，等等) 介面來收集有關分析的應用程式，以及可能的資料修改的應用程式的行為層面。</span><span class="sxs-lookup"><span data-stu-id="c2714-132">This component, also known as the profiler "agent," implements the [ICorProfilerCallback](icorprofilercallback-interface.md)[ICorProfilerCallback Interface](icorprofilercallback-interface.md)(2,3,etc.) interfaces and consumes the [ICorProfilerInfo](icorprofilerinfo-interface.md)(2,3,etc.) interfaces to collect data about the analyzed application and potentially modify aspects of the application’s behavior.</span></span>

<span data-ttu-id="c2714-133">**Profiler UI**</span><span class="sxs-lookup"><span data-stu-id="c2714-133">**Profiler UI**</span></span>

<span data-ttu-id="c2714-134">這是程式碼剖析工具的使用者互動的桌面應用程式。</span><span class="sxs-lookup"><span data-stu-id="c2714-134">This is a desktop application that the profiler user interacts with.</span></span> <span data-ttu-id="c2714-135">它負責向使用者顯示應用程式狀態，並提供使用者的方式來控制分析的應用程式的行為。</span><span class="sxs-lookup"><span data-stu-id="c2714-135">It’s responsible for displaying application status to the user and giving the user the means to control the behavior of the analyzed application.</span></span> <span data-ttu-id="c2714-136">此外，此元件一律會在它自己的處理序空間，與正在分析之應用程式的處理序空間分開執行。</span><span class="sxs-lookup"><span data-stu-id="c2714-136">This component always runs in its own process space, separate from the process space of the application being profiled.</span></span> <span data-ttu-id="c2714-137">Profiler UI 也可以做為連結觸發程序 」 處理程序，呼叫[iclrprofiling:: Attachprofiler](iclrprofiling-attachprofiler-method.md)方法，讓分析的應用程式，以載入 Profiler DLL 在這些情況下，分析工具 DLL 不提供支援在啟動時載入。</span><span class="sxs-lookup"><span data-stu-id="c2714-137">The Profiler UI can also act as the "attach trigger," which is the process that calls the [ICLRProfiling::AttachProfiler](iclrprofiling-attachprofiler-method.md) method, to cause the analyzed application to load the Profiler DLL in those cases where the profiler DLL did not load on startup.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c2714-138">Profiler UI 應保持 Windows 桌面應用程式，即使它是用來控制和報告上的 Windows 市集應用程式。</span><span class="sxs-lookup"><span data-stu-id="c2714-138">Your Profiler UI should remain a Windows desktop application, even when it is used to control and report on a Windows Store app.</span></span> <span data-ttu-id="c2714-139">未預期要能夠封裝並寄送您的診斷工具，在 Windows 市集中。</span><span class="sxs-lookup"><span data-stu-id="c2714-139">Don’t expect to be able to package and ship your diagnostics tool in the Windows Store.</span></span> <span data-ttu-id="c2714-140">您的工具必須執行 Windows 市集應用程式無法執行，且許多這些項目之內 Profiler UI 動作。</span><span class="sxs-lookup"><span data-stu-id="c2714-140">Your tool needs to do things that Windows Store apps cannot do, and many of those things reside inside your Profiler UI.</span></span>

<span data-ttu-id="c2714-141">整份文件、 範例程式碼會假設：</span><span class="sxs-lookup"><span data-stu-id="c2714-141">Throughout this document, the sample code assumes that:</span></span>

- <span data-ttu-id="c2714-142">Profiler DLL 是以 c + + 撰寫的因為它必須是原生 DLL，根據 CLR Profiling API 的需求。</span><span class="sxs-lookup"><span data-stu-id="c2714-142">Your Profiler DLL is written in C++, because it must be a native DLL, as per the requirements of the CLR Profiling API.</span></span>

- <span data-ttu-id="c2714-143">Profiler UI 是以 C# 撰寫的。</span><span class="sxs-lookup"><span data-stu-id="c2714-143">Your Profiler UI is written in C#.</span></span> <span data-ttu-id="c2714-144">這並非必要，但因為沒有任何需求 Profiler UI 的程序的語言，為什麼不選擇精簡、 簡單的語言？</span><span class="sxs-lookup"><span data-stu-id="c2714-144">This isn’t necessary, but because there are no requirements on the language for your Profiler UI’s process, why not pick a language that’s concise and simple?</span></span>

### <a name="windows-rt-devices"></a><span data-ttu-id="c2714-145">Windows RT 裝置</span><span class="sxs-lookup"><span data-stu-id="c2714-145">Windows RT devices</span></span>

<span data-ttu-id="c2714-146">Windows RT 裝置相當已鎖定。</span><span class="sxs-lookup"><span data-stu-id="c2714-146">Windows RT devices are quite locked down.</span></span> <span data-ttu-id="c2714-147">協力廠商程式碼剖析工具只是無法載入這類裝置。</span><span class="sxs-lookup"><span data-stu-id="c2714-147">Third-party profilers simply cannot be loaded on such devices.</span></span> <span data-ttu-id="c2714-148">本文件著重在 Windows 8 電腦上。</span><span class="sxs-lookup"><span data-stu-id="c2714-148">This document focuses on Windows 8 PCs.</span></span>

## <a name="consuming-windows-runtime-apis"></a><span data-ttu-id="c2714-149">使用 Windows 執行階段 Api</span><span class="sxs-lookup"><span data-stu-id="c2714-149">Consuming Windows Runtime APIs</span></span>

<span data-ttu-id="c2714-150">在下列各節所述的案例數目，Profiler UI 桌面應用程式需要使用一些新的 Windows 執行階段 Api。</span><span class="sxs-lookup"><span data-stu-id="c2714-150">In a number of scenarios discussed in the following sections, your Profiler UI desktop application needs to consume some new Windows Runtime APIs.</span></span> <span data-ttu-id="c2714-151">您會想要參考的文件以了解哪些 Windows 執行階段 Api 可從桌面應用程式，以及其行為是否不同時稱為從桌面應用程式和 Windows 市集應用程式。</span><span class="sxs-lookup"><span data-stu-id="c2714-151">You’ll want to consult the documentation to understand which Windows Runtime APIs can be used from desktop applications, and whether their behavior is different when called from desktop applications and Windows Store apps.</span></span>

<span data-ttu-id="c2714-152">如果您的 Profiler UI 以 managed 程式碼撰寫，會有幾個步驟，您需要如何讓您使用這些簡單的 Windows 執行階段 Api。</span><span class="sxs-lookup"><span data-stu-id="c2714-152">If your Profiler UI is written in managed code, there will be a few steps you’ll need to do to make consuming those Windows Runtime APIs easy.</span></span> <span data-ttu-id="c2714-153">請參閱[受管理的傳統型應用程式和 Windows 執行階段](https://go.microsoft.com/fwlink/?LinkID=271858)文件，如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="c2714-153">See the [Managed desktop apps and Windows Runtime](https://go.microsoft.com/fwlink/?LinkID=271858) article for more information.</span></span>

## <a name="loading-the-profiler-dll"></a><span data-ttu-id="c2714-154">正在載入 Profiler DLL</span><span class="sxs-lookup"><span data-stu-id="c2714-154">Loading the Profiler DLL</span></span>

<span data-ttu-id="c2714-155">本章節描述如何 Profiler UI 會導致 Windows 市集應用程式載入 Profiler DLL。</span><span class="sxs-lookup"><span data-stu-id="c2714-155">This section describes how your Profiler UI causes the Windows Store app to load your Profiler DLL.</span></span> <span data-ttu-id="c2714-156">本章節所討論的程式碼位於您 Profiler UI 的桌面應用程式，並因此牽涉到使用安全的桌面應用程式，但不一定是安全的 Windows 市集應用程式的 Windows Api。</span><span class="sxs-lookup"><span data-stu-id="c2714-156">The code discussed in this section belongs in your Profiler UI desktop app, and therefore involves using Windows APIs that are safe for desktop apps but not necessarily safe for Windows Store apps.</span></span>

<span data-ttu-id="c2714-157">Profiler UI 可能會造成您 Profiler DLL 載入至應用程式的處理序空間有兩種：</span><span class="sxs-lookup"><span data-stu-id="c2714-157">Your Profiler UI can cause your Profiler DLL to be loaded into the application’s process space in two ways:</span></span>

- <span data-ttu-id="c2714-158">在應用程式啟動時，環境變數來控制。</span><span class="sxs-lookup"><span data-stu-id="c2714-158">At application startup, as controlled by environment variables.</span></span>

- <span data-ttu-id="c2714-159">藉由附加至應用程式，啟動完成之後呼叫[iclrprofiling:: Attachprofiler](iclrprofiling-attachprofiler-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="c2714-159">By attaching to the application after startup is complete by calling the [ICLRProfiling::AttachProfiler](iclrprofiling-attachprofiler-method.md) method.</span></span>

<span data-ttu-id="c2714-160">啟動載入和附加負載的 Profiler DLL 才能正常運作，使用 Windows 市集應用程式，將會出現您的第一個障礙之一。</span><span class="sxs-lookup"><span data-stu-id="c2714-160">One of your first roadblocks will be getting startup-load and attach-load of your Profiler DLL to work properly with Windows Store apps.</span></span> <span data-ttu-id="c2714-161">這兩種形式的載入共用共同的一些特殊考量，我們現在就開始使用它們。</span><span class="sxs-lookup"><span data-stu-id="c2714-161">Both forms of loading share some special considerations in common, so let’s start with them.</span></span>

### <a name="common-considerations-for-startup-and-attach-loads"></a><span data-ttu-id="c2714-162">常見的考量，啟動並附加載入</span><span class="sxs-lookup"><span data-stu-id="c2714-162">Common considerations for startup and attach loads</span></span>

<span data-ttu-id="c2714-163">**簽署您 Profiler DLL**</span><span class="sxs-lookup"><span data-stu-id="c2714-163">**Signing your Profiler DLL**</span></span>

<span data-ttu-id="c2714-164">當 Windows 嘗試載入 Profiler DLL 時，它會確認已正確簽署您 Profiler 的 DLL。</span><span class="sxs-lookup"><span data-stu-id="c2714-164">When Windows attempts to load your Profiler DLL, it verifies that your Profiler DLL is properly signed.</span></span> <span data-ttu-id="c2714-165">如果沒有，則預設的載入會失敗。</span><span class="sxs-lookup"><span data-stu-id="c2714-165">If not, the load fails by default.</span></span> <span data-ttu-id="c2714-166">執行此作業的方法有兩種：</span><span class="sxs-lookup"><span data-stu-id="c2714-166">There are two ways to do this:</span></span>

- <span data-ttu-id="c2714-167">請確定您 Profiler 的 DLL 帶正負號。</span><span class="sxs-lookup"><span data-stu-id="c2714-167">Ensure that your Profiler DLL is signed.</span></span>

- <span data-ttu-id="c2714-168">告訴您的使用者，他們必須使用您的工具之前在其 Windows 8 電腦上安裝開發人員授權。</span><span class="sxs-lookup"><span data-stu-id="c2714-168">Tell your user that they must install a developer license on their Windows 8 machine before using your tool.</span></span> <span data-ttu-id="c2714-169">這可自動從 Visual Studio 或以手動方式從命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="c2714-169">This can be done automatically from Visual Studio or manually from a command prompt.</span></span> <span data-ttu-id="c2714-170">如需詳細資訊，請參閱 <<c0> [ 取得開發人員授權](https://msdn.microsoft.com/library/windows/apps/Hh974578.aspx)。</span><span class="sxs-lookup"><span data-stu-id="c2714-170">For more information, see [Get a developer license](https://msdn.microsoft.com/library/windows/apps/Hh974578.aspx).</span></span>

<span data-ttu-id="c2714-171">**檔案系統權限**</span><span class="sxs-lookup"><span data-stu-id="c2714-171">**File system permissions**</span></span>

<span data-ttu-id="c2714-172">Windows 市集應用程式必須有權限來載入及執行 Profiler DLL 中的檔案系統上的位置從 residesBy 預設的 Windows 市集應用程式沒有這類權限，大部分的目錄，以及任何失敗的嘗試載入 Profiler DLL會產生看起來類似下面的 Windows 應用程式事件記錄檔中的項目：</span><span class="sxs-lookup"><span data-stu-id="c2714-172">The Windows Store app must have permission to load and execute your Profiler DLL from the location on the file system in which it residesBy default, the Windows Store app doesn’t have such permission on most directories, and any failed attempt to load your Profiler DLL will produce an entry in the Windows Application event log that looks something like this:</span></span>

```Output
NET Runtime version 4.0.30319.17929 - Loading profiler failed during CoCreateInstance.  Profiler CLSID: '{xxxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx}'.  HRESULT: 0x80070005.  Process ID (decimal): 4688.  Message ID: [0x2504].
```

<span data-ttu-id="c2714-173">一般而言，Windows 市集應用程式只能存取一組有限的磁碟上的位置。</span><span class="sxs-lookup"><span data-stu-id="c2714-173">Generally, Windows Store apps are only allowed to access a limited set of locations on the disk.</span></span> <span data-ttu-id="c2714-174">每一個 Windows 市集應用程式可以存取自己的應用程式資料資料夾，以及少數的其他區域，為其授與所有 Windows 市集應用程式存取的檔案系統中。</span><span class="sxs-lookup"><span data-stu-id="c2714-174">Each Windows Store app can access its own application data folders, as well as a few other areas in the file system for which all Windows Store apps are granted access.</span></span> <span data-ttu-id="c2714-175">最好的方式是安裝 Profiler DLL 和其相依性，Program Files 或 Program Files (x86) 下的某處，因為所有的 Windows 市集應用程式具有讀取和執行預設的權限。</span><span class="sxs-lookup"><span data-stu-id="c2714-175">It's best to install your Profiler DLL and its dependencies somewhere under Program Files or Program Files (x86), because all Windows Store apps have read and execute permissions there by default.</span></span>

### <a name="startup-load"></a><span data-ttu-id="c2714-176">啟動負載</span><span class="sxs-lookup"><span data-stu-id="c2714-176">Startup load</span></span>

<span data-ttu-id="c2714-177">一般而言，在傳統型應用程式，Profiler UI 會提示啟動負載 Profiler DLL 的初始化環境區塊，其中包含必要的 CLR 程式碼剖析 API 環境變數 (亦即`COR_PROFILER`， `COR_ENABLE_PROFILING`，和`COR_PROFILER_PATH`)，以及然後使用該環境區塊中建立新的處理序。</span><span class="sxs-lookup"><span data-stu-id="c2714-177">Typically, in a desktop app, your Profiler UI prompts a startup load of your Profiler DLL by initializing an environment block that contains the required CLR Profiling API environment variables (i.e., `COR_PROFILER`, `COR_ENABLE_PROFILING`, and `COR_PROFILER_PATH`), and then creating a new process with that environment block.</span></span> <span data-ttu-id="c2714-178">同樣適用於 Windows 市集應用程式，但機制並不相同。</span><span class="sxs-lookup"><span data-stu-id="c2714-178">The same holds true for Windows Store apps, but the mechanisms are different.</span></span>

<span data-ttu-id="c2714-179">**不會執行提高權限**</span><span class="sxs-lookup"><span data-stu-id="c2714-179">**Don’t run elevated**</span></span>

<span data-ttu-id="c2714-180">如果處理序嘗試繁衍 （spawn） Windows 市集應用程式處理序 B 程序的應執行在中度完整性層級，不是在高整合層級 （亦即未提高權限）。</span><span class="sxs-lookup"><span data-stu-id="c2714-180">If Process A attempts to spawn Windows Store app Process B, Process A should be run at medium integrity level, not at high integrity level (that is, not elevated).</span></span> <span data-ttu-id="c2714-181">這表示，應該執行 Profiler UI，在中度完整性層級，或它必須繁衍 （spawn） 負責啟動 Windows 市集應用程式中整合性層級的另一個桌面程序。</span><span class="sxs-lookup"><span data-stu-id="c2714-181">This means that either your Profiler UI should be running at medium integrity level, or it must spawn another desktop process at medium integrity level to take care of launching the Windows Store app.</span></span>

<span data-ttu-id="c2714-182">**選擇 Windows 市集應用程式設定檔**</span><span class="sxs-lookup"><span data-stu-id="c2714-182">**Choosing a Windows Store App to profile**</span></span>

<span data-ttu-id="c2714-183">首先，您會想詢問您程式碼剖析工具的使用者若要啟動哪一個 Windows 市集應用程式。</span><span class="sxs-lookup"><span data-stu-id="c2714-183">First, you’ll want to ask your profiler user which Windows Store app to launch.</span></span> <span data-ttu-id="c2714-184">傳統型應用程式，或許您會顯示檔案瀏覽對話方塊中，，而且使用者會尋找並選取 .exe 檔案。</span><span class="sxs-lookup"><span data-stu-id="c2714-184">For desktop apps, perhaps you’d show a file Browse dialog, and the user would find and select an .exe file.</span></span> <span data-ttu-id="c2714-185">Windows 市集應用程式各不相同，但使用 瀏覽對話方塊沒有任何意義。</span><span class="sxs-lookup"><span data-stu-id="c2714-185">But Windows Store apps are different, and using a Browse dialog doesn’t make sense.</span></span> <span data-ttu-id="c2714-186">相反地，最好是對使用者顯示安裝該使用者即可從選取的 Windows 市集應用程式的清單。</span><span class="sxs-lookup"><span data-stu-id="c2714-186">Instead, it’s better to show the user a list of Windows Store apps installed for that user to select from.</span></span>

<span data-ttu-id="c2714-187">您可以使用[PackageManager 類別](https://msdn.microsoft.com/library/windows/apps/windows.management.deployment.packagemanager.aspx)來產生這份清單。</span><span class="sxs-lookup"><span data-stu-id="c2714-187">You can use the [PackageManager class](https://msdn.microsoft.com/library/windows/apps/windows.management.deployment.packagemanager.aspx) to generate this list.</span></span> <span data-ttu-id="c2714-188">`PackageManager` 是適用於桌面應用程式，Windows 執行階段類別，而且事實上*只*用於桌面應用程式。</span><span class="sxs-lookup"><span data-stu-id="c2714-188">`PackageManager` is a Windows Runtime class that is available to desktop apps, and in fact it is *only* available to desktop apps.</span></span>

<span data-ttu-id="c2714-189">下列程式碼範例從撰寫為傳統型應用程式在 C# yses 假設 Profiler UI`PackageManager`來產生 Windows 應用程式清單：</span><span class="sxs-lookup"><span data-stu-id="c2714-189">The following code example from a hypothetical Profiler UI written as a desktop app in C# yses the `PackageManager` to generate a list of Windows apps:</span></span>

```csharp
string currentUserSID = WindowsIdentity.GetCurrent().User.ToString();
IAppxFactory appxFactory = (IAppxFactory) new AppxFactory();
PackageManager packageManager = new PackageManager();
IEnumerable<Package> packages = packageManager.FindPackagesForUser(currentUserSID);
```

<span data-ttu-id="c2714-190">**指定自訂的環境區塊**</span><span class="sxs-lookup"><span data-stu-id="c2714-190">**Specifying the custom environment block**</span></span>

<span data-ttu-id="c2714-191">新的 COM 介面， [IPackageDebugSettings](https://msdn.microsoft.com/library/hh438393\(v=vs.85\).aspx)，可讓您自訂的 Windows 市集應用程式，以便於某些形式的診斷的執行行為。</span><span class="sxs-lookup"><span data-stu-id="c2714-191">A new COM interface, [IPackageDebugSettings](https://msdn.microsoft.com/library/hh438393\(v=vs.85\).aspx), allows you to customize the execution behavior of a Windows Store app to make some forms of diagnostics easier.</span></span> <span data-ttu-id="c2714-192">其中一個方法中， [EnableDebugging](https://msdn.microsoft.com/library/hh438395\(v=vs.85\).aspx)，可讓您傳遞給 Windows 市集應用程式的環境區塊，當它啟動時，以及其他有用的效果，例如停用自動程序暫止。</span><span class="sxs-lookup"><span data-stu-id="c2714-192">One of its methods, [EnableDebugging](https://msdn.microsoft.com/library/hh438395\(v=vs.85\).aspx), lets you pass an environment block to the Windows Store app when it’s launched, along with other useful effects like disabling automatic process suspension.</span></span> <span data-ttu-id="c2714-193">環境區塊是很重要，因為這是您要指定環境變數 (`COR_PROFILER`， `COR_ENABLE_PROFILING`，和`COR_PROFILER_PATH)`) 載入 Profiler DLL 使用 CLR。</span><span class="sxs-lookup"><span data-stu-id="c2714-193">The environment block is important because that’s where you need to specify the environment variables (`COR_PROFILER`, `COR_ENABLE_PROFILING`, and `COR_PROFILER_PATH)`) used by the CLR to load your Profiler DLL .</span></span>

<span data-ttu-id="c2714-194">請考慮下列程式碼片段：</span><span class="sxs-lookup"><span data-stu-id="c2714-194">Consider the following code snippet:</span></span>

```csharp
IPackageDebugSettings pkgDebugSettings = new PackageDebugSettings();
pkgDebugSettings.EnableDebugging(packgeFullName, debuggerCommandLine, 
                                                                 (IntPtr)fixedEnvironmentPzz);
```

<span data-ttu-id="c2714-195">有一些您必須取得適當的項目：</span><span class="sxs-lookup"><span data-stu-id="c2714-195">There are a couple of items you'll need to get right:</span></span>

- <span data-ttu-id="c2714-196">`packageFullName` 可以逐一查看封裝，並同時決定`package.Id.FullName`。</span><span class="sxs-lookup"><span data-stu-id="c2714-196">`packageFullName` can be determined while iterating over the packages and grabbing `package.Id.FullName`.</span></span>

- <span data-ttu-id="c2714-197">`debuggerCommandLine` 更有趣的是。</span><span class="sxs-lookup"><span data-stu-id="c2714-197">`debuggerCommandLine` is a bit more interesting.</span></span> <span data-ttu-id="c2714-198">若要為 Windows 市集應用程式中傳遞自訂的環境區塊，您要撰寫您自己的圖片，最簡單的 dummy 偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="c2714-198">In order to pass the custom environment block to the Windows Store app, you need to write your own, simplistic dummy debugger.</span></span> <span data-ttu-id="c2714-199">Windows 會產生暫止的 Windows 市集應用程式，並再啟動您的偵錯工具，包含類似的命令列，在此範例中，以將附加偵錯工具：</span><span class="sxs-lookup"><span data-stu-id="c2714-199">Windows spawns the Windows Store app suspended and then attaches your debugger by launching your debugger with a command line like in this example:</span></span>

    ```Output
    MyDummyDebugger.exe -p 1336 -tid 1424
    ```

     <span data-ttu-id="c2714-200">何處`-p 1336`表示的 Windows 市集應用程式處理序識別碼 1336，和`-tid 1424`表示執行緒 ID 1424 是暫止的執行緒。</span><span class="sxs-lookup"><span data-stu-id="c2714-200">where `-p 1336` means the Windows Store app has Process ID 1336, and `-tid 1424` means Thread ID 1424 is the thread that is suspended.</span></span> <span data-ttu-id="c2714-201">虛擬偵錯工具會剖析從命令列 ThreadID，繼續執行該執行緒，，然後結束。</span><span class="sxs-lookup"><span data-stu-id="c2714-201">Your dummy debugger would parse the ThreadID from the command-line, resume that thread, and then exit.</span></span>

     <span data-ttu-id="c2714-202">以下是一些範例來執行這項操作的 c + + 程式碼 （請務必加入錯誤檢查） ！:</span><span class="sxs-lookup"><span data-stu-id="c2714-202">Here’s some example C++ code to do this (be sure to add error checking!):</span></span>

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

     <span data-ttu-id="c2714-203">您要部署此虛擬偵錯工具為您的診斷工具安裝的一部分，然後指定 在這個偵錯工具的路徑`debuggerCommandLine`參數。</span><span class="sxs-lookup"><span data-stu-id="c2714-203">You’ll need to deploy this dummy debugger as part of your diagnostics tool installation, and then specify the path to this debugger in the `debuggerCommandLine` parameter.</span></span>

<span data-ttu-id="c2714-204">**啟動 Windows 市集應用程式**</span><span class="sxs-lookup"><span data-stu-id="c2714-204">**Launching the Windows Store app**</span></span>

<span data-ttu-id="c2714-205">若要啟動的 Windows 市集應用程式目前最後到達。</span><span class="sxs-lookup"><span data-stu-id="c2714-205">The moment to launch the Windows Store app has finally arrived.</span></span> <span data-ttu-id="c2714-206">如果您已經已經嘗試自行執行，您可能已經注意[CreateProcess](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createprocessa)是不在您建立 Windows 市集應用程式處理序方法。</span><span class="sxs-lookup"><span data-stu-id="c2714-206">If you’ve already already tried doing this yourself, you may have noticed that [CreateProcess](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createprocessa) is not how you create a Windows Store app process.</span></span> <span data-ttu-id="c2714-207">相反地，您必須使用[IApplicationActivationManager::ActivateApplication](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-iapplicationactivationmanager-activateapplication)方法。</span><span class="sxs-lookup"><span data-stu-id="c2714-207">Instead, you’ll need to use the [IApplicationActivationManager::ActivateApplication](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-iapplicationactivationmanager-activateapplication) method.</span></span> <span data-ttu-id="c2714-208">若要這樣做，您必須取得您要啟動的 Windows 市集應用程式的應用程式使用者模型識別碼。</span><span class="sxs-lookup"><span data-stu-id="c2714-208">To do that, you’ll need to get the App User Model ID of the Windows Store app that you’re launching.</span></span> <span data-ttu-id="c2714-209">這表示您必須執行一些探查的資訊清單。</span><span class="sxs-lookup"><span data-stu-id="c2714-209">And that means you’ll need to do a little digging through the manifest.</span></span>

<span data-ttu-id="c2714-210">逐一查看您的套件時 (請參閱中的 「 選擇 Windows 市集應用程式來設定檔 」[啟動負載](#startup-load)稍早一節)，您會想要擷取目前的封裝資訊清單中包含的應用程式集：</span><span class="sxs-lookup"><span data-stu-id="c2714-210">While iterating over your packages (see "Choosing a Windows Store App to Profile" in the [Startup load](#startup-load) section earlier), you’ll want to grab the set of applications contained in the current package’s manifest:</span></span>

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

<span data-ttu-id="c2714-211">是，一個封裝可以有多個應用程式，以及每個應用程式有自己的應用程式使用者模型識別碼。</span><span class="sxs-lookup"><span data-stu-id="c2714-211">Yes, one package can have multiple applications, and each application has its own Application User Model ID.</span></span> <span data-ttu-id="c2714-212">因此，您會想要詢問您的使用者設定檔，哪一個應用程式，並抓取應用程式使用者模型識別碼，從該特定應用程式：</span><span class="sxs-lookup"><span data-stu-id="c2714-212">So you’ll want to ask your user which application to profile, and grab the Application User Model ID from that particular application:</span></span>

```csharp
while (appsEnum.GetHasCurrent() != 0)
{
    IAppxManifestApplication app = appsEnum.GetCurrent();
    string appUserModelId = app.GetAppUserModelId();
    //...
}
```

<span data-ttu-id="c2714-213">最後，您現在有您要啟動的 Windows 市集應用程式：</span><span class="sxs-lookup"><span data-stu-id="c2714-213">Finally, you now have what you need to launch the Windows Store app:</span></span>

```csharp
IApplicationActivationManager appActivationMgr = new ApplicationActivationManager();
appActivationMgr.ActivateApplication(appUserModelId, appArgs, ACTIVATEOPTIONS.AO_NONE, out pid);
```

<span data-ttu-id="c2714-214">**務必要記得呼叫 DisableDebugging**</span><span class="sxs-lookup"><span data-stu-id="c2714-214">**Remember to call DisableDebugging**</span></span>

<span data-ttu-id="c2714-215">當您呼叫[IPackageDebugSettings::EnableDebugging](https://msdn.microsoft.com/library/hh438395\(v=VS.85\).aspx)，您所做的承諾，您會自行善後藉由呼叫[IPackageDebugSettings::DisableDebugging](https://msdn.microsoft.com/library/hh438394\(v=vs.85\).aspx)方法，因此請務必執行可透過程式碼剖析工作階段時。</span><span class="sxs-lookup"><span data-stu-id="c2714-215">When you called [IPackageDebugSettings::EnableDebugging](https://msdn.microsoft.com/library/hh438395\(v=VS.85\).aspx), you made a promise that you would clean up after yourself by calling the [IPackageDebugSettings::DisableDebugging](https://msdn.microsoft.com/library/hh438394\(v=vs.85\).aspx) method, so be sure to do that when the profiling session is over.</span></span>

### <a name="attach-load"></a><span data-ttu-id="c2714-216">將連接負載</span><span class="sxs-lookup"><span data-stu-id="c2714-216">Attach load</span></span>

<span data-ttu-id="c2714-217">當 Profiler UI 會想要將其 Profiler DLL 附加至已經開始執行的應用程式時，它會使用[iclrprofiling:: Attachprofiler](iclrprofiling-attachprofiler-method.md)。</span><span class="sxs-lookup"><span data-stu-id="c2714-217">When your Profiler UI wants to attach its Profiler DLL to an application that has already started running, it uses [ICLRProfiling::AttachProfiler](iclrprofiling-attachprofiler-method.md).</span></span> <span data-ttu-id="c2714-218">這同樣適用 Windows 市集應用程式。</span><span class="sxs-lookup"><span data-stu-id="c2714-218">The same holds true with Windows Store apps.</span></span> <span data-ttu-id="c2714-219">但除了稍早所列的一般考量，請確定目標 Windows 市集應用程式不會遭擱置。</span><span class="sxs-lookup"><span data-stu-id="c2714-219">But in addition to the common considerations listed earlier, make sure the that the target Windows Store app is not suspended.</span></span>

<span data-ttu-id="c2714-220">**EnableDebugging**</span><span class="sxs-lookup"><span data-stu-id="c2714-220">**EnableDebugging**</span></span>

<span data-ttu-id="c2714-221">如同啟動載入、 呼叫[IPackageDebugSettings::EnableDebugging](https://msdn.microsoft.com/library/hh438395\(v=VS.85\).aspx)方法。</span><span class="sxs-lookup"><span data-stu-id="c2714-221">As with startup load, call the [IPackageDebugSettings::EnableDebugging](https://msdn.microsoft.com/library/hh438395\(v=VS.85\).aspx) method.</span></span> <span data-ttu-id="c2714-222">您不需要它來傳遞環境區塊，但您需要其中一個其他功能： 停用自動程序暫止。</span><span class="sxs-lookup"><span data-stu-id="c2714-222">You don’t need it for passing an environment block, but you need one of its other features: disabling automatic process suspension.</span></span> <span data-ttu-id="c2714-223">否則，當您 Profiler UI 會呼叫[AttachProfiler](iclrprofiling-attachprofiler-method.md)，目標 Windows 市集應用程式可能會暫止。</span><span class="sxs-lookup"><span data-stu-id="c2714-223">Otherwise, when your Profiler UI calls [AttachProfiler](iclrprofiling-attachprofiler-method.md), the target Windows Store app may be suspended.</span></span> <span data-ttu-id="c2714-224">事實上，這可能是如果使用者現在互動 Profiler UI，並為 Windows 市集應用程式不會啟動任何使用者的畫面。</span><span class="sxs-lookup"><span data-stu-id="c2714-224">In fact, this is likely if the user is now interacting with your Profiler UI, and the Windows Store app is not active on any of the user’s screens.</span></span> <span data-ttu-id="c2714-225">如果 Windows 市集應用程式暫停的情況下，它將無法回應任何表示 CLR 傳送給它來附加您 Profiler 的 DLL。</span><span class="sxs-lookup"><span data-stu-id="c2714-225">And if the Windows Store app is suspended, it won’t be able to respond to any signal that the CLR sends to it to attach your Profiler DLL.</span></span>

<span data-ttu-id="c2714-226">因此，您會想要這麼做：</span><span class="sxs-lookup"><span data-stu-id="c2714-226">So you’ll want to do something like this:</span></span>

```csharp
IPackageDebugSettings pkgDebugSettings = new PackageDebugSettings();
pkgDebugSettings.EnableDebugging(packgeFullName, null /* debuggerCommandLine */, 
                                                                 IntPtr.Zero /* environment */);
```

<span data-ttu-id="c2714-227">這是除了您未指定偵錯工具命令列或環境區塊，則會進行啟動載入案例中，相同的呼叫。</span><span class="sxs-lookup"><span data-stu-id="c2714-227">This is the same call you’d make for the startup load case, except you don’t specify a debugger command line or an environment block.</span></span>

<span data-ttu-id="c2714-228">**DisableDebugging**</span><span class="sxs-lookup"><span data-stu-id="c2714-228">**DisableDebugging**</span></span>

<span data-ttu-id="c2714-229">一如往常，別忘了呼叫[IPackageDebugSettings::DisableDebugging](https://msdn.microsoft.com/library/hh438394\(v=vs.85\).aspx)完成您的程式碼剖析工作階段。</span><span class="sxs-lookup"><span data-stu-id="c2714-229">As always, don’t forget to call [IPackageDebugSettings::DisableDebugging](https://msdn.microsoft.com/library/hh438394\(v=vs.85\).aspx) when your profiling session is completed.</span></span>

## <a name="running-inside-the-windows-store-app"></a><span data-ttu-id="c2714-230">在 Windows 市集應用程式中執行</span><span class="sxs-lookup"><span data-stu-id="c2714-230">Running inside the Windows Store app</span></span>

<span data-ttu-id="c2714-231">因此 Windows 市集應用程式最後已載入您 Profiler 的 DLL。</span><span class="sxs-lookup"><span data-stu-id="c2714-231">So the Windows Store app has finally loaded your Profiler DLL.</span></span> <span data-ttu-id="c2714-232">現在您 Profiler 的 DLL 必須接受教導，學習如何播放 Windows 市集應用程式所需的不同規則，包括其中所允許的 Api，以及如何執行與較小權限。</span><span class="sxs-lookup"><span data-stu-id="c2714-232">Now your Profiler DLL must be taught how to play by the different rules required by Windows Store apps, including which APIs are allowable and how to run with reduced permissions.</span></span>

### <a name="stick-to-the-windows-store-app-apis"></a><span data-ttu-id="c2714-233">堅持在 Windows 市集應用程式 api</span><span class="sxs-lookup"><span data-stu-id="c2714-233">Stick to the Windows Store app APIs</span></span>

<span data-ttu-id="c2714-234">當您瀏覽 Windows API，您會發現每一種 API 會記載為適用於傳統型應用程式、 Windows 市集應用程式，或兩者。</span><span class="sxs-lookup"><span data-stu-id="c2714-234">As you browse the Windows API, you’ll notice that every API is documented as being applicable to desktop apps, Windows Store apps, or both.</span></span> <span data-ttu-id="c2714-235">例如，**需求**的文件 區段[InitializeCriticalSectionAndSpinCount](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionandspincount)函式可讓您指出函式適用於傳統型應用程式。</span><span class="sxs-lookup"><span data-stu-id="c2714-235">For example, the **Requirements** section of the documentation for the [InitializeCriticalSectionAndSpinCount](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionandspincount) function indicates that the function applies to desktop apps only.</span></span> <span data-ttu-id="c2714-236">相反地， [InitializeCriticalSectionEx](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionex)函式是適用於傳統型應用程式和 Windows 市集應用程式。</span><span class="sxs-lookup"><span data-stu-id="c2714-236">In contrast, the [InitializeCriticalSectionEx](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionex) function is available for both desktop apps and Windows Store apps.</span></span>

<span data-ttu-id="c2714-237">在開發 Profiler DLL 時，將它視為是 Windows 市集應用程式，而且只會使用記載為可供 Windows 市集應用程式的 Api。</span><span class="sxs-lookup"><span data-stu-id="c2714-237">When developing your Profiler DLL, treat it as if it’s a Windows Store app and only use APIs that are documented as available to Windows Store apps.</span></span> <span data-ttu-id="c2714-238">分析相依性 (比方說，您可以執行`link /dump /imports`針對您要稽核的 Profiler DLL)，然後搜尋 若要查看哪些相依性為 確定，這不是文件。</span><span class="sxs-lookup"><span data-stu-id="c2714-238">Analyze your dependencies (for example, you can run `link /dump /imports` against your Profiler DLL to audit), and then search the docs to see which of your dependencies are ok and which aren’t.</span></span> <span data-ttu-id="c2714-239">在大部分情況下，您的違規可藉由直接取代為較新表單時，就安全的 api (例如，取代[InitializeCriticalSectionAndSpinCount](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionandspincount)使用[InitializeCriticalSectionEx](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionex))。</span><span class="sxs-lookup"><span data-stu-id="c2714-239">In most cases, your violations can be fixed by simply replacing them with a newer form of the API that is documented as safe (for example, replacing [InitializeCriticalSectionAndSpinCount](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionandspincount) with [InitializeCriticalSectionEx](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionex)).</span></span>

<span data-ttu-id="c2714-240">您可能會發現您 Profiler 的 DLL 會呼叫適用於桌面應用程式，某些 Api，而且尚未似乎運作甚至 Profiler DLL 載入時的 Windows 市集應用程式內。</span><span class="sxs-lookup"><span data-stu-id="c2714-240">You might notice that your Profiler DLL calls some APIs that apply to desktop apps only, and yet they seem to work even when your Profiler DLL is loaded inside a Windows Store app.</span></span> <span data-ttu-id="c2714-241">請注意，它是非常危險的使用與載入 Windows 市集應用程式的程序時在 Profiler DLL 中的 Windows 市集應用程式搭配使用未記載的任何 API:</span><span class="sxs-lookup"><span data-stu-id="c2714-241">Be aware that it’s risky to use any API not documented for use with Windows Store apps in your Profiler DLL when loaded into a Windows Store app process:</span></span>

- <span data-ttu-id="c2714-242">這類 Api 不保證能夠在執行 Windows 市集應用程式的唯一內容中呼叫時。</span><span class="sxs-lookup"><span data-stu-id="c2714-242">Such APIs are not guaranteed to work when called in the unique context that Windows Store apps run in.</span></span>

- <span data-ttu-id="c2714-243">從不同的 Windows 市集應用程式處理序內呼叫，這類 Api 可能不一致的方式運作。</span><span class="sxs-lookup"><span data-stu-id="c2714-243">Such APIs might not work consistently when called from within different Windows Store app processes.</span></span>

- <span data-ttu-id="c2714-244">這類 Api 可能會看似正常運作，從 Windows 市集應用程式的目前版本的 Windows，但可能會中斷或停用 Windows 的未來版本中。</span><span class="sxs-lookup"><span data-stu-id="c2714-244">Such APIs might seem to work fine from Windows Store apps in the current version of Windows, but may break or be disabled in future releases of Windows.</span></span>

<span data-ttu-id="c2714-245">若要修正您所有的違規，並避免風險，是的最佳建議。</span><span class="sxs-lookup"><span data-stu-id="c2714-245">The best advice is to fix all your violations and avoid the risk.</span></span>

<span data-ttu-id="c2714-246">您可能會發現您絕對的工作需要特定的 API 並無法找到適用於 Windows 市集應用程式的替代項目。</span><span class="sxs-lookup"><span data-stu-id="c2714-246">You might find that you absolutely cannot do without a particular API and cannot find a replacement suitable for Windows Store apps.</span></span> <span data-ttu-id="c2714-247">在此情況下，最小值：</span><span class="sxs-lookup"><span data-stu-id="c2714-247">In such a case, at a minimum:</span></span>

- <span data-ttu-id="c2714-248">測試、 測試、 測試即時 daylights 超出該 API 的使用方式。</span><span class="sxs-lookup"><span data-stu-id="c2714-248">Test, test, test the living daylights out of your usage of that API.</span></span>

- <span data-ttu-id="c2714-249">了解此 API 可能會突然中斷或消失如果呼叫從 Windows 市集內的應用程式在未來的版本的 Windows。</span><span class="sxs-lookup"><span data-stu-id="c2714-249">Understand that the API might suddenly break or disappear if called from inside Windows Store apps in future releases of Windows.</span></span> <span data-ttu-id="c2714-250">這不會由 Microsoft 視為相容性問題，支援您的使用量，它將不會優先使用。</span><span class="sxs-lookup"><span data-stu-id="c2714-250">This won’t be considered a compatibility concern by Microsoft, and supporting your usage of it will not be a priority.</span></span>

### <a name="reduced-permissions"></a><span data-ttu-id="c2714-251">降低權限</span><span class="sxs-lookup"><span data-stu-id="c2714-251">Reduced permissions</span></span>

<span data-ttu-id="c2714-252">它已超出本主題列出 Windows 市集應用程式權限不同於傳統型應用程式的所有方法的範圍。</span><span class="sxs-lookup"><span data-stu-id="c2714-252">It’s outside the scope of this topic to list all the ways that Windows Store app permissions differ from desktop apps.</span></span> <span data-ttu-id="c2714-253">但，當然每次您 Profiler 的 DLL （載入 Windows 市集應用程式相較於傳統型應用程式） 時嘗試存取的任何資源的行為會有所差異。</span><span class="sxs-lookup"><span data-stu-id="c2714-253">But certainly the behavior will be different every time your Profiler DLL (when loaded into a Windows Store app as compared to a desktop app) tries to access any resources.</span></span> <span data-ttu-id="c2714-254">檔案系統是最常見的範例。</span><span class="sxs-lookup"><span data-stu-id="c2714-254">The file system is the most common example.</span></span> <span data-ttu-id="c2714-255">有一些會放在指定的 Windows 市集應用程式是否可存取的磁碟上 (請參閱[檔案存取和權限 (Windows 執行階段應用程式](https://msdn.microsoft.com/library/windows/apps/hh967755.aspx))，而且您 Profiler 的 DLL 會在相同的限制下。</span><span class="sxs-lookup"><span data-stu-id="c2714-255">There are but a few places on disk that a given Windows Store app is allowed to access (see [File access and permissions (Windows Runtime apps](https://msdn.microsoft.com/library/windows/apps/hh967755.aspx)), and your Profiler DLL will be under the same restrictions.</span></span> <span data-ttu-id="c2714-256">徹底測試您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="c2714-256">Test your code thoroughly.</span></span>

### <a name="inter-process-communication"></a><span data-ttu-id="c2714-257">處理序間通訊</span><span class="sxs-lookup"><span data-stu-id="c2714-257">Inter-process communication</span></span>

<span data-ttu-id="c2714-258">在這份文件開頭的圖表所示，Profiler DLL （載入至 Windows 市集應用程式處理序空間中） 可能需要與 Profiler UI （執行個別的桌面應用程式處理序空間中） 透過您自己自訂處理序間通訊通訊 (IPC) 通道。</span><span class="sxs-lookup"><span data-stu-id="c2714-258">As shown in the diagram at the beginning of this paper, your Profiler DLL (loaded into the Windows Store app process space) will likely need to communicate with your Profiler UI (running in a separate desktop app process space) through your own custom inter-process communication (IPC) channel.</span></span> <span data-ttu-id="c2714-259">Profiler UI 會將訊號傳送至 Profiler DLL，以修改其行為，和 Profiler DLL 從已分析的 Windows 市集應用程式傳送資料至 Profiler UI 來後置處理和顯示程式碼剖析工具的使用者。</span><span class="sxs-lookup"><span data-stu-id="c2714-259">The Profiler UI sends signals to the Profiler DLL to modify its behavior, and the Profiler DLL sends data from the analyzed Windows Store app back to the Profiler UI for post-processing and displaying to the profiler user.</span></span>

<span data-ttu-id="c2714-260">大部分的程式碼剖析工具需要使用這種方式，但您 Profiler 的 DLL 載入 Windows 市集應用程式時，您的選擇，IPC 機制有更多限制。</span><span class="sxs-lookup"><span data-stu-id="c2714-260">Most profilers need to work this way, but your choices for IPC mechanisms are more limited when your Profiler DLL is loaded into a Windows Store app.</span></span> <span data-ttu-id="c2714-261">比方說，具名的管道不屬於 Windows 市集應用程式 SDK，因此您無法使用它們。</span><span class="sxs-lookup"><span data-stu-id="c2714-261">For example, named pipes are not part of the Windows Store app SDK, so you cannot use them.</span></span>

<span data-ttu-id="c2714-262">但當然，檔案仍在儘管在更多限制的方式。</span><span class="sxs-lookup"><span data-stu-id="c2714-262">But of course, files are still in, albeit in a more limited fashion.</span></span> <span data-ttu-id="c2714-263">事件也會提供。</span><span class="sxs-lookup"><span data-stu-id="c2714-263">Events are also available.</span></span>

<span data-ttu-id="c2714-264">**透過檔案進行通訊**</span><span class="sxs-lookup"><span data-stu-id="c2714-264">**Communicating via files**</span></span>

<span data-ttu-id="c2714-265">大部分的資料可能會透過檔案傳遞 Profiler DLL 和 Profiler UI 之間。</span><span class="sxs-lookup"><span data-stu-id="c2714-265">Most of your data will likely pass between the Profiler DLL and Profiler UI via files.</span></span> <span data-ttu-id="c2714-266">索引鍵是挑選檔案位置，您 （在 Windows 市集應用程式的內容） 的 Profiler DLL 和 Profiler UI 具有讀取和寫入權限。</span><span class="sxs-lookup"><span data-stu-id="c2714-266">The key is to pick a file location that both your Profiler DLL (in the context of a Windows Store app) and Profiler UI have read and write access to.</span></span> <span data-ttu-id="c2714-267">例如，暫存資料夾的路徑是您 Profiler DLL 和 Profiler UI 可以存取的位置，但沒有其他的 Windows 市集應用程式封裝可以存取 （因此防護您記錄從其他 Windows 市集應用程式套件的任何資訊）。</span><span class="sxs-lookup"><span data-stu-id="c2714-267">For example, the Temporary Folder path is a location that both your Profiler DLL and Profiler UI can access, but no other Windows Store app package can access (thus shielding any information you log from other Windows Store app packages).</span></span>

<span data-ttu-id="c2714-268">您的 Profiler UI 和 Profiler DLL 可以判斷此路徑獨立。</span><span class="sxs-lookup"><span data-stu-id="c2714-268">Both your Profiler UI and Profiler DLL can determine this path independently.</span></span> <span data-ttu-id="c2714-269">Profiler UI，它會逐一為目前的使用者安裝的所有套件時 （請參閱稍早的範例程式碼），取得存取權`PackageId`類別，可以使用此程式碼片段的程式碼衍生來源的暫存資料夾路徑。</span><span class="sxs-lookup"><span data-stu-id="c2714-269">Your Profiler UI, when it iterates through all packages installed for the current user (see the sample code earlier), gets access to the `PackageId` class, from which the Temporary Folder path can be derived with code similar to this snippet.</span></span> <span data-ttu-id="c2714-270">（如往常，錯誤檢查省略以求簡單扼要。）</span><span class="sxs-lookup"><span data-stu-id="c2714-270">(As always, error checking is omitted for brevity.)</span></span>

```csharp
// C# code for the Profiler UI.
ApplicationData appData =
    ApplicationDataManager.CreateForPackageFamily(
        packageId.FamilyName);

tempDir = appData.TemporaryFolder.Path;
```

<span data-ttu-id="c2714-271">同時，Profiler DLL 基本上相同，但它可以更輕鬆地[ApplicationData](https://msdn.microsoft.com/library/windows/apps/windows.storage.applicationdata.aspx)類別[ApplicationData.Current](https://msdn.microsoft.com/library/windows/apps/windows.storage.applicationdata.current.aspx)屬性。</span><span class="sxs-lookup"><span data-stu-id="c2714-271">Meanwhile, your Profiler DLL can do basically the same thing, though it can more easily get to the [ApplicationData](https://msdn.microsoft.com/library/windows/apps/windows.storage.applicationdata.aspx) class by using the [ApplicationData.Current](https://msdn.microsoft.com/library/windows/apps/windows.storage.applicationdata.current.aspx) property.</span></span>

<span data-ttu-id="c2714-272">**透過事件進行通訊**</span><span class="sxs-lookup"><span data-stu-id="c2714-272">**Communicating via events**</span></span>

<span data-ttu-id="c2714-273">如果您想在 Profiler UI 與 Profiler DLL 之間的簡單訊號語意，您可以使用 Windows 市集應用程式，以及桌面應用程式內的事件。</span><span class="sxs-lookup"><span data-stu-id="c2714-273">If you want simple signaling semantics between your Profiler UI and Profiler DLL, you can use events inside Windows Store apps as well as desktop apps.</span></span>

<span data-ttu-id="c2714-274">從您 Profiler 的 DLL，您可以直接呼叫[CreateEventEx](/windows/desktop/api/synchapi/nf-synchapi-createeventexa)函式來建立具名的事件，您想要的任何名稱。</span><span class="sxs-lookup"><span data-stu-id="c2714-274">From your Profiler DLL, you can simply call the [CreateEventEx](/windows/desktop/api/synchapi/nf-synchapi-createeventexa) function to create a named event with any name you like.</span></span> <span data-ttu-id="c2714-275">例如: </span><span class="sxs-lookup"><span data-stu-id="c2714-275">For example:</span></span>

```cpp
// Profiler DLL in Windows Store app (C++).
CreateEventEx(
    NULL,  // Not inherited
    "MyNamedEvent"
    CREATE_EVENT_MANUAL_RESET, /* explicit ResetEvent() required; leave initial state unsignaled */
    EVENT_ALL_ACCESS);
```

<span data-ttu-id="c2714-276">Profiler UI 則需要尋找 Windows 市集應用程式的命名空間下該具名的事件。</span><span class="sxs-lookup"><span data-stu-id="c2714-276">Your Profiler UI then needs to find that named event under the Windows Store app’s namespace.</span></span> <span data-ttu-id="c2714-277">例如，無法呼叫 Profiler UI [CreateEventEx](/windows/desktop/api/synchapi/nf-synchapi-createeventexa)，指定做為事件名稱</span><span class="sxs-lookup"><span data-stu-id="c2714-277">For example, your Profiler UI could call [CreateEventEx](/windows/desktop/api/synchapi/nf-synchapi-createeventexa), specifying the event name as</span></span>

`AppContainerNamedObjects\<acSid>\MyNamedEvent`

<span data-ttu-id="c2714-278">`<acSid>` 為 Windows 市集應用程式的 AppContainer SID。</span><span class="sxs-lookup"><span data-stu-id="c2714-278">`<acSid>` is the Windows Store app’s AppContainer SID.</span></span> <span data-ttu-id="c2714-279">本主題稍早章節說明如何以逐一查看目前的使用者安裝的套件。</span><span class="sxs-lookup"><span data-stu-id="c2714-279">An earlier section of this topic showed how to iterate over the packages installed for the current user.</span></span> <span data-ttu-id="c2714-280">您可以從該範例程式碼中，取得 packageId。</span><span class="sxs-lookup"><span data-stu-id="c2714-280">From that sample code, you can obtain the packageId.</span></span> <span data-ttu-id="c2714-281">從 packageId 中，您可以取得和`<acSid>`與下列類似的程式碼：</span><span class="sxs-lookup"><span data-stu-id="c2714-281">And from the packageId, you can obtain the `<acSid>` with code similar to the following:</span></span>

```csharp
IntPtr acPSID;
DeriveAppContainerSidFromAppContainerName(packageId.FamilyName, out acPSID);

string acSid;
ConvertSidToStringSid(acPSID, out acSid);

string acDir;
GetAppContainerFolderPath(acSid, out acDir);
```

### <a name="no-shutdown-notifications"></a><span data-ttu-id="c2714-282">沒有關機通知</span><span class="sxs-lookup"><span data-stu-id="c2714-282">No shutdown notifications</span></span>

<span data-ttu-id="c2714-283">執行時的 Windows 市集應用程式內，Profiler DLL 不應該仰賴依據其中一個[icorprofilercallback:: Shutdown](icorprofilercallback-shutdown-method.md)甚至[DllMain](/windows/desktop/Dlls/dllmain) (與`DLL_PROCESS_DETACH`) 正在呼叫以通知您 Profiler 的 DLL正在結束的 Windows 市集應用程式。</span><span class="sxs-lookup"><span data-stu-id="c2714-283">When running inside a Windows Store app, your Profiler DLL should not rely on either [ICorProfilerCallback::Shutdown](icorprofilercallback-shutdown-method.md) or even [DllMain](/windows/desktop/Dlls/dllmain) (with `DLL_PROCESS_DETACH`) being called to notify your Profiler DLL that the Windows Store app is exiting.</span></span> <span data-ttu-id="c2714-284">事實上，您應該預期它們將永遠不可叫用。</span><span class="sxs-lookup"><span data-stu-id="c2714-284">In fact, you should expect they will never be called.</span></span> <span data-ttu-id="c2714-285">在過去，許多 Profiler Dll 使用這些通知便利的地方來排清至磁碟、 關閉檔案，將通知傳回到的 Profiler UI 等等的快取。但現在您 Profiler 的 DLL 必須稍有不同的組織。</span><span class="sxs-lookup"><span data-stu-id="c2714-285">Historically, many Profiler DLLs have used those notifications as convenient places to flush caches to disk, close files, send notifications back to the Profiler UI, etc. But now your Profiler DLL needs to be organized a little differently.</span></span>

<span data-ttu-id="c2714-286">Profiler DLL 應該是它會記錄資訊。</span><span class="sxs-lookup"><span data-stu-id="c2714-286">Your Profiler DLL should be logging information as it goes.</span></span> <span data-ttu-id="c2714-287">基於效能考量，您可能想要批次在記憶體中的資訊和排清到磁碟隨著批次的成長的大小超過某個臨界值。</span><span class="sxs-lookup"><span data-stu-id="c2714-287">For performance reasons, you may want to batch information in memory and flush it to disk as the batch grows in size past some threshold.</span></span> <span data-ttu-id="c2714-288">但假設可能會遺失任何尚未排清至磁碟的資訊。</span><span class="sxs-lookup"><span data-stu-id="c2714-288">But assume that any information not yet flushed to disk can be lost.</span></span> <span data-ttu-id="c2714-289">這表示您會想要明智的做法，挑選您的閾值和 Profiler UI 需要強行寫入的 Profiler dll 的資訊不完整處理。</span><span class="sxs-lookup"><span data-stu-id="c2714-289">This means you’ll want to pick your threshold wisely, and that your Profiler UI needs to be hardened to deal with incomplete information written by the Profiler DLL.</span></span>

## <a name="windows-runtime-metadata-files"></a><span data-ttu-id="c2714-290">Windows 執行階段中繼資料檔案</span><span class="sxs-lookup"><span data-stu-id="c2714-290">Windows Runtime metadata files</span></span>

<span data-ttu-id="c2714-291">它超出範圍的詳細說明此文件檔案是在 Windows 執行階段中繼資料 (WinMD)。</span><span class="sxs-lookup"><span data-stu-id="c2714-291">It is outside the scope of this document to go into detail on what Windows Runtime metadata (WinMD) files are.</span></span> <span data-ttu-id="c2714-292">本章節僅限於 WinMD 檔案載入的 Profiler DLL 正在分析 Windows 市集應用程式時，CLR Profiling API 的回應方式。</span><span class="sxs-lookup"><span data-stu-id="c2714-292">This section is limited to how the CLR Profiling API reacts when WinMD files are loaded by the Windows Store app your Profiler DLL is analyzing.</span></span>

### <a name="managed-and-non-managed-winmds"></a><span data-ttu-id="c2714-293">受控和非受控 Winmd</span><span class="sxs-lookup"><span data-stu-id="c2714-293">Managed and non-managed WinMDs</span></span>

<span data-ttu-id="c2714-294">如果開發人員會使用 Visual Studio 來建立新的 Windows 執行階段元件專案，該專案的組建會產生 WinMD 檔案，描述開發人員所撰寫的中繼資料 （型別描述的類別、 介面等）。</span><span class="sxs-lookup"><span data-stu-id="c2714-294">If a developer uses Visual Studio to create a new Windows Runtime Component project, a build of that project produces a WinMD file that describes the metadata (the type descriptions of classes, interfaces, etc.) authored by the developer.</span></span> <span data-ttu-id="c2714-295">如果這個專案是以 C# 或 VB 撰寫的 managed 的語言專案，該相同的 WinMD 檔案也會包含這些類型 （亦即，它包含所有由開發人員的原始程式碼所編譯的 IL） 的實作。</span><span class="sxs-lookup"><span data-stu-id="c2714-295">If this project is a managed language project written in C# or VB, that same WinMD file also contains the implementation of those types (meaning that it contains all the IL compiled from the developer’s source code).</span></span> <span data-ttu-id="c2714-296">這類檔案稱為受管理的 WinMD 檔案。</span><span class="sxs-lookup"><span data-stu-id="c2714-296">Such files are known as managed WinMD files.</span></span> <span data-ttu-id="c2714-297">它們有趣，因為它們包含 Windows 執行階段中繼資料和基礎實作。</span><span class="sxs-lookup"><span data-stu-id="c2714-297">They're interesting in that they contain both Windows Runtime metadata and the underlying implementation.</span></span>

<span data-ttu-id="c2714-298">相反地，如果開發人員的 c + + 建立 Windows 執行階段元件專案，該專案的組建產生 WinMD 檔案，僅包含中繼資料，並實作會編譯成不同的原生 DLL。</span><span class="sxs-lookup"><span data-stu-id="c2714-298">In contrast, if a developer creates a Windows Runtime Component project for C++, a build of that project produces a WinMD file that contains only metadata, and the implementation is compiled into a separate native DLL.</span></span> <span data-ttu-id="c2714-299">同樣地，隨附於 Windows SDK 的 WinMD 檔案會包含只有中繼資料，實作編譯成不同的原生 Dll 隨附為 Windows 的一部分。</span><span class="sxs-lookup"><span data-stu-id="c2714-299">Similarly, the WinMD files that ship in the Windows SDK contain only metadata, with the implementation compiled into separate native DLLs that ship as part of Windows.</span></span>

<span data-ttu-id="c2714-300">以下資訊適用於這兩個受管理的 Winmd，包含中繼資料和實作，以及未受管理的 Winmd，包含只有中繼資料。</span><span class="sxs-lookup"><span data-stu-id="c2714-300">The information below applies to both managed WinMDs, which contain metadata and implementation, and to non-managed WinMDs, which contain only metadata.</span></span>

### <a name="winmd-files-look-like-clr-modules"></a><span data-ttu-id="c2714-301">WinMD 檔案看起來像 CLR 模組</span><span class="sxs-lookup"><span data-stu-id="c2714-301">WinMD files look like CLR modules</span></span>

<span data-ttu-id="c2714-302">就 CLR 而言，所有的 WinMD 檔案都是模組。</span><span class="sxs-lookup"><span data-stu-id="c2714-302">As far as the CLR is concerned, all WinMD files are modules.</span></span> <span data-ttu-id="c2714-303">當 WinMD 檔案載入您 Profiler DLL 和其 Moduleid 為何，相同的方式，與其他受管理的模組，因此會告訴 CLR Profiling API。</span><span class="sxs-lookup"><span data-stu-id="c2714-303">The CLR Profiling API therefore tells your Profiler DLL when WinMD files load and what their ModuleIDs are, in the same way as for other managed modules.</span></span>

<span data-ttu-id="c2714-304">Profiler DLL 可以區分來自其他模組 WinMD 檔案藉由呼叫[ICorProfilerInfo3::GetModuleInfo2](icorprofilerinfo3-getmoduleinfo2-method.md)方法，並檢查`pdwModuleFlags`輸出參數[COR_PRF_MODULE_WINDOWS_執行階段](cor-prf-module-flags-enumeration.md)旗標。</span><span class="sxs-lookup"><span data-stu-id="c2714-304">Your Profiler DLL can distinguish WinMD files from other modules by calling the [ICorProfilerInfo3::GetModuleInfo2](icorprofilerinfo3-getmoduleinfo2-method.md) method and inspecting the `pdwModuleFlags` output parameter for the [COR_PRF_MODULE_WINDOWS_RUNTIME](cor-prf-module-flags-enumeration.md) flag.</span></span> <span data-ttu-id="c2714-305">（它是設定才 ModuleID 代表 WinMD）。</span><span class="sxs-lookup"><span data-stu-id="c2714-305">(It’s set if and only if the ModuleID represents a WinMD.)</span></span>

### <a name="reading-metadata-from-winmds"></a><span data-ttu-id="c2714-306">從 Winmd 讀取中繼資料</span><span class="sxs-lookup"><span data-stu-id="c2714-306">Reading metadata from WinMDs</span></span>

<span data-ttu-id="c2714-307">WinMD 檔案，例如一般模組，包含中繼資料，可以透過讀取[中繼資料 Api](../../../../docs/framework/unmanaged-api/metadata/index.md)。</span><span class="sxs-lookup"><span data-stu-id="c2714-307">WinMD files, like regular modules, contain metadata that can be read via the [Metadata APIs](../../../../docs/framework/unmanaged-api/metadata/index.md).</span></span> <span data-ttu-id="c2714-308">不過，CLR 將 Windows 執行階段型別至.NET Framework 型別時它會讀取 WinMD 檔案，讓開發人員以 managed 程式碼程式，並使用 WinMD 檔案可以有更自然的程式設計體驗。</span><span class="sxs-lookup"><span data-stu-id="c2714-308">However, the CLR maps Windows Runtime types to .NET Framework types when it reads WinMD files so that developers who program in managed code and consume the WinMD file can have a more natural programming experience.</span></span> <span data-ttu-id="c2714-309">如需這些對應的一些範例，請參閱[.NET Framework 支援的 Windows 市集應用程式和 Windows 執行階段](../../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)。</span><span class="sxs-lookup"><span data-stu-id="c2714-309">For some examples of these mappings, see [.NET Framework Support for Windows Store Apps and Windows Runtime](../../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md).</span></span>

<span data-ttu-id="c2714-310">因此何種檢視您的分析工具會使用中繼資料 Api 時： 原始的 Windows 執行階段檢視中或對應的.NET Framework 檢視？</span><span class="sxs-lookup"><span data-stu-id="c2714-310">So which view will your profiler get when it uses the metadata APIs: the raw Windows Runtime view, or the mapped .NET Framework view?</span></span>  <span data-ttu-id="c2714-311">答案： 它是由您。</span><span class="sxs-lookup"><span data-stu-id="c2714-311">The answer: it’s up to you.</span></span>

<span data-ttu-id="c2714-312">當您呼叫[icorprofilerinfo:: Getmodulemetadata](icorprofilerinfo-getmodulemetadata-method.md)方法來取得中繼資料介面，例如 WinMD [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)，您可以選擇設定[ofNoTransform](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md)在`dwOpenFlags`參數來關閉這項對應。</span><span class="sxs-lookup"><span data-stu-id="c2714-312">When you call the [ICorProfilerInfo::GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) method on a WinMD to obtain a metadata interface, such as [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md),  you can choose to set [ofNoTransform](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) in the `dwOpenFlags` parameter to turn off this mapping.</span></span> <span data-ttu-id="c2714-313">否則，根據預設，會啟用對應。</span><span class="sxs-lookup"><span data-stu-id="c2714-313">Otherwise, by default, the mapping will be enabled.</span></span> <span data-ttu-id="c2714-314">通常，分析工具會保留啟用，對應，使 Profiler DLL 取得從 WinMD 中繼資料 （例如，類型的名稱） 的字串會看起來就熟悉且自然的程式碼剖析工具的使用者。</span><span class="sxs-lookup"><span data-stu-id="c2714-314">Typically, a profiler will keep the mapping enabled, so that the strings that the Profiler DLL obtains from the WinMD metadata (for example, names of types) will look familiar and natural to the profiler user.</span></span>

### <a name="modifying-metadata-from-winmds"></a><span data-ttu-id="c2714-315">修改從 Winmd 中繼資料</span><span class="sxs-lookup"><span data-stu-id="c2714-315">Modifying metadata from WinMDs</span></span>

<span data-ttu-id="c2714-316">不支援修改 Winmd 中繼資料。</span><span class="sxs-lookup"><span data-stu-id="c2714-316">Modifying metadata in WinMDs is not supported.</span></span> <span data-ttu-id="c2714-317">如果您呼叫[icorprofilerinfo:: Getmodulemetadata](icorprofilerinfo-getmodulemetadata-method.md)方法對 WinMD 的檔案，並指定[ofWrite](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md)中`dwOpenFlags`參數或例如尋求可寫入的中繼資料介面[IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)， [GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md)將會失敗。</span><span class="sxs-lookup"><span data-stu-id="c2714-317">If you call the [ICorProfilerInfo::GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) method for a WinMD file and specify [ofWrite](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) in the `dwOpenFlags` parameter or ask for a writeable metadata interface such as [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md), [GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) will fail.</span></span> <span data-ttu-id="c2714-318">這是以 IL 重寫的分析，需要修改中繼資料，以支援其檢測 （例如，若要新增 AssemblyRefs 或新的方法） 的特別重要。</span><span class="sxs-lookup"><span data-stu-id="c2714-318">This is of particular importance to IL-rewriting profilers, which need to modify metadata to support their instrumentation (for example, to add AssemblyRefs or new methods).</span></span> <span data-ttu-id="c2714-319">因此您應檢查有無[COR_PRF_MODULE_WINDOWS_RUNTIME](cor-prf-module-flags-enumeration.md)第一次 （如前一節所述） 並避免這類模組在要求可寫入的中繼資料介面。</span><span class="sxs-lookup"><span data-stu-id="c2714-319">So you should check for [COR_PRF_MODULE_WINDOWS_RUNTIME](cor-prf-module-flags-enumeration.md) first (as discussed in the previous section) and refrain from asking for writeable metadata interfaces on such modules.</span></span>

### <a name="resolving-assembly-references-with-winmds"></a><span data-ttu-id="c2714-320">解析組件參考 Winmd</span><span class="sxs-lookup"><span data-stu-id="c2714-320">Resolving assembly references with WinMDs</span></span>

<span data-ttu-id="c2714-321">許多程式碼剖析工具需要解析中繼資料參考，以手動方式來協助與檢測或型別檢查。</span><span class="sxs-lookup"><span data-stu-id="c2714-321">Many profilers need to resolve metadata references manually to aid with instrumentation or type inspection.</span></span> <span data-ttu-id="c2714-322">這類程式碼剖析工具必須要了解 CLR 如何解析指向 Winmd 的組件參考，因為這些參考會解析以完全不同的方式，比標準的組件參考。</span><span class="sxs-lookup"><span data-stu-id="c2714-322">Such profilers need to be aware of how the CLR resolves assembly references that point to WinMDs, because those references are resolved in a completely different way than standard assembly references.</span></span>

## <a name="memory-profilers"></a><span data-ttu-id="c2714-323">記憶體分析工具</span><span class="sxs-lookup"><span data-stu-id="c2714-323">Memory profilers</span></span>

<span data-ttu-id="c2714-324">Managed 的堆積的記憶體回收行程不完全不同的 Windows 市集應用程式和傳統型應用程式中。</span><span class="sxs-lookup"><span data-stu-id="c2714-324">The garbage collector and managed heap are not fundamentally different in a Windows Store app and a desktop app.</span></span> <span data-ttu-id="c2714-325">不過，有程式碼剖析工具作者需要留意的某些細微的差異。</span><span class="sxs-lookup"><span data-stu-id="c2714-325">However, there are some subtle differences that profiler authors need to be aware of.</span></span>

### <a name="forcegc-creates-a-managed-thread"></a><span data-ttu-id="c2714-326">ForceGC 建立 managed 的執行緒</span><span class="sxs-lookup"><span data-stu-id="c2714-326">ForceGC creates a managed thread</span></span>

<span data-ttu-id="c2714-327">在執行記憶體分析時，Profiler DLL 通常會建立個別的執行緒，要呼叫[ForceGC 方法](icorprofilerinfo-forcegc-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="c2714-327">When doing memory profiling, your Profiler DLL typically creates a separate thread from which to call the [ForceGC Method](icorprofilerinfo-forcegc-method.md) method.</span></span> <span data-ttu-id="c2714-328">這是什麼新玩意兒。</span><span class="sxs-lookup"><span data-stu-id="c2714-328">This is nothing new.</span></span> <span data-ttu-id="c2714-329">但可能會令人意外執行廢棄項目集合內的 Windows 市集應用程式的動作，可能會轉換成 managed 執行緒的執行緒 （例如，程式碼剖析 API ThreadID 會建立該執行緒）。</span><span class="sxs-lookup"><span data-stu-id="c2714-329">But what might be surprising is that the act of doing a garbage collection inside a Windows Store app may transform your thread into a managed thread (for example, a Profiling API ThreadID will be created for that thread).</span></span>

<span data-ttu-id="c2714-330">若要瞭解這個結果，就一定要了解同步和非同步呼叫之間的差異，CLR Profiling API 所定義。</span><span class="sxs-lookup"><span data-stu-id="c2714-330">To understand the consequences of this, it’s important to understand the differences between synchronous and asynchronous calls as defined by the CLR Profiling API.</span></span> <span data-ttu-id="c2714-331">請注意，這是非常不同於 Windows 市集應用程式中的非同步呼叫的概念。</span><span class="sxs-lookup"><span data-stu-id="c2714-331">Note that this is very different from the concept of asynchronous calls in Windows Store apps.</span></span> <span data-ttu-id="c2714-332">請參閱部落格文章[為什麼我們 CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](https://blogs.msdn.microsoft.com/davbr/2008/12/23/why-we-have-corprof_e_unsupported_call_sequence/)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="c2714-332">See the blog post [Why we have CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](https://blogs.msdn.microsoft.com/davbr/2008/12/23/why-we-have-corprof_e_unsupported_call_sequence/) for more information.</span></span>

<span data-ttu-id="c2714-333">相關的點是，在您的分析工具所建立的執行緒上所做的呼叫一律是同步的即使這些呼叫會從外部 Profiler DLL 的其中一項的實作進行[ICorProfilerCallback](icorprofilercallback-interface.md)方法。</span><span class="sxs-lookup"><span data-stu-id="c2714-333">The relevant point is that calls made on threads created by your profiler are always considered synchronous, even if those calls are made from outside an implementation of one of your Profiler DLL’s [ICorProfilerCallback](icorprofilercallback-interface.md) methods.</span></span> <span data-ttu-id="c2714-334">至少，用這種情況。</span><span class="sxs-lookup"><span data-stu-id="c2714-334">At least, that used to be the case.</span></span> <span data-ttu-id="c2714-335">現在，CLR 已轉換成 managed 執行緒分析工具的執行緒因為呼叫[ForceGC 方法](icorprofilerinfo-forcegc-method.md)，執行緒不會再視為您的分析工具執行緒。</span><span class="sxs-lookup"><span data-stu-id="c2714-335">Now that the CLR has turned your profiler’s thread into a managed thread because of your call to [ForceGC Method](icorprofilerinfo-forcegc-method.md), that thread is no longer considered your profiler’s thread.</span></span> <span data-ttu-id="c2714-336">因此，CLR 會強制執行更嚴格定義的項目會限定為該執行緒同步 — 也就是呼叫必須來自 Profiler DLL 的其中一項[ICorProfilerCallback](icorprofilercallback-interface.md)限定為同步的方法。</span><span class="sxs-lookup"><span data-stu-id="c2714-336">As such, the CLR enforces a more stringent definition of what qualifies as synchronous for that thread—namely that a call must originate from inside one of your Profiler DLL’s [ICorProfilerCallback](icorprofilercallback-interface.md) methods to qualify as synchronous.</span></span>

<span data-ttu-id="c2714-337">這代表在實務上什麼？</span><span class="sxs-lookup"><span data-stu-id="c2714-337">What does this mean in practice?</span></span> <span data-ttu-id="c2714-338">大部分[ICorProfilerInfo](icorprofilerinfo-interface.md)方法僅提供以同步方式呼叫的安全，否則將會立即失敗。</span><span class="sxs-lookup"><span data-stu-id="c2714-338">Most [ICorProfilerInfo](icorprofilerinfo-interface.md) methods are only safe to be called synchronously, and will immediately fail otherwise.</span></span> <span data-ttu-id="c2714-339">因此，如果您 Profiler 的 DLL 會重複使用您[ForceGC 方法](icorprofilerinfo-forcegc-method.md)通常做程式碼剖析工具所建立執行緒上的其他呼叫的執行緒 (例如，若要[RequestProfilerDetach](icorprofilerinfo3-requestprofilerdetach-method.md)， [RequestReJIT](icorprofilerinfo4-requestrejit-method.md)，或[RequestRevert](icorprofilerinfo4-requestrevert-method.md))，您要有問題。</span><span class="sxs-lookup"><span data-stu-id="c2714-339">So if your Profiler DLL reuses your [ForceGC Method](icorprofilerinfo-forcegc-method.md) thread for other calls typically made on profiler-created threads (for example, to [RequestProfilerDetach](icorprofilerinfo3-requestprofilerdetach-method.md), [RequestReJIT](icorprofilerinfo4-requestrejit-method.md), or [RequestRevert](icorprofilerinfo4-requestrevert-method.md)), you’re going to have trouble.</span></span> <span data-ttu-id="c2714-340">即使這類非同步安全函式[DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md)已從受管理的執行緒呼叫時的特殊規則。</span><span class="sxs-lookup"><span data-stu-id="c2714-340">Even an asynchronous-safe function such as [DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) has special rules when called from managed threads.</span></span> <span data-ttu-id="c2714-341">(請參閱部落格文章[Profiler 堆疊查核行程： 基礎及更新版本](https://blogs.msdn.microsoft.com/davbr/2005/10/06/profiler-stack-walking-basics-and-beyond/)如需詳細資訊。)</span><span class="sxs-lookup"><span data-stu-id="c2714-341">(See the blog post [Profiler stack walking: Basics and beyond](https://blogs.msdn.microsoft.com/davbr/2005/10/06/profiler-stack-walking-basics-and-beyond/) for more information.)</span></span>

<span data-ttu-id="c2714-342">因此，我們建議您 Profiler 的 DLL 會呼叫建立任何執行緒[ForceGC 方法](icorprofilerinfo-forcegc-method.md)應*只*為了觸發 Gc，然後回應 GC 回呼。</span><span class="sxs-lookup"><span data-stu-id="c2714-342">Therefore, we recommend that any thread your Profiler DLL creates to call [ForceGC Method](icorprofilerinfo-forcegc-method.md) should be used *only* for the purpose of triggering GCs and then responding to the GC callbacks.</span></span> <span data-ttu-id="c2714-343">它不應該呼叫程式碼剖析 API 來執行其他工作，例如 stack 取樣或中斷連結。</span><span class="sxs-lookup"><span data-stu-id="c2714-343">It should not call into the Profiling API to perform other tasks like stack sampling or detaching.</span></span>

### <a name="conditionalweaktablereferences"></a><span data-ttu-id="c2714-344">ConditionalWeakTableReferences</span><span class="sxs-lookup"><span data-stu-id="c2714-344">ConditionalWeakTableReferences</span></span>

<span data-ttu-id="c2714-345">從.NET Framework 4.5 開始，沒有新的 GC 回呼[ConditionalWeakTableElementReferences](icorprofilercallback5-conditionalweaktableelementreferences-method.md)，提供程式碼剖析工具更完整資訊*相依控制代碼*。</span><span class="sxs-lookup"><span data-stu-id="c2714-345">Starting with the .NET Framework 4.5, there is a new GC callback, [ConditionalWeakTableElementReferences](icorprofilercallback5-conditionalweaktableelementreferences-method.md), which gives the profiler more complete information about *dependent handles*.</span></span> <span data-ttu-id="c2714-346">這些控制代碼有效地會加入從來源物件的參考到目標物件為了 GC 存留期管理。</span><span class="sxs-lookup"><span data-stu-id="c2714-346">These handles effectively add a reference from a source object to a target object for the purpose of GC lifetime management.</span></span> <span data-ttu-id="c2714-347">相依控制代碼已經不新奇，但開發人員以 managed 程式碼程式還能建立自己的相依控制代碼使用<xref:System.Runtime.CompilerServices.ConditionalWeakTable%602?displayProperty=nameWithType>甚至是在 Windows 8 和.NET Framework 4.5 之前的類別。</span><span class="sxs-lookup"><span data-stu-id="c2714-347">Dependent handles are nothing new, and developers who program in managed code have been able to create their own dependent handles by using the <xref:System.Runtime.CompilerServices.ConditionalWeakTable%602?displayProperty=nameWithType> class even before Windows 8 and the .NET Framework 4.5.</span></span>

<span data-ttu-id="c2714-348">不過，受管理的 XAML Windows 市集應用程式現在會使大量使用相依的控制代碼。</span><span class="sxs-lookup"><span data-stu-id="c2714-348">However, managed XAML Windows Store apps now make heavy use of dependent handles.</span></span> <span data-ttu-id="c2714-349">特別是，CLR 會使用它們來協助管理受管理的物件和未受管理的 Windows 執行階段物件之間的參考循環。</span><span class="sxs-lookup"><span data-stu-id="c2714-349">In particular, the CLR uses them to aid with managing reference cycles between managed objects and unmanaged Windows Runtime objects.</span></span> <span data-ttu-id="c2714-350">這表示它是更重要現在比以往記憶體分析工具，以了解這些相依的控制代碼，讓他們可以視覺化以及剩餘的堆積圖形中的邊緣。</span><span class="sxs-lookup"><span data-stu-id="c2714-350">This means that it’s more important now than ever for memory profilers to be informed of these dependent handles so that they can be visualized along with the rest of the edges in the heap graph.</span></span> <span data-ttu-id="c2714-351">應該使用 Profiler DLL [RootReferences2](icorprofilercallback2-rootreferences2-method.md)， [ObjectReferences](icorprofilercallback-objectreferences-method.md)，並[ConditionalWeakTableElementReferences](icorprofilercallback5-conditionalweaktableelementreferences-method.md)一起以形成完整的堆積圖形檢視.</span><span class="sxs-lookup"><span data-stu-id="c2714-351">Your Profiler DLL should use [RootReferences2](icorprofilercallback2-rootreferences2-method.md), [ObjectReferences](icorprofilercallback-objectreferences-method.md), and [ConditionalWeakTableElementReferences](icorprofilercallback5-conditionalweaktableelementreferences-method.md) together to form a complete view of the heap graph.</span></span>

## <a name="conclusion"></a><span data-ttu-id="c2714-352">結論</span><span class="sxs-lookup"><span data-stu-id="c2714-352">Conclusion</span></span>

<span data-ttu-id="c2714-353">您可使用 CLR Profiling API 來分析 Windows 市集應用程式內執行的 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="c2714-353">It is possible to use the CLR Profiling API to analyze managed code running inside Windows Store apps.</span></span> <span data-ttu-id="c2714-354">事實上，您可以採用現有的剖析您正在開發的工具，並進行一些特定的變更，以便它可以針對 Windows 市集應用程式。</span><span class="sxs-lookup"><span data-stu-id="c2714-354">In fact, you can take an existing profiler that you’re developing and make some specific changes so that it can target Windows Store apps.</span></span> <span data-ttu-id="c2714-355">Profiler UI 應該用來啟用 Windows 市集應用程式偵錯模式中的使用新的 Api。</span><span class="sxs-lookup"><span data-stu-id="c2714-355">Your Profiler UI should use the new APIs for activating the Windows Store app in debugging mode.</span></span> <span data-ttu-id="c2714-356">請確定您 Profiler 的 DLL 會使用僅適用於 Windows 市集應用程式的 Api。</span><span class="sxs-lookup"><span data-stu-id="c2714-356">Make sure that your Profiler DLL consumes only those APIs applicable for Windows Store apps.</span></span> <span data-ttu-id="c2714-357">應該寫入您 Profiler DLL 和 Profiler UI 之間的通訊機制，記住的 Windows 市集應用程式 API 限制與受限的權限，可供 Windows 市集應用程式的認知。</span><span class="sxs-lookup"><span data-stu-id="c2714-357">The communication mechanism between your Profiler DLL and Profiler UI should be written with the Windows Store app API restrictions in mind and with awareness of the restricted permissions in place for Windows Store apps.</span></span> <span data-ttu-id="c2714-358">Profiler DLL 應該留意 CLR 如何處理 Winmd 和記憶體回收行程的行為有何不同方面 managed 執行緒。</span><span class="sxs-lookup"><span data-stu-id="c2714-358">Your Profiler DLL should be aware of how the CLR treats WinMDs, and how the Garbage Collector’s behavior is different with respect to managed threads.</span></span>

## <a name="resources"></a><span data-ttu-id="c2714-359">資源</span><span class="sxs-lookup"><span data-stu-id="c2714-359">Resources</span></span>

<span data-ttu-id="c2714-360">**通用語言執行平台**</span><span class="sxs-lookup"><span data-stu-id="c2714-360">**The Common Language Runtime**</span></span>

- [<span data-ttu-id="c2714-361">分析 （Unmanaged 的 API 參考）</span><span class="sxs-lookup"><span data-stu-id="c2714-361">Profiling (Unmanaged API Reference)</span></span>](index.md)

- [<span data-ttu-id="c2714-362">中繼資料 （Unmanaged API 參考）</span><span class="sxs-lookup"><span data-stu-id="c2714-362">Metadata (Unmanaged API Reference)</span></span>](../metadata/index.md)

<span data-ttu-id="c2714-363">**Windows 執行階段的 CLR 的互動**</span><span class="sxs-lookup"><span data-stu-id="c2714-363">**The CLR's interaction with the Windows Runtime**</span></span>

- [<span data-ttu-id="c2714-364">Windows 市集應用程式和 Windows 執行階段的 .NET Framework 支援</span><span class="sxs-lookup"><span data-stu-id="c2714-364">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](../../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)

<span data-ttu-id="c2714-365">**Windows 市集應用程式**</span><span class="sxs-lookup"><span data-stu-id="c2714-365">**Windows Store apps**</span></span>

- [<span data-ttu-id="c2714-366">檔案存取權和權限 （Windows 執行階段應用程式</span><span class="sxs-lookup"><span data-stu-id="c2714-366">File access and permissions (Windows Runtime apps</span></span>](https://msdn.microsoft.com/library/windows/apps/hh967755.aspx)

- [<span data-ttu-id="c2714-367">取得開發人員授權</span><span class="sxs-lookup"><span data-stu-id="c2714-367">Get a developer license</span></span>](https://msdn.microsoft.com/library/windows/apps/Hh974578.aspx)

- <span data-ttu-id="c2714-368">[IPackageDebugSettings 介面](https://msdn.microsoft.com/library/hh438393\(v=vs.85\).aspx)</span><span class="sxs-lookup"><span data-stu-id="c2714-368">[IPackageDebugSettings Interface](https://msdn.microsoft.com/library/hh438393\(v=vs.85\).aspx)</span></span>
