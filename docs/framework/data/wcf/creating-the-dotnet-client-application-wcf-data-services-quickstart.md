---
title: 建立 .NET Framework 用戶端應用程式 (WCF 資料服務快速入門)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 41ade767-eeab-437d-9121-9797e8fb8045
ms.openlocfilehash: 4beaba24e42b15ebc45ece6e5319a2b14df54ab6
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975386"
---
# <a name="creating-the-net-framework-client-application-wcf-data-services-quickstart"></a><span data-ttu-id="56940-102">建立 .NET Framework 用戶端應用程式 (WCF 資料服務快速入門)</span><span class="sxs-lookup"><span data-stu-id="56940-102">Creating the .NET Framework Client Application (WCF Data Services Quickstart)</span></span>

<span data-ttu-id="56940-103">這是 WCF Data Services 快速入門的最後一項工作。</span><span class="sxs-lookup"><span data-stu-id="56940-103">This is the final task of the WCF Data Services quickstart.</span></span> <span data-ttu-id="56940-104">在這項工作中，您會在方案中加入主控台應用程式、在這個新的用戶端應用程式中加入開放式資料通訊協定（OData）摘要的參考，並使用產生的用戶端資料服務類別和用戶端，從用戶端應用程式存取 OData 摘要磁帶.</span><span class="sxs-lookup"><span data-stu-id="56940-104">In this task, you will add a console application to the solution, add a reference to the Open Data Protocol (OData) feed into this new client application, and access the OData feed from the client application by using the generated client data service classes and client libraries.</span></span>

