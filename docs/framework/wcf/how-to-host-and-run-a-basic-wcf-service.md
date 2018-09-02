---
title: HOW TO：裝載和執行基本 Windows Communication Foundation 服務
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: e2bf16bd07c7ac9d918a4ae95d7f4aa185d436ec
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43404667"
---
# <a name="how-to-host-and-run-a-basic-windows-communication-foundation-service"></a>HOW TO：裝載和執行基本 Windows Communication Foundation 服務
這是建立 Windows Communication Foundation (WCF) 應用程式所需之六個工作中的第三個工作。 如需這六個工作的概觀，請參閱[使用者入門教學課程](../../../docs/framework/wcf/getting-started-tutorial.md)主題。  
  
 本主題描述如何在主控台應用程式中裝載 Windows Communication Foundation (WCF) 服務。 這個程序包含下列步驟：  
  
-   建立主控台應用程式專案以裝載服務。  
  
-   建立服務的服務主機。  
  
-   啟用中繼資料交換。  
  
-   開啟服務主機。  
  
 這個程序之後的範例會列出這項工作所會撰寫的完整程式碼清單。  
  
## <a name="to-create-a-new-console-application-to-host-the-service"></a>若要建立新的主控台應用程式以裝載服務  
  
1.  以滑鼠右鍵按一下 [使用者入門] 方案並選取 [新增]、[新增專案]，以建立新的主控台應用程式專案。 在 [新增專案] 對話方塊的左側，選取 [C#] 或 [VB] 下方的 [Windows]。 在對話方塊的中間區段中選取 [主控台應用程式]。 將專案命名為 GettingStartedHost。  
  
2.  以滑鼠右鍵按一下 [方案總管] 中的 [GettingStartedHost] 專案並選取 [屬性]，將 GettingStartedHost 專案的目標 Framework 設定為 .NET Framework 4.5。 在標示 [目標 Framework] 的下拉式方塊中選取 [.NET Framework 4.5]。 設定 VB 專案目標 Framework 的方式稍有不同，請在 GettingStartedHost 專案屬性對話方塊中，按一下螢幕左側的 [編譯] 索引標籤，然後按一下對話方塊左下角的 [進階編譯選項] 按鈕。 接著在標籤為 [目標 Framework] 的下拉式方塊中選取 [.NET Framework 4.5]。  
  
     設定目標 Framework 會導致 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] 重新載入該方案，請在出現提示時按下 [確定]。  
  
3.  在 [方案總管] 中，以滑鼠右鍵按一下 [GettingStartedHost] 專案底下的 [參考] 資料夾並選取 [新增參考]，將 GettingStartedLib 專案的參考新增至 GettingStartedHost 專案。 在 [新增參考] 對話方塊的左側選取 [方案]，選取對話方塊中間區段中的 [GettingStartedLib]，然後按一下 [新增]。 這樣 GettingStartedHost 專案就可以使用 GettingStartedLib 中所定義的型別。  
  
4.  在 [方案總管] 中，以滑鼠右鍵按一下 [GettingStartedHost] 專案底下的 [參考] 資料夾並選取 [新增參考]，將 System.ServiceModel 的參考新增至 GettingStartedHost 專案。 在 [新增參考] 對話方塊中，選取對話方塊左側的 [Framework]。 在 [搜尋組件] 文字方塊中輸入 `System.ServiceModel`。 在對話方塊中間區段中選取 [System.ServiceModel]，按一下 [新增] 按鈕，然後按一下 [關閉] 按鈕。 按一下主功能表下的 [全部儲存] 按鈕，以儲存方案。  
  
### <a name="to-host-the-service"></a>若要裝載服務  
  
