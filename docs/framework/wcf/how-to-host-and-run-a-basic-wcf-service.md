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
# <a name="tutorial-host-and-run-a-basic-windows-communication-foundation-service"></a><span data-ttu-id="69bbc-102">教程：託管並運行基本的 Windows 通信基礎服務</span><span class="sxs-lookup"><span data-stu-id="69bbc-102">Tutorial: Host and run a basic Windows Communication Foundation service</span></span>

<span data-ttu-id="69bbc-103">本教程介紹創建基本 Windows 通信基礎 （WCF） 應用程式所需的五個任務中的第三個。</span><span class="sxs-lookup"><span data-stu-id="69bbc-103">This tutorial describes the third of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="69bbc-104">有關教程的概述，請參閱[教程：開始使用 Windows 通信基礎應用程式](getting-started-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="69bbc-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="69bbc-105">創建 WCF 應用程式的下一個任務是在主控台應用程式中託管 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="69bbc-105">The next task for creating a WCF application is to host a WCF service in a console application.</span></span> <span data-ttu-id="69bbc-106">WCF 服務公開一個或多個終結點，每個*終結點*公開一個或多個服務操作。</span><span class="sxs-lookup"><span data-stu-id="69bbc-106">A WCF service exposes one or more *endpoints*, each of which exposes one or more service operations.</span></span> <span data-ttu-id="69bbc-107">服務終結點指定以下資訊：</span><span class="sxs-lookup"><span data-stu-id="69bbc-107">A service endpoint specifies the following information:</span></span>

- <span data-ttu-id="69bbc-108">您可以在其中找到服務的位址。</span><span class="sxs-lookup"><span data-stu-id="69bbc-108">An address where you can find the service.</span></span>
- <span data-ttu-id="69bbc-109">包含描述用戶端必須如何與服務通信的資訊的綁定。</span><span class="sxs-lookup"><span data-stu-id="69bbc-109">A binding that contains the information that describes how a client must communicate with the service.</span></span>
- <span data-ttu-id="69bbc-110">定義服務為其用戶端提供的功能的協定。</span><span class="sxs-lookup"><span data-stu-id="69bbc-110">A contract that defines the functionality that the service provides to its clients.</span></span>

<span data-ttu-id="69bbc-111">在本教學課程中，您會了解如何：</span><span class="sxs-lookup"><span data-stu-id="69bbc-111">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="69bbc-112">創建和配置用於託管 WCF 服務的主控台應用專案。</span><span class="sxs-lookup"><span data-stu-id="69bbc-112">Create and configure a console app project for hosting a WCF service.</span></span>
> - <span data-ttu-id="69bbc-113">添加代碼以承載 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="69bbc-113">Add code to host the WCF service.</span></span>
> - <span data-ttu-id="69bbc-114">更新設定檔。</span><span class="sxs-lookup"><span data-stu-id="69bbc-114">Update the configuration file.</span></span>
> - <span data-ttu-id="69bbc-115">啟動 WCF 服務並驗證其正在運行。</span><span class="sxs-lookup"><span data-stu-id="69bbc-115">Start the WCF service and verify it's running.</span></span>

## <a name="create-and-configure-a-console-app-project-for-hosting-the-service"></a><span data-ttu-id="69bbc-116">創建和配置託管服務的主控台應用專案</span><span class="sxs-lookup"><span data-stu-id="69bbc-116">Create and configure a console app project for hosting the service</span></span>

1. <span data-ttu-id="69bbc-117">在視覺化工作室中創建主控台應用專案：</span><span class="sxs-lookup"><span data-stu-id="69bbc-117">Create a console app project in Visual Studio:</span></span>

    1. <span data-ttu-id="69bbc-118">在 **"檔"** 功能表中，選擇 **"打開** > **專案/解決方案**"並流覽到您以前創建的**入門**解決方案 （*獲取入門.sln*）。</span><span class="sxs-lookup"><span data-stu-id="69bbc-118">From the **File** menu, select **Open** > **Project/Solution** and browse to the **GettingStarted** solution you previously created (*GettingStarted.sln*).</span></span> <span data-ttu-id="69bbc-119">選取 [開啟]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="69bbc-119">Select **Open**.</span></span>

    2. <span data-ttu-id="69bbc-120">在 **"查看"** 功能表中，選擇 **"解決方案資源管理器**"。</span><span class="sxs-lookup"><span data-stu-id="69bbc-120">From the **View** menu, select **Solution Explorer**.</span></span>

    3. <span data-ttu-id="69bbc-121">在 **"解決方案資源管理器"** 視窗中，選擇 **"入門"** 解決方案（頂部節點），然後從快顯功能表中選擇 **"添加新** > **專案**"。</span><span class="sxs-lookup"><span data-stu-id="69bbc-121">In the **Solution Explorer** window, select the **GettingStarted** solution (top node), and then select **Add** > **New Project** from the shortcut menu.</span></span>

    4. <span data-ttu-id="69bbc-122">在左側的 **"添加新專案**"視窗中，在 **"可視 C#"** 或"**可視基本**"下選擇**Windows 桌面**類別。</span><span class="sxs-lookup"><span data-stu-id="69bbc-122">In the **Add New Project** window, on the left side, select the **Windows Desktop** category under **Visual C#** or **Visual Basic**.</span></span>

    5. <span data-ttu-id="69bbc-123">選擇**主控台應用 （.NET 框架）** 範本，然後輸入"*入門主機*"**的名稱**。</span><span class="sxs-lookup"><span data-stu-id="69bbc-123">Select the **Console App (.NET Framework)** template, and enter *GettingStartedHost* for the **Name**.</span></span> <span data-ttu-id="69bbc-124">選取 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="69bbc-124">Select **OK**.</span></span>

2. <span data-ttu-id="69bbc-125">在**入門主機**專案中向**入門專案**增加參考：</span><span class="sxs-lookup"><span data-stu-id="69bbc-125">Add a reference in the **GettingStartedHost** project to the **GettingStartedLib** project:</span></span>

    1. <span data-ttu-id="69bbc-126">在 **"解決方案資源管理器"** 視窗中，選擇 **"入門主機**"專案下的 **"參考"** 資料夾，然後從快顯功能表中選擇 **"增加參考**"。</span><span class="sxs-lookup"><span data-stu-id="69bbc-126">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedHost** project, and then select **Add Reference** from the shortcut menu.</span></span>

    2. <span data-ttu-id="69bbc-127">在"**添加參考**"對話方塊中，在視窗左側**的專案**下，選擇 **"解決方案**"。</span><span class="sxs-lookup"><span data-stu-id="69bbc-127">In the **Add Reference** dialog, under **Projects** on the left side of the window, select **Solution**.</span></span>

    3. <span data-ttu-id="69bbc-128">在視窗的中心部分選擇 **"獲取開始Lib"，** 然後選擇 **"確定**"。</span><span class="sxs-lookup"><span data-stu-id="69bbc-128">Select **GettingStartedLib** in the center section of the window, and then select **OK**.</span></span>

       <span data-ttu-id="69bbc-129">此操作使**入門專案**中定義的類型可供**入門主項目目使用**。</span><span class="sxs-lookup"><span data-stu-id="69bbc-129">This action makes the types defined in the **GettingStartedLib** project available to the **GettingStartedHost** project.</span></span>

3. <span data-ttu-id="69bbc-130">在**入門主機**專案中向<xref:System.ServiceModel>程式集增加參考：</span><span class="sxs-lookup"><span data-stu-id="69bbc-130">Add a reference in the **GettingStartedHost** project to the <xref:System.ServiceModel> assembly:</span></span>

    1. <span data-ttu-id="69bbc-131">在 **"解決方案資源管理器"** 視窗中，選擇 **"入門主機**"專案下的 **"參考"** 資料夾，然後從快顯功能表中選擇 **"增加參考**"。</span><span class="sxs-lookup"><span data-stu-id="69bbc-131">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedHost** project, and then select **Add Reference** from the shortcut menu.</span></span>

    2. <span data-ttu-id="69bbc-132">在"**增加參考**"視窗中，在視窗左側的 **"程式集**"下，選擇 **"框架**"。</span><span class="sxs-lookup"><span data-stu-id="69bbc-132">In the **Add Reference** window, under **Assemblies** on the left side of the window, select **Framework**.</span></span>

    3. <span data-ttu-id="69bbc-133">選擇 **"系統.服務模式"，** 然後選擇 **"確定**"。</span><span class="sxs-lookup"><span data-stu-id="69bbc-133">Select **System.ServiceModel**, and then select **OK**.</span></span>

    4. <span data-ttu-id="69bbc-134">通過選擇 **"全部保存檔** > **"保存**解決方案。</span><span class="sxs-lookup"><span data-stu-id="69bbc-134">Save the solution by selecting **File** > **Save All**.</span></span>

## <a name="add-code-to-host-the-service"></a><span data-ttu-id="69bbc-135">添加代碼以承載服務</span><span class="sxs-lookup"><span data-stu-id="69bbc-135">Add code to host the service</span></span>

<span data-ttu-id="69bbc-136">要託管服務，請添加代碼以執行以下步驟：</span><span class="sxs-lookup"><span data-stu-id="69bbc-136">To host the service, you add code to do the following steps:</span></span>

1. <span data-ttu-id="69bbc-137">為基本位址創建 URI。</span><span class="sxs-lookup"><span data-stu-id="69bbc-137">Create a URI for the base address.</span></span>
2. <span data-ttu-id="69bbc-138">創建用於託管服務的類實例。</span><span class="sxs-lookup"><span data-stu-id="69bbc-138">Create a class instance for hosting the service.</span></span>
3. <span data-ttu-id="69bbc-139">創建服務終結點。</span><span class="sxs-lookup"><span data-stu-id="69bbc-139">Create a service endpoint.</span></span>
4. <span data-ttu-id="69bbc-140">啟用中繼資料交換。</span><span class="sxs-lookup"><span data-stu-id="69bbc-140">Enable metadata exchange.</span></span>
5. <span data-ttu-id="69bbc-141">打開服務主機以偵聽傳入消息。</span><span class="sxs-lookup"><span data-stu-id="69bbc-141">Open the service host to listen for incoming messages.</span></span>
  
<span data-ttu-id="69bbc-142">對程式碼進行下列變更：</span><span class="sxs-lookup"><span data-stu-id="69bbc-142">Make the following changes to the code:</span></span>

1. <span data-ttu-id="69bbc-143">打開**入門霍斯特**專案中**的Program.cs**或**Module1.vb**檔，並將其代碼替換為以下代碼：</span><span class="sxs-lookup"><span data-stu-id="69bbc-143">Open the **Program.cs** or **Module1.vb** file in the **GettingStartedHost** project and replace its code with the following code:</span></span>

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

    <span data-ttu-id="69bbc-144">有關此代碼的工作原理的資訊，請參閱[服務託管程式步驟](#service-hosting-program-steps)。</span><span class="sxs-lookup"><span data-stu-id="69bbc-144">For information about how this code works, see [Service hosting program steps](#service-hosting-program-steps).</span></span>

2. <span data-ttu-id="69bbc-145">更新專案屬性：</span><span class="sxs-lookup"><span data-stu-id="69bbc-145">Update the project properties:</span></span>

   1. <span data-ttu-id="69bbc-146">在 **"解決方案資源管理器"** 視窗中，選擇 **"入門主機"** 資料夾，然後從快顯功能表中選擇 **"屬性**"。</span><span class="sxs-lookup"><span data-stu-id="69bbc-146">In the **Solution Explorer** window, select the **GettingStartedHost** folder, and then select **Properties** from the shortcut menu.</span></span>

   2. <span data-ttu-id="69bbc-147">在 **"入門主機"** 屬性頁上，選擇"**應用程式**"選項卡：</span><span class="sxs-lookup"><span data-stu-id="69bbc-147">On the **GettingStartedHost** properties page, select the **Application** tab:</span></span>

      - <span data-ttu-id="69bbc-148">對於 C# 專案，從**啟始物件**清單中選擇 **"入門主機.程式"。**</span><span class="sxs-lookup"><span data-stu-id="69bbc-148">For C# projects, select **GettingStartedHost.Program** from the **Startup object** list.</span></span>

      - <span data-ttu-id="69bbc-149">對於視覺化基本專案，從**啟始物件**清單中選擇 **"服務.程式**"。</span><span class="sxs-lookup"><span data-stu-id="69bbc-149">For Visual Basic projects, select **Service.Program** from the **Startup object** list.</span></span>

   3. <span data-ttu-id="69bbc-150">在 **"檔"** 功能表中，選擇 **"全部保存**"。</span><span class="sxs-lookup"><span data-stu-id="69bbc-150">From the **File** menu, select **Save All**.</span></span>

## <a name="verify-the-service-is-working"></a><span data-ttu-id="69bbc-151">驗證服務是否正常工作</span><span class="sxs-lookup"><span data-stu-id="69bbc-151">Verify the service is working</span></span>

1. <span data-ttu-id="69bbc-152">構建解決方案，然後從 Visual Studio 內部運行**入門主機**主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="69bbc-152">Build the solution, and then run the **GettingStartedHost** console application from inside Visual Studio.</span></span>

    <span data-ttu-id="69bbc-153">服務必須具有管理員許可權運行。</span><span class="sxs-lookup"><span data-stu-id="69bbc-153">The service must be run with administrator privileges.</span></span> <span data-ttu-id="69bbc-154">由於您使用管理員許可權打開了 Visual Studio，因此在視覺化工作室中運行 **"入門主機"** 時，應用程式也具有管理員許可權運行。</span><span class="sxs-lookup"><span data-stu-id="69bbc-154">Because you opened Visual Studio with administrator privileges, when you run **GettingStartedHost** in Visual Studio, the application is run with administrator privileges as well.</span></span> <span data-ttu-id="69bbc-155">作為替代方法，您可以以管理員身份打開新的命令提示符（從快顯功能表中選擇 **"以管理員身份運行"），** > **Run as administrator**並在其中運行 **"獲取啟動Host.exe"。**</span><span class="sxs-lookup"><span data-stu-id="69bbc-155">As an alternative, you can open a new command prompt as an administrator (select **More** > **Run as administrator** from the shortcut menu) and run **GettingStartedHost.exe** within it.</span></span>

2. <span data-ttu-id="69bbc-156">打開 Web 瀏覽器，然後流覽到 服務頁面`http://localhost:8000/GettingStarted/CalculatorService`。</span><span class="sxs-lookup"><span data-stu-id="69bbc-156">Open a web browser and browse to the service's page at `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>

   > [!NOTE]
   > <span data-ttu-id="69bbc-157">此類服務需要適當的許可權才能在電腦上註冊 HTTP 位址以進行偵聽。</span><span class="sxs-lookup"><span data-stu-id="69bbc-157">Services such as this one require the proper permission to register HTTP addresses on the machine for listening.</span></span> <span data-ttu-id="69bbc-158">系統管理員帳戶具有此權限，但是非系統管理員帳戶則必須被授與 HTTP 命名空間的權限。</span><span class="sxs-lookup"><span data-stu-id="69bbc-158">Administrator accounts have this permission, but non-administrator accounts must be granted permission for HTTP namespaces.</span></span> <span data-ttu-id="69bbc-159">如需如何設定命名空間保留的詳細資訊，請參閱[設定 HTTP 和 HTTPS](feature-details/configuring-http-and-https.md)。</span><span class="sxs-lookup"><span data-stu-id="69bbc-159">For more information about how to configure namespace reservations, see [Configuring HTTP and HTTPS](feature-details/configuring-http-and-https.md).</span></span>

## <a name="service-hosting-program-steps"></a><span data-ttu-id="69bbc-160">服務託管程式步驟</span><span class="sxs-lookup"><span data-stu-id="69bbc-160">Service hosting program steps</span></span>

<span data-ttu-id="69bbc-161">添加到託管服務的代碼中的步驟描述如下：</span><span class="sxs-lookup"><span data-stu-id="69bbc-161">The steps in the code you added to host the service are described as follows:</span></span>

- <span data-ttu-id="69bbc-162">**步驟 1：** 創建類的`Uri`實例以保存服務的基本位址。</span><span class="sxs-lookup"><span data-stu-id="69bbc-162">**Step 1**: Create an instance of the `Uri` class to hold the base address of the service.</span></span> <span data-ttu-id="69bbc-163">包含基本位址的 URL 具有標識服務的可選 URI。</span><span class="sxs-lookup"><span data-stu-id="69bbc-163">A URL that contains a base address has an optional URI that identifies a service.</span></span> <span data-ttu-id="69bbc-164">基本位址的格式如下： `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>`。</span><span class="sxs-lookup"><span data-stu-id="69bbc-164">The base address is formatted as follows: `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>`.</span></span> <span data-ttu-id="69bbc-165">計算機服務的基本位址使用 HTTP 傳輸、本地主機、埠 8000 和 URI 段"入門"。</span><span class="sxs-lookup"><span data-stu-id="69bbc-165">The base address for the calculator service uses the HTTP transport, localhost, port 8000, and the URI segment, GettingStarted.</span></span>

- <span data-ttu-id="69bbc-166">**步驟 2：** 創建類的<xref:System.ServiceModel.ServiceHost>實例，用於託管服務。</span><span class="sxs-lookup"><span data-stu-id="69bbc-166">**Step 2**: Create an instance of the <xref:System.ServiceModel.ServiceHost> class, which you use to host the service.</span></span> <span data-ttu-id="69bbc-167">建構函式採用兩個參數：實現服務協定的類類型和服務的基本位址。</span><span class="sxs-lookup"><span data-stu-id="69bbc-167">The constructor takes two parameters: the type of the class that implements the service contract and the base address of the service.</span></span>

- <span data-ttu-id="69bbc-168">**步驟 3**：<xref:System.ServiceModel.Description.ServiceEndpoint>創建實例。</span><span class="sxs-lookup"><span data-stu-id="69bbc-168">**Step 3**: Create a <xref:System.ServiceModel.Description.ServiceEndpoint> instance.</span></span> <span data-ttu-id="69bbc-169">服務端點是由位址、繫結和服務合約所組成。</span><span class="sxs-lookup"><span data-stu-id="69bbc-169">A service endpoint is composed of an address, a binding, and a service contract.</span></span> <span data-ttu-id="69bbc-170"><xref:System.ServiceModel.Description.ServiceEndpoint>建構函式由服務協定介面類別型、綁定和位址組成。</span><span class="sxs-lookup"><span data-stu-id="69bbc-170">The <xref:System.ServiceModel.Description.ServiceEndpoint> constructor is composed of the service contract interface type, a binding, and an address.</span></span> <span data-ttu-id="69bbc-171">服務合約是您在服務類型中所定義和實作的 `ICalculator`。</span><span class="sxs-lookup"><span data-stu-id="69bbc-171">The service contract is `ICalculator`, which you defined and implement in the service type.</span></span> <span data-ttu-id="69bbc-172">此示例的綁定是<xref:System.ServiceModel.WSHttpBinding>，這是一個內置綁定，並連接到符合 WS-\* 規範的終結點。</span><span class="sxs-lookup"><span data-stu-id="69bbc-172">The binding for this sample is <xref:System.ServiceModel.WSHttpBinding>, which is a built-in binding and connects to endpoints that conform to the WS-\* specifications.</span></span> <span data-ttu-id="69bbc-173">有關 WCF 綁定的詳細資訊，請參閱[WCF 綁定概述](bindings-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="69bbc-173">For more information about WCF bindings, see [WCF bindings overview](bindings-overview.md).</span></span> <span data-ttu-id="69bbc-174">將位址追加到基本位址以標識終結點。</span><span class="sxs-lookup"><span data-stu-id="69bbc-174">You append the address to the base address to identify the endpoint.</span></span> <span data-ttu-id="69bbc-175">代碼將位址指定為計算機服務，終結點的完全限定位址為`http://localhost:8000/GettingStarted/CalculatorService`。</span><span class="sxs-lookup"><span data-stu-id="69bbc-175">The code specifies the address as CalculatorService and the fully qualified address for the endpoint as `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="69bbc-176">對於 .NET 框架版本 4 及更高版本，添加服務終結點是可選的。</span><span class="sxs-lookup"><span data-stu-id="69bbc-176">For .NET Framework Version 4 and later, adding a service endpoint is optional.</span></span> <span data-ttu-id="69bbc-177">對於這些版本，如果不添加代碼或配置，WCF 會為服務實現的每個基本位址和協定組合添加一個預設終結點。</span><span class="sxs-lookup"><span data-stu-id="69bbc-177">For these versions, if you don't add your code or configuration, WCF adds one default endpoint for each combination of base address and contract implemented by the service.</span></span> <span data-ttu-id="69bbc-178">有關預設終結點的詳細資訊，請參閱[指定終結點位址](specifying-an-endpoint-address.md)。</span><span class="sxs-lookup"><span data-stu-id="69bbc-178">For more information about default endpoints, see [Specifying an endpoint address](specifying-an-endpoint-address.md).</span></span> <span data-ttu-id="69bbc-179">有關預設終結點、綁定和行為的詳細資訊，請參閱[WCF 服務的](samples/simplified-configuration-for-wcf-services.md)[簡化配置](simplified-configuration.md)和簡化配置。</span><span class="sxs-lookup"><span data-stu-id="69bbc-179">For more information about default endpoints, bindings, and behaviors, see [Simplified configuration](simplified-configuration.md) and [Simplified configuration for WCF services](samples/simplified-configuration-for-wcf-services.md).</span></span>

- <span data-ttu-id="69bbc-180">**步驟 4**：啟用中繼資料交換。</span><span class="sxs-lookup"><span data-stu-id="69bbc-180">**Step 4**: Enable metadata exchange.</span></span> <span data-ttu-id="69bbc-181">用戶端使用中繼資料交換生成用於調用服務操作的代理。</span><span class="sxs-lookup"><span data-stu-id="69bbc-181">Clients use metadata exchange to generate proxies for calling the service operations.</span></span> <span data-ttu-id="69bbc-182">要啟用中繼資料交換，請創建<xref:System.ServiceModel.Description.ServiceMetadataBehavior>實例，將其<xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled>屬性設置為`true`，並將`ServiceMetadataBehavior`物件添加到<xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A><xref:System.ServiceModel.ServiceHost>實例的集合中。</span><span class="sxs-lookup"><span data-stu-id="69bbc-182">To enable metadata exchange, create a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance, set its <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled> property to `true`, and add the `ServiceMetadataBehavior` object to the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> collection of the <xref:System.ServiceModel.ServiceHost> instance.</span></span>

- <span data-ttu-id="69bbc-183">**步驟 5** <xref:System.ServiceModel.ServiceHost> ： 打開以偵聽傳入的消息。</span><span class="sxs-lookup"><span data-stu-id="69bbc-183">**Step 5**: Open <xref:System.ServiceModel.ServiceHost> to listen for incoming messages.</span></span> <span data-ttu-id="69bbc-184">應用程式等待您按**Enter**。</span><span class="sxs-lookup"><span data-stu-id="69bbc-184">The application waits for you to press **Enter**.</span></span> <span data-ttu-id="69bbc-185">應用程式具現化後<xref:System.ServiceModel.ServiceHost>，它執行一個 try/catch 塊。</span><span class="sxs-lookup"><span data-stu-id="69bbc-185">After the application instantiates <xref:System.ServiceModel.ServiceHost>, it executes a try/catch block.</span></span> <span data-ttu-id="69bbc-186">有關安全捕獲引發<xref:System.ServiceModel.ServiceHost>異常的詳細資訊，請參閱[使用關閉和中止來釋放 WCF 用戶端資源](samples/use-close-abort-release-wcf-client-resources.md)。</span><span class="sxs-lookup"><span data-stu-id="69bbc-186">For more information about safely catching exceptions thrown by <xref:System.ServiceModel.ServiceHost>, see [Use Close and Abort to release WCF client resources](samples/use-close-abort-release-wcf-client-resources.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="69bbc-187">添加 WCF 服務庫時，如果通過啟動服務主機來調試它，Visual Studio 會為您託管它。</span><span class="sxs-lookup"><span data-stu-id="69bbc-187">When you add a WCF service library, Visual Studio hosts it for you if you debug it by starting a service host.</span></span> <span data-ttu-id="69bbc-188">為了避免衝突，您可以阻止 Visual Studio 託管 WCF 服務庫。</span><span class="sxs-lookup"><span data-stu-id="69bbc-188">To avoid conflicts, you can prevent Visual Studio from hosting the WCF service library.</span></span>
>
> 1. <span data-ttu-id="69bbc-189">在**解決方案資源管理器**中選擇**入門專案**，然後從快顯功能表中選擇 **"屬性**"。</span><span class="sxs-lookup"><span data-stu-id="69bbc-189">Select the **GettingStartedLib** project in **Solution Explorer** and choose **Properties** from the shortcut menu.</span></span>
> 2. <span data-ttu-id="69bbc-190">在同**一解決方案中調試另一個專案時**，選擇**WCF 選項**並取消選中"啟動 WCF 服務主機"。</span><span class="sxs-lookup"><span data-stu-id="69bbc-190">Select **WCF Options** and uncheck **Start WCF Service Host when debugging another project in the same solution**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="69bbc-191">後續步驟</span><span class="sxs-lookup"><span data-stu-id="69bbc-191">Next steps</span></span>

<span data-ttu-id="69bbc-192">在本教學課程中，您已了解如何：</span><span class="sxs-lookup"><span data-stu-id="69bbc-192">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="69bbc-193">創建和配置用於託管 WCF 服務的主控台應用專案。</span><span class="sxs-lookup"><span data-stu-id="69bbc-193">Create and configure a console app project for hosting a WCF service.</span></span>
> - <span data-ttu-id="69bbc-194">添加代碼以承載 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="69bbc-194">Add code to host the WCF service.</span></span>
> - <span data-ttu-id="69bbc-195">更新設定檔。</span><span class="sxs-lookup"><span data-stu-id="69bbc-195">Update the configuration file.</span></span>
> - <span data-ttu-id="69bbc-196">啟動 WCF 服務並驗證其正在運行。</span><span class="sxs-lookup"><span data-stu-id="69bbc-196">Start the WCF service and verify it's running.</span></span>

<span data-ttu-id="69bbc-197">進入下一個教程，瞭解如何創建 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="69bbc-197">Advance to the next tutorial to learn how to create a WCF client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="69bbc-198">教程：創建 WCF 用戶端</span><span class="sxs-lookup"><span data-stu-id="69bbc-198">Tutorial: Create a WCF client</span></span>](how-to-create-a-wcf-client.md)
