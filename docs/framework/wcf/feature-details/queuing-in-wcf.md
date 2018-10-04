---
title: WCF 中的佇列
ms.date: 03/30/2017
ms.assetid: e98d76ba-1acf-42cd-b137-0f8214661112
ms.openlocfilehash: f04055df2c6d4b0a51b36040a5b377bb8738c534
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48266620"
---
# <a name="queuing-in-wcf"></a>WCF 中的佇列
本節說明如何使用 Windows Communication Foundation (WCF) 中的佇列的通訊。  
  
## <a name="queues-as-a-wcf-transport-binding"></a>當做 WCF 傳輸繫結排入佇列  
 在 WCF 中，合約會指定要交換內容。 合約是一種與企業相關或應用程式特定的訊息交換。 繫結中會指定用來交換訊息 (或「如何交換」) 的機制。 在 WCF 中的繫結會封裝訊息交換的詳細資料。 這些繫結會公開組態旋鈕，讓使用者控制繫結所表示之傳輸或通訊協定的各個層面。 WCF 中的佇列會被視為，如同任何其他傳輸繫結，也就是許多佇列應用程式的一大優點。 目前許多佇列應用程式都是透過其他遠端程序呼叫 (RPC) 型的分散式應用程式來撰寫，導致在遵循上和維護上都有難度。 使用 WCF，撰寫分散式應用程式的樣式是不變，讓您更輕鬆地遵循和維護。 另外，藉由根據商務邏輯獨立析出交換機制，您可以更輕鬆地設定傳輸或進行變更，而不會影響應用程式特定的程式碼。 下圖會說明使用 MSMQ 做為傳輸之 WCF 服務和用戶端的結構。  
  
 ![已排入佇列應用程式圖表](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "分散式佇列圖")  
  
 如上圖所示，用戶端和服務只能定義應用程式語意 (Semantics)，也就是合約和實作。 服務會使用偏好的設定來設定佇列繫結， 用戶端會使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)來產生 WCF 用戶端至服務並將產生描述用以將訊息傳送至服務的繫結的組態檔。 因此，為了傳送佇列的訊息，用戶端會具現化 WCF 用戶端，並叫用作業。 使訊息傳送至傳輸佇列並傳輸至目標佇列。 如此一來，傳送和接收訊息的應用程式就可以避開佇列通訊的所有複雜操作。  
  
 在 WCF 中的佇列繫結相關的警告包括：  
  
-   所有服務作業必須為單向，因為預設已排入佇列的 WCF 繫結不支援使用佇列的雙工通訊。 雙向通訊範例 ([雙向通訊](../../../../docs/framework/wcf/samples/two-way-communication.md)) 說明如何實作使用佇列的雙工通訊中使用兩個單向合約。  
  
-   若要產生 WCF 用戶端使用中繼資料交換會需要在服務上的其他 HTTP 端點，以便它來產生 WCF 用戶端，並取得以適當地設定佇列的通訊的繫結資訊可以直接查詢。  
  
-   根據佇列繫結，WCF 之外的額外組態需要。 比方說，<xref:System.ServiceModel.NetMsmqBinding>隨附 WCF 的類別會要求您設定繫結，以及至少要設定訊息佇列 (MSMQ)。  
  
 下列各節描述的特定佇列繫結隨附於 WCF 中，根據 MSMQ。  
  
