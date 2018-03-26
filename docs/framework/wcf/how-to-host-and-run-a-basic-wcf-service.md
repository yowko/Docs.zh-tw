---
title: HOW TO：裝載和執行基本 Windows Communication Foundation 服務
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF services [WCF]
- WCF services [WCF], running
ms.assetid: 31774d36-923b-4e2d-812e-aa190127266f
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1e1c00abfec36622f5da493165259fb1786ab8d6
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/26/2018
---
# <a name="how-to-host-and-run-a-basic-windows-communication-foundation-service"></a><span data-ttu-id="401bf-102">HOW TO：裝載和執行基本 Windows Communication Foundation 服務</span><span class="sxs-lookup"><span data-stu-id="401bf-102">How to: Host and Run a Basic Windows Communication Foundation Service</span></span>
<span data-ttu-id="401bf-103">這是在建立 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 應用程式時必須進行的六個工作中的第三個。</span><span class="sxs-lookup"><span data-stu-id="401bf-103">This is the third of six tasks required to create a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] application.</span></span> <span data-ttu-id="401bf-104">六個工作的概觀，請參閱[入門教學課程](../../../docs/framework/wcf/getting-started-tutorial.md)主題。</span><span class="sxs-lookup"><span data-stu-id="401bf-104">For an overview of all six of the tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>  
  
 <span data-ttu-id="401bf-105">本主題說明如何在主控台應用程式中裝載 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="401bf-105">This topic describes how to host a [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] service in a console application.</span></span> <span data-ttu-id="401bf-106">這個程序包含下列步驟：</span><span class="sxs-lookup"><span data-stu-id="401bf-106">This procedure consists of the following steps:</span></span>  
  
-   <span data-ttu-id="401bf-107">建立主控台應用程式專案以裝載服務。</span><span class="sxs-lookup"><span data-stu-id="401bf-107">Create a console application project to host the service.</span></span>  
  
-   <span data-ttu-id="401bf-108">建立服務的服務主機。</span><span class="sxs-lookup"><span data-stu-id="401bf-108">Create a service host for the service.</span></span>  
  
-   <span data-ttu-id="401bf-109">啟用中繼資料交換。</span><span class="sxs-lookup"><span data-stu-id="401bf-109">Enable metadata exchange.</span></span>  
  
-   <span data-ttu-id="401bf-110">開啟服務主機。</span><span class="sxs-lookup"><span data-stu-id="401bf-110">Open the service host.</span></span>  
  
 <span data-ttu-id="401bf-111">這個程序之後的範例會列出這項工作所會撰寫的完整程式碼清單。</span><span class="sxs-lookup"><span data-stu-id="401bf-111">A complete listing of the code written in this task is provided in the example following the procedure.</span></span>  
  
## <a name="to-create-a-new-console-application-to-host-the-service"></a><span data-ttu-id="401bf-112">若要建立新的主控台應用程式以裝載服務</span><span class="sxs-lookup"><span data-stu-id="401bf-112">To create a new console application to host the service</span></span>  
  
1.  <span data-ttu-id="401bf-113">以滑鼠右鍵按一下 開始使用的方案，選取 建立新的主控台應用程式專案**新增**，**新專案**。</span><span class="sxs-lookup"><span data-stu-id="401bf-113">Create a new Console Application project by right-clicking on the Getting Started solution, selecting, **Add**, **New Project**.</span></span> <span data-ttu-id="401bf-114">在**加入新的專案**對話方塊左側的對話方塊中，選取**Windows**下**C#**或**VB**。</span><span class="sxs-lookup"><span data-stu-id="401bf-114">In the **Add New Project** dialog on the left hand side of the dialog select **Windows** under **C#** or **VB**.</span></span> <span data-ttu-id="401bf-115">在對話方塊中間區段選取**主控台應用程式**。</span><span class="sxs-lookup"><span data-stu-id="401bf-115">In the center section of the dialog select **Console Application**.</span></span> <span data-ttu-id="401bf-116">將專案命名為 GettingStartedHost。</span><span class="sxs-lookup"><span data-stu-id="401bf-116">Name the project GettingStartedHost.</span></span>  
  
