---
title: "招聘程序"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d5fcacbb-c884-4b37-a5d6-02b1b8eec7b4
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1f9f201e14abdcfb98c33e947428137eca3caeaf
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="hiring-process"></a>招聘程序
此範例示範如何使用傳訊活動和裝載為工作流程服務的兩個工作流程來實作商務程序。 這些工作流程是虛擬公司 Contoso, Inc. 的 IT 基礎結構的一部分。  
  
 `HiringRequest` 工作流程 (實作為 <xref:System.Activities.Statements.Flowchart>) 會要求組織中的幾位經理提供授權。 為了達成這個目標，此工作流程會使用組織中的其他現有服務 (在我們的案例中，也就是收件匣服務和實作為一般 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務的組織資料服務)。  
  
 `ResumeRequest` 工作流程 (實作為 <xref:System.Activities.Statements.Sequence>) 會在 Contoso 的外部職涯網站上刊登工作，並管理履歷表的取得。 刊登的工作會留在外部網站一段固定的期間 (直到過了期限)，或者直到 Contoso 的員工決定將它取下為止。  
  
 此範例示範以下的 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] 功能：  
  
-   將商務程序模型化的 <xref:System.Activities.Statements.Flowchart> 和 <xref:System.Activities.Statements.Sequence> 工作流程。  
  
-   工作流程服務。  
  
-   訊息活動。  
  
-   以內容為主的相互關聯。  
  
-   自訂活動 (宣告式和以程式碼為主)。  
  
-   系統提供的 SQL Server 持續性。  
  
-   自訂 <xref:System.Activities.Persistence.PersistenceParticipant>。  
  
-   自訂追蹤。  
  
-   Windows 事件追蹤 (ETW)。  
  
-   活動撰寫。  
  
-   <xref:System.Activities.Statements.Parallel> 活動。  
  
-   <xref:System.Activities.Statements.CancellationScope> 活動。  
  
-   永久性計時器 (<xref:System.Activities.Statements.Delay> 活動)。  
  
-   交易。  
  
