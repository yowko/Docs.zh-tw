---
title: 使用 .NET Framework 方法管理檔案 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], walkthroughs
- text files [Visual Basic], writing to
- reading text files [Visual Basic]
- text, writing to files
- files [Visual Basic], searching
- StreamReader class, walkthroughs
- files [Visual Basic], accessing
- I/O [Visual Basic], writing text to files
- writing to files [Visual Basic], walkthroughs
- StreamWriter class, walkthroughs
- text files [Visual Basic], reading
- I/O [Visual Basic], reading text from files
ms.assetid: 7d2109eb-f98a-4389-b43d-30f384aaa7d5
ms.openlocfilehash: 89645c489cb9f21ffe415fb7c02ae09fca9a7444
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54505701"
---
# <a name="walkthrough-manipulating-files-by-using-net-framework-methods-visual-basic"></a><span data-ttu-id="eafcb-102">逐步解說：使用 .NET Framework 方法管理檔案 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eafcb-102">Walkthrough: Manipulating Files by Using .NET Framework Methods (Visual Basic)</span></span>
<span data-ttu-id="eafcb-103">本逐步解說示範如何使用 <xref:System.IO.StreamReader> 類別開啟和讀取檔案、檢查是否正在存取檔案、在 <xref:System.IO.StreamReader> 類別執行個體讀取的檔案內搜尋字串，並使用 <xref:System.IO.StreamWriter> 類別寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="eafcb-103">This walkthrough demonstrates how to open and read a file using the <xref:System.IO.StreamReader> class, check to see if a file is being accessed, search for a string within a file read with an instance of the <xref:System.IO.StreamReader> class, and write to a file using the <xref:System.IO.StreamWriter> class.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-application"></a><span data-ttu-id="eafcb-104">建立應用程式</span><span class="sxs-lookup"><span data-stu-id="eafcb-104">Creating the Application</span></span>  
 <span data-ttu-id="eafcb-105">若要啟動 Visual Studio 並開始專案，您可以建立表單，以供使用者寫入至指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="eafcb-105">Start Visual Studio and begin the project by creating a form that the user can use to write to the designated file.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="eafcb-106">若要建立專案</span><span class="sxs-lookup"><span data-stu-id="eafcb-106">To create the project</span></span>  
  
1.  <span data-ttu-id="eafcb-107">在 [檔案] 功能表上，選取 [新增專案]。</span><span class="sxs-lookup"><span data-stu-id="eafcb-107">On the **File** menu, select **New Project**.</span></span>  
  
2.  <span data-ttu-id="eafcb-108">按一下 [新增專案] 窗格的 [Windows 應用程式]。</span><span class="sxs-lookup"><span data-stu-id="eafcb-108">In the **New Project** pane, click **Windows Application**.</span></span>  
  
3.  <span data-ttu-id="eafcb-109">在 [名稱] 方塊中，輸入 `MyDiary` 並按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="eafcb-109">In the **Name** box type `MyDiary` and click **OK**.</span></span>  
  
     <span data-ttu-id="eafcb-110">Visual Studio 即會將專案新增至 [方案總管]，並開啟 [Windows Form 設計工具]。</span><span class="sxs-lookup"><span data-stu-id="eafcb-110">Visual Studio adds the project to **Solution Explorer**, and the **Windows Forms Designer** opens.</span></span>  
  
4.  <span data-ttu-id="eafcb-111">將下表的控制項新增至表單，並設定其屬性的對應值。</span><span class="sxs-lookup"><span data-stu-id="eafcb-111">Add the controls in the following table to the form and set the corresponding values for their properties.</span></span>  
  
