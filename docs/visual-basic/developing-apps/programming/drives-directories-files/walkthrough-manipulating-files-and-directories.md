---
title: 在 Visual Basic 中管理檔案和目錄
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], reading text
- reading files [Visual Basic], text
- I/O [Visual Basic], walkthroughs
- text, writing to files
- text, reading from files
- reading text from files [Visual Basic], walkthroughs
- Visual Basic code, file access
- files [Visual Basic], writing text
- I/O [Visual Basic], writing text to files
- file access, walkthroughs
- writing to files [Visual Basic], walkthroughs
- I/O [Visual Basic], reading text from files
ms.assetid: cae77565-9f78-4e46-8e42-eb2f9f8e1ffd
ms.openlocfilehash: 4d0aac533759f8cc20ac4f19d7f0e49fef17bf56
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59314681"
---
# <a name="walkthrough-manipulating-files-and-directories-in-visual-basic"></a><span data-ttu-id="d8354-102">逐步解說：在 Visual Basic 中管理檔案和目錄</span><span class="sxs-lookup"><span data-stu-id="d8354-102">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>
<span data-ttu-id="d8354-103">本逐步解說提供 Visual Basic 中檔案 I/O 的基本概念簡介。</span><span class="sxs-lookup"><span data-stu-id="d8354-103">This walkthrough provides an introduction to the fundamentals of file I/O in Visual Basic.</span></span> <span data-ttu-id="d8354-104">其中說明如何建立一個小型應用程式，以提列並檢查目錄中的文字檔案。</span><span class="sxs-lookup"><span data-stu-id="d8354-104">It describes how to create a small application that lists and examines text files in a directory.</span></span> <span data-ttu-id="d8354-105">針對每個選取的文字檔案，應用程式會提供檔案屬性和第一行內容。</span><span class="sxs-lookup"><span data-stu-id="d8354-105">For each selected text file, the application provides file attributes and the first line of content.</span></span> <span data-ttu-id="d8354-106">您也可以選擇將資訊寫入記錄檔。</span><span class="sxs-lookup"><span data-stu-id="d8354-106">There is an option to write information to a log file.</span></span>  
  
 <span data-ttu-id="d8354-107">本逐步解說使用 Visual Basic 所提供的 `My.Computer.FileSystem Object` 成員。</span><span class="sxs-lookup"><span data-stu-id="d8354-107">This walkthrough uses members of the `My.Computer.FileSystem Object`, which are available in Visual Basic.</span></span> <span data-ttu-id="d8354-108">如需詳細資訊，請參閱 <xref:Microsoft.VisualBasic.FileIO.FileSystem>。</span><span class="sxs-lookup"><span data-stu-id="d8354-108">See <xref:Microsoft.VisualBasic.FileIO.FileSystem> for more information.</span></span> <span data-ttu-id="d8354-109">本逐步解說最後會提供使用來自 <xref:System.IO> 命名空間之類別的對等範例。</span><span class="sxs-lookup"><span data-stu-id="d8354-109">At the end of the walkthrough, an equivalent example is provided that uses classes from the <xref:System.IO> namespace.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-the-project"></a><span data-ttu-id="d8354-110">若要建立專案</span><span class="sxs-lookup"><span data-stu-id="d8354-110">To create the project</span></span>  
  
1. <span data-ttu-id="d8354-111">按一下 [檔案] 功能表上的 [新增專案]。</span><span class="sxs-lookup"><span data-stu-id="d8354-111">On the **File** menu, click **New Project**.</span></span>  
  
     <span data-ttu-id="d8354-112">[ **新增專案** ] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="d8354-112">The **New Project** dialog box appears.</span></span>  
  
2. <span data-ttu-id="d8354-113">在 [已安裝的範本] 窗格中，展開 [Visual Basic]，然後按一下 [Windows]。</span><span class="sxs-lookup"><span data-stu-id="d8354-113">In the **Installed Templates** pane, expand **Visual Basic**, and then click **Windows**.</span></span> <span data-ttu-id="d8354-114">在中間的 [範本] 窗格中，按一下 [Windows Forms 應用程式]。</span><span class="sxs-lookup"><span data-stu-id="d8354-114">In the **Templates** pane in the middle, click **Windows Forms Application**.</span></span>  
  
