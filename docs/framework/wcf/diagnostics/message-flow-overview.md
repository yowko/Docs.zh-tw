---
title: "訊息流程概觀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fb0899e1-84cc-4d90-b45b-dc5a50063943
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6fe4d8222bfed231c618ee4e5616dab37f912836
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="message-flow-overview"></a>訊息流程概觀
在包含互連服務的分散式系統中，您必須判斷服務之間的因果關係。 請務必了解屬於要求流程一部分的各種元件，以便支援重要案例，例如健康監視、疑難排解和根本原因分析。 為了讓各種服務之間的追蹤相互關聯，我們透過下列功能，在 .NET Framework 4 中加入了支援：  
  
-   分析追蹤：使用 Windows 事件追蹤 (ETW) 的高效能、低詳細等級追蹤功能。  
  
-   WCF/WF 服務的端對端活動模型：這項功能支援 <xref:System.ServiceModel> 和 <xref:System.Workflow.ComponentModel> 命名空間所產生之追蹤的相互關聯。  
  
-   WF 的 ETW 追蹤：這項功能會使用 WF 服務所產生的追蹤記錄來提供工作流程之目前狀態和進度的可視性。  
  
 在追蹤或追蹤記錄中記錄的錯誤可用來尋找程式碼缺失或格式錯誤的訊息。 在事件的訊息標頭中，Correlation 節點的 ActivityId 屬性可用來判斷錯誤的活動。 若要啟用訊息流程追蹤的活動識別碼，請參閱[設定訊息流程追蹤](../../../../docs/framework/wcf/diagnostics/etw/configuring-message-flow-tracing.md)。 本主題將示範如何在＜使用者入門教學課程＞中建立的專案內啟用訊息流程追蹤。  
  
### <a name="to-enable-message-flow-tracing-in-the-getting-started-tutorial"></a>若要在使用者入門教學課程中啟用訊息流程追蹤  
  
1.  開啟事件檢視器，依序按一下**啟動**，**執行**，並輸入`eventvwr.exe`。  
  
2.  如果您尚未啟用分析追蹤，展開**Applications and Services Logs**， **Microsoft**， **Windows**，**應用程式伺服器-應用程式**. 選取**檢視**，**顯示分析與偵錯記錄檔**。 以滑鼠右鍵按一下**分析**選取**啟用記錄**。 讓 [事件檢視器] 保持開啟狀態，以便檢視追蹤。  
  
3.  開啟範例中建立[入門教學課程](../../../../docs/framework/wcf/getting-started-tutorial.md)中[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]。 請注意，您必須以系統管理員的身分執行 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]，才能建立此服務。 如果您有[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]範例的安裝，您可以開啟[入門](../../../../docs/framework/wcf/samples/getting-started-sample.md)，其中包含已完成本教學課程中建立的專案。  
  
4.  以滑鼠右鍵按一下**服務**專案，然後選取**新增**，**新項目**。 選取**應用程式組態檔**按一下**確定**。  
  
5.  將下列程式碼加入至您在上一個步驟中建立的 App.Config 檔案。  
  
    ```xml  
    <system.serviceModel>  
      <diagnostics>  
        <endToEndTracing propagateActivity="true" messageFlowTracing="true"/>  
      </diagnostics>  
    </system.serviceModel>  
    ```  
  
6.  按 CTRL+F5 鍵執行伺服器應用程式，而不偵錯。 執行用戶端專案，以滑鼠右鍵按一下**用戶端**專案，並選取**偵錯**，**開始新執行個體**。  
  
7.  若要追蹤用戶端與伺服器之間的事件，請將下列程式碼加入至用戶端專案中的應用程式組態檔。  
  
    ```xml  
    <diagnostics>  
      <endToEndTracing propagateActivity="true" messageFlowTracing="true"/>  
    </diagnostics>  
    ```  
  
8.  在用戶端的 Program.cs 中，加入下列 Using 陳述式。  
  
    ```  
    using System.Diagnostics;  
    ```  
  
9. 在用戶端專案 program.cs 檔案的 Main 方法中，設定要在事件記錄檔中傳播的追蹤 GUID。  
  
    ```  
    Guid guid = Guid.NewGuid();  
    Trace.CorrelationManager.ActivityId = guid;  
    ```  
  
10. 重新整理並檢查**分析**記錄檔。  尋找 [事件 ID] 為 220 的事件。  選取事件，然後按一下 **詳細資料**預覽窗格中的索引標籤。 這個事件將包含呼叫活動的相互關聯 ID。  
  
    ```xml  
    <Correlation ActivityID="{A066CCF1-8AB3-459B-B62F-F79F957A5036}" />  
    ```  
  
    > [!NOTE]
    >  在 ActivityID 中，具有相同 GUID 的所有事件都與單一要求相關。 這可用來相互關聯特定用戶端與特定服務之間的訊息。 如果用戶端呼叫了其他服務，ActivityID 就可以識別相同的用戶端。  
  
11. 在某些情況下，ActivityID 可能會從原始 GUID 變更為新的 ActivityID。 在該情況下，系統會發出傳輸事件。 這個事件 ID 為 499，而且此事件的標頭將包含下列資料。  
  
    ```xml  
    <Event xmlns="http://schemas.microsoft.com/win/2004/08/events/event">  
        <System>  
            <Provider Name="Microsoft-Windows-Application Server-Applications" Guid="{c651f5f6-1c0d-492e-8ae1-b4efd7c9d503}" />   
            <EventID>499</EventID>   
            ...  
            <Correlation ActivityID="{A066CCF1-8AB3-459B-B62F-F79F957A5036}" RelatedActivityID="{85FC0930-9C49-42DA-804B-A7368104BD1B}" />   
            ...  
       </System>  
    </Event>  
    ```  
  
    > [!NOTE]
    >  傳輸事件會記錄作用中 ActivityID 從指定為 ActivityID 的 GUID 變更為指定為 RelatedActivityID 的 GUID。 當系統發出傳輸事件之後，所有事件都將包含新的 GUID 做為 ActivityID。