|<span data-ttu-id="eafcb-112">**物件**</span><span class="sxs-lookup"><span data-stu-id="eafcb-112">**Object**</span></span>|<span data-ttu-id="eafcb-113">**屬性**</span><span class="sxs-lookup"><span data-stu-id="eafcb-113">**Properties**</span></span>|<span data-ttu-id="eafcb-114">**值**</span><span class="sxs-lookup"><span data-stu-id="eafcb-114">**Value**</span></span>|  
|---|---|---|   
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="eafcb-115">**名稱**</span><span class="sxs-lookup"><span data-stu-id="eafcb-115">**Name**</span></span><br /><br /> <span data-ttu-id="eafcb-116">**Text**</span><span class="sxs-lookup"><span data-stu-id="eafcb-116">**Text**</span></span>|`Submit`<br /><br /> <span data-ttu-id="eafcb-117">**提交項目**</span><span class="sxs-lookup"><span data-stu-id="eafcb-117">**Submit Entry**</span></span>|  
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="eafcb-118">**名稱**</span><span class="sxs-lookup"><span data-stu-id="eafcb-118">**Name**</span></span><br /><br /> <span data-ttu-id="eafcb-119">**Text**</span><span class="sxs-lookup"><span data-stu-id="eafcb-119">**Text**</span></span>|`Clear`<br /><br /> <span data-ttu-id="eafcb-120">**清除項目**</span><span class="sxs-lookup"><span data-stu-id="eafcb-120">**Clear Entry**</span></span>|  
|<xref:System.Windows.Forms.TextBox>|<span data-ttu-id="eafcb-121">**名稱**</span><span class="sxs-lookup"><span data-stu-id="eafcb-121">**Name**</span></span><br /><br /> <span data-ttu-id="eafcb-122">**Text**</span><span class="sxs-lookup"><span data-stu-id="eafcb-122">**Text**</span></span><br /><br /> <span data-ttu-id="eafcb-123">**多行**</span><span class="sxs-lookup"><span data-stu-id="eafcb-123">**Multiline**</span></span>|`Entry`<br /><br /> <span data-ttu-id="eafcb-124">**請輸入某些內容。**</span><span class="sxs-lookup"><span data-stu-id="eafcb-124">**Please enter something.**</span></span><br /><br /> `False`|  
  
## <a name="writing-to-the-file"></a><span data-ttu-id="eafcb-125">寫入檔案</span><span class="sxs-lookup"><span data-stu-id="eafcb-125">Writing to the File</span></span>  
 <span data-ttu-id="eafcb-126">若要新增透過應用程式寫入檔案的功能，請使用 <xref:System.IO.StreamWriter> 類別。</span><span class="sxs-lookup"><span data-stu-id="eafcb-126">To add the ability to write to a file via the application, use the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="eafcb-127"><xref:System.IO.StreamWriter> 是專為以特定的編碼方式輸出字元而量身打造，而<xref:System.IO.Stream> 類別則是針對位元組輸入和輸出而設計。</span><span class="sxs-lookup"><span data-stu-id="eafcb-127"><xref:System.IO.StreamWriter> is designed for character output in a particular encoding, whereas the <xref:System.IO.Stream> class is designed for byte input and output.</span></span> <span data-ttu-id="eafcb-128">使用 <xref:System.IO.StreamWriter> 將資訊行寫入標準文字檔案。</span><span class="sxs-lookup"><span data-stu-id="eafcb-128">Use <xref:System.IO.StreamWriter> for writing lines of information to a standard text file.</span></span> <span data-ttu-id="eafcb-129">如需 <xref:System.IO.StreamWriter> 類別的詳細資訊，請參閱 <xref:System.IO.StreamWriter>。</span><span class="sxs-lookup"><span data-stu-id="eafcb-129">For more information on the <xref:System.IO.StreamWriter> class, see <xref:System.IO.StreamWriter>.</span></span>  
  
#### <a name="to-add-writing-functionality"></a><span data-ttu-id="eafcb-130">若要新增寫入功能</span><span class="sxs-lookup"><span data-stu-id="eafcb-130">To add writing functionality</span></span>  
  
1.  <span data-ttu-id="eafcb-131">從 [檢視] 功能表上，選擇 [程式碼] 以開啟程式碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="eafcb-131">From the **View** menu, choose **Code** to open the Code Editor.</span></span>  
  
2.  <span data-ttu-id="eafcb-132">由於應用程式會參考 <xref:System.IO> 命名空間，因此請在表單類別宣告開始之前 (其會開始 `Public Class Form1`)，於程式碼開頭加入下列陳述式。</span><span class="sxs-lookup"><span data-stu-id="eafcb-132">Because the application references the <xref:System.IO> namespace, add the following statements at the very beginning of your code, before the class declaration for the form, which begins `Public Class Form1`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#35](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_1.vb)]  
  
     <span data-ttu-id="eafcb-133">在寫入檔案之前，您必須建立 <xref:System.IO.StreamWriter> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="eafcb-133">Before writing to the file, you must create an instance of a <xref:System.IO.StreamWriter> class.</span></span>  
  
