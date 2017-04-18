---
title: "具有延伸保護的整合式 Windows 驗證 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 81731998-d5e7-49e4-ad38-c8e6d01689d0
caps.latest.revision: 13
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 13
---
# 具有延伸保護的整合式 Windows 驗證
改良了會影響整合式 Windows 驗證的方式。 <xref:System.Net.HttpWebRequest>處理、、、 <xref:System.Net.HttpListener><xref:System.Net.Mail.SmtpClient><xref:System.Net.Security.SslStream>、 <xref:System.Net.Security.NegotiateStream>和相關的類別。 <xref:System.Net> 和相關的命名空間。  支援將以延伸保護可以增強安全性。  
  
 這些變更可能會影響使用這些類別建立 Web 要求和接收回應使用整合式 Windows 驗證的應用程式。  這項變更也可能影響配置使用整合式 Windows 驗證的 Web 伺服器和用戶端應用程式。  
  
 這些變更也會影響到使用這些類別進行其他型別要求和接收回應使用整合式 Windows 驗證的應用程式。  
  
 支援延伸保護的變更會套用至在 Windows 7 和 Windows Server 2008 R2 的應用程式才能使用。  擴充的防護功能無法在舊版的 Windows 上使用。  
  
## 概觀  
 整合式 Windows 驗證的設計，讓一些認證挑戰回應能夠具有萬用的性質，這表示可以重複使用或轉寄它們。  應該最好也會建構要求回應在一個最小值與目標特定的資訊和某些通道特定資訊。  服務可以提供擴充的保護確定認證挑戰回應包含 Service 特定的資訊 \(例如服務主要名稱 \(SPN\) \(SPN\)。  在認證交換的資訊，這個服務可以更妥善地防止可能不正確地使用了認證要求回應的惡意用途。  
  
 延伸保護設計為提升至設計的驗證通訊協定緩衝區和驗證轉送攻擊。  它會集中通道和服務繫結資訊的概念。  
  
 整體目標如下:  
  
1.  如果用戶端更新支援延伸保護，應用程式應該提供通道繫結和服務繫結資訊給任何支援的驗證通訊協定。  只能提供通道繫結資訊，就會繫結至的通道 \(TLS 時\)。  一定要提供服務繫結資訊。  
  
2.  適當地設定更新之伺服器可能會驗證通道和服務繫結資訊，以便在用戶端驗證語彙基元和拒絕時驗證嘗試，如果通道繫結不相符。  根據部署案例中，伺服器可能會驗證通道繫結，服務繫結或兩者。  
  
3.  更新伺服器能夠接受或拒絕不包含原則的通道繫結資訊的下層用戶端要求。  
  
 延伸保護使用的資訊包括下列兩個部分或其中一個:  
  
1.  通道繫結語彙基元或 CBT。  
  
2.  提供服務主要名稱 \(SPN\) 的格式或服務繫結資訊。  
  
 服務繫結資訊是用戶端的意圖的指示驗證特定服務端點。  它會從用戶端傳送至伺服器具有下列屬性:  
  
-   SPN 值必須在執行用戶端驗證 \(Authentication\) 的伺服器以純文字格式。  
  
-   SPN 值是公用的。  
  
-   必須使用密碼保護 SPN 在傳輸中這類呼叫攔截式攻擊，無法插入、移除或修改其值。  
  
 CBT 是 TLS \(例如\) 中的目前行之外的安全通道屬性繫結 \(繫結\) 至內部，驗證用戶端通道的提供者之間。  CBT 必須具有下列屬性 \(也會由定義 IETF RFC 5056\):  
  
-   當外部通道存在時， CBT 的值必須是識別或之屬性外通道或伺服器端點，獨立達到談的用戶端和伺服器端。  
  
-   用戶端送出的 CBT 的值不可以是攻擊者可能會影響下列事項。  
  
-   確定未將 CBT 值的秘密。  但是這並不表示服務繫結和通道繫結資訊的值可以由任何其他，但執行驗證的伺服器一律檢查，做為帶有 CBT 的通訊協定可能進行加密。  
  
-   CBT 必須是密碼保護在傳輸中這類的完整性攻擊者無法插入，移除或修改其值。  
  
 通道以傳輸繫結 SPN 和 CBT 的用戶端完成至伺服器為防止遭他人修改的方式。  驗證伺服器通道繫結資訊與其符合原則並拒絕它認為不是本身所要目標的驗證嘗試。  如此一來，兩個通道變成一起密碼繫結。  
  
 若要保留現有的用戶端與應用程式的相容性，伺服器可能不支援延伸保護的用戶端設定成允許驗證嘗試。  具有「完全硬化」設定不同的是，這稱為「部分會硬化」設定。  
  
 在 <xref:System.Net> 的多個元件和 <xref:System.Net.Security> 命名空間表示呼叫的應用程式執行整合式 Windows 驗證。  本章節說明 System.Net 元件的變更加入至整合式 Windows 驗證其使用的延伸保護。  
  
 延伸保護在 Windows 7 上目前支援。  提供機制，讓應用程式可以判斷作業系統是否支援延伸保護。  
  
## 支援延伸保護的變更。  
 驗證處理序使用整合式 Windows 驗證時，會根據使用的驗證通訊協定，通常包括一個挑戰發行由目的電腦和送回給用戶端電腦。  延伸保護將新功能加入至這個驗證程序  
  
 <xref:System.Security.Authentication.ExtendedProtection> 命名空間提供使用應用程式的延伸保護進行驗證的支援。  此命名空間中的 <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding> 類別代表通道繫結。  此命名空間中的類別 <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> 表示伺服器用來延伸保護原則來驗證連入用戶端連接。  其他類別成員使用與擴充的保護。  
  
 伺服器應用程式，這些類別包括下列各項:  
  
 具有下列項目的 <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> :  
  
-   表示的 <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.OSSupportsExtendedProtection%2A> 屬性作業系統是否支援與延伸保護的整合式 Windows 驗證。  
  
-   <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> 值，表示延伸保護原則的強制實施時間。  
  
-   表示部署案例的 <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> 值。  這會影響延伸保護方式檢查。  
  
-   選擇性 <xref:System.Security.Authentication.ExtendedProtection.ServiceNameCollection> 包含自訂 SPN 清單用來比對包含用戶端所提供時，或者當驗證所需的目標。  
  
-   包含自訂通道繫結用於驗證的選擇性 <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding> 。  這個案例並不是常見的情況。  
  
 <xref:System.Security.Authentication.ExtendedProtection.Configuration> 命名空間提供使用應用程式的延伸保護進行驗證設定的支援。  
  
 許多功能變更支援在現有的 <xref:System.Net> 命名空間的延伸保護。  這些變更包括:  
  
-   新的 <xref:System.Net.TransportContext> 類別加入至表示傳輸內容的 <xref:System.Net> 命名空間。  
  
-   新的 <xref:System.Net.HttpWebRequest.EndGetRequestStream%2A> 和 <xref:System.Net.HttpWebRequest.GetRequestStream%2A> 允許擷取 <xref:System.Net.TransportContext> 支援延伸保護用戶端應用程式的多載方法。 <xref:System.Net.HttpWebRequest> 分類。  
  
-   為支援的伺服器應用程式的 <xref:System.Net.HttpListener> 和 <xref:System.Net.HttpListenerRequest> 類別的時機。  
  
 功能變更支援 SMTP 用戶端應用程式的延伸保護在現有的 <xref:System.Net.Mail> 命名空間:  
  
-   表示包含用於驗證，使用時的 <xref:System.Net.Mail.SmtpClient> 類別的 <xref:System.Net.Mail.SmtpClient.TargetName%2A> 屬性擴充 SMTP 用戶端應用程式的保護。  
  
 許多功能變更支援在現有的 <xref:System.Net.Security> 命名空間的延伸保護。  這些變更包括:  
  
-   新的 <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsClient%2A> 和 <xref:System.Net.Security.NegotiateStream.AuthenticateAsClient%2A> 允許藉由 CBT 支援延伸保護用戶端應用程式的多載方法。 <xref:System.Net.Security.NegotiateStream> 分類。  
  
-   新的 <xref:System.Net.Security.NegotiateStream.BeginAuthenticateAsServer%2A> 和 <xref:System.Net.Security.NegotiateStream.AuthenticateAsServer%2A> 允許藉由 <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> 支援延伸保護伺服器應用程式的多載方法。 <xref:System.Net.Security.NegotiateStream> 分類。  
  
-   在支援用戶端和伺服器應用程式的延伸保護的 <xref:System.Net.Security.SslStream> 類別的新 <xref:System.Net.Security.SslStream.TransportContext%2A> 屬性。  
  
 <xref:System.Net.Configuration.SmtpNetworkElement> 屬性加入至延伸保護的支援設定 SMTP 用戶端的 <xref:System.Net.Security> 命名空間的。  
  
## 用戶端應用程式的延伸保護  
 延伸保護支援大部分的用戶端應用程式會自動發生。  <xref:System.Net.HttpWebRequest> 和 <xref:System.Net.Mail.SmtpClient> 類別支援擴充保護，當視窗基礎版本支援延伸保護。  <xref:System.Net.HttpWebRequest> 執行個體傳送自 <xref:System.Uri>建構的 SPN。  根據預設， <xref:System.Net.Mail.SmtpClient> 執行個體傳送自 SMTP 電子郵件伺服器的主機名稱建構的 SPN。  
  
 自訂驗證的用戶端應用程式，可以使用 <xref:System.Net.HttpWebRequest.EndGetRequestStream%28System.IAsyncResult%2CSystem.Net.TransportContext%40%29?displayProperty=fullName> 或使用 <xref:System.Net.TransportContext.GetChannelBinding%2A> 方法，允許擷取 <xref:System.Net.TransportContext> 和 CBT 在 <xref:System.Net.HttpWebRequest> 的 <xref:System.Net.HttpWebRequest.GetRequestStream%28System.Net.TransportContext%40%29?displayProperty=fullName> 方法。  
  
 使用的 SPN。 <xref:System.Net.HttpWebRequest> 執行個體所傳送的整合式 Windows 驗證某一特定服務可以設定 <xref:System.Net.AuthenticationManager.CustomTargetNameDictionary%2A> 屬性覆寫。  
  
 <xref:System.Net.Mail.SmtpClient.TargetName%2A> 屬性可用於 SMTP 連接來設定自訂 SPN 使用整合式 Windows 驗證。  
  
## 伺服器應用程式的延伸保護  
 在執行 HTTP 驗證時，<xref:System.Net.HttpListener> 已驗證服務繫結自動提供機制。  
  
 最安全的案例是啟用 HTTPS:\/\/前置字元的延伸保護。  在這個案例中，設定為 <xref:System.Net.HttpListener.ExtendedProtectionPolicy%2A?displayProperty=fullName><xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> 和 <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> 設為或， <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement><xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement>，並 <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> 設為 <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> 的 <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> A 值在已部分硬化的方式，將 <xref:System.Net.HttpListener> ，而 <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> 對應至完全硬化的方式。  
  
 在這個組態中，會在要求至伺服器傳遞一個外部安全通道時，外部通道的通道繫結會查詢。  這個通道繫結傳遞至驗證 SSPI 呼叫，驗證繫結在驗證 BLOB 的通道相符。  有三個可能的結果:  
  
1.  伺服器的基礎作業系統不支援延伸保護。  要求不會公開給應用程式，因此，一個未授權 \(401 個\) 回應會傳回至用戶端。  訊息會記錄到指定這個原因的 <xref:System.Net.HttpListener> 追蹤來源為失敗。  
  
2.  SSPI 呼叫失敗表示用戶端指定不符合從外部通道或用戶端擷取的預期值失敗提供通道繫結的通道繫結，當伺服器上的延伸保護原則 <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement>處置。  在這兩種情況下，要求不會公開給應用程式，因此，一個未授權 \(401 個\) 回應會傳回至用戶端。  訊息會記錄到指定這個原因的 <xref:System.Net.HttpListener> 追蹤來源為失敗。  
  
3.  用戶端指定正確的通道繫結或允許連接，而不指定通道繫結，因為伺服器上的延伸保護原則設定要求傳回給處理應用程式的 <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> 。  服務名稱檢查不會自動執行。  使用 <xref:System.Net.HttpListenerRequest.ServiceName%2A> 屬性，應用程式可以選擇執行其服務名稱驗證，不過，在這些狀況是多餘的。  
  
 如果應用程式正在其 SSPI 呼叫執行以 BLOB 的驗證反覆傳入 HTTP 要求的本文中且希望支援通道繫結，它需要從這個外部安全通道擷取繫結使用 <xref:System.Net.HttpListener> 的預期通道用於傳遞至原生 Win32 [AcceptSecurityContext](http://go.microsoft.com/fwlink/?LinkId=147021) 函式。  若要這樣做，請使用 <xref:System.Net.HttpListenerRequest.TransportContext%2A> 屬性並呼叫方法 <xref:System.Net.TransportContext.GetChannelBinding%2A> 擷取 CBT。  只有端點繫結支援。  如果有任何其他 <xref:System.Security.Authentication.ExtendedProtection.ChannelBindingKind><xref:System.NotSupportedException> 指定，則會擲回。  如果基礎作業系統支援以不同的繫結， <xref:System.Net.TransportContext.GetChannelBinding%2A> 方法會傳回 <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding> 包裝指標的 <xref:System.Runtime.InteropServices.SafeHandle> 至通道繫結適用於傳遞給這個函式 [AcceptSecurityContext](http://go.microsoft.com/fwlink/?LinkId=147021) 在 `pInput` 做為參數傳遞的 SecBuffer 結構的 pvBuffer 成員。  <xref:System.Security.Authentication.ExtendedProtection.ChannelBinding.Size%2A> 屬性 \(以位元組為單位\)，通道繫結中，長度。  如果基礎作業系統不支援通道繫結，函式會傳回 `null`。  
  
 在不使用時，另一種可能的案例是啟用 HTTP:\/\/前置字元的延伸保護 Proxy。  在這個案例中，設定為 <xref:System.Net.HttpListener.ExtendedProtectionPolicy%2A?displayProperty=fullName><xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> 和 <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> 設為或， <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement><xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement>，並 <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> 設為 <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> 的 <xref:System.Security.Authentication.ExtendedProtection.ProtectionScenario> A 值在已部分硬化的方式，將 <xref:System.Net.HttpListener> ，而 <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> 對應至完全硬化的方式。  
  
 允許的服務名稱預設清單會根據 <xref:System.Net.HttpListener>向註冊的前置詞建立。  這個預設清單可以 <xref:System.Net.HttpListener.DefaultServiceNames%2A> 屬性加以檢查。  如果這份清單並不是完整的，應用程式會在建構函式中指定自訂名稱集合會取代預設的服務清單的 <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> 類別。  
  
 在這個組態中，要求時，通常會對伺服器，但是沒有外部安全通道驗證會繼續進行，而不需通道繫結檢查。  如果驗證成功，內容為用戶端提供及驗證可接受的服務名稱清單的服務名稱進行查詢。  有四種可能的結果:  
  
1.  伺服器的基礎作業系統不支援延伸保護。  要求不會公開給應用程式，因此，一個未授權 \(401 個\) 回應會傳回至用戶端。  訊息會記錄到指定這個原因的 <xref:System.Net.HttpListener> 追蹤來源為失敗。  
  
2.  用戶端的基礎作業系統不支援延伸保護。  在 <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> 組態中，驗證嘗試都會成功，並且要求會傳回應用程式。  在 <xref:System.Security.Authentication.ExtendedProtection.PolicyEnforcement> 組態中，驗證嘗試都會失敗。  要求不會公開給應用程式，因此，一個未授權 \(401 個\) 回應會傳回至用戶端。  訊息會記錄到指定這個原因的 <xref:System.Net.HttpListener> 追蹤來源為失敗。  
  
3.  用戶端的基礎作業系統支援延伸保護，不過，應用程式沒有指定服務繫結。  要求不會公開給應用程式，因此，一個未授權 \(401 個\) 回應會傳回至用戶端。  訊息會記錄到指定這個原因的 <xref:System.Net.HttpListener> 追蹤來源為失敗。  
  
4.  用戶端指定服務繫結。  服務繫結使用允許的服務繫結清單進行比較。  如果相符，要求傳回應用程式。  否則，要求不會公開給應用程式，因此，一個未授權 \(401 個\) 回應將會自動傳回給用戶端。  訊息會記錄到指定這個原因的 <xref:System.Net.HttpListener> 追蹤來源為失敗。  
  
 如果可接受服務名稱清單允許的清單中的這個簡單的方法是不夠的，應用程式可能會查詢 <xref:System.Net.HttpListenerRequest.ServiceName%2A> 屬性提供自己的服務名稱驗證。  在案例 1 和 2 頂端，屬性會傳回 `null`。  案例 3，則會傳回空字串。  案例 4，用戶端所指定的服務名稱會傳回。  
  
 這些擴充的保護功能只能由已驗證的伺服器應用程式可以使用與要求的其他型別，而且，當使用受信任的 Proxy。  
  
## 請參閱  
 <xref:System.Security.Authentication.ExtendedProtection>   
 <xref:System.Security.Authentication.ExtendedProtection.Configuration>