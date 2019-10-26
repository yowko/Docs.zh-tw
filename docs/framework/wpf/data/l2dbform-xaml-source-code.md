---
title: L2DBForm.xaml 原始程式碼
ms.date: 10/22/2019
ms.topic: sample
ms.openlocfilehash: 290b00e136f0c49e1b27d4fa1bca7321eebe936e
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920941"
---
# <a name="l2dbformxaml-source-code"></a><span data-ttu-id="064fb-102">L2DBForm.xaml 原始程式碼</span><span class="sxs-lookup"><span data-stu-id="064fb-102">L2DBForm.xaml source code</span></span>

<span data-ttu-id="064fb-103">此頁面包含並描述[使用 LINQ to XML 範例的 WPF 資料](linq-to-xml-data-binding-sample.md)系結的 XAML 原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="064fb-103">This page contains and describes the XAML source file for the [WPF data binding using LINQ to XML example](linq-to-xml-data-binding-sample.md).</span></span>

## <a name="overall-ui-structure"></a><span data-ttu-id="064fb-104">整體 UI 結構</span><span class="sxs-lookup"><span data-stu-id="064fb-104">Overall UI structure</span></span>

<span data-ttu-id="064fb-105">就像 WPF 專案一般，這個檔案包含一個父元素、一個 <xref:System.Windows.Window> XML 專案，與 `LinqToXmlDataBinding` 命名空間中 `L2XDBFrom` 的衍生類別相關聯。</span><span class="sxs-lookup"><span data-stu-id="064fb-105">As is typical for a WPF project, this file contains one parent element, a <xref:System.Windows.Window> XML element that's associated with the derived class `L2XDBFrom` in the `LinqToXmlDataBinding` namespace.</span></span>

<span data-ttu-id="064fb-106">工作區包含在指定了淺藍色背景的 <xref:System.Windows.Controls.StackPanel> 中。</span><span class="sxs-lookup"><span data-stu-id="064fb-106">The client area is contained within a <xref:System.Windows.Controls.StackPanel> that's given a light blue background.</span></span> <span data-ttu-id="064fb-107">這個面板包含四個 <xref:System.Windows.Controls.DockPanel> UI 區段，以 <xref:System.Windows.Controls.Separator> 列分隔。</span><span class="sxs-lookup"><span data-stu-id="064fb-107">This panel contains four <xref:System.Windows.Controls.DockPanel> UI sections separated by <xref:System.Windows.Controls.Separator> bars.</span></span> <span data-ttu-id="064fb-108">這些章節的[用途如下所述。](linq-to-xml-data-binding-sample.md#overview)</span><span class="sxs-lookup"><span data-stu-id="064fb-108">The purpose of these sections is described [here](linq-to-xml-data-binding-sample.md#overview).</span></span>

<span data-ttu-id="064fb-109">每個區段都包含一個可以識別自身的標籤。</span><span class="sxs-lookup"><span data-stu-id="064fb-109">Each section contains a label that identifies it.</span></span> <span data-ttu-id="064fb-110">在前兩個區段中，這個標籤會透過使用 <xref:System.Windows.FrameworkElement.LayoutTransform%2A>而旋轉 90 度。</span><span class="sxs-lookup"><span data-stu-id="064fb-110">In the first two sections, this label is rotated 90 degrees through the use of a <xref:System.Windows.FrameworkElement.LayoutTransform%2A>.</span></span> <span data-ttu-id="064fb-111">區段的其餘部分包含適用于該區段目的的 UI 元素，例如，文字區塊、文字方塊和按鈕。</span><span class="sxs-lookup"><span data-stu-id="064fb-111">The rest of the section contains UI elements appropriate to the purpose of that section, for example, text blocks, text boxes, and buttons.</span></span> <span data-ttu-id="064fb-112">有時候，子系 <xref:System.Windows.Controls.StackPanel> 用於調整這些子控制項。</span><span class="sxs-lookup"><span data-stu-id="064fb-112">Sometimes a child <xref:System.Windows.Controls.StackPanel> is used to align these child controls.</span></span>

