---
title: 移除檢視狀態，設計工具會新增至 XAML 檔案
ms.date: 03/30/2017
ms.assetid: a801ce22-8699-483c-a392-7bb3834aae4f
ms.openlocfilehash: 0d4dccb16796893df58f709e011657457cc71670
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48781683"
---
# <a name="removing-the-view-state-the-designer-adds-to-an-xaml-file"></a><span data-ttu-id="674d0-102">移除檢視狀態，設計工具會新增至 XAML 檔案</span><span class="sxs-lookup"><span data-stu-id="674d0-102">Removing the View State the Designer Adds to an XAML File</span></span>
<span data-ttu-id="674d0-103">此範例示範如何建立衍生自 <xref:System.Windows.Markup.XamlWriter> 的類別，以及從 XAML 檔案移除檢視狀態。</span><span class="sxs-lookup"><span data-stu-id="674d0-103">This sample demonstrates how to create a class that derives from <xref:System.Windows.Markup.XamlWriter> and removes view state from a XAML file.</span></span> [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] <span data-ttu-id="674d0-104">會將資訊寫入到 XAML 文件中，也就是檢視狀態。</span><span class="sxs-lookup"><span data-stu-id="674d0-104"> writes information into the XAML document, which is known as view state.</span></span> <span data-ttu-id="674d0-105">檢視狀態是指設計階段必要的資訊，例如執行階段不需要的版面配置定位。</span><span class="sxs-lookup"><span data-stu-id="674d0-105">View state refers to the information that is required at design time, such as layout positioning, that is not required at runtime.</span></span> [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)] <span data-ttu-id="674d0-106">會在編輯時將這項資訊插入到 XAML 文件中。</span><span class="sxs-lookup"><span data-stu-id="674d0-106"> inserts this information into the XAML document as it is edited.</span></span> [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)] <span data-ttu-id="674d0-107">會將檢視狀態寫入到含 `mc:Ignorable` 屬性的 XAML 檔案中，所以當執行階段載入 XAML 檔案時並不會載入這項資訊。</span><span class="sxs-lookup"><span data-stu-id="674d0-107"> writes the view state into the XAML file with the `mc:Ignorable` attribute, so this information is not loaded when the runtime loads the XAML file.</span></span> <span data-ttu-id="674d0-108">這個範例示範如何在處理 XAML 節點時建立可移除檢視狀態資訊的類別。</span><span class="sxs-lookup"><span data-stu-id="674d0-108">This sample demonstrates how to create a class that removes that view state information while processing XAML nodes.</span></span>

## <a name="discussion"></a><span data-ttu-id="674d0-109">討論</span><span class="sxs-lookup"><span data-stu-id="674d0-109">Discussion</span></span>
 <span data-ttu-id="674d0-110">這個範例示範如何建立自訂寫入器。</span><span class="sxs-lookup"><span data-stu-id="674d0-110">This sample demonstrates how to create a custom writer.</span></span>

 <span data-ttu-id="674d0-111">若要建置自訂的 XAML 寫入器，請建立繼承自 <xref:System.Windows.Markup.XamlWriter> 的類別。</span><span class="sxs-lookup"><span data-stu-id="674d0-111">To build a custom XAML writer, create a class that inherits from <xref:System.Windows.Markup.XamlWriter>.</span></span> <span data-ttu-id="674d0-112">因為 XAML 寫入器通常巢狀的通常會以追蹤 「 內部 」 XAML 寫入器。</span><span class="sxs-lookup"><span data-stu-id="674d0-112">As XAML writers are often nested, it is typical to keep track of an "inner" XAML writer.</span></span> <span data-ttu-id="674d0-113">這些 「 內部 ' 寫入器可以想像成其餘 XAML 寫入器，可讓您有多個進入點執行工作，然後委派至堆疊的其餘部分的處理堆疊的參考。</span><span class="sxs-lookup"><span data-stu-id="674d0-113">These "inner’ writers can be thought of as the reference to the remaining stack of XAML writers, allowing you to have multiple entry points to do work and then delegate processing to the remainder of the stack.</span></span>

 <span data-ttu-id="674d0-114">在這個範例中有數個值得注意的項目。</span><span class="sxs-lookup"><span data-stu-id="674d0-114">In this sample, there are a few items of interest.</span></span> <span data-ttu-id="674d0-115">一個是正在寫入的項目是否來自設計工具命名空間的檢查。</span><span class="sxs-lookup"><span data-stu-id="674d0-115">One is the check to see whether the item being written is from a designer namespace.</span></span> <span data-ttu-id="674d0-116">請注意，這同時也會將工作流程中設計工具命名空間的其他類型用法刪除。</span><span class="sxs-lookup"><span data-stu-id="674d0-116">Note that this also strips out the use of other types from the designer namespace in a workflow.</span></span>

