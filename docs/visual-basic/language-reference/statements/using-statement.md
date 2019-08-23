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
ms.openlocfilehash: 346a26ad5751599831d8b0d3e0497e4d488eb76c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957537"
---
# <a name="using-statement-visual-basic"></a><span data-ttu-id="92de3-102">Using 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92de3-102">Using Statement (Visual Basic)</span></span>
<span data-ttu-id="92de3-103">宣告`Using`區塊的開頭, 並選擇性地取得區塊所控制的系統資源。</span><span class="sxs-lookup"><span data-stu-id="92de3-103">Declares the beginning of a `Using` block and optionally acquires the system resources that the block controls.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92de3-104">語法</span><span class="sxs-lookup"><span data-stu-id="92de3-104">Syntax</span></span>  
  
```  
Using { resourcelist | resourceexpression }  
    [ statements ]  
End Using  
```  
  
## <a name="parts"></a><span data-ttu-id="92de3-105">組件</span><span class="sxs-lookup"><span data-stu-id="92de3-105">Parts</span></span>  
  
|<span data-ttu-id="92de3-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="92de3-106">Term</span></span>|<span data-ttu-id="92de3-107">定義</span><span class="sxs-lookup"><span data-stu-id="92de3-107">Definition</span></span>|  
|---|---|  
|`resourcelist`|<span data-ttu-id="92de3-108">如果您沒有提供`resourceexpression`, 則為必要。</span><span class="sxs-lookup"><span data-stu-id="92de3-108">Required if you do not supply `resourceexpression`.</span></span> <span data-ttu-id="92de3-109">這個`Using`區塊所控制的一或多個系統資源清單, 並以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="92de3-109">List of one or more system resources that this `Using` block controls, separated by commas.</span></span>|  
|`resourceexpression`|<span data-ttu-id="92de3-110">如果您沒有提供`resourcelist`, 則為必要。</span><span class="sxs-lookup"><span data-stu-id="92de3-110">Required if you do not supply `resourcelist`.</span></span> <span data-ttu-id="92de3-111">參考要由這個`Using`區塊控制之系統資源的參考變數或運算式。</span><span class="sxs-lookup"><span data-stu-id="92de3-111">Reference variable or expression referring to a system resource to be controlled by this `Using` block.</span></span>|  
|`statements`|<span data-ttu-id="92de3-112">選擇性。</span><span class="sxs-lookup"><span data-stu-id="92de3-112">Optional.</span></span> <span data-ttu-id="92de3-113">`Using`區塊執行的語句區塊。</span><span class="sxs-lookup"><span data-stu-id="92de3-113">Block of statements that the `Using` block runs.</span></span>|  
|`End Using`|<span data-ttu-id="92de3-114">必要項。</span><span class="sxs-lookup"><span data-stu-id="92de3-114">Required.</span></span> <span data-ttu-id="92de3-115">結束`Using`區塊的定義, 並處置它所控制的所有資源。</span><span class="sxs-lookup"><span data-stu-id="92de3-115">Terminates the definition of the `Using` block and disposes of all the resources that it controls.</span></span>|  
  
 <span data-ttu-id="92de3-116">`resourcelist`元件中的每個資源都有下列語法和部分:</span><span class="sxs-lookup"><span data-stu-id="92de3-116">Each resource in the `resourcelist` part has the following syntax and parts:</span></span>  
  
 `resourcename As New resourcetype [ ( [ arglist ] ) ]`  
  
 <span data-ttu-id="92de3-117">-或-</span><span class="sxs-lookup"><span data-stu-id="92de3-117">-or-</span></span>  
  
 `resourcename As resourcetype = resourceexpression`  
  
## <a name="resourcelist-parts"></a><span data-ttu-id="92de3-118">resourcelist 元件</span><span class="sxs-lookup"><span data-stu-id="92de3-118">resourcelist Parts</span></span>  
  
