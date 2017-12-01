---
title: "決定何時實作事件架構非同步模式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: a00046aa-785d-4f7f-a8e5-d06475ea50da
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 48de1b736c251a61a2ad34975c77bc2bca139626
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="deciding-when-to-implement-the-event-based-asynchronous-pattern"></a>決定何時實作事件架構非同步模式
事件架構非同步模式提供模式來公開非同步行為之類別。 此模式中，介紹[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]定義兩種模式來公開非同步行為： 非同步模式根據<xref:System.IAsyncResult?displayProperty=nameWithType>介面和事件為基礎的模式。 本主題說明它是適合您實作這兩種模式。  
  
 如需有關使用非同步程式設計<xref:System.IAsyncResult>介面，請參閱[事件架構非同步模式 (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)。  
  
## <a name="general-principles"></a>一般原則  
 一般情況下，您應該使用事件架構非同步模式盡可能的非同步功能公開。 不過，有一些以事件為基礎的模式無法滿足的需求。 在這些情況下，您可能需要實作<xref:System.IAsyncResult>除了以事件為基礎模式的模式。  
  
> [!NOTE]
>  很少<xref:System.IAsyncResult>模式實作不具也實作以事件為基礎的模式。  
  
## <a name="guidelines"></a>方針  
 下列清單說明當您應該實作事件架構非同步模式的指導方針：  
  
-   作為預設應用程式開發介面的事件為基礎的模式來公開您的類別的非同步行為。  
  
-   不會公開<xref:System.IAsyncResult>模式時您的類別主要用於用戶端應用程式，例如 Windows Form。  
  
-   只會公開<xref:System.IAsyncResult>模式需要時將它以符合您的需求。 例如，與現有的 API 相容性可能需要您公開<xref:System.IAsyncResult>模式。  
  
-   不會公開<xref:System.IAsyncResult>模式，而不會也讓事件為基礎的模式。  
  
-   如果您必須公開<xref:System.IAsyncResult>模式，這樣一個進階選項。 例如，如果您產生 proxy 物件，產生事件為基礎的模式根據預設，與選項，以產生<xref:System.IAsyncResult>模式。  
  
-   根據事件架構模式實作您<xref:System.IAsyncResult>模式實作。  
  
-   避免公開這兩個以事件為基礎的模式和<xref:System.IAsyncResult>相同類別上的模式。 公開"較高層級"類別的事件基礎模式和<xref:System.IAsyncResult>模式上的 「 層級降低 」 類別。 例如，在比較以事件為基礎模式<xref:System.Net.WebClient>元件<xref:System.IAsyncResult>模式上<xref:System.Web.HttpRequest>類別。  
  
    -   公開 （expose) 事件為基礎的模式和<xref:System.IAsyncResult>相容性需求時，在相同類別上的模式。 例如，如果您已經釋放的 API，會使用<xref:System.IAsyncResult>模式中，您需要保留<xref:System.IAsyncResult>回溯相容性模式。  
  
    -   公開 （expose) 事件為基礎的模式和<xref:System.IAsyncResult>模式相同類別上，如果產生的物件模型複雜性上限分開實作的優點。 最好是公開比避免公開以事件為基礎模式的單一類別的兩個模式。  
  
    -   如果您必須公開這兩個以事件為基礎的模式和<xref:System.IAsyncResult>模式的單一類別，使用<xref:System.ComponentModel.EditorBrowsableAttribute>設<xref:System.ComponentModel.EditorBrowsableState.Advanced>標示<xref:System.IAsyncResult>模式實作，做為進階功能。 這表示設計環境，例如[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]IntelliSense、 顯示<xref:System.IAsyncResult>屬性和方法。 這些屬性和方法仍然完整地使用，但開發人員使用透過 IntelliSense 可以清楚地檢視應用程式開發介面。  
  
## <a name="criteria-for-exposing-the-iasyncresult-pattern-in-addition-to-the-event-based-pattern"></a>準則來公開以事件為基礎模式除了 IAsyncResult 模式  
 雖然事件架構非同步模式有許多好處，在先前所述的案例下，它也有一些缺點，您應該注意如果效能是您最重要的需求。  
  
 有三種案例，以事件為基礎的模式不會處理與<xref:System.IAsyncResult>模式：  
  
-   封鎖等候上一個<xref:System.IAsyncResult>  
  
-   封鎖許多等候<xref:System.IAsyncResult>物件  
  
-   輪詢完成<xref:System.IAsyncResult>  
  
 您可以使用以事件為基礎的模式，來解決這些案例，但這樣做很比使用較繁瑣<xref:System.IAsyncResult>模式。  
  
 開發人員經常使用<xref:System.IAsyncResult>模式通常會有極高的效能需求的服務。 例如，輪詢完成案例是高效能伺服器技術。  
  
 此外，事件為基礎的模式會比效率<xref:System.IAsyncResult>模式，因為它會建立多個物件，特別是<xref:System.EventArgs>，而且因為它會在執行緒之間同步處理。  
  
 下列清單顯示一些建議，如果您決定使用，請遵循<xref:System.IAsyncResult>模式：  
  
-   只會公開<xref:System.IAsyncResult>模式時您特別需要支援<xref:System.Threading.WaitHandle>或<xref:System.IAsyncResult>物件。  
  
-   只會公開<xref:System.IAsyncResult>模式時使用的現有 API<xref:System.IAsyncResult>模式。  
  
-   如果您有根據現有 API<xref:System.IAsyncResult>模式，請考慮也公開您的下一個版本中事件為基礎的模式。  
  
-   只會公開<xref:System.IAsyncResult>模式，如果您有高的效能需求，因此您已確認無法符合 endpointlistener 事件為基礎的模式，但可以達成<xref:System.IAsyncResult>模式。  
  
## <a name="see-also"></a>另請參閱  
 [逐步解說：實作支援事件架構非同步模式的元件](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 [事件架構非同步模式 (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [使用事件架構非同步模式設計多執行緒程式](../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)  
 [實作事件架構非同步模式](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)  
 [實作事件架構非同步模式的最佳作法](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 [事件架構非同步模式概觀](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
