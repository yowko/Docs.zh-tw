---
title: 執行 IEnumerable
ms.date: 07/31/2018
helpviewer_keywords:
- control flow [Visual Basic]
- enumerable interfaces
- loop structures [Visual Basic], optimizing performance
- control flow [Visual Basic]
ms.assetid: c60d7589-51f2-4463-a2d5-22506bbc1554
ms.openlocfilehash: f1f0036c38299f2392f8c8705e67b7bb6b7db068
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058634"
---
# <a name="walkthrough-implementing-ienumerableof-t-in-visual-basic"></a><span data-ttu-id="ea00d-102">逐步解說：在 Visual Basic 中實作 IEnumerable(Of T)</span><span class="sxs-lookup"><span data-stu-id="ea00d-102">Walkthrough: Implementing IEnumerable(Of T) in Visual Basic</span></span>

<span data-ttu-id="ea00d-103"><xref:System.Collections.Generic.IEnumerable%601>介面是由可傳回一次一個專案的一系列值的類別所執行。</span><span class="sxs-lookup"><span data-stu-id="ea00d-103">The <xref:System.Collections.Generic.IEnumerable%601> interface is implemented by classes that can return a sequence of values one item at a time.</span></span> <span data-ttu-id="ea00d-104">一次只傳回一個專案的優點是，您不需要將一組完整的資料載入記憶體中，就能使用它。</span><span class="sxs-lookup"><span data-stu-id="ea00d-104">The advantage of returning data one item at a time is that you do not have to load the complete set of data into memory to work with it.</span></span> <span data-ttu-id="ea00d-105">您只需要使用足夠的記憶體從資料載入單一專案。</span><span class="sxs-lookup"><span data-stu-id="ea00d-105">You only have to use sufficient memory to load a single item from the data.</span></span> <span data-ttu-id="ea00d-106">執行介面的類別 `IEnumerable(T)` 可以搭配 `For Each` 迴圈或 LINQ 查詢使用。</span><span class="sxs-lookup"><span data-stu-id="ea00d-106">Classes that implement the `IEnumerable(T)` interface can be used with `For Each` loops or LINQ queries.</span></span>  
  
 <span data-ttu-id="ea00d-107">例如，假設應用程式必須讀取大型文字檔，並從符合特定搜尋準則的檔案傳回每一行。</span><span class="sxs-lookup"><span data-stu-id="ea00d-107">For example, consider an application that must read a large text file and return each line from the file that matches particular search criteria.</span></span> <span data-ttu-id="ea00d-108">應用程式會使用 LINQ 查詢，從檔案傳回符合指定準則的行。</span><span class="sxs-lookup"><span data-stu-id="ea00d-108">The application uses a LINQ query to return lines from the file that match the specified criteria.</span></span> <span data-ttu-id="ea00d-109">若要使用 LINQ 查詢來查詢檔案的內容，應用程式可以將檔案的內容載入陣列或集合中。</span><span class="sxs-lookup"><span data-stu-id="ea00d-109">To query the contents of the file by using a LINQ query, the application could load the contents of the file into an array or a collection.</span></span> <span data-ttu-id="ea00d-110">不過，將整個檔案載入至陣列或集合中的記憶體，會比所需的記憶體多出許多。</span><span class="sxs-lookup"><span data-stu-id="ea00d-110">However, loading the whole file into an array or collection would consume far more memory than is required.</span></span> <span data-ttu-id="ea00d-111">LINQ 查詢可以改為使用可列舉類別來查詢檔案內容，只傳回符合搜尋準則的值。</span><span class="sxs-lookup"><span data-stu-id="ea00d-111">The LINQ query could instead query the file contents by using an enumerable class, returning only values that match the search criteria.</span></span> <span data-ttu-id="ea00d-112">只傳回幾個相符值的查詢會耗用較少的記憶體。</span><span class="sxs-lookup"><span data-stu-id="ea00d-112">Queries that return only a few matching values would consume far less memory.</span></span>  
  
 <span data-ttu-id="ea00d-113">您可以建立一個類別來執行 <xref:System.Collections.Generic.IEnumerable%601> 介面，以將來源資料公開為可列舉的資料。</span><span class="sxs-lookup"><span data-stu-id="ea00d-113">You can create a class that implements the <xref:System.Collections.Generic.IEnumerable%601> interface to expose source data as enumerable data.</span></span> <span data-ttu-id="ea00d-114">您執行介面的類別 `IEnumerable(T)` 需要另一個類別來 <xref:System.Collections.Generic.IEnumerator%601> 執行介面，以逐一查看來源資料。</span><span class="sxs-lookup"><span data-stu-id="ea00d-114">Your class that implements the `IEnumerable(T)` interface will require another class that implements the <xref:System.Collections.Generic.IEnumerator%601> interface to iterate through the source data.</span></span> <span data-ttu-id="ea00d-115">這兩個類別可讓您以特定類型的順序傳回資料的專案。</span><span class="sxs-lookup"><span data-stu-id="ea00d-115">These two classes enable you to return items of data sequentially as a specific type.</span></span>  
  
 <span data-ttu-id="ea00d-116">在這個逐步解說中，您將建立一個類別，它會執行 `IEnumerable(Of String)` 介面和一個類別，該類別會 `IEnumerator(Of String)` 執行介面，一次一行讀取文字檔。</span><span class="sxs-lookup"><span data-stu-id="ea00d-116">In this walkthrough, you will create a class that implements the `IEnumerable(Of String)` interface and a class that implements the `IEnumerator(Of String)` interface to read a text file one line at a time.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-enumerable-class"></a><span data-ttu-id="ea00d-117">建立可列舉類別</span><span class="sxs-lookup"><span data-stu-id="ea00d-117">Creating the Enumerable Class</span></span>  
  
