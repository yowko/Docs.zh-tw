---
title: HOW TO：使用 Visual C# 功能存取 Office Interop 物件 - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- optional parameters [C#], Office programming
- named and optional arguments [C#], Office programming
- dynamic [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
- Office programming [C#]
ms.assetid: 041b25c2-3512-4e0f-a4ea-ceb2999e4d5e
ms.openlocfilehash: 8e99402752b3fafb486735d56d66737f03ceec30
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972093"
---
# <a name="how-to-access-office-interop-objects-by-using-visual-c-features-c-programming-guide"></a><span data-ttu-id="20066-102">作法：使用 Visual C# 功能存取 Office Interop 物件 (C# 程式設計指南)</span><span class="sxs-lookup"><span data-stu-id="20066-102">How to: Access Office Interop Objects by Using Visual C# Features (C# Programming Guide)</span></span>

<span data-ttu-id="20066-103">Visual C# 的功能可以簡化 Office API 物件存取。</span><span class="sxs-lookup"><span data-stu-id="20066-103">Visual C# has features that simplify access to Office API objects.</span></span> <span data-ttu-id="20066-104">新功能包括具名引數和選擇性引數、稱為 `dynamic` 的新類型，以及傳遞引數以像是實值參數的形式，參考 COM 方法中參數的能力。</span><span class="sxs-lookup"><span data-stu-id="20066-104">The new features include named and optional arguments, a new type called `dynamic`, and the ability to pass arguments to reference parameters in COM methods as if they were value parameters.</span></span>

<span data-ttu-id="20066-105">在本主題中，您將使用新的功能撰寫可建立及顯示 Microsoft Office Excel 工作表的程式碼。</span><span class="sxs-lookup"><span data-stu-id="20066-105">In this topic you will use the new features to write code that creates and displays a Microsoft Office Excel worksheet.</span></span> <span data-ttu-id="20066-106">接著，您將要撰寫可加入 Office Word 文件的程式碼，而該文件包含連結至 Excel 工作表的圖示。</span><span class="sxs-lookup"><span data-stu-id="20066-106">You will then write code to add an Office Word document that contains an icon that is linked to the Excel worksheet.</span></span>

<span data-ttu-id="20066-107">若要完成這個逐步解說，電腦上必須安裝 Microsoft Office Excel 2007 和 Microsoft Office Word 2007 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="20066-107">To complete this walkthrough, you must have Microsoft Office Excel 2007 and Microsoft Office Word 2007, or later versions, installed on your computer.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-new-console-application"></a><span data-ttu-id="20066-108">建立新的主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="20066-108">To create a new console application</span></span>

1. <span data-ttu-id="20066-109">啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="20066-109">Start Visual Studio.</span></span>

2. <span data-ttu-id="20066-110">在 [檔案] 功能表中，指向 [新增]，然後按一下 [專案]。</span><span class="sxs-lookup"><span data-stu-id="20066-110">On the **File** menu, point to **New**, and then click **Project**.</span></span> <span data-ttu-id="20066-111">[ **新增專案** ] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="20066-111">The **New Project** dialog box appears.</span></span>

3. <span data-ttu-id="20066-112">在 [已安裝的範本] 窗格中，展開 [Visual C#]，然後按一下 [Windows]。</span><span class="sxs-lookup"><span data-stu-id="20066-112">In the **Installed Templates** pane, expand **Visual C#**, and then click **Windows**.</span></span>

4. <span data-ttu-id="20066-113">查看 [新增專案] 對話方塊頂端，確定已選取 [.NET Framework 4] (或更新版本) 作為目標架構。</span><span class="sxs-lookup"><span data-stu-id="20066-113">Look at the top of the **New Project** dialog box to make sure that **.NET Framework 4** (or later version) is selected as a target framework.</span></span>

5. <span data-ttu-id="20066-114">按一下 [範本] 窗格中的 [主控台應用程式]。</span><span class="sxs-lookup"><span data-stu-id="20066-114">In the **Templates** pane, click **Console Application**.</span></span>

6. <span data-ttu-id="20066-115">在 [名稱] 欄位中鍵入專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="20066-115">Type a name for your project in the **Name** field.</span></span>

7. <span data-ttu-id="20066-116">按一下 [確定 **Deploying Office Solutions**]。</span><span class="sxs-lookup"><span data-stu-id="20066-116">Click **OK**.</span></span>

     <span data-ttu-id="20066-117">新的專案隨即出現在方案總管中。</span><span class="sxs-lookup"><span data-stu-id="20066-117">The new project appears in **Solution Explorer**.</span></span>

## <a name="to-add-references"></a><span data-ttu-id="20066-118">加入參考</span><span class="sxs-lookup"><span data-stu-id="20066-118">To add references</span></span>

1. <span data-ttu-id="20066-119">在方案總管中，於專案名稱上按一下滑鼠右鍵，然後按一下 [新增參考]。</span><span class="sxs-lookup"><span data-stu-id="20066-119">In **Solution Explorer**, right-click your project's name and then click **Add Reference**.</span></span> <span data-ttu-id="20066-120">[加入參考] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="20066-120">The **Add Reference** dialog box appears.</span></span>

2. <span data-ttu-id="20066-121">在 [組件] 頁面的 [元件名稱] 清單中，選取 [Microsoft.Office.Interop.Word]，然後按住 CTRL 鍵並選取 [Microsoft.Office.Interop.Excel]。</span><span class="sxs-lookup"><span data-stu-id="20066-121">On the **Assemblies**  page, select **Microsoft.Office.Interop.Word** in the **Component Name** list, and then hold down the CTRL key and select **Microsoft.Office.Interop.Excel**.</span></span>  <span data-ttu-id="20066-122">如果看不到組件，則可能需要確定組件已安裝及顯示 (請參閱[如何：安裝 Office 主要 Interop 組件](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies))</span><span class="sxs-lookup"><span data-stu-id="20066-122">If you do not see the assemblies, you may need to ensure they are installed and displayed (see [How to: Install Office Primary Interop Assemblies](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies))</span></span>

3. <span data-ttu-id="20066-123">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="20066-123">Click **OK**.</span></span>

## <a name="to-add-necessary-using-directives"></a><span data-ttu-id="20066-124">加入必要的 using 指示詞</span><span class="sxs-lookup"><span data-stu-id="20066-124">To add necessary using directives</span></span>

1. <span data-ttu-id="20066-125">在方案總管中，以滑鼠右鍵按一下 **Program.cs** 檔案，然後按一下 [檢視程式碼]。</span><span class="sxs-lookup"><span data-stu-id="20066-125">In **Solution Explorer**, right-click the **Program.cs** file and then click **View Code**.</span></span>

2. <span data-ttu-id="20066-126">將下列 `using` 指示詞加入程式碼檔案頂端。</span><span class="sxs-lookup"><span data-stu-id="20066-126">Add the following `using` directives to the top of the code file.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#1)]

## <a name="to-create-a-list-of-bank-accounts"></a><span data-ttu-id="20066-127">建立銀行帳戶清單</span><span class="sxs-lookup"><span data-stu-id="20066-127">To create a list of bank accounts</span></span>

1. <span data-ttu-id="20066-128">將下列類別定義貼入 `Program` 類別下的 **Program.cs**。</span><span class="sxs-lookup"><span data-stu-id="20066-128">Paste the following class definition into **Program.cs**, under the `Program` class.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#2)]

2. <span data-ttu-id="20066-129">將下列程式碼加入 `Main` 方法，以建立含有兩個帳戶的 `bankAccounts` 清單。</span><span class="sxs-lookup"><span data-stu-id="20066-129">Add the following code to the `Main` method to create a `bankAccounts` list that contains two accounts.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#3)]

## <a name="to-declare-a-method-that-exports-account-information-to-excel"></a><span data-ttu-id="20066-130">宣告將帳戶資訊匯出至 Excel 的方法</span><span class="sxs-lookup"><span data-stu-id="20066-130">To declare a method that exports account information to Excel</span></span>

1. <span data-ttu-id="20066-131">將下列方法加入 `Program` 類別，以設定 Excel 試算表。</span><span class="sxs-lookup"><span data-stu-id="20066-131">Add the following method to the `Program` class to set up an Excel worksheet.</span></span>

     <span data-ttu-id="20066-132"><xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> 方法有用以指定特定範本的選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="20066-132">Method <xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A> has an optional parameter for specifying a particular template.</span></span> <span data-ttu-id="20066-133">如果您想要使用參數的預設值，則可利用選擇性參數 (C# 4 中的新功能) 省略該參數的引數。</span><span class="sxs-lookup"><span data-stu-id="20066-133">Optional parameters, new in C# 4, enable you to omit the argument for that parameter if you want to use the parameter's default value.</span></span> <span data-ttu-id="20066-134">因為下列程式碼中未傳送引數，所以 `Add` 使用預設範本並建立新的活頁簿。</span><span class="sxs-lookup"><span data-stu-id="20066-134">Because no argument is sent in the following code, `Add` uses the default template and creates a new workbook.</span></span> <span data-ttu-id="20066-135">舊版 C# 中對等的陳述式需要有預留位置引數：`ExcelApp.Workbooks.Add(Type.Missing)`。</span><span class="sxs-lookup"><span data-stu-id="20066-135">The equivalent statement in earlier versions of C# requires a placeholder argument: `ExcelApp.Workbooks.Add(Type.Missing)`.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#4)]

2. <span data-ttu-id="20066-136">在 `DisplayInExcel` 結尾，加入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="20066-136">Add the following code at the end of `DisplayInExcel`.</span></span> <span data-ttu-id="20066-137">程式碼會將值插入工作表第一個資料列的前兩個資料行。</span><span class="sxs-lookup"><span data-stu-id="20066-137">The code inserts values into the first two columns of the first row of the worksheet.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#5)]

3. <span data-ttu-id="20066-138">在 `DisplayInExcel` 結尾，加入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="20066-138">Add the following code at the end of `DisplayInExcel`.</span></span> <span data-ttu-id="20066-139">`foreach` 迴圈會將帳戶清單中的資訊，放入工作表連續資料列的前兩個資料行。</span><span class="sxs-lookup"><span data-stu-id="20066-139">The `foreach` loop puts the information from the list of accounts into the first two columns of successive rows of the worksheet.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#7)]

4. <span data-ttu-id="20066-140">在 `DisplayInExcel` 結尾加入下列程式碼，以調整資料行寬度以容納內容。</span><span class="sxs-lookup"><span data-stu-id="20066-140">Add the following code at the end of `DisplayInExcel` to adjust the column widths to fit the content.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#13)]

     <span data-ttu-id="20066-141">因為 `ExcelApp.Columns[1]` 會傳回 `Object`，所以舊版 C# 需要明確轉換這些作業，而 `AutoFit` 是 Excel <xref:Microsoft.Office.Interop.Excel.Range> 方法。</span><span class="sxs-lookup"><span data-stu-id="20066-141">Earlier versions of C# require explicit casting for these operations because `ExcelApp.Columns[1]` returns an `Object`, and `AutoFit` is an Excel <xref:Microsoft.Office.Interop.Excel.Range> method.</span></span> <span data-ttu-id="20066-142">下列各行會顯示轉型。</span><span class="sxs-lookup"><span data-stu-id="20066-142">The following lines show the casting.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#14)]

     <span data-ttu-id="20066-143">如果 [/link](../../language-reference/compiler-options/link-compiler-option.md) 編譯器選項參考組件；或者，同樣地，如果 Excel [內嵌 Interop 型別] 屬性設定為 true，C# 4 和更新版本會自動將傳回的 `Object` 轉換為 `dynamic`。</span><span class="sxs-lookup"><span data-stu-id="20066-143">C# 4, and later versions, converts the returned `Object` to `dynamic` automatically if the assembly is referenced by the [/link](../../language-reference/compiler-options/link-compiler-option.md) compiler option or, equivalently, if the Excel **Embed Interop Types** property is set to true.</span></span> <span data-ttu-id="20066-144">這個屬性的預設值為 True。</span><span class="sxs-lookup"><span data-stu-id="20066-144">True is the default value for this property.</span></span>

## <a name="to-run-the-project"></a><span data-ttu-id="20066-145">執行專案</span><span class="sxs-lookup"><span data-stu-id="20066-145">To run the project</span></span>

1. <span data-ttu-id="20066-146">在 `Main` 結尾，加入下行。</span><span class="sxs-lookup"><span data-stu-id="20066-146">Add the following line at the end of `Main`.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#8)]

2. <span data-ttu-id="20066-147">按下 CTRL+F5。</span><span class="sxs-lookup"><span data-stu-id="20066-147">Press CTRL+F5.</span></span>

     <span data-ttu-id="20066-148">隨即會出現內含兩個帳戶資料的 Excel 工作表。</span><span class="sxs-lookup"><span data-stu-id="20066-148">An Excel worksheet appears that contains the data from the two accounts.</span></span>

## <a name="to-add-a-word-document"></a><span data-ttu-id="20066-149">加入 Word 文件</span><span class="sxs-lookup"><span data-stu-id="20066-149">To add a Word document</span></span>

1. <span data-ttu-id="20066-150">為了說明 C# 4 和更新版本中加強 Office 程式設計的其他方法，下列程式碼會開啟 Word 應用程式，並建立 Excel 工作表連結的圖示。</span><span class="sxs-lookup"><span data-stu-id="20066-150">To illustrate additional ways in which C# 4, and later versions, enhances Office programming, the following code opens a Word application and creates an icon that links to the Excel worksheet.</span></span>

     <span data-ttu-id="20066-151">將本步驟稍後提供的 `CreateIconInWordDoc` 方法，貼入 `Program` 類別。</span><span class="sxs-lookup"><span data-stu-id="20066-151">Paste method `CreateIconInWordDoc`, provided later in this step, into the `Program` class.</span></span> <span data-ttu-id="20066-152">`CreateIconInWordDoc` 使用具名和選擇性引數來降低 <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> 和 <xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A> 方法呼叫的複雜性。</span><span class="sxs-lookup"><span data-stu-id="20066-152">`CreateIconInWordDoc` uses named and optional arguments to reduce the complexity of the method calls to <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> and <xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A>.</span></span> <span data-ttu-id="20066-153">這些呼叫採用 C# 4 引進的兩個其他新功能，簡化了具有參考參數之 COM 方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="20066-153">These calls incorporate two other new features introduced in C# 4 that simplify calls to COM methods that have reference parameters.</span></span> <span data-ttu-id="20066-154">首先，您可以將引數以實值參數的形式傳送到參考參數。</span><span class="sxs-lookup"><span data-stu-id="20066-154">First, you can send arguments to the reference parameters as if they were value parameters.</span></span> <span data-ttu-id="20066-155">也就是說，可以直接傳送值而無須建立每個參考參數的變數。</span><span class="sxs-lookup"><span data-stu-id="20066-155">That is, you can send values directly, without creating a variable for each reference parameter.</span></span> <span data-ttu-id="20066-156">編譯器會產生暫存變數來保存引數值，並在從呼叫返回時捨棄變數。</span><span class="sxs-lookup"><span data-stu-id="20066-156">The compiler generates temporary variables to hold the argument values, and discards the variables when you return from the call.</span></span> <span data-ttu-id="20066-157">其次，您可以省略引數清單中的 `ref` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="20066-157">Second, you can omit the `ref` keyword in the argument list.</span></span>

     <span data-ttu-id="20066-158">`Add` 方法有四個參考參數，而且都是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="20066-158">The `Add` method has four reference parameters, all of which are optional.</span></span> <span data-ttu-id="20066-159">在 C# 4.0 與更新版本中，如果想要使用其預設值，可以省略任何或所有參數的引數。</span><span class="sxs-lookup"><span data-stu-id="20066-159">In C# 4.0 and later versions, you can omit arguments for any or all of the parameters if you want to use their default values.</span></span> <span data-ttu-id="20066-160">在 C# 3.0與舊版中，必須為每個參數提供引數，且引數必須是變數，因為參數是參考參數。</span><span class="sxs-lookup"><span data-stu-id="20066-160">In C# 3.0 and earlier versions, an argument must be provided for each parameter, and the argument must be a variable because the parameters are reference parameters.</span></span>

     <span data-ttu-id="20066-161">`PasteSpecial` 方法會將內容插入剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="20066-161">The `PasteSpecial` method inserts the contents of the Clipboard.</span></span> <span data-ttu-id="20066-162">此方法有七個參考參數，且都是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="20066-162">The method has seven reference parameters, all of which are optional.</span></span> <span data-ttu-id="20066-163">下列程式碼指定其中兩個的引數：`Link` 可建立剪貼簿的內容的來源連結，以及 `DisplayAsIcon` 可將連結顯示為圖示。</span><span class="sxs-lookup"><span data-stu-id="20066-163">The following code specifies arguments for two of them: `Link`, to create a link to the source of the Clipboard contents, and `DisplayAsIcon`, to display the link as an icon.</span></span> <span data-ttu-id="20066-164">在 C# 4.0 與更新版本中，可以為這兩者使用具名引數，並省略其他引數。</span><span class="sxs-lookup"><span data-stu-id="20066-164">In C# 4.0 and later versions, you can use named arguments for those two and omit the others.</span></span> <span data-ttu-id="20066-165">雖然這些是參考參數，但是您不需要使用 `ref` 關鍵字，或建立傳送為引數的變數。</span><span class="sxs-lookup"><span data-stu-id="20066-165">Although these are reference parameters, you do not have to use the `ref` keyword, or to create variables to send in as arguments.</span></span> <span data-ttu-id="20066-166">可以直接傳送值。</span><span class="sxs-lookup"><span data-stu-id="20066-166">You can send the values directly.</span></span> <span data-ttu-id="20066-167">在 C# 3.0 舊版中，必須為每個參考參數提供變數引數。</span><span class="sxs-lookup"><span data-stu-id="20066-167">In C# 3.0 and earlier versions, you must supply a variable argument for each reference parameter.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#9)]

     <span data-ttu-id="20066-168">在 C# 3.0 與舊版語言中，需要有下列更為複雜的程式碼。</span><span class="sxs-lookup"><span data-stu-id="20066-168">In C# 3.0 and earlier versions of the language, the following more complex code is required.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#10)]

2. <span data-ttu-id="20066-169">在 `Main` 結尾，加入下列陳述式。</span><span class="sxs-lookup"><span data-stu-id="20066-169">Add the following statement at the end of `Main`.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#11)]

3. <span data-ttu-id="20066-170">在 `DisplayInExcel` 結尾，加入下列陳述式。</span><span class="sxs-lookup"><span data-stu-id="20066-170">Add the following statement at the end of `DisplayInExcel`.</span></span> <span data-ttu-id="20066-171">`Copy` 方法會將工作表加入剪貼簿。</span><span class="sxs-lookup"><span data-stu-id="20066-171">The `Copy` method adds the worksheet to the Clipboard.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#12)]

4. <span data-ttu-id="20066-172">按下 CTRL+F5。</span><span class="sxs-lookup"><span data-stu-id="20066-172">Press CTRL+F5.</span></span>

     <span data-ttu-id="20066-173">隨即會出現含有圖示的 Word 文件。</span><span class="sxs-lookup"><span data-stu-id="20066-173">A Word document appears that contains an icon.</span></span> <span data-ttu-id="20066-174">按兩下圖示，即可將該工作表帶到前景。</span><span class="sxs-lookup"><span data-stu-id="20066-174">Double-click the icon to bring the worksheet to the foreground.</span></span>

## <a name="to-set-the-embed-interop-types-property"></a><span data-ttu-id="20066-175">設定內嵌 Interop 類型屬性</span><span class="sxs-lookup"><span data-stu-id="20066-175">To set the Embed Interop Types property</span></span>

1. <span data-ttu-id="20066-176">當您在執行階段呼叫不需要主要 Interop 組件 (PIA) 的 COM 類型時，可以使用其他增強功能。</span><span class="sxs-lookup"><span data-stu-id="20066-176">Additional enhancements are possible when you call a COM type that does not require a primary interop assembly (PIA) at run time.</span></span> <span data-ttu-id="20066-177">移除與 PIA 的相依性，可達成版本獨立且更容易進行部署。</span><span class="sxs-lookup"><span data-stu-id="20066-177">Removing the dependency on PIAs results in version independence and easier deployment.</span></span> <span data-ttu-id="20066-178">如需沒有 PIA 的程式設計優點詳細資訊，請參閱[逐步解說：從 Managed 組件內嵌類型](../../../standard/assembly/embed-types-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="20066-178">For more information about the advantages of programming without PIAs, see [Walkthrough: Embedding Types from Managed Assemblies](../../../standard/assembly/embed-types-visual-studio.md).</span></span>

     <span data-ttu-id="20066-179">此外，程式設計會更為容易，因為 COM 方法所需和所傳回的類型可以使用類型 `dynamic` 而非 `Object` 加以呈現。</span><span class="sxs-lookup"><span data-stu-id="20066-179">In addition, programming is easier because the types that are required and returned by COM methods can be represented by using the type `dynamic` instead of `Object`.</span></span> <span data-ttu-id="20066-180">除非處於執行階段，否則不會評估類型為 `dynamic` 的變數，如此即無須明確轉型。</span><span class="sxs-lookup"><span data-stu-id="20066-180">Variables that have type `dynamic` are not evaluated until run time, which eliminates the need for explicit casting.</span></span> <span data-ttu-id="20066-181">如需詳細資訊，請參閱[使用動態類型](../types/using-type-dynamic.md)。</span><span class="sxs-lookup"><span data-stu-id="20066-181">For more information, see [Using Type dynamic](../types/using-type-dynamic.md).</span></span>

     <span data-ttu-id="20066-182">在 C# 4 中，預設行為是內嵌型別資訊，而非使用 PIA。</span><span class="sxs-lookup"><span data-stu-id="20066-182">In C# 4, embedding type information instead of using PIAs is default behavior.</span></span> <span data-ttu-id="20066-183">因為使用該預設值，已簡化了數個先前的範例，因為明確轉型已非必要。</span><span class="sxs-lookup"><span data-stu-id="20066-183">Because of that default, several of the previous examples are simplified because explicit casting is not required.</span></span> <span data-ttu-id="20066-184">例如，`worksheet` 中的 `DisplayInExcel` 宣告，撰寫為 `Excel._Worksheet workSheet = excelApp.ActiveSheet`，而非 `Excel._Worksheet workSheet = (Excel.Worksheet)excelApp.ActiveSheet`。</span><span class="sxs-lookup"><span data-stu-id="20066-184">For example, the declaration of `worksheet` in `DisplayInExcel` is written as `Excel._Worksheet workSheet = excelApp.ActiveSheet` rather than `Excel._Worksheet workSheet = (Excel.Worksheet)excelApp.ActiveSheet`.</span></span> <span data-ttu-id="20066-185">如果沒有預設值，則相同方法中的 `AutoFit` 呼叫也需要明確轉型，因為 `ExcelApp.Columns[1]` 會傳回 `Object`，而 `AutoFit` 是 Excel 方法。</span><span class="sxs-lookup"><span data-stu-id="20066-185">The calls to `AutoFit` in the same method also would require explicit casting without the default, because `ExcelApp.Columns[1]` returns an `Object`, and `AutoFit` is an Excel  method.</span></span> <span data-ttu-id="20066-186">下列程式碼會顯示轉型。</span><span class="sxs-lookup"><span data-stu-id="20066-186">The following code shows the casting.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#14)]

2. <span data-ttu-id="20066-187">若要變更預設值，並使用 PIA 而非內嵌類型資訊，請展開方案總管中的 [參考] 節點，然後選取 **Microsoft.Office.Interop.Excel** 或 **Microsoft.Office.Interop.Word**。</span><span class="sxs-lookup"><span data-stu-id="20066-187">To change the default and use PIAs instead of embedding type information, expand the **References** node in **Solution Explorer** and then select **Microsoft.Office.Interop.Excel** or **Microsoft.Office.Interop.Word**.</span></span>

3. <span data-ttu-id="20066-188">如果看不到 [屬性] 視窗，請按 **F4** 鍵。</span><span class="sxs-lookup"><span data-stu-id="20066-188">If you cannot see the **Properties** window, press **F4**.</span></span>

4. <span data-ttu-id="20066-189">在屬性清單中尋找 [內嵌 Interop 類型]，並將其值變更為 **False**。</span><span class="sxs-lookup"><span data-stu-id="20066-189">Find **Embed Interop Types** in the list of properties, and change its value to **False**.</span></span> <span data-ttu-id="20066-190">同樣地，也可以在命令提示字元處使用 [/reference](../../language-reference/compiler-options/reference-compiler-option.md) 編譯器選項，而非 [/link](../../language-reference/compiler-options/link-compiler-option.md) 進行編譯。</span><span class="sxs-lookup"><span data-stu-id="20066-190">Equivalently, you can compile by using the [/reference](../../language-reference/compiler-options/reference-compiler-option.md) compiler option instead of [/link](../../language-reference/compiler-options/link-compiler-option.md) at a command prompt.</span></span>

## <a name="to-add-additional-formatting-to-the-table"></a><span data-ttu-id="20066-191">加入表格的其他格式</span><span class="sxs-lookup"><span data-stu-id="20066-191">To add additional formatting to the table</span></span>

1. <span data-ttu-id="20066-192">將 `AutoFit` 中對兩個 `DisplayInExcel` 的呼叫，取代為下列陳述式。</span><span class="sxs-lookup"><span data-stu-id="20066-192">Replace the two calls to `AutoFit` in `DisplayInExcel` with the following statement.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#15)]

     <span data-ttu-id="20066-193">這個方法 <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> 有七個值參數，全部都是選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="20066-193">The <xref:Microsoft.Office.Interop.Excel.Range.AutoFormat%2A> method has seven value parameters, all of which are optional.</span></span> <span data-ttu-id="20066-194">您可利用具名引數和選擇性引數，提供零個引數、數個引數或所有引數。</span><span class="sxs-lookup"><span data-stu-id="20066-194">Named and optional arguments enable you to provide arguments for none, some, or all of them.</span></span> <span data-ttu-id="20066-195">在前述陳述式中，只為其中一個參數 (`Format`) 提供引數。</span><span class="sxs-lookup"><span data-stu-id="20066-195">In the previous statement, an argument is supplied for only one of the parameters, `Format`.</span></span> <span data-ttu-id="20066-196">因為 `Format` 是參數清單中的第一個參數，所以無須提供參數名稱。</span><span class="sxs-lookup"><span data-stu-id="20066-196">Because `Format` is the first parameter in the parameter list, you do not have to provide the parameter name.</span></span> <span data-ttu-id="20066-197">但如果包含參數名稱，則可能較容易了解該陳述式，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="20066-197">However, the statement might be easier to understand if the parameter name is included, as is shown in the following code.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#16)]

2. <span data-ttu-id="20066-198">按 CTRL + F5 鍵查看結果。</span><span class="sxs-lookup"><span data-stu-id="20066-198">Press CTRL+F5 to see the result.</span></span> <span data-ttu-id="20066-199">其他格式會列在 <xref:Microsoft.Office.Interop.Excel.XlRangeAutoFormat> 列舉中。</span><span class="sxs-lookup"><span data-stu-id="20066-199">Other formats are listed in the <xref:Microsoft.Office.Interop.Excel.XlRangeAutoFormat> enumeration.</span></span>

3. <span data-ttu-id="20066-200">請比較步驟 1 中的陳述式與下列程式碼，這樣會顯示 C# 3.0 或舊版中所需的引數。</span><span class="sxs-lookup"><span data-stu-id="20066-200">Compare the statement in step 1 with the following code, which shows the arguments that are required in C# 3.0 and earlier versions.</span></span>

     [!code-csharp[csProgGuideOfficeHowTo#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/program.cs#17)]

## <a name="example"></a><span data-ttu-id="20066-201">範例</span><span class="sxs-lookup"><span data-stu-id="20066-201">Example</span></span>

<span data-ttu-id="20066-202">下列程式碼顯示完整範例。</span><span class="sxs-lookup"><span data-stu-id="20066-202">The following code shows the complete example.</span></span>

[!code-csharp[csProgGuideOfficeHowTo#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideofficehowto/cs/walkthrough.cs#18)]

## <a name="see-also"></a><span data-ttu-id="20066-203">另請參閱</span><span class="sxs-lookup"><span data-stu-id="20066-203">See also</span></span>

- <xref:System.Type.Missing?displayProperty=nameWithType>
- [<span data-ttu-id="20066-204">dynamic</span><span class="sxs-lookup"><span data-stu-id="20066-204">dynamic</span></span>](../../language-reference/keywords/dynamic.md)
- [<span data-ttu-id="20066-205">使用動態型別</span><span class="sxs-lookup"><span data-stu-id="20066-205">Using Type dynamic</span></span>](../types/using-type-dynamic.md)
- [<span data-ttu-id="20066-206">具名和選擇性引數</span><span class="sxs-lookup"><span data-stu-id="20066-206">Named and Optional Arguments</span></span>](../classes-and-structs/named-and-optional-arguments.md)
- [<span data-ttu-id="20066-207">如何：在 Office 程式設計中使用具名和選擇性引數</span><span class="sxs-lookup"><span data-stu-id="20066-207">How to: Use Named and Optional Arguments in Office Programming</span></span>](../classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
