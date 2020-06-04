---
title: 執行 IEnumerable
ms.date: 07/31/2018
helpviewer_keywords:
- control flow [Visual Basic]
- enumerable interfaces
- loop structures [Visual Basic], optimizing performance
- control flow [Visual Basic]
ms.assetid: c60d7589-51f2-4463-a2d5-22506bbc1554
ms.openlocfilehash: 582957c91eac63cf7f72dd2f6c0cf40e627be686
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402027"
---
# <a name="walkthrough-implementing-ienumerableof-t-in-visual-basic"></a><span data-ttu-id="0d447-102">逐步解說：在 Visual Basic 中實作 IEnumerable(Of T)</span><span class="sxs-lookup"><span data-stu-id="0d447-102">Walkthrough: Implementing IEnumerable(Of T) in Visual Basic</span></span>
<span data-ttu-id="0d447-103"><xref:System.Collections.Generic.IEnumerable%601>介面是由類別所實，可以一次傳回一個專案的一連串值。</span><span class="sxs-lookup"><span data-stu-id="0d447-103">The <xref:System.Collections.Generic.IEnumerable%601> interface is implemented by classes that can return a sequence of values one item at a time.</span></span> <span data-ttu-id="0d447-104">將資料一次傳回一個專案的優點是，您不需要將一組完整的資料載入記憶體中，就可以使用它。</span><span class="sxs-lookup"><span data-stu-id="0d447-104">The advantage of returning data one item at a time is that you do not have to load the complete set of data into memory to work with it.</span></span> <span data-ttu-id="0d447-105">您只需要使用足夠的記憶體，即可從資料載入單一專案。</span><span class="sxs-lookup"><span data-stu-id="0d447-105">You only have to use sufficient memory to load a single item from the data.</span></span> <span data-ttu-id="0d447-106">執行介面的類別 `IEnumerable(T)` 可以搭配 `For Each` 迴圈或 LINQ 查詢使用。</span><span class="sxs-lookup"><span data-stu-id="0d447-106">Classes that implement the `IEnumerable(T)` interface can be used with `For Each` loops or LINQ queries.</span></span>  
  
 <span data-ttu-id="0d447-107">例如，假設有一個應用程式必須讀取大型文字檔，並從檔案傳回符合特定搜尋條件的每一行。</span><span class="sxs-lookup"><span data-stu-id="0d447-107">For example, consider an application that must read a large text file and return each line from the file that matches particular search criteria.</span></span> <span data-ttu-id="0d447-108">應用程式會使用 LINQ 查詢來傳回檔案中符合指定準則的行。</span><span class="sxs-lookup"><span data-stu-id="0d447-108">The application uses a LINQ query to return lines from the file that match the specified criteria.</span></span> <span data-ttu-id="0d447-109">若要使用 LINQ 查詢來查詢檔案的內容，應用程式可以將檔案內容載入陣列或集合中。</span><span class="sxs-lookup"><span data-stu-id="0d447-109">To query the contents of the file by using a LINQ query, the application could load the contents of the file into an array or a collection.</span></span> <span data-ttu-id="0d447-110">不過，將整個檔案載入陣列或集合會耗用比所需更多的記憶體。</span><span class="sxs-lookup"><span data-stu-id="0d447-110">However, loading the whole file into an array or collection would consume far more memory than is required.</span></span> <span data-ttu-id="0d447-111">LINQ 查詢可以改為使用可列舉的類別來查詢檔案內容，只傳回符合搜尋條件的值。</span><span class="sxs-lookup"><span data-stu-id="0d447-111">The LINQ query could instead query the file contents by using an enumerable class, returning only values that match the search criteria.</span></span> <span data-ttu-id="0d447-112">只傳回幾個相符值的查詢會耗用較少的記憶體。</span><span class="sxs-lookup"><span data-stu-id="0d447-112">Queries that return only a few matching values would consume far less memory.</span></span>  
  
 <span data-ttu-id="0d447-113">您可以建立一個類別來執行 <xref:System.Collections.Generic.IEnumerable%601> 介面，以將來源資料公開為可列舉的資料。</span><span class="sxs-lookup"><span data-stu-id="0d447-113">You can create a class that implements the <xref:System.Collections.Generic.IEnumerable%601> interface to expose source data as enumerable data.</span></span> <span data-ttu-id="0d447-114">您的類別若 `IEnumerable(T)` 要執行介面，將需要另一個實作為介面的類別， <xref:System.Collections.Generic.IEnumerator%601> 以反復處理來源資料。</span><span class="sxs-lookup"><span data-stu-id="0d447-114">Your class that implements the `IEnumerable(T)` interface will require another class that implements the <xref:System.Collections.Generic.IEnumerator%601> interface to iterate through the source data.</span></span> <span data-ttu-id="0d447-115">這兩個類別可讓您以特定類型順序傳回資料的專案。</span><span class="sxs-lookup"><span data-stu-id="0d447-115">These two classes enable you to return items of data sequentially as a specific type.</span></span>  
  
 <span data-ttu-id="0d447-116">在此逐步解說中，您將建立一個執行介面的類別，以及一個執行介面的類別，以便一 `IEnumerable(Of String)` `IEnumerator(Of String)` 次一行讀取文字檔。</span><span class="sxs-lookup"><span data-stu-id="0d447-116">In this walkthrough, you will create a class that implements the `IEnumerable(Of String)` interface and a class that implements the `IEnumerator(Of String)` interface to read a text file one line at a time.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-the-enumerable-class"></a><span data-ttu-id="0d447-117">建立可列舉類別</span><span class="sxs-lookup"><span data-stu-id="0d447-117">Creating the Enumerable Class</span></span>  
  
