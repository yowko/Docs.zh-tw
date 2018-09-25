---
title: WSTrustChannelFactory 和 WSTrustChannel
ms.date: 03/30/2017
ms.assetid: 96cec467-e963-4132-b18b-7d0b3a2e979f
author: BrucePerlerMS
ms.openlocfilehash: ecc62292b2b064219127c369f43141a31ffe606d
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47080113"
---
# <a name="wstrustchannelfactory-and-wstrustchannel"></a>WSTrustChannelFactory 和 WSTrustChannel
如果您已熟悉 Windows Communication Foundation (WCF)，則應該知道 WCF 已是同盟感知用戶端。 若以 <xref:System.ServiceModel.WSFederationHttpBinding> 或類似的自訂繫結設定 WCF 用戶端，您就可以啟用對服務的同盟驗證。

 WCF 會在背景取得安全性權杖服務 (STS) 發行的權杖，並且使用此權杖對服務進行驗證。 這個方法的主要限制在於無法查看用戶端與伺服器的通訊。 WCF 會根據繫結上發出的權杖參數，自動對 STS 產生要求安全性權杖 (RST)。 這表示用戶端無法改變每個要求的 RST 參數，請檢查要求安全性權杖回應 (RSTR) 以取得顯示宣告這類資訊，或是快取權杖以供未來使用。

 WCF 用戶端目前適用於基本同盟情節。 不過，Windows Identity Foundation (WIF) 支援的其中一個主要情節需要在某個層級上對 RST 進行控制，而 WCF 不會輕易允許進行這項控制。 因此，WIF 新增了幾項功能，可讓您更充分掌控與 STS 的通訊。

 WIF 支援下列同盟情節：

- 使用不具任何 WIF 相依性的 WCF 用戶端對同盟服務進行驗證

- 在 WCF 用戶端上啟用 WIF，將 ActAs 或 OnBehalfOf 元素插入 STS 的 RST