|<span data-ttu-id="92de3-119">詞彙</span><span class="sxs-lookup"><span data-stu-id="92de3-119">Term</span></span>|<span data-ttu-id="92de3-120">定義</span><span class="sxs-lookup"><span data-stu-id="92de3-120">Definition</span></span>|  
|---|---|  
|`resourcename`|<span data-ttu-id="92de3-121">必要項。</span><span class="sxs-lookup"><span data-stu-id="92de3-121">Required.</span></span> <span data-ttu-id="92de3-122">參考`Using`區塊所控制之系統資源的參考變數。</span><span class="sxs-lookup"><span data-stu-id="92de3-122">Reference variable that refers to a system resource that the `Using` block controls.</span></span>|  
|`New`|<span data-ttu-id="92de3-123">如果語句取得`Using`資源, 則為必要。</span><span class="sxs-lookup"><span data-stu-id="92de3-123">Required if the `Using` statement acquires the resource.</span></span> <span data-ttu-id="92de3-124">如果您已經取得資源, 請使用第二個替代語法。</span><span class="sxs-lookup"><span data-stu-id="92de3-124">If you have already acquired the resource, use the second syntax alternative.</span></span>|  
|`resourcetype`|<span data-ttu-id="92de3-125">必要項。</span><span class="sxs-lookup"><span data-stu-id="92de3-125">Required.</span></span> <span data-ttu-id="92de3-126">資源的類別。</span><span class="sxs-lookup"><span data-stu-id="92de3-126">The class of the resource.</span></span> <span data-ttu-id="92de3-127">類別必須執行<xref:System.IDisposable>介面。</span><span class="sxs-lookup"><span data-stu-id="92de3-127">The class must implement the <xref:System.IDisposable> interface.</span></span>|  
|`arglist`|<span data-ttu-id="92de3-128">選擇性。</span><span class="sxs-lookup"><span data-stu-id="92de3-128">Optional.</span></span> <span data-ttu-id="92de3-129">您要傳遞至函式的引數清單, 以建立的`resourcetype`實例。</span><span class="sxs-lookup"><span data-stu-id="92de3-129">List of arguments you are passing to the constructor to create an instance of `resourcetype`.</span></span> <span data-ttu-id="92de3-130">請參閱[參數清單](../../../visual-basic/language-reference/statements/parameter-list.md)。</span><span class="sxs-lookup"><span data-stu-id="92de3-130">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`resourceexpression`|<span data-ttu-id="92de3-131">必要項。</span><span class="sxs-lookup"><span data-stu-id="92de3-131">Required.</span></span> <span data-ttu-id="92de3-132">參考滿足需求之`resourcetype`系統資源的變數或運算式。</span><span class="sxs-lookup"><span data-stu-id="92de3-132">Variable or expression referring to a system resource satisfying the requirements of `resourcetype`.</span></span> <span data-ttu-id="92de3-133">如果您使用第二個語法替代, 則必須先取得資源, 然後再將`Using`控制權傳遞給語句。</span><span class="sxs-lookup"><span data-stu-id="92de3-133">If you use the second syntax alternative, you must acquire the resource before passing control to the `Using` statement.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92de3-134">備註</span><span class="sxs-lookup"><span data-stu-id="92de3-134">Remarks</span></span>  
 <span data-ttu-id="92de3-135">有時候, 您的程式碼需要非受控資源, 例如檔案控制代碼、COM 包裝函式或 SQL 連接。</span><span class="sxs-lookup"><span data-stu-id="92de3-135">Sometimes your code requires an unmanaged resource, such as a file handle, a COM wrapper, or a SQL connection.</span></span> <span data-ttu-id="92de3-136">當您的程式碼完成時,區塊會保證一或多個這類資源的處置。`Using`</span><span class="sxs-lookup"><span data-stu-id="92de3-136">A `Using` block guarantees the disposal of one or more such resources when your code is finished with them.</span></span> <span data-ttu-id="92de3-137">這讓它們可供其他程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="92de3-137">This makes them available for other code to use.</span></span>  
  
 <span data-ttu-id="92de3-138">受控資源會由 .NET Framework 垃圾收集行程 (GC) 處置, 而不需要您進行任何額外的程式碼撰寫。</span><span class="sxs-lookup"><span data-stu-id="92de3-138">Managed resources are disposed of by the .NET Framework garbage collector (GC) without any extra coding on your part.</span></span> <span data-ttu-id="92de3-139">您不需要受控資源`Using`的區塊。</span><span class="sxs-lookup"><span data-stu-id="92de3-139">You do not need a `Using` block for managed resources.</span></span> <span data-ttu-id="92de3-140">不過, 您仍然可以使用`Using`區塊來強制處置受管理的資源, 而不是等候垃圾收集行程。</span><span class="sxs-lookup"><span data-stu-id="92de3-140">However, you can still use a `Using` block to force the disposal of a managed resource instead of waiting for the garbage collector.</span></span>  
  
 <span data-ttu-id="92de3-141">`Using`區塊有三個部分: [取得]、[使用方式] 和 [處置]。</span><span class="sxs-lookup"><span data-stu-id="92de3-141">A `Using` block has three parts: acquisition, usage, and disposal.</span></span>  
  
