---
title: 如何裝載和執行基本的 Windows Communication Foundation 服務
ms.date: 09/14/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: 3a029ef23ba3e9a0dd62e410739fa8734acc202a
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55277767"
---
# <a name="how-to-host-and-run-a-basic-windows-communication-foundation-service"></a>如何裝載和執行基本的 Windows Communication Foundation 服務

這是建立 Windows Communication Foundation (WCF) 應用程式所需之六個工作中的第三個工作。 如需這六個工作的概觀，請參閱[使用者入門教學課程](getting-started-tutorial.md)主題。

本主題描述如何在主控台應用程式中裝載 Windows Communication Foundation (WCF) 服務。 這個程序包含下列步驟：

- 建立主控台應用程式專案以裝載服務。

- 建立服務的服務主機。

- 啟用中繼資料交換。

- 開啟服務主機。

這個程序之後的範例會列出這項工作所會撰寫的完整程式碼清單。

## <a name="create-a-new-console-application-to-host-the-service"></a>建立新的主控台應用程式來裝載服務

1. Visual Studio 中建立新的主控台應用程式專案，開始使用的方案上按一下滑鼠右鍵，然後選取**新增** > **新專案**。 在 **加入新的專案** 對話方塊的左側，選取**Windows 桌面** 類別下的**Visual C#** 或**Visual Basic**。 選取 **主控台應用程式 (.NET Framework)** 範本，然後再將專案命名為**GettingStartedHost**。

2. 將 GettingStartedLib 專案的參考加入至 GettingStartedHost 專案。 以滑鼠右鍵按一下**參考**的 GettingStartedHost 專案底下的資料夾**方案總管**，然後選取**加入參考**。 在 [**加入參考**對話方塊中，選取**解決方案**左手邊的對話方塊中，選取 GettingStartedLib] 對話方塊中，[中心] 部分中，然後選擇**新增**。 這樣 GettingStartedHost 專案就可以使用 GettingStartedLib 中所定義的型別。

3. 將 System.ServiceModel 的參考加入至 GettingStartedHost 專案。 以滑鼠右鍵按一下**參考**的 GettingStartedHost 專案底下的資料夾**方案總管**，然後選取**加入參考**。 在 **加入參考**對話方塊中，選取**Framework**在對話方塊左側**組件**。 尋找並選取**System.ServiceModel**，然後選擇**確定**。 選取儲存方案**檔案** > **全部儲存**。

## <a name="host-the-service"></a>裝載服務

開啟 Program.cs 或 Module.vb 檔案，並輸入下列程式碼：

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
            // Step 1 Create a URI to serve as the base address.
            Uri baseAddress = new Uri("http://localhost:8000/GettingStarted/");

            // Step 2 Create a ServiceHost instance
            ServiceHost selfHost = new ServiceHost(typeof(CalculatorService), baseAddress);

            try
            {
                // Step 3 Add a service endpoint.
                selfHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), "CalculatorService");

                // Step 4 Enable metadata exchange.
                ServiceMetadataBehavior smb = new ServiceMetadataBehavior();
                smb.HttpGetEnabled = true;
                selfHost.Description.Behaviors.Add(smb);

                // Step 5 Start the service.
                selfHost.Open();
                Console.WriteLine("The service is ready.");
                Console.WriteLine("Press <ENTER> to terminate service.");
                Console.WriteLine();
                Console.ReadLine();

                // Close the ServiceHostBase to shutdown the service.
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
Imports GettingStartedLibVB.GettingStartedLib

Module Service

    Class Program
        Shared Sub Main()
            ' Step 1 Create a URI to serve as the base address
            Dim baseAddress As New Uri("http://localhost:8000/ServiceModelSamples/Service")

            ' Step 2 Create a ServiceHost instance
            Dim selfHost As New ServiceHost(GetType(CalculatorService), baseAddress)
           Try

                ' Step 3 Add a service endpoint
                ' Add a service endpoint
                selfHost.AddServiceEndpoint( _
                    GetType(ICalculator), _
                    New WSHttpBinding(), _
                    "CalculatorService")

                ' Step 4 Enable metadata exchange.
                Dim smb As New ServiceMetadataBehavior()
                smb.HttpGetEnabled = True
                selfHost.Description.Behaviors.Add(smb)

                ' Step 5 Start the service
                selfHost.Open()
                Console.WriteLine("The service is ready.")
                Console.WriteLine("Press <ENTER> to terminate service.")
                Console.WriteLine()
                Console.ReadLine()

                ' Close the ServiceHostBase to shutdown the service.
                selfHost.Close()
            Catch ce As CommunicationException
                Console.WriteLine("An exception occurred: {0}", ce.Message)
                selfHost.Abort()
            End Try
        End Sub
    End Class

