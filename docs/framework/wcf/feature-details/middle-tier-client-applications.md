---
title: 中介層用戶端應用程式
ms.date: 03/30/2017
ms.assetid: f9714a64-d0ae-4a98-bca0-5d370fdbd631
ms.openlocfilehash: 4cca832266b2eb2ab7b1b4eb1a5fe937525db97d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="middle-tier-client-applications"></a>中介層用戶端應用程式
本主題討論各種使用 Windows Communication Foundation (WCF) 的中介層用戶端應用程式的特定問題。  
  
## <a name="increasing-middle-tier-client-performance"></a>提升中介層用戶端效能  
 相較於先前的通訊技術，例如 Web 服務使用[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]，建立 WCF 用戶端執行個體可以是因為 WCF 的豐富功能集而更為複雜。 例如，<xref:System.ServiceModel.ChannelFactory%601> 物件開啟時，它可以和服務建立安全工作階段，而這個程序通常會增加用戶端執行個體的啟動時間。 一般而言，這些附加功能不會影響用戶端應用程式大幅因為 WCF 用戶端會進行數個呼叫，，然後關閉。  
  
 中介層用戶端應用程式，不過，可以快速建立許多 WCF 用戶端物件，如此一來，需要更高的初始化需求。 呼叫服務時，有兩種主要方式可以提高中介層應用程式的效能：  
  
-   快取的 WCF 用戶端物件，並重複使用的後續呼叫盡可能。  
  
-   建立<xref:System.ServiceModel.ChannelFactory%601>物件，然後使用該物件來建立新的 WCF 用戶端通道物件，每個呼叫。  
  
 使用這些方式時要考慮的問題：  
  
-   如果服務使用工作階段維護用戶端特定狀態，然後您無法重複使用的中介層 WCF 用戶端具有多個用戶端層要求因為服務的狀態與在的中介層用戶端。  
  
-   如果服務必須在每個用戶端執行驗證，您必須建立新的用戶端針對每個連入要求而勿重複使用的中介層 WCF 用戶端 （或 WCF 用戶端通道物件） 由於中介層上的中介層用戶端認證WCF 用戶端之後就無法修改 (或<xref:System.ServiceModel.ChannelFactory%601>) 已建立。  
  
-   當通道及其建立的用戶端為安全執行緒 (Thread-Safe) 時，它們可能不支援同時將一個以上的訊息寫入網路傳輸。 如果您正在傳送大型訊息，尤其是傳送資料流 (Streaming) 時，傳送作業可能會進入封鎖狀態而等候其他傳送作業完成。 這會產生兩種問題：無法並行存取，以及可能在控制流程返回重複使用通道的服務時發生死結 (Deadlock) 狀況 (亦即，共用用戶端呼叫某個服務，而這個服務的程式碼路徑又反過來回呼此共用用戶端)。 這是不論您重複使用的 WCF 用戶端的類型，則為 true。  
  
-   您必須處理已發生錯誤的通道，不論您是否共用該通道。 不過，在重複使用通道時，發生錯誤的通道可撤銷一個以上的暫止要求或傳送。  
  
 如需示範其最佳作法重複使用多個要求的用戶端的範例，請參閱[資料繫結的 ASP.NET 用戶端中](../../../../docs/framework/wcf/samples/data-binding-in-an-aspnet-client.md)。  
  
 此外，您還可以為那些使用可透過 <xref:System.Xml.Serialization.XmlSerializer> 加以序列化之資料型別的用戶端增進啟動效能。這些用戶端會在執行階段針對這些資料型別產生並編譯序列化程式碼，可能因此拖慢啟動效能。 [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)可以藉由從應用程式的編譯組件產生必要的序列化程式碼改善這些應用程式的啟動效能。 如需詳細資訊，請參閱[How to： 改善啟動時間的 WCF 用戶端應用程式使用 XmlSerializer](../../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用 WCF 用戶端存取服務](../../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md)