- <span data-ttu-id="92de3-142">取得表示建立變數, 並將它初始化以參考系統資源。</span><span class="sxs-lookup"><span data-stu-id="92de3-142">*Acquisition* means creating a variable and initializing it to refer to the system resource.</span></span> <span data-ttu-id="92de3-143">語句可以取得一或多個資源, 您也可以在進入區塊並將它提供`Using`給語句之前, 取得剛好一個資源。 `Using`</span><span class="sxs-lookup"><span data-stu-id="92de3-143">The `Using` statement can acquire one or more resources, or you can acquire exactly one resource before entering the block and supply it to the `Using` statement.</span></span> <span data-ttu-id="92de3-144">如果您提供`resourceexpression`, 則必須先取得資源, 然後再將控制權`Using`傳遞給語句。</span><span class="sxs-lookup"><span data-stu-id="92de3-144">If you supply `resourceexpression`, you must acquire the resource before passing control to the `Using` statement.</span></span>  
  
- <span data-ttu-id="92de3-145">*使用*方式表示存取資源, 並對它們執行動作。</span><span class="sxs-lookup"><span data-stu-id="92de3-145">*Usage* means accessing the resources and performing actions with them.</span></span> <span data-ttu-id="92de3-146">`Using` 和`End Using`之間的語句代表資源的使用。</span><span class="sxs-lookup"><span data-stu-id="92de3-146">The statements between `Using` and `End Using` represent the usage of the resources.</span></span>  
  
- <span data-ttu-id="92de3-147">*處置*表示在中<xref:System.IDisposable.Dispose%2A> `resourcename`的物件上呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="92de3-147">*Disposal* means calling the <xref:System.IDisposable.Dispose%2A> method on the object in `resourcename`.</span></span> <span data-ttu-id="92de3-148">這可讓物件完全終止其資源。</span><span class="sxs-lookup"><span data-stu-id="92de3-148">This allows the object to cleanly terminate its resources.</span></span> <span data-ttu-id="92de3-149">語句會處置`Using`區塊控制項底下的資源。 `End Using`</span><span class="sxs-lookup"><span data-stu-id="92de3-149">The `End Using` statement disposes of the resources under the `Using` block's control.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="92de3-150">行為</span><span class="sxs-lookup"><span data-stu-id="92de3-150">Behavior</span></span>  
 <span data-ttu-id="92de3-151">區塊的行為`Try`就像 ... `Using`區塊會使用資源, 而區塊會處置它們的結構。`Finally` `Finally` `Try`</span><span class="sxs-lookup"><span data-stu-id="92de3-151">A `Using` block behaves like a `Try`...`Finally` construction in which the `Try` block uses the resources and the `Finally` block disposes of them.</span></span> <span data-ttu-id="92de3-152">因此, `Using`不論您如何結束區塊, 區塊都會保證資源的處置。</span><span class="sxs-lookup"><span data-stu-id="92de3-152">Because of this, the `Using` block guarantees disposal of the resources, no matter how you exit the block.</span></span> <span data-ttu-id="92de3-153">即使是未處理的例外狀況 (除外<xref:System.StackOverflowException>), 也是如此。</span><span class="sxs-lookup"><span data-stu-id="92de3-153">This is true even in the case of an unhandled exception, except for a <xref:System.StackOverflowException>.</span></span>  
  
 <span data-ttu-id="92de3-154">`Using`語句所取得之每個資源變數的範圍會限制`Using`為區塊。</span><span class="sxs-lookup"><span data-stu-id="92de3-154">The scope of every resource variable acquired by the `Using` statement is limited to the `Using` block.</span></span>  
  
 <span data-ttu-id="92de3-155">如果您在`Using`語句中指定多個系統資源, 其效果會與您在另一個中嵌套`Using`區塊的結果相同。</span><span class="sxs-lookup"><span data-stu-id="92de3-155">If you specify more than one system resource in the `Using` statement, the effect is the same as if you nested `Using` blocks one within another.</span></span>  
  
 <span data-ttu-id="92de3-156">如果`resourcename` <xref:System.IDisposable.Dispose%2A>為`Nothing`, 則不會呼叫, 而且不會擲回任何例外狀況。</span><span class="sxs-lookup"><span data-stu-id="92de3-156">If `resourcename` is `Nothing`, no call to <xref:System.IDisposable.Dispose%2A> is made, and no exception is thrown.</span></span>  
  