3.  <span data-ttu-id="eafcb-134">從 [檢視] 功能表上，選擇 [設計工具] 以返回 Windows Forms 設計工具。</span><span class="sxs-lookup"><span data-stu-id="eafcb-134">From the **View** menu, choose **Designer** to return to the **Windows Forms Designer**.</span></span> <span data-ttu-id="eafcb-135">按兩下 `Submit` 按鈕，建立該按鈕的 <xref:System.Windows.Forms.Control.Click> 事件處理常式，然後加入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="eafcb-135">Double-click the `Submit` button to create a <xref:System.Windows.Forms.Control.Click> event handler for the button, and then add the following code.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#36](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_2.vb)]  
  
> [!NOTE]
>  <span data-ttu-id="eafcb-136">Visual Studio 整合式開發環境 (IDE) 會返回程式碼編輯器，並在事件處理常式中放入您應該新增程式碼的位置插入點。</span><span class="sxs-lookup"><span data-stu-id="eafcb-136">The Visual Studio Integrated Development Environment (IDE) will return to the Code Editor and position the insertion point within the event handler where you should add the code.</span></span>  
  
1.  <span data-ttu-id="eafcb-137">若要寫入檔案，請使用 <xref:System.IO.StreamWriter> 類別的 <xref:System.IO.StreamWriter.Write%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="eafcb-137">To write to the file, use the <xref:System.IO.StreamWriter.Write%2A> method of the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="eafcb-138">將下列程式碼新增至 `Dim fw As StreamWriter` 正後方。</span><span class="sxs-lookup"><span data-stu-id="eafcb-138">Add the following code directly after `Dim fw As StreamWriter`.</span></span> <span data-ttu-id="eafcb-139">您不用擔心系統會在找不到檔案時擲回例外狀況，因為若檔案不存在，系統會加以建立。</span><span class="sxs-lookup"><span data-stu-id="eafcb-139">You do not need to worry that an exception will be thrown if the file is not found, because it will be created if it does not already exist.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#37](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_3.vb)]  
  
2.  <span data-ttu-id="eafcb-140">您可在 `Dim ReadString As String` 正後方加入下列程式碼，確定使用者無法提交空白項目。</span><span class="sxs-lookup"><span data-stu-id="eafcb-140">Make sure that the user cannot submit a blank entry by adding the following code directly after `Dim ReadString As String`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#38](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_4.vb)]  
  
3.  <span data-ttu-id="eafcb-141">由於此為日記，因此使用者會需要針對每個項目指派日期。</span><span class="sxs-lookup"><span data-stu-id="eafcb-141">Because this is a diary, the user will want to assign a date to each entry.</span></span> <span data-ttu-id="eafcb-142">在 `fw = New StreamWriter("C:\MyDiary.txt", True)` 之後插入下列程式碼，以將 `Today` 變數設為目前的日期。</span><span class="sxs-lookup"><span data-stu-id="eafcb-142">Insert the following code after `fw = New StreamWriter("C:\MyDiary.txt", True)` to set the variable `Today` to the current date.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#39](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_5.vb)]  
  
4.  <span data-ttu-id="eafcb-143">最後，附加程式碼來清除 <xref:System.Windows.Forms.TextBox>。</span><span class="sxs-lookup"><span data-stu-id="eafcb-143">Finally, attach code to clear the <xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="eafcb-144">將下列程式碼加入 `Clear` 按鈕的 <xref:System.Windows.Forms.Control.Click> 事件。</span><span class="sxs-lookup"><span data-stu-id="eafcb-144">Add the following code to the `Clear` button's <xref:System.Windows.Forms.Control.Click> event.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#40](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_6.vb)]  
  