<span data-ttu-id="ea00d-118">**建立可列舉類別專案**</span><span class="sxs-lookup"><span data-stu-id="ea00d-118">**Create the enumerable class project**</span></span>

1. <span data-ttu-id="ea00d-119">在 Visual Basic **的 [檔案** ] 功能表上，指向 [ **新增** ]，然後按一下 [ **專案**]。</span><span class="sxs-lookup"><span data-stu-id="ea00d-119">In Visual Basic, on the **File** menu, point to **New** and then click **Project**.</span></span>

1. <span data-ttu-id="ea00d-120">在 [新增專案]\*\*\*\* 對話方塊的 [專案類型]\*\*\*\* 窗格中，確認已選取 [Windows]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ea00d-120">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="ea00d-121">在 [範本]\*\*\*\* 窗格中，選取 [類別庫]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ea00d-121">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="ea00d-122">在 [名稱]\*\*\*\* 方塊中，輸入 `StreamReaderEnumerable` 並按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ea00d-122">In the **Name** box, type `StreamReaderEnumerable`, and then click **OK**.</span></span> <span data-ttu-id="ea00d-123">新的專案隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="ea00d-123">The new project is displayed.</span></span>

1. <span data-ttu-id="ea00d-124">在 **方案總管**中，以滑鼠右鍵按一下 Class1 檔案，然後按一下 [ **重新命名**]。</span><span class="sxs-lookup"><span data-stu-id="ea00d-124">In **Solution Explorer**, right-click the Class1.vb file and click **Rename**.</span></span> <span data-ttu-id="ea00d-125">將檔案重新命名為 `StreamReaderEnumerable.vb`，然後按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="ea00d-125">Rename the file to `StreamReaderEnumerable.vb` and press ENTER.</span></span> <span data-ttu-id="ea00d-126">重新命名檔案時，也會將類別重新命名為 `StreamReaderEnumerable`。</span><span class="sxs-lookup"><span data-stu-id="ea00d-126">Renaming the file will also rename the class to `StreamReaderEnumerable`.</span></span> <span data-ttu-id="ea00d-127">此類別會實作 `IEnumerable(Of String)` 介面。</span><span class="sxs-lookup"><span data-stu-id="ea00d-127">This class will implement the `IEnumerable(Of String)` interface.</span></span>

