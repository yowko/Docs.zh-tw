---
title: 佇列訊息的疑難排解
ms.date: 03/30/2017
ms.assetid: a5f2836f-018d-42f5-a571-1e97e64ea5b0
ms.openlocfilehash: ed114cc9a37fff549e8bfc874765252fd18893a9
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345583"
---
# <a name="troubleshooting-queued-messaging"></a>佇列訊息的疑難排解

本節包含在 Windows Communication Foundation （WCF）中使用佇列的常見問題和疑難排解說明。

## <a name="common-questions"></a>常見問題

**問：** 我使用了 WCF Beta 1，而我安裝了 MSMQ 的修補程式。 我是否需要移除這個 Hotfix？

**答：** 可以。 不再支援這個 Hotfix。 WCF 現在可以在沒有修補程式需求的 MSMQ 上運作。

**問：** MSMQ 有兩個系結： <xref:System.ServiceModel.NetMsmqBinding> 和 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>。 我應該在什麼狀況下使用它們？

**答：** 當您想要使用 MSMQ 做為兩個 WCF 應用程式之間佇列通訊的傳輸時，請使用 <xref:System.ServiceModel.NetMsmqBinding>。 當您想要使用現有的 MSMQ 應用程式與新的 WCF 應用程式通訊時，請使用 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>。

**問：** 我必須升級 MSMQ 才能使用 <xref:System.ServiceModel.NetMsmqBinding> 和 `MsmqIntegration` 系結嗎？

**答：** 否。 這兩個系結都適用于 [!INCLUDE[wxp](../../../../includes/wxp-md.md)] 和 Windows Server 2003 上的 MSMQ 3.0。 當您升級至 Windows Vista 中的 MSMQ 4.0 時，系結的某些功能就會變成可用。

**問：** <xref:System.ServiceModel.NetMsmqBinding> 和 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> 系結的哪些功能可在 MSMQ 4.0 中使用，但不在 MSMQ 3.0 中？

**答：** 下列功能可在 MSMQ 4.0 中取得，但無法在 MSMQ 3.0 中使用：

- 只有 MSMQ 4.0 支援自訂的寄不出的信件佇列。

- MSMQ 3.0 和 4.0 以不同的方式處理有害訊息。

- 只有 MSMQ 4.0 支援遠端交易讀取。

如需詳細資訊，請參閱[Windows Vista、Windows Server 2003 和 WINDOWS XP 中的佇列功能差異](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)。

**問：** 我可以在佇列通訊的一端使用 MSMQ 3.0，而在另一端使用 MSMQ 4.0 嗎？

**答：** 可以。

**問：** 我想要將現有的 MSMQ 應用程式與新的 WCF 用戶端或伺服器整合。 我是否需要為 MSMQ 基礎結構的兩端同時升級？

**答：** 否。 您不需要將任何一端升級至 MSMQ 4.0。

## <a name="troubleshooting"></a>疑難排解

本章節包含最常見疑難排解問題的解答。 屬於已知限制的問題也會在版本資訊中加以說明。

**問：** 我嘗試使用私用佇列，但收到下列例外狀況： `System.InvalidOperationException`： URL 無效。 佇列的 URL 不可包含 '$' 字元。 請使用 net.msmq://machine/private/queueName 中的語法，來定址私用佇列。

**答：** 請檢查您設定和程式碼中的佇列統一資源識別項（URI）。 請勿在 URI 中使用 "$" 字元。 例如，若要定址名為 OrdersQueue 的私用佇列，請將 URI 指定為 net.msmq://localhost/private/ordersQueue。

**問：** 在佇列應用程式上呼叫 `ServiceHost.Open()` 會擲回下列例外狀況： `System.ArgumentException`：基底位址不能包含 URI 查詢字串。 為什麼？

**答：** 檢查您的設定檔和程式碼中的佇列 URI。 雖然 MSMQ 佇列支援使用 '?' 字元，但 URI 會將這個字元解譯為字串查詢的開頭。 為了避免這個問題，請使用不含 '?' 字元的佇列名稱。

**問：** 我的傳送成功，但在接收者上未叫用服務作業。 為什麼？

**答：** 若要判斷答案，請完成下列檢查清單：

