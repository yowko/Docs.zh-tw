---
title: 實現 IE500
ms.date: 07/31/2018
helpviewer_keywords:
- control flow [Visual Basic]
- enumerable interfaces
- loop structures [Visual Basic], optimizing performance
- control flow [Visual Basic]
ms.assetid: c60d7589-51f2-4463-a2d5-22506bbc1554
ms.openlocfilehash: 4151a680050f234d450d8de5e67a767c54e8df68
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266907"
---
# <a name="walkthrough-implementing-ienumerableof-t-in-visual-basic"></a><span data-ttu-id="d1758-102">逐步解說：在 Visual Basic 中實作 IEnumerable(Of T)</span><span class="sxs-lookup"><span data-stu-id="d1758-102">Walkthrough: Implementing IEnumerable(Of T) in Visual Basic</span></span>
<span data-ttu-id="d1758-103">介面<xref:System.Collections.Generic.IEnumerable%601>由類實現，這些類可以一次返回一個項的值序列。</span><span class="sxs-lookup"><span data-stu-id="d1758-103">The <xref:System.Collections.Generic.IEnumerable%601> interface is implemented by classes that can return a sequence of values one item at a time.</span></span> <span data-ttu-id="d1758-104">一次返回一個專案的資料的優點是，您不必將完整的資料集載入到記憶體中才能使用它。</span><span class="sxs-lookup"><span data-stu-id="d1758-104">The advantage of returning data one item at a time is that you do not have to load the complete set of data into memory to work with it.</span></span> <span data-ttu-id="d1758-105">您只需要使用足夠的記憶體從資料載入單個項。</span><span class="sxs-lookup"><span data-stu-id="d1758-105">You only have to use sufficient memory to load a single item from the data.</span></span> <span data-ttu-id="d1758-106">實現介面的`IEnumerable(T)`類可用於`For Each`迴圈或 LINQ 查詢。</span><span class="sxs-lookup"><span data-stu-id="d1758-106">Classes that implement the `IEnumerable(T)` interface can be used with `For Each` loops or LINQ queries.</span></span>  
  
 <span data-ttu-id="d1758-107">例如，考慮一個應用程式，該應用程式必須讀取大型文字檔，並從檔返回與特定搜尋條件匹配的每行。</span><span class="sxs-lookup"><span data-stu-id="d1758-107">For example, consider an application that must read a large text file and return each line from the file that matches particular search criteria.</span></span> <span data-ttu-id="d1758-108">應用程式使用 LINQ 查詢從檔返回與指定條件匹配的行。</span><span class="sxs-lookup"><span data-stu-id="d1758-108">The application uses a LINQ query to return lines from the file that match the specified criteria.</span></span> <span data-ttu-id="d1758-109">要使用 LINQ 查詢查詢檔的內容，應用程式可以將檔的內容載入到陣列或集合中。</span><span class="sxs-lookup"><span data-stu-id="d1758-109">To query the contents of the file by using a LINQ query, the application could load the contents of the file into an array or a collection.</span></span> <span data-ttu-id="d1758-110">但是，將整個檔載入到陣列或集合中會消耗的記憶體遠遠多於所需的記憶體。</span><span class="sxs-lookup"><span data-stu-id="d1758-110">However, loading the whole file into an array or collection would consume far more memory than is required.</span></span> <span data-ttu-id="d1758-111">LINQ 查詢可以使用枚舉類查詢檔內容，僅返回與搜尋條件匹配的值。</span><span class="sxs-lookup"><span data-stu-id="d1758-111">The LINQ query could instead query the file contents by using an enumerable class, returning only values that match the search criteria.</span></span> <span data-ttu-id="d1758-112">僅返回幾個匹配值的查詢消耗的記憶體要少得多。</span><span class="sxs-lookup"><span data-stu-id="d1758-112">Queries that return only a few matching values would consume far less memory.</span></span>  
  
 <span data-ttu-id="d1758-113">您可以創建實現介面的類，<xref:System.Collections.Generic.IEnumerable%601>以將來源資料公開為枚舉資料。</span><span class="sxs-lookup"><span data-stu-id="d1758-113">You can create a class that implements the <xref:System.Collections.Generic.IEnumerable%601> interface to expose source data as enumerable data.</span></span> <span data-ttu-id="d1758-114">實現介面的`IEnumerable(T)`類將需要實現<xref:System.Collections.Generic.IEnumerator%601>介面的另一個類來遍經來源資料反覆運算。</span><span class="sxs-lookup"><span data-stu-id="d1758-114">Your class that implements the `IEnumerable(T)` interface will require another class that implements the <xref:System.Collections.Generic.IEnumerator%601> interface to iterate through the source data.</span></span> <span data-ttu-id="d1758-115">這兩個類使您能夠按順序將資料項目作為特定類型返回。</span><span class="sxs-lookup"><span data-stu-id="d1758-115">These two classes enable you to return items of data sequentially as a specific type.</span></span>  
  
 <span data-ttu-id="d1758-116">在本演練中，您將創建實現介面的`IEnumerable(Of String)`類和實現`IEnumerator(Of String)`介面一次讀取一行文字檔的類。</span><span class="sxs-lookup"><span data-stu-id="d1758-116">In this walkthrough, you will create a class that implements the `IEnumerable(Of String)` interface and a class that implements the `IEnumerator(Of String)` interface to read a text file one line at a time.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-enumerable-class"></a><span data-ttu-id="d1758-117">創建可枚舉類</span><span class="sxs-lookup"><span data-stu-id="d1758-117">Creating the Enumerable Class</span></span>  
  
