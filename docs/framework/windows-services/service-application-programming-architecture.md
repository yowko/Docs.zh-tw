---
title: "服務應用程式的程式設計架構 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ServiceBase 類別, 服務狀態"
  - "ServiceController 類別"
  - "ServiceController 元件, 程式設計架構"
  - "ServiceProcessInstaller 類別, 服務應用程式程式碼模型"
  - "服務, 程式設計架構"
  - "服務, 狀態"
  - "Windows 服務應用程式, 程式碼模型"
  - "Windows 服務應用程式, 狀態"
ms.assetid: 83230026-d068-4174-97ff-e264c896eb2f
caps.latest.revision: 15
author: "ghogen"
ms.author: "ghogen"
manager: "douge"
caps.handback.revision: 15
---
# 服務應用程式的程式設計架構
Windows 服務應用程式以繼承自 <xref:System.ServiceProcess.ServiceBase?displayProperty=fullName> 類別的類別為基礎。  您可以覆寫此類別中的方法並定義它們的功能來決定您的服務的行為。  
  
 涉及服務建立的主要類別為：  
  
-   <xref:System.ServiceProcess.ServiceBase?displayProperty=fullName> \- 在建立服務時覆寫 <xref:System.ServiceProcess.ServiceBase> 類別中的方法，並定義程式碼來決定服務在這個繼承的類別中運作的方式。  
  
-   <xref:System.ServiceProcess.ServiceProcessInstaller?displayProperty=fullName> 和 <xref:System.ServiceProcess.ServiceInstaller?displayProperty=fullName> \- 使用這些類別安裝和解除安裝服務。  
  
 此外，名為 <xref:System.ServiceProcess.ServiceController> 的類別可以用以管理服務本身。  建立服務時並不會涉及此類別，但是可以使用此類別來啟動和停止服務、傳遞命令給服務及傳回一連串的列舉型別 \(Enumeration\)。  
  
## 定義服務的行為  
 在您的服務類別中，您可以覆寫用來決定當 \[服務控制管理員\] 中的服務狀態改變時，將發生什麼事情的基底類別 \(Base Class\) 函式。  <xref:System.ServiceProcess.ServiceBase> 類別會公開下列方法，您可以覆寫這些方法，以加入自訂的行為。  
  
|方法|覆寫目的|  
|--------|----------|  
|<xref:System.ServiceProcess.ServiceBase.OnStart%2A>|表示當您的服務開始執行時應該採取的行動。  您必須在此程序中撰寫服務的程式碼來執行有用的工作。|  
|<xref:System.ServiceProcess.ServiceBase.OnPause%2A>|表示當您的服務暫停時應該發生的事情。|  
|<xref:System.ServiceProcess.ServiceBase.OnStop%2A>|表示當您的服務停止執行時應該發生的事情。|  
|<xref:System.ServiceProcess.ServiceBase.OnContinue%2A>|表示當您的服務在暫停後繼續正常運作時應該發生的事情。|  
|<xref:System.ServiceProcess.ServiceBase.OnShutdown%2A>|表示您的系統關機前，如果服務還在執行中時應該發生的事情。|  
|<xref:System.ServiceProcess.ServiceBase.OnCustomCommand%2A>|表示當您的服務收到自訂命令時應該發生的事情。  如需自訂命令的詳細資訊，請參閱 MSDN Online。|  
|<xref:System.ServiceProcess.ServiceBase.OnPowerEvent%2A>|表示當收到電源管理事件時，例如電池電力不足或暫停作業時，服務應該如何回應。|  
  
> [!NOTE]
>  這些方法都會顯示服務在存留期中移動時的狀態；服務會從某個狀態轉換為下一個狀態。  例如，在呼叫 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 前，您永遠無法使服務回應 <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> 命令。  
  
 還有其他一些有趣的屬性和方法，  這些需求包括：  
  
-   <xref:System.ServiceProcess.ServiceBase> 類別的 <xref:System.ServiceProcess.ServiceBase.Run%2A> 方法。  這是服務的主要進入點 \(Entry Point\)。  當您使用 Windows 服務範本建立服務時，程式碼會插入至應用程式的 `Main` 方法以執行服務。  程式碼看起來如下：  
  
     [!code-csharp[VbRadconService#6](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/VbRadconService/CS/MyNewService.cs#6)]
     [!code-vb[VbRadconService#6](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#6)]  
  
    > [!NOTE]
    >  這些範例是使用 <xref:System.ServiceProcess.ServiceBase> 型別的陣列，可以加入應用程式包含的每一個服務，然後所有的服務可以一起執行。  但是，如果您只要建立單一的服務，可以選擇不要使用陣列，並直接宣告繼承自 <xref:System.ServiceProcess.ServiceBase> 的新物件，再執行此物件即可。  如需範例，請參閱 [如何：以程式設計方式撰寫服務](../../../docs/framework/windows-services/how-to-write-services-programmatically.md)。  
  
-   <xref:System.ServiceProcess.ServiceBase> 類別中一系列的屬性。  這些屬性會決定您的服務中可以呼叫那些方法。  例如，當 <xref:System.ServiceProcess.ServiceBase.CanStop%2A> 屬性設定為 `true` 時，就可以呼叫服務的 <xref:System.ServiceProcess.ServiceBase.OnStop%2A> 方法。  當 <xref:System.ServiceProcess.ServiceBase.CanPauseAndContinue%2A> 屬性設定為 `true` 時，就可以呼叫 <xref:System.ServiceProcess.ServiceBase.OnPause%2A> 和 <xref:System.ServiceProcess.ServiceBase.OnContinue%2A> 方法。  當您將這些屬性設定為 `true` 時，您應該也要覆寫並定義相關方法的處理。  
  
    > [!NOTE]
    >  服務必須至少覆寫 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 和 <xref:System.ServiceProcess.ServiceBase.OnStop%2A> 才會有用。  
  
 您也可以使用稱為 <xref:System.ServiceProcess.ServiceController> 的元件，與現有的服務溝通並控制它的行為。  
  
## 請參閱  
 [Windows 服務應用程式簡介](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)   
 [如何：建立 Windows 服務](../../../docs/framework/windows-services/how-to-create-windows-services.md)