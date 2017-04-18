---
title: "@ServiceHost | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# @ServiceHost
將用來產生服務主機的處理站，與要裝載的服務和存取或編譯 .svc 檔案中提供的程式碼所需的其他程式設計方面加以關聯。  
  
## 語法  
  
```  
  
<% @ServiceHost   
Service = "Service, ServiceNamespace"   
Factory = "Factory, FactoryNamespace"  
Debug = "Debug"  
Language = "Language"   
CodeBehind = "CodeBehind"%>  
```  
  
## 屬性  
  
#### 服務  
 所裝載之服務的 CLR 型別名稱。  這應該是實作一個以上的服務合約之型別的限定名稱。  
  
#### Factory  
 用來具現化服務主機的服務主機處理站之 CLR 型別名稱。  這是一個選擇性的屬性。  如果沒有指定，則使用預設的 <xref:System.ServiceModel.Activation.ServiceHostFactory>，它會傳回 <xref:System.ServiceModel.ServiceHost> 的執行個體。  
  
#### 偵錯  
 表示 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 服務是否應該使用偵錯符號進行編譯。  如果 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 服務應以偵錯符號編譯，則為 `true`，否則為 `false`。  
  
#### 語言  
 指定編譯檔案內 \(.svc\) 所有內嵌程式碼時使用的語言。  這些值可以表示任何 .NET 支援的語言，包括 C\#、VB 和 JS \(分別指 C\#、Visual Basic .NET 和 JScript .NET\)。  這是一個選擇性的屬性。  
  
#### CodeBehind  
 當實作 XML Web Service 的類別不是存放在相同的檔案中，且尚未編譯為組件並置於 \\Bin 目錄內的時候，請指定實作 XML Web Service 的原始程式檔。  
  
## 備註  
 用來裝載服務的 <xref:System.ServiceModel.ServiceHost> 是 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 程式設計模型中的擴充點。  因為 <xref:System.ServiceModel.ServiceHost> 是潛在的多型型別，而裝載環境不應直接具現化多型型別，所以使用處理站模式加以具現化。  
  
 預設實作會使用 <xref:System.ServiceModel.Activation.ServiceHostFactory> 來建立 <xref:System.ServiceModel.ServiceHost> 的執行個體。  但您可在 [@ServiceHost](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) 指示詞中指定處理站實作的 CLR 型別名稱，藉此提供您自己的處理站 \(會傳回您的衍生主機之處理站\)。  
  
 若要使用您自己的自訂服務主機處理站而非預設處理站，請依下列方式在 [@ServiceHost](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) 指示詞中提供型別名稱︰  
  
```  
<% @ServiceHost Factory=”DerivedFactory” Service=”MyService” %>  
```  
  
 盡可能保持處理站實作的簡便。  假設您有許多自訂邏輯，那麼若您將邏輯放在主機而非處理站內，則這些程式碼就更能重複使用。  
  
 例如，若要針對 `MyService` 啟用具備 AJAX 能力的端點，請在 [@ServiceHost](../../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) 指示詞內，對 `Factory` 屬性之值指定 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>，而不要使用預設的 <xref:System.ServiceModel.Activation.ServiceHostFactory>，如下列範例所示。  
  
## 範例  
  
```  
<% @ServiceHost   
Service="MyService"  
Language="C#"  
Debug="true"  
Factory="WebScriptServiceHostFactory"  
%>  
```  
  
## 請參閱  
 [自訂服務裝載](../../../../../docs/framework/wcf/samples/custom-service-host.md)