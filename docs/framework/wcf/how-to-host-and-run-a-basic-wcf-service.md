---
title: HOW TO：裝載和執行基本 Windows Communication Foundation 服務
ms.date: 09/14/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: 710ccd69d7b0f8cd8cd3e04729fd952308a3fb4a
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53129372"
---
# <a name="how-to-host-and-run-a-basic-windows-communication-foundation-service"></a><span data-ttu-id="147df-102">HOW TO：裝載和執行基本 Windows Communication Foundation 服務</span><span class="sxs-lookup"><span data-stu-id="147df-102">How to: Host and Run a Basic Windows Communication Foundation Service</span></span>

<span data-ttu-id="147df-103">這是建立 Windows Communication Foundation (WCF) 應用程式所需之六個工作中的第三個工作。</span><span class="sxs-lookup"><span data-stu-id="147df-103">This is the third of six tasks required to create a Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="147df-104">如需這六個工作的概觀，請參閱[使用者入門教學課程](../../../docs/framework/wcf/getting-started-tutorial.md)主題。</span><span class="sxs-lookup"><span data-stu-id="147df-104">For an overview of all six of the tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>

<span data-ttu-id="147df-105">本主題描述如何在主控台應用程式中裝載 Windows Communication Foundation (WCF) 服務。</span><span class="sxs-lookup"><span data-stu-id="147df-105">This topic describes how to host a Windows Communication Foundation (WCF) service in a console application.</span></span> <span data-ttu-id="147df-106">這個程序包含下列步驟：</span><span class="sxs-lookup"><span data-stu-id="147df-106">This procedure consists of the following steps:</span></span>

- <span data-ttu-id="147df-107">建立主控台應用程式專案以裝載服務。</span><span class="sxs-lookup"><span data-stu-id="147df-107">Create a console application project to host the service.</span></span>

- <span data-ttu-id="147df-108">建立服務的服務主機。</span><span class="sxs-lookup"><span data-stu-id="147df-108">Create a service host for the service.</span></span>

- <span data-ttu-id="147df-109">啟用中繼資料交換。</span><span class="sxs-lookup"><span data-stu-id="147df-109">Enable metadata exchange.</span></span>

- <span data-ttu-id="147df-110">開啟服務主機。</span><span class="sxs-lookup"><span data-stu-id="147df-110">Open the service host.</span></span>

<span data-ttu-id="147df-111">這個程序之後的範例會列出這項工作所會撰寫的完整程式碼清單。</span><span class="sxs-lookup"><span data-stu-id="147df-111">A complete listing of the code written in this task is provided in the example following the procedure.</span></span>

## <a name="create-a-new-console-application-to-host-the-service"></a><span data-ttu-id="147df-112">建立新的主控台應用程式來裝載服務</span><span class="sxs-lookup"><span data-stu-id="147df-112">Create a new console application to host the service</span></span>

1. <span data-ttu-id="147df-113">Visual Studio 中建立新的主控台應用程式專案，開始使用的方案上按一下滑鼠右鍵，然後選取**新增** > **新專案**。</span><span class="sxs-lookup"><span data-stu-id="147df-113">Create a new Console Application project in Visual Studio by right-clicking on the Getting Started solution and selecting **Add** > **New Project**.</span></span> <span data-ttu-id="147df-114">在 **加入新的專案** 對話方塊的左側，選取**Windows 桌面** 類別下的**Visual C#** 或**Visual Basic**。</span><span class="sxs-lookup"><span data-stu-id="147df-114">In the **Add New Project** dialog, on the left-hand side, select the **Windows Desktop** category under **Visual C#** or **Visual Basic**.</span></span> <span data-ttu-id="147df-115">選取 **主控台應用程式 (.NET Framework)** 範本，然後再將專案命名為**GettingStartedHost**。</span><span class="sxs-lookup"><span data-stu-id="147df-115">Select the **Console App (.NET Framework)** template, and then name the project **GettingStartedHost**.</span></span>