## <a name="adding-display-features-to-the-diary"></a><span data-ttu-id="eafcb-145">新增日記的顯示功能</span><span class="sxs-lookup"><span data-stu-id="eafcb-145">Adding Display Features to the Diary</span></span>  
 <span data-ttu-id="eafcb-146">在本節中，您會新增功能以顯示 `DisplayEntry`<xref:System.Windows.Forms.TextBox> 中的最新項目。</span><span class="sxs-lookup"><span data-stu-id="eafcb-146">In this section, you add a feature that displays the latest entry in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="eafcb-147">您也可以加入 <xref:System.Windows.Forms.ComboBox> 以顯示各種項目，使用者可以從中選取要在 `DisplayEntry`<xref:System.Windows.Forms.TextBox> 中顯示的項目。</span><span class="sxs-lookup"><span data-stu-id="eafcb-147">You can also add a <xref:System.Windows.Forms.ComboBox> that displays various entries and from which a user can select an entry to display in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="eafcb-148"><xref:System.IO.StreamReader> 類別的執行個體會讀取 `MyDiary.txt`。</span><span class="sxs-lookup"><span data-stu-id="eafcb-148">An instance of the <xref:System.IO.StreamReader> class reads from `MyDiary.txt`.</span></span> <span data-ttu-id="eafcb-149">像 <xref:System.IO.StreamWriter> 類別一樣，<xref:System.IO.StreamReader> 適用於文字檔案。</span><span class="sxs-lookup"><span data-stu-id="eafcb-149">Like the <xref:System.IO.StreamWriter> class, <xref:System.IO.StreamReader> is intended for use with text files.</span></span>  
  
 <span data-ttu-id="eafcb-150">在本節逐步解說中，請將下表的控制項新增至表單，並設定其屬性的對應值。</span><span class="sxs-lookup"><span data-stu-id="eafcb-150">For this section of the walkthrough, add the controls in the following table to the form and set the corresponding values for their properties.</span></span>  
  
|<span data-ttu-id="eafcb-151">控制項</span><span class="sxs-lookup"><span data-stu-id="eafcb-151">Control</span></span>|<span data-ttu-id="eafcb-152">屬性</span><span class="sxs-lookup"><span data-stu-id="eafcb-152">Properties</span></span>|<span data-ttu-id="eafcb-153">值</span><span class="sxs-lookup"><span data-stu-id="eafcb-153">Values</span></span>|  
|-------------|----------------|------------|  
|<xref:System.Windows.Forms.TextBox>|<span data-ttu-id="eafcb-154">**名稱**</span><span class="sxs-lookup"><span data-stu-id="eafcb-154">**Name**</span></span><br /><br /> <span data-ttu-id="eafcb-155">**可見**</span><span class="sxs-lookup"><span data-stu-id="eafcb-155">**Visible**</span></span><br /><br /> <span data-ttu-id="eafcb-156">**Size**</span><span class="sxs-lookup"><span data-stu-id="eafcb-156">**Size**</span></span><br /><br /> <span data-ttu-id="eafcb-157">**多行**</span><span class="sxs-lookup"><span data-stu-id="eafcb-157">**Multiline**</span></span>|`DisplayEntry`<br /><br /> `False`<br /><br /> `120,60`<br /><br /> `True`|  
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="eafcb-158">**名稱**</span><span class="sxs-lookup"><span data-stu-id="eafcb-158">**Name**</span></span><br /><br /> <span data-ttu-id="eafcb-159">**Text**</span><span class="sxs-lookup"><span data-stu-id="eafcb-159">**Text**</span></span>|`Display`<br /><br /> <span data-ttu-id="eafcb-160">**顯示**</span><span class="sxs-lookup"><span data-stu-id="eafcb-160">**Display**</span></span>|  
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="eafcb-161">**名稱**</span><span class="sxs-lookup"><span data-stu-id="eafcb-161">**Name**</span></span><br /><br /> <span data-ttu-id="eafcb-162">**文字**</span><span class="sxs-lookup"><span data-stu-id="eafcb-162">**Text**</span></span>|`GetEntries`<br /><br /> <span data-ttu-id="eafcb-163">**取得項目**</span><span class="sxs-lookup"><span data-stu-id="eafcb-163">**Get Entries**</span></span>|  
|<xref:System.Windows.Forms.ComboBox>|<span data-ttu-id="eafcb-164">**名稱**</span><span class="sxs-lookup"><span data-stu-id="eafcb-164">**Name**</span></span><br /><br /> <span data-ttu-id="eafcb-165">**Text**</span><span class="sxs-lookup"><span data-stu-id="eafcb-165">**Text**</span></span><br /><br /> <span data-ttu-id="eafcb-166">**已啟用**</span><span class="sxs-lookup"><span data-stu-id="eafcb-166">**Enabled**</span></span>|`PickEntries`<br /><br /> <span data-ttu-id="eafcb-167">**選取項目**</span><span class="sxs-lookup"><span data-stu-id="eafcb-167">**Select an Entry**</span></span><br /><br /> `False`|  
  
