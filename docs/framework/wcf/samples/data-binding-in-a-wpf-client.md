---
title: Windows Presentation Foundation 用戶端中的資料繫結
ms.date: 03/30/2017
ms.assetid: bb8c8293-5973-4aef-9b07-afeff5d3293c
ms.openlocfilehash: a5e3e06afbe790af7c791449a2fe1bfc1bde372e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69953552"
---
# <a name="data-binding-in-a-windows-presentation-foundation-client"></a><span data-ttu-id="06a76-102">Windows Presentation Foundation 用戶端中的資料繫結</span><span class="sxs-lookup"><span data-stu-id="06a76-102">Data Binding in a Windows Presentation Foundation Client</span></span>
<span data-ttu-id="06a76-103">這個範例示範使用 Windows Presentation Foundation (WPF) 用戶端中的資料繫結。</span><span class="sxs-lookup"><span data-stu-id="06a76-103">This sample demonstrates the use of data binding in a Windows Presentation Foundation (WPF) client.</span></span> <span data-ttu-id="06a76-104">此範例會使用 Windows Communication Foundation (WCF) 服務, 隨機產生專輯陣列以傳回用戶端。</span><span class="sxs-lookup"><span data-stu-id="06a76-104">The sample uses a Windows Communication Foundation (WCF) service that randomly generates an array of albums to return to the client.</span></span> <span data-ttu-id="06a76-105">每張專輯各有名稱、價格和曲目表。</span><span class="sxs-lookup"><span data-stu-id="06a76-105">Each album has a name, a price, and a list of album tracks.</span></span> <span data-ttu-id="06a76-106">曲目有名稱和時間長度。</span><span class="sxs-lookup"><span data-stu-id="06a76-106">The album tracks have a name and duration.</span></span> <span data-ttu-id="06a76-107">服務所傳回的資訊會自動系結至 Windows Presentation Foundation (WPF) 用戶端所提供的使用者介面 (UI)。</span><span class="sxs-lookup"><span data-stu-id="06a76-107">The information that is returned by the service is automatically bound to the user interface (UI) provided by the Windows Presentation Foundation (WPF) client.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="06a76-108">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="06a76-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="06a76-109">資料繫結允許資料來源自動繫結至 UI。</span><span class="sxs-lookup"><span data-stu-id="06a76-109">Data binding allows a data source to be automatically bound to a UI.</span></span> <span data-ttu-id="06a76-110">這可以簡化程式設計模型，因為您不必透過程式設計方式，使用資料物件或資料物件陣列中的資料來更新每個 UI 項目。</span><span class="sxs-lookup"><span data-stu-id="06a76-110">This simplifies the programming model because it does not require that you programmatically update each UI element with the data from a data object or an array of data objects.</span></span> <span data-ttu-id="06a76-111">您可以將物件繫結至單一 UI 項目，或是將陣列繫結至接受多個輸入的控制項，例如`ListBox`。</span><span class="sxs-lookup"><span data-stu-id="06a76-111">You can bind an object to a single UI element or an array to a control that takes multiple inputs, such as a `ListBox`.</span></span> <span data-ttu-id="06a76-112">下列程式碼示範如何將資料繫結至 UI 項目的 `DataContext`。</span><span class="sxs-lookup"><span data-stu-id="06a76-112">The following code shows how to bind data to the `DataContext` of a UI element.</span></span>  
  
```  
// Event handler executed when call is complete  
void client_GetAlbumListCompleted(object sender, GetAlbumListCompletedEventArgs e)  
{  
    // This is on the UI thread, myPanel can be accessed directly  
    myPanel.DataContext = e.Result;   
}  
```  
  
 <span data-ttu-id="06a76-113">在前面的範例中，名為 `DataContext` 之 `grid` 配置項目的 `myPanel` 會設定為 `GetAlbumList` 方法所傳回的資料。</span><span class="sxs-lookup"><span data-stu-id="06a76-113">In the previous sample, the `DataContext` for the `grid` layout element named `myPanel` is set to the data returned by the `GetAlbumList` method.</span></span> <span data-ttu-id="06a76-114">`DataContext` 允許項目從父項目繼承有關用於繫結之資料來源的資訊，以及繫結的其他特性 (例如，路徑)。</span><span class="sxs-lookup"><span data-stu-id="06a76-114">The `DataContext` allows elements to inherit information from their parent elements about the data source that is used for binding, as well as other characteristics of the binding such as the path.</span></span> <span data-ttu-id="06a76-115">每次更新伺服器上的資料時都必須執行此一程式碼行。</span><span class="sxs-lookup"><span data-stu-id="06a76-115">The line of code must be executed every time the data on the server is updated.</span></span> <span data-ttu-id="06a76-116">例如，當初始化視窗以及增加新專輯時，就會執行它。</span><span class="sxs-lookup"><span data-stu-id="06a76-116">For example, it is executed when the window is initialized and when a new album is added.</span></span>  
  
 <span data-ttu-id="06a76-117">在下列範例 XAML 程式碼中，`ListBox` 會指定 `ItemsSource="{Binding }"`。</span><span class="sxs-lookup"><span data-stu-id="06a76-117">In the following sample XAML code, the `ListBox` specifies `ItemsSource="{Binding }"`.</span></span>  
  
