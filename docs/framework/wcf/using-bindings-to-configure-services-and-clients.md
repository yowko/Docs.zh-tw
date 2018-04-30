---
title: 使用繫結來設定服務和用戶端
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- bindings [WCF], using
ms.assetid: c39479c3-0766-4a17-ba4c-97a74607f392
caps.latest.revision: 33
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 68c8c2c93ce29147247c332848025fd931bf7854
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2018
---
# <a name="using-bindings-to-configure-services-and-clients"></a>使用繫結來設定服務和用戶端
繫結是指定連接端點所需要之通訊詳細資料的物件。 更明確的說，繫結包含藉由定義傳輸、網路格式 (訊息編碼) 的細節，用於建立用戶端或服務執行階段的組態資訊，以及用於個別端點或用戶端通道的通訊協定。 如果要建立可以運作的 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 服務，服務中每個端點都需要繫結。 本主題將說明什麼是繫結、如何定義繫結，以及如何為端點指定特定繫結。  
  
## <a name="what-a-binding-defines"></a>繫結所定義的內容  
 繫結中的資訊可能很基本，也可能很複雜。 最基本的繫結只會指定連線至端點時必須使用的傳輸通訊協定 (例如 HTTP)。 說的更簡單一點，繫結中所含有關如何連線至端點的資訊，屬於下表其中一種類別。  
  
 通訊協定  
 判斷使用的安全性機制，是可靠的傳訊能力或交易內容流量設定。  
  
 Transport  
 判斷要使用的基礎傳輸通訊協定 (例如，TCP 或 HTTP)。  
  
 編碼  
 判斷訊息編碼，例如 text/XML、二進位或 Message Transmission Optimization Mechanism (MTOM)，它會決定在網路上如何將訊息表示為位元組資料流。  
  
## <a name="system-provided-bindings"></a>系統提供的繫結  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 包括一組系統提供的繫結，設計來涵蓋大部分的應用程式需求和案例。 下列類別則表示系統提供之繫結的一些範例：  
  
-   <xref:System.ServiceModel.BasicHttpBinding>：一種 HTTP 通訊協定繫結，適用於連線至 Web 服務，並符合 WS-I Basic Profile 1.1 規格 (例如，以 ASP.NET Web 服務 [ASMX] 為基礎的服務)。  
  
-   <xref:System.ServiceModel.WSHttpBinding>：一種 HTTP 通訊協定繫結，適用於連線至符合 Web 服務規格通訊協定的端點。  
  
-   <xref:System.ServiceModel.NetNamedPipeBinding>：使用 .NET 二進位編碼和框架技術搭配 Windows 具名管道傳輸以連線至相同電腦上的其他 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 端點。  
  
-   <xref:System.ServiceModel.NetMsmqBinding>：使用 .NET 二進位編碼和框架技術搭配訊息佇列 (亦稱為 MSMQ)，以建立與其他 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 端點的佇列訊息連線。  
  
 如需完整的系統提供繫結，並說明，請參閱[之繫結](../../../docs/framework/wcf/system-provided-bindings.md)。  
  
## <a name="custom-bindings"></a>自訂繫結  
 如果系統提供的繫結集合沒有服務應用程式所需的正確功能組合，您可以建立 <xref:System.ServiceModel.Channels.CustomBinding> 繫結。 如需有關的項目<xref:System.ServiceModel.Channels.CustomBinding>繫結，請參閱[ \<customBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)和[自訂繫結](../../../docs/framework/wcf/extending/custom-bindings.md)。  
  
## <a name="using-bindings"></a>使用繫結  
 使用繫結牽涉到兩個基本步驟：  
  
1.  選取或定義繫結。 最簡單的方法是選擇其中一個系統提供的繫結，並使用其預設值。 也可以選擇系統提供的繫結，並重設其屬性值以符合您的需求。 或者，您可以建立自訂繫結並依需要設定每個屬性。  
  
2.  請建立使用這個繫結的端點。  
  
## <a name="code-and-configuration"></a>程式碼和組態  
 您可以透過程式碼或組態來定義或設定繫結。 這兩種方法與所使用的繫結型別無關，例如，您是否使用系統提供的或 <xref:System.ServiceModel.Channels.CustomBinding> 繫結。 一般來說，使用程式碼可讓您在編譯時完全控制繫結的定義。 另一方面，使用組態可讓系統管理員或 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務或用戶端的使用者變更繫結的參數。 這種彈性常常是有需要的，因為沒有辦法可以預測要部署 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 應用程式的特定電腦需求和網路狀況。 將繫結 (和位址) 資訊和程式碼分開可讓系統管理員變更繫結詳細資料，而不需要重新編譯或重新部署應用程式。 請注意，如果繫結是以程式碼定義的，它會覆寫組態檔中任何以組態為基礎所做的定義。 如需這些方法的範例，請參閱下列主題：  
  
-   [如何： 將 WCF 服務裝載於受管理的應用程式](../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)提供的範例程式碼中建立繫結。  
  
-   [如何： 設定用戶端](../../../docs/framework/wcf/how-to-configure-a-basic-wcf-client.md)提供建立使用設定的用戶端的範例。  
  
## <a name="see-also"></a>另請參閱  
 [建立端點概觀](../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [如何：在設定中指定服務繫結](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)  
 [如何：在程式碼中指定服務繫結](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-code.md)  
 [如何：在設定中指定用戶端繫結](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md)  
 [如何：在程式碼中指定用戶端繫結](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-code.md)
