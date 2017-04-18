---
title: "佇列訊息的疑難排解 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a5f2836f-018d-42f5-a571-1e97e64ea5b0
caps.latest.revision: 19
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 19
---
# 佇列訊息的疑難排解
本章節包含在 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 中使用佇列之常見問題與疑難排解說明。  
  
## 常見問題  
 **問**：我使用過 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Beta 1，而且有安裝 MSMQ Hotfix。我是否需要移除這個 Hotfix？  
  
 **答**：是的。不再支援這個 Hotfix。現在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 可以執行 MSMQ 而不需要 Hotfix。  
  
 **問**：MSMQ 有兩個繫結 <xref:System.ServiceModel.NetMsmqBinding> 和 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>。我應該在什麼狀況下使用它們？  
  
 **答**：當您要使用 MSMQ 做為兩個 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式之間佇列通訊的傳輸方式時，請使用 <xref:System.ServiceModel.NetMsmqBinding>。當您要使用現有的 MSMQ 應用程式與新的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式通訊時，請使用 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>。  
  
 **問**：我是否需要升級 MSMQ 才能使用 <xref:System.ServiceModel.NetMsmqBinding> 和 `MsmqIntegration` 繫結？  
  
 **答**：不用。兩種繫結都可以配合 [!INCLUDE[wxp](../../../../includes/wxp-md.md)] 和 [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 上的 MSMQ 3.0 使用。這些繫結中的特定功能要等到您使用 [!INCLUDE[wv](../../../../includes/wv-md.md)] 升級至 MSMQ 4.0 時才可使用。  
  
 **問**：<xref:System.ServiceModel.NetMsmqBinding> 和 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> 繫結中的哪些功能只能在 MSMQ 4.0 中使用，而不能在 MSMQ 3.0 中使用？  
  
 **答**：下列功能可以在 MSMQ 4.0 中使用，但是不能在 MSMQ 3.0 中使用：  
  
-   只有 MSMQ 4.0 支援自訂的寄不出的信件佇列。  
  
-   MSMQ 3.0 和 4.0 以不同的方式處理有害訊息。  
  
-   只有 MSMQ 4.0 支援遠端交易讀取。  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Windows Vista、Windows Server 2003 和 Windows XP 之間的佇列功能差異](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md).  
  
 **問**：我是否能在佇列通訊的一端使用 MSMQ 3.0，而在另一端使用 MSMQ 4.0？  
  
 **答**：是的。  
  
 **問**：我要整合現有的 MSMQ 應用程式與新的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端或伺服器。我是否需要為 MSMQ 基礎結構的兩端同時升級？  
  
 **答**：不用。您不需要將任何一端升級至 MSMQ 4.0。  
  
## 疑難排解  
 本章節包含最常見疑難排解問題的解答。屬於已知限制的問題也會在版本資訊中加以說明。  
  
 **問**：我在嘗試使用私用佇列時收到下列例外狀況：`System.InvalidOperationException`：URL 無效。佇列的 URL 不可包含 '$' 字元。請使用 net.msmq:\/\/machine\/private\/queueName 中的語法，來定址私用佇列。  
  
 **答**：請檢查組態和程式碼中的佇列統一資源識別項 \(URI\)。請勿在 URI 中使用 "$" 字元。例如，若要定址名為 OrdersQueue 的私用佇列，請將 URI 指定為 net.msmq:\/\/localhost\/private\/ordersQueue。  
  
 **問**：在佇列的應用程式上呼叫 `ServiceHost.Open()` 會擲回下列例外狀況：`System.ArgumentException`：起始位址不得包含 URI 查詢字串。為什麼？  
  
 **答**：請檢查組態檔和程式碼中的佇列 URI。雖然 MSMQ 佇列支援使用 '?' 字元，但 URI 會將這個字元解譯為字串查詢的開頭。為了避免這個問題，請使用不含 '?' 字元的佇列名稱。  
  
 **問**：我的傳送已經成功，但是接收者上卻沒有叫用任何服務作業。為什麼？  
  
 **答**：若要判斷答案，請逐一進行下列檢查清單：  
  
-   檢查交易式佇列需求是否相容於指定的保證。請注意下列準則：  
  
    -   您只能將具有「正好一次」保證 \(<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> \= `true`\) 的永久性訊息 \(資料包和工作階段\) 傳送到交易式佇列。  
  
    -   您只能傳送具有「正好一次」保證的工作階段。  
  
    -   從交易式佇列接收工作階段中的訊息時需要進行交易。  
  
    -   對於非交易式的佇列，您只能傳送或接收不具保證 \(<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> \= `false`\) 的變動性或永久性訊息 \(僅限資料包\)。  
  
