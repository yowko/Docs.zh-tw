---
title: 佇列訊息的疑難排解
ms.date: 03/30/2017
ms.assetid: a5f2836f-018d-42f5-a571-1e97e64ea5b0
ms.openlocfilehash: 5c039c34983647884561f33645f26e4a89280248
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2020
ms.locfileid: "76921260"
---
# <a name="troubleshooting-queued-messaging"></a><span data-ttu-id="82d44-102">佇列訊息的疑難排解</span><span class="sxs-lookup"><span data-stu-id="82d44-102">Troubleshooting Queued Messaging</span></span>

<span data-ttu-id="82d44-103">本節包含在 Windows Communication Foundation （WCF）中使用佇列的常見問題和疑難排解說明。</span><span class="sxs-lookup"><span data-stu-id="82d44-103">This section contains common questions and troubleshooting help for using queues in Windows Communication Foundation (WCF).</span></span>

## <a name="common-questions"></a><span data-ttu-id="82d44-104">常見問題</span><span class="sxs-lookup"><span data-stu-id="82d44-104">Common Questions</span></span>

<span data-ttu-id="82d44-105">**問：** 我使用了 WCF Beta 1，而我安裝了 MSMQ 的修補程式。</span><span class="sxs-lookup"><span data-stu-id="82d44-105">**Q:** I used WCF Beta 1 and I installed the MSMQ hotfix.</span></span> <span data-ttu-id="82d44-106">我是否需要移除這個 Hotfix？</span><span class="sxs-lookup"><span data-stu-id="82d44-106">Do I need to remove the hotfix?</span></span>

<span data-ttu-id="82d44-107">**答：** 可以。</span><span class="sxs-lookup"><span data-stu-id="82d44-107">**A:** Yes.</span></span> <span data-ttu-id="82d44-108">不再支援這個 Hotfix。</span><span class="sxs-lookup"><span data-stu-id="82d44-108">This hotfix is no longer supported.</span></span> <span data-ttu-id="82d44-109">WCF 現在可以在沒有修補程式需求的 MSMQ 上運作。</span><span class="sxs-lookup"><span data-stu-id="82d44-109">WCF now works on MSMQ without a hotfix requirement.</span></span>

<span data-ttu-id="82d44-110">**問：** MSMQ 有兩個系結： <xref:System.ServiceModel.NetMsmqBinding> 和 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>。</span><span class="sxs-lookup"><span data-stu-id="82d44-110">**Q:** There are two bindings for MSMQ: <xref:System.ServiceModel.NetMsmqBinding> and <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>.</span></span> <span data-ttu-id="82d44-111">我應該在什麼狀況下使用它們？</span><span class="sxs-lookup"><span data-stu-id="82d44-111">What should I use and when?</span></span>

<span data-ttu-id="82d44-112">**答：** 當您想要使用 MSMQ 做為兩個 WCF 應用程式之間佇列通訊的傳輸時，請使用 <xref:System.ServiceModel.NetMsmqBinding>。</span><span class="sxs-lookup"><span data-stu-id="82d44-112">**A:** Use the <xref:System.ServiceModel.NetMsmqBinding> when you want to use MSMQ as a transport for queued communication between two WCF applications.</span></span> <span data-ttu-id="82d44-113">當您想要使用現有的 MSMQ 應用程式與新的 WCF 應用程式通訊時，請使用 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>。</span><span class="sxs-lookup"><span data-stu-id="82d44-113">Use the <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> when you want to use existing MSMQ applications to communicate with new WCF applications.</span></span>

<span data-ttu-id="82d44-114">**問：** 我必須升級 MSMQ 才能使用 <xref:System.ServiceModel.NetMsmqBinding> 和 `MsmqIntegration` 系結嗎？</span><span class="sxs-lookup"><span data-stu-id="82d44-114">**Q:** Do I have to upgrade MSMQ to use the <xref:System.ServiceModel.NetMsmqBinding> and `MsmqIntegration` bindings?</span></span>

<span data-ttu-id="82d44-115">**答：** 否。</span><span class="sxs-lookup"><span data-stu-id="82d44-115">**A:** No.</span></span> <span data-ttu-id="82d44-116">這兩個系結都適用于 Windows XP 和 Windows Server 2003 上的 MSMQ 3.0。</span><span class="sxs-lookup"><span data-stu-id="82d44-116">Both bindings work with MSMQ 3.0 on Windows XP and Windows Server 2003.</span></span> <span data-ttu-id="82d44-117">當您升級至 Windows Vista 中的 MSMQ 4.0 時，系結的某些功能就會變成可用。</span><span class="sxs-lookup"><span data-stu-id="82d44-117">Certain features of the bindings become available when you upgrade to MSMQ 4.0 in Windows Vista.</span></span>

<span data-ttu-id="82d44-118">**問：** <xref:System.ServiceModel.NetMsmqBinding> 和 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> 系結的哪些功能可在 MSMQ 4.0 中使用，但不在 MSMQ 3.0 中？</span><span class="sxs-lookup"><span data-stu-id="82d44-118">**Q:** What features of the <xref:System.ServiceModel.NetMsmqBinding> and <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> bindings are available in MSMQ 4.0 but not in MSMQ 3.0?</span></span>

<span data-ttu-id="82d44-119">**答：** 下列功能可在 MSMQ 4.0 中取得，但無法在 MSMQ 3.0 中使用：</span><span class="sxs-lookup"><span data-stu-id="82d44-119">**A:** The following features are available in MSMQ 4.0 but not in MSMQ 3.0:</span></span>

- <span data-ttu-id="82d44-120">只有 MSMQ 4.0 支援自訂的寄不出的信件佇列。</span><span class="sxs-lookup"><span data-stu-id="82d44-120">Custom dead-letter queue is supported only on MSMQ 4.0.</span></span>

- <span data-ttu-id="82d44-121">MSMQ 3.0 和 4.0 以不同的方式處理有害訊息。</span><span class="sxs-lookup"><span data-stu-id="82d44-121">MSMQ 3.0 and 4.0 handle poison messages differently.</span></span>