3. <span data-ttu-id="d8354-115">在 [名稱] 方塊中，輸入 `FileExplorer` 以設定專案名稱，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="d8354-115">In the **Name** box, type `FileExplorer` to set the project name, and then click **OK**.</span></span>  
  
     <span data-ttu-id="d8354-116">Visual Studio 即會將專案新增至 [方案總管]，並開啟 [Windows Forms 設計工具]。</span><span class="sxs-lookup"><span data-stu-id="d8354-116">Visual Studio adds the project to **Solution Explorer**, and the Windows Forms Designer opens.</span></span>  
  
4. <span data-ttu-id="d8354-117">將下表的控制項新增至表單，並設定其屬性的對應值。</span><span class="sxs-lookup"><span data-stu-id="d8354-117">Add the controls in the following table to the form, and set the corresponding values for their properties.</span></span>  
  
    |<span data-ttu-id="d8354-118">控制項</span><span class="sxs-lookup"><span data-stu-id="d8354-118">Control</span></span>|<span data-ttu-id="d8354-119">屬性</span><span class="sxs-lookup"><span data-stu-id="d8354-119">Property</span></span>|<span data-ttu-id="d8354-120">值</span><span class="sxs-lookup"><span data-stu-id="d8354-120">Value</span></span>|  
    |-------------|--------------|-----------|  
    |**<span data-ttu-id="d8354-121">ListBox</span><span class="sxs-lookup"><span data-stu-id="d8354-121">ListBox</span></span>**|**<span data-ttu-id="d8354-122">名稱</span><span class="sxs-lookup"><span data-stu-id="d8354-122">Name</span></span>**|`filesListBox`|  
    |**<span data-ttu-id="d8354-123">按鈕</span><span class="sxs-lookup"><span data-stu-id="d8354-123">Button</span></span>**|**<span data-ttu-id="d8354-124">名稱</span><span class="sxs-lookup"><span data-stu-id="d8354-124">Name</span></span>**<br /><br /> **<span data-ttu-id="d8354-125">Text</span><span class="sxs-lookup"><span data-stu-id="d8354-125">Text</span></span>**|`browseButton`<br /><br /> **<span data-ttu-id="d8354-126">瀏覽</span><span class="sxs-lookup"><span data-stu-id="d8354-126">Browse</span></span>**|  
    |**<span data-ttu-id="d8354-127">按鈕</span><span class="sxs-lookup"><span data-stu-id="d8354-127">Button</span></span>**|**<span data-ttu-id="d8354-128">名稱</span><span class="sxs-lookup"><span data-stu-id="d8354-128">Name</span></span>**<br /><br /> **<span data-ttu-id="d8354-129">Text</span><span class="sxs-lookup"><span data-stu-id="d8354-129">Text</span></span>**|`examineButton`<br /><br /> **<span data-ttu-id="d8354-130">檢查</span><span class="sxs-lookup"><span data-stu-id="d8354-130">Examine</span></span>**|  
    |**<span data-ttu-id="d8354-131">核取方塊</span><span class="sxs-lookup"><span data-stu-id="d8354-131">CheckBox</span></span>**|**<span data-ttu-id="d8354-132">名稱</span><span class="sxs-lookup"><span data-stu-id="d8354-132">Name</span></span>**<br /><br /> **<span data-ttu-id="d8354-133">Text</span><span class="sxs-lookup"><span data-stu-id="d8354-133">Text</span></span>**|`saveCheckBox`<br /><br /> **<span data-ttu-id="d8354-134">儲存結果</span><span class="sxs-lookup"><span data-stu-id="d8354-134">Save Results</span></span>**|  
    |**<span data-ttu-id="d8354-135">FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="d8354-135">FolderBrowserDialog</span></span>**|**<span data-ttu-id="d8354-136">名稱</span><span class="sxs-lookup"><span data-stu-id="d8354-136">Name</span></span>**|`FolderBrowserDialog1`|  
  
