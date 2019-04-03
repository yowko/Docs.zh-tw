---
title: 在 Visual Basic 中實作 IEnumerable
ms.date: 07/31/2018
helpviewer_keywords:
- control flow [Visual Basic]
- enumerable interfaces
- loop structures [Visual Basic], optimizing performance
- control flow [Visual Basic]
ms.assetid: c60d7589-51f2-4463-a2d5-22506bbc1554
ms.openlocfilehash: 5fc96e1ae3624adc197b5b13029498b9aa90c95e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819498"
---
# <a name="walkthrough-implementing-ienumerableof-t-in-visual-basic"></a><span data-ttu-id="a2253-102">逐步解說：在 Visual Basic 中實作 IEnumerable(Of T)</span><span class="sxs-lookup"><span data-stu-id="a2253-102">Walkthrough: Implementing IEnumerable(Of T) in Visual Basic</span></span>
<span data-ttu-id="a2253-103"><xref:System.Collections.Generic.IEnumerable%601>可以一次傳回的值的一個項目序列的類別會實作介面。</span><span class="sxs-lookup"><span data-stu-id="a2253-103">The <xref:System.Collections.Generic.IEnumerable%601> interface is implemented by classes that can return a sequence of values one item at a time.</span></span> <span data-ttu-id="a2253-104">傳回的資料一次的一個項目是您沒有將一組完整的資料載入記憶體，才能使用它的優點。</span><span class="sxs-lookup"><span data-stu-id="a2253-104">The advantage of returning data one item at a time is that you do not have to load the complete set of data into memory to work with it.</span></span> <span data-ttu-id="a2253-105">您只需要使用足夠的記憶體載入資料的單一項目。</span><span class="sxs-lookup"><span data-stu-id="a2253-105">You only have to use sufficient memory to load a single item from the data.</span></span> <span data-ttu-id="a2253-106">類別實作`IEnumerable(T)`介面可與`For Each`迴圈或 LINQ 查詢。</span><span class="sxs-lookup"><span data-stu-id="a2253-106">Classes that implement the `IEnumerable(T)` interface can be used with `For Each` loops or LINQ queries.</span></span>  
  
 <span data-ttu-id="a2253-107">例如，假設應用程式必須讀取大型文字檔，並傳回符合特定搜尋條件的檔案中的每一行。</span><span class="sxs-lookup"><span data-stu-id="a2253-107">For example, consider an application that must read a large text file and return each line from the file that matches particular search criteria.</span></span> <span data-ttu-id="a2253-108">應用程式會使用 LINQ 查詢，傳回符合指定的準則的檔案的行。</span><span class="sxs-lookup"><span data-stu-id="a2253-108">The application uses a LINQ query to return lines from the file that match the specified criteria.</span></span> <span data-ttu-id="a2253-109">若要使用 LINQ 查詢來查詢檔案的內容，應用程式無法載入檔案的內容是陣列或集合。</span><span class="sxs-lookup"><span data-stu-id="a2253-109">To query the contents of the file by using a LINQ query, the application could load the contents of the file into an array or a collection.</span></span> <span data-ttu-id="a2253-110">不過，將整個檔案載入陣列或集合會耗用超過所需的更多記憶體。</span><span class="sxs-lookup"><span data-stu-id="a2253-110">However, loading the whole file into an array or collection would consume far more memory than is required.</span></span> <span data-ttu-id="a2253-111">LINQ 查詢可以使用 enumerable 類別，傳回符合搜尋條件的值，改為查詢的檔案內容。</span><span class="sxs-lookup"><span data-stu-id="a2253-111">The LINQ query could instead query the file contents by using an enumerable class, returning only values that match the search criteria.</span></span> <span data-ttu-id="a2253-112">傳回只有少數的查詢比對值會耗用更少的記憶體。</span><span class="sxs-lookup"><span data-stu-id="a2253-112">Queries that return only a few matching values would consume far less memory.</span></span>  
  
 <span data-ttu-id="a2253-113">您可以建立可實作類別<xref:System.Collections.Generic.IEnumerable%601>介面公開為可列舉的資料來源資料。</span><span class="sxs-lookup"><span data-stu-id="a2253-113">You can create a class that implements the <xref:System.Collections.Generic.IEnumerable%601> interface to expose source data as enumerable data.</span></span> <span data-ttu-id="a2253-114">您的類別可實作`IEnumerable(T)`介面需要實作的另一個類別<xref:System.Collections.Generic.IEnumerator%601>來逐一查看來源資料的介面。</span><span class="sxs-lookup"><span data-stu-id="a2253-114">Your class that implements the `IEnumerable(T)` interface will require another class that implements the <xref:System.Collections.Generic.IEnumerator%601> interface to iterate through the source data.</span></span> <span data-ttu-id="a2253-115">這兩個類別可讓您依序為特定類型傳回的資料的項目。</span><span class="sxs-lookup"><span data-stu-id="a2253-115">These two classes enable you to return items of data sequentially as a specific type.</span></span>  
  
 <span data-ttu-id="a2253-116">本逐步解說中，您將建立一個類別，實作`IEnumerable(Of String)`介面和類別可實作`IEnumerator(Of String)`介面來讀取一次的文字檔案的一行。</span><span class="sxs-lookup"><span data-stu-id="a2253-116">In this walkthrough, you will create a class that implements the `IEnumerable(Of String)` interface and a class that implements the `IEnumerator(Of String)` interface to read a text file one line at a time.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-enumerable-class"></a><span data-ttu-id="a2253-117">建立列舉類別</span><span class="sxs-lookup"><span data-stu-id="a2253-117">Creating the Enumerable Class</span></span>  
  
