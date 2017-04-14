---
title: "屬性方格擴充性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3530c3a3-756d-4712-9f10-fb2897414d3a
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# 屬性方格擴充性
開發人員可以自訂在設計工具內選取指定活動時顯示的屬性方格。這樣做可以製造豐富的編輯經驗。這個範例將示範其做法。  
  
## 示範  
 工作流程設計工具屬性方格擴充性。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`  
  
## 討論  
 若要擴充屬性方格，開發人員可以選擇自訂屬性方格編輯器的內嵌外觀，或是提供對話方塊，顯示更進階的編輯介面。本範例中會示範兩種不同的編輯器：內嵌編輯器和對話方塊編輯器。  
  
## 內嵌編輯器  
 內嵌編輯器範例會示範下列操作：  
  
-   建立衍生自 <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor> 的型別。  
  
-   在建構函式中，<xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> 值是使用 [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] 資料範本設定。這個值可繫結至 XAML 範本，但是本範例會使用程式碼初始化資料繫結。  
  
-   資料範本擁有屬性方格中所呈現項目之 <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> 的資料內容。請注意，在下列程式碼 \(來自 CustomInlineEditor.cs\) 中，此內容會接著繫結至 `Value` 屬性。  
  
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
  
-   由於活動和設計工具位於相同組件中，因此活動設計工具屬性的登錄是在活動本身的靜態建構函式中完成，如 SimpleCodeActivity.cs 中的下列範例所示。  
  
    ```  
    static SimpleCodeActivity()  
    {  
        AttributeTableBuilder builder = new AttributeTableBuilder();  
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));  
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));  
        MetadataStore.AddAttributeTable(builder.CreateTable());  
    }  
  
    ```  
  
## 對話方塊編輯器  
 對話方塊編輯器範例會示範下列操作：  
  
1.  建立衍生自 <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor> 的型別。  
  
2.  使用 [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] 資料範本設定建構函式中的 <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> 值。這個值可在 XAML 中建立，但是在本範例中會使用程式碼建立。  
  
3.  資料範本擁有屬性方格中所呈現項目之 <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> 的資料內容。在下列程式碼中，此內容會接著繫結至 `Value` 屬性。此外務必包含 <xref:System.Activities.Presentation.PropertyEditing.EditModeSwitchButton>，以提供在 FilePickerEditor.cs 中引發對話方塊的按鈕。  
  
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
  
4.  覆寫設計工具型別中的 <xref:Microsoft.Windows.Design.PropertyEditing.ShowDialog%2A> 方法，以處理對話方塊的顯示。在這個範例中會顯示基本的 <xref:System.Windows.Forms.FileDialog>。  
  
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
  
5.  由於活動和設計工具位於相同組件中，因此活動設計工具屬性的登錄是在活動本身的靜態建構函式中完成，如 SimpleCodeActivity.cs 中的下列範例所示。  
  
    ```  
    static SimpleCodeActivity()  
    {  
        AttributeTableBuilder builder = new AttributeTableBuilder();  
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));  
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));  
        MetadataStore.AddAttributeTable(builder.CreateTable());  
    }  
  
    ```  
  
## 若要安裝、建立及執行範例  
  
1.  建置方案，然後開啟 Workflow1.xaml。  
  
2.  從工具箱將 \[**SimpleCodeActivity**\] 拖曳至設計工具畫布上。  
  
3.  按一下 \[**SimpleCodeActivity**\]，然後開啟屬性方格，其中會有滑桿控制項和檔案挑選控制項。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`