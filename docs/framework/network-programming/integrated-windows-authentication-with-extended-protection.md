---
title: 具有延伸保護的整合式 Windows 驗證
ms.date: 03/30/2017
ms.assetid: 81731998-d5e7-49e4-ad38-c8e6d01689d0
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 88170162e4149580d532129666348d226540aced
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398127"
---
# <a name="integrated-windows-authentication-with-extended-protection"></a>具有延伸保護的整合式 Windows 驗證
已建立的增強功能會影響 <xref:System.Net> 中的 <xref:System.Net.HttpWebRequest>、<xref:System.Net.HttpListener>、<xref:System.Net.Mail.SmtpClient>、<xref:System.Net.Security.SslStream>、<xref:System.Net.Security.NegotiateStream> 和相關類別以及相關命名空間處理整合式 Windows 驗證的方式。 為加強安全性，擴充保護已新增支援。  
  
 這些變更可能會影響使用這些類別提出 Web 要求並接收回應的應用程式，它們使用整合式 Windows 驗證。 這項變更也會影響設定成使用整合式 Windows 驗證的網頁伺服器和用戶端應用程式。  
  
 這些變更也會影響使用這些類別提出其他類型要求並接收回應的應用程式，它們使用整合式 Windows 驗證。  
  
 支援擴充保護的變更僅供 Windows 7 和 Windows Server 2008 R2 的應用程式使用。 舊版 Windows 無法使用擴充保護的功能。  
  
## <a name="overview"></a>總覽  
 整合式 Windows 驗證的設計可讓某些認證的挑戰回應成為通用的，這表示可以重複使用或轉寄它們。 挑戰回應至少應該使用目標特定資訊建構，最好也能使用某些通道特定資訊。 服務隨後可以提供擴充保護，確保認證的挑戰回應包含服務特定資訊，例如服務主體名稱 (SPN)。 在認證交換時利用此資訊，服務就能進一步免於惡意使用可能未正確使用的認證挑戰回應。  
  
 擴充保護旨在增強驗證通訊協定，以強化其降低驗證轉送攻擊的功能。 它會圍繞著通道和服務繫結資訊的概念打轉。  
  
 整體目標如下：  
  
1.  如已更新用戶端支援擴充保護，應用程式應該向所有支援的驗證通訊協定提供通道繫結和服務繫結資訊。 有要繫結的通道 (TLS) 時，只能提供通道繫結資訊。 應該一律提供服務繫結資訊。  
  
2.  已正確設定的更新伺服器可能會在當它出現於用戶端驗證權杖時，驗證通道和服務繫結資訊，並在通道繫結不相符時，拒絕驗證嘗試。 根據部署案例，伺服器可能會驗證通道繫結、服務繫結或兩者都驗證。  
  
3.  更新的伺服器能夠接受或拒絕下層用戶端要求，這些要求不包含以原則為基礎的通道繫結資訊。  
  
 擴充保護所使用的資訊，是由下列兩個部分的其中之一或全部所組成：  
  
1.  通道繫結權杖或 CBT。  
  
2.  使用服務主體名稱或 SPN 格式的服務繫結資訊。  
  
 服務繫結資訊會指出用戶端意圖驗證特定的服務端點。 用戶端與伺服器之間的通訊使用下列屬性：  
  
-   以純文字格式執行用戶端驗證的伺服器必須能夠取得 SPN 值。  
  
-   SPN 的值是公用的。  
  
-   SPN 在傳輸中必須以密碼編譯方式保護，令攔截式攻擊無法插入、移除或修改其值。  
  
 CBT 是外部安全通道 (例如 TLS) 的屬性，透過內部、用戶端驗證型的通道用來繫結 (bind) 至交談。 CBT 必須具有下列屬性 (也由 IETF RFC 5056 定義)：  
  
-   有外部通道存在時，CBT 的值必須是能識別外部通道或伺服器端點的屬性，獨立抵達交談的用戶端和伺服器端。  
  
-   用戶端傳送的 CBT 值絕不能是會受攻擊者影響的項目。  
  
-   不保證 CBT 值的保密性。 但這不表示，當帶有 CBT 的通訊協定可能加密它時，伺服器執行驗證以外的任何其他驗證一律可以檢查服務繫結的值以及通道繫結資訊。  
  
