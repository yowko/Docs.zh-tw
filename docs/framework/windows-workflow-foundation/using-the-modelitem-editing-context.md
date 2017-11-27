---
title: "使用 ModelItem 編輯內容"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7f9f1ea5-0147-4079-8eca-be94f00d3aa1
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fde8bf45e01f8e3fede04c08d63177271a4a6faf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="using-the-modelitem-editing-context"></a><span data-ttu-id="e311e-102">使用 ModelItem 編輯內容</span><span class="sxs-lookup"><span data-stu-id="e311e-102">Using the ModelItem Editing Context</span></span>
<span data-ttu-id="e311e-103"><xref:System.Activities.Presentation.Model.ModelItem> 編輯內容是主機應用程式用來與設計工具通訊的物件。</span><span class="sxs-lookup"><span data-stu-id="e311e-103">The <xref:System.Activities.Presentation.Model.ModelItem> editing context is the object that the host application uses to communicate with the designer.</span></span> <span data-ttu-id="e311e-104"><xref:System.Activities.Presentation.EditingContext> 公開兩個可使用的方法：<xref:System.Activities.Presentation.EditingContext.Items%2A> 和 <xref:System.Activities.Presentation.EditingContext.Services%2A></span><span class="sxs-lookup"><span data-stu-id="e311e-104"><xref:System.Activities.Presentation.EditingContext> exposes two methods, <xref:System.Activities.Presentation.EditingContext.Items%2A> and <xref:System.Activities.Presentation.EditingContext.Services%2A>, which can be used</span></span>  
  
## <a name="the-items-collection"></a><span data-ttu-id="e311e-105">Items 集合</span><span class="sxs-lookup"><span data-stu-id="e311e-105">The Items collection</span></span>  
 <span data-ttu-id="e311e-106"><xref:System.Activities.Presentation.EditingContext.Items%2A> 集合是用來存取在主機與設計工具之間共用的資料，或是提供給所有設計工具的資料。</span><span class="sxs-lookup"><span data-stu-id="e311e-106">The <xref:System.Activities.Presentation.EditingContext.Items%2A> collection is used to access data that is shared between the host and the designer, or data that is available to all designers.</span></span> <span data-ttu-id="e311e-107">這個集合具有下列功能 (經由 <xref:System.Activities.Presentation.ContextItemManager> 類別存取)：</span><span class="sxs-lookup"><span data-stu-id="e311e-107">This collection has the following capabilities, accessed via the <xref:System.Activities.Presentation.ContextItemManager> class:</span></span>  
  
1.  <xref:System.Activities.Presentation.ContextItemManager.GetValue%2A>  
  
2.  <xref:System.Activities.Presentation.ContextItemManager.Subscribe%2A>  
  
3.  <xref:System.Activities.Presentation.ContextItemManager.Unsubscribe%2A>  
  
4.  <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A>  
  
## <a name="the-services-collection"></a><span data-ttu-id="e311e-108">Services 集合</span><span class="sxs-lookup"><span data-stu-id="e311e-108">The Services collection</span></span>  
 <span data-ttu-id="e311e-109"><xref:System.Activities.Presentation.EditingContext.Services%2A> 集合是用來存取設計工具與主機互動所用的服務，或是所有設計工具使用的服務。</span><span class="sxs-lookup"><span data-stu-id="e311e-109">The <xref:System.Activities.Presentation.EditingContext.Services%2A> collection is used to access services that the designer uses to interact with the host, or services that all designers use.</span></span> <span data-ttu-id="e311e-110">這個集合具有下列重要方法：</span><span class="sxs-lookup"><span data-stu-id="e311e-110">This collection has the following methods of note:</span></span>  
  
1.  <xref:System.Activities.Presentation.ServiceManager.Publish%2A>  
  
2.  <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A>  
  
3.  <xref:System.Activities.Presentation.ServiceManager.Unsubscribe%2A>  
  
4.  <xref:System.Activities.Presentation.ServiceManager.GetService%2A>  
  
## <a name="assigning-a-designer-an-activity"></a><span data-ttu-id="e311e-111">將活動指派給設計工具</span><span class="sxs-lookup"><span data-stu-id="e311e-111">Assigning a designer an activity</span></span>  
 <span data-ttu-id="e311e-112">若要指定活動所使用的設計工具，請使用 Designer 屬性。</span><span class="sxs-lookup"><span data-stu-id="e311e-112">To specify which designer an activity uses, the Designer attribute is used.</span></span>  
  
