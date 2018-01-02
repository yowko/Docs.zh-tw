---
title: "&lt;serviceActivations&gt; 的 &lt;add&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 956134f0db25055fb9a2f9317a770989cfdab67f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltserviceactivationsgt"></a>&lt;serviceActivations&gt; 的 &lt;add&gt;
組態項目，這個項目可讓您定義虛擬服務啟動設定，這些設定會對應至您的 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 服務型別。 如此一來，不需 .svc 檔案也能啟動裝載於 WAS/IIS 中的服務。  
  
 \<系統。ServiceModel >  
\<ServiceHostingEnvironment >  
  
## <a name="syntax"></a>語法  
  
```xml  
<serviceHostingEnvironment>   
   <serviceActivations>  
      <add factory="String"  
           service="String"/>  
   </serviceActivations>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|factory|字串，指定產生服務啟動項目之處理站的 CLR 型別名稱。|  
|服務|實作服務的 ServiceType 可以是完整 Typename 或簡短 Typename (置於 App_Code 資料夾時)。|  
|relativeAddress|在目前 IIS 應用程式中的相對位址，例如 "Service.svc"。 在 WCF 4.0 中，此相對位址必須包含其中一個已知的副檔名 (.svc、.xamlx...)。relativeUrl 不一定要有實體檔案存在|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<serviceHostingEnvironment >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|描述啟動設定的組態區段。|  
  
## <a name="remarks"></a>備註  
 下列範例示範如何在您的 web.config 檔案中設定啟動設定。  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <serviceHostingEnvironment>  
      <serviceActivations>  
        <add service="GreetingService"/>  
      </serviceActivations>  
    </serviceHostingEnvironment>  
  </system.serviceModel>  
</configuration>  
```  
  
 使用這個組態時，您不需要使用 .svc 檔案也可以啟動 GreetingService。  
  
 請注意，`<serviceHostingEnvironment>` 是應用程式層級的組態。 您必須將包含該組態的 `web.config` 置於虛擬應用程式的根之下。 此外，`serviceHostingEnvironment` 是 machinetoApplication 可繼承的區段。 如果在電腦的根中註冊單一服務，則應用程式中的每個服務都會繼承這個服務。  
  
 以組態為主的啟動支援透過 HTTP 和非 HTTP 通訊協定啟動。 這項作業需要 relatativeAddress 中的擴充，也就是 .svc、.xoml 或 .xamlx。 您可以將自己的擴充對應至已知的 buildProvider，這樣您就可以透過任何擴充啟動服務。 發生衝突時，`<serviceActivations>` 區段會覆寫 .svc 註冊。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.ServiceModel.Configuration.ServiceActivationElement>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>
