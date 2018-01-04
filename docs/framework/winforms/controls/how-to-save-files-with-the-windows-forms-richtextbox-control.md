---
title: "如何：使用 Windows Form RichTextBox 控制項儲存檔案"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7fece6685c1ac71d6ddc152e25c22010e6d579c2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-save-files-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="33b71-102">如何：使用 Windows Form RichTextBox 控制項儲存檔案</span><span class="sxs-lookup"><span data-stu-id="33b71-102">How to: Save Files with the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="33b71-103">Windows Form<xref:System.Windows.Forms.RichTextBox>控制項可以撰寫會在幾種格式之一顯示的資訊：</span><span class="sxs-lookup"><span data-stu-id="33b71-103">The Windows Forms <xref:System.Windows.Forms.RichTextBox> control can write the information it displays in one of several formats:</span></span>  
  
-   <span data-ttu-id="33b71-104">純文字</span><span class="sxs-lookup"><span data-stu-id="33b71-104">Plain text</span></span>  
  
-   <span data-ttu-id="33b71-105">Unicode 純文字</span><span class="sxs-lookup"><span data-stu-id="33b71-105">Unicode plain text</span></span>  
  
-   <span data-ttu-id="33b71-106">Rtf 格式 (RTF)</span><span class="sxs-lookup"><span data-stu-id="33b71-106">Rich-Text Format (RTF)</span></span>  
  
-   <span data-ttu-id="33b71-107">RTF 以空格取代 OLE 物件</span><span class="sxs-lookup"><span data-stu-id="33b71-107">RTF with spaces in place of OLE objects</span></span>  
  
-   <span data-ttu-id="33b71-108">OLE 物件的文字表示的純文字</span><span class="sxs-lookup"><span data-stu-id="33b71-108">Plain text with a textual representation of OLE objects</span></span>  
  
 <span data-ttu-id="33b71-109">若要儲存檔案時，呼叫<xref:System.Windows.Forms.RichTextBox.SaveFile%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="33b71-109">To save a file, call the <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> method.</span></span> <span data-ttu-id="33b71-110">您也可以使用**SaveFile**方法，將資料儲存至資料流。</span><span class="sxs-lookup"><span data-stu-id="33b71-110">You can also use the **SaveFile** method to save data to a stream.</span></span> <span data-ttu-id="33b71-111">如需詳細資訊，請參閱<xref:System.Windows.Forms.RichTextBox.SaveFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>。</span><span class="sxs-lookup"><span data-stu-id="33b71-111">For more information, see <xref:System.Windows.Forms.RichTextBox.SaveFile%28System.IO.Stream%2CSystem.Windows.Forms.RichTextBoxStreamType%29>.</span></span>  
  
### <a name="to-save-the-contents-of-the-control-to-a-file"></a><span data-ttu-id="33b71-112">若要將控制項的內容儲存至檔案</span><span class="sxs-lookup"><span data-stu-id="33b71-112">To save the contents of the control to a file</span></span>  
  
1.  <span data-ttu-id="33b71-113">判斷要儲存之檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="33b71-113">Determine the path of the file to be saved.</span></span>  
  
     <span data-ttu-id="33b71-114">若要在真實世界應用程式中這樣做，您通常會使用<xref:System.Windows.Forms.SaveFileDialog>元件。</span><span class="sxs-lookup"><span data-stu-id="33b71-114">To do this in a real-world application, you would typically use the <xref:System.Windows.Forms.SaveFileDialog> component.</span></span> <span data-ttu-id="33b71-115">如需概觀，請參閱[SaveFileDialog 元件概觀](../../../../docs/framework/winforms/controls/savefiledialog-component-overview-windows-forms.md)。</span><span class="sxs-lookup"><span data-stu-id="33b71-115">For an overview, see [SaveFileDialog Component Overview](../../../../docs/framework/winforms/controls/savefiledialog-component-overview-windows-forms.md).</span></span>  
  
