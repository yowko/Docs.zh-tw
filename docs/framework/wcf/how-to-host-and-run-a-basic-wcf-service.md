---
title: 教學課程：裝載和執行基本 Windows Communication Foundation 服務
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: 984c5e73a8efc4e9c2d487485267868ffa2f60f3
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928717"
---
# <a name="tutorial-host-and-run-a-basic-windows-communication-foundation-service"></a>教學課程：裝載和執行基本 Windows Communication Foundation 服務

本教學課程說明建立基本 Windows Communication Foundation （WCF）應用程式所需的五個工作中的第三個。 如需教學課程的總覽，請[參閱教學課程：Windows Communication Foundation 應用程式](getting-started-tutorial.md)入門。

建立 WCF 應用程式的下一個工作是在主控台應用程式中裝載 WCF 服務。 WCF 服務會公開一或多個端點，其中每個*端點*都會公開一個或多個服務作業。 服務端點會指定下列資訊：

- 您可以在其中找到服務的位址。
- 系結，其中包含描述用戶端必須如何與服務通訊的資訊。 
- 定義服務提供給其用戶端之功能的合約。

在本教學課程中，您將了解如何：
> [!div class="checklist"]
>
> - 建立和設定主控台應用程式專案來裝載 WCF 服務。
> - 加入程式碼來裝載 WCF 服務。
> - 更新設定檔。
> - 啟動 WCF 服務，並確認它正在執行。

## <a name="create-and-configure-a-console-app-project-for-hosting-the-service"></a>建立和設定主控台應用程式專案以裝載服務