- 檢查異動式佇列需求是否相容於指定的保證。 請注意下列準則：

  - 您只能將具有「正好一次」保證（<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `true`）的永久性訊息（資料包和會話）傳送至交易式佇列。

  - 您只能傳送具有「正好一次」保證的工作階段。

  - 從異動式佇列接收工作階段中的訊息時需要進行異動。

  - 您只能傳送或接收非交易式佇列的 volatile 或永久性訊息（僅限資料包），而不保證（<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `false`）。

- 檢查寄不出的信件佇列。 如果您在其中找到訊息，請判斷它們為何沒有傳遞。

- 檢查傳出佇列是否有連接或定址問題。

**問：** 我已經指定自訂的寄不出的信件佇列，但是當我啟動傳送者應用程式時，收到的例外狀況是找不到寄不出的信件佇列，或是傳送應用程式沒有寄不出的信件佇列的許可權。 為什麼會發生這種問題？

**答：** 自訂寄不出的信件佇列 URI 必須在第一個區段中包含 "localhost" 或電腦名稱稱，例如 net.tcp：//localhost/private/myAppdead-letter queue。

**問：** 是否一律需要定義自訂的寄不出的信件佇列，或是否有預設的寄不出的信件佇列？

**答：** 如果保證是「正好一次」（<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `true`），而且如果您沒有指定自訂的寄不出的信件佇列，預設值就是全系統的交易式寄不出的信件佇列。

如果保證為 none （<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `false`），則預設為沒有寄不出的信件佇列功能。

**問：** 我的服務在 SvcHost 上擲回。請開啟並顯示「ListenerFactory 無法符合 EndpointListener 需求」訊息。 為什麼？

答： 請檢查您的服務合約。 您可能忘了將 "IsOneWay =`true`" 放在所有服務作業上。 佇列只會支援單向服務作業。

**問：** 佇列中有訊息，但未叫用服務作業。 問題出在哪裡？

**答：** 判斷您的服務主機是否發生錯誤。 您可以查看追蹤，或是實作 `IErrorHandler` 以檢查這點。 根據預設，如果偵測到有害訊息，便會發生服務主機錯誤。

**問：** 佇列中有訊息，但我的 Web 主控佇列服務並未啟動。 為什麼？

**答：** 最常見的原因是許可權。

1. 請確定 `NetMsmqActivator` 處理序正在執行，而且 `NetMsmqActivator` 處理序的身分識別已授與在佇列上讀取和搜尋的權限。

2. 如果 `NetMsmqActivator` 正在監視遠端電腦上的佇列，請確定 `NetMsmqActivator` 不是以受限制的權杖執行。 若要以不受限制的權杖執行 `NetMsmqActivator`：

    ```console
    sc sidtype NetMsmqActivator unrestricted
    ```

如需與非安全性相關的 Web 主機問題，請參閱： [Web 裝載佇列的應用程式](../../../../docs/framework/wcf/feature-details/web-hosting-a-queued-application.md)。

**問：** 存取會話最簡單的方式是什麼？

**答：** 在對應至會話中最後一則訊息的作業上設定 [自動完成] =`true`，然後在所有剩餘的服務作業上設定 [自動完成] = [`false`]。

**問：** 哪裡可以找到有關 MSMQ 常見問題的解答？