## <a name="structured-exception-handling-within-a-using-block"></a><span data-ttu-id="92de3-157">Using 區塊內的結構化例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="92de3-157">Structured Exception Handling Within a Using Block</span></span>  
 <span data-ttu-id="92de3-158">如果您需要處理區塊內可能發生的例外狀況, `Using`您可以新增 [完成`Try`...]`Finally`對它進行結構。</span><span class="sxs-lookup"><span data-stu-id="92de3-158">If you need to handle an exception that might occur within the `Using` block, you can add a complete `Try`...`Finally` construction to it.</span></span> <span data-ttu-id="92de3-159">如果您需要處理`Using`語句無法成功取得資源的情況, 您可以測試以`resourcename`查看是否為`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="92de3-159">If you need to handle the case where the `Using` statement is not successful in acquiring a resource, you can test to see if `resourcename` is `Nothing`.</span></span>  
  
## <a name="structured-exception-handling-instead-of-a-using-block"></a><span data-ttu-id="92de3-160">結構化例外狀況處理, 而不是 Using 區塊</span><span class="sxs-lookup"><span data-stu-id="92de3-160">Structured Exception Handling Instead of a Using Block</span></span>  
 <span data-ttu-id="92de3-161">如果您需要更精確地控制資源的取得, 或在`Finally`區塊中需要額外的程式碼, 您可以將`Using`區塊重寫為`Try`.。。`Finally`結構。</span><span class="sxs-lookup"><span data-stu-id="92de3-161">If you need finer control over the acquisition of the resources, or you need additional code in the `Finally` block, you can rewrite the `Using` block as a `Try`...`Finally` construction.</span></span> <span data-ttu-id="92de3-162">下列範例會顯示`Try`在`resource`的`Using`取得與處置中, 對等的基本架構和結構。</span><span class="sxs-lookup"><span data-stu-id="92de3-162">The following example shows skeleton `Try` and `Using` constructions that are equivalent in the acquisition and disposal of `resource`.</span></span>  
  
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
> <span data-ttu-id="92de3-163">`Using`區塊內的程式碼不應該將中`resourcename`的物件指派給另一個變數。</span><span class="sxs-lookup"><span data-stu-id="92de3-163">The code inside the `Using` block should not assign the object in `resourcename` to another variable.</span></span> <span data-ttu-id="92de3-164">當您`Using`結束區塊時, 系統會處置資源, 而另一個變數無法存取其指向的資源。</span><span class="sxs-lookup"><span data-stu-id="92de3-164">When you exit the `Using` block, the resource is disposed, and the other variable cannot access the resource to which it points.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92de3-165">範例</span><span class="sxs-lookup"><span data-stu-id="92de3-165">Example</span></span>  
 <span data-ttu-id="92de3-166">下列範例會建立名為 log .txt 的檔案, 並將兩行文字寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="92de3-166">The following example creates a file that is named log.txt and writes two lines of text to the file.</span></span> <span data-ttu-id="92de3-167">此範例也會讀取相同的檔案, 並顯示文字行。</span><span class="sxs-lookup"><span data-stu-id="92de3-167">The example also reads that same file and displays the lines of text.</span></span>  
  
 <span data-ttu-id="92de3-168"><xref:System.IDisposable> `Using`由於和類別<xref:System.IO.TextReader>會實作為介面, 因此程式碼可以使用語句來確保檔案在寫入和讀取作業之後會正確地關閉。 <xref:System.IO.TextWriter></span><span class="sxs-lookup"><span data-stu-id="92de3-168">Because the <xref:System.IO.TextWriter> and <xref:System.IO.TextReader> classes implement the <xref:System.IDisposable> interface, the code can use `Using` statements to ensure that the file is correctly closed after the write and read operations.</span></span>  
  
 [!code-vb[VbVbalrStatements#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#50)]  
  
## <a name="see-also"></a><span data-ttu-id="92de3-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92de3-169">See also</span></span>

- <xref:System.IDisposable>
- [<span data-ttu-id="92de3-170">Try...Catch...Finally 陳述式</span><span class="sxs-lookup"><span data-stu-id="92de3-170">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="92de3-171">如何：處置系統資源</span><span class="sxs-lookup"><span data-stu-id="92de3-171">How to: Dispose of a System Resource</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md)
