---
title: Using 陳述式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.using
helpviewer_keywords:
- resource disposal
- Try...Catch...Finally statements, equivalent to Using statement
- resources [Visual Basic], disposing
- Using statement [Visual Basic]
ms.assetid: 665d1580-dd54-4e96-a9a9-6be2a68948f1
ms.openlocfilehash: 1cf0772bf4e9a77474849c59454617261475fa76
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966082"
---
# <a name="using-statement-visual-basic"></a><span data-ttu-id="cb004-102">Using 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb004-102">Using Statement (Visual Basic)</span></span>
<span data-ttu-id="cb004-103">宣告的開頭`Using`封鎖，並選擇性地取得區塊所控制的系統資源。</span><span class="sxs-lookup"><span data-stu-id="cb004-103">Declares the beginning of a `Using` block and optionally acquires the system resources that the block controls.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb004-104">語法</span><span class="sxs-lookup"><span data-stu-id="cb004-104">Syntax</span></span>  
  
```  
Using { resourcelist | resourceexpression }  
    [ statements ]  
End Using  
```  
  
## <a name="parts"></a><span data-ttu-id="cb004-105">組件</span><span class="sxs-lookup"><span data-stu-id="cb004-105">Parts</span></span>  
  
|<span data-ttu-id="cb004-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="cb004-106">Term</span></span>|<span data-ttu-id="cb004-107">定義</span><span class="sxs-lookup"><span data-stu-id="cb004-107">Definition</span></span>|  
|---|---|  
|`resourcelist`|<span data-ttu-id="cb004-108">如果您未提供所需`resourceexpression`。</span><span class="sxs-lookup"><span data-stu-id="cb004-108">Required if you do not supply `resourceexpression`.</span></span> <span data-ttu-id="cb004-109">這個清單的一或多個系統資源`Using`封鎖控制項，並以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="cb004-109">List of one or more system resources that this `Using` block controls, separated by commas.</span></span>|  
|`resourceexpression`|<span data-ttu-id="cb004-110">如果您未提供所需`resourcelist`。</span><span class="sxs-lookup"><span data-stu-id="cb004-110">Required if you do not supply `resourcelist`.</span></span> <span data-ttu-id="cb004-111">參考變數或運算式，指的系統資源，來控制這個`Using`區塊。</span><span class="sxs-lookup"><span data-stu-id="cb004-111">Reference variable or expression referring to a system resource to be controlled by this `Using` block.</span></span>|  
|`statements`|<span data-ttu-id="cb004-112">選擇性。</span><span class="sxs-lookup"><span data-stu-id="cb004-112">Optional.</span></span> <span data-ttu-id="cb004-113">陳述式區塊，`Using`封鎖執行。</span><span class="sxs-lookup"><span data-stu-id="cb004-113">Block of statements that the `Using` block runs.</span></span>|  
|`End Using`|<span data-ttu-id="cb004-114">必要項。</span><span class="sxs-lookup"><span data-stu-id="cb004-114">Required.</span></span> <span data-ttu-id="cb004-115">結束的定義`Using`區塊，並處置它所控制的所有資源。</span><span class="sxs-lookup"><span data-stu-id="cb004-115">Terminates the definition of the `Using` block and disposes of all the resources that it controls.</span></span>|  
  
 <span data-ttu-id="cb004-116">在每個資源`resourcelist`組件具有下列語法和組成部分：</span><span class="sxs-lookup"><span data-stu-id="cb004-116">Each resource in the `resourcelist` part has the following syntax and parts:</span></span>  
  
 `resourcename As New resourcetype [ ( [ arglist ] ) ]`  
  
 <span data-ttu-id="cb004-117">-或-</span><span class="sxs-lookup"><span data-stu-id="cb004-117">-or-</span></span>  
  
 `resourcename As resourcetype = resourceexpression`  
  
## <a name="resourcelist-parts"></a><span data-ttu-id="cb004-118">resourcelist 組件</span><span class="sxs-lookup"><span data-stu-id="cb004-118">resourcelist Parts</span></span>  
  
