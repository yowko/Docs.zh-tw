---
title: 逐步解說：建立和使用動態物件 (C# 和 Visual Basic)
description: 瞭解如何在此逐步解說中建立和使用動態物件。 建立自訂動態物件，以及使用 ' IronPython ' 程式庫的專案。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dynamic objects [Visual Basic]
- dynamic objects
- dynamic objects [C#]
ms.assetid: 568f1645-1305-4906-8625-5d77af81e04f
ms.openlocfilehash: 144651d3b14f6f6093ab07f1df7be10e6d05ae89
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381251"
---
# <a name="walkthrough-creating-and-using-dynamic-objects-c-and-visual-basic"></a><span data-ttu-id="46895-104">逐步解說：建立和使用動態物件 (C# 和 Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="46895-104">Walkthrough: Creating and Using Dynamic Objects (C# and Visual Basic)</span></span>

<span data-ttu-id="46895-105">動態物件會在執行階段公開成員 (例如屬性和方法)，而不是在編譯時期。</span><span class="sxs-lookup"><span data-stu-id="46895-105">Dynamic objects expose members such as properties and methods at run time, instead of at compile time.</span></span> <span data-ttu-id="46895-106">這可讓您建立物件，以使用與靜態類型或格式不相符的結構。</span><span class="sxs-lookup"><span data-stu-id="46895-106">This enables you to create objects to work with structures that do not match a static type or format.</span></span> <span data-ttu-id="46895-107">例如，您可以使用動態物件來參考 HTML 文件物件模型 (DOM)，其可包含任何有效的 HTML 標記項目和屬性組合。</span><span class="sxs-lookup"><span data-stu-id="46895-107">For example, you can use a dynamic object to reference the HTML Document Object Model (DOM), which can contain any combination of valid HTML markup elements and attributes.</span></span> <span data-ttu-id="46895-108">由於每個 HTML 文件都是唯一的，因此系統會在執行階段決定特定的 HTML 文件成員。</span><span class="sxs-lookup"><span data-stu-id="46895-108">Because each HTML document is unique, the members for a particular HTML document are determined at run time.</span></span> <span data-ttu-id="46895-109">參考 HTML 項目屬性的常用方法，是將屬性名稱傳遞給項目的 `GetProperty` 方法。</span><span class="sxs-lookup"><span data-stu-id="46895-109">A common method to reference an attribute of an HTML element is to pass the name of the attribute to the `GetProperty` method of the element.</span></span> <span data-ttu-id="46895-110">若要參考 HTML 項目 `<div id="Div1">` 的 `id` 屬性，您要先取得 `<div>` 項目的參考，然後再使用 `divElement.GetProperty("id")`。</span><span class="sxs-lookup"><span data-stu-id="46895-110">To reference the `id` attribute of the HTML element `<div id="Div1">`, you first obtain a reference to the `<div>` element, and then use `divElement.GetProperty("id")`.</span></span> <span data-ttu-id="46895-111">如果您使用動態物件，則可以 `divElement.id` 的形式來參考 `id` 屬性。</span><span class="sxs-lookup"><span data-stu-id="46895-111">If you use a dynamic object, you can reference the `id` attribute as `divElement.id`.</span></span>  
  
 <span data-ttu-id="46895-112">動態物件也可讓您方便存取動態語言 (諸如 IronPython 和 IronRuby)。</span><span class="sxs-lookup"><span data-stu-id="46895-112">Dynamic objects also provide convenient access to dynamic languages such as IronPython and IronRuby.</span></span> <span data-ttu-id="46895-113">您可以使用動態物件，參考在執行階段受到解譯的動態指令碼。</span><span class="sxs-lookup"><span data-stu-id="46895-113">You can use a dynamic object to refer to a dynamic script that is interpreted at run time.</span></span>  
  
 <span data-ttu-id="46895-114">您可以使用晚期繫結，參考動態物件。</span><span class="sxs-lookup"><span data-stu-id="46895-114">You reference a dynamic object by using late binding.</span></span> <span data-ttu-id="46895-115">在 C# 中，您可以將晚期繫結物件的類型指定為 `dynamic`。</span><span class="sxs-lookup"><span data-stu-id="46895-115">In C#, you specify the type of a late-bound object as `dynamic`.</span></span> <span data-ttu-id="46895-116">在 Visual Basic 中，您可以將晚期繫結物件的類型指定為 `Object`。</span><span class="sxs-lookup"><span data-stu-id="46895-116">In Visual Basic, you specify the type of a late-bound object as `Object`.</span></span> <span data-ttu-id="46895-117">如需詳細資訊，請參閱 [dynamic](../../language-reference/builtin-types/reference-types.md) 以及[早期和晚期繫結](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)。</span><span class="sxs-lookup"><span data-stu-id="46895-117">For more information, see [dynamic](../../language-reference/builtin-types/reference-types.md) and [Early and Late Binding](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md).</span></span>  
  
 <span data-ttu-id="46895-118">您可以在 <xref:System.Dynamic?displayProperty=nameWithType> 命名空間中使用類別，以建立自訂動態物件。</span><span class="sxs-lookup"><span data-stu-id="46895-118">You can create custom dynamic objects by using the classes in the <xref:System.Dynamic?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="46895-119">例如，您可以建立 <xref:System.Dynamic.ExpandoObject>，並在執行階段中指定該物件的成員。</span><span class="sxs-lookup"><span data-stu-id="46895-119">For example, you can create an <xref:System.Dynamic.ExpandoObject> and specify the members of that object at run time.</span></span> <span data-ttu-id="46895-120">您也可以建立繼承 <xref:System.Dynamic.DynamicObject> 類別的專屬類型。</span><span class="sxs-lookup"><span data-stu-id="46895-120">You can also create your own type that inherits the <xref:System.Dynamic.DynamicObject> class.</span></span> <span data-ttu-id="46895-121">接著，您即可覆寫 <xref:System.Dynamic.DynamicObject> 類別的成員，以提供執行階段動態功能。</span><span class="sxs-lookup"><span data-stu-id="46895-121">You can then override the members of the <xref:System.Dynamic.DynamicObject> class to provide run-time dynamic functionality.</span></span>  
  
 <span data-ttu-id="46895-122">在這個逐步解說中，您將執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="46895-122">In this walkthrough you will perform the following tasks:</span></span>  
  
- <span data-ttu-id="46895-123">建立自訂物件，以將文字檔內容動態公開為物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="46895-123">Create a custom object that dynamically exposes the contents of a text file as properties of an object.</span></span>  
  
- <span data-ttu-id="46895-124">建立專案，以使用 `IronPython` 程式庫。</span><span class="sxs-lookup"><span data-stu-id="46895-124">Create a project that uses an `IronPython` library.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="46895-125">必要條件</span><span class="sxs-lookup"><span data-stu-id="46895-125">Prerequisites</span></span>  

<span data-ttu-id="46895-126">您需具備適用於 .NET 的 [IronPython](https://ironpython.net/) 才能完成此逐步解說。</span><span class="sxs-lookup"><span data-stu-id="46895-126">You need [IronPython](https://ironpython.net/) for .NET to complete this walkthrough.</span></span> <span data-ttu-id="46895-127">請移至[下載頁面](https://ironpython.net/download/)以取得最新版本。</span><span class="sxs-lookup"><span data-stu-id="46895-127">Go to their [Download page](https://ironpython.net/download/) to obtain the latest version.</span></span>
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-a-custom-dynamic-object"></a><span data-ttu-id="46895-128">建立自訂的動態物件</span><span class="sxs-lookup"><span data-stu-id="46895-128">Creating a Custom Dynamic Object</span></span>

<span data-ttu-id="46895-129">您在本逐步解說中建立的第一個專案，會定義自訂的動態物件，以搜尋文字檔的內容。</span><span class="sxs-lookup"><span data-stu-id="46895-129">The first project that you create in this walkthrough defines a custom dynamic object that searches the contents of a text file.</span></span> <span data-ttu-id="46895-130">動態屬性的名稱可指定要搜尋的文字。</span><span class="sxs-lookup"><span data-stu-id="46895-130">Text to search for is specified by the name of a dynamic property.</span></span> <span data-ttu-id="46895-131">例如，如果呼叫程式碼指定 `dynamicFile.Sample`，動態類別會傳回字串的泛型清單，其中包含檔案中開頭為 "Sample" 的所有行。</span><span class="sxs-lookup"><span data-stu-id="46895-131">For example, if calling code specifies `dynamicFile.Sample`, the dynamic class returns a generic list of strings that contains all of the lines from the file that begin with "Sample".</span></span> <span data-ttu-id="46895-132">搜尋不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="46895-132">The search is case-insensitive.</span></span> <span data-ttu-id="46895-133">動態類別也支援兩個選擇性引數。</span><span class="sxs-lookup"><span data-stu-id="46895-133">The dynamic class also supports two optional arguments.</span></span> <span data-ttu-id="46895-134">第一個引數是搜尋選項列舉值，其指定動態類別應該在行開頭、行結尾或行的任何位置，搜尋相符項目。</span><span class="sxs-lookup"><span data-stu-id="46895-134">The first argument is a search option enum value that specifies that the dynamic class should search for matches at the start of the line, the end of the line, or anywhere in the line.</span></span> <span data-ttu-id="46895-135">第二個引數指定動態類別應該先修剪文字的前置和後端空格，再進行搜尋。</span><span class="sxs-lookup"><span data-stu-id="46895-135">The second argument specifies that the dynamic class should trim leading and trailing spaces from each line before searching.</span></span> <span data-ttu-id="46895-136">例如，如果呼叫程式碼指定 `dynamicFile.Sample(StringSearchOption.Contains)`，動態類別即會在行的任何位置搜尋 "Sample"。</span><span class="sxs-lookup"><span data-stu-id="46895-136">For example, if calling code specifies `dynamicFile.Sample(StringSearchOption.Contains)`, the dynamic class searches for "Sample" anywhere in a line.</span></span> <span data-ttu-id="46895-137">如果呼叫程式碼指定 `dynamicFile.Sample(StringSearchOption.StartsWith, false)`，則動態類別會在每一行開頭搜尋 "Sample"，且不會移除前置和後端空格。</span><span class="sxs-lookup"><span data-stu-id="46895-137">If calling code specifies `dynamicFile.Sample(StringSearchOption.StartsWith, false)`, the dynamic class searches for "Sample" at the start of each line, and does not remove leading and trailing spaces.</span></span> <span data-ttu-id="46895-138">動態類別的預設行為是在每一行開頭搜尋相符項目，並移除前置和後端空格。</span><span class="sxs-lookup"><span data-stu-id="46895-138">The default behavior of the dynamic class is to search for a match at the start of each line and to remove leading and trailing spaces.</span></span>  
  
### <a name="to-create-a-custom-dynamic-class"></a><span data-ttu-id="46895-139">若要建立自訂動態類別</span><span class="sxs-lookup"><span data-stu-id="46895-139">To create a custom dynamic class</span></span>  
  
1. <span data-ttu-id="46895-140">啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="46895-140">Start Visual Studio.</span></span>  
  
2. <span data-ttu-id="46895-141">**在 [檔案**] 功能表上，指向 [**新增**]，然後按一下 [**專案**]。</span><span class="sxs-lookup"><span data-stu-id="46895-141">On the **File** menu, point to **New** and then click **Project**.</span></span>  
  
3. <span data-ttu-id="46895-142">在 [新增專案]\*\*\*\* 對話方塊的 [專案類型]\*\*\*\* 窗格中，確認已選取 [Windows]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="46895-142">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="46895-143">選取 [範本]\*\*\*\* 窗格中的 [主控台應用程式]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="46895-143">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="46895-144">在 [名稱]\*\*\*\* 方塊中，輸入 `DynamicSample` 並按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="46895-144">In the **Name** box, type `DynamicSample`, and then click **OK**.</span></span> <span data-ttu-id="46895-145">隨即建立新專案。</span><span class="sxs-lookup"><span data-stu-id="46895-145">The new project is created.</span></span>  
  
4. <span data-ttu-id="46895-146">以滑鼠右鍵按一下 DynamicSample 專案，再指向 [新增]\*\*\*\*，然後按一下 [類別]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="46895-146">Right-click the DynamicSample project and point to **Add**, and then click **Class**.</span></span> <span data-ttu-id="46895-147">在 [名稱]\*\*\*\* 方塊中，輸入 `ReadOnlyFile` 並按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="46895-147">In the **Name** box, type `ReadOnlyFile`, and then click **OK**.</span></span> <span data-ttu-id="46895-148">隨即新增檔案，其中包含 ReadOnlyFile 類別。</span><span class="sxs-lookup"><span data-stu-id="46895-148">A new file is added that contains the ReadOnlyFile class.</span></span>  
  
5. <span data-ttu-id="46895-149">在 ReadOnlyFile.cs 或 ReadOnlyFile.vb 檔案頂端，新增下列程式碼以匯入 <xref:System.IO?displayProperty=nameWithType> 和 <xref:System.Dynamic?displayProperty=nameWithType> 命名空間。</span><span class="sxs-lookup"><span data-stu-id="46895-149">At the top of the ReadOnlyFile.cs or ReadOnlyFile.vb file, add the following code to import the <xref:System.IO?displayProperty=nameWithType> and <xref:System.Dynamic?displayProperty=nameWithType> namespaces.</span></span>  

    [!code-csharp[VbDynamicWalkthrough#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#1)]
    [!code-vb[VbDynamicWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#1)]  

6. <span data-ttu-id="46895-150">自訂動態物件會使用列舉，來判斷搜尋準則。</span><span class="sxs-lookup"><span data-stu-id="46895-150">The custom dynamic object uses an enum to determine the search criteria.</span></span> <span data-ttu-id="46895-151">在 class 陳述式之前，加入下列列舉定義。</span><span class="sxs-lookup"><span data-stu-id="46895-151">Before the class statement, add the following enum definition.</span></span>  
  
    [!code-csharp[VbDynamicWalkthrough#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#2)]
    [!code-vb[VbDynamicWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#2)]
  
7. <span data-ttu-id="46895-152">如下列程式碼範例所示，更新繼承 `DynamicObject` 類別的 class 陳述式。</span><span class="sxs-lookup"><span data-stu-id="46895-152">Update the class statement to inherit the `DynamicObject` class, as shown in the following code example.</span></span>  
  
    [!code-csharp[VbDynamicWalkthrough#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#3)]
    [!code-vb[VbDynamicWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#3)]

8. <span data-ttu-id="46895-153">將下列程式碼新增至 `ReadOnlyFile` 類別，以定義檔案路徑的私用欄位和 `ReadOnlyFile` 類別的建構函式。</span><span class="sxs-lookup"><span data-stu-id="46895-153">Add the following code to the `ReadOnlyFile` class to define a private field for the file path and a constructor for the `ReadOnlyFile` class.</span></span>  
  
    [!code-csharp[VbDynamicWalkthrough#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#4)]
    [!code-vb[VbDynamicWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#4)]
  
9. <span data-ttu-id="46895-154">將下列 `GetPropertyValue` 方法新增至 `ReadOnlyFile` 類別。</span><span class="sxs-lookup"><span data-stu-id="46895-154">Add the following `GetPropertyValue` method to the `ReadOnlyFile` class.</span></span> <span data-ttu-id="46895-155">`GetPropertyValue` 方法會以輸入形式採用搜尋準則，並傳回文字檔中符合搜尋條件的幾行內容。</span><span class="sxs-lookup"><span data-stu-id="46895-155">The `GetPropertyValue` method takes, as input, search criteria and returns the lines from a text file that match that search criteria.</span></span> <span data-ttu-id="46895-156">`ReadOnlyFile` 類別所提供的動態方法會呼叫 `GetPropertyValue` 方法，以擷取其各自的結果。</span><span class="sxs-lookup"><span data-stu-id="46895-156">The dynamic methods provided by the `ReadOnlyFile` class call the `GetPropertyValue` method to retrieve their respective results.</span></span>  
  
    [!code-csharp[VbDynamicWalkthrough#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#5)]
    [!code-vb[VbDynamicWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#5)]  
  
10. <span data-ttu-id="46895-157">在 `GetPropertyValue` 方法後面，新增下面程式碼以覆寫 <xref:System.Dynamic.DynamicObject> 類別的 <xref:System.Dynamic.DynamicObject.TryGetMember%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="46895-157">After the `GetPropertyValue` method, add the following code to override the <xref:System.Dynamic.DynamicObject.TryGetMember%2A> method of the <xref:System.Dynamic.DynamicObject> class.</span></span> <span data-ttu-id="46895-158">如果系統要求動態類別的成員，但未指定任何參數，則會呼叫 <xref:System.Dynamic.DynamicObject.TryGetMember%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="46895-158">The <xref:System.Dynamic.DynamicObject.TryGetMember%2A> method is called when a member of a dynamic class is requested and no arguments are specified.</span></span> <span data-ttu-id="46895-159">`binder` 引數包含參考成員的相關資訊，而 `result` 引數會參考指定成員傳回的結果。</span><span class="sxs-lookup"><span data-stu-id="46895-159">The `binder` argument contains information about the referenced member, and the `result` argument references the result returned for the specified member.</span></span> <span data-ttu-id="46895-160"><xref:System.Dynamic.DynamicObject.TryGetMember%2A> 方法會傳回布林值：如果要求的成員存在，該值會傳回 `true`；否則會傳回 `false`。</span><span class="sxs-lookup"><span data-stu-id="46895-160">The <xref:System.Dynamic.DynamicObject.TryGetMember%2A> method returns a Boolean value that returns `true` if the requested member exists; otherwise it returns `false`.</span></span>  
  
    [!code-csharp[VbDynamicWalkthrough#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#6)]
    [!code-vb[VbDynamicWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#6)]
  
11. <span data-ttu-id="46895-161">在 `TryGetMember` 方法後面，新增下面程式碼以覆寫 <xref:System.Dynamic.DynamicObject> 類別的 <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="46895-161">After the `TryGetMember` method, add the following code to override the <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> method of the <xref:System.Dynamic.DynamicObject> class.</span></span> <span data-ttu-id="46895-162">如果系統要求具有引數的動態類別成員，則會呼叫 <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="46895-162">The <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> method is called when a member of a dynamic class is requested with arguments.</span></span> <span data-ttu-id="46895-163">`binder` 引數包含參考成員的相關資訊，而 `result` 引數會參考指定成員傳回的結果。</span><span class="sxs-lookup"><span data-stu-id="46895-163">The `binder` argument contains information about the referenced member, and the `result` argument references the result returned for the specified member.</span></span> <span data-ttu-id="46895-164">`args` 引數包含傳遞給該成員的引數陣列。</span><span class="sxs-lookup"><span data-stu-id="46895-164">The `args` argument contains an array of the arguments that are passed to the member.</span></span> <span data-ttu-id="46895-165"><xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> 方法會傳回布林值：如果要求的成員存在，該值會傳回 `true`；否則會傳回 `false`。</span><span class="sxs-lookup"><span data-stu-id="46895-165">The <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> method returns a Boolean value that returns `true` if the requested member exists; otherwise it returns `false`.</span></span>  
  
    <span data-ttu-id="46895-166">自訂版 `TryInvokeMember` 方法需要的第一個引數，是來自上一個步驟所定義的 `StringSearchOption` 列舉。</span><span class="sxs-lookup"><span data-stu-id="46895-166">The custom version of the `TryInvokeMember` method expects the first argument to be a value from the `StringSearchOption` enum that you defined in a previous step.</span></span> <span data-ttu-id="46895-167">`TryInvokeMember` 方法需要的第二個引數是布林值。</span><span class="sxs-lookup"><span data-stu-id="46895-167">The `TryInvokeMember` method expects the second argument to be a Boolean value.</span></span> <span data-ttu-id="46895-168">如果這兩個引數有一個或兩個是有效的值，即會將其傳遞給 `GetPropertyValue` 方法以擷取結果。</span><span class="sxs-lookup"><span data-stu-id="46895-168">If one or both arguments are valid values, they are passed to the `GetPropertyValue` method to retrieve the results.</span></span>  
  
    [!code-csharp[VbDynamicWalkthrough#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/readonlyfile.cs#7)]
    [!code-vb[VbDynamicWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/readonlyfile.vb#7)]
  
12. <span data-ttu-id="46895-169">儲存並關閉檔案。</span><span class="sxs-lookup"><span data-stu-id="46895-169">Save and close the file.</span></span>  
  
#### <a name="to-create-a-sample-text-file"></a><span data-ttu-id="46895-170">若要建立範例文字檔</span><span class="sxs-lookup"><span data-stu-id="46895-170">To create a sample text file</span></span>  
  
1. <span data-ttu-id="46895-171">以滑鼠右鍵按一下 DynamicSample 專案，再指向 [新增]\*\*\*\*，然後按一下 [新增項目]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="46895-171">Right-click the DynamicSample project and point to **Add**, and then click **New Item**.</span></span> <span data-ttu-id="46895-172">在 [已安裝的範本]\*\*\*\* 窗格中，選取 [一般]\*\*\*\*，然後選取 [文字檔]\*\*\*\* 範本。</span><span class="sxs-lookup"><span data-stu-id="46895-172">In the **Installed Templates** pane, select **General**, and then select the **Text File** template.</span></span> <span data-ttu-id="46895-173">保留 [名稱]\*\*\*\* 方塊中的 TextFile1.txt 預設名稱，然後再按一下 [新增]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="46895-173">Leave the default name of TextFile1.txt in the **Name** box, and then click **Add**.</span></span> <span data-ttu-id="46895-174">新的文字檔隨即加入專案中。</span><span class="sxs-lookup"><span data-stu-id="46895-174">A new text file is added to the project.</span></span>  
  
2. <span data-ttu-id="46895-175">將下列文字複製到 TextFile1.txt 檔案。</span><span class="sxs-lookup"><span data-stu-id="46895-175">Copy the following text to the TextFile1.txt file.</span></span>  
  
    ```text  
    List of customers and suppliers  
  
    Supplier: Lucerne Publishing (https://www.lucernepublishing.com/)  
    Customer: Preston, Chris  
    Customer: Hines, Patrick  
    Customer: Cameron, Maria  
    Supplier: Graphic Design Institute (https://www.graphicdesigninstitute.com/)
    Supplier: Fabrikam, Inc. (https://www.fabrikam.com/)
    Customer: Seubert, Roxanne  
    Supplier: Proseware, Inc. (http://www.proseware.com/)
    Customer: Adolphi, Stephan  
    Customer: Koch, Paul  
    ```  
  
3. <span data-ttu-id="46895-176">儲存並關閉檔案。</span><span class="sxs-lookup"><span data-stu-id="46895-176">Save and close the file.</span></span>  
  
#### <a name="to-create-a-sample-application-that-uses-the-custom-dynamic-object"></a><span data-ttu-id="46895-177">若要建立使用自訂動態物件的範例應用程式</span><span class="sxs-lookup"><span data-stu-id="46895-177">To create a sample application that uses the custom dynamic object</span></span>  
  
1. <span data-ttu-id="46895-178">在 [方案總管]\*\*\*\* 中，如果您是使用 Visual Basic，請按兩下 Module1.vb 檔案；或者，如果您是使用 Visual C#，請按兩下 Program.cs 檔案。</span><span class="sxs-lookup"><span data-stu-id="46895-178">In **Solution Explorer**, double-click the Module1.vb file if you are using Visual Basic or the Program.cs file if you are using Visual C#.</span></span>  
  
2. <span data-ttu-id="46895-179">將下列程式碼加入 Main 程序，以為 TextFile1.txt 檔案建立 `ReadOnlyFile` 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="46895-179">Add the following code to the Main procedure to create an instance of the `ReadOnlyFile` class for the TextFile1.txt file.</span></span> <span data-ttu-id="46895-180">程式碼會使用晚期繫結呼叫動態成員，並擷取包含字串 "Customer" 的文字行。</span><span class="sxs-lookup"><span data-stu-id="46895-180">The code uses late binding to call dynamic members and retrieve lines of text that contain the string "Customer".</span></span>  
  
     [!code-csharp[VbDynamicWalkthrough#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthrough/cs/program.cs#8)]
     [!code-vb[VbDynamicWalkthrough#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthrough/vb/module1.vb#8)]
  
3. <span data-ttu-id="46895-181">儲存檔案，並按 CTRL+F5 建置及執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="46895-181">Save the file and press CTRL+F5 to build and run the application.</span></span>  
  
## <a name="calling-a-dynamic-language-library"></a><span data-ttu-id="46895-182">呼叫動態語言程式庫</span><span class="sxs-lookup"><span data-stu-id="46895-182">Calling a Dynamic Language Library</span></span>  

<span data-ttu-id="46895-183">您在本逐步解說中建立的下一個專案，會存取以動態語言 IronPython 撰寫的程式庫。</span><span class="sxs-lookup"><span data-stu-id="46895-183">The next project that you create in this walkthrough accesses a library that is written in the dynamic language IronPython.</span></span>
  
### <a name="to-create-a-custom-dynamic-class"></a><span data-ttu-id="46895-184">若要建立自訂動態類別</span><span class="sxs-lookup"><span data-stu-id="46895-184">To create a custom dynamic class</span></span>
  
1. <span data-ttu-id="46895-185">**在 Visual Studio 的 [檔案**] 功能表上，指向 [**新增**]，然後按一下 [**專案**]。</span><span class="sxs-lookup"><span data-stu-id="46895-185">In Visual Studio, on the **File** menu, point to **New** and then click **Project**.</span></span>  
  
2. <span data-ttu-id="46895-186">在 [新增專案]\*\*\*\* 對話方塊的 [專案類型]\*\*\*\* 窗格中，確認已選取 [Windows]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="46895-186">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="46895-187">選取 [範本]\*\*\*\* 窗格中的 [主控台應用程式]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="46895-187">Select **Console Application** in the **Templates** pane.</span></span> <span data-ttu-id="46895-188">在 [名稱]\*\*\*\* 方塊中，輸入 `DynamicIronPythonSample` 並按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="46895-188">In the **Name** box, type `DynamicIronPythonSample`, and then click **OK**.</span></span> <span data-ttu-id="46895-189">隨即建立新專案。</span><span class="sxs-lookup"><span data-stu-id="46895-189">The new project is created.</span></span>  
  
3. <span data-ttu-id="46895-190">如果您是使用 Visual Basic，請以滑鼠右鍵按一下 DynamicIronPythonSample 專案，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="46895-190">If you are using Visual Basic, right-click the DynamicIronPythonSample project and then click **Properties**.</span></span> <span data-ttu-id="46895-191">按一下 [**參考**] 索引標籤。按一下 [**新增**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="46895-191">Click the **References** tab. Click the **Add** button.</span></span> <span data-ttu-id="46895-192">如果您是使用 Visual C#，請在方案總管\*\*\*\* 中，以滑鼠右鍵按一下 [參考]\*\*\*\* 資料夾，然後按一下 [加入參考]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="46895-192">If you are using Visual C#, in **Solution Explorer**, right-click the **References** folder and then click **Add Reference**.</span></span>  
  
4. <span data-ttu-id="46895-193">在 [瀏覽]\*\*\*\* 索引標籤上，瀏覽至安裝 IronPython 程式庫的資料夾。</span><span class="sxs-lookup"><span data-stu-id="46895-193">On the **Browse** tab, browse to the folder where the IronPython libraries are installed.</span></span> <span data-ttu-id="46895-194">例如 C:\Program Files\IronPython 2.6 for .NET 4.0。</span><span class="sxs-lookup"><span data-stu-id="46895-194">For example, C:\Program Files\IronPython 2.6 for .NET 4.0.</span></span> <span data-ttu-id="46895-195">選取 **IronPython.dll**、**IronPython.Modules.dll**、**Microsoft.Scripting.dll** 和 **Microsoft.Dynamic.dll** 程式庫。</span><span class="sxs-lookup"><span data-stu-id="46895-195">Select the **IronPython.dll**, **IronPython.Modules.dll**, **Microsoft.Scripting.dll**, and **Microsoft.Dynamic.dll** libraries.</span></span> <span data-ttu-id="46895-196">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="46895-196">Click **OK**.</span></span>  
  
5. <span data-ttu-id="46895-197">如果您是使用 Visual Basic，請編輯 Module1.vb 檔案。</span><span class="sxs-lookup"><span data-stu-id="46895-197">If you are using Visual Basic, edit the Module1.vb file.</span></span> <span data-ttu-id="46895-198">如果您是使用 Visual C#，請編輯 Program.cs 檔案。</span><span class="sxs-lookup"><span data-stu-id="46895-198">If you are using Visual C#, edit the Program.cs file.</span></span>  
  
6. <span data-ttu-id="46895-199">在檔案頂端，加入下列程式碼以匯入來自 IronPython 程式庫的 `Microsoft.Scripting.Hosting` 和 `IronPython.Hosting` 命名空間。</span><span class="sxs-lookup"><span data-stu-id="46895-199">At the top of the file, add the following code to import the `Microsoft.Scripting.Hosting` and `IronPython.Hosting` namespaces from the IronPython libraries.</span></span>  
  
    [!code-csharp[VbDynamicWalkthroughIronPython#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/cs/program.cs#1)]
    [!code-vb[VbDynamicWalkthroughIronPython#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/vb/module1.vb#1)]
  
7. <span data-ttu-id="46895-200">在 Main 方法中加入下列程式碼，以建立裝載 IronPython 程式庫的新 `Microsoft.Scripting.Hosting.ScriptRuntime` 物件。</span><span class="sxs-lookup"><span data-stu-id="46895-200">In the Main method, add the following code to create a new `Microsoft.Scripting.Hosting.ScriptRuntime` object to host the IronPython libraries.</span></span> <span data-ttu-id="46895-201">`ScriptRuntime` 物件會載入 IronPython 程式庫模組 random.py。</span><span class="sxs-lookup"><span data-stu-id="46895-201">The `ScriptRuntime` object loads the IronPython library module random.py.</span></span>  
  
     [!code-csharp[VbDynamicWalkthroughIronPython#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/cs/program.cs#2)]
     [!code-vb[VbDynamicWalkthroughIronPython#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/vb/module1.vb#2)]
  
8. <span data-ttu-id="46895-202">在程式碼載入 random.py 模組之後，請加入下列程式碼以建立整數陣列。</span><span class="sxs-lookup"><span data-stu-id="46895-202">After the code to load the random.py module, add the following code to create an array of integers.</span></span> <span data-ttu-id="46895-203">系統會將陣列傳遞給 random.py 模組的 `shuffle` 方法，其會隨機排序陣列中的值。</span><span class="sxs-lookup"><span data-stu-id="46895-203">The array is passed to the `shuffle` method of the random.py module, which randomly sorts the values in the array.</span></span>  
  
     [!code-csharp[VbDynamicWalkthroughIronPython#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/cs/program.cs#3)]
     [!code-vb[VbDynamicWalkthroughIronPython#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbdynamicwalkthroughironpython/vb/module1.vb#3)]
  
9. <span data-ttu-id="46895-204">儲存檔案，並按 CTRL+F5 建置及執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="46895-204">Save the file and press CTRL+F5 to build and run the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46895-205">另請參閱</span><span class="sxs-lookup"><span data-stu-id="46895-205">See also</span></span>

- <xref:System.Dynamic?displayProperty=nameWithType>
- <xref:System.Dynamic.DynamicObject?displayProperty=nameWithType>
- [<span data-ttu-id="46895-206">使用動態類型</span><span class="sxs-lookup"><span data-stu-id="46895-206">Using Type dynamic</span></span>](./using-type-dynamic.md)
- [<span data-ttu-id="46895-207">早期和晚期繫結</span><span class="sxs-lookup"><span data-stu-id="46895-207">Early and Late Binding</span></span>](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [<span data-ttu-id="46895-208">動態</span><span class="sxs-lookup"><span data-stu-id="46895-208">dynamic</span></span>](../../language-reference/builtin-types/reference-types.md)
- [<span data-ttu-id="46895-209">實作動態介面 (Microsoft TechNet 的可下載 PDF)</span><span class="sxs-lookup"><span data-stu-id="46895-209">Implementing Dynamic Interfaces (downloadable PDF from Microsoft TechNet)</span></span>](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/implementing-dynamic-interfaces.pdf)
