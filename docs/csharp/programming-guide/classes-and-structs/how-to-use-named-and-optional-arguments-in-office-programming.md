---
title: '如何在 Office 程式設計中使用指名的和選擇性引數-c # 程式設計指南'
description: 瞭解如何使用具名引數和選擇性引數來加速存取 COM 介面，例如 Microsoft Office automation Api。
ms.date: 07/20/2015
helpviewer_keywords:
- named and optional arguments [C#], Office programming
- optional arguments [C#], Office programming
- named arguments [C#], Office programming
ms.topic: how-to
ms.custom: contperfq2
ms.assetid: 65b8a222-bcd8-454c-845f-84adff5a356f
ms.openlocfilehash: 9960ba2c39d58734a04cb7ca892ed321fd09822b
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2020
ms.locfileid: "95099044"
---
# <a name="how-to-use-named-and-optional-arguments-in-office-programming-c-programming-guide"></a><span data-ttu-id="3f034-103">如何在 Office 程式設計中使用指名的和選擇性引數 (c # 程式設計手冊) </span><span class="sxs-lookup"><span data-stu-id="3f034-103">How to use named and optional arguments in Office programming (C# Programming Guide)</span></span>

<span data-ttu-id="3f034-104">C# 4 中引進的具名引數和選擇性引數，可加強 C# 程式設計的便利性、彈性和可讀性。</span><span class="sxs-lookup"><span data-stu-id="3f034-104">Named arguments and optional arguments, introduced in C# 4, enhance convenience, flexibility, and readability in C# programming.</span></span> <span data-ttu-id="3f034-105">此外，這些功能還可大幅加速對 COM 介面 (例如 Microsoft Office Automation API) 的存取。</span><span class="sxs-lookup"><span data-stu-id="3f034-105">In addition, these features greatly facilitate access to COM interfaces such as the Microsoft Office automation APIs.</span></span>

<span data-ttu-id="3f034-106">在下列範例中，[ConvertToTable](<xref:Microsoft.Office.Interop.Word.Range.ConvertToTable%2A>) 方法有十六個參數，這些參數代表資料表的特性，例如欄數和列數、格式、邊框、字型和顏色。</span><span class="sxs-lookup"><span data-stu-id="3f034-106">In the following example, method [ConvertToTable](<xref:Microsoft.Office.Interop.Word.Range.ConvertToTable%2A>) has sixteen parameters that represent characteristics of a table, such as number of columns and rows, formatting, borders, fonts, and colors.</span></span> <span data-ttu-id="3f034-107">所有十六個參數都是選擇性的，因為大多時候您不會想要為所有參數指定特定值。</span><span class="sxs-lookup"><span data-stu-id="3f034-107">All sixteen parameters are optional, because most of the time you do not want to specify particular values for all of them.</span></span> <span data-ttu-id="3f034-108">不過，如果不使用具名和選擇性引數，則必須為每個參數提供值或預留位置值。</span><span class="sxs-lookup"><span data-stu-id="3f034-108">However, without named and optional arguments, a value or a placeholder value has to be provided for each parameter.</span></span> <span data-ttu-id="3f034-109">如果使用具名和選擇性引數，就只會為專案所需的參數指定值。</span><span class="sxs-lookup"><span data-stu-id="3f034-109">With named and optional arguments, you specify values only for the parameters that are required for your project.</span></span>

<span data-ttu-id="3f034-110">您必須已在電腦上安裝 Microsoft Office Word，才能完成這些程序。</span><span class="sxs-lookup"><span data-stu-id="3f034-110">You must have Microsoft Office Word installed on your computer to complete these procedures.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-new-console-application"></a><span data-ttu-id="3f034-111">建立新的主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="3f034-111">To create a new console application</span></span>

1. <span data-ttu-id="3f034-112">啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="3f034-112">Start Visual Studio.</span></span>

2. <span data-ttu-id="3f034-113">在 **[檔案]** 功能表上，指向 **[開新檔案]** ，然後按一下 **[專案]** 。</span><span class="sxs-lookup"><span data-stu-id="3f034-113">On the **File** menu, point to **New**, and then click **Project**.</span></span>

3. <span data-ttu-id="3f034-114">在 [範本類別] 窗格中，展開 [Visual C#]，然後按一下 [Windows]。</span><span class="sxs-lookup"><span data-stu-id="3f034-114">In the **Templates Categories** pane, expand **Visual C#**, and then click **Windows**.</span></span>

4. <span data-ttu-id="3f034-115">查看 [範本] 窗格頂端，確定 [.NET Framework 4] 出現在 [目標 Framework] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="3f034-115">Look in the top of the **Templates** pane to make sure that **.NET Framework 4** appears in the **Target Framework** box.</span></span>

5. <span data-ttu-id="3f034-116">按一下 [範本] 窗格中的 [主控台應用程式]。</span><span class="sxs-lookup"><span data-stu-id="3f034-116">In the **Templates** pane, click **Console Application**.</span></span>

6. <span data-ttu-id="3f034-117">在 [名稱] 欄位中鍵入專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="3f034-117">Type a name for your project in the **Name** field.</span></span>

7. <span data-ttu-id="3f034-118">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="3f034-118">Click **OK**.</span></span>

     <span data-ttu-id="3f034-119">新的專案隨即會出現在方案總管中。</span><span class="sxs-lookup"><span data-stu-id="3f034-119">The new project appears in **Solution Explorer**.</span></span>

## <a name="to-add-a-reference"></a><span data-ttu-id="3f034-120">若要加入參考</span><span class="sxs-lookup"><span data-stu-id="3f034-120">To add a reference</span></span>

1. <span data-ttu-id="3f034-121">在方案總管中，於專案名稱上按一下滑鼠右鍵，然後按一下 [新增參考]。</span><span class="sxs-lookup"><span data-stu-id="3f034-121">In **Solution Explorer**, right-click your project's name and then click **Add Reference**.</span></span> <span data-ttu-id="3f034-122">[新增參考] 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="3f034-122">The **Add Reference** dialog box appears.</span></span>

2. <span data-ttu-id="3f034-123">在 [.NET] 頁面上，選取 [元件名稱] 清單中的 [Microsoft.Office.Interop.Word]。</span><span class="sxs-lookup"><span data-stu-id="3f034-123">On the **.NET** page, select **Microsoft.Office.Interop.Word** in the **Component Name** list.</span></span>

3. <span data-ttu-id="3f034-124">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="3f034-124">Click **OK**.</span></span>

## <a name="to-add-necessary-using-directives"></a><span data-ttu-id="3f034-125">加入必要的 using 指示詞</span><span class="sxs-lookup"><span data-stu-id="3f034-125">To add necessary using directives</span></span>

1. <span data-ttu-id="3f034-126">在方案總管中，以滑鼠右鍵按一下 *Program.cs* 檔案，然後按一下 [檢視程式碼]。</span><span class="sxs-lookup"><span data-stu-id="3f034-126">In **Solution Explorer**, right-click the *Program.cs* file and then click **View Code**.</span></span>

2. <span data-ttu-id="3f034-127">將下列指示詞新增 `using` 至程式碼檔案的頂端：</span><span class="sxs-lookup"><span data-stu-id="3f034-127">Add the following `using` directives to the top of the code file:</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#4)]

## <a name="to-display-text-in-a-word-document"></a><span data-ttu-id="3f034-128">在 Word 文件中顯示文字</span><span class="sxs-lookup"><span data-stu-id="3f034-128">To display text in a Word document</span></span>

1. <span data-ttu-id="3f034-129">在 `Program` *Program.cs* 的類別中，新增下列方法來建立 word 應用程式和 word 檔。</span><span class="sxs-lookup"><span data-stu-id="3f034-129">In the `Program` class in *Program.cs*, add the following method to create a Word application and a Word document.</span></span> <span data-ttu-id="3f034-130">[Add](<xref:Microsoft.Office.Interop.Word.Documents.Add%2A>) 方法有四個選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="3f034-130">The [Add](<xref:Microsoft.Office.Interop.Word.Documents.Add%2A>) method has four optional parameters.</span></span> <span data-ttu-id="3f034-131">此範例會使用其預設值。</span><span class="sxs-lookup"><span data-stu-id="3f034-131">This example uses their default values.</span></span> <span data-ttu-id="3f034-132">因此，呼叫陳述式中不需要引數。</span><span class="sxs-lookup"><span data-stu-id="3f034-132">Therefore, no arguments are necessary in the calling statement.</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#6)]

2. <span data-ttu-id="3f034-133">在方法的結尾新增下列程式碼，以定義要在檔中顯示文字的位置，以及要顯示的文字：</span><span class="sxs-lookup"><span data-stu-id="3f034-133">Add the following code at the end of the method to define where to display text in the document, and what text to display:</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#7)]

## <a name="to-run-the-application"></a><span data-ttu-id="3f034-134">若要執行應用程式</span><span class="sxs-lookup"><span data-stu-id="3f034-134">To run the application</span></span>

1. <span data-ttu-id="3f034-135">將下列語句新增至 Main：</span><span class="sxs-lookup"><span data-stu-id="3f034-135">Add the following statement to Main:</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#8)]

2. <span data-ttu-id="3f034-136">按下<kbd>CTRL</kbd> + <kbd>F5</kbd>來執行專案。</span><span class="sxs-lookup"><span data-stu-id="3f034-136">Press <kbd>CTRL</kbd>+<kbd>F5</kbd> to run the project.</span></span> <span data-ttu-id="3f034-137">隨即會出現含有指定文字的 Word 文件。</span><span class="sxs-lookup"><span data-stu-id="3f034-137">A Word document appears that contains the specified text.</span></span>

## <a name="to-change-the-text-to-a-table"></a><span data-ttu-id="3f034-138">將文字變更為表格</span><span class="sxs-lookup"><span data-stu-id="3f034-138">To change the text to a table</span></span>
  
1. <span data-ttu-id="3f034-139">使用 `ConvertToTable` 方法將文字放在表格中。</span><span class="sxs-lookup"><span data-stu-id="3f034-139">Use the `ConvertToTable` method to enclose the text in a table.</span></span> <span data-ttu-id="3f034-140">此方法有十六個選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="3f034-140">The method has sixteen optional parameters.</span></span> <span data-ttu-id="3f034-141">IntelliSense 會以方括號括住選擇性參數，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="3f034-141">IntelliSense encloses optional parameters in brackets, as shown in the following illustration.</span></span>

     ![ConvertToTable 方法的參數清單](./media/how-to-use-named-and-optional-arguments-in-office-programming/convert-table-parameters.png)

     <span data-ttu-id="3f034-143">具名和選擇性引數可讓您只針對要變更的參數指定值。</span><span class="sxs-lookup"><span data-stu-id="3f034-143">Named and optional arguments enable you to specify values for only the parameters that you want to change.</span></span> <span data-ttu-id="3f034-144">將下列程式碼新增至 `DisplayInWord` 方法的結尾，以建立簡單的表格。</span><span class="sxs-lookup"><span data-stu-id="3f034-144">Add the following code to the end of method `DisplayInWord` to create a simple table.</span></span> <span data-ttu-id="3f034-145">此引數會指定以 `range` 內文字字串中的逗號來分隔表格的儲存格。</span><span class="sxs-lookup"><span data-stu-id="3f034-145">The argument specifies that the commas in the text string in `range` separate the cells of the table.</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#9)]

     <span data-ttu-id="3f034-146">在舊版的 c # 中，的呼叫 `ConvertToTable` 需要每個參數的參考引數，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="3f034-146">In earlier versions of C#, the call to `ConvertToTable` requires a reference argument for each parameter, as shown in the following code:</span></span>
  
     [!code-csharp[csProgGuideNamedAndOptional#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#14)]

2. <span data-ttu-id="3f034-147">按下<kbd>CTRL</kbd> + <kbd>F5</kbd>來執行專案。</span><span class="sxs-lookup"><span data-stu-id="3f034-147">Press <kbd>CTRL</kbd>+<kbd>F5</kbd> to run the project.</span></span>

## <a name="to-experiment-with-other-parameters"></a><span data-ttu-id="3f034-148">試驗其他參數</span><span class="sxs-lookup"><span data-stu-id="3f034-148">To experiment with other parameters</span></span>

1. <span data-ttu-id="3f034-149">若要變更資料表，使其具有一個資料行和三個數據列，請將中的最後一行取代 `DisplayInWord` 為下列語句，然後輸入<kbd>CTRL</kbd> + <kbd>F5</kbd>。</span><span class="sxs-lookup"><span data-stu-id="3f034-149">To change the table so that it has one column and three rows, replace the last line in `DisplayInWord` with the following statement and then type <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span></span>  

     [!code-csharp[csProgGuideNamedAndOptional#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#10)]

2. <span data-ttu-id="3f034-150">若要指定資料表的預先定義格式，請將中的最後一行取代為 `DisplayInWord` 下列語句，然後輸入<kbd>CTRL</kbd> + <kbd>F5</kbd>。</span><span class="sxs-lookup"><span data-stu-id="3f034-150">To specify a predefined format for the table, replace the last line in `DisplayInWord` with the following statement and then type <kbd>CTRL</kbd>+<kbd>F5</kbd>.</span></span> <span data-ttu-id="3f034-151">此格式可以是任何 [WdTableFormat](<xref:Microsoft.Office.Interop.Word.WdTableFormat>) 常數。</span><span class="sxs-lookup"><span data-stu-id="3f034-151">The format can be any of the [WdTableFormat](<xref:Microsoft.Office.Interop.Word.WdTableFormat>) constants.</span></span>

     [!code-csharp[csProgGuideNamedAndOptional#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#11)]

## <a name="example"></a><span data-ttu-id="3f034-152">範例</span><span class="sxs-lookup"><span data-stu-id="3f034-152">Example</span></span>

<span data-ttu-id="3f034-153">下列程式碼包含完整的範例：</span><span class="sxs-lookup"><span data-stu-id="3f034-153">The following code includes the full example:</span></span>

 [!code-csharp[csProgGuideNamedAndOptional#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidenamedandoptional/cs/wordprogram.cs#12)]

## <a name="see-also"></a><span data-ttu-id="3f034-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f034-154">See also</span></span>

- [<span data-ttu-id="3f034-155">具名和選擇性引數</span><span class="sxs-lookup"><span data-stu-id="3f034-155">Named and Optional Arguments</span></span>](./named-and-optional-arguments.md)