-   檢查寄不出的信件佇列。如果您在其中找到訊息，請判斷它們為何沒有傳遞。  
  
-   檢查傳出佇列是否有連接或定址問題。  
  
 **問**：我有指定自訂的寄不出的信件佇列，不過當我啟動寄件者應用程式時，卻收到例外狀況，表示找不到寄不出的信件佇列，或是傳送應用程式沒有寄不出的信件佇列的權限。為什麼會發生這種問題？  
  
 **答**：自訂的寄不出的信件佇列 URI，其第一個區段中必須包含 "localhost" 或是電腦名稱。例如，net.msmq:\/\/localhost\/private\/myAppdead\-letter 佇列。  
  
 **問**：我是否一定要定義自訂的寄不出的信件佇列，或是否有預設的寄不出的信件佇列？  
  
 **答**：如果保證是「正好一次」\(<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> \= `true`\)，而且如果您沒有指定自訂的寄不出的信件佇列，預設值便會是整個系統交易式寄不出的信件佇列。  
  
 如果沒有保證 \(<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> \= `false`\)，預設值就會是沒有寄不出的信件佇列功能。  
  
 **問**：我的服務在 SvcHost.Open 時擲回例外狀況，當時訊息為「ListenerFactory 無法符合 EndpointListener 需求」。為什麼？  
  
 答：請檢查您的服務合約。您可能忘記在所有的服務作業中設定 “IsOneWay\=`true`”。佇列只會支援單向服務作業。  
  
 **問**：佇列中有訊息，但是沒有叫用服務作業。問題出在哪裡？  
  
 **答**：判斷您的服務主機是否出錯。您可以查看追蹤，或是實作 `IErrorHandler` 以檢查這點。根據預設，如果偵測到有害訊息，便會發生服務主機錯誤。  
  
 **問**：佇列中有訊息，但是我的 Web 裝載的佇列服務卻沒有啟動。為什麼？  
  
 **答**：最常見的原因是權限。  
  
1.  請確定 `NetMsmqActivator` 處理序正在執行，而且 `NetMsmqActivator` 處理序的身分識別已授與在佇列上讀取和搜尋的權限。  
  