### <a name="to-select-a-folder-and-list-files-in-a-folder"></a><span data-ttu-id="d8354-137">若要選取資料夾，並列出資料夾中的檔案</span><span class="sxs-lookup"><span data-stu-id="d8354-137">To select a folder, and list files in a folder</span></span>  
  
1. <span data-ttu-id="d8354-138">按兩下表單的控制項，以建立 `browseButton` 的 `Click` 事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="d8354-138">Create a `Click` event handler for `browseButton` by double-clicking the control on the form.</span></span> <span data-ttu-id="d8354-139">[程式碼編輯器] 隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="d8354-139">The Code Editor opens.</span></span>  
  
2. <span data-ttu-id="d8354-140">將下列程式碼加入至 `Click` 事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="d8354-140">Add the following code to the `Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#103)]  
  
     <span data-ttu-id="d8354-141">`FolderBrowserDialog1.ShowDialog` 呼叫會開啟 [瀏覽資料夾] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d8354-141">The `FolderBrowserDialog1.ShowDialog` call opens the **Browse For Folder** dialog box.</span></span> <span data-ttu-id="d8354-142">使用者按一下 [確定] 之後，系統會以引數形式將 <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> 屬性傳送給 `ListFiles` 方法，以在下一個步驟中加入。</span><span class="sxs-lookup"><span data-stu-id="d8354-142">After the user clicks **OK**, the <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property is sent as an argument to the `ListFiles` method, which is added in the next step.</span></span>  
  
3. <span data-ttu-id="d8354-143">新增下列 `ListFiles` 方法。</span><span class="sxs-lookup"><span data-stu-id="d8354-143">Add the following `ListFiles` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#104)]  
  
     <span data-ttu-id="d8354-144">此程式碼會先清除 **ListBox**。</span><span class="sxs-lookup"><span data-stu-id="d8354-144">This code first clears the **ListBox**.</span></span>  
  
     <span data-ttu-id="d8354-145"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> 方法接著會擷取一組字串，目錄中每個檔案一個字串。</span><span class="sxs-lookup"><span data-stu-id="d8354-145">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A> method then retrieves a collection of strings, one for each file in the directory.</span></span> <span data-ttu-id="d8354-146">`GetFiles` 方法可接受搜尋模式引數，以擷取符合特定模式的檔案。</span><span class="sxs-lookup"><span data-stu-id="d8354-146">The `GetFiles` method accepts a search pattern argument to retrieve files that match a particular pattern.</span></span> <span data-ttu-id="d8354-147">在此範例中，僅會傳回副檔名為 .txt 的檔案。</span><span class="sxs-lookup"><span data-stu-id="d8354-147">In this example, only files that have the extension .txt are returned.</span></span>  
  
     <span data-ttu-id="d8354-148">隨即將 `GetFiles` 方法所傳回的字串新增至 **ListBox**。</span><span class="sxs-lookup"><span data-stu-id="d8354-148">The strings that are returned by the `GetFiles` method are then added to the **ListBox**.</span></span>  
  
4. <span data-ttu-id="d8354-149">執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d8354-149">Run the application.</span></span> <span data-ttu-id="d8354-150">按一下 [瀏覽] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="d8354-150">Click the **Browse** button.</span></span> <span data-ttu-id="d8354-151">在 [瀏覽資料夾] 對話方塊中，瀏覽至包含 .txt 檔案的資料夾，然後選取資料夾並按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="d8354-151">In the **Browse For Folder** dialog box, browse to a folder that contains .txt files, and then select the folder and click **OK**.</span></span>  
  
     <span data-ttu-id="d8354-152">`ListBox` 包含所選資料夾中的 .txt 檔案清單。</span><span class="sxs-lookup"><span data-stu-id="d8354-152">The `ListBox` contains a list of .txt files in the selected folder.</span></span>  
  
5. <span data-ttu-id="d8354-153">停止執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d8354-153">Stop running the application.</span></span>  
  
### <a name="to-obtain-attributes-of-a-file-and-content-from-a-text-file"></a><span data-ttu-id="d8354-154">若要取得檔案的屬性以及文字檔案的內容</span><span class="sxs-lookup"><span data-stu-id="d8354-154">To obtain attributes of a file, and content from a text file</span></span>  
  
1. <span data-ttu-id="d8354-155">按兩下表單上的控制項，以建立 `examineButton` 的 `Click` 事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="d8354-155">Create a `Click` event handler for `examineButton` by double-clicking the control on the form.</span></span>  
  
2. <span data-ttu-id="d8354-156">將下列程式碼加入至 `Click` 事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="d8354-156">Add the following code to the `Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#105)]  
  
     <span data-ttu-id="d8354-157">程式碼會驗證 `ListBox` 中已選取項目。</span><span class="sxs-lookup"><span data-stu-id="d8354-157">The code verifies that an item is selected in the `ListBox`.</span></span> <span data-ttu-id="d8354-158">接著，它會從 `ListBox` 取得檔案路徑的項目。</span><span class="sxs-lookup"><span data-stu-id="d8354-158">It then obtains the file path entry from the `ListBox`.</span></span> <span data-ttu-id="d8354-159"><xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> 方法用來檢查檔案是否仍然存在。</span><span class="sxs-lookup"><span data-stu-id="d8354-159">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.FileExists%2A> method is used to check whether the file still exists.</span></span>  
  
     <span data-ttu-id="d8354-160">系統會以引數形式將檔案路徑傳送給 `GetTextForOutput` 方法，以在下一個步驟中加入。</span><span class="sxs-lookup"><span data-stu-id="d8354-160">The file path is sent as an argument to the `GetTextForOutput` method, which is added in the next step.</span></span> <span data-ttu-id="d8354-161">這個方法會傳回字串，其中包含檔案資訊。</span><span class="sxs-lookup"><span data-stu-id="d8354-161">This method returns a string that contains file information.</span></span> <span data-ttu-id="d8354-162">**MessageBox** 中會顯示檔案資訊。</span><span class="sxs-lookup"><span data-stu-id="d8354-162">The file information appears in a **MessageBox**.</span></span>  
  