2.  <span data-ttu-id="33b71-116">呼叫<xref:System.Windows.Forms.RichTextBox.SaveFile%2A>方法<xref:System.Windows.Forms.RichTextBox>控制項，指定要儲存的檔案和 （選擇性） 的檔案類型。</span><span class="sxs-lookup"><span data-stu-id="33b71-116">Call the <xref:System.Windows.Forms.RichTextBox.SaveFile%2A> method of the <xref:System.Windows.Forms.RichTextBox> control, specifying the file to save and optionally a file type.</span></span> <span data-ttu-id="33b71-117">如果您呼叫具有檔案名稱做為其唯一的引數的方法時，檔案會儲存為 RTF。</span><span class="sxs-lookup"><span data-stu-id="33b71-117">If you call the method with a file name as its only argument, the file will be saved as RTF.</span></span> <span data-ttu-id="33b71-118">若要指定其他檔案類型，請呼叫以 <xref:System.Windows.Forms.RichTextBoxStreamType> 列舉值為其第二個引數的方法。</span><span class="sxs-lookup"><span data-stu-id="33b71-118">To specify another file type, call the method with a value of the <xref:System.Windows.Forms.RichTextBoxStreamType> enumeration as its second argument.</span></span>  
  
     <span data-ttu-id="33b71-119">在下列範例中，設定路徑的 rtf 文字檔案位置是**我的文件**資料夾。</span><span class="sxs-lookup"><span data-stu-id="33b71-119">In the example below, the path set for the location of the rich-text file is the **My Documents** folder.</span></span> <span data-ttu-id="33b71-120">使用這個位置是因為您可以假設執行 Windows 作業系統的大部分電腦都會包含此資料夾。</span><span class="sxs-lookup"><span data-stu-id="33b71-120">This location is used because you can assume that most computers running the Windows operating system will include this folder.</span></span> <span data-ttu-id="33b71-121">選擇此位置也可讓使用者以最少的系統存取層級可安全地執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="33b71-121">Choosing this location also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="33b71-122">以下範例假設的表單具有<xref:System.Windows.Forms.RichTextBox>已經加入的控制項。</span><span class="sxs-lookup"><span data-stu-id="33b71-122">The example below assumes a form with a <xref:System.Windows.Forms.RichTextBox> control already added.</span></span>  
  
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
    >  <span data-ttu-id="33b71-123">如果檔案不存在，此範例就會建立新的檔案。</span><span class="sxs-lookup"><span data-stu-id="33b71-123">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="33b71-124">如果必須建立檔案的應用程式，則該應用程式需要資料夾的建立權限。</span><span class="sxs-lookup"><span data-stu-id="33b71-124">If an application needs to create a file, that application needs Create access for the folder.</span></span> <span data-ttu-id="33b71-125">您可以使用存取控制清單來設定權限。</span><span class="sxs-lookup"><span data-stu-id="33b71-125">Permissions are set using access control lists.</span></span> <span data-ttu-id="33b71-126">如果檔案已經存在，應用程式只需要寫入權，較小者的權限。</span><span class="sxs-lookup"><span data-stu-id="33b71-126">If the file already exists, the application needs only Write access, a lesser privilege.</span></span> <span data-ttu-id="33b71-127">可能的話，它是更安全，在部署期間，建立檔案並只授與讀取權限到單一檔案，而建立資料夾的存取。</span><span class="sxs-lookup"><span data-stu-id="33b71-127">Where possible, it is more secure to create the file during deployment, and only grant Read access to a single file, rather than Create access for a folder.</span></span> <span data-ttu-id="33b71-128">此外，將資料寫入使用者資料夾，而不是根資料夾或 Program Files 資料夾，也更加安全。</span><span class="sxs-lookup"><span data-stu-id="33b71-128">Also, it is more secure to write data to user folders than to the root folder or the Program Files folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33b71-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="33b71-129">See Also</span></span>  
 <xref:System.Windows.Forms.RichTextBox.SaveFile%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.RichTextBox>  
 [<span data-ttu-id="33b71-130">RichTextBox 控制項</span><span class="sxs-lookup"><span data-stu-id="33b71-130">RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [<span data-ttu-id="33b71-131">在 Windows Forms 上使用的控制項</span><span class="sxs-lookup"><span data-stu-id="33b71-131">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