2.  如果 `NetMsmqActivator` 正在監視遠端電腦上的佇列，請確定 `NetMsmqActivator` 不是以受限制的權杖執行。若要以不受限制的權杖執行 `NetMsmqActivator`：  
  
    ```  
    sc sidtype NetMsmqActivator unrestricted  
    ```  
  
 如需了解非安全性相關的 Web 主機問題，請參閱：[以 Web 裝載佇列應用程式](../../../../docs/framework/wcf/feature-details/web-hosting-a-queued-application.md)。  
  
 **問**：怎樣才能最輕鬆地存取工作階段？  
  
 **答**：在對應於工作階段中最後一個訊息的作業上，設定 AutoComplete\=`true`，並在所有剩餘的服務作業上設定 AutoComplete\=`false`。  
  
 **問**：我可以從何處找到關於 MSMQ 常見問題的答案？  
  
 **答**：[!INCLUDE[crabout](../../../../includes/crabout-md.md)] MSMQ 的詳細資訊，請參閱 [Microsoft Message Queuing](http://go.microsoft.com/fwlink/?LinkId=87810) \(本頁面可能為英文\)。  
  
 **問**：為何從同時包含佇列工作階段訊息與佇列資料包訊息的佇列讀取時，我的服務會擲回 `ProtocolException`？  
  
 **答**：佇列工作階段訊息與佇列資料包訊息的組成方式有基本上的差異。因此，預期要讀取佇列工作階段訊息的服務無法接收佇列資料包訊息，而預期要讀取佇列資料包訊息的服務無法接收工作階段訊息。嘗試從相同佇列同時讀取這兩種訊息類型時，便會擲回下列例外狀況：  
  
```  
System.ServiceModel.MsmqPoisonMessageException: The transport channel detected a poison message. This occurred because the message exceeded the maximum number of delivery attempts or because the channel detected a fundamental problem with the message. The inner exception may contain additional information.   
---> System.ServiceModel.ProtocolException: An incoming MSMQ message contained invalid or unexpected .NET Message Framing information in its body. The message cannot be received. Ensure that the sender is using a compatible service contract with a matching SessionMode.  
```  
  
 當應用程式從相同的電腦同時傳送佇列工作階段訊息和佇列資料包訊息時，系統的寄不出的信件佇列以及自訂的寄不出的信件佇列特別容易受到這個問題影響。無法成功傳送的訊息會移到寄不出的信件佇列中。在這些狀況下，寄不出的信件佇列中可能會同時有工作階段訊息和資料包訊息。在執行階段從佇列讀取時，沒有任何方法可以分開這兩種訊息，因此，應用程式不應該從相同的電腦同時傳送佇列工作階段訊息和佇列資料包訊息。  
  
### MSMQ 整合：特定疑難排解  
 **問**：當我傳送訊息時或是開啟服務主機時，發生了表示配置錯誤的錯誤。為什麼？  
  
 **答**：當使用 MSMQ 整合繫結時，您必須使用 msmq.formatname 配置。例如，msmq.formatname:DIRECT\=OS:.\\private$\\OrdersQueue。不過當指定自訂的寄不出的信件佇列時，您必須使用 net.msmq 配置。  
  
 **問**：當我在 [!INCLUDE[wv](../../../../includes/wv-md.md)] 上使用公用或私用格式名稱並開啟服務主機時，發生了一個錯誤。為什麼？  
  
 **答**：[!INCLUDE[wv](../../../../includes/wv-md.md)] 上的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 整合通道會檢查是否能為主應用程式佇列開啟子佇列來處理有害訊息。子佇列的名稱衍生自傳遞至接聽項的 msmq.formatname URI。但是 MSMQ 中的子佇列名稱只能是直接格式名稱。所以您會看到錯誤。請將佇列 URI 變更為直接格式名稱。  
  
 **問**：當從 MSMQ 應用程式接收訊息時，訊息停在佇列中，而且未由接收的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式加以讀取。為什麼？  
  
 **答**：請檢查訊息是否具有本文。如果訊息沒有本文，MSMQ 整合通道便會忽略該訊息。實作 `IErrorHandler`，即可獲得例外狀況的通知和檢查追蹤。  
  
### 安全性相關疑難排解  
 **問**：當我執行在工作群組模式中使用預設繫結的範例時，訊息似乎有傳送，卻始終沒有被接收者接收。  
  
 **答**：根據預設，訊息會使用需要 Active Directory 目錄服務的 MSMQ 內部憑證來進行簽署。由於工作群組模式中並沒有提供 Active Directory，因此簽署訊息會失敗。這樣一來，訊息會落入寄不出的信件佇列，而且會指示造成失敗的原因，例如「簽章不正確」。  
  
 解決方法是關閉安全性。藉由設定 <xref:System.ServiceModel.NetMsmqSecurity.Mode%2A> \= <xref:System.ServiceModel.NetMsmqSecurityMode>，讓它在工作群組模式下運作，即可做到這點。  
  
 另一個解決方法是從 <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A> 屬性取得 <xref:System.ServiceModel.MsmqTransportSecurity>，並將其設定為 <xref:System.ServiceModel.MsmqAuthenticationMode>，並設定用戶端憑證。  
  
 而另外一種解決方法是搭配 Active Directory 整合來安裝 MSMQ。  
  
 **問**：當我以預設繫結 \(傳輸安全性已啟用\) 在 Active Directory 中將訊息傳送到佇列時，我收到「找不到內部憑證」訊息。我要如何修正此問題？  
  
 **答**：這個訊息表示傳送者在 Active Directory 中的憑證必須進行更新。若要做到這點，請依序開啟 \[**控制台**\]、\[**系統管理工具**\]、\[**電腦管理**\]，接著以滑鼠右鍵按一下 \[**MSMQ**\] 並選取 \[**內容**\]。選取 \[**使用者憑證**\] 索引標籤，並按一下 \[**更新**\] 按鈕。  
  
 **問**：當我使用 <xref:System.ServiceModel.MsmqAuthenticationMode> 傳送訊息以及指定要使用的憑證時，我收到「無效的憑證」訊息。我要如何修正此問題？  
  
 **答**：您無法在憑證模式下使用本機電腦憑證存放區。您必須使用憑證嵌入式管理單元，將憑證從電腦憑證存放區複製到目前使用者存放區。若要取得憑證嵌入式管理單元：  
  
1.  依序按一下 \[**開始**\]、\[**執行**\]，然後輸入 `mmc`，接著按一下 \[**確定**\]。  
  
2.  在 \[**Microsoft 管理主控台**\] 中，開啟 \[**檔案**\] 功能表，然後選取 \[**新增\/移除嵌入式管理單元**\]。  
  
3.  在 \[**新增\/移除嵌入式管理單元**\] 對話方塊中，按一下 \[**新增**\] 按鈕。  
  
4.  在 \[**新增獨立嵌入式管理單元**\] 對話方塊中，選取憑證嵌入式管理單元，並按一下 \[**新增**\]。  
  
5.  在 \[**憑證**\] 嵌入式管理單元對話方塊中，選取 \[**我的使用者帳戶**\]，並按一下 \[**完成**\]。  
  
6.  接下來，使用先前步驟來新增第二個憑證嵌入式管理單元，不過這次要選取 \[**電腦帳戶**\]，然後按 \[**下一步**\]。  
  
7.  選取 \[**本機電腦**\] 並按一下 \[**完成**\]。現在，您可以從電腦憑證存放區將憑證拖放到目前使用者存放區。  
  
 **問**：當我的服務在工作群組模式中從另一部電腦上的佇列讀取時，發生「拒絕存取」例外狀況。  
  
 **答**：在工作群組模式中，若要讓遠端應用程式獲得佇列的存取，該應用程式必須具有存取佇列的權限。請將 “Anonymous login” \(匿名登入\) 新增到佇列的存取控制清單 \(ACL\)，以便授與應用程式讀取權限。  
  
 **問**：當網路服務用戶端 \(或是任何沒有網域帳戶的用戶端\) 傳送佇列訊息時，傳送因為無效的憑證而失敗。我要如何修正此問題？  
  
 **答**：請檢查繫結組態。預設繫結會開啟 MSMQ 傳輸安全性以簽署訊息。請關閉此選項。  
  
### 遠端交易接收  
 **問**：我在電腦 A 上設有佇列，而且有一個會從電腦 B 上的佇列讀取訊息的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務 \(遠端交易接收案例\)，但是無法從佇列讀取訊息。追蹤資訊以「無法匯入指定的交易」訊息表示接收失敗。我該如何修正此問題？  
  
 **答**：造成這個問題有三個可能原因：  
  
-   如果您是在網域模式中，遠端交易接收便需要 Microsoft Distributed Transaction Coordinator \(MSDTC\) 網路存取。您可以使用 \[**新增\/移除元件**\] 來啟用這個選項。  
  
     ![啟用網路 DTC 存取](../../../../docs/framework/wcf/feature-details/media/applicationserveraddcomps.jpg "ApplicationServerAddComps")  
  
-   檢查與交易管理員進行通訊的驗證模式。如果是在工作群組模式中，您就必須選取 \[不需要驗證\]。如果是在網域模式中，您就必須選取 \[要求相互驗證\]。  
  
     ![啟用 XA 異動](../../../../docs/framework/wcf/feature-details/media/4f3695e0-fb0b-4c5b-afac-75f8860d2bb0.jpg "4f3695e0\-fb0b\-4c5b\-afac\-75f8860d2bb0")  
  
-   確定 MSDTC 有出現在 \[**網際網路連線防火牆**\] 設定的例外清單中。  
  
-   確定您是使用 [!INCLUDE[wv](../../../../includes/wv-md.md)]。[!INCLUDE[wv](../../../../includes/wv-md.md)] 上的 MSMQ 支援遠端交易讀取。在舊版 Window 中的 MSMQ 並不支援遠端交易讀取。  
  
 **問**：如果從佇列進行讀取的服務是網路服務 \(例如，使用 Web 主機\)，為什麼我會收到在從佇列讀取時所引發的拒絕存取例外狀況？  
  
 **答**：網路服務讀取權限必須加入至佇列 ACL 中，才能確保網路服務可以從佇列讀取。  
  
 **問**：我是否能根據遠端電腦佇列中的訊息，使用 MSMQ 啟動服務來啟動應用程式？  
  
 **答**：是的。若要這樣做，您必須將 MSMQ 啟動服務設定成當做網路服務執行，並新增在遠端電腦上佇列的網路服務存取。  
  
## 使用自訂 MSMQ 繫結並啟用 ReceiveContext  
 使用自訂 MSMQ 繫結並啟用 <xref:System.ServiceModel.Channels.ReceiveContext> 時，傳入訊息的處理就會使用執行緒集區執行緒，因為原生 MSMQ 不支援非同步 <xref:System.ServiceModel.Channels.ReceiveContext> 接收的 I\/O 完成。這是因為處理這類訊息會使用 <xref:System.ServiceModel.Channels.ReceiveContext> 的內部交易，而且 MSMQ 不支援非同步處理。若要解決這個問題，您可以將 <xref:System.ServiceModel.Description.SynchronousReceiveBehavior> 加入至端點，以便強制執行同步處理，或將 <xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.MaxPendingReceives%2A> 設定為 1。