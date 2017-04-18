---
title: "建立資料服務 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 34d1d971-5e18-4c22-9bf6-d3612e27ea59
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# 建立資料服務
在此工作中，您將建立一個範例資料服務，這個服務會使用 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 公開以 Northwind 範例資料庫為基礎的 [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] 摘要。此工作包含下列基本步驟：  
  
1.  建立 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web 應用程式。  
  
2.  使用 [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] 工具來定義資料模型。  
  
3.  將資料服務加入至 Web 應用程式。  
  
4.  啟用資料服務的存取。  
  
> [!NOTE]
>  當您完成這項工作時所建立的 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web 應用程式會在 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 提供的 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 程式開發伺服器上執行。  [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 程式開發伺服器只支援從本機電腦存取。  若要一併在開發期間更輕鬆地測試資料服務並進行疑難排解，請考慮使用 Internet Information Services \(IIS\) 執行可裝載資料服務的應用程式。  如需詳細資訊，請參閱[HOW TO：開發在 IIS 上執行的 WCF Data Service](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md)。  
  
### 若要建立 ASP.NET Web 應用程式  
  
1.  在 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 的 \[**檔案**\] 功能表上，選取 \[**新增**\]，然後選取 \[**專案**\]。  
  
2.  在 \[**新增專案**\] 對話方塊的 \[[!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]\] 或 \[[!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]\] 下方，選取 \[**Web**\] 範本，然後選取 \[**ASP.NET Web 應用程式**\]。  
  
    > [!NOTE]
    >  如果您使用 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] Web Developer，就必須建立新網站，而非建立新的 Web 應用程式。  
  
3.  輸入 `NorthwindService` 做為專案的名稱。  
  
4.  按一下 \[**確定**\]。  
  
5.  \(選擇性\) 指定 Web 應用程式的連接埠號碼。  注意：快速入門的其餘部分會使用通訊埠編號 `12345`。  
  
    1.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下您剛建立的 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 專案名稱，然後按一下 \[**屬性**\]。  
  
    2.  選取 \[**Web**\] 索引標籤，並將 \[**指定通訊埠**\] 文字方塊的值設定為 `12345`。  
  
### 若要定義資料模型  
  
1.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 專案名稱，然後按一下 \[**加入新項目**\]。  
  
2.  在 \[**加入新項目**\] 對話方塊中，按一下 \[**資料**\] 範本，然後選取 \[**ADO.NET 實體資料模型**\]。  
  
3.  針對資料模型的名稱，輸入 `Northwind.edmx`。  
  
4.  在 [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] 精靈中，選取 \[**從資料庫產生**\]，然後按 \[**下一步**\]。  
  
5.  進行下列其中一項步驟，將資料模型連接至資料庫，然後按一下 \[**下一步**\]：  
  
    -   如果您尚未設定資料庫連接，請按一下 \[**新增連接**\]，然後建立新的連接。  如需詳細資訊，請參閱 [HOW TO：建立連接至 SQL Server 資料庫](http://go.microsoft.com/fwlink/?LinkId=123631)。  此 [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] 執行個體必須已附加 Northwind 範例資料庫。  
  
         \-或\-  
  
    -   如果您擁有已經設定為連接至 Northwind 資料庫的資料庫連接，請從連接清單中選取該連接。  
  
6.  在精靈的最後一頁上，選取資料庫中所有資料表的核取方塊，並且清除檢視表和預存程序 \(Stored Procedure\) 的核取方塊。  
  
7.  按一下 \[**完成**\] 關閉精靈。  
  
    > [!NOTE]
    >  這樣產生的資料模型會在實體類型上公開外部索引鍵屬性。  使用 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 2008 建立的資料模型不包含這些外部索引鍵屬性。  因此，您必須更新之前為了存取 Northwind 資料服務所建立之任何用戶端應用程式的用戶端資料服務類別，此資料服務是在嘗試存取這一版的 Northwind 資料服務之前使用 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 2008 所建立。  
  
### 若要建立資料服務  
  
1.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 專案名稱，然後按一下 \[**加入新項目**\]。  
  
2.  選取 \[**加入新項目**\] 對話方塊中的 \[**WCF Data Service**\]。  
  
3.  針對服務名稱，輸入 `Northwind`。  
  
     [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]Visual Studio 會針對新的服務建立 XML 標記和程式碼檔案。  根據預設，程式碼編輯器視窗隨即開啟。  在 \[**方案總管**\] 中，這個服務將會具有名稱 Northwind，副檔名為 .svc.cs 或 .svc.vb。  
  
4.  在資料服務的程式碼裡，於定義資料服務和型別的類別定義中，取代註解 `/* TODO: put your data source class name here */`，該型別是資料模型的實體容器，在這個案例中是 `NorthwindEntities`。  類別定義看起來應如下列：  
  
     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#servicedefinition)]  
  
### 若要啟用資料服務資源的存取  
  
1.  在資料服務的程式碼中，以下列程式碼取代 `InitializeService` 函數中的預留位置程式碼：  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#allreadconfig)]  
  
     如此可讓授權的用戶端具有指定之實體集資源的讀取和寫入存取權。  
  
    > [!NOTE]
    >  任何可存取 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 應用程式的用戶端也可以存取資料服務公開的資源。  在產生資料服務的過程中，若要避免未經授權存取資源，您也應該要保護應用程式本身。  如需詳細資訊，請參閱[保護 WCF Data Services 的安全](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)。  
  
## 後續步驟  
 您已成功建立可公開 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 摘要的新資料服務 \(此摘要是以 Northwind 範例資料庫為基礎\)，而且您已啟用用戶端的摘要存取權，該用戶端擁有 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web 應用程式權限。  接著，您會從 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 啟動資料服務，然後透過 Web 瀏覽器送出 HTTP GET 要求，藉以存取 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 摘要：  
  
 [從 Web 瀏覽器存取服務](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)  
  
## 請參閱  
 [ADO.NET Entity Data Model  Tools](http://msdn.microsoft.com/zh-tw/91076853-0881-421b-837a-f582f36be527)