1. 在 Visual Studio 中建立主控台應用程式專案： 
 
    1. 從 [**檔案] 功能表中，選取 [** **開啟** > **專案/方案**]，然後流覽至您先前建立的**GettingStarted**方案（*GettingStarted*）。 選取 [開啟]。

    2. 從 [ **View** ] 功能表中，選取 [**方案總管**]。
    
    3. 在 [**方案總管**] 視窗中，選取 [ **GettingStarted** ] 解決方案（最上層節點），然後從快捷方式功能表選取 [**加入** > **新專案**]。 

    4. 在左側的 [**加入新專案**] 視窗中，選取 [  **C#視覺效果**] 或 [ **Visual Basic**] 底下的 [ **Windows 桌面**] 類別。 

    5. 選取 [**主控台應用程式（.NET Framework）** ] 範本，然後在 [**名稱**] 中輸入*GettingStartedHost* 。 選取 [確定]。

2. 將**GettingStartedHost**專案中的參考新增至**GettingStartedLib**專案： 

    1. 在 [**方案總管**] 視窗中，選取 [ **GettingStartedHost** ] 專案底下的 [**參考**] 資料夾，然後從快捷方式功能表選取 [**加入參考**]。 

    2. 在 [**加入參考**] 對話方塊中，于視窗左側的 [**專案**] 底下，選取 [**方案**]。 
 
    3. 在視窗的中間區段中選取 [ **GettingStartedLib** ]，然後選取 **[確定]** 。 

       此動作會讓**GettingStartedLib**專案中定義的類型可供**GettingStartedHost**專案使用。

3. 將**GettingStartedHost**專案中的參考新增至<xref:System.ServiceModel>元件： 

    1. 在 [**方案總管**] 視窗中，選取 [ **GettingStartedHost** ] 專案底下的 [**參考**] 資料夾，然後從快捷方式功能表選取 [**加入參考**]。
    
    2. 在 [**加入參考**] 視窗中，于視窗左側的 [**元件**] 底下，選取 [**架構**]。 

    3. 選取 [ **System.servicemodel**]，然後選取 **[確定]** 。 
    
    4. 選取 > [檔案] [**全部儲存**]**以儲存方案**。

## <a name="add-code-to-host-the-service"></a>新增程式碼以裝載服務

若要裝載服務，您可以新增程式碼來執行下列步驟： 

1. 建立基底位址的 URI。
2. 建立用來裝載服務的類別實例。
3. 建立服務端點。
4. 啟用中繼資料交換。
5. 開啟服務主機以接聽傳入訊息。
  
對程式碼進行下列變更:

1. 開啟**GettingStartedHost**專案中的**Program.cs**或**Module1**檔案，並以下列程式碼取代其程式碼：

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
    
    如需有關此程式碼如何運作的詳細資訊，請參閱[服務裝載程式步驟](#service-hosting-program-steps)。

2. 更新專案屬性：

   1. 在 [**方案總管**] 視窗中，選取 [ **GettingStartedHost** ] 資料夾，然後從快捷方式功能表選取 [**屬性**]。

   2. 在 [ **GettingStartedHost**屬性] 頁面上，選取 [**應用程式**] 索引標籤：

      - 針對C# [專案]，從 [**啟始物件**] 清單中選取 [ **GettingStartedHost** ]。

      - 針對 Visual Basic 專案，從 [**啟始物件**] 清單中選取 [**服務**]。

   3. 從 [**檔案**] 功能表中，選取 [**全部儲存**]。

## <a name="verify-the-service-is-working"></a>確認服務正在運作

1. 建立解決方案，然後從 Visual Studio 內執行**GettingStartedHost**主控台應用程式。 

    服務必須以系統管理員許可權執行。 因為您以系統管理員許可權開啟 Visual Studio，所以當您在 Visual Studio 中執行**GettingStartedHost**時，應用程式也會以系統管理員許可權執行。 或者，您可以系統管理員身分開啟新的命令提示字元（從快捷方式功能表選取 [**更多** > 以**系統管理員身分執行**]），然後在其中執行**GettingStartedHost** 。

2. 開啟網頁瀏覽器，並流覽至位於`http://localhost:8000/GettingStarted/CalculatorService`的服務頁面。
   
   > [!NOTE]
   > 這一類服務需要適當的許可權，才能在電腦上註冊 HTTP 位址以供接聽。 系統管理員帳戶具有此權限，但是非系統管理員帳戶則必須被授與 HTTP 命名空間的權限。 如需如何設定命名空間保留的詳細資訊，請參閱[設定 HTTP 和 HTTPS](feature-details/configuring-http-and-https.md)。 

## <a name="service-hosting-program-steps"></a>服務裝載程式步驟

您新增來裝載服務之程式碼中的步驟如下所述：

- **步驟 1**：建立`Uri`類別的實例，以保存服務的基底位址。 包含基底位址的 URL 具有可識別服務的選擇性 URI。 基底位址的格式如下： `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>`。 計算機服務的基底位址會使用 HTTP 傳輸、localhost、埠8000和 URI 區段 GettingStarted。

- **步驟 2**：建立<xref:System.ServiceModel.ServiceHost>類別的實例，以用來裝載服務。 此函式會採用兩個參數：實作為服務合約之類別的型別，以及服務的基底位址。

- **步驟 3**：建立 <xref:System.ServiceModel.Description.ServiceEndpoint> 執行個體。 服務端點是由位址、繫結和服務合約所組成。 此<xref:System.ServiceModel.Description.ServiceEndpoint>函式是由服務合約介面型別、系結和位址所組成。 服務合約是您在服務類型中所定義和實作的 `ICalculator`。 這個範例的系結是<xref:System.ServiceModel.WSHttpBinding>，它是內建的系結，並會連接到符合 WS-* 規格的端點。 如需 WCF 系結的詳細資訊，請參閱 Wcf 系結[總覽](bindings-overview.md)。 您會將位址附加至基底位址，以識別端點。 此程式碼會將位址指定為 CalculatorService，並將端點的完整位址`http://localhost:8000/GettingStarted/CalculatorService`指定為。

    > [!IMPORTANT]
    > 針對 .NET Framework 第4版和更新版本，新增服務端點是選擇性的。 在這些版本中，如果您未新增程式碼或設定，WCF 會為服務所執行之每個基底位址和合約的組合加入一個預設端點。 如需預設端點的詳細資訊，請參閱[指定端點位址](specifying-an-endpoint-address.md)。 如需預設端點、系結和行為的詳細資訊，請參閱[簡化](simplified-configuration.md)的設定和[WCF 服務的簡化](samples/simplified-configuration-for-wcf-services.md)設定。

- **步驟 4**：啟用中繼資料交換。 用戶端會使用中繼資料交換來產生 proxy，以呼叫服務作業。 若要啟用中繼資料交換， <xref:System.ServiceModel.Description.ServiceMetadataBehavior>請建立實例， <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled>將其`true`屬性設定`ServiceMetadataBehavior`為，並<xref:System.ServiceModel.ServiceHost>將物件<xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A>加入至實例的集合。

- **步驟 5**：開啟<xref:System.ServiceModel.ServiceHost>以接聽傳入訊息。 應用程式會等候您按下**enter**鍵。 在應用程式具<xref:System.ServiceModel.ServiceHost>現化之後，它會執行 try/catch 區塊。 如需安全攔截所<xref:System.ServiceModel.ServiceHost>擲回之例外狀況的詳細資訊，請參閱[使用 Close 和 Abort 釋放 WCF 用戶端資源](samples/use-close-abort-release-wcf-client-resources.md)。

> [!IMPORTANT]
> 當您新增 WCF 服務程式庫時，如果您藉由啟動服務主機來進行偵錯工具，Visual Studio 會為您裝載它。 若要避免衝突，您可以防止 Visual Studio 裝載 WCF 服務程式庫。 
>
> 1. 在**方案總管**中選取 [ **GettingStartedLib** ] 專案，然後從快捷方式功能表中選擇 [**屬性**]。
> 2. 選取 [ **WCF 選項**]，然後取消核取**相同方案中的另一個專案時，啟動 WCF 服務主機**。

## <a name="next-steps"></a>後續步驟

在本教學課程中，您將了解如何：
> [!div class="checklist"]
>
> - 建立和設定主控台應用程式專案來裝載 WCF 服務。
> - 加入程式碼來裝載 WCF 服務。
> - 更新設定檔。
> - 啟動 WCF 服務，並確認它正在執行。

請前進到下一個教學課程，以瞭解如何建立 WCF 用戶端。

> [!div class="nextstepaction"]
> [教學課程：建立 WCF 用戶端](how-to-create-a-wcf-client.md)