-   開啟 Program.cs 或 Module.vb 檔案，並輸入下列程式碼：  
  
    ```csharp
    // program.cs  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using System.ServiceModel;  
    using GettingStartedLib;  
    using System.ServiceModel.Description;   
  
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
    'Module1.vb  
    Imports System  
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
  
    1.  步驟 1：建立 Uri 類別的執行個體以保留服務的基底位址 (Base Address)。 服務是由包含基底位址及選擇性 URI 的 URL 所識別。 基底位址的格式如下：[傳輸]://[電腦名稱或網域][:選擇性埠號 #]/[選擇性 URI 區段]，計算機服務的基底位址會使用 HTTP 傳輸、localhost、連接埠 8000 和 URI 區段 "GettingStarted"  
  
    2.  步驟 2：建立 <xref:System.ServiceModel.ServiceHost> 類別的執行個體以裝載服務。 建構函式接受兩個參數：實作服務合約之類別的型別以及服務的基底位址。  
  
    3.  步驟 3：建立 <xref:System.ServiceModel.Description.ServiceEndpoint> 執行個體。 服務端點是由位址、繫結和服務合約所組成。 因此 <xref:System.ServiceModel.Description.ServiceEndpoint> 建構函式會接受服務合約介面型別、繫結和位址。 服務合約是您在服務類型中所定義和實作的 `ICalculator`。 這個範例使用的繫結是 <xref:System.ServiceModel.WSHttpBinding>，這是用來連接至符合 WS-* 規格之端點的內建繫結。 如需 WCF 繫結的詳細資訊，請參閱 [WCF 繫結概觀](../../../docs/framework/wcf/bindings-overview.md)。 位址會附加至基底位址以識別端點。 此程式碼中指定的位址是"CalculatorService"，因此端點的完整的位址是`"http://localhost:8000/GettingStarted/CalculatorService"`。  
  
        > [!IMPORTANT]
        >  使用 .NET Framework 4 (含) 以後版本時，加入服務端點是選擇性的。 在這些版本中，如果沒有在程式碼或組態中加入端點，則 WCF 會為服務所實作之合約與基底位址的每個組合加入一個預設端點。 如需預設端點的詳細資訊，請參閱[指定端點位址](../../../docs/framework/wcf/specifying-an-endpoint-address.md)。 如需預設端點、繫結和行為的詳細資訊，請參閱[簡化的組態](../../../docs/framework/wcf/simplified-configuration.md)和 [WCF 服務的簡化組態](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。  
  
    4.  步驟 4：啟用中繼資料交換。 用戶端會使用中繼資料交換來產生用於呼叫服務作業的 Proxy。 若要啟用中繼資料交換，請建立 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 執行個體，將其 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> 屬性設定為 `true`，並將行為新增至 <xref:System.ServiceModel.ServiceHost> 執行個體的 <!--zz <xref:System.ServiceModel.ServiceHost.Behaviors%2A>  -->`System.ServiceModel.ServiceHost.Behaviors%2A` 集合。  
  
    5.  步驟 5：開啟 <xref:System.ServiceModel.ServiceHost> 以開始接聽傳入訊息。 注意程式碼會等待使用者按下 Enter。 如果不這麼做，應用程式會立即關閉而服務也將關閉。另外也要注意使用的 try/catch 區塊。 在 <xref:System.ServiceModel.ServiceHost> 具現化之後，會將所有其他程式碼放置在 try/catch 區塊中。 如需安全攔截 <xref:System.ServiceModel.ServiceHost> 擲回之例外狀況的詳細資訊，請參閱[避免 Using 陳述式發生問題](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md)  
  
> [!IMPORTANT]
> 編輯 App.config 以反映在程式碼中所做的變更 GettingStartedLib 中： 
> 1. 變更至第 14 行 `<service name="GettingStartedLib.CalculatorService">`
> 2. 變更第 17 行至 `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`
> 3. 變更到第 22 行 `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`
        
### <a name="to-verify-the-service-is-working"></a>若要驗證服務是否執行中  
  
1.  從 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] 中執行 GettingStartedHost 主控台應用程式。 在 [!INCLUDE[wv](../../../includes/wv-md.md)] (含) 以後版本的作業系統中執行時，必須以系統管理員權限來執行服務。 因為 Visual Studio 是以系統管理員權限的身分執行，所以 GettingStartedHost 也要以系統管理員權限的身分執行。 您也可以利用系統管理員權限開啟命令提示字元執行，然後透過命令提示字元執行 service.exe。  
  
2.  開啟 Internet Explorer，並瀏覽至服務位於 `http://localhost:8000/GettingStarted/CalculatorService` 的偵錯頁面。  
  
## <a name="example"></a>範例  
 下列範例包含此教學課程上一個步驟的服務合約和實作，並且會將服務裝載到主控台應用程式中。  
  
 若要使用命令列編譯器編譯這個範例，請將 IService1.cs 和 Service1.cs 編譯成參考 `System.ServiceModel.dll` 的類別程式庫。 然後將 Program.cs 編譯為主控台應用程式。  
  
```csharp
// IService1.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.Text;  
  
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
// Service1.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.Text;  
  
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
//Program.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.ServiceModel;  
using GettingStartedLib;  
using System.ServiceModel.Description;   
  
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
'IService1.vb  
Imports System  
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
'Service1.vb  
Imports System  
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
'Module1.vb  
Imports System  
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
>  此類服務需要權限才能將 HTTP 位址註冊到電腦上，以便接聽。 系統管理員帳戶具有此權限，但是非系統管理員帳戶則必須被授與 HTTP 命名空間的權限。 如需如何設定命名空間保留的詳細資訊，請參閱[設定 HTTP 和 HTTPS](../../../docs/framework/wcf/feature-details/configuring-http-and-https.md)。 在 Visual Studio 下執行時，必須以系統管理員權限的身分執行 service.exe。  
  
 服務目前正在執行中。 繼續進行[如何：建立用戶端](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)。 如需針對資訊進行疑難排解，請參閱[針對使用者入門教學課程進行疑難排解](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md)。  
  
## <a name="see-also"></a>另請參閱  
 [快速入門](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [自我裝載](../../../docs/framework/wcf/samples/self-host.md)
