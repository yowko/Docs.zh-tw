---
title: "如何：取得 .NET Framework 4.5 安裝程式的進度"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
helpviewer_keywords:
- progress information, .NET Framework installer
- .NET Framework, installing
ms.assetid: 0a1a3ba3-7e46-4df2-afd3-f3a8237e1c4f
caps.latest.revision: "30"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c11d1c3469100b8bd0eb530a59bb3a01b152f3f1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-get-progress-from-the-net-framework-45-installer"></a><span data-ttu-id="934f6-102">如何：取得 .NET Framework 4.5 安裝程式的進度</span><span class="sxs-lookup"><span data-stu-id="934f6-102">How to: Get Progress from the .NET Framework 4.5 Installer</span></span>
<span data-ttu-id="934f6-103">[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 是可轉散發套件的執行階段。</span><span class="sxs-lookup"><span data-stu-id="934f6-103">The [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] is a redistributable runtime.</span></span> <span data-ttu-id="934f6-104">如果您為這個 .NET Framework 版本開發應用程式，可以在應用程式安裝程式中包含 (鏈結) [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 安裝程式做為必要條件。</span><span class="sxs-lookup"><span data-stu-id="934f6-104">If you develop apps for this version of the .NET Framework, you can include (chain) [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] setup as a prerequisite part of your app's setup.</span></span> <span data-ttu-id="934f6-105">若要呈現自訂或整合的安裝體驗，您可能要以無訊息模式啟動 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 安裝程式並追蹤其進度，同時顯示應用程式的安裝進度。</span><span class="sxs-lookup"><span data-stu-id="934f6-105">To present a customized or unified setup experience, you may want to silently launch [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] setup and track its progress while showing your app's setup progress.</span></span> <span data-ttu-id="934f6-106">若要啟用無訊息追蹤，[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 安裝程式 (可監控) 會使用記憶體對應 I/O (MMIO) 區段定義通訊協定，以便與您的安裝程式 (監控程式或 Chainer) 進行通訊。</span><span class="sxs-lookup"><span data-stu-id="934f6-106">To enable silent tracking, [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] setup (which can be watched) defines a protocol by using a memory-mapped I/O (MMIO) segment to communicate with your setup (the watcher or chainer).</span></span> <span data-ttu-id="934f6-107">此通訊協定會定義一種方式讓 Chainer 取得進度資訊、取得詳細結果、回應訊息，以及取消 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="934f6-107">This protocol defines a way for a chainer to obtain progress information, get detailed results, respond to messages, and cancel the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] setup.</span></span>  
  
-   <span data-ttu-id="934f6-108">**引動過程**。</span><span class="sxs-lookup"><span data-stu-id="934f6-108">**Invocation** .</span></span>  <span data-ttu-id="934f6-109">若要呼叫 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 安裝程式並從 MMIO 區段獲取進度資訊，您的安裝程式必須執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="934f6-109">To call [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] setup and receive progress information from the MMIO section, your setup program must do the following:</span></span>  
  
    1.  <span data-ttu-id="934f6-110">呼叫 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 可轉散發程式：</span><span class="sxs-lookup"><span data-stu-id="934f6-110">Call the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]redistributable program:</span></span>  
  
        ```  
        dotNetFx45_Full_x86_x64.exe /q /norestart /pipe section-name  
        ```  
  
         <span data-ttu-id="934f6-111">「區段名稱」是您想要用來識別應用程式的任意名稱。</span><span class="sxs-lookup"><span data-stu-id="934f6-111">where *section name* is any name you want to use to identify your app.</span></span> <span data-ttu-id="934f6-112">.NET Framework 安裝程式會以非同步方式讀寫 MMIO 區段，所以您可能會覺得在這段期間使用事件和訊息很方便。</span><span class="sxs-lookup"><span data-stu-id="934f6-112">.NET Framework setup reads and writes to the MMIO section asynchronously, so you might find it convenient to use events and messages during that time.</span></span> <span data-ttu-id="934f6-113">在範例中，.NET Framework 安裝程序是由配置 MMIO 區段 (`TheSectionName`) 及定義事件 (`TheEventName`) 的建構函式所建立：</span><span class="sxs-lookup"><span data-stu-id="934f6-113">In the example, the .NET Framework setup process is created by a constructor that both allocates the MMIO section (`TheSectionName`) and defines an event (`TheEventName`):</span></span>  
  
        ```  
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName")  
        ```  
  
         <span data-ttu-id="934f6-114">請用對您安裝程式而言的唯一名稱來取代這些名稱。</span><span class="sxs-lookup"><span data-stu-id="934f6-114">Please replace those names with names that are unique to your setup program.</span></span>  
  
    2.  <span data-ttu-id="934f6-115">讀取 MMIO 區段。</span><span class="sxs-lookup"><span data-stu-id="934f6-115">Read from the MMIO section.</span></span> <span data-ttu-id="934f6-116">在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 中，下載作業與安裝作業會同時進行：.NET Framework 的某一部分可能會進行安裝，另一個部分則進行下載。</span><span class="sxs-lookup"><span data-stu-id="934f6-116">In the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], the download and installation operations are simultaneous: One part of the .NET Framework might be installing while another part is downloading.</span></span> <span data-ttu-id="934f6-117">因此，傳回 (也就是寫入) 至 MMIO 區段的進度是從 0 遞增到 255 的兩個數字 (`m_downloadSoFar` 和 `m_installSoFar`)。</span><span class="sxs-lookup"><span data-stu-id="934f6-117">As a result, progress is sent back (that is, written) to the MMIO section as two numbers (`m_downloadSoFar` and `m_installSoFar`) that increase from 0 to 255.</span></span> <span data-ttu-id="934f6-118">當 255 寫入而 .NET Framework 結束時，安裝即已完成。</span><span class="sxs-lookup"><span data-stu-id="934f6-118">When 255 is written and the .NET Framework exits, the installation is complete.</span></span>  
  
