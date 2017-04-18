---
title: "使用 ServiceThrottlingBehavior 來控制 WCF 服務效能 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "行為 [WCF] 時，服務效能"
ms.assetid: f9dc120c-dc24-49d5-930e-b22f5bc73423
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# 使用 ServiceThrottlingBehavior 來控制 WCF 服務效能
<xref:System.ServiceModel.Description.ServiceThrottlingBehavior>類別會公開可用來限制多少個執行個體或工作階段會建立應用程式層級的屬性。 您可以使用這個行為來微調 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 應用程式的效能。  
  
## <a name="controlling-service-instances-and-concurrent-calls"></a>控制服務執行個體及同時呼叫的數目  
 使用<xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A>屬性來指定上主動處理的訊息數目上限<xref:System.ServiceModel.ServiceHost>類別，而<xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A>屬性，以指定的最大數目<xref:System.ServiceModel.InstanceContext>服務中的物件。  
  
 因為通常決定這些屬性的設定執行應用程式的實際經驗之後會在進行載入，設定<xref:System.ServiceModel.Description.ServiceThrottlingBehavior>屬性通常指定應用程式組態檔中使用[ <> \> ](../../../../docs/framework/configure-apps/file-schema/wcf/servicethrottling.md)項目。  
  
 下列程式碼範例示範使用<xref:System.ServiceModel.Description.ServiceThrottlingBehavior>類別從應用程式組態檔設定<xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A>， <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A>，和<xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A>屬性設為 1 簡單。 至於特定應用程式的最佳設定，則需要透過實際經驗來判斷。  
  
 [!code-csharp[ServiceThrottlingBehavior#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/servicethrottlingbehavior/cs/hostapplication.exe.config#3)]  
  
 確切的執行階段行為的值取決於<xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>和<xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>屬性，以控制多少訊息可在執行的作業以及服務的存留期<xref:System.ServiceModel.InstanceContext>相對於傳入通道工作階段，分別。  
  
 如需詳細資訊，請參閱<xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A>，和<xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A>。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>   
 <xref:System.ServiceModel.NetTcpBinding.MaxConnections%2A>