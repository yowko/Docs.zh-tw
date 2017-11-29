---
title: "如何：使用 OpenFileDialog 元件開啟檔案"
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
- OpenFileDialog component [Windows Forms], opening files
- OpenFile method [Windows Forms], OpenFileDialog component
- files [Windows Forms], opening with OpenFileDialog component
ms.assetid: 9d88367a-cc21-4ffd-be74-89fd63767d35
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 52726a770e33bec4b5ec9b24f33deb44ed6379b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-open-files-using-the-openfiledialog-component"></a><span data-ttu-id="d89d5-102">如何：使用 OpenFileDialog 元件開啟檔案</span><span class="sxs-lookup"><span data-stu-id="d89d5-102">How to: Open Files Using the OpenFileDialog Component</span></span>
<span data-ttu-id="d89d5-103"><xref:System.Windows.Forms.OpenFileDialog>元件可讓使用者瀏覽其電腦或網路上的任何電腦的資料夾，然後選取一或多個要開啟的檔案。</span><span class="sxs-lookup"><span data-stu-id="d89d5-103">The <xref:System.Windows.Forms.OpenFileDialog> component allows users to browse the folders of their computer or any computer on the network and select one or more files to open.</span></span> <span data-ttu-id="d89d5-104">對話方塊會傳回使用者在對話方塊中所選取之檔案的路徑和名稱。</span><span class="sxs-lookup"><span data-stu-id="d89d5-104">The dialog box returns the path and name of the file the user selected in the dialog box.</span></span>  
  
 <span data-ttu-id="d89d5-105">使用者選取要開啟的檔案之後，開啟檔案的機制有兩種方式。</span><span class="sxs-lookup"><span data-stu-id="d89d5-105">Once the user has selected the file to be opened, there are two approaches to the mechanism of opening the file.</span></span> <span data-ttu-id="d89d5-106">如果您想要使用的檔案資料流，您可以建立的執行個體<xref:System.IO.StreamReader>類別。</span><span class="sxs-lookup"><span data-stu-id="d89d5-106">If you prefer to work with file streams, you can create an instance of the <xref:System.IO.StreamReader> class.</span></span> <span data-ttu-id="d89d5-107">或者，您可以使用<xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A>方法，以開啟選取的檔案。</span><span class="sxs-lookup"><span data-stu-id="d89d5-107">Alternately, you can use the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method to open the selected file.</span></span>  
  
 <span data-ttu-id="d89d5-108">下列第一個範例牽涉到<xref:System.Security.Permissions.FileIOPermission>權限檢查 （如 「 安全性下方的附註 」 中所述），但可讓您存取的檔名。</span><span class="sxs-lookup"><span data-stu-id="d89d5-108">The first example below involves a <xref:System.Security.Permissions.FileIOPermission> permission check (as described in the "Security Note" below), but gives you access to the filename.</span></span> <span data-ttu-id="d89d5-109">您可以從本機電腦、內部網路和網際網路區域使用這項技術。</span><span class="sxs-lookup"><span data-stu-id="d89d5-109">You can use this technique from the Local Machine, Intranet, and Internet zones.</span></span> <span data-ttu-id="d89d5-110">第二個方法也會執行<xref:System.Security.Permissions.FileIOPermission>權限檢查，但比較適合內部網路或網際網路區域中的應用程式。</span><span class="sxs-lookup"><span data-stu-id="d89d5-110">The second method also does a <xref:System.Security.Permissions.FileIOPermission> permission check, but is better suited for applications in the Intranet or Internet zones.</span></span>  
  
### <a name="to-open-a-file-as-a-stream-using-the-openfiledialog-component"></a><span data-ttu-id="d89d5-111">使用 OpenFileDialog 元件開啟檔案作為資料流</span><span class="sxs-lookup"><span data-stu-id="d89d5-111">To open a file as a stream using the OpenFileDialog component</span></span>  
  
