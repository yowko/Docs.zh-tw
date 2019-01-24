---
title: HOW TO：將檔案載入 Windows Forms RichTextBox 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- text boxes [Windows Forms], displaying files
- examples [Windows Forms], text boxes
- .rtf files [Windows Forms], opening in RichTextBox control
- RTF files [Windows Forms], opening in RichTextBox control
- text files [Windows Forms], displaying in RichTextBox control
- .rtf files [Windows Forms], displaying in RichTextBox control
- RichTextBox control [Windows Forms], opening files
- RTF files [Windows Forms], displaying in RichTextBox control
ms.assetid: c03451be-f285-4428-a71a-c41e002cc919
ms.openlocfilehash: 99f869cd5fd3ffc35a58d3d4e7f12161cab3a7ad
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54666042"
---
# <a name="how-to-load-files-into-the-windows-forms-richtextbox-control"></a><span data-ttu-id="eac5f-102">HOW TO：將檔案載入 Windows Forms RichTextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="eac5f-102">How to: Load Files into the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="eac5f-103">Windows Forms <xref:System.Windows.Forms.RichTextBox> 控制項可以顯示純文字、Unicode 純文字或 Rich Text 格式 (RTF) 檔案。</span><span class="sxs-lookup"><span data-stu-id="eac5f-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control can display a plain-text, Unicode plain-text, or Rich-Text-Format (RTF) file.</span></span> <span data-ttu-id="eac5f-104">執行方式是呼叫 <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="eac5f-104">To do so, call the <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> method.</span></span> <span data-ttu-id="eac5f-105">您也可以使用 <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> 方法從資料流載入資料。</span><span class="sxs-lookup"><span data-stu-id="eac5f-105">You can also use the <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> method to load data from a stream.</span></span> <span data-ttu-id="eac5f-106">如需詳細資訊，請參閱 <xref:System.Windows.Forms.RichTextBox.LoadFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>。</span><span class="sxs-lookup"><span data-stu-id="eac5f-106">For more information, see <xref:System.Windows.Forms.RichTextBox.LoadFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.</span></span>  
  
### <a name="to-load-a-file-into-the-richtextbox-control"></a><span data-ttu-id="eac5f-107">將檔案載入 RichTextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="eac5f-107">To load a file into the RichTextBox control</span></span>  
  
