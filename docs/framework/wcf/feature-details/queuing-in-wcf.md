---
title: WCF 中的佇列
ms.date: 03/30/2017
ms.assetid: e98d76ba-1acf-42cd-b137-0f8214661112
ms.openlocfilehash: 27c92b0f728b909de16a059485a38ff7fb0fb765
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913382"
---
# <a name="queuing-in-wcf"></a>WCF 中的佇列
本節說明如何使用 Windows Communication Foundation (WCF) 中的佇列通訊。  
  
## <a name="queues-as-a-wcf-transport-binding"></a>當做 WCF 傳輸繫結排入佇列  
 在 WCF 中, 合約會指定要交換的內容。 合約是一種與企業相關或應用程式特定的訊息交換。 繫結中會指定用來交換訊息 (或「如何交換」) 的機制。 WCF 中的系結會封裝訊息交換的詳細資料。 這些繫結會公開組態旋鈕，讓使用者控制繫結所表示之傳輸或通訊協定的各個層面。 WCF 中的佇列處理方式就像任何其他傳輸系結一樣, 對於許多佇列應用程式來說, 這是一個很大的優點。 目前許多佇列應用程式都是透過其他遠端程序呼叫 (RPC) 型的分散式應用程式來撰寫，導致在遵循上和維護上都有難度。 使用 WCF 時, 撰寫分散式應用程式的樣式也是相同的, 讓您更容易遵循和維護。 另外，藉由根據商務邏輯獨立析出交換機制，您可以更輕鬆地設定傳輸或進行變更，而不會影響應用程式特定的程式碼。 下圖會說明使用 MSMQ 做為傳輸之 WCF 服務和用戶端的結構。  
  
 ![排入佇列的應用程式圖表](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "分散式-佇列-圖表")  
  
 如上圖所示，用戶端和服務只能定義應用程式語意 (Semantics)，也就是合約和實作。 服務會使用偏好的設定來設定佇列繫結， 用戶端會使用[System.servicemodel 中繼資料公用程式工具 (Svcutil)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)來產生 WCF 用戶端至服務, 並產生描述用來將訊息傳送至服務之系結的設定檔。 因此, 若要傳送佇列訊息, 用戶端會具現化 WCF 用戶端, 並對其叫用作業。 使訊息傳送至傳輸佇列並傳輸至目標佇列。 如此一來，傳送和接收訊息的應用程式就可以避開佇列通訊的所有複雜操作。  
  
 WCF 中佇列系結的相關注意事項包括:  
  
- 所有服務作業都必須是單向的, 因為 WCF 中的預設佇列系結不支援使用佇列的雙工通訊。 雙向通訊範例 ([雙向通訊](../../../../docs/framework/wcf/samples/two-way-communication.md)) 說明如何使用 2 1 向合約來執行使用佇列的雙工通訊。  
  
- 若要使用中繼資料交換產生 WCF 用戶端, 必須在服務上有額外的 HTTP 端點, 以便直接查詢它以產生 WCF 用戶端, 並取得系結資訊以適當地設定佇列通訊。  
  
- 根據佇列的系結, 需要 WCF 以外的額外設定。 例如, 隨附于<xref:System.ServiceModel.NetMsmqBinding> WCF 的類別會要求您設定系結, 以及至少設定訊息佇列 (MSMQ)。  
  
 下列各節描述 WCF 隨附的特定佇列系結, 這些系結是以 MSMQ 為基礎。  
  
