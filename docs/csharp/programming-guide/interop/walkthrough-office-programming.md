---
title: 逐步解說：Office 程式設計 (C# 與 Visual Basic)
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Office, programming in Visual Basic and C#
- Office programming [C#]
- Office programming [Visual Basic]
ms.assetid: 519cff31-f80b-4f0e-a56b-26358d0f8c51
ms.openlocfilehash: a9b7a32cc3eb9d65b7c4a8e241eedca14cbf11bb
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2019
ms.locfileid: "67398144"
---
# <a name="walkthrough-office-programming-c-and-visual-basic"></a><span data-ttu-id="5e42f-102">逐步解說：Office 程式設計 (C# 與 Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5e42f-102">Walkthrough: Office Programming (C# and Visual Basic)</span></span>

<span data-ttu-id="5e42f-103">Visual Studio 在 C# 和 Visual Basic 中提供可改善 Microsoft Office 程式設計的功能。</span><span class="sxs-lookup"><span data-stu-id="5e42f-103">Visual Studio offers features in C# and Visual Basic that improve Microsoft Office programming.</span></span> <span data-ttu-id="5e42f-104">有助益的 C# 功能包括具名和選擇性引數以及類型為 `dynamic` 的傳回值。</span><span class="sxs-lookup"><span data-stu-id="5e42f-104">Helpful C# features include named and optional arguments and return values of type `dynamic`.</span></span> <span data-ttu-id="5e42f-105">在 COM 程式設計中，您可以省略 `ref` 關鍵字並存取索引的屬性。</span><span class="sxs-lookup"><span data-stu-id="5e42f-105">In COM programming, you can omit the `ref` keyword and gain access to indexed properties.</span></span> <span data-ttu-id="5e42f-106">Visual Basic 中的功能包含自動實作的屬性、Lambda 運算式中的陳述式，以及集合初始設定式。</span><span class="sxs-lookup"><span data-stu-id="5e42f-106">Features in Visual Basic include auto-implemented properties, statements in lambda expressions, and collection initializers.</span></span>

<span data-ttu-id="5e42f-107">這兩種語言都會啟用類型資訊的內嵌，以允許部署與 COM 元件互動的組件，而不需要將主要 Interop 組件 (PIA) 部署至使用者電腦。</span><span class="sxs-lookup"><span data-stu-id="5e42f-107">Both languages enable embedding of type information, which allows deployment of assemblies that interact with COM components without deploying primary interop assemblies (PIAs) to the user's computer.</span></span> <span data-ttu-id="5e42f-108">如需詳細資訊，請參閱[逐步解說：從 Managed 組件內嵌類型](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="5e42f-108">For more information, see [Walkthrough: Embedding Types from Managed Assemblies](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md).</span></span>

<span data-ttu-id="5e42f-109">這個逐步解說會示範 Office 程式設計內容中的這些功能，但其中大部分也適用於一般的程式設計。</span><span class="sxs-lookup"><span data-stu-id="5e42f-109">This walkthrough demonstrates these features in the context of Office programming, but many of these features are also useful in general programming.</span></span> <span data-ttu-id="5e42f-110">在這個逐步解說中，您會使用 Excel 增益集應用程式來建立 Excel 活頁簿。</span><span class="sxs-lookup"><span data-stu-id="5e42f-110">In the walkthrough, you use an Excel Add-in application to create an Excel workbook.</span></span> <span data-ttu-id="5e42f-111">接著，建立含有活頁簿連結的 Word 文件。</span><span class="sxs-lookup"><span data-stu-id="5e42f-111">Next, you create a Word document that contains a link to the workbook.</span></span> <span data-ttu-id="5e42f-112">最後，了解如何啟用和停用 PIA 相依性。</span><span class="sxs-lookup"><span data-stu-id="5e42f-112">Finally, you see how to enable and disable the PIA dependency.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5e42f-113">必要條件</span><span class="sxs-lookup"><span data-stu-id="5e42f-113">Prerequisites</span></span>

<span data-ttu-id="5e42f-114">電腦上必須安裝 Microsoft Office Excel 和 Microsoft Office Word 才能完成此逐步解說。</span><span class="sxs-lookup"><span data-stu-id="5e42f-114">You must have Microsoft Office Excel and Microsoft Office Word installed on your computer to complete this walkthrough.</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

### <a name="to-set-up-an-excel-add-in-application"></a><span data-ttu-id="5e42f-115">設定 Excel 增益集應用程式</span><span class="sxs-lookup"><span data-stu-id="5e42f-115">To set up an Excel Add-in application</span></span>

1. <span data-ttu-id="5e42f-116">啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="5e42f-116">Start Visual Studio.</span></span>

2. <span data-ttu-id="5e42f-117">在 [檔案]  功能表中，指向 [新增]  ，然後按一下 [專案]  。</span><span class="sxs-lookup"><span data-stu-id="5e42f-117">On the **File** menu, point to **New**, and then click **Project**.</span></span>

3. <span data-ttu-id="5e42f-118">在 [已安裝的範本]  窗格中，展開 **Visual Basic** 或 **Visual C#** ，並展開 **Office**，然後按一下 Office 產品的版本年份。</span><span class="sxs-lookup"><span data-stu-id="5e42f-118">In the **Installed Templates** pane, expand **Visual Basic** or **Visual C#**, expand **Office**, and then click the version year of the Office product.</span></span>

4. <span data-ttu-id="5e42f-119">在 [範本]  窗格中，按一下 [Excel \<版本 > 增益集]  。</span><span class="sxs-lookup"><span data-stu-id="5e42f-119">In the **Templates** pane, click **Excel \<version> Add-in**.</span></span>

5. <span data-ttu-id="5e42f-120">查看 [範本]  窗格頂端，確定 **.NET Framework 4** 或更新版本出現在 [目標 Framework]  方塊中。</span><span class="sxs-lookup"><span data-stu-id="5e42f-120">Look at the top of the **Templates** pane to make sure that **.NET Framework 4**, or a later version, appears in the **Target Framework** box.</span></span>

6. <span data-ttu-id="5e42f-121">視需要在 [名稱]  方塊中，輸入您專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="5e42f-121">Type a name for your project in the **Name** box, if you want to.</span></span>

7. <span data-ttu-id="5e42f-122">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="5e42f-122">Click **OK**.</span></span>

8. <span data-ttu-id="5e42f-123">新的專案隨即會出現在方案總管  中。</span><span class="sxs-lookup"><span data-stu-id="5e42f-123">The new project appears in **Solution Explorer**.</span></span>

### <a name="to-add-references"></a><span data-ttu-id="5e42f-124">加入參考</span><span class="sxs-lookup"><span data-stu-id="5e42f-124">To add references</span></span>

1. <span data-ttu-id="5e42f-125">在方案總管  中，於專案名稱上按一下滑鼠右鍵，然後按一下 [新增參考]  。</span><span class="sxs-lookup"><span data-stu-id="5e42f-125">In **Solution Explorer**, right-click your project's name and then click **Add Reference**.</span></span> <span data-ttu-id="5e42f-126">[加入參考]  對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="5e42f-126">The **Add Reference** dialog box appears.</span></span>

2. <span data-ttu-id="5e42f-127">在 [組件]  索引標籤上，選取 **Microsoft.Office.Interop.Excel** `<version>.0.0.0` 版 (如需 Office 產品版本號碼的金鑰，請參閱 [Microsoft 版本](https://en.wikipedia.org/wiki/Microsoft_Office#Versions))，並在 [元件名稱]  清單中，按住 CTRL 鍵，然後選取 **Microsoft.Office.Interop.Word** `version <version>.0.0.0`。</span><span class="sxs-lookup"><span data-stu-id="5e42f-127">On the **Assemblies** tab, select **Microsoft.Office.Interop.Excel**, version `<version>.0.0.0` (for a key to the Office product version numbers, see [Microsoft Versions](https://en.wikipedia.org/wiki/Microsoft_Office#Versions)), in the **Component Name** list, and then hold down the CTRL key and select **Microsoft.Office.Interop.Word**, `version <version>.0.0.0`.</span></span> <span data-ttu-id="5e42f-128">如果看不到組件，則可能需要確定組件已安裝及顯示 (請參閱[如何：安裝 Office 主要 Interop 組件](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies))。</span><span class="sxs-lookup"><span data-stu-id="5e42f-128">If you do not see the assemblies, you may need to ensure they are installed and displayed (see [How to: Install Office Primary Interop Assemblies](/visualstudio/vsto/how-to-install-office-primary-interop-assemblies)).</span></span>

3. <span data-ttu-id="5e42f-129">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="5e42f-129">Click **OK**.</span></span>

### <a name="to-add-necessary-imports-statements-or-using-directives"></a><span data-ttu-id="5e42f-130">加入必要的 Imports 陳述式或 using 指示詞</span><span class="sxs-lookup"><span data-stu-id="5e42f-130">To add necessary Imports statements or using directives</span></span>

1. <span data-ttu-id="5e42f-131">在方案總管  中，以滑鼠右鍵按一下 **ThisAddIn.vb** 或 **ThisAddIn.cs** 檔案，然後按一下 [檢視程式碼]  。</span><span class="sxs-lookup"><span data-stu-id="5e42f-131">In **Solution Explorer**, right-click the **ThisAddIn.vb** or **ThisAddIn.cs** file and then click **View Code**.</span></span>

2. <span data-ttu-id="5e42f-132">將下列 `Imports` 陳述式 (Visual Basic) 或 `using` 指示詞 (C#) 加入還沒有這兩者的程式碼檔案頂端。</span><span class="sxs-lookup"><span data-stu-id="5e42f-132">Add the following `Imports` statements (Visual Basic) or `using` directives (C#) to the top of the code file if they are not already present.</span></span>

     [!code-csharp[csOfficeWalkthrough#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#1)]

     [!code-vb[csOfficeWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#1)]

### <a name="to-create-a-list-of-bank-accounts"></a><span data-ttu-id="5e42f-133">建立銀行帳戶清單</span><span class="sxs-lookup"><span data-stu-id="5e42f-133">To create a list of bank accounts</span></span>

1. <span data-ttu-id="5e42f-134">在方案總管  中，以滑鼠右鍵按一下您的專案名稱，再按一下 [新增]  ，然後按一下 [類別]  。</span><span class="sxs-lookup"><span data-stu-id="5e42f-134">In **Solution Explorer**, right-click your project's name, click **Add**, and then click **Class**.</span></span> <span data-ttu-id="5e42f-135">如果您使用 Visual Basic，請將類別命名為 Account.vb；如果您使用 C#，則請將類別命名為 Account.cs。</span><span class="sxs-lookup"><span data-stu-id="5e42f-135">Name the class Account.vb if you are using Visual Basic or Account.cs if you are using C#.</span></span> <span data-ttu-id="5e42f-136">按一下 [加入]  。</span><span class="sxs-lookup"><span data-stu-id="5e42f-136">Click **Add**.</span></span>

2. <span data-ttu-id="5e42f-137">將 `Account` 類別的定義取代為下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="5e42f-137">Replace the definition of the `Account` class with the following code.</span></span> <span data-ttu-id="5e42f-138">類別定義使用「自動實作屬性」  。</span><span class="sxs-lookup"><span data-stu-id="5e42f-138">The class definitions use *auto-implemented properties*.</span></span> <span data-ttu-id="5e42f-139">如需詳細資訊，請參閱[自動實作的屬性](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="5e42f-139">For more information, see [Auto-Implemented Properties](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>

     [!code-csharp[csOfficeWalkthrough#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/account.cs#2)]

     [!code-vb[csOfficeWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/account.vb#2)]

3. <span data-ttu-id="5e42f-140">若要建立含有兩個帳戶的 `bankAccounts` 清單，請將下列程式碼新增至 *ThisAddIn.vb* 或 *ThisAddIn.cs* 中的 `ThisAddIn_Startup` 方法。</span><span class="sxs-lookup"><span data-stu-id="5e42f-140">To create a `bankAccounts` list that contains two accounts, add the following code to the `ThisAddIn_Startup` method in *ThisAddIn.vb* or *ThisAddIn.cs*.</span></span> <span data-ttu-id="5e42f-141">清單宣告使用「集合初始設定式」  。</span><span class="sxs-lookup"><span data-stu-id="5e42f-141">The list declarations use *collection initializers*.</span></span> <span data-ttu-id="5e42f-142">如需詳細資訊，請參閱[集合初始設定式](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)。</span><span class="sxs-lookup"><span data-stu-id="5e42f-142">For more information, see [Collection Initializers](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md).</span></span>

     [!code-csharp[csOfficeWalkthrough#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#3)]

     [!code-vb[csOfficeWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#3)]

### <a name="to-export-data-to-excel"></a><span data-ttu-id="5e42f-143">將資料匯出至 Excel</span><span class="sxs-lookup"><span data-stu-id="5e42f-143">To export data to Excel</span></span>

1. <span data-ttu-id="5e42f-144">在相同的檔案中，將下列方法加入 `ThisAddIn` 類別。</span><span class="sxs-lookup"><span data-stu-id="5e42f-144">In the same file, add the following method to the `ThisAddIn` class.</span></span> <span data-ttu-id="5e42f-145">這個方法會設定 Excel 活頁簿，並將資料匯出到 Excel 活頁簿。</span><span class="sxs-lookup"><span data-stu-id="5e42f-145">The method sets up an Excel workbook and exports data to it.</span></span>

     [!code-csharp[csOfficeWalkthrough#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#4)]

     [!code-vb[csOfficeWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#4)]

     <span data-ttu-id="5e42f-146">在這個方法中，使用了兩個新的 C# 功能。</span><span class="sxs-lookup"><span data-stu-id="5e42f-146">Two new C# features are used in this method.</span></span> <span data-ttu-id="5e42f-147">這兩個功能已存在於 Visual Basic 中。</span><span class="sxs-lookup"><span data-stu-id="5e42f-147">Both of these features already exist in Visual Basic.</span></span>

    - <span data-ttu-id="5e42f-148">[Add](<xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A>) 方法提供用來指定特定範本的選擇性參數  。</span><span class="sxs-lookup"><span data-stu-id="5e42f-148">Method [Add](<xref:Microsoft.Office.Interop.Excel.Workbooks.Add%2A>) has an *optional parameter* for specifying a particular template.</span></span> <span data-ttu-id="5e42f-149">如果您想要使用參數的預設值，則可利用選擇性參數 (C# 4 中的新功能) 省略該參數的引數。</span><span class="sxs-lookup"><span data-stu-id="5e42f-149">Optional parameters, new in C# 4, enable you to omit the argument for that parameter if you want to use the parameter's default value.</span></span> <span data-ttu-id="5e42f-150">因為上一個範例中未傳送引數，所以 `Add` 會使用預設範本並建立新的活頁簿。</span><span class="sxs-lookup"><span data-stu-id="5e42f-150">Because no argument is sent in the previous example, `Add` uses the default template and creates a new workbook.</span></span> <span data-ttu-id="5e42f-151">舊版 C# 中對等的陳述式需要有預留位置引數：`excelApp.Workbooks.Add(Type.Missing)`。</span><span class="sxs-lookup"><span data-stu-id="5e42f-151">The equivalent statement in earlier versions of C# requires a placeholder argument: `excelApp.Workbooks.Add(Type.Missing)`.</span></span>

         <span data-ttu-id="5e42f-152">如需詳細資訊，請參閱[具名和選擇性引數](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)。</span><span class="sxs-lookup"><span data-stu-id="5e42f-152">For more information, see [Named and Optional Arguments](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md).</span></span>

    - <span data-ttu-id="5e42f-153">[Range](<xref:Microsoft.Office.Interop.Excel.Range>) 物件的 `Range` 和 `Offset` 屬性會使用「編製過索引的屬性」  功能。</span><span class="sxs-lookup"><span data-stu-id="5e42f-153">The `Range` and `Offset` properties of the [Range](<xref:Microsoft.Office.Interop.Excel.Range>) object use the *indexed properties* feature.</span></span> <span data-ttu-id="5e42f-154">您可利用這項功能使用下列一般 C# 語法，來使用 COM 類型的這些屬性。</span><span class="sxs-lookup"><span data-stu-id="5e42f-154">This feature enables you to consume these properties from COM types by using the following typical C# syntax.</span></span> <span data-ttu-id="5e42f-155">您可利用編製過索引的屬性，使用 `Value` 物件的 `Range` 屬性，而不需要使用 `Value2` 屬性。</span><span class="sxs-lookup"><span data-stu-id="5e42f-155">Indexed properties also enable you to use the `Value` property of the `Range` object, eliminating the need to use the `Value2` property.</span></span> <span data-ttu-id="5e42f-156">`Value` 屬性編製過索引，但您可選擇是否要編製索引。</span><span class="sxs-lookup"><span data-stu-id="5e42f-156">The `Value` property is indexed, but the index is optional.</span></span> <span data-ttu-id="5e42f-157">在下列範例中，同時使用了選擇性引數與編製過索引的屬性。</span><span class="sxs-lookup"><span data-stu-id="5e42f-157">Optional arguments and indexed properties work together in the following example.</span></span>

         [!code-csharp[csOfficeWalkthrough#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#5)]

         <span data-ttu-id="5e42f-158">在舊版語言中，需要下列特殊語法。</span><span class="sxs-lookup"><span data-stu-id="5e42f-158">In earlier versions of the language, the following special syntax is required.</span></span>

         [!code-csharp[csOfficeWalkthrough#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#6)]

         <span data-ttu-id="5e42f-159">您無法建立自己本身的編製過索引的屬性。</span><span class="sxs-lookup"><span data-stu-id="5e42f-159">You cannot create indexed properties of your own.</span></span> <span data-ttu-id="5e42f-160">這個功能僅支援使用現有已編製過索引的屬性。</span><span class="sxs-lookup"><span data-stu-id="5e42f-160">The feature only supports consumption of existing indexed properties.</span></span>

         <span data-ttu-id="5e42f-161">如需詳細資訊，請參閱[如何：在 COM Interop 程式設計中使用已編製索引的屬性](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md)。</span><span class="sxs-lookup"><span data-stu-id="5e42f-161">For more information, see [How to: Use Indexed Properties in COM Interop Programming](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md).</span></span>

2. <span data-ttu-id="5e42f-162">在 `DisplayInExcel` 結尾加入下列程式碼，以調整資料行寬度以容納內容。</span><span class="sxs-lookup"><span data-stu-id="5e42f-162">Add the following code at the end of `DisplayInExcel` to adjust the column widths to fit the content.</span></span>

     [!code-csharp[csOfficeWalkthrough#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#7)]

     [!code-vb[csOfficeWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#7)]

     <span data-ttu-id="5e42f-163">這些新增內容可示範 C# 中的另一項功能：將 COM 主機 (例如 Office) 傳回的 `Object` 值，視為具有 [dynamic](../../../csharp/language-reference/keywords/dynamic.md) 類型。</span><span class="sxs-lookup"><span data-stu-id="5e42f-163">These additions demonstrate another feature in C#: treating `Object` values returned from COM hosts such as Office as if they have type [dynamic](../../../csharp/language-reference/keywords/dynamic.md).</span></span> <span data-ttu-id="5e42f-164">如果已將 [內嵌 Interop 類型]  設定為其預設值 `True`，則會自動發生這種情況；同樣地，當 [/link](../../../csharp/language-reference/compiler-options/link-compiler-option.md) 編譯器選項參考了組件時也會如此。</span><span class="sxs-lookup"><span data-stu-id="5e42f-164">This happens automatically when **Embed Interop Types** is set to its default value, `True`, or, equivalently, when the assembly is referenced by the [/link](../../../csharp/language-reference/compiler-options/link-compiler-option.md) compiler option.</span></span> <span data-ttu-id="5e42f-165">`dynamic` 類型可以進行晚期繫結 (Visual Basic 中已有這個功能)，並避免在 C# 3.0 和語言舊版本中需要明確轉型。</span><span class="sxs-lookup"><span data-stu-id="5e42f-165">Type `dynamic` allows late binding, already available in Visual Basic, and avoids the explicit casting required in C# 3.0 and earlier versions of the language.</span></span>

     <span data-ttu-id="5e42f-166">例如，`excelApp.Columns[1]` 會傳回 `Object`；而 `AutoFit` 則為 Excel [Range](<xref:Microsoft.Office.Interop.Excel.Range>) 方法。</span><span class="sxs-lookup"><span data-stu-id="5e42f-166">For example, `excelApp.Columns[1]` returns an `Object`, and `AutoFit` is an Excel  [Range](<xref:Microsoft.Office.Interop.Excel.Range>) method.</span></span> <span data-ttu-id="5e42f-167">如果沒有 `dynamic`，則在呼叫 `excelApp.Columns[1]` 方法之前，必須將 `Range` 所傳回的物件，轉型為 `AutoFit` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="5e42f-167">Without `dynamic`, you must cast the object returned by `excelApp.Columns[1]` as an instance of `Range` before calling method `AutoFit`.</span></span>

     [!code-csharp[csOfficeWalkthrough#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#8)]

     <span data-ttu-id="5e42f-168">如需內嵌 Interop 類型的詳細資訊，請參閱本主題稍後的＜尋找 PIA 參考＞和＜還原 PIA 相依性＞程序。</span><span class="sxs-lookup"><span data-stu-id="5e42f-168">For more information about embedding interop types, see procedures "To find the PIA reference" and "To restore the PIA dependency" later in this topic.</span></span> <span data-ttu-id="5e42f-169">如需 `dynamic` 的詳細資訊，請參閱 [dynamic](../../../csharp/language-reference/keywords/dynamic.md) 或[使用動態類型](../../../csharp/programming-guide/types/using-type-dynamic.md)。</span><span class="sxs-lookup"><span data-stu-id="5e42f-169">For more information about `dynamic`, see [dynamic](../../../csharp/language-reference/keywords/dynamic.md) or [Using Type dynamic](../../../csharp/programming-guide/types/using-type-dynamic.md).</span></span>

### <a name="to-invoke-displayinexcel"></a><span data-ttu-id="5e42f-170">叫用 DisplayInExcel</span><span class="sxs-lookup"><span data-stu-id="5e42f-170">To invoke DisplayInExcel</span></span>

1. <span data-ttu-id="5e42f-171">在 `ThisAddIn_StartUp` 方法的結尾，加入下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="5e42f-171">Add the following code at the end of the `ThisAddIn_StartUp` method.</span></span> <span data-ttu-id="5e42f-172">`DisplayInExcel` 呼叫包含兩個引數。</span><span class="sxs-lookup"><span data-stu-id="5e42f-172">The call to `DisplayInExcel` contains two arguments.</span></span> <span data-ttu-id="5e42f-173">第一個引數是要處理的帳戶清單名稱。</span><span class="sxs-lookup"><span data-stu-id="5e42f-173">The first argument is the name of the list of accounts to be processed.</span></span> <span data-ttu-id="5e42f-174">第二個引數則是多行的 Lambda 運算式，定義如何處理資料。</span><span class="sxs-lookup"><span data-stu-id="5e42f-174">The second argument is a multiline lambda expression that defines how the data is to be processed.</span></span> <span data-ttu-id="5e42f-175">每個帳戶的 `ID` 和 `balance` 值都會顯示在相鄰的儲存格中，而且如果餘額小於零，則會以紅色顯示資料列。</span><span class="sxs-lookup"><span data-stu-id="5e42f-175">The `ID` and `balance` values for each account are displayed in adjacent cells, and the row is displayed in red if the balance is less than zero.</span></span> <span data-ttu-id="5e42f-176">如需詳細資訊，請參閱 [Lambda 運算式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="5e42f-176">For more information, see [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>

     [!code-csharp[csOfficeWalkthrough#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#9)]

     [!code-vb[csOfficeWalkthrough#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#9)]

2. <span data-ttu-id="5e42f-177">若要執行程式，請按 F5 鍵。</span><span class="sxs-lookup"><span data-stu-id="5e42f-177">To run the program, press F5.</span></span> <span data-ttu-id="5e42f-178">隨即會出現內含帳戶資料的 Excel 工作表。</span><span class="sxs-lookup"><span data-stu-id="5e42f-178">An Excel worksheet appears that contains the data from the accounts.</span></span>

### <a name="to-add-a-word-document"></a><span data-ttu-id="5e42f-179">加入 Word 文件</span><span class="sxs-lookup"><span data-stu-id="5e42f-179">To add a Word document</span></span>

1. <span data-ttu-id="5e42f-180">在 `ThisAddIn_StartUp` 方法的結尾加入下列程式碼，可以建立內含 Excel 活頁簿連結的 Word 文件。</span><span class="sxs-lookup"><span data-stu-id="5e42f-180">Add the following code at the end of the `ThisAddIn_StartUp` method to create a Word document that contains a link to the Excel workbook.</span></span>

     [!code-csharp[csOfficeWalkthrough#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csofficewalkthrough/cs/thisaddin.cs#10)]

     [!code-vb[csOfficeWalkthrough#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csofficewalkthrough/vb/thisaddin.vb#10)]

     <span data-ttu-id="5e42f-181">這個程式碼將會示範 C# 中的數個新功能：省略 COM 程式設計中 `ref` 關鍵字、具名引數和選擇性引數的能力。</span><span class="sxs-lookup"><span data-stu-id="5e42f-181">This code demonstrates several of the new features in C#: the ability to omit the `ref` keyword in COM programming, named arguments, and optional arguments.</span></span> <span data-ttu-id="5e42f-182">Visual Basic 中已有這些功能。</span><span class="sxs-lookup"><span data-stu-id="5e42f-182">These features already exist in Visual Basic.</span></span> <span data-ttu-id="5e42f-183">[PasteSpecial](<xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A>) 方法有七個參數，全部都定義為選擇性參考參數。</span><span class="sxs-lookup"><span data-stu-id="5e42f-183">The [PasteSpecial](<xref:Microsoft.Office.Interop.Word.Selection.PasteSpecial%2A>) method has seven parameters, all of which are defined as optional reference parameters.</span></span> <span data-ttu-id="5e42f-184">您可利用具名引數和選擇性引數，指定想要依名稱存取的參數，以及將引數只傳送給那些參數。</span><span class="sxs-lookup"><span data-stu-id="5e42f-184">Named and optional arguments enable you to designate the parameters you want to access by name and to send arguments to only those parameters.</span></span> <span data-ttu-id="5e42f-185">在這個範例中會傳送引數，表示應建立剪貼簿上的活頁簿連結 (參數 `Link`)，且連結會以圖示形式顯示在 Word 文件中 (參數 `DisplayAsIcon`)。</span><span class="sxs-lookup"><span data-stu-id="5e42f-185">In this example, arguments are sent to indicate that a link to the workbook on the Clipboard should be created (parameter `Link`) and that the link is to be displayed in the Word document as an icon (parameter `DisplayAsIcon`).</span></span> <span data-ttu-id="5e42f-186">在 Visual C# 中也可省略這些引數的 `ref` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="5e42f-186">Visual C# also enables you to omit the `ref` keyword for these arguments.</span></span>

### <a name="to-run-the-application"></a><span data-ttu-id="5e42f-187">若要執行應用程式</span><span class="sxs-lookup"><span data-stu-id="5e42f-187">To run the application</span></span>

1. <span data-ttu-id="5e42f-188">按 F5 執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="5e42f-188">Press F5 to run the application.</span></span> <span data-ttu-id="5e42f-189">隨即會啟動 Excel，並會顯示含有 `bankAccounts` 中兩個帳戶資訊的資料表。</span><span class="sxs-lookup"><span data-stu-id="5e42f-189">Excel starts and displays a table that contains the information from the two accounts in `bankAccounts`.</span></span> <span data-ttu-id="5e42f-190">然後，會出現包含 Excel 資料表連結的 Word 文件。</span><span class="sxs-lookup"><span data-stu-id="5e42f-190">Then a Word document appears that contains a link to the Excel table.</span></span>

### <a name="to-clean-up-the-completed-project"></a><span data-ttu-id="5e42f-191">清除已完成的專案</span><span class="sxs-lookup"><span data-stu-id="5e42f-191">To clean up the completed project</span></span>

1. <span data-ttu-id="5e42f-192">在 Visual Studio 中，按一下 [建置]  功能表上的 [清除方案]  。</span><span class="sxs-lookup"><span data-stu-id="5e42f-192">In Visual Studio, click **Clean Solution** on the **Build** menu.</span></span> <span data-ttu-id="5e42f-193">否則，每次在電腦上開啟 Excel 時，都會執行增益集。</span><span class="sxs-lookup"><span data-stu-id="5e42f-193">Otherwise, the add-in will run every time that you open Excel on your computer.</span></span>

### <a name="to-find-the-pia-reference"></a><span data-ttu-id="5e42f-194">尋找 PIA 參考</span><span class="sxs-lookup"><span data-stu-id="5e42f-194">To find the PIA reference</span></span>

1. <span data-ttu-id="5e42f-195">重新執行應用程式，但不要按一下 [清除方案]  。</span><span class="sxs-lookup"><span data-stu-id="5e42f-195">Run the application again, but do not click **Clean Solution**.</span></span>

2. <span data-ttu-id="5e42f-196">選取 [開始]  。</span><span class="sxs-lookup"><span data-stu-id="5e42f-196">Select the **Start**.</span></span> <span data-ttu-id="5e42f-197">找出 **Microsoft Visual Studio\<版本>** ，開啟開發人員命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="5e42f-197">Locate **Microsoft Visual Studio \<version>** and open a developer command prompt.</span></span>

3. <span data-ttu-id="5e42f-198">在 [Visual Studio 開發人員命令提示字元] 視窗中鍵入 `ildasm`，然後按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="5e42f-198">Type `ildasm` in the Developer Command Prompt for Visual Studio window, and then press ENTER.</span></span> <span data-ttu-id="5e42f-199">隨即會出現 IL DASM 視窗。</span><span class="sxs-lookup"><span data-stu-id="5e42f-199">The IL DASM window appears.</span></span>

4. <span data-ttu-id="5e42f-200">在 IL DASM 視窗的 [檔案]  功能表上，選取 [檔案]   > [開啟]  。</span><span class="sxs-lookup"><span data-stu-id="5e42f-200">On the **File** menu in the IL DASM window, select **File** > **Open**.</span></span> <span data-ttu-id="5e42f-201">按兩下 [Visual Studio \<版本>]  ，然後按兩下 [專案]  。</span><span class="sxs-lookup"><span data-stu-id="5e42f-201">Double-click **Visual Studio \<version>**, and then double-click **Projects**.</span></span> <span data-ttu-id="5e42f-202">開啟您專案的資料夾，並查看 bin/Debug 資料夾中的 <您的專案名稱>  .dll。</span><span class="sxs-lookup"><span data-stu-id="5e42f-202">Open the folder for your project, and look in the bin/Debug folder for *your project name*.dll.</span></span> <span data-ttu-id="5e42f-203">按兩下 <您的專案名稱>  .dll。</span><span class="sxs-lookup"><span data-stu-id="5e42f-203">Double-click *your project name*.dll.</span></span> <span data-ttu-id="5e42f-204">新的視窗除了顯示會其他模組和組件的參考之外，還會顯示您專案的屬性。</span><span class="sxs-lookup"><span data-stu-id="5e42f-204">A new window displays your project's attributes, in addition to references to other modules and assemblies.</span></span> <span data-ttu-id="5e42f-205">請注意，組件中會包含命名空間 `Microsoft.Office.Interop.Excel` 和 `Microsoft.Office.Interop.Word`。</span><span class="sxs-lookup"><span data-stu-id="5e42f-205">Note that namespaces `Microsoft.Office.Interop.Excel` and `Microsoft.Office.Interop.Word` are included in the assembly.</span></span> <span data-ttu-id="5e42f-206">在 Visual Studio 中，編譯器預設會將您所需要的類型從參考的 PIA 匯入組件。</span><span class="sxs-lookup"><span data-stu-id="5e42f-206">By default in Visual Studio, the compiler imports the types you need from a referenced PIA into your assembly.</span></span>

     <span data-ttu-id="5e42f-207">如需詳細資訊，請參閱[如何：檢視組件內容](../../../framework/app-domains/how-to-view-assembly-contents.md)。</span><span class="sxs-lookup"><span data-stu-id="5e42f-207">For more information, see [How to: View Assembly Contents](../../../framework/app-domains/how-to-view-assembly-contents.md).</span></span>

5. <span data-ttu-id="5e42f-208">按兩下**資訊清單**圖示。</span><span class="sxs-lookup"><span data-stu-id="5e42f-208">Double-click the **MANIFEST** icon.</span></span> <span data-ttu-id="5e42f-209">隨即會出現一個視窗，內含專案所參考之項目的組件清單。</span><span class="sxs-lookup"><span data-stu-id="5e42f-209">A window appears that contains a list of assemblies that contain items referenced by the project.</span></span> <span data-ttu-id="5e42f-210">`Microsoft.Office.Interop.Excel` 和 `Microsoft.Office.Interop.Word` 未包含在清單中。</span><span class="sxs-lookup"><span data-stu-id="5e42f-210">`Microsoft.Office.Interop.Excel` and `Microsoft.Office.Interop.Word` are not included in the list.</span></span> <span data-ttu-id="5e42f-211">因為您專案所需的類型已匯入組件中，所以不需要 PIA 參考。</span><span class="sxs-lookup"><span data-stu-id="5e42f-211">Because the types your project needs have been imported into your assembly, references to a PIA are not required.</span></span> <span data-ttu-id="5e42f-212">這會讓部署更為容易。</span><span class="sxs-lookup"><span data-stu-id="5e42f-212">This makes deployment easier.</span></span> <span data-ttu-id="5e42f-213">PIA 不需要存在於使用者的電腦上，而且因為應用程式不需要部署特定版本的 PIA，所以應用程式可以設計成與多個版本的 Office 搭配使用，但前提是所有版本都有必要的 API。</span><span class="sxs-lookup"><span data-stu-id="5e42f-213">The PIAs do not have to be present on the user's computer, and because an application does not require deployment of a specific version of a PIA, applications can be designed to work with multiple versions of Office, provided that the necessary APIs exist in all versions.</span></span>

     <span data-ttu-id="5e42f-214">因為不再需要部署 PIA，所以您可以在使用多個版本 Office (包括舊版本) 的進階情況下，建立應用程式。</span><span class="sxs-lookup"><span data-stu-id="5e42f-214">Because deployment of PIAs is no longer necessary, you can create an application in advanced scenarios that works with multiple versions of Office, including earlier versions.</span></span> <span data-ttu-id="5e42f-215">不過，這只適用於程式碼未使用供任何 API 時 (目前所用 Office 版本中不提供)。</span><span class="sxs-lookup"><span data-stu-id="5e42f-215">However, this works only if your code does not use any APIs that are not available in the version of Office you are working with.</span></span> <span data-ttu-id="5e42f-216">您不一定清楚舊版本中是否有特定 API，也因為此，不建議使用舊版 Office。</span><span class="sxs-lookup"><span data-stu-id="5e42f-216">It is not always clear whether a particular API was available in an earlier version, and for that reason working with earlier versions of Office is not recommended.</span></span>

    > [!NOTE]
    > <span data-ttu-id="5e42f-217">在 Office 2003 之前，Office 未發行 PIA。</span><span class="sxs-lookup"><span data-stu-id="5e42f-217">Office did not publish PIAs before Office 2003.</span></span> <span data-ttu-id="5e42f-218">因此，產生 Office 2002 或舊版 Interop 組件唯一的方法，是匯入 COM 參考。</span><span class="sxs-lookup"><span data-stu-id="5e42f-218">Therefore, the only way to generate an interop assembly for Office 2002 or earlier versions is by importing the COM reference.</span></span>

6. <span data-ttu-id="5e42f-219">關閉資訊清單視窗和組件視窗。</span><span class="sxs-lookup"><span data-stu-id="5e42f-219">Close the manifest window and the assembly window.</span></span>

### <a name="to-restore-the-pia-dependency"></a><span data-ttu-id="5e42f-220">還原 PIA 相依性</span><span class="sxs-lookup"><span data-stu-id="5e42f-220">To restore the PIA dependency</span></span>

1. <span data-ttu-id="5e42f-221">在方案總管  中，按一下 [顯示所有檔案]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="5e42f-221">In **Solution Explorer**, click the **Show All Files** button.</span></span> <span data-ttu-id="5e42f-222">展開 [參考]  資料夾，然後選取 **Microsoft.Office.Interop.Excel**。</span><span class="sxs-lookup"><span data-stu-id="5e42f-222">Expand the **References** folder and select **Microsoft.Office.Interop.Excel**.</span></span> <span data-ttu-id="5e42f-223">按 F4 顯示 [屬性]  視窗。</span><span class="sxs-lookup"><span data-stu-id="5e42f-223">Press F4 to display the **Properties** window.</span></span>

2. <span data-ttu-id="5e42f-224">在 [屬性]  視窗中，將 [內嵌 Interop 類型]  屬性從 [True]  變更為 [False]  。</span><span class="sxs-lookup"><span data-stu-id="5e42f-224">In the **Properties** window, change the **Embed Interop Types** property from **True** to **False**.</span></span>

3. <span data-ttu-id="5e42f-225">為 `Microsoft.Office.Interop.Word`，重複本程序中的步驟 1 和 2。</span><span class="sxs-lookup"><span data-stu-id="5e42f-225">Repeat steps 1 and 2 in this procedure for `Microsoft.Office.Interop.Word`.</span></span>

4. <span data-ttu-id="5e42f-226">在 C# 中，將 `Autofit` 方法結尾的兩個 `DisplayInExcel` 呼叫標為註解。</span><span class="sxs-lookup"><span data-stu-id="5e42f-226">In C#, comment out the two calls to `Autofit` at the end of the `DisplayInExcel` method.</span></span>

5. <span data-ttu-id="5e42f-227">按 F5 鍵，確認專案仍然正確地執行。</span><span class="sxs-lookup"><span data-stu-id="5e42f-227">Press F5 to verify that the project still runs correctly.</span></span>

6. <span data-ttu-id="5e42f-228">重複前一個程序中的步驟 1-3，開啟組件視窗。</span><span class="sxs-lookup"><span data-stu-id="5e42f-228">Repeat steps 1-3 from the previous procedure to open the assembly window.</span></span> <span data-ttu-id="5e42f-229">請注意，`Microsoft.Office.Interop.Word` 和 `Microsoft.Office.Interop.Excel` 已不在內嵌的組件清單中。</span><span class="sxs-lookup"><span data-stu-id="5e42f-229">Notice that `Microsoft.Office.Interop.Word` and `Microsoft.Office.Interop.Excel` are no longer in the list of embedded assemblies.</span></span>

7. <span data-ttu-id="5e42f-230">按兩下**資訊清單**圖示，並捲動所參考之組件的清單。</span><span class="sxs-lookup"><span data-stu-id="5e42f-230">Double-click the **MANIFEST** icon and scroll through the list of referenced assemblies.</span></span> <span data-ttu-id="5e42f-231">`Microsoft.Office.Interop.Word` 和 `Microsoft.Office.Interop.Excel` 都在清單中。</span><span class="sxs-lookup"><span data-stu-id="5e42f-231">Both `Microsoft.Office.Interop.Word` and `Microsoft.Office.Interop.Excel` are in the list.</span></span> <span data-ttu-id="5e42f-232">由於應用程式會參考 Excel 和 Word PIA，而且 [內嵌 Interop 類型]  屬性設定為 [False]  ，所以使用者電腦上必須具有這兩個組件。</span><span class="sxs-lookup"><span data-stu-id="5e42f-232">Because the application references the Excel and Word PIAs, and the **Embed Interop Types** property is set to **False**, both assemblies must exist on the end user's computer.</span></span>

8. <span data-ttu-id="5e42f-233">在 Visual Studio 中，按一下 [建置]  功能表上的 [清除方案]  ，清除已完成的專案。</span><span class="sxs-lookup"><span data-stu-id="5e42f-233">In Visual Studio, click **Clean Solution** on the **Build** menu to clean up the completed project.</span></span>

## <a name="see-also"></a><span data-ttu-id="5e42f-234">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e42f-234">See also</span></span>

- [<span data-ttu-id="5e42f-235">自動實作的屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5e42f-235">Auto-Implemented Properties (Visual Basic)</span></span>](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)
- [<span data-ttu-id="5e42f-236">自動實作的屬性 (C#)</span><span class="sxs-lookup"><span data-stu-id="5e42f-236">Auto-Implemented Properties (C#)</span></span>](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md)
- [<span data-ttu-id="5e42f-237">集合初始設定式</span><span class="sxs-lookup"><span data-stu-id="5e42f-237">Collection Initializers</span></span>](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [<span data-ttu-id="5e42f-238">物件和集合初始設定式</span><span class="sxs-lookup"><span data-stu-id="5e42f-238">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
- [<span data-ttu-id="5e42f-239">選擇性參數</span><span class="sxs-lookup"><span data-stu-id="5e42f-239">Optional Parameters</span></span>](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
- [<span data-ttu-id="5e42f-240">依位置和名稱傳遞引數</span><span class="sxs-lookup"><span data-stu-id="5e42f-240">Passing Arguments by Position and by Name</span></span>](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name.md)
- [<span data-ttu-id="5e42f-241">具名和選擇性引數</span><span class="sxs-lookup"><span data-stu-id="5e42f-241">Named and Optional Arguments</span></span>](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)
- [<span data-ttu-id="5e42f-242">早期和晚期繫結</span><span class="sxs-lookup"><span data-stu-id="5e42f-242">Early and Late Binding</span></span>](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [<span data-ttu-id="5e42f-243">dynamic</span><span class="sxs-lookup"><span data-stu-id="5e42f-243">dynamic</span></span>](../../../csharp/language-reference/keywords/dynamic.md)
- [<span data-ttu-id="5e42f-244">使用動態型別</span><span class="sxs-lookup"><span data-stu-id="5e42f-244">Using Type dynamic</span></span>](../../../csharp/programming-guide/types/using-type-dynamic.md)
- [<span data-ttu-id="5e42f-245">Lambda 運算式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5e42f-245">Lambda Expressions (Visual Basic)</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="5e42f-246">Lambda 運算式 (C#)</span><span class="sxs-lookup"><span data-stu-id="5e42f-246">Lambda Expressions (C#)</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)
- [<span data-ttu-id="5e42f-247">如何：在 COM Interop 程式設計中使用已編製索引的屬性</span><span class="sxs-lookup"><span data-stu-id="5e42f-247">How to: Use Indexed Properties in COM Interop Programming</span></span>](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md)
- <span data-ttu-id="5e42f-248">[逐步解說：在 Visual Studio 中內嵌來自 Microsoft Office 組件的類型資訊](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ee317478(v%3dvs.120)) \(英文\)</span><span class="sxs-lookup"><span data-stu-id="5e42f-248">[Walkthrough: Embedding Type Information from Microsoft Office Assemblies in Visual Studio](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ee317478(v%3dvs.120))</span></span>
- [<span data-ttu-id="5e42f-249">逐步解說：從受控組件內嵌類型</span><span class="sxs-lookup"><span data-stu-id="5e42f-249">Walkthrough: Embedding Types from Managed Assemblies</span></span>](../../../csharp/programming-guide/concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)
- [<span data-ttu-id="5e42f-250">逐步解說：建立 Excel 的第一個 VSTO 增益集</span><span class="sxs-lookup"><span data-stu-id="5e42f-250">Walkthrough: Creating Your First VSTO Add-in for Excel</span></span>](/visualstudio/vsto/walkthrough-creating-your-first-vsto-add-in-for-excel)
- [<span data-ttu-id="5e42f-251">COM Interop</span><span class="sxs-lookup"><span data-stu-id="5e42f-251">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)
- [<span data-ttu-id="5e42f-252">互通性</span><span class="sxs-lookup"><span data-stu-id="5e42f-252">Interoperability</span></span>](../../../csharp/programming-guide/interop/index.md)