<span data-ttu-id="a2253-118">**建立 enumerable 類別專案**</span><span class="sxs-lookup"><span data-stu-id="a2253-118">**Create the enumerable class project**</span></span>

1.  <span data-ttu-id="a2253-119">在 Visual Basic 中，在**檔案**功能表上，指向**新增**，然後按一下 **專案**。</span><span class="sxs-lookup"><span data-stu-id="a2253-119">In Visual Basic, on the **File** menu, point to **New** and then click **Project**.</span></span>

1.  <span data-ttu-id="a2253-120">在 [新增專案] 對話方塊的 [專案類型] 窗格中，確認已選取 [Windows]。</span><span class="sxs-lookup"><span data-stu-id="a2253-120">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="a2253-121">在 [範本] 窗格中，選取 [類別庫]。</span><span class="sxs-lookup"><span data-stu-id="a2253-121">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="a2253-122">在 [名稱] 方塊中，輸入 `StreamReaderEnumerable` 並按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="a2253-122">In the **Name** box, type `StreamReaderEnumerable`, and then click **OK**.</span></span> <span data-ttu-id="a2253-123">新的專案會顯示。</span><span class="sxs-lookup"><span data-stu-id="a2253-123">The new project is displayed.</span></span>

1.  <span data-ttu-id="a2253-124">在 **方案總管**，以滑鼠右鍵按一下 Class1.vb 檔案，然後按一下**重新命名**。</span><span class="sxs-lookup"><span data-stu-id="a2253-124">In **Solution Explorer**, right-click the Class1.vb file and click **Rename**.</span></span> <span data-ttu-id="a2253-125">將檔案重新命名為 `StreamReaderEnumerable.vb`，然後按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="a2253-125">Rename the file to `StreamReaderEnumerable.vb` and press ENTER.</span></span> <span data-ttu-id="a2253-126">重新命名檔案時，也會將類別重新命名為 `StreamReaderEnumerable`。</span><span class="sxs-lookup"><span data-stu-id="a2253-126">Renaming the file will also rename the class to `StreamReaderEnumerable`.</span></span> <span data-ttu-id="a2253-127">此類別會實作 `IEnumerable(Of String)` 介面。</span><span class="sxs-lookup"><span data-stu-id="a2253-127">This class will implement the `IEnumerable(Of String)` interface.</span></span>

1.  <span data-ttu-id="a2253-128">StreamReaderEnumerable 專案上按一下滑鼠右鍵，指向**新增**，然後按一下**新項目**。</span><span class="sxs-lookup"><span data-stu-id="a2253-128">Right-click the StreamReaderEnumerable project, point to **Add**, and then click **New Item**.</span></span> <span data-ttu-id="a2253-129">選取 **類別**範本。</span><span class="sxs-lookup"><span data-stu-id="a2253-129">Select the **Class** template.</span></span> <span data-ttu-id="a2253-130">在 **名稱**方塊中，輸入`StreamReaderEnumerator.vb`然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="a2253-130">In the **Name** box, type `StreamReaderEnumerator.vb` and click **OK**.</span></span>

 <span data-ttu-id="a2253-131">在此專案中的第一個類別是 enumerable 類別，並且會實作`IEnumerable(Of String)`介面。</span><span class="sxs-lookup"><span data-stu-id="a2253-131">The first class in this project is the enumerable class and will implement the `IEnumerable(Of String)` interface.</span></span> <span data-ttu-id="a2253-132">這個泛型介面實作<xref:System.Collections.IEnumerable>介面和這個類別的取用者可以存取做為輸入值的保證`String`。</span><span class="sxs-lookup"><span data-stu-id="a2253-132">This generic interface implements the <xref:System.Collections.IEnumerable> interface and guarantees that consumers of this class can access values typed as `String`.</span></span>  
  