3. <span data-ttu-id="d8354-163">新增下列 `GetTextForOutput` 方法。</span><span class="sxs-lookup"><span data-stu-id="d8354-163">Add the following `GetTextForOutput` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#107)]  
  
     <span data-ttu-id="d8354-164">程式碼使用 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> 方法來取得檔案參數。</span><span class="sxs-lookup"><span data-stu-id="d8354-164">The code uses the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> method to obtain file parameters.</span></span> <span data-ttu-id="d8354-165">檔案參數會新增至 <xref:System.Text.StringBuilder>。</span><span class="sxs-lookup"><span data-stu-id="d8354-165">The file parameters are added to a <xref:System.Text.StringBuilder>.</span></span>  
  
     <span data-ttu-id="d8354-166"><xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> 方法會將檔案內容讀入 <xref:System.IO.StreamReader>。</span><span class="sxs-lookup"><span data-stu-id="d8354-166">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A> method reads the file contents into a <xref:System.IO.StreamReader>.</span></span> <span data-ttu-id="d8354-167">系統會由 `StreamReader` 取得第一行的內容，並將其新增至 `StringBuilder`。</span><span class="sxs-lookup"><span data-stu-id="d8354-167">The first line of the contents is obtained from the `StreamReader` and is added to the `StringBuilder`.</span></span>  
  
4. <span data-ttu-id="d8354-168">執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d8354-168">Run the application.</span></span> <span data-ttu-id="d8354-169">按一下 [瀏覽]，並瀏覽至包含 .txt 檔案的資料夾。</span><span class="sxs-lookup"><span data-stu-id="d8354-169">Click **Browse**, and browse to a folder that contains .txt files.</span></span> <span data-ttu-id="d8354-170">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="d8354-170">Click **OK**.</span></span>  
  
     <span data-ttu-id="d8354-171">選取 `ListBox` 中的檔案，然後按一下 [檢查]。</span><span class="sxs-lookup"><span data-stu-id="d8354-171">Select a file in the `ListBox`, and then click **Examine**.</span></span> <span data-ttu-id="d8354-172">`MessageBox` 隨即顯示檔案資訊。</span><span class="sxs-lookup"><span data-stu-id="d8354-172">A `MessageBox` shows the file information.</span></span>  
  
