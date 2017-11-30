---
title: "控制資源使用並改善效能"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a829669-5f76-4c88-80ec-92d0c62c0660
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d11cc876ba6fc9dcd94a88ebcde18b4bd13797de
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="controlling-resource-consumption-and-improving-performance"></a>控制資源使用並改善效能
此主題描述 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 架構的不同領域中，用於控制資源消耗並影響效能度量資訊的各種屬性。  
  
## <a name="properties-that-constrain-resource-consumption-in-wcf"></a>WCF 中限制資源消耗的屬性  
 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 因安全或效能的考量，對特定型別的程序加以限制。 這些限制主要有兩種形式，可能是配額與節流閥。 *配額*當達到或超過觸發立即例外狀況在某個時間點，系統中的限制。 *會先調節*都不會立即造成擲回例外狀況的限制。 相反地，當達到節流閥限制時，仍將持續處理，但會在節流閥的值所設定的限制範圍內。 此限制處理可能在其他地方觸發例外狀況，不過需視應用程式而定。  
  
 除了配額與節流閥之間的差異外，有些限制屬性位於序列化層級，有些位於傳輸層級，有些則在應用程式層級。 例如，全由系統提供的傳輸繫結項目實作之 <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A?displayProperty=nameWithType> 配額，預設為 65,536 位元組，防止惡意用戶端利用消耗過多記憶體的方式，對服務發動阻絕服務攻擊  (一般而言，您可調低此值以增進效能)。  
  
 序列化配額的範例為 <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> 屬性，這種屬性會指定序列化程式在單一 <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A> 方法呼叫中，序列化或還原序列化的物件最大數量。 應用程式層級的節流閥範例為 <xref:System.ServiceModel.Dispatcher.ServiceThrottle.MaxConcurrentSessions%2A?displayProperty=nameWithType> 屬性，其預設的同時工作階段通道連線數為 10  (與配額不同，若達到此節流閥值，應用程式會持續處理，但不接受新工作階段通道，也就是說在其他工作階段通道結束之前，新用戶端將無法連接)。  
  
 這些控制項在設計上是要提供緩和特定類型攻擊的現成方法，或是改善效能度量資訊，例如記憶體使用量、啟動時間等等。 然而，根據應用程式而定，這些控制項會阻礙服務應用程式的效能，甚至造成應用程式無法運作。 例如，設計處理視訊資料流的應用程式，可能很容易就超過預設的 <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A?displayProperty=nameWithType> 屬性。 此主題提供適用於 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 所有層級應用程式之各種控制項的概觀，描述各種取得設定是否妨礙應用程式之詳細資訊的方法，以及描述修正各種問題的方法。 多數節流閥與某些配額可在應用程式層級取得，即使基底屬性為序列化或傳輸限制。 例如，您可設定 <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> 屬性使用服務類別上的 <xref:System.ServiceModel.ServiceBehaviorAttribute.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> 屬性。  
  
> [!NOTE]
>  如果您有特定問題，您應該先閱讀[WCF 疑難排解快速入門](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md)以查看您的問題 （和解決方案） 清單中是否那里。  
  
 屬性，以限制序列化程序所述[資料的安全性考量](../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)。 中所列的屬性，以限制與傳輸相關的資源耗用量[傳輸配額](../../../docs/framework/wcf/feature-details/transport-quotas.md)。 限制消耗應用程式層資源的屬性為 <xref:System.ServiceModel.Dispatcher.ServiceThrottle> 類別之成員。  
  
## <a name="detecting-application-and-performance-issues-related-to-quota-settings"></a>偵測應用程式及與配額設定值相關的效能問題  
 上述值的預設值選取原則是讓各種應用程式類別都能有基本應用程式功能，同時提供對一般安全性問題的基本保護。 然而，不同應用程式的設計可能會超出一個或更多個節流閥的設定值 (雖然在其他方面，應用程式依然安全，且一如往常般運作)。 出現這些狀況時，您必須找出是哪些節流閥值被超過以及超過多少，然後決定應對方法以增加應用程式的輸送量。  
  
 一般而言，撰寫應用程式與偵錯時，您會在組態檔或以程式設計的方式，將 <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> 屬性設為 `true`。 如此會指示 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 傳回服務例外狀況堆疊，追蹤至用戶端應用程式加以檢視。 此功能會報告多數的應用程式層級例外狀況，顯示可能造成問題的配額值 (若該值為問題所在)。  
  
 有些例外狀況會在執行階段在低於應用程式層可見範圍之下發生，並且無法使用此機制傳回，這些例外可能無法透過自訂的 <xref:System.ServiceModel.Dispatcher.IErrorHandler?displayProperty=nameWithType> 實作來處理。 如果您處於像是 Microsoft Visual Studio 的開發環境之下，這些例外狀況大多會自動顯示。 不過，有些例外狀況可以而被掩蓋開發環境設定，例如[Just My Code](http://go.microsoft.com/fwlink/?LinkId=82174) Visual Studio 2005 中的設定。  
  
 不論您開發環境的功能如何，您都可以使用 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 追蹤與訊息記錄功能偵錯所有例外狀況，並調整應用程式的效能。 如需詳細資訊，請參閱[使用追蹤疑難排解您的應用程式](../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)。  
  
## <a name="performance-issues-and-xmlserializer"></a>效能問題與 XmlSerializer  
 使用資料型別 (可使用 <xref:System.Xml.Serialization.XmlSerializer> 加以序列化) 的服務和用戶端應用程式會在執行階段針對這些資料型別產生和編譯序列化程式碼，這可能會導致啟動的效能變慢。  
  
> [!NOTE]
>  預先產生的序列化程式碼只能用於用戶端應用程式中，而不能用於服務中。  
  
 [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)可以藉由從應用程式的編譯組件產生必要的序列化程式碼改善這些應用程式的啟動效能。 如需詳細資訊，請參閱[How to： 改善啟動時間的 WCF 用戶端應用程式使用 XmlSerializer](../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)。  
  
## <a name="performance-issues-when-hosting-wcf-services-under-aspnet"></a>在 ASP.NET 下裝載 WCF 服務時的效能問題  
 在 IIS 和 ASP.NET 下裝載 WCF 服務時，IIS 和 ASP.NET 的組態設定可能會影響 WCF 服務的處理量和記憶體使用量。  [!INCLUDE[crabout](../../../includes/crabout-md.md)]ASP.NET 的效能，請參閱[改善 ASP.NET 效能](http://go.microsoft.com/fwlink/?LinkId=186462)。  一個可能會造成意外結果的設定是 <xref:System.Web.Configuration.ProcessModelSection.MinWorkerThreads%2A> 的屬性 <xref:System.Web.Configuration.ProcessModelSection>。 如果您的應用程式有固定或少量的用戶端，將 <xref:System.Web.Configuration.ProcessModelSection.MinWorkerThreads%2A> 設定為 2 可能會讓 CPU 使用率接近 100% 的多處理器電腦提高處理量。 但提高效能有其代價：這也會造成記憶體使用量增加，因而減少延展性。  
  
## <a name="see-also"></a>另請參閱  
 [管理與診斷](../../../docs/framework/wcf/diagnostics/index.md)  
 [大型的資料與資料流](../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)
