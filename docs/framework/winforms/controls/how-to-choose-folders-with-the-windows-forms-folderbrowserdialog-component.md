---
title: 使用 FolderBrowserDialog 元件選擇資料夾
description: 瞭解如何在您建立的 Windows 應用程式中使用 Windows Forms FolderBrowserDialog 元件，以提示使用者選取資料夾。
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
ms.openlocfilehash: 11d01bbaec3b82bc221960ebab5e33ca1aa302db
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903671"
---
# <a name="how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component"></a><span data-ttu-id="bdbf8-103">如何：使用 Windows Form FolderBrowserDialog 元件選擇資料夾</span><span class="sxs-lookup"><span data-stu-id="bdbf8-103">How to: Choose Folders with the Windows Forms FolderBrowserDialog Component</span></span>

<span data-ttu-id="bdbf8-104">通常，在您建立的 Windows 應用程式內，必須提示使用者選取資料夾時，最常是在儲存一組檔案時。</span><span class="sxs-lookup"><span data-stu-id="bdbf8-104">Often, within Windows applications you create, you will have to prompt users to select a folder, most frequently to save a set of files.</span></span> <span data-ttu-id="bdbf8-105">Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> 元件可讓您輕鬆完成這項工作。</span><span class="sxs-lookup"><span data-stu-id="bdbf8-105">The Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> component allows you to easily accomplish this task.</span></span>

### <a name="to-choose-folders-with-the-folderbrowserdialog-component"></a><span data-ttu-id="bdbf8-106">使用 FolderBrowserDialog 元件選擇資料夾</span><span class="sxs-lookup"><span data-stu-id="bdbf8-106">To choose folders with the FolderBrowserDialog component</span></span>

1. <span data-ttu-id="bdbf8-107">在程式中，請檢查 <xref:System.Windows.Forms.FolderBrowserDialog> 元件的 <xref:System.Windows.Forms.Form.DialogResult%2A> 屬性，以查看對話方塊的關閉方式，並取得元件屬性的值 <xref:System.Windows.Forms.FolderBrowserDialog> <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> 。</span><span class="sxs-lookup"><span data-stu-id="bdbf8-107">In a procedure, check the <xref:System.Windows.Forms.FolderBrowserDialog> component's <xref:System.Windows.Forms.Form.DialogResult%2A> property to see how the dialog box was closed and get the value of the <xref:System.Windows.Forms.FolderBrowserDialog> component's <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property.</span></span>

2. <span data-ttu-id="bdbf8-108">如果您需要設定會出現在對話方塊樹狀檢視中的最上層資料夾，請設定 <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> 屬性，這會採用列舉的成員 <xref:System.Environment.SpecialFolder> 。</span><span class="sxs-lookup"><span data-stu-id="bdbf8-108">If you need to set the top-most folder that will appear within the tree view of the dialog box, set the <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> property, which takes a member of the <xref:System.Environment.SpecialFolder> enumeration.</span></span>

3. <span data-ttu-id="bdbf8-109">此外，您可以設定 <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A> 屬性，以指定出現在資料夾瀏覽器樹狀檢視頂端的文字字串。</span><span class="sxs-lookup"><span data-stu-id="bdbf8-109">Additionally, you can set the <xref:System.Windows.Forms.FolderBrowserDialog.Description%2A> property, which specifies the text string that appears at the top of the folder-browser tree view.</span></span>

    <span data-ttu-id="bdbf8-110">在下列範例中， <xref:System.Windows.Forms.FolderBrowserDialog> 會使用元件來選取資料夾，類似于在 Visual Studio 中建立專案時，系統會提示您選取資料夾以將其儲存在其中。</span><span class="sxs-lookup"><span data-stu-id="bdbf8-110">In the example below, the <xref:System.Windows.Forms.FolderBrowserDialog> component is used to select a folder, similar to when you create a project in Visual Studio and are prompted to select a folder to save it in.</span></span> <span data-ttu-id="bdbf8-111">在此範例中，會在表單上的控制項中顯示資料夾名稱 <xref:System.Windows.Forms.TextBox> 。</span><span class="sxs-lookup"><span data-stu-id="bdbf8-111">In this example, the folder name is then displayed in a <xref:System.Windows.Forms.TextBox> control on the form.</span></span> <span data-ttu-id="bdbf8-112">最好將位置放在可編輯的區域（例如 <xref:System.Windows.Forms.TextBox> 控制項）中，讓使用者可以在發生錯誤或其他問題時編輯選取專案。</span><span class="sxs-lookup"><span data-stu-id="bdbf8-112">It is a good idea to place the location in an editable area, such as a <xref:System.Windows.Forms.TextBox> control, so that users may edit their selection in case of error or other issues.</span></span> <span data-ttu-id="bdbf8-113">這個範例假設有一個具有 <xref:System.Windows.Forms.FolderBrowserDialog> 元件和控制項的表單 <xref:System.Windows.Forms.TextBox> 。</span><span class="sxs-lookup"><span data-stu-id="bdbf8-113">This example assumes a form with a <xref:System.Windows.Forms.FolderBrowserDialog> component and a <xref:System.Windows.Forms.TextBox> control.</span></span>

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
    > <span data-ttu-id="bdbf8-114">若要使用這個類別，您的元件需要屬性所授與的許可權層級 <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> ，這是 <xref:System.Security.Permissions.FileIOPermissionAccess> 列舉的一部分。</span><span class="sxs-lookup"><span data-stu-id="bdbf8-114">To use this class, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A> property, which is part of the <xref:System.Security.Permissions.FileIOPermissionAccess> enumeration.</span></span> <span data-ttu-id="bdbf8-115">若在部分信任內容中執行，程序可能會因為權限不足而擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="bdbf8-115">If you are running in a partial-trust context, the process might throw an exception because of insufficient privileges.</span></span> <span data-ttu-id="bdbf8-116">如需詳細資訊，請參閱 [Code Access Security Basics](../../misc/code-access-security-basics.md)。</span><span class="sxs-lookup"><span data-stu-id="bdbf8-116">For more information, see [Code Access Security Basics](../../misc/code-access-security-basics.md).</span></span>

<span data-ttu-id="bdbf8-117">如需如何儲存檔案的資訊，請參閱[如何：使用 SaveFileDialog 元件儲存檔案](how-to-save-files-using-the-savefiledialog-component.md)。</span><span class="sxs-lookup"><span data-stu-id="bdbf8-117">For information on how to save files, see [How to: Save Files Using the SaveFileDialog Component](how-to-save-files-using-the-savefiledialog-component.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bdbf8-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bdbf8-118">See also</span></span>

- <xref:System.Windows.Forms.FolderBrowserDialog>
- [<span data-ttu-id="bdbf8-119">FolderBrowserDialog 元件概觀 (Windows Form)</span><span class="sxs-lookup"><span data-stu-id="bdbf8-119">FolderBrowserDialog Component Overview (Windows Forms)</span></span>](folderbrowserdialog-component-overview-windows-forms.md)
- [<span data-ttu-id="bdbf8-120">FolderBrowserDialog 元件</span><span class="sxs-lookup"><span data-stu-id="bdbf8-120">FolderBrowserDialog Component</span></span>](folderbrowserdialog-component-windows-forms.md)
