---
title: <localServiceSettings> 項目
ms.date: 03/30/2017
ms.assetid: 0658549c-3f65-46dd-8c5c-9895441ed734
ms.openlocfilehash: 4883fd563ecf989d67c369085df4fc43d0c5f078
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400309"
---
# <a name="localservicesettings-element"></a>\<localServiceSettings > 元素
指定此繫結之本機服務的安全性設定。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<系結 >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<系結 >** \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<安全性 >** ](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<localServiceSettings >**  
  
## <a name="syntax"></a>語法  
  
```xml  
<security>
  <localServiceSettings detectReplays="Boolean"
                        inactivityTimeout="TimeSpan"
                        issuedCookieLifeTime="TimeSpan"
                        maxCachedCookies="Integer"
                        maxClockSkew="TimeSpan"
                        maxPendingSessions="Integer"
                        maxStatefulNegotiations="Integer"
                        negotiationTimeout="TimeSpan"
                        reconnectTransportOnFailure="Boolean"
                        replayCacheSize="Integer"
                        replayWindow="TimeSpan"
                        sessionKeyRenewalInterval="TimeSpan"
                        sessionKeyRolloverInterval="TimeSpan"
                        timestampValidityDuration="TimeSpan" />
</security>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`detectReplays`|布林值，這個值會指定是否會偵測及自動處理對通道所發出的重新執行攻擊。 預設為 `false`。|  
|`inactivityTimeout`|正的 <xref:System.TimeSpan>，指定通道在無活動的狀態下要等候多長的時間才會逾時。預設為 "01:00:00"。|  
|`issuedCookieLifeTime`|<xref:System.TimeSpan>，指定發出給所有新的安全性 Cookie 的存留期。 超過存留期的 Cookie 會回收，而且必須再次交涉。 預設值為 "10:00:00"。|  
|`maxCachedCookies`|正整數，這個值會指定可以快取的 Cookie 數目上限。 預設值是 1000。|  
|`maxClockSkew`|<xref:System.TimeSpan>，指定通訊雙方之系統時鐘之間的最大時間差異。 預設值為 "00:05:00"。<br /><br /> 當這個值設定為預設值時，接收者接受之訊息的傳送時間時間戳記會比收到訊息的時間早或晚 5 分鐘。 沒有通過傳送時間測試的訊息會遭到拒絕。 這個設定會配合 `replayWindow` 屬性使用。|  
|`maxPendingSessions`|正整數，這個值會指定服務支援之擱置中安全性工作階段數目上限。 當達到這個限制時，所有新的用戶端都會收到 SOAP 錯誤。 預設值為 1000。|  
|`maxStatefulNegotiations`|正整數，這個值會指定可以同時為作用中的安全性交涉數目。 超過限制的交涉工作階段會排入佇列，而且只有在低於限制的空間可供使用時才能完成。 預設值為 1024。|  
|`negotiationTimeout`|<xref:System.TimeSpan>，指定通道所使用之安全性原則的存留期。 超過此時間時，通道會與用戶端重新交涉新安全性原則。 預設值為 "00:02:00"。|  
|`reconnectTransportOnFailure`|布林值，指定使用 WS-Reliable 訊息的連線是否會在傳輸失敗之後嘗試重新連線。 預設為 `true`，表示無限次嘗試重新連線。 無活動逾時會打破這個循環，而這樣會使得通道在無法重新連線時擲回例外狀況。|  
|`replayCacheSize`|正整數，指定用於偵測重新執行攻擊之已快取 Nonce 數目。 如果超過這個限制，便會移除最舊的 Nonce，然後為新訊息建立新的 Nonce。 預設值為 500000。|  
|`replayWindow`|<xref:System.TimeSpan>，指定個別訊息 Nonce 有效的持續期間。<br /><br /> 過了這段時間後，將不會接受與先前所傳送之訊息擁有相同 Nonce 的訊息。 這個屬性是配合 `maxClockSkew` 屬性使用，以防止重新執行攻擊。 攻擊者可以在重新執行視窗逾期之後重新執行訊息。 然而，這個訊息無法通過 `maxClockSkew` 測試，因為它會拒絕傳送時間之時間戳記比收到訊息的時間早或晚的訊息。|  
|`sessionKeyRenewalInterval`|指定持續期間的 <xref:System.TimeSpan>，啟動器將在這段期間過後更新安全性工作階段的金鑰。 預設為 "10:00:00"。|  
|`sessionKeyRolloverInterval`|<xref:System.TimeSpan>，指定前一個工作階段金鑰在金鑰更新期間對傳入訊息屬有效的時間間隔。 預設為 "00:05:00"。<br /><br /> 在金鑰更新之後，用戶端和伺服器都必須使用最新的可用金鑰來傳送訊息。 雙方都會接受由前一個工作階段金鑰保護的傳入訊息，直到變換時間逾期。|  
|`timestampValidityDuration`|正的 <xref:System.TimeSpan>，指定時間戳記有效的持續期間。 預設為 "00:15:00"。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<security>](security-of-custombinding.md)|指定自訂繫結的安全性選項。|  
|[\<secureConversationBootstrap>](secureconversationbootstrap.md)|指定用於啟始安全對話服務的預設值。|  
  
## <a name="remarks"></a>備註  
 這些是本機設定，因為它們並未發行成為服務之安全性原則的一部分，因此不會影響用戶端的繫結。  
  
 `localServiceSecuritySettings` 項目的下列屬性有助於降低阻絕服務 (DOS) 安全性攻擊：  
  
- `maxCachedCookies`：控制在執行 SPNEGO 或 SSL 交涉之後，伺服器所快取有時間界限之 SecurityContextToken 的上限。  
  
- `issuedCookieLifetime`：控制在 SPNEGO 或 SSL 交涉之後，伺服器所發出的 SecurityContextToken 的存留期 (Lifetime)。 伺服器會在這段時間內快取 SecurityContextToken。  
  
- `maxPendingSessions`：控制在伺服器中建立的安全對話上限，但是不會針對這些對話處理應用程式訊息。 這個配額會防止用戶端在服務中建立安全對話，由此服務會針對每個用戶端保留對話狀態，但不會使用這些對話。  
  
- `inactivityTimeout`：控制服務讓安全對話保持運作，而不會從中接收應用程式訊息的時間上限。 這個配額會防止用戶端在服務中建立安全對話，由此服務會針對每個用戶端保留對話狀態，但不會使用這些對話。  
  
 在安全對話工作階段中，請注意繫結上的 `inactivityTimeout` 和 `receiveTimeout` 屬性都會影響工作階段逾時。 其中時間較短的屬性值會決定逾時發生的時間。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.LocalServiceSettings%2A>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [繫結](../../../wcf/bindings.md)
- [擴充繫結](../../../wcf/extending/extending-bindings.md)
- [自訂繫結](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [如何：使用 SecurityBindingElement 建立自訂系結](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [自訂繫結安全性](../../../wcf/samples/custom-binding-security.md)
