---
title: "使用用戶端存取服務 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c8329832-bf66-4064-9034-bf39f153fc2d
caps.latest.revision: 15
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 15
---
# 使用用戶端存取服務
用戶端應用程式必須建立、設定，以及使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端或通道物件來與服務通訊。  [WCF 用戶端概觀](../../../../docs/framework/wcf/wcf-client-overview.md)主題將概要說明在建立基礎用戶端和通道物件時所需要的物件和步驟，以及這些物件的使用方式。  
  
 本主題會就用戶端應用程式以及在不同案例下可能有用的用戶端和通道物件，提供一些相關問題的深入資訊。  
  
## 概觀  
 本主題將說明下列項目的相關行為和問題：  
  
-   通道和工作階段存留期 \(Lifetime\)。  
  
-   處理例外狀況。  
  
-   瞭解封鎖問題。  
  
-   以互動方式初始化通道。  
  
### 通道和工作階段存留期。  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 應用程式包含兩種通道：資料包和工作階段。  
  
 「*資料包*」\(Datagram\) 通道是指其中的所有訊息都各不相關的通道。  使用資料包通道時，如果輸入或輸出作業失敗，下一個作業通常不會受到影響，而且還可以重複使用同一個通道。  基於這點，資料包通道通常不會發生錯誤。  
  
 「*工作階段*」\(Session\) 通道則是連線至其他端點的通道。  某一端工作階段中的訊息永遠都會與另一端的相同工作階段相關聯。  此外，工作階段中的參與者雙方都必須同意其對話需求已被滿足，這樣工作階段才能算是成功。  如果它們不同意，工作階段通道可能會發生錯誤。  
  
 呼叫第一個作業，便可明確地或隱含地開啟用戶端。  
  
> [!NOTE]
>  通常嘗試明確地偵測錯的工作階段通道不會有任何效用，因為您收到通知的時間會依工作階段實作而有不同。  例如，由於 <xref:System.ServiceModel.NetTcpBinding?displayProperty=fullName> \(已停用可靠工作階段\) 會面臨 TCP 連線的工作階段，如果您接聽服務或用戶端上的 <xref:System.ServiceModel.ICommunicationObject.Faulted?displayProperty=fullName> 事件，您就有可能會在發生網路失敗時立刻收到通知。  但可靠工作階段 \(透過已啟用 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=fullName> 的繫結所建立\) 是設計用來隔離服務與小型的網路失敗。  如果工作階段可在合理的時間內重新建立，則相同繫結 \(針對可靠工作階段所設定\) 就可能不會發生錯誤，除非中斷情形持續了更長的一段時間。  
  
 根據預設，大部分系統提供的繫結 \(會將通道公開至應用程式層\) 都會使用工作階段，但 <xref:System.ServiceModel.BasicHttpBinding?displayProperty=fullName> 則不會。  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [使用工作階段](../../../../docs/framework/wcf/using-sessions.md).  
  
### 工作階段的正確用法  
 工作階段會提供特定方式來瞭解整個訊息交換是否已經完成，以及兩端是否都認為此工作階段成功。  建議由呼叫應用程式在一個 try 區塊中開啟通道、使用通道，以及關閉通道。  如果工作階段通道已開啟，而呼叫一次 <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=fullName> 方法後有成功傳回該呼叫，就表示工作階段成功。  在這個案例中所謂的成功，是指所有傳遞可保證已達成指定的繫結，而且另一端在呼叫 <xref:System.ServiceModel.ICommunicationObject.Close%2A> 之前並沒有呼叫通道上的 <xref:System.ServiceModel.ICommunicationObject.Abort%2A?displayProperty=fullName>。  
  
 下列章節將提供這個用戶端方法的範例。  
  
### 例外狀況處理  
 在用戶端應用程式中處理例外狀況是很直接的工作。  如果通道是在 try 區塊中開啟、使用以及關閉，則除非有擲回例外狀況，否則對話就算成功。  一般來說，如果有擲回例外狀況，對話就會中止。  
  
