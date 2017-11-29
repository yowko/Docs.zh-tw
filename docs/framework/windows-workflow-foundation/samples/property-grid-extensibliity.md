---
title: "屬性方格擴充性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3530c3a3-756d-4712-9f10-fb2897414d3a
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e0df8ed572a0a02147e3bdf45dd880305363e8bd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="property-grid-extensibliity"></a><span data-ttu-id="227b0-102">屬性方格擴充性</span><span class="sxs-lookup"><span data-stu-id="227b0-102">Property Grid Extensibliity</span></span>
<span data-ttu-id="227b0-103">開發人員可以自訂在設計工具內選取指定活動時顯示的屬性方格。</span><span class="sxs-lookup"><span data-stu-id="227b0-103">A developer can customize the property grid that is displayed when a given activity is selected within the designer.</span></span> <span data-ttu-id="227b0-104">這樣做可以製造豐富的編輯經驗。</span><span class="sxs-lookup"><span data-stu-id="227b0-104">This can be done to create a rich editing experience.</span></span> <span data-ttu-id="227b0-105">這個範例將示範其做法。</span><span class="sxs-lookup"><span data-stu-id="227b0-105">This sample shows how this can be done.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="227b0-106">示範</span><span class="sxs-lookup"><span data-stu-id="227b0-106">Demonstrates</span></span>  
 <span data-ttu-id="227b0-107">工作流程設計工具屬性方格擴充性。</span><span class="sxs-lookup"><span data-stu-id="227b0-107">Workflow designer property grid extensibility.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="227b0-108">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="227b0-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="227b0-109">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="227b0-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="227b0-110">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="227b0-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="227b0-111">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="227b0-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`  
  
## <a name="discussion"></a><span data-ttu-id="227b0-112">討論</span><span class="sxs-lookup"><span data-stu-id="227b0-112">Discussion</span></span>  
 <span data-ttu-id="227b0-113">若要擴充屬性方格，開發人員可以選擇自訂屬性方格編輯器的內嵌外觀，或是提供對話方塊，顯示更進階的編輯介面。</span><span class="sxs-lookup"><span data-stu-id="227b0-113">To extend the property grid, a developer has options to customize the inline appearance of a property grid editor or provide a dialog that appears for a more advanced editing surface.</span></span> <span data-ttu-id="227b0-114">本範例中會示範兩種不同的編輯器：內嵌編輯器和對話方塊編輯器。</span><span class="sxs-lookup"><span data-stu-id="227b0-114">There are two different editors demonstrated in this sample; an inline editor and a dialog editor.</span></span>  
  
## <a name="inline-editor"></a><span data-ttu-id="227b0-115">內嵌編輯器</span><span class="sxs-lookup"><span data-stu-id="227b0-115">Inline Editor</span></span>  
 <span data-ttu-id="227b0-116">內嵌編輯器範例會示範下列操作：</span><span class="sxs-lookup"><span data-stu-id="227b0-116">The inline editor sample demonstrates the following:</span></span>  
  
-   <span data-ttu-id="227b0-117">建立衍生自 <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor> 的型別。</span><span class="sxs-lookup"><span data-stu-id="227b0-117">Creates a type that derives from <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor>.</span></span>  
  
-   <span data-ttu-id="227b0-118">在建構函式中，<xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> 值是使用 [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] 資料範本設定。</span><span class="sxs-lookup"><span data-stu-id="227b0-118">In the constructor, the <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> value is set with a [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] data template.</span></span> <span data-ttu-id="227b0-119">這個值可繫結至 XAML 範本，但是本範例會使用程式碼初始化資料繫結。</span><span class="sxs-lookup"><span data-stu-id="227b0-119">This can be bound to a XAML template, but in this sample, code is used to initialize data binding.</span></span>  
  
-   <span data-ttu-id="227b0-120">資料範本擁有屬性方格中所呈現項目之 <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> 的資料內容。</span><span class="sxs-lookup"><span data-stu-id="227b0-120">The data template has a data context of the <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> of the item rendered in the property grid.</span></span> <span data-ttu-id="227b0-121">請注意，在下列程式碼 (來自 CustomInlineEditor.cs) 中，此內容會接著繫結至 `Value` 屬性。</span><span class="sxs-lookup"><span data-stu-id="227b0-121">Note in the following code (from CustomInlineEditor.cs) that this context then binds to the `Value` property.</span></span>  
  
    ```csharp  
    FrameworkElementFactory stack = new FrameworkElementFactory(typeof(StackPanel));  
    FrameworkElementFactory slider = new FrameworkElementFactory(typeof(Slider));  
    Binding sliderBinding = new Binding("Value");  
    sliderBinding.Mode = BindingMode.TwoWay;  
    slider.SetValue(Slider.MinimumProperty, 0.0);  
    slider.SetValue(Slider.MaximumProperty, 100.0);  
    slider.SetValue(Slider.ValueProperty, sliderBinding);  
    stack.AppendChild(slider);  
    ```  
  
-   <span data-ttu-id="227b0-122">由於活動和設計工具位於相同組件中，因此活動設計工具屬性的登錄是在活動本身的靜態建構函式中完成，如 SimpleCodeActivity.cs 中的下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="227b0-122">Because the activity and the designer are in the same assembly, registration of the activity designer attributes are accomplished in the static constructor of the activity itself, as shown in the following example from SimpleCodeActivity.cs.</span></span>  
  
    ```  
    static SimpleCodeActivity()  
    {  
        AttributeTableBuilder builder = new AttributeTableBuilder();  
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));  
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));  
        MetadataStore.AddAttributeTable(builder.CreateTable());  
    }  
    ```  
  
## <a name="dialog-editor"></a><span data-ttu-id="227b0-123">對話方塊編輯器</span><span class="sxs-lookup"><span data-stu-id="227b0-123">Dialog Editor</span></span>  
 <span data-ttu-id="227b0-124">對話方塊編輯器範例會示範下列操作：</span><span class="sxs-lookup"><span data-stu-id="227b0-124">The dialog editor sample demonstrates the following:</span></span>  
  
1.  <span data-ttu-id="227b0-125">建立衍生自 <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor> 的型別。</span><span class="sxs-lookup"><span data-stu-id="227b0-125">Creates a type that derives from <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor>.</span></span>  
  
2.  <span data-ttu-id="227b0-126">使用 <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> 資料範本設定建構函式中的 [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] 值。</span><span class="sxs-lookup"><span data-stu-id="227b0-126">Sets the <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> value in the constructor with a [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] data template.</span></span> <span data-ttu-id="227b0-127">這個值可在 XAML 中建立，但是在本範例中會使用程式碼建立。</span><span class="sxs-lookup"><span data-stu-id="227b0-127">This can be created in XAML, but in this sample, this is created in code.</span></span>  
  
3.  <span data-ttu-id="227b0-128">資料範本擁有屬性方格中所呈現項目之 <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> 的資料內容。</span><span class="sxs-lookup"><span data-stu-id="227b0-128">The data template has a data context of the <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> of the item rendered in the property grid.</span></span> <span data-ttu-id="227b0-129">在下列程式碼中，此內容會接著繫結至 `Value` 屬性。</span><span class="sxs-lookup"><span data-stu-id="227b0-129">In the following code, this then binds to the `Value` property.</span></span> <span data-ttu-id="227b0-130">此外務必包含 <xref:System.Activities.Presentation.PropertyEditing.EditModeSwitchButton>，以提供在 FilePickerEditor.cs 中引發對話方塊的按鈕。</span><span class="sxs-lookup"><span data-stu-id="227b0-130">It is critical to also include an <xref:System.Activities.Presentation.PropertyEditing.EditModeSwitchButton> to provide the button that raises the dialog in FilePickerEditor.cs.</span></span>  
  
    ```  
    this.InlineEditorTemplate = new DataTemplate();  
  
    FrameworkElementFactory stack = new FrameworkElementFactory(typeof(StackPanel));  
    stack.SetValue(StackPanel.OrientationProperty, Orientation.Horizontal);  
    FrameworkElementFactory label = new FrameworkElementFactory(typeof(Label));  
    Binding labelBinding = new Binding("Value");  
    label.SetValue(Label.ContentProperty, labelBinding);  
    label.SetValue(Label.MaxWidthProperty, 90.0);  
  
    stack.AppendChild(label);  
  
    FrameworkElementFactory editModeSwitch = new FrameworkElementFactory(typeof(EditModeSwitchButton));  
  
    editModeSwitch.SetValue(EditModeSwitchButton.TargetEditModeProperty, PropertyContainerEditMode.Dialog);  
  
    stack.AppendChild(editModeSwitch);  
  
    this.InlineEditorTemplate.VisualTree = stack;  
    ```  
  
4.  <span data-ttu-id="227b0-131">覆寫<!--zz <xref:Microsoft.Windows.Design.PropertyEditing.ShowDialog%2A>-->`Microsoft.Windows.Design.PropertyEditing.ShowDialog`設計工具的型別，以處理對話方塊的顯示中的方法。</span><span class="sxs-lookup"><span data-stu-id="227b0-131">Overrides the <!--zz <xref:Microsoft.Windows.Design.PropertyEditing.ShowDialog%2A>--> `Microsoft.Windows.Design.PropertyEditing.ShowDialog` method in the designer type to handle the display of the dialog.</span></span> <span data-ttu-id="227b0-132">在這個範例中會顯示基本的 <xref:System.Windows.Forms.FileDialog>。</span><span class="sxs-lookup"><span data-stu-id="227b0-132">In this sample, a basic <xref:System.Windows.Forms.FileDialog> is shown.</span></span>  
  
    ```  
    public override void ShowDialog(PropertyValue propertyValue, IInputElement commandSource)  
    {  
        Microsoft.Win32.OpenFileDialog ofd = new Microsoft.Win32.OpenFileDialog();  
        if (ofd.ShowDialog() == true)  
        {  
            propertyValue.Value = ofd.FileName;  
        }  
    }  
    ```  
  
5.  <span data-ttu-id="227b0-133">由於活動和設計工具位於相同組件中，因此活動設計工具屬性的登錄是在活動本身的靜態建構函式中完成，如 SimpleCodeActivity.cs 中的下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="227b0-133">Because the activity and the designer are in the same assembly, registration of the activity designer attributes are accomplished in the static constructor of the activity itself, as shown in the following example from SimpleCodeActivity.cs.</span></span>  
  
    ```  
    static SimpleCodeActivity()  
    {  
        AttributeTableBuilder builder = new AttributeTableBuilder();  
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));  
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));  
        MetadataStore.AddAttributeTable(builder.CreateTable());  
    }  
    ```  
  
## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="227b0-134">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="227b0-134">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="227b0-135">建置方案，然後開啟 Workflow1.xaml。</span><span class="sxs-lookup"><span data-stu-id="227b0-135">Build the solution, and then open Workflow1.xaml.</span></span>  
  
2.  <span data-ttu-id="227b0-136">拖曳**SimpleCodeActivity**從 [工具箱] 拖曳至設計工具的畫布。</span><span class="sxs-lookup"><span data-stu-id="227b0-136">Drag a **SimpleCodeActivity** from the toolbox onto the designer canvas.</span></span>  
  
3.  <span data-ttu-id="227b0-137">按一下**SimpleCodeActivity** ，然後開啟屬性方格，其中會有滑桿控制項和檔案挑選控制項。</span><span class="sxs-lookup"><span data-stu-id="227b0-137">Click the **SimpleCodeActivity** and then open the property grid where there is a slider control and a file picking control.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="227b0-138">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="227b0-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="227b0-139">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="227b0-139">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="227b0-140">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="227b0-140">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="227b0-141">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="227b0-141">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`
