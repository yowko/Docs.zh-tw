---
title: 控制資源使用並改善效能
ms.date: 03/30/2017
ms.assetid: 9a829669-5f76-4c88-80ec-92d0c62c0660
ms.openlocfilehash: 11d1333ed0ae8b46f8f87fa6f4643d4b31fac3ff
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54664157"
---
# <a name="controlling-resource-consumption-and-improving-performance"></a>控制資源使用並改善效能
本主題說明 Windows Communication Foundation (WCF) 架構的運作，以控制資源耗用量並影響效能度量資訊的不同區域中的各種屬性。

## <a name="properties-that-constrain-resource-consumption-in-wcf"></a>WCF 中限制資源消耗的屬性
 Windows Communication Foundation (WCF) 適用於特定類型的處理程序，基於安全性或效能條件約束。 這些限制主要有兩種形式，可能是配額與節流閥。 *配額*達到或超過閾值時觸發立即的例外狀況在某個時間點，系統中的限制。 *節流*都不會立即造成擲回例外狀況的限制。 相反地，當達到節流閥限制時，仍將持續處理，但會在節流閥的值所設定的限制範圍內。 此限制處理可能在其他地方觸發例外狀況，不過需視應用程式而定。

 除了配額與節流閥之間的差異外，有些限制屬性位於序列化層級，有些位於傳輸層級，有些則在應用程式層級。 例如，全由系統提供的傳輸繫結項目實作之 <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A?displayProperty=nameWithType> 配額，預設為 65,536 位元組，防止惡意用戶端利用消耗過多記憶體的方式，對服務發動阻絕服務攻擊  (一般而言，您可調低此值以增進效能)。

 序列化配額的範例為 <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> 屬性，這種屬性會指定序列化程式在單一 <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A> 方法呼叫中，序列化或還原序列化的物件最大數量。 應用程式層級的節流閥範例為 <xref:System.ServiceModel.Dispatcher.ServiceThrottle.MaxConcurrentSessions%2A?displayProperty=nameWithType> 屬性，其預設的同時工作階段通道連線數為 10  (與配額不同，若達到此節流閥值，應用程式會持續處理，但不接受新工作階段通道，也就是說在其他工作階段通道結束之前，新用戶端將無法連接)。

 這些控制項在設計上是要提供緩和特定類型攻擊的現成方法，或是改善效能度量資訊，例如記憶體使用量、啟動時間等等。 然而，根據應用程式而定，這些控制項會阻礙服務應用程式的效能，甚至造成應用程式無法運作。 例如，設計處理視訊資料流的應用程式，可能很容易就超過預設的 <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A?displayProperty=nameWithType> 屬性。 本主題提供的各種控制項概觀套用至所有層級的 WCF 應用程式、 描述各種取得設定是否妨礙應用程式的詳細資訊，以及描述修正各種問題的方式。 多數節流閥與某些配額可在應用程式層級取得，即使基底屬性為序列化或傳輸限制。 例如，您可設定 <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> 屬性使用服務類別上的 <xref:System.ServiceModel.ServiceBehaviorAttribute.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> 屬性。

> [!NOTE]
> 如果您有特定問題，您應該先閱讀[WCF 疑難排解快速入門](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md)以查看您的問題 （及解決方法） 清單中是否那里。

 限制序列化程序的屬性會列在[資料的安全性考量](../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)。 限制傳輸相關資源的耗用量的屬性會列在[傳輸配額](../../../docs/framework/wcf/feature-details/transport-quotas.md)。 限制消耗應用程式層資源的屬性為 <xref:System.ServiceModel.Dispatcher.ServiceThrottle> 類別之成員。

## <a name="detecting-application-and-performance-issues-related-to-quota-settings"></a>偵測應用程式及與配額設定值相關的效能問題
 上述值的預設值選取原則是讓各種應用程式類別都能有基本應用程式功能，同時提供對一般安全性問題的基本保護。 然而，不同應用程式的設計可能會超出一個或更多個節流閥的設定值 (雖然在其他方面，應用程式依然安全，且一如往常般運作)。 出現這些狀況時，您必須找出是哪些節流閥值被超過以及超過多少，然後決定應對方法以增加應用程式的輸送量。

 一般而言，撰寫應用程式與偵錯時，您會在組態檔或以程式設計的方式，將 <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> 屬性設為 `true`。 這會指示 WCF 在用戶端應用程式，以檢視會傳回服務例外狀況堆疊追蹤。 此功能會報告多數的應用程式層級例外狀況，顯示可能造成問題的配額值 (若該值為問題所在)。

 有些例外狀況會在執行階段在低於應用程式層可見範圍之下發生，並且無法使用此機制傳回，這些例外可能無法透過自訂的 <xref:System.ServiceModel.Dispatcher.IErrorHandler?displayProperty=nameWithType> 實作來處理。 如果您處於像是 Microsoft Visual Studio 的開發環境之下，這些例外狀況大多會自動顯示。 不過，某些例外狀況可以加上遮罩的開發環境設定，例如[Just My Code](/visualstudio/debugger/just-my-code) Visual Studio。

 不論您的開發環境的功能，您可以使用 WCF 追蹤和訊息記錄的功能來偵錯所有例外狀況，並調整您的應用程式的效能。 如需詳細資訊，請參閱 <<c0> [ 使用疑難排解您的應用程式追蹤](../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md)。

## <a name="performance-issues-and-xmlserializer"></a>效能問題與 XmlSerializer
 使用資料型別 (可使用 <xref:System.Xml.Serialization.XmlSerializer> 加以序列化) 的服務和用戶端應用程式會在執行階段針對這些資料型別產生和編譯序列化程式碼，這可能會導致啟動的效能變慢。

> [!NOTE]
> 預先產生的序列化程式碼只能用於用戶端應用程式中，而不能用於服務中。

 [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)可改善這些應用程式的啟動效能，藉由從應用程式編譯的組件產生必要的序列化程式碼。 如需詳細資訊，請參閱[＜How to：改善啟動時間的 WCF 用戶端應用程式的使用 XmlSerializer](../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)。

## <a name="performance-issues-when-hosting-wcf-services-under-aspnet"></a>在 ASP.NET 下裝載 WCF 服務時的效能問題
 在 IIS 和 ASP.NET 下裝載 WCF 服務時，IIS 和 ASP.NET 的組態設定可能會影響 WCF 服務的處理量和記憶體使用量。  如需有關 ASP.NET 效能的詳細資訊，請參閱[提升 ASP.NET 效能](https://go.microsoft.com/fwlink/?LinkId=186462)。  一個可能會造成意外結果的設定是 <xref:System.Web.Configuration.ProcessModelSection.MinWorkerThreads%2A> 的屬性 <xref:System.Web.Configuration.ProcessModelSection>。 如果您的應用程式有固定或少量的用戶端，將 <xref:System.Web.Configuration.ProcessModelSection.MinWorkerThreads%2A> 設定為 2 可能會讓 CPU 使用率接近 100% 的多處理器電腦提高處理量。 但提高效能有其代價：這也會造成記憶體使用量增加，因而減少延展性。

## <a name="see-also"></a>另請參閱

- [管理與診斷](../../../docs/framework/wcf/diagnostics/index.md)
- [大型資料和資料流](../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)
