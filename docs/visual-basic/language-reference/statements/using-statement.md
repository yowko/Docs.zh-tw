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
ms.openlocfilehash: 819af63acb6a1f038300bcb999dcfb904eb8a457
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592081"
---
# <a name="using-statement-visual-basic"></a><span data-ttu-id="fb419-102">Using 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fb419-102">Using Statement (Visual Basic)</span></span>

<span data-ttu-id="fb419-103">宣告 @no__t 0 區塊的開頭，並選擇性地取得區塊所控制的系統資源。</span><span class="sxs-lookup"><span data-stu-id="fb419-103">Declares the beginning of a `Using` block and optionally acquires the system resources that the block controls.</span></span>

## <a name="syntax"></a><span data-ttu-id="fb419-104">語法</span><span class="sxs-lookup"><span data-stu-id="fb419-104">Syntax</span></span>

```vb
Using { resourcelist | resourceexpression }
    [ statements ]
End Using
```

## <a name="parts"></a><span data-ttu-id="fb419-105">組件</span><span class="sxs-lookup"><span data-stu-id="fb419-105">Parts</span></span>

|<span data-ttu-id="fb419-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="fb419-106">Term</span></span>|<span data-ttu-id="fb419-107">定義</span><span class="sxs-lookup"><span data-stu-id="fb419-107">Definition</span></span>|  
|---|---|  
|`resourcelist`|<span data-ttu-id="fb419-108">如果您未提供 `resourceexpression`，則為必要。</span><span class="sxs-lookup"><span data-stu-id="fb419-108">Required if you do not supply `resourceexpression`.</span></span> <span data-ttu-id="fb419-109">這個 `Using` 區塊控制項的一或多個系統資源清單，並以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="fb419-109">List of one or more system resources that this `Using` block controls, separated by commas.</span></span>|  
|`resourceexpression`|<span data-ttu-id="fb419-110">如果您未提供 `resourcelist`，則為必要。</span><span class="sxs-lookup"><span data-stu-id="fb419-110">Required if you do not supply `resourcelist`.</span></span> <span data-ttu-id="fb419-111">參考要由此 @no__t 0 區塊控制之系統資源的參考變數或運算式。</span><span class="sxs-lookup"><span data-stu-id="fb419-111">Reference variable or expression referring to a system resource to be controlled by this `Using` block.</span></span>|  
|`statements`|<span data-ttu-id="fb419-112">選擇性。</span><span class="sxs-lookup"><span data-stu-id="fb419-112">Optional.</span></span> <span data-ttu-id="fb419-113">@No__t 0 區塊執行的語句區塊。</span><span class="sxs-lookup"><span data-stu-id="fb419-113">Block of statements that the `Using` block runs.</span></span>|  
|`End Using`|<span data-ttu-id="fb419-114">必要項。</span><span class="sxs-lookup"><span data-stu-id="fb419-114">Required.</span></span> <span data-ttu-id="fb419-115">結束 @no__t 0 區塊的定義，並處置它所控制的所有資源。</span><span class="sxs-lookup"><span data-stu-id="fb419-115">Terminates the definition of the `Using` block and disposes of all the resources that it controls.</span></span>|  

 <span data-ttu-id="fb419-116">@No__t 0 部分中的每個資源都有下列語法和部分：</span><span class="sxs-lookup"><span data-stu-id="fb419-116">Each resource in the `resourcelist` part has the following syntax and parts:</span></span>

 `resourcename As New resourcetype [ ( [ arglist ] ) ]`

 <span data-ttu-id="fb419-117">-或-</span><span class="sxs-lookup"><span data-stu-id="fb419-117">-or-</span></span>

 `resourcename As resourcetype = resourceexpression`

## <a name="resourcelist-parts"></a><span data-ttu-id="fb419-118">resourcelist 元件</span><span class="sxs-lookup"><span data-stu-id="fb419-118">resourcelist Parts</span></span>