- 單獨使用 WIF 從 STS 取得權杖，然後讓 WCF 用戶端使用此權杖進行驗證。 如需詳細資訊，請參閱 [ClaimsAwareWebService](https://go.microsoft.com/fwlink/?LinkID=248406) 範例。

 第一個案例本身即已說明：現有的 WCF 用戶端將繼續使用 WIF 信賴憑證者和 STS。 本主題將討論其餘兩種情節。

## <a name="enhancing-an-existing-wcf-client-with-actas--onbehalfof"></a>使用 ActAs / OnBehalfOf 增強現有的 WCF 用戶端
在典型的身分識別委派情節中，用戶端會呼叫中層服務，而中層服務接著會呼叫後端服務。 中層服務會作為用戶端或以用戶端的身分執行。

> [!TIP]
> ActAs 和 OnBehalfOf 之間有何不同？
>
> 從 Ws-trust 通訊協定的觀點而言：
>
> 1. ActAs RST 元素指出要求者需要包含有關兩個不同實體之宣告的權杖，這兩個實體是：要求者，以及 ActAs 元素中的權杖所代表的外部實體。
> 2. OnBehalfOf RST 元素指出要求者需要只包含有關一個實體之宣告的權杖：OnBehalfOf 元素中的權杖所代表的外部實體。
>
> ActAs 功能通常用於需要複合委派的狀況，此時收到發行權杖的最後一位收件者可以檢查整個委派鏈結，而且不只會看到用戶端，而是會看到所有的中繼媒介。 這樣它便可執行存取控制、稽核工作，以及其他架構在整個身分識別委派鏈結上的相關活動。 ActAs 功能一般是在多介層系統中用於在層與層之間驗證和傳遞身分識別相關資訊，而不需要將這項資訊傳遞到應用程式/商務邏輯層。
>
> 在必須使用原始用戶端的身分識別，以便有效執行與 Windows 身分識別模擬功能相同的功能時，就會使用 OnBehalfOf 功能。 使用 OnBehalfOf 時，收到發行權杖的最後一位收件者只會看到有關原始用戶端的宣告，中繼媒介的相關資訊並未加以保留。 Proxy 模式是 OnBehalfOf 功能常見的一種使用模式，用戶端在這種模式下無法直接存取 STS，而是透過 Proxy 閘道進行通訊。 Proxy 閘道會驗證呼叫者，並將該呼叫者的相關資訊放入 RST 訊息的 OnBehalfOf 元素，而該訊息接著會傳送到實際 STS 以進行處理。 結果權杖僅包含與該 Proxy 用戶端相關的宣告，因此可讓 Proxy 完全透明呈現給發行權杖的接收者。請注意，WIF 不支援將 \<wsse:SecurityTokenReference> 或 \<wsa:EndpointReferences> 作為 \<wst:OnBehalfOf> 的子系。 WS-Trust 規格允許使用三種方式來識別原始的要求者 (代表 Proxy 正在運作的用戶端)。 這些是：
>
> - 安全性權杖參考。 權杖的參考出現在訊息中，或可能從頻外取得。
> - 端點參考。 作為用於查詢資料的索引鍵，同樣是在頻外進行。
> - 安全性權杖。 直接識別原始的要求者。
>
> WIF 僅支援加密或未加密的安全性權杖作為 \<wst:OnBehalfOf> 的直接子元素。

 這項資訊會使用 RST 中的 ActAs 和 OnBehalfOf 權杖元素傳遞給 WS-Trust 簽發者。

 WCF 會在繫結上公開能夠將任意 XML 元素加入至 RST 的擴充點。 不過，由於擴充點繫於繫結，因此要求每次呼叫時 RST 內容都要改變的情節，必須針對每次呼叫重新建立用戶端，而這樣做會降低效能。 WIF 會在 `ChannelFactory` 類別上使用擴充方法，讓開發人員能夠將透過其他方式取得的任何權杖附加至 RST。 下列程式碼範例示範如何取得代表用戶端的權杖 (例如 X.509、使用者名稱或安全性聲明標記語言 (SAML) 權杖)，並且將該權杖附加至傳送給簽發者的 RST。

```csharp
IHelloService serviceChannel = channelFactory.CreateChannelActingAs<IHelloService>(clientSamlToken);
serviceChannel.Hello("Hi!");
```

 WIF 提供下列優點：

- 每個通道的 RST 都可以修改；因此中層服務不必為每個用戶端重新建立通道處理站，這樣就能改善效能。

- 這種方法適用現有的 WCF 用戶端，能為想要啟用身分識別委派語意的現有 WCF 中層服務提供輕鬆升級的管道。

 不過，這裡仍然無法查看用戶端與 STS 之間的通訊。 我們將在第三個情節中檢視這點。

## <a name="communicating-directly-with-an-issuer-and-using-the-issued-token-to-authenticate"></a>與簽發者直接通訊並使用發行的權杖進行驗證
對於某些進階的情節而言，只是增強 WCF 用戶端是不夠的。 僅使用 WCF 的開發人員通常會使用 Message In/Message Out 合約，並且手動處理用戶端的簽發者回應剖析。

WIF 引進了 <xref:System.ServiceModel.Security.WSTrustChannelFactory> 和 <xref:System.ServiceModel.Security.WSTrustChannel> 類別，讓用戶端與 WS-Trust 簽發者能夠直接通訊。 <xref:System.ServiceModel.Security.WSTrustChannelFactory> 和 <xref:System.ServiceModel.Security.WSTrustChannel> 類別可讓強型別 RST 和 RSTR 物件在用戶端與簽發者之間流動，如下列程式碼範例中所示。

```csharp
WSTrustChannelFactory trustChannelFactory = new WSTrustChannelFactory(stsBinding, stsAddress);
WSTrustChannel channel = (WSTrustChannel) trustChannelFactory.CreateChannel();
RequestSecurityToken rst = new RequestSecurityToken(RequestTypes.Issue);
rst.AppliesTo = new EndpointAddress(serviceAddress);
RequestSecurityTokenResponse rstr = null;
SecurityToken token = channel.Issue(rst, out rstr);
```

請注意，<xref:System.ServiceModel.Security.WSTrustChannel.Issue%2A> 方法上的 `out` 參數允許存取 RSTR，以便進行用戶端檢查。

到目前為止，您只了解如何取得權杖。 從 <xref:System.ServiceModel.Security.WSTrustChannel> 物件傳回的權杖是 `GenericXmlSecurityToken`，其中包含對信賴憑證者進行驗證所需的全部資訊。 下列程式碼範例示範如何使用這個權杖。

```csharp
IHelloService serviceChannel = channelFactory.CreateChannelWithIssuedToken<IHelloService>( token );
serviceChannel.Hello("Hi!");
```

`ChannelFactory` 物件上的 <xref:System.ServiceModel.ChannelFactory%601.CreateChannelWithIssuedToken%2A> 擴充方法會對 WIF 指出，您已透過其他方式取得權杖，因此應該停止對簽發者進行一般 WCF 呼叫，並且改用您取得的權杖對信賴憑證者進行驗證。 這具備下列優點：

- 可讓您完全掌控權杖發行程序。

- 透過直接在傳出的 RST 上設定這些屬性的方式支援 ActAs/OnBehalfOf 情節。

- 可根據 RSTR 的內容做出動態用戶端信任的決策。

- 可讓您快取和重複使用從 <xref:System.ServiceModel.Security.WSTrustChannel.Issue%2A> 方法傳回的權杖。

- <xref:System.ServiceModel.Security.WSTrustChannelFactory> 和 <xref:System.ServiceModel.Security.WSTrustChannel> 允許您根據 WCF 的最佳做法控制通道快取、錯誤和復原語意。

## <a name="see-also"></a>另請參閱

- [WIF 功能](../../../docs/framework/security/wif-features.md)