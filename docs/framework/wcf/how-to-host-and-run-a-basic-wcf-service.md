---
title: 教程：託管並運行基本的 Windows 通信基礎服務
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: 30eb86987b83427b94c6fff22755cde3d73dd9f0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184076"
---
# <a name="tutorial-host-and-run-a-basic-windows-communication-foundation-service"></a>教程：託管並運行基本的 Windows 通信基礎服務

本教程介紹創建基本 Windows 通信基礎 （WCF） 應用程式所需的五個任務中的第三個。 有關教程的概述，請參閱[教程：開始使用 Windows 通信基礎應用程式](getting-started-tutorial.md)。

創建 WCF 應用程式的下一個任務是在主控台應用程式中託管 WCF 服務。 WCF 服務公開一個或多個終結點，每個*終結點*公開一個或多個服務操作。 服務終結點指定以下資訊：

- 您可以在其中找到服務的位址。
- 包含描述用戶端必須如何與服務通信的資訊的綁定。
- 定義服務為其用戶端提供的功能的協定。

在本教學課程中，您會了解如何：
> [!div class="checklist"]
>
> - 創建和配置用於託管 WCF 服務的主控台應用專案。
> - 添加代碼以承載 WCF 服務。
> - 更新設定檔。
> - 啟動 WCF 服務並驗證其正在運行。

## <a name="create-and-configure-a-console-app-project-for-hosting-the-service"></a>創建和配置託管服務的主控台應用專案

1. 在視覺化工作室中創建主控台應用專案：

    1. 在 **"檔"** 功能表中，選擇 **"打開** > **專案/解決方案**"並流覽到您以前創建的**入門**解決方案 （*獲取入門.sln*）。 選取 [開啟]****。

    2. 在 **"查看"** 功能表中，選擇 **"解決方案資源管理器**"。

    3. 在 **"解決方案資源管理器"** 視窗中，選擇 **"入門"** 解決方案（頂部節點），然後從快顯功能表中選擇 **"添加新** > **專案**"。

    4. 在左側的 **"添加新專案**"視窗中，在 **"可視 C#"** 或"**可視基本**"下選擇**Windows 桌面**類別。

    5. 選擇**主控台應用 （.NET 框架）** 範本，然後輸入"*入門主機*"**的名稱**。 選取 [確定]****。

2. 在**入門主機**專案中向**入門專案**增加參考：

    1. 在 **"解決方案資源管理器"** 視窗中，選擇 **"入門主機**"專案下的 **"參考"** 資料夾，然後從快顯功能表中選擇 **"增加參考**"。

    2. 在"**添加參考**"對話方塊中，在視窗左側**的專案**下，選擇 **"解決方案**"。

    3. 在視窗的中心部分選擇 **"獲取開始Lib"，** 然後選擇 **"確定**"。

       此操作使**入門專案**中定義的類型可供**入門主項目目使用**。

3. 在**入門主機**專案中向<xref:System.ServiceModel>程式集增加參考：

    1. 在 **"解決方案資源管理器"** 視窗中，選擇 **"入門主機**"專案下的 **"參考"** 資料夾，然後從快顯功能表中選擇 **"增加參考**"。

    2. 在"**增加參考**"視窗中，在視窗左側的 **"程式集**"下，選擇 **"框架**"。

    3. 選擇 **"系統.服務模式"，** 然後選擇 **"確定**"。

    4. 通過選擇 **"全部保存檔** > **"保存**解決方案。

## <a name="add-code-to-host-the-service"></a>添加代碼以承載服務

要託管服務，請添加代碼以執行以下步驟：

1. 為基本位址創建 URI。
2. 創建用於託管服務的類實例。
3. 創建服務終結點。
4. 啟用中繼資料交換。
5. 打開服務主機以偵聽傳入消息。
  
對程式碼進行下列變更：