-   CBT 在傳輸中必須受到密碼編譯式的完整性保護，令攻擊者無法插入、移除或修改其值。  
  
 透過用戶端將 SPN 和 CBT 以防竄改方式傳送到伺服器，即完成通道繫結。 伺服器驗證通道繫結資訊是否與其原則一致，拒絕它本身不認為是預期目標的驗證嘗試。 如此一來，兩個通道就會以密碼編譯方式繫結在一起。  
  
 為保留現有用戶端和應用程式的相容性，您可設定伺服器允許尚不支援擴充保護的用戶端嘗試驗證。 相較於「完全強化」組態，這稱為「部分強化」組態。  
  
 <xref:System.Net> 和 <xref:System.Net.Security> 命名空間中的多個元件都會代表呼叫端應用程式執行整合式 Windows 驗證。 本節描述在使用整合式 Windows 驗證時新增擴充保護的 System.Net 元件變更。  
  
 Windows 7 目前支援的擴充保護。 提供一種機制，讓應用程式可以判斷作業系統是否支援擴充保護。  
  
## <a name="changes-to-support-extended-protection"></a>支援擴充保護的變更  
 與整合式 Windows 驗證搭配使用的驗證程序，視所用的驗證通訊協定而定，通常包含目的地電腦所發出並傳回給用戶端電腦的挑戰。 擴充的保護會在此驗證程序中新增功能  
  
 <xref:System.Security.Authentication.ExtendedProtection> 命名空間支援應用程式使用擴充保護進行驗證。 這個命名空間中的 <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding> 類別代表通道繫結。 命名空間的 <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> 類別代表伺服器用於驗證傳入用戶端連接的擴充保護原則。 其他類別成員是搭配擴充保護使用。  
  
 就伺服器應用程式而言，這些類別包括下列：  
  
 <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy>，具有下列項目：  
  
-   <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.OSSupportsExtendedProtection%2A> 屬性，指出作業系統是否支援使用擴充保護的整合式 Windows 驗證。  
  
-   <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> 值，指出應該在何時強制執行延伸的保護原則。  
  
-   <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> 值，指出部署案例。 這會影響檢查擴充保護的方式。  
  
-   選擇性的 <xref:System.Security.Authentication.ExtendedProtection.ServiceNameCollection>，其包含的自訂 SPN 清單，是用來比對用戶端提供為預期驗證目標的 SPN。  
  
-   選擇性的 <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding>，包含的自訂通道繫結可用於驗證。 此案例不是常見案例  
  
 <xref:System.Security.Authentication.ExtendedProtection.Configuration> 命名空間支援應用程式使用擴充保護的驗證組態。  
  
 已進行一些功能變更，以支援現有 <xref:System.Net> 命名空間中的擴充保護。 這些變更包括下列項目：  
  
-   新的 <xref:System.Net.TransportContext> 類別新增至表示傳輸內容的 <xref:System.Net> 命名空間。  
  
-   <xref:System.Net.HttpWebRequest> 類別中的新 <xref:System.Net.HttpWebRequest.EndGetRequestStream%2A> 和 <xref:System.Net.HttpWebRequest.GetRequestStream%2A> 多載方法，可讓您擷取 <xref:System.Net.TransportContext> 以支援用戶端應用程式的擴充保護。  
  
-   新增 <xref:System.Net.HttpListener> 和 <xref:System.Net.HttpListenerRequest> 類別以支援伺服器應用程式。  
  
 已進行一項功能變更，以支援現有 <xref:System.Net.Mail> 命名空間中的 SMTP 用戶端應用程式的擴充保護：  
  
-   <xref:System.Net.Mail.SmtpClient> 類別中的 <xref:System.Net.Mail.SmtpClient.TargetName%2A> 屬性，代表使用 SMTP 用戶端應用程式的擴充保護時，用於驗證的 SPN。  
  
 已進行一些功能變更，以支援現有 <xref:System.Net.Security> 命名空間中的擴充保護。 這些變更包括下列項目：  
  
-   <xref:System.Net.Security.NegotiateStream> 類別中的新 <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsClient%2A> 和 <xref:System.Net.Security.NegotiateStream.AuthenticateAsClient%2A> 多載方法，允許傳送 CBT 以支援用戶端應用程式的擴充保護。  
  
-   <xref:System.Net.Security.NegotiateStream> 類別中的新 <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsServer%2A> 和 <xref:System.Net.Security.NegotiateStream.AuthenticateAsServer%2A> 多載方法，允許傳送 <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> 以支援伺服器應用程式的擴充保護。  
  