<span data-ttu-id="d1758-118">**創建枚舉類專案**</span><span class="sxs-lookup"><span data-stu-id="d1758-118">**Create the enumerable class project**</span></span>

1. <span data-ttu-id="d1758-119">在"視覺化基本"中，在 **"檔"** 功能表上，指向 **"新建"，** 然後按一下"**專案**"。</span><span class="sxs-lookup"><span data-stu-id="d1758-119">In Visual Basic, on the **File** menu, point to **New** and then click **Project**.</span></span>

1. <span data-ttu-id="d1758-120">在 [新增專案]\*\*\*\* 對話方塊的 [專案類型]\*\*\*\* 窗格中，確認已選取 [Windows]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d1758-120">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="d1758-121">在 [範本]\*\*\*\* 窗格中，選取 [類別庫]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d1758-121">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="d1758-122">在 [名稱]\*\*\*\* 方塊中，輸入 `StreamReaderEnumerable` 並按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d1758-122">In the **Name** box, type `StreamReaderEnumerable`, and then click **OK**.</span></span> <span data-ttu-id="d1758-123">將顯示新專案。</span><span class="sxs-lookup"><span data-stu-id="d1758-123">The new project is displayed.</span></span>

1. <span data-ttu-id="d1758-124">在**解決方案資源管理器**中，按右鍵 Class1.vb 檔，然後按一下 **"重命名**"。</span><span class="sxs-lookup"><span data-stu-id="d1758-124">In **Solution Explorer**, right-click the Class1.vb file and click **Rename**.</span></span> <span data-ttu-id="d1758-125">將檔案重新命名為 `StreamReaderEnumerable.vb`，然後按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="d1758-125">Rename the file to `StreamReaderEnumerable.vb` and press ENTER.</span></span> <span data-ttu-id="d1758-126">重新命名檔案時，也會將類別重新命名為 `StreamReaderEnumerable`。</span><span class="sxs-lookup"><span data-stu-id="d1758-126">Renaming the file will also rename the class to `StreamReaderEnumerable`.</span></span> <span data-ttu-id="d1758-127">此類別會實作 `IEnumerable(Of String)` 介面。</span><span class="sxs-lookup"><span data-stu-id="d1758-127">This class will implement the `IEnumerable(Of String)` interface.</span></span>

1. <span data-ttu-id="d1758-128">按右鍵 StreamReaderE"專案，指向 **"添加**"，然後按一下 **"新專案**"。</span><span class="sxs-lookup"><span data-stu-id="d1758-128">Right-click the StreamReaderEnumerable project, point to **Add**, and then click **New Item**.</span></span> <span data-ttu-id="d1758-129">選擇**類**範本。</span><span class="sxs-lookup"><span data-stu-id="d1758-129">Select the **Class** template.</span></span> <span data-ttu-id="d1758-130">在 [名稱]\*\*\*\* 方塊中輸入 `StreamReaderEnumerator.vb`，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d1758-130">In the **Name** box, type `StreamReaderEnumerator.vb` and click **OK**.</span></span>

 <span data-ttu-id="d1758-131">此專案中的第一個類是枚舉類，將實現介面`IEnumerable(Of String)`。</span><span class="sxs-lookup"><span data-stu-id="d1758-131">The first class in this project is the enumerable class and will implement the `IEnumerable(Of String)` interface.</span></span> <span data-ttu-id="d1758-132">此泛型介面實現<xref:System.Collections.IEnumerable>介面，並保證此類的消費者可以便捷鍵入為`String`的值。</span><span class="sxs-lookup"><span data-stu-id="d1758-132">This generic interface implements the <xref:System.Collections.IEnumerable> interface and guarantees that consumers of this class can access values typed as `String`.</span></span>  
  