-   <span data-ttu-id="934f6-119">**結束代碼**</span><span class="sxs-lookup"><span data-stu-id="934f6-119">**Exit codes**.</span></span> <span data-ttu-id="934f6-120">呼叫 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 可轉散發程式命令中的下列結束代碼，會指出安裝成功或失敗：</span><span class="sxs-lookup"><span data-stu-id="934f6-120">The following exit codes from the command to call the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] redistributable program indicate whether setup has succeeded or failed:</span></span>  
  
    -   <span data-ttu-id="934f6-121">0 - 安裝順利完成。</span><span class="sxs-lookup"><span data-stu-id="934f6-121">0 - Setup completed successfully.</span></span>  
  
    -   <span data-ttu-id="934f6-122">3010 – 安裝成功，需要重新啟動系統。</span><span class="sxs-lookup"><span data-stu-id="934f6-122">3010 – Setup completed successfully; a system restart is required.</span></span>  
  
    -   <span data-ttu-id="934f6-123">1602 – 已取消安裝。</span><span class="sxs-lookup"><span data-stu-id="934f6-123">1602 – Setup has been canceled.</span></span>  
  
    -   <span data-ttu-id="934f6-124">所有其他代碼 - 安裝程式發生錯誤，詳細資料請檢查在 %temp%中建立的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="934f6-124">All other codes - Setup encountered errors; examine the log files created in %temp% for details.</span></span>  
  
-   <span data-ttu-id="934f6-125">**取消安裝程式**。</span><span class="sxs-lookup"><span data-stu-id="934f6-125">**Canceling setup**.</span></span> <span data-ttu-id="934f6-126">您可以使用 `Abort` 方法設定 MMIO 區段中的 `m_downloadAbort` 和 `m_ installAbort` 旗標，隨時取消安裝程式。</span><span class="sxs-lookup"><span data-stu-id="934f6-126">You can cancel setup at any time by using the `Abort` method to set the `m_downloadAbort` and `m_ installAbort` flags in the MMIO section.</span></span>  
  