```  
[Designer(typeof(MyClassDesigner))]  
public sealed class MyClass : CodeActivity  
{  
```  
  
## <a name="creating-a-service"></a><span data-ttu-id="e311e-113">建立服務</span><span class="sxs-lookup"><span data-stu-id="e311e-113">Creating a service</span></span>  
 <span data-ttu-id="e311e-114">若要建立在設計工具與主機之間當做資訊管道的服務，您必須建立介面和實作。</span><span class="sxs-lookup"><span data-stu-id="e311e-114">To create a service that serves as a conduit of information between the designer and the host, an interface and an implementation must be created.</span></span> <span data-ttu-id="e311e-115"><xref:System.Activities.Presentation.ServiceManager.Publish%2A> 方法會使用此介面來定義服務的成員，而且此實作包含服務的邏輯。</span><span class="sxs-lookup"><span data-stu-id="e311e-115">The interface is used by the <xref:System.Activities.Presentation.ServiceManager.Publish%2A> method to define the members of the service, and the implementation contains the logic for the service.</span></span> <span data-ttu-id="e311e-116">在下列程式碼範例中，系統會建立服務介面和實作。</span><span class="sxs-lookup"><span data-stu-id="e311e-116">In the following code example, a service interface and implementation are created.</span></span>  
  
```  
public interface IMyService  
    {  
        IEnumerable<string> GetValues(string DisplayName);  
    }  
  
    public class MyServiceImpl : IMyService  
    {  
        public IEnumerable<string> GetValues(string DisplayName)  
        {  
            return new string[]  {   
                DisplayName + " One",   
                DisplayName + " Two",  
                "Three " + DisplayName  
            } ;  
        }  
    }  
```  
  
## <a name="publishing-a-service"></a><span data-ttu-id="e311e-117">發行服務</span><span class="sxs-lookup"><span data-stu-id="e311e-117">Publishing a service</span></span>  
 <span data-ttu-id="e311e-118">為了讓設計工具取用服務，主機必須先使用 <xref:System.Activities.Presentation.ServiceManager.Publish%2A> 方法來發行服務。</span><span class="sxs-lookup"><span data-stu-id="e311e-118">For a designer to consume a service, it must first be published by the host using the <xref:System.Activities.Presentation.ServiceManager.Publish%2A> method.</span></span>  
  
```  
this.Context.Services.Publish<IMyService>(new MyServiceImpl);  
```  
  
## <a name="subscribing-to-a-service"></a><span data-ttu-id="e311e-119">訂閱服務</span><span class="sxs-lookup"><span data-stu-id="e311e-119">Subscribing to a service</span></span>  
 <span data-ttu-id="e311e-120">設計工具會使用 <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> 方法中的 <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A> 方法來取得服務的存取權。</span><span class="sxs-lookup"><span data-stu-id="e311e-120">The designer obtains access to the service using the <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> method in the <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A> method.</span></span> <span data-ttu-id="e311e-121">下列程式碼片段示範如何訂閱服務。</span><span class="sxs-lookup"><span data-stu-id="e311e-121">The following code snippet demonstrates how to subscribe to a service.</span></span>  
  
```  
protected override void OnModelItemChanged(object newItem)  
{  
    if (!subscribed)  
    {  
        this.Context.Services.Subscribe<IMyService>(  
            servInstance =>  
            {  
                listBox1.ItemsSource = servInstance.GetValues(this.ModelItem.Properties["DisplayName"].ComputedValue.ToString());  
            }  
            );  
        subscribed = true;   
    }  
}  
```  
  
## <a name="sharing-data-using-the-items-collection"></a><span data-ttu-id="e311e-122">使用 Items 集合共用資料</span><span class="sxs-lookup"><span data-stu-id="e311e-122">Sharing data using the Items collection</span></span>  
 <span data-ttu-id="e311e-123">使用 Items 集合與使用 Services 集合很相似，不過 <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> 會用來取代 Publish。</span><span class="sxs-lookup"><span data-stu-id="e311e-123">Using the Items collection is similar to using the Services collection, except that <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> is used instead of Publish.</span></span> <span data-ttu-id="e311e-124">這個集合比較適合在設計工具與主機之間共用簡單的資料，而非複雜的功能。</span><span class="sxs-lookup"><span data-stu-id="e311e-124">This collection is more appropriate for sharing simple data between the designers and the host, rather than complex functionality.</span></span>  
  
