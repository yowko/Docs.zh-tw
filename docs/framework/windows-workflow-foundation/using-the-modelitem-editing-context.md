---
title: 使用 ModelItem 編輯內容
ms.date: 03/30/2017
ms.assetid: 7f9f1ea5-0147-4079-8eca-be94f00d3aa1
ms.openlocfilehash: a2628bbbf2f6684e5d484b05cd5a2ac622f3b664
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59296874"
---
# <a name="using-the-modelitem-editing-context"></a>使用 ModelItem 編輯內容
<xref:System.Activities.Presentation.Model.ModelItem> 編輯內容是主機應用程式用來與設計工具通訊的物件。 <xref:System.Activities.Presentation.EditingContext> 會公開兩個方法：<xref:System.Activities.Presentation.EditingContext.Items%2A>和<xref:System.Activities.Presentation.EditingContext.Services%2A>，可以使用  
  
## <a name="the-items-collection"></a>Items 集合  
 <xref:System.Activities.Presentation.EditingContext.Items%2A> 集合是用來存取在主機與設計工具之間共用的資料，或是提供給所有設計工具的資料。 這個集合具有下列功能 (經由 <xref:System.Activities.Presentation.ContextItemManager> 類別存取)：  
  
1. <xref:System.Activities.Presentation.ContextItemManager.GetValue%2A>  
  
2. <xref:System.Activities.Presentation.ContextItemManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ContextItemManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A>  
  
## <a name="the-services-collection"></a>Services 集合  
 <xref:System.Activities.Presentation.EditingContext.Services%2A> 集合是用來存取設計工具與主機互動所用的服務，或是所有設計工具使用的服務。 這個集合具有下列重要方法：  
  
1. <xref:System.Activities.Presentation.ServiceManager.Publish%2A>  
  
2. <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A>  
  
3. <xref:System.Activities.Presentation.ServiceManager.Unsubscribe%2A>  
  
4. <xref:System.Activities.Presentation.ServiceManager.GetService%2A>  
  
## <a name="assigning-a-designer-an-activity"></a>將活動指派給設計工具  
 若要指定活動所使用的設計工具，請使用 Designer 屬性。  
  
```  
[Designer(typeof(MyClassDesigner))]  
public sealed class MyClass : CodeActivity  
{  
```  
  
## <a name="creating-a-service"></a>建立服務  
 若要建立在設計工具與主機之間當做資訊管道的服務，您必須建立介面和實作。 <xref:System.Activities.Presentation.ServiceManager.Publish%2A> 方法會使用此介面來定義服務的成員，而且此實作包含服務的邏輯。 在下列程式碼範例中，系統會建立服務介面和實作。  
  
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
  
## <a name="publishing-a-service"></a>發行服務  
 為了讓設計工具取用服務，主機必須先使用 <xref:System.Activities.Presentation.ServiceManager.Publish%2A> 方法來發行服務。  
  
```  
this.Context.Services.Publish<IMyService>(new MyServiceImpl);  
```  
  
## <a name="subscribing-to-a-service"></a>訂閱服務  
 設計工具會使用 <xref:System.Activities.Presentation.ServiceManager.Subscribe%2A> 方法中的 <xref:System.Activities.Presentation.WorkflowViewElement.OnModelItemChanged%2A> 方法來取得服務的存取權。 下列程式碼片段示範如何訂閱服務。  
  
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
  
## <a name="sharing-data-using-the-items-collection"></a>使用 Items 集合共用資料  
 使用 Items 集合與使用 Services 集合很相似，不過 <xref:System.Activities.Presentation.ContextItemManager.SetValue%2A> 會用來取代 Publish。 這個集合比較適合在設計工具與主機之間共用簡單的資料，而非複雜的功能。  
  
## <a name="editingcontext-host-items-and-services"></a>EditingContext 主機項目和服務  
 .NET Framework 提供許多內建項目和透過編輯內容存取的服務。  
  
 Items：  
  
-   <xref:System.Activities.Presentation.Hosting.AssemblyContextControlItem>:管理將會用於工作流程內部控制項 （例如 「 運算式編輯器 」 中） 的參考本機組件的清單。  
  
-   <xref:System.Activities.Presentation.Hosting.ReadOnlyState>:表示設計工具是否處於唯讀狀態。  
  
-   <xref:System.Activities.Presentation.View.Selection>:定義目前選取之物件的集合。  
  
-   <xref:System.Activities.Presentation.Hosting.WorkflowCommandExtensionItem>:  
  
-   <xref:System.Activities.Presentation.WorkflowFileItem>:提供目前編輯工作階段為基礎的檔案的相關資訊。  
  
 Services：  
  
-   <xref:System.Activities.Presentation.Model.AttachedPropertiesService>:可讓屬性加入至目前的執行個體，使用<xref:System.Activities.Presentation.Model.AttachedPropertiesService.AddProperty%2A>。  
  
-   <xref:System.Activities.Presentation.View.DesignerView>:允許存取設計工具畫布的屬性。  
  
-   <xref:System.Activities.Presentation.IActivityToolboxService>:允許更新工具箱的內容。  
  
-   <xref:System.Activities.Presentation.Hosting.ICommandService>:用來整合設計工具的命令 （例如操作功能表） 與提供的自訂服務實作。  
  
-   <xref:System.Activities.Presentation.Debug.IDesignerDebugView>:提供設計工具的偵錯工具的功能。  
  
-   <xref:System.Activities.Presentation.View.IExpressionEditorService>:提供存取 [運算式編輯器] 對話方塊。  
  
-   <xref:System.Activities.Presentation.IIntegratedHelpService>:為設計工具提供整合式的說明功能。  
  
-   <xref:System.Activities.Presentation.Validation.IValidationErrorService>:使用的驗證錯誤提供存取<xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A>。  
  
-   <xref:System.Activities.Presentation.IWorkflowDesignerStorageService>:提供內部服務來儲存和擷取資料。 此服務由.NET Framework 中，內部使用，並不適合外部使用。  
  
-   <xref:System.Activities.Presentation.IXamlLoadErrorService>:可讓您存取 XAML 載入錯誤集合使用<xref:System.Activities.Presentation.IXamlLoadErrorService.ShowXamlLoadErrors%2A>。  
  
-   <xref:System.Activities.Presentation.Services.ModelService>:供設計工具使用，與正在編輯之工作流程的模型進行互動。  
  
-   <xref:System.Activities.Presentation.Model.ModelTreeManager>:提供存取權的模型項目樹狀目錄中使用根<xref:System.Activities.Presentation.Model.ModelItem.Root%2A>。  
  
-   <xref:System.Activities.Presentation.UndoEngine>:提供復原和取消復原功能。  
  
-   <xref:System.Activities.Presentation.Services.ViewService>:將視覺元素對應至基礎模型項目。  
  
-   <xref:System.Activities.Presentation.View.ViewStateService>:儲存檢視模型項目的狀態。  
  
-   <xref:System.Activities.Presentation.View.VirtualizedContainerService>:用來自訂虛擬容器 UI 行為。  
  
-   <xref:System.Activities.Presentation.Hosting.WindowHelperService>:用來註冊和取消註冊事件通知的委派。 它也允許設定視窗擁有者。
