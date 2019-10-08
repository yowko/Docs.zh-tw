---
title: HOW TO：在 Office 程式設計中使用具名引數和選用引數 - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- named and optional arguments [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
ms.assetid: 65b8a222-bcd8-454c-845f-84adff5a356f
ms.openlocfilehash: 90b60a6410ffbe7f9802b01bf3303b6e842a1424
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002797"
---
# <a name="how-to-use-named-and-optional-arguments-in-office-programming-c-programming-guide"></a><span data-ttu-id="1a63e-102">HOW TO：在 Office 程式設計中使用具名引數和選用引數 (C# 程式設計指南)</span><span class="sxs-lookup"><span data-stu-id="1a63e-102">How to: Use Named and Optional Arguments in Office Programming (C# Programming Guide)</span></span>

<span data-ttu-id="1a63e-103">C# 4 中引進的具名引數和選擇性引數，可加強 C# 程式設計的便利性、彈性和可讀性。</span><span class="sxs-lookup"><span data-stu-id="1a63e-103">Named arguments and optional arguments, introduced in C# 4, enhance convenience, flexibility, and readability in C# programming.</span></span> <span data-ttu-id="1a63e-104">此外，這些功能還可大幅加速對 COM 介面 (例如 Microsoft Office Automation API) 的存取。</span><span class="sxs-lookup"><span data-stu-id="1a63e-104">In addition, these features greatly facilitate access to COM interfaces such as the Microsoft Office automation APIs.</span></span>

<span data-ttu-id="1a63e-105">在下列範例中，[ConvertToTable](<xref:Microsoft.Office.Interop.Word.Range.ConvertToTable%2A>) 方法有十六個參數，這些參數代表資料表的特性，例如欄數和列數、格式、邊框、字型和顏色。</span><span class="sxs-lookup"><span data-stu-id="1a63e-105">In the following example, method [ConvertToTable](<xref:Microsoft.Office.Interop.Word.Range.ConvertToTable%2A>) has sixteen parameters that represent characteristics of a table, such as number of columns and rows, formatting, borders, fonts, and colors.</span></span> <span data-ttu-id="1a63e-106">所有十六個參數都是選擇性的，因為大多時候您不會想要為所有參數指定特定值。</span><span class="sxs-lookup"><span data-stu-id="1a63e-106">All sixteen parameters are optional, because most of the time you do not want to specify particular values for all of them.</span></span> <span data-ttu-id="1a63e-107">不過，如果不使用具名和選擇性引數，則必須為每個參數提供值或預留位置值。</span><span class="sxs-lookup"><span data-stu-id="1a63e-107">However, without named and optional arguments, a value or a placeholder value has to be provided for each parameter.</span></span> <span data-ttu-id="1a63e-108">如果使用具名和選擇性引數，就只會為專案所需的參數指定值。</span><span class="sxs-lookup"><span data-stu-id="1a63e-108">With named and optional arguments, you specify values only for the parameters that are required for your project.</span></span>

<span data-ttu-id="1a63e-109">您必須已在電腦上安裝 Microsoft Office Word，才能完成這些程序。</span><span class="sxs-lookup"><span data-stu-id="1a63e-109">You must have Microsoft Office Word installed on your computer to complete these procedures.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-new-console-application"></a><span data-ttu-id="1a63e-110">建立新的主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="1a63e-110">To create a new console application</span></span>

1. <span data-ttu-id="1a63e-111">啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="1a63e-111">Start Visual Studio.</span></span>

2. <span data-ttu-id="1a63e-112">在 [檔案] 功能表中，指向 [新增]，然後按一下 [專案]。</span><span class="sxs-lookup"><span data-stu-id="1a63e-112">On the **File** menu, point to **New**, and then click **Project**.</span></span>

3. <span data-ttu-id="1a63e-113">在 [範本類別] 窗格中，展開 [Visual C#]，然後按一下 [Windows]。</span><span class="sxs-lookup"><span data-stu-id="1a63e-113">In the **Templates Categories** pane, expand **Visual C#**, and then click **Windows**.</span></span>

4. <span data-ttu-id="1a63e-114">查看 [範本] 窗格頂端，確定 [.NET Framework 4] 出現在 [目標 Framework] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="1a63e-114">Look in the top of the **Templates** pane to make sure that **.NET Framework 4** appears in the **Target Framework** box.</span></span>

5. <span data-ttu-id="1a63e-115">按一下 [範本] 窗格中的 [主控台應用程式]。</span><span class="sxs-lookup"><span data-stu-id="1a63e-115">In the **Templates** pane, click **Console Application**.</span></span>

6. <span data-ttu-id="1a63e-116">在 [名稱] 欄位中鍵入專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="1a63e-116">Type a name for your project in the **Name** field.</span></span>

7. <span data-ttu-id="1a63e-117">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="1a63e-117">Click **OK**.</span></span>

     <span data-ttu-id="1a63e-118">新的專案隨即會出現在**方案總管**中。</span><span class="sxs-lookup"><span data-stu-id="1a63e-118">The new project appears in **Solution Explorer**.</span></span>

## <a name="to-add-a-reference"></a><span data-ttu-id="1a63e-119">若要加入參考</span><span class="sxs-lookup"><span data-stu-id="1a63e-119">To add a reference</span></span>

1. <span data-ttu-id="1a63e-120">在**方案總管**中，以滑鼠右鍵按一下您的專案名稱，然後按一下 [加入參考]。</span><span class="sxs-lookup"><span data-stu-id="1a63e-120">In **Solution Explorer**, right-click your project's name and then click **Add Reference**.</span></span> <span data-ttu-id="1a63e-121">[加入參考] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="1a63e-121">The **Add Reference** dialog box appears.</span></span>

2. <span data-ttu-id="1a63e-122">在 [.NET] 頁面上，選取 [元件名稱] 清單中的 [Microsoft.Office.Interop.Word]。</span><span class="sxs-lookup"><span data-stu-id="1a63e-122">On the **.NET** page, select **Microsoft.Office.Interop.Word** in the **Component Name** list.</span></span>

3. <span data-ttu-id="1a63e-123">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="1a63e-123">Click **OK**.</span></span>

## <a name="to-add-necessary-using-directives"></a><span data-ttu-id="1a63e-124">加入必要的 using 指示詞</span><span class="sxs-lookup"><span data-stu-id="1a63e-124">To add necessary using directives</span></span>

1. <span data-ttu-id="1a63e-125">在方案總管中，以滑鼠右鍵按一下 *Program.cs* 檔案，然後按一下 [檢視程式碼]。</span><span class="sxs-lookup"><span data-stu-id="1a63e-125">In **Solution Explorer**, right-click the *Program.cs* file and then click **View Code**.</span></span>

2. <span data-ttu-id="1a63e-126">將下列 `using` 指示詞新增至程式碼檔案的頂端：</span><span class="sxs-lookup"><span data-stu-id="1a63e-126">Add the following `using` directives to the top of the code file:</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#4)]

## <a name="to-display-text-in-a-word-document"></a><span data-ttu-id="1a63e-127">在 Word 文件中顯示文字</span><span class="sxs-lookup"><span data-stu-id="1a63e-127">To display text in a Word document</span></span>

1. <span data-ttu-id="1a63e-128">在*Program.cs*的 `Program` 類別中，新增下列方法來建立 word 應用程式和 word 檔。</span><span class="sxs-lookup"><span data-stu-id="1a63e-128">In the `Program` class in *Program.cs*, add the following method to create a Word application and a Word document.</span></span> <span data-ttu-id="1a63e-129">[Add](<xref:Microsoft.Office.Interop.Word.Documents.Add%2A>) 方法有四個選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="1a63e-129">The [Add](<xref:Microsoft.Office.Interop.Word.Documents.Add%2A>) method has four optional parameters.</span></span> <span data-ttu-id="1a63e-130">此範例會使用其預設值。</span><span class="sxs-lookup"><span data-stu-id="1a63e-130">This example uses their default values.</span></span> <span data-ttu-id="1a63e-131">因此，呼叫陳述式中不需要引數。</span><span class="sxs-lookup"><span data-stu-id="1a63e-131">Therefore, no arguments are necessary in the calling statement.</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#6)]

2. <span data-ttu-id="1a63e-132">在方法的結尾新增下列程式碼，以定義要在檔中顯示文字的位置，以及要顯示的文字：</span><span class="sxs-lookup"><span data-stu-id="1a63e-132">Add the following code at the end of the method to define where to display text in the document, and what text to display:</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#7)]

## <a name="to-run-the-application"></a><span data-ttu-id="1a63e-133">若要執行應用程式</span><span class="sxs-lookup"><span data-stu-id="1a63e-133">To run the application</span></span>

1. <span data-ttu-id="1a63e-134">將下列語句加入 Main：</span><span class="sxs-lookup"><span data-stu-id="1a63e-134">Add the following statement to Main:</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#8)]

2. <span data-ttu-id="1a63e-135">按<kbd>CTRL</kbd>+<kbd>F5</kbd>來執行專案。</span><span class="sxs-lookup"><span data-stu-id="1a63e-135">Press <kbd>CTRL</kbd>+<kbd>F5</kbd> to run the project.</span></span> <span data-ttu-id="1a63e-136">隨即會出現含有指定文字的 Word 文件。</span><span class="sxs-lookup"><span data-stu-id="1a63e-136">A Word document appears that contains the specified text.</span></span>

## <a name="to-change-the-text-to-a-table"></a><span data-ttu-id="1a63e-137">將文字變更為表格</span><span class="sxs-lookup"><span data-stu-id="1a63e-137">To change the text to a table</span></span>
  
1. <span data-ttu-id="1a63e-138">使用 `ConvertToTable` 方法將文字放在表格中。</span><span class="sxs-lookup"><span data-stu-id="1a63e-138">Use the `ConvertToTable` method to enclose the text in a table.</span></span> <span data-ttu-id="1a63e-139">此方法有十六個選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="1a63e-139">The method has sixteen optional parameters.</span></span> <span data-ttu-id="1a63e-140">IntelliSense 會以方括號括住選擇性參數，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="1a63e-140">IntelliSense encloses optional parameters in brackets, as shown in the following illustration.</span></span>

     ![ConvertToTable 方法的參數清單](./media/how-to-use-named-and-optional-arguments-in-office-programming/convert-table-parameters.png)

     <span data-ttu-id="1a63e-142">具名和選擇性引數可讓您只針對要變更的參數指定值。</span><span class="sxs-lookup"><span data-stu-id="1a63e-142">Named and optional arguments enable you to specify values for only the parameters that you want to change.</span></span> <span data-ttu-id="1a63e-143">將下列程式碼新增至 `DisplayInWord` 方法的結尾，以建立簡單的表格。</span><span class="sxs-lookup"><span data-stu-id="1a63e-143">Add the following code to the end of method `DisplayInWord` to create a simple table.</span></span> <span data-ttu-id="1a63e-144">此引數會指定以 `range` 內文字字串中的逗號來分隔表格的儲存格。</span><span class="sxs-lookup"><span data-stu-id="1a63e-144">The argument specifies that the commas in the text string in `range` separate the cells of the table.</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#9)]

     <span data-ttu-id="1a63e-145">在舊版中C#，對 `ConvertToTable` 的呼叫需要每個參數都有參考引數，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="1a63e-145">In earlier versions of C#, the call to `ConvertToTable` requires a reference argument for each parameter, as shown in the following code:</span></span>
  
     [!code-csharp[csProgGuideNamedAndOptional#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#14)]

2. <span data-ttu-id="1a63e-146">按<kbd>CTRL</kbd>+<kbd>F5</kbd>來執行專案。</span><span class="sxs-lookup"><span data-stu-id="1a63e-146">Press <kbd>CTRL</kbd>+<kbd>F5</kbd> to run the project.</span></span>

## <a name="to-experiment-with-other-parameters"></a><span data-ttu-id="1a63e-147">試驗其他參數</span><span class="sxs-lookup"><span data-stu-id="1a63e-147">To experiment with other parameters</span></span>

1. <span data-ttu-id="1a63e-148">若要變更資料表，使其具有一個資料行和三個數據列，請將 `DisplayInWord` 中的最後一行取代為下列語句，然後輸入<kbd>CTRL</kbd>+<kbd>F5</kbd>。</span><span class="sxs-lookup"><span data-stu-id="1a63e-148">To change the table so that it has one column and three rows, replace the last line in `DisplayInWord` with the following statement and then type <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span></span>  

     [!code-csharp[csProgGuideNamedAndOptional#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#10)]

2. <span data-ttu-id="1a63e-149">若要為數據表指定預先定義的格式，請將 `DisplayInWord` 中的最後一行取代為下列語句，然後輸入<kbd>CTRL</kbd>+<kbd>F5</kbd>。</span><span class="sxs-lookup"><span data-stu-id="1a63e-149">To specify a predefined format for the table, replace the last line in `DisplayInWord` with the following statement and then type <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span></span> <span data-ttu-id="1a63e-150">此格式可以是任何 [WdTableFormat](<xref:Microsoft.Office.Interop.Word.WdTableFormat>) 常數。</span><span class="sxs-lookup"><span data-stu-id="1a63e-150">The format can be any of the [WdTableFormat](<xref:Microsoft.Office.Interop.Word.WdTableFormat>) constants.</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#11)]

## <a name="example"></a><span data-ttu-id="1a63e-151">範例</span><span class="sxs-lookup"><span data-stu-id="1a63e-151">Example</span></span>

<span data-ttu-id="1a63e-152">下列程式碼包含完整的範例：</span><span class="sxs-lookup"><span data-stu-id="1a63e-152">The following code includes the full example:</span></span>

 [!code-csharp[csProgGuideNamedAndOptional#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#12)]

## <a name="see-also"></a><span data-ttu-id="1a63e-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a63e-153">See also</span></span>

- [<span data-ttu-id="1a63e-154">具名和選擇性引數</span><span class="sxs-lookup"><span data-stu-id="1a63e-154">Named and Optional Arguments</span></span>](./named-and-optional-arguments.md)