### <a name="msmq"></a>MSMQ  
 佇列的傳輸只有在 WCF 對其佇列通訊使用 MSMQ。  
  
 MSMQ 是 Windows 隨附的選用元件，而且會以 NT 服務的身分執行。 MSMQ 會擷取傳輸佇列中要進行傳輸的訊息，以及要傳遞至目標佇列的訊息。 MSMQ 佇列管理員會實作可靠訊息傳輸通訊協定，使訊息不會在傳輸期間遺失。 此通訊協定可以是原生通訊協定，或是 SOAP Reliable Message Protocol (SRMP) 這類 SOAP 架構的通訊協定。  
  
 在 MSMQ 中，佇列可以為交易式或非交易式。 交易式佇列可讓您在交易中擷取及傳送訊息，然後永久將訊息儲存在佇列中。 傳送至交易式佇列的訊息只會依序傳輸一次。 您可以使用非交易式佇列來同時傳送變動性 (volatile) 和永久性 (durable) 訊息。 傳送至非交易式佇列的訊息並不保證傳輸可靠，因此便有可能遺失訊息。  
  
 MSMQ 佇列的安全也可以使用向 Active Directory 目錄服務註冊的 Windows 身分識別來保護。 在安裝 MSMQ 時，您可以安裝 Active Directory 整合，而此時電腦必須是 Windows 網域網路的成員。  
  
 如需 MSMQ 的詳細資訊，請參閱[安裝訊息佇列 (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)。  
  
### <a name="netmsmqbinding"></a>NetMsmqBinding  
 [ \<NetMsmqBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)是 WCF 提供兩個的 WCF 端點，以便使用 MSMQ 進行通訊的佇列繫結。 因此，繫結會公開特定用於 MSMQ 的屬性。 不過，在 `NetMsmqBinding` 中不會公開所有 MSMQ 功能和屬性。 精簡型 `NetMsmqBinding` 是使用大多數客戶都認為足夠的最佳功能組來設計。  
  
 `NetMsmqBinding` 闡述了到目前為止以繫結屬性為形式討論的核心佇列概念。 這些屬性接著會向 MSMQ 傳達傳輸及傳送訊息的方式。 下列章節討論屬性分類。 如需詳細資訊，請參閱更完整地描述特定屬性的概念主題。  
  
#### <a name="exactlyonce-and-durable-properties"></a>ExactlyOnce 和 Durable 屬性  
 `ExactlyOnce` 和 `Durable` 屬性會影響在佇列之間傳輸訊息的方式：  
  
-   `ExactlyOnce`：設定為 `true` (預設值) 時，佇列通道會確定傳送的訊息沒有重複， 也會確定沒有遺失訊息。 如果無法傳送訊息，或者在可以傳送訊息之前訊息存留時間到期，就會在寄不出的信件佇列中記錄失敗的訊息和傳送失敗的原因。 設定為 `false` 時，佇列通道會傳輸訊息。 在這個情況下，您可以選擇寄不出的信件佇列。  
  
-   `Durable:` 設定為 `true` (預設值) 時，佇列通道會確定 MSMQ 將訊息永久儲存在磁碟上。 因此，如果停止後重新啟動 MSMQ 服務，磁碟上的訊息就會傳輸至目標佇列或傳遞至服務。 設定為 `false` 時，訊息會儲存在變動性存放區中，而且在停止後重新啟動 MSMQ 服務時會遺失。  
  
 如果是 `ExactlyOnce` 可靠傳輸，MSMQ 則會需要使用交易式佇列， 也需要從交易式佇列讀取交易。 因此，當您使用 `NetMsmqBinding` 時，交易一定會在 `ExactlyOnce` 設定為 `true` 的狀況下傳送或接收訊息。 同樣地，MSMQ 必須使用非交易式佇列才能得到最佳保證，例如當 `ExactlyOnce` 為 `false` 以及用於變動性傳訊時。 因此，將 `ExactlyOnce` 設定為 `false` 或將 durable 設定為 `false` 時，您無法使用交易來進行傳送或接收。  
  
> [!NOTE]
>  您一定要根據繫結中的設定建立正確的佇列 (交易式或非交易式)。 如果 `ExactlyOnce` 為 `true`，請使用交易式佇列，否則請使用非交易式佇列。  
  
#### <a name="dead-letter-queue-properties"></a>寄不出的信件佇列屬性  
 寄不出的信件佇列是用來儲存無法傳遞的訊息。 使用者可以撰寫補償邏輯，用來從寄不出的信件佇列中讀取訊息。  
  
 許多佇列系統都會提供全系統範圍之寄不出的信件佇列。 MSMQ 會對無法傳遞至非交易式佇列的訊息提供全系統範圍的非交易式寄不出的信件佇列，並對無法傳遞至交易式佇列的訊息提供全系統範圍的交易式寄不出的信件佇列。  
  
 如果將訊息傳送至不同目標佇列的用戶端共用 MSMQ 服務，則用戶端傳送的所有訊息都會移至同一個寄不出的信件佇列。 您不一定都要這麼做， 為了加強隔離效果，WCF 和中的 MSMQ[!INCLUDE[wv](../../../../includes/wv-md.md)]提供自訂的寄不出信件佇列 （或應用程式特定之寄不出信件佇列），使用者可以指定儲存無法傳遞的訊息。 因此，不同的用戶端就不會共用同一個寄不出的信件佇列。  
  
 繫結中有兩個重要的屬性：  
  
-   `DeadLetterQueue`：這個屬性是一種列舉，指出是否要求寄不出的信件佇列。 列舉中也包含寄不出的信件佇列種類 (如果有要求的話)。 這些值則為 `None`、`System` 和 `Custom`。 如需有關這些屬性的解釋的詳細資訊，請參閱[使用寄不出信件佇列來處理訊息傳輸失敗](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)  
  
-   `CustomDeadLetterQueue`：這個屬性是應用程式特定之寄不出的信件佇列的統一資源識別碼 (URI) 位址。 這是必要的如果`DeadLetterQueue`。`Custom` 選擇。  
  
#### <a name="poison-message-handling-properties"></a>有害訊息處理屬性  
 當服務在交易中從目標佇列中讀取訊息時，可能會因為各種原因而無法處理訊息。 然後服務會將訊息放回佇列，以便再次讀取。 若要處理重複失敗的訊息，可以在繫結中設定一組有害訊息處理屬性。 有害訊息處理屬性有四個：`ReceiveRetryCount`、`MaxRetryCycles`、`RetryCycleDelay` 和 `ReceiveErrorHandling`。 如需有關這些屬性的詳細資訊，請參閱 <<c0> [ 有害訊息處理](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)。  
  
#### <a name="security-properties"></a>安全性屬性  
 MSMQ 會公開本身的安全性模型，例如佇列上或傳送驗證訊息上的存取控制清單 (ACL)。 `NetMsmqBinding` 會將這些安全性屬性當做部分傳輸安全性設定公開。 在傳輸安全性的繫結中有兩個屬性：`MsmqAuthenticationMode` 和 `MsmqProtectionLevel`。 這些屬性中的設定取決於設定 MSMQ 的方式。 如需詳細資訊，請參閱 <<c0> [ 保護訊息使用傳輸安全性](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)。  
  
 除了傳輸安全性以外，也可以使用訊息安全性來保護實際的 SOAP 訊息本身。 如需詳細資訊，請參閱 <<c0> [ 保護訊息使用訊息安全性](../../../../docs/framework/wcf/feature-details/securing-messages-using-message-security.md)。  
  
 `MsmqTransportSecurity` 也會公開 `MsmqEncryptionAlgorithm` 和 `MsmqHashAlgorithm` 這兩個屬性。 進行訊息的佇列對佇列傳輸加密，以及進行簽章雜湊處理時，可選用這些不同演算法的列舉。  
  
#### <a name="other-properties"></a>其他屬性  
 除了上述屬性，下面也有繫結中公開的其他 MSMQ 特定屬性：  
  
-   `UseSourceJournal`：指出已開啟來源日誌記錄的屬性。 來源日誌記錄是一個 MSMQ 功能，可追蹤已順利從傳輸佇列傳輸的訊息。  
  
-   `UseMsmqTracing`：指出已開啟 MSMQ 追蹤的屬性。 每次裝載 MSMQ 佇列管理員的電腦上有訊息傳入或傳出時，MSMQ 追蹤就會將報告訊息傳送至報告佇列。  
  
-   `QueueTransferProtocol`：用於佇列對佇列訊息傳輸的通訊協定列舉。 MSMQ 會實作原生佇列對佇列傳輸通訊協定，以及稱為 SOAP Reliable Messaging Protocol (SRMP) 的 SOAP 架構通訊協定。 在佇列對佇列傳輸中使用 HTTP 傳輸時，就會使用 SRMP。 在佇列對佇列傳輸中使用 HTTPS 時，則會使用 SRMP。  
  
-   `UseActiveDirectory`：布林值，指出是否必須使用 Active Directory 解析佇列位址。 根據預設，這個屬性為關閉狀態。 如需詳細資訊，請參閱 <<c0> [ 服務端點與佇列定址](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md)。  
  
### <a name="msmqintegrationbinding"></a>MsmqIntegrationBinding  
 `MsmqIntegrationBinding`您想在 C、 c + +、 COM 或 System.Messaging Api 撰寫的現有 MSMQ 應用程式與通訊的 WCF 端點時使用。  
  
 其繫結屬性與 `NetMsmqBinding` 一樣， 但是會有下列差異：  
  
-   `MsmqIntegrationBinding` 的作業合約受限為採用類型為 <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> 的單一參數，其中類型參數為本文類型。  
  
-   許多 MSMQ 原生訊息屬性會在 <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> 中公開以供使用。  
  
-   為了協助序列化和還原序列化訊息本文，XML 和 ActiveX 等序列化程式都會提供讓您使用。  
  
### <a name="sample-code"></a>程式碼範例  
 如需如何撰寫使用 MSMQ 之 WCF 服務的逐步指示，請參閱下列主題：  
  
-   [如何：與 WCF 端點和訊息佇列應用程式交換訊息](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
  
-   [如何：與 WCF 端點交換佇列訊息](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
  
 如需示範在 WCF 中使用 MSMQ 的完整程式碼範例，請參閱下列主題：  
  
-   [異動 MSMQ 繫結](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)  
  
-   [變動性佇列通訊](../../../../docs/framework/wcf/samples/volatile-queued-communication.md)  
  
-   [無效信件佇列](../../../../docs/framework/wcf/samples/dead-letter-queues.md)  
  
-   [工作階段和佇列](../../../../docs/framework/wcf/samples/sessions-and-queues.md)  
  
-   [雙向通訊](../../../../docs/framework/wcf/samples/two-way-communication.md) 
  
-   [SRMP](../../../../docs/framework/wcf/samples/srmp.md)  
  
-   [訊息佇列上的訊息安全性](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)  
  
## <a name="see-also"></a>另請參閱  
 [服務端點與佇列定址](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md)  
 [以 Web 裝載佇列應用程式](../../../../docs/framework/wcf/feature-details/web-hosting-a-queued-application.md)
