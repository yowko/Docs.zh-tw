---
title: HOW TO：使用 Windows Forms RichTextBox 控制項儲存檔案
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- saving files
- RTF files [Windows Forms], saving in RichTextBox control
- examples [Windows Forms], text boxes
- saving files [Windows Forms], RichTextBox control
- files [Windows Forms], saving with RichTextBox control
- RichTextBox control [Windows Forms], saving files
- .rtf files [Windows Forms], saving in RichTextBox control
- text files [Windows Forms], saving from RichTextBox control
ms.assetid: 4a58ec19-84d1-4383-9110-298c06adcfca
ms.openlocfilehash: 9a4f5a98c9fea9658d9d9a400faa773b78a12f3a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64638324"
---
# <a name="how-to-save-files-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="a1a8b-102">HOW TO：使用 Windows Forms RichTextBox 控制項儲存檔案</span><span class="sxs-lookup"><span data-stu-id="a1a8b-102">How to: Save Files with the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="a1a8b-103">Windows Form<xref:System.Windows.Forms.RichTextBox>控制項可以撰寫會在幾種格式之一中顯示的資訊：</span><span class="sxs-lookup"><span data-stu-id="a1a8b-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control can write the information it displays in one of several formats:</span></span>  
  
- <span data-ttu-id="a1a8b-104">純文字</span><span class="sxs-lookup"><span data-stu-id="a1a8b-104">Plain text</span></span>  
  
- <span data-ttu-id="a1a8b-105">Unicode 純文字</span><span class="sxs-lookup"><span data-stu-id="a1a8b-105">Unicode plain text</span></span>  
  
- <span data-ttu-id="a1a8b-106">Rich Text Format (RTF)</span><span class="sxs-lookup"><span data-stu-id="a1a8b-106">Rich-Text Format (RTF)</span></span>  
  
- <span data-ttu-id="a1a8b-107">RTF 空格 OLE 物件的位置</span><span class="sxs-lookup"><span data-stu-id="a1a8b-107">RTF with spaces in place of OLE objects</span></span>  
  
- <span data-ttu-id="a1a8b-108">OLE 物件的文字表示的純文字</span><span class="sxs-lookup"><span data-stu-id="a1a8b-108">Plain text with a textual representation of OLE objects</span></span>  
  
 <span data-ttu-id="a1a8b-109">若要儲存檔案，請呼叫<xref:System.Windows.Forms.RichTextBox.SaveFile%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="a1a8b-109">To save a file, call the <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> method.</span></span> <span data-ttu-id="a1a8b-110">您也可以使用**SaveFile**方法，將資料儲存至資料流。</span><span class="sxs-lookup"><span data-stu-id="a1a8b-110">You can also use the **SaveFile** method to save data to a stream.</span></span> <span data-ttu-id="a1a8b-111">如需詳細資訊，請參閱 <xref:System.Windows.Forms.RichTextBox.SaveFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>。</span><span class="sxs-lookup"><span data-stu-id="a1a8b-111">For more information, see <xref:System.Windows.Forms.RichTextBox.SaveFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.</span></span>  
  
### <a name="to-save-the-contents-of-the-control-to-a-file"></a><span data-ttu-id="a1a8b-112">將控制項的內容儲存至檔案</span><span class="sxs-lookup"><span data-stu-id="a1a8b-112">To save the contents of the control to a file</span></span>  
  