2.  <span data-ttu-id="401bf-117">上按一下滑鼠右鍵，將 GettingStartedHost 專案的目標 framework 設定為.NET Framework 4.5 **GettingStartedHost**在 [方案總管] 中，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="401bf-117">Set the target framework of the GettingStartedHost project to .NET Framework 4.5 by right clicking on **GettingStartedHost** in the Solution Explorer and selecting **Properties**.</span></span> <span data-ttu-id="401bf-118">下拉式方塊中標示為**目標 Framework**選取**.NET Framework 4.5**。</span><span class="sxs-lookup"><span data-stu-id="401bf-118">In the dropdown box labeled **Target Framework** select **.NET Framework 4.5**.</span></span> <span data-ttu-id="401bf-119">設定目標 framework VB 專案的方式稍有不同，請在 GettingStartedHost 專案屬性對話方塊，按一下**編譯**畫面中，左側索引標籤，然後按一下 **進階編譯選項**位於對話方塊左下角的按鈕。</span><span class="sxs-lookup"><span data-stu-id="401bf-119">Setting the target framework for a VB project is a little different, in the GettingStartedHost project properties dialog, click the **Compile** tab on the left-hand side of the screen, and then click the **Advanced Compile Options** button at the lower left-hand corner of the dialog.</span></span> <span data-ttu-id="401bf-120">然後選取**.NET Framework 4.5**下拉式方塊中標示為**目標 Framework**。</span><span class="sxs-lookup"><span data-stu-id="401bf-120">Then select **.NET Framework 4.5** in the dropdown box labeled **Target Framework**.</span></span>  
  
     <span data-ttu-id="401bf-121">設定目標 framework 會導致[!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]若要重新載入該方案，請按**確定**出現提示時。</span><span class="sxs-lookup"><span data-stu-id="401bf-121">Setting the target framework will cause [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] to reload the solution, press **OK** when prompted.</span></span>  
  
3.  <span data-ttu-id="401bf-122">將 GettingStartedLib 專案的參考加入至 GettingStartedHost 專案，以滑鼠右鍵按一下上**參考**資料夾在 [方案總管] 並選取 [GettingStartedHost] 專案底下**加入參考**.</span><span class="sxs-lookup"><span data-stu-id="401bf-122">Add a reference to the GettingStartedLib project to the GettingStartedHost project by right clicking on the **References** folder under the GettingStartedHost project in the solution explorer and select **Add Reference**.</span></span> <span data-ttu-id="401bf-123">在**加入參考**對話方塊中，選取**方案**對話方塊和 [GettingStartedLib] 對話方塊，再按一下中間區段中的左側**新增**。</span><span class="sxs-lookup"><span data-stu-id="401bf-123">In the **Add Reference** dialog, select **Solution** on the left-hand side of the dialog and select GettingStartedLib in the center section of the dialog and click **Add**.</span></span> <span data-ttu-id="401bf-124">這樣 GettingStartedHost 專案就可以使用 GettingStartedLib 中所定義的型別。</span><span class="sxs-lookup"><span data-stu-id="401bf-124">This makes the types defined in GettingStartedLib available to the GettingStartedHost project.</span></span>  
  