<span data-ttu-id="0d447-118">**建立可列舉的類別專案**</span><span class="sxs-lookup"><span data-stu-id="0d447-118">**Create the enumerable class project**</span></span>

1. <span data-ttu-id="0d447-119">**在 Visual Basic 的 [檔案**] 功能表上，指向 [**新增**]，然後按一下 [**專案**]。</span><span class="sxs-lookup"><span data-stu-id="0d447-119">In Visual Basic, on the **File** menu, point to **New** and then click **Project**.</span></span>

1. <span data-ttu-id="0d447-120">在 [新增專案]\*\*\*\* 對話方塊的 [專案類型]\*\*\*\* 窗格中，確認已選取 [Windows]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0d447-120">In the **New Project** dialog box, in the **Project Types** pane, make sure that **Windows** is selected.</span></span> <span data-ttu-id="0d447-121">在 [範本]\*\*\*\* 窗格中，選取 [類別庫]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0d447-121">Select **Class Library** in the **Templates** pane.</span></span> <span data-ttu-id="0d447-122">在 [名稱]\*\*\*\* 方塊中，輸入 `StreamReaderEnumerable` 並按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0d447-122">In the **Name** box, type `StreamReaderEnumerable`, and then click **OK**.</span></span> <span data-ttu-id="0d447-123">隨即顯示新專案。</span><span class="sxs-lookup"><span data-stu-id="0d447-123">The new project is displayed.</span></span>

1. <span data-ttu-id="0d447-124">在**方案總管**中，以滑鼠右鍵按一下 [Class1] 檔案，然後按一下 [**重新命名**]。</span><span class="sxs-lookup"><span data-stu-id="0d447-124">In **Solution Explorer**, right-click the Class1.vb file and click **Rename**.</span></span> <span data-ttu-id="0d447-125">將檔案重新命名為 `StreamReaderEnumerable.vb`，然後按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="0d447-125">Rename the file to `StreamReaderEnumerable.vb` and press ENTER.</span></span> <span data-ttu-id="0d447-126">重新命名檔案時，也會將類別重新命名為 `StreamReaderEnumerable`。</span><span class="sxs-lookup"><span data-stu-id="0d447-126">Renaming the file will also rename the class to `StreamReaderEnumerable`.</span></span> <span data-ttu-id="0d447-127">此類別會實作 `IEnumerable(Of String)` 介面。</span><span class="sxs-lookup"><span data-stu-id="0d447-127">This class will implement the `IEnumerable(Of String)` interface.</span></span>