- <span data-ttu-id="82d44-122">只有 MSMQ 4.0 支援遠端交易讀取。</span><span class="sxs-lookup"><span data-stu-id="82d44-122">Only MSMQ 4.0 supports remote transacted read.</span></span>

<span data-ttu-id="82d44-123">如需詳細資訊，請參閱[Windows Vista、Windows Server 2003 和 WINDOWS XP 中的佇列功能差異](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)。</span><span class="sxs-lookup"><span data-stu-id="82d44-123">For more information, see [Differences in Queuing Features in Windows Vista, Windows Server 2003, and Windows XP](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md).</span></span>

<span data-ttu-id="82d44-124">**問：** 我可以在佇列通訊的一端使用 MSMQ 3.0，而在另一端使用 MSMQ 4.0 嗎？</span><span class="sxs-lookup"><span data-stu-id="82d44-124">**Q:** Can I use MSMQ 3.0 on one side of a queued communication and MSMQ 4.0 on the other side?</span></span>

<span data-ttu-id="82d44-125">**答：** 可以。</span><span class="sxs-lookup"><span data-stu-id="82d44-125">**A:** Yes.</span></span>

<span data-ttu-id="82d44-126">**問：** 我想要將現有的 MSMQ 應用程式與新的 WCF 用戶端或伺服器整合。</span><span class="sxs-lookup"><span data-stu-id="82d44-126">**Q:** I want to integrate existing MSMQ applications with new WCF clients or servers.</span></span> <span data-ttu-id="82d44-127">我是否需要為 MSMQ 基礎結構的兩端同時升級？</span><span class="sxs-lookup"><span data-stu-id="82d44-127">Do I need to upgrade both sides of my MSMQ infrastructure?</span></span>

<span data-ttu-id="82d44-128">**答：** 否。</span><span class="sxs-lookup"><span data-stu-id="82d44-128">**A:** No.</span></span> <span data-ttu-id="82d44-129">您不需要將任何一端升級至 MSMQ 4.0。</span><span class="sxs-lookup"><span data-stu-id="82d44-129">You do not have to upgrade to MSMQ 4.0 on either side.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="82d44-130">疑難排解</span><span class="sxs-lookup"><span data-stu-id="82d44-130">Troubleshooting</span></span>

<span data-ttu-id="82d44-131">本章節包含最常見疑難排解問題的解答。</span><span class="sxs-lookup"><span data-stu-id="82d44-131">This section contains answers to most common troubleshooting issues.</span></span> <span data-ttu-id="82d44-132">屬於已知限制的問題也會在版本資訊中加以說明。</span><span class="sxs-lookup"><span data-stu-id="82d44-132">Some issues that are known limitations are also described in the release notes.</span></span>

<span data-ttu-id="82d44-133">**問：** 我嘗試使用私用佇列，但收到下列例外狀況： `System.InvalidOperationException`： URL 無效。</span><span class="sxs-lookup"><span data-stu-id="82d44-133">**Q:** I am trying to use a private queue and I get the following exception: `System.InvalidOperationException`: The URL is invalid.</span></span> <span data-ttu-id="82d44-134">佇列的 URL 不可包含 '$' 字元。</span><span class="sxs-lookup"><span data-stu-id="82d44-134">The URL for the queue cannot contain the '$' character.</span></span> <span data-ttu-id="82d44-135">請使用 net.msmq://machine/private/queueName 中的語法，來定址私用佇列。</span><span class="sxs-lookup"><span data-stu-id="82d44-135">Use the syntax in net.msmq://machine/private/queueName to address a private queue.</span></span>

<span data-ttu-id="82d44-136">**答：** 請檢查您設定和程式碼中的佇列統一資源識別項（URI）。</span><span class="sxs-lookup"><span data-stu-id="82d44-136">**A:** Please check the queue Uniform Resource Identifier (URI) in your configuration and code.</span></span> <span data-ttu-id="82d44-137">請勿在 URI 中使用 "$" 字元。</span><span class="sxs-lookup"><span data-stu-id="82d44-137">Do not use the "$" character in the URI.</span></span> <span data-ttu-id="82d44-138">例如，若要定址名為 OrdersQueue 的私用佇列，請將 URI 指定為 net.msmq://localhost/private/ordersQueue。</span><span class="sxs-lookup"><span data-stu-id="82d44-138">For example, to address a private queue named OrdersQueue, specify the URI as net.msmq://localhost/private/ordersQueue.</span></span>

<span data-ttu-id="82d44-139">**問：** 在佇列應用程式上呼叫 `ServiceHost.Open()` 會擲回下列例外狀況： `System.ArgumentException`：基底位址不能包含 URI 查詢字串。</span><span class="sxs-lookup"><span data-stu-id="82d44-139">**Q:** Calling `ServiceHost.Open()` on my queued application throws the following exception: `System.ArgumentException`: A base address cannot contain a URI query string.</span></span> <span data-ttu-id="82d44-140">為什麼？</span><span class="sxs-lookup"><span data-stu-id="82d44-140">Why?</span></span>

<span data-ttu-id="82d44-141">**答：** 檢查您的設定檔和程式碼中的佇列 URI。</span><span class="sxs-lookup"><span data-stu-id="82d44-141">**A:** Check the queue URI in your configuration file and in your code.</span></span> <span data-ttu-id="82d44-142">雖然 MSMQ 佇列支援使用 '?' 字元，但 URI 會將這個字元解譯為字串查詢的開頭。</span><span class="sxs-lookup"><span data-stu-id="82d44-142">While MSMQ queues support the use of the '?' character, URIs interpret this character as the beginning of a string query.</span></span> <span data-ttu-id="82d44-143">為了避免這個問題，請使用不含 '?' 字元的佇列名稱。</span><span class="sxs-lookup"><span data-stu-id="82d44-143">To avoid this issue, use queue names that do not contain '?' characters.</span></span>

<span data-ttu-id="82d44-144">**問：** 我的傳送成功，但在接收者上未叫用服務作業。</span><span class="sxs-lookup"><span data-stu-id="82d44-144">**Q:** My send succeeded but no service operation is invoked on the receiver.</span></span> <span data-ttu-id="82d44-145">為什麼？</span><span class="sxs-lookup"><span data-stu-id="82d44-145">Why?</span></span>