-   <xref:System.Net.Security.SslStream> 類別的新 <xref:System.Net.Security.SslStream.TransportContext%2A> 屬性，支援用戶端和伺服器應用程式的擴充保護。  
  
 已新增 <xref:System.Net.Configuration.SmtpNetworkElement> 屬性，支援 <xref:System.Net.Security> 命名空間中 SMTP 用戶端擴充保護的組態。  
  
## <a name="extended-protection-for-client-applications"></a>用戶端應用程式的擴充保護  
 大部分用戶端應用程式的擴充保護支援都會自動發生。 只要 Windows 基礎版本支援擴充保護，<xref:System.Net.HttpWebRequest> 和 <xref:System.Net.Mail.SmtpClient> 類別就支援擴充保護。 <xref:System.Net.HttpWebRequest> 執行個體傳送從 <xref:System.Uri> 建構的 SPN。 根據預設，<xref:System.Net.Mail.SmtpClient> 執行個體會傳送從 SMTP 郵件伺服器主機名稱建構的 SPN。  
  
 針對自訂驗證，用戶端應用程式可以使用 <xref:System.Net.HttpWebRequest> 類別的 <xref:System.Net.HttpWebRequest.EndGetRequestStream%28System.IAsyncResult%2CSystem.Net.TransportContext%40%29?displayProperty=nameWithType> 或 <xref:System.Net.HttpWebRequest.GetRequestStream%28System.Net.TransportContext%40%29?displayProperty=nameWithType> 方法，允許擷取 <xref:System.Net.TransportContext> 和使用 <xref:System.Net.TransportContext.GetChannelBinding%2A> 方法的 CBT。  
  
 <xref:System.Net.HttpWebRequest> 執行個體傳送至指定服務用於整合式 Windows 驗證的 SPN，可藉由設定 <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A> 屬性予以覆寫。  
  
 <xref:System.Net.Mail.SmtpClient.TargetName%2A> 屬性可用來設定自訂的 SPN，用於 SMTP 連線的整合式 Windows 驗證。  
  
## <a name="extended-protection-for-server-applications"></a>伺服器應用程式的擴充保護  
 <xref:System.Net.HttpListener> 會在執行 HTTP 驗證時，自動提供驗證服務繫結的機制。  
  
 最安全的案例是啟用 HTTPS:// 前置詞的擴充保護。 在本例中，將 <xref:System.Net.HttpListener.ExtendedProtectionPolicy%2A?displayProperty=nameWithType> 設定成將 <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> 設成 <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> 或 <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> 的 <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy>，以及 <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> 設成 <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario.TransportSelected>。值 <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> 會將 <xref:System.Net.HttpListener> 置於部分強化模式中，而 <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> 則對應到完全強化模式。  
  
 在此組態中，當透過外部安全通道向伺服器提出要求時，會查詢外部通道是否有通道繫結。 此通道繫結會傳遞給驗證 SSPI 呼叫，確認驗證 Blob 中的通道繫結是否相符。 有三個可能的結果：  
  
1.  伺服器的基礎作業系統不支援擴充的保護。 要求不會向應用程式公開，且未經授權的 (401) 回應會傳回至用戶端。 記錄到 <xref:System.Net.HttpListener> 追蹤來源的訊息會指定失敗的原因。  
  
2.  SSPI 呼叫失敗，表示可能是用戶端指定的通道繫結不符合從外部通道擷取的預期值，或針對 <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> 在伺服器上設定擴充保護原則時，用戶端無法提供通道繫結。 這兩種情況下，要求都不會向應用程式公開，且未經授權的 (401) 回應會傳回至用戶端。 記錄到 <xref:System.Net.HttpListener> 追蹤來源的訊息會指定失敗的原因。  
  
