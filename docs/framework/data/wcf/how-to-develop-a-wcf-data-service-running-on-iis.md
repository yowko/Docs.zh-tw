---
title: HOW TO：開發在 IIS 上執行的 WCF 資料服務
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- WCF Data Services, hosting
ms.assetid: f6f768c5-4989-49e3-a36f-896ab4ded86e
ms.openlocfilehash: 78e8c3cacd89f88cbfa062cb30e5b3474c2614ca
ms.sourcegitcommit: 680a741667cf6859de71586a0caf6be14f4f7793
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59517816"
---
# <a name="how-to-develop-a-wcf-data-service-running-on-iis"></a>HOW TO：開發在 IIS 上執行的 WCF 資料服務

本主題說明如何使用 WCF Data Services 來建立資料服務由執行網際網路資訊服務 (IIS) 上的 ASP.NET Web 應用程式所裝載的 Northwind 範例資料庫為基礎。 如需如何建立 ASP.NET 程式開發伺服器執行的 ASP.NET Web 應用程式相同的 Northwind 資料服務的範例，請參閱 < [WCF Data Services 快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)。

> [!NOTE]
> 若要建立 Northwind 資料服務，您必須在本機電腦上安裝 Northwind 範例資料庫。 若要下載此範例資料庫，請參閱下載頁面： [SQL Server 的範例資料庫](https://go.microsoft.com/fwlink/?linkid=24758)。

 本主題示範如何使用 Entity Framework 提供者建立資料服務。 有其他資料服務提供者可以使用。 如需詳細資訊，請參閱 <<c0> [ 資料服務提供者](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)。

 當您建立服務之後，您必須明確提供資料服務資源的存取權。 如需詳細資訊，請參閱[如何：啟用資料服務的存取權](../../../../docs/framework/data/wcf/how-to-enable-access-to-the-data-service-wcf-data-services.md)。

## <a name="create-the-aspnet-web-application-that-runs-on-iis"></a>建立在 IIS 執行的 ASP.NET web 應用程式

1. 在 Visual Studio 中，在**檔案**功能表上，選取**新增** > **專案**。

2. 在 **新的專案**對話方塊中，選取**已安裝**> [**Visual C#** 或**Visual Basic**] > **Web**類別目錄。

3. 選取  **ASP.NET Web 應用程式**範本。

1. 輸入`NorthwindService`做為專案的名稱。

5. 按一下 [確定] 。

6. 在 **專案**功能表上，選取**NorthwindService 屬性**。

7. 選取  **Web**索引標籤，然後按**使用本機 IIS Web 伺服器**。

8. 按一下 **建立虛擬目錄**，然後按一下**確定**。

9. 在具有系統管理員權限的命令提示字元中，執行下列其中一個命令 (視作業系統而定)：

    -   32 位元系統：

        ```console
        "%windir%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

    -   64 位元系統：

        ```console
        "%windir%\Microsoft.NET\Framework64\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

     這樣會確定 Windows Communication Foundation (WCF) 已在電腦上登錄。

10. 在具有系統管理員權限的命令提示字元中，執行下列其中一個命令 (視作業系統而定)：

    -   32 位元系統：

        ```console
        "%windir%\Microsoft.NET\Framework\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

    -   64 位元系統：

        ```console
        "%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

     這樣可確保 IIS 會在電腦上安裝 WCF 之後正確執行。 此外，您可能也必須重新啟動 IIS。

11. 當 ASP.NET 應用程式在 IIS7 上執行時，您也必須執行下列步驟：

    1. 開啟 IIS 管理員，並瀏覽至底下的 PhotoService 應用程式**Default Web Site**。

    2. 在 **功能檢視**，按兩下**驗證**。

    3. 在 **驗證**頁面上，選取**匿名驗證**。

    4. 在 **動作**窗格中，按一下**編輯**來設定安全性主體匿名使用者會連線至站台。

    5. 在 **編輯匿名驗證認證**對話方塊中，選取**應用程式集區識別**。

    > [!IMPORTANT]
    > 當您使用 Network Service 帳戶時，就會將與該帳戶相關聯的所有內部網路存取權授與匿名使用者。

12. 使用 SQL Server Management Studio、sqlcmd.exe 公用程式或 Visual Studio 中的 Transact-SQL 編輯器，針對已附加 Northwind 資料庫的 SQL Server 執行個體執行下列 Transact-SQL 命令：

    ```sql
    CREATE LOGIN [NT AUTHORITY\NETWORK SERVICE] FROM WINDOWS;
    GO
    ```

    這樣會在用來執行 IIS 之 Windows 帳戶的 SQL Server 執行個體中建立登入。 如此可讓 IIS 連接至 SQL Server 執行個體。

13. 當附加 Northwind 資料庫之後，執行下列 Transact-SQL 命令：

    ```sql
    USE Northwind
    GO
    CREATE USER [NT AUTHORITY\NETWORK SERVICE]
    FOR LOGIN [NT AUTHORITY\NETWORK SERVICE] WITH DEFAULT_SCHEMA=[dbo];
    GO
    ALTER LOGIN [NT AUTHORITY\NETWORK SERVICE]
    WITH DEFAULT_DATABASE=[Northwind];
    GO
    EXEC sp_addrolemember 'db_datareader', 'NT AUTHORITY\NETWORK SERVICE'
    GO
    EXEC sp_addrolemember 'db_datawriter', 'NT AUTHORITY\NETWORK SERVICE'
    GO
    ```

    這樣會授與新登入的權限，此權限可讓 IIS 讀取 Northwind 資料庫中的資料並將資料寫入其中。

## <a name="define-the-data-model"></a>定義資料模型

1. 在 [**方案總管] 中**，以滑鼠右鍵按一下 ASP.NET 專案中，名稱，然後按一下**新增** > **新項目**。

2. 在 **加入新項目**對話方塊中，選取**ADO.NET 實體資料模型**。

3. 針對資料模型的名稱，輸入`Northwind.edmx`。

4. 在 實體資料模型精靈 中，選取**從資料庫產生**，然後按一下**下一步**。

5. 連接到資料庫的資料模型，執行下列步驟中，其中，然後按一下**下一步**:

    -   如果您沒有已設定的資料庫連線，請按一下**新的連接**並建立新的連接。 如需詳細資訊，請參閱[如何：建立連接至 SQL Server 資料庫](https://go.microsoft.com/fwlink/?LinkId=123631)。 此 SQL Server 執行個體必須已附加 Northwind 範例資料庫。

         \-或-

    -   如果您擁有已經設定為連接至 Northwind 資料庫的資料庫連接，請從連接清單中選取該連接。

6. 在精靈的最後一頁上，選取資料庫中所有資料表的核取方塊，並且清除檢視表和預存程序 (Stored Procedure) 的核取方塊。

7. 按一下 **完成**即可關閉精靈。

## <a name="create-the-data-service"></a>建立資料服務

1. 在 **方案總管**，以滑鼠右鍵按一下您的 ASP.NET 專案的名稱，然後按一下**新增** > **新項目**。

2. 在 **加入新項目**對話方塊中，選取**WCF 資料服務**。

   ![Visual Studio 2015 中的 WCF 資料服務項目範本](media/wcf-data-service-item-template.png)

   > [!NOTE]
   > **WCF 資料服務**範本位於 Visual Studio 2015，但不是能在 Visual Studio 2017。

3. 針對服務的名稱，輸入`Northwind`。

     Visual Studio 會針對新的服務建立 XML 標記和程式碼檔案。 根據預設，程式碼編輯器視窗隨即開啟。 在 [**方案總管] 中**，服務都有名稱、 Northwind 和延伸模組。 svc.cs 或.svc.vb。

4. 在資料服務的程式碼裡，於定義資料服務和型別的類別定義中，取代註解 `/* TODO: put your data source class name here */`，該型別是資料模型的實體容器，在這個案例中是 `NorthwindEntities`。 類別定義看起來應如下列：

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

## <a name="see-also"></a>另請參閱

- [將資料當作服務公開](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md)
