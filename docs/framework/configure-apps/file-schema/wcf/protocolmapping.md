---
title: <protocolMapping>
ms.date: 03/30/2017
ms.assetid: 5076644b-1f33-4f26-9488-87de9fcda04c
ms.openlocfilehash: 6ec17457c8742fdf17208c6588e0ab70ece7c42a
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55268664"
---
# <a name="protocolmapping"></a>\<protocolMapping>
表示用於定義一組預設通訊協定之間的對應傳輸通訊協定配置 （例如 http、 net.tcp、 net.pipe 等） 和 WCF 繫結組態區段。 當在執行階段建立預設端點，Windows Communication Foundation (WCF) 會查看所設定的對應，並決定哪些繫結，以使用特定基礎位址。  
  
[**\<system.serviceModel>**](system-servicemodel.md)  
&nbsp;&nbsp;**\<protocolMapping>**  
  
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
 無。  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<filters>](filters-of-routing.md)|包含傳輸通訊協定配置 （例如 http、 net.tcp、 net.pipe 等） 與 WCF 繫結之間的預設通訊協定對應。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<system.serviceModel>](system-servicemodel.md)|所有 WCF 組態項目的根項目。|  
  
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
