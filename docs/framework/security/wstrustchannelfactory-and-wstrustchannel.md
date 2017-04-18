---
title: "WSTrustChannelFactory 和 WSTrustChannel | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 96cec467-e963-4132-b18b-7d0b3a2e979f
caps.latest.revision: 9
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 9
---
# WSTrustChannelFactory 和 WSTrustChannel
如果您已熟悉 Windows Communication Foundation \(WCF\)，您知道 WCF 用戶端已明確的聯合。  藉由設定 WCF 用戶端以 <xref:System.ServiceModel.WSFederationHttpBinding> 或類似的自訂繫結，您可以啟用等位的驗證加入至服務。  
  
 WCF 用於 Security Token Service \(STS\) 在幕後發行的權杖並使用語彙基元驗證加入至服務。  對這個方法的主要限制在於沒有可讓您與伺服器的用戶端通訊。  WCF 自動產生要求安全性權杖 \(RST\) 會根據發出的權杖參數的 STS 繫結。  這表示用戶端無法改變 RST 參數每個要求，並檢查要求安全性權杖回應 \(RSTR\) 取得資訊 \(例如顯示宣告或快取語彙基元之後使用。  
  
 目前， WCF 用戶端適用於基本的聯合案例。  不過， Windows Identity Foundation \(WIF\) 支援的其中一個主要案例需要對 RST 的控制項在 WCF 不被允許的層級。  因此， WIF 加入對通訊的詳細控制與 STS 的功能。  
  
 WIF 聯合支援下列案例:  
  
-   使用未經驗證的任何 WIF 相依性的 WCF 用戶端對一行的服務。  
  
-   使 WCF 用戶端的 WIF 插入 ActAs 或 OnBehalfOf 項目 RST 至 STS  
  
-   使用將個別的 WIF 衍生自 STS 的語彙基元 WCF 用戶端驗證的權杖。  如 [ClaimsAwareWebService](http://go.microsoft.com/fwlink/?LinkID=248406) 需詳細資訊，請參閱範例。  
  
 第一個案例是明顯:現有的 WCF 用戶端將繼續與 WIF 信賴憑證者和 STSs 一起使用。  本主題討論其餘兩案例。  
  
## 引發有 ActAs\/OnBehalfOf 現有的 WCF 用戶端  
 在典型的識別委派案例中，用戶端呼叫中介層服務，然後呼叫的後端服務。  中介層服務做為或動作，代表用戶端。  
  
> [!TIP]
>  ActAs 和 OnBehalfOf 有何不同?  
>   
>  從 WS\-Trust procotol 位置:  
>   
>  1.  ActAs RST 項目表示要求者想要該語彙基元包含宣告約兩個不同的實體:要求者與 ActAs 項目的語彙基元所表示之外部實體。  
> 2.  OnBehalfOf RST 項目表示要求者想要該語彙基元包含宣告只有大約實體:在 OnBehalfOf 項目的語彙基元所表示之外部實體。  
>   
>  ActAs 功能通常用來要求複合委派，核發之權杖最後的收件者可以檢查整個委派鏈結和看到不僅用戶端，不過，所有中繼的案例。  這讓它執行根據整個識別委派鏈結和其他相關活動的存取控制，稽核。  ActAs 功能通常用來在多層系統驗證和透過如需識別的資訊在層之間，而不需要將這個資訊在應用程式和商務邏輯層。  
>   
>  OnBehalfOf 功能用於原始的用戶端只識別重要且有效的方式與在 Windows 的識別模擬功能的案例。  當使用時， OnBehalfOf 核發之權杖的最後的收件者可以只看到有關原始用戶端的宣告，，而有關的中繼資訊不會保留。  OnBehalfOf 功能所使用的一般模式是用戶端不能直接存取 STS，而是透過 Proxy 閘道通訊的 Proxy 樣式。  代理閘道驗證呼叫端並將有關呼叫程式的資訊。然後會傳送至處理的真正的 STS RST 訊息的 OnBehalfOf 項目。  只發生的權杖包含宣告與用戶端到 Proxy 相關，讓 Proxy 完全透明已發行的權杖的接收。請注意 WIF 不支援 \<wsse:Timestamp 項目: SecurityTokenReference\> 或 \<wsa: 做為項目的子系的 EndpointReferences \<\> : OnBehalfOf\>。  WS\-Trust 規格允許三種方式識別原始要求者 \(表示誰 Proxy 動作\)。  這些是：  
>   
>  -   安全性權杖參考。  out 語彙基元的參考，在訊息或無法擷取的超出範圍\)。  
> -   端點參考。  用來，索引鍵查閱資料，再超出範圍。  
> -   安全性權杖。  直接識別原始要求者。  
>   
>  WIF 只支援安全性權杖，加密或解密，做為項目的直接 \<子項目: OnBehalfOf\>。  
  
 使用 RST，的 ActAs 語彙基元和 OnBehalfOf 項目這項資訊來表示對 WS\-Trust 簽發者。  
  
 WCF 公開在允許任意 XML 項目加入至 RST 的繫結的擴充點。  不過，，因為擴充點會繫結至繫結，要求的案例 RST 內容每次呼叫變更必須重新建立每個呼叫的用戶端，會降低效能。  WIF 使用 `ChannelFactory` 類別的擴充方法可讓開發人員附加是衍生的超出範圍的 RST 的所有語彙基元。  下列程式碼範例會示範如何取得代表用戶端的權杖 \(例如 X.509、使用者名稱或安全性判斷提示 Markup Language \(SAML\) 語彙基元\) 並將它附加至傳送給簽發者的安全性。  
  
```  
IHelloService serviceChannel = channelFactory.CreateChannelActingAs<IHelloService>( clientSamlToken );  
serviceChannel.Hello(“Hi!”);  
```  
  
 WIF 提供下列優點:  
  
-   包含可以每通道修改;因此，中介層服務不需要重新建立每個用戶端的通道處理站，以提高效能。  
  
-   這個使用現有的 WCF 用戶端，使簡單升級路徑可現有 WCF 中介層服務要啟用識別委派語意。  
  
 不過，仍有可讓您與 STS 的用戶端通訊。  我們會檢查這個中第三種情況。  
  
## 通訊直接與簽發者和使用發行的權杖驗證  
 對於某些進階案例，提高 WCF 用戶端不夠。  通常會使用 WCF 只使用訊息在\/訊息合約並手動處理簽發者回應用戶端剖析的開發人員。  
  
 WIF 引入 <xref:System.ServiceModel.Security.WSTrustChannelFactory> 和 <xref:System.ServiceModel.Security.WSTrustChannel> 類別可讓用戶端直接與 WS\-Trust 簽發者通訊。  <xref:System.ServiceModel.Security.WSTrustChannelFactory> 和 <xref:System.ServiceModel.Security.WSTrustChannel> 類別會啟用對流程的強型別的 RST 和 RSTR 物件在用戶端和簽發者之間，如下列程式碼範例所示。  
  
```  
WSTrustChannelFactory trustChannelFactory = new WSTrustChannelFactory( stsBinding, stsAddress );  
WSTrustChannel channel = (WSTrustChannel) trustChannelFactory.CreateChannel();  
RequestSecurityToken rst = new RequestSecurityToken(RequestTypes.Issue);  
rst.AppliesTo = new EndpointAddress(serviceAddress);  
RequestSecurityTokenResponse rstr = null;  
SecurityToken token = channel.Issue(rst, out rstr);  
```  
  
 請注意在 <xref:System.ServiceModel.Security.WSTrustChannel.Issue%2A> 方法的 `out` 參數允許套用至 RSTR 的存取用戶端檢查的。  
  
 目前為止，我們只會看到如何取得語彙基元。  從 <xref:System.ServiceModel.Security.WSTrustChannel> 物件傳回的語彙基元是包含所有資訊為驗證需要為信賴憑證者的 `GenericXmlSecurityToken` 。  下列程式碼範例顯示如何使用這個語彙基元。  
  
```  
IHelloService serviceChannel = channelFactory.CreateChannelWithIssuedToken<IHelloService>( token ); serviceChannel.Hello(“Hi!”);  
```  
  
 在 `ChannelFactory` 物件的 <xref:System.ServiceModel.ChannelFactory%601.CreateChannelWithIssuedToken%2A> 擴充方法會向 WIF 所衍生自的語彙基元超出範圍，因此，它應該停止正常 WCF 呼叫簽發者和使用您取得驗證到信賴憑證者的語彙基元。  這有下列優點:  
  
-   它可讓您對權杖發行處理序的控制權。  
  
-   它會直接設定在外送 RST 的這些屬性支援 ActAs\/OnBehalfOf 案例。  
  
-   它可讓動態用戶端信任決策做以 RSTR 的內容。  
  
-   它可讓您快取並重複使用從 <xref:System.ServiceModel.Security.WSTrustChannel.Issue%2A> 方法所傳回的語彙基元。  
  
-   <xref:System.ServiceModel.Security.WSTrustChannelFactory> 和 <xref:System.ServiceModel.Security.WSTrustChannel> 允許通道快取、錯誤和復原語意控制以 WCF 最佳做法。  
  
## 請參閱  
 [WIF 功能](../../../docs/framework/security/wif-features.md)