## <a name="window-resource-section"></a><span data-ttu-id="064fb-113">視窗資源區段</span><span class="sxs-lookup"><span data-stu-id="064fb-113">Window resource section</span></span>

<span data-ttu-id="064fb-114">第 9 行的 `<Window.Resources>` 開頭標記表示視窗資源區段的開頭，</span><span class="sxs-lookup"><span data-stu-id="064fb-114">The opening `<Window.Resources>` tag on line 9 indicates the start of the window resource section.</span></span> <span data-ttu-id="064fb-115">並以第 35 行的結束標記表示結尾。</span><span class="sxs-lookup"><span data-stu-id="064fb-115">It ends with the closing tag on line 35.</span></span>

<span data-ttu-id="064fb-116">跨越第 11 行到第 25 行的 `<ObjectDataProvider>` 標記會宣告名稱為 <xref:System.Windows.Data.ObjectDataProvider>的 `LoadedBooks`，並使用 <xref:System.Xml.Linq.XElement> 當做來源。</span><span class="sxs-lookup"><span data-stu-id="064fb-116">The `<ObjectDataProvider>` tag, which spans lines 11 through 25, declares a <xref:System.Windows.Data.ObjectDataProvider>, named `LoadedBooks`, that uses an <xref:System.Xml.Linq.XElement> as the source.</span></span> <span data-ttu-id="064fb-117">這個 <xref:System.Xml.Linq.XElement> 會藉由剖析內嵌的 XML 文件 ( `CDATA` 項目) 來初始化。</span><span class="sxs-lookup"><span data-stu-id="064fb-117">The <xref:System.Xml.Linq.XElement> is initialized by parsing an embedded XML document (a `CDATA` element).</span></span> <span data-ttu-id="064fb-118">請注意，宣告內嵌的 XML 檔以及剖析時，會保留空白字元。</span><span class="sxs-lookup"><span data-stu-id="064fb-118">Notice that white space is preserved when declaring the embedded XML document and also when it's parsed.</span></span> <span data-ttu-id="064fb-119">保留空白字元是因為用於顯示原始 XML 的 <xref:System.Windows.Controls.TextBlock> 控制項沒有特殊的 XML 格式化功能。</span><span class="sxs-lookup"><span data-stu-id="064fb-119">White space is preserved because the <xref:System.Windows.Controls.TextBlock> control, which is used to display the raw XML, has no special XML formatting capabilities.</span></span>

<span data-ttu-id="064fb-120">最後在第 28 到 34 行會定義名稱為 <xref:System.Windows.DataTemplate> 的 `BookTemplate` 。</span><span class="sxs-lookup"><span data-stu-id="064fb-120">Lastly, a <xref:System.Windows.DataTemplate> named `BookTemplate` is defined on lines 28 through 34.</span></span> <span data-ttu-id="064fb-121">這個範本將用於顯示 [書籍清單] UI 區段中的項目。</span><span class="sxs-lookup"><span data-stu-id="064fb-121">This template is used to display the entries in the **Book List** UI section.</span></span> <span data-ttu-id="064fb-122">它會使用資料繫結和 LINQ to XML 動態屬性，透過下列指派，擷取書籍 ID 和書籍名稱：</span><span class="sxs-lookup"><span data-stu-id="064fb-122">It uses data binding and LINQ to XML dynamic properties to retrieve the book ID and book name through the following assignments:</span></span>

```xaml
Text="{Binding Path=Attribute[id].Value}"Text="{Binding Path=Value}"
```

## <a name="data-binding-code"></a><span data-ttu-id="064fb-123">資料繫結程式碼</span><span class="sxs-lookup"><span data-stu-id="064fb-123">Data binding code</span></span>

<span data-ttu-id="064fb-124">除了 <xref:System.Windows.DataTemplate> 項目之外，資料繫結也會用在這個檔案的其他多個地方。</span><span class="sxs-lookup"><span data-stu-id="064fb-124">In addition to the <xref:System.Windows.DataTemplate> element, data binding is used in a number of other places in this file.</span></span>

