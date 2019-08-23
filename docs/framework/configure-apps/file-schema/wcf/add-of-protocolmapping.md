---
title: <add> 的 <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 08e62249-1641-41d1-91b1-66d7b46244e4
ms.openlocfilehash: df69b5f8a79489b722c1074f118b9c6f6e8e363d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926662"
---
# <a name="add-of-protocolmapping"></a>\<新增 protocolMapping > \<的 >
代表傳輸通訊協定配置 (例如 HTTP、net.tcp、net.pipe 等) 和 Windows Communication Foundation (WCF) 系結之間的預設通訊協定對應。 在執行時間建立預設端點時, WCF 會查看設定的對應, 並決定要用於特定位址的系結。  
  
 \<system.serviceModel>  
\<protocolMapping>  
\<add>  
  
## <a name="syntax"></a>語法  
  
```xml  
<protocolMapping>
  <add binding="String"
       bindingConfiguration="String"
       scheme="http/net.msmq/net.pipe/net.tcp" />
</protocolMapping>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|項目|描述|  
|-------------|-----------------|  
|繫結|指定在建立預設端點期間用於端點之繫結類型的字串。|  
|bindingConfiguration|指定要參考之繫結組態區段名稱的字串。|  
|scheme|要用於預設端點的傳輸通訊協定配置。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<protocolMapping>](protocolmapping.md)|代表設定區段, 用於定義傳輸通訊協定配置 (例如 HTTP、net.tcp、net.pipe 等) 和 Windows Communication Foundation (WCF) 系結之間的預設通訊協定對應。|  
  
## <a name="example"></a>範例  
 下列組態範例示範 machine.config 檔案中的預設通訊協定對應。 您可以透過修改 machine.config 檔案，在電腦層級覆寫這個預設對應。 或者，如果您只想在應用程式範圍內覆寫該預設對應，也可以覆寫應用程式組態檔中的這個區段，並且變更個別通訊協定配置的對應。  
  
```xml  
<protocolMapping>
  <add scheme="http"
       binding="basicHttpBinding" />
  <add scheme="net.tcp"
       binding="netTcpBinding" />
  <add scheme="net.pipe"
       binding="netNamedPipeBinding" />
  <add scheme="net.msmq"
       binding="netMsmqBinding" />
</protocolMapping>
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>