5. <span data-ttu-id="d8354-173">停止執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d8354-173">Stop running the application.</span></span>  
  
### <a name="to-add-a-log-entry"></a><span data-ttu-id="d8354-174">若要新增記錄項目</span><span class="sxs-lookup"><span data-stu-id="d8354-174">To add a log entry</span></span>  
  
1. <span data-ttu-id="d8354-175">將下列程式碼加入 `examineButton_Click` 事件處理常式的結尾。</span><span class="sxs-lookup"><span data-stu-id="d8354-175">Add the following code to the end of the `examineButton_Click` event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#106)]  
  
     <span data-ttu-id="d8354-176">程式碼會將記錄檔路徑設為將記錄檔放入所選檔案的相同目錄中。</span><span class="sxs-lookup"><span data-stu-id="d8354-176">The code sets the log file path to put the log file in the same directory as that of the selected file.</span></span> <span data-ttu-id="d8354-177">記錄項目的文字則會設為目前的日期和時間，後面接著檔案資訊。</span><span class="sxs-lookup"><span data-stu-id="d8354-177">The text of the log entry is set to the current date and time followed by the file information.</span></span>  
  
     <span data-ttu-id="d8354-178">將 `append` 引數設定為 `True` 的 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> 方法用來建立記錄項目。</span><span class="sxs-lookup"><span data-stu-id="d8354-178">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> method, with the `append` argument set to `True`, is used to create the log entry.</span></span>  
  
2. <span data-ttu-id="d8354-179">執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d8354-179">Run the application.</span></span> <span data-ttu-id="d8354-180">瀏覽至文字檔案，在 `ListBox` 中加以選取，並選取 [儲存結果] 核取方塊，然後按一下 [檢查]。</span><span class="sxs-lookup"><span data-stu-id="d8354-180">Browse to a text file, select it in the `ListBox`, select the **Save Results** check box, and then click **Examine**.</span></span> <span data-ttu-id="d8354-181">確認記錄項目已寫入 `log.txt` 檔案。</span><span class="sxs-lookup"><span data-stu-id="d8354-181">Verify that the log entry is written to the `log.txt` file.</span></span>  
  
3. <span data-ttu-id="d8354-182">停止執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d8354-182">Stop running the application.</span></span>  
  
### <a name="to-use-the-current-directory"></a><span data-ttu-id="d8354-183">若要使用目前的目錄</span><span class="sxs-lookup"><span data-stu-id="d8354-183">To use the current directory</span></span>  
  
1. <span data-ttu-id="d8354-184">按兩下表單的控制項，以建立 `Form1_Load` 的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="d8354-184">Create an event handler for `Form1_Load` by double-clicking the form.</span></span>  
  
2. <span data-ttu-id="d8354-185">將下列程式碼加入事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="d8354-185">Add the following code to the event handler.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#102)]  
  
     <span data-ttu-id="d8354-186">此程式碼會將資料夾瀏覽器的預設目錄設為目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="d8354-186">This code sets the default directory of the folder browser to the current directory.</span></span>  
  
3. <span data-ttu-id="d8354-187">執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d8354-187">Run the application.</span></span> <span data-ttu-id="d8354-188">當您首次按一下 [瀏覽] 時，[瀏覽資料夾] 對話方塊即會開啟至目前目錄。</span><span class="sxs-lookup"><span data-stu-id="d8354-188">When you click **Browse** the first time, the **Browse For Folder** dialog box opens to the current directory.</span></span>  
  
4. <span data-ttu-id="d8354-189">停止執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d8354-189">Stop running the application.</span></span>  
  
### <a name="to-selectively-enable-controls"></a><span data-ttu-id="d8354-190">若要選擇性地啟用控制項</span><span class="sxs-lookup"><span data-stu-id="d8354-190">To selectively enable controls</span></span>  
  
