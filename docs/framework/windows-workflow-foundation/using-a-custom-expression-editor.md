---
title: "使用自訂運算式編輯器"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0901b58b-e037-44a8-8281-f6f54361cfca
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3a809c1d0eeb8f45d55f4e1f436b70ceb01b4a2f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="using-a-custom-expression-editor"></a><span data-ttu-id="91eeb-102">使用自訂運算式編輯器</span><span class="sxs-lookup"><span data-stu-id="91eeb-102">Using a Custom Expression Editor</span></span>
<span data-ttu-id="91eeb-103">可以實作自訂運算式編輯器，以提供更豐富、更簡單的運算式編輯體驗。</span><span class="sxs-lookup"><span data-stu-id="91eeb-103">A custom expression editor can be implemented to provide a richer or simpler expression editing experience.</span></span> <span data-ttu-id="91eeb-104">在一些案例中，您可能會想要使用自訂運算式編輯器：</span><span class="sxs-lookup"><span data-stu-id="91eeb-104">There are several scenarios in which you might want to use a custom expression editor:</span></span>  
  
-   <span data-ttu-id="91eeb-105">為 IntelliSense 和重新裝載的工作流程設計工具中其他豐富的編輯功能提供支援。</span><span class="sxs-lookup"><span data-stu-id="91eeb-105">To provide support for IntelliSense and other rich editing features in a rehosted workflow designer.</span></span> <span data-ttu-id="91eeb-106">由於預設的 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 運算式編輯器無法在重新裝載的應用程式中使用，因此必須提供這項功能。</span><span class="sxs-lookup"><span data-stu-id="91eeb-106">This functionality must be provided because the default [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] expression editor cannot be used in rehosted applications.</span></span>  
  
-   <span data-ttu-id="91eeb-107">為了簡化商業分析師使用者的運算式編輯體驗，如此就不需要例如學習 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 或處理 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 運算式。</span><span class="sxs-lookup"><span data-stu-id="91eeb-107">To simplify the expression editing experience for the business analyst users, so that they are not, for example, required to learn [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] or deal with [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] expressions.</span></span>  
  
 <span data-ttu-id="91eeb-108">實作自訂運算式編輯器所需的三個基本步驟：</span><span class="sxs-lookup"><span data-stu-id="91eeb-108">Three basic steps are needed to implement a custom expression editor:</span></span>  
  
1.  <span data-ttu-id="91eeb-109">實作 <xref:System.Activities.Presentation.View.IExpressionEditorService> 介面。</span><span class="sxs-lookup"><span data-stu-id="91eeb-109">Implement the <xref:System.Activities.Presentation.View.IExpressionEditorService> interface.</span></span> <span data-ttu-id="91eeb-110">這個介面可管理建立和解構運算式編輯器。</span><span class="sxs-lookup"><span data-stu-id="91eeb-110">This interface manages the creation and destruction of expression editors.</span></span>  
  
2.  <span data-ttu-id="91eeb-111">實作 <xref:System.Activities.Presentation.View.IExpressionEditorInstance> 介面。</span><span class="sxs-lookup"><span data-stu-id="91eeb-111">Implement the <xref:System.Activities.Presentation.View.IExpressionEditorInstance> interface.</span></span> <span data-ttu-id="91eeb-112">這個介面會實作運算式編輯 UI 的 UI。</span><span class="sxs-lookup"><span data-stu-id="91eeb-112">This interface implements the UI for expression editing UI.</span></span>  
  
3.  <span data-ttu-id="91eeb-113">在重新裝載的工作流程應用程式中發行 <xref:System.Activities.Presentation.View.IExpressionEditorService>。</span><span class="sxs-lookup"><span data-stu-id="91eeb-113">Publish the <xref:System.Activities.Presentation.View.IExpressionEditorService> in your rehosted workflow application.</span></span>  
  
## <a name="implementing-a-custom-expression-editor-in-a-class-library"></a><span data-ttu-id="91eeb-114">在類別庫中實作自訂運算式編輯器</span><span class="sxs-lookup"><span data-stu-id="91eeb-114">Implementing a Custom Expression Editor in a Class Library</span></span>  
 <span data-ttu-id="91eeb-115">以下為 (概念證明) `MyEditorService` 類別的程式碼範例，該類別會實作包含在 MyExpressionEditorService 程式庫專案中的 <xref:System.Activities.Presentation.View.IExpressionEditorService> 介面。</span><span class="sxs-lookup"><span data-stu-id="91eeb-115">Here is a sample of code for a (proof of concept) `MyEditorService` class that implements the <xref:System.Activities.Presentation.View.IExpressionEditorService> interface is contained in a MyExpressionEditorService library project.</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Activities.Presentation.View;  