### <a name="msmq"></a>MSMQ  
 WCF 中的佇列傳輸會使用 MSMQ 來進行佇列通訊。  
  
 MSMQ 是 Windows 隨附的選用元件，而且會以 NT 服務的身分執行。 MSMQ 會擷取傳輸佇列中要進行傳輸的訊息，以及要傳遞至目標佇列的訊息。 MSMQ 佇列管理員會實作可靠訊息傳輸通訊協定，使訊息不會在傳輸期間遺失。 此通訊協定可以是原生通訊協定，或是 SOAP Reliable Message Protocol (SRMP) 這類 SOAP 架構的通訊協定。  
  
 在 MSMQ 中，佇列可以為異動式或非異動式。 交易式佇列可讓您在交易中擷取及傳送訊息，然後永久將訊息儲存在佇列中。 傳送至交易式佇列的訊息只會依序傳輸一次。 您可以使用非異動式佇列來同時傳送變動性 (volatile) 和永久性 (durable) 訊息。 傳送至非交易式佇列的訊息並不保證傳輸可靠，因此便有可能遺失訊息。  
  
 MSMQ 佇列的安全也可以使用向 Active Directory 目錄服務註冊的 Windows 身分識別來保護。 在安裝 MSMQ 時，您可以安裝 Active Directory 整合，而此時電腦必須是 Windows 網域網路的成員。  
  
 如需 MSMQ 的詳細資訊, 請參閱[安裝訊息佇列 (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)。  
  
### <a name="netmsmqbinding"></a>NetMsmqBinding  
 NetMsmqBinding > 是佇列系結, wcf 提供兩個 wcf 端點來使用 MSMQ 進行通訊。 [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md) 因此，繫結會公開特定用於 MSMQ 的屬性。 不過，在 `NetMsmqBinding` 中不會公開所有 MSMQ 功能和屬性。 精簡型 `NetMsmqBinding` 是使用大多數客戶都認為足夠的最佳功能組來設計。  
  
 `NetMsmqBinding` 闡述了到目前為止以繫結屬性為形式討論的核心佇列概念。 這些屬性接著會向 MSMQ 傳達傳輸及傳送訊息的方式。 下列章節討論屬性分類。 如需詳細資訊, 請參閱概念主題, 以更完整地描述特定屬性。  
  
#### <a name="exactlyonce-and-durable-properties"></a>ExactlyOnce 和 Durable 屬性  
 `ExactlyOnce` 和 `Durable` 屬性會影響在佇列之間傳輸訊息的方式：  
  
- `ExactlyOnce`：當設定為`true` (預設值) 時, 佇列通道會確保訊息在傳遞時不會重複。 也會確定沒有遺失訊息。 如果無法傳送訊息，或者在可以傳送訊息之前訊息存留時間到期，就會在寄不出的信件佇列中記錄失敗的訊息和傳送失敗的原因。 設定為 `false` 時，佇列通道會傳輸訊息。 在這個情況下，您可以選擇寄不出的信件佇列。  
  
- `Durable:` 設定為 `true` (預設值) 時，佇列通道會確定 MSMQ 將訊息永久儲存在磁碟上。 因此，如果停止後重新啟動 MSMQ 服務，磁碟上的訊息就會傳輸至目標佇列或傳遞至服務。 設定為 `false` 時，訊息會儲存在變動性存放區中，而且在停止後重新啟動 MSMQ 服務時會遺失。  
  
 如果是 `ExactlyOnce` 可靠傳輸，MSMQ 則會需要使用異動式佇列， 也需要從異動式佇列讀取異動。 因此，當您使用 `NetMsmqBinding` 時，異動一定會在 `ExactlyOnce` 設定為 `true` 的狀況下傳送或接收訊息。 同樣地，MSMQ 必須使用非交易式佇列才能得到最佳保證，例如當 `ExactlyOnce` 為 `false` 以及用於變動性傳訊時。 因此，將 `ExactlyOnce` 設定為 `false` 或將 durable 設定為 `false` 時，您無法使用異動來進行傳送或接收。  
  
> [!NOTE]
> 您一定要根據繫結程序中的設定建立正確的佇列 (異動式或非異動式)。 如果 `ExactlyOnce` 為 `true`，請使用交易式佇列，否則請使用非交易式佇列。  
  
#### <a name="dead-letter-queue-properties"></a>寄不出的信件佇列屬性  
 寄不出的信件佇列是用來儲存無法傳遞的訊息。 使用者可以撰寫補償邏輯，用來從寄不出的信件佇列中讀取訊息。  
  
 許多佇列系統都會提供全系統範圍之寄不出的信件佇列。 MSMQ 會對無法傳遞至非異動式佇列的訊息提供全系統範圍的非異動式寄不出的信件佇列，並對無法傳遞至異動式佇列的訊息提供全系統範圍的異動式寄不出的信件佇列。  
  
 如果將訊息傳送至不同目標佇列的用戶端共用 MSMQ 服務，則用戶端傳送的所有訊息都會移至同一個寄不出的信件佇列。 您不一定都要這麼做， 為獲得更好的隔離, 中[!INCLUDE[wv](../../../../includes/wv-md.md)]的 WCF 和 MSMQ 會提供自訂的寄不出的信件佇列 (或應用程式特定的寄不出的信件佇列), 讓使用者可以指定來儲存無法傳遞的訊息。 因此，不同的用戶端就不會共用同一個寄不出的信件佇列。  
  
 繫結中有兩個重要的屬性：  
  
- `DeadLetterQueue`：這個屬性是一個列舉, 指出是否要求寄不出的信件佇列。 列舉中也包含寄不出的信件佇列種類 (如果有要求的話)。 這些值則為 `None`、`System` 和 `Custom`。 如需這些屬性之解讀的詳細資訊, 請參閱使用寄不出[的信件佇列來處理訊息傳輸失敗](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)  
  
- `CustomDeadLetterQueue`：此屬性是應用程式特定寄不出的信件佇列的統一資源識別元 (URI) 位址。 這是必要的`DeadLetterQueue`。`Custom` 已選擇。  
  
#### <a name="poison-message-handling-properties"></a>有害訊息處理屬性  
 當服務在異動中從目標佇列中讀取訊息時，可能會因為各種原因而無法處理訊息。 然後服務會將訊息放回佇列，以便再次讀取。 若要處理重複失敗的訊息，可以在繫結中設定一組有害訊息處理屬性。 有害訊息處理屬性有四個：`ReceiveRetryCount`、`MaxRetryCycles`、`RetryCycleDelay` 和 `ReceiveErrorHandling`。 如需這些屬性的詳細資訊, 請參閱[有害訊息處理](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)。  
  
#### <a name="security-properties"></a>安全性屬性  
 MSMQ 會公開本身的安全性模型，例如佇列上或傳送驗證訊息上的存取控制清單 (ACL)。 `NetMsmqBinding` 會將這些安全性屬性當做部分傳輸安全性設定公開。 在傳輸安全性的繫結中有兩個屬性：`MsmqAuthenticationMode` 和 `MsmqProtectionLevel`。 這些屬性中的設定取決於設定 MSMQ 的方式。 如需詳細資訊, 請參閱[使用傳輸安全性保護訊息](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)。  
  
 除了傳輸安全性以外，也可以使用訊息安全性來保護實際的 SOAP 訊息本身。 如需詳細資訊, 請參閱[使用訊息安全性保護訊息](../../../../docs/framework/wcf/feature-details/securing-messages-using-message-security.md)。  
  
 `MsmqTransportSecurity` 也會公開 `MsmqEncryptionAlgorithm` 和 `MsmqHashAlgorithm` 這兩個屬性。 進行訊息的佇列對佇列傳輸加密，以及進行簽章雜湊處理時，可選用這些不同演算法的列舉。  
  
#### <a name="other-properties"></a>其他屬性  
 除了上述屬性，下面也有繫結程序中公開的其他 MSMQ 特定屬性：  
  
- `UseSourceJournal`：屬性, 表示已開啟來來源日誌。 來源日誌記錄是一個 MSMQ 功能，可追蹤已順利從傳輸佇列傳輸的訊息。  
  
- `UseMsmqTracing`：屬性, 表示已開啟 MSMQ 追蹤。 每次裝載 MSMQ 佇列管理員的電腦上有訊息傳入或傳出時，MSMQ 追蹤就會將報告訊息傳送至報告佇列。  
  
- `QueueTransferProtocol`：用於佇列對佇列訊息傳輸之通訊協定的列舉。 MSMQ 會實作原生佇列對佇列傳輸通訊協定，以及稱為 SOAP Reliable Messaging Protocol (SRMP) 的 SOAP 架構通訊協定。 在佇列對佇列傳輸中使用 HTTP 傳輸時，就會使用 SRMP。 在佇列對佇列傳輸中使用 HTTPS 時，則會使用 SRMP。  
  
- `UseActiveDirectory`：布林值, 指出是否必須將 Active Directory 用於佇列位址解析。 根據預設，這個屬性為關閉狀態。 如需詳細資訊, 請參閱[服務端點和佇列定址](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md)。  
  
### <a name="msmqintegrationbinding"></a>MsmqIntegrationBinding  
 當您想要讓 WCF 端點與以 C、 C++、COM 或 system.web api 撰寫的現有 MSMQ 應用程式進行通訊時,會使用。`MsmqIntegrationBinding`  
  
 其繫結屬性與 `NetMsmqBinding` 一樣， 但是會有下列差異：  
  
- `MsmqIntegrationBinding` 的作業合約受限為採用類型為 <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> 的單一參數，其中型別參數為本文類型。  
  
- 許多 MSMQ 原生訊息屬性會在 <xref:System.ServiceModel.MsmqIntegration.MsmqMessage%601> 中公開以供使用。  
  
- 為了協助序列化和還原序列化訊息本文，XML 和 ActiveX 等序列化程式都會提供讓您使用。  
  
### <a name="sample-code"></a>程式碼範例  
 如需如何撰寫使用 MSMQ 之 WCF 服務的逐步指示，請參閱下列主題：  
  
- [如何：與 WCF 端點和訊息佇列應用程式交換訊息](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
  
- [如何：與 WCF 端點交換佇列的訊息](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
  
 如需示範在 WCF 中使用 MSMQ 的完整程式碼範例，請參閱下列主題：  
  
- [異動 MSMQ 繫結](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)  
  
- [變動性佇列通訊](../../../../docs/framework/wcf/samples/volatile-queued-communication.md)  
  
- [無效信件佇列](../../../../docs/framework/wcf/samples/dead-letter-queues.md)  
  
- [工作階段和佇列](../../../../docs/framework/wcf/samples/sessions-and-queues.md)  
  
- [雙向通訊](../../../../docs/framework/wcf/samples/two-way-communication.md) 
  
- [SRMP](../../../../docs/framework/wcf/samples/srmp.md)  
  
- [訊息佇列上的訊息安全性](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)  
  
## <a name="see-also"></a>另請參閱

- [服務端點與佇列定址](../../../../docs/framework/wcf/feature-details/service-endpoints-and-queue-addressing.md)
- [以 Web 裝載佇列應用程式](../../../../docs/framework/wcf/feature-details/web-hosting-a-queued-application.md)
