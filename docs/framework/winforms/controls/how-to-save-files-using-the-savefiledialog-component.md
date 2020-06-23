---
title: 如何：使用 SaveFileDialog 元件儲存檔案
description: 瞭解如何使用 SaveFileDialog 元件來流覽檔案系統，並選取要儲存的檔案。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- saving files
- SaveFileDialog component [Windows Forms], saving files
- files [Windows Forms], saving
- OpenFile method [Windows Forms], saving files with SaveFileDialog component
ms.assetid: 02e8f409-b83f-4707-babb-e71f6b223d90
ms.openlocfilehash: cd773c3d4aa2b907eb09dd87c3fdbe138bf533bb
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904399"
---
# <a name="how-to-save-files-using-the-savefiledialog-component"></a><span data-ttu-id="de690-103">如何：使用 SaveFileDialog 元件儲存檔案</span><span class="sxs-lookup"><span data-stu-id="de690-103">How to: Save Files Using the SaveFileDialog Component</span></span>

<span data-ttu-id="de690-104">此 <xref:System.Windows.Forms.SaveFileDialog> 元件可讓使用者流覽檔案系統，並選取要儲存的檔案。</span><span class="sxs-lookup"><span data-stu-id="de690-104">The <xref:System.Windows.Forms.SaveFileDialog> component allows users to browse the file system and select files to be saved.</span></span> <span data-ttu-id="de690-105">對話方塊會傳回使用者在對話方塊中所選取之檔案的路徑和名稱。</span><span class="sxs-lookup"><span data-stu-id="de690-105">The dialog box returns the path and name of the file the user has selected in the dialog box.</span></span> <span data-ttu-id="de690-106">不過，您必須撰寫程式碼，以實際將檔案寫入至磁碟。</span><span class="sxs-lookup"><span data-stu-id="de690-106">However, you must write the code to actually write the files to disk.</span></span>

### <a name="to-save-a-file-using-the-savefiledialog-component"></a><span data-ttu-id="de690-107">使用 SaveFileDialog 元件儲存檔案</span><span class="sxs-lookup"><span data-stu-id="de690-107">To save a file using the SaveFileDialog component</span></span>

