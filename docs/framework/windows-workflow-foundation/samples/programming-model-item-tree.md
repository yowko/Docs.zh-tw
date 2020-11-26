---
title: 程式設計模型項目樹狀
ms.date: 03/30/2017
ms.assetid: 0229efde-19ac-4bdc-a187-c6227a7bd1a5
ms.openlocfilehash: 059bb3edcfe41f52e2244ff6f5bf3fc78a4262bb
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96235801"
---
# <a name="programming-model-item-tree"></a><span data-ttu-id="426db-102">程式設計模型項目樹狀</span><span class="sxs-lookup"><span data-stu-id="426db-102">Programming Model Item Tree</span></span>

<span data-ttu-id="426db-103">這個範例示範如何 <xref:System.Activities.Presentation.Model.ModelItem> 使用 Windows Presentation Foundation (WPF) 樹狀檢視中的宣告式資料系結，來流覽樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="426db-103">This sample demonstrates how to navigate the <xref:System.Activities.Presentation.Model.ModelItem> tree using declarative data binding from the Windows Presentation Foundation (WPF) Tree View.</span></span>

## <a name="sample-details"></a><span data-ttu-id="426db-104">範例詳細資料</span><span class="sxs-lookup"><span data-stu-id="426db-104">Sample Details</span></span>

 <span data-ttu-id="426db-105"><xref:System.Activities.Presentation.Model.ModelItem>樹狀結構是 Windows 工作流程設計工具基礎結構用來公開所編輯之基礎實例相關資料的抽象概念。</span><span class="sxs-lookup"><span data-stu-id="426db-105">The <xref:System.Activities.Presentation.Model.ModelItem> tree is the abstraction that is used by the Windows Workflow Designer infrastructure to expose the data about the underlying instance being edited.</span></span> <span data-ttu-id="426db-106">下圖是工作流程設計工具內各層基礎結構的描述。</span><span class="sxs-lookup"><span data-stu-id="426db-106">The following illustration is a depiction of the various layers of infrastructure within the Workflow Designer.</span></span>

 ![顯示工作流程設計工具架構的圖表。](./media/programming-model-item-tree/workflow-designer-architecture.jpg)

 <span data-ttu-id="426db-108"><xref:System.Activities.Presentation.Model.ModelItem> 包含基礎值的指標，以及 <xref:System.Activities.Presentation.Model.ModelProperty> 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="426db-108">A <xref:System.Activities.Presentation.Model.ModelItem> consists of a pointer to the underlying value, as well as a collection of <xref:System.Activities.Presentation.Model.ModelProperty> objects.</span></span> <span data-ttu-id="426db-109"><xref:System.Activities.Presentation.Model.ModelProperty> 物件則是由名稱、屬性型別和值的指標這類資料所構成，而值的指標則會是另一個 <xref:System.Activities.Presentation.Model.ModelItem>。</span><span class="sxs-lookup"><span data-stu-id="426db-109">A <xref:System.Activities.Presentation.Model.ModelProperty> object in turn, consists of data such as the name and type of the property and then a pointer to the value, which in turn, is another <xref:System.Activities.Presentation.Model.ModelItem>.</span></span> <span data-ttu-id="426db-110">值轉換子可用來操作從 <xref:System.Activities.Presentation.Model.ModelItem> 傳回的一些 <xref:System.Activities.Presentation.Model.ModelProperty>，讓它們在樹狀檢視中正確顯示。</span><span class="sxs-lookup"><span data-stu-id="426db-110">A value converter is used to manipulate some of the <xref:System.Activities.Presentation.Model.ModelItem>s returned from a <xref:System.Activities.Presentation.Model.ModelProperty> to make them appear correctly in the tree view.</span></span> <span data-ttu-id="426db-111">接著這個範例會示範如何使用命令式語法，以命令方式對 <xref:System.Activities.Presentation.Model.ModelItem> 樹狀進行程式設計，如下面範例中所示。</span><span class="sxs-lookup"><span data-stu-id="426db-111">The sample then demonstrates how to imperatively program against the <xref:System.Activities.Presentation.Model.ModelItem> tree using the imperative syntax, as seen in the following example.</span></span>

```csharp
ModelItem mi = wd.Context.Services.GetService<ModelService>().Root;
ModelProperty mp = mi.Properties["Activities"];
mp.Collection.Add(new Persist());
ModelItem justAdded = mp.Collection.Last();
justAdded.Properties["DisplayName"].SetValue("new name");
```

#### <a name="to-use-this-sample"></a><span data-ttu-id="426db-112">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="426db-112">To use this sample</span></span>

1. <span data-ttu-id="426db-113">在 Visual Studio 2010 中開啟 ProgrammingModelItemTree .sln 方案。</span><span class="sxs-lookup"><span data-stu-id="426db-113">Open the ProgrammingModelItemTree.sln solution in Visual Studio 2010.</span></span>

2. <span data-ttu-id="426db-114">從 [**組建**] 功能表選取 [**組建方案**] 來建立方案。</span><span class="sxs-lookup"><span data-stu-id="426db-114">Build the solution by selecting **Build Solution** from the **Build** menu.</span></span>

3. <span data-ttu-id="426db-115">按 F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="426db-115">Press F5 to run the application.</span></span> <span data-ttu-id="426db-116">WPF 表單隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="426db-116">The WPF form is then displayed.</span></span>

4. <span data-ttu-id="426db-117">按一下 [ **載入 WF** ] 按鈕載入， <xref:System.Activities.Presentation.Model.ModelItem> 並將它系結至樹狀檢視。</span><span class="sxs-lookup"><span data-stu-id="426db-117">Click the **Load WF** button to load the <xref:System.Activities.Presentation.Model.ModelItem> and bind it to the tree view.</span></span>

5. <span data-ttu-id="426db-118">按一下 [ **變更模型專案樹狀** ] 按鈕會執行上述程式碼，將專案加入至樹狀結構並設定屬性。</span><span class="sxs-lookup"><span data-stu-id="426db-118">Clicking the **Change Model Item Tree** button executes the preceding code to add an item into the tree and set a property.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="426db-119">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="426db-119">The samples may already be installed on your computer.</span></span> <span data-ttu-id="426db-120">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="426db-120">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="426db-121">如果此目錄不存在，請移至 [Windows Communication Foundation (wcf) 並 Windows Workflow Foundation (適用于) 4 的 WF .NET Framework 範例](https://www.microsoft.com/download/details.aspx?id=21459) 下載所有 WINDOWS COMMUNICATION FOUNDATION 的 wcf (和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="426db-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="426db-122">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="426db-122">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a><span data-ttu-id="426db-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="426db-123">See also</span></span>

- <xref:System.Windows.Data.IValueConverter>