<span data-ttu-id="d1758-133">**添加代碼以實現 IE500**</span><span class="sxs-lookup"><span data-stu-id="d1758-133">**Add the code to implement IEnumerable**</span></span>

1. <span data-ttu-id="d1758-134">打開流閱讀器數位.vb 檔。</span><span class="sxs-lookup"><span data-stu-id="d1758-134">Open the StreamReaderEnumerable.vb file.</span></span>

2. <span data-ttu-id="d1758-135">在`Public Class StreamReaderEnumerable`之後的行上鍵入以下內容，然後按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="d1758-135">On the line after `Public Class StreamReaderEnumerable`, type the following and press ENTER.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#1)]

   <span data-ttu-id="d1758-136">Visual Basic 使用`IEnumerable(Of String)`介面所需的成員自動填滿類。</span><span class="sxs-lookup"><span data-stu-id="d1758-136">Visual Basic automatically populates the class with the members that are required by the `IEnumerable(Of String)` interface.</span></span>
  
3. <span data-ttu-id="d1758-137">此枚舉類將一次從文字檔中讀取一行。</span><span class="sxs-lookup"><span data-stu-id="d1758-137">This enumerable class will read lines from a text file one line at a time.</span></span> <span data-ttu-id="d1758-138">將以下代碼添加到類中，以公開將檔路徑作為輸入參數的公共建構函式。</span><span class="sxs-lookup"><span data-stu-id="d1758-138">Add the following code to the class to expose a public constructor that takes a file path as an input parameter.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#2)]

4. <span data-ttu-id="d1758-139">介面方法的實現將返回`StreamReaderEnumerator`類的新實例。 <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> `IEnumerable(Of String)`</span><span class="sxs-lookup"><span data-stu-id="d1758-139">Your implementation of the <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method of the `IEnumerable(Of String)` interface will return a new instance of the `StreamReaderEnumerator` class.</span></span> <span data-ttu-id="d1758-140">`GetEnumerator`可以實現`IEnumerable``Private`介面的方法，因為您必須只公開`IEnumerable(Of String)`介面的成員。</span><span class="sxs-lookup"><span data-stu-id="d1758-140">The implementation of the `GetEnumerator` method of the `IEnumerable` interface can be made `Private`, because you have to expose only members of the `IEnumerable(Of String)` interface.</span></span> <span data-ttu-id="d1758-141">將 Visual Basic 為`GetEnumerator`方法生成的代碼替換為以下代碼。</span><span class="sxs-lookup"><span data-stu-id="d1758-141">Replace the code that Visual Basic generated for the `GetEnumerator` methods with the following code.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#3)]  
  
<span data-ttu-id="d1758-142">**添加代碼以實現 IEnumerator**</span><span class="sxs-lookup"><span data-stu-id="d1758-142">**Add the code to implement IEnumerator**</span></span>

1. <span data-ttu-id="d1758-143">打開流閱讀器數位器.vb 檔。</span><span class="sxs-lookup"><span data-stu-id="d1758-143">Open the StreamReaderEnumerator.vb file.</span></span>

2. <span data-ttu-id="d1758-144">在`Public Class StreamReaderEnumerator`之後的行上鍵入以下內容，然後按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="d1758-144">On the line after `Public Class StreamReaderEnumerator`, type the following and press ENTER.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#4)]

   <span data-ttu-id="d1758-145">Visual Basic 使用`IEnumerator(Of String)`介面所需的成員自動填滿類。</span><span class="sxs-lookup"><span data-stu-id="d1758-145">Visual Basic automatically populates the class with the members that are required by the `IEnumerator(Of String)` interface.</span></span>

3. <span data-ttu-id="d1758-146">枚舉器類打開文字檔並執行檔 I/O 以從檔中讀取行。</span><span class="sxs-lookup"><span data-stu-id="d1758-146">The enumerator class opens the text file and performs the file I/O to read the lines from the file.</span></span> <span data-ttu-id="d1758-147">將以下代碼添加到類中，以公開將檔路徑作為輸入參數的公共建構函式，並打開文字檔進行讀取。</span><span class="sxs-lookup"><span data-stu-id="d1758-147">Add the following code to the class to expose a public constructor that takes a file path as an input parameter and open the text file for reading.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#5)]

