---
title: <baseAddressPrefixFilters>
ms.date: 03/30/2017
ms.assetid: 8cab2a9a-c51f-4283-bb60-2ad0c274fd46
ms.openlocfilehash: 0673507b72690c3a5c7dcc35442c05e378dba43c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153031"
---
# <a name="baseaddressprefixfilters"></a>\<基本位址首碼篩選器>
表示指定傳遞篩選器的配置元素的集合，這些元素提供了在 IIS 中託管 Windows 通信基礎 （WCF） 應用程式時選擇適當 Internet 資訊服務 （IIS） 綁定的機制。  
  
> [!WARNING]
> \<基底位址首碼篩選器>無法識別"本地主機";改用完全限定的電腦名稱稱。  
  
[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<系統.服務模式>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<服務託管環境>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<基本位址首碼篩選器>**  
  
## <a name="syntax"></a>語法  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
   </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<添加>](add-of-baseaddressprefixfilter.md)|新增組態項目，這個項目會指定由服務主機使用之基底位址的前置詞篩選條件。|  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<服務託管環境>](servicehostingenvironment.md)|定義服務裝載環境為特定傳輸產生的類型。|  
  
## <a name="remarks"></a>備註  
 前置詞篩選條件為共用裝載提供者提供一種方式，使其可指定服務所要使用的 URI。 它可讓共用主機在同一個網站上裝載多個應用程式，而且同一個配置中可以有不同的基底位址。  
  
 IIS 網站是包含虛擬目錄的虛擬應用程式的容器 (Container)。 網站中的應用程式則可以透過一個或多個 IIS 繫結來存取。 IIS 繫結提供繫結通訊協定和繫結這兩項資訊。 繫結通訊協定 (例如 HTTP) 會定義產生通訊的配置，而繫結資訊 (例如 IPAddress、Port、Hostheader) 包含用來存取該網站的資料。  
  
 IIS 支援為每個網站指定多個 IIS 繫結，讓每個配置都有多個基底位址。 由於網站下託管的 WCF 服務允許為每個方案僅綁定到一個基本位址，因此可以使用首碼篩選器功能來選擇託管服務所需的基本位址。 IIS 提供的傳入基底位址會依據選擇性的前置詞清單篩選條件進行篩選。  
  
 例如，您的網站可以包含以下基本位址：
  
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
> 篩選條件不支援任何萬用字元。 此外，IIS 提供的 baseAddress 中，可能會有位址繫結程序至不在 `baseAddressPrefixFilters` 清單中的配置， 而且這些位址尚未經過篩選。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [裝載](../../../wcf/feature-details/hosting.md)