1. <span data-ttu-id="0d447-128">以滑鼠右鍵按一下 [StreamReaderEnumerable] 專案，指向 [**加入**]，然後按一下 [**新增專案**]。</span><span class="sxs-lookup"><span data-stu-id="0d447-128">Right-click the StreamReaderEnumerable project, point to **Add**, and then click **New Item**.</span></span> <span data-ttu-id="0d447-129">選取 [**類別**] 範本。</span><span class="sxs-lookup"><span data-stu-id="0d447-129">Select the **Class** template.</span></span> <span data-ttu-id="0d447-130">在 [名稱]\*\*\*\* 方塊中輸入 `StreamReaderEnumerator.vb`，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0d447-130">In the **Name** box, type `StreamReaderEnumerator.vb` and click **OK**.</span></span>

 <span data-ttu-id="0d447-131">這個專案中的第一個類別是可列舉的類別，並會執行 `IEnumerable(Of String)` 介面。</span><span class="sxs-lookup"><span data-stu-id="0d447-131">The first class in this project is the enumerable class and will implement the `IEnumerable(Of String)` interface.</span></span> <span data-ttu-id="0d447-132">這個泛型介面會執行 <xref:System.Collections.IEnumerable> 介面，並保證這個類別的取用者可以存取輸入為的值 `String` 。</span><span class="sxs-lookup"><span data-stu-id="0d447-132">This generic interface implements the <xref:System.Collections.IEnumerable> interface and guarantees that consumers of this class can access values typed as `String`.</span></span>  
  
<span data-ttu-id="0d447-133">**新增程式碼以執行 IEnumerable**</span><span class="sxs-lookup"><span data-stu-id="0d447-133">**Add the code to implement IEnumerable**</span></span>

1. <span data-ttu-id="0d447-134">開啟 [StreamReaderEnumerable] 檔案。</span><span class="sxs-lookup"><span data-stu-id="0d447-134">Open the StreamReaderEnumerable.vb file.</span></span>

2. <span data-ttu-id="0d447-135">在後面的一行 `Public Class StreamReaderEnumerable` 中，輸入下列程式碼，然後按 enter 鍵。</span><span class="sxs-lookup"><span data-stu-id="0d447-135">On the line after `Public Class StreamReaderEnumerable`, type the following and press ENTER.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#1)]

   <span data-ttu-id="0d447-136">Visual Basic 會使用介面所需的成員，自動填入類別 `IEnumerable(Of String)` 。</span><span class="sxs-lookup"><span data-stu-id="0d447-136">Visual Basic automatically populates the class with the members that are required by the `IEnumerable(Of String)` interface.</span></span>
  
3. <span data-ttu-id="0d447-137">這個可列舉的類別會一次從文字檔讀取一行的程式程式碼。</span><span class="sxs-lookup"><span data-stu-id="0d447-137">This enumerable class will read lines from a text file one line at a time.</span></span> <span data-ttu-id="0d447-138">將下列程式碼新增至類別，以公開公用的函式，以接受檔案路徑做為輸入參數。</span><span class="sxs-lookup"><span data-stu-id="0d447-138">Add the following code to the class to expose a public constructor that takes a file path as an input parameter.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#2)]

4. <span data-ttu-id="0d447-139">介面的方法執行 <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> `IEnumerable(Of String)` 將會傳回類別的新實例 `StreamReaderEnumerator` 。</span><span class="sxs-lookup"><span data-stu-id="0d447-139">Your implementation of the <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method of the `IEnumerable(Of String)` interface will return a new instance of the `StreamReaderEnumerator` class.</span></span> <span data-ttu-id="0d447-140">可以執行介面的 `GetEnumerator` 方法 `IEnumerable` `Private` ，因為您必須只公開介面的成員 `IEnumerable(Of String)` 。</span><span class="sxs-lookup"><span data-stu-id="0d447-140">The implementation of the `GetEnumerator` method of the `IEnumerable` interface can be made `Private`, because you have to expose only members of the `IEnumerable(Of String)` interface.</span></span> <span data-ttu-id="0d447-141">使用下列程式碼取代為方法所產生的程式碼 Visual Basic `GetEnumerator` 。</span><span class="sxs-lookup"><span data-stu-id="0d447-141">Replace the code that Visual Basic generated for the `GetEnumerator` methods with the following code.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#3)]  
  
