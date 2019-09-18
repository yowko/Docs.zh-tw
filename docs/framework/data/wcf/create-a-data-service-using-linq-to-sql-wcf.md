---
title: 作法：使用 LINQ to SQL 資料來源建立資料服務（WCF Data Services）
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, LINQ to SQL
- WCF Data Services, providers
ms.assetid: 3b01c2fd-8c6e-4bf5-b38f-9e61bdc3c328
ms.openlocfilehash: 6489e451f3790e38ea821104fd2aca5a8c091ba6
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052994"
---
# <a name="how-to-create-a-data-service-using-a-linq-to-sql-data-source-wcf-data-services"></a>HOW TO：使用 LINQ to SQL 資料來源建立資料服務（WCF Data Services）

WCF Data Services 會將實體資料公開為數據服務。 反映提供者可讓您定義以任何類別為基礎的資料模型，其會公開傳回實作為<xref:System.Linq.IQueryable%601>的成員。 若要可以更新資料來源的資料，這些類別也必須實作 <xref:System.Data.Services.IUpdatable> 介面。 如需詳細資訊，請參閱[資料服務提供者](data-services-providers-wcf-data-services.md)。 本主題說明如何使用反映提供者，建立存取 Northwind 範例資料庫的 LINQ to SQL 類別以及如何根據這些資料類別，建立資料服務。

## <a name="to-add-linq-to-sql-classes-to-a-project"></a>將 LINQ to SQL 類別加入至專案

1. 從 Visual Basic 或C#應用程式中，按一下 [**專案**] 功能表上的 [**加入** > **新專案**]。

2. 按一下 [ **LINQ to SQL 類別**] 範本。

3. 將名稱變更為**Northwind. .dbml**。

4. 按一下 [新增]。

     Northwind.dbml 檔案會加入至專案，且會開啟 [物件關聯式設計工具] (O/R 設計工具)。

5. 在 **伺服器**/**資料庫總管**的 Northwind 底下，展開  `Customers` **資料表** ，然後將資料表拖曳至 物件關聯式設計工具（O/R 設計工具）。

     隨即建立 `Customer` 實體類別，並出現在設計介面上。

6. 針對 `Orders`、`Order_Details` 和 `Products` 資料表，重複步驟 6。

7. 以滑鼠右鍵按一下代表 LINQ to SQL 類別的新 .dbml 檔案，然後按一下 [**查看程式碼**]。

     這樣會建立名為 Northwind.cs 的新程式碼後置頁面，其中包含繼承自 <xref:System.Data.Linq.DataContext> 類別的部分類別定義，在此案例中是 `NorthwindDataContext`。

8. 以下列程式碼取代 Northwind.cs 程式碼檔案的內容。 此程式碼透過延伸 LINQ to SQL 產生的 <xref:System.Data.Linq.DataContext> 和資料類別，實作反映提供者：

     [!code-csharp[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_linq_provider/cs/northwind.cs#linq2sqlprovider)]
     [!code-vb[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_linq_provider/vb/northwind.vb#linq2sqlprovider)]

### <a name="to-create-a-data-service-by-using-a-linq-to-sql-based-data-model"></a>使用 LINQ to SQL 架構資料模組建立資料服務

1. 在**方案總管**中，以滑鼠右鍵按一下 ASP.NET 專案的名稱，然後按一下 [**加入** > **新專案**]。

2. 在 [**加入新專案**] 對話方塊中，從 [ **Web** ] 類別選取 [ **WCF 資料服務**] 範本。

   ![Visual Studio 2015 中的 WCF 資料服務專案範本](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > **WCF 資料服務**範本可在 Visual Studio 2015 中取得，但 Visual Studio 2017 則不提供。

3. 提供服務的名稱，然後按一下 **[確定]** 。

     Visual Studio 會針對新的服務建立 XML 標記和程式碼檔案。 根據預設，程式碼編輯器視窗隨即開啟。

4. 在資料服務的程式碼裡，於定義資料服務和型別的類別定義中，取代註解 `/* TODO: put your data source class name here */`，該型別是資料模型的實體容器，在這個案例中是 `NorthwindDataContext`。

5. 在資料服務的程式碼中，以下列程式碼取代 `InitializeService` 函數中的預留位置程式碼：

     [!code-csharp[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_linq_provider/cs/northwind.svc.cs#enableaccess)]
     [!code-vb[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_linq_provider/vb/northwind.svc.vb#enableaccess)]

     如此可讓已授權用戶端存取三個指定實體集的資源。

6. 若要使用網頁瀏覽器測試 Northwind 資料服務，請依照[從網頁瀏覽器存取服務](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)主題中的指示進行。

## <a name="see-also"></a>另請參閱

- [如何：使用 ADO.NET Entity Framework 資料來源建立資料服務](create-a-data-service-using-an-adonet-ef-data-wcf.md)
- [如何：使用反映提供者建立資料服務](create-a-data-service-using-rp-wcf-data-services.md)
- [資料服務提供者](data-services-providers-wcf-data-services.md)