<span data-ttu-id="82d44-146">**答：** 若要判斷答案，請完成下列檢查清單：</span><span class="sxs-lookup"><span data-stu-id="82d44-146">**A:** To determine the answer, work through the following check list:</span></span>

- <span data-ttu-id="82d44-147">檢查異動式佇列需求是否相容於指定的保證。</span><span class="sxs-lookup"><span data-stu-id="82d44-147">Check that the transactional queue requirements are compatible with the assurances specified.</span></span> <span data-ttu-id="82d44-148">請注意下列準則：</span><span class="sxs-lookup"><span data-stu-id="82d44-148">Note the following principles:</span></span>

  - <span data-ttu-id="82d44-149">您只能將具有「正好一次」保證（<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `true`）的永久性訊息（資料包和會話）傳送至交易式佇列。</span><span class="sxs-lookup"><span data-stu-id="82d44-149">You can send durable messages (datagrams and sessions) with "exactly once" assurances (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `true`) only to a transactional queue.</span></span>

  - <span data-ttu-id="82d44-150">您只能傳送具有「正好一次」保證的工作階段。</span><span class="sxs-lookup"><span data-stu-id="82d44-150">You can send sessions only with "exactly once" assurances.</span></span>

  - <span data-ttu-id="82d44-151">從異動式佇列接收工作階段中的訊息時需要進行異動。</span><span class="sxs-lookup"><span data-stu-id="82d44-151">A transaction is required to receive messages in a session from a transactional queue.</span></span>

  - <span data-ttu-id="82d44-152">您只能傳送或接收非交易式佇列的 volatile 或永久性訊息（僅限資料包），而不保證（<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `false`）。</span><span class="sxs-lookup"><span data-stu-id="82d44-152">You can send or receive volatile or durable messages (datagrams only) with no assurances (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `false`) only to a non-transactional queue.</span></span>

- <span data-ttu-id="82d44-153">檢查寄不出的信件佇列。</span><span class="sxs-lookup"><span data-stu-id="82d44-153">Check the dead-letter queue.</span></span> <span data-ttu-id="82d44-154">如果您在其中找到訊息，請判斷它們為何沒有傳遞。</span><span class="sxs-lookup"><span data-stu-id="82d44-154">If you find the messages there, determine why they were not delivered.</span></span>

- <span data-ttu-id="82d44-155">檢查傳出佇列是否有連接或定址問題。</span><span class="sxs-lookup"><span data-stu-id="82d44-155">Check the outgoing queues for connectivity or addressing problems.</span></span>

<span data-ttu-id="82d44-156">**問：** 我已經指定自訂的寄不出的信件佇列，但是當我啟動傳送者應用程式時，收到的例外狀況是找不到寄不出的信件佇列，或是傳送應用程式沒有寄不出的信件佇列的許可權。</span><span class="sxs-lookup"><span data-stu-id="82d44-156">**Q:** I have specified a custom dead-letter queue, but when I start the sender application, I get an exception that either the dead-letter queue is not found, or the sending application has no permission to the dead-letter queue.</span></span> <span data-ttu-id="82d44-157">為什麼會發生這種問題？</span><span class="sxs-lookup"><span data-stu-id="82d44-157">Why is this happening?</span></span>

<span data-ttu-id="82d44-158">**答：** 自訂寄不出的信件佇列 URI 必須在第一個區段中包含 "localhost" 或電腦名稱稱，例如 net.tcp：//localhost/private/myAppdead-letter queue。</span><span class="sxs-lookup"><span data-stu-id="82d44-158">**A:** The custom dead-letter queue URI must include a "localhost" or the computer name in the first segment, for example, net.msmq://localhost/private/myAppdead-letter queue.</span></span>

<span data-ttu-id="82d44-159">**問：** 是否一律需要定義自訂的寄不出的信件佇列，或是否有預設的寄不出的信件佇列？</span><span class="sxs-lookup"><span data-stu-id="82d44-159">**Q:** Is it always necessary to define a custom dead-letter queue, or is there a default dead-letter queue?</span></span>

<span data-ttu-id="82d44-160">**答：** 如果保證是「正好一次」（<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `true`），而且如果您沒有指定自訂的寄不出的信件佇列，預設值就是全系統的交易式寄不出的信件佇列。</span><span class="sxs-lookup"><span data-stu-id="82d44-160">**A:** If assurances are "exactly once" (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `true`), and if you do not specify a custom dead-letter queue, the default is a system-wide transactional dead-letter queue.</span></span>

<span data-ttu-id="82d44-161">如果保證為 none （<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `false`），則預設為沒有寄不出的信件佇列功能。</span><span class="sxs-lookup"><span data-stu-id="82d44-161">If assurances are none (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `false`), then the default is no dead-letter queue functionality.</span></span>

<span data-ttu-id="82d44-162">**問：** 我的服務在 SvcHost 上擲回。請開啟並顯示「ListenerFactory 無法符合 EndpointListener 需求」訊息。</span><span class="sxs-lookup"><span data-stu-id="82d44-162">**Q:** My service throws on SvcHost.Open with a message "EndpointListener requirements cannot be met by the ListenerFactory".</span></span> <span data-ttu-id="82d44-163">為什麼？</span><span class="sxs-lookup"><span data-stu-id="82d44-163">Why?</span></span>

<span data-ttu-id="82d44-164">答：</span><span class="sxs-lookup"><span data-stu-id="82d44-164">A.</span></span> <span data-ttu-id="82d44-165">請檢查您的服務合約。</span><span class="sxs-lookup"><span data-stu-id="82d44-165">Check your service contract.</span></span> <span data-ttu-id="82d44-166">您可能忘了將 "IsOneWay =`true`" 放在所有服務作業上。</span><span class="sxs-lookup"><span data-stu-id="82d44-166">You may have forgotten to put "IsOneWay=`true`" on all the service operations.</span></span> <span data-ttu-id="82d44-167">佇列只會支援單向服務作業。</span><span class="sxs-lookup"><span data-stu-id="82d44-167">Queues support only one-way service operations.</span></span>