End Module
```

**步驟 1** -建立來保存服務的基底位址 Uri 類別的執行個體。 服務是由包含基底位址及選擇性 URI 的 URL 所識別。 基底位址的格式如下：[傳輸]://[電腦名稱或網域][:選擇性埠號 #]/[選擇性 URI 區段]，計算機服務的基底位址會使用 HTTP 傳輸、localhost、連接埠 8000 和 URI 區段 "GettingStarted"

**步驟 2** – 建立的執行個體<xref:System.ServiceModel.ServiceHost>來裝載服務的類別。 建構函式接受兩個參數：實作服務合約之類別的型別以及服務的基底位址。

**步驟 3** – 建立<xref:System.ServiceModel.Description.ServiceEndpoint>執行個體。 服務端點是由位址、繫結和服務合約所組成。 因此 <xref:System.ServiceModel.Description.ServiceEndpoint> 建構函式會接受服務合約介面型別、繫結和位址。 服務合約是您在服務類型中所定義和實作的 `ICalculator`。 這個範例使用的繫結是 <xref:System.ServiceModel.WSHttpBinding>，這是用來連接至符合 WS-* 規格之端點的內建繫結。 如需 WCF 繫結的詳細資訊，請參閱 [WCF 繫結概觀](bindings-overview.md)。 位址會附加至基底位址以識別端點。 此程式碼中指定的位址是"CalculatorService"，因此端點的完整的位址是`"http://localhost:8000/GettingStarted/CalculatorService"`。

    > [!IMPORTANT]
    > Adding a service endpoint is optional when using .NET Framework 4 or later. In these versions, if no endpoints are added in code or configuration, WCF adds one default endpoint for each combination of base address and contract implemented by the service. For more information about default endpoints see [Specifying an Endpoint Address](specifying-an-endpoint-address.md). For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](simplified-configuration.md) and [Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md).

**步驟 4** – 啟用中繼資料交換。 用戶端會使用中繼資料交換來產生用於呼叫服務作業的 Proxy。 若要啟用中繼資料交換，請建立 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 執行個體，將其 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> 屬性設定為 `true`，並將行為加入至 <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> 執行個體的 <xref:System.ServiceModel.ServiceHost> 集合。

**步驟 5** – 開啟<xref:System.ServiceModel.ServiceHost>來接聽內送訊息。 注意程式碼會等待使用者按下 Enter。 如果不這麼做，應用程式會立即關閉而服務也將關閉。另外也要注意使用的 try/catch 區塊。 在 <xref:System.ServiceModel.ServiceHost> 具現化之後，會將所有其他程式碼放置在 try/catch 區塊中。 如需安全攔截擲回例外狀況的詳細資訊<xref:System.ServiceModel.ServiceHost>，請參閱[使用關閉和中止發行 WCF 用戶端資源](samples/use-close-abort-release-wcf-client-resources.md)

> [!IMPORTANT]
> 編輯 App.config 以反映在程式碼中所做的變更 GettingStartedLib 中：
> 1. 變更至第 14 行 `<service name="GettingStartedLib.CalculatorService">`
> 2. 變更第 17 行至 `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
> 3. 變更到第 22 行 `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`

## <a name="verify-the-service-is-working"></a>確認服務正常運作

1. 執行 GettingStartedHost 主控台應用程式在 Visual Studio 內從。

   服務必須以系統管理員權限執行。 由於 Visual Studio 已開啟系統管理員權限，所以 GettingStartedHost 也會執行系統管理員權限。 您也可以開啟新的命令提示字元使用**系統管理員身分執行**並執行 service.exe。

2. 開啟網頁瀏覽器並瀏覽至服務的偵錯頁面`http://localhost:8000/GettingStarted/CalculatorService`。

## <a name="example"></a>範例

下列範例包含此教學課程上一個步驟的服務合約和實作，並且會將服務裝載到主控台應用程式中。

若要使用命令列編譯器中編譯它，編譯成參考類別庫的 IService1.cs 和 Service1.cs `System.ServiceModel.dll`。 Program.cs 編譯為主控台應用程式。

```csharp
using System;
using System.ServiceModel;

namespace GettingStartedLib
{
        [ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]
        public interface ICalculator
        {
            [OperationContract]
            double Add(double n1, double n2);
            [OperationContract]
            double Subtract(double n1, double n2);
            [OperationContract]
            double Multiply(double n1, double n2);
            [OperationContract]
            double Divide(double n1, double n2);
        }
}
```

