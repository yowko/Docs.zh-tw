---
title: '@ServiceHost'
ms.date: 03/30/2017
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
ms.openlocfilehash: 730b1188a95d0e35d7431d43884e867e5520585e
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46320306"
---
# <a name="servicehost"></a>\@ServiceHost
將用來產生服務主機的處理站，與要裝載的服務和存取或編譯 .svc 檔案中提供的程式碼所需的其他程式設計方面加以關聯。  
  
## <a name="syntax"></a>語法  
  
```  
<% @ServiceHost   
Service = "Service, ServiceNamespace"   
Factory = "Factory, FactoryNamespace"  
Debug = "Debug"  
Language = "Language"   
CodeBehind = "CodeBehind"%>  
```  
  
## <a name="attributes"></a>屬性  
  
#### <a name="service"></a>服務  
 所裝載之服務的 CLR 型別名稱。 這應該是實作一個以上的服務合約之型別的限定名稱。  
  
#### <a name="factory"></a>Factory  
 用來具現化服務主機的服務主機處理站之 CLR 型別名稱。 這是一個選擇性的屬性。 如果沒有指定，則使用預設的 <xref:System.ServiceModel.Activation.ServiceHostFactory>，它會傳回 <xref:System.ServiceModel.ServiceHost> 的執行個體。  
  
#### <a name="debug"></a>偵錯  
 表示 Windows Communication Foundation (WCF) 服務是否應該使用偵錯符號進行編譯。 `true` 如果應該以偵錯符號; 編譯的 WCF 服務否則， `false`。  
  
#### <a name="language"></a>語言  
 指定編譯檔案內 (.svc) 所有內嵌程式碼時使用的語言。 這些值可以表示任何 .NET 支援的語言，包括 C#、VB 和 JS (分別指 C#、Visual Basic .NET 和 JScript .NET)。 這是一個選擇性的屬性。  
  
#### <a name="codebehind"></a>CodeBehind  
 當實作 XML Web Service 的類別不是存放在相同的檔案中，且尚未編譯為組件並置於 \Bin 目錄內的時候，請指定實作 XML Web Service 的原始程式檔。  
  
## <a name="remarks"></a>備註  
 <xref:System.ServiceModel.ServiceHost>用來裝載服務是 Windows Communication Foundation (WCF) 的程式設計模型中的擴充點。 因為 <xref:System.ServiceModel.ServiceHost> 是潛在的多型型別，而裝載環境不應直接具現化多型型別，所以使用處理站模式加以具現化。  
  
 預設實作會使用 <xref:System.ServiceModel.Activation.ServiceHostFactory> 來建立 <xref:System.ServiceModel.ServiceHost> 的執行個體。 您可以指定在您處理站實作的 CLR 型別名稱，以提供您自己的處理站 （會傳回衍生的主機），但[ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)指示詞。  
  
 若要使用您自己的自訂服務主機處理站而非預設處理站，只提供中的類型名稱[ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)指示詞，如下所示：  
  
```xml  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 盡可能保持處理站實作的簡便。 假設您有許多自訂邏輯，那麼若您將邏輯放在主機而非處理站內，則這些程式碼就更能重複使用。  
  
 例如，若要啟用的啟用 AJAX 的端點`MyService`，指定<xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>的值`Factory`屬性，而非預設<xref:System.ServiceModel.Activation.ServiceHostFactory>，請在[ @ServiceHost ](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)為指示詞下列範例所示。  
  
## <a name="example"></a>範例  
  
```  
<% @ServiceHost   
Service="MyService"  
Language="C#"  
Debug="true"  
Factory="WebScriptServiceHostFactory"  
%>  
```  
  
## <a name="see-also"></a>另請參閱  
 [自訂服務主機](../../../../../docs/framework/wcf/samples/custom-service-host.md)