```csharp
static Boolean IsDesignerAttachedProperty(XamlMember xamlMember)
{
    return xamlMember.IsAttachable &&
        xamlMember.PreferredXamlNamespace.Equals(c_sapNamespaceURI, StringComparison.OrdinalIgnoreCase);
}

const String c_sapNamespaceURI = "http://schemas.microsoft.com/netfx/2009/xaml/activities/presentation";

// The next item of interest is the constructor, where the utilization of the inner XAML writer is seen.
public ViewStateCleaningWriter(XamlWriter innerWriter)
{
    this.InnerWriter = innerWriter;
    this.MemberStack = new Stack<XamlMember>();
}

XamlWriter InnerWriter {get; set; }
Stack<XamlMember> MemberStack {get; set; }
```

 <span data-ttu-id="674d0-117">這也會建立周遊節點資料流時所用的 XAML 成員堆疊。</span><span class="sxs-lookup"><span data-stu-id="674d0-117">This also creates a stack of XAML members that are used while traversing the node stream.</span></span> <span data-ttu-id="674d0-118">此範例的剩餘的工作部分大多包含在<!--zz  <xref:System.Windows.Markup.XamlWriter.WriteStartMember%2A>-->`System.Windows.Markup.XamlWriter.WriteStartMember`方法。</span><span class="sxs-lookup"><span data-stu-id="674d0-118">The remaining work of this sample is largely contained in the <!--zz  <xref:System.Windows.Markup.XamlWriter.WriteStartMember%2A>--> `System.Windows.Markup.XamlWriter.WriteStartMember` method.</span></span>

```csharp
public override void WriteStartMember(XamlMember xamlMember)
{
    MemberStack.Push(xamlMember);

    if (IsDesignerAttachedProperty(xamlMember))
    {
        m_attachedPropertyDepth++;
    }

    if (m_attachedPropertyDepth > 0)
    {
        return;
    }

    InnerWriter.WriteStartMember(xamlMember);
}
```

 <span data-ttu-id="674d0-119">後續方法接著檢查它們是否仍包含在檢視狀態容器中，如果是的話則返回，而不會在寫入器堆疊向下傳遞節點。</span><span class="sxs-lookup"><span data-stu-id="674d0-119">Subsequent methods then check to see whether they are still contained in a view state container, and if so, return, and do not pass the node down the writer stack.</span></span>

```csharp
public override void WriteValue(Object value)
{
    if (m_attachedPropertyDepth > 0)
    {
        return;
    }

    InnerWriter.WriteValue(value);
}
```

 <span data-ttu-id="674d0-120">若要使用自訂 XAML 寫入器，您必須將它鏈結在 XAML 寫入器堆疊中。</span><span class="sxs-lookup"><span data-stu-id="674d0-120">To use a custom XAML writer, you must chain it together in a stack of XAML writers.</span></span> <span data-ttu-id="674d0-121">下列程式碼示範這個使用方式。</span><span class="sxs-lookup"><span data-stu-id="674d0-121">The following code shows how this can be used.</span></span>

```csharp
XmlWriterSettings writerSettings = new XmlWriterSettings {  Indent = true };
XmlWriter xmlWriter = XmlWriter.Create(File.OpenWrite(args[1]), writerSettings);
XamlXmlWriter xamlWriter = new XamlXmlWriter(xmlWriter, new XamlSchemaContext());
XamlServices.Save(new ViewStateCleaningWriter(ActivityXamlServices.CreateBuilderWriter(xamlWriter)), ab);
```

#### <a name="to-use-this-sample"></a><span data-ttu-id="674d0-122">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="674d0-122">To use this sample</span></span>