<span data-ttu-id="0d447-142">**新增程式碼以執行 IEnumerator**</span><span class="sxs-lookup"><span data-stu-id="0d447-142">**Add the code to implement IEnumerator**</span></span>

1. <span data-ttu-id="0d447-143">開啟 [StreamReaderEnumerator] 檔案。</span><span class="sxs-lookup"><span data-stu-id="0d447-143">Open the StreamReaderEnumerator.vb file.</span></span>

2. <span data-ttu-id="0d447-144">在後面的一行 `Public Class StreamReaderEnumerator` 中，輸入下列程式碼，然後按 enter 鍵。</span><span class="sxs-lookup"><span data-stu-id="0d447-144">On the line after `Public Class StreamReaderEnumerator`, type the following and press ENTER.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#4)]

   <span data-ttu-id="0d447-145">Visual Basic 會使用介面所需的成員，自動填入類別 `IEnumerator(Of String)` 。</span><span class="sxs-lookup"><span data-stu-id="0d447-145">Visual Basic automatically populates the class with the members that are required by the `IEnumerator(Of String)` interface.</span></span>

3. <span data-ttu-id="0d447-146">列舉值類別會開啟文字檔，並執行檔案 i/o 以讀取檔案中的行。</span><span class="sxs-lookup"><span data-stu-id="0d447-146">The enumerator class opens the text file and performs the file I/O to read the lines from the file.</span></span> <span data-ttu-id="0d447-147">將下列程式碼新增至類別，以公開公用的函式，以使用檔案路徑做為輸入參數，並開啟文字檔進行讀取。</span><span class="sxs-lookup"><span data-stu-id="0d447-147">Add the following code to the class to expose a public constructor that takes a file path as an input parameter and open the text file for reading.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#5)]

4. <span data-ttu-id="0d447-148">`Current`和介面的屬性會 `IEnumerator(Of String)` `IEnumerator` 從文字檔傳回目前的專案做為 `String` 。</span><span class="sxs-lookup"><span data-stu-id="0d447-148">The `Current` properties for both the `IEnumerator(Of String)` and `IEnumerator` interfaces return the current item from the text file as a `String`.</span></span> <span data-ttu-id="0d447-149">可以執行介面的 `Current` 屬性 `IEnumerator` `Private` ，因為您必須只公開介面的成員 `IEnumerator(Of String)` 。</span><span class="sxs-lookup"><span data-stu-id="0d447-149">The implementation of the `Current` property of the `IEnumerator` interface can be made `Private`, because you have to expose only members of the `IEnumerator(Of String)` interface.</span></span> <span data-ttu-id="0d447-150">使用下列程式碼取代為屬性所產生的程式碼 Visual Basic `Current` 。</span><span class="sxs-lookup"><span data-stu-id="0d447-150">Replace the code that Visual Basic generated for the `Current` properties with the following code.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#6)]

5. <span data-ttu-id="0d447-151">`MoveNext`介面的方法會 `IEnumerator` 導覽至文字檔中的下一個專案，並更新屬性所傳回的值 `Current` 。</span><span class="sxs-lookup"><span data-stu-id="0d447-151">The `MoveNext` method of the `IEnumerator` interface navigates to the next item in the text file and updates the value that is returned by the `Current` property.</span></span> <span data-ttu-id="0d447-152">如果沒有其他要讀取的專案，方法會傳回， `MoveNext` `False` 否則方法會傳回 `MoveNext` `True` 。</span><span class="sxs-lookup"><span data-stu-id="0d447-152">If there are no more items to read, the `MoveNext` method returns `False`; otherwise the `MoveNext` method returns `True`.</span></span> <span data-ttu-id="0d447-153">將下列程式碼新增至 `MoveNext` 方法。</span><span class="sxs-lookup"><span data-stu-id="0d447-153">Add the following code to the `MoveNext` method.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#7)]

