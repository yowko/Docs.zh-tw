---
title: "Deciding When to Implement the Event-based Asynchronous Pattern | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Event-based Asynchronous Pattern"
  - "ProgressChangedEventArgs class"
  - "BackgroundWorker component"
  - "events [.NET Framework], asynchronous"
  - "AsyncOperationManager class"
  - "threading [.NET Framework], asynchronous features"
  - "AsyncOperation class"
  - "AsyncCompletedEventArgs class"
ms.assetid: a00046aa-785d-4f7f-a8e5-d06475ea50da
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Deciding When to Implement the Event-based Asynchronous Pattern
事件架構非同步模式提供了一個模式來公開類別的非同步行為。  在引入這個模式之後，[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 定義了兩個模式來公開非同步行為：以 <xref:System.IAsyncResult?displayProperty=fullName> 介面為根據的非同步模式，以及事件架構的模式。  這個主題將描述實作這兩個模式的適當時機。  
  
 如需使用 <xref:System.IAsyncResult> 介面進行非同步程式設計的詳細資訊，請參閱[Event\-based Asynchronous Pattern \(EAP\)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)。  
  
## 一般原則  
 一般來說，您應該盡量使用事件架構非同步模式來公開非同步功能。  但是，此事件架構模式無法滿足一些要求；  在這些情況下，您可能需要在此事件架構模式之外也實作 <xref:System.IAsyncResult> 模式。  
  
> [!NOTE]
>  實作 <xref:System.IAsyncResult> 模式而沒有同時實作此事件架構模式的情況，是相當罕見的。  
  
## 方針  
 下列清單描述當您應該實作事件架構非同步模式時所適用的方針：  
  
-   將此事件架構模式當做預設 API 使用，以公開類別的非同步行為。  
  
-   當您的類別主要用於用戶端應用程式中 \(例如 Windows Form\) 時，不要公開 <xref:System.IAsyncResult> 模式。  
  
-   當必須滿足您的需求時，只要公開 <xref:System.IAsyncResult> 模式。  例如，與現有 API 之間的相容性可能會要求您公開 <xref:System.IAsyncResult> 模式。  
  
-   如果沒有公開此事件架構模式，也不能公開 <xref:System.IAsyncResult> 模式。  
  
-   如果您必須公開 <xref:System.IAsyncResult> 模式，請以進階選項的方式來處理。  例如，如果您要產生 Proxy 物件，則預設會產生此事件架構模式，並附帶一個可產生 <xref:System.IAsyncResult> 模式的選項。  
  
-   在 <xref:System.IAsyncResult> 模式實作上建置您的事件架構模式實作。  
  
-   避免在相同類別上同時公開此事件架構模式和 <xref:System.IAsyncResult> 模式。  在「較高層級」類別上公開事件架構模式，以及在「較低層級」類別上公開 <xref:System.IAsyncResult> 模式。  例如，將 <xref:System.Net.WebClient> 元件上的事件架構模式與 <xref:System.Web.HttpRequest> 類別上的 <xref:System.IAsyncResult> 模式相比較。  
  
    -   當相容性需要時，在相同類別上公開此事件架構模式和 <xref:System.IAsyncResult> 模式。  例如，如果您已經發行使用 <xref:System.IAsyncResult> 模式的 API，您將需要保留 <xref:System.IAsyncResult> 模式，以提供回溯相容性 \(Backward Compatibility\)。  
  
    -   如果產生的物件模型複雜度帶來的好處更勝於分隔實作的好處，則可在相同類別上公開此事件架構模式和 <xref:System.IAsyncResult> 模式。  在單一類別上公開兩個模式的作法，要比避免公開此事件架構模式更理想。  
  
    -   如果您必須在單一類別上同時公開此事件架構模式和 <xref:System.IAsyncResult> 模式，請使用設定為 <xref:System.ComponentModel.EditorBrowsableState> 的 <xref:System.ComponentModel.EditorBrowsableAttribute>，以將 <xref:System.IAsyncResult> 模式實作標記為進階功能。  如此可向設計環境 \(例如 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] IntelliSense\) 指示，不要顯示 <xref:System.IAsyncResult> 屬性和方法。  這些屬性和方法仍然有完整的可用性，但是透過 IntelliSense 工作的開發人員會對此 API 有更清楚的概念。  
  
## 在事件架構模式之外也公開 IAsyncResult 模式的準則  
 雖然在之前提到的案例之下，事件架構非同步模式有許多優點，但是它也有一些缺點，而當效能是您最大的需求時，應該要特別留意這些缺點。  
  
 此事件架構模式及 <xref:System.IAsyncResult> 模式未處理到三種情況：  
  
-   封鎖一個 <xref:System.IAsyncResult> 的等候  
  
-   封鎖許多 <xref:System.IAsyncResult> 物件的等候  
  
-   輪詢 <xref:System.IAsyncResult> 的完成  
  
 您可以使用此事件架構模式來處理這些情況，但是這樣做要比使用 <xref:System.IAsyncResult> 模式更為麻煩。  
  
 開發人員經常會針對一般有極高效能需求的服務使用 <xref:System.IAsyncResult> 模式。  例如，輪詢完成案例就是一項高效能伺服器的技術。  
  
 此外，此事件架構模式的效率要比 <xref:System.IAsyncResult> 模式差，因為它會建立更多的物件，尤其是 <xref:System.EventArgs>，而且它也會跨處理序同步處理。  
  
 下列清單將顯示在您決定要使用 <xref:System.IAsyncResult> 模式之後所應該遵循的一些建議：  
  
-   當您特別需要 <xref:System.Threading.WaitHandle> 或 <xref:System.IAsyncResult> 物件的支援時，只要公開 <xref:System.IAsyncResult> 模式。  
  
-   當您有使用 <xref:System.IAsyncResult> 模式的現有 API 時，只要公開 <xref:System.IAsyncResult> 模式。  
  
-   如果現有的 API 是以 <xref:System.IAsyncResult> 模式為根據，請考慮在下一版中公開事件架構模式。  
  
-   如果您有極高的效能需求，而您驗證過此事件架構模式不能滿足這項需求，但是 <xref:System.IAsyncResult> 模式卻可以時，只要公開 <xref:System.IAsyncResult> 模式。  
  
## 請參閱  
 [Walkthrough: Implementing a Component That Supports the Event\-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)   
 [Event\-based Asynchronous Pattern \(EAP\)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)   
 [Multithreaded Programming with the Event\-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)   
 [Implementing the Event\-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)   
 [實作事件架構非同步模式的最佳作法](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)   
 [Event\-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)