|<span data-ttu-id="cb004-119">詞彙</span><span class="sxs-lookup"><span data-stu-id="cb004-119">Term</span></span>|<span data-ttu-id="cb004-120">定義</span><span class="sxs-lookup"><span data-stu-id="cb004-120">Definition</span></span>|  
|---|---|  
|`resourcename`|<span data-ttu-id="cb004-121">必要項。</span><span class="sxs-lookup"><span data-stu-id="cb004-121">Required.</span></span> <span data-ttu-id="cb004-122">指的是系統資源的參考變數，`Using`封鎖控制權。</span><span class="sxs-lookup"><span data-stu-id="cb004-122">Reference variable that refers to a system resource that the `Using` block controls.</span></span>|  
|`New`|<span data-ttu-id="cb004-123">需要`Using`陳述式會取得資源。</span><span class="sxs-lookup"><span data-stu-id="cb004-123">Required if the `Using` statement acquires the resource.</span></span> <span data-ttu-id="cb004-124">如果您已經取得資源，請使用第二個語法替代方案。</span><span class="sxs-lookup"><span data-stu-id="cb004-124">If you have already acquired the resource, use the second syntax alternative.</span></span>|  
|`resourcetype`|<span data-ttu-id="cb004-125">必要項。</span><span class="sxs-lookup"><span data-stu-id="cb004-125">Required.</span></span> <span data-ttu-id="cb004-126">資源的類別。</span><span class="sxs-lookup"><span data-stu-id="cb004-126">The class of the resource.</span></span> <span data-ttu-id="cb004-127">此類別必須實作<xref:System.IDisposable>介面。</span><span class="sxs-lookup"><span data-stu-id="cb004-127">The class must implement the <xref:System.IDisposable> interface.</span></span>|  
|`arglist`|<span data-ttu-id="cb004-128">選擇性。</span><span class="sxs-lookup"><span data-stu-id="cb004-128">Optional.</span></span> <span data-ttu-id="cb004-129">您要傳遞至要建立的執行個體建構函式的引數清單的`resourcetype`。</span><span class="sxs-lookup"><span data-stu-id="cb004-129">List of arguments you are passing to the constructor to create an instance of `resourcetype`.</span></span> <span data-ttu-id="cb004-130">請參閱[參數清單](../../../visual-basic/language-reference/statements/parameter-list.md)。</span><span class="sxs-lookup"><span data-stu-id="cb004-130">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`resourceexpression`|<span data-ttu-id="cb004-131">必要項。</span><span class="sxs-lookup"><span data-stu-id="cb004-131">Required.</span></span> <span data-ttu-id="cb004-132">變數或運算式指滿足需求的系統資源`resourcetype`。</span><span class="sxs-lookup"><span data-stu-id="cb004-132">Variable or expression referring to a system resource satisfying the requirements of `resourcetype`.</span></span> <span data-ttu-id="cb004-133">如果您使用第二個語法替代方案，您必須先取得資源，將控制項傳遞至`Using`陳述式。</span><span class="sxs-lookup"><span data-stu-id="cb004-133">If you use the second syntax alternative, you must acquire the resource before passing control to the `Using` statement.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cb004-134">備註</span><span class="sxs-lookup"><span data-stu-id="cb004-134">Remarks</span></span>  
 <span data-ttu-id="cb004-135">有時候您的程式碼需要 unmanaged 的資源，例如檔案控制代碼、 COM 包裝函式或 SQL 連接。</span><span class="sxs-lookup"><span data-stu-id="cb004-135">Sometimes your code requires an unmanaged resource, such as a file handle, a COM wrapper, or a SQL connection.</span></span> <span data-ttu-id="cb004-136">A`Using`區塊與他們完成您的程式碼時，保證一或多個這類資源的處置。</span><span class="sxs-lookup"><span data-stu-id="cb004-136">A `Using` block guarantees the disposal of one or more such resources when your code is finished with them.</span></span> <span data-ttu-id="cb004-137">這使其可供其他程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="cb004-137">This makes them available for other code to use.</span></span>  
  
 <span data-ttu-id="cb004-138">受管理的資源處置掉.NET Framework 記憶體回收行程 (GC) 而不需要任何額外的程式碼，就在您的組件。</span><span class="sxs-lookup"><span data-stu-id="cb004-138">Managed resources are disposed of by the .NET Framework garbage collector (GC) without any extra coding on your part.</span></span> <span data-ttu-id="cb004-139">您不需要`Using`區塊的 managed 資源。</span><span class="sxs-lookup"><span data-stu-id="cb004-139">You do not need a `Using` block for managed resources.</span></span> <span data-ttu-id="cb004-140">不過，您仍然可以使用`Using`區塊，以強制受管理的資源，而不是等待記憶體回收行程的處置。</span><span class="sxs-lookup"><span data-stu-id="cb004-140">However, you can still use a `Using` block to force the disposal of a managed resource instead of waiting for the garbage collector.</span></span>  
  
 <span data-ttu-id="cb004-141">A`Using`區塊有三個部分︰ 取得、 使用量以及各種可供使用。</span><span class="sxs-lookup"><span data-stu-id="cb004-141">A `Using` block has three parts: acquisition, usage, and disposal.</span></span>  
  