```csharp
using System;
using System.ServiceModel;

namespace GettingStartedLib
{
    public class CalculatorService : ICalculator
    {
        public double Add(double n1, double n2)
        {
            double result = n1 + n2;
            Console.WriteLine("Received Add({0},{1})", n1, n2);
            // Code added to write output to the console window.
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Subtract(double n1, double n2)
        {
            double result = n1 - n2;
            Console.WriteLine("Received Subtract({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Multiply(double n1, double n2)
        {
            double result = n1 * n2;
            Console.WriteLine("Received Multiply({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }

        public double Divide(double n1, double n2)
        {
            double result = n1 / n2;
            Console.WriteLine("Received Divide({0},{1})", n1, n2);
            Console.WriteLine("Return: {0}", result);
            return result;
        }
    }
}
```

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
            // Step 1 of the address configuration procedure: Create a URI to serve as the base address.
            Uri baseAddress = new Uri("http://localhost:8000/ServiceModelSamples/Service");

            // Step 2 of the hosting procedure: Create ServiceHost
            ServiceHost selfHost = new ServiceHost(typeof(CalculatorService), baseAddress);

            try
            {
                // Step 3 of the hosting procedure: Add a service endpoint.
                selfHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), "CalculatorService");

                // Step 4 of the hosting procedure: Enable metadata exchange.
                ServiceMetadataBehavior smb = new ServiceMetadataBehavior();
                smb.HttpGetEnabled = true;
                selfHost.Description.Behaviors.Add(smb);

                // Step 5 of the hosting procedure: Start (and then stop) the service.
                selfHost.Open();
                Console.WriteLine("The service is ready.");
                Console.WriteLine("Press <ENTER> to terminate service.");
                Console.WriteLine();
                Console.ReadLine();

                // Close the ServiceHostBase to shutdown the service.
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

Namespace GettingStartedLib

    <ServiceContract(Namespace:="http://Microsoft.ServiceModel.Samples")> _
    Public Interface ICalculator

        <OperationContract()> _
        Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()> _
        Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()> _
        Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double
        <OperationContract()> _
        Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double
    End Interface
End Namespace
```

```vb
Imports System.ServiceModel

Namespace GettingStartedLib

    Public Class CalculatorService
        Implements ICalculator

        Public Function Add(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Add
            Dim result As Double = n1 + n2
            ' Code added to write output to the console window.
            Console.WriteLine("Received Add({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result
        End Function

        Public Function Subtract(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Subtract
            Dim result As Double = n1 - n2
            Console.WriteLine("Received Subtract({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result

        End Function

        Public Function Multiply(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Multiply
            Dim result As Double = n1 * n2
            Console.WriteLine("Received Multiply({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result

        End Function

        Public Function Divide(ByVal n1 As Double, ByVal n2 As Double) As Double Implements ICalculator.Divide
            Dim result As Double = n1 / n2
            Console.WriteLine("Received Divide({0},{1})", n1, n2)
            Console.WriteLine("Return: {0}", result)
            Return result

        End Function
    End Class
End Namespace
```

```vb
Imports System.ServiceModel
Imports System.ServiceModel.Description
Imports GettingStartedLibVB.GettingStartedLib

Module Service

    Class Program
        Shared Sub Main()
            ' Step 1 of the address configuration procedure: Create a URI to serve as the base address.
            Dim baseAddress As New Uri("http://localhost:8000/ServiceModelSamples/Service")

            ' Step 2 of the hosting procedure: Create ServiceHost
            Dim selfHost As New ServiceHost(GetType(CalculatorService), baseAddress)
            Try

                ' Step 3 of the hosting procedure: Add a service endpoint.
                ' Add a service endpoint
                selfHost.AddServiceEndpoint( _
                    GetType(ICalculator), _
                    New WSHttpBinding(), _
                    "CalculatorService")

                ' Step 4 of the hosting procedure: Enable metadata exchange.
                ' Enable metadata exchange
                Dim smb As New ServiceMetadataBehavior()
                smb.HttpGetEnabled = True
                selfHost.Description.Behaviors.Add(smb)

                ' Step 5 of the hosting procedure: Start (and then stop) the service.
                selfHost.Open()
                Console.WriteLine("The service is ready.")
                Console.WriteLine("Press <ENTER> to terminate service.")
                Console.WriteLine()
                Console.ReadLine()

                ' Close the ServiceHostBase to shutdown the service.
                selfHost.Close()
            Catch ce As CommunicationException
                Console.WriteLine("An exception occurred: {0}", ce.Message)
                selfHost.Abort()
            End Try
        End Sub
    End Class

End Module
```

> [!NOTE]
> 此類服務需要權限才能將 HTTP 位址註冊到電腦上，以便接聽。 系統管理員帳戶具有此權限，但是非系統管理員帳戶則必須被授與 HTTP 命名空間的權限。 如需如何設定命名空間保留的詳細資訊，請參閱[設定 HTTP 和 HTTPS](feature-details/configuring-http-and-https.md)。 在 Visual Studio 下執行時，必須以系統管理員權限的身分執行 service.exe。

## <a name="next-steps"></a>後續步驟

服務目前正在執行中。 在下一個工作中，您可以建立 WCF 用戶端。

> [!div class="nextstepaction"]
> [如何：建立 WCF 用戶端](how-to-create-a-wcf-client.md)

如需針對資訊進行疑難排解，請參閱[針對使用者入門教學課程進行疑難排解](troubleshooting-the-getting-started-tutorial.md)。

## <a name="see-also"></a>另請參閱

- [快速入門](samples/getting-started-sample.md)
- [自我裝載](samples/self-host.md)