<span data-ttu-id="82d44-168">**問：** 佇列中有訊息，但未叫用服務作業。</span><span class="sxs-lookup"><span data-stu-id="82d44-168">**Q:** There are messages in the queue but no service operation is invoked.</span></span> <span data-ttu-id="82d44-169">問題出在哪裡？</span><span class="sxs-lookup"><span data-stu-id="82d44-169">What is the problem?</span></span>

<span data-ttu-id="82d44-170">**答：** 判斷您的服務主機是否發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="82d44-170">**A:** Determine if your service host is faulted.</span></span> <span data-ttu-id="82d44-171">您可以查看追蹤，或是實作 `IErrorHandler` 以檢查這點。</span><span class="sxs-lookup"><span data-stu-id="82d44-171">You can check by looking at the trace or implementing `IErrorHandler`.</span></span> <span data-ttu-id="82d44-172">根據預設，如果偵測到有害訊息，便會發生服務主機錯誤。</span><span class="sxs-lookup"><span data-stu-id="82d44-172">Service host faults, by default, if a poison message is detected.</span></span>

<span data-ttu-id="82d44-173">**問：** 佇列中有訊息，但我的 Web 主控佇列服務並未啟動。</span><span class="sxs-lookup"><span data-stu-id="82d44-173">**Q:** There are messages in the queue but my Web-hosted queued service is not getting activated.</span></span> <span data-ttu-id="82d44-174">為什麼？</span><span class="sxs-lookup"><span data-stu-id="82d44-174">Why?</span></span>

<span data-ttu-id="82d44-175">**答：** 最常見的原因是許可權。</span><span class="sxs-lookup"><span data-stu-id="82d44-175">**A:** The most common reason is permissions.</span></span>

1. <span data-ttu-id="82d44-176">請確定 `NetMsmqActivator` 處理序正在執行，而且 `NetMsmqActivator` 處理序的身分識別已授與在佇列上讀取和搜尋的權限。</span><span class="sxs-lookup"><span data-stu-id="82d44-176">Ensure that the `NetMsmqActivator` process is running and the identity of the `NetMsmqActivator` process is given read and seek permission on the queue.</span></span>

2. <span data-ttu-id="82d44-177">如果 `NetMsmqActivator` 正在監視遠端電腦上的佇列，請確定 `NetMsmqActivator` 不是以受限制的權杖執行。</span><span class="sxs-lookup"><span data-stu-id="82d44-177">If the `NetMsmqActivator` is monitoring queues on a remote machine, ensure that `NetMsmqActivator` does not run under a restricted token.</span></span> <span data-ttu-id="82d44-178">若要以不受限制的權杖執行 `NetMsmqActivator`：</span><span class="sxs-lookup"><span data-stu-id="82d44-178">To run the `NetMsmqActivator` with an unrestricted token:</span></span>

    ```console
    sc sidtype NetMsmqActivator unrestricted
    ```

<span data-ttu-id="82d44-179">如需與非安全性相關的 Web 主機問題，請參閱： [Web 裝載佇列的應用程式](../../../../docs/framework/wcf/feature-details/web-hosting-a-queued-application.md)。</span><span class="sxs-lookup"><span data-stu-id="82d44-179">For non-security related Web host issues refer to: [Web Hosting a Queued Application](../../../../docs/framework/wcf/feature-details/web-hosting-a-queued-application.md).</span></span>

<span data-ttu-id="82d44-180">**問：** 存取會話最簡單的方式是什麼？</span><span class="sxs-lookup"><span data-stu-id="82d44-180">**Q:** What is the easiest way to access sessions?</span></span>

<span data-ttu-id="82d44-181">**答：** 在對應至會話中最後一則訊息的作業上設定 [自動完成] =`true`，然後在所有剩餘的服務作業上設定 [自動完成] = [`false`]。</span><span class="sxs-lookup"><span data-stu-id="82d44-181">**A:** Set AutoComplete=`true` on the operation that corresponds to the last message in the session, and set AutoComplete=`false` on all remaining service operations.</span></span>

<span data-ttu-id="82d44-182">**問：** 為什麼當我從包含佇列會話訊息和佇列資料包訊息的佇列讀取時，我的服務會擲回 `ProtocolException`？</span><span class="sxs-lookup"><span data-stu-id="82d44-182">**Q:** Why does my service throw a `ProtocolException` when reading from a queue that contains both queued session messages and queued datagram messages?</span></span>

<span data-ttu-id="82d44-183">**答：** 佇列會話訊息和佇列資料包訊息的組成方式有基本差異。</span><span class="sxs-lookup"><span data-stu-id="82d44-183">**A:** There is a fundamental difference in the way queued session messages and queued datagram messages are composed.</span></span> <span data-ttu-id="82d44-184">因此，預期要讀取佇列工作階段訊息的服務無法接收佇列資料包訊息，而預期要讀取佇列資料包訊息的服務無法接收工作階段訊息。</span><span class="sxs-lookup"><span data-stu-id="82d44-184">Because of this, a service that is expecting to read a queued session message cannot receive a queued datagram message and a service expecting to read a queued datagram message cannot receive a session message.</span></span> <span data-ttu-id="82d44-185">嘗試從相同佇列同時讀取這兩種訊息類型時，便會擲回下列例外狀況：</span><span class="sxs-lookup"><span data-stu-id="82d44-185">Attempting to read both types of messages from the same queue throws the following exception:</span></span>

```console
System.ServiceModel.MsmqPoisonMessageException: The transport channel detected a poison message. This occurred because the message exceeded the maximum number of delivery attempts or because the channel detected a fundamental problem with the message. The inner exception may contain additional information.
---> System.ServiceModel.ProtocolException: An incoming MSMQ message contained invalid or unexpected .NET Message Framing information in its body. The message cannot be received. Ensure that the sender is using a compatible service contract with a matching SessionMode.
```

