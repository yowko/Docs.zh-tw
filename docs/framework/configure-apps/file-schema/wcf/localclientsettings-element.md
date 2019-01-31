---
title: <localClientSettings> 項目
ms.date: 03/30/2017
ms.assetid: 4680ace5-f4e1-4fcb-b9d8-a4a4af5cd7ae
ms.openlocfilehash: e43a03258f4a76c1d19c7bdcff99fcb1d1db19ac
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55278924"
---
# <a name="localclientsettings-element"></a>\<localClientSettings > 項目
指定此繫結之本機用戶端的安全性設定。  
  
 \<system.serviceModel>  
\<bindings>  
\<customBinding>  
\<binding>  
\<安全性 >  
  
## <a name="syntax"></a>語法  
  
```xml  
<security>
   <localClientSettings cacheCookies="Boolean"
                        cookieRenewalThresholdPercentage="Integer"
                        detectReplays="Boolean"
                        maxClockSkew="TimeSpan"
                        maxCookieCachingTime="TimeSpan"
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
|`cacheCookies`|布林值，指定是否啟用 Cookie 快取。 預設為 `false`。|  
|`cookieRenewalThresholdPercentage`|整數，指定可更新的 Cookie 百分比上限。 這個值應介於 0 到 100 之間 (含 0 和 100)。 預設值為 90。|  
|`detectReplays`|布林值，這個值會指定是否會偵測及自動處理對通道所發出的重新執行攻擊。 預設為 `false`。|  
|`maxClockSkew`|<xref:System.TimeSpan>，指定通訊雙方之系統時鐘之間的最大時間差異。 預設值為 "00:05:00"。<br /><br /> 當這個值設定為預設值時，接收者接受之訊息的傳送時間時間戳記會比收到訊息的時間早或晚 5 分鐘。 沒有通過傳送時間測試的訊息會遭到拒絕。 這個設定會配合 `replayWindow` 屬性使用。|  
|`maxCookieCachingTime`|<xref:System.TimeSpan>，指定 Cookie 的最長存留期。 預設值為 "10675199.02:48:05.4775807"。|  
|`reconnectTransportOnFailure`|布林值，指定使用 WS-Reliable 訊息的連線是否會在傳輸失敗之後嘗試重新連線。 預設為 `true`，表示無限次嘗試重新連線。 無活動逾時會打破這個循環，而這樣會使得通道在無法重新連線時擲回例外狀況。|  
|`replayCacheSize`|正整數，指定用於偵測重新執行攻擊之已快取 Nonce 數目。 如果超過這個限制，便會移除最舊的 Nonce，然後為新訊息建立新的 Nonce。 預設值為 500000。|  
|`replayWindow`|<xref:System.TimeSpan>，指定個別訊息 Nonce 有效的持續期間。<br /><br /> 過了這段時間後，將不會接受與先前所傳送之訊息擁有相同 Nonce 的訊息。 這個屬性是配合 `maxClockSkew` 屬性使用，以防止重新執行攻擊。 攻擊者可以在重新執行視窗逾期之後重新執行訊息。 然而，這個訊息無法通過 `maxClockSkew` 測試，因為它會拒絕傳送時間之時間戳記比收到訊息的時間早或晚的訊息。|  
|`sessionKeyRenewalInterval`|指定持續期間的 <xref:System.TimeSpan>，啟動器將在這段期間過後更新安全性工作階段的金鑰。 預設為 "10:00:00"。|  
|`sessionKeyRolloverInterval`|<xref:System.TimeSpan>，指定前一個工作階段金鑰在金鑰更新期間對傳入訊息屬有效的時間間隔。 預設為 "00:05:00"。<br /><br /> 在金鑰更新之後，用戶端和伺服器都必須使用最新的可用金鑰來傳送訊息。 雙方都會接受由前一個工作階段金鑰保護的傳入訊息，直到變換時間逾期。|  
|`timestampValidityDuration`|正的 <xref:System.TimeSpan>，指定時間戳記有效的持續期間。 預設為 "00:15:00"。|  
  
### <a name="child-elements"></a>子元素  
 無  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|指定自訂繫結的安全性選項。|  
|[\<secureConversationBootstrap>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|指定用於啟始安全對話服務的預設值。|  
  
## <a name="remarks"></a>備註  
 這些是本機設定，這意味著它們不是衍生自服務之安全性原則的設定。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.LocalClientSettings%2A>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A>
- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [繫結](../../../../../docs/framework/wcf/bindings.md)
- [擴充繫結](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [自訂繫結](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [如何：建立自訂繫結使用 SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [自訂繫結安全性](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
