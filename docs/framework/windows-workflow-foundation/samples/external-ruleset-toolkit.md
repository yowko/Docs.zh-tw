---
title: "外部 Ruleset 工具組 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a306d283-a031-475e-aa01-9ae86e7adcb0
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# 外部 Ruleset 工具組
通常在工作流程應用程式內使用規則時，這些規則算是組件的一部分。  在某些案例中，您可能會想要將 RuleSet 與組件分開維護，讓它們不需要重新建置及部署工作流程組件便可加以更新。  這個範例可讓您用資料庫來管理及編輯 RuleSet，並可從執行階段的工作流程中存取這些 RuleSet。  這樣可讓執行中的工作流程執行個體自動納入 RuleSet 變更。  
  
 外部 RuleSet 工具組範例包含 Windows Forms 工具，可用於在資料庫中管理及編輯 RuleSet 版本。  它也包含執行這些規則的活動和主機服務。  
  
> [!NOTE]
>  這個範例需要 [Microsoft SQL Server](http://go.microsoft.com/fwlink/?LinkId=96181)。  
  
 [!INCLUDE[vsprvsext](../../../../includes/vsprvsext-md.md)] 提供 RuleSet 編輯器做為 Windows Workflow Foundation \(WF\) 的一部分。  您可以在工作流程中按兩下 `Policy` 活動來啟動這個編輯器；它會將已定義的 RuleSet 物件序列化到與此工作流程有關聯的 .rules 檔案 \(`Policy` 活動會針對該工作流程執行 RuleSet 執行個體\)。  當您建置工作流程專案時，.rules 檔案會編譯成組件來做為資源。  
  
 這個範例的元件包括：  
  
-   RuleSet 圖形使用者介面工具，它可用於編輯及管理資料庫中 RuleSet 版本。  
  
-   設定在主應用程式上的 RuleSet 服務，它可以從資料庫存取 RuleSet。  
  
-   `ExternalPolicy` 活動，它會向 RuleSet 服務要求 RuleSet，並針對工作流程執行 RuleSet。  
  
 這些元件的互動方式如圖 1 所示。  後面各節將說明各個元件。  
  
 ![外部 RuleSet 範例概念概觀](../../../../docs/framework/windows-workflow-foundation/samples/media/rulesettoolkitsampleoverview.gif "RuleSetToolkitSampleOverview")  
  
 圖 1：範例概觀  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。  請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[適用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。  此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ExternalRuleSetToolKit`  
  
## RuleSet 工具  
 RuleSet 工具的螢幕擷取畫面如圖 2 所示。  您可以從 \[**規則存放區**\] 功能表，從資料庫載入可用的 RuleSet，並將修改過的 RuleSet 存回該存放區。  應用程式組態檔會提供 RuleSet 資料庫的資料庫連線字串。  當您啟動此工具時，它會從設定的資料庫自動載入 RuleSet。  
  
 ![外部 RuleSet 工具組範例輸出](../../../../docs/framework/windows-workflow-foundation/samples/media/rulesetbrowser.gif "RuleSetBrowser")  
  
 圖 2：RuleSet 瀏覽器  
  
 RuleSet 工具會將主要和次要版本號碼套用至 RuleSet，讓您可以同時維護及儲存多個版本 \(除了版本控制功能，此工具不提供鎖定或其他組態管理功能\)。  使用這個工具，您便可以建立新的 RuleSet 版本或刪除現有的版本。  當您按一下 \[**新增**\] 時，此工具會建立新的 RuleSet 名稱，並套用 1.0 版。  當您複製某個版本時，此工具會建立所選取 RuleSet 版本的複本 \(包括其內含的規則\)，並指派全新的唯一版本號碼。  這些版本號碼是以現有 RuleSet 的版本號碼為基礎。  您可以使用表單中相關欄位來變更該 RuleSet 的名稱和版本號碼。  
  
 當您按一下 \[**編輯規則**\] 時，就會啟動 RuleSet 編輯器，如圖 3 所示。  
  
 ![外部 RuleSet 工具組範例輸出](../../../../docs/framework/windows-workflow-foundation/samples/media/ruleseteditor.gif "RuleSetEditor")  
  
 圖 3：RuleSet 編輯器  
  
 這等於重新裝載屬於 Windows Workflow Foundation [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 增益集之一部分的編輯器對話方塊。  它會提供相同的功能，包括 Intellisense 支援。  這些規則是針對與工具中 RuleSet 有關聯的目標類型 \(例如工作流程\) 所撰寫；當您按一下主要工具對話方塊中的 \[**瀏覽**\] 時，\[**工作流程\/類型選取器**\] 對話方塊便會出現，如圖 4 所示。  
  
 ![工作流程&#47;類型選取項目](../../../../docs/framework/windows-workflow-foundation/samples/media/71f08d57-e8f2-499e-8151-ece2cbdcabfd.gif "71f08d57\-e8f2\-499e\-8151\-ece2cbdcabfd")  
  
 圖 4：工作流程\/類型選取器  
  
 您可以使用 \[**工作流程\/類型選取器**\] 對話方塊來指定組件及該組件內的特定類型。  這個類型就是所撰寫 \(及執行\) 之規則的目標類型。  在多數情況下，此目標類型是工作流程或某些其他活動類型。  然而，您可以對任何 .NET 型別執行 RuleSet。  
  
 組件檔案的路徑和類型名稱會隨 RuleSet 存放在資料庫中，因此如果是從資料庫擷取該 RuleSet，此工具會嘗試自動載入該目標類型。  
  
 當您在 \[**工作流程\/類型選取器**\] 對話方塊中按一下 \[**確定**\] 時，它會根據 RuleSet 來驗證所選取的類型，以確保該目標類型具有規則會參考的所有成員。  錯誤會顯示在 \[**驗證錯誤**\] 對話方塊中 \(請參閱圖 5\)。  您可以選擇不管錯誤而繼續變更，或按一下 \[**取消**\]。  您可以從主要工具對話方塊內的 \[**工具**\] 功能表按一下 \[**驗證**\]，針對目標活動來重新驗證 RuleSet 版本。  
  
 ![從外部 RuleSet 範例驗證錯誤](../../../../docs/framework/windows-workflow-foundation/samples/media/validationerrorsruleset.png "ValidationErrorsRuleSet")  
  
 圖 5：驗證錯誤  
  
 您可以從工具中的 \[**資料**\] 功能表匯入及匯出 RuleSet。  當您按一下 \[**匯入**\] 時，檔案選擇器對話方塊便會出現，這時您就可以從中選取 .rules 檔案。  這個檔案不一定是您最初在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建立的檔案。  此 .rules 檔案應該會包含已序列化的 `RuleDefinitions` 執行個體，該執行個體會包含條件的集合和 RuleSet 的集合。  雖然此工具不會使用該條件集合，但是它會使用 `RuleDefinitions` .rules 格式來允許與 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 環境的互動。  
  
 選取 .rules 檔案之後，\[**RuleSet 選取器**\] 對話方塊便會出現 \(請參閱圖 6\)。  您可以使用此對話方塊，選擇要匯入之檔案中的 RuleSet \(預設值是指定所有 RuleSet\)。  在此 .rules 檔案中的 RuleSet 並沒有版本號碼，因為它們在 WF 專案中的版本控制和組件中的版本是相同的。  在匯入程序期間，此工具會自動指派下一個可用的主要版本號碼 \(您可以在匯入之後變更\)；您可以在 \[**RuleSet 選取器**\] 清單中看到指派的版本號碼。  
  
 此工具會針對其匯入的各個 RuleSet，根據 RuleSet 中所使用的成員，嘗試從 .rules 檔案 \(如果存在\) 位置下的 bin\\Debug 資料夾找出相關聯的類型。  如果此工具找到多個相符的類型，它就會嘗試根據 .rules 檔案名稱和類型名稱之間的配對來選擇類型 \(例如，`Workflow1` 類型會對應至 Workflow1.rules\)。  如果存在多個相符類型，便會提示您要選取類型。  如果這個自動識別機制無法找出相符的組件或類型，則在匯入之後，您可以按一下主要工具對話方塊上的 \[**瀏覽**\] 來巡覽至相關的類型。  
  
 ![Ruleset 選取器](../../../../docs/framework/windows-workflow-foundation/samples/media/rulesetselector.gif "RuleSetSelector")  
  
 圖 6：RuleSet 選取器  
  
 當您從主要工具功能表按一下 \[**資料\-匯出**\] 時，\[**RuleSet 選取器**\] 對話方塊會再次出現，這時您可以從其中決定應從資料庫匯出的 RuleSet。  當您按一下 \[**確定**\] 時，\[**儲存檔案**\] 對話方塊會出現，這時您可在其中指定結果 .rules 檔案的名稱和位置。  由於 .rules 檔案不包含版本資訊，因此您只能選取一個具有指定 RuleSet 名稱的 RuleSet 版本。  
  
## PolicyFromService 活動  
 `PolicyFromService` 活動的程式碼是很直接的工作。  它的運作方式十分類似 WF 所提供的 `Policy` 活動，但是它不是從 .rules 檔案擷取目標 RuleSet，而是呼叫主機服務以取得 RuleSet 執行個體。  然後它會對根工作流程活動執行個體執行 RuleSet。  
  
 如果要在工作流程中使用活動，請從您的工作流程專案新增 `PolicyActivities` 和 `RuleSetService` 組件的參考。  如需如何將活動新增至工具箱的討論，請參閱本主題結尾的程序。  
  
 在將活動放入工作流程之後，您必須提供要執行的 RuleSet 的名稱。  您可以輸入名稱做為常值，或繫結至另一個活動的工作流程變數或屬性。  或者，您可以輸入應該要執行之特定 RuleSet 的版本號碼。  如果您保留主要和次要版本號碼的預設值為 0 ，該活動就會自動使用資料庫提供的最新版本號碼。  
  
## RuleSet 服務  
 此服務會負責從資料庫擷取指定的 RuleSet 版本，並將它傳回給呼叫活動。  如先前所討論，如果傳遞到 `GetRuleSet` 呼叫中的主要和次要版本值都是 0，此服務便會擷取最新的版本。  此時並不會快取任何 RuleSet 定義或執行個體；同樣地，這時沒有可將 RuleSet 版本標記為「已部署」以便區別進行中之 RuleSet 的功能。  
  
 由服務存取的資料庫，應該要經由應用程式組態檔設定於主機上。  
  
#### 執行工具  
  
1.  負責設定由工具和服務使用之 RuleSet 資料表的資料夾中包含 Setup.sql 檔案。  您可以執行 Setup.cmd 批次檔，以便在 SQL Express 上建立 Rules 資料庫，以及設定 RuleSet 資料表。  
  
2.  如果您編輯批次檔或 Setup.sql，並指定不要使用 SQL Express 或是不要將資料表放入名稱有別於 `Rules` 的資料庫中，則在 RuleSet 工具和 `UsageSample` 專案中的應用程式組態檔應該要編輯成相同資訊。  
  
3.  在執行 Setup.sql 指令碼之後，您就可以建置 `ExternalRuleSetToolkit` 方案，然後從 ExternalRuleSetTool 專案啟動 RuleSet 工具。  
  
4.  `RuleSetToolkitUsageSample` 循序工作流程主控台應用程式方案包括工作流程範例。  此工作流程是由一個 `PolicyFromService` 活動和兩個變數、`orderValue` 和 `discount` 所組成的，而且它是目標 RuleSet 執行的依據。  
  
5.  如果要使用範例，請建置 `RuleSetToolkitUsageSample` 方案。  接著，從 RuleSet 工具主功能表按一下 \[**資料\-匯入**\]，並指向 RuleSetToolkitUsageSample 資料夾中的 DiscountRuleSet.rules 檔案。  按一下 \[**規則存放區\-儲存**\] 功能表選項，即可將匯入的 RuleSet 儲存至資料庫。  
  
6.  由於 `PolicyActivities` 組件是從範例工作流程專案參考的，因此 `PolicyFromService` 活動會出現在工作流程中。  然而，根據預設，它不會出現在工具箱中。  若要將它新增至工具箱，請執行下列操作：  
  
    -   用滑鼠右鍵按一下工具箱，然後選取 \[**選擇項目**\] \(這可能需要一段時間\)。  
  
    -   當 \[**選擇工具箱項目**\] 對話方塊出現時，按一下 \[**活動**\] 索引標籤。  
  
    -   瀏覽至 `ExternalRuleSetToolkit` 方案中的 `PolicyActivities` 組件，然後按一下 \[**開啟**\]。  
  
    -   請確定已在 \[**選擇工具箱項目**\] 對話方塊中選取了 `PolicyFromService` 活動，然後按一下 \[**確定**\]。  
  
    -   現在活動應會出現在 \[**RuleSetToolkitUsageSample 元件**\] 分類中的工具箱中。  
  
7.  RuleSet 服務已經由 Program.cs 中的下列陳述式，設定於主控台應用程式主機上。  
  
    ```  
    workflowRuntime.AddService(new RuleSetService());  
    ```  
  
8.  您也可以使用組態檔在主機上設定服務，如需詳細資訊，請參閱 SDK 文件。  
  
9. 應用程式組態檔會新增至工作流程專案，以指定要由服務使用的資料庫的連線字串。  這個連線字串應該就是 RuleSet 工具所使用的連線字串，它會指向包含該 RuleSet 資料表的資料庫。  
  
10. 現在，您可以用處理其他任何工作流程主控台應用程式的方式來執行 `RuleSetToolkitUsageSample` 專案。  在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中按 F5 或 Ctrl\+F5，或直接執行 RuleSetToolkitUsageSample.exe 檔案。  
  
    > [!NOTE]
    >  您必須先關閉 RuleSet 工具才可重新編譯此使用範例，因為工具會載入此使用範例組件。  
  
## 請參閱