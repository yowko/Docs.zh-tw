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
# <a name="tutorial-host-and-run-a-basic-windows-communication-foundation-service"></a><span data-ttu-id="4a952-102">教學課程：裝載和執行基本 Windows Communication Foundation 服務</span><span class="sxs-lookup"><span data-stu-id="4a952-102">Tutorial: Host and run a basic Windows Communication Foundation service</span></span>

<span data-ttu-id="4a952-103">本教學課程說明建立基本 Windows Communication Foundation （WCF）應用程式所需的五個工作中的第三個。</span><span class="sxs-lookup"><span data-stu-id="4a952-103">This tutorial describes the third of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="4a952-104">如需教學課程的總覽，請[參閱教學課程：Windows Communication Foundation 應用程式](getting-started-tutorial.md)入門。</span><span class="sxs-lookup"><span data-stu-id="4a952-104">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="4a952-105">建立 WCF 應用程式的下一個工作是在主控台應用程式中裝載 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="4a952-105">The next task for creating a WCF application is to host a WCF service in a console application.</span></span> <span data-ttu-id="4a952-106">WCF 服務會公開一或多個端點，其中每個*端點*都會公開一個或多個服務作業。</span><span class="sxs-lookup"><span data-stu-id="4a952-106">A WCF service exposes one or more *endpoints*, each of which exposes one or more service operations.</span></span> <span data-ttu-id="4a952-107">服務端點會指定下列資訊：</span><span class="sxs-lookup"><span data-stu-id="4a952-107">A service endpoint specifies the following information:</span></span>

- <span data-ttu-id="4a952-108">您可以在其中找到服務的位址。</span><span class="sxs-lookup"><span data-stu-id="4a952-108">An address where you can find the service.</span></span>
- <span data-ttu-id="4a952-109">系結，其中包含描述用戶端必須如何與服務通訊的資訊。</span><span class="sxs-lookup"><span data-stu-id="4a952-109">A binding that contains the information that describes how a client must communicate with the service.</span></span> 
- <span data-ttu-id="4a952-110">定義服務提供給其用戶端之功能的合約。</span><span class="sxs-lookup"><span data-stu-id="4a952-110">A contract that defines the functionality that the service provides to its clients.</span></span>

<span data-ttu-id="4a952-111">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="4a952-111">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="4a952-112">建立和設定主控台應用程式專案來裝載 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="4a952-112">Create and configure a console app project for hosting a WCF service.</span></span>
> - <span data-ttu-id="4a952-113">加入程式碼來裝載 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="4a952-113">Add code to host the WCF service.</span></span>
> - <span data-ttu-id="4a952-114">更新設定檔。</span><span class="sxs-lookup"><span data-stu-id="4a952-114">Update the configuration file.</span></span>
> - <span data-ttu-id="4a952-115">啟動 WCF 服務，並確認它正在執行。</span><span class="sxs-lookup"><span data-stu-id="4a952-115">Start the WCF service and verify it's running.</span></span>

## <a name="create-and-configure-a-console-app-project-for-hosting-the-service"></a><span data-ttu-id="4a952-116">建立和設定主控台應用程式專案以裝載服務</span><span class="sxs-lookup"><span data-stu-id="4a952-116">Create and configure a console app project for hosting the service</span></span>

