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
ms.openlocfilehash: 38fd9b89e2719be8ce4d33b1b50f68171d587369
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2019
ms.locfileid: "58410091"
---
# <a name="tutorial-host-and-run-a-basic-windows-communication-foundation-service"></a><span data-ttu-id="764e6-102">教學課程：裝載和執行基本的 Windows Communication Foundation 服務</span><span class="sxs-lookup"><span data-stu-id="764e6-102">Tutorial: Host and run a basic Windows Communication Foundation service</span></span>

<span data-ttu-id="764e6-103">本教學課程說明建立基本的 Windows Communication Foundation (WCF) 應用程式所需的五個工作的第三個。</span><span class="sxs-lookup"><span data-stu-id="764e6-103">This tutorial describes the third of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="764e6-104">如需教學課程的概觀，請參閱[教學課程：開始使用 Windows Communication Foundation 應用程式](getting-started-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="764e6-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="764e6-105">建立 WCF 應用程式的下一個工作是將 WCF 服務裝載於主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="764e6-105">The next task for creating a WCF application is to host a WCF service in a console application.</span></span> <span data-ttu-id="764e6-106">WCF 服務公開一或多個*端點*，其中每一個都會公開一或多個服務作業。</span><span class="sxs-lookup"><span data-stu-id="764e6-106">A WCF service exposes one or more *endpoints*, each of which exposes one or more service operations.</span></span> <span data-ttu-id="764e6-107">服務端點會指定下列資訊：</span><span class="sxs-lookup"><span data-stu-id="764e6-107">A service endpoint specifies the following information:</span></span> 
- <span data-ttu-id="764e6-108">您可以在其中找到服務位址。</span><span class="sxs-lookup"><span data-stu-id="764e6-108">An address where you can find the service.</span></span>
- <span data-ttu-id="764e6-109">繫結，其中包含描述如何在用戶端必須與服務通訊的資訊。</span><span class="sxs-lookup"><span data-stu-id="764e6-109">A binding that contains the information that describes how a client must communicate with the service.</span></span> 
- <span data-ttu-id="764e6-110">定義服務提供給其用戶端功能的合約。</span><span class="sxs-lookup"><span data-stu-id="764e6-110">A contract that defines the functionality that the service provides to its clients.</span></span>

<span data-ttu-id="764e6-111">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="764e6-111">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="764e6-112">建立及設定 WCF 服務裝載的主控台應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="764e6-112">Create and configure a console app project for hosting a WCF service.</span></span>
> - <span data-ttu-id="764e6-113">加入裝載 WCF 服務的程式碼。</span><span class="sxs-lookup"><span data-stu-id="764e6-113">Add code to host the WCF service.</span></span>
> - <span data-ttu-id="764e6-114">更新組態檔。</span><span class="sxs-lookup"><span data-stu-id="764e6-114">Update the configuration file.</span></span>
> - <span data-ttu-id="764e6-115">啟動 WCF 服務，並確認它正在執行。</span><span class="sxs-lookup"><span data-stu-id="764e6-115">Start the WCF service and verify it's running.</span></span>


## <a name="create-and-configure-a-console-app-project-for-hosting-the-service"></a><span data-ttu-id="764e6-116">建立及設定裝載服務的主控台應用程式專案</span><span class="sxs-lookup"><span data-stu-id="764e6-116">Create and configure a console app project for hosting the service</span></span>

1. <span data-ttu-id="764e6-117">Visual Studio 中建立主控台應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="764e6-117">Create a console app project in Visual Studio:</span></span> 
 
    1. <span data-ttu-id="764e6-118">從**檔案**功能表上，選取**開放** > **專案/方案**並瀏覽至**GettingStarted**解決方案您先前建立 (*GettingStarted.sln*)。</span><span class="sxs-lookup"><span data-stu-id="764e6-118">From the **File** menu, select **Open** > **Project/Solution** and browse to the **GettingStarted** solution you previously created (*GettingStarted.sln*).</span></span> <span data-ttu-id="764e6-119">選取 [開啟] 。</span><span class="sxs-lookup"><span data-stu-id="764e6-119">Select **Open**.</span></span>

    2. <span data-ttu-id="764e6-120">從**檢視**功能表上，選取**方案總管 中**。</span><span class="sxs-lookup"><span data-stu-id="764e6-120">From the **View** menu, select **Solution Explorer**.</span></span>
    
    3. <span data-ttu-id="764e6-121">在 [**方案總管] 中**視窗中，選取**GettingStarted**方案 （最上層節點），然後再選取**新增** > **新專案**快顯功能表中。</span><span class="sxs-lookup"><span data-stu-id="764e6-121">In the **Solution Explorer** window, select the **GettingStarted** solution (top node), and then select **Add** > **New Project** from the shortcut menu.</span></span> 

    4. <span data-ttu-id="764e6-122">在 [**加入新的專案**視窗中的，在左側，選取**Windows 桌面**] 類別下的**Visual C#** 或**Visual Basic**.</span><span class="sxs-lookup"><span data-stu-id="764e6-122">In the **Add New Project** window, on the left side, select the **Windows Desktop** category under **Visual C#** or **Visual Basic**.</span></span> 

    5. <span data-ttu-id="764e6-123">選取 **主控台應用程式 (.NET Framework)** 範本，然後輸入*GettingStartedHost*如**名稱**。</span><span class="sxs-lookup"><span data-stu-id="764e6-123">Select the **Console App (.NET Framework)** template, and enter *GettingStartedHost* for the **Name**.</span></span> <span data-ttu-id="764e6-124">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="764e6-124">Select **OK**.</span></span>

2. <span data-ttu-id="764e6-125">加入參考**GettingStartedHost**專案加入**GettingStartedLib**專案：</span><span class="sxs-lookup"><span data-stu-id="764e6-125">Add a reference in the **GettingStartedHost** project to the **GettingStartedLib** project:</span></span> 

    1. <span data-ttu-id="764e6-126">在 **方案總管 中**視窗中，選取**參考**下的資料夾**GettingStartedHost**專案，然後再選取**加入參考**快顯功能表中。</span><span class="sxs-lookup"><span data-stu-id="764e6-126">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedHost** project, and then select **Add Reference** from the shortcut menu.</span></span> 

    2. <span data-ttu-id="764e6-127">在 [**加入參考**] 對話方塊底下**專案**在視窗的左側，選取**解決方案**。</span><span class="sxs-lookup"><span data-stu-id="764e6-127">In the **Add Reference** dialog, under **Projects** on the left side of the window, select **Solution**.</span></span> 
 
    3. <span data-ttu-id="764e6-128">選取  **GettingStartedLib**在視窗中，然後再選取 中心 區段**確定**。</span><span class="sxs-lookup"><span data-stu-id="764e6-128">Select **GettingStartedLib** in the center section of the window, and then select **OK**.</span></span> 

       <span data-ttu-id="764e6-129">這個動作可定義中的型別**GettingStartedLib**專案能夠**GettingStartedHost**專案。</span><span class="sxs-lookup"><span data-stu-id="764e6-129">This action makes the types defined in the **GettingStartedLib** project available to the **GettingStartedHost** project.</span></span>

3. <span data-ttu-id="764e6-130">加入參考**GettingStartedHost**專案加入<xref:System.ServiceModel>組件：</span><span class="sxs-lookup"><span data-stu-id="764e6-130">Add a reference in the **GettingStartedHost** project to the <xref:System.ServiceModel> assembly:</span></span> 

    1. <span data-ttu-id="764e6-131">在 **方案總管 中**視窗中，選取**參考**下的資料夾**GettingStartedHost**專案，然後再選取**加入參考**快顯功能表中。</span><span class="sxs-lookup"><span data-stu-id="764e6-131">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedHost** project, and then select **Add Reference** from the shortcut menu.</span></span>
    
    2. <span data-ttu-id="764e6-132">在 [**加入參考**] 視窗底下**組件**在視窗的左側，選取**Framework**。</span><span class="sxs-lookup"><span data-stu-id="764e6-132">In the **Add Reference** window, under **Assemblies** on the left side of the window, select **Framework**.</span></span> 

    3. <span data-ttu-id="764e6-133">選取  **System.ServiceModel**，然後選取**確定**。</span><span class="sxs-lookup"><span data-stu-id="764e6-133">Select **System.ServiceModel**, and then select **OK**.</span></span> 
    
    4. <span data-ttu-id="764e6-134">選取儲存方案**檔案** > **全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="764e6-134">Save the solution by selecting **File** > **Save All**.</span></span>

## <a name="add-code-to-host-the-service"></a><span data-ttu-id="764e6-135">加入程式碼來裝載服務</span><span class="sxs-lookup"><span data-stu-id="764e6-135">Add code to host the service</span></span>

<span data-ttu-id="764e6-136">若要裝載服務，您可以加入程式碼，以執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="764e6-136">To host the service, you add code to do the following steps:</span></span> 
   1. <span data-ttu-id="764e6-137">建立的基底位址的 URI。</span><span class="sxs-lookup"><span data-stu-id="764e6-137">Create a URI for the base address.</span></span>
   2. <span data-ttu-id="764e6-138">建立裝載服務的類別執行個體。</span><span class="sxs-lookup"><span data-stu-id="764e6-138">Create a class instance for hosting the service.</span></span>
   3. <span data-ttu-id="764e6-139">建立服務端點。</span><span class="sxs-lookup"><span data-stu-id="764e6-139">Create a service endpoint.</span></span>
   4. <span data-ttu-id="764e6-140">啟用中繼資料交換。</span><span class="sxs-lookup"><span data-stu-id="764e6-140">Enable metadata exchange.</span></span>
   5. <span data-ttu-id="764e6-141">開啟服務主機來接聽內送訊息。</span><span class="sxs-lookup"><span data-stu-id="764e6-141">Open the service host to listen for incoming messages.</span></span>
  
<span data-ttu-id="764e6-142">程式碼進行下列變更：</span><span class="sxs-lookup"><span data-stu-id="764e6-142">Make the following changes to the code:</span></span>

1. <span data-ttu-id="764e6-143">開啟**Program.cs**或是**Module1.vb**中的檔案**GettingStartedHost**專案，並以下列程式碼取代其程式碼：</span><span class="sxs-lookup"><span data-stu-id="764e6-143">Open the **Program.cs** or **Module1.vb** file in the **GettingStartedHost** project and replace its code with the following code:</span></span>

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
    
    <span data-ttu-id="764e6-144">如需此程式碼的運作方式的資訊，請參閱[服務裝載程式步驟](#service-hosting-program-steps)。</span><span class="sxs-lookup"><span data-stu-id="764e6-144">For information about how this code works, see [Service hosting program steps](#service-hosting-program-steps).</span></span>


2. <span data-ttu-id="764e6-145">更新專案屬性：</span><span class="sxs-lookup"><span data-stu-id="764e6-145">Update the project properties:</span></span>

   1. <span data-ttu-id="764e6-146">在 **方案總管**視窗中，選取**GettingStartedHost**資料夾，然後再選取**屬性**從捷徑功能表。</span><span class="sxs-lookup"><span data-stu-id="764e6-146">In the **Solution Explorer** window, select the **GettingStartedHost** folder, and then select **Properties** from the shortcut menu.</span></span>

   2. <span data-ttu-id="764e6-147">在 [ **GettingStartedHost**屬性頁面上，選取**應用程式**] 索引標籤：</span><span class="sxs-lookup"><span data-stu-id="764e6-147">On the **GettingStartedHost** properties page, select the **Application** tab:</span></span>

      - <span data-ttu-id="764e6-148">針對C#專案中，選取**GettingStartedHost.Program**從**啟始物件**清單。</span><span class="sxs-lookup"><span data-stu-id="764e6-148">For C# projects, select **GettingStartedHost.Program** from the **Startup object** list.</span></span>

      - <span data-ttu-id="764e6-149">針對 Visual Basic 專案中，選取**Service.Program**從**啟始物件**清單。</span><span class="sxs-lookup"><span data-stu-id="764e6-149">For Visual Basic projects, select **Service.Program** from the **Startup object** list.</span></span>

   3. <span data-ttu-id="764e6-150">從**檔案**功能表上，選取**全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="764e6-150">From the **File** menu, select **Save All**.</span></span>


## <a name="verify-the-service-is-working"></a><span data-ttu-id="764e6-151">確認服務正常運作</span><span class="sxs-lookup"><span data-stu-id="764e6-151">Verify the service is working</span></span>

1. <span data-ttu-id="764e6-152">建置方案，然後再執行**GettingStartedHost**主控台應用程式在 Visual Studio 內從。</span><span class="sxs-lookup"><span data-stu-id="764e6-152">Build the solution, and then run the **GettingStartedHost** console application from inside Visual Studio.</span></span> 

    <span data-ttu-id="764e6-153">服務必須以系統管理員權限執行。</span><span class="sxs-lookup"><span data-stu-id="764e6-153">The service must be run with administrator privileges.</span></span> <span data-ttu-id="764e6-154">當您執行時，系統管理員權限，以開啟 Visual Studio **GettingStartedHost**在 Visual Studio 中，應用程式執行系統管理員權限。</span><span class="sxs-lookup"><span data-stu-id="764e6-154">Because you opened Visual Studio with administrator privileges, when you run **GettingStartedHost** in Visual Studio, the application is run with administrator privileges as well.</span></span> <span data-ttu-id="764e6-155">或者，您可以開啟新的命令提示字元，以系統管理員身分 (選取**更多** > **系統管理員身分執行**從快顯功能表) 並執行**GettingStartedHost.exe**其內。</span><span class="sxs-lookup"><span data-stu-id="764e6-155">As an alternative, you can open a new command prompt as an administrator (select **More** > **Run as administrator** from the shortcut menu) and run **GettingStartedHost.exe** within it.</span></span>

2. <span data-ttu-id="764e6-156">開啟網頁瀏覽器並瀏覽至服務的頁面在`http://localhost:8000/GettingStarted/CalculatorService`。</span><span class="sxs-lookup"><span data-stu-id="764e6-156">Open a web browser and browse to the service's page at `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>
   
   > [!NOTE]
   > <span data-ttu-id="764e6-157">此類服務需要在接聽的機器上的 HTTP 位址註冊適當的權限。</span><span class="sxs-lookup"><span data-stu-id="764e6-157">Services such as this one require the proper permission to register HTTP addresses on the machine for listening.</span></span> <span data-ttu-id="764e6-158">系統管理員帳戶具有此權限，但是非系統管理員帳戶則必須被授與 HTTP 命名空間的權限。</span><span class="sxs-lookup"><span data-stu-id="764e6-158">Administrator accounts have this permission, but non-administrator accounts must be granted permission for HTTP namespaces.</span></span> <span data-ttu-id="764e6-159">如需如何設定命名空間保留的詳細資訊，請參閱[設定 HTTP 和 HTTPS](feature-details/configuring-http-and-https.md)。</span><span class="sxs-lookup"><span data-stu-id="764e6-159">For more information about how to configure namespace reservations, see [Configuring HTTP and HTTPS](feature-details/configuring-http-and-https.md).</span></span> 


## <a name="service-hosting-program-steps"></a><span data-ttu-id="764e6-160">服務裝載程式步驟</span><span class="sxs-lookup"><span data-stu-id="764e6-160">Service hosting program steps</span></span>

<span data-ttu-id="764e6-161">您新增至主機服務的描述，如下所示的程式碼中的步驟：</span><span class="sxs-lookup"><span data-stu-id="764e6-161">The steps in the code you added to host the service are described as follows:</span></span>

- <span data-ttu-id="764e6-162">**步驟 1**:建立的執行個體`Uri`類別，以維持服務的基底位址。</span><span class="sxs-lookup"><span data-stu-id="764e6-162">**Step 1**: Create an instance of the `Uri` class to hold the base address of the service.</span></span> <span data-ttu-id="764e6-163">包含基底位址的 URL 包含選擇性 URI 識別服務。</span><span class="sxs-lookup"><span data-stu-id="764e6-163">A URL that contains a base address has an optional URI that identifies a service.</span></span> <span data-ttu-id="764e6-164">基底地址的格式如下： `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>`。</span><span class="sxs-lookup"><span data-stu-id="764e6-164">The base address is formatted as follows: `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>`.</span></span> <span data-ttu-id="764e6-165">HTTP 傳輸、 localhost、 連接埠 8000 和 URI 區段 GettingStarted，則會使用計算機服務的基底位址。</span><span class="sxs-lookup"><span data-stu-id="764e6-165">The base address for the calculator service uses the HTTP transport, localhost, port 8000, and the URI segment, GettingStarted.</span></span>

- <span data-ttu-id="764e6-166">**步驟 2**:建立的執行個體<xref:System.ServiceModel.ServiceHost>類別，用來裝載服務。</span><span class="sxs-lookup"><span data-stu-id="764e6-166">**Step 2**: Create an instance of the <xref:System.ServiceModel.ServiceHost> class, which you use to host the service.</span></span> <span data-ttu-id="764e6-167">建構函式接受兩個參數： 實作服務合約與基底位址的服務類別的型別。</span><span class="sxs-lookup"><span data-stu-id="764e6-167">The constructor takes two parameters: the type of the class that implements the service contract and the base address of the service.</span></span>

- <span data-ttu-id="764e6-168">**步驟 3**:建立 <xref:System.ServiceModel.Description.ServiceEndpoint> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="764e6-168">**Step 3**: Create a <xref:System.ServiceModel.Description.ServiceEndpoint> instance.</span></span> <span data-ttu-id="764e6-169">服務端點是由位址、繫結和服務合約所組成。</span><span class="sxs-lookup"><span data-stu-id="764e6-169">A service endpoint is composed of an address, a binding, and a service contract.</span></span> <span data-ttu-id="764e6-170"><xref:System.ServiceModel.Description.ServiceEndpoint>建構函式組成服務合約介面型別、 繫結和位址。</span><span class="sxs-lookup"><span data-stu-id="764e6-170">The <xref:System.ServiceModel.Description.ServiceEndpoint> constructor is composed of the service contract interface type, a binding, and an address.</span></span> <span data-ttu-id="764e6-171">服務合約是您在服務類型中所定義和實作的 `ICalculator`。</span><span class="sxs-lookup"><span data-stu-id="764e6-171">The service contract is `ICalculator`, which you defined and implement in the service type.</span></span> <span data-ttu-id="764e6-172">此範例中的繫結是<xref:System.ServiceModel.WSHttpBinding>，這是內建繫結並連接到端點符合 WS-\* 規格。</span><span class="sxs-lookup"><span data-stu-id="764e6-172">The binding for this sample is <xref:System.ServiceModel.WSHttpBinding>, which is a built-in binding and connects to endpoints that conform to the WS-\* specifications.</span></span> <span data-ttu-id="764e6-173">如需有關 WCF 繫結的詳細資訊，請參閱 < [WCF 繫結概觀](bindings-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="764e6-173">For more information about WCF bindings, see [WCF bindings overview](bindings-overview.md).</span></span> <span data-ttu-id="764e6-174">您附加至基底位址以識別端點的位址。</span><span class="sxs-lookup"><span data-stu-id="764e6-174">You append the address to the base address to identify the endpoint.</span></span> <span data-ttu-id="764e6-175">程式碼會指定位址 CalculatorService 以及做為端點的完整的位址`http://localhost:8000/GettingStarted/CalculatorService`。</span><span class="sxs-lookup"><span data-stu-id="764e6-175">The code specifies the address as CalculatorService and the fully qualified address for the endpoint as `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="764e6-176">.NET Framework 第 4 版和更新版本，新增服務端點是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="764e6-176">For .NET Framework Version 4 and later, adding a service endpoint is optional.</span></span> <span data-ttu-id="764e6-177">如需這些版本中，如果您未新增您的程式碼或組態中，WCF 會加入一個預設端點，每個組合的基底位址和服務所實作的合約。</span><span class="sxs-lookup"><span data-stu-id="764e6-177">For these versions, if you don't add your code or configuration, WCF adds one default endpoint for each combination of base address and contract implemented by the service.</span></span> <span data-ttu-id="764e6-178">如需有關預設端點的詳細資訊，請參閱 <<c0> [ 指定端點位址](specifying-an-endpoint-address.md)。</span><span class="sxs-lookup"><span data-stu-id="764e6-178">For more information about default endpoints, see [Specifying an endpoint address](specifying-an-endpoint-address.md).</span></span> <span data-ttu-id="764e6-179">如需有關預設端點、 繫結和行為的詳細資訊，請參閱 <<c0> [ 經過簡化的組態](simplified-configuration.md)並[WCF 服務的簡化組態](samples/simplified-configuration-for-wcf-services.md)。</span><span class="sxs-lookup"><span data-stu-id="764e6-179">For more information about default endpoints, bindings, and behaviors, see [Simplified configuration](simplified-configuration.md) and [Simplified configuration for WCF services](samples/simplified-configuration-for-wcf-services.md).</span></span>

- <span data-ttu-id="764e6-180">**步驟 4**:啟用中繼資料交換。</span><span class="sxs-lookup"><span data-stu-id="764e6-180">**Step 4**: Enable metadata exchange.</span></span> <span data-ttu-id="764e6-181">用戶端會使用中繼資料交換來產生 proxy 呼叫服務作業。</span><span class="sxs-lookup"><span data-stu-id="764e6-181">Clients use metadata exchange to generate proxies for calling the service operations.</span></span> <span data-ttu-id="764e6-182">若要啟用中繼資料交換，建立<xref:System.ServiceModel.Description.ServiceMetadataBehavior>執行個體、 將其<xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled>屬性設`true`，並新增`ServiceMetadataBehavior`物件<xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A>集合<xref:System.ServiceModel.ServiceHost>執行個體。</span><span class="sxs-lookup"><span data-stu-id="764e6-182">To enable metadata exchange, create a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance, set its <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled> property to `true`, and add the `ServiceMetadataBehavior` object to the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> collection of the <xref:System.ServiceModel.ServiceHost> instance.</span></span>

- <span data-ttu-id="764e6-183">**步驟 5**:開啟<xref:System.ServiceModel.ServiceHost>來接聽內送訊息。</span><span class="sxs-lookup"><span data-stu-id="764e6-183">**Step 5**: Open <xref:System.ServiceModel.ServiceHost> to listen for incoming messages.</span></span> <span data-ttu-id="764e6-184">應用程式會等候您按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="764e6-184">The application waits for you to press **Enter**.</span></span> <span data-ttu-id="764e6-185">應用程式具現化之後<xref:System.ServiceModel.ServiceHost>，它會執行 try/catch 區塊。</span><span class="sxs-lookup"><span data-stu-id="764e6-185">After the application instantiates <xref:System.ServiceModel.ServiceHost>, it executes a try/catch block.</span></span> <span data-ttu-id="764e6-186">如需安全攔截擲回例外狀況的詳細資訊<xref:System.ServiceModel.ServiceHost>，請參閱 <<c2> [ 使用關閉和中止發行 WCF 用戶端資源](samples/use-close-abort-release-wcf-client-resources.md)。</span><span class="sxs-lookup"><span data-stu-id="764e6-186">For more information about safely catching exceptions thrown by <xref:System.ServiceModel.ServiceHost>, see [Use Close and Abort to release WCF client resources](samples/use-close-abort-release-wcf-client-resources.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="764e6-187">當您新增的 WCF 服務程式庫時，Visual Studio 裝載它，如果您啟動服務主機來偵錯。</span><span class="sxs-lookup"><span data-stu-id="764e6-187">When you add a WCF service library, Visual Studio hosts it for you if you debug it by starting a service host.</span></span> <span data-ttu-id="764e6-188">若要避免衝突，您可以防止 Visual Studio 裝載 WCF 服務程式庫。</span><span class="sxs-lookup"><span data-stu-id="764e6-188">To avoid conflicts, you can prevent Visual Studio from hosting the WCF service library.</span></span> 
> 1. <span data-ttu-id="764e6-189">選取  **GettingStartedLib**專案中**方案總管**，然後選擇 **屬性**從捷徑功能表。</span><span class="sxs-lookup"><span data-stu-id="764e6-189">Select the **GettingStartedLib** project in **Solution Explorer** and choose **Properties** from the shortcut menu.</span></span>
> 2. <span data-ttu-id="764e6-190">選取  **WCF 選項**並取消核取**啟動 WCF 服務主機時相同的方案中的另一個專案進行偵錯**。</span><span class="sxs-lookup"><span data-stu-id="764e6-190">Select **WCF Options** and uncheck **Start WCF Service Host when debugging another project in the same solution**.</span></span>


## <a name="next-steps"></a><span data-ttu-id="764e6-191">後續步驟</span><span class="sxs-lookup"><span data-stu-id="764e6-191">Next steps</span></span>

<span data-ttu-id="764e6-192">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="764e6-192">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
> - <span data-ttu-id="764e6-193">建立及設定 WCF 服務裝載的主控台應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="764e6-193">Create and configure a console app project for hosting a WCF service.</span></span>
> - <span data-ttu-id="764e6-194">加入裝載 WCF 服務的程式碼。</span><span class="sxs-lookup"><span data-stu-id="764e6-194">Add code to host the WCF service.</span></span>
> - <span data-ttu-id="764e6-195">更新組態檔。</span><span class="sxs-lookup"><span data-stu-id="764e6-195">Update the configuration file.</span></span>
> - <span data-ttu-id="764e6-196">啟動 WCF 服務，並確認它正在執行。</span><span class="sxs-lookup"><span data-stu-id="764e6-196">Start the WCF service and verify it's running.</span></span>

<span data-ttu-id="764e6-197">請前進到下一個教學課程，以了解如何建立 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="764e6-197">Advance to the next tutorial to learn how to create a WCF client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="764e6-198">教學課程：建立 WCF 用戶端</span><span class="sxs-lookup"><span data-stu-id="764e6-198">Tutorial: Create a WCF client</span></span>](how-to-create-a-wcf-client.md)