> [!NOTE]
>  不建議使用 `using` 陳述式 \([!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 中的 `Using`\)。  這是因為 `using` 陳述式的結尾可能會引發例外狀況而遮蓋掉您想瞭解的其他例外狀況。  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [避免 Using 陳述式發生問題](../../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md).  
  
 下列程式碼範例會顯示使用 try\/catch 區塊而非 `using` 陳述式的建議用戶端模式。  
  
 [!code-csharp[FaultContractAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/client.cs#3)]
 [!code-vb[FaultContractAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/client.vb#3)]  
  
> [!NOTE]
>  檢查 <xref:System.ServiceModel.ICommunicationObject.State%2A?displayProperty=fullName> 屬性的值屬於競爭條件，因此不建議用來判斷是否要重複使用或關閉通道。  
  
 即使在關閉時發生例外狀況，資料包通道也絕不會發生錯誤。  此外，無法使用安全對話來進行驗證的非雙工用戶端通常會擲回 <xref:System.ServiceModel.Security.MessageSecurityException?displayProperty=fullName>。  不過，如果使用安全對話的雙工用戶端驗證失敗，則用戶端就會轉而收到 <xref:System.TimeoutException?displayProperty=fullName>。  
  
 如需在應用程式層級使用錯誤資訊的完整資訊，請參閱[指定與處理合約和服務中的錯誤](../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)。  [預期的例外狀況](../../../../docs/framework/wcf/samples/expected-exceptions.md) 會說明預期的例外狀況，並示範例外狀況的處理方式。  [!INCLUDE[crabout](../../../../includes/crabout-md.md)]如何在開發通道時處理錯誤的詳細資訊，請參閱 [處理例外狀況和錯誤](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)。  
  
### 用戶端封鎖和效能  
 當應用程式同步呼叫要求\-回覆作業時，除非有收到傳回值或擲回例外狀況 \(例如 <xref:System.TimeoutException?displayProperty=fullName>\)，否則用戶端會封鎖。  這個行為類似本機行為。  當應用程式同步叫用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端物件或通道上的作業時，除非通道層可以將資料寫入至網路或有擲回例外狀況，否則用戶端不會傳回。  雖然單向訊息交換模式 \(指定方式是標示作業的 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=fullName> 設定為 `true`\) 可以讓某些用戶端更能有效回應，但單向作業也會根據繫結和已經傳送的訊息來執行封鎖。  單向作業只能進行訊息交換，無法執行其他作業。  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [單向服務](../../../../docs/framework/wcf/feature-details/one-way-services.md).  
  
 不論在何種訊息交換模式下，大型資料區塊都會減慢用戶端的處理速度。  若要瞭解如何處理這些問題，請參閱[大型資料與資料流](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)。  
  
 如果您的應用程式必須在完成作業的同時執行更多工作，則您應該在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端實作的服務合約介面上建立非同步方法組。  要這樣做的最簡單方式就是使用 [ServiceModel 中繼資料公用程式工具 \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) 上的 `/async` 參數。  如需範例，請參閱 [HOW TO：以非同步方式呼叫 WCF 服務作業](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)。  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]提升用戶端效能的詳細資訊，請參閱[中介層用戶端應用程式](../../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md)。  
  
### 讓使用者以動態方式選取認證  
 <xref:System.ServiceModel.Dispatcher.IInteractiveChannelInitializer> 介面可讓應用程式顯示使用者介面，以便使用者選擇要在逾時計時器啟動之前用來建立通道的認證。  
  
 應用程式開發人員可以透過兩種方式來使用插入的 <xref:System.ServiceModel.Dispatcher.IInteractiveChannelInitializer>。  用戶端應用程式可以在開啟通道之前呼叫 <xref:System.ServiceModel.ClientBase%601.DisplayInitializationUI%2A?displayProperty=fullName> 或 <xref:System.ServiceModel.IClientChannel.DisplayInitializationUI%2A?displayProperty=fullName> \(或非同步版本\) \(「*明確*」\(Explicit\) 方式\)，或呼叫第一項作業 \(「*隱含*」\(Implicit\) 方式\)。  
  
 如果使用隱含方式，應用程式就必須在 <xref:System.ServiceModel.ClientBase%601> 或 <xref:System.ServiceModel.IClientChannel> 延伸上呼叫第一項作業。  如果呼叫第一項作業以外的任何作業，就會擲回例外狀況。  
  
 如果使用明確方式，應用程式必須依照順序執行下列步驟：  
  
1.  呼叫 <xref:System.ServiceModel.ClientBase%601.DisplayInitializationUI%2A?displayProperty=fullName> 或 <xref:System.ServiceModel.IClientChannel.DisplayInitializationUI%2A?displayProperty=fullName> \(或非同步版本\)。  
  
2.  當初始設定式已回傳時，在 <xref:System.ServiceModel.IClientChannel> 物件或是 <xref:System.ServiceModel.ClientBase%601.InnerChannel%2A?displayProperty=fullName> 屬性傳回的 <xref:System.ServiceModel.IClientChannel> 物件上呼叫 <xref:System.ServiceModel.ICommunicationObject.Open%2A> 方法。  
  
3.  呼叫作業。  
  
 建議您採用明確方式來處理使用者介面的實際執行品質應用程式控制。  
  
 使用隱含方式的應用程式會叫用使用者介面初始設定式，但若應用程式的使用者無法在繫結的傳送逾時期限之內回應，當使用者介面傳回時就會擲回例外狀況。  
  
## 請參閱  
 [雙工服務](../../../../docs/framework/wcf/feature-details/duplex-services.md)   
 [HOW TO：使用單向和要求\-回覆合約來存取服務](../../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)   
 [HOW TO：使用雙工合約存取服務](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)   
 [HOW TO：存取 WSE 3.0 服務](../../../../docs/framework/wcf/feature-details/how-to-access-a-wse-3-0-service-with-a-wcf-client.md)   
 [HOW TO：使用 ChannelFactory](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)   
 [HOW TO：以非同步方式呼叫 WCF 服務作業](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)   
 [中介層用戶端應用程式](../../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md)