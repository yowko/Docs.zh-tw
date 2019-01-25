---
title: '&lt;baseAddressPrefixFilters&gt;'
ms.date: 03/30/2017
ms.assetid: 8cab2a9a-c51f-4283-bb60-2ad0c274fd46
ms.openlocfilehash: 21a926d07aa818ce4ff5c2b85a04167fdd531047
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54667241"
---
# <a name="ltbaseaddressprefixfiltersgt"></a>&lt;baseAddressPrefixFilters&gt;
表示的組態項目會指定通過篩選器，提供一個機制，Windows Communication Foundation (WCF) 應用程式裝載在 IIS 時挑選適當的 Internet Information Services (IIS) 繫結的集合。  
  
> [!WARNING]
>  \<baseAddressPrefixFilters > 沒有辨識"localhost"，改為使用完整的電腦名稱。  
  
 \<system.ServiceModel>  
\<ServiceHostingEnvironment>  
  
## <a name="syntax"></a>語法  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
   </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddressprefixfilter.md)|新增組態項目，這個項目會指定由服務主機使用之基底位址的前置詞篩選條件。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<serviceHostingEnvironment>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|定義服務裝載環境為特定傳輸產生的類型。|  
  
## <a name="remarks"></a>備註  
 前置詞篩選條件為共用裝載提供者提供一種方式，使其可指定服務所要使用的 URI。 它可讓共用主機在同一個網站上裝載多個應用程式，而且同一個配置中可以有不同的基底位址。  
  
 IIS 網站是包含虛擬目錄的虛擬應用程式的容器 (Container)。 網站中的應用程式則可以透過一個或多個 IIS 繫結來存取。 IIS 繫結提供繫結通訊協定和繫結這兩項資訊。 繫結通訊協定 (例如 HTTP) 會定義產生通訊的配置，而繫結資訊 (例如 IPAddress、Port、Hostheader) 包含用來存取該網站的資料。  
  
 IIS 支援為每個網站指定多個 IIS 繫結，讓每個配置都有多個基底位址。 因為在網站下裝載的 WCF 服務可讓每個配置的繫結至一個基底位址，您可以使用前置詞篩選功能挑選裝載服務所需的基底位址。 IIS 提供的傳入基底位址會依據選擇性的前置詞清單篩選條件進行篩選。  
  
 例如，您的網站可能包含下列基底位址。  
  
```  
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 您可以使用下列組態檔在 appdomain 層級指定前置詞篩選條件。  
  
```xml  
<system.serviceModel>
  <serviceHostingEnvironment>
    <baseAddressPrefixFilters>
      <add prefix="net.tcp://test1.fabrikam.com:8000" />
      <add prefix="http://test2.fabrikam.com:9000" />
    </baseAddressPrefixFilters>
  </serviceHostingEnvironment>
</system.serviceModel>
```  
  
 在此範例中，`net.tcp://test1.fabrikam.com:8000` 和 `http://test2.fabrikam.com:9000` 分別是其配置的唯一基底位址，而且已被允許通過篩選。  
  
 根據預設，如果沒有指定前置詞，則所有位址都會通過。 如果指定前置詞，則只會允許要通過之配置的相符基底位址。  
  
> [!NOTE]
>  篩選條件不支援任何萬用字元。 此外，IIS 提供的 baseAddress 中，可能會有位址繫結至不在 `baseAddressPrefixFilters` 清單中的配置， 而且這些位址尚未經過篩選。  
  
## <a name="see-also"></a>另請參閱
- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [裝載](../../../../../docs/framework/wcf/feature-details/hosting.md)