#### <a name="to-populate-the-combo-box"></a><span data-ttu-id="eafcb-168">若要填入下拉式方塊</span><span class="sxs-lookup"><span data-stu-id="eafcb-168">To populate the combo box</span></span>  
  
1.  <span data-ttu-id="eafcb-169">系統會使用 `PickEntries`<xref:System.Windows.Forms.ComboBox> 來顯示使用者提交每個項目的日期，因此使用者可以選取特定日期的項目。</span><span class="sxs-lookup"><span data-stu-id="eafcb-169">The `PickEntries`<xref:System.Windows.Forms.ComboBox> is used to display the dates on which a user submits each entry, so the user can select an entry from a specific date.</span></span> <span data-ttu-id="eafcb-170">對 `GetEntries` 按鈕建立 <xref:System.Windows.Forms.Control.Click> 事件處理常式，並加入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="eafcb-170">Create a <xref:System.Windows.Forms.Control.Click> event handler to the `GetEntries` button and add the following code.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#41](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_7.vb)]  
  
2.  <span data-ttu-id="eafcb-171">若要測試您的程式碼，請按 F5 以編譯應用程式，然後按一下 [取得項目]。</span><span class="sxs-lookup"><span data-stu-id="eafcb-171">To test your code, press F5 to compile the application, and then click **Get Entries**.</span></span> <span data-ttu-id="eafcb-172">在 <xref:System.Windows.Forms.ComboBox> 中按一下下拉式箭號以顯示項目日期。</span><span class="sxs-lookup"><span data-stu-id="eafcb-172">Click the drop-down arrow in the <xref:System.Windows.Forms.ComboBox> to display the entry dates.</span></span>  
  
#### <a name="to-choose-and-display-individual-entries"></a><span data-ttu-id="eafcb-173">若要選擇並顯示個別項目</span><span class="sxs-lookup"><span data-stu-id="eafcb-173">To choose and display individual entries</span></span>  
  
1.  <span data-ttu-id="eafcb-174">為 `Display` 按鈕建立 <xref:System.Windows.Forms.Control.Click> 事件處理常式，並加入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="eafcb-174">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `Display` button and add the following code.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#42](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_8.vb)]  
  
2.  <span data-ttu-id="eafcb-175">若要測試您的程式碼，請按 F5 以編譯應用程式，然後提交項目。</span><span class="sxs-lookup"><span data-stu-id="eafcb-175">To test your code, press F5 to compile the application, and then submit an entry.</span></span> <span data-ttu-id="eafcb-176">按一下 [取得項目]，從 <xref:System.Windows.Forms.ComboBox> 選取項目，然後按一下 [顯示]。</span><span class="sxs-lookup"><span data-stu-id="eafcb-176">Click **Get Entries**, select an entry from the <xref:System.Windows.Forms.ComboBox>, and then click **Display**.</span></span> <span data-ttu-id="eafcb-177">選取項目的內容會出現在 `DisplayEntry`<xref:System.Windows.Forms.TextBox> 中。</span><span class="sxs-lookup"><span data-stu-id="eafcb-177">The contents of the selected entry appear in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span>  
  
## <a name="enabling-users-to-delete-or-modify-entries"></a><span data-ttu-id="eafcb-178">讓使用者可以刪除或修改項目</span><span class="sxs-lookup"><span data-stu-id="eafcb-178">Enabling Users to Delete or Modify Entries</span></span>  
 <span data-ttu-id="eafcb-179">最後，您可以包含其他功能，讓使用者可以利用 `DeleteEntry` 和 `EditEntry` 按鈕，刪除或修改項目。</span><span class="sxs-lookup"><span data-stu-id="eafcb-179">Finally, you can include additional functionality enables users to delete or modify an entry by using `DeleteEntry` and `EditEntry` buttons.</span></span> <span data-ttu-id="eafcb-180">未顯示項目時，這兩個按鈕皆為停用狀態。</span><span class="sxs-lookup"><span data-stu-id="eafcb-180">Both buttons remain disabled unless an entry is displayed.</span></span>  
  
 <span data-ttu-id="eafcb-181">將下表的控制項新增至表單，並設定其屬性的對應值。</span><span class="sxs-lookup"><span data-stu-id="eafcb-181">Add the controls in the following table to the form and set the corresponding values for their properties.</span></span>  
  
