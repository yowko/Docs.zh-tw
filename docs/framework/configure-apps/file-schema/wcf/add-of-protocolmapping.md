---
title: '&lt;protocolMapping&gt; 的 &lt;add&gt;'
ms.date: 03/30/2017
ms.assetid: 08e62249-1641-41d1-91b1-66d7b46244e4
ms.openlocfilehash: e21c3ca665d6a75394d70da43ec2044e00f16429
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145480"
---
# <a name="ltaddgt-of-ltprotocolmappinggt"></a>&lt;protocolMapping&gt; 的 &lt;add&gt;
代表傳輸通訊協定配置 （例如 http、 net.tcp、 net.pipe 等） 與 Windows Communication Foundation (WCF) 繫結之間的預設通訊協定對應。 當在執行階段建立預設端點，WCF 會查看所設定的對應，並決定哪些繫結，以使用特定基礎位址。  
  
 \<system.serviceModel>  
\<protocolMapping >  
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
  
|元素|描述|  
|-------------|-----------------|  
|繫結|指定在建立預設端點期間用於端點之繫結類型的字串。|  
|bindingConfiguration|指定要參考之繫結組態區段名稱的字串。|  
|scheme|要用於預設端點的傳輸通訊協定配置。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<protocolMapping >](../../../../../docs/framework/configure-apps/file-schema/wcf/protocolmapping.md)|表示組態區段，用於定義傳輸通訊協定配置 （例如 http、 net.tcp、 net.pipe 等） 和 Windows Communication Foundation (WCF) 繫結之間的預設通訊協定對應。|  
  
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
 <xref:System.ServiceModel.Configuration.ProtocolMappingSection?displayProperty=nameWithType>      
 <xref:System.ServiceModel.Configuration.ProtocolMappingElement?displayProperty=nameWithType>    
