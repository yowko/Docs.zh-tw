---
title: HOW TO：建立 Windows Communication Foundation 用戶端
ms.date: 09/14/2018
helpviewer_keywords:
- clients [WCF], running
- WCF clients [WCF], running
ms.assetid: a67884cc-1c4b-416b-8c96-5c954099f19f
ms.openlocfilehash: 1eadb5008575a1a53d685db14d68e42d0dce1360
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/21/2018
ms.locfileid: "46539703"
---
# <a name="how-to-create-a-windows-communication-foundation-client"></a><span data-ttu-id="54a7f-102">HOW TO：建立 Windows Communication Foundation 用戶端</span><span class="sxs-lookup"><span data-stu-id="54a7f-102">How to: Create a Windows Communication Foundation Client</span></span>

<span data-ttu-id="54a7f-103">這是建立 Windows Communication Foundation (WCF) 應用程式所需的六個工作的第四個。</span><span class="sxs-lookup"><span data-stu-id="54a7f-103">This is the fourth of six tasks required to create a Windows Communication Foundation (WCF) application.</span></span> <span data-ttu-id="54a7f-104">如需這六個工作的概觀，請參閱[使用者入門教學課程](../../../docs/framework/wcf/getting-started-tutorial.md)主題。</span><span class="sxs-lookup"><span data-stu-id="54a7f-104">For an overview of all six of the tasks, see the [Getting Started Tutorial](../../../docs/framework/wcf/getting-started-tutorial.md) topic.</span></span>

<span data-ttu-id="54a7f-105">本主題描述如何從 WCF 服務擷取中繼資料，並使用它來建立 WCF proxy 以存取服務。</span><span class="sxs-lookup"><span data-stu-id="54a7f-105">This topic describes how to retrieve metadata from a WCF service and use it to create a WCF proxy that can access the service.</span></span> <span data-ttu-id="54a7f-106">這項工作使用來完成**加入服務參考**Visual Studio 所提供的功能。</span><span class="sxs-lookup"><span data-stu-id="54a7f-106">This task is completed by using the **Add Service Reference** functionality provided by Visual Studio.</span></span> <span data-ttu-id="54a7f-107">這個工具會從服務的 MEX 端點取得中繼資料，並以您所選擇的語言 (預設為 C#) 產生用戶端 Proxy 的 Managed 原始程式碼檔。</span><span class="sxs-lookup"><span data-stu-id="54a7f-107">This tool obtains the metadata from the service’s MEX endpoint and generates a managed source code file for a client proxy in the language you have chosen (C# by default).</span></span> <span data-ttu-id="54a7f-108">除了建立用戶端 Proxy，此工具也會建立或更新用戶端的組態檔，讓用戶端應用程式在其中一個端點與服務連線。</span><span class="sxs-lookup"><span data-stu-id="54a7f-108">In addition to creating the client proxy, the tool also creates or updates the client configuration file which enables the client application to connect to the service at one of its endpoints.</span></span>

> [!NOTE]
> <span data-ttu-id="54a7f-109">您也可以使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)工具來產生 proxy 類別和組態，而不使用**加入服務參考**Visual Studio 中。</span><span class="sxs-lookup"><span data-stu-id="54a7f-109">You can also use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool to generate the proxy class and configuration instead of using **Add Service Reference** in Visual Studio.</span></span>

> [!NOTE]
> <span data-ttu-id="54a7f-110">當從 Visual Studio 中的類別庫專案中呼叫 WCF 服務，您可以使用**加入服務參考**功能來自動產生 proxy 和相關聯的組態檔。</span><span class="sxs-lookup"><span data-stu-id="54a7f-110">When calling a WCF service from a class library project in Visual Studio, you can use the **Add Service Reference** feature to automatically generate a proxy and associated configuration file.</span></span> <span data-ttu-id="54a7f-111">類別庫專案將不會使用組態檔。</span><span class="sxs-lookup"><span data-stu-id="54a7f-111">The configuration file will not be used by the class library project.</span></span> <span data-ttu-id="54a7f-112">您要在產生的組態檔中加入呼叫類別庫的可執行檔的 app.config 檔案的設定。</span><span class="sxs-lookup"><span data-stu-id="54a7f-112">You need to add the settings in the generated configuration file to the app.config file for the executable that calls the class library.</span></span>

<span data-ttu-id="54a7f-113">用戶端應用程式會使用產生的 Proxy 類別來建立與服務通訊的用戶端。</span><span class="sxs-lookup"><span data-stu-id="54a7f-113">The client application uses the generated proxy class to communicate with the service.</span></span> <span data-ttu-id="54a7f-114">此程序所述[如何： 使用用戶端](../../../docs/framework/wcf/how-to-use-a-wcf-client.md)。</span><span class="sxs-lookup"><span data-stu-id="54a7f-114">This procedure is described in [How to: Use a Client](../../../docs/framework/wcf/how-to-use-a-wcf-client.md).</span></span>

