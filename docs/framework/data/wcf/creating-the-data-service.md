---
title: 在 Visual Studio 中建立 WCF 資料服務
ms.date: 08/24/2018
dev_langs:
- csharp
- vb
ms.assetid: 34d1d971-5e18-4c22-9bf6-d3612e27ea59
ms.openlocfilehash: 582f5f2d6d82613736ed795eebe5129284cdac6e
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052988"
---
# <a name="create-the-data-service"></a>建立資料服務

在本主題中，您會建立範例資料服務，使用 WCF Data Services 來公開[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]以 Northwind 範例資料庫為基礎的摘要。 這個工作包含下列基本步驟：

1. 建立 ASP.NET Web 應用程式。

2. 使用實體資料模型工具定義資料模型。

3. 將資料服務加入至 Web 應用程式。

4. 啟用資料服務的存取。

## <a name="create-the-aspnet-web-app"></a>建立 ASP.NET web 應用程式

1. **在 Visual Studio 的 [檔案**] 功能表上，選取 [**新增** > **專案**]。

1. 在 [**新增專案**] 對話方塊的 [Visual Basic] 或 [ C#視覺效果] 底下，選取 [ **web** ] 類別，然後選取 [ **ASP.NET web 應用程式**]。

1. 輸入`NorthwindService`作為專案的名稱，然後選取 **[確定]** 。

1. 在 [**新增 ASP.NET Web 應用程式**] 對話方塊中，選取 [**空白**]，然後選取 **[確定]** 。

1. (選擇性) 指定 Web 應用程式的連接埠號碼。 注意：此通訊埠`12345`編號會用於這一系列的快速入門主題。

    1. 在**方案總管**中，以滑鼠右鍵按一下您剛建立的 ASP.NET 專案，然後選擇 [**屬性**]。

    2. 選取 [ **Web** ] 索引標籤，並將 [**特定埠**] 文字方塊的`12345`值設定為。

## <a name="define-the-data-model"></a>定義資料模型

1. 在**方案總管**中，以滑鼠右鍵按一下 ASP.NET 專案的名稱，然後按一下 [**加入** > **新專案**]。

2. 在 [**加入新專案**] 對話方塊中，選取 [**資料**] 類別，然後選取 [ **ADO.NET 實體資料模型**]。

3. 針對資料模型的名稱，輸入`Northwind.edmx`。

4. 在**實體資料模型 Wizard**中，從 [資料庫] 選取 [ **EF Designer**]，然後按 **[下一步]** 。

5. 執行下列其中一個步驟，將資料模型連接至資料庫，然後按 **[下一步]** ：

    - 如果您尚未設定資料庫連接，請按一下 [**新增連接**]，然後建立新的連接。 如需詳細資訊，請參閱[如何：建立 SQL Server 資料庫](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90))的連接。 此 SQL Server 執行個體必須已附加 Northwind 範例資料庫。

         \-或-

    - 如果您擁有已經設定為連接至 Northwind 資料庫的資料庫連接，請從連接清單中選取該連接。

6. 在精靈的最後一頁上，選取資料庫中所有資料表的核取方塊，並且清除檢視表和預存程序 (Stored Procedure) 的核取方塊。

7. 按一下 [完成] 以關閉精靈。

## <a name="create-the-wcf-data-service"></a>建立 WCF 資料服務

1. 在**方案總管**中，以滑鼠右鍵按一下 ASP.NET 專案，然後選擇 [**加入** > **新專案**]。

2. 在 [**加入新專案**] 對話方塊中，從 [ **Web** ] 類別選取 [ **WCF 資料服務**專案] 範本。

   ![Visual Studio 2015 中的 WCF 資料服務專案範本](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > **WCF 資料服務**範本可在 Visual Studio 2015 中取得，但 Visual Studio 2017 則不提供。

3. 針對服務的名稱，輸入`Northwind`。

     Visual Studio 會針對新的服務建立 XML 標記和程式碼檔案。 根據預設，程式碼編輯器視窗隨即開啟。 在 [**方案總管] 中**，此服務具有名稱 Northwind，副檔名 *.svc.cs*或 *.svc.vb*。

4. 在資料服務的程式碼裡，於定義資料服務和型別的類別定義中，取代註解 `/* TODO: put your data source class name here */`，該型別是資料模型的實體容器，在這個案例中是 `NorthwindEntities`。 類別定義看起來應如下列：

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

## <a name="enable-access-to-data-service-resources"></a>啟用資料服務資源的存取權

1. 在資料服務的程式碼中，以下列程式碼取代 `InitializeService` 函數中的預留位置程式碼：

     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#allreadconfig)]

     如此可讓授權的用戶端具有指定之實體集資源的讀取和寫入存取權。

    > [!NOTE]
    > 任何可以存取 ASP.NET 應用程式的用戶端也可以存取資料服務公開的資源。 在產生資料服務的過程中，若要避免未經授權存取資源，您也應該要保護應用程式本身。 如需詳細資訊，請參閱 [Securing WCF Data Services](securing-wcf-data-services.md)。

## <a name="next-steps"></a>後續步驟

您已成功建立新的資料服務，它會公開以 Northwind 範例資料庫為基礎的 OData 摘要，而且您已針對具有 ASP.NET Web 應用程式許可權的用戶端，啟用其摘要的存取權。 接下來，您將從 Visual Studio 啟動資料服務，並透過網頁瀏覽器提交 HTTP GET 要求，以存取 OData 摘要：

> [!div class="nextstepaction"]
> [從網頁瀏覽器存取服務](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

## <a name="see-also"></a>另請參閱

- [ADO.NET 實體資料模型工具](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))