using System.Activities.Presentation.Hosting;  
using System.Activities.Presentation.Model;  
  
namespace MyExpressionEditorService  
{  
    public class MyEditorService : IExpressionEditorService  
    {  
        public void CloseExpressionEditors()  
        {  
  
        }  
        public IExpressionEditorInstance CreateExpressionEditor(AssemblyContextControlItem assemblies, ImportedNamespaceContextItem importedNamespaces, List<ModelItem> variables, string text)  
        {  
            MyExpressionEditorInstance instance = new MyExpressionEditorInstance();  
            return instance;  
        }  
        public IExpressionEditorInstance CreateExpressionEditor(AssemblyContextControlItem assemblies, ImportedNamespaceContextItem importedNamespaces, List<ModelItem> variables, string text, System.Windows.Size initialSize)  
                {  
            MyExpressionEditorInstance instance = new MyExpressionEditorInstance();  
            return instance;  
        }  
        public IExpressionEditorInstance CreateExpressionEditor(AssemblyContextControlItem assemblies, ImportedNamespaceContextItem importedNamespaces, List<ModelItem> variables, string text, Type expressionType)  
            {  
            MyExpressionEditorInstance instance = new MyExpressionEditorInstance();  
            return instance;  
        }  
        public IExpressionEditorInstance CreateExpressionEditor(AssemblyContextControlItem assemblies, ImportedNamespaceContextItem importedNamespaces, List<ModelItem> variables, string text, Type expressionType, System.Windows.Size initialSize)  
        {  
            MyExpressionEditorInstance instance = new MyExpressionEditorInstance();  
            return instance;  
        }  
        public void UpdateContext(AssemblyContextControlItem assemblies, ImportedNamespaceContextItem importedNamespaces)  
        {  
  
        }  
  
    }  
}  
```  
  
 <span data-ttu-id="91eeb-116">以下為 `MyExpressionEditorInstance` 類別的程式碼，該類別會實作 MyExpressionEditorService 程式庫專案中的 <xref:System.Activities.Presentation.View.IExpressionEditorInstance> 介面。</span><span class="sxs-lookup"><span data-stu-id="91eeb-116">Here is the code for a `MyExpressionEditorInstance` class that implements the <xref:System.Activities.Presentation.View.IExpressionEditorInstance> interface in a MyExpressionEditorService library project.</span></span>  
  
```  
using System;  
using System.Activities.Presentation.View;  
using System.Windows;  
using System.Reflection;  
using System.Windows.Controls;  
  
namespace MyExpressionEditorService  
{  
    public class MyExpressionEditorInstance : IExpressionEditorInstance  
    {  
        private TextBox textBox = new TextBox();  
  
        public bool AcceptsReturn { get; set; }  
        public bool AcceptsTab { get; set; }  
        public bool HasAggregateFocus {  
            get  
            {  
                return true;  
            }  
        }  
  
        public System.Windows.Controls.ScrollBarVisibility HorizontalScrollBarVisibility { get; set; }  
        public System.Windows.Controls.Control HostControl {  
            get  
            {  
                return textBox;  
            }  
        }  
        public int MaxLines { get; set; }  
        public int MinLines { get; set; }  
        public string Text { get; set; }  
        public System.Windows.Controls.ScrollBarVisibility VerticalScrollBarVisibility { get; set; }  
  
        public event EventHandler Closing;  
        public event EventHandler GotAggregateFocus;  
        public event EventHandler LostAggregateFocus;  
        public event EventHandler TextChanged;  
  
        public bool CanCompleteWord()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanCopy()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanCut()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanDecreaseFilterLevel()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanGlobalIntellisense()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanIncreaseFilterLevel()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanParameterInfo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanPaste()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanQuickInfo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanRedo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool CanUndo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
  