## <a name="to-create-a-windows-communication-foundation-client"></a><span data-ttu-id="54a7f-115">若要建立 Windows Communication Foundation 用戶端</span><span class="sxs-lookup"><span data-stu-id="54a7f-115">To create a Windows Communication Foundation client</span></span>

1. <span data-ttu-id="54a7f-116">Visual Studio 中建立新的主控台應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="54a7f-116">Create a new console application project in Visual Studio.</span></span> <span data-ttu-id="54a7f-117">中的 [入門] 方案上按一下滑鼠右鍵**方案總管**，然後選取**新增** > **新專案**。</span><span class="sxs-lookup"><span data-stu-id="54a7f-117">Right-click on the Getting Started solution in **Solution Explorer** and select **Add** > **New Project**.</span></span> <span data-ttu-id="54a7f-118">在 **加入新的專案** 對話方塊的左側，選取**Windows 桌面** 類別下的**Visual C#** 或**Visual Basic**。</span><span class="sxs-lookup"><span data-stu-id="54a7f-118">In the **Add New Project** dialog, on the left-hand side, select the **Windows Desktop** category under **Visual C#** or **Visual Basic**.</span></span> <span data-ttu-id="54a7f-119">選取 **主控台應用程式 (.NET Framework)** 範本，然後再將專案命名為**GettingStartedClient**。</span><span class="sxs-lookup"><span data-stu-id="54a7f-119">Select the **Console App (.NET Framework)** template, and then name the project **GettingStartedClient**.</span></span>

2. <span data-ttu-id="54a7f-120">將 System.ServiceModel 的參考新增至 [gettingstartedclient] 專案中。</span><span class="sxs-lookup"><span data-stu-id="54a7f-120">Add a reference to System.ServiceModel to the GettingStartedClient project.</span></span> <span data-ttu-id="54a7f-121">以滑鼠右鍵按一下**參考**中 [gettingstartedclient] 專案下的資料夾**方案總管**，然後選取**加入參考**。</span><span class="sxs-lookup"><span data-stu-id="54a7f-121">Right-click on the **References** folder under the GettingStartedClient project in **Solution Explorer**, and then select **Add Reference**.</span></span> <span data-ttu-id="54a7f-122">在 **加入參考**對話方塊中，選取**Framework**在對話方塊左側**組件**。</span><span class="sxs-lookup"><span data-stu-id="54a7f-122">In the **Add Reference** dialog, select **Framework** on the left-hand side of the dialog under **Assemblies**.</span></span> <span data-ttu-id="54a7f-123">尋找並選取**System.ServiceModel**，然後選擇**確定**。</span><span class="sxs-lookup"><span data-stu-id="54a7f-123">Find and select **System.ServiceModel**, and then choose **OK**.</span></span> <span data-ttu-id="54a7f-124">選取儲存方案**檔案** > **全部儲存**。</span><span class="sxs-lookup"><span data-stu-id="54a7f-124">Save the solution by selecting **File** > **Save All**.</span></span>

