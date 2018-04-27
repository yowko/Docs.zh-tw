---
title: 使用自訂運算式編輯器
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0901b58b-e037-44a8-8281-f6f54361cfca
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6e9481364a70257f6c1711692daf5c81eee9fd88
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="using-a-custom-expression-editor"></a>使用自訂運算式編輯器
可以實作自訂運算式編輯器，以提供更豐富、更簡單的運算式編輯體驗。 在一些案例中，您可能會想要使用自訂運算式編輯器：  
  
-   為 IntelliSense 和重新裝載的工作流程設計工具中其他豐富的編輯功能提供支援。 必須提供這項功能，因為無法在重新裝載的應用程式中使用預設 Visual Studio 的運算式編輯器。  
  
-   若要簡化的運算式編輯體驗，商務分析師的使用者，讓它們比方說，不需要了解 Visual Basic 或 Visual Basic 運算式處理。  
  
 實作自訂運算式編輯器所需的三個基本步驟：  
  
1.  實作 <xref:System.Activities.Presentation.View.IExpressionEditorService> 介面。 這個介面可管理建立和解構運算式編輯器。  
  
2.  實作 <xref:System.Activities.Presentation.View.IExpressionEditorInstance> 介面。 這個介面會實作運算式編輯 UI 的 UI。  
  
3.  在重新裝載的工作流程應用程式中發行 <xref:System.Activities.Presentation.View.IExpressionEditorService>。  
  
## <a name="implementing-a-custom-expression-editor-in-a-class-library"></a>在類別庫中實作自訂運算式編輯器  
 以下為 (概念證明) `MyEditorService` 類別的程式碼範例，該類別會實作包含在 MyExpressionEditorService 程式庫專案中的 <xref:System.Activities.Presentation.View.IExpressionEditorService> 介面。  
  
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
  
 以下為 `MyExpressionEditorInstance` 類別的程式碼，該類別會實作 MyExpressionEditorService 程式庫專案中的 <xref:System.Activities.Presentation.View.IExpressionEditorInstance> 介面。  
  
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
  
### <a name="publishing-a-custom-expression-editor-in-a-wpf-project"></a>在 WPF 專案中發行自訂運算式編輯器  
 以下程式碼示範如何在 [!INCLUDE[avalon2](../../../includes/avalon2-md.md)] 應用程式中重新裝載設計工具，以及如何建立和發行 `MyEditorService` 服務。 使用此程式碼前，請從包含 avalon2 應用程式的專案將參考加入到 MyExpressionEditorService 程式庫專案中。  
  
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
  
### <a name="notes"></a>注意  
 如果您使用**ExpressionTextBox**控制項中的自訂活動設計工具中，則不需要建立和終結運算式編輯器使用<xref:System.Activities.Presentation.View.IExpressionEditorService.CreateExpressionEditor%2A>和<xref:System.Activities.Presentation.View.IExpressionEditorService.CloseExpressionEditors%2A>方法<xref:System.Activities.Presentation.View.IExpressionEditorService>介面。 <xref:System.Activities.Presentation.View.ExpressionTextBox> 類別會為您管理這項工作。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Activities.Presentation.View.IExpressionEditorService>  
 <xref:System.Activities.Presentation.View.IExpressionEditorInstance>  
 [在自訂活動設計工具中使用 ExpressionTextBox](../../../docs/framework/windows-workflow-foundation/samples/using-the-expressiontextbox-in-a-custom-activity-designer.md)
