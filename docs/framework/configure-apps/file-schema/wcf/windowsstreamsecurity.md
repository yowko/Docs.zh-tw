---
title: <windowsStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
ms.openlocfilehash: dab8505a9ddb348a6f7fe16ae9acb3a0119a8b06
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73735891"
---
# <a name="windowsstreamsecurity"></a>\<Windowsstreamsecurity 正在 >
指定自訂繫結的 Windows 資料流安全性設定。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp; &nbsp;[ **\<system system.servicemodel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<** ](bindings.md)系結 >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<** 系結 >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<windowsstreamsecurity 正在 >**  
  
## <a name="syntax"></a>語法  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign" />
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|protectionLevel|定義訊息層級安全性。 簽章訊息可降低訊息在傳輸期間遭第三方竄改的風險。 加密會提供傳輸期間的資料層級隱私權。 有效值包括以下的值：<br /><br /> -None：沒有保護。<br />-Sign：訊息已簽署。<br />-EncryptAndSign：訊息已簽署並加密。<br /><br /> 預設為 EncryptAndSign。<br /><br /> 此屬性的型別為 <xref:System.Net.Security.ProtectionLevel>。|  
  
### <a name="child-elements"></a>子項目  
 None  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<binding >](bindings.md)|定義自訂繫結的所有繫結功能。|  
  
## <a name="remarks"></a>備註  
 TCP 和具名管道這類使用資料流導向通訊協定的傳輸，支援資料流傳輸升級。 具體來說，WCF 會提供安全性升級。 此傳輸安全性的設定是由這個 configuration 專案封裝，也是由[\<sslStreamSecurity >](sslstreamsecurity.md)（可以設定並新增至自訂系結）所封裝。  
  
## <a name="see-also"></a>請參閱

- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>
- [繫結](../../../wcf/bindings.md)
- [擴充繫結](../../../wcf/extending/extending-bindings.md)
- [自訂繫結](../../../wcf/extending/custom-bindings.md)
- [\<customBinding >](custombinding.md)
