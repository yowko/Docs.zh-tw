---
title: 中介層用戶端應用程式
ms.date: 03/30/2017
ms.assetid: f9714a64-d0ae-4a98-bca0-5d370fdbd631
ms.openlocfilehash: c50223a55765f211dae710f96bffa7716ce36b32
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598810"
---
# <a name="middle-tier-client-applications"></a>中介層用戶端應用程式
本主題討論使用 Windows Communication Foundation （WCF）之仲介層用戶端應用程式特定的各種問題。  
  
## <a name="increasing-middle-tier-client-performance"></a>提升中介層用戶端效能  
 相較于先前的通訊技術（例如使用 ASP.NET 的 Web 服務），wcf 用戶端實例的建立可能會因為 WCF 的豐富功能集而更複雜。 例如，<xref:System.ServiceModel.ChannelFactory%601> 物件開啟時，它可以和服務建立安全工作階段，而這個程序通常會增加用戶端執行個體的啟動時間。 一般而言，這些額外的功能不會影響用戶端應用程式，因為 WCF 用戶端會進行數次呼叫，然後關閉。  
  
 不過，仲介層用戶端應用程式可以快速建立許多 WCF 用戶端物件，因此會有更高的初始化需求。 呼叫服務時，有兩種主要方式可以提高中介層應用程式的效能：  
  
- 快取 WCF 用戶端物件，並在可能的後續呼叫中重複使用它。  
  
- 建立 <xref:System.ServiceModel.ChannelFactory%601> 物件，然後使用該物件為每個呼叫建立新的 WCF 用戶端通道物件。  
  
 使用這些方式時要考慮的問題：  
  
- 如果服務使用會話來維護用戶端特定的狀態，您就無法重複使用中介層 WCF 用戶端與多個用戶端層要求，因為服務的狀態會系結至仲介層用戶端的狀態。  
  
- 如果服務必須以每個用戶端為基礎執行驗證，您必須針對仲介層上的每個傳入要求建立新的用戶端，而不是重複使用仲介層 WCF 用戶端（或 WCF 用戶端通道物件），因為在建立 WCF 用戶端（或）之後，無法修改仲介層的用戶端認證 <xref:System.ServiceModel.ChannelFactory%601> 。  
  
- 當通道及其建立的用戶端為安全執行緒 (Thread-Safe) 時，它們可能不支援同時將一個以上的訊息寫入網路傳輸。 如果您正在傳送大型訊息，尤其是傳送資料流 (Streaming) 時，傳送作業可能會進入封鎖狀態而等候其他傳送作業完成。 這會產生兩種問題：無法並行存取，以及可能在控制流程返回重複使用通道的服務時發生死結 (Deadlock) 狀況 (亦即，共用用戶端呼叫某個服務，而這個服務的程式碼路徑又反過來回呼此共用用戶端)。 無論您重複使用的 WCF 用戶端類型為何，都是如此。  
  
- 您必須處理已發生錯誤的通道，不論您是否共用該通道。 不過，在重複使用通道時，發生錯誤的通道可撤銷一個以上的暫止要求或傳送。  
  
 如需示範針對多個要求重複使用用戶端之最佳作法的範例，請參閱[ASP.NET 用戶端中的資料](../samples/data-binding-in-an-aspnet-client.md)系結。  
  
 此外，您還可以為那些使用可透過 <xref:System.Xml.Serialization.XmlSerializer> 加以序列化之資料型別的用戶端增進啟動效能。這些用戶端會在執行階段針對這些資料型別產生並編譯序列化程式碼，可能因此拖慢啟動效能。 [System.servicemodel 中繼資料公用程式工具（Svcutil）](../servicemodel-metadata-utility-tool-svcutil-exe.md)可以從應用程式的已編譯元件產生必要的序列化程式碼，以改善這些應用程式的啟動效能。 如需詳細資訊，請參閱[如何：使用 XmlSerializer 改善 WCF 用戶端應用程式的啟動時間](startup-time-of-wcf-client-applications-using-the-xmlserializer.md)。  
  
## <a name="see-also"></a>請參閱

- [使用 WCF 用戶端存取服務](accessing-services-using-a-client.md)