-   <span data-ttu-id="cb004-142">*取得*表示建立變數，並初始化參考的系統資源。</span><span class="sxs-lookup"><span data-stu-id="cb004-142">*Acquisition* means creating a variable and initializing it to refer to the system resource.</span></span> <span data-ttu-id="cb004-143">`Using`陳述式可以取得一或多個資源，或您可以輸入區塊之前，先取得一個資源，並提供它`Using`陳述式。</span><span class="sxs-lookup"><span data-stu-id="cb004-143">The `Using` statement can acquire one or more resources, or you can acquire exactly one resource before entering the block and supply it to the `Using` statement.</span></span> <span data-ttu-id="cb004-144">如果您提供`resourceexpression`，您必須先取得資源，將控制項傳遞至`Using`陳述式。</span><span class="sxs-lookup"><span data-stu-id="cb004-144">If you supply `resourceexpression`, you must acquire the resource before passing control to the `Using` statement.</span></span>  
  
-   <span data-ttu-id="cb004-145">*使用量*表示的資源存取和使用它們執行動作。</span><span class="sxs-lookup"><span data-stu-id="cb004-145">*Usage* means accessing the resources and performing actions with them.</span></span> <span data-ttu-id="cb004-146">之間的陳述式`Using`和`End Using`代表資源的使用量。</span><span class="sxs-lookup"><span data-stu-id="cb004-146">The statements between `Using` and `End Using` represent the usage of the resources.</span></span>  
  
-   <span data-ttu-id="cb004-147">*處置*方法呼叫<xref:System.IDisposable.Dispose%2A>方法中的物件上`resourcename`。</span><span class="sxs-lookup"><span data-stu-id="cb004-147">*Disposal* means calling the <xref:System.IDisposable.Dispose%2A> method on the object in `resourcename`.</span></span> <span data-ttu-id="cb004-148">這可讓物件完全終止其資源。</span><span class="sxs-lookup"><span data-stu-id="cb004-148">This allows the object to cleanly terminate its resources.</span></span> <span data-ttu-id="cb004-149">`End Using`陳述式處置的資源下`Using`區塊的控制項。</span><span class="sxs-lookup"><span data-stu-id="cb004-149">The `End Using` statement disposes of the resources under the `Using` block's control.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="cb004-150">行為</span><span class="sxs-lookup"><span data-stu-id="cb004-150">Behavior</span></span>  
 <span data-ttu-id="cb004-151">A`Using`區塊的行為類似`Try`...`Finally`所在的建構`Try`區塊中使用的資源和`Finally`區塊處置它們。</span><span class="sxs-lookup"><span data-stu-id="cb004-151">A `Using` block behaves like a `Try`...`Finally` construction in which the `Try` block uses the resources and the `Finally` block disposes of them.</span></span> <span data-ttu-id="cb004-152">因為這個緣故，`Using`區塊都保證會處置的資源，無論您如何結束區塊。</span><span class="sxs-lookup"><span data-stu-id="cb004-152">Because of this, the `Using` block guarantees disposal of the resources, no matter how you exit the block.</span></span> <span data-ttu-id="cb004-153">即使發生例外狀況，則為 true，這是除了<xref:System.StackOverflowException>。</span><span class="sxs-lookup"><span data-stu-id="cb004-153">This is true even in the case of an unhandled exception, except for a <xref:System.StackOverflowException>.</span></span>  
  
 <span data-ttu-id="cb004-154">取得每個資源變數的範圍`Using`陳述式僅限於`Using`區塊。</span><span class="sxs-lookup"><span data-stu-id="cb004-154">The scope of every resource variable acquired by the `Using` statement is limited to the `Using` block.</span></span>  
  
 <span data-ttu-id="cb004-155">如果您指定一個以上的系統資源，在`Using`陳述式，效果會相同，如同您巢狀`Using`封鎖其中一個在另一個。</span><span class="sxs-lookup"><span data-stu-id="cb004-155">If you specify more than one system resource in the `Using` statement, the effect is the same as if you nested `Using` blocks one within another.</span></span>  
  
 <span data-ttu-id="cb004-156">如果`resourcename`是`Nothing`，不需要呼叫<xref:System.IDisposable.Dispose%2A>進行，而且會擲回任何例外狀況。</span><span class="sxs-lookup"><span data-stu-id="cb004-156">If `resourcename` is `Nothing`, no call to <xref:System.IDisposable.Dispose%2A> is made, and no exception is thrown.</span></span>  
  