4. <span data-ttu-id="d1758-148">`Current` `IEnumerator`和 介面的屬性將當前項從文字檔返回為`String` `IEnumerator(Of String)`</span><span class="sxs-lookup"><span data-stu-id="d1758-148">The `Current` properties for both the `IEnumerator(Of String)` and `IEnumerator` interfaces return the current item from the text file as a `String`.</span></span> <span data-ttu-id="d1758-149">`Current`可以實現`IEnumerator``Private`介面的屬性，因為您必須只公開`IEnumerator(Of String)`介面的成員。</span><span class="sxs-lookup"><span data-stu-id="d1758-149">The implementation of the `Current` property of the `IEnumerator` interface can be made `Private`, because you have to expose only members of the `IEnumerator(Of String)` interface.</span></span> <span data-ttu-id="d1758-150">將 Visual Basic 為`Current`屬性生成的代碼替換為以下代碼。</span><span class="sxs-lookup"><span data-stu-id="d1758-150">Replace the code that Visual Basic generated for the `Current` properties with the following code.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#6)]

5. <span data-ttu-id="d1758-151">介面的方法導航到文字檔中的下一個項，並更新`Current`屬性返回的值。 `MoveNext` `IEnumerator`</span><span class="sxs-lookup"><span data-stu-id="d1758-151">The `MoveNext` method of the `IEnumerator` interface navigates to the next item in the text file and updates the value that is returned by the `Current` property.</span></span> <span data-ttu-id="d1758-152">如果沒有要讀取的項，`MoveNext`則方法將返回`False`;否則該方法`MoveNext`將返回`True`。</span><span class="sxs-lookup"><span data-stu-id="d1758-152">If there are no more items to read, the `MoveNext` method returns `False`; otherwise the `MoveNext` method returns `True`.</span></span> <span data-ttu-id="d1758-153">將下列程式碼新增至 `MoveNext` 方法。</span><span class="sxs-lookup"><span data-stu-id="d1758-153">Add the following code to the `MoveNext` method.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#7)]

6. <span data-ttu-id="d1758-154">`IEnumerator`介面`Reset`的方法指示反覆運算器指向文字檔的開頭並清除當前項值。</span><span class="sxs-lookup"><span data-stu-id="d1758-154">The `Reset` method of the `IEnumerator` interface directs the iterator to point to the start of the text file and clears the current item value.</span></span> <span data-ttu-id="d1758-155">將下列程式碼新增至 `Reset` 方法。</span><span class="sxs-lookup"><span data-stu-id="d1758-155">Add the following code to the `Reset` method.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#8)]

7. <span data-ttu-id="d1758-156">`IEnumerator`介面`Dispose`的方法保證在銷毀反覆運算器之前釋放所有非託管資源。</span><span class="sxs-lookup"><span data-stu-id="d1758-156">The `Dispose` method of the `IEnumerator` interface guarantees that all unmanaged resources are released before the iterator is destroyed.</span></span> <span data-ttu-id="d1758-157">`StreamReader`物件使用的檔案控制代碼是非託管資源，必須在銷毀反覆運算器實例之前關閉。</span><span class="sxs-lookup"><span data-stu-id="d1758-157">The file handle that is used by the `StreamReader` object is an unmanaged resource and must be closed before the iterator instance is destroyed.</span></span> <span data-ttu-id="d1758-158">將為`Dispose`該方法生成的 Visual Basic 的代碼替換為以下代碼。</span><span class="sxs-lookup"><span data-stu-id="d1758-158">Replace the code that Visual Basic generated for the `Dispose` method with the following code.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#9)]
  
## <a name="using-the-sample-iterator"></a><span data-ttu-id="d1758-159">使用樣品反覆運算器</span><span class="sxs-lookup"><span data-stu-id="d1758-159">Using the Sample Iterator</span></span>

 <span data-ttu-id="d1758-160">可以在代碼中使用枚舉類以及需要實現`IEnumerable`的物件（如`For Next`迴圈或 LINQ 查詢）的控制項結構。</span><span class="sxs-lookup"><span data-stu-id="d1758-160">You can use an enumerable class in your code together with control structures that require an object that implements `IEnumerable`, such as a `For Next` loop or a LINQ query.</span></span> <span data-ttu-id="d1758-161">下面的示例顯示了 LINQ 查詢`StreamReaderEnumerable`中的 。</span><span class="sxs-lookup"><span data-stu-id="d1758-161">The following example shows the `StreamReaderEnumerable` in a LINQ query.</span></span>  
  
 [!code-vb[VbVbalrIteratorWalkthrough#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/Module1.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="d1758-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1758-162">See also</span></span>

- [<span data-ttu-id="d1758-163">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="d1758-163">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="d1758-164">控制流程</span><span class="sxs-lookup"><span data-stu-id="d1758-164">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="d1758-165">迴圈結構</span><span class="sxs-lookup"><span data-stu-id="d1758-165">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="d1758-166">For Each...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="d1758-166">For Each...Next Statement</span></span>](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