## <a name="chainer-sample"></a><span data-ttu-id="934f6-127">Chainer 範例</span><span class="sxs-lookup"><span data-stu-id="934f6-127">Chainer Sample</span></span>  
 <span data-ttu-id="934f6-128">Chainer 範例以無訊息模式啟動並追蹤 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 安裝程式，同時顯示進度。</span><span class="sxs-lookup"><span data-stu-id="934f6-128">The Chainer sample silently launches and tracks [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] setup while showing progress.</span></span> <span data-ttu-id="934f6-129">此範例類似為 .NET Framework 4 提供的 Chainer 範例。</span><span class="sxs-lookup"><span data-stu-id="934f6-129">This sample is similar to the Chainer sample provided for the .NET Framework 4.</span></span> <span data-ttu-id="934f6-130">但另外，它可以處理關閉 .NET Framework 4 應用程式的訊息方塊，避免系統重新啟動。</span><span class="sxs-lookup"><span data-stu-id="934f6-130">However, in addition, it can avoid system restarts by processing the message box for closing .NET Framework 4 apps.</span></span> <span data-ttu-id="934f6-131">如需此訊息方塊的資訊，請參閱[在 .NET Framework 4.5 安裝期間減少系統重新啟動的次數](../../../docs/framework/deployment/reducing-system-restarts.md)。</span><span class="sxs-lookup"><span data-stu-id="934f6-131">For information about this message box, see [Reducing System Restarts During .NET Framework 4.5 Installations](../../../docs/framework/deployment/reducing-system-restarts.md).</span></span> <span data-ttu-id="934f6-132">您可以使用此範例配合 .NET Framework 4 安裝程式，在該案例中不會傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="934f6-132">You can use this sample with the .NET Framework 4 installer; in that scenario, the message is simply not sent.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="934f6-133">您必須以系統管理員身分執行此範例。</span><span class="sxs-lookup"><span data-stu-id="934f6-133">You must run the example as an administrator.</span></span>  
  
 <span data-ttu-id="934f6-134">您可以從 MSDN 範例庫下載適用於 [.NET Framework 4.5 Chainer 範例](http://go.microsoft.com/fwlink/?LinkId=231345)的完整 Visual Studio 方案。</span><span class="sxs-lookup"><span data-stu-id="934f6-134">You can download the complete Visual Studio solution for the [.NET Framework 4.5 Chainer Sample](http://go.microsoft.com/fwlink/?LinkId=231345) from the MSDN Samples Gallery.</span></span>  
  
 <span data-ttu-id="934f6-135">以下各節會說明此範例中的重要檔案：MMIOChainer.h、ChainingdotNet4.cpp 和 IProgressObserver.h。</span><span class="sxs-lookup"><span data-stu-id="934f6-135">The following sections describe the significant files in this sample: MMIOChainer.h, ChainingdotNet4.cpp, and IProgressObserver.h.</span></span>  
  
#### <a name="mmiochainerh"></a><span data-ttu-id="934f6-136">MMIOChainer.h</span><span class="sxs-lookup"><span data-stu-id="934f6-136">MMIOChainer.h</span></span>  
  
-   <span data-ttu-id="934f6-137">MMIOChainer.h 檔案 (請參閱[完整程式碼](http://go.microsoft.com/fwlink/?LinkId=231369)) 包含資料結構定義和基底類別 (Chainer 類別會從其中衍生)。</span><span class="sxs-lookup"><span data-stu-id="934f6-137">The MMIOChainer.h file (see [complete code](http://go.microsoft.com/fwlink/?LinkId=231369)) contains the data structure definition and the base class from which the chainer class should be derived.</span></span> <span data-ttu-id="934f6-138">[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 會擴充 MMIO 資料結構，處理 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 安裝程式需要的資料。</span><span class="sxs-lookup"><span data-stu-id="934f6-138">The [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] extends the MMIO data structure to handle data that the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] installer needs.</span></span> <span data-ttu-id="934f6-139">MMIO 結構的變更與舊版相容，因此 .NET Framework 4 Chainer 不需要重新編譯，即可使用 .NET Framework 4.5 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="934f6-139">The changes to the MMIO structure are backward-compatible, so a .NET Framework 4 chainer can work with .NET Framework 4.5 setup without requiring recompilation.</span></span> <span data-ttu-id="934f6-140">不過，本案例不支援減少系統重新啟動的功能。</span><span class="sxs-lookup"><span data-stu-id="934f6-140">However, this scenario does not support the feature for reducing system restarts.</span></span>  
  
     <span data-ttu-id="934f6-141">版本欄位會提供識別結構和訊息格式修訂的方法。</span><span class="sxs-lookup"><span data-stu-id="934f6-141">A version field provides a means of identifying revisions to the structure and message format.</span></span>  <span data-ttu-id="934f6-142">.NET Framework 安裝程式會呼叫 `VirtualQuery` 函式來判斷檔案對應的大小，以判斷 Chainer 介面的版本。</span><span class="sxs-lookup"><span data-stu-id="934f6-142">The .NET Framework setup determines the version of the chainer interface by calling the `VirtualQuery` function to determine the size of the file mapping.</span></span>  <span data-ttu-id="934f6-143">如果大小足以容納版本欄位，.NET Framework 安裝程式就會使用指定的值。</span><span class="sxs-lookup"><span data-stu-id="934f6-143">If the size is large enough to accommodate the version field, .NET Framework setup uses the specified value.</span></span> <span data-ttu-id="934f6-144">如果檔案對應太小無法包含版本欄位，也就是 .NET Framework 4 的情況，則安裝程序會假設版本 0 (4)。</span><span class="sxs-lookup"><span data-stu-id="934f6-144">If the file mapping is too small to contain a version field, which is the case with the .NET Framework 4, the setup process assumes version 0 (4).</span></span> <span data-ttu-id="934f6-145">如果 Chainer 不支援 .NET Framework 安裝程式想要傳送的訊息版本，.NET Framework 安裝程式會假設忽略回應。</span><span class="sxs-lookup"><span data-stu-id="934f6-145">If the chainer does not support the version of the message that .NET Framework setup wants to send, .NET Framework setup assumes an ignore response.</span></span>  
  
     <span data-ttu-id="934f6-146">MMIO 資料結構定義如下：</span><span class="sxs-lookup"><span data-stu-id="934f6-146">The MMIO data structure is defined as follows:</span></span>  
  
    ```cpp  
    // MMIO data structure for interprocess communication  
        struct MmioDataStructure  
        {  
            bool m_downloadFinished;               // Is download complete?  
            bool m_installFinished;                // Is installation complete?  
            bool m_downloadAbort;                  // Set to cause downloader to abort.  
            bool m_installAbort;                   // Set to cause installer to abort.  
            HRESULT m_hrDownloadFinished;          // Resulting HRESULT for download.  
            HRESULT m_hrInstallFinished;           // Resulting HRESULT for installation.  
            HRESULT m_hrInternalError;  
            WCHAR m_szCurrentItemStep[MAX_PATH];  
            unsigned char m_downloadSoFar;         // Download progress 0-255 (0-100% done).   
            unsigned char m_installSoFar;          // Installation progress 0-255 (0-100% done).  
            WCHAR m_szEventName[MAX_PATH];         // Event that chainer creates and chainee opens to sync communications.  
  
            BYTE m_version;                        // Version of the data structure, set by chainer:  
                                                   // 0x0: .NET Framework 4   
                                                   // 0x1: .NET Framework 4.5  
  
            DWORD m_messageCode;                   // Current message sent by the chainee; 0 if no message is active.  
            DWORD m_messageResponse;               // Chainer's response to current message; 0 if not yet handled.  
            DWORD m_messageDataLength;             // Length of the m_messageData field, in bytes.  
            BYTE m_messageData[1];                 // Variable-length buffer; content depends on m_messageCode.  
        };  
    ```  
  
-   <span data-ttu-id="934f6-147">`MmioDataStructure` 資料結構不應直接使用，請改用 `MmioChainer` 類別實作您的 Chainer。</span><span class="sxs-lookup"><span data-stu-id="934f6-147">The `MmioDataStructure` data structure should not be used directly; use the `MmioChainer` class instead to implement your chainer.</span></span> <span data-ttu-id="934f6-148">衍生自 `MmioChainer` 類別以鏈結 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 可轉散發套件。</span><span class="sxs-lookup"><span data-stu-id="934f6-148">Derive from the `MmioChainer` class to chain the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] redistributable.</span></span>  
  
#### <a name="iprogressobserverh"></a><span data-ttu-id="934f6-149">IProgressObserver.h</span><span class="sxs-lookup"><span data-stu-id="934f6-149">IProgressObserver.h</span></span>  
  
-   <span data-ttu-id="934f6-150">IProgressObserver.h 檔案會實作進度觀察器 ([請參閱完整程式碼](http://go.microsoft.com/fwlink/?LinkId=231370))。</span><span class="sxs-lookup"><span data-stu-id="934f6-150">The IProgressObserver.h file implements a progress observer ([see complete code](http://go.microsoft.com/fwlink/?LinkId=231370)).</span></span> <span data-ttu-id="934f6-151">這個觀察器會收到下載和安裝進度通知 (指定為不帶正負號的 `char`，即 0-255，指出完成度 1%-100%)。</span><span class="sxs-lookup"><span data-stu-id="934f6-151">This observer gets notified of download and installation progress (specified as an unsigned `char`, 0-255, indicating 1%-100% complete).</span></span> <span data-ttu-id="934f6-152">當 Chainee 傳送訊息時也會通知觀察器，而觀察器應該傳送回應。</span><span class="sxs-lookup"><span data-stu-id="934f6-152">The observer is also notified when the chainee sends a message, and the observer should send a response.</span></span>  
  
    ```cpp  
        class IProgressObserver  
        {  
        public:  
            virtual void OnProgress(unsigned char) = 0; // 0 - 255:  255 == 100%  
            virtual void Finished(HRESULT) = 0;         // Called when operation is complete    
            virtual DWORD Send(DWORD dwMessage, LPVOID pData, DWORD dwDataLength) = 0; // Called when a message is sent  
        };  
    ```  
  
#### <a name="chainingdotnet45cpp"></a><span data-ttu-id="934f6-153">ChainingdotNet4.5.cpp</span><span class="sxs-lookup"><span data-stu-id="934f6-153">ChainingdotNet4.5.cpp</span></span>  
  
-   <span data-ttu-id="934f6-154">衍生自 `MmioChainer` 類別的 [ChainingdotNet4.5.cpp](http://go.microsoft.com/fwlink/?LinkId=231368) 檔案會實作 `Server` 類別，並覆寫適當的方法以顯示進度資訊。</span><span class="sxs-lookup"><span data-stu-id="934f6-154">The [ChainingdotNet4.5.cpp](http://go.microsoft.com/fwlink/?LinkId=231368) file implements the `Server` class, which derives from the `MmioChainer` class and overrides the appropriate methods to display progress information.</span></span> <span data-ttu-id="934f6-155">MmioChainer 會以指定的區段名稱建立區段，並以指定的事件名稱初始化 Chainer。</span><span class="sxs-lookup"><span data-stu-id="934f6-155">The MmioChainer creates a section with the specified section name and initializes the chainer with the specified event name.</span></span> <span data-ttu-id="934f6-156">事件名稱會儲存在對應的資料結構中。</span><span class="sxs-lookup"><span data-stu-id="934f6-156">The event name is saved in the mapped data structure.</span></span> <span data-ttu-id="934f6-157">您應該使用唯一的區段和事件名稱。</span><span class="sxs-lookup"><span data-stu-id="934f6-157">You should make the section and event names unique.</span></span> <span data-ttu-id="934f6-158">下列程式碼中的 `Server` 類別會啟動指定的安裝程式、監視其進度，並傳回結束代碼。</span><span class="sxs-lookup"><span data-stu-id="934f6-158">The `Server` class in the following code launches the specified setup program, monitors its progress, and returns an exit code.</span></span>  
  
    ```cpp  
    class Server : public ChainerSample::MmioChainer, public ChainerSample::IProgressObserver  
    {  
    public:  
        …………….  
        Server():ChainerSample::MmioChainer(L"TheSectionName", L"TheEventName") //customize for your event names  
        {}  
    ```  
  
     <span data-ttu-id="934f6-159">安裝是在 Main 方法中啟動。</span><span class="sxs-lookup"><span data-stu-id="934f6-159">The installation is started in the Main method.</span></span>  
  
    ```cpp  
    // Main entry point for program  
    int __cdecl main(int argc, _In_count_(argc) char **_argv)  
    {  
        int result = 0;  
        CString args;  
        if (argc > 1)  
        {  
            args = CString(_argv[1]);  
        }  
  
        if (IsNetFx4Present(NETFX45_RC_REVISION))  
        {  
            printf(".NET Framework 4.5 is already installed");  
        }  
        else  
        {  
            result = Server().Launch(args);  
        }  
  
        return result;  
    }  
    ```  
  
-   <span data-ttu-id="934f6-160">在啟動安裝之前，Chainer 會藉由呼叫 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 查看是否已安裝 `IsNetFx4Present`。</span><span class="sxs-lookup"><span data-stu-id="934f6-160">Before launching the installation, the chainer checks to see if the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] is already installed by calling `IsNetFx4Present`:</span></span>  
  
    ```cpp  
    ///  Checks for presence of the .NET Framework 4.  
    ///    A value of 0 for dwMinimumRelease indicates a check for the .NET Framework 4 full  
    ///    Any other value indicates a check for a specific compatible release of the .NET Framework 4.  
    #define NETFX40_FULL_REVISION 0  
    // TODO: Replace with released revision number  
    #define NETFX45_RC_REVISION MAKELONG(50309, 5)   // .NET Framework 4.5   
    bool IsNetFx4Present(DWORD dwMinimumRelease)  
    {  
        DWORD dwError = ERROR_SUCCESS;  
        HKEY hKey = NULL;  
        DWORD dwData = 0;  
        DWORD dwType = 0;  
        DWORD dwSize = sizeof(dwData);  
  
        dwError = ::RegOpenKeyExW(HKEY_LOCAL_MACHINE, L"SOFTWARE\\Microsoft\\NET Framework Setup\\NDP\\v4\\Full", 0, KEY_READ, &hKey);  
        if (ERROR_SUCCESS == dwError)  
        {  
            dwError = ::RegQueryValueExW(hKey, L"Release", 0, &dwType, (LPBYTE)&dwData, &dwSize);  
  
            if ((ERROR_SUCCESS == dwError) && (REG_DWORD != dwType))  
            {  
                dwError = ERROR_INVALID_DATA;  
            }  
            else if (ERROR_FILE_NOT_FOUND == dwError)  
            {  
                // Release value was not found, let's check for 4.0.  
                dwError = ::RegQueryValueExW(hKey, L"Install", 0, &dwType, (LPBYTE)&dwData, &dwSize);  
  
                // Install = (REG_DWORD)1;  
                if ((ERROR_SUCCESS == dwError) && (REG_DWORD == dwType) && (dwData == 1))  
                {  
                    // treat 4.0 as Release = 0  
                    dwData = 0;  
                }  
                else  
                {  
                    dwError = ERROR_INVALID_DATA;  
                }  
            }  
        }  
  
        if (hKey != NULL)  
        {  
            ::RegCloseKey(hKey);  
        }  
  
        return ((ERROR_SUCCESS == dwError) && (dwData >= dwMinimumRelease));  
    }  
    ```  
  
-   <span data-ttu-id="934f6-161">您可以在 `Launch` 方法中變更可執行檔路徑 (範例中為 Setup.exe)，指向正確的位置，或自訂程式碼來決定位置。</span><span class="sxs-lookup"><span data-stu-id="934f6-161">You can change the path of the executable (Setup.exe in the example) in the `Launch` method to point to its correct location, or customize the code to determine the location.</span></span> <span data-ttu-id="934f6-162">`MmioChainer` 基底類別提供衍生類別呼叫的封鎖 `Run()` 方法。</span><span class="sxs-lookup"><span data-stu-id="934f6-162">The `MmioChainer` base class provides a blocking `Run()` method that the derived class calls.</span></span>  
  
    ```cpp  
    bool Launch(const CString& args)  
    {  
    CString cmdline = L"dotNetFx45_Full_x86_x64.exe -pipe TheSectionName " + args; // Customize with name and location of setup .exe that you want to run  
    STARTUPINFO si = {0};  
    si.cb = sizeof(si);  
    PROCESS_INFORMATION pi = {0};  
  
    // Launch the Setup.exe that installs the .NET Framework 4.5  
    BOOL bLaunchedSetup = ::CreateProcess(NULL,   
     cmdline.GetBuffer(),  
     NULL, NULL, FALSE, 0, NULL, NULL,   
     &si,  
     &pi);  
  
    // If successful   
    if (bLaunchedSetup != 0)  
    {  
    IProgressObserver& observer = dynamic_cast<IProgressObserver&>(*this);  
    Run(pi.hProcess, observer);  
  
    ……………………..   
    return (bLaunchedSetup != 0);  
    }  
    ```  
  
-   <span data-ttu-id="934f6-163">`Send` 方法會攔截並處理訊息。</span><span class="sxs-lookup"><span data-stu-id="934f6-163">The `Send` method intercepts and processes the messages.</span></span>  <span data-ttu-id="934f6-164">這個 .NET Framework 版本中唯一支援的訊息是關閉應用程式訊息。</span><span class="sxs-lookup"><span data-stu-id="934f6-164">In this version of the .NET Framework, the only supported message is the close application message.</span></span>  
  
    ```cpp  
            // SendMessage  
            //  
            // Send a message and wait for the response.  
            // dwMessage: Message to send  
            // pData: The buffer to copy the data to  
            // dwDataLength: Initially a pointer to the size of pBuffer.  Upon successful call, the number of bytes copied to pBuffer.  
            //--------------------------------------------------------------  
        virtual DWORD Send(DWORD dwMessage, LPVOID pData, DWORD dwDataLength)  
        {  
            DWORD dwResult = 0;  
            printf("recieved message: %d\n", dwMessage);  
            // Handle message  
            switch (dwMessage)  
            {  
            case MMIO_CLOSE_APPS:  
                {  
                    printf("    applications are holding files in use:\n");  
                    IronMan::MmioCloseApplications* applications = reinterpret_cast<IronMan::MmioCloseApplications*>(pData);  
                    for(DWORD i = 0; i < applications->m_dwApplicationsSize; i++)  
                    {  
                        printf("      %ls (%d)\n", applications->m_applications[i].m_szName, applications->m_applications[i].m_dwPid);  
                    }  
  
                    printf("    should appliations be closed? (Y)es, (N)o, (R)efresh : ");  
                    while (dwResult == 0)  
                    {  
                        switch (toupper(getwchar()))  
                        {  
                        case 'Y':  
                            dwResult = IDYES;  // Close apps  
                            break;  
                        case 'N':  
                            dwResult = IDNO;  
                            break;  
                        case 'R':  
                            dwResult = IDRETRY;  
                            break;  
                        }  
                    }  
                    printf("\n");  
                    break;  
                }  
            default:  
                break;  
            }  
            printf("  response: %d\n  ", dwResult);  
            return dwResult;  
        }  
    };  
    ```  
  
-   <span data-ttu-id="934f6-165">進度資料是不帶正負號的 `char`，介於 0 (0%) 和 255 (100%) 之間。</span><span class="sxs-lookup"><span data-stu-id="934f6-165">Progress data is an unsigned `char` between 0 (0%) and 255 (100%).</span></span>  
  
    ```cpp  
    private: // IProgressObserver  
        virtual void OnProgress(unsigned char ubProgressSoFar)  
        {…………  
       }  
    ```  
  
-   <span data-ttu-id="934f6-166">HRESULT 會傳遞至 `Finished` 方法。</span><span class="sxs-lookup"><span data-stu-id="934f6-166">The HRESULT is passed to the `Finished` method.</span></span>  
  
    ```cpp  
    virtual void Finished(HRESULT hr)  
    {  
    // This HRESULT is communicated over MMIO and may be different than process  
    // Exit code of the Chainee Setup.exe itself  
    printf("\r\nFinished HRESULT: 0x%08X\r\n", hr);  
    }  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="934f6-167">[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 可轉散發套件一般會寫入許多進度訊息和表示完成的單一訊息 (在 Chainer 端)。</span><span class="sxs-lookup"><span data-stu-id="934f6-167">The [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] redistributable typically writes many progress messages and a single message that indicates completion (on the chainer side).</span></span> <span data-ttu-id="934f6-168">它也會以非同步方式讀取，尋找 `Abort` 記錄。</span><span class="sxs-lookup"><span data-stu-id="934f6-168">It also reads asynchronously, looking for `Abort` records.</span></span> <span data-ttu-id="934f6-169">如果收到 `Abort` 記錄，即取消安裝，並在中止安裝且復原安裝作業之後，以 E_ABORT 寫入完成記錄當成資料。</span><span class="sxs-lookup"><span data-stu-id="934f6-169">If it receives an `Abort` record, it cancels the installation, and writes a finished record with E_ABORT as its data after the installation has been aborted and setup operations have been rolled back.</span></span>  
  
 <span data-ttu-id="934f6-170">一般的伺服器會建立隨機的 MMIO 檔案名稱、建立檔案 (如先前 `Server::CreateSection` 的程式碼範例所示)，並使用 `CreateProcess` 方法以 `-pipe someFileSectionName` 選項傳遞管道名稱來啟動可轉散發套件。</span><span class="sxs-lookup"><span data-stu-id="934f6-170">A typical server creates a random MMIO file name, creates the file (as shown in the previous code example, in `Server::CreateSection`), and launches the redistributable by using the `CreateProcess` method and passing the pipe name with the `-pipe someFileSectionName` option.</span></span> <span data-ttu-id="934f6-171">伺服器應利用應用程式 UI 特定的程式碼實作 `OnProgress`、`Send` 和 `Finished` 方法。</span><span class="sxs-lookup"><span data-stu-id="934f6-171">The server should implement `OnProgress`, `Send`, and `Finished` methods with application UI-specific code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="934f6-172">請參閱</span><span class="sxs-lookup"><span data-stu-id="934f6-172">See Also</span></span>  
 [<span data-ttu-id="934f6-173">開發人員部署手冊</span><span class="sxs-lookup"><span data-stu-id="934f6-173">Deployment Guide for Developers</span></span>](../../../docs/framework/deployment/deployment-guide-for-developers.md)  
 [<span data-ttu-id="934f6-174">部署</span><span class="sxs-lookup"><span data-stu-id="934f6-174">Deployment</span></span>](../../../docs/framework/deployment/index.md)