|<span data-ttu-id="eafcb-182">控制項</span><span class="sxs-lookup"><span data-stu-id="eafcb-182">Control</span></span>|<span data-ttu-id="eafcb-183">屬性</span><span class="sxs-lookup"><span data-stu-id="eafcb-183">Properties</span></span>|<span data-ttu-id="eafcb-184">值</span><span class="sxs-lookup"><span data-stu-id="eafcb-184">Values</span></span>|  
|-------------|----------------|------------|  
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="eafcb-185">**名稱**</span><span class="sxs-lookup"><span data-stu-id="eafcb-185">**Name**</span></span><br /><br /> <span data-ttu-id="eafcb-186">**Text**</span><span class="sxs-lookup"><span data-stu-id="eafcb-186">**Text**</span></span><br /><br /> <span data-ttu-id="eafcb-187">**已啟用**</span><span class="sxs-lookup"><span data-stu-id="eafcb-187">**Enabled**</span></span>|`DeleteEntry`<br /><br /> <span data-ttu-id="eafcb-188">**刪除項目**</span><span class="sxs-lookup"><span data-stu-id="eafcb-188">**Delete Entry**</span></span><br /><br /> `False`|  
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="eafcb-189">**名稱**</span><span class="sxs-lookup"><span data-stu-id="eafcb-189">**Name**</span></span><br /><br /> <span data-ttu-id="eafcb-190">**Text**</span><span class="sxs-lookup"><span data-stu-id="eafcb-190">**Text**</span></span><br /><br /> <span data-ttu-id="eafcb-191">**已啟用**</span><span class="sxs-lookup"><span data-stu-id="eafcb-191">**Enabled**</span></span>|`EditEntry`<br /><br /> <span data-ttu-id="eafcb-192">**編輯項目**</span><span class="sxs-lookup"><span data-stu-id="eafcb-192">**Edit Entry**</span></span><br /><br /> `False`|  
|<xref:System.Windows.Forms.Button>|<span data-ttu-id="eafcb-193">**名稱**</span><span class="sxs-lookup"><span data-stu-id="eafcb-193">**Name**</span></span><br /><br /> <span data-ttu-id="eafcb-194">**Text**</span><span class="sxs-lookup"><span data-stu-id="eafcb-194">**Text**</span></span><br /><br /> <span data-ttu-id="eafcb-195">**已啟用**</span><span class="sxs-lookup"><span data-stu-id="eafcb-195">**Enabled**</span></span>|`SubmitEdit`<br /><br /> <span data-ttu-id="eafcb-196">**提交編輯**</span><span class="sxs-lookup"><span data-stu-id="eafcb-196">**Submit Edit**</span></span><br /><br /> `False`|  
  
#### <a name="to-enable-deletion-and-modification-of-entries"></a><span data-ttu-id="eafcb-197">若要啟用項目的刪除和修改功能</span><span class="sxs-lookup"><span data-stu-id="eafcb-197">To enable deletion and modification of entries</span></span>  
  
1.  <span data-ttu-id="eafcb-198">將下列程式碼加入 `Display` 按鈕的 <xref:System.Windows.Forms.Control.Click> 事件，放在 `DisplayEntry.Text = ReadString` 之後。</span><span class="sxs-lookup"><span data-stu-id="eafcb-198">Add the following code to the `Display` button's <xref:System.Windows.Forms.Control.Click> event, after `DisplayEntry.Text = ReadString`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#43](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_9.vb)]  
  
2.  <span data-ttu-id="eafcb-199">為 `DeleteEntry` 按鈕建立 <xref:System.Windows.Forms.Control.Click> 事件處理常式，並加入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="eafcb-199">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `DeleteEntry` button and add the following code.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#44](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_10.vb)]  
  
