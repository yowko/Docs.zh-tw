---
title: 作法：使用 ADO.NET Entity Framework 資料來源建立資料服務（WCF Data Services）
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, providers
- WCF Data Services, Entity Framework
ms.assetid: 6d11fec8-0108-42f5-8719-2a7866d04428
ms.openlocfilehash: 8c597738d656b32e7b4c75246027b726f425c6ef
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053010"
---
# <a name="how-to-create-a-data-service-using-an-adonet-entity-framework-data-source-wcf-data-services"></a>HOW TO：使用 ADO.NET Entity Framework 資料來源建立資料服務（WCF Data Services）

WCF Data Services 會將實體資料公開為數據服務。 當資料來源為關係資料庫時，NETEntity 架構會提供此實體資料。 本主題示範如何在以現有資料庫為基礎的 Visual Studio Web 應用程式中建立 Entity Framework 架構資料模型，並使用此資料模型建立新的資料服務。

Entity Framework 也提供命令列工具，可在 Visual Studio 專案以外產生 Entity Framework 模型。 如需詳細資訊，請參閱[如何：使用 Edmgen.exe 來產生模型和對應](../adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)檔。

## <a name="to-add-an-entity-framework-model-that-is-based-on-an-existing-database-to-an-existing-web-application"></a>若要將以現有資料庫為基礎的 Entity Framework 模型加入至現有的 Web 應用程式

1. 在 [**專案**] 功能表上，按一下 [**加入** > **新專案**]。

2. 在 [**範本**] 窗格中，按一下 [**資料**] 類別，然後選取 [ **ADO.NET 實體資料模型**]。

3. 輸入模型名稱，然後按一下 [**新增**]。

     Entity Data Model 精靈的第一個頁面便會出現。

4. 在 [**選擇模型內容**] 對話方塊中，選取 [**從資料庫產生**]。 然後按 [下一步]。

5. 按一下 [**新增連接**] 按鈕。

6. 在 [**連接屬性**] 對話方塊中，輸入您的伺服器名稱、選取驗證方法、輸入資料庫名稱，然後按一下 **[確定]** 。

     [**選擇您的資料連線**] 對話方塊會以您的資料庫連接設定進行更新。

7. 確定已核取 [**將 app.config 中的實體連接設定儲存為：** ] 核取方塊。 然後按 [下一步]。

8. 在 [**選擇您的資料庫物件**] 對話方塊中，選取您計畫要在資料服務中公開的所有資料庫物件。

    > [!NOTE]
    > 資料服務不會自動公開包含在資料模型中的物件， 必須由服務本身明確公開。 如需詳細資訊，請參閱設定[資料服務](configuring-the-data-service-wcf-data-services.md)。

9. 按一下 **[完成**] 以完成嚮導。

     這樣會根據特定資料庫建立預設資料模型。 Entity Framework 可讓您自訂資料模型。 如需詳細資訊，請參閱[實體資料模型工具](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738480(v=vs.100))工作。

## <a name="to-create-the-data-service-by-using-the-new-data-model"></a>若要使用新的資料模型建立資料服務

1. 在 Visual Studio 中開啟代表該資料模型的 .edmx 檔案。

2. 在 [**模型瀏覽器**] 中，以滑鼠右鍵按一下模型，再按一下 [**屬性**]，然後記下實體容器的名稱。

3. 在**方案總管**中，以滑鼠右鍵按一下 ASP.NET 專案的名稱，然後按一下 [**加入** > **新專案**]。

4. 在 [**加入新專案**] 對話方塊中，選取 [ **Web** ] 類別中的 [ **WCF 資料服務**] 範本。

   ![Visual Studio 2015 中的 WCF 資料服務專案範本](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > **WCF 資料服務**範本可在 Visual Studio 2015 中取得，但 Visual Studio 2017 則不提供。

5. 提供服務的名稱，然後按一下 **[確定]** 。

     Visual Studio 會針對新的服務建立 XML 標記和程式碼檔案。 根據預設，程式碼編輯器視窗隨即開啟。

6. 在資料服務的程式碼中，以繼承自 `/* TODO: put your data source class name here */` 類別且為資料模型實體容器 (您已在步驟 2 中記下該容器) 的型別，取代定義資料服務之類別定義中的 <xref:System.Data.Objects.ObjectContext> 註解。

7. 在資料服務的程式碼中，啟用已授權的用戶端以存取資料服務所公開的實體集。 如需詳細資訊，請參閱[建立資料服務](creating-the-data-service.md)。

8. 若要使用網頁瀏覽器測試 Northwind 資料服務，請依照[從網頁瀏覽器存取服務](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)主題中的指示進行。

## <a name="see-also"></a>另請參閱

- [定義 WCF Data Services](defining-wcf-data-services.md)
- [資料服務提供者](data-services-providers-wcf-data-services.md)
- [如何：使用反映提供者建立資料服務](create-a-data-service-using-rp-wcf-data-services.md)
- [如何：使用 LINQ to SQL 資料來源建立資料服務](create-a-data-service-using-linq-to-sql-wcf.md)