<span data-ttu-id="a2253-133">**加入程式碼以實作 IEnumerable**</span><span class="sxs-lookup"><span data-stu-id="a2253-133">**Add the code to implement IEnumerable**</span></span>

1. <span data-ttu-id="a2253-134">開啟 StreamReaderEnumerable.vb 檔案。</span><span class="sxs-lookup"><span data-stu-id="a2253-134">Open the StreamReaderEnumerable.vb file.</span></span>

2. <span data-ttu-id="a2253-135">之後的行上`Public Class StreamReaderEnumerable`，輸入下列命令並按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="a2253-135">On the line after `Public Class StreamReaderEnumerable`, type the following and press ENTER.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#1)]

   <span data-ttu-id="a2253-136">Visual Basic 會自動填入所需的成員類別`IEnumerable(Of String)`介面。</span><span class="sxs-lookup"><span data-stu-id="a2253-136">Visual Basic automatically populates the class with the members that are required by the `IEnumerable(Of String)` interface.</span></span>
  
3. <span data-ttu-id="a2253-137">這個可列舉的類別會一次讀取行從文字檔案一列。</span><span class="sxs-lookup"><span data-stu-id="a2253-137">This enumerable class will read lines from a text file one line at a time.</span></span> <span data-ttu-id="a2253-138">將下列程式碼加入至類別公開的公用建構函式做為輸入參數的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="a2253-138">Add the following code to the class to expose a public constructor that takes a file path as an input parameter.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#2)]

4. <span data-ttu-id="a2253-139">您實作<xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A>方法`IEnumerable(Of String)`介面會傳回的新執行個體`StreamReaderEnumerator`類別。</span><span class="sxs-lookup"><span data-stu-id="a2253-139">Your implementation of the <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method of the `IEnumerable(Of String)` interface will return a new instance of the `StreamReaderEnumerator` class.</span></span> <span data-ttu-id="a2253-140">實作`GetEnumerator`方法`IEnumerable`介面可以成為`Private`，因為您不必只成員公開`IEnumerable(Of String)`介面。</span><span class="sxs-lookup"><span data-stu-id="a2253-140">The implementation of the `GetEnumerator` method of the `IEnumerable` interface can be made `Private`, because you have to expose only members of the `IEnumerable(Of String)` interface.</span></span> <span data-ttu-id="a2253-141">取代為所產生的 Visual Basic 程式碼`GetEnumerator`為下列程式碼的方法。</span><span class="sxs-lookup"><span data-stu-id="a2253-141">Replace the code that Visual Basic generated for the `GetEnumerator` methods with the following code.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#3)]  
  
<span data-ttu-id="a2253-142">**加入程式碼以實作 IEnumerator**</span><span class="sxs-lookup"><span data-stu-id="a2253-142">**Add the code to implement IEnumerator**</span></span>

1. <span data-ttu-id="a2253-143">開啟 StreamReaderEnumerator.vb 檔案。</span><span class="sxs-lookup"><span data-stu-id="a2253-143">Open the StreamReaderEnumerator.vb file.</span></span>

2. <span data-ttu-id="a2253-144">之後的行上`Public Class StreamReaderEnumerator`，輸入下列命令並按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="a2253-144">On the line after `Public Class StreamReaderEnumerator`, type the following and press ENTER.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#4)]

   <span data-ttu-id="a2253-145">Visual Basic 會自動填入所需的成員類別`IEnumerator(Of String)`介面。</span><span class="sxs-lookup"><span data-stu-id="a2253-145">Visual Basic automatically populates the class with the members that are required by the `IEnumerator(Of String)` interface.</span></span>

3. <span data-ttu-id="a2253-146">列舉值類別開啟文字檔，並執行檔案 I/O，若要從檔案讀取的行。</span><span class="sxs-lookup"><span data-stu-id="a2253-146">The enumerator class opens the text file and performs the file I/O to read the lines from the file.</span></span> <span data-ttu-id="a2253-147">將下列程式碼加入至類別公開的公用建構函式做為輸入參數的檔案路徑，並開啟文字檔案進行讀取。</span><span class="sxs-lookup"><span data-stu-id="a2253-147">Add the following code to the class to expose a public constructor that takes a file path as an input parameter and open the text file for reading.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#5)]

