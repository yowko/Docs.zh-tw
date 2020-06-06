---
title: '@ServiceHost'
ms.date: 03/30/2017
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
ms.openlocfilehash: fdd6d83836c4ef31a4d7c8e68cb0cc050ac6bea4
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "76787793"
---
# <a name="servicehost"></a>\@ServiceHost

將用來產生服務主機的處理站，與要裝載的服務和存取或編譯 .svc 檔案中提供的程式碼所需的其他程式設計方面加以關聯。

## <a name="syntax"></a>語法

```xml
<% @ServiceHost
Service = "Service, ServiceNamespace"
Factory = "Factory, FactoryNamespace"
Debug = "Debug"
Language = "Language"
CodeBehind = "CodeBehind"
%>
```

## <a name="attributes"></a>屬性

### <a name="service"></a>Service

所裝載之服務的 CLR 型別名稱。 這應該是實作一個以上的服務合約之型別的限定名稱。

### <a name="factory"></a>Factory

用來具現化服務主機的服務主機處理站之 CLR 型別名稱。 這是一個選擇性的屬性。 如果沒有指定，則使用預設的 <xref:System.ServiceModel.Activation.ServiceHostFactory>，它會傳回 <xref:System.ServiceModel.ServiceHost> 的執行個體。

### <a name="debug"></a>偵錯

指出是否應該使用 debug 符號來編譯 Windows Communication Foundation （WCF）服務。 `true`如果 WCF 服務應使用 debug 符號進行編譯，則為，否則為 `false` 。

### <a name="language"></a>Language

指定編譯檔案內 (.svc) 所有內嵌程式碼時使用的語言。 值可以代表任何。NET 支援的語言，包括 `C#` 、 `VB` 和 `JS` ，分別參考 c #、Visual Basic 和 JScript .net。 這是一個選擇性的屬性。

### <a name="codebehind"></a>CodeBehind

當實 XML Web Service 的類別不存在於相同的檔案中，而且尚未編譯成元件並放在*\bin*目錄中時，指定用來執行 XML Web Service 的原始程式檔。

## <a name="remarks"></a>備註

<xref:System.ServiceModel.ServiceHost>用來裝載服務的是 Windows Communication Foundation （WCF）程式設計模型內的擴充性點。 因為 <xref:System.ServiceModel.ServiceHost> 是潛在的多型型別，而裝載環境不應直接具現化多型型別，所以使用處理站模式加以具現化。

預設實作會使用 <xref:System.ServiceModel.Activation.ServiceHostFactory> 來建立 <xref:System.ServiceModel.ServiceHost> 的執行個體。 但是，您可以藉由在指示詞中指定 factory 的 CLR 型別名稱，來提供您自己的處理站（一個傳回您的衍生主機） `@ServiceHost` 。

若要使用您自己的自訂服務主機 factory，而不是預設的 factory，只要在指示詞中提供型別名稱，如下所示 `@ServiceHost` 。

```xml
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>
```

盡可能保持處理站實作的簡便。 假設您有許多自訂邏輯，那麼若您將邏輯放在主機而非處理站內，則這些程式碼就更能重複使用。

例如，若要啟用已啟用 AJAX 的端點 `MyService` ，請 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> 在指示詞中指定屬性值的， `Factory` 而不是預設的（ <xref:System.ServiceModel.Activation.ServiceHostFactory> `@ServiceHost` 如下列範例所示）：

```xml
<% @ServiceHost
Service="MyService"
Language="C#"
Debug="true"
Factory="WebScriptServiceHostFactory"
%>
```

## <a name="see-also"></a>另請參閱

- [自訂服務裝載](../../../wcf/samples/custom-service-host.md)