1. <span data-ttu-id="674d0-123">使用 Visual Studio 2010 開啟 ViewStateCleaningWriter.sln 方案檔案。</span><span class="sxs-lookup"><span data-stu-id="674d0-123">Using Visual Studio 2010, open the ViewStateCleaningWriter.sln solution file.</span></span>

2. <span data-ttu-id="674d0-124">開啟命令提示字元，然後巡覽到建置 ViewStageCleaningWriter.exe 的目錄。</span><span class="sxs-lookup"><span data-stu-id="674d0-124">Open a command prompt and navigate to the directory where the ViewStageCleaningWriter.exe is built.</span></span>

3. <span data-ttu-id="674d0-125">對 Workflow1.xaml 檔案執行 ViewStateCleaningWriter.exe。</span><span class="sxs-lookup"><span data-stu-id="674d0-125">Run ViewStateCleaningWriter.exe on the Workflow1.xaml file.</span></span>

   <span data-ttu-id="674d0-126">下列範例示範此可執行檔的語法。</span><span class="sxs-lookup"><span data-stu-id="674d0-126">The syntax for the executable is shown in the following example.</span></span>

   ```console
   ViewStateCleaningWriter.exe [input file] [output file]
   ```

   <span data-ttu-id="674d0-127">這會輸出至 XAML 檔案\[outfile]，其中包含所有其檢視狀態資訊已移除。</span><span class="sxs-lookup"><span data-stu-id="674d0-127">This outputs a XAML file to \[outfile], which has all its view state information removed.</span></span>

> [!NOTE]
> <span data-ttu-id="674d0-128"><xref:System.Activities.Statements.Sequence> 工作流程的數個虛擬化提示會被移除。</span><span class="sxs-lookup"><span data-stu-id="674d0-128">For a <xref:System.Activities.Statements.Sequence> workflow, a number of virtualization hints are removed.</span></span> <span data-ttu-id="674d0-129">這樣會導致設計工具下次載入時重新計算配置。</span><span class="sxs-lookup"><span data-stu-id="674d0-129">This causes the designer to recalculate layout the next time it is loaded.</span></span> <span data-ttu-id="674d0-130">對 <xref:System.Activities.Statements.Flowchart> 使用這個範例時，所有定位和線條路由資訊都會被移除，在設計工具後續載入時，所有活動都會堆疊在畫面左側。</span><span class="sxs-lookup"><span data-stu-id="674d0-130">When you use this sample for a <xref:System.Activities.Statements.Flowchart>, all positioning and line routing information are removed and on subsequent loading into the designer, all activities are stacked on the left side of the screen.</span></span>

#### <a name="to-create-a-sample-xaml-file-for-use-with-this-sample"></a><span data-ttu-id="674d0-131">若要建立這個範例所用的範例 XAML 檔案</span><span class="sxs-lookup"><span data-stu-id="674d0-131">To create a sample XAML file for use with this sample</span></span>

1. <span data-ttu-id="674d0-132">開啟 Visual Studio 2010。</span><span class="sxs-lookup"><span data-stu-id="674d0-132">Open Visual Studio 2010.</span></span>

2. <span data-ttu-id="674d0-133">建立新的工作流程主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="674d0-133">Create a new Workflow Console Application.</span></span>

3. <span data-ttu-id="674d0-134">將數個活動拖放到畫布上。</span><span class="sxs-lookup"><span data-stu-id="674d0-134">Drag and drop a few activities onto the canvas</span></span>

4. <span data-ttu-id="674d0-135">儲存工作流程 XAML 檔案。</span><span class="sxs-lookup"><span data-stu-id="674d0-135">Save the workflow XAML file.</span></span>

5. <span data-ttu-id="674d0-136">檢查 XAML 檔案是否有檢視狀態附加屬性。</span><span class="sxs-lookup"><span data-stu-id="674d0-136">Inspect the XAML file to see the view state attached properties.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="674d0-137">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="674d0-137">The samples may already be installed on your machine.</span></span> <span data-ttu-id="674d0-138">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="674d0-138">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="674d0-139">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="674d0-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="674d0-140">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="674d0-140">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ViewStateCleaningWriter`