6. <span data-ttu-id="0d447-154">`Reset`介面的方法會 `IEnumerator` 指示反覆運算器指向文字檔的開頭，並清除目前的專案值。</span><span class="sxs-lookup"><span data-stu-id="0d447-154">The `Reset` method of the `IEnumerator` interface directs the iterator to point to the start of the text file and clears the current item value.</span></span> <span data-ttu-id="0d447-155">將下列程式碼新增至 `Reset` 方法。</span><span class="sxs-lookup"><span data-stu-id="0d447-155">Add the following code to the `Reset` method.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#8)]

7. <span data-ttu-id="0d447-156">`Dispose`介面的方法可 `IEnumerator` 保證在反覆運算器終結之前釋放所有非受控資源。</span><span class="sxs-lookup"><span data-stu-id="0d447-156">The `Dispose` method of the `IEnumerator` interface guarantees that all unmanaged resources are released before the iterator is destroyed.</span></span> <span data-ttu-id="0d447-157">物件所使用的檔案控制代碼 `StreamReader` 是非受控資源，必須在反覆運算器實例終結之前關閉。</span><span class="sxs-lookup"><span data-stu-id="0d447-157">The file handle that is used by the `StreamReader` object is an unmanaged resource and must be closed before the iterator instance is destroyed.</span></span> <span data-ttu-id="0d447-158">使用下列程式碼取代為方法所產生的程式碼 Visual Basic `Dispose` 。</span><span class="sxs-lookup"><span data-stu-id="0d447-158">Replace the code that Visual Basic generated for the `Dispose` method with the following code.</span></span>

     [!code-vb[VbVbalrIteratorWalkthrough#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/StreamReaderIterator.vb#9)]
  
## <a name="using-the-sample-iterator"></a><span data-ttu-id="0d447-159">使用範例反覆運算器</span><span class="sxs-lookup"><span data-stu-id="0d447-159">Using the Sample Iterator</span></span>

 <span data-ttu-id="0d447-160">您可以在程式碼中使用可列舉的類別，以及需要可執行之物件的控制項結構 `IEnumerable` ，例如 `For Next` 迴圈或 LINQ 查詢。</span><span class="sxs-lookup"><span data-stu-id="0d447-160">You can use an enumerable class in your code together with control structures that require an object that implements `IEnumerable`, such as a `For Next` loop or a LINQ query.</span></span> <span data-ttu-id="0d447-161">下列範例會顯示 `StreamReaderEnumerable` LINQ 查詢中的。</span><span class="sxs-lookup"><span data-stu-id="0d447-161">The following example shows the `StreamReaderEnumerable` in a LINQ query.</span></span>  
  
 [!code-vb[VbVbalrIteratorWalkthrough#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIteratorWalkthrough/VB/Module1.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="0d447-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d447-162">See also</span></span>

- [<span data-ttu-id="0d447-163">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="0d447-163">Introduction to LINQ in Visual Basic</span></span>](../linq/introduction-to-linq.md)
- [<span data-ttu-id="0d447-164">控制流程</span><span class="sxs-lookup"><span data-stu-id="0d447-164">Control Flow</span></span>](index.md)
- [<span data-ttu-id="0d447-165">迴圈結構</span><span class="sxs-lookup"><span data-stu-id="0d447-165">Loop Structures</span></span>](loop-structures.md)
- [<span data-ttu-id="0d447-166">For Each...Next 陳述式</span><span class="sxs-lookup"><span data-stu-id="0d447-166">For Each...Next Statement</span></span>](../../../language-reference/statements/for-each-next-statement.md)
