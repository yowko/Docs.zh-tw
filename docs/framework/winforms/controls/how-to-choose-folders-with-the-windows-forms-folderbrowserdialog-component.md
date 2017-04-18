---
title: "如何：使用 Windows Form FolderBrowserDialog 元件選擇資料夾 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "目錄 [Windows Form], 選擇"
  - "目錄 [Windows Form], 選取"
  - "FolderBrowserDialog 元件 [Windows Form], 選擇目錄"
  - "資料夾 [Windows Form], 選擇"
  - "資料夾 [Windows Form], 選取"
ms.assetid: 4593670e-7c7d-4661-b46b-4ffb63258adb
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 如何：使用 Windows Form FolderBrowserDialog 元件選擇資料夾
通常，在您建立的 Windows 應用程式中，必須要提示使用者選取資料夾，該資料夾最常用在儲存一組檔案。  Windows Form <xref:System.Windows.Forms.FolderBrowserDialog> 元件可讓您輕鬆完成這項工作。  
  
### 若要使用 FolderBrowserDialog 元件選擇資料夾  
  
1.  在程序中，檢查 <xref:System.Windows.Forms.FolderBrowserDialog> 元件的 <xref:System.Windows.Forms.Form.DialogResult%2A> 屬性，查看對話方塊如何關閉，並取得 <xref:System.Windows.Forms.FolderBrowserDialog> 元件的 <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> 屬性的值。  
  
2.  如果您需要設定將出現在對話方塊樹狀檢視中最上層的資料夾，請設定 <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> 屬性，它使用 [SpecialFolder](frlrfSystemEnvironmentSpecialFolderClassTopic) 列舉型別的成員。  
  
3.  此外，也可以設定 <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A> 屬性，指定出現在資料夾 \- 瀏覽器樹狀檢視上方的文字字串。  
  
     在以下範例中，<xref:System.Windows.Forms.FolderBrowserDialog> 元件是用以選取資料夾，類似於在 Visual Studio 中建立專案時，提示您選取儲存專案的資料夾。  在此範例中，資料夾名稱會接著顯示在表單上的 <xref:System.Windows.Forms.TextBox> 控制項中。  最好能將位置放在可編輯區域 \(如 <xref:System.Windows.Forms.TextBox> 控制項\) 內，這樣使用者在發生錯誤或其他問題時就可以編輯選擇。  這個範例假設含 <xref:System.Windows.Forms.FolderBrowserDialog> 元件和 <xref:System.Windows.Forms.TextBox> 控制項的表單。  
  
    ```vb  
    Public Sub ChooseFolder()  
        If FolderBrowserDialog1.ShowDialog() = DialogResult.OK Then  
            TextBox1.Text = FolderBrowserDialog1.SelectedPath  
        End If  
    End Sub  
  
    ```  
  
    ```csharp  
    public void ChooseFolder()  
    {  
        if (folderBrowserDialog1.ShowDialog() == DialogResult.OK)   
        {  
            textBox1.Text = folderBrowserDialog1.SelectedPath;  
        }  
    }  
  
    ```  
  
    ```cpp  
    public:  
       void ChooseFolder()  
       {  
          if (folderBrowserDialog1->ShowDialog() == DialogResult::OK)  
          {  
             textBox1->Text = folderBrowserDialog1->SelectedPath;  
          }  
       }  
    ```  
  
    > [!IMPORTANT]
    >  若要使用這個類別，您的組件需要由 [FileIOPermissionAttribute.PathDiscoveryProperty](frlrfSystemSecurityPermissionsFileIOPermissionAttributeClassPathDiscoveryTopic) 屬性授與的權限，它是 <xref:System.Security.Permissions.FileIOPermissionAccess> 列舉型別的一部分。  如果您正在部分信任的內容中執行動作，則會因權限不足而導致處理序擲回例外狀況。  如需詳細資訊，請參閱[Code Access Security Basics](../../../../docs/framework/misc/code-access-security-basics.md)。  
  
 如需如何儲存檔案的詳細資訊，請參閱 [如何：使用 SaveFileDialog 元件儲存檔案](../../../../docs/framework/winforms/controls/how-to-save-files-using-the-savefiledialog-component.md)。  
  
## 請參閱  
 <xref:System.Windows.Forms.FolderBrowserDialog>   
 [FolderBrowserDialog 元件概觀 \(Windows Form\)](../../../../docs/framework/winforms/controls/folderbrowserdialog-component-overview-windows-forms.md)   
 [FolderBrowserDialog 元件](../../../../docs/framework/winforms/controls/folderbrowserdialog-component-windows-forms.md)