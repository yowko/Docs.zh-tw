---
title: 使用 FolderBrowserDialog 元件選擇資料夾
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
ms.openlocfilehash: 313388442101f341cfed366143f3c9669fb45cbd
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742236"
---
# <a name="how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component"></a>如何：使用 Windows Form FolderBrowserDialog 元件選擇資料夾

通常，在您建立的 Windows 應用程式內，必須提示使用者選取資料夾時，最常是在儲存一組檔案時。 Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> 元件可讓您輕鬆完成這項工作。

### <a name="to-choose-folders-with-the-folderbrowserdialog-component"></a>使用 FolderBrowserDialog 元件選擇資料夾

1. 在程式中，請檢查 <xref:System.Windows.Forms.FolderBrowserDialog> 元件的 <xref:System.Windows.Forms.Form.DialogResult%2A> 屬性，以查看對話方塊的關閉方式，並取得 <xref:System.Windows.Forms.FolderBrowserDialog> 元件 <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> 屬性的值。

2. 如果您需要設定會出現在對話方塊樹狀檢視中的最上層資料夾，請設定 <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> 屬性，它會採用 <xref:System.Environment.SpecialFolder> 列舉的成員。

3. 此外，您可以設定 <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A> 屬性，以指定出現在資料夾瀏覽器樹狀檢視頂端的文字字串。

    在下列範例中，會使用 <xref:System.Windows.Forms.FolderBrowserDialog> 元件來選取資料夾，類似于在 Visual Studio 中建立專案時，系統會提示您選取資料夾以將其儲存在其中。 在此範例中，資料夾名稱接著會顯示在表單上的 <xref:System.Windows.Forms.TextBox> 控制項中。 最好將位置放在可編輯的區域，例如 <xref:System.Windows.Forms.TextBox> 控制項，讓使用者可以在發生錯誤或其他問題時編輯選取專案。 這個範例假設有一個表單具有 <xref:System.Windows.Forms.FolderBrowserDialog> 元件和 <xref:System.Windows.Forms.TextBox> 控制項。

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
    > 若要使用這個類別，您的元件需要 <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> 屬性所授與的許可權層級，這是 <xref:System.Security.Permissions.FileIOPermissionAccess> 列舉的一部分。 若在部分信任內容中執行，程序可能會因為權限不足而擲回例外狀況。 如需詳細資訊，請參閱 [Code Access Security Basics](../../misc/code-access-security-basics.md)。

如需如何儲存檔案的資訊，請參閱[如何：使用 SaveFileDialog 元件儲存檔案](how-to-save-files-using-the-savefiledialog-component.md)。

## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.FolderBrowserDialog>
- [FolderBrowserDialog 元件概觀 (Windows Forms)](folderbrowserdialog-component-overview-windows-forms.md)
- [FolderBrowserDialog 元件](folderbrowserdialog-component-windows-forms.md)