4.  <span data-ttu-id="401bf-125">將 System.ServiceModel 的參考加入至 GettingStartedHost 專案，以滑鼠右鍵按一下**參考**資料夾在方案總管，然後選取 GettingStartedHost 專案底下**新增**參考。</span><span class="sxs-lookup"><span data-stu-id="401bf-125">Add a reference to System.ServiceModel to the GettingStartedHost project by right-clicking the **Reference** folder under the GettingStartedHost project in Solution Explorer and select **Add** Reference.</span></span> <span data-ttu-id="401bf-126">在**加入參考**對話方塊中，選取**Framework**對話方塊的左側。</span><span class="sxs-lookup"><span data-stu-id="401bf-126">In the **Add Reference** dialog select **Framework** on the left-hand side of the dialog.</span></span> <span data-ttu-id="401bf-127">在 [搜尋組件] 文字方塊中輸入 `System.ServiceModel`。</span><span class="sxs-lookup"><span data-stu-id="401bf-127">In the Search Assemblies textbox, type in `System.ServiceModel`.</span></span> <span data-ttu-id="401bf-128">在對話方塊中間區段選取**System.ServiceModel**，按一下 [**新增**按鈕，然後按一下**關閉**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="401bf-128">In the center section of the dialog select **System.ServiceModel**, click the **Add** button, and click the **Close** button.</span></span> <span data-ttu-id="401bf-129">按一下主功能表下的 [全部儲存] 按鈕，以儲存方案。</span><span class="sxs-lookup"><span data-stu-id="401bf-129">Save the solution by clicking the Save All button below the main menu.</span></span>  
  
### <a name="to-host-the-service"></a><span data-ttu-id="401bf-130">若要裝載服務</span><span class="sxs-lookup"><span data-stu-id="401bf-130">To host the service</span></span>  
  
-   <span data-ttu-id="401bf-131">開啟 Program.cs 或 Module.vb 檔案，並輸入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="401bf-131">Open the Program.cs or Module.vb file and enter the following code:</span></span>  
  
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
  
    1.  <span data-ttu-id="401bf-132">步驟 1：建立 Uri 類別的執行個體以保留服務的基底位址 (Base Address)。</span><span class="sxs-lookup"><span data-stu-id="401bf-132">Step 1 - Creates an instance of the Uri class to hold the base address of the service.</span></span> <span data-ttu-id="401bf-133">服務是由包含基底位址及選擇性 URI 的 URL 所識別。</span><span class="sxs-lookup"><span data-stu-id="401bf-133">Services are identified by a URL which contains a base address and an optional URI.</span></span> <span data-ttu-id="401bf-134">基底地址的格式如下: [傳輸]:// [電腦名稱或網域] [: 選擇性埠 #] / [選擇性 URI 區段] 的計算機服務的基底位址會使用 HTTP 傳輸、 localhost、 連接埠 8000 和 URI 區段"GettingStarted"</span><span class="sxs-lookup"><span data-stu-id="401bf-134">The base address is formatted as follows:[transport]://[machine-name or domain][:optional port #]/[optional URI segment]The base address for the calculator service uses the HTTP transport, localhost, port 8000, and the URI segment "GettingStarted"</span></span>  
  
    2.  <span data-ttu-id="401bf-135">步驟 2：建立 <xref:System.ServiceModel.ServiceHost> 類別的執行個體以裝載服務。</span><span class="sxs-lookup"><span data-stu-id="401bf-135">Step 2 – Creates an instance of the <xref:System.ServiceModel.ServiceHost> class to host the service.</span></span> <span data-ttu-id="401bf-136">建構函式接受兩個參數：實作服務合約之類別的型別以及服務的基底位址。</span><span class="sxs-lookup"><span data-stu-id="401bf-136">The constructor takes two parameters, the type of the class that implements the service contract, and the base address of the service.</span></span>  
  
    3.  <span data-ttu-id="401bf-137">步驟 3： 建立<!--zz <xref:System.ServiceModel.ServiceEndpoint>-->` System.ServiceModel.ServiceEndpoint`執行個體。</span><span class="sxs-lookup"><span data-stu-id="401bf-137">Step 3 – Creates a <!--zz <xref:System.ServiceModel.ServiceEndpoint>--> ` System.ServiceModel.ServiceEndpoint` instance.</span></span> <span data-ttu-id="401bf-138">服務端點是由位址、繫結和服務合約所組成。</span><span class="sxs-lookup"><span data-stu-id="401bf-138">A service endpoint is composed of an address, a binding, and a service contract.</span></span> <span data-ttu-id="401bf-139"><!--zz <xref:System.ServiceModel.ServiceEndpoint>--> ` System.ServiceModel.ServiceEndpoint`服務合約介面型別、 繫結和位址，因此會採用建構函式。</span><span class="sxs-lookup"><span data-stu-id="401bf-139">The <!--zz <xref:System.ServiceModel.ServiceEndpoint>--> ` System.ServiceModel.ServiceEndpoint`  constructor therefore takes the service contract interface type, a binding, and an address.</span></span> <span data-ttu-id="401bf-140">服務合約是您在服務類型中所定義和實作的 `ICalculator`。</span><span class="sxs-lookup"><span data-stu-id="401bf-140">The service contract is `ICalculator`, which you defined and implement in the service type.</span></span> <span data-ttu-id="401bf-141">這個範例使用的繫結是 <xref:System.ServiceModel.WSHttpBinding>，這是用來連接至符合 WS-\* 規格之端點的內建繫結。</span><span class="sxs-lookup"><span data-stu-id="401bf-141">The binding used in this sample is <xref:System.ServiceModel.WSHttpBinding> which is a built-in binding that is used for connecting to endpoints that conform to the WS-\* specifications.</span></span> <span data-ttu-id="401bf-142">如需有關 WCF 繫結的詳細資訊，請參閱[WCF 繫結概觀](../../../docs/framework/wcf/bindings-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="401bf-142">For more information about WCF bindings, see [WCF Bindings Overview](../../../docs/framework/wcf/bindings-overview.md).</span></span> <span data-ttu-id="401bf-143">位址會附加至基底位址以識別端點。</span><span class="sxs-lookup"><span data-stu-id="401bf-143">The address is appended to the base address to identify the endpoint.</span></span> <span data-ttu-id="401bf-144">此程式碼中指定的位址是"CalculatorService"，因此端點的完整的位址是`"http://localhost:8000/GettingStarted/CalculatorService"`新增服務端點是選擇性時使用.NET Framework 4.0 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="401bf-144">The address specified in this code is "CalculatorService" so the fully qualified address for the endpoint is `"http://localhost:8000/GettingStarted/CalculatorService"` Adding a service endpoint is optional when using .NET Framework 4.0 or later.</span></span> <span data-ttu-id="401bf-145">在這些版本中，如果沒有在程式碼或組態中加入端點，則 WCF 會為服務所實作之合約與基底位址的每個組合加入一個預設端點。</span><span class="sxs-lookup"><span data-stu-id="401bf-145">In these versions, if no endpoints are added in code or configuration, WCF adds one default endpoint for each combination of base address and contract implemented by the service.</span></span> <span data-ttu-id="401bf-146">如需有關預設端點請參閱[指定端點位址](../../../docs/framework/wcf/specifying-an-endpoint-address.md)。</span><span class="sxs-lookup"><span data-stu-id="401bf-146">For more information about default endpoints see [Specifying an Endpoint Address](../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="401bf-147"> 預設端點、繫結和行為的詳細資訊，請參閱 [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="401bf-147"> default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="401bf-148">使用 .NET Framework 4 (含) 以後版本時，加入服務端點是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="401bf-148">Adding a service endpoint is optional when using .NET Framework 4 or later.</span></span> <span data-ttu-id="401bf-149">在這些版本中，如果沒有在程式碼或組態中加入端點，則 WCF 會為服務所實作之合約與基底位址的每個組合加入一個預設端點。</span><span class="sxs-lookup"><span data-stu-id="401bf-149">In these versions, if no endpoints are added in code or configuration, WCF adds one default endpoint for each combination of base address and contract implemented by the service.</span></span> <span data-ttu-id="401bf-150">如需有關預設端點請參閱[指定端點位址](../../../docs/framework/wcf/specifying-an-endpoint-address.md)。</span><span class="sxs-lookup"><span data-stu-id="401bf-150">For more information about default endpoints see [Specifying an Endpoint Address](../../../docs/framework/wcf/specifying-an-endpoint-address.md).</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="401bf-151"> 預設端點、繫結和行為的詳細資訊，請參閱 [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="401bf-151"> default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
    4.  <span data-ttu-id="401bf-152">步驟 4：啟用中繼資料交換。</span><span class="sxs-lookup"><span data-stu-id="401bf-152">Step 4 – Enable metadata exchange.</span></span> <span data-ttu-id="401bf-153">用戶端會使用中繼資料交換來產生用於呼叫服務作業的 Proxy。</span><span class="sxs-lookup"><span data-stu-id="401bf-153">Clients will use metadata exchange to generate proxies that will be used to call the service operations.</span></span> <span data-ttu-id="401bf-154">若要啟用中繼資料交換建立<xref:System.ServiceModel.Description.ServiceMetadataBehavior>執行個體、 將它的<xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A>屬性`true`，並將行為加入至<!--zz <xref:System.ServiceModel.ServiceHost.Behaviors%2A>  -->`System.ServiceModel.ServiceHost.Behaviors%2A`集合<xref:System.ServiceModel.ServiceHost>執行個體。</span><span class="sxs-lookup"><span data-stu-id="401bf-154">To enable metadata exchange create a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> instance, set it’s <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true`, and add the behavior to the <!--zz <xref:System.ServiceModel.ServiceHost.Behaviors%2A>  -->`System.ServiceModel.ServiceHost.Behaviors%2A` collection of the <xref:System.ServiceModel.ServiceHost> instance.</span></span>  
  
    5.  <span data-ttu-id="401bf-155">步驟 5：開啟 <xref:System.ServiceModel.ServiceHost> 以開始接聽傳入訊息。</span><span class="sxs-lookup"><span data-stu-id="401bf-155">Step 5 – Open the <xref:System.ServiceModel.ServiceHost> to listen for incoming messages.</span></span> <span data-ttu-id="401bf-156">注意程式碼會等待使用者按下 Enter。</span><span class="sxs-lookup"><span data-stu-id="401bf-156">Notice the code waits for the user to hit enter.</span></span> <span data-ttu-id="401bf-157">如果不這麼做，應用程式會立即關閉而服務也將關閉。另外也要注意使用的 try/catch 區塊。</span><span class="sxs-lookup"><span data-stu-id="401bf-157">If you do not do this, the app will close immediately and the service will shut down.Also notice a  try/catch block used.</span></span> <span data-ttu-id="401bf-158">在 <xref:System.ServiceModel.ServiceHost> 具現化之後，會將所有其他程式碼放置在 try/catch 區塊中。</span><span class="sxs-lookup"><span data-stu-id="401bf-158">After the <xref:System.ServiceModel.ServiceHost> has been instantiated, all other code is placed in a try/catch block.</span></span> <span data-ttu-id="401bf-159">如需有關安全地攔截，所擲回的例外狀況<xref:System.ServiceModel.ServiceHost>，請參閱[避免 Using 陳述式的問題](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md)</span><span class="sxs-lookup"><span data-stu-id="401bf-159">For more information about safely catching exceptions thrown by <xref:System.ServiceModel.ServiceHost>, see [Avoiding Problems with the Using Statement](../../../docs/framework/wcf/samples/avoiding-problems-with-the-using-statement.md)</span></span>  
  
### <a name="to-verify-the-service-is-working"></a><span data-ttu-id="401bf-160">若要驗證服務是否執行中</span><span class="sxs-lookup"><span data-stu-id="401bf-160">To verify the service is working</span></span>  
  
1.  <span data-ttu-id="401bf-161">從 [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] 中執行 GettingStartedHost 主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="401bf-161">Run the GettingStartedHost console application from inside [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].</span></span> <span data-ttu-id="401bf-162">在 [!INCLUDE[wv](../../../includes/wv-md.md)] (含) 以後版本的作業系統中執行時，必須以系統管理員權限來執行服務。</span><span class="sxs-lookup"><span data-stu-id="401bf-162">When running on [!INCLUDE[wv](../../../includes/wv-md.md)] and later operating systems, the service must be run with administrator privileges.</span></span> <span data-ttu-id="401bf-163">因為 [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] 是以系統管理員權限的身分執行，所以 GettingStartedHost 也要以系統管理員權限的身分執行。</span><span class="sxs-lookup"><span data-stu-id="401bf-163">Because [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] was run with Administrator privileges, GettingStartedHost is also run with Administrator privileges.</span></span> <span data-ttu-id="401bf-164">您也可以利用系統管理員權限開啟命令提示字元執行，然後透過命令提示字元執行 service.exe。</span><span class="sxs-lookup"><span data-stu-id="401bf-164">You can also start a new command prompt running it with Administrator privileges and run service.exe within it.</span></span>  
  
2.  <span data-ttu-id="401bf-165">開啟 Internet Explorer，並瀏覽至服務位於 `http://localhost:8000/GettingStarted/CalculatorService` 的偵錯頁面。</span><span class="sxs-lookup"><span data-stu-id="401bf-165">Open Internet Explorer and browse to the service's debug page at `http://localhost:8000/GettingStarted/CalculatorService`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="401bf-166">範例</span><span class="sxs-lookup"><span data-stu-id="401bf-166">Example</span></span>  
 <span data-ttu-id="401bf-167">下列範例包含此教學課程上一個步驟的服務合約和實作，並且會將服務裝載到主控台應用程式中。</span><span class="sxs-lookup"><span data-stu-id="401bf-167">The following example includes the service contract and implementation from previous steps in the tutorial and hosts the service in a console application.</span></span>  
  
 <span data-ttu-id="401bf-168">若要使用命令列編譯器編譯這項，編譯成類別程式庫參考的 IService1.cs 和 Service1.cs `System.ServiceModel.dll`。</span><span class="sxs-lookup"><span data-stu-id="401bf-168">To compile this with a command-line compiler, compile IService1.cs and Service1.cs into a class library referencing `System.ServiceModel.dll`.</span></span> <span data-ttu-id="401bf-169">然後將 Program.cs 編譯為主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="401bf-169">And compile Program.cs to a console application.</span></span>  
  
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
>  <span data-ttu-id="401bf-170">此類服務需要權限才能將 HTTP 位址註冊到電腦上，以便接聽。</span><span class="sxs-lookup"><span data-stu-id="401bf-170">Services such as this one require permission to register HTTP addresses on the machine for listening.</span></span> <span data-ttu-id="401bf-171">系統管理員帳戶具有此權限，但是非系統管理員帳戶則必須被授與 HTTP 命名空間的權限。</span><span class="sxs-lookup"><span data-stu-id="401bf-171">Administrator accounts have this permission, but non-administrator accounts must be granted permission for HTTP namespaces.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="401bf-172"> 如何設定命名空間保留區，請參閱[設定 HTTP 和 HTTPS](../../../docs/framework/wcf/feature-details/configuring-http-and-https.md)。</span><span class="sxs-lookup"><span data-stu-id="401bf-172"> how to configure namespace reservations, see [Configuring HTTP and HTTPS](../../../docs/framework/wcf/feature-details/configuring-http-and-https.md).</span></span> <span data-ttu-id="401bf-173">在 [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] 下執行時，必須以系統管理員權限的身分執行 service.exe。</span><span class="sxs-lookup"><span data-stu-id="401bf-173">When running under [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)], the service.exe must be run with administrator privileges.</span></span>  
  
 <span data-ttu-id="401bf-174">服務目前正在執行中。</span><span class="sxs-lookup"><span data-stu-id="401bf-174">Now the service is running.</span></span> <span data-ttu-id="401bf-175">若要繼續[How to： 建立用戶端](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)。</span><span class="sxs-lookup"><span data-stu-id="401bf-175">Proceed to [How to: Create a Client](../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span> <span data-ttu-id="401bf-176">如需疑難排解資訊，請參閱[疑難排解入門教學課程](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="401bf-176">For troubleshooting information, see [Troubleshooting the Getting Started Tutorial](../../../docs/framework/wcf/troubleshooting-the-getting-started-tutorial.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="401bf-177">另請參閱</span><span class="sxs-lookup"><span data-stu-id="401bf-177">See Also</span></span>  
 [<span data-ttu-id="401bf-178">快速入門</span><span class="sxs-lookup"><span data-stu-id="401bf-178">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)  
 [<span data-ttu-id="401bf-179">自我裝載</span><span class="sxs-lookup"><span data-stu-id="401bf-179">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)