<span data-ttu-id="82d44-186">當應用程式從相同的電腦同時傳送佇列工作階段訊息和佇列資料包訊息時，系統的寄不出的信件佇列以及自訂的寄不出的信件佇列特別容易受到這個問題影響。</span><span class="sxs-lookup"><span data-stu-id="82d44-186">The system dead-letter queue, as well as any custom dead-letter queue, is particularly susceptible to this issue if an application sends both queued session messages and queued datagram messages from the same computer.</span></span> <span data-ttu-id="82d44-187">無法成功傳送的訊息會移到寄不出的信件佇列中。</span><span class="sxs-lookup"><span data-stu-id="82d44-187">If a message cannot be sent successfully, it is moved to the dead-letter queue.</span></span> <span data-ttu-id="82d44-188">在這些狀況下，寄不出的信件佇列中可能會同時有工作階段訊息和資料包訊息。</span><span class="sxs-lookup"><span data-stu-id="82d44-188">Under these circumstances, it is possible to have both session and datagram messages in the dead-letter queue.</span></span> <span data-ttu-id="82d44-189">在執行階段從佇列讀取時，沒有任何方法可以分開這兩種訊息，因此，應用程式不應該從相同的電腦同時傳送佇列工作階段訊息和佇列資料包訊息。</span><span class="sxs-lookup"><span data-stu-id="82d44-189">There is no way to separate both types of messages at runtime when reading from a queue, therefore, applications should not send both queued session messages and queued datagram messages from the same computer.</span></span>

### <a name="msmq-integration-specific-troubleshooting"></a><span data-ttu-id="82d44-190">MSMQ 整合：特定疑難排解</span><span class="sxs-lookup"><span data-stu-id="82d44-190">MSMQ Integration: Specific Troubleshooting</span></span>

<span data-ttu-id="82d44-191">**問：** 當我傳送訊息時，或當我開啟服務主機時，會收到指出配置錯誤的錯誤。</span><span class="sxs-lookup"><span data-stu-id="82d44-191">**Q:** When I send a message, or when I open the service host, I get an error that indicates the scheme is wrong.</span></span> <span data-ttu-id="82d44-192">為什麼？</span><span class="sxs-lookup"><span data-stu-id="82d44-192">Why?</span></span>

<span data-ttu-id="82d44-193">**答：** 當您使用 MSMQ 整合系結時，您必須使用 msmq.formatname 配置。</span><span class="sxs-lookup"><span data-stu-id="82d44-193">**A:** When you use the MSMQ integration binding, you must use the msmq.formatname scheme.</span></span> <span data-ttu-id="82d44-194">例如，msmq.formatname:DIRECT=OS:.\private$\OrdersQueue。</span><span class="sxs-lookup"><span data-stu-id="82d44-194">For example, msmq.formatname:DIRECT=OS:.\private$\OrdersQueue.</span></span> <span data-ttu-id="82d44-195">不過當指定自訂的寄不出的信件佇列時，您必須使用 net.msmq 配置。</span><span class="sxs-lookup"><span data-stu-id="82d44-195">But when you specify the custom dead-letter queue, you must use the net.msmq scheme.</span></span>

<span data-ttu-id="82d44-196">**問：** 當我使用公用或私用格式名稱，並在 Windows Vista 上開啟服務主機時，會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="82d44-196">**Q:** When I use a public or private format name and open the service host on Windows Vista, I get an error.</span></span> <span data-ttu-id="82d44-197">為什麼？</span><span class="sxs-lookup"><span data-stu-id="82d44-197">Why?</span></span>

<span data-ttu-id="82d44-198">**答：** Windows Vista 上的 WCF 整合通道會檢查是否可以開啟主要應用程式佇列的子佇列來處理有害訊息。</span><span class="sxs-lookup"><span data-stu-id="82d44-198">**A:** The WCF integration channel on Windows Vista checks to see if a sub-queue can be opened for the main application queue for handling poison messages.</span></span> <span data-ttu-id="82d44-199">子佇列的名稱衍生自傳遞至接聽項的 msmq.formatname URI。</span><span class="sxs-lookup"><span data-stu-id="82d44-199">The sub-queue name is derived from an msmq.formatname URI passed to the listener.</span></span> <span data-ttu-id="82d44-200">但是 MSMQ 中的子佇列名稱只能是直接格式名稱。</span><span class="sxs-lookup"><span data-stu-id="82d44-200">The sub-queue name in MSMQ can only be a direct format name.</span></span> <span data-ttu-id="82d44-201">所以您會看到錯誤。</span><span class="sxs-lookup"><span data-stu-id="82d44-201">So you see the error.</span></span> <span data-ttu-id="82d44-202">請將佇列 URI 變更為直接格式名稱。</span><span class="sxs-lookup"><span data-stu-id="82d44-202">Change the queue URI to a direct format name.</span></span>

<span data-ttu-id="82d44-203">**問：** 從 MSMQ 應用程式接收訊息時，訊息位於佇列中，而且不會由接收 WCF 應用程式讀取。</span><span class="sxs-lookup"><span data-stu-id="82d44-203">**Q:** When receiving a message from an MSMQ application, the message sits in the queue and is not read by the receiving WCF application.</span></span> <span data-ttu-id="82d44-204">為什麼？</span><span class="sxs-lookup"><span data-stu-id="82d44-204">Why?</span></span>

<span data-ttu-id="82d44-205">**答：** 請檢查訊息是否有主體。</span><span class="sxs-lookup"><span data-stu-id="82d44-205">**A:** Check to see whether the message has a body.</span></span> <span data-ttu-id="82d44-206">如果訊息沒有本文，MSMQ 整合通道便會忽略該訊息。</span><span class="sxs-lookup"><span data-stu-id="82d44-206">If the message has no body, the MSMQ integration channel ignores the message.</span></span> <span data-ttu-id="82d44-207">實作 `IErrorHandler`，即可獲得例外狀況的通知和檢查追蹤。</span><span class="sxs-lookup"><span data-stu-id="82d44-207">Implement `IErrorHandler` to be notified of exceptions and check the traces.</span></span>