2. <span data-ttu-id="147df-116">將 GettingStartedLib 專案的參考加入至 GettingStartedHost 專案。</span><span class="sxs-lookup"><span data-stu-id="147df-116">Add a reference to the GettingStartedLib project to the GettingStartedHost project.</span></span> <span data-ttu-id="147df-117">以滑鼠右鍵按一下**參考**的 GettingStartedHost 專案底下的資料夾**方案總管**，然後選取**加入參考**。</span><span class="sxs-lookup"><span data-stu-id="147df-117">Right-click on the **References** folder under the GettingStartedHost project in **Solution Explorer**, and then select **Add Reference**.</span></span> <span data-ttu-id="147df-118">在 [**加入參考**對話方塊中，選取**解決方案**左手邊的對話方塊中，選取 GettingStartedLib] 對話方塊中，[中心] 部分中，然後選擇**新增**。</span><span class="sxs-lookup"><span data-stu-id="147df-118">In the **Add Reference** dialog, select **Solution** on the left-hand side of the dialog, select GettingStartedLib in the center section of the dialog, and then choose **Add**.</span></span> <span data-ttu-id="147df-119">這樣 GettingStartedHost 專案就可以使用 GettingStartedLib 中所定義的型別。</span><span class="sxs-lookup"><span data-stu-id="147df-119">This makes the types defined in GettingStartedLib available to the GettingStartedHost project.</span></span>

3. <span data-ttu-id="147df-120">將 System.ServiceModel 的參考加入至 GettingStartedHost 專案。</span><span class="sxs-lookup"><span data-stu-id="147df-120">Add a reference to System.ServiceModel to the GettingStartedHost project.</span></span> <span data-ttu-id="147df-121">以滑鼠右鍵按一下**參考**的 GettingStartedHost 專案底下的資料夾**方案總管**，然後選取**加入參考**。</span><span class="sxs-lookup"><span data-stu-id="147df-121">Right-click the **References** folder under the GettingStartedHost project in **Solution Explorer** and select **Add Reference**.</span></span> <span data-ttu-id="147df-122">在 **加入參考**對話方塊中，選取**Framework**在對話方塊左側**組件**。</span><span class="sxs-lookup"><span data-stu-id="147df-122">In the **Add Reference** dialog, select **Framework** on the left-hand side of the dialog under **Assemblies**.</span></span> <span data-ttu-id="147df-123">尋找並選取**System.ServiceModel**，然後選擇**確定**。</span><span class="sxs-lookup"><span data-stu-id="147df-123">Find and select **System.ServiceModel**, and then choose **OK**.</span></span> <span data-ttu-id="147df-124">選取儲存方案**檔案** > **全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="147df-124">Save the solution by selecting **File** > **Save All**.</span></span>

## <a name="host-the-service"></a><span data-ttu-id="147df-125">裝載服務</span><span class="sxs-lookup"><span data-stu-id="147df-125">Host the service</span></span>

<span data-ttu-id="147df-126">開啟 Program.cs 或 Module.vb 檔案，並輸入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="147df-126">Open the Program.cs or Module.vb file and enter the following code:</span></span>

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

<span data-ttu-id="147df-127">**步驟 1** -建立來保存服務的基底位址 Uri 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="147df-127">**Step 1** - Creates an instance of the Uri class to hold the base address of the service.</span></span> <span data-ttu-id="147df-128">服務是由包含基底位址及選擇性 URI 的 URL 所識別。</span><span class="sxs-lookup"><span data-stu-id="147df-128">Services are identified by a URL which contains a base address and an optional URI.</span></span> <span data-ttu-id="147df-129">基底位址的格式如下：[傳輸]://[電腦名稱或網域][:選擇性埠號 #]/[選擇性 URI 區段]，計算機服務的基底位址會使用 HTTP 傳輸、localhost、連接埠 8000 和 URI 區段 "GettingStarted"</span><span class="sxs-lookup"><span data-stu-id="147df-129">The base address is formatted as follows:[transport]://[machine-name or domain][:optional port #]/[optional URI segment]The base address for the calculator service uses the HTTP transport, localhost, port 8000, and the URI segment "GettingStarted"</span></span>