1. <span data-ttu-id="ea00d-128">以滑鼠右鍵按一下 StreamReaderEnumerable 專案，指向 [ **加入**]，然後按一下 [ **新增專案**]。</span><span class="sxs-lookup"><span data-stu-id="ea00d-128">Right-click the StreamReaderEnumerable project, point to **Add**, and then click **New Item**.</span></span> <span data-ttu-id="ea00d-129">選取 [ **類別** ] 範本。</span><span class="sxs-lookup"><span data-stu-id="ea00d-129">Select the **Class** template.</span></span> <span data-ttu-id="ea00d-130">在 [名稱]\*\*\*\* 方塊中輸入 `StreamReaderEnumerator.vb`，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="ea00d-130">In the **Name** box, type `StreamReaderEnumerator.vb` and click **OK**.</span></span>

 <span data-ttu-id="ea00d-131">此專案中的第一個類別是可列舉的類別，而且將會執行 `IEnumerable(Of String)` 介面。</span><span class="sxs-lookup"><span data-stu-id="ea00d-131">The first class in this project is the enumerable class and will implement the `IEnumerable(Of String)` interface.</span></span> <span data-ttu-id="ea00d-132">這個泛型介面會實 <xref:System.Collections.IEnumerable> 作為介面，並保證這個類別的取用者可以存取輸入的值 `String` 。</span><span class="sxs-lookup"><span data-stu-id="ea00d-132">This generic interface implements the <xref:System.Collections.IEnumerable> interface and guarantees that consumers of this class can access values typed as `String`.</span></span>  
  
<span data-ttu-id="ea00d-133">**新增程式碼以執行 IEnumerable**</span><span class="sxs-lookup"><span data-stu-id="ea00d-133">**Add the code to implement IEnumerable**</span></span>

1. <span data-ttu-id="ea00d-134">開啟 StreamReaderEnumerable .vb 檔案。</span><span class="sxs-lookup"><span data-stu-id="ea00d-134">Open the StreamReaderEnumerable.vb file.</span></span>

2. <span data-ttu-id="ea00d-135">在 [後行] `Public Class StreamReaderEnumerable` 中，輸入下列程式碼，然後按 enter 鍵。</span><span class="sxs-lookup"><span data-stu-id="ea00d-135">On the line after `Public Class StreamReaderEnumerable`, type the following and press ENTER.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#1)]

   <span data-ttu-id="ea00d-136">Visual Basic 會自動將介面所需的成員填入類別 `IEnumerable(Of String)` 。</span><span class="sxs-lookup"><span data-stu-id="ea00d-136">Visual Basic automatically populates the class with the members that are required by the `IEnumerable(Of String)` interface.</span></span>
  
3. <span data-ttu-id="ea00d-137">這個可列舉類別會一次從文字檔讀取一行。</span><span class="sxs-lookup"><span data-stu-id="ea00d-137">This enumerable class will read lines from a text file one line at a time.</span></span> <span data-ttu-id="ea00d-138">將下列程式碼加入至類別，以公開接受檔案路徑做為輸入參數的公用函式。</span><span class="sxs-lookup"><span data-stu-id="ea00d-138">Add the following code to the class to expose a public constructor that takes a file path as an input parameter.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#2)]

