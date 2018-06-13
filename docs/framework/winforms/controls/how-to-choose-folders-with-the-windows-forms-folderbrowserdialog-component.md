---
title: 如何：使用 Windows Form FolderBrowserDialog 元件選擇資料夾
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
ms.openlocfilehash: 657aad6efa195ec3d9741f4f91d4e01af4a54a19
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531231"
---
# <a name="how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component"></a>如何：使用 Windows Form FolderBrowserDialog 元件選擇資料夾
通常，在您建立的 Windows 應用程式內，必須提示使用者選取資料夾時，最常是在儲存一組檔案時。 Windows Form<xref:System.Windows.Forms.FolderBrowserDialog>元件可讓您輕鬆地完成這項工作。  
  
### <a name="to-choose-folders-with-the-folderbrowserdialog-component"></a>使用 FolderBrowserDialog 元件選擇資料夾  
  
1.  在程序，請檢查<xref:System.Windows.Forms.FolderBrowserDialog>元件的<xref:System.Windows.Forms.Form.DialogResult%2A>屬性，以查看如何關閉對話方塊，並取得的值<xref:System.Windows.Forms.FolderBrowserDialog>元件的<xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A>屬性。  
  
2.  如果您需要設定最上層資料夾將會出現在對話方塊的 在樹狀檢視中，設定<xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A>屬性，其中需要的成員<xref:System.Environment.SpecialFolder>列舉型別。  
  
3.  此外，您可以設定<xref:System.Windows.Forms.FolderBrowserDialog.Description%2A>屬性，指定文字字串出現在資料夾瀏覽器樹狀結構檢視的頂端。  
  
     在下列範例中，<xref:System.Windows.Forms.FolderBrowserDialog>元件可用來選取資料夾，當您在 Visual Studio 中建立的專案，並會提示您選取要儲存在資料夾上類似。 在此範例中，資料夾名稱即會顯示在<xref:System.Windows.Forms.TextBox>表單上的控制項。 最好將位置放在可編輯的區域，例如<xref:System.Windows.Forms.TextBox>控制，以便使用者可以編輯其選取項目，如果發生錯誤或其他問題。 這個範例假設的表單具有<xref:System.Windows.Forms.FolderBrowserDialog>元件和<xref:System.Windows.Forms.TextBox>控制項。  
  
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
    >  若要使用這個類別，您的組件需要權限層級授與由<xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A>屬性，這是組件的<xref:System.Security.Permissions.FileIOPermissionAccess>列舉型別。 若在部分信任內容中執行，程序可能會因為權限不足而擲回例外狀況。 如需詳細資訊，請參閱[程式碼存取安全性基本概念](../../../../docs/framework/misc/code-access-security-basics.md)。  
  
 如需如何儲存檔案的資訊，請參閱[如何：使用 SaveFileDialog 元件儲存檔案](../../../../docs/framework/winforms/controls/how-to-save-files-using-the-savefiledialog-component.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.FolderBrowserDialog>  
 [FolderBrowserDialog 元件概觀 (Windows Forms)](../../../../docs/framework/winforms/controls/folderbrowserdialog-component-overview-windows-forms.md)  
 [FolderBrowserDialog 元件](../../../../docs/framework/winforms/controls/folderbrowserdialog-component-windows-forms.md)
