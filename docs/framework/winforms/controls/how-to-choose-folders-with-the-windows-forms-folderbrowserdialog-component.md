---
title: HOW TO：使用 Windows Forms FolderBrowserDialog 元件選擇資料夾
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- directories [Windows Forms], choosing
- FolderBrowserDialog component [Windows Forms], choosing directories
- folders [Windows Forms], selecting
- folders [Windows Forms], choosing
- directories [Windows Forms], selecting
ms.assetid: 4593670e-7c7d-4661-b46b-4ffb63258adb
ms.openlocfilehash: 050af6d10faec3dd09998349dcf96e96ea0f9201
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61746912"
---
# <a name="how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component"></a>HOW TO：使用 Windows Forms FolderBrowserDialog 元件選擇資料夾
通常，在您建立的 Windows 應用程式內，必須提示使用者選取資料夾時，最常是在儲存一組檔案時。 Windows Form<xref:System.Windows.Forms.FolderBrowserDialog>元件可讓您輕鬆地完成這項工作。  
  
### <a name="to-choose-folders-with-the-folderbrowserdialog-component"></a>使用 FolderBrowserDialog 元件選擇資料夾  
  
1. 在程序中，檢查<xref:System.Windows.Forms.FolderBrowserDialog>元件的<xref:System.Windows.Forms.Form.DialogResult%2A>屬性，請參閱  對話方塊中關閉的方式，並取得的值<xref:System.Windows.Forms.FolderBrowserDialog>元件的<xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A>屬性。  
  
2. 如果您要設定最上層資料夾會出現在對話方塊中的樹狀檢視時，請設定<xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A>屬性，以採用的成員<xref:System.Environment.SpecialFolder>列舉型別。  
  
3. 此外，您可以設定<xref:System.Windows.Forms.FolderBrowserDialog.Description%2A>屬性，指定文字字串出現在資料夾瀏覽器樹狀檢視頂端。  
  
     在下列範例中，<xref:System.Windows.Forms.FolderBrowserDialog>元件可用來選取資料夾，類似於當您在 Visual Studio 中建立專案並選取資料夾，將它儲存在系統提示。 在此範例中，資料夾名稱即會顯示在<xref:System.Windows.Forms.TextBox>表單上的控制項。 它是個不錯的主意，將位置放在可編輯的區域中，例如<xref:System.Windows.Forms.TextBox>控制項，以便使用者可以編輯其選取項目，如果發生錯誤或其他問題。 這個範例假設使用的表單<xref:System.Windows.Forms.FolderBrowserDialog>元件和<xref:System.Windows.Forms.TextBox>控制項。  
  
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
    >  若要使用這個類別，您的組件需要權限層級授與所<xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A>屬性，這是組件的<xref:System.Security.Permissions.FileIOPermissionAccess>列舉型別。 若在部分信任內容中執行，程序可能會因為權限不足而擲回例外狀況。 如需詳細資訊，請參閱[程式碼存取安全性基本概念](../../misc/code-access-security-basics.md)。  
  
 如需如何儲存檔案的資訊，請參閱[How to:使用 SaveFileDialog 元件儲存檔案](how-to-save-files-using-the-savefiledialog-component.md)。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.FolderBrowserDialog>
- [FolderBrowserDialog 元件概觀 (Windows Forms)](folderbrowserdialog-component-overview-windows-forms.md)
- [FolderBrowserDialog 元件](folderbrowserdialog-component-windows-forms.md)