4. <span data-ttu-id="ea00d-139">您對介面的 <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> 方法的執行 `IEnumerable(Of String)` 將會傳回類別的新實例 `StreamReaderEnumerator` 。</span><span class="sxs-lookup"><span data-stu-id="ea00d-139">Your implementation of the <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method of the `IEnumerable(Of String)` interface will return a new instance of the `StreamReaderEnumerator` class.</span></span> <span data-ttu-id="ea00d-140">`GetEnumerator` `IEnumerable` 您可以執行介面的方法 `Private` ，因為您必須只公開介面的成員 `IEnumerable(Of String)` 。</span><span class="sxs-lookup"><span data-stu-id="ea00d-140">The implementation of the `GetEnumerator` method of the `IEnumerable` interface can be made `Private`, because you have to expose only members of the `IEnumerable(Of String)` interface.</span></span> <span data-ttu-id="ea00d-141">以下列程式碼取代 Visual Basic 為方法產生的程式碼 `GetEnumerator` 。</span><span class="sxs-lookup"><span data-stu-id="ea00d-141">Replace the code that Visual Basic generated for the `GetEnumerator` methods with the following code.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#3)]  
  
<span data-ttu-id="ea00d-142">**新增程式碼以執行 IEnumerator**</span><span class="sxs-lookup"><span data-stu-id="ea00d-142">**Add the code to implement IEnumerator**</span></span>

1. <span data-ttu-id="ea00d-143">開啟 StreamReaderEnumerator .vb 檔案。</span><span class="sxs-lookup"><span data-stu-id="ea00d-143">Open the StreamReaderEnumerator.vb file.</span></span>

2. <span data-ttu-id="ea00d-144">在 [後行] `Public Class StreamReaderEnumerator` 中，輸入下列程式碼，然後按 enter 鍵。</span><span class="sxs-lookup"><span data-stu-id="ea00d-144">On the line after `Public Class StreamReaderEnumerator`, type the following and press ENTER.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#4)]

   <span data-ttu-id="ea00d-145">Visual Basic 會自動將介面所需的成員填入類別 `IEnumerator(Of String)` 。</span><span class="sxs-lookup"><span data-stu-id="ea00d-145">Visual Basic automatically populates the class with the members that are required by the `IEnumerator(Of String)` interface.</span></span>

3. <span data-ttu-id="ea00d-146">列舉值類別會開啟文字檔，並執行檔案 i/o 以讀取檔案中的行。</span><span class="sxs-lookup"><span data-stu-id="ea00d-146">The enumerator class opens the text file and performs the file I/O to read the lines from the file.</span></span> <span data-ttu-id="ea00d-147">將下列程式碼加入至類別，以公開公用的函式，該函式會使用檔案路徑做為輸入參數，並開啟文字檔進行讀取。</span><span class="sxs-lookup"><span data-stu-id="ea00d-147">Add the following code to the class to expose a public constructor that takes a file path as an input parameter and open the text file for reading.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#5)]

4. <span data-ttu-id="ea00d-148">`Current`和介面的屬性會 `IEnumerator(Of String)` `IEnumerator` 從文字檔傳回目前的專案做為 `String` 。</span><span class="sxs-lookup"><span data-stu-id="ea00d-148">The `Current` properties for both the `IEnumerator(Of String)` and `IEnumerator` interfaces return the current item from the text file as a `String`.</span></span> <span data-ttu-id="ea00d-149">`Current` `IEnumerator` `Private` 因為您必須只公開介面的成員，所以可以執行介面的屬性 `IEnumerator(Of String)` 。</span><span class="sxs-lookup"><span data-stu-id="ea00d-149">The implementation of the `Current` property of the `IEnumerator` interface can be made `Private`, because you have to expose only members of the `IEnumerator(Of String)` interface.</span></span> <span data-ttu-id="ea00d-150">以下列程式碼取代 Visual Basic 為屬性產生的程式碼 `Current` 。</span><span class="sxs-lookup"><span data-stu-id="ea00d-150">Replace the code that Visual Basic generated for the `Current` properties with the following code.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#6)]