## <a name="editingcontext-host-items-and-services"></a><span data-ttu-id="e311e-125">EditingContext 主機項目和服務</span><span class="sxs-lookup"><span data-stu-id="e311e-125">EditingContext host items and services</span></span>  
 <span data-ttu-id="e311e-126">.Net Framework 提供了許多透過編輯內容存取的內建項目和服務。</span><span class="sxs-lookup"><span data-stu-id="e311e-126">The .Net Framework provides a number of built-in items and services accessed through the editing context.</span></span>  
  
 <span data-ttu-id="e311e-127">Items：</span><span class="sxs-lookup"><span data-stu-id="e311e-127">Items:</span></span>  
  
-   <span data-ttu-id="e311e-128"><xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem>：管理參考本機組件的清單，這些組件將會用於控制項的工作流程內部 (例如運算式編輯器)。</span><span class="sxs-lookup"><span data-stu-id="e311e-128"><xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem>: Manages the list of referenced local assemblies that will be used inside the workflow for controls (such as the expression editor).</span></span>  
  
-   <span data-ttu-id="e311e-129"><xref:System.Activities.Presentation.Hosting.ReadOnlyState>：指出設計工具是否處於唯讀狀態。</span><span class="sxs-lookup"><span data-stu-id="e311e-129"><xref:System.Activities.Presentation.Hosting.ReadOnlyState>: Indicates whether the designer is in a read-only state.</span></span>  
  
-   <span data-ttu-id="e311e-130"><xref:System.Activities.Presentation.View.Selection>：定義目前選取的物件集合。</span><span class="sxs-lookup"><span data-stu-id="e311e-130"><xref:System.Activities.Presentation.View.Selection>: Defines the collection of objects that are currently selected.</span></span>  
  
-   <span data-ttu-id="e311e-131"><xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem>:</span><span class="sxs-lookup"><span data-stu-id="e311e-131"><xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem>:</span></span>  
  
-   <span data-ttu-id="e311e-132"><xref:System.Activities.Presentation.WorkflowFileItem>：提供目前編輯工作階段所依據之檔案的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e311e-132"><xref:System.Activities.Presentation.WorkflowFileItem>: Provides information on the file that the current editing session is based on.</span></span>  
  
 <span data-ttu-id="e311e-133">Services：</span><span class="sxs-lookup"><span data-stu-id="e311e-133">Services:</span></span>  
  
-   <span data-ttu-id="e311e-134"><xref:System.Activities.Presentation.Model.AttachedPropertiesService>：允許使用 <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>，將屬性加入至目前執行個體。</span><span class="sxs-lookup"><span data-stu-id="e311e-134"><xref:System.Activities.Presentation.Model.AttachedPropertiesService>: Allows properties to be added to the current instance, using <xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>.</span></span>  
  
-   <span data-ttu-id="e311e-135"><xref:System.Activities.Presentation.View.DesignerView>：允許存取設計工具畫布的屬性。</span><span class="sxs-lookup"><span data-stu-id="e311e-135"><xref:System.Activities.Presentation.View.DesignerView>: Allows access to the properties of the designer canvas.</span></span>  
  
-   <span data-ttu-id="e311e-136"><xref:System.Activities.Presentation.IActivityToolboxService>：允許更新工具箱的內容。</span><span class="sxs-lookup"><span data-stu-id="e311e-136"><xref:System.Activities.Presentation.IActivityToolboxService>: Allows the contents of the toolbox to be updated.</span></span>  
  
-   <span data-ttu-id="e311e-137"><xref:System.Activities.Presentation.Hosting.ICommandService>：用來整合設計工具命令 (例如內容功能表) 與提供的自訂服務實作。</span><span class="sxs-lookup"><span data-stu-id="e311e-137"><xref:System.Activities.Presentation.Hosting.ICommandService>: Used to integrate designer commands (such as Context Menu) with custom-provided service implementations.</span></span>  
  
-   <span data-ttu-id="e311e-138"><xref:System.Activities.Presentation.Debug.IDesignerDebugView>：提供設計工具之偵錯工具的功能。</span><span class="sxs-lookup"><span data-stu-id="e311e-138"><xref:System.Activities.Presentation.Debug.IDesignerDebugView>: Provides functionality for the designer debugger.</span></span>  
  
-   <span data-ttu-id="e311e-139"><xref:System.Activities.Presentation.View.IExpressionEditorService>：可讓您存取 [運算式編輯器] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e311e-139"><xref:System.Activities.Presentation.View.IExpressionEditorService>: Provides access to the Expression Editor dialog.</span></span>  
  