<span data-ttu-id="064fb-125">在第 38 行的 `<StackPanel>` 開頭標記中，此面板的 <xref:System.Windows.FrameworkElement.DataContext%2A> 屬性會設定為 `LoadedBooks` 資料提供者。</span><span class="sxs-lookup"><span data-stu-id="064fb-125">In the opening `<StackPanel>` tag on line 38, the <xref:System.Windows.FrameworkElement.DataContext%2A> property of this panel is set to the `LoadedBooks` data provider.</span></span>

```xaml
DataContext="{Binding Source={StaticResource LoadedBooks}}
```

<span data-ttu-id="064fb-126">設定資料內容可以讓 (第 46 行) 名為 `tbRawXml` 的 <xref:System.Windows.Controls.TextBlock> 繫結至此資料提供者的 `Xml` 屬性，以顯示原始 XML：</span><span class="sxs-lookup"><span data-stu-id="064fb-126">Setting the data context makes it possible (on line 46) for the <xref:System.Windows.Controls.TextBlock> named `tbRawXml` to display the raw XML by binding to this data provider's `Xml` property:</span></span>

```xaml
Text="{Binding Path=Xml}"
```

<span data-ttu-id="064fb-127">第 58 到 62 行 [書籍清單] <xref:System.Windows.Controls.ListBox>**UI 區段中的** 會將其顯示項目的範本設定為視窗資源區段中定義的 `BookTemplate` ：</span><span class="sxs-lookup"><span data-stu-id="064fb-127">The <xref:System.Windows.Controls.ListBox> in the **Book List** UI section, on lines 58 through 62, sets the template for its display items to the `BookTemplate` defined in the window resource section:</span></span>

```xaml
ItemTemplate ="{StaticResource BookTemplate}"
```

<span data-ttu-id="064fb-128">接著在第 59 到 62 行，書籍的實際值會繫結到此清單方塊：</span><span class="sxs-lookup"><span data-stu-id="064fb-128">Then, on lines 59 through 62, the actual values of the books are bound to this list box:</span></span>

```xaml
<ListBox.ItemsSource>
    <Binding Path="Elements[{http://www.mybooks.com}book]"/>
</ListBox.ItemsSource>
```

<span data-ttu-id="064fb-129">第三個 UI 區段，也就是 [ **編輯選取的書籍**] 會先將父代 <xref:System.Windows.FrameworkElement.DataContext%2A> 的 <xref:System.Windows.Controls.StackPanel> 繫結到目前從 [ **書籍清單** ] UI 區段 (第 82 行) 選取的項目：</span><span class="sxs-lookup"><span data-stu-id="064fb-129">The third UI section, **Edit Selected Book**, first binds the <xref:System.Windows.FrameworkElement.DataContext%2A> of the parent <xref:System.Windows.Controls.StackPanel> to the currently selected item in from the **Book List** UI section (line 82):</span></span>

```xaml
DataContext="{Binding ElementName=lbBooks, Path=SelectedItem}"
```

<span data-ttu-id="064fb-130">接著，它會使用雙向資料繫結，讓書籍項目的目前值顯示到此面板的兩個文字方塊中，或從其中更新。</span><span class="sxs-lookup"><span data-stu-id="064fb-130">It then uses two-way data binding, so that the current values of the book elements are displayed to, and updated from, the two text boxes in this panel.</span></span> <span data-ttu-id="064fb-131">動態屬性的資料繫結類似於 `BookTemplate` 資料範本中所使用的資料繫結：</span><span class="sxs-lookup"><span data-stu-id="064fb-131">Data binding to dynamic properties is similar to the data binding used in the `BookTemplate` data template:</span></span>

```xaml
Text="{Binding Path=Attribute[id].Value}"...Text="{Binding Path=Value}"
```