- <span data-ttu-id="de690-108">顯示 [儲存檔案]\*\*\*\* 對話方塊，並呼叫方法來儲存使用者所選取的檔案。</span><span class="sxs-lookup"><span data-stu-id="de690-108">Display the **Save File** dialog box and call a method to save the file selected by the user.</span></span>

  <span data-ttu-id="de690-109">使用 <xref:System.Windows.Forms.SaveFileDialog> 元件的 <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> 方法來儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="de690-109">Use the <xref:System.Windows.Forms.SaveFileDialog> component's <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> method to save the file.</span></span> <span data-ttu-id="de690-110">這個方法會提供您 <xref:System.IO.Stream> 可以寫入的物件。</span><span class="sxs-lookup"><span data-stu-id="de690-110">This method gives you a <xref:System.IO.Stream> object you can write to.</span></span>

  <span data-ttu-id="de690-111">下列範例會使用 <xref:System.Windows.Forms.DialogResult> 屬性來取得檔案的名稱，以及用來儲存檔案的 <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="de690-111">The example below uses the <xref:System.Windows.Forms.DialogResult> property to get the name of the file, and the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method to save the file.</span></span> <span data-ttu-id="de690-112"><xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A>方法會提供您要寫入檔案的資料流程。</span><span class="sxs-lookup"><span data-stu-id="de690-112">The <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> method gives you a stream to write the file to.</span></span>

  <span data-ttu-id="de690-113">在下列範例中，有一個 <xref:System.Windows.Forms.Button> 控制項已指派映射。</span><span class="sxs-lookup"><span data-stu-id="de690-113">In the example below, there is a <xref:System.Windows.Forms.Button> control with an image assigned to it.</span></span> <span data-ttu-id="de690-114">當您按一下此按鈕時， <xref:System.Windows.Forms.SaveFileDialog> 元件會具現化，並具有允許 .gif、jpeg 和 .bmp 類型檔案的篩選準則。</span><span class="sxs-lookup"><span data-stu-id="de690-114">When you click the button, a <xref:System.Windows.Forms.SaveFileDialog> component is instantiated with a filter that allows files of type .gif, .jpeg, and .bmp.</span></span> <span data-ttu-id="de690-115">如果在 [儲存檔案] 對話方塊中選取這類型的檔案，則會儲存按鈕的影像。</span><span class="sxs-lookup"><span data-stu-id="de690-115">If a file of this type is selected in the Save File dialog box, the button's image is saved.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="de690-116">若要取得或設定 <xref:System.Windows.Forms.FileDialog.FileName%2A> 屬性，您的元件需要由類別授與的許可權層級 <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="de690-116">To get or set the <xref:System.Windows.Forms.FileDialog.FileName%2A> property, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="de690-117">若在部分信任內容中執行，程序可能會因為權限不足而擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="de690-117">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="de690-118">如需詳細資訊，請參閱 [Code Access Security Basics](../../misc/code-access-security-basics.md)。</span><span class="sxs-lookup"><span data-stu-id="de690-118">For more information, see [Code Access Security Basics](../../misc/code-access-security-basics.md).</span></span>

  <span data-ttu-id="de690-119">此範例假設您的表單具有 <xref:System.Windows.Forms.Button> 控制項 <xref:System.Windows.Forms.ButtonBase.Image%2A> ，其屬性設定為 .gif、jpeg 或 .bmp 類型的檔案。</span><span class="sxs-lookup"><span data-stu-id="de690-119">The example assumes your form has a <xref:System.Windows.Forms.Button> control with its <xref:System.Windows.Forms.ButtonBase.Image%2A> property set to a file of type .gif, .jpeg, or .bmp.</span></span>

  > [!NOTE]
  > <span data-ttu-id="de690-120"><xref:System.Windows.Forms.FileDialog>類別的 <xref:System.Windows.Forms.FileDialog.FilterIndex%2A> 屬性（由於繼承，這是類別的一部分 <xref:System.Windows.Forms.SaveFileDialog> ）會使用以一為基礎的索引。</span><span class="sxs-lookup"><span data-stu-id="de690-120">The <xref:System.Windows.Forms.FileDialog> class's <xref:System.Windows.Forms.FileDialog.FilterIndex%2A> property (which, due to inheritance, is part of the <xref:System.Windows.Forms.SaveFileDialog> class) uses a one-based index.</span></span> <span data-ttu-id="de690-121">如果您要撰寫程式碼，以特定格式來儲存資料 (例如，以純文字與二進位格式儲存檔案)，則這十分重要。</span><span class="sxs-lookup"><span data-stu-id="de690-121">This is important if you are writing code to save data in a specific format (for example, saving a file in plain text versus binary format).</span></span> <span data-ttu-id="de690-122">下列範例具有這個屬性。</span><span class="sxs-lookup"><span data-stu-id="de690-122">This property is featured in the example below.</span></span>

  ```vb
  Private Sub Button2_Click(ByVal sender As System.Object, _
  ByVal e As System.EventArgs) Handles Button2.Click
      ' Displays a SaveFileDialog so the user can save the Image
      ' assigned to Button2.
      Dim saveFileDialog1 As New SaveFileDialog()
      saveFileDialog1.Filter = "JPeg Image|*.jpg|Bitmap Image|*.bmp|Gif Image|*.gif"
      saveFileDialog1.Title = "Save an Image File"
      saveFileDialog1.ShowDialog()

      ' If the file name is not an empty string open it for saving.
      If saveFileDialog1.FileName <> "" Then
        ' Saves the Image via a FileStream created by the OpenFile method.
        Dim fs As System.IO.FileStream = Ctype _
            (saveFileDialog1.OpenFile(), System.IO.FileStream)
        ' Saves the Image in the appropriate ImageFormat based upon the
        ' file type selected in the dialog box.
        ' NOTE that the FilterIndex property is one-based.
        Select Case saveFileDialog1.FilterIndex
            Case 1
              Me.button2.Image.Save(fs, _
                  System.Drawing.Imaging.ImageFormat.Jpeg)

            Case 2
              Me.button2.Image.Save(fs, _
                  System.Drawing.Imaging.ImageFormat.Bmp)

            Case 3
              Me.button2.Image.Save(fs, _
                  System.Drawing.Imaging.ImageFormat.Gif)
          End Select

          fs.Close()
      End If
  End Sub
  ```

  ```csharp
  private void button2_Click(object sender, System.EventArgs e)
  {
      // Displays a SaveFileDialog so the user can save the Image
      // assigned to Button2.
      SaveFileDialog saveFileDialog1 = new SaveFileDialog();
      saveFileDialog1.Filter = "JPeg Image|*.jpg|Bitmap Image|*.bmp|Gif Image|*.gif";
      saveFileDialog1.Title = "Save an Image File";
      saveFileDialog1.ShowDialog();

      // If the file name is not an empty string open it for saving.
      if(saveFileDialog1.FileName != "")
      {
        // Saves the Image via a FileStream created by the OpenFile method.
        System.IO.FileStream fs =
            (System.IO.FileStream)saveFileDialog1.OpenFile();
        // Saves the Image in the appropriate ImageFormat based upon the
        // File type selected in the dialog box.
        // NOTE that the FilterIndex property is one-based.
        switch(saveFileDialog1.FilterIndex)
        {
            case 1 :
            this.button2.Image.Save(fs,
              System.Drawing.Imaging.ImageFormat.Jpeg);
            break;

            case 2 :
            this.button2.Image.Save(fs,
              System.Drawing.Imaging.ImageFormat.Bmp);
            break;

            case 3 :
            this.button2.Image.Save(fs,
              System.Drawing.Imaging.ImageFormat.Gif);
            break;
        }

      fs.Close();
      }
  }
  ```

  ```cpp
  private:
      System::Void button2_Click(System::Object ^ sender,
        System::EventArgs ^ e)
      {
        // Displays a SaveFileDialog so the user can save the Image
        // assigned to Button2.
        SaveFileDialog ^ saveFileDialog1 = new SaveFileDialog();
        saveFileDialog1->Filter =
            "JPeg Image|*.jpg|Bitmap Image|*.bmp|Gif Image|*.gif";
        saveFileDialog1->Title = "Save an Image File";
        saveFileDialog1->ShowDialog();
        // If the file name is not an empty string, open it for saving.
        if(saveFileDialog1->FileName != "")
        {
            // Saves the Image through a FileStream created by
            // the OpenFile method.
            System::IO::FileStream ^ fs =
              safe_cast\<System::IO::FileStream*>(
              saveFileDialog1->OpenFile());
            // Saves the Image in the appropriate ImageFormat based on
            // the file type selected in the dialog box.
            // Note that the FilterIndex property is one based.
            switch(saveFileDialog1->FilterIndex)
            {
              case 1 :
                  this->button2->Image->Save(fs,
                    System::Drawing::Imaging::ImageFormat::Jpeg);
                  break;
              case 2 :
                  this->button2->Image->Save(fs,
                    System::Drawing::Imaging::ImageFormat::Bmp);
                  break;
              case 3 :
                  this->button2->Image->Save(fs,
                    System::Drawing::Imaging::ImageFormat::Gif);
                  break;
            }
        fs->Close();
        }
      }
  ```

  <span data-ttu-id="de690-123">（Visual c # 和 Visual C++）將下列程式碼放在表單的函式中，以註冊事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="de690-123">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>

  ```csharp
  this.button2.Click += new System.EventHandler(this.button2_Click);
  ```

  ```cpp
  this->button2->Click += gcnew
      System::EventHandler(this, &Form1::button2_Click);
  ```

  <span data-ttu-id="de690-124">如需寫入檔案資料流程的詳細資訊，請參閱 <xref:System.IO.FileStream.BeginWrite%2A> 和 <xref:System.IO.FileStream.Write%2A> 。</span><span class="sxs-lookup"><span data-stu-id="de690-124">For more information about writing file streams, see <xref:System.IO.FileStream.BeginWrite%2A> and <xref:System.IO.FileStream.Write%2A>.</span></span>

  > [!NOTE]
  > <span data-ttu-id="de690-125">某些控制項（例如 <xref:System.Windows.Forms.RichTextBox> 控制項）具有儲存檔案的能力。</span><span class="sxs-lookup"><span data-stu-id="de690-125">Certain controls, such as the <xref:System.Windows.Forms.RichTextBox> control, have the ability to save files.</span></span>

## <a name="see-also"></a><span data-ttu-id="de690-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="de690-126">See also</span></span>

- <xref:System.Windows.Forms.SaveFileDialog>
- [<span data-ttu-id="de690-127">SaveFileDialog 元件</span><span class="sxs-lookup"><span data-stu-id="de690-127">SaveFileDialog Component</span></span>](savefiledialog-component-windows-forms.md)