<span data-ttu-id="147df-130">**步驟 2** – 建立的執行個體<xref:System.ServiceModel.ServiceHost>來裝載服務的類別。</span><span class="sxs-lookup"><span data-stu-id="147df-130">**Step 2** – Creates an instance of the <xref:System.ServiceModel.ServiceHost> class to host the service.</span></span> <span data-ttu-id="147df-131">建構函式接受兩個參數：實作服務合約之類別的型別以及服務的基底位址。</span><span class="sxs-lookup"><span data-stu-id="147df-131">The constructor takes two parameters, the type of the class that implements the service contract, and the base address of the service.</span></span>

<span data-ttu-id="147df-132">**步驟 3** – 建立<xref:System.ServiceModel.Description.ServiceEndpoint>執行個體。</span><span class="sxs-lookup"><span data-stu-id="147df-132">**Step 3** – Creates a <xref:System.ServiceModel.Description.ServiceEndpoint> instance.</span></span> <span data-ttu-id="147df-133">服務端點是由位址、繫結和服務合約所組成。</span><span class="sxs-lookup"><span data-stu-id="147df-133">A service endpoint is composed of an address, a binding, and a service contract.</span></span> <span data-ttu-id="147df-134">因此 <xref:System.ServiceModel.Description.ServiceEndpoint> 建構函式會接受服務合約介面型別、繫結和位址。</span><span class="sxs-lookup"><span data-stu-id="147df-134">The <xref:System.ServiceModel.Description.ServiceEndpoint> constructor therefore takes the service contract interface type, a binding, and an address.</span></span> <span data-ttu-id="147df-135">服務合約是您在服務類型中所定義和實作的 `ICalculator`。</span><span class="sxs-lookup"><span data-stu-id="147df-135">The service contract is `ICalculator`, which you defined and implement in the service type.</span></span> <span data-ttu-id="147df-136">這個範例使用的繫結是 <xref:System.ServiceModel.WSHttpBinding>，這是用來連接至符合 WS-\* 規格之端點的內建繫結。</span><span class="sxs-lookup"><span data-stu-id="147df-136">The binding used in this sample is <xref:System.ServiceModel.WSHttpBinding> which is a built-in binding that is used for connecting to endpoints that conform to the WS-\* specifications.</span></span> <span data-ttu-id="147df-137">如需 WCF 繫結的詳細資訊，請參閱 [WCF 繫結概觀](../../../docs/framework/wcf/bindings-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="147df-137">For more information about WCF bindings, see [WCF Bindings Overview](../../../docs/framework/wcf/bindings-overview.md).</span></span> <span data-ttu-id="147df-138">位址會附加至基底位址以識別端點。</span><span class="sxs-lookup"><span data-stu-id="147df-138">The address is appended to the base address to identify the endpoint.</span></span> <span data-ttu-id="147df-139">此程式碼中指定的位址是"CalculatorService"，因此端點的完整的位址是`"http://localhost:8000/GettingStarted/CalculatorService"`。</span><span class="sxs-lookup"><span data-stu-id="147df-139">The address specified in this code is "CalculatorService" so the fully qualified address for the endpoint is `"http://localhost:8000/GettingStarted/CalculatorService"`.</span></span>

    > [!IMPORTANT]
    > Adding a service endpoint is optional when using .NET Framework 4 or later. In these versions, if no endpoints are added in code or configuration, WCF adds one default endpoint for each combination of base address and contract implemented by the service. For more information about default endpoints see [Specifying an Endpoint Address](../../../docs/framework/wcf/specifying-an-endpoint-address.md). For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).

