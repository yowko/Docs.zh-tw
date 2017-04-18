---
title: "如何：將沒有使用者介面的控制項加入至 Windows Form | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "NonVisualSelection"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "控制項 [Windows Form], 隱藏式"
  - "不可見的控制項"
  - "隱藏式控制項"
  - "Windows Form 控制項, 加入至表單"
  - "Windows Form 控制項, 隱藏式"
ms.assetid: 52134d9c-cff6-4eed-8e2b-3d5eb3bd494e
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 如何：將沒有使用者介面的控制項加入至 Windows Form
一項非視覺性的控制項 \(或元件\) 可提供功能給應用程式。  不像其他的控制項，元件並不將使用者介面提供給使用者，所以並不需要顯示在 Windows Form 設計工具表面。  當將一個元件加入表單上，Windows Form 設計工具在表單底部顯示一個可調整大小的匣，所有的元件都在這個匣上顯示。  當將一個控制項加入元件匣上，您可以選取這個元件並設定它的屬性，就像您對表單上其他控制項一樣。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表指令可能會與 \[說明\] 中描述的不同。  若要變更設定，請從 \[**工具**\] 功能表中選擇 \[**匯入和匯出設定**\]。  如需詳細資訊，請參閱 [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要將元件加入 Windows Form  
  
1.  開啟表單。  如需詳細資訊，請參閱 [How to: Display Windows Forms in the Designer](http://msdn.microsoft.com/zh-tw/bf3f1e5b-ea07-4529-85c6-6af3ded0cec5)。  
  
2.  在 \[**工具箱**\] 中，按一下元件並拖曳到表單中。  
  
     您的元件出現在元件匣上。  
  
 再者，元件可以在執行階段時加入至表單。  這是一般案例，特別是因為元件不像具有使用者介面的控制項，它並沒有視覺運算式。  在下列的範例中，會在執行階段時加入 <xref:System.Windows.Forms.Timer> 元件   \(請注意，[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 包含許多不同的計時器，在此例中，請使用 Windows Form <xref:System.Windows.Forms.Timer> 元件。  如需 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中不同計時器的詳細資訊，請參閱[Introduction to Server\-Based Timers](http://msdn.microsoft.com/zh-tw/adc0bc0a-a519-4812-bafc-fb9d1a5801fc)\)。  
  
> [!CAUTION]
>  元件通常具有控制項相關的屬性，這些屬性必須針對元件進行設定才能有效運作。  在以下的 <xref:System.Windows.Forms.Timer> 元件範例中，設定 `Interval` 屬性。  請確定，當加入元件到您的專案，您已設定元件需要的屬性。  
  
#### 若要以程式設計方式將元件加入 Windows Form 中  
  
1.  在程式碼中建立 <xref:System.Windows.Forms.Timer> 類別的執行個體。  
  
2.  設定 `Interval` 屬性，決定計時器刻度之間的時間。  
  
3.  為元件設定任何其他必要屬性。  
  
     下列程式碼示範使用 <xref:System.Windows.Forms.Timer> 物件的 `Interval` 屬性集 \(Property Set\) 來建立該物件。  
  
    ```vb  
    Public Sub CreateTimer()  
       Dim timerKeepTrack As New System.Windows.Forms.Timer  
       timerKeepTrack.Interval = 1000  
    End Sub  
  
    ```  
  
    ```csharp  
    public void createTimer()  
    {  
       System.Windows.Forms.Timer timerKeepTrack = new  
           System.Windows.Forms.Timer();  
       timerKeepTrack.Interval = 1000;  
    }  
  
    ```  
  
    ```cpp  
    public:  
       void createTimer()  
       {  
          System::Windows::Forms::Timer^ timerKeepTrack = gcnew  
             System::Windows::Forms::Timer();  
          timerKeepTrack->Interval = 1000;  
       }  
    ```  
  
    > [!IMPORTANT]
    >  參考惡意的 UserControl，可能會讓本機電腦透過網路暴露在安全性風險下。  這只會在使用者惡意建立破壞性的自訂控制項，且稍後您不小心將它加入專案的情況下，才會是要考慮的問題。  
  
## 請參閱  
 [Windows Form 控制項](../../../../docs/framework/winforms/controls/index.md)   
 [如何：將控制項加入至 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)   
 [如何：將 ActiveX 控制項加入至 Windows Form](../../../../docs/framework/winforms/controls/how-to-add-activex-controls-to-windows-forms.md)   
 [如何：在 Windows Form 之間複製控制項](../../../../docs/framework/winforms/controls/how-to-copy-controls-between-windows-forms.md)   
 [將控制項加入 Windows Form](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)   
 [標記個別 Windows Form 控制項並提供其捷徑](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)   
 [在 Windows Form 上使用的控制項](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)   
 [依功能區分 Windows Form 控制項](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)