<span data-ttu-id="064fb-132">最後一個 UI 區段 ([Add New Book] \(新增新的書籍))，不會在其 XAML 程式碼中使用資料繫結。</span><span class="sxs-lookup"><span data-stu-id="064fb-132">The last UI section, **Add New Book**, doesn't use data binding in its XAML code.</span></span> <span data-ttu-id="064fb-133">而是在其檔案 *L2DBForm.xaml.cs* 的事件處理程式碼中使用資料繫結。</span><span class="sxs-lookup"><span data-stu-id="064fb-133">Instead, data binding is in its event handling code in the file *L2DBForm.xaml.cs*.</span></span>

## <a name="example"></a><span data-ttu-id="064fb-134">範例</span><span class="sxs-lookup"><span data-stu-id="064fb-134">Example</span></span>

### <a name="description"></a><span data-ttu-id="064fb-135">描述</span><span class="sxs-lookup"><span data-stu-id="064fb-135">Description</span></span>

> [!NOTE]
> <span data-ttu-id="064fb-136">建議您將下列程式碼複製到程式碼編輯器 (例如，Visual Studio 中的 C# 原始程式碼編輯器)，如此將更容易追蹤行號。</span><span class="sxs-lookup"><span data-stu-id="064fb-136">We recommend that you copy the following code below into a code editor, such as the C# source code editor in Visual Studio, so that line numbers will be easier to track.</span></span>

### <a name="code"></a><span data-ttu-id="064fb-137">程式碼</span><span class="sxs-lookup"><span data-stu-id="064fb-137">Code</span></span>

```xml
<Window x:Class="LinqToXmlDataBinding.L2XDBForm"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:system="clr-namespace:System;assembly=mscorlib"
    xmlns:xlinq="clr-namespace:System.Xml.Linq;assembly=System.Xml.Linq"
    xmlns:local="clr-namespace:LinqToXmlDataBinding"
    Title="WPF Data Binding using LINQ-to-XML" Height="665" Width="500" ResizeMode="NoResize">

    <Window.Resources>
        <!-- Books provider and inline data -->
        <ObjectDataProvider x:Key="LoadedBooks" ObjectType="{x:Type xlinq:XElement}" MethodName="Parse">
            <ObjectDataProvider.MethodParameters>
                <system:String xml:space="preserve">
<![CDATA[
<books xmlns="http://www.mybooks.com">
  <book id="0">book zero</book>
  <book id="1">book one</book>
  <book id="2">book two</book>
  <book id="3">book three</book>
</books>
]]>
                </system:String>
                <xlinq:LoadOptions>PreserveWhitespace</xlinq:LoadOptions>
            </ObjectDataProvider.MethodParameters>
        </ObjectDataProvider>

        <!-- Template for use in Books List listbox. -->
        <DataTemplate x:Key="BookTemplate">
            <StackPanel Orientation="Horizontal">
                <TextBlock Margin="3" Text="{Binding Path=Attribute[id].Value}"/>
                <TextBlock Margin="3" Text="-"/>
                <TextBlock Margin="3" Text="{Binding Path=Value}"/>
            </StackPanel>
        </DataTemplate>
    </Window.Resources>

    <!-- Main visual content container -->
    <StackPanel Background="lightblue" DataContext="{Binding Source={StaticResource LoadedBooks}}">
        <!-- Raw XML display section -->
        <DockPanel Margin="5">
            <Label  Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" FontWeight="Bold">XML
            <Label.LayoutTransform>
                <RotateTransform Angle="90"/>
            </Label.LayoutTransform>
            </Label>
            <TextBlock Name="tbRawXml" Height="200" Background="LightGray" Text="{Binding Path=Xml}" TextTrimming="CharacterEllipsis" />
        </DockPanel>

        <Separator Height="4" Margin="5" />

        <!-- List box to display all books section -->
        <DockPanel Margin="5">
            <Label  Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" FontWeight="Bold">Book List
                <Label.LayoutTransform>
                    <RotateTransform Angle="90"/>
                </Label.LayoutTransform>
            </Label>
            <ListBox Name="lbBooks" Height="200" Width="415" ItemTemplate ="{StaticResource BookTemplate}">
                <ListBox.ItemsSource>
                    <Binding Path="Elements[{http://www.mybooks.com}book]"/>
                </ListBox.ItemsSource>
            </ListBox>
            <Button Margin="5" DockPanel.Dock="Right" Height="30" Width ="130" Content="Remove Selected Book" Click="OnRemoveBook">
            <Button.LayoutTransform>
                <RotateTransform Angle="90"/>
            </Button.LayoutTransform>
            </Button>
        </DockPanel>

        <Separator Height="4" Margin="5" />

        <!-- Edit current selection section -->
        <DockPanel Margin="5">
            <TextBlock Margin="5" Height="30" Width="65" DockPanel.Dock="Right" Background="LightGray" TextWrapping="Wrap" TextAlignment="Center">
                    Changes are live!
                <TextBlock.LayoutTransform>
                    <RotateTransform Angle="90"/>
                </TextBlock.LayoutTransform>
            </TextBlock>
            <StackPanel>
                <Label Width="450" Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" HorizontalAlignment="Left" FontWeight="Bold">Edit Selected Book</Label>
                <StackPanel Margin="1" DataContext="{Binding ElementName=lbBooks, Path=SelectedItem}">
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">ID:</Label>
                        <TextBox Name="editAttributeTextBox" Width="410" Text="{Binding Path=Attribute[id].Value}">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="Bold" TextAlignment="Center">
                                    <Label>Edit the selected book ID and see it changed.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">Value:</Label>
                        <TextBox Name="editValueTextBox" Width="410" Text="{Binding Path=Value}" Height="25">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="Bold" TextAlignment="Center">
                                    <Label>Edit the selected book Value and see it changed.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                </StackPanel>
            </StackPanel>
        </DockPanel>

        <Separator Height="4" Margin="5" />

        <!-- Add new book section -->
        <DockPanel Margin="5">
            <Button Margin="5" Height="30" DockPanel.Dock="Right" Click ="OnAddBook">Add Book
                <Button.LayoutTransform>
                    <RotateTransform Angle="90"/>
                </Button.LayoutTransform>
            </Button>
            <StackPanel>
                <Label Width="450" Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" HorizontalAlignment="Left" FontWeight="Bold">Add New Book</Label>
                <StackPanel Margin="1">
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">ID:</Label>
                        <TextBox Name="tbAddID" Width="410">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="Bold" TextAlignment="Center">
                                    <Label>Enter a book ID and Value pair, then click Add Book.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">Value:</Label>
                        <TextBox Name="tbAddValue" Width="410" Height="25">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="UltraBold" TextAlignment="Center">
                                    <Label>Enter a book ID and Value pair, then click Add Book.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                </StackPanel>
            </StackPanel>
        </DockPanel>
    </StackPanel>
</Window>
```

### <a name="comments"></a><span data-ttu-id="064fb-138">註解</span><span class="sxs-lookup"><span data-stu-id="064fb-138">Comments</span></span>

<span data-ttu-id="064fb-139">如需與 WPF UI 項目建立關聯之事件處理常式的 C# 原始程式碼，請參閱 [L2DBForm.xaml.cs 原始程式碼](l2dbform-xaml-cs-source-code.md)。</span><span class="sxs-lookup"><span data-stu-id="064fb-139">For the C# source code for the event handlers associated with the WPF UI elements, see [L2DBForm.xaml.cs source code](l2dbform-xaml-cs-source-code.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="064fb-140">請參閱</span><span class="sxs-lookup"><span data-stu-id="064fb-140">See also</span></span>

- [<span data-ttu-id="064fb-141">逐步解說：LinqToXmlDataBinding 範例</span><span class="sxs-lookup"><span data-stu-id="064fb-141">Walkthrough: LinqToXmlDataBinding example</span></span>](linq-to-xml-data-binding-sample.md)
- [<span data-ttu-id="064fb-142">L2DBForm.xaml.cs 來源程式碼</span><span class="sxs-lookup"><span data-stu-id="064fb-142">L2DBForm.xaml.cs source code</span></span>](l2dbform-xaml-cs-source-code.md)