5. <span data-ttu-id="ea00d-151">`MoveNext`介面的方法會 `IEnumerator` 流覽至文字檔中的下一個專案，並更新屬性所傳回的值 `Current` 。</span><span class="sxs-lookup"><span data-stu-id="ea00d-151">The `MoveNext` method of the `IEnumerator` interface navigates to the next item in the text file and updates the value that is returned by the `Current` property.</span></span> <span data-ttu-id="ea00d-152">如果沒有其他要讀取的專案，方法會傳回 `MoveNext` `False` ; 否則， `MoveNext` 方法 `True` 會傳回。</span><span class="sxs-lookup"><span data-stu-id="ea00d-152">If there are no more items to read, the `MoveNext` method returns `False`; otherwise the `MoveNext` method returns `True`.</span></span> <span data-ttu-id="ea00d-153">將下列程式碼新增至 `MoveNext` 方法。</span><span class="sxs-lookup"><span data-stu-id="ea00d-153">Add the following code to the `MoveNext` method.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#7)]

6. <span data-ttu-id="ea00d-154">`Reset`介面的方法會 `IEnumerator` 指示反覆運算器指向文字檔的開頭，並清除目前的專案值。</span><span class="sxs-lookup"><span data-stu-id="ea00d-154">The `Reset` method of the `IEnumerator` interface directs the iterator to point to the start of the text file and clears the current item value.</span></span> <span data-ttu-id="ea00d-155">將下列程式碼新增至 `Reset` 方法。</span><span class="sxs-lookup"><span data-stu-id="ea00d-155">Add the following code to the `Reset` method.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#8)]

7. <span data-ttu-id="ea00d-156">`Dispose`介面的方法可 `IEnumerator` 保證在反覆運算器終結之前釋放所有非受控資源。</span><span class="sxs-lookup"><span data-stu-id="ea00d-156">The `Dispose` method of the `IEnumerator` interface guarantees that all unmanaged resources are released before the iterator is destroyed.</span></span> <span data-ttu-id="ea00d-157">物件所使用的檔案控制代碼 `StreamReader` 是未受管理的資源，而且必須在終結 iterator 實例之前關閉。</span><span class="sxs-lookup"><span data-stu-id="ea00d-157">The file handle that is used by the `StreamReader` object is an unmanaged resource and must be closed before the iterator instance is destroyed.</span></span> <span data-ttu-id="ea00d-158">以下列程式碼取代 Visual Basic 為方法產生的程式碼 `Dispose` 。</span><span class="sxs-lookup"><span data-stu-id="ea00d-158">Replace the code that Visual Basic generated for the `Dispose` method with the following code.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#9)]
  
## <a name="using-the-sample-iterator"></a><span data-ttu-id="ea00d-159">使用範例反覆運算器</span><span class="sxs-lookup"><span data-stu-id="ea00d-159">Using the Sample Iterator</span></span>

 <span data-ttu-id="ea00d-160">您可以使用程式碼中的可列舉類別，以及需要執行物件（ `IEnumerable` 例如 `For Next` 迴圈或 LINQ 查詢）的控制結構。</span><span class="sxs-lookup"><span data-stu-id="ea00d-160">You can use an enumerable class in your code together with control structures that require an object that implements `IEnumerable`, such as a `For Next` loop or a LINQ query.</span></span> <span data-ttu-id="ea00d-161">下列範例顯示 `StreamReaderEnumerable` LINQ 查詢中的。</span><span class="sxs-lookup"><span data-stu-id="ea00d-161">The following example shows the `StreamReaderEnumerable` in a LINQ query.</span></span>  
  
 [!code-vb[VbVbalrIteratorWalkthrough#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/Module1.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="ea00d-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea00d-162">See also</span></span>

- [<span data-ttu-id="ea00d-163">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="ea00d-163">Introduction to LINQ in Visual Basic</span></span>](../linq/introduction-to-linq.md)
- [<span data-ttu-id="ea00d-164">控制流程</span><span class="sxs-lookup"><span data-stu-id="ea00d-164">Control Flow</span></span>](index.md)
- [<span data-ttu-id="ea00d-165">迴圈結構</span><span class="sxs-lookup"><span data-stu-id="ea00d-165">Loop Structures</span></span>](loop-structures.md)
- [<span data-ttu-id="ea00d-166">For Each...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="ea00d-166">For Each...Next Statement</span></span>](../../../language-reference/statements/for-each-next-statement.md)