1. 打開**入門霍斯特**專案中**的Program.cs**或**Module1.vb**檔，並將其代碼替換為以下代碼：

    ```csharp
    using System;
    using System.ServiceModel;
    using System.ServiceModel.Description;
    using GettingStartedLib;

    namespace GettingStartedHost
    {
        class Program
        {
            static void Main(string[] args)
            {
                // Step 1: Create a URI to serve as the base address.
                Uri baseAddress = new Uri("http://localhost:8000/GettingStarted/");

                // Step 2: Create a ServiceHost instance.
                ServiceHost selfHost = new ServiceHost(typeof(CalculatorService), baseAddress);

                try
                {
                    // Step 3: Add a service endpoint.
                    selfHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), "CalculatorService");

                    // Step 4: Enable metadata exchange.
                    ServiceMetadataBehavior smb = new ServiceMetadataBehavior();
                    smb.HttpGetEnabled = true;
                    selfHost.Description.Behaviors.Add(smb)    ;

                    // Step 5: Start the service.
                    selfHost.Open();
                    Console.WriteLine("The service is ready.");

                    // Close the ServiceHost to stop the service.
                    Console.WriteLine("Press <Enter> to terminate the service.");
                    Console.WriteLine();
                    Console.ReadLine();
                    selfHost.Close();
                }
                catch (CommunicationException ce)
                {
                    Console.WriteLine("An exception occurred: {0}", ce.Message);
                    selfHost.Abort();
                }
            }
        }
    }
    ```

    ```vb
    Imports System.ServiceModel
    Imports System.ServiceModel.Description
    Imports GettingStartedLib.GettingStartedLib

    Module Service

        Class Program
            Shared Sub Main()
                ' Step 1: Create a URI to serve as the base address.
                Dim baseAddress As New Uri("http://localhost:8000/GettingStarted/")

                ' Step 2: Create a ServiceHost instance.
                Dim selfHost As New ServiceHost(GetType(CalculatorService), baseAddress)
               Try

                    ' Step 3: Add a service endpoint.
                    selfHost.AddServiceEndpoint( _
                        GetType(ICalculator), _
                        New WSHttpBinding(), _
                        "CalculatorService")

                    ' Step 4: Enable metadata exchange.
                    Dim smb As New ServiceMetadataBehavior()
                    smb.HttpGetEnabled = True
                    selfHost.Description.Behaviors.Add(smb)

                    ' Step 5: Start the service.
                    selfHost.Open()
                    Console.WriteLine("The service is ready.")

                    ' Close the ServiceHost to stop the service.
                    Console.WriteLine("Press <Enter> to terminate the service.")
                    Console.WriteLine()
                    Console.ReadLine()
                    selfHost.Close()

                Catch ce As CommunicationException
                    Console.WriteLine("An exception occurred: {0}", ce.Message)
                    selfHost.Abort()
                End Try
            End Sub
        End Class

    End Module
    ```

    有關此代碼的工作原理的資訊，請參閱[服務託管程式步驟](#service-hosting-program-steps)。

2. 更新專案屬性：

   1. 在 **"解決方案資源管理器"** 視窗中，選擇 **"入門主機"** 資料夾，然後從快顯功能表中選擇 **"屬性**"。

   2. 在 **"入門主機"** 屬性頁上，選擇"**應用程式**"選項卡：

      - 對於 C# 專案，從**啟始物件**清單中選擇 **"入門主機.程式"。**

      - 對於視覺化基本專案，從**啟始物件**清單中選擇 **"服務.程式**"。

   3. 在 **"檔"** 功能表中，選擇 **"全部保存**"。

## <a name="verify-the-service-is-working"></a>驗證服務是否正常工作

1. 構建解決方案，然後從 Visual Studio 內部運行**入門主機**主控台應用程式。

    服務必須具有管理員許可權運行。 由於您使用管理員許可權打開了 Visual Studio，因此在視覺化工作室中運行 **"入門主機"** 時，應用程式也具有管理員許可權運行。 作為替代方法，您可以以管理員身份打開新的命令提示符（從快顯功能表中選擇 **"以管理員身份運行"），** > **Run as administrator**並在其中運行 **"獲取啟動Host.exe"。**

2. 打開 Web 瀏覽器，然後流覽到 服務頁面`http://localhost:8000/GettingStarted/CalculatorService`。

   > [!NOTE]
   > 此類服務需要適當的許可權才能在電腦上註冊 HTTP 位址以進行偵聽。 系統管理員帳戶具有此權限，但是非系統管理員帳戶則必須被授與 HTTP 命名空間的權限。 如需如何設定命名空間保留的詳細資訊，請參閱[設定 HTTP 和 HTTPS](feature-details/configuring-http-and-https.md)。

## <a name="service-hosting-program-steps"></a>服務託管程式步驟

添加到託管服務的代碼中的步驟描述如下：

- **步驟 1：** 創建類的`Uri`實例以保存服務的基本位址。 包含基本位址的 URL 具有標識服務的可選 URI。 基本位址的格式如下： `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>`。 計算機服務的基本位址使用 HTTP 傳輸、本地主機、埠 8000 和 URI 段"入門"。

- **步驟 2：** 創建類的<xref:System.ServiceModel.ServiceHost>實例，用於託管服務。 建構函式採用兩個參數：實現服務協定的類類型和服務的基本位址。

- **步驟 3**：<xref:System.ServiceModel.Description.ServiceEndpoint>創建實例。 服務端點是由位址、繫結和服務合約所組成。 <xref:System.ServiceModel.Description.ServiceEndpoint>建構函式由服務協定介面類別型、綁定和位址組成。 服務合約是您在服務類型中所定義和實作的 `ICalculator`。 此示例的綁定是<xref:System.ServiceModel.WSHttpBinding>，這是一個內置綁定，並連接到符合 WS-* 規範的終結點。 有關 WCF 綁定的詳細資訊，請參閱[WCF 綁定概述](bindings-overview.md)。 將位址追加到基本位址以標識終結點。 代碼將位址指定為計算機服務，終結點的完全限定位址為`http://localhost:8000/GettingStarted/CalculatorService`。

    > [!IMPORTANT]
    > 對於 .NET 框架版本 4 及更高版本，添加服務終結點是可選的。 對於這些版本，如果不添加代碼或配置，WCF 會為服務實現的每個基本位址和協定組合添加一個預設終結點。 有關預設終結點的詳細資訊，請參閱[指定終結點位址](specifying-an-endpoint-address.md)。 有關預設終結點、綁定和行為的詳細資訊，請參閱[WCF 服務的](samples/simplified-configuration-for-wcf-services.md)[簡化配置](simplified-configuration.md)和簡化配置。

- **步驟 4**：啟用中繼資料交換。 用戶端使用中繼資料交換生成用於調用服務操作的代理。 要啟用中繼資料交換，請創建<xref:System.ServiceModel.Description.ServiceMetadataBehavior>實例，將其<xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled>屬性設置為`true`，並將`ServiceMetadataBehavior`物件添加到<xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A><xref:System.ServiceModel.ServiceHost>實例的集合中。

- **步驟 5** <xref:System.ServiceModel.ServiceHost> ： 打開以偵聽傳入的消息。 應用程式等待您按**Enter**。 應用程式具現化後<xref:System.ServiceModel.ServiceHost>，它執行一個 try/catch 塊。 有關安全捕獲引發<xref:System.ServiceModel.ServiceHost>異常的詳細資訊，請參閱[使用關閉和中止來釋放 WCF 用戶端資源](samples/use-close-abort-release-wcf-client-resources.md)。

> [!IMPORTANT]
> 添加 WCF 服務庫時，如果通過啟動服務主機來調試它，Visual Studio 會為您託管它。 為了避免衝突，您可以阻止 Visual Studio 託管 WCF 服務庫。
>
> 1. 在**解決方案資源管理器**中選擇**入門專案**，然後從快顯功能表中選擇 **"屬性**"。
> 2. 在同**一解決方案中調試另一個專案時**，選擇**WCF 選項**並取消選中"啟動 WCF 服務主機"。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您已了解如何：
> [!div class="checklist"]
>
> - 創建和配置用於託管 WCF 服務的主控台應用專案。
> - 添加代碼以承載 WCF 服務。
> - 更新設定檔。
> - 啟動 WCF 服務並驗證其正在運行。

進入下一個教程，瞭解如何創建 WCF 用戶端。

> [!div class="nextstepaction"]
> [教程：創建 WCF 用戶端](how-to-create-a-wcf-client.md)