4. <span data-ttu-id="a2253-148">`Current`屬性兩者`IEnumerator(Of String)`並`IEnumerator`介面會傳回目前的項目從文字檔`String`。</span><span class="sxs-lookup"><span data-stu-id="a2253-148">The `Current` properties for both the `IEnumerator(Of String)` and `IEnumerator` interfaces return the current item from the text file as a `String`.</span></span> <span data-ttu-id="a2253-149">實作`Current`的屬性`IEnumerator`介面可以成為`Private`，因為您不必只成員公開`IEnumerator(Of String)`介面。</span><span class="sxs-lookup"><span data-stu-id="a2253-149">The implementation of the `Current` property of the `IEnumerator` interface can be made `Private`, because you have to expose only members of the `IEnumerator(Of String)` interface.</span></span> <span data-ttu-id="a2253-150">取代為所產生的 Visual Basic 程式碼`Current`為下列程式碼的屬性。</span><span class="sxs-lookup"><span data-stu-id="a2253-150">Replace the code that Visual Basic generated for the `Current` properties with the following code.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#6)]

5. <span data-ttu-id="a2253-151">`MoveNext`方法`IEnumerator`介面瀏覽到文字檔中的下一個項目，並更新所傳回的值`Current`屬性。</span><span class="sxs-lookup"><span data-stu-id="a2253-151">The `MoveNext` method of the `IEnumerator` interface navigates to the next item in the text file and updates the value that is returned by the `Current` property.</span></span> <span data-ttu-id="a2253-152">若要閱讀，沒有其他項目是否`MoveNext`方法會傳回`False`; 否則為`MoveNext`方法會傳回`True`。</span><span class="sxs-lookup"><span data-stu-id="a2253-152">If there are no more items to read, the `MoveNext` method returns `False`; otherwise the `MoveNext` method returns `True`.</span></span> <span data-ttu-id="a2253-153">將下列程式碼加入至 `MoveNext` 方法。</span><span class="sxs-lookup"><span data-stu-id="a2253-153">Add the following code to the `MoveNext` method.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#7)]

6. <span data-ttu-id="a2253-154">`Reset`方法的`IEnumerator`介面會指示迭代器，指向 文字檔的開始，並清除目前的項目值。</span><span class="sxs-lookup"><span data-stu-id="a2253-154">The `Reset` method of the `IEnumerator` interface directs the iterator to point to the start of the text file and clears the current item value.</span></span> <span data-ttu-id="a2253-155">將下列程式碼加入至 `Reset` 方法。</span><span class="sxs-lookup"><span data-stu-id="a2253-155">Add the following code to the `Reset` method.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#8)]

7. <span data-ttu-id="a2253-156">`Dispose`方法的`IEnumerator`介面可確保提供迭代器終結之前，就會釋放所有的 unmanaged 的資源。</span><span class="sxs-lookup"><span data-stu-id="a2253-156">The `Dispose` method of the `IEnumerator` interface guarantees that all unmanaged resources are released before the iterator is destroyed.</span></span> <span data-ttu-id="a2253-157">檔案控制代碼，以供`StreamReader`物件是 unmanaged 的資源，而且必須先關閉終結迭代器執行個體。</span><span class="sxs-lookup"><span data-stu-id="a2253-157">The file handle that is used by the `StreamReader` object is an unmanaged resource and must be closed before the iterator instance is destroyed.</span></span> <span data-ttu-id="a2253-158">取代為所產生的 Visual Basic 程式碼`Dispose`為下列程式碼的方法。</span><span class="sxs-lookup"><span data-stu-id="a2253-158">Replace the code that Visual Basic generated for the `Dispose` method with the following code.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#9)] 
  
## <a name="using-the-sample-iterator"></a><span data-ttu-id="a2253-159">使用範例迭代器</span><span class="sxs-lookup"><span data-stu-id="a2253-159">Using the Sample Iterator</span></span>

 <span data-ttu-id="a2253-160">您可以使用 enumerable 類別，在您的程式碼，以及需要實作的物件的控制結構`IEnumerable`，例如`For Next`迴圈或 LINQ 查詢。</span><span class="sxs-lookup"><span data-stu-id="a2253-160">You can use an enumerable class in your code together with control structures that require an object that implements `IEnumerable`, such as a `For Next` loop or a LINQ query.</span></span> <span data-ttu-id="a2253-161">下列範例所示`StreamReaderEnumerable`LINQ 查詢中。</span><span class="sxs-lookup"><span data-stu-id="a2253-161">The following example shows the `StreamReaderEnumerable` in a LINQ query.</span></span>  
  
 [!code-vb[VbVbalrIteratorWalkthrough#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/Module1.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="a2253-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2253-162">See also</span></span>

- [<span data-ttu-id="a2253-163">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="a2253-163">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="a2253-164">控制流程</span><span class="sxs-lookup"><span data-stu-id="a2253-164">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="a2253-165">迴圈結構</span><span class="sxs-lookup"><span data-stu-id="a2253-165">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="a2253-166">For Each...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="a2253-166">For Each...Next Statement</span></span>](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
