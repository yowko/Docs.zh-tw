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
ms.openlocfilehash: 2bff105d5c97a8b98d094a1ce3a4f033aa5971be
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59116073"
---
# <a name="how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component"></a><span data-ttu-id="ef2b2-102">HOW TO：使用 Windows Forms FolderBrowserDialog 元件選擇資料夾</span><span class="sxs-lookup"><span data-stu-id="ef2b2-102">How to: Choose Folders with the Windows Forms FolderBrowserDialog Component</span></span>
<span data-ttu-id="ef2b2-103">通常，在您建立的 Windows 應用程式內，必須提示使用者選取資料夾時，最常是在儲存一組檔案時。</span><span class="sxs-lookup"><span data-stu-id="ef2b2-103">Often, within Windows applications you create, you will have to prompt users to select a folder, most frequently to save a set of files.</span></span> <span data-ttu-id="ef2b2-104">Windows Form<xref:System.Windows.Forms.FolderBrowserDialog>元件可讓您輕鬆地完成這項工作。</span><span class="sxs-lookup"><span data-stu-id="ef2b2-104">The Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> component allows you to easily accomplish this task.</span></span>  
  
### <a name="to-choose-folders-with-the-folderbrowserdialog-component"></a><span data-ttu-id="ef2b2-105">使用 FolderBrowserDialog 元件選擇資料夾</span><span class="sxs-lookup"><span data-stu-id="ef2b2-105">To choose folders with the FolderBrowserDialog component</span></span>  
  
1.  <span data-ttu-id="ef2b2-106">在程序中，檢查<xref:System.Windows.Forms.FolderBrowserDialog>元件的<xref:System.Windows.Forms.Form.DialogResult%2A>屬性，請參閱  對話方塊中關閉的方式，並取得的值<xref:System.Windows.Forms.FolderBrowserDialog>元件的<xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="ef2b2-106">In a procedure, check the <xref:System.Windows.Forms.FolderBrowserDialog> component's <xref:System.Windows.Forms.Form.DialogResult%2A> property to see how the dialog box was closed and get the value of the <xref:System.Windows.Forms.FolderBrowserDialog> component's <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property.</span></span>  
  
2.  <span data-ttu-id="ef2b2-107">如果您要設定最上層資料夾會出現在對話方塊中的樹狀檢視時，請設定<xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A>屬性，以採用的成員<xref:System.Environment.SpecialFolder>列舉型別。</span><span class="sxs-lookup"><span data-stu-id="ef2b2-107">If you need to set the top-most folder that will appear within the tree view of the dialog box, set the <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> property, which takes a member of the <xref:System.Environment.SpecialFolder> enumeration.</span></span>  
  
3.  <span data-ttu-id="ef2b2-108">此外，您可以設定<xref:System.Windows.Forms.FolderBrowserDialog.Description%2A>屬性，指定文字字串出現在資料夾瀏覽器樹狀檢視頂端。</span><span class="sxs-lookup"><span data-stu-id="ef2b2-108">Additionally, you can set the <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A> property, which specifies the text string that appears at the top of the folder-browser tree view.</span></span>  
  
     <span data-ttu-id="ef2b2-109">在下列範例中，<xref:System.Windows.Forms.FolderBrowserDialog>元件可用來選取資料夾，類似於當您在 Visual Studio 中建立專案並選取資料夾，將它儲存在系統提示。</span><span class="sxs-lookup"><span data-stu-id="ef2b2-109">In the example below, the <xref:System.Windows.Forms.FolderBrowserDialog> component is used to select a folder, similar to when you create a project in Visual Studio and are prompted to select a folder to save it in.</span></span> <span data-ttu-id="ef2b2-110">在此範例中，資料夾名稱即會顯示在<xref:System.Windows.Forms.TextBox>表單上的控制項。</span><span class="sxs-lookup"><span data-stu-id="ef2b2-110">In this example, the folder name is then displayed in a <xref:System.Windows.Forms.TextBox> control on the form.</span></span> <span data-ttu-id="ef2b2-111">它是個不錯的主意，將位置放在可編輯的區域中，例如<xref:System.Windows.Forms.TextBox>控制項，以便使用者可以編輯其選取項目，如果發生錯誤或其他問題。</span><span class="sxs-lookup"><span data-stu-id="ef2b2-111">It is a good idea to place the location in an editable area, such as a <xref:System.Windows.Forms.TextBox> control, so that users may edit their selection in case of error or other issues.</span></span> <span data-ttu-id="ef2b2-112">這個範例假設使用的表單<xref:System.Windows.Forms.FolderBrowserDialog>元件和<xref:System.Windows.Forms.TextBox>控制項。</span><span class="sxs-lookup"><span data-stu-id="ef2b2-112">This example assumes a form with a <xref:System.Windows.Forms.FolderBrowserDialog> component and a <xref:System.Windows.Forms.TextBox> control.</span></span>  
  
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
    >  <span data-ttu-id="ef2b2-113">若要使用這個類別，您的組件需要權限層級授與所<xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A>屬性，這是組件的<xref:System.Security.Permissions.FileIOPermissionAccess>列舉型別。</span><span class="sxs-lookup"><span data-stu-id="ef2b2-113">To use this class, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> property, which is part of the <xref:System.Security.Permissions.FileIOPermissionAccess> enumeration.</span></span> <span data-ttu-id="ef2b2-114">若在部分信任內容中執行，程序可能會因為權限不足而擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ef2b2-114">If you are running in a partial-trust context, the process might throw an exception because of insufficient privileges.</span></span> <span data-ttu-id="ef2b2-115">如需詳細資訊，請參閱[程式碼存取安全性基本概念](../../misc/code-access-security-basics.md)。</span><span class="sxs-lookup"><span data-stu-id="ef2b2-115">For more information, see [Code Access Security Basics](../../misc/code-access-security-basics.md).</span></span>  
  
 <span data-ttu-id="ef2b2-116">如需如何儲存檔案的資訊，請參閱[How to:使用 SaveFileDialog 元件儲存檔案](how-to-save-files-using-the-savefiledialog-component.md)。</span><span class="sxs-lookup"><span data-stu-id="ef2b2-116">For information on how to save files, see [How to: Save Files Using the SaveFileDialog Component](how-to-save-files-using-the-savefiledialog-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef2b2-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef2b2-117">See also</span></span>

- <xref:System.Windows.Forms.FolderBrowserDialog>
- [<span data-ttu-id="ef2b2-118">FolderBrowserDialog 元件概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="ef2b2-118">FolderBrowserDialog Component Overview (Windows Forms)</span></span>](folderbrowserdialog-component-overview-windows-forms.md)
- [<span data-ttu-id="ef2b2-119">FolderBrowserDialog 元件</span><span class="sxs-lookup"><span data-stu-id="ef2b2-119">FolderBrowserDialog Component</span></span>](folderbrowserdialog-component-windows-forms.md)
