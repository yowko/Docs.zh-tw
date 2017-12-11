---
title: "建立資料服務"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 34d1d971-5e18-4c22-9bf6-d3612e27ea59
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 22fc561d7df9bbd81bf19d351af2d07bc6b51237
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="creating-the-data-service"></a>建立資料服務
在這個工作中，您將建立使用的範例資料服務[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]公開 [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] Northwind 範例資料庫為基礎的摘要。 這個工作包含下列基本步驟：  
  
1.  建立 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web 應用程式。  
  
2.  使用 [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] 工具來定義資料模型。  
  
3.  將資料服務加入至 Web 應用程式。  
  
4.  啟用資料服務的存取。  
  
> [!NOTE]
>  當您完成這項工作時所建立的 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web 應用程式會在 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 提供的 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 程式開發伺服器上執行。 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 程式開發伺服器只支援從本機電腦存取。 若要一併在開發期間更輕鬆地測試資料服務並進行疑難排解，請考慮使用 Internet Information Services (IIS) 執行可裝載資料服務的應用程式。 如需詳細資訊，請參閱 [How to: Develop a WCF Data Service Running on IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md)。  
  
### <a name="to-create-the-aspnet-web-application"></a>若要建立 ASP.NET Web 應用程式  
  
1.  在[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]上**檔案**功能表上，選取**新增**，然後選取**專案**。  
  
2.  在**新專案**對話方塊之下[!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]或[!INCLUDE[csprcs](../../../../includes/csprcs-md.md)]選取**Web**範本，，然後選取**ASP.NET Web 應用程式**。  
  
    > [!NOTE]
    >  如果您使用 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] Web Developer，就必須建立新網站，而非建立新的 Web 應用程式。  
  
3.  型別`NorthwindService`做為專案的名稱。  
  
4.  按一下 [確定]。  
  
5.  (選擇性) 指定 Web 應用程式的連接埠號碼。 注意：快速入門的其餘部分會使用通訊埠編號 `12345`。  
  
    1.  在**方案總管 中**，以滑鼠右鍵按一下名稱[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]專案您剛才建立的，然後按一下**屬性**。  
  
    2.  選取**Web**索引標籤，然後設定的值**特定通訊埠**文字方塊`12345`。  
  
### <a name="to-define-the-data-model"></a>若要定義資料模型  
  
1.  在**方案總管 中**，以滑鼠右鍵按一下名稱[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]專案，然後再按一下**加入新項目。**  
  
2.  在**加入新項目**對話方塊中，按一下 **資料**範本，然後選取**ADO.NET 實體資料模型**。  
  
3.  資料模型的名稱，輸入`Northwind.edmx`。  
  
4.  在[!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)]精靈中，選取**從資料庫產生**，然後按一下 **下一步**。  
  
5.  執行下列步驟中，連接到資料庫的資料模型，然後按一下**下一步**:  
  
    -   如果您沒有已設定的資料庫連接，按一下**新連線**並建立新的連接。 如需詳細資訊，請參閱[How to： 建立連接至 SQL Server 資料庫](http://go.microsoft.com/fwlink/?LinkId=123631)。 此 [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] 執行個體必須已附加 Northwind 範例資料庫。  
  
         \-或-  
  
    -   如果您擁有已經設定為連接至 Northwind 資料庫的資料庫連接，請從連接清單中選取該連接。  
  
6.  在精靈的最後一頁上，選取資料庫中所有資料表的核取方塊，並且清除檢視表和預存程序 (Stored Procedure) 的核取方塊。  
  
7.  按一下**完成**關閉精靈。  
  
    > [!NOTE]
    >  這樣產生的資料模型會在實體類型上公開外部索引鍵屬性。 使用 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 2008 建立的資料模型不包含這些外部索引鍵屬性。 因此，您必須更新之前為了存取 Northwind 資料服務所建立之任何用戶端應用程式的用戶端資料服務類別，此資料服務是在嘗試存取這一版的 Northwind 資料服務之前使用 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 2008 所建立。  
  
### <a name="to-create-the-data-service"></a>若要建立資料服務  
  
1.  在**方案總管 中**，以滑鼠右鍵按一下名稱您[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]專案，然後再按一下**加入新項目**。  
  
2.  在**加入新項目**對話方塊中，選取**WCF 資料服務**。  
  
3.  服務的名稱，輸入`Northwind`。  
  
     [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]Visual Studio 會針對新的服務建立 XML 標記和程式碼檔案。 根據預設，程式碼編輯器視窗隨即開啟。 在**方案總管 中**，服務將會具有名稱 Northwind，副檔名。 為.svc.cs 或.svc.vb。  
  
4.  在資料服務的程式碼裡，於定義資料服務和型別的類別定義中，取代註解 `/* TODO: put your data source class name here */`，該型別是資料模型的實體容器，在這個案例中是 `NorthwindEntities`。 類別定義看起來應如下列：  
  
     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#servicedefinition)]  
  
### <a name="to-enable-access-to-data-service-resources"></a>若要啟用資料服務資源的存取  
  
1.  在資料服務的程式碼中，以下列程式碼取代 `InitializeService` 函數中的預留位置程式碼：  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#allreadconfig)]  
  
     如此可讓授權的用戶端具有指定之實體集資源的讀取和寫入存取權。  
  
    > [!NOTE]
    >  任何可存取 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 應用程式的用戶端也可以存取資料服務公開的資源。 在產生資料服務的過程中，若要避免未經授權存取資源，您也應該要保護應用程式本身。 如需詳細資訊，請參閱 [Securing WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)。  
  
## <a name="next-steps"></a>後續步驟  
 您已成功建立新的資料服務公開[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]摘要，根據 Northwind 範例資料庫，而且您已啟用的存取權之用戶端上的權限摘要[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]Web 應用程式。 接下來，您會開始從資料服務[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]，您將存取[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]透過網頁瀏覽器的 HTTP GET 要求提交摘要：  
  
 [從網頁瀏覽器存取服務](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)  
  
## <a name="see-also"></a>另請參閱  
 [ADO.NET 實體資料模型工具](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527)