1.  <span data-ttu-id="d89d5-112">顯示 [開啟檔案] 對話方塊，並呼叫方法來開啟使用者所選取的檔案。</span><span class="sxs-lookup"><span data-stu-id="d89d5-112">Display the **Open File** dialog box and call a method to open the file selected by the user.</span></span>  
  
     <span data-ttu-id="d89d5-113">其中一個方法是使用<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>方法來顯示開啟檔案 對話方塊中，使用的執行個體<xref:System.IO.StreamReader>類別來開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="d89d5-113">One approach is to use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the Open File dialog box, and use an instance of the <xref:System.IO.StreamReader> class to open the file.</span></span>  
  
     <span data-ttu-id="d89d5-114">使用下列範例<xref:System.Windows.Forms.Button>控制項的<xref:System.Windows.Forms.Control.Click>事件處理常式，以開啟的執行個體<xref:System.Windows.Forms.OpenFileDialog>元件。</span><span class="sxs-lookup"><span data-stu-id="d89d5-114">The example below uses the <xref:System.Windows.Forms.Button> control's <xref:System.Windows.Forms.Control.Click> event handler to open an instance of the <xref:System.Windows.Forms.OpenFileDialog> component.</span></span> <span data-ttu-id="d89d5-115">如果選擇檔案且使用者按一下 [確定]，則會開啟在對話方塊中所選取的檔案。</span><span class="sxs-lookup"><span data-stu-id="d89d5-115">When a file is chosen and the user clicks **OK**, the file selected in the dialog box opens.</span></span> <span data-ttu-id="d89d5-116">在此情況下，內容會顯示在訊息方塊中，只是為了顯示已讀取的檔案資料流。</span><span class="sxs-lookup"><span data-stu-id="d89d5-116">In this case, the contents are displayed in a message box, just to show that the file stream has been read.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="d89d5-117">取得或設定<xref:System.Windows.Forms.FileDialog.FileName%2A>屬性，您的組件需要權限層級授與由<xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType>類別。</span><span class="sxs-lookup"><span data-stu-id="d89d5-117">To get or set the <xref:System.Windows.Forms.FileDialog.FileName%2A> property, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="d89d5-118">若在部分信任內容中執行，程序可能會因為權限不足而擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d89d5-118">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="d89d5-119">如需詳細資訊，請參閱[程式碼存取安全性基本概念](../../../../docs/framework/misc/code-access-security-basics.md)。</span><span class="sxs-lookup"><span data-stu-id="d89d5-119">For more information, see [Code Access Security Basics](../../../../docs/framework/misc/code-access-security-basics.md).</span></span>  
  
     <span data-ttu-id="d89d5-120">這個範例假設您的表單具有<xref:System.Windows.Forms.Button>控制項和<xref:System.Windows.Forms.OpenFileDialog>元件。</span><span class="sxs-lookup"><span data-stu-id="d89d5-120">The example assumes your form has a <xref:System.Windows.Forms.Button> control and an <xref:System.Windows.Forms.OpenFileDialog> component.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles Button1.Click  
       If OpenFileDialog1.ShowDialog() = System.Windows.Forms.DialogResult.OK Then  
         Dim sr As New System.IO.StreamReader(OpenFileDialog1.FileName)  
         MessageBox.Show(sr.ReadToEnd)  
         sr.Close()  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       if(openFileDialog1.ShowDialog() == System.Windows.Forms.DialogResult.OK)  
       {  
          System.IO.StreamReader sr = new   
             System.IO.StreamReader(openFileDialog1.FileName);  
          MessageBox.Show(sr.ReadToEnd());  
          sr.Close();  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          if(openFileDialog1->ShowDialog() == System::Windows::Forms::DialogResult::OK)  
          {  
             System::IO::StreamReader ^ sr = gcnew  
                System::IO::StreamReader(openFileDialog1->FileName);  
             MessageBox::Show(sr->ReadToEnd());  
             sr->Close();  
          }  
       }  
    ```  
  
     <span data-ttu-id="d89d5-121">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 和 [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) 請將下列程式碼置於表單的建構函式中，以註冊事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="d89d5-121">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="d89d5-122">如需從檔案資料流讀取的詳細資訊，請參閱<xref:System.IO.FileStream.BeginRead%2A>和<xref:System.IO.FileStream.Read%2A>。</span><span class="sxs-lookup"><span data-stu-id="d89d5-122">For more information about reading from file streams, see <xref:System.IO.FileStream.BeginRead%2A> and <xref:System.IO.FileStream.Read%2A>.</span></span>  
  
### <a name="to-open-a-file-as-a-file-using-the-openfiledialog-component"></a><span data-ttu-id="d89d5-123">使用 OpenFileDialog 元件開啟檔案作為檔案</span><span class="sxs-lookup"><span data-stu-id="d89d5-123">To open a file as a file using the OpenFileDialog component</span></span>  
  
1.  <span data-ttu-id="d89d5-124">使用<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>方法，以顯示對話方塊和<xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A>方法來開啟檔案。</span><span class="sxs-lookup"><span data-stu-id="d89d5-124">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box and the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method to open the file.</span></span>  
  
     <span data-ttu-id="d89d5-125"><xref:System.Windows.Forms.OpenFileDialog>元件的<xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A>方法會傳回撰寫檔案的位元組。</span><span class="sxs-lookup"><span data-stu-id="d89d5-125">The <xref:System.Windows.Forms.OpenFileDialog> component's <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method returns the bytes that compose the file.</span></span> <span data-ttu-id="d89d5-126">這些位元組提供您可從中讀取的資料流。</span><span class="sxs-lookup"><span data-stu-id="d89d5-126">These bytes give you a stream to read from.</span></span> <span data-ttu-id="d89d5-127">在下列範例中，<xref:System.Windows.Forms.OpenFileDialog>元件具現化"cursor"篩選器，讓使用者選擇只具有副檔名的檔案且`.cur`。</span><span class="sxs-lookup"><span data-stu-id="d89d5-127">In the example below, an <xref:System.Windows.Forms.OpenFileDialog> component is instantiated with a "cursor" filter on it, allowing the user to choose only files with the file name extension`.cur`.</span></span> <span data-ttu-id="d89d5-128">如果選擇 `.cur` 檔案，則表單的資料指標會設定為所選取的資料指標。</span><span class="sxs-lookup"><span data-stu-id="d89d5-128">If a`.cur` file is chosen, the form's cursor is set to the selected cursor.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="d89d5-129">若要呼叫<xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A>方法，您的組件需要權限層級授與由<xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType>類別。</span><span class="sxs-lookup"><span data-stu-id="d89d5-129">To call the <xref:System.Windows.Forms.OpenFileDialog.OpenFile%2A> method, your assembly requires a privilege level granted by the <xref:System.Security.Permissions.FileIOPermission?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="d89d5-130">若在部分信任內容中執行，程序可能會因為權限不足而擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d89d5-130">If you are running in a partial-trust context, the process might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="d89d5-131">如需詳細資訊，請參閱[程式碼存取安全性基本概念](../../../../docs/framework/misc/code-access-security-basics.md)。</span><span class="sxs-lookup"><span data-stu-id="d89d5-131">For more information, see [Code Access Security Basics](../../../../docs/framework/misc/code-access-security-basics.md).</span></span>  
  
     <span data-ttu-id="d89d5-132">這個範例假設您的表單具有<xref:System.Windows.Forms.Button>控制項。</span><span class="sxs-lookup"><span data-stu-id="d89d5-132">The example assumes your form has a <xref:System.Windows.Forms.Button> control.</span></span>  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles Button1.Click  
       ' Displays an OpenFileDialog so the user can select a Cursor.  
       Dim openFileDialog1 As New OpenFileDialog()  
       openFileDialog1.Filter = "Cursor Files|*.cur"  
       openFileDialog1.Title = "Select a Cursor File"  
  
       ' Show the Dialog.  
       ' If the user clicked OK in the dialog and   
       ' a .CUR file was selected, open it.  
       If openFileDialog1.ShowDialog() = System.Windows.Forms.DialogResult.OK Then  
         ' Assign the cursor in the Stream to the Form's Cursor property.  
         Me.Cursor = New Cursor(openFileDialog1.OpenFile())  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       // Displays an OpenFileDialog so the user can select a Cursor.  
       OpenFileDialog openFileDialog1 = new OpenFileDialog();  
       openFileDialog1.Filter = "Cursor Files|*.cur";  
       openFileDialog1.Title = "Select a Cursor File";  
  
       // Show the Dialog.  
       // If the user clicked OK in the dialog and  
       // a .CUR file was selected, open it.  
        if (openFileDialog1.ShowDialog() == System.Windows.Forms.DialogResult.OK)  
       {  
          // Assign the cursor in the Stream to the Form's Cursor property.  
          this.Cursor = new Cursor(openFileDialog1.OpenFile());  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          // Displays an OpenFileDialog so the user can select a Cursor.  
          OpenFileDialog ^ openFileDialog1 = new OpenFileDialog();  
          openFileDialog1->Filter = "Cursor Files|*.cur";  
          openFileDialog1->Title = "Select a Cursor File";  
  
          // Show the Dialog.  
          // If the user clicked OK in the dialog and  
          // a .CUR file was selected, open it.  
          if (openFileDialog1->ShowDialog() == System::Windows::Forms::DialogResult::OK)  
          {  
             // Assign the cursor in the Stream to  
             // the Form's Cursor property.  
             this->Cursor = gcnew  
                System::Windows::Forms::Cursor(  
                openFileDialog1->OpenFile());  
          }  
       }  
    ```  
  
     <span data-ttu-id="d89d5-133">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 和 [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) 請將下列程式碼置於表單的建構函式中，以註冊事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="d89d5-133">([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d89d5-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d89d5-134">See Also</span></span>  
 <xref:System.Windows.Forms.OpenFileDialog>  
 [<span data-ttu-id="d89d5-135">OpenFileDialog 元件</span><span class="sxs-lookup"><span data-stu-id="d89d5-135">OpenFileDialog Component</span></span>](../../../../docs/framework/winforms/controls/openfiledialog-component-windows-forms.md)