3.  <span data-ttu-id="eafcb-200">當使用者顯示項目時，`EditEntry` 按鈕即變成啟用。</span><span class="sxs-lookup"><span data-stu-id="eafcb-200">When a user displays an entry, the `EditEntry` button becomes enabled.</span></span> <span data-ttu-id="eafcb-201">將下列程式碼加入 `Display` 按鈕的 <xref:System.Windows.Forms.Control.Click> 事件，放在 `DisplayEntry.Text = ReadString` 之後。</span><span class="sxs-lookup"><span data-stu-id="eafcb-201">Add the following code to the <xref:System.Windows.Forms.Control.Click> event of the `Display` button after `DisplayEntry.Text = ReadString`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#45](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_11.vb)]  
  
4.  <span data-ttu-id="eafcb-202">為 `EditEntry` 按鈕建立 <xref:System.Windows.Forms.Control.Click> 事件處理常式，並加入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="eafcb-202">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `EditEntry` button and add the following code.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#46](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_12.vb)]  
  
5.  <span data-ttu-id="eafcb-203">為 `SubmitEdit` 按鈕建立 <xref:System.Windows.Forms.Control.Click> 事件處理常式，並加入下列程式碼</span><span class="sxs-lookup"><span data-stu-id="eafcb-203">Create a <xref:System.Windows.Forms.Control.Click> event handler for the `SubmitEdit` button and add the following code</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#47](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/walkthrough-manipulating-files-by-using-net-framework-methods_13.vb)]  
  
 <span data-ttu-id="eafcb-204">若要測試您的程式碼，請按 F5 以編譯應用程式。</span><span class="sxs-lookup"><span data-stu-id="eafcb-204">To test your code, press F5 to compile the application.</span></span> <span data-ttu-id="eafcb-205">按一下 [取得項目]，並選取項目，然後按一下 [顯示]。</span><span class="sxs-lookup"><span data-stu-id="eafcb-205">Click **Get Entries**, select an entry, and then click **Display**.</span></span> <span data-ttu-id="eafcb-206">此項目會出現在 `DisplayEntry`<xref:System.Windows.Forms.TextBox> 中。</span><span class="sxs-lookup"><span data-stu-id="eafcb-206">The entry appears in the `DisplayEntry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="eafcb-207">按一下 [編輯項目]。</span><span class="sxs-lookup"><span data-stu-id="eafcb-207">Click **Edit Entry**.</span></span> <span data-ttu-id="eafcb-208">此項目會出現在 `Entry`<xref:System.Windows.Forms.TextBox> 中。</span><span class="sxs-lookup"><span data-stu-id="eafcb-208">The entry appears in the `Entry`<xref:System.Windows.Forms.TextBox>.</span></span> <span data-ttu-id="eafcb-209">編輯 `Entry`<xref:System.Windows.Forms.TextBox> 中的項目，然後按一下 [提交編輯]。</span><span class="sxs-lookup"><span data-stu-id="eafcb-209">Edit the entry in the `Entry`<xref:System.Windows.Forms.TextBox> and click **Submit Edit**.</span></span> <span data-ttu-id="eafcb-210">開啟 `MyDiary.txt` 檔案，確認您的修正。</span><span class="sxs-lookup"><span data-stu-id="eafcb-210">Open the `MyDiary.txt` file to confirm your correction.</span></span> <span data-ttu-id="eafcb-211">現在，選取項目，然後按一下 [刪除項目]。</span><span class="sxs-lookup"><span data-stu-id="eafcb-211">Now select an entry and click **Delete Entry**.</span></span> <span data-ttu-id="eafcb-212">當 <xref:System.Windows.Forms.MessageBox> 要求確認時，請按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="eafcb-212">When the <xref:System.Windows.Forms.MessageBox> requests confirmation, click **OK**.</span></span> <span data-ttu-id="eafcb-213">關閉應用程式，並開啟 `MyDiary.txt` 以確認刪除。</span><span class="sxs-lookup"><span data-stu-id="eafcb-213">Close the application and open `MyDiary.txt` to confirm the deletion.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eafcb-214">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eafcb-214">See also</span></span>
- <xref:System.IO.StreamReader>
- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="eafcb-215">逐步解說</span><span class="sxs-lookup"><span data-stu-id="eafcb-215">Walkthroughs</span></span>](../../../../visual-basic/walkthroughs.md)