**答：** 如需 MSMQ 的詳細資訊，請參閱[Microsoft Message Queuing](https://go.microsoft.com/fwlink/?LinkId=87810)。

**問：** 為什麼當我從包含佇列會話訊息和佇列資料包訊息的佇列讀取時，我的服務會擲回 `ProtocolException`？

**答：** 佇列會話訊息和佇列資料包訊息的組成方式有基本差異。 因此，預期要讀取佇列工作階段訊息的服務無法接收佇列資料包訊息，而預期要讀取佇列資料包訊息的服務無法接收工作階段訊息。 嘗試從相同佇列同時讀取這兩種訊息類型時，便會擲回下列例外狀況：

```console
System.ServiceModel.MsmqPoisonMessageException: The transport channel detected a poison message. This occurred because the message exceeded the maximum number of delivery attempts or because the channel detected a fundamental problem with the message. The inner exception may contain additional information.
---> System.ServiceModel.ProtocolException: An incoming MSMQ message contained invalid or unexpected .NET Message Framing information in its body. The message cannot be received. Ensure that the sender is using a compatible service contract with a matching SessionMode.
```

當應用程式從相同的電腦同時傳送佇列工作階段訊息和佇列資料包訊息時，系統的寄不出的信件佇列以及自訂的寄不出的信件佇列特別容易受到這個問題影響。 無法成功傳送的訊息會移到寄不出的信件佇列中。 在這些狀況下，寄不出的信件佇列中可能會同時有工作階段訊息和資料包訊息。 在執行階段從佇列讀取時，沒有任何方法可以分開這兩種訊息，因此，應用程式不應該從相同的電腦同時傳送佇列工作階段訊息和佇列資料包訊息。

### <a name="msmq-integration-specific-troubleshooting"></a>MSMQ 整合：特定疑難排解

**問：** 當我傳送訊息時，或當我開啟服務主機時，會收到指出配置錯誤的錯誤。 為什麼？

**答：** 當您使用 MSMQ 整合系結時，您必須使用 msmq.formatname 配置。 例如，msmq.formatname:DIRECT=OS:.\private$\OrdersQueue。 不過當指定自訂的寄不出的信件佇列時，您必須使用 net.msmq 配置。

**問：** 當我使用公用或私用格式名稱，並在 Windows Vista 上開啟服務主機時，會收到錯誤。 為什麼？

**答：** Windows Vista 上的 WCF 整合通道會檢查是否可以開啟主要應用程式佇列的子佇列來處理有害訊息。 子佇列的名稱衍生自傳遞至接聽項的 msmq.formatname URI。 但是 MSMQ 中的子佇列名稱只能是直接格式名稱。 所以您會看到錯誤。 請將佇列 URI 變更為直接格式名稱。

**問：** 從 MSMQ 應用程式接收訊息時，訊息位於佇列中，而且不會由接收 WCF 應用程式讀取。 為什麼？

**答：** 請檢查訊息是否有主體。 如果訊息沒有本文，MSMQ 整合通道便會忽略該訊息。 實作 `IErrorHandler`，即可獲得例外狀況的通知和檢查追蹤。

### <a name="security-related-troubleshooting"></a>安全性相關疑難排解

**問：** 當我執行在工作組模式中使用預設系結的範例時，訊息似乎會被傳送，但收件者永遠不會收到。

**答：** 根據預設，會使用需要 Active Directory 目錄服務的 MSMQ 內部憑證來簽署訊息。 由於工作群組模式中並沒有提供 Active Directory，因此簽署訊息會失敗。 因此，訊息會放在寄不出的信件佇列中，而且會指出失敗的原因，例如「錯誤的簽章」。

解決方法是關閉安全性。 這是藉由設定 <xref:System.ServiceModel.NetMsmqSecurity.Mode%2A> = <xref:System.ServiceModel.NetMsmqSecurityMode.None>，使其在工作組模式中正常執行。

另一個解決方法是從 <xref:System.ServiceModel.MsmqTransportSecurity> 屬性取得 <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>，並將其設定為 <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate>，並設定用戶端憑證。

而另外一種解決方法是搭配 Active Directory 整合來安裝 MSMQ。

**問：** 當我在 Active Directory 佇列中傳送具有預設系結（傳輸安全性）的訊息時，會收到「找不到內部憑證」訊息。 如何修正這個問題？

**答：** 這表示必須更新寄件者 Active Directory 中的憑證。 若要這麼做，請開啟 **控制台**、系統**管理工具**、**電腦管理**、以滑鼠右鍵按一下  **MSMQ**，**然後選取** 選取 [**使用者憑證**] 索引標籤，然後按一下 [**更新**] 按鈕。

**問：** 當我使用 <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate> 傳送訊息，並指定要使用的憑證時，我收到「不正確憑證」訊息。 如何修正這個問題？

**答：** 您不能使用具有憑證模式的本機電腦憑證存放區。 您必須使用憑證嵌入式管理單元，將憑證從電腦憑證存放區複製到目前使用者存放區。 若要取得憑證嵌入式管理單元：

1. 按一下 [**開始**]，選取 [**執行**]，輸入 `mmc`，然後按一下 **[確定]** 。

2. 在**Microsoft Management Console**中，開啟 [檔案 **] 功能表，** 然後選取 [**新增/移除嵌入式管理單元**]。

3. 在 [**新增/移除嵌入式管理單元**] 對話方塊中，按一下 [**新增**] 按鈕。

4. 在 [**新增獨立嵌入式管理單元**] 對話方塊中，選取 [憑證]，然後按一下 [**新增**]。

5. 在 [**憑證**嵌入式管理單元] 對話方塊中，選取 [**我的使用者帳戶]，** 然後按一下 **[完成]** 。

6. 接下來，使用先前的步驟新增第二個憑證嵌入式管理單元，但這次請選取 [**電腦帳戶**]，然後按 **[下一步]** 。

7. 選取 [本機電腦]，再按一下 [完成]。 現在，您可以從電腦憑證存放區將憑證拖放到目前使用者存放區。

**問：** 當我的服務在工作組模式中從另一部電腦上的佇列讀取時，出現「拒絕存取」例外狀況。

**答：** 在工作組模式中，若要讓遠端應用程式取得佇列的存取權，應用程式必須具有存取佇列的許可權。 將「匿名登入」新增至佇列的存取控制清單（ACL），並授與讀取權限。

**問：** 當網路服務用戶端（或任何不含網域帳戶的用戶端）傳送佇列訊息時，傳送會因為憑證無效而失敗。 如何修正這個問題？

**答：** 檢查系結設定。 預設繫結會開啟 MSMQ 傳輸安全性以簽署訊息。 請關閉此選項。

### <a name="remote-transacted-receives"></a>遠端交易接收

**問：** 當我在電腦 A 上有佇列，而 WCF 服務從電腦 B 上的佇列讀取訊息時（遠端交易接收案例），則不會從佇列讀取訊息。 追蹤資訊表示接收失敗，訊息為「無法匯入交易」。 可以做什麼來修正這個問題？

**答：** 有三個可能的原因：

- 如果您是在網域模式中，遠端交易接收便需要 Microsoft Distributed Transaction Coordinator (MSDTC) 網路存取。 您可以使用 [**新增/移除元件**] 來啟用此。

  ![顯示啟用網路 DTC 存取的螢幕擷取畫面。](./media/troubleshooting-queued-messaging/enable-distributed-transaction-coordinator-access.jpg)

- 檢查與交易管理員進行通訊的驗證模式。 如果您是在工作組模式中，則必須選取 [不需要驗證]。 如果您是在網域模式中，則必須選取 [需要相互驗證]。

  ![啟用 XA 交易](../../../../docs/framework/wcf/feature-details/media/4f3695e0-fb0b-4c5b-afac-75f8860d2bb0.jpg "4f3695e0-fb0b-4c5b-afac-75f8860d2bb0")

- 請確定 MSDTC 位於**網際網路連線防火牆**設定的例外清單中。

- 請確定您使用的是 Windows Vista。 Windows Vista 上的 MSMQ 支援遠端交易讀取。 在舊版 Window 中的 MSMQ 並不支援遠端交易讀取。

**問：** 當從佇列讀取的服務是網路服務（例如，在 Web 主機中）時，為何會在讀取佇列時引發拒絕存取的例外狀況？

**答：** 必須將網路服務讀取權限新增至佇列 ACL，以確保網路服務可以從佇列讀取。

**問：** 我是否可以使用 MSMQ 啟用服務，根據遠端電腦上佇列中的訊息來啟動應用程式？

**答：** 可以。 若要這樣做，您必須將 MSMQ 啟動服務設定成當做網路服務執行，並新增在遠端電腦上佇列的網路服務存取。

## <a name="using-custom-msmq-bindings-with-receivecontext-enabled"></a>使用自訂 MSMQ 繫結並啟用 ReceiveContext

使用自訂 MSMQ 繫結並啟用 <xref:System.ServiceModel.Channels.ReceiveContext> 時，傳入訊息的處理就會使用執行緒集區執行緒，因為原生 MSMQ 不支援非同步 <xref:System.ServiceModel.Channels.ReceiveContext> 接收的 I/O 完成。 這是因為處理這類訊息會使用 <xref:System.ServiceModel.Channels.ReceiveContext> 的內部交易，而且 MSMQ 不支援非同步處理。 若要解決這個問題，您可以將 <xref:System.ServiceModel.Description.SynchronousReceiveBehavior> 加入至端點，以便強制執行同步處理，或將 <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.MaxPendingReceives%2A> 設定為 1。
