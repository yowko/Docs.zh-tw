---
title: 在 Visual Studio 中建立 WCF 資料服務
ms.date: 08/24/2018
dev_langs:
- csharp
- vb
ms.assetid: 34d1d971-5e18-4c22-9bf6-d3612e27ea59
ms.openlocfilehash: e8d82ff8958af12842366911b6633ea6b2e0efbb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59517222"
---
# <a name="create-the-data-service"></a>建立資料服務

本主題中，您可以建立會使用 WCF 資料服務公開的範例資料服務[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]Northwind 範例資料庫為基礎的摘要。 這個工作包含下列基本步驟：

1. 建立 ASP.NET Web 應用程式。

2. 使用實體資料模型工具定義資料模型。

3. 將資料服務加入至 Web 應用程式。

4. 啟用資料服務的存取。

## <a name="create-the-aspnet-web-app"></a>建立 ASP.NET web 應用程式

1. 在 Visual Studio 中，在**檔案**功能表上，選取**新增** > **專案**。

1. 在 **新的專案**對話方塊的 Visual Basic 或 Visual C# 中選取下**Web**類別目錄，然後選取**ASP.NET Web 應用程式**。

1. 請輸入`NorthwindService`做為名稱的專案，然後選取 **[確定]**。

1. 在 **新的 ASP.NET Web 應用程式**對話方塊中，選取**空白**，然後選取**確定**。

1. (選擇性) 指定 Web 應用程式的連接埠號碼。 注意： 連接埠號碼`12345`會在這一系列的快速入門主題。

    1. 在 **方案總管**，以滑鼠右鍵按一下您剛才建立的 ASP.NET 專案，然後選擇**屬性**。

    2. 選取  **Web**索引標籤，並將值**特定連接埠**文字方塊中，以`12345`。

## <a name="define-the-data-model"></a>定義資料模型

1. 在 [**方案總管] 中**，以滑鼠右鍵按一下 ASP.NET 專案中，名稱，然後按一下**新增** > **新項目**。

2. 在 **加入新項目**對話方塊中，選取**資料**類別，然後再選取**ADO.NET 實體資料模型**。

3. 針對資料模型的名稱，輸入`Northwind.edmx`。

4. 在**Entity Data Model 精靈**，選取**資料庫的 EF Designer**，然後按一下**下一步**。

5. 連接到資料庫的資料模型，執行下列步驟中，其中，然後按一下**下一步**:

    -   如果您沒有已設定的資料庫連線，請按一下**新的連接**並建立新的連接。 如需詳細資訊，請參閱[如何：建立連接至 SQL Server 資料庫](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90))。 此 SQL Server 執行個體必須已附加 Northwind 範例資料庫。

         \-或-

    -   如果您擁有已經設定為連接至 Northwind 資料庫的資料庫連接，請從連接清單中選取該連接。

6. 在精靈的最後一頁上，選取資料庫中所有資料表的核取方塊，並且清除檢視表和預存程序 (Stored Procedure) 的核取方塊。

7. 按一下 **完成**即可關閉精靈。

## <a name="create-the-wcf-data-service"></a>建立 WCF 資料服務

1. 在 [**方案總管] 中**，以滑鼠右鍵按一下 ASP.NET 專案，然後選擇**新增** > **新項目**。

2. 在 **加入新項目**對話方塊中，選取**WCF 資料服務**項目範本，從**Web**類別目錄。

   ![Visual Studio 2015 中的 WCF 資料服務項目範本](media/wcf-data-service-item-template.png)

   > [!NOTE]
   > **WCF 資料服務**範本位於 Visual Studio 2015，但不是能在 Visual Studio 2017。

3. 如需服務的名稱，輸入`Northwind`。

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
    > 任何可以存取 ASP.NET 應用程式的用戶端也可以存取資料服務公開的資源。 在產生資料服務的過程中，若要避免未經授權存取資源，您也應該要保護應用程式本身。 如需詳細資訊，請參閱 [Securing WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md)。

## <a name="next-steps"></a>後續步驟

您已成功建立新的資料服務公開以 Northwind 範例資料庫為基礎的 OData 摘要，且您已啟用存取該用戶端擁有 ASP.NET Web 應用程式的權限摘要。 接下來，您將從 Visual Studio 啟動資料服務，並存取 OData 摘要送出 HTTP GET 要求，透過網頁瀏覽器：

> [!div class="nextstepaction"]
> [從網頁瀏覽器存取服務](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

## <a name="see-also"></a>另請參閱

- [ADO.NET 實體資料模型工具](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))