|<span data-ttu-id="fb419-119">詞彙</span><span class="sxs-lookup"><span data-stu-id="fb419-119">Term</span></span>|<span data-ttu-id="fb419-120">定義</span><span class="sxs-lookup"><span data-stu-id="fb419-120">Definition</span></span>|  
|---|---|  
|`resourcename`|<span data-ttu-id="fb419-121">必要項。</span><span class="sxs-lookup"><span data-stu-id="fb419-121">Required.</span></span> <span data-ttu-id="fb419-122">參考變數，參照 @no__t 0 區塊所控制的系統資源。</span><span class="sxs-lookup"><span data-stu-id="fb419-122">Reference variable that refers to a system resource that the `Using` block controls.</span></span>|  
|`New`|<span data-ttu-id="fb419-123">如果 `Using` 語句取得資源，則為必要。</span><span class="sxs-lookup"><span data-stu-id="fb419-123">Required if the `Using` statement acquires the resource.</span></span> <span data-ttu-id="fb419-124">如果您已經取得資源，請使用第二個替代語法。</span><span class="sxs-lookup"><span data-stu-id="fb419-124">If you have already acquired the resource, use the second syntax alternative.</span></span>|  
|`resourcetype`|<span data-ttu-id="fb419-125">必要項。</span><span class="sxs-lookup"><span data-stu-id="fb419-125">Required.</span></span> <span data-ttu-id="fb419-126">資源的類別。</span><span class="sxs-lookup"><span data-stu-id="fb419-126">The class of the resource.</span></span> <span data-ttu-id="fb419-127">類別必須執行 0 @no__t 介面。</span><span class="sxs-lookup"><span data-stu-id="fb419-127">The class must implement the <xref:System.IDisposable> interface.</span></span>|  
|`arglist`|<span data-ttu-id="fb419-128">選擇性。</span><span class="sxs-lookup"><span data-stu-id="fb419-128">Optional.</span></span> <span data-ttu-id="fb419-129">您要傳遞至函式的引數清單，以建立 `resourcetype` 的實例。</span><span class="sxs-lookup"><span data-stu-id="fb419-129">List of arguments you are passing to the constructor to create an instance of `resourcetype`.</span></span> <span data-ttu-id="fb419-130">請參閱[參數清單](parameter-list.md)。</span><span class="sxs-lookup"><span data-stu-id="fb419-130">See [Parameter List](parameter-list.md).</span></span>|  
|`resourceexpression`|<span data-ttu-id="fb419-131">必要項。</span><span class="sxs-lookup"><span data-stu-id="fb419-131">Required.</span></span> <span data-ttu-id="fb419-132">參考系統資源的變數或運算式，滿足 `resourcetype` 的需求。</span><span class="sxs-lookup"><span data-stu-id="fb419-132">Variable or expression referring to a system resource satisfying the requirements of `resourcetype`.</span></span> <span data-ttu-id="fb419-133">如果您使用第二個語法替代，則必須先取得資源，然後再將控制權傳遞給 `Using` 語句。</span><span class="sxs-lookup"><span data-stu-id="fb419-133">If you use the second syntax alternative, you must acquire the resource before passing control to the `Using` statement.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb419-134">備註</span><span class="sxs-lookup"><span data-stu-id="fb419-134">Remarks</span></span>

 <span data-ttu-id="fb419-135">有時候，您的程式碼需要非受控資源，例如檔案控制代碼、COM 包裝函式或 SQL 連接。</span><span class="sxs-lookup"><span data-stu-id="fb419-135">Sometimes your code requires an unmanaged resource, such as a file handle, a COM wrapper, or a SQL connection.</span></span> <span data-ttu-id="fb419-136">當您的程式碼完成時，@no__t 0 區塊可保證一或多個這類資源的處置。</span><span class="sxs-lookup"><span data-stu-id="fb419-136">A `Using` block guarantees the disposal of one or more such resources when your code is finished with them.</span></span> <span data-ttu-id="fb419-137">這讓它們可供其他程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="fb419-137">This makes them available for other code to use.</span></span>

 <span data-ttu-id="fb419-138">受控資源會由 .NET Framework 垃圾收集行程（GC）處置，而不需要您進行任何額外的程式碼撰寫。</span><span class="sxs-lookup"><span data-stu-id="fb419-138">Managed resources are disposed of by the .NET Framework garbage collector (GC) without any extra coding on your part.</span></span> <span data-ttu-id="fb419-139">您不需要受控資源的 `Using` 區塊。</span><span class="sxs-lookup"><span data-stu-id="fb419-139">You do not need a `Using` block for managed resources.</span></span> <span data-ttu-id="fb419-140">不過，您仍然可以使用 `Using` 區塊來強制處置受管理的資源，而不是等候垃圾收集行程。</span><span class="sxs-lookup"><span data-stu-id="fb419-140">However, you can still use a `Using` block to force the disposal of a managed resource instead of waiting for the garbage collector.</span></span>

 <span data-ttu-id="fb419-141">@No__t-0 區塊有三個部分：取得、使用和處置。</span><span class="sxs-lookup"><span data-stu-id="fb419-141">A `Using` block has three parts: acquisition, usage, and disposal.</span></span>