-   相同方案中一個以上的工作流程。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\HiringProcess`  
  
## <a name="description-of-the-process"></a>程序說明  
 Contoso, Inc. 想要嚴密控制每一個部門的員工人數。 因此，每當任何員工想要起始新的招聘程序時，都需要先通過招聘申請程序的核准，然後才能真正招聘人員。 這個程序稱為招聘程序申請 (定義在 HiringRequestService 專案中)，而且是由以下步驟所組成：  
  
1.  員工 (申請者) 起始招聘程序申請。  
  
2.  申請者的經理必須核准申請：  
  
    1.  經理可以拒絕申請。  
  
    2.  經理可以將申請退回給申請者，要求提供其他資訊：  
  
        1.  申請者複查申請，並將申請送回給經理。  
  
    3.  經理可以核准申請。  
  
3.  當申請者的經理核准之後，部門主管必須核准申請：  
  
    1.  部門主管可以拒絕申請。  
  
    2.  部門主管可以核准申請。  
  
4.  當部門主管核准之後，此程序需要兩位人力資源部門經理或 CEO 的核准：  
  
    1.  此程序可以轉換為已接受或已拒絕狀態。  
  
    2.  如果已接受此程序，就會啟動新的 `ResumeRequest` 工作流程執行個體 (`ResumeRequest` 會透過服務參考連結到 HiringRequest.csproj)。  
  
 一旦經理核准新員工的招聘之後，人力資源部門就必須尋找適當的人選。 這個程序是由第二個工作流程所執行 (`ResumeRequest`，定義在 ResumeRequestService.csproj 中)。 此工作流程定義的程序會將工作機會的刊登內容提交給 Contoso 的外部職涯網站、接收求職者的履歷表，並監控工作刊登的狀態。 刊登的工作職務會留在外部網站一段固定的期間 (直到過了期限)，或者直到 Contoso 的員工決定將它取下為止。 `ResumeRequest` 工作流程包含下列步驟：  
  
1.  Contoso 的員工會輸入這個職務的相關資訊及逾時期間。 一旦員工輸入這項資訊之後，該職務就會刊登在職涯網站上。  
  
2.  刊登該資訊之後，有興趣的人士就可以提交履歷表。 當有人提交履歷表時，履歷表就會儲存在一筆連結至職位空缺的記錄中。  
  
3.  求職者可以在到期期限之前提交履歷表，或者 Contoso 人力資源部門的人員如果確定要停止此程序，可以取下刊登的工作機會。  
  
## <a name="projects-in-the-sample"></a>範例中的專案  
 下表顯示範例方案中的專案。  
  
|Project|描述|  
|-------------|-----------------|  
|ContosoHR|包含資料合約、商務物件和儲存機制類別。|  
|HiringRequestService|包含招聘申請程序工作流程的定義。<br /><br /> 這個專案會實作為主控台應用程式，該應用程式會自行裝載此工作流程 (xaml 檔案) 當做服務。|  
|ResumeRequestService|這是一個工作流程服務，它會在到期之前或是某人決定要停止程序之前收集求職者的履歷表。<br /><br /> 此專案會實作為宣告式工作流程服務 (xamlx)。|  
|OrgService|這是公開組織資訊 (員工、職位、職位類型和部門) 的服務。 您可以將這項服務視為企業資源規劃 (ERP) 的公司組織模組。<br /><br /> 這個專案會實作為可公開 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務的主控台應用程式。|  
|InboxService|包含員工之可操作任務的收件匣。<br /><br /> 這個專案會實作為可公開 WCF 服務的主控台應用程式。|  
|InternalClient|用來與此程序互動的 Web 應用程式。 使用者可以啟動、參與及檢視其 HiringProcess 工作流程。 他們也可以使用這個應用程式來啟動及監控 ResumeRequest 程序。<br /><br /> 此網站會實作為 Contoso 的內部網路。 這個專案會實作為 ASP.NET 網站。|  
|CareersWebSite|公開 Contoso 職缺的外部網站。 任何求職者都可以巡覽至這個網站，並提交履歷表。|  
  
## <a name="feature-summary"></a>功能摘要  
 下表說明此範例中使用每一個功能的方式。  
  
|功能|描述|Project|  
|-------------|-----------------|-------------|  
|流程圖|商務程序以流程圖來表示。 此流程圖說明所代表的程序與公司在白板上所畫的程序相同。|HiringRequestService|  
|工作流程服務|包含程序定義的流程圖會裝載於服務中 (在此範例中，此服務會裝載於主控台應用程式內)。|HiringRequestService|  
|訊息活動|此流程圖會以兩種方式使用訊息活動：<br /><br /> -若要取得使用者 （用來在每一個核准步驟中接收決策與相關的資訊） 的資訊。<br />-若要與其他現有服務 （InboxService 和 OrgDataService 透過服務參考使用） 進行互動。|HiringRequestService|  
|以內容為主的相互關聯|核准訊息會依招聘申請的 ID 屬性建立相互關聯性：<br /><br /> -處理序啟動時，就會使用之要求的 ID 初始化相互關聯控制代碼。<br />-傳入的核准訊息相互關聯依其 ID （每一個核准訊息的第一個參數是要求的識別碼）。|HiringRequestService / ResumeRequestService|  
|自訂活動 (宣告式和以程式碼為主)|此範例中有幾個自訂活動：<br /><br /> -   `SaveActionTracking`： 這個活動會發出自訂<xref:System.Activities.Tracking.TrackingRecord>(使用<xref:System.Activities.NativeActivityContext.Track%2A>)。 這個活動已經使用命令式程式碼擴充 <xref:System.Activities.NativeActivity> 來撰寫。<br />-   `GetEmployeesByPositionTypes`： 這個活動會接收職位類型 Id 的清單，並傳回擁有該職位 Contoso 中的人員清單。 此活動已經以宣告方式撰寫 (使用活動設計工具)。<br />-   `SaveHiringRequestInfo`： 這個活動會將資訊儲存`HiringRequest`(使用`HiringRequestRepository.Save`)。 這個活動已經使用命令式程式碼擴充 <xref:System.Activities.CodeActivity> 來撰寫。|HiringRequestService|  
|系統提供的 SQL Server 持續性|裝載流程圖程序定義的 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 執行個體會設定為使用系統提供的 SQL Server 持續性。|HiringRequestService / ResumeRequestService|  
|自訂追蹤|此範例包含的自訂追蹤參與者會儲存 `HiringRequestProcess` 的記錄 (這樣會記錄已經執行的動作、動作執行者與執行時間)。 原始程式碼位於 HiringRequestService 的 Tracking 資料夾中。|HiringRequestService|  
|ETW 追蹤|系統提供的 ETW 追蹤會設定於 HiringRequestService 服務的 App.config 檔案中。|HiringRequestService|  
|活動撰寫|此程序定義會使用 <xref:System.Activities.Activity> 的免費撰寫。 此流程圖包含幾個序列和平行活動，這些活動同時也包含其他活動 (依此類推)。|HiringRequestService|  
|平行活動|-   <xref:System.Activities.Statements.ParallelForEach%601>用來在 CEO 和人力資源部門經理的收件匣中註冊，以平行方式 （等候兩位人力資源部門經理的核准步驟）。<br />-   <xref:System.Activities.Statements.Parallel>用來執行某些清除工作。 在已完成和已拒絕步驟中|HiringRequestService|  
|模型取消|此流程圖會使用 <xref:System.Activities.Statements.CancellationScope> 建立取消行為 (在此案例中，它會執行某些清除工作)。|HiringRequestService|  
|客戶持續性參與者|`HiringRequestPersistenceParticipant` 會將工作流程變數中的資料儲存到 Contoso HR 資料庫內所儲存的資料表中。|HiringRequestService|  
|工作流程服務|`ResumeRequestService` 是使用工作流程服務所實作。 工作流程定義和服務資訊會包含在 ResumeRequestService.xamlx 中。 此服務會設定為使用持續性與追蹤。|ResumeRequestService|  
|永久性計時器|`ResumeRequestService` 會使用永久性計時器來定義刊登工作的期間 (一旦過了期限之後，刊登就會結束)。|ResumeRequestService|  
|異動|<xref:System.Activities.Statements.TransactionScope> 是用來確保數個活動執行內的資料都是一致的 (當收到新的履歷表時)。|ResumeRequestService|  
|異動|自訂持續性參與者 (`HiringRequestPersistenceParticipant`) 和自訂追蹤參與者 (`HistoryFileTrackingParticipant`) 會使用相同的交易。|HiringRequestService|  
|在 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 應用程式中使用 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]。|工作流程是從兩個 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 應用程式進行存取。|InternalClient / CareersWebSite|  
  
## <a name="data-storage"></a>資料儲存  
 資料會儲存在名為 `ContosoHR` 的 SQL Server 資料庫中 (用來建立此資料庫的指令碼位於 `DbSetup` 資料夾中)。 工作流程執行個體會儲存在名為 `InstanceStore` 的 SQL Server 資料庫中 (用來建立執行個體存放區的指令碼屬於 [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] 散發的一部分)。  
  
 從 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 命令提示字元執行 Setup.cmd 指令碼來建立這兩個資料庫。  
  
## <a name="running-the-sample"></a>執行範例  
  
#### <a name="to-create-the-databases"></a>若要建立資料庫  
  
1.  開啟 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 命令提示字元。  
  
2.  巡覽至範例資料夾。  
  
3.  執行 Setup.cmd。  
  
4.  確認 `ContosoHR` 和 `InstanceStore` 這兩個資料庫都已經在 SQL Express 中建立。  
  
#### <a name="to-set-up-the-solution-for-execution"></a>若要設定執行的方案  
  
1.  以系統管理員身分執行 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]。 開啟 HiringRequest.sln。  
  
2.  以滑鼠右鍵按一下方案中的**方案總管 中**選取**屬性**。  
  
3.  選取的選項**多個啟始專案**並設定**CareersWebSite**， **InternalClient**， **HiringRequestService**，和**ResumeRequestService**至**啟動**。 保留**ContosoHR**， **InboxService**，和**OrgService**為 None。  
  
4.  按 CTRL+SHIFT+B 建置此方案。 確認建置是否成功。  
  
#### <a name="to-run-the-solution"></a>若要執行方案  
  
1.  在建置方案之後，按 CTRL+F5 執行而不偵錯。 確認所有服務都已啟動。  
  
2.  以滑鼠右鍵按一下**InternalClient**中方案，然後選取**瀏覽器中的檢視**。 隨即顯示 `InternalClient` 的預設頁面。 確定服務正在執行，然後按一下連結。  
  
3.  **HiringRequest**模組會顯示。 您可以遵循這裡所詳述的案例。  
  
4.  一旦 `HiringRequest` 完成之後，您可以啟動 `ResumeRequest`。 您可以遵循這裡所詳述的案例。  
  
5.  當張貼 `ResumeRequest` 時，它會公佈在公開網站上 (Contoso 職涯網站)。 若要查看工作的刊登 (並申請該職位)，請巡覽至職涯網站。  
  
6.  以滑鼠右鍵按一下**CareersWebSite**方案並選取**瀏覽器中的檢視**。  
  
7.  瀏覽回`InternalClient`以滑鼠右鍵按一下**InternalClient**方案中，然後選取**瀏覽器中的檢視**。  
  
8.  移至**job Postings**區段按一下**Jobpostings**收件匣上方功能表中的連結。 您可以遵循這裡所詳述的案例。  
  
## <a name="scenarios"></a>案例  
  
### <a name="hiring-request"></a>招聘申請  
  
1.  Michael Alexander (軟體工程師) 想要在工程部門申請一個新的職位，請公司招聘至少有三年 C# 經驗的測試軟體工程師 (SDET)。  
  
2.  建立之後的要求會出現在 Michael 的收件匣 (按一下**重新整理**如果看不到要求) 等候 Michael 的經理 Peter Brehm 的核准。  
  
3.  Peter 想要針對 Michael 的申請採取行動。 他認為這個職位需要五年的 C# 經驗而不是三年，所以傳回他的意見以供審查。  
  
4.  Michael 在他的收件匣看到經理傳給他的郵件，而且他想要採取行動。Michael 看到職位申請的記錄，並同意 Peter 的意見。 Michael 於是將職位描述修改為需要五年的 C# 經驗，並接受修改。  
  
5.  Peter 針對 Michael 修改過的申請採取行動，並接受申請。 現在此申請必須由工程部門總監 Tsvi Reiter 核准。  
  
6.  Tsvi Reiter 想要加快申請的腳步，所以他加入一項註解表示此申請非常緊急，並接受申請。  
  
7.  現在此申請必須由兩位人力資源部門經理或 CEO 核准。 CEO Brian Richard Goldstein 看到 Tsvi 發出的緊急申請。 他採取的動作是接受此申請，因此跳過兩位人力資源部門經理的核准步驟。  
  
8.  此申請從 Michael 的收件匣中移除，現在會開始招聘 SDET 的程序。  
  
### <a name="start-resume-request"></a>開始請求履歷表  
  
1.  現在，工作位置正在等候刊登在外部網站上可以在適用於人員 (您可以看到它按一下**Jobpostings**連結)。 目前這個職位的內容在人力資源部門代表手中，該名代表負責完成此職位的內容，並將它刊登在網站上。  
  
2.  人力資源部門想要編輯此職位 (按一下**編輯**連結) 藉由設定 60 分鐘的逾時 （在現實生活中，這可能是天或週）。 此逾時期間可允許根據指定的時間從外部網站取下該職位。  
  
3.  它會出現在儲存編輯過的職位之後, 在**Receiving Resumes** （重新整理網頁即可看到新的職位） 索引標籤。  
  
### <a name="collecting-resumes"></a>收集履歷表  
  
1.  此職位應該會出現在外部網站上。 當某個人對這個工作有興趣時，他可以申請這個職位並提交履歷表。  
  
2.  如果您回到工作刊登清單服務，您可以 「 檢視繼續 」，已收集到目前為止。  
  
3.  人力資源部門可以停止收集履歷表 (例如，在找到適當的人選之後)。  
  
## <a name="troubleshooting"></a>疑難排解  
  
1.  確定當您執行 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 時，具有系統管理員權限。  
  
2.  如果此方案建置失敗，請確認以下事項：  
  
    -   若要參考`ContosoHR`中並未遺失`InternalClient`或`CareersWebSite`專案。  
  
3.  如果此方案執行失敗，請確認以下事項：  
  
    1.  所有服務都在執行中。  
  
    2.  服務參考已更新。  
  
        1.  開啟 App_WebReferences 資料夾  
  
        2.  以滑鼠右鍵按一下**Contoso**選取**更新 Web/服務參考**。  
  
        3.  在 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 中按 CTRL+SHIFT+B 重新建置此方案。  
  
## <a name="uninstalling"></a>解除安裝  
  
1.  執行 DbSetup 資料夾中的 Cleanup.bat，以刪除 SQL Server 執行個體存放區。  
  
2.  從硬碟中刪除原始程式碼。