---
title: 教學課程：裝載和執行基本的 Windows Communication Foundation 服務
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: ad9536b1f27ba3945bf76d0474de4825033a1e8b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197902"
---
# <a name="tutorial-host-and-run-a-basic-windows-communication-foundation-service"></a>教學課程：裝載和執行基本的 Windows Communication Foundation 服務

本教學課程說明建立基本的 Windows Communication Foundation (WCF) 應用程式所需的五個工作的第三個。 如需教學課程的概觀，請參閱[教學課程：開始使用 Windows Communication Foundation 應用程式](getting-started-tutorial.md)。

建立 WCF 應用程式的下一個工作是將 WCF 服務裝載於主控台應用程式。 WCF 服務公開一或多個*端點*，其中每一個都會公開一或多個服務作業。 服務端點會指定下列資訊： 
- 您可以在其中找到服務位址。
- 繫結，其中包含描述如何在用戶端必須與服務通訊的資訊。 
- 定義服務提供給其用戶端功能的合約。

在本教學課程中，您將了解如何：
> [!div class="checklist"]
> - 建立及設定 WCF 服務裝載的主控台應用程式專案。
> - 加入裝載 WCF 服務的程式碼。
> - 更新組態檔。
> - 啟動 WCF 服務，並確認它正在執行。

## <a name="create-and-configure-a-console-app-project-for-hosting-the-service"></a>建立及設定裝載服務的主控台應用程式專案

1. Visual Studio 中建立主控台應用程式專案： 
 
    1. 從**檔案**功能表上，選取**開放** > **專案/方案**並瀏覽至**GettingStarted**解決方案您先前建立 (*GettingStarted.sln*)。 選取 [開啟] 。

    2. 從**檢視**功能表上，選取**方案總管 中**。
    
    3. 在 [**方案總管] 中**視窗中，選取**GettingStarted**方案 （最上層節點），然後再選取**新增** > **新專案**快顯功能表中。 

    4. 在 [**加入新的專案**視窗中的，在左側，選取**Windows 桌面**] 類別下的**Visual C#** 或**Visual Basic**. 

    5. 選取 **主控台應用程式 (.NET Framework)** 範本，然後輸入*GettingStartedHost*如**名稱**。 選取 [確定]。

2. 加入參考**GettingStartedHost**專案加入**GettingStartedLib**專案： 

    1. 在 **方案總管 中**視窗中，選取**參考**下的資料夾**GettingStartedHost**專案，然後再選取**加入參考**快顯功能表中。 

    2. 在 [**加入參考**] 對話方塊底下**專案**在視窗的左側，選取**解決方案**。 
 
    3. 選取  **GettingStartedLib**在視窗中，然後再選取 中心 區段**確定**。 

       這個動作可定義中的型別**GettingStartedLib**專案能夠**GettingStartedHost**專案。

3. 加入參考**GettingStartedHost**專案加入<xref:System.ServiceModel>組件： 

    1. 在 **方案總管 中**視窗中，選取**參考**下的資料夾**GettingStartedHost**專案，然後再選取**加入參考**快顯功能表中。
    
    2. 在 [**加入參考**] 視窗底下**組件**在視窗的左側，選取**Framework**。 

    3. 選取  **System.ServiceModel**，然後選取**確定**。 
    
    4. 選取儲存方案**檔案** > **全部儲存**。

## <a name="add-code-to-host-the-service"></a>加入程式碼來裝載服務

若要裝載服務，您可以加入程式碼，以執行下列步驟： 
   1. 建立的基底位址的 URI。
   2. 建立裝載服務的類別執行個體。
   3. 建立服務端點。
   4. 啟用中繼資料交換。
   5. 開啟服務主機來接聽內送訊息。
  
程式碼進行下列變更：