- <span data-ttu-id="fb419-142">取得*表示建立*變數，並將它初始化以參考系統資源。</span><span class="sxs-lookup"><span data-stu-id="fb419-142">*Acquisition* means creating a variable and initializing it to refer to the system resource.</span></span> <span data-ttu-id="fb419-143">@No__t-0 語句可以取得一或多個資源，或者您可以在輸入區塊並將它提供給 `Using` 語句之前，只取得一個資源。</span><span class="sxs-lookup"><span data-stu-id="fb419-143">The `Using` statement can acquire one or more resources, or you can acquire exactly one resource before entering the block and supply it to the `Using` statement.</span></span> <span data-ttu-id="fb419-144">如果您提供 `resourceexpression`，則必須先取得資源，然後再將控制權傳遞給 `Using` 語句。</span><span class="sxs-lookup"><span data-stu-id="fb419-144">If you supply `resourceexpression`, you must acquire the resource before passing control to the `Using` statement.</span></span>

- <span data-ttu-id="fb419-145">*使用*方式表示存取資源，並對它們執行動作。</span><span class="sxs-lookup"><span data-stu-id="fb419-145">*Usage* means accessing the resources and performing actions with them.</span></span> <span data-ttu-id="fb419-146">@No__t-0 和 `End Using` 之間的語句代表資源的使用。</span><span class="sxs-lookup"><span data-stu-id="fb419-146">The statements between `Using` and `End Using` represent the usage of the resources.</span></span>

- <span data-ttu-id="fb419-147">*處置*表示在 `resourcename` 中的物件上呼叫 <xref:System.IDisposable.Dispose%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="fb419-147">*Disposal* means calling the <xref:System.IDisposable.Dispose%2A> method on the object in `resourcename`.</span></span> <span data-ttu-id="fb419-148">這可讓物件完全終止其資源。</span><span class="sxs-lookup"><span data-stu-id="fb419-148">This allows the object to cleanly terminate its resources.</span></span> <span data-ttu-id="fb419-149">@No__t-0 語句會處置 `Using` 區塊控制項下的資源。</span><span class="sxs-lookup"><span data-stu-id="fb419-149">The `End Using` statement disposes of the resources under the `Using` block's control.</span></span>

## <a name="behavior"></a><span data-ttu-id="fb419-150">行為</span><span class="sxs-lookup"><span data-stu-id="fb419-150">Behavior</span></span>

 <span data-ttu-id="fb419-151">@No__t 0 區塊的行為就像是 `Try` ... `Finally` 結構，其中 `Try` 區塊會使用資源，而 `Finally` 區塊則會處置它們。</span><span class="sxs-lookup"><span data-stu-id="fb419-151">A `Using` block behaves like a `Try`...`Finally` construction in which the `Try` block uses the resources and the `Finally` block disposes of them.</span></span> <span data-ttu-id="fb419-152">因此，不論您如何結束區塊，@no__t 0 區塊都會保證資源的處置。</span><span class="sxs-lookup"><span data-stu-id="fb419-152">Because of this, the `Using` block guarantees disposal of the resources, no matter how you exit the block.</span></span> <span data-ttu-id="fb419-153">即使在未處理的例外狀況中，也是如此，但 <xref:System.StackOverflowException> 除外。</span><span class="sxs-lookup"><span data-stu-id="fb419-153">This is true even in the case of an unhandled exception, except for a <xref:System.StackOverflowException>.</span></span>

 <span data-ttu-id="fb419-154">@No__t-0 語句所取得之每個資源變數的範圍僅限於 `Using` 區塊。</span><span class="sxs-lookup"><span data-stu-id="fb419-154">The scope of every resource variable acquired by the `Using` statement is limited to the `Using` block.</span></span>

 <span data-ttu-id="fb419-155">如果您在 `Using` 語句中指定多個系統資源，效果會與您在另一個中嵌套 `Using` 個區塊相同。</span><span class="sxs-lookup"><span data-stu-id="fb419-155">If you specify more than one system resource in the `Using` statement, the effect is the same as if you nested `Using` blocks one within another.</span></span>

 <span data-ttu-id="fb419-156">如果 `resourcename` 是 `Nothing`，則不會呼叫 <xref:System.IDisposable.Dispose%2A>，也不會擲回任何例外狀況。</span><span class="sxs-lookup"><span data-stu-id="fb419-156">If `resourcename` is `Nothing`, no call to <xref:System.IDisposable.Dispose%2A> is made, and no exception is thrown.</span></span>

