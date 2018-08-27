---
title: 如何：使用 Visual C# 功能存取 Office Interop 物件 (C# 程式設計指南)
ms.date: 07/20/2015
helpviewer_keywords:
- optional parameters [C#], Office programming
- named and optional arguments [C#], Office programming
- dynamic [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
- Office programming [C#]
ms.assetid: 041b25c2-3512-4e0f-a4ea-ceb2999e4d5e
ms.openlocfilehash: 4e2599f34e80f70a36d6f497f908887aa6853121
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2018
ms.locfileid: "42932104"
---
# <a name="how-to-access-office-interop-objects-by-using-visual-c-features-c-programming-guide"></a><span data-ttu-id="0cd48-102">如何：使用 Visual C# 功能存取 Office Interop 物件 (C# 程式設計指南)</span><span class="sxs-lookup"><span data-stu-id="0cd48-102">How to: Access Office Interop Objects by Using Visual C# Features (C# Programming Guide)</span></span>
<span data-ttu-id="0cd48-103">Visual C# 的功能可以簡化 Office API 物件存取。</span><span class="sxs-lookup"><span data-stu-id="0cd48-103">Visual C# has features that simplify access to Office API objects.</span></span> <span data-ttu-id="0cd48-104">新功能包括具名引數和選擇性引數、稱為 `dynamic` 的新類型，以及傳遞引數以像是實值參數的形式，參考 COM 方法中參數的能力。</span><span class="sxs-lookup"><span data-stu-id="0cd48-104">The new features include named and optional arguments, a new type called `dynamic`, and the ability to pass arguments to reference parameters in COM methods as if they were value parameters.</span></span>  
  
 <span data-ttu-id="0cd48-105">在本主題中，您將使用新的功能撰寫可建立及顯示 Microsoft Office Excel 工作表的程式碼。</span><span class="sxs-lookup"><span data-stu-id="0cd48-105">In this topic you will use the new features to write code that creates and displays a Microsoft Office Excel worksheet.</span></span> <span data-ttu-id="0cd48-106">接著，您將要撰寫可加入 Office Word 文件的程式碼，而該文件包含連結至 Excel 工作表的圖示。</span><span class="sxs-lookup"><span data-stu-id="0cd48-106">You will then write code to add an Office Word document that contains an icon that is linked to the Excel worksheet.</span></span>  
  
 <span data-ttu-id="0cd48-107">若要完成這個逐步解說，電腦上必須安裝 Microsoft Office Excel 2007 和 Microsoft Office Word 2007 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="0cd48-107">To complete this walkthrough, you must have Microsoft Office Excel 2007 and Microsoft Office Word 2007, or later versions, installed on your computer.</span></span>  
  
 <span data-ttu-id="0cd48-108">如果您使用 [!INCLUDE[windowsver](~/includes/windowsver-md.md)] 以前的作業系統，請確定已安裝 [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0cd48-108">If you are using an operating system that is older than [!INCLUDE[windowsver](~/includes/windowsver-md.md)], make sure that [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] is installed.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-new-console-application"></a><span data-ttu-id="0cd48-109">建立新的主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="0cd48-109">To create a new console application</span></span>  
  
1.  <span data-ttu-id="0cd48-110">啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="0cd48-110">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="0cd48-111">在 [檔案]  功能表中，指向 [新增] ，然後按一下 [專案] 。</span><span class="sxs-lookup"><span data-stu-id="0cd48-111">On the **File** menu, point to **New**, and then click **Project**.</span></span> <span data-ttu-id="0cd48-112">[ **新增專案** ] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="0cd48-112">The **New Project** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="0cd48-113">在 [已安裝的範本] 窗格中，展開 [Visual C#]，然後按一下 [Windows]。</span><span class="sxs-lookup"><span data-stu-id="0cd48-113">In the **Installed Templates** pane, expand **Visual C#**, and then click **Windows**.</span></span>  
  
4.  <span data-ttu-id="0cd48-114">查看 [新增專案] 對話方塊頂端，確定已選取 [.NET Framework 4] (或更新版本) 作為目標架構。</span><span class="sxs-lookup"><span data-stu-id="0cd48-114">Look at the top of the **New Project** dialog box to make sure that **.NET Framework 4** (or later version) is selected as a target framework.</span></span>  
  
5.  <span data-ttu-id="0cd48-115">按一下 [範本] 窗格中的 [主控台應用程式]。</span><span class="sxs-lookup"><span data-stu-id="0cd48-115">In the **Templates** pane, click **Console Application**.</span></span>  
  
6.  <span data-ttu-id="0cd48-116">在 [名稱] 欄位中鍵入專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="0cd48-116">Type a name for your project in the **Name** field.</span></span>  
  
7.  <span data-ttu-id="0cd48-117">按一下 [確定 **Deploying Office Solutions**]。</span><span class="sxs-lookup"><span data-stu-id="0cd48-117">Click **OK**.</span></span>  
  
     <span data-ttu-id="0cd48-118">新的專案隨即會出現在方案總管中。</span><span class="sxs-lookup"><span data-stu-id="0cd48-118">The new project appears in **Solution Explorer**.</span></span>  
  
### <a name="to-add-references"></a><span data-ttu-id="0cd48-119">加入參考</span><span class="sxs-lookup"><span data-stu-id="0cd48-119">To add references</span></span>  
  
1.  <span data-ttu-id="0cd48-120">在方案總管中，於專案名稱上按一下滑鼠右鍵，然後按一下 [新增參考]。</span><span class="sxs-lookup"><span data-stu-id="0cd48-120">In **Solution Explorer**, right-click your project's name and then click **Add Reference**.</span></span> <span data-ttu-id="0cd48-121">[加入參考] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="0cd48-121">The **Add Reference** dialog box appears.</span></span>  
  
2.  <span data-ttu-id="0cd48-122">在 [組件] 頁面的 [元件名稱] 清單中，選取 [Microsoft.Office.Interop.Word]，然後按住 CTRL 鍵並選取 [Microsoft.Office.Interop.Excel]。</span><span class="sxs-lookup"><span data-stu-id="0cd48-122">On the **Assemblies**  page, select **Microsoft.Office.Interop.Word** in the **Component Name** list, and then hold down the CTRL key and select **Microsoft.Office.Interop.Excel**.</span></span>  <span data-ttu-id="0cd48-123">如果看不到組件，則可能需要確定它們已安裝並已顯示 (請參閱[如何：安裝 Office 主要 Interop 組件](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies))。</span><span class="sxs-lookup"><span data-stu-id="0cd48-123">If you do not see the assemblies, you may need to ensure they are installed and displayed (see [How to: Install Office Primary Interop Assemblies](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies))</span></span>  
  
3.  <span data-ttu-id="0cd48-124">按一下 [確定 **Deploying Office Solutions**]。</span><span class="sxs-lookup"><span data-stu-id="0cd48-124">Click **OK**.</span></span>  
  
### <a name="to-add-necessary-using-directives"></a><span data-ttu-id="0cd48-125">加入必要的 using 指示詞</span><span class="sxs-lookup"><span data-stu-id="0cd48-125">To add necessary using directives</span></span>  
  
1.  <span data-ttu-id="0cd48-126">在方案總管中，以滑鼠右鍵按一下 **Program.cs** 檔案，然後按一下 [檢視程式碼]。</span><span class="sxs-lookup"><span data-stu-id="0cd48-126">In **Solution Explorer**, right-click the **Program.cs** file and then click **View Code**.</span></span>  
  
2.  <span data-ttu-id="0cd48-127">將下列 `using` 指示詞加入程式碼檔案頂端。</span><span class="sxs-lookup"><span data-stu-id="0cd48-127">Add the following `using` directives to the top of the code file.</span></span>  
  
     [!code-csharp[csProgGuideOfficeHowTo#1](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_1.cs)]  
  
### <a name="to-create-a-list-of-bank-accounts"></a><span data-ttu-id="0cd48-128">建立銀行帳戶清單</span><span class="sxs-lookup"><span data-stu-id="0cd48-128">To create a list of bank accounts</span></span>  
  
1.  <span data-ttu-id="0cd48-129">將下列類別定義貼入 `Program` 類別下的 **Program.cs**。</span><span class="sxs-lookup"><span data-stu-id="0cd48-129">Paste the following class definition into **Program.cs**, under the `Program` class.</span></span>  
  
     [!code-csharp[csProgGuideOfficeHowTo#2](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_2.cs)]  
  
2.  <span data-ttu-id="0cd48-130">將下列程式碼加入 `Main` 方法，以建立含有兩個帳戶的 `bankAccounts` 清單。</span><span class="sxs-lookup"><span data-stu-id="0cd48-130">Add the following code to the `Main` method to create a `bankAccounts` list that contains two accounts.</span></span>  
  
     [!code-csharp[csProgGuideOfficeHowTo#3](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_3.cs)]  
  
### <a name="to-declare-a-method-that-exports-account-information-to-excel"></a><span data-ttu-id="0cd48-131">宣告將帳戶資訊匯出至 Excel 的方法</span><span class="sxs-lookup"><span data-stu-id="0cd48-131">To declare a method that exports account information to Excel</span></span>  
  
1.  <span data-ttu-id="0cd48-132">將下列方法加入 `Program` 類別，以設定 Excel 試算表。</span><span class="sxs-lookup"><span data-stu-id="0cd48-132">Add the following method to the `Program` class to set up an Excel worksheet.</span></span>  
  
     <span data-ttu-id="0cd48-133">[新增](https://msdn.microsoft.com/library/microsoft.office.interop.excel.workbooks.add.aspx)方法具有指定特定範本的選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="0cd48-133">Method [Add](https://msdn.microsoft.com/library/microsoft.office.interop.excel.workbooks.add.aspx) has an optional parameter for specifying a particular template.</span></span> <span data-ttu-id="0cd48-134">如果您想要使用參數的預設值，則可利用選擇性參數 ([!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)] 中的新功能) 省略該參數的引數。</span><span class="sxs-lookup"><span data-stu-id="0cd48-134">Optional parameters, new in [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], enable you to omit the argument for that parameter if you want to use the parameter's default value.</span></span> <span data-ttu-id="0cd48-135">因為下列程式碼中未傳送引數，所以 `Add` 使用預設範本並建立新的活頁簿。</span><span class="sxs-lookup"><span data-stu-id="0cd48-135">Because no argument is sent in the following code, `Add` uses the default template and creates a new workbook.</span></span> <span data-ttu-id="0cd48-136">舊版 C# 中對等的陳述式需要有預留位置引數：`ExcelApp.Workbooks.Add(Type.Missing)`。</span><span class="sxs-lookup"><span data-stu-id="0cd48-136">The equivalent statement in earlier versions of C# requires a placeholder argument: `ExcelApp.Workbooks.Add(Type.Missing)`.</span></span>  
  
     [!code-csharp[csProgGuideOfficeHowTo#4](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_4.cs)]  
  
2.  <span data-ttu-id="0cd48-137">在 `DisplayInExcel` 結尾，加入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="0cd48-137">Add the following code at the end of `DisplayInExcel`.</span></span> <span data-ttu-id="0cd48-138">程式碼會將值插入工作表第一個資料列的前兩個資料行。</span><span class="sxs-lookup"><span data-stu-id="0cd48-138">The code inserts values into the first two columns of the first row of the worksheet.</span></span>  
  
     [!code-csharp[csProgGuideOfficeHowTo#5](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_5.cs)]  
  
3.  <span data-ttu-id="0cd48-139">在 `DisplayInExcel` 結尾，加入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="0cd48-139">Add the following code at the end of `DisplayInExcel`.</span></span> <span data-ttu-id="0cd48-140">`foreach` 迴圈會將帳戶清單中的資訊，放入工作表連續資料列的前兩個資料行。</span><span class="sxs-lookup"><span data-stu-id="0cd48-140">The `foreach` loop puts the information from the list of accounts into the first two columns of successive rows of the worksheet.</span></span>  
  
     [!code-csharp[csProgGuideOfficeHowTo#7](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_6.cs)]  
  
4.  <span data-ttu-id="0cd48-141">在 `DisplayInExcel` 結尾加入下列程式碼，以調整資料行寬度以容納內容。</span><span class="sxs-lookup"><span data-stu-id="0cd48-141">Add the following code at the end of `DisplayInExcel` to adjust the column widths to fit the content.</span></span>  
  
     [!code-csharp[csProgGuideOfficeHowTo#13](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_7.cs)]  
  
     <span data-ttu-id="0cd48-142">舊版 C# 需要明確轉換這些作業，因為 `ExcelApp.Columns[1]` 會傳回 `Object`，而 `AutoFit` 是 Excel [Range](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range.aspx) 方法。</span><span class="sxs-lookup"><span data-stu-id="0cd48-142">Earlier versions of C# require explicit casting for these operations because `ExcelApp.Columns[1]` returns an `Object`, and `AutoFit` is an Excel [Range](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range.aspx) method.</span></span> <span data-ttu-id="0cd48-143">下列各行會顯示轉型。</span><span class="sxs-lookup"><span data-stu-id="0cd48-143">The following lines show the casting.</span></span>  
  
     [!code-csharp[csProgGuideOfficeHowTo#14](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_8.cs)]  
  
     <span data-ttu-id="0cd48-144">如果 [/link](../../../csharp/language-reference/compiler-options/link-compiler-option.md) 編譯器選項參考組件；或者，同樣地，如果 Excel **內嵌 Interop 類型**屬性設定為 true，則 [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)] 和更新版本會自動將傳回的 `Object` 轉換為 `dynamic`。</span><span class="sxs-lookup"><span data-stu-id="0cd48-144">[!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], and later versions, converts the returned `Object` to `dynamic` automatically if the assembly is referenced by the [/link](../../../csharp/language-reference/compiler-options/link-compiler-option.md) compiler option or, equivalently, if the Excel **Embed Interop Types** property is set to true.</span></span> <span data-ttu-id="0cd48-145">這個屬性的預設值為 True。</span><span class="sxs-lookup"><span data-stu-id="0cd48-145">True is the default value for this property.</span></span>  
  
### <a name="to-run-the-project"></a><span data-ttu-id="0cd48-146">執行專案</span><span class="sxs-lookup"><span data-stu-id="0cd48-146">To run the project</span></span>  
  
1.  <span data-ttu-id="0cd48-147">在 `Main` 結尾，加入下行。</span><span class="sxs-lookup"><span data-stu-id="0cd48-147">Add the following line at the end of `Main`.</span></span>  
  
     [!code-csharp[csProgGuideOfficeHowTo#8](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_9.cs)]  
  
2.  <span data-ttu-id="0cd48-148">按下 CTRL+F5。</span><span class="sxs-lookup"><span data-stu-id="0cd48-148">Press CTRL+F5.</span></span>  
  
     <span data-ttu-id="0cd48-149">隨即會出現內含兩個帳戶資料的 Excel 工作表。</span><span class="sxs-lookup"><span data-stu-id="0cd48-149">An Excel worksheet appears that contains the data from the two accounts.</span></span>  
  
### <a name="to-add-a-word-document"></a><span data-ttu-id="0cd48-150">加入 Word 文件</span><span class="sxs-lookup"><span data-stu-id="0cd48-150">To add a Word document</span></span>  
  
1.  <span data-ttu-id="0cd48-151">為了說明 [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)] 和更新版本中加強 Office 程式設計的其他方法，下列程式碼會開啟 Word 應用程式，並建立 Excel 工作表連結的圖示。</span><span class="sxs-lookup"><span data-stu-id="0cd48-151">To illustrate additional ways in which [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], and later versions, enhances Office programming, the following code opens a Word application and creates an icon that links to the Excel worksheet.</span></span>  
  
     <span data-ttu-id="0cd48-152">將本步驟稍後提供的 `CreateIconInWordDoc` 方法，貼入 `Program` 類別。</span><span class="sxs-lookup"><span data-stu-id="0cd48-152">Paste method `CreateIconInWordDoc`, provided later in this step, into the `Program` class.</span></span> <span data-ttu-id="0cd48-153">`CreateIconInWordDoc` 使用具名和選擇性引數來降低 [Documents.Add](https://msdn.microsoft.com/library/microsoft.office.interop.word.documents.add.aspx) 和 [Selection.PasteSpecial](https://msdn.microsoft.com/library/microsoft.office.interop.word.selection.pastespecial.aspx) 方法呼叫的複雜性。</span><span class="sxs-lookup"><span data-stu-id="0cd48-153">`CreateIconInWordDoc` uses named and optional arguments to reduce the complexity of the method calls to [Add](https://msdn.microsoft.com/library/microsoft.office.interop.word.documents.add.aspx) and [PasteSpecial](https://msdn.microsoft.com/library/microsoft.office.interop.word.selection.pastespecial.aspx).</span></span> <span data-ttu-id="0cd48-154">這些呼叫採用 [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)] 引進的兩個其他新功能，簡化了具有參考參數之 COM 方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="0cd48-154">These calls incorporate two other new features introduced in [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)] that simplify calls to COM methods that have reference parameters.</span></span> <span data-ttu-id="0cd48-155">首先，您可以將引數以實值參數的形式傳送到參考參數。</span><span class="sxs-lookup"><span data-stu-id="0cd48-155">First, you can send arguments to the reference parameters as if they were value parameters.</span></span> <span data-ttu-id="0cd48-156">也就是說，可以直接傳送值而無須建立每個參考參數的變數。</span><span class="sxs-lookup"><span data-stu-id="0cd48-156">That is, you can send values directly, without creating a variable for each reference parameter.</span></span> <span data-ttu-id="0cd48-157">編譯器會產生暫存變數來保存引數值，並在從呼叫返回時捨棄變數。</span><span class="sxs-lookup"><span data-stu-id="0cd48-157">The compiler generates temporary variables to hold the argument values, and discards the variables when you return from the call.</span></span> <span data-ttu-id="0cd48-158">其次，您可以省略引數清單中的 `ref` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="0cd48-158">Second, you can omit the `ref` keyword in the argument list.</span></span>  
  
     <span data-ttu-id="0cd48-159">`Add` 方法有四個參考參數，而且都是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="0cd48-159">The `Add` method has four reference parameters, all of which are optional.</span></span> <span data-ttu-id="0cd48-160">在 [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)] 或更新版本中，如果想要使用其預設值，可以省略任何或所有參數的引數。</span><span class="sxs-lookup"><span data-stu-id="0cd48-160">In [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], or later versions, you can omit arguments for any or all of the parameters if you want to use their default values.</span></span> <span data-ttu-id="0cd48-161">在 [!INCLUDE[csharp_orcas_long](~/includes/csharp-orcas-long-md.md)] 和舊版本中，必須為每個參數提供引數，且引數必須是變數，因為參數是參考參數。</span><span class="sxs-lookup"><span data-stu-id="0cd48-161">In [!INCLUDE[csharp_orcas_long](~/includes/csharp-orcas-long-md.md)] and earlier versions, an argument must be provided for each parameter, and the argument must be a variable because the parameters are reference parameters.</span></span>  
  
     <span data-ttu-id="0cd48-162">`PasteSpecial` 方法會將內容插入剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="0cd48-162">The `PasteSpecial` method inserts the contents of the Clipboard.</span></span> <span data-ttu-id="0cd48-163">此方法有七個參考參數，且都是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="0cd48-163">The method has seven reference parameters, all of which are optional.</span></span> <span data-ttu-id="0cd48-164">下列程式碼指定其中兩個的引數：`Link` 可建立剪貼簿的內容的來源連結，以及 `DisplayAsIcon` 可將連結顯示為圖示。</span><span class="sxs-lookup"><span data-stu-id="0cd48-164">The following code specifies arguments for two of them: `Link`, to create a link to the source of the Clipboard contents, and `DisplayAsIcon`, to display the link as an icon.</span></span> <span data-ttu-id="0cd48-165">在 [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)] 中，可以為這兩者使用具名引數，並省略其他引數。</span><span class="sxs-lookup"><span data-stu-id="0cd48-165">In [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], you can use named arguments for those two and omit the others.</span></span> <span data-ttu-id="0cd48-166">雖然這些是參考參數，但是您不需要使用 `ref` 關鍵字，或建立傳送為引數的變數。</span><span class="sxs-lookup"><span data-stu-id="0cd48-166">Although these are reference parameters, you do not have to use the `ref` keyword, or to create variables to send in as arguments.</span></span> <span data-ttu-id="0cd48-167">可以直接傳送值。</span><span class="sxs-lookup"><span data-stu-id="0cd48-167">You can send the values directly.</span></span> <span data-ttu-id="0cd48-168">在 [!INCLUDE[csharp_orcas_long](~/includes/csharp-orcas-long-md.md)] 和舊版本中，必須為每個參考參數傳送變數引數。</span><span class="sxs-lookup"><span data-stu-id="0cd48-168">In [!INCLUDE[csharp_orcas_long](~/includes/csharp-orcas-long-md.md)] and earlier versions, you must send a variable argument for each reference parameter.</span></span>  
  
     [!code-csharp[csProgGuideOfficeHowTo#9](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_10.cs)]  
  
     <span data-ttu-id="0cd48-169">在 [!INCLUDE[csharp_orcas_long](~/includes/csharp-orcas-long-md.md)] 或舊版語言中，需要有下列更為複雜的程式碼。</span><span class="sxs-lookup"><span data-stu-id="0cd48-169">In [!INCLUDE[csharp_orcas_long](~/includes/csharp-orcas-long-md.md)] or earlier versions of the language, the following more complex code is required.</span></span>  
  
     [!code-csharp[csProgGuideOfficeHowTo#10](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_11.cs)]  
  
2.  <span data-ttu-id="0cd48-170">在 `Main` 結尾，加入下列陳述式。</span><span class="sxs-lookup"><span data-stu-id="0cd48-170">Add the following statement at the end of `Main`.</span></span>  
  
     [!code-csharp[csProgGuideOfficeHowTo#11](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_12.cs)]  
  
3.  <span data-ttu-id="0cd48-171">在 `DisplayInExcel` 結尾，加入下列陳述式。</span><span class="sxs-lookup"><span data-stu-id="0cd48-171">Add the following statement at the end of `DisplayInExcel`.</span></span> <span data-ttu-id="0cd48-172">`Copy` 方法會將工作表加入剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="0cd48-172">The `Copy` method adds the worksheet to the Clipboard.</span></span>  
  
     [!code-csharp[csProgGuideOfficeHowTo#12](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_13.cs)]  
  
4.  <span data-ttu-id="0cd48-173">按下 CTRL+F5。</span><span class="sxs-lookup"><span data-stu-id="0cd48-173">Press CTRL+F5.</span></span>  
  
     <span data-ttu-id="0cd48-174">隨即會出現含有圖示的 Word 文件。</span><span class="sxs-lookup"><span data-stu-id="0cd48-174">A Word document appears that contains an icon.</span></span> <span data-ttu-id="0cd48-175">按兩下圖示，即可將該工作表帶到前景。</span><span class="sxs-lookup"><span data-stu-id="0cd48-175">Double-click the icon to bring the worksheet to the foreground.</span></span>  
  
### <a name="to-set-the-embed-interop-types-property"></a><span data-ttu-id="0cd48-176">設定內嵌 Interop 類型屬性</span><span class="sxs-lookup"><span data-stu-id="0cd48-176">To set the Embed Interop Types property</span></span>  
  
1.  <span data-ttu-id="0cd48-177">當您在執行階段呼叫不需要主要 Interop 組件 (PIA) 的 COM 類型時，可以使用其他增強功能。</span><span class="sxs-lookup"><span data-stu-id="0cd48-177">Additional enhancements are possible when you call a COM type that does not require a primary interop assembly (PIA) at run time.</span></span> <span data-ttu-id="0cd48-178">移除與 PIA 的相依性，可達成版本獨立且更容易進行部署。</span><span class="sxs-lookup"><span data-stu-id="0cd48-178">Removing the dependency on PIAs results in version independence and easier deployment.</span></span> <span data-ttu-id="0cd48-179">如需沒有 PIA 的程式設計優點的詳細資訊，請參閱[逐步解說：從 Managed 組件內嵌類型](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21)。</span><span class="sxs-lookup"><span data-stu-id="0cd48-179">For more information about the advantages of programming without PIAs, see [Walkthrough: Embedding Types from Managed Assemblies](http://msdn.microsoft.com/library/b28ec92c-1867-4847-95c0-61adfe095e21).</span></span>  
  
     <span data-ttu-id="0cd48-180">此外，程式設計會更為容易，因為 COM 方法所需和所傳回的類型可以使用類型 `dynamic` 而非 `Object` 加以呈現。</span><span class="sxs-lookup"><span data-stu-id="0cd48-180">In addition, programming is easier because the types that are required and returned by COM methods can be represented by using the type `dynamic` instead of `Object`.</span></span> <span data-ttu-id="0cd48-181">除非處於執行階段，否則不會評估類型為 `dynamic` 的變數，如此即無須明確轉型。</span><span class="sxs-lookup"><span data-stu-id="0cd48-181">Variables that have type `dynamic` are not evaluated until run time, which eliminates the need for explicit casting.</span></span> <span data-ttu-id="0cd48-182">如需詳細資訊，請參閱[使用動態類型](../../../csharp/programming-guide/types/using-type-dynamic.md)。</span><span class="sxs-lookup"><span data-stu-id="0cd48-182">For more information, see [Using Type dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md).</span></span>  
  
     <span data-ttu-id="0cd48-183">在 [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)] 中，預設行為是內嵌類型資訊，而非使用 PIA。</span><span class="sxs-lookup"><span data-stu-id="0cd48-183">In [!INCLUDE[csharp_dev10_long](~/includes/csharp-dev10-long-md.md)], embedding type information instead of using PIAs is default behavior.</span></span> <span data-ttu-id="0cd48-184">因為使用該預設值，已簡化了數個先前的範例，因為明確轉型已非必要。</span><span class="sxs-lookup"><span data-stu-id="0cd48-184">Because of that default, several of the previous examples are simplified because explicit casting is not required.</span></span> <span data-ttu-id="0cd48-185">例如，`worksheet` 中的 `DisplayInExcel` 宣告，撰寫為 `Excel._Worksheet workSheet = excelApp.ActiveSheet`，而非 `Excel._Worksheet workSheet = (Excel.Worksheet)excelApp.ActiveSheet`。</span><span class="sxs-lookup"><span data-stu-id="0cd48-185">For example, the declaration of `worksheet` in `DisplayInExcel` is written as `Excel._Worksheet workSheet = excelApp.ActiveSheet` rather than `Excel._Worksheet workSheet = (Excel.Worksheet)excelApp.ActiveSheet`.</span></span> <span data-ttu-id="0cd48-186">如果沒有預設值，則相同方法中的 `AutoFit` 呼叫也需要明確轉型，因為 `ExcelApp.Columns[1]` 會傳回 `Object`，而 `AutoFit` 是 Excel 方法。</span><span class="sxs-lookup"><span data-stu-id="0cd48-186">The calls to `AutoFit` in the same method also would require explicit casting without the default, because `ExcelApp.Columns[1]` returns an `Object`, and `AutoFit` is an Excel  method.</span></span> <span data-ttu-id="0cd48-187">下列程式碼會顯示轉型。</span><span class="sxs-lookup"><span data-stu-id="0cd48-187">The following code shows the casting.</span></span>  
  
     [!code-csharp[csProgGuideOfficeHowTo#14](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_8.cs)]  
  
2.  <span data-ttu-id="0cd48-188">若要變更預設值，並使用 PIA 而非內嵌類型資訊，請展開方案總管中的 [參考] 節點，然後選取 **Microsoft.Office.Interop.Excel** 或 **Microsoft.Office.Interop.Word**。</span><span class="sxs-lookup"><span data-stu-id="0cd48-188">To change the default and use PIAs instead of embedding type information, expand the **References** node in **Solution Explorer** and then select **Microsoft.Office.Interop.Excel** or **Microsoft.Office.Interop.Word**.</span></span>  
  
3.  <span data-ttu-id="0cd48-189">如果看不到 [屬性] 視窗，請按 **F4** 鍵。</span><span class="sxs-lookup"><span data-stu-id="0cd48-189">If you cannot see the **Properties** window, press **F4**.</span></span>  
  
4.  <span data-ttu-id="0cd48-190">在屬性清單中尋找 [內嵌 Interop 類型]，並將其值變更為 **False**。</span><span class="sxs-lookup"><span data-stu-id="0cd48-190">Find **Embed Interop Types** in the list of properties, and change its value to **False**.</span></span> <span data-ttu-id="0cd48-191">同樣地，也可以在命令提示字元處使用 [/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) 編譯器選項，而非 [/link](../../../csharp/language-reference/compiler-options/link-compiler-option.md) 進行編譯。</span><span class="sxs-lookup"><span data-stu-id="0cd48-191">Equivalently, you can compile by using the [/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) compiler option instead of [/link](../../../csharp/language-reference/compiler-options/link-compiler-option.md) at a command prompt.</span></span>  
  
### <a name="to-add-additional-formatting-to-the-table"></a><span data-ttu-id="0cd48-192">加入表格的其他格式</span><span class="sxs-lookup"><span data-stu-id="0cd48-192">To add additional formatting to the table</span></span>  
  
1.  <span data-ttu-id="0cd48-193">將 `AutoFit` 中對兩個 `DisplayInExcel` 的呼叫，取代為下列陳述式。</span><span class="sxs-lookup"><span data-stu-id="0cd48-193">Replace the two calls to `AutoFit` in `DisplayInExcel` with the following statement.</span></span>  
  
     [!code-csharp[csProgGuideOfficeHowTo#15](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_14.cs)]  
  
     <span data-ttu-id="0cd48-194">[Range.AutoFormat](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range.autoformat.aspx) 方法有七個實值參數，都是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="0cd48-194">The [AutoFormat](https://msdn.microsoft.com/library/microsoft.office.interop.excel.range.autoformat.aspx) method has seven value parameters, all of which are optional.</span></span> <span data-ttu-id="0cd48-195">您可利用具名引數和選擇性引數，提供零個引數、數個引數或所有引數。</span><span class="sxs-lookup"><span data-stu-id="0cd48-195">Named and optional arguments enable you to provide arguments for none, some, or all of them.</span></span> <span data-ttu-id="0cd48-196">在前述陳述式中，只為其中一個參數 (`Format`) 提供引數。</span><span class="sxs-lookup"><span data-stu-id="0cd48-196">In the previous statement, an argument is supplied for only one of the parameters, `Format`.</span></span> <span data-ttu-id="0cd48-197">因為 `Format` 是參數清單中的第一個參數，所以無須提供參數名稱。</span><span class="sxs-lookup"><span data-stu-id="0cd48-197">Because `Format` is the first parameter in the parameter list, you do not have to provide the parameter name.</span></span> <span data-ttu-id="0cd48-198">但如果包含參數名稱，則可能較容易了解該陳述式，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="0cd48-198">However, the statement might be easier to understand if the parameter name is included, as is shown in the following code.</span></span>  
  
     [!code-csharp[csProgGuideOfficeHowTo#16](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_15.cs)]  
  
2.  <span data-ttu-id="0cd48-199">按 CTRL + F5 鍵查看結果。</span><span class="sxs-lookup"><span data-stu-id="0cd48-199">Press CTRL+F5 to see the result.</span></span> <span data-ttu-id="0cd48-200">其他格式會列在 [XlRangeAutoFormat ](https://msdn.microsoft.com/library/microsoft.office.interop.excel.xlrangeautoformat.aspx) 列舉中。</span><span class="sxs-lookup"><span data-stu-id="0cd48-200">Other formats are listed in the [XlRangeAutoFormat](https://msdn.microsoft.com/library/microsoft.office.interop.excel.xlrangeautoformat.aspx) enumeration.</span></span>  
  
3.  <span data-ttu-id="0cd48-201">請比較步驟 1 中的陳述式與下列程式碼，這樣會顯示 [!INCLUDE[csharp_orcas_long](~/includes/csharp-orcas-long-md.md)] 或舊版本中所需的引數。</span><span class="sxs-lookup"><span data-stu-id="0cd48-201">Compare the statement in step 1 with the following code, which shows the arguments that are required in [!INCLUDE[csharp_orcas_long](~/includes/csharp-orcas-long-md.md)] or earlier versions.</span></span>  
  
     [!code-csharp[csProgGuideOfficeHowTo#17](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_16.cs)]  
  
## <a name="example"></a><span data-ttu-id="0cd48-202">範例</span><span class="sxs-lookup"><span data-stu-id="0cd48-202">Example</span></span>  
 <span data-ttu-id="0cd48-203">下列程式碼顯示完整範例。</span><span class="sxs-lookup"><span data-stu-id="0cd48-203">The following code shows the complete example.</span></span>  
  
 [!code-csharp[csProgGuideOfficeHowTo#18](../../../csharp/programming-guide/interop/codesnippet/CSharp/how-to-access-office-onterop-objects_17.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="0cd48-204">請參閱</span><span class="sxs-lookup"><span data-stu-id="0cd48-204">See Also</span></span>  
 <xref:System.Type.Missing?displayProperty=nameWithType>  
 [<span data-ttu-id="0cd48-205">dynamic</span><span class="sxs-lookup"><span data-stu-id="0cd48-205">dynamic</span></span>](../../../csharp/language-reference/keywords/dynamic.md)  
 [<span data-ttu-id="0cd48-206">使用動態型別</span><span class="sxs-lookup"><span data-stu-id="0cd48-206">Using Type dynamic</span></span>](../../../csharp/programming-guide/types/using-type-dynamic.md)  
 [<span data-ttu-id="0cd48-207">具名和選擇性引數</span><span class="sxs-lookup"><span data-stu-id="0cd48-207">Named and Optional Arguments</span></span>](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)  
 [<span data-ttu-id="0cd48-208">如何：在 Office 程式設計中使用具名和選擇性引數</span><span class="sxs-lookup"><span data-stu-id="0cd48-208">How to: Use Named and Optional Arguments in Office Programming</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