> [!NOTE]
> <span data-ttu-id="56940-105">不需要 .NET Framework 架構的用戶端應用程式也可存取資料摘要。</span><span class="sxs-lookup"><span data-stu-id="56940-105">A .NET Framework-based client application is not required to access a data feed.</span></span> <span data-ttu-id="56940-106">任何取用 OData 摘要的應用程式元件都可存取資料服務。</span><span class="sxs-lookup"><span data-stu-id="56940-106">The data service can be accessed by any application component that consumes an OData feed.</span></span> <span data-ttu-id="56940-107">如需詳細資訊，請參閱[在用戶端應用程式中使用資料服務](using-a-data-service-in-a-client-application-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="56940-107">For more information, see [Using a Data Service in a Client Application](using-a-data-service-in-a-client-application-wcf-data-services.md).</span></span>

## <a name="to-create-the-client-application-by-using-visual-studio"></a><span data-ttu-id="56940-108">若要使用 Visual Studio 建立用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="56940-108">To create the client application by using Visual Studio</span></span>

1. <span data-ttu-id="56940-109">在**方案總管**中，以滑鼠右鍵按一下方案，然後按一下 [**加入**]，再按一下 [**新增專案**]。</span><span class="sxs-lookup"><span data-stu-id="56940-109">In **Solution Explorer**, right-click the solution, click **Add**, and then click **New Project**.</span></span>

2. <span data-ttu-id="56940-110">在左窗格中，選取 [**已安裝**] > [**視覺C#效果**] 或 [ **Visual Basic**] > **Windows 桌面**]，然後選取 [ **WPF 應用程式** 範本。</span><span class="sxs-lookup"><span data-stu-id="56940-110">In the left pane, select **Installed** > [**Visual C#** or **Visual Basic**] > **Windows Desktop**, and then select the **WPF App** template.</span></span>

3. <span data-ttu-id="56940-111">輸入 `NorthwindClient` 作為 [專案名稱]，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="56940-111">Enter `NorthwindClient` for the project name, and then click **OK**.</span></span>

4. <span data-ttu-id="56940-112">開啟 MainWindow.xaml 檔案，並以下列程式碼取代 XAML 程式碼：</span><span class="sxs-lookup"><span data-stu-id="56940-112">Open the file MainWindow.xaml and replace the XAML code with the following code:</span></span>

     [!code-xaml[Astoria Quickstart Client#Window1Xaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_client/vb/window1.xaml#window1xaml)]

## <a name="to-add-a-data-service-reference-to-the-project"></a><span data-ttu-id="56940-113">若要將資料服務參考加入至專案</span><span class="sxs-lookup"><span data-stu-id="56940-113">To add a data service reference to the project</span></span>

1. <span data-ttu-id="56940-114">在**方案總管**中，以滑鼠右鍵按一下 NorthwindClient 專案，按一下 [**加入** > **服務參考**]，然後按一下 [**探索**]。</span><span class="sxs-lookup"><span data-stu-id="56940-114">In **Solution Explorer**, right-click the NorthwindClient project, click **Add** > **Service Reference**, and then click **Discover**.</span></span>

     <span data-ttu-id="56940-115">這會顯示您在第一個工作中建立的 Northwind 資料服務。</span><span class="sxs-lookup"><span data-stu-id="56940-115">This displays the Northwind data service that you created in the first task.</span></span>

2. <span data-ttu-id="56940-116">在 [**命名空間**] 文字方塊中，輸入 `Northwind`，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="56940-116">In the **Namespace** text box, type `Northwind`, and then click **OK**.</span></span>

     <span data-ttu-id="56940-117">這會將新的程式碼檔案加入至專案中，此專案包含的資料類別可用來存取做為物件的資料服務資源，並與之進行互動。</span><span class="sxs-lookup"><span data-stu-id="56940-117">This adds a new code file to the project, which contains the data classes that are used to access and interact with data service resources as objects.</span></span> <span data-ttu-id="56940-118">在命名空間 `NorthwindClient.Northwind` 中建立資料類別。</span><span class="sxs-lookup"><span data-stu-id="56940-118">The data classes are created in the namespace `NorthwindClient.Northwind`.</span></span>

## <a name="to-access-data-service-data-in-the-wpf-application"></a><span data-ttu-id="56940-119">在 WPF 應用程式中存取資料服務的資料</span><span class="sxs-lookup"><span data-stu-id="56940-119">To access data service data in the WPF application</span></span>

1. <span data-ttu-id="56940-120">在 [ **NorthwindClient**] 下的**方案總管**中，以滑鼠右鍵按一下專案，然後按一下 [**加入參考**]。</span><span class="sxs-lookup"><span data-stu-id="56940-120">In **Solution Explorer** under **NorthwindClient**, right-click the project and click **Add Reference**.</span></span>

2. <span data-ttu-id="56940-121">在 [**加入參考**] 對話方塊中，按一下 [ **.net** ] 索引標籤，選取 [system.web] 元件，然後按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="56940-121">In the **Add Reference** dialog box, click the **.NET** tab, select the System.Data.Services.Client.dll assembly, and then click **OK**.</span></span>

3. <span data-ttu-id="56940-122">在 [ **NorthwindClient**] 下的**方案總管**中，開啟 mainwindow.xaml 檔案的字碼頁，然後在 Visual Basic 中加入下列 `using` 語句（`Imports`）。</span><span class="sxs-lookup"><span data-stu-id="56940-122">In **Solution Explorer** under **NorthwindClient**, open the code page for the MainWindow.xaml file, and add the following `using` statement (`Imports` in Visual Basic).</span></span>

    [!code-csharp[Astoria Quickstart Client#Using](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_client/cs/window1.xaml.cs#using)]
    [!code-vb[Astoria Quickstart Client#Using](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_client/vb/window1.xaml.vb#using)]

4. <span data-ttu-id="56940-123">插入下列查詢資料服務的程式碼，並將 <xref:System.Data.Services.Client.DataServiceCollection%601> 的結果繫結到 `MainWindow` 類別裡：</span><span class="sxs-lookup"><span data-stu-id="56940-123">Insert the following code that queries that data service and binds the result to a <xref:System.Data.Services.Client.DataServiceCollection%601> into the `MainWindow` class:</span></span>

    > [!NOTE]
    > <span data-ttu-id="56940-124">您必須用裝載 Northwind 資料服務之執行個體的伺服器及連接埠來取代主機名稱 `localhost:12345`。</span><span class="sxs-lookup"><span data-stu-id="56940-124">You must replace the host name `localhost:12345` with the server and port that is hosting your instance of the Northwind data service.</span></span>

     [!code-csharp[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_client/cs/window1.xaml.cs#querycode)]
     [!code-vb[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_client/vb/window1.xaml.vb#querycode)]

5. <span data-ttu-id="56940-125">將下列儲存變更的程式碼插入 `MainWindow` 類別中：</span><span class="sxs-lookup"><span data-stu-id="56940-125">Insert the following code that saves changes into the `MainWindow` class:</span></span>

     [!code-csharp[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_client/cs/window1.xaml.cs#savechanges)]
     [!code-vb[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_client/vb/window1.xaml.vb#savechanges)]

## <a name="to-build-and-run-the-northwindclient-application"></a><span data-ttu-id="56940-126">建置和執行 NorthwindClient 應用程式</span><span class="sxs-lookup"><span data-stu-id="56940-126">To build and run the NorthwindClient application</span></span>

1. <span data-ttu-id="56940-127">在**方案總管**中，以滑鼠右鍵按一下 NorthwindClient 專案，然後選取 [**設定為啟始專案**]。</span><span class="sxs-lookup"><span data-stu-id="56940-127">In **Solution Explorer**, right-click the NorthwindClient project and select **Set as startup project**.</span></span>

2. <span data-ttu-id="56940-128">按**F5**啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="56940-128">Press **F5** to start the application.</span></span>

     <span data-ttu-id="56940-129">如此會建置方案，並啟動用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="56940-129">This builds the solution and starts the client application.</span></span> <span data-ttu-id="56940-130">從服務要求資料，並顯示在主控台中。</span><span class="sxs-lookup"><span data-stu-id="56940-130">Data is requested from the service and displayed in the console.</span></span>

3. <span data-ttu-id="56940-131">在資料格的 [**數量**] 資料行中編輯值，然後按一下 [**儲存**]。</span><span class="sxs-lookup"><span data-stu-id="56940-131">Edit a value in the **Quantity** column of the data grid, and then click **Save**.</span></span>

     <span data-ttu-id="56940-132">資料服務的變更會被儲存。</span><span class="sxs-lookup"><span data-stu-id="56940-132">Changes are saved to the data service.</span></span>

    > [!NOTE]
    > <span data-ttu-id="56940-133">此版本的 NorthwindClient 應用程式不支援新增及刪除實體。</span><span class="sxs-lookup"><span data-stu-id="56940-133">This version of the NorthwindClient application does not support adding and deleting of entities.</span></span>

## <a name="next-steps"></a><span data-ttu-id="56940-134">後續步驟</span><span class="sxs-lookup"><span data-stu-id="56940-134">Next Steps</span></span>

<span data-ttu-id="56940-135">您已成功建立存取範例 Northwind OData 摘要的用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="56940-135">You have successfully created the client application that accesses the sample Northwind OData feed.</span></span> <span data-ttu-id="56940-136">您也已完成 WCF Data Services 快速入門！</span><span class="sxs-lookup"><span data-stu-id="56940-136">You've also completed the WCF Data Services quickstart!</span></span>

<span data-ttu-id="56940-137">如需從 .NET Framework 應用程式存取 OData 摘要的詳細資訊，請參閱[WCF Data Services 用戶端程式庫](wcf-data-services-client-library.md)。</span><span class="sxs-lookup"><span data-stu-id="56940-137">For more information about accessing an OData feed from a .NET Framework application, see [WCF Data Services Client Library](wcf-data-services-client-library.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="56940-138">請參閱</span><span class="sxs-lookup"><span data-stu-id="56940-138">See also</span></span>

- [<span data-ttu-id="56940-139">使用者入門</span><span class="sxs-lookup"><span data-stu-id="56940-139">Getting Started</span></span>](getting-started-with-wcf-data-services.md)
- [<span data-ttu-id="56940-140">資源</span><span class="sxs-lookup"><span data-stu-id="56940-140">Resources</span></span>](wcf-data-services-resources.md)