<span data-ttu-id="147df-140">**步驟 4** – 啟用中繼資料交換。</span><span class="sxs-lookup"><span data-stu-id="147df-140">**Step 4** – Enable metadata exchange.</span></span> <span data-ttu-id="147df-141">用戶端會使用中繼資料交換來產生用於呼叫服務作業的 Proxy。</span><span class="sxs-lookup"><span data-stu-id="147df-141">Clients will use metadata exchange to generate proxies that will be used to call the service operations.</span></span> <span data-ttu-id="147df-142">若要啟用中繼資料交換，請建立 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 執行個體，將其 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> 屬性設定為 `true`，並將行為新增至 <xref:System.ServiceModel.ServiceHost> 執行個體的 <!--zz <xref:System.ServiceModel.ServiceHost.Behaviors%2A>  -->`System.ServiceModel.ServiceHost.Behaviors%2A` 集合。</span><span class="sxs-lookup"><span data-stu-id="147df-142">To enable metadata exchange create a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance, set it’s <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true`, and add the behavior to the <!--zz <xref:System.ServiceModel.ServiceHost.Behaviors%2A>  -->`System.ServiceModel.ServiceHost.Behaviors%2A` collection of the <xref:System.ServiceModel.ServiceHost> instance.</span></span>

<span data-ttu-id="147df-143">**步驟 5** – 開啟<xref:System.ServiceModel.ServiceHost>來接聽內送訊息。</span><span class="sxs-lookup"><span data-stu-id="147df-143">**Step 5** – Open the <xref:System.ServiceModel.ServiceHost> to listen for incoming messages.</span></span> <span data-ttu-id="147df-144">注意程式碼會等待使用者按下 Enter。</span><span class="sxs-lookup"><span data-stu-id="147df-144">Notice the code waits for the user to hit enter.</span></span> <span data-ttu-id="147df-145">如果不這麼做，應用程式會立即關閉而服務也將關閉。另外也要注意使用的 try/catch 區塊。</span><span class="sxs-lookup"><span data-stu-id="147df-145">If you do not do this, the app will close immediately and the service will shut down.Also notice a  try/catch block used.</span></span> <span data-ttu-id="147df-146">在 <xref:System.ServiceModel.ServiceHost> 具現化之後，會將所有其他程式碼放置在 try/catch 區塊中。</span><span class="sxs-lookup"><span data-stu-id="147df-146">After the <xref:System.ServiceModel.ServiceHost> has been instantiated, all other code is placed in a try/catch block.</span></span> <span data-ttu-id="147df-147">如需安全攔截擲回例外狀況的詳細資訊<xref:System.ServiceModel.ServiceHost>，請參閱[使用關閉和中止發行 WCF 用戶端資源](../../../docs/framework/wcf/samples/use-close-abort-release-wcf-client-resources.md)</span><span class="sxs-lookup"><span data-stu-id="147df-147">For more information about safely catching exceptions thrown by <xref:System.ServiceModel.ServiceHost>, see [Use Close and Abort to release WCF client resources](../../../docs/framework/wcf/samples/use-close-abort-release-wcf-client-resources.md)</span></span>

> [!IMPORTANT]
> <span data-ttu-id="147df-148">編輯 App.config 以反映在程式碼中所做的變更 GettingStartedLib 中：</span><span class="sxs-lookup"><span data-stu-id="147df-148">Edit App.config in GettingStartedLib to reflect the changes made in code:</span></span>
> 1. <span data-ttu-id="147df-149">變更至第 14 行 `<service name="GettingStartedLib.CalculatorService">`</span><span class="sxs-lookup"><span data-stu-id="147df-149">Change line 14 to `<service name="GettingStartedLib.CalculatorService">`</span></span>
> 2. <span data-ttu-id="147df-150">變更第 17 行至 `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span><span class="sxs-lookup"><span data-stu-id="147df-150">Change line 17 to `<add baseAddress = "http://localhost:8000/GettingStarted/CalculatorService" />`</span></span>
> 3. <span data-ttu-id="147df-151">變更到第 22 行 `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span><span class="sxs-lookup"><span data-stu-id="147df-151">Change line 22 to `<endpoint address="" binding="wsHttpBinding" contract="GettingStartedLib.ICalculator">`</span></span>

## <a name="verify-the-service-is-working"></a><span data-ttu-id="147df-152">確認服務正常運作</span><span class="sxs-lookup"><span data-stu-id="147df-152">Verify the service is working</span></span>

1. <span data-ttu-id="147df-153">執行 GettingStartedHost 主控台應用程式在 Visual Studio 內從。</span><span class="sxs-lookup"><span data-stu-id="147df-153">Run the GettingStartedHost console application from inside Visual Studio.</span></span>

   <span data-ttu-id="147df-154">服務必須以系統管理員權限執行。</span><span class="sxs-lookup"><span data-stu-id="147df-154">The service must be run with administrator privileges.</span></span> <span data-ttu-id="147df-155">由於 Visual Studio 已開啟系統管理員權限，所以 GettingStartedHost 也會執行系統管理員權限。</span><span class="sxs-lookup"><span data-stu-id="147df-155">Because Visual Studio was opened with administrator privileges, GettingStartedHost is also run with administrator privileges.</span></span> <span data-ttu-id="147df-156">您也可以開啟新的命令提示字元使用**系統管理員身分執行**並執行 service.exe。</span><span class="sxs-lookup"><span data-stu-id="147df-156">You can also open a new command prompt using **Run as administrator** and run service.exe within it.</span></span>

2. <span data-ttu-id="147df-157">開啟網頁瀏覽器並瀏覽至服務的偵錯頁面`http://localhost:8000/GettingStarted/CalculatorService`。</span><span class="sxs-lookup"><span data-stu-id="147df-157">Open a web browser and browse to the service's debug page at `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>