1. <span data-ttu-id="a1a8b-113">判斷要儲存之檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="a1a8b-113">Determine the path of the file to be saved.</span></span>  
  
     <span data-ttu-id="a1a8b-114">若要在真實世界應用程式中這樣做，您通常會使用<xref:System.Windows.Forms.SaveFileDialog>元件。</span><span class="sxs-lookup"><span data-stu-id="a1a8b-114">To do this in a real-world application, you would typically use the <xref:System.Windows.Forms.SaveFileDialog> component.</span></span> <span data-ttu-id="a1a8b-115">如需概觀，請參閱[SaveFileDialog 元件概觀](savefiledialog-component-overview-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="a1a8b-115">For an overview, see [SaveFileDialog Component Overview](savefiledialog-component-overview-windows-forms.md).</span></span>  
  
2. <span data-ttu-id="a1a8b-116">呼叫<xref:System.Windows.Forms.RichTextBox.SaveFile%2A>方法的<xref:System.Windows.Forms.RichTextBox>控制項，指定要儲存的檔案和選擇性的檔案類型。</span><span class="sxs-lookup"><span data-stu-id="a1a8b-116">Call the <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> method of the <xref:System.Windows.Forms.RichTextBox> control, specifying the file to save and optionally a file type.</span></span> <span data-ttu-id="a1a8b-117">如果您呼叫具有某檔案名稱為其唯一引數的方法，該檔案會儲存為 RTF。</span><span class="sxs-lookup"><span data-stu-id="a1a8b-117">If you call the method with a file name as its only argument, the file will be saved as RTF.</span></span> <span data-ttu-id="a1a8b-118">若要指定其他檔案類型，請呼叫以 <xref:System.Windows.Forms.RichTextBoxStreamType> 列舉值為其第二個引數的方法。</span><span class="sxs-lookup"><span data-stu-id="a1a8b-118">To specify another file type, call the method with a value of the <xref:System.Windows.Forms.RichTextBoxStreamType> enumeration as its second argument.</span></span>  
  
     <span data-ttu-id="a1a8b-119">在下列範例中，將路徑設為 rtf 文字檔案的位置**我的文件**資料夾。</span><span class="sxs-lookup"><span data-stu-id="a1a8b-119">In the example below, the path set for the location of the rich-text file is the **My Documents** folder.</span></span> <span data-ttu-id="a1a8b-120">因為您可以假設大部分執行 Windows 作業系統的電腦將會包含此資料夾，會使用此位置。</span><span class="sxs-lookup"><span data-stu-id="a1a8b-120">This location is used because you can assume that most computers running the Windows operating system will include this folder.</span></span> <span data-ttu-id="a1a8b-121">選擇此位置也可讓具有最少的系統存取層級的使用者安全地執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="a1a8b-121">Choosing this location also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="a1a8b-122">下列範例假設表單<xref:System.Windows.Forms.RichTextBox>已經加入的控制項。</span><span class="sxs-lookup"><span data-stu-id="a1a8b-122">The example below assumes a form with a <xref:System.Windows.Forms.RichTextBox> control already added.</span></span>  
  
    ```vb  
    Public Sub SaveFile()  
       ' You should replace the bold file name in the   
       ' sample below with a file name of your own choosing.  
       RichTextBox1.SaveFile(System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Testdoc.rtf", _  
          RichTextBoxStreamType.RichNoOleObjs)  
    End Sub  
    ```  
  
    ```csharp  
    public void SaveFile()  
    {  
       // You should replace the bold file name in the   
       // sample below with a file name of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       richTextBox1.SaveFile(System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Testdoc.rtf",  
          RichTextBoxStreamType.RichNoOleObjs);  
    }  
    ```  
  
    ```cpp  
    public:  
       void SaveFile()  
       {  
          // You should replace the bold file name in the   
          // sample below with a file name of your own choosing.  
          richTextBox1->SaveFile(String::Concat  
             (System::Environment::GetFolderPath  
             (System::Environment::SpecialFolder::Personal),  
             "\\Testdoc.rtf"), RichTextBoxStreamType::RichNoOleObjs);  
       }  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="a1a8b-123">如果檔案不存在，此範例就會建立新的檔案。</span><span class="sxs-lookup"><span data-stu-id="a1a8b-123">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="a1a8b-124">如果應用程式需要建立檔案，該應用程式會需要建立存取資料夾。</span><span class="sxs-lookup"><span data-stu-id="a1a8b-124">If an application needs to create a file, that application needs Create access for the folder.</span></span> <span data-ttu-id="a1a8b-125">您可以使用存取控制清單來設定權限。</span><span class="sxs-lookup"><span data-stu-id="a1a8b-125">Permissions are set using access control lists.</span></span> <span data-ttu-id="a1a8b-126">如果檔案已經存在，則應用程式必須只寫入權限的較低的權限。</span><span class="sxs-lookup"><span data-stu-id="a1a8b-126">If the file already exists, the application needs only Write access, a lesser privilege.</span></span> <span data-ttu-id="a1a8b-127">可能的話，它是在部署期間，建立檔案和只授與讀取權限，以單一檔案，而非建立資料夾的存取更安全。</span><span class="sxs-lookup"><span data-stu-id="a1a8b-127">Where possible, it is more secure to create the file during deployment, and only grant Read access to a single file, rather than Create access for a folder.</span></span> <span data-ttu-id="a1a8b-128">此外，將資料寫入使用者資料夾，而不是根資料夾或 Program Files 資料夾，也更加安全。</span><span class="sxs-lookup"><span data-stu-id="a1a8b-128">Also, it is more secure to write data to user folders than to the root folder or the Program Files folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1a8b-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1a8b-129">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox.SaveFile%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="a1a8b-130">RichTextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="a1a8b-130">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="a1a8b-131">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="a1a8b-131">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
