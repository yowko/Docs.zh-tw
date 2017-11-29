---
title: "使用 ServiceThrottlingBehavior 來控制 WCF 服務效能"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: behavior [WCF], service performance
ms.assetid: f9dc120c-dc24-49d5-930e-b22f5bc73423
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 01f3815c095012d10fdfd56893125135c35f8009
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="using-servicethrottlingbehavior-to-control-wcf-service-performance"></a>使用 ServiceThrottlingBehavior 來控制 WCF 服務效能
<xref:System.ServiceModel.Description.ServiceThrottlingBehavior> 類別會公開可用來限制應用程式層級上所能建立之執行個體或工作階段數目的屬性。 您可以使用這個行為來微調 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 應用程式的效能。  
  
## <a name="controlling-service-instances-and-concurrent-calls"></a>控制服務執行個體及同時呼叫的數目  
 您可以使用 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> 屬性指定透過 <xref:System.ServiceModel.ServiceHost> 類別主動處理的訊息數目上限，並使用 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> 屬性來指定服務中 <xref:System.ServiceModel.InstanceContext> 物件的數目上限。  
  
 因為判斷這些屬性的設定通常會進行執行應用程式對實際的經驗後載入，設定<xref:System.ServiceModel.Description.ServiceThrottlingBehavior>屬性通常會指定在應用程式組態檔中使用[ \<serviceThrottling >](../../../../docs/framework/configure-apps/file-schema/wcf/servicethrottling.md)項目。  
  
 下列程式碼範例簡單示範如何從應用程式組態檔使用 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior> 類別，將 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentSessions%2A>、<xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> 和 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> 屬性設定為 1。 至於特定應用程式的最佳設定，則需要透過實際經驗來判斷。  
  
 [!code-xml[ServiceThrottlingBehavior#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/servicethrottlingbehavior/cs/hostapplication.exe.config#3)]  
  
 確切的執行階段行為將取決於 <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> 和 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> 屬性的值，因為這兩個屬性分別控制可在作業中同時執行的訊息數目，以及 <xref:System.ServiceModel.InstanceContext> 服務相對於傳入通道工作階段的存留期。  
  
 如需詳細資訊，請參閱 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentCalls%2A> 和 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A>。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>  
 <xref:System.ServiceModel.NetTcpBinding.MaxConnections%2A>