## <a name="structured-exception-handling-within-a-using-block"></a><span data-ttu-id="fb419-157">Using 區塊內的結構化例外狀況處理</span><span class="sxs-lookup"><span data-stu-id="fb419-157">Structured Exception Handling Within a Using Block</span></span>

 <span data-ttu-id="fb419-158">如果您需要處理可能發生在 `Using` 區塊中的例外狀況，您可以在其中加入完整的 `Try` ... `Finally` 的結構。</span><span class="sxs-lookup"><span data-stu-id="fb419-158">If you need to handle an exception that might occur within the `Using` block, you can add a complete `Try`...`Finally` construction to it.</span></span> <span data-ttu-id="fb419-159">如果您需要處理 `Using` 語句無法成功取得資源的情況，您可以測試以查看 `resourcename` 是否 `Nothing`。</span><span class="sxs-lookup"><span data-stu-id="fb419-159">If you need to handle the case where the `Using` statement is not successful in acquiring a resource, you can test to see if `resourcename` is `Nothing`.</span></span>

## <a name="structured-exception-handling-instead-of-a-using-block"></a><span data-ttu-id="fb419-160">結構化例外狀況處理，而不是 Using 區塊</span><span class="sxs-lookup"><span data-stu-id="fb419-160">Structured Exception Handling Instead of a Using Block</span></span>

 <span data-ttu-id="fb419-161">如果您需要更精確地控制資源的取得，或在 `Finally` 區塊中需要額外的程式碼，您可以將 @no__t 1 區塊重寫為 `Try` ... `Finally` 結構。</span><span class="sxs-lookup"><span data-stu-id="fb419-161">If you need finer control over the acquisition of the resources, or you need additional code in the `Finally` block, you can rewrite the `Using` block as a `Try`...`Finally` construction.</span></span> <span data-ttu-id="fb419-162">下列範例會顯示在 `resource` 的取得與處置中，對等的基本架構 `Try` 和 @no__t 1 的結構。</span><span class="sxs-lookup"><span data-stu-id="fb419-162">The following example shows skeleton `Try` and `Using` constructions that are equivalent in the acquisition and disposal of `resource`.</span></span>

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
> <span data-ttu-id="fb419-163">@No__t-0 區塊內的程式碼不應該將 `resourcename` 中的物件指派給另一個變數。</span><span class="sxs-lookup"><span data-stu-id="fb419-163">The code inside the `Using` block should not assign the object in `resourcename` to another variable.</span></span> <span data-ttu-id="fb419-164">當您結束 `Using` 區塊時，系統會處置資源，而另一個變數無法存取其指向的資源。</span><span class="sxs-lookup"><span data-stu-id="fb419-164">When you exit the `Using` block, the resource is disposed, and the other variable cannot access the resource to which it points.</span></span>

## <a name="example"></a><span data-ttu-id="fb419-165">範例</span><span class="sxs-lookup"><span data-stu-id="fb419-165">Example</span></span>

 <span data-ttu-id="fb419-166">下列範例會建立名為 log .txt 的檔案，並將兩行文字寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="fb419-166">The following example creates a file that is named log.txt and writes two lines of text to the file.</span></span> <span data-ttu-id="fb419-167">此範例也會讀取相同的檔案，並顯示文字行：</span><span class="sxs-lookup"><span data-stu-id="fb419-167">The example also reads that same file and displays the lines of text:</span></span>

 <span data-ttu-id="fb419-168">因為 <xref:System.IO.TextWriter> 和 @no__t 1 類別會執行 @no__t 2 介面，所以程式碼可以使用 `Using` 語句，以確保檔案在寫入和讀取作業之後會正確地關閉。</span><span class="sxs-lookup"><span data-stu-id="fb419-168">Because the <xref:System.IO.TextWriter> and <xref:System.IO.TextReader> classes implement the <xref:System.IDisposable> interface, the code can use `Using` statements to ensure that the file is correctly closed after the write and read operations.</span></span>

 [!code-vb[VbVbalrStatements#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#50)]

## <a name="see-also"></a><span data-ttu-id="fb419-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb419-169">See also</span></span>

- <xref:System.IDisposable>
- [<span data-ttu-id="fb419-170">Try...Catch...Finally 陳述式</span><span class="sxs-lookup"><span data-stu-id="fb419-170">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
- <span data-ttu-id="fb419-171">[如何：處置系統資源 @ no__t-0</span><span class="sxs-lookup"><span data-stu-id="fb419-171">[How to: Dispose of a System Resource](../../programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md)</span></span>