-   <span data-ttu-id="e311e-140"><xref:System.Activities.Presentation.IIntegratedHelpService>：為設計工具提供整合式說明功能。</span><span class="sxs-lookup"><span data-stu-id="e311e-140"><xref:System.Activities.Presentation.IIntegratedHelpService>: Provides the designer with integrated help functionality.</span></span>  
  
-   <span data-ttu-id="e311e-141"><xref:System.Activities.Presentation.Validation.IValidationErrorService>：可讓您使用 <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> 來存取驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="e311e-141"><xref:System.Activities.Presentation.Validation.IValidationErrorService>: Provides access to validation errors using <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>.</span></span>  
  
-   <span data-ttu-id="e311e-142"><xref:System.Activities.Presentation.IWorkflowDesignerStorageService>：提供內部服務來儲存和擷取資料。</span><span class="sxs-lookup"><span data-stu-id="e311e-142"><xref:System.Activities.Presentation.IWorkflowDesignerStorageService>: Provides an internal service to store and retrieve data.</span></span> <span data-ttu-id="e311e-143">這項服務是供 .Net Framework 內部使用，不適合外部使用。</span><span class="sxs-lookup"><span data-stu-id="e311e-143">This service is used internally by the .Net Framework, and is not intended for external use.</span></span>  
  
-   <span data-ttu-id="e311e-144"><xref:System.Activities.Presentation.IXamlLoadErrorService>：可讓您使用 <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A> 來存取 XAML 載入錯誤集合。</span><span class="sxs-lookup"><span data-stu-id="e311e-144"><xref:System.Activities.Presentation.IXamlLoadErrorService>: Provides access to the XAML load error collection using <xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>.</span></span>  
  
-   <span data-ttu-id="e311e-145"><xref:System.Activities.Presentation.Services.ModelService>：設計工具用來與所編輯之工作流程的模型互動。</span><span class="sxs-lookup"><span data-stu-id="e311e-145"><xref:System.Activities.Presentation.Services.ModelService>: Used by the designer to interact with the model of the workflow being edited.</span></span>  
  
-   <span data-ttu-id="e311e-146"><xref:System.Activities.Presentation.Model.ModelTreeManager>：可讓您使用 <xref:System.Activities.Presentation.Model.ModelItem.Root%2A> 來存取模型項目樹狀結構的根。</span><span class="sxs-lookup"><span data-stu-id="e311e-146"><xref:System.Activities.Presentation.Model.ModelTreeManager>: Provides access to the root of the model item tree using <xref:System.Activities.Presentation.Model.ModelItem.Root%2A>.</span></span>  
  
-   <span data-ttu-id="e311e-147"><xref:System.Activities.Presentation.UndoEngine>：提供復原和取消復原功能。</span><span class="sxs-lookup"><span data-stu-id="e311e-147"><xref:System.Activities.Presentation.UndoEngine>: Provides undo and redo functionality.</span></span>  
  
-   <span data-ttu-id="e311e-148"><xref:System.Activities.Presentation.Services.ViewService>：將視覺化項目對應至基礎模型項目。</span><span class="sxs-lookup"><span data-stu-id="e311e-148"><xref:System.Activities.Presentation.Services.ViewService>: Maps visual elements to underlying model items.</span></span>  
  
-   <span data-ttu-id="e311e-149"><xref:System.Activities.Presentation.View.ViewStateService>：儲存模型項目的檢視狀態。</span><span class="sxs-lookup"><span data-stu-id="e311e-149"><xref:System.Activities.Presentation.View.ViewStateService>: Stores view states for model items.</span></span>  
  
-   <span data-ttu-id="e311e-150"><xref:System.Activities.Presentation.View.VirtualizedContainerService>：用來自訂虛擬容器 UI 行為。</span><span class="sxs-lookup"><span data-stu-id="e311e-150"><xref:System.Activities.Presentation.View.VirtualizedContainerService>: Used to customize the virtual container UI behavior.</span></span>  
  
-   <span data-ttu-id="e311e-151"><xref:System.Activities.Presentation.Hosting.WindowHelperService>：用來註冊和取消註冊事件通知的委派。</span><span class="sxs-lookup"><span data-stu-id="e311e-151"><xref:System.Activities.Presentation.Hosting.WindowHelperService>: Used to register and unregister delegates for event notifications.</span></span> <span data-ttu-id="e311e-152">它也允許設定視窗擁有者。</span><span class="sxs-lookup"><span data-stu-id="e311e-152">Also allows a window owner to be set.</span></span>