        public void ClearSelection()  
        {  
            MessageBox.Show(MethodBase.GetCurrentMethod().Name);  
        }  
        public void Close()  
        {  
            MessageBox.Show(MethodBase.GetCurrentMethod().Name);  
        }  
        public bool CompleteWord()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool Copy()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool Cut()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool DecreaseFilterLevel()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public void Focus()  
        {  
            MessageBox.Show(MethodBase.GetCurrentMethod().Name);  
        }  
        public string GetCommittedText()  
        {  
            return "CommittedText";  
        }  
        public bool GlobalIntellisense()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool IncreaseFilterLevel()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool ParameterInfo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool Paste()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool QuickInfo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool Redo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
        public bool Undo()  
        {  
            return (MessageBox.Show(MethodBase.GetCurrentMethod().Name, "TestEditorInstance", MessageBoxButton.YesNo) == MessageBoxResult.Yes);  
        }  
    }  
}  
```  
  
### <a name="publishing-a-custom-expression-editor-in-a-wpf-project"></a><span data-ttu-id="91eeb-117">在 WPF 專案中發行自訂運算式編輯器</span><span class="sxs-lookup"><span data-stu-id="91eeb-117">Publishing a Custom Expression Editor in a WPF Project</span></span>  
 <span data-ttu-id="91eeb-118">以下程式碼示範如何在 [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] 應用程式中重新裝載設計工具，以及如何建立和發行 `MyEditorService` 服務。</span><span class="sxs-lookup"><span data-stu-id="91eeb-118">Here is the code that shows how to rehost the designer in a [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] application and how to create and publish the `MyEditorService` service.</span></span> <span data-ttu-id="91eeb-119">使用此程式碼前，請從包含 avalon2 應用程式的專案將參考加入到 MyExpressionEditorService 程式庫專案中。</span><span class="sxs-lookup"><span data-stu-id="91eeb-119">Before using this code, add a reference to the MyExpressionEditorService library project from the project that contains the avalon2 application.</span></span>  
  
```  
using System.Windows;  
using System.Windows.Controls;  
using System.Activities.Presentation;  
using System.Activities.Statements;  
using System.Activities.Core.Presentation;  
using System.Activities.Presentation.View;  
using MyExpressionEditorService;  
  
namespace WpfApplication1  
{  
    /// <summary>  
    /// Interaction logic for MainWindow.xaml  
    /// </summary>  
    public partial class MainWindow : Window  
    {  
  
        private MyEditorService expressionEditorService;  
        public MainWindow()  
        {  
            InitializeComponent();  
            new DesignerMetadata().Register();  
            createDesigner();  
        }  
  
        public void createDesigner()  
        {  
            WorkflowDesigner designer = new WorkflowDesigner();  
            Sequence root = new Sequence()  
            {  
                Activities = {  
                new Assign(),  
                new WriteLine()}  
            };  
  
            designer.Load(root);  
  
            Grid.SetColumn(designer.View, 0);  
  
            // Create ExpressionEditorService   
            this.expressionEditorService = new MyEditorService();  
  
            // Publish the instance of MyEditorService.  
            designer.Context.Services.Publish<IExpressionEditorService>(this.expressionEditorService);  
  
            MyGrid.Children.Add(designer.View);  
        }  
    }  
}  
```  
  
### <a name="notes"></a><span data-ttu-id="91eeb-120">注意</span><span class="sxs-lookup"><span data-stu-id="91eeb-120">Notes</span></span>  
 <span data-ttu-id="91eeb-121">如果您使用**ExpressionTextBox**控制項中的自訂活動設計工具中，則不需要建立和終結運算式編輯器使用<xref:System.Activities.Presentation.View.IExpressionEditorService.CreateExpressionEditor%2A>和<xref:System.Activities.Presentation.View.IExpressionEditorService.CloseExpressionEditors%2A>方法<xref:System.Activities.Presentation.View.IExpressionEditorService>介面。</span><span class="sxs-lookup"><span data-stu-id="91eeb-121">If you are using an **ExpressionTextBox** control in a custom activity designer, it is not necessary to create and destroy expression editors using the <xref:System.Activities.Presentation.View.IExpressionEditorService.CreateExpressionEditor%2A> and <xref:System.Activities.Presentation.View.IExpressionEditorService.CloseExpressionEditors%2A> methods of the <xref:System.Activities.Presentation.View.IExpressionEditorService> interface.</span></span> <span data-ttu-id="91eeb-122"><xref:System.Activities.Presentation.View.ExpressionTextBox> 類別會為您管理這項工作。</span><span class="sxs-lookup"><span data-stu-id="91eeb-122">The <xref:System.Activities.Presentation.View.ExpressionTextBox> class manages this for you.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91eeb-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91eeb-123">See Also</span></span>  
 <xref:System.Activities.Presentation.View.IExpressionEditorService>  
 <xref:System.Activities.Presentation.View.IExpressionEditorInstance>  
 [<span data-ttu-id="91eeb-124">使用自訂活動設計工具中的 ExpressionTextBox</span><span class="sxs-lookup"><span data-stu-id="91eeb-124">Using the ExpressionTextBox in a Custom Activity Designer</span></span>](../../../docs/framework/windows-workflow-foundation/samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)