```xml  
<ListBox   
          ItemTemplate="{StaticResource AlbumStyle}"  
          ItemsSource="{Binding }"   
          IsSynchronizedWithCurrentItem="true" />  
```  
  
 <span data-ttu-id="06a76-118">這會指定繫結於最上層 UI 項目的資料也要繫結至這個控制項 (即專輯的陣列)。</span><span class="sxs-lookup"><span data-stu-id="06a76-118">This specifies that the data bound to the top-level UI element is also bound to this control (that is, the array of Albums).</span></span> <span data-ttu-id="06a76-119">此外，`ItemTemplate="{StaticResource AlbumStyle}"` 還會指定要用於 `ListBox` 中每個項目的資料範本。</span><span class="sxs-lookup"><span data-stu-id="06a76-119">In addition, `ItemTemplate="{StaticResource AlbumStyle}"` specifies the data template to be used for each item in the `ListBox`.</span></span> <span data-ttu-id="06a76-120">您也可以定義資料範本來指定資料的格式化方式。</span><span class="sxs-lookup"><span data-stu-id="06a76-120">You can also define data templates to specify how the data should be formatted.</span></span> <span data-ttu-id="06a76-121">您可以對應用程式中的其他 UI 項目重複使用這些資料範本，其好處是只需在同一處定義和維護資料範本。</span><span class="sxs-lookup"><span data-stu-id="06a76-121">These data templates can be reused for other UI elements in the application, the advantage is that the data template is defined and maintained in one place.</span></span>  
  
 <span data-ttu-id="06a76-122">`AlbumStyle` 資料範本會將方格與兩個 `TextBlock` 並排配置在一起。</span><span class="sxs-lookup"><span data-stu-id="06a76-122">The `AlbumStyle` data template lays out a grid with two `TextBlock`s side by side.</span></span> <span data-ttu-id="06a76-123">一個指定專輯的名稱，另一個則指定專輯中的曲目。</span><span class="sxs-lookup"><span data-stu-id="06a76-123">One specifies the name of the Album and the other the number of Tracks in the album.</span></span>  
  
```xaml  
<DataTemplate x:Key="AlbumStyle">  
    <Grid>  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition Width="260" />  
            <ColumnDefinition Width="60" />  
        </Grid.ColumnDefinitions>  
        <TextBlock Grid.Column="0" TextContent="{Binding Path=Title}" />  
        <TextBlock Grid.Column="1" TextContent="{Binding Path=Tracks#.Count}" HorizontalAlignment="Right" />  
    </Grid>  
</DataTemplate>  
```  
  
 <span data-ttu-id="06a76-124">下列 XAML 程式碼會建立第二個 `ListBox`。</span><span class="sxs-lookup"><span data-stu-id="06a76-124">The following XAML code creates a second `ListBox`.</span></span>  
  
```xaml  
<ListBox Grid.Row="2"   
            Grid.ColumnSpan="2"   
            ItemTemplate="{StaticResource TrackStyle}"  
            ItemsSource="{Binding Path=Tracks}" />  
```  
  
 <span data-ttu-id="06a76-125">程式碼會指定 `ItemsSource` 的路徑。</span><span class="sxs-lookup"><span data-stu-id="06a76-125">The code specifies a path for the `ItemsSource`.</span></span> <span data-ttu-id="06a76-126">這表示繫結至此控制項的資料不是最上層資料，而是名為 `Tracks` 之最上層資料的屬性。</span><span class="sxs-lookup"><span data-stu-id="06a76-126">This indicates that the data bound to this control is not the top-level data but a property of the top-level data named `Tracks`.</span></span> <span data-ttu-id="06a76-127">這個屬性代表專輯內所含曲目的陣列。</span><span class="sxs-lookup"><span data-stu-id="06a76-127">This property represents the array of tracks contained within the album.</span></span> <span data-ttu-id="06a76-128">此外，還會指定不同的 `DataTemplate`，其名稱為 `TrackStyle`。</span><span class="sxs-lookup"><span data-stu-id="06a76-128">In addition, a different `DataTemplate` named `TrackStyle` is specified.</span></span> <span data-ttu-id="06a76-129">`TrackStyle` 範本的配置與 `AlbumStyle` 範本的配置相似，但 `TextBlock` 是繫結於不同的屬性。</span><span class="sxs-lookup"><span data-stu-id="06a76-129">The layout of the `TrackStyle` template is similar to that of the `AlbumStyle` template, but the `TextBlock`s are bound to different properties.</span></span> <span data-ttu-id="06a76-130">這是因為兩個範本各自使用於不同的資料物件。</span><span class="sxs-lookup"><span data-stu-id="06a76-130">This is because the two templates are used with different data objects.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="06a76-131">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="06a76-131">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="06a76-132">請確定您已[針對 Windows Communication Foundation 範例執行一次安裝程式](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="06a76-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="06a76-133">若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="06a76-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="06a76-134">若要在單一或跨電腦設定中執行範例, 請遵循執行[Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)中的指示。</span><span class="sxs-lookup"><span data-stu-id="06a76-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="06a76-135">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="06a76-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="06a76-136">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="06a76-136">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="06a76-137">如果此目錄不存在, 請移至[.NET Framework 4 的 Windows Communication Foundation (wcf) 和 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780), 以下載所有 Windows Communication Foundation (wcf) [!INCLUDE[wf1](../../../../includes/wf1-md.md)]和範例。</span><span class="sxs-lookup"><span data-stu-id="06a76-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="06a76-138">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="06a76-138">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WPFDataBinding`  