3. <span data-ttu-id="54a7f-125">加入至計算機服務的服務參考。</span><span class="sxs-lookup"><span data-stu-id="54a7f-125">Add a service reference to the Calculator Service.</span></span>

   1. <span data-ttu-id="54a7f-126">首先，啟動 GettingStartedHost 主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="54a7f-126">First, start up the GettingStartedHost console application.</span></span>

   2. <span data-ttu-id="54a7f-127">一旦主機正在執行，以滑鼠右鍵按一下**參考**中 [gettingstartedclient] 專案下的資料夾**方案總管**，然後選取**新增** >  **服務參考**。</span><span class="sxs-lookup"><span data-stu-id="54a7f-127">Once the host is running, right-click the **References** folder under the GettingStartedClient project in **Solution Explorer** and select **Add** > **Service Reference**.</span></span>

   3. <span data-ttu-id="54a7f-128">在的 [位址] 方塊中輸入下列 URL**加入服務參考**對話方塊： [http://localhost:8000/GettingStartedClient/Service](http://localhost:8000/GettingStartedClient/Service)</span><span class="sxs-lookup"><span data-stu-id="54a7f-128">Enter the following URL in the address box of the **Add Service Reference** dialog: [http://localhost:8000/GettingStartedClient/Service](http://localhost:8000/GettingStartedClient/Service)</span></span>

   4. <span data-ttu-id="54a7f-129">選擇**移**。</span><span class="sxs-lookup"><span data-stu-id="54a7f-129">Choose **Go**.</span></span>

   <span data-ttu-id="54a7f-130">CalculatorService 所示**Services**清單方塊。</span><span class="sxs-lookup"><span data-stu-id="54a7f-130">The CalculatorService is displayed in the **Services** list box.</span></span> <span data-ttu-id="54a7f-131">按兩下 CalculatorService 將它展開並顯示服務所實作的服務合約。</span><span class="sxs-lookup"><span data-stu-id="54a7f-131">Double-click CalculatorService to expand it and show the service contracts implemented by the service.</span></span> <span data-ttu-id="54a7f-132">保留為預設命名空間-選擇**確定**。</span><span class="sxs-lookup"><span data-stu-id="54a7f-132">Leave the default namespace as-is and choose **OK**.</span></span>

    <span data-ttu-id="54a7f-133">當您將使用 Visual Studio 服務的參考時，新的項目會出現在**方案總管**下方**服務參考**gettingstartedclient 專案底下的資料夾。</span><span class="sxs-lookup"><span data-stu-id="54a7f-133">When you add a reference to a service using Visual Studio, a new item appears in **Solution Explorer** under the **Service References** folder under the GettingStartedClient project.</span></span> <span data-ttu-id="54a7f-134">如果您使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)工具、 原始程式碼檔和 app.config 檔案會產生。</span><span class="sxs-lookup"><span data-stu-id="54a7f-134">If you use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool, a source code file and app.config file are generated.</span></span>

    <span data-ttu-id="54a7f-135">您也可以使用命令列工具[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)搭配適當的參數，來建立用戶端程式碼。</span><span class="sxs-lookup"><span data-stu-id="54a7f-135">You can also use the command-line tool [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) with the appropriate switches to create the client code.</span></span> <span data-ttu-id="54a7f-136">下列範例會產生服務的程式碼檔案與組態檔。</span><span class="sxs-lookup"><span data-stu-id="54a7f-136">The following example generates a code file and a configuration file for the service.</span></span> <span data-ttu-id="54a7f-137">第一個範例示範如何在 VB 中，產生 proxy 和第二個示範如何在 C# 中產生的 proxy:</span><span class="sxs-lookup"><span data-stu-id="54a7f-137">The first example shows how to generate the proxy in VB, and the second shows how to generate the proxy in C#:</span></span>

    ```shell
    svcutil.exe /language:vb /out:generatedProxy.vb /config:app.config http://localhost:8000/GettingStartedClient/service
    ```

    ```shell
    svcutil.exe /language:cs /out:generatedProxy.cs /config:app.config http://localhost:8000/GettingStartedClient/service
    ```

## <a name="next-steps"></a><span data-ttu-id="54a7f-138">後續步驟</span><span class="sxs-lookup"><span data-stu-id="54a7f-138">Next steps</span></span>

<span data-ttu-id="54a7f-139">您已建立用戶端應用程式將用來呼叫計算機服務的 proxy。</span><span class="sxs-lookup"><span data-stu-id="54a7f-139">You've created the proxy that the client application will use to call the calculator service.</span></span> <span data-ttu-id="54a7f-140">請繼續進行系列中的下一個主題。</span><span class="sxs-lookup"><span data-stu-id="54a7f-140">Proceed to the next topic in the series.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="54a7f-141">如何：設定用戶端</span><span class="sxs-lookup"><span data-stu-id="54a7f-141">How to: Configure a Client</span></span>](../../../docs/framework/wcf/how-to-configure-a-basic-wcf-client.md)

## <a name="see-also"></a><span data-ttu-id="54a7f-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="54a7f-142">See also</span></span>

- [<span data-ttu-id="54a7f-143">ServiceModel 中繼資料公用程式工具 (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="54a7f-143">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [<span data-ttu-id="54a7f-144">快速入門</span><span class="sxs-lookup"><span data-stu-id="54a7f-144">Getting Started</span></span>](../../../docs/framework/wcf/samples/getting-started-sample.md)
- [<span data-ttu-id="54a7f-145">自我裝載</span><span class="sxs-lookup"><span data-stu-id="54a7f-145">Self-Host</span></span>](../../../docs/framework/wcf/samples/self-host.md)
- [<span data-ttu-id="54a7f-146">如何：使用組態檔發行服務的中繼資料</span><span class="sxs-lookup"><span data-stu-id="54a7f-146">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="54a7f-147">如何：使用 Svcutil.exe 來下載中繼資料文件</span><span class="sxs-lookup"><span data-stu-id="54a7f-147">How to: Use Svcutil.exe to Download Metadata Documents</span></span>](../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)