1. 開啟**Program.cs**或是**Module1.vb**中的檔案**GettingStartedHost**專案，並以下列程式碼取代其程式碼：

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
    
    如需此程式碼的運作方式的資訊，請參閱[服務裝載程式步驟](#service-hosting-program-steps)。

2. 更新專案屬性：

   1. 在 **方案總管**視窗中，選取**GettingStartedHost**資料夾，然後再選取**屬性**從捷徑功能表。

   2. 在 [ **GettingStartedHost**屬性頁面上，選取**應用程式**] 索引標籤：

      - 針對C#專案中，選取**GettingStartedHost.Program**從**啟始物件**清單。

      - 針對 Visual Basic 專案中，選取**Service.Program**從**啟始物件**清單。

   3. 從**檔案**功能表上，選取**全部儲存**。

## <a name="verify-the-service-is-working"></a>確認服務正常運作

1. 建置方案，然後再執行**GettingStartedHost**主控台應用程式在 Visual Studio 內從。 

    服務必須以系統管理員權限執行。 當您執行時，系統管理員權限，以開啟 Visual Studio **GettingStartedHost**在 Visual Studio 中，應用程式執行系統管理員權限。 或者，您可以開啟新的命令提示字元，以系統管理員身分 (選取**更多** > **系統管理員身分執行**從快顯功能表) 並執行**GettingStartedHost.exe**其內。

2. 開啟網頁瀏覽器並瀏覽至服務的頁面在`http://localhost:8000/GettingStarted/CalculatorService`。
   
   > [!NOTE]
   > 此類服務需要在接聽的機器上的 HTTP 位址註冊適當的權限。 系統管理員帳戶具有此權限，但是非系統管理員帳戶則必須被授與 HTTP 命名空間的權限。 如需如何設定命名空間保留的詳細資訊，請參閱[設定 HTTP 和 HTTPS](feature-details/configuring-http-and-https.md)。 

## <a name="service-hosting-program-steps"></a>服務裝載程式步驟

您新增至主機服務的描述，如下所示的程式碼中的步驟：

- **步驟 1**:建立的執行個體`Uri`類別，以維持服務的基底位址。 包含基底位址的 URL 包含選擇性 URI 識別服務。 基底地址的格式如下： `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>`。 HTTP 傳輸、 localhost、 連接埠 8000 和 URI 區段 GettingStarted，則會使用計算機服務的基底位址。

- **步驟 2**:建立的執行個體<xref:System.ServiceModel.ServiceHost>類別，用來裝載服務。 建構函式接受兩個參數： 實作服務合約與基底位址的服務類別的型別。

- **步驟 3**:建立 <xref:System.ServiceModel.Description.ServiceEndpoint> 執行個體。 服務端點是由位址、繫結和服務合約所組成。 <xref:System.ServiceModel.Description.ServiceEndpoint>建構函式組成服務合約介面型別、 繫結和位址。 服務合約是您在服務類型中所定義和實作的 `ICalculator`。 此範例中的繫結是<xref:System.ServiceModel.WSHttpBinding>，這是內建繫結並連接到端點符合 WS-* 規格。 如需有關 WCF 繫結的詳細資訊，請參閱 < [WCF 繫結概觀](bindings-overview.md)。 您附加至基底位址以識別端點的位址。 程式碼會指定位址 CalculatorService 以及做為端點的完整的位址`http://localhost:8000/GettingStarted/CalculatorService`。

    > [!IMPORTANT]
    > .NET Framework 第 4 版和更新版本，新增服務端點是選擇性的。 如需這些版本中，如果您未新增您的程式碼或組態中，WCF 會加入一個預設端點，每個組合的基底位址和服務所實作的合約。 如需有關預設端點的詳細資訊，請參閱 <<c0> [ 指定端點位址](specifying-an-endpoint-address.md)。 如需有關預設端點、 繫結和行為的詳細資訊，請參閱 <<c0> [ 經過簡化的組態](simplified-configuration.md)並[WCF 服務的簡化組態](samples/simplified-configuration-for-wcf-services.md)。

- **步驟 4**:啟用中繼資料交換。 用戶端會使用中繼資料交換來產生 proxy 呼叫服務作業。 若要啟用中繼資料交換，建立<xref:System.ServiceModel.Description.ServiceMetadataBehavior>執行個體、 將其<xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled>屬性設`true`，並新增`ServiceMetadataBehavior`物件<xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A>集合<xref:System.ServiceModel.ServiceHost>執行個體。

- **步驟 5**:開啟<xref:System.ServiceModel.ServiceHost>來接聽內送訊息。 應用程式會等候您按下**Enter**。 應用程式具現化之後<xref:System.ServiceModel.ServiceHost>，它會執行 try/catch 區塊。 如需安全攔截擲回例外狀況的詳細資訊<xref:System.ServiceModel.ServiceHost>，請參閱 <<c2> [ 使用關閉和中止發行 WCF 用戶端資源](samples/use-close-abort-release-wcf-client-resources.md)。

> [!IMPORTANT]
> 當您新增的 WCF 服務程式庫時，Visual Studio 裝載它，如果您啟動服務主機來偵錯。 若要避免衝突，您可以防止 Visual Studio 裝載 WCF 服務程式庫。 
> 1. 選取  **GettingStartedLib**專案中**方案總管**，然後選擇 **屬性**從捷徑功能表。
> 2. 選取  **WCF 選項**並取消核取**啟動 WCF 服務主機時相同的方案中的另一個專案進行偵錯**。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您將了解如何：
> [!div class="checklist"]
> - 建立及設定 WCF 服務裝載的主控台應用程式專案。
> - 加入裝載 WCF 服務的程式碼。
> - 更新組態檔。
> - 啟動 WCF 服務，並確認它正在執行。

請前進到下一個教學課程，以了解如何建立 WCF 用戶端。

> [!div class="nextstepaction"]
> [教學課程：建立 WCF 用戶端](how-to-create-a-wcf-client.md)