1.  <span data-ttu-id="eac5f-108">決定要使用 <xref:System.Windows.Forms.OpenFileDialog> 元件開啟的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="eac5f-108">Determine the path of the file to be opened using the <xref:System.Windows.Forms.OpenFileDialog> component.</span></span> <span data-ttu-id="eac5f-109">如需概觀，請參閱[OpenFileDialog 元件概觀](../../../../docs/framework/winforms/controls/openfiledialog-component-overview-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="eac5f-109">For an overview, see [OpenFileDialog Component Overview](../../../../docs/framework/winforms/controls/openfiledialog-component-overview-windows-forms.md).</span></span>  
  
2.  <span data-ttu-id="eac5f-110">呼叫 <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> 控制項的 <xref:System.Windows.Forms.RichTextBox> 方法，指定要載入的檔案，也可指定檔案類型。</span><span class="sxs-lookup"><span data-stu-id="eac5f-110">Call the <xref:System.Windows.Forms.RichTextBox.LoadFile%2A> method of the <xref:System.Windows.Forms.RichTextBox> control, specifying the file to load and optionally a file type.</span></span> <span data-ttu-id="eac5f-111">在下例中，要載入的檔案取自 <xref:System.Windows.Forms.OpenFileDialog> 元件的 <xref:System.Windows.Forms.FileDialog.FileName%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="eac5f-111">In the example below, the file to load is taken from the <xref:System.Windows.Forms.OpenFileDialog> component's <xref:System.Windows.Forms.FileDialog.FileName%2A> property.</span></span> <span data-ttu-id="eac5f-112">如果呼叫的方法以檔案名稱為其唯一引數，則檔案類型會假設為 RTF。</span><span class="sxs-lookup"><span data-stu-id="eac5f-112">If you call the method with a file name as its only argument, the file type will be assumed to be RTF.</span></span> <span data-ttu-id="eac5f-113">若要指定其他檔案類型，請呼叫以 <xref:System.Windows.Forms.RichTextBoxStreamType> 列舉值為其第二個引數的方法。</span><span class="sxs-lookup"><span data-stu-id="eac5f-113">To specify another file type, call the method with a value of the <xref:System.Windows.Forms.RichTextBoxStreamType> enumeration as its second argument.</span></span>  
  
     <span data-ttu-id="eac5f-114">在下例中，按一下按鈕即會顯示 <xref:System.Windows.Forms.OpenFileDialog> 元件。</span><span class="sxs-lookup"><span data-stu-id="eac5f-114">In the example below, the <xref:System.Windows.Forms.OpenFileDialog> component is shown when a button is clicked.</span></span> <span data-ttu-id="eac5f-115">所選檔案會隨即開啟，並顯示在 <xref:System.Windows.Forms.RichTextBox> 控制項中。</span><span class="sxs-lookup"><span data-stu-id="eac5f-115">The file selected is then opened and displayed in the <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="eac5f-116">本例假設表單有`btnOpenFile`按鈕。</span><span class="sxs-lookup"><span data-stu-id="eac5f-116">This example assumes a form has a button,`btnOpenFile`.</span></span>  
  
    ```vb  
    Private Sub btnOpenFile_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles btnOpenFile.Click  
         If OpenFileDialog1.ShowDialog() = DialogResult.OK Then  
           RichTextBox1.LoadFile(OpenFileDialog1.FileName, _  
              RichTextBoxStreamType.RichText)  
          End If  
    End Sub  
    ```  
  
    ```csharp  
    private void btnOpenFile_Click(object sender, System.EventArgs e)  
    {  
       if(openFileDialog1.ShowDialog() == DialogResult.OK)  
       {  
         richTextBox1.LoadFile(openFileDialog1.FileName, RichTextBoxStreamType.RichText);  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void btnOpenFile_Click(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          if(openFileDialog1->ShowDialog() == DialogResult::OK)  
          {  
             richTextBox1->LoadFile(openFileDialog1->FileName,  
                RichTextBoxStreamType::RichText);  
          }  
       }  
    ```  
  
     <span data-ttu-id="eac5f-117">(Visual C# [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) 下列程式碼置於表單的建構函式，以註冊事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="eac5f-117">(Visual C#, [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.btnOpenFile.Click += new System.EventHandler(this. btnOpenFile_Click);  
    ```  
  
    ```cpp  
    this->btnOpenFile->Click += gcnew   
       System::EventHandler(this, &Form1::btnOpenFile_Click);  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="eac5f-118">若要執行此程序，您的組件可能需要由 <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> 類別授與的權限層級。</span><span class="sxs-lookup"><span data-stu-id="eac5f-118">To run this process, your assembly may require a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="eac5f-119">若在部分信任內容中執行，程序可能會因為權限不足而擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="eac5f-119">If you are running in a partial-trust context, the process might throw an exception because of insufficient privileges.</span></span> <span data-ttu-id="eac5f-120">如需詳細資訊，請參閱[程式碼存取安全性基本概念](../../../../docs/framework/misc/code-access-security-basics.md)。</span><span class="sxs-lookup"><span data-stu-id="eac5f-120">For more information, see [Code Access Security Basics](../../../../docs/framework/misc/code-access-security-basics.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eac5f-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eac5f-121">See also</span></span>
- <xref:System.Windows.Forms.RichTextBox.LoadFile%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="eac5f-122">RichTextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="eac5f-122">RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)
- [<span data-ttu-id="eac5f-123">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="eac5f-123">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
