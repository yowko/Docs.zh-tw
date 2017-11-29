---
title: "程式設計模型項目樹狀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0229efde-19ac-4bdc-a187-c6227a7bd1a5
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 18de9d7f9cedc40a6c143a4dae5567c9acf2cf88
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="programming-model-item-tree"></a><span data-ttu-id="e072f-102">程式設計模型項目樹狀</span><span class="sxs-lookup"><span data-stu-id="e072f-102">Programming Model Item Tree</span></span>
<span data-ttu-id="e072f-103">這個範例示範如何使用來自 <xref:System.Activities.Presentation.Model.ModelItem> 樹狀檢視的宣告式資料繫結巡覽 [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="e072f-103">This sample demonstrates how to navigate the <xref:System.Activities.Presentation.Model.ModelItem> tree using declarative data binding from the [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] Tree View.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="e072f-104">範例詳細資料</span><span class="sxs-lookup"><span data-stu-id="e072f-104">Sample Details</span></span>  
 <span data-ttu-id="e072f-105"><xref:System.Activities.Presentation.Model.ModelItem> 樹狀結構是一個抽象概念，由 [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] 基礎結構用來公開要編輯之基礎執行個體的相關資料。</span><span class="sxs-lookup"><span data-stu-id="e072f-105">The <xref:System.Activities.Presentation.Model.ModelItem> tree is the abstraction that is used by the [!INCLUDE[wfd1](../../../../includes/wfd1-md.md)] infrastructure to expose the data about the underlying instance being edited.</span></span> <span data-ttu-id="e072f-106">下圖描述 [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)] 內基礎結構的各個不同層。</span><span class="sxs-lookup"><span data-stu-id="e072f-106">The following illustration is a depiction of the various layers of infrastructure within the [!INCLUDE[wfd2](../../../../includes/wfd2-md.md)].</span></span>  
  
 <span data-ttu-id="e072f-107">![Workflow Designer 架構](../../../../docs/framework/windows-workflow-foundation/samples/media/workflowdesignerarch.JPG "WorkflowDesignerArch")</span><span class="sxs-lookup"><span data-stu-id="e072f-107">![Workflow Designer Architecture](../../../../docs/framework/windows-workflow-foundation/samples/media/workflowdesignerarch.JPG "WorkflowDesignerArch")</span></span>  
  
 <span data-ttu-id="e072f-108"><xref:System.Activities.Presentation.Model.ModelItem> 包含基礎值的指標，以及 <xref:System.Activities.Presentation.Model.ModelProperty> 物件的集合。</span><span class="sxs-lookup"><span data-stu-id="e072f-108">A <xref:System.Activities.Presentation.Model.ModelItem> consists of a pointer to the underlying value, as well as a collection of <xref:System.Activities.Presentation.Model.ModelProperty> objects.</span></span> <span data-ttu-id="e072f-109"><xref:System.Activities.Presentation.Model.ModelProperty> 物件則是由名稱、屬性型別和值的指標這類資料所構成，而值的指標則會是另一個 <xref:System.Activities.Presentation.Model.ModelItem>。</span><span class="sxs-lookup"><span data-stu-id="e072f-109">A <xref:System.Activities.Presentation.Model.ModelProperty> object in turn, consists of data such as the name and type of the property and then a pointer to the value, which in turn, is another <xref:System.Activities.Presentation.Model.ModelItem>.</span></span> <span data-ttu-id="e072f-110">值轉換子可用來操作從 <xref:System.Activities.Presentation.Model.ModelItem> 傳回的一些 <xref:System.Activities.Presentation.Model.ModelProperty>，讓它們在樹狀檢視中正確顯示。</span><span class="sxs-lookup"><span data-stu-id="e072f-110">A value converter is used to manipulate some of the <xref:System.Activities.Presentation.Model.ModelItem>s returned from a <xref:System.Activities.Presentation.Model.ModelProperty> to make them appear correctly in the tree view.</span></span> <span data-ttu-id="e072f-111">接著這個範例會示範如何使用命令式語法，以命令方式對 <xref:System.Activities.Presentation.Model.ModelItem> 樹狀結構進行程式設計，如下面範例中所示。</span><span class="sxs-lookup"><span data-stu-id="e072f-111">The sample then demonstrates how to imperatively program against the <xref:System.Activities.Presentation.Model.ModelItem> tree using the imperative syntax, as seen in the following example.</span></span>  
  
```csharp  
ModelItem mi = wd.Context.Services.GetService<ModelService>().Root;  
ModelProperty mp = mi.Properties["Activities"];  
mp.Collection.Add(new Persist());  
ModelItem justAdded = mp.Collection.Last();  
justAdded.Properties["DisplayName"].SetValue("new name");  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="e072f-112">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="e072f-112">To use this sample</span></span>  
  
1.  <span data-ttu-id="e072f-113">在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟 [ProgrammingModelItemTree.sln] 方案。</span><span class="sxs-lookup"><span data-stu-id="e072f-113">Open the ProgrammingModelItemTree.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="e072f-114">選取 建置方案**建置方案**從**建置**功能表。</span><span class="sxs-lookup"><span data-stu-id="e072f-114">Build the solution by selecting **Build Solution** from the **Build** menu.</span></span>  
  
3.  <span data-ttu-id="e072f-115">按 F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="e072f-115">Press F5 to run the application.</span></span> <span data-ttu-id="e072f-116">[!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] 格式隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="e072f-116">The [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] form is then displayed.</span></span>  
  
4.  <span data-ttu-id="e072f-117">按一下**載入 WF**按鈕以載入<xref:System.Activities.Presentation.Model.ModelItem>並將它繫結至樹狀檢視。</span><span class="sxs-lookup"><span data-stu-id="e072f-117">Click the **Load WF** button to load the <xref:System.Activities.Presentation.Model.ModelItem> and bind it to the tree view.</span></span>  
  
5.  <span data-ttu-id="e072f-118">按一下**變更模型項目樹狀**按鈕會執行上述程式碼加入到樹狀結構項目和設定屬性。</span><span class="sxs-lookup"><span data-stu-id="e072f-118">Clicking the **Change Model Item Tree** button executes the preceding code to add an item into the tree and set a property.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e072f-119">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="e072f-119">The samples may already be installed on your computer.</span></span> <span data-ttu-id="e072f-120">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="e072f-120">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e072f-121">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="e072f-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e072f-122">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="e072f-122">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\ProgrammingModelItemTree`  
  
## <a name="see-also"></a><span data-ttu-id="e072f-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e072f-123">See Also</span></span>  
 <xref:System.Windows.Data.IValueConverter>