### <a name="security-related-troubleshooting"></a><span data-ttu-id="82d44-208">安全性相關疑難排解</span><span class="sxs-lookup"><span data-stu-id="82d44-208">Security-Related Troubleshooting</span></span>

<span data-ttu-id="82d44-209">**問：** 當我執行在工作組模式中使用預設系結的範例時，訊息似乎會被傳送，但收件者永遠不會收到。</span><span class="sxs-lookup"><span data-stu-id="82d44-209">**Q:** When I run the sample that uses a default binding in workgroup mode, messages seem to get sent but are never received by the receiver.</span></span>

<span data-ttu-id="82d44-210">**答：** 根據預設，會使用需要 Active Directory 目錄服務的 MSMQ 內部憑證來簽署訊息。</span><span class="sxs-lookup"><span data-stu-id="82d44-210">**A:** By default, messages are signed using an MSMQ internal certificate that requires the Active Directory directory service.</span></span> <span data-ttu-id="82d44-211">由於工作群組模式中並沒有提供 Active Directory，因此簽署訊息會失敗。</span><span class="sxs-lookup"><span data-stu-id="82d44-211">In workgroup mode, because Active Directory is not available, signing the message fails.</span></span> <span data-ttu-id="82d44-212">因此，訊息會放在寄不出的信件佇列中，而且會指出失敗的原因，例如「錯誤的簽章」。</span><span class="sxs-lookup"><span data-stu-id="82d44-212">So the message lands in the dead-letter queue and failure cause, such as "Bad signature", is indicated.</span></span>

<span data-ttu-id="82d44-213">解決方法是關閉安全性。</span><span class="sxs-lookup"><span data-stu-id="82d44-213">The workaround is to turn off security.</span></span> <span data-ttu-id="82d44-214">這是藉由設定 <xref:System.ServiceModel.NetMsmqSecurity.Mode%2A> = <xref:System.ServiceModel.NetMsmqSecurityMode.None>，使其在工作組模式中正常執行。</span><span class="sxs-lookup"><span data-stu-id="82d44-214">This is done by setting <xref:System.ServiceModel.NetMsmqSecurity.Mode%2A> = <xref:System.ServiceModel.NetMsmqSecurityMode.None> to make it work in workgroup mode.</span></span>

<span data-ttu-id="82d44-215">另一個解決方法是從 <xref:System.ServiceModel.MsmqTransportSecurity> 屬性取得 <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>，並將其設定為 <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate>，並設定用戶端憑證。</span><span class="sxs-lookup"><span data-stu-id="82d44-215">Another workaround is to get the <xref:System.ServiceModel.MsmqTransportSecurity> from the <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A> property and set it to <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate>, and set the client certificate.</span></span>

<span data-ttu-id="82d44-216">而另外一種解決方法是搭配 Active Directory 整合來安裝 MSMQ。</span><span class="sxs-lookup"><span data-stu-id="82d44-216">Yet another workaround is to install MSMQ with Active Directory integration.</span></span>

<span data-ttu-id="82d44-217">**問：** 當我在 Active Directory 佇列中傳送具有預設系結（傳輸安全性）的訊息時，會收到「找不到內部憑證」訊息。</span><span class="sxs-lookup"><span data-stu-id="82d44-217">**Q:** When I send a message with default binding (transport security turned on) in Active Directory to a queue, I get an "internal certificate not found" message.</span></span> <span data-ttu-id="82d44-218">如何修正這個問題？</span><span class="sxs-lookup"><span data-stu-id="82d44-218">How do I fix this?</span></span>