3.  用戶端指定了正確的通道繫結，或允許連接但未指定通道繫結，因為伺服器上使用 <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> 設定擴充保護原則。要求會傳回應用程式處理。 不會自動執行服務名稱檢查。 應用程式可選擇執行它自己使用 <xref:System.Net.HttpListenerRequest.ServiceName%2A> 屬性的服務名稱驗證，但在這些情況下會重複。  
  
 如果應用程式進行自己的 SSPI 呼叫，執行以在 HTTP 要求主體內來回傳遞的 Blob 為基礎的驗證，而且想要支援通道繫結，它需要從使用 <xref:System.Net.HttpListener> 的外部安全通道擷取預期的通道繫結，才能將它傳遞給原生的 Win32 [AcceptSecurityContext](http://go.microsoft.com/fwlink/?LinkId=147021) 函式。 若要這樣做，請使用 <xref:System.Net.HttpListenerRequest.TransportContext%2A> 屬性並呼叫 <xref:System.Net.TransportContext.GetChannelBinding%2A> 方法來擷取 CBT。 僅支援端點繫結。 如指定任何其他 <xref:System.Security.Authentication.ExtendedProtection.ChannelBindingKind.Endpoint>，就會擲回 <xref:System.NotSupportedException>。 如果基礎作業系統支援通道繫結，<xref:System.Net.TransportContext.GetChannelBinding%2A> 方法會將 <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding><xref:System.Runtime.InteropServices.SafeHandle> 包裝的指標傳回給通道繫結，此通道繫結適合傳遞給 [AcceptSecurityContext](http://go.microsoft.com/fwlink/?LinkId=147021) 函式作為傳入 `pInput` 參數之 SecBuffer 結構的 pvBuffer 成員。 <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding.Size%2A> 屬性包含通道繫結的長度，以位元組為單位。 如果基礎作業系統不支援通道繫結，此函式會傳回 `null`。  
  
 另一個可能的案例是，在不使用 Proxy 的情況下，啟用 HTTP:// 前置詞的擴充保護。 在本例中，將 <xref:System.Net.HttpListener.ExtendedProtectionPolicy%2A?displayProperty=nameWithType> 設定成將 <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> 設成 <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> 或 <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> 的 <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy>，以及 <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> 設成 <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario.TransportSelected>。值 <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> 會將 <xref:System.Net.HttpListener> 置於部分強化模式中，而 <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> 則對應到完全強化模式。  
  
 會根據已向 <xref:System.Net.HttpListener> 登錄的前置詞建立所允許服務名稱的預設清單。 此預設清單可透過 <xref:System.Net.HttpListener.DefaultServiceNames%2A> 屬性檢查。 如果這份清單不完整，應用程式可以在建構函式中針對會使用的 <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> 類別指定自訂的服務名稱集合，而不是預設的服務名稱清單。  
  
 在此組態中，向沒有外部安全通道的伺服器提出要求時，通常會在沒有通道繫結檢查的情況下繼續驗證。 如果驗證成功，會查詢內容是否有用戶端提供的服務名稱，用以比對驗證可接受的服務名稱清單。 有四個可能的結果：  
  
1.  伺服器的基礎作業系統不支援擴充的保護。 要求不會向應用程式公開，且未經授權的 (401) 回應會傳回至用戶端。 記錄到 <xref:System.Net.HttpListener> 追蹤來源的訊息會指定失敗的原因。  
  
2.  用戶端的基礎作業系統不支援擴充的保護。 在 <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.WhenSupported> 組態中，該驗證嘗試會成功，且要求會傳回給應用程式。 在 <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement.Always> 組態中，驗證嘗試會失敗。 要求不會向應用程式公開，且未經授權的 (401) 回應會傳回至用戶端。 記錄到 <xref:System.Net.HttpListener> 追蹤來源的訊息會指定失敗的原因。  
  
3.  用戶端基礎作業系統支援擴充的保護，但應用程式未指定服務繫結。 要求不會向應用程式公開，且未經授權的 (401) 回應會傳回至用戶端。 記錄到 <xref:System.Net.HttpListener> 追蹤來源的訊息會指定失敗的原因。  
  
4.  用戶端指定了服務繫結。 比較服務繫結和允許的服務繫結清單。 如果相符，則要求會傳回至應用程式。 否則，要求不會向應用程式公開，且未經授權的 (401) 回應會自動傳回至用戶端。 記錄到 <xref:System.Net.HttpListener> 追蹤來源的訊息會指定失敗的原因。  
  
 如果使用可接受服務名稱允許清單的這個簡單方法不足，應用程式可以查詢 <xref:System.Net.HttpListenerRequest.ServiceName%2A> 屬性，提供它自己的服務名稱驗證。 在上述的 1 和 2 案例中，屬性會傳回 `null`。 在案例 3 中，它會傳回空字串。 在案例 4 中，會傳回用戶端指定的服務名稱。  
  
 伺服器應用程式也可以使用這些擴充的保護功能，搭配其他類型的要求進行驗證，以及在使用受信任的 Proxy 時進行驗證。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Security.Authentication.ExtendedProtection>  
 <xref:System.Security.Authentication.ExtendedProtection.Configuration>
