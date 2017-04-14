---
title: "如何：啟動服務 | Microsoft Docs"
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
  - "服務, 啟動"
  - "Windows 服務應用程式, 啟動"
ms.assetid: 9ea77955-2d96-4c3d-913c-14db7604cdad
caps.latest.revision: 16
author: "ghogen"
ms.author: "ghogen"
manager: "douge"
caps.handback.revision: 14
---
# 如何：啟動服務
安裝服務後，必須啟動該服務。  啟動時會呼叫服務類別的 <xref:System.ServiceProcess.ServiceBase.OnStart%2A> 方法。  通常，<xref:System.ServiceProcess.ServiceBase.OnStart%2A> 方法中定義了服務會執行的有用工作。  當服務啟動後，將維持作用直到手動暫停或停止該服務。  
  
 服務可以設定為自動啟動或手動啟動。  自動啟動的服務會在有安裝該服務的電腦重新啟動或第一次開機時啟動該服務。  使用者必須啟動要手動啟動的服務。  
  
> [!NOTE]
>  根據預設，使用 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 建立的服務會設定為手動啟動。  
  
 有數種方法可手動啟動服務，包括從 \[**伺服器總管\]**\]、從 \[**服務控制管理員**\]，或從程式碼中使用稱為 <xref:System.ServiceProcess.ServiceController> 的元件。  
  
 您可以設定 <xref:System.ServiceProcess.ServiceInstaller> 類別的 <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> 屬性，決定服務要手動啟動或自動啟動。  
  
### 若要指定服務應該如何啟動  
  
1.  建立您的服務後，為它加入必要的安裝程式。  如需詳細資訊，請參閱[如何：加入 Installer 至服務應用程式](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)。  
  
2.  在設計工具中，按一下您正在使用的服務安裝程式。  
  
3.  在 \[**屬性**\] 視窗中，將 <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> 屬性設定為下列其中一個值：  
  
    |服務安裝時機|設定值|  
    |------------|---------|  
    |當電腦重新啟動時|**自動**|  
    |當明確的使用者動作啟動服務時|**Manual**|  
  
    > [!TIP]
    >  若要讓服務永遠不啟動，您可以將 <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> 屬性設定為 \[**停用**\]。  當您預備重新啟動伺服器數次，並希望防止服務在開機時正常啟動來節省時間時，就可以這麼做。  
  
    > [!NOTE]
    >  當安裝您的服務後，這些屬性和其他屬性都可以改變。  
  
     有數種方法可以啟動 <xref:System.ServiceProcess.ServiceInstaller.StartType%2A> 處理序設定為 \[**手動**\] 的服務，包括從 \[**伺服器總管**\]、從 Windows 的 \[**服務控制管理員**\]，或從程式碼中。  重要的是，請注意並非所有方法都可真正啟動 \[**服務控制管理員**\] 內容中的服務；\[**伺服器總管**\] 和程式設計的服務啟動方式，才能真正地操作控制器。  
  
### 若要從伺服器總管中手動啟動服務  
  
1.  在 \[**伺服器總管**\] 中，加入您要使用且沒有列在其中的伺服器。  如需詳細資訊，請參閱[如何：存取及初始化伺服器總管\/資料庫總管](../Topic/How%20to:%20Access%20and%20Initialize%20Server%20Explorer-Database%20Explorer.md)。  
  
2.  展開 \[**服務**\] 節點，然後找出您想要啟動的服務。  
  
3.  在服務名稱上按一下滑鼠右鍵，再按一下 \[**啟動**\]。  
  
### 若要從服務控制管理員中手動啟動服務  
  
1.  執行下列步驟，開啟 \[**服務控制管理員**\]：  
  
    -   在 Windows XP 和 2000 Professional 中，在桌面的 \[**我的電腦**\] 上按一下滑鼠右鍵，然後按一下 \[**管理**\]。  在出現的對話方塊中，展開 \[**服務和應用程式**\] 節點。  
  
         \-或\-  
  
    -   在 Windows Server 2003 和 Windows 2000 Server 中，按一下 \[**開始**\]，指向 \[**程式集**\]，按一下 \[**系統管理工具**\]，然後按一下 \[**服務**\]。  
  
        > [!NOTE]
        >  在 Windows NT 4.0 版中，您可以從 \[**控制台**\] 中開啟這個對話方塊。  
  
     現在您應該可以看到您的服務列在這個視窗的 \[**服務**\] 區段中。  
  
2.  從清單中選取您的服務，以滑鼠右鍵按一下該服務，再按一下 \[**啟動**\]。  
  
### 若要從程式碼中手動啟動服務  
  
1.  建立 <xref:System.ServiceProcess.ServiceController> 類別的執行個體，設定它與您要管理的服務互動。  
  
2.  呼叫 <xref:System.ServiceProcess.ServiceController.Start%2A> 方法啟動服務。  
  
## 請參閱  
 [Windows 服務應用程式簡介](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)   
 [如何：建立 Windows 服務](../../../docs/framework/windows-services/how-to-create-windows-services.md)   
 [如何：加入 Installer 至服務應用程式](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)   
 [如何：存取及初始化伺服器總管\/資料庫總管](../Topic/How%20to:%20Access%20and%20Initialize%20Server%20Explorer-Database%20Explorer.md)