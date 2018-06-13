---
title: .NET Framework 系統管理員部署手冊
ms.date: 04/10/2018
helpviewer_keywords:
- administrator's guide, deploying .NET Framework
- deployment [.NET Framework], administrator's guide
ms.assetid: bee14036-0436-44e8-89f5-4bc61317977a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9b4c2d4205e87d8be21f82eaf74b17e316d9057e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33394328"
---
# <a name="net-framework-deployment-guide-for-administrators"></a>.NET Framework 系統管理員部署手冊
這篇逐步解說文章將描述系統管理員如何使用 Microsoft System Center Configuration Manager，在整個網路上部署 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 及其系統相依性。 本文章假設所有目標用戶端電腦都符合 .NET Framework 的最低需求。 如需安裝 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 的軟體和硬體需求清單，請參閱[系統需求](../../../docs/framework/get-started/system-requirements.md)。  
  
> [!NOTE]
>  本文中提到的軟體包括 (但不限於) [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]、System Center Configuration Manager 和 Active Directory，這些軟體皆受授權條款和條件之限制。 這些指示假定軟體之適當使用人均已檢視並接受該等授權條款和條件。 這些指示不可撤回任何該等授權合約之規定條件。  
>   
>  如需 .NET Framework 支援的資訊，請參閱 Microsoft 技術支援網站上的 [Microsoft .NET Framework 支援週期原則](http://go.microsoft.com/fwlink/?LinkId=196607)。  
  
 此主題包括下列章節：  
  
 [部署程序](#the_deployment_process)  
 [部署 .NET Framework](#deploying_in_a_test_environment)  
 [建立集合](#creating_a_collection)  
 [建立套件和程式](#creating_a_package)  
 [選取發佈點](#select_dist_point)  
 [部署套件](#deploying_package)  
[資源](#resources)  
[疑難排解](#troubleshooting)  
  
<a name="the_deployment_process"></a>   
## <a name="the-deployment-process"></a>部署程序  
 一旦您備妥提供支援的基礎結構之後，便可以用 System Center 2012 Configuration Manager 將 .NET Framework 可轉散發套件部署到網路上的電腦。 建置基礎結構包括建立和定義五個主要部分：集合、軟體套件和程式、發佈點以及部署。  
  
-   **集合**：集合是指例如使用者、使用者群組或電腦等 Configuration Manager 資源的群組，也就是 .NET Framework 部署的目標。 如需詳細資訊，請參閱 Configuration Manager 文件庫中的 [Configuration Manager 中的集合](http://technet.microsoft.com/library/gg682169.aspx)。  
  
-   **套件和程式**：通常代表要安裝到用戶端電腦上的軟體應用程式，不過也可能包含個別檔案、更新，甚至個別命令。 如需詳細資訊，請參閱 Configuration Manager 文件庫中的 [Configuration Manager 中的套件和程式](http://technet.microsoft.com/library/gg699369.aspx)。  
  
-   **發佈點**：是指 Configuration Manager 網站系統角色，負責存放軟體在用戶端電腦上執行所需的檔案。 當 Configuration Manager 用戶端接收並處理軟體部署時，就會連絡發佈點，以便下載軟體相關內容並啟動安裝程序。 如需詳細資訊，請參閱 Configuration Manager 文件庫中的[介紹 Configuration Manager 中的內容管理](http://technet.microsoft.com/library/gg682083.aspx)。  
  
-   **部署**：負責指示所指定目標集合的適當成員安裝軟體套件。 如需詳細資訊，請參閱 Configuration Manager 文件庫中的[如何在 Configuration Manager 中部署應用程式](http://technet.microsoft.com/library/gg682082.aspx)。  
  
> [!IMPORTANT]
>  本主題中的程序包含建立和部署套件與程式的一般設定，不過可能無法涵蓋所有可能的設定。 如需其他 Configuration Manager 部署選項，請參閱 [Configuration Manager 文件庫](http://technet.microsoft.com/library/gg682041.aspx)。  
  
<a name="deploying_in_a_test_environment"></a>   
## <a name="deploying-the-net-framework"></a>部署 .NET Framework  
 您可以使用 System Center 2012 Configuration Manager 部署 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 的無訊息安裝，也就是說使用者不會與安裝程序互動。 請依照下列步驟：  
  
1.  [建立集合](#creating_a_collection)。  
  
2.  [建立 .NET Framework 可轉散發套件的套件和程式](#creating_a_package)。  
  
3.  [選取發佈點](#select_dist_point)。  
  
4.  [部署套件](#deploying_package)。  
  
<a name="creating_a_collection"></a>   
### <a name="create-a-collection"></a>建立集合  
 在這個步驟中，您將選取部署套件和程式的目標電腦，並將它們組成裝置集合。 若要在 Configuration Manager 中建立集合，您可以使用直接成員資格規則 (也就是手動指定集合成員) 或查詢規則 (也就是 Configuration Manager 根據您指定的準則決定集合成員)。 如需包括查詢和直接規則的成員資格規則詳細資訊，請參閱 Configuration Manager 文件庫中的[介紹 Configuration Manager 中的集合](http://technet.microsoft.com/library/gg682177.aspx)。  
  
 若要建立集合：  
  
1.  在 Configuration Manager 主控台中，選擇 [資產與相容性]。  
  
2.  在 [資產與相容性] 工作區中，選擇 [裝置集合]。  
  
3.  在 [首頁] 索引標籤的 [建立] 群組中，選擇 [建立裝置集合]。  
  
4.  在 [建立裝置集合精靈] 的 [一般] 頁面上，輸入集合的名稱。  
  
5.  選擇 [瀏覽] 以指定限制集合。  
  
6.  在 [成員資格規則] 頁面上，選擇 [新增規則]，然後選擇 [直接規則] 開啟 [建立直接成員資格規則精靈]。 選擇 [下一步]。  
  
7.  在 [搜尋資源] 頁面的 [資源類別] 清單中，選擇 [系統資源]。 在 [屬性名稱] 清單中，選擇 [名稱]。 在 [值] 欄位中輸入 `%`，然後選擇 [下一步]。  
  
8.  在 [選取資源] 頁面中，選取要在其中部署 .NET Framework 之每一部電腦的核取方塊。 選擇 [下一步]，然後完成精靈。  
  
9. 在 [建立裝置集合精靈] 的 [成員資格規則] 頁面上，選擇 [下一步]，然後完成精靈。  
  
 如需有關集合的詳細資訊，請參閱 Configuration Manager 文件庫中的 [Configuration Manager 中的集合](http://technet.microsoft.com/library/bb693730.aspx)。  
  
<a name="creating_a_package"></a>   
### <a name="create-a-package-and-program-for-the-net-framework-redistributable-package"></a>建立 .NET Framework 可轉散發套件的套件和程式  
 下列步驟會手動建立 .NET Framework 可轉散發套件的封裝。 套件包含指定的 .NET Framework 安裝參數，以及要從中將套件散發至目標電腦的來源位置。  
  
 若要建立封裝：  
  
1.  在 Configuration Manager 主控台中，選擇 [軟體程式庫]。  
  
2.  在 [軟體程式庫] 工作區中展開 [應用程式管理]，然後選擇 [套件]。  
  
3.  在 [首頁] 索引標籤的 [建立] 群組中，選擇 [建立套件]。  
  
4.  在 [建立套件和程式精靈] 的 [套件] 頁面上，輸入下列資訊：  
  
    -   名稱：`.NET Framework 4.5`  
  
    -   製造商：`Microsoft`  
  
    -   語言。 `English (US)`  
  
5.  選擇 [此套件包含來源檔案]，然後選擇 [瀏覽] 以選取包含 .NET Framework 安裝檔案的本機或網路資料夾。 選取資料夾後，選擇 [確定]，然後選擇 [下一步]。  
  
6.  在精靈的 [程式類型] 頁面上，選擇 [標準程式]，然後選擇 [下一步]。  
  
7.  在 [建立套件和程式精靈] 的 [程式] 頁面上，輸入下列資訊：  
  
    1.  **名稱：** `.NET Framework 4.5`  
  
    2.  **命令列︰** `dotNetFx45_Full_x86_x64.exe /q /norestart /ChainingPackage ADMINDEPLOYMENT` (這些步驟後的資料表中會說明命令列選項)  
  
    3.  **執行：** 選擇 [隱藏]。  
  
    4.  **程式可以執行：** 選擇這個選項會指定無論使用者是否登入，程式都可以執行。  
  
8.  在 [需求] 頁面上，選擇 [下一步] 接受預設值，然後完成精靈。  
  
 下表描述在步驟 7 中指定的命令列選項。  
  
|選項|描述|  
|------------|-----------------|  
|**/q**|設定無訊息模式。 不需要使用者輸入，也不會顯示輸出。|  
|**/norestart**|避免安裝程式自動重新開機。 如果您使用這個選項，Configuration Manager 就必須處理電腦重新啟動。|  
|**/chainingpackage** *PackageName*|指定執行鏈結之封裝的名稱。 已註冊 [Microsoft 客戶經驗改進計劃](http://go.microsoft.com/fwlink/p/?LinkId=248244)的人將會收到這項資訊與其他安裝工作階段資訊的報告。 如果套件名稱包含空格，分隔符號請使用雙引號，例如：**/chainingpackage "Chaining Product"**。|  
  
 這些步驟會建立名為 .NET Framework 4.5 的套件。 程式會部署 .NET Framework 4.5 的無訊息安裝。 在無訊息安裝中，使用者不會與安裝程序互動，而鏈結應用程式必須擷取傳回碼並處理重新開機，請參閱[取得安裝套件的進度資訊](http://go.microsoft.com/fwlink/?LinkId=179606)。  
 
<a name="select_dist_point"></a>   
### <a name="select-a-distribution-point"></a>選取發佈點  
 若要從伺服器將套件和程式散發到用戶端電腦，您必須先將站台系統指定為發佈點，然後再將套件散發至發佈點。  
  
 利用下列步驟為您在上一節中建立的 .NET Framework 4.5 套件選取發佈點：  
  
1.  在 Configuration Manager 主控台中，選擇 [軟體程式庫]。  
  
2.  在 [軟體程式庫] 工作區中展開 [應用程式管理]，然後選擇 [套件]。  
  
3.  從套件清單中，選取您在上一節中建立的套件 [.NET Framework 4.5]。  
  
4.  在 [首頁] 索引標籤的 [部署] 群組中，選擇 [散發內容]。  
  
5.  在 [散發內容精靈] 的 [一般] 索引標籤上，選擇 [下一步]。  
  
6.  在精靈的 [內容目的地] 頁面上，選擇 [新增]，然後選擇 [發佈點]。  
  
7.  在 [新增發佈點] 對話方塊中，選取要裝載套件和程式的發佈點，然後選擇 [確定]。  
  
8.  完成精靈。  
  
 現在套件中將會包含進行 .NET Framework 4.5 無訊息部署所需的全部資訊。 在您部署套件和程式之前，請先確認它已安裝在發佈點上，請參閱 Configuration Manager 文件庫中[在 Configuration Manager 中進行內容管理的操作和維護](http://technet.microsoft.com/library/gg712694.aspx#BKMK_MonitorContent)的＜監視內容＞一節。  
  
<a name="deploying_package"></a>   
### <a name="deploy-the-package"></a>部署套件  
 若要部署 .NET Framework 4.5 套件和程式：  
  
1.  在 Configuration Manager 主控台中，選擇 [軟體程式庫]。  
  
2.  在 [軟體程式庫] 工作區中展開 [應用程式管理]，然後選擇 [套件]。  
  
3.  從套件清單中，選取您所建立名為 [.NET Framework 4.5] 的套件。  
  
4.  在 [首頁] 索引標籤的 [部署] 群組中，選擇 [部署]。  
  
5.  在 [部署軟體精靈] 的 [一般] 頁面上，選擇 [瀏覽]，然後選取您先前建立的集合。 選擇 [下一步]。  
  
6.  在精靈的 [內容] 頁面上，確認已顯示軟體的發佈點，然後選擇 [下一步]。  
  
7.  在精靈的 [部署設定] 頁面中，確認 [動作] 設定為 [安裝]，且 [用途] 設定為 [必要項]。 這樣可確保軟體套件會是目標電腦上的必要安裝。 選擇 [下一步]。  
  
8.  在精靈的 [排程] 頁面中，指定要安裝 .NET Framework 的時機。 您可以選擇 [新增] 指派安裝時間，或是指示軟體在使用者登入或登出時安裝，或是盡快安裝。 選擇 [下一步]。  
  
9. 在精靈的 [使用者經驗] 頁面上，使用預設值並選擇 [下一步]。  
  
    > [!WARNING]
    >  您的實際執行環境可能有一些原則，而且這些原則需要不同的部署排程選項。 如需這些選項的詳細資訊，請參閱 TechNet Library 中的[通告名稱屬性：排程索引標籤](http://technet.microsoft.com/library/bb694016.aspx)。  
  
10. 在精靈的 [發佈點] 頁面上，使用預設值並選擇 [下一步]。  
  
11. 完成精靈。 您可以在 [監視] 工作區的 [部署] 節點中監視部署進度。  
  
 現在套件將會部署至目標集合，而且 .NET Framework 4.5 的無訊息安裝將開始進行。 如需 .NET Framework 4.5 安裝錯誤碼的詳細資訊，請參閱本主題稍後的[傳回碼](#return_codes)一節。  
  
<a name="resources"></a>   
## <a name="resources"></a>資源  
 如需有關測試和部署 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 可轉散發套件之基礎結構的詳細資訊，請參閱下列資源。  
  
 **Active Directory、DNS、DHCP：**  
  
-   [適用於 Windows Server 2008 的 Active Directory 網域服務](http://technet.microsoft.com/library/dd378891.aspx)  
  
-   [DNS 伺服器](http://technet.microsoft.com/library/cc732997.aspx)  
  
-   [DHCP 伺服器](http://technet.microsoft.com/library/cc896553.aspx)  
  
 **SQL Server 2008：**  
  
-   [安裝 SQL Server 2008 (SQL Server 影片)](http://technet.microsoft.com/library/dd299415.aspx)  
  
-   [適用於資料庫管理員的 SQL Server 2008 安全性概觀](http://download.microsoft.com/download/a/c/d/acd8e043-d69b-4f09-bc9e-4168b65aaa71/SQL2008SecurityOverviewforAdmins.docx)  
  
 **System Center 2012 Configuration Manager (管理點、發佈點)：**  
  
-   [System Center 2012 Configuration Manager 的網站管理](http://technet.microsoft.com/library/gg681983.aspx)  
  
-   [Configuration Manager 單一網站規劃與部署](http://technet.microsoft.com/library/bb680961.aspx)  
  
 **適用於 Windows 電腦的 System Center 2012 Configuration Manager 用戶端：**  
  
-   [部署 System Center 2012 Configuration Manager 的用戶端](http://technet.microsoft.com/library/gg699391.aspx)  
  
<a name="troubleshooting"></a>   
## <a name="troubleshooting"></a>疑難排解  
  
### <a name="log-file-locations"></a>記錄檔位置  
 在 .NET Framework 安裝過程中會產生下列記錄檔：  
  
 %temp%\Microsoft .NET Framework *版本*\*.txt  
 %temp%\Microsoft .NET Framework *版本*\*.html  
  
 其中*版本*是您要安裝的 .NET Framework 版本，例如 4.5 或 4.7.2。  
 
 您也可以使用 .NET Framework 安裝命令中的 `/log` 命令列選項，指定寫入記錄檔的目錄。 如需詳細資訊，請參閱[開發人員的 .NET Framework 部署指南](deployment-guide-for-developers.md#command-line-options)。 
 
 您可以使用[記錄收集工具](https://www.microsoft.com/download/details.aspx?id=12493)來收集 .NET Framework 記錄檔並建立縮減檔案大小的壓縮封包檔 (.cab)。  
  
<a name="return_codes"></a>   
### <a name="return-codes"></a>傳回碼  
 下表列出 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 可轉散發安裝程式最常見的傳回碼。 所有版本的安裝程式的傳回碼都相同。  
  
 如需詳細資訊的連結，請參閱下一節：[下載錯誤碼](#additional_error_codes)。  
  
|傳回碼|描述|  
|-----------------|-----------------|  
|0|安裝已順利完成。|  
|1602|使用者已取消安裝。|  
|1603|安裝期間發生嚴重錯誤。|  
|1641|需要重新開機才能完成安裝。 這個訊息表示成功。|  
|3010|需要重新開機才能完成安裝。 這個訊息表示成功。|  
|5100|使用者的電腦不符合系統需求。|  
  
<a name="additional_error_codes"></a>   
### <a name="download-error-codes"></a>下載錯誤碼  
  
-   [背景智慧型傳送服務 (BITS) 錯誤碼](http://msdn.microsoft.com/library/aa362823.aspx)  
  
-   [URL Moniker 錯誤碼](http://msdn.microsoft.com/library/ms775145.aspx)  
  
-   [WinHttp 錯誤碼](http://msdn.microsoft.com/library/aa383770.aspx)  
  
 其他錯誤碼：  
  
-   [Windows 安裝程式錯誤碼](http://msdn.microsoft.com/library/aa368542.aspx)  
  
-   [Windows Update 代理程式結果碼](http://technet.microsoft.com/library/cc720442.aspx)  
  
## <a name="see-also"></a>請參閱  
 [開發人員部署手冊](../../../docs/framework/deployment/deployment-guide-for-developers.md)  
 [系統需求](../../../docs/framework/get-started/system-requirements.md)
