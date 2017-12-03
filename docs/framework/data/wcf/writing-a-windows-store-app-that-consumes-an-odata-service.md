---
title: "撰寫使用 OData 服務的 Windows 市集應用程式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: csharp
ms.assetid: 9917a0e9-ec93-49e5-a366-fd39b892eb8b
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eeee9dcf27d63f5bc40dfdfce1ff7d8104060b6a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="writing-a-windows-store-app-that-consumes-an-odata-service"></a><span data-ttu-id="4e3fa-102">撰寫使用 OData 服務的 Windows 市集應用程式</span><span class="sxs-lookup"><span data-stu-id="4e3fa-102">Writing a Windows Store App that consumes an OData Service</span></span>
<span data-ttu-id="4e3fa-103">Windows 8 引入新的應用程式類型： Windows 市集應用程式。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-103">Windows 8 introduces a new type of application: the Windows Store app.</span></span> <span data-ttu-id="4e3fa-104">Windows 市集應用程式具有全新的外觀及操作，可在多種裝置上執行，並透過 Windows 市集提供。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-104">Windows Store apps have a brand new look and feel, run on a variety of devices, and are made available on the Windows Store.</span></span> <span data-ttu-id="4e3fa-105">本主題說明如何撰寫使用 OData 服務 (尤其是 NetFlix Catalog OData 服務) 的 Windows 市集應用程式。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-105">This topic describes how to write a Windows Store app that consumes an OData service, specifically the NetFlix Catalog OData service.</span></span> <span data-ttu-id="4e3fa-106">如需 Windows 市集應用程式的詳細資訊，請閱讀[Windows 市集應用程式使用者入門](http://msdn.microsoft.com/library/windows/apps/br211386.aspx)。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-106">For more information about Windows Store Apps, please read [Getting Started with Windows Store apps](http://msdn.microsoft.com/library/windows/apps/br211386.aspx).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="4e3fa-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="4e3fa-107">Prerequisites</span></span>  
  
1.  [<span data-ttu-id="4e3fa-108">Microsoft Windows 8</span><span class="sxs-lookup"><span data-stu-id="4e3fa-108">Microsoft Windows 8</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=266654)  
  
2.  [<span data-ttu-id="4e3fa-109">Microsoft Visual Studio 2012</span><span class="sxs-lookup"><span data-stu-id="4e3fa-109">Microsoft Visual Studio 2012</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=266655)  
  
3.  [<span data-ttu-id="4e3fa-110">WCF 資料服務</span><span class="sxs-lookup"><span data-stu-id="4e3fa-110">WCF Data Services</span></span>](http://msdn.microsoft.com/data/bb931106)  
  
#### <a name="creating-the-default-windows-store-grid-application"></a><span data-ttu-id="4e3fa-111">建立預設 Windows 市集格線應用程式</span><span class="sxs-lookup"><span data-stu-id="4e3fa-111">Creating the default Windows Store Grid Application</span></span>  
  
1.  <span data-ttu-id="4e3fa-112">使用 C# 和 XAML 建立新的 Windows 市集格線應用程式。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-112">Create a new Windows Store Grid Application using C# and XAML.</span></span> <span data-ttu-id="4e3fa-113">將應用程式命名為 OData.WindowsStore.NetflixDemo：</span><span class="sxs-lookup"><span data-stu-id="4e3fa-113">Name the application OData.WindowsStore.NetflixDemo:</span></span>  
  
     <span data-ttu-id="4e3fa-114">![新增專案 對話方塊](../../../../docs/framework/data/wcf/media/win8clientcreatenewproject.png "Win8ClientCreateNewProject")</span><span class="sxs-lookup"><span data-stu-id="4e3fa-114">![New Project Dialog](../../../../docs/framework/data/wcf/media/win8clientcreatenewproject.png "Win8ClientCreateNewProject")</span></span>  
  
2.  <span data-ttu-id="4e3fa-115">開啟 Package.appxmanifest，然後在顯示名稱文字方塊中輸入易記名稱。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-115">Open the Package.appxmanifest and enter a friendly name in the Display name text box.</span></span> <span data-ttu-id="4e3fa-116">這會指定搭配 Windows 8 搜尋功能使用的應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-116">This specifies the application name used with the Windows 8 search functionality.</span></span>  
  
     <span data-ttu-id="4e3fa-117">![應用程式資訊清單檔](../../../../docs/framework/data/wcf/media/appxmanifest.png "appxmanifest")</span><span class="sxs-lookup"><span data-stu-id="4e3fa-117">![Application manifest file](../../../../docs/framework/data/wcf/media/appxmanifest.png "appxmanifest")</span></span>  
  
3.  <span data-ttu-id="4e3fa-118">輸入中的易記名稱\<AppName > App.xaml 檔案中的項目。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-118">Enter a friendly name in the \<AppName> element in the App.xaml file.</span></span> <span data-ttu-id="4e3fa-119">這會設定應用程式啟動時所顯示的應用程式名稱：</span><span class="sxs-lookup"><span data-stu-id="4e3fa-119">This sets the application name that is displayed when the application is launched:</span></span>  
  
     <span data-ttu-id="4e3fa-120">![App.xaml 檔案](../../../../docs/framework/data/wcf/media/appxaml.png "appxaml")</span><span class="sxs-lookup"><span data-stu-id="4e3fa-120">![App.xaml file](../../../../docs/framework/data/wcf/media/appxaml.png "appxaml")</span></span>  
  
4.  <span data-ttu-id="4e3fa-121">建置並啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-121">Build and launch the application.</span></span> <span data-ttu-id="4e3fa-122">請先參閱應用程式的啟動顯示畫面。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-122">You first see the application’s splash screen.</span></span> <span data-ttu-id="4e3fa-123">下面的螢幕擷取畫面顯示預設啟動顯示畫面。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-123">The screenshot below displays the default splash screen.</span></span> <span data-ttu-id="4e3fa-124">使用的影像儲存在專案的 Assets 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-124">The image used is stored in the project’s Assets folder.</span></span>  
  
     <span data-ttu-id="4e3fa-125">![預設應用程式啟動顯示畫面](../../../../docs/framework/data/wcf/media/defualtappsplash.png "defualtAppSplash")</span><span class="sxs-lookup"><span data-stu-id="4e3fa-125">![The default app splash screen](../../../../docs/framework/data/wcf/media/defualtappsplash.png "defualtAppSplash")</span></span>  
  
     <span data-ttu-id="4e3fa-126">然後，應用程式便會顯示。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-126">Then the application will be displayed.</span></span>  
  
     <span data-ttu-id="4e3fa-127">![預設的應用程式](../../../../docs/framework/data/wcf/media/defaultapplication.png "DefaultApplication")</span><span class="sxs-lookup"><span data-stu-id="4e3fa-127">![The default application](../../../../docs/framework/data/wcf/media/defaultapplication.png "DefaultApplication")</span></span>  
  
     <span data-ttu-id="4e3fa-128">預設應用程式在 SampleDataSource.cs 中定義一組類別：SampleDataGroup 和 SampleDataItem，兩者都是衍生自 SampleDataCommon，而 SampleDataCommon 本身則衍生自 BindableBase。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-128">The default application defines a set of classes in SampleDataSource.cs: SampleDataGroup and SampleDataItem, both of which are derived from SampleDataCommon, which itself is derived from BindableBase.</span></span> <span data-ttu-id="4e3fa-129">SampleDataGroup 和 SampleDataItem 會繫結至預設 GridView。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-129">SampleDataGroup and SampleDataItem are bound to the default GridView.</span></span> <span data-ttu-id="4e3fa-130">SampleDataSource.cs 位於 NetflixDemo 專案內的 DataModel 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-130">SampleDataSource.cs is located in the DataModel folder within the NetflixDemo project.</span></span> <span data-ttu-id="4e3fa-131">此應用程式會顯示群組集合。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-131">The application displays a grouped collection.</span></span> <span data-ttu-id="4e3fa-132">每個群組包含任何數目的項目，分別由 SampleDataGroup 和 SampleDataItem 表示。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-132">Each group contains any number of items, represented by SampleDataGroup and SampleDataItem, respectively.</span></span> <span data-ttu-id="4e3fa-133">在上一個螢幕擷取畫面中，您會看到稱為「群組標題 1」的一個群組，並同時顯示群組中的所有項目。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-133">In the previous screen shot you can see a group called Group Title 1 and all of the items in the group displayed together.</span></span>  
  
     <span data-ttu-id="4e3fa-134">應用程式的主頁面是 GroupedItemsPage.xaml。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-134">The main page of the application is GroupedItemsPage.xaml.</span></span> <span data-ttu-id="4e3fa-135">其中包含的 GridView 會顯示 SampleDataSource.cs 類別所建立的範例資料。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-135">It contains a GridView that displays the sample data created by the SampleDataSource.cs class.</span></span> <span data-ttu-id="4e3fa-136">GroupedItemsPage 是由 App.xaml.cs 呼叫 rootFrame.Navigate 所載入：</span><span class="sxs-lookup"><span data-stu-id="4e3fa-136">The GroupedItemsPage is loaded by the App.xaml.cs in a call to rootFrame.Navigate:</span></span>  
  
    ```csharp  
    if (!rootFrame.Navigate(typeof(GroupedItemsPage), "AllGroups"))  
    {  
        throw new Exception("Failed to create initial page");  
    }  
    ```  
  
     <span data-ttu-id="4e3fa-137">這會具現化 GroupedItemsPage，並呼叫其 LoadState 方法。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-137">This causes the GroupedItemsPage to be instantiated and it’s LoadState method is called.</span></span> <span data-ttu-id="4e3fa-138">LoadState 會建立靜態 SampleDataSource 執行個體，再由其建立 SampleDataGroup 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-138">LoadState causes the static SampleDataSource instance to be created, which creates a collection of SampleDataGroup objects.</span></span> <span data-ttu-id="4e3fa-139">每個 SampleDataGroup 物件都包含 SampleDataItem 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-139">Each SampleDataGroup object contains a collection of SampleDataItem objects.</span></span> <span data-ttu-id="4e3fa-140">LoadState 在 DefaultViewModel 中儲存 SampleDataGroup 物件的集合：</span><span class="sxs-lookup"><span data-stu-id="4e3fa-140">LoadState stores the collection of SampleDataGroup objects in the DefaultViewModel:</span></span>  
  
    ```csharp  
    protected override void LoadState(Object navigationParameter, Dictionary<String, Object> pageState)  
    {  
        var sampleDataGroups = SampleDataSource.GetGroups((String)navigationParameter);  
        this.DefaultViewModel["Groups"] = sampleDataGroups;  
    }  
    ```  
  
     <span data-ttu-id="4e3fa-141">DefaultViewModel 接著會繫結至 GridView。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-141">The DefaultViewModel is then bound to the GridView.</span></span> <span data-ttu-id="4e3fa-142">這會在設定資料繫結時，於 GroupedItemsPage.xaml 檔案中提供參考。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-142">This is referenced in the GroupedItemsPage.xaml file when configuring the data binding.</span></span>  
  
    ```xaml
    <CollectionViewSource  
                x:Name="groupedItemsViewSource"  
                Source="{Binding Groups}"  
                IsSourceGrouped="true"  
                ItemsPath="TopItems"  
                d:Source="{Binding AllGroups, Source={d:DesignInstance Type=data:SampleDataSource, IsDesignTimeCreatable=True}}"/>  
    ```  
  
     <span data-ttu-id="4e3fa-143">CollectionViewSource 可當做處理群組集合的 Proxy。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-143">The CollectionViewSource is used as a proxy for handling grouped collections.</span></span> <span data-ttu-id="4e3fa-144">進行繫結時，它會逐一查看 SampleDataGroup 物件的集合，以填入 GridView。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-144">When binding occurs, it iterates through the collection of SampleDataGroup objects to populate the GridView.</span></span>  <span data-ttu-id="4e3fa-145">ItemsPath 屬性指示 CollectionViewSource 在每個 SampleDataGroup 物件上，使用哪些屬性來尋找物件所包含的 SampleDataItems。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-145">The ItemsPath attribute tells the CollectionViewSource what property on each SampleDataGroup object to use to find the SampleDataItems it contains.</span></span> <span data-ttu-id="4e3fa-146">在此範例中，每個 SampleDataGroup 物件都包含 SampleDataItem 物件的 TopItems 集合。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-146">In this case each SampleDataGroup object contains a TopItems collection of SampleDataItem objects.</span></span>  
  
     <span data-ttu-id="4e3fa-147">在 Netflix 應用程式中，影片會依內容類型分組。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-147">For the Netflix application, movies are grouped by genre.</span></span> <span data-ttu-id="4e3fa-148">因此，應用程式會顯示一些內容類型及該內容類型中的影片清單。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-148">So the application displays a number of genres and a list of movies within that genre.</span></span>  
  
#### <a name="add-a-service-reference-to-the-netflix-odata-service"></a><span data-ttu-id="4e3fa-149">將服務參考加入 Netflix OData 服務</span><span class="sxs-lookup"><span data-stu-id="4e3fa-149">Add a Service Reference to the Netflix OData Service</span></span>  
  
1.  <span data-ttu-id="4e3fa-150">對 Netflix OData 服務進行任何呼叫之前，必須加入服務參考。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-150">Before we can make any calls to the Netflix OData service we need to add a service reference.</span></span> <span data-ttu-id="4e3fa-151">以滑鼠右鍵按一下 [方案總管] 中的專案，並選取 [加入服務參考]。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-151">Right-click the project in the Solution Explorer and select Add Service Reference…</span></span>  
  
     <span data-ttu-id="4e3fa-152">![加入服務參考對話方塊](../../../../docs/framework/data/wcf/media/addservicereferenceodata.png "AddServiceReferenceOData")</span><span class="sxs-lookup"><span data-stu-id="4e3fa-152">![Add Service Reference Dialog](../../../../docs/framework/data/wcf/media/addservicereferenceodata.png "AddServiceReferenceOData")</span></span>  
  
2.  <span data-ttu-id="4e3fa-153">在位址列中輸入 Netflix OData 服務的 URL，然後按一下 [移至]。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-153">Enter the URL for the Netflix OData service in the Address bar and click Go.</span></span> <span data-ttu-id="4e3fa-154">將服務參考的命名空間設為 Netflix，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-154">Set the Namespace of the service reference to Netflix and click OK.</span></span>  
  
     <span data-ttu-id="4e3fa-155">![加入服務參考錯誤](../../../../docs/framework/data/wcf/media/addservicereferenceerror.png "AddServiceReferenceError")</span><span class="sxs-lookup"><span data-stu-id="4e3fa-155">![Add Service Reference Error](../../../../docs/framework/data/wcf/media/addservicereferenceerror.png "AddServiceReferenceError")</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4e3fa-156">如果您尚未安裝[WCF 資料服務工具為 Windows 市集應用程式](http://go.microsoft.com/fwlink/p/?LinkId=266652)，系統將提示您使用如上述那一個訊息。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-156">If you have not yet installed [WCF Data Services Tools for Windows Store Apps](http://go.microsoft.com/fwlink/p/?LinkId=266652), you will be prompted with a message such as the one above.</span></span> <span data-ttu-id="4e3fa-157">您必須下載並安裝連結中所參考的工具，再繼續進行。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-157">You will need to download and install the tools referenced in the link to continue.</span></span>  
  
 <span data-ttu-id="4e3fa-158">加入服務參考會產生強型別類別，WCF 資料服務將使用此類別來剖析 Netflix OData 服務傳回的 OData。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-158">Adding a service reference generates strongly typed classes that WCF Data Services will use to parse the OData returned by the Netflix OData service.</span></span> <span data-ttu-id="4e3fa-159">在 SampleDataSource.cs 中定義的類別可繫結至 GridView，因此必須將資料從產生的 OData 用戶端類別傳送至 SampleDataSource.cs 中定義之可繫結的類別。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-159">The classes defined in SampleDataSource.cs can be bound to the GridView so we need to transfer the data from the generated OData client classes into the bindable classes defined in SampleDataSource.cs.</span></span>  <span data-ttu-id="4e3fa-160">若要執行這項操作，必須對 SampleDataSource.cs 中定義的資料模型進行一些變更。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-160">In order to do this, we need to make some changes to the data model defined in SampleDataSource.cs.</span></span>  
  
#### <a name="update-the-data-model-for-the-application"></a><span data-ttu-id="4e3fa-161">更新應用程式的資料模型</span><span class="sxs-lookup"><span data-stu-id="4e3fa-161">Update the data model for the application</span></span>  
  
1.  <span data-ttu-id="4e3fa-162">中的程式碼取代現有的程式碼在 SampleDataSource.cs 中[gist](https://gist.github.com/3419288)。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-162">Replace the existing code in SampleDataSource.cs with the code from [this gist](https://gist.github.com/3419288).</span></span> <span data-ttu-id="4e3fa-163">更新的程式碼會加入 LoadMovies 方法 (至 SampleDataSource 類別)，以針對 Netflix OData 服務執行查詢，並填入內容類型 (allGroups) 清單及每種內容類型的影片清單。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-163">The updated code adds a LoadMovies method (to the SampleDataSource class)  that performs a query against the Netflix OData service and populates a list of genres (allGroups) and within each genre a list of movies.</span></span> <span data-ttu-id="4e3fa-164">SampleDataGroup 類別用於表示內容類型，而 SampleDataItem 類別用於表示影片。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-164">The SampleDataGroup class is used to represent a genre and the SampleDataItem class is used to represent a movie.</span></span>  
  
    ```csharp  
    public static async void LoadMovies()  
    {  
        IEnumerable<Title> titles = await ((DataServiceQuery<Title>)Context.Titles  
            .Expand("Genres,AudioFormats,AudioFormats/Language,Awards,Cast")  
            .Where(t => t.Rating == "PG")  
            .OrderByDescending(t => t.ReleaseYear)  
            .Take(300)).ExecuteAsync();  
  
        foreach (Title title in titles)  
        {  
            foreach (Genre netflixGenre in title.Genres)  
            {  
                SampleDataGroup genre = GetGroup(netflixGenre.Name);  
                if (genre == null)  
                {  
                    genre = new SampleDataGroup(netflixGenre.Name, netflixGenre.Name, String.Empty, title.BoxArt.LargeUrl, String.Empty);  
                    Instance.AllGroups.Add(genre);  
                }  
                var content = new StringBuilder();  
                // Write additional things to content here if you want them to display in the item detail.  
                genre.Items.Add(new SampleDataItem(title.Id, title.Name, String.Format("{0}rnrn{1} ({2})", title.Synopsis, title.Rating, title.ReleaseYear), title.BoxArt.HighDefinitionUrl ?? title.BoxArt.LargeUrl, "Description", content.ToString()));  
            }  
        }  
    }  
    ```  
  
     <span data-ttu-id="4e3fa-165">[工作架構非同步模式](http://go.microsoft.com/fwlink/p/?LinkId=266651)(TAP) 用來以非同步方式取得 300 部 (Take) 最近 (OrderByDescending) PG 分級 (Where) 影片從 Netflix。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-165">The [Task-based Asynchronous Pattern](http://go.microsoft.com/fwlink/p/?LinkId=266651) (TAP) is used to asynchronously get 300 (Take) recent (OrderByDescending) PG-rated (Where) movies back from Netflix.</span></span> <span data-ttu-id="4e3fa-166">程式碼的其餘部分會從 OData 摘要傳回的實體，建構 SimpleDataItems 和 SimpleDataGroups。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-166">The rest of the code constructs SimpleDataItems and SimpleDataGroups from the entities that were returned in the OData feed.</span></span>  
  
     <span data-ttu-id="4e3fa-167">SampleDataSource 類別也實作簡單的搜尋方法。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-167">The SampleDataSource class also implements a simple search method.</span></span> <span data-ttu-id="4e3fa-168">在此範例中，該類別會在記憶體中簡單地搜尋載入的影片。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-168">In this case, it does a simple in-memory search of the loaded movies.</span></span>  
  
    ```csharp  
    public static IEnumerable<SampleDataItem> Search(string searchString)  
    {  
            var regex = new Regex(searchString, RegexOptions.CultureInvariant | RegexOptions.IgnoreCase | RegexOptions.IgnorePatternWhitespace);  
            return Instance.AllGroups  
                .SelectMany(g => g.Items)  
                .Where(m => regex.IsMatch(m.Title) || regex.IsMatch(m.Subtitle))  
                    .Distinct(new SampleDataItemComparer());  
    }  
    ```  
  
     <span data-ttu-id="4e3fa-169">另外，還會在 SampleDataSource.cs 中定義稱為 ExtensionMethods 的類別。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-169">Also in SampleDataSource.cs a class called ExtensionMethods is defined.</span></span> <span data-ttu-id="4e3fa-170">這些擴充方法使用 TAP 模式允許 SampleDataSource 執行 OData 查詢，而不封鎖 UI。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-170">Each of these extension methods uses the TAP pattern to allow the SampleDataSource to execute an OData query without blocking the UI.</span></span> <span data-ttu-id="4e3fa-171">例如，下列程式碼使用 Task.Factory.FromAsync 方法實作 TAP。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-171">For example, the following code uses the Task.Factory.FromAsync method to implement TAP.</span></span>  
  
    ```csharp  
    public static async Task<IEnumerable<T>> ExecuteAsync<T>(this DataServiceQuery<T> query)  
    {  
        return await Task.Factory.FromAsync<IEnumerable<T>>(query.BeginExecute(null, null), query.EndExecute);  
    }  
    ```  
  
     <span data-ttu-id="4e3fa-172">如同預設的應用程式，此應用程式的主頁面是 GroupedItemsPage。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-172">As in the default application, the main page of the application is GroupedItemsPage.</span></span> <span data-ttu-id="4e3fa-173">不過，此時會顯示從 Netflix 擷取之依內容類型分組的影片。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-173">This time, however, it displays the movies retrieved from Netflix grouped by genre.</span></span>  <span data-ttu-id="4e3fa-174">具現化 GroupedItemsPage 時，會呼叫其 LoadState 方法。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-174">When the GroupedItemsPage is instantiated, its LoadState method is called.</span></span> <span data-ttu-id="4e3fa-175">如前所述，LoadState 會建立靜態 SampleDataSource 執行個體，並呼叫 Netflix OData 服務。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-175">LoadState causes the static SampleDataSource instance to be created, making a call to the Netflix OData service as discussed previously.</span></span> <span data-ttu-id="4e3fa-176">LoadState 在 DefaultViewModel 中儲存內容類型 (SampleDataGroup 物件) 的集合：</span><span class="sxs-lookup"><span data-stu-id="4e3fa-176">LoadState stores the collection of genres (SampleDataGroup objects) in the DefaultViewModel:</span></span>  
  
    ```csharp  
    protected override void LoadState(Object navigationParameter, Dictionary<String, Object> pageState)  
    {  
  
        var sampleDataGroups = SampleDataSource.GetGroups((String)navigationParameter);  
        this.DefaultViewModel["Groups"] = sampleDataGroups;  
    }  
    ```  
  
     <span data-ttu-id="4e3fa-177">如前所述，接著會使用 DefaultViewModel 將資料繫結至 GridView。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-177">As described previously, the DefaultViewModel is then used to bind the data to the GridView.</span></span>  
  
#### <a name="add-a-search-contract-to-allow-the-application-to-participate-in-windows-search"></a><span data-ttu-id="4e3fa-178">加入搜尋合約，讓應用程式參與 Windows 搜尋</span><span class="sxs-lookup"><span data-stu-id="4e3fa-178">Add a search contract to allow the application to participate in Windows search</span></span>  
  
1.  <span data-ttu-id="4e3fa-179">將搜尋合約加入應用程式中。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-179">Add a search contract to the application.</span></span> <span data-ttu-id="4e3fa-180">如此可讓應用程式與 Windows 8 搜尋體驗進行整合。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-180">This allows the application to integrate with the Windows 8 search experience.</span></span> <span data-ttu-id="4e3fa-181">將搜尋合約命名為 SearchResultsPage.xaml</span><span class="sxs-lookup"><span data-stu-id="4e3fa-181">Name the search contract SearchResultsPage.xaml</span></span>  
  
     <span data-ttu-id="4e3fa-182">![加入搜尋合約](../../../../docs/framework/data/wcf/media/addsearchcontract.png "AddSearchContract")</span><span class="sxs-lookup"><span data-stu-id="4e3fa-182">![Add a search contract](../../../../docs/framework/data/wcf/media/addsearchcontract.png "AddSearchContract")</span></span>  
  
2.  <span data-ttu-id="4e3fa-183">移除 queryText 前後的內嵌引號，即可修改 SearchResultsPage.xaml.cs 的第 58 行。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-183">Modify line 58 of SearchResultsPage.xaml.cs by removing the embedded quotes around queryText.</span></span>  
  
    ```csharp  
    // Communicate results through the view model  
    this.DefaultViewModel["QueryText"] = queryText;  
    this.DefaultViewModel["Filters"] = filterList;  
    this.DefaultViewModel["ShowFilters"] = filterList.Count > 1;  
    ```  
  
3.  <span data-ttu-id="4e3fa-184">在 SearchResultsPage.xaml.cs 的第 81 行插入下列兩行程式碼，以擷取搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-184">Insert the following two lines of code at line 81 in SearchResultsPage.xaml.cs to retrieve the search results.</span></span>  
  
    ```csharp  
    // TODO: Respond to the change in active filter by setting this.DefaultViewModel["Results"]  
                    //       to a collection of items with bindable Image, Title, Subtitle, and Description properties  
                    var searchValue = (string)this.DefaultViewModel["QueryText"];  
                    this.DefaultViewModel["Results"] = new List<SampleDataItem>(SampleDataSource.Search(searchValue));  
    ```  
  
 <span data-ttu-id="4e3fa-185">當使用者叫用 Windows 搜尋時，輸入搜尋字詞，然後觸碰搜尋列中的 Netflix Demo 應用程式圖示，即會執行 SearchResultsPage 的 LoadState 方法。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-185">When a user invokes Windows search, types in a search term and then touches the Netflix Demo app icon in the search bar, the LoadState method of the SearchResultsPage is executed.</span></span> <span data-ttu-id="4e3fa-186">傳送至 LoadState 的巡覽參數包含查詢文字。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-186">The navigation parameter sent to LoadState contains the query text.</span></span> <span data-ttu-id="4e3fa-187">接著呼叫 Filter_SelectionChanged 方法，再呼叫 SampleDataSource 類別上的 Search 方法。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-187">Next the Filter_SelectionChanged method is called which then calls the Search method on the SampleDataSource class.</span></span> <span data-ttu-id="4e3fa-188">所傳回的結果會顯示在 SearchResultsPage.xaml 頁面上。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-188">The results are returned and displayed in the SearchResultsPage.xaml page.</span></span>  
  
```csharp  
/// <summary>  
        /// Invoked when a filter is selected using the ComboBox in snapped view state.  
        /// </summary>  
        /// <param name="sender">The ComboBox instance.</param>  
        /// <param name="e">Event data describing how the selected filter was changed.</param>  
        void Filter_SelectionChanged(object sender, SelectionChangedEventArgs e)  
        {  
            // Determine what filter was selected  
            var selectedFilter = e.AddedItems.FirstOrDefault() as Filter;  
            if (selectedFilter != null)  
            {  
                // Mirror the results into the corresponding Filter object to allow the  
                // RadioButton representation used when not snapped to reflect the change  
                selectedFilter.Active = true;  
  
                // TODO: Respond to the change in active filter by setting this.DefaultViewModel["Results"]  
                //       to a collection of items with bindable Image, Title, Subtitle, and Description properties  
                var searchValue = (string)this.DefaultViewModel["QueryText"];  
                this.DefaultViewModel["Results"] = new List<SampleDataItem>(SampleDataSource.Search(searchValue));  
  
                // Ensure results are found  
                object results;  
                ICollection resultsCollection;  
                if (this.DefaultViewModel.TryGetValue("Results", out results) &&  
                    (resultsCollection = results as ICollection) != null &&  
                    resultsCollection.Count != 0)  
                {  
                    VisualStateManager.GoToState(this, "ResultsFound", true);  
                    return;  
                }  
            }  
  
            // Display informational text when there are no search results.  
            VisualStateManager.GoToState(this, "NoResultsFound", true);  
        }  
```  
  
 <span data-ttu-id="4e3fa-189">如需詳細資訊，將搜尋整合至應用程式，請參閱[搜尋： 整合到 Windows 8 搜尋體驗](http://go.microsoft.com/fwlink/p/?LinkId=266650)。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-189">For more information on integrating search into an application see, [Search: integrating into the Windows 8 search experience](http://go.microsoft.com/fwlink/p/?LinkId=266650).</span></span>  
  
## <a name="run-the-application"></a><span data-ttu-id="4e3fa-190">執行應用程式</span><span class="sxs-lookup"><span data-stu-id="4e3fa-190">Run the application</span></span>  
 <span data-ttu-id="4e3fa-191">按 F5 鍵啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-191">Launch the application by pressing F5.</span></span> <span data-ttu-id="4e3fa-192">請注意，應用程式啟動之後，需要幾秒鐘的時間載入影像。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-192">Note that it will take a few seconds to load the images upon application launch.</span></span> <span data-ttu-id="4e3fa-193">此外，您的第一個搜尋嘗試可能不會傳回任何結果。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-193">Also, your first search attempt may not return any results.</span></span> <span data-ttu-id="4e3fa-194">在實際的應用程式中，您會想要處理這兩個問題。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-194">In a real-world application, you would want to deal with both of these issues.</span></span>  
  
 <span data-ttu-id="4e3fa-195">應用程式會呼叫 Netflix OData 服務，接收所產生之 OData 用戶端類別中的資料，然後將該資料傳送至可繫結的資料類別 (SampleDataSource、SampleDataGroup 和 SampleDataItem)。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-195">The application calls the Netflix OData service, receives the data in the generated OData client classes and then transfers that data to bindable data classes (SampleDataSource, SampleDataGroup, and SampleDataItem).</span></span> <span data-ttu-id="4e3fa-196">接著使用這些可繫結的類別，將資料繫結至 GridView。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-196">It uses these bindable classes to bind the data to the GridView.</span></span> <span data-ttu-id="4e3fa-197">如果您不熟悉 XAML 資料繫結如何運作，請參閱[群組清單或方格 （Windows 市集應用程式使用 C# /vb/c + + 和 XAML） 中的項目如何](http://msdn.microsoft.com/library/windows/apps/xaml/hh780627)。</span><span class="sxs-lookup"><span data-stu-id="4e3fa-197">If you are unfamiliar with how XAML databinding works see [How to group items in a list or grid (Windows Store apps using C#/VB/C++ and XAML)](http://msdn.microsoft.com/library/windows/apps/xaml/hh780627).</span></span>