## <a name="structured-exception-handling-within-a-using-block"></a><span data-ttu-id="cb004-157">處理使用的區塊內的結構化例外狀況</span><span class="sxs-lookup"><span data-stu-id="cb004-157">Structured Exception Handling Within a Using Block</span></span>  
 <span data-ttu-id="cb004-158">如果您需要處理中可能發生的例外狀況`Using`區塊中，您可以新增完整`Try`...`Finally`給它的建構。</span><span class="sxs-lookup"><span data-stu-id="cb004-158">If you need to handle an exception that might occur within the `Using` block, you can add a complete `Try`...`Finally` construction to it.</span></span> <span data-ttu-id="cb004-159">如果您要處理的情況所在`Using`陳述式不成功取得資源，您可以測試是否`resourcename`是`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="cb004-159">If you need to handle the case where the `Using` statement is not successful in acquiring a resource, you can test to see if `resourcename` is `Nothing`.</span></span>  
  
## <a name="structured-exception-handling-instead-of-a-using-block"></a><span data-ttu-id="cb004-160">結構化例外狀況，而不使用區塊處理</span><span class="sxs-lookup"><span data-stu-id="cb004-160">Structured Exception Handling Instead of a Using Block</span></span>  
 <span data-ttu-id="cb004-161">如果您需要更精細地控制擷取的資源，或您需要額外的程式碼中`Finally`區塊中，您可以重新撰寫`Using`封鎖`Try`...`Finally`建構。</span><span class="sxs-lookup"><span data-stu-id="cb004-161">If you need finer control over the acquisition of the resources, or you need additional code in the `Finally` block, you can rewrite the `Using` block as a `Try`...`Finally` construction.</span></span> <span data-ttu-id="cb004-162">下列範例示範基本架構`Try`並`Using`建構，而且相當於取得和處置`resource`。</span><span class="sxs-lookup"><span data-stu-id="cb004-162">The following example shows skeleton `Try` and `Using` constructions that are equivalent in the acquisition and disposal of `resource`.</span></span>  
  
```vb  
Using resource As New resourceType   
    ' Insert code to work with resource.  
End Using  
  
' For the acquisition and disposal of resource, the following  
' Try construction is equivalent to the Using block.  
Dim resource As New resourceType  
Try   
    ' Insert code to work with resource.  
Finally   
    If resource IsNot Nothing Then  
        resource.Dispose()   
    End If  
End Try   
```  
  
> [!NOTE]
>  <span data-ttu-id="cb004-163">內的程式碼`Using`區塊不應該指派中的物件`resourcename`給另一個變數。</span><span class="sxs-lookup"><span data-stu-id="cb004-163">The code inside the `Using` block should not assign the object in `resourcename` to another variable.</span></span> <span data-ttu-id="cb004-164">當您結束`Using`區塊中，資源處置，而另一個變數無法存取它所指向的資源。</span><span class="sxs-lookup"><span data-stu-id="cb004-164">When you exit the `Using` block, the resource is disposed, and the other variable cannot access the resource to which it points.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb004-165">範例</span><span class="sxs-lookup"><span data-stu-id="cb004-165">Example</span></span>  
 <span data-ttu-id="cb004-166">下列範例會建立名為 log.txt，並將兩行文字寫入檔案的檔案。</span><span class="sxs-lookup"><span data-stu-id="cb004-166">The following example creates a file that is named log.txt and writes two lines of text to the file.</span></span> <span data-ttu-id="cb004-167">範例也會讀取該相同的檔案，並顯示的文字行。</span><span class="sxs-lookup"><span data-stu-id="cb004-167">The example also reads that same file and displays the lines of text.</span></span>  
  
 <span data-ttu-id="cb004-168">因為<xref:System.IO.TextWriter>並<xref:System.IO.TextReader>類別會實作<xref:System.IDisposable>介面，可以使用程式碼`Using`陳述式來確認檔案正確關閉之後寫入和讀取作業。</span><span class="sxs-lookup"><span data-stu-id="cb004-168">Because the <xref:System.IO.TextWriter> and <xref:System.IO.TextReader> classes implement the <xref:System.IDisposable> interface, the code can use `Using` statements to ensure that the file is correctly closed after the write and read operations.</span></span>  
  
 [!code-vb[VbVbalrStatements#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#50)]  
  
## <a name="see-also"></a><span data-ttu-id="cb004-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb004-169">See also</span></span>
- <xref:System.IDisposable>
- [<span data-ttu-id="cb004-170">Try...Catch...Finally 陳述式</span><span class="sxs-lookup"><span data-stu-id="cb004-170">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="cb004-171">如何：處置系統資源</span><span class="sxs-lookup"><span data-stu-id="cb004-171">How to: Dispose of a System Resource</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md)