<span data-ttu-id="82d44-219">**答：** 這表示必須更新寄件者 Active Directory 中的憑證。</span><span class="sxs-lookup"><span data-stu-id="82d44-219">**A:** This means that the certificate in Active Directory for the sender must be renewed.</span></span> <span data-ttu-id="82d44-220">若要這麼做，請開啟 **控制台**、系統**管理工具**、**電腦管理**、以滑鼠右鍵按一下  **MSMQ**，**然後選取**</span><span class="sxs-lookup"><span data-stu-id="82d44-220">To do so, open **Control Panel**, **Administrative Tools**, **Computer Management**, right-click **MSMQ**, and select **Properties**.</span></span> <span data-ttu-id="82d44-221">選取 [**使用者憑證**] 索引標籤，然後按一下 [**更新**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="82d44-221">Select the **User Certificate** tab and click the **Renew** button.</span></span>

<span data-ttu-id="82d44-222">**問：** 當我使用 <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate> 傳送訊息，並指定要使用的憑證時，我收到「不正確憑證」訊息。</span><span class="sxs-lookup"><span data-stu-id="82d44-222">**Q:** When I send a message using <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate> and specify the certificate to use, I get an "Invalid certificate" message.</span></span> <span data-ttu-id="82d44-223">如何修正這個問題？</span><span class="sxs-lookup"><span data-stu-id="82d44-223">How do I fix this?</span></span>

<span data-ttu-id="82d44-224">**答：** 您不能使用具有憑證模式的本機電腦憑證存放區。</span><span class="sxs-lookup"><span data-stu-id="82d44-224">**A:** You cannot use a local machine certificate store with certificate mode.</span></span> <span data-ttu-id="82d44-225">您必須使用憑證嵌入式管理單元，將憑證從電腦憑證存放區複製到目前使用者存放區。</span><span class="sxs-lookup"><span data-stu-id="82d44-225">You have to copy the certificate from the machine certificate store to the current user store using the Certificate snap-in.</span></span> <span data-ttu-id="82d44-226">若要取得憑證嵌入式管理單元：</span><span class="sxs-lookup"><span data-stu-id="82d44-226">To get the Certificate snap-in:</span></span>

1. <span data-ttu-id="82d44-227">按一下 [**開始**]，選取 [**執行**]，輸入 `mmc`，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="82d44-227">Click **Start**, select **Run**, type `mmc`, and click **OK**.</span></span>

2. <span data-ttu-id="82d44-228">在**Microsoft Management Console**中，開啟 [檔案 **] 功能表，** 然後選取 [**新增/移除嵌入式管理單元**]。</span><span class="sxs-lookup"><span data-stu-id="82d44-228">In the **Microsoft Management Console**, open the **File** menu and select **Add/Remove Snap-in**.</span></span>

3. <span data-ttu-id="82d44-229">在 [**新增/移除嵌入式管理單元**] 對話方塊中，按一下 [**新增**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="82d44-229">In the **Add/Remove Snap-in** dialog box, click the **Add** button.</span></span>

4. <span data-ttu-id="82d44-230">在 [**新增獨立嵌入式管理單元**] 對話方塊中，選取 [憑證]，然後按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="82d44-230">In the **Add Standalone Snap-in** dialog box, select Certificates and click **Add**.</span></span>

5. <span data-ttu-id="82d44-231">在 [**憑證**嵌入式管理單元] 對話方塊中，選取 [**我的使用者帳戶]，** 然後按一下 **[完成]** 。</span><span class="sxs-lookup"><span data-stu-id="82d44-231">In the **Certificates** snap-in dialog box, select **My user account,** and click **Finish**.</span></span>

6. <span data-ttu-id="82d44-232">接下來，使用先前的步驟新增第二個憑證嵌入式管理單元，但這次請選取 [**電腦帳戶**]，然後按 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="82d44-232">Next, add a second Certificates snap-in using the previous steps, but this time select **Computer account** and click **Next**.</span></span>

7. <span data-ttu-id="82d44-233">選取 [**本機電腦**]，然後按一下 **[完成]** 。</span><span class="sxs-lookup"><span data-stu-id="82d44-233">Select **Local Computer** and click **Finish**.</span></span> <span data-ttu-id="82d44-234">現在，您可以從電腦憑證存放區將憑證拖放到目前使用者存放區。</span><span class="sxs-lookup"><span data-stu-id="82d44-234">You can now drag and drop certificates from the machine certificate store to the current user store.</span></span>

<span data-ttu-id="82d44-235">**問：** 當我的服務在工作組模式中從另一部電腦上的佇列讀取時，出現「拒絕存取」例外狀況。</span><span class="sxs-lookup"><span data-stu-id="82d44-235">**Q:** When my service reads from a queue on another computer in workgroup mode, I get an "access denied" exception.</span></span>

<span data-ttu-id="82d44-236">**答：** 在工作組模式中，若要讓遠端應用程式取得佇列的存取權，應用程式必須具有存取佇列的許可權。</span><span class="sxs-lookup"><span data-stu-id="82d44-236">**A:** In workgroup mode, for a remote application to gain access to the queue, the application must have permission to access the queue.</span></span> <span data-ttu-id="82d44-237">將「匿名登入」新增至佇列的存取控制清單（ACL），並授與讀取權限。</span><span class="sxs-lookup"><span data-stu-id="82d44-237">Add "Anonymous login" to the queue's access control list (ACL) and give it read permission.</span></span>

<span data-ttu-id="82d44-238">**問：** 當網路服務用戶端（或任何不含網域帳戶的用戶端）傳送佇列訊息時，傳送會因為憑證無效而失敗。</span><span class="sxs-lookup"><span data-stu-id="82d44-238">**Q:** When a network service client (or any client that does not have a domain account) sends a queued message, the send fails with an invalid certificate.</span></span> <span data-ttu-id="82d44-239">如何修正這個問題？</span><span class="sxs-lookup"><span data-stu-id="82d44-239">How do I fix this?</span></span>

<span data-ttu-id="82d44-240">**答：** 檢查系結設定。</span><span class="sxs-lookup"><span data-stu-id="82d44-240">**A:** Check the binding configuration.</span></span> <span data-ttu-id="82d44-241">預設繫結會開啟 MSMQ 傳輸安全性以簽署訊息。</span><span class="sxs-lookup"><span data-stu-id="82d44-241">The default binding has MSMQ transport security turned on to sign the message.</span></span> <span data-ttu-id="82d44-242">請關閉此選項。</span><span class="sxs-lookup"><span data-stu-id="82d44-242">Turn it off.</span></span>

### <a name="remote-transacted-receives"></a><span data-ttu-id="82d44-243">遠端交易接收</span><span class="sxs-lookup"><span data-stu-id="82d44-243">Remote Transacted Receives</span></span>

<span data-ttu-id="82d44-244">**問：** 當我在電腦 A 上有佇列，而 WCF 服務從電腦 B 上的佇列讀取訊息時（遠端交易接收案例），則不會從佇列讀取訊息。</span><span class="sxs-lookup"><span data-stu-id="82d44-244">**Q:** When I have a queue on machine A, and a WCF service that reads messages from a queue on machine B (the remote transacted receive scenario), messages are not read from the queue.</span></span> <span data-ttu-id="82d44-245">追蹤資訊表示接收失敗，訊息為「無法匯入交易」。</span><span class="sxs-lookup"><span data-stu-id="82d44-245">Tracing information indicates the receive failed with the message "Transaction cannot be imported."</span></span> <span data-ttu-id="82d44-246">我可以做什麼來修正這個問題？</span><span class="sxs-lookup"><span data-stu-id="82d44-246">What can I do to fix this?</span></span>

<span data-ttu-id="82d44-247">**答：** 有三個可能的原因：</span><span class="sxs-lookup"><span data-stu-id="82d44-247">**A:** There are three possible reasons for this:</span></span>

- <span data-ttu-id="82d44-248">如果您是在網域模式中，遠端交易接收便需要 Microsoft Distributed Transaction Coordinator (MSDTC) 網路存取。</span><span class="sxs-lookup"><span data-stu-id="82d44-248">If you are in domain mode, remote transacted receive requires Microsoft Distributed Transaction Coordinator (MSDTC) network access.</span></span> <span data-ttu-id="82d44-249">您可以使用 [**新增/移除元件**] 來啟用此。</span><span class="sxs-lookup"><span data-stu-id="82d44-249">You can enable this using **Add/Remove Components**.</span></span>

  ![顯示啟用網路 DTC 存取的螢幕擷取畫面。](./media/troubleshooting-queued-messaging/enable-distributed-transaction-coordinator-access.jpg)

- <span data-ttu-id="82d44-251">檢查與交易管理員進行通訊的驗證模式。</span><span class="sxs-lookup"><span data-stu-id="82d44-251">Check the authentication mode for communicating with the transaction manager.</span></span> <span data-ttu-id="82d44-252">如果您是在工作組模式中，則必須選取 [不需要驗證]。</span><span class="sxs-lookup"><span data-stu-id="82d44-252">If you are in workgroup mode, "No Authentication Required" must be selected.</span></span> <span data-ttu-id="82d44-253">如果您是在網域模式中，則必須選取 [需要相互驗證]。</span><span class="sxs-lookup"><span data-stu-id="82d44-253">If you are in domain mode, then "Mutual Authentication Required" must be selected.</span></span>

  <span data-ttu-id="82d44-254">![啟用 XA 交易](../../../../docs/framework/wcf/feature-details/media/4f3695e0-fb0b-4c5b-afac-75f8860d2bb0.jpg "4f3695e0-fb0b-4c5b-afac-75f8860d2bb0")</span><span class="sxs-lookup"><span data-stu-id="82d44-254">![Enabling XA transactions](../../../../docs/framework/wcf/feature-details/media/4f3695e0-fb0b-4c5b-afac-75f8860d2bb0.jpg "4f3695e0-fb0b-4c5b-afac-75f8860d2bb0")</span></span>

- <span data-ttu-id="82d44-255">請確定 MSDTC 位於**網際網路連線防火牆**設定的例外清單中。</span><span class="sxs-lookup"><span data-stu-id="82d44-255">Make sure that MSDTC is in the list of exceptions in the **Internet Connection Firewall** settings.</span></span>

- <span data-ttu-id="82d44-256">請確定您使用的是 Windows Vista。</span><span class="sxs-lookup"><span data-stu-id="82d44-256">Ensure that you are using Windows Vista.</span></span> <span data-ttu-id="82d44-257">Windows Vista 上的 MSMQ 支援遠端交易讀取。</span><span class="sxs-lookup"><span data-stu-id="82d44-257">MSMQ on Windows Vista supports remote transacted read.</span></span> <span data-ttu-id="82d44-258">在舊版 Window 中的 MSMQ 並不支援遠端交易讀取。</span><span class="sxs-lookup"><span data-stu-id="82d44-258">MSMQ on earlier Windows releases does not support remote transacted read.</span></span>

<span data-ttu-id="82d44-259">**問：** 當從佇列讀取的服務是網路服務（例如，在 Web 主機中）時，為何會在讀取佇列時引發拒絕存取的例外狀況？</span><span class="sxs-lookup"><span data-stu-id="82d44-259">**Q:** When the service reading from the queue is a network service, for example, in a Web host, why do I get an access-denied exception is raised when reading from the queue?</span></span>

<span data-ttu-id="82d44-260">**答：** 必須將網路服務讀取權限新增至佇列 ACL，以確保網路服務可以從佇列讀取。</span><span class="sxs-lookup"><span data-stu-id="82d44-260">**A:** Network service read access must be added to the queue ACL to ensure that a network service can read from the queue.</span></span>

<span data-ttu-id="82d44-261">**問：** 我是否可以使用 MSMQ 啟用服務，根據遠端電腦上佇列中的訊息來啟動應用程式？</span><span class="sxs-lookup"><span data-stu-id="82d44-261">**Q:** Can I use the MSMQ activation service to activate applications based on messages in a queue on a remote machine?</span></span>

<span data-ttu-id="82d44-262">**答：** 可以。</span><span class="sxs-lookup"><span data-stu-id="82d44-262">**A:** Yes.</span></span> <span data-ttu-id="82d44-263">若要這樣做，您必須將 MSMQ 啟動服務設定成當做網路服務執行，並新增在遠端電腦上佇列的網路服務存取。</span><span class="sxs-lookup"><span data-stu-id="82d44-263">To do this, you must configure the MSMQ activation service to run as a network service, and add network service access to the queue on the remote machine.</span></span>

## <a name="using-custom-msmq-bindings-with-receivecontext-enabled"></a><span data-ttu-id="82d44-264">使用自訂 MSMQ 繫結並啟用 ReceiveContext</span><span class="sxs-lookup"><span data-stu-id="82d44-264">Using Custom MSMQ Bindings with ReceiveContext Enabled</span></span>

<span data-ttu-id="82d44-265">使用自訂 MSMQ 繫結並啟用 <xref:System.ServiceModel.Channels.ReceiveContext> 時，傳入訊息的處理就會使用執行緒集區執行緒，因為原生 MSMQ 不支援非同步 <xref:System.ServiceModel.Channels.ReceiveContext> 接收的 I/O 完成。</span><span class="sxs-lookup"><span data-stu-id="82d44-265">When using a custom MSMQ binding with <xref:System.ServiceModel.Channels.ReceiveContext> enabled processing an incoming message will use a thread pool thread because native MSMQ does not support I/O completion for asynchronous <xref:System.ServiceModel.Channels.ReceiveContext> receives.</span></span> <span data-ttu-id="82d44-266">這是因為處理這類訊息會使用 <xref:System.ServiceModel.Channels.ReceiveContext> 的內部交易，而且 MSMQ 不支援非同步處理。</span><span class="sxs-lookup"><span data-stu-id="82d44-266">This is because processing such a message uses internal transactions for <xref:System.ServiceModel.Channels.ReceiveContext> and MSMQ does not support asynchronous processing.</span></span> <span data-ttu-id="82d44-267">若要解決這個問題，您可以將 <xref:System.ServiceModel.Description.SynchronousReceiveBehavior> 加入至端點，以便強制執行同步處理，或將 <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.MaxPendingReceives%2A> 設定為 1。</span><span class="sxs-lookup"><span data-stu-id="82d44-267">To work around this issue you can add a <xref:System.ServiceModel.Description.SynchronousReceiveBehavior> to the endpoint to force synchronous processing or set <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.MaxPendingReceives%2A> to 1.</span></span>