1. <span data-ttu-id="4a952-117">在 Visual Studio 中建立主控台應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="4a952-117">Create a console app project in Visual Studio:</span></span> 
 
    1. <span data-ttu-id="4a952-118">從 [**檔案] 功能表中，選取 [** **開啟** > **專案/方案**]，然後流覽至您先前建立的**GettingStarted**方案（*GettingStarted*）。</span><span class="sxs-lookup"><span data-stu-id="4a952-118">From the **File** menu, select **Open** > **Project/Solution** and browse to the **GettingStarted** solution you previously created (*GettingStarted.sln*).</span></span> <span data-ttu-id="4a952-119">選取 [開啟]。</span><span class="sxs-lookup"><span data-stu-id="4a952-119">Select **Open**.</span></span>

    2. <span data-ttu-id="4a952-120">從 [ **View** ] 功能表中，選取 [**方案總管**]。</span><span class="sxs-lookup"><span data-stu-id="4a952-120">From the **View** menu, select **Solution Explorer**.</span></span>
    
    3. <span data-ttu-id="4a952-121">在 [**方案總管**] 視窗中，選取 [ **GettingStarted** ] 解決方案（最上層節點），然後從快捷方式功能表選取 [**加入** > **新專案**]。</span><span class="sxs-lookup"><span data-stu-id="4a952-121">In the **Solution Explorer** window, select the **GettingStarted** solution (top node), and then select **Add** > **New Project** from the shortcut menu.</span></span> 

    4. <span data-ttu-id="4a952-122">在左側的 [**加入新專案**] 視窗中，選取 [  **C#視覺效果**] 或 [ **Visual Basic**] 底下的 [ **Windows 桌面**] 類別。</span><span class="sxs-lookup"><span data-stu-id="4a952-122">In the **Add New Project** window, on the left side, select the **Windows Desktop** category under **Visual C#** or **Visual Basic**.</span></span> 

    5. <span data-ttu-id="4a952-123">選取 [**主控台應用程式（.NET Framework）** ] 範本，然後在 [**名稱**] 中輸入*GettingStartedHost* 。</span><span class="sxs-lookup"><span data-stu-id="4a952-123">Select the **Console App (.NET Framework)** template, and enter *GettingStartedHost* for the **Name**.</span></span> <span data-ttu-id="4a952-124">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="4a952-124">Select **OK**.</span></span>

2. <span data-ttu-id="4a952-125">將**GettingStartedHost**專案中的參考新增至**GettingStartedLib**專案：</span><span class="sxs-lookup"><span data-stu-id="4a952-125">Add a reference in the **GettingStartedHost** project to the **GettingStartedLib** project:</span></span> 

    1. <span data-ttu-id="4a952-126">在 [**方案總管**] 視窗中，選取 [ **GettingStartedHost** ] 專案底下的 [**參考**] 資料夾，然後從快捷方式功能表選取 [**加入參考**]。</span><span class="sxs-lookup"><span data-stu-id="4a952-126">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedHost** project, and then select **Add Reference** from the shortcut menu.</span></span> 

    2. <span data-ttu-id="4a952-127">在 [**加入參考**] 對話方塊中，于視窗左側的 [**專案**] 底下，選取 [**方案**]。</span><span class="sxs-lookup"><span data-stu-id="4a952-127">In the **Add Reference** dialog, under **Projects** on the left side of the window, select **Solution**.</span></span> 
 
    3. <span data-ttu-id="4a952-128">在視窗的中間區段中選取 [ **GettingStartedLib** ]，然後選取 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="4a952-128">Select **GettingStartedLib** in the center section of the window, and then select **OK**.</span></span> 

       <span data-ttu-id="4a952-129">此動作會讓**GettingStartedLib**專案中定義的類型可供**GettingStartedHost**專案使用。</span><span class="sxs-lookup"><span data-stu-id="4a952-129">This action makes the types defined in the **GettingStartedLib** project available to the **GettingStartedHost** project.</span></span>

3. <span data-ttu-id="4a952-130">將**GettingStartedHost**專案中的參考新增至<xref:System.ServiceModel>元件：</span><span class="sxs-lookup"><span data-stu-id="4a952-130">Add a reference in the **GettingStartedHost** project to the <xref:System.ServiceModel> assembly:</span></span> 

    1. <span data-ttu-id="4a952-131">在 [**方案總管**] 視窗中，選取 [ **GettingStartedHost** ] 專案底下的 [**參考**] 資料夾，然後從快捷方式功能表選取 [**加入參考**]。</span><span class="sxs-lookup"><span data-stu-id="4a952-131">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedHost** project, and then select **Add Reference** from the shortcut menu.</span></span>
    
    2. <span data-ttu-id="4a952-132">在 [**加入參考**] 視窗中，于視窗左側的 [**元件**] 底下，選取 [**架構**]。</span><span class="sxs-lookup"><span data-stu-id="4a952-132">In the **Add Reference** window, under **Assemblies** on the left side of the window, select **Framework**.</span></span> 

    3. <span data-ttu-id="4a952-133">選取 [ **System.servicemodel**]，然後選取 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="4a952-133">Select **System.ServiceModel**, and then select **OK**.</span></span> 
    
    4. <span data-ttu-id="4a952-134">選取 > [檔案] [**全部儲存**]**以儲存方案**。</span><span class="sxs-lookup"><span data-stu-id="4a952-134">Save the solution by selecting **File** > **Save All**.</span></span>

## <a name="add-code-to-host-the-service"></a><span data-ttu-id="4a952-135">新增程式碼以裝載服務</span><span class="sxs-lookup"><span data-stu-id="4a952-135">Add code to host the service</span></span>

<span data-ttu-id="4a952-136">若要裝載服務，您可以新增程式碼來執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="4a952-136">To host the service, you add code to do the following steps:</span></span> 

1. <span data-ttu-id="4a952-137">建立基底位址的 URI。</span><span class="sxs-lookup"><span data-stu-id="4a952-137">Create a URI for the base address.</span></span>
2. <span data-ttu-id="4a952-138">建立用來裝載服務的類別實例。</span><span class="sxs-lookup"><span data-stu-id="4a952-138">Create a class instance for hosting the service.</span></span>
3. <span data-ttu-id="4a952-139">建立服務端點。</span><span class="sxs-lookup"><span data-stu-id="4a952-139">Create a service endpoint.</span></span>
4. <span data-ttu-id="4a952-140">啟用中繼資料交換。</span><span class="sxs-lookup"><span data-stu-id="4a952-140">Enable metadata exchange.</span></span>
5. <span data-ttu-id="4a952-141">開啟服務主機以接聽傳入訊息。</span><span class="sxs-lookup"><span data-stu-id="4a952-141">Open the service host to listen for incoming messages.</span></span>
  
<span data-ttu-id="4a952-142">對程式碼進行下列變更:</span><span class="sxs-lookup"><span data-stu-id="4a952-142">Make the following changes to the code:</span></span>

1. <span data-ttu-id="4a952-143">開啟**GettingStartedHost**專案中的**Program.cs**或**Module1**檔案，並以下列程式碼取代其程式碼：</span><span class="sxs-lookup"><span data-stu-id="4a952-143">Open the **Program.cs** or **Module1.vb** file in the **GettingStartedHost** project and replace its code with the following code:</span></span>

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
    
    <span data-ttu-id="4a952-144">如需有關此程式碼如何運作的詳細資訊，請參閱[服務裝載程式步驟](#service-hosting-program-steps)。</span><span class="sxs-lookup"><span data-stu-id="4a952-144">For information about how this code works, see [Service hosting program steps](#service-hosting-program-steps).</span></span>

2. <span data-ttu-id="4a952-145">更新專案屬性：</span><span class="sxs-lookup"><span data-stu-id="4a952-145">Update the project properties:</span></span>

   1. <span data-ttu-id="4a952-146">在 [**方案總管**] 視窗中，選取 [ **GettingStartedHost** ] 資料夾，然後從快捷方式功能表選取 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="4a952-146">In the **Solution Explorer** window, select the **GettingStartedHost** folder, and then select **Properties** from the shortcut menu.</span></span>

   2. <span data-ttu-id="4a952-147">在 [ **GettingStartedHost**屬性] 頁面上，選取 [**應用程式**] 索引標籤：</span><span class="sxs-lookup"><span data-stu-id="4a952-147">On the **GettingStartedHost** properties page, select the **Application** tab:</span></span>

      - <span data-ttu-id="4a952-148">針對C# [專案]，從 [**啟始物件**] 清單中選取 [ **GettingStartedHost** ]。</span><span class="sxs-lookup"><span data-stu-id="4a952-148">For C# projects, select **GettingStartedHost.Program** from the **Startup object** list.</span></span>

      - <span data-ttu-id="4a952-149">針對 Visual Basic 專案，從 [**啟始物件**] 清單中選取 [**服務**]。</span><span class="sxs-lookup"><span data-stu-id="4a952-149">For Visual Basic projects, select **Service.Program** from the **Startup object** list.</span></span>

   3. <span data-ttu-id="4a952-150">從 [**檔案**] 功能表中，選取 [**全部儲存**]。</span><span class="sxs-lookup"><span data-stu-id="4a952-150">From the **File** menu, select **Save All**.</span></span>

## <a name="verify-the-service-is-working"></a><span data-ttu-id="4a952-151">確認服務正在運作</span><span class="sxs-lookup"><span data-stu-id="4a952-151">Verify the service is working</span></span>

1. <span data-ttu-id="4a952-152">建立解決方案，然後從 Visual Studio 內執行**GettingStartedHost**主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="4a952-152">Build the solution, and then run the **GettingStartedHost** console application from inside Visual Studio.</span></span> 

    <span data-ttu-id="4a952-153">服務必須以系統管理員許可權執行。</span><span class="sxs-lookup"><span data-stu-id="4a952-153">The service must be run with administrator privileges.</span></span> <span data-ttu-id="4a952-154">因為您以系統管理員許可權開啟 Visual Studio，所以當您在 Visual Studio 中執行**GettingStartedHost**時，應用程式也會以系統管理員許可權執行。</span><span class="sxs-lookup"><span data-stu-id="4a952-154">Because you opened Visual Studio with administrator privileges, when you run **GettingStartedHost** in Visual Studio, the application is run with administrator privileges as well.</span></span> <span data-ttu-id="4a952-155">或者，您可以系統管理員身分開啟新的命令提示字元（從快捷方式功能表選取 [**更多** > 以**系統管理員身分執行**]），然後在其中執行**GettingStartedHost** 。</span><span class="sxs-lookup"><span data-stu-id="4a952-155">As an alternative, you can open a new command prompt as an administrator (select **More** > **Run as administrator** from the shortcut menu) and run **GettingStartedHost.exe** within it.</span></span>

2. <span data-ttu-id="4a952-156">開啟網頁瀏覽器，並流覽至位於`http://localhost:8000/GettingStarted/CalculatorService`的服務頁面。</span><span class="sxs-lookup"><span data-stu-id="4a952-156">Open a web browser and browse to the service's page at `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>
   
   > [!NOTE]
   > <span data-ttu-id="4a952-157">這一類服務需要適當的許可權，才能在電腦上註冊 HTTP 位址以供接聽。</span><span class="sxs-lookup"><span data-stu-id="4a952-157">Services such as this one require the proper permission to register HTTP addresses on the machine for listening.</span></span> <span data-ttu-id="4a952-158">系統管理員帳戶具有此權限，但是非系統管理員帳戶則必須被授與 HTTP 命名空間的權限。</span><span class="sxs-lookup"><span data-stu-id="4a952-158">Administrator accounts have this permission, but non-administrator accounts must be granted permission for HTTP namespaces.</span></span> <span data-ttu-id="4a952-159">如需如何設定命名空間保留的詳細資訊，請參閱[設定 HTTP 和 HTTPS](feature-details/configuring-http-and-https.md)。</span><span class="sxs-lookup"><span data-stu-id="4a952-159">For more information about how to configure namespace reservations, see [Configuring HTTP and HTTPS](feature-details/configuring-http-and-https.md).</span></span> 

## <a name="service-hosting-program-steps"></a><span data-ttu-id="4a952-160">服務裝載程式步驟</span><span class="sxs-lookup"><span data-stu-id="4a952-160">Service hosting program steps</span></span>

<span data-ttu-id="4a952-161">您新增來裝載服務之程式碼中的步驟如下所述：</span><span class="sxs-lookup"><span data-stu-id="4a952-161">The steps in the code you added to host the service are described as follows:</span></span>

- <span data-ttu-id="4a952-162">**步驟 1**：建立`Uri`類別的實例，以保存服務的基底位址。</span><span class="sxs-lookup"><span data-stu-id="4a952-162">**Step 1**: Create an instance of the `Uri` class to hold the base address of the service.</span></span> <span data-ttu-id="4a952-163">包含基底位址的 URL 具有可識別服務的選擇性 URI。</span><span class="sxs-lookup"><span data-stu-id="4a952-163">A URL that contains a base address has an optional URI that identifies a service.</span></span> <span data-ttu-id="4a952-164">基底位址的格式如下： `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>`。</span><span class="sxs-lookup"><span data-stu-id="4a952-164">The base address is formatted as follows: `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>`.</span></span> <span data-ttu-id="4a952-165">計算機服務的基底位址會使用 HTTP 傳輸、localhost、埠8000和 URI 區段 GettingStarted。</span><span class="sxs-lookup"><span data-stu-id="4a952-165">The base address for the calculator service uses the HTTP transport, localhost, port 8000, and the URI segment, GettingStarted.</span></span>

- <span data-ttu-id="4a952-166">**步驟 2**：建立<xref:System.ServiceModel.ServiceHost>類別的實例，以用來裝載服務。</span><span class="sxs-lookup"><span data-stu-id="4a952-166">**Step 2**: Create an instance of the <xref:System.ServiceModel.ServiceHost> class, which you use to host the service.</span></span> <span data-ttu-id="4a952-167">此函式會採用兩個參數：實作為服務合約之類別的型別，以及服務的基底位址。</span><span class="sxs-lookup"><span data-stu-id="4a952-167">The constructor takes two parameters: the type of the class that implements the service contract and the base address of the service.</span></span>

- <span data-ttu-id="4a952-168">**步驟 3**：建立 <xref:System.ServiceModel.Description.ServiceEndpoint> 執行個體。</span><span class="sxs-lookup"><span data-stu-id="4a952-168">**Step 3**: Create a <xref:System.ServiceModel.Description.ServiceEndpoint> instance.</span></span> <span data-ttu-id="4a952-169">服務端點是由位址、繫結和服務合約所組成。</span><span class="sxs-lookup"><span data-stu-id="4a952-169">A service endpoint is composed of an address, a binding, and a service contract.</span></span> <span data-ttu-id="4a952-170">此<xref:System.ServiceModel.Description.ServiceEndpoint>函式是由服務合約介面型別、系結和位址所組成。</span><span class="sxs-lookup"><span data-stu-id="4a952-170">The <xref:System.ServiceModel.Description.ServiceEndpoint> constructor is composed of the service contract interface type, a binding, and an address.</span></span> <span data-ttu-id="4a952-171">服務合約是您在服務類型中所定義和實作的 `ICalculator`。</span><span class="sxs-lookup"><span data-stu-id="4a952-171">The service contract is `ICalculator`, which you defined and implement in the service type.</span></span> <span data-ttu-id="4a952-172">這個範例的系結是<xref:System.ServiceModel.WSHttpBinding>，它是內建的系結，並會連接到符合 WS-\* 規格的端點。</span><span class="sxs-lookup"><span data-stu-id="4a952-172">The binding for this sample is <xref:System.ServiceModel.WSHttpBinding>, which is a built-in binding and connects to endpoints that conform to the WS-\* specifications.</span></span> <span data-ttu-id="4a952-173">如需 WCF 系結的詳細資訊，請參閱 Wcf 系結[總覽](bindings-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="4a952-173">For more information about WCF bindings, see [WCF bindings overview](bindings-overview.md).</span></span> <span data-ttu-id="4a952-174">您會將位址附加至基底位址，以識別端點。</span><span class="sxs-lookup"><span data-stu-id="4a952-174">You append the address to the base address to identify the endpoint.</span></span> <span data-ttu-id="4a952-175">此程式碼會將位址指定為 CalculatorService，並將端點的完整位址`http://localhost:8000/GettingStarted/CalculatorService`指定為。</span><span class="sxs-lookup"><span data-stu-id="4a952-175">The code specifies the address as CalculatorService and the fully qualified address for the endpoint as `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="4a952-176">針對 .NET Framework 第4版和更新版本，新增服務端點是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="4a952-176">For .NET Framework Version 4 and later, adding a service endpoint is optional.</span></span> <span data-ttu-id="4a952-177">在這些版本中，如果您未新增程式碼或設定，WCF 會為服務所執行之每個基底位址和合約的組合加入一個預設端點。</span><span class="sxs-lookup"><span data-stu-id="4a952-177">For these versions, if you don't add your code or configuration, WCF adds one default endpoint for each combination of base address and contract implemented by the service.</span></span> <span data-ttu-id="4a952-178">如需預設端點的詳細資訊，請參閱[指定端點位址](specifying-an-endpoint-address.md)。</span><span class="sxs-lookup"><span data-stu-id="4a952-178">For more information about default endpoints, see [Specifying an endpoint address](specifying-an-endpoint-address.md).</span></span> <span data-ttu-id="4a952-179">如需預設端點、系結和行為的詳細資訊，請參閱[簡化](simplified-configuration.md)的設定和[WCF 服務的簡化](samples/simplified-configuration-for-wcf-services.md)設定。</span><span class="sxs-lookup"><span data-stu-id="4a952-179">For more information about default endpoints, bindings, and behaviors, see [Simplified configuration](simplified-configuration.md) and [Simplified configuration for WCF services](samples/simplified-configuration-for-wcf-services.md).</span></span>

- <span data-ttu-id="4a952-180">**步驟 4**：啟用中繼資料交換。</span><span class="sxs-lookup"><span data-stu-id="4a952-180">**Step 4**: Enable metadata exchange.</span></span> <span data-ttu-id="4a952-181">用戶端會使用中繼資料交換來產生 proxy，以呼叫服務作業。</span><span class="sxs-lookup"><span data-stu-id="4a952-181">Clients use metadata exchange to generate proxies for calling the service operations.</span></span> <span data-ttu-id="4a952-182">若要啟用中繼資料交換， <xref:System.ServiceModel.Description.ServiceMetadataBehavior>請建立實例， <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled>將其`true`屬性設定`ServiceMetadataBehavior`為，並<xref:System.ServiceModel.ServiceHost>將物件<xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A>加入至實例的集合。</span><span class="sxs-lookup"><span data-stu-id="4a952-182">To enable metadata exchange, create a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance, set its <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled> property to `true`, and add the `ServiceMetadataBehavior` object to the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> collection of the <xref:System.ServiceModel.ServiceHost> instance.</span></span>

- <span data-ttu-id="4a952-183">**步驟 5**：開啟<xref:System.ServiceModel.ServiceHost>以接聽傳入訊息。</span><span class="sxs-lookup"><span data-stu-id="4a952-183">**Step 5**: Open <xref:System.ServiceModel.ServiceHost> to listen for incoming messages.</span></span> <span data-ttu-id="4a952-184">應用程式會等候您按下**enter**鍵。</span><span class="sxs-lookup"><span data-stu-id="4a952-184">The application waits for you to press **Enter**.</span></span> <span data-ttu-id="4a952-185">在應用程式具<xref:System.ServiceModel.ServiceHost>現化之後，它會執行 try/catch 區塊。</span><span class="sxs-lookup"><span data-stu-id="4a952-185">After the application instantiates <xref:System.ServiceModel.ServiceHost>, it executes a try/catch block.</span></span> <span data-ttu-id="4a952-186">如需安全攔截所<xref:System.ServiceModel.ServiceHost>擲回之例外狀況的詳細資訊，請參閱[使用 Close 和 Abort 釋放 WCF 用戶端資源](samples/use-close-abort-release-wcf-client-resources.md)。</span><span class="sxs-lookup"><span data-stu-id="4a952-186">For more information about safely catching exceptions thrown by <xref:System.ServiceModel.ServiceHost>, see [Use Close and Abort to release WCF client resources](samples/use-close-abort-release-wcf-client-resources.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4a952-187">當您新增 WCF 服務程式庫時，如果您藉由啟動服務主機來進行偵錯工具，Visual Studio 會為您裝載它。</span><span class="sxs-lookup"><span data-stu-id="4a952-187">When you add a WCF service library, Visual Studio hosts it for you if you debug it by starting a service host.</span></span> <span data-ttu-id="4a952-188">若要避免衝突，您可以防止 Visual Studio 裝載 WCF 服務程式庫。</span><span class="sxs-lookup"><span data-stu-id="4a952-188">To avoid conflicts, you can prevent Visual Studio from hosting the WCF service library.</span></span> 
>
> 1. <span data-ttu-id="4a952-189">在**方案總管**中選取 [ **GettingStartedLib** ] 專案，然後從快捷方式功能表中選擇 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="4a952-189">Select the **GettingStartedLib** project in **Solution Explorer** and choose **Properties** from the shortcut menu.</span></span>
> 2. <span data-ttu-id="4a952-190">選取 [ **WCF 選項**]，然後取消核取**相同方案中的另一個專案時，啟動 WCF 服務主機**。</span><span class="sxs-lookup"><span data-stu-id="4a952-190">Select **WCF Options** and uncheck **Start WCF Service Host when debugging another project in the same solution**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4a952-191">後續步驟</span><span class="sxs-lookup"><span data-stu-id="4a952-191">Next steps</span></span>

<span data-ttu-id="4a952-192">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="4a952-192">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="4a952-193">建立和設定主控台應用程式專案來裝載 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="4a952-193">Create and configure a console app project for hosting a WCF service.</span></span>
> - <span data-ttu-id="4a952-194">加入程式碼來裝載 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="4a952-194">Add code to host the WCF service.</span></span>
> - <span data-ttu-id="4a952-195">更新設定檔。</span><span class="sxs-lookup"><span data-stu-id="4a952-195">Update the configuration file.</span></span>
> - <span data-ttu-id="4a952-196">啟動 WCF 服務，並確認它正在執行。</span><span class="sxs-lookup"><span data-stu-id="4a952-196">Start the WCF service and verify it's running.</span></span>

<span data-ttu-id="4a952-197">請前進到下一個教學課程，以瞭解如何建立 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="4a952-197">Advance to the next tutorial to learn how to create a WCF client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4a952-198">教學課程：建立 WCF 用戶端</span><span class="sxs-lookup"><span data-stu-id="4a952-198">Tutorial: Create a WCF client</span></span>](how-to-create-a-wcf-client.md)