## <a name="example"></a><span data-ttu-id="147df-158">範例</span><span class="sxs-lookup"><span data-stu-id="147df-158">Example</span></span>

<span data-ttu-id="147df-159">下列範例包含此教學課程上一個步驟的服務合約和實作，並且會將服務裝載到主控台應用程式中。</span><span class="sxs-lookup"><span data-stu-id="147df-159">The following example includes the service contract and implementation from previous steps in the tutorial and hosts the service in a console application.</span></span>

<span data-ttu-id="147df-160">若要使用命令列編譯器中編譯它，編譯成參考類別庫的 IService1.cs 和 Service1.cs `System.ServiceModel.dll`。</span><span class="sxs-lookup"><span data-stu-id="147df-160">To compile this with a command-line compiler, compile IService1.cs and Service1.cs into a class library that references `System.ServiceModel.dll`.</span></span> <span data-ttu-id="147df-161">Program.cs 編譯為主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="147df-161">Compile Program.cs as a console application.</span></span>

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
> <span data-ttu-id="147df-162">此類服務需要權限才能將 HTTP 位址註冊到電腦上，以便接聽。</span><span class="sxs-lookup"><span data-stu-id="147df-162">Services such as this one require permission to register HTTP addresses on the machine for listening.</span></span> <span data-ttu-id="147df-163">系統管理員帳戶具有此權限，但是非系統管理員帳戶則必須被授與 HTTP 命名空間的權限。</span><span class="sxs-lookup"><span data-stu-id="147df-163">Administrator accounts have this permission, but non-administrator accounts must be granted permission for HTTP namespaces.</span></span> <span data-ttu-id="147df-164">如需如何設定命名空間保留的詳細資訊，請參閱[設定 HTTP 和 HTTPS](../../../docs/framework/wcf/feature-details/configuring-http-and-https.md)。</span><span class="sxs-lookup"><span data-stu-id="147df-164">For more information about how to configure namespace reservations, see [Configuring HTTP and HTTPS](../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).</span></span> <span data-ttu-id="147df-165">在 Visual Studio 下執行時，必須以系統管理員權限的身分執行 service.exe。</span><span class="sxs-lookup"><span data-stu-id="147df-165">When running under Visual Studio, the service.exe must be run with administrator privileges.</span></span>

## <a name="next-steps"></a><span data-ttu-id="147df-166">後續步驟</span><span class="sxs-lookup"><span data-stu-id="147df-166">Next steps</span></span>

<span data-ttu-id="147df-167">服務目前正在執行中。</span><span class="sxs-lookup"><span data-stu-id="147df-167">Now the service is running.</span></span> <span data-ttu-id="147df-168">在下一個工作中，您可以建立 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="147df-168">In the next task, you create a WCF client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="147df-169">操作說明：建立 WCF 用戶端</span><span class="sxs-lookup"><span data-stu-id="147df-169">How to: Create a WCF client</span></span>](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)

<span data-ttu-id="147df-170">如需針對資訊進行疑難排解，請參閱[針對使用者入門教學課程進行疑難排解](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="147df-170">For troubleshooting information, see [Troubleshooting the Getting Started Tutorial](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="147df-171">另請參閱</span><span class="sxs-lookup"><span data-stu-id="147df-171">See also</span></span>

- [<span data-ttu-id="147df-172">快速入門</span><span class="sxs-lookup"><span data-stu-id="147df-172">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)
- [<span data-ttu-id="147df-173">自我裝載</span><span class="sxs-lookup"><span data-stu-id="147df-173">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)