1. <span data-ttu-id="d8354-191">新增下列 `SetEnabled` 方法。</span><span class="sxs-lookup"><span data-stu-id="d8354-191">Add the following `SetEnabled` method.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#108)]  
  
     <span data-ttu-id="d8354-192">`SetEnabled` 方法會依據 `ListBox` 中是否選取項目，來啟用或停用控制項。</span><span class="sxs-lookup"><span data-stu-id="d8354-192">The `SetEnabled` method enables or disables controls depending on whether an item is selected in the `ListBox`.</span></span>  
  
2. <span data-ttu-id="d8354-193">按兩下表單的 `ListBox` 控制項，以建立 `filesListBox` 的 `SelectedIndexChanged` 事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="d8354-193">Create a `SelectedIndexChanged` event handler for `filesListBox` by double-clicking the `ListBox` control on the form.</span></span>  
  
3. <span data-ttu-id="d8354-194">在新的 `filesListBox_SelectedIndexChanged` 事件處理常式中，新增 `SetEnabled` 的呼叫。</span><span class="sxs-lookup"><span data-stu-id="d8354-194">Add a call to `SetEnabled` in the new `filesListBox_SelectedIndexChanged` event handler.</span></span>  
  
4. <span data-ttu-id="d8354-195">在 `browseButton_Click` 事件處理常式結尾，新增 `SetEnabled` 的呼叫。</span><span class="sxs-lookup"><span data-stu-id="d8354-195">Add a call to `SetEnabled` at the end of the `browseButton_Click` event handler.</span></span>  
  
5. <span data-ttu-id="d8354-196">在 `Form1_Load` 事件處理常式結尾，新增 `SetEnabled` 的呼叫。</span><span class="sxs-lookup"><span data-stu-id="d8354-196">Add a call to `SetEnabled` at the end of the `Form1_Load` event handler.</span></span>  
  
6. <span data-ttu-id="d8354-197">執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="d8354-197">Run the application.</span></span> <span data-ttu-id="d8354-198">如果 `ListBox` 中未選取項目，則會停用 [儲存結果] 核取方塊和 [檢查] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="d8354-198">The **Save Results** check box and the **Examine** button are disabled if an item is not selected in the `ListBox`.</span></span>  
  
## <a name="full-example-using-mycomputerfilesystem"></a><span data-ttu-id="d8354-199">使用 My.Computer.FileSystem 的完整範例</span><span class="sxs-lookup"><span data-stu-id="d8354-199">Full example using My.Computer.FileSystem</span></span>  
 <span data-ttu-id="d8354-200">下列是完整範例。</span><span class="sxs-lookup"><span data-stu-id="d8354-200">Following is the complete example.</span></span>  
  
 [!code-vb[VbVbcnMyFileSystem#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class2.vb#101)]  
  
## <a name="full-example-using-systemio"></a><span data-ttu-id="d8354-201">使用 System.IO 的完整範例</span><span class="sxs-lookup"><span data-stu-id="d8354-201">Full example using System.IO</span></span>  
 <span data-ttu-id="d8354-202">下列對等範例使用來自 <xref:System.IO> 命名空間的類別，而不是使用 `My.Computer.FileSystem` 物件。</span><span class="sxs-lookup"><span data-stu-id="d8354-202">The following equivalent example uses classes from the <xref:System.IO> namespace instead of using `My.Computer.FileSystem` objects.</span></span>  
  
 [!code-vb[VbVbcnMyFileSystem#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/class3.vb#111)]  
  
## <a name="see-also"></a><span data-ttu-id="d8354-203">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8354-203">See also</span></span>

- <xref:System.IO>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CurrentDirectory%2A>
- [<span data-ttu-id="d8354-204">逐步解說：使用 .NET Framework 方法管理檔案</span><span class="sxs-lookup"><span data-stu-id="d8354-204">Walkthrough: Manipulating Files by Using .NET Framework Methods</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-by-using-net-framework-methods.md)
