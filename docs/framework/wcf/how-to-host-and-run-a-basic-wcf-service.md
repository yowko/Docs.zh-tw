---
title: 教學課程：裝載和執行基本 Windows Communication Foundation 服務
description: 瞭解如何在主控台應用程式中裝載 WCF 服務，做為一系列文章的一部分，協助您開始建立 WCF 應用程式。
ms.date: 03/19/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
ms.openlocfilehash: 5318991087e71430523681d601d3b38c4513027b
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246125"
---
# <a name="tutorial-host-and-run-a-basic-windows-communication-foundation-service"></a><span data-ttu-id="57b71-103">教學課程：裝載和執行基本 Windows Communication Foundation 服務</span><span class="sxs-lookup"><span data-stu-id="57b71-103">Tutorial: Host and run a basic Windows Communication Foundation service</span></span>

<span data-ttu-id="57b71-104">本教學課程說明建立基本 Windows Communication Foundation （WCF）應用程式所需的五個工作中的第三個。</span><span class="sxs-lookup"><span data-stu-id="57b71-104">This tutorial describes the third of five tasks required to create a basic Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="57b71-105">如需教學課程的總覽，請參閱[教學課程：開始使用 Windows Communication Foundation 應用程式](getting-started-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="57b71-105">For an overview of the tutorials, see [Tutorial: Get started with Windows Communication Foundation applications](getting-started-tutorial.md).</span></span>

<span data-ttu-id="57b71-106">建立 WCF 應用程式的下一個工作是在主控台應用程式中裝載 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="57b71-106">The next task for creating a WCF application is to host a WCF service in a console application.</span></span> <span data-ttu-id="57b71-107">WCF 服務會公開一或多個端點，其中每個*端點*都會公開一個或多個服務作業。</span><span class="sxs-lookup"><span data-stu-id="57b71-107">A WCF service exposes one or more *endpoints*, each of which exposes one or more service operations.</span></span> <span data-ttu-id="57b71-108">服務端點會指定下列資訊：</span><span class="sxs-lookup"><span data-stu-id="57b71-108">A service endpoint specifies the following information:</span></span>

- <span data-ttu-id="57b71-109">您可以在其中找到服務的位址。</span><span class="sxs-lookup"><span data-stu-id="57b71-109">An address where you can find the service.</span></span>
- <span data-ttu-id="57b71-110">系結，其中包含描述用戶端必須如何與服務通訊的資訊。</span><span class="sxs-lookup"><span data-stu-id="57b71-110">A binding that contains the information that describes how a client must communicate with the service.</span></span>
- <span data-ttu-id="57b71-111">定義服務提供給其用戶端之功能的合約。</span><span class="sxs-lookup"><span data-stu-id="57b71-111">A contract that defines the functionality that the service provides to its clients.</span></span>

<span data-ttu-id="57b71-112">在本教學課程中，您會了解如何：</span><span class="sxs-lookup"><span data-stu-id="57b71-112">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="57b71-113">建立和設定主控台應用程式專案來裝載 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="57b71-113">Create and configure a console app project for hosting a WCF service.</span></span>
> - <span data-ttu-id="57b71-114">加入程式碼來裝載 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="57b71-114">Add code to host the WCF service.</span></span>
> - <span data-ttu-id="57b71-115">更新設定檔。</span><span class="sxs-lookup"><span data-stu-id="57b71-115">Update the configuration file.</span></span>
> - <span data-ttu-id="57b71-116">啟動 WCF 服務，並確認它正在執行。</span><span class="sxs-lookup"><span data-stu-id="57b71-116">Start the WCF service and verify it's running.</span></span>

## <a name="create-and-configure-a-console-app-project-for-hosting-the-service"></a><span data-ttu-id="57b71-117">建立和設定主控台應用程式專案以裝載服務</span><span class="sxs-lookup"><span data-stu-id="57b71-117">Create and configure a console app project for hosting the service</span></span>

1. <span data-ttu-id="57b71-118">在 Visual Studio 中建立主控台應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="57b71-118">Create a console app project in Visual Studio:</span></span>

    1. <span data-ttu-id="57b71-119">從 [檔案]**功能表中，選取 [** **開啟**  >  **專案/方案**]，然後流覽至您先前建立的**GettingStarted**方案（*GettingStarted*）。</span><span class="sxs-lookup"><span data-stu-id="57b71-119">From the **File** menu, select **Open** > **Project/Solution** and browse to the **GettingStarted** solution you previously created (*GettingStarted.sln*).</span></span> <span data-ttu-id="57b71-120">選取 [開啟] 。</span><span class="sxs-lookup"><span data-stu-id="57b71-120">Select **Open**.</span></span>

    2. <span data-ttu-id="57b71-121">從 [ **View** ] 功能表中，選取 [**方案總管**]。</span><span class="sxs-lookup"><span data-stu-id="57b71-121">From the **View** menu, select **Solution Explorer**.</span></span>

    3. <span data-ttu-id="57b71-122">在 [**方案總管**] 視窗中，選取 [ **GettingStarted** ] 解決方案（最上層節點），然後從快捷方式功能表選取 [**加入**  >  **新專案**]。</span><span class="sxs-lookup"><span data-stu-id="57b71-122">In the **Solution Explorer** window, select the **GettingStarted** solution (top node), and then select **Add** > **New Project** from the shortcut menu.</span></span>

    4. <span data-ttu-id="57b71-123">在 [**加入新專案**] 視窗的左側，選取 [ **Visual c #** ] 或 [ **Visual Basic**] 底下的 [ **Windows 桌面**] 類別。</span><span class="sxs-lookup"><span data-stu-id="57b71-123">In the **Add New Project** window, on the left side, select the **Windows Desktop** category under **Visual C#** or **Visual Basic**.</span></span>

    5. <span data-ttu-id="57b71-124">選取 [**主控台應用程式（.NET Framework）** ] 範本，然後在 [**名稱**] 中輸入*GettingStartedHost* 。</span><span class="sxs-lookup"><span data-stu-id="57b71-124">Select the **Console App (.NET Framework)** template, and enter *GettingStartedHost* for the **Name**.</span></span> <span data-ttu-id="57b71-125">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="57b71-125">Select **OK**.</span></span>

2. <span data-ttu-id="57b71-126">將**GettingStartedHost**專案中的參考新增至**GettingStartedLib**專案：</span><span class="sxs-lookup"><span data-stu-id="57b71-126">Add a reference in the **GettingStartedHost** project to the **GettingStartedLib** project:</span></span>

    1. <span data-ttu-id="57b71-127">在 [**方案總管**] 視窗中，選取 [ **GettingStartedHost** ] 專案底下的 [**參考**] 資料夾，然後從快捷方式功能表選取 [**加入參考**]。</span><span class="sxs-lookup"><span data-stu-id="57b71-127">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedHost** project, and then select **Add Reference** from the shortcut menu.</span></span>

    2. <span data-ttu-id="57b71-128">在 [**加入參考**] 對話方塊中，于視窗左側的 [**專案**] 底下，選取 [**方案**]。</span><span class="sxs-lookup"><span data-stu-id="57b71-128">In the **Add Reference** dialog, under **Projects** on the left side of the window, select **Solution**.</span></span>

    3. <span data-ttu-id="57b71-129">在視窗的中間區段中選取 [ **GettingStartedLib** ]，然後選取 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="57b71-129">Select **GettingStartedLib** in the center section of the window, and then select **OK**.</span></span>

       <span data-ttu-id="57b71-130">此動作會讓**GettingStartedLib**專案中定義的類型可供**GettingStartedHost**專案使用。</span><span class="sxs-lookup"><span data-stu-id="57b71-130">This action makes the types defined in the **GettingStartedLib** project available to the **GettingStartedHost** project.</span></span>

3. <span data-ttu-id="57b71-131">將**GettingStartedHost**專案中的參考新增至 <xref:System.ServiceModel> 元件：</span><span class="sxs-lookup"><span data-stu-id="57b71-131">Add a reference in the **GettingStartedHost** project to the <xref:System.ServiceModel> assembly:</span></span>

    1. <span data-ttu-id="57b71-132">在 [**方案總管**] 視窗中，選取 [ **GettingStartedHost** ] 專案底下的 [**參考**] 資料夾，然後從快捷方式功能表選取 [**加入參考**]。</span><span class="sxs-lookup"><span data-stu-id="57b71-132">In the **Solution Explorer** window, select the **References** folder under the **GettingStartedHost** project, and then select **Add Reference** from the shortcut menu.</span></span>

    2. <span data-ttu-id="57b71-133">在 [**加入參考**] 視窗中，于視窗左側的 [**元件**] 底下，選取 [**架構**]。</span><span class="sxs-lookup"><span data-stu-id="57b71-133">In the **Add Reference** window, under **Assemblies** on the left side of the window, select **Framework**.</span></span>

    3. <span data-ttu-id="57b71-134">選取 [ **System.servicemodel**]，然後選取 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="57b71-134">Select **System.ServiceModel**, and then select **OK**.</span></span>

    4. <span data-ttu-id="57b71-135">選取 [檔案] [ **File**  >  **全部儲存**] 以儲存方案。</span><span class="sxs-lookup"><span data-stu-id="57b71-135">Save the solution by selecting **File** > **Save All**.</span></span>

## <a name="add-code-to-host-the-service"></a><span data-ttu-id="57b71-136">新增程式碼以裝載服務</span><span class="sxs-lookup"><span data-stu-id="57b71-136">Add code to host the service</span></span>

<span data-ttu-id="57b71-137">若要裝載服務，您可以新增程式碼來執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="57b71-137">To host the service, you add code to do the following steps:</span></span>

1. <span data-ttu-id="57b71-138">建立基底位址的 URI。</span><span class="sxs-lookup"><span data-stu-id="57b71-138">Create a URI for the base address.</span></span>
2. <span data-ttu-id="57b71-139">建立用來裝載服務的類別實例。</span><span class="sxs-lookup"><span data-stu-id="57b71-139">Create a class instance for hosting the service.</span></span>
3. <span data-ttu-id="57b71-140">建立服務端點。</span><span class="sxs-lookup"><span data-stu-id="57b71-140">Create a service endpoint.</span></span>
4. <span data-ttu-id="57b71-141">啟用中繼資料交換。</span><span class="sxs-lookup"><span data-stu-id="57b71-141">Enable metadata exchange.</span></span>
5. <span data-ttu-id="57b71-142">開啟服務主機以接聽傳入訊息。</span><span class="sxs-lookup"><span data-stu-id="57b71-142">Open the service host to listen for incoming messages.</span></span>
  
<span data-ttu-id="57b71-143">對程式碼進行下列變更：</span><span class="sxs-lookup"><span data-stu-id="57b71-143">Make the following changes to the code:</span></span>

1. <span data-ttu-id="57b71-144">開啟**GettingStartedHost**專案中的**Program.cs**或**Module1**檔案，並以下列程式碼取代其程式碼：</span><span class="sxs-lookup"><span data-stu-id="57b71-144">Open the **Program.cs** or **Module1.vb** file in the **GettingStartedHost** project and replace its code with the following code:</span></span>

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
                    selfHost.Description.Behaviors.Add(smb);

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

    <span data-ttu-id="57b71-145">如需有關此程式碼如何運作的詳細資訊，請參閱[服務裝載程式步驟](#service-hosting-program-steps)。</span><span class="sxs-lookup"><span data-stu-id="57b71-145">For information about how this code works, see [Service hosting program steps](#service-hosting-program-steps).</span></span>

2. <span data-ttu-id="57b71-146">更新專案屬性：</span><span class="sxs-lookup"><span data-stu-id="57b71-146">Update the project properties:</span></span>

   1. <span data-ttu-id="57b71-147">在 [**方案總管**] 視窗中，選取 [ **GettingStartedHost** ] 資料夾，然後從快捷方式功能表選取 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="57b71-147">In the **Solution Explorer** window, select the **GettingStartedHost** folder, and then select **Properties** from the shortcut menu.</span></span>

   2. <span data-ttu-id="57b71-148">在 [ **GettingStartedHost**屬性] 頁面上，選取 [**應用程式**] 索引標籤：</span><span class="sxs-lookup"><span data-stu-id="57b71-148">On the **GettingStartedHost** properties page, select the **Application** tab:</span></span>

      - <span data-ttu-id="57b71-149">針對 c # 專案，請從 [**啟始物件**] 清單中選取 [ **GettingStartedHost** ]。</span><span class="sxs-lookup"><span data-stu-id="57b71-149">For C# projects, select **GettingStartedHost.Program** from the **Startup object** list.</span></span>

      - <span data-ttu-id="57b71-150">針對 Visual Basic 專案，從 [**啟始物件**] 清單中選取 [**服務**]。</span><span class="sxs-lookup"><span data-stu-id="57b71-150">For Visual Basic projects, select **Service.Program** from the **Startup object** list.</span></span>

   3. <span data-ttu-id="57b71-151">從 [**檔案**] 功能表中，選取 [**全部儲存**]。</span><span class="sxs-lookup"><span data-stu-id="57b71-151">From the **File** menu, select **Save All**.</span></span>

## <a name="verify-the-service-is-working"></a><span data-ttu-id="57b71-152">確認服務正在運作</span><span class="sxs-lookup"><span data-stu-id="57b71-152">Verify the service is working</span></span>

1. <span data-ttu-id="57b71-153">建立解決方案，然後從 Visual Studio 內執行**GettingStartedHost**主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="57b71-153">Build the solution, and then run the **GettingStartedHost** console application from inside Visual Studio.</span></span>

    <span data-ttu-id="57b71-154">服務必須以系統管理員許可權執行。</span><span class="sxs-lookup"><span data-stu-id="57b71-154">The service must be run with administrator privileges.</span></span> <span data-ttu-id="57b71-155">因為您以系統管理員許可權開啟 Visual Studio，所以當您在 Visual Studio 中執行**GettingStartedHost**時，應用程式也會以系統管理員許可權執行。</span><span class="sxs-lookup"><span data-stu-id="57b71-155">Because you opened Visual Studio with administrator privileges, when you run **GettingStartedHost** in Visual Studio, the application is run with administrator privileges as well.</span></span> <span data-ttu-id="57b71-156">或者，您可以系統管理員身分開啟新的命令提示字元（從快捷方式功能表選取 [**更多**以  >  **系統管理員身分執行**]），然後在其中執行**GettingStartedHost.exe** 。</span><span class="sxs-lookup"><span data-stu-id="57b71-156">As an alternative, you can open a new command prompt as an administrator (select **More** > **Run as administrator** from the shortcut menu) and run **GettingStartedHost.exe** within it.</span></span>

2. <span data-ttu-id="57b71-157">開啟網頁瀏覽器，並流覽至位於的服務頁面 `http://localhost:8000/GettingStarted/CalculatorService` 。</span><span class="sxs-lookup"><span data-stu-id="57b71-157">Open a web browser and browse to the service's page at `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>

   > [!NOTE]
   > <span data-ttu-id="57b71-158">這一類服務需要適當的許可權，才能在電腦上註冊 HTTP 位址以供接聽。</span><span class="sxs-lookup"><span data-stu-id="57b71-158">Services such as this one require the proper permission to register HTTP addresses on the machine for listening.</span></span> <span data-ttu-id="57b71-159">系統管理員帳戶具有此權限，但是非系統管理員帳戶則必須被授與 HTTP 命名空間的權限。</span><span class="sxs-lookup"><span data-stu-id="57b71-159">Administrator accounts have this permission, but non-administrator accounts must be granted permission for HTTP namespaces.</span></span> <span data-ttu-id="57b71-160">如需如何設定命名空間保留的詳細資訊，請參閱[設定 HTTP 和 HTTPS](feature-details/configuring-http-and-https.md)。</span><span class="sxs-lookup"><span data-stu-id="57b71-160">For more information about how to configure namespace reservations, see [Configuring HTTP and HTTPS](feature-details/configuring-http-and-https.md).</span></span>

## <a name="service-hosting-program-steps"></a><span data-ttu-id="57b71-161">服務裝載程式步驟</span><span class="sxs-lookup"><span data-stu-id="57b71-161">Service hosting program steps</span></span>

<span data-ttu-id="57b71-162">您新增來裝載服務之程式碼中的步驟如下所述：</span><span class="sxs-lookup"><span data-stu-id="57b71-162">The steps in the code you added to host the service are described as follows:</span></span>

- <span data-ttu-id="57b71-163">**步驟 1**：建立類別的實例 `Uri` ，以保存服務的基底位址。</span><span class="sxs-lookup"><span data-stu-id="57b71-163">**Step 1**: Create an instance of the `Uri` class to hold the base address of the service.</span></span> <span data-ttu-id="57b71-164">包含基底位址的 URL 具有可識別服務的選擇性 URI。</span><span class="sxs-lookup"><span data-stu-id="57b71-164">A URL that contains a base address has an optional URI that identifies a service.</span></span> <span data-ttu-id="57b71-165">基底位址的格式如下： `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>` 。</span><span class="sxs-lookup"><span data-stu-id="57b71-165">The base address is formatted as follows: `<transport>://<machine-name or domain><:optional port #>/<optional URI segment>`.</span></span> <span data-ttu-id="57b71-166">計算機服務的基底位址會使用 HTTP 傳輸、localhost、埠8000和 URI 區段 GettingStarted。</span><span class="sxs-lookup"><span data-stu-id="57b71-166">The base address for the calculator service uses the HTTP transport, localhost, port 8000, and the URI segment, GettingStarted.</span></span>

- <span data-ttu-id="57b71-167">**步驟 2**：建立類別的實例 <xref:System.ServiceModel.ServiceHost> ，以用來裝載服務。</span><span class="sxs-lookup"><span data-stu-id="57b71-167">**Step 2**: Create an instance of the <xref:System.ServiceModel.ServiceHost> class, which you use to host the service.</span></span> <span data-ttu-id="57b71-168">此函式會採用兩個參數：實作為服務合約之類別的型別，以及服務的基底位址。</span><span class="sxs-lookup"><span data-stu-id="57b71-168">The constructor takes two parameters: the type of the class that implements the service contract and the base address of the service.</span></span>

- <span data-ttu-id="57b71-169">**步驟 3**：建立 <xref:System.ServiceModel.Description.ServiceEndpoint> 實例。</span><span class="sxs-lookup"><span data-stu-id="57b71-169">**Step 3**: Create a <xref:System.ServiceModel.Description.ServiceEndpoint> instance.</span></span> <span data-ttu-id="57b71-170">服務端點是由位址、繫結和服務合約所組成。</span><span class="sxs-lookup"><span data-stu-id="57b71-170">A service endpoint is composed of an address, a binding, and a service contract.</span></span> <span data-ttu-id="57b71-171">此函式 <xref:System.ServiceModel.Description.ServiceEndpoint> 是由服務合約介面型別、系結和位址所組成。</span><span class="sxs-lookup"><span data-stu-id="57b71-171">The <xref:System.ServiceModel.Description.ServiceEndpoint> constructor is composed of the service contract interface type, a binding, and an address.</span></span> <span data-ttu-id="57b71-172">服務合約是您在服務類型中所定義和實作的 `ICalculator`。</span><span class="sxs-lookup"><span data-stu-id="57b71-172">The service contract is `ICalculator`, which you defined and implement in the service type.</span></span> <span data-ttu-id="57b71-173">這個範例的系結是 <xref:System.ServiceModel.WSHttpBinding> ，它是內建的系結，並會連接到符合 WS-\* 規格的端點。</span><span class="sxs-lookup"><span data-stu-id="57b71-173">The binding for this sample is <xref:System.ServiceModel.WSHttpBinding>, which is a built-in binding and connects to endpoints that conform to the WS-\* specifications.</span></span> <span data-ttu-id="57b71-174">如需 WCF 系結的詳細資訊，請參閱 Wcf 系結[總覽](bindings-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="57b71-174">For more information about WCF bindings, see [WCF bindings overview](bindings-overview.md).</span></span> <span data-ttu-id="57b71-175">您會將位址附加至基底位址，以識別端點。</span><span class="sxs-lookup"><span data-stu-id="57b71-175">You append the address to the base address to identify the endpoint.</span></span> <span data-ttu-id="57b71-176">此程式碼會將位址指定為 CalculatorService，並將端點的完整位址指定為 `http://localhost:8000/GettingStarted/CalculatorService` 。</span><span class="sxs-lookup"><span data-stu-id="57b71-176">The code specifies the address as CalculatorService and the fully qualified address for the endpoint as `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="57b71-177">針對 .NET Framework 第4版和更新版本，新增服務端點是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="57b71-177">For .NET Framework Version 4 and later, adding a service endpoint is optional.</span></span> <span data-ttu-id="57b71-178">在這些版本中，如果您未新增程式碼或設定，WCF 會為服務所執行之每個基底位址和合約的組合加入一個預設端點。</span><span class="sxs-lookup"><span data-stu-id="57b71-178">For these versions, if you don't add your code or configuration, WCF adds one default endpoint for each combination of base address and contract implemented by the service.</span></span> <span data-ttu-id="57b71-179">如需預設端點的詳細資訊，請參閱[指定端點位址](specifying-an-endpoint-address.md)。</span><span class="sxs-lookup"><span data-stu-id="57b71-179">For more information about default endpoints, see [Specifying an endpoint address](specifying-an-endpoint-address.md).</span></span> <span data-ttu-id="57b71-180">如需預設端點、系結和行為的詳細資訊，請參閱[簡化](simplified-configuration.md)的設定和[WCF 服務的簡化](samples/simplified-configuration-for-wcf-services.md)設定。</span><span class="sxs-lookup"><span data-stu-id="57b71-180">For more information about default endpoints, bindings, and behaviors, see [Simplified configuration](simplified-configuration.md) and [Simplified configuration for WCF services](samples/simplified-configuration-for-wcf-services.md).</span></span>

- <span data-ttu-id="57b71-181">**步驟 4**：啟用中繼資料交換。</span><span class="sxs-lookup"><span data-stu-id="57b71-181">**Step 4**: Enable metadata exchange.</span></span> <span data-ttu-id="57b71-182">用戶端會使用中繼資料交換來產生 proxy，以呼叫服務作業。</span><span class="sxs-lookup"><span data-stu-id="57b71-182">Clients use metadata exchange to generate proxies for calling the service operations.</span></span> <span data-ttu-id="57b71-183">若要啟用中繼資料交換，請建立 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 實例，將其 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled> 屬性設定為 `true` ，並將 `ServiceMetadataBehavior` 物件加入至 <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> 實例的集合 <xref:System.ServiceModel.ServiceHost> 。</span><span class="sxs-lookup"><span data-stu-id="57b71-183">To enable metadata exchange, create a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance, set its <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled> property to `true`, and add the `ServiceMetadataBehavior` object to the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> collection of the <xref:System.ServiceModel.ServiceHost> instance.</span></span>

- <span data-ttu-id="57b71-184">**步驟 5**：開啟 <xref:System.ServiceModel.ServiceHost> 以接聽傳入訊息。</span><span class="sxs-lookup"><span data-stu-id="57b71-184">**Step 5**: Open <xref:System.ServiceModel.ServiceHost> to listen for incoming messages.</span></span> <span data-ttu-id="57b71-185">應用程式會等候您按下**enter**鍵。</span><span class="sxs-lookup"><span data-stu-id="57b71-185">The application waits for you to press **Enter**.</span></span> <span data-ttu-id="57b71-186">在應用程式具現化之後 <xref:System.ServiceModel.ServiceHost> ，它會執行 try/catch 區塊。</span><span class="sxs-lookup"><span data-stu-id="57b71-186">After the application instantiates <xref:System.ServiceModel.ServiceHost>, it executes a try/catch block.</span></span> <span data-ttu-id="57b71-187">如需安全攔截所擲回之例外狀況的詳細資訊 <xref:System.ServiceModel.ServiceHost> ，請參閱[使用 Close 和 ABORT 釋放 WCF 用戶端資源](samples/use-close-abort-release-wcf-client-resources.md)。</span><span class="sxs-lookup"><span data-stu-id="57b71-187">For more information about safely catching exceptions thrown by <xref:System.ServiceModel.ServiceHost>, see [Use Close and Abort to release WCF client resources](samples/use-close-abort-release-wcf-client-resources.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="57b71-188">當您新增 WCF 服務程式庫時，如果您藉由啟動服務主機來進行偵錯工具，Visual Studio 會為您裝載它。</span><span class="sxs-lookup"><span data-stu-id="57b71-188">When you add a WCF service library, Visual Studio hosts it for you if you debug it by starting a service host.</span></span> <span data-ttu-id="57b71-189">若要避免衝突，您可以防止 Visual Studio 裝載 WCF 服務程式庫。</span><span class="sxs-lookup"><span data-stu-id="57b71-189">To avoid conflicts, you can prevent Visual Studio from hosting the WCF service library.</span></span>
>
> 1. <span data-ttu-id="57b71-190">在**方案總管**中選取 [ **GettingStartedLib** ] 專案，然後從快捷方式功能表中選擇 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="57b71-190">Select the **GettingStartedLib** project in **Solution Explorer** and choose **Properties** from the shortcut menu.</span></span>
> 2. <span data-ttu-id="57b71-191">選取 [ **WCF 選項**]，然後取消核取**相同方案中的另一個專案時，啟動 WCF 服務主機**。</span><span class="sxs-lookup"><span data-stu-id="57b71-191">Select **WCF Options** and uncheck **Start WCF Service Host when debugging another project in the same solution**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="57b71-192">後續步驟</span><span class="sxs-lookup"><span data-stu-id="57b71-192">Next steps</span></span>

<span data-ttu-id="57b71-193">在本教學課程中，您已了解如何：</span><span class="sxs-lookup"><span data-stu-id="57b71-193">In this tutorial, you learned how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="57b71-194">建立和設定主控台應用程式專案來裝載 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="57b71-194">Create and configure a console app project for hosting a WCF service.</span></span>
> - <span data-ttu-id="57b71-195">加入程式碼來裝載 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="57b71-195">Add code to host the WCF service.</span></span>
> - <span data-ttu-id="57b71-196">更新設定檔。</span><span class="sxs-lookup"><span data-stu-id="57b71-196">Update the configuration file.</span></span>
> - <span data-ttu-id="57b71-197">啟動 WCF 服務，並確認它正在執行。</span><span class="sxs-lookup"><span data-stu-id="57b71-197">Start the WCF service and verify it's running.</span></span>

<span data-ttu-id="57b71-198">請前進到下一個教學課程，以瞭解如何建立 WCF 用戶端。</span><span class="sxs-lookup"><span data-stu-id="57b71-198">Advance to the next tutorial to learn how to create a WCF client.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="57b71-199">教學課程：建立 WCF 用戶端</span><span class="sxs-lookup"><span data-stu-id="57b71-199">Tutorial: Create a WCF client</span></span>](how-to-create-a-wcf-client.md)
