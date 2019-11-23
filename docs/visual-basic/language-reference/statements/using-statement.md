---
title: Using 陳述式
ms.date: 07/20/2015
f1_keywords:
- vb.using
helpviewer_keywords:
- resource disposal
- Try...Catch...Finally statements, equivalent to Using statement
- resources [Visual Basic], disposing
- Using statement [Visual Basic]
ms.assetid: 665d1580-dd54-4e96-a9a9-6be2a68948f1
ms.openlocfilehash: 6ec0e228b3898f66f27e322b5db2dd7f3bf3d7d6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352763"
---
# <a name="using-statement-visual-basic"></a><span data-ttu-id="192a1-102">Using 陳述式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="192a1-102">Using Statement (Visual Basic)</span></span>

<span data-ttu-id="192a1-103">Declares the beginning of a `Using` block and optionally acquires the system resources that the block controls.</span><span class="sxs-lookup"><span data-stu-id="192a1-103">Declares the beginning of a `Using` block and optionally acquires the system resources that the block controls.</span></span>

## <a name="syntax"></a><span data-ttu-id="192a1-104">語法</span><span class="sxs-lookup"><span data-stu-id="192a1-104">Syntax</span></span>

```vb
Using { resourcelist | resourceexpression }
    [ statements ]
End Using
```

## <a name="parts"></a><span data-ttu-id="192a1-105">組件</span><span class="sxs-lookup"><span data-stu-id="192a1-105">Parts</span></span>

|<span data-ttu-id="192a1-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="192a1-106">Term</span></span>|<span data-ttu-id="192a1-107">定義</span><span class="sxs-lookup"><span data-stu-id="192a1-107">Definition</span></span>|  
|---|---|  
|`resourcelist`|<span data-ttu-id="192a1-108">Required if you do not supply `resourceexpression`.</span><span class="sxs-lookup"><span data-stu-id="192a1-108">Required if you do not supply `resourceexpression`.</span></span> <span data-ttu-id="192a1-109">List of one or more system resources that this `Using` block controls, separated by commas.</span><span class="sxs-lookup"><span data-stu-id="192a1-109">List of one or more system resources that this `Using` block controls, separated by commas.</span></span>|  
|`resourceexpression`|<span data-ttu-id="192a1-110">Required if you do not supply `resourcelist`.</span><span class="sxs-lookup"><span data-stu-id="192a1-110">Required if you do not supply `resourcelist`.</span></span> <span data-ttu-id="192a1-111">Reference variable or expression referring to a system resource to be controlled by this `Using` block.</span><span class="sxs-lookup"><span data-stu-id="192a1-111">Reference variable or expression referring to a system resource to be controlled by this `Using` block.</span></span>|  
|`statements`|<span data-ttu-id="192a1-112">選擇項。</span><span class="sxs-lookup"><span data-stu-id="192a1-112">Optional.</span></span> <span data-ttu-id="192a1-113">Block of statements that the `Using` block runs.</span><span class="sxs-lookup"><span data-stu-id="192a1-113">Block of statements that the `Using` block runs.</span></span>|  
|`End Using`|<span data-ttu-id="192a1-114">必要項。</span><span class="sxs-lookup"><span data-stu-id="192a1-114">Required.</span></span> <span data-ttu-id="192a1-115">Terminates the definition of the `Using` block and disposes of all the resources that it controls.</span><span class="sxs-lookup"><span data-stu-id="192a1-115">Terminates the definition of the `Using` block and disposes of all the resources that it controls.</span></span>|  

 <span data-ttu-id="192a1-116">Each resource in the `resourcelist` part has the following syntax and parts:</span><span class="sxs-lookup"><span data-stu-id="192a1-116">Each resource in the `resourcelist` part has the following syntax and parts:</span></span>

 `resourcename As New resourcetype [ ( [ arglist ] ) ]`

 <span data-ttu-id="192a1-117">-或-</span><span class="sxs-lookup"><span data-stu-id="192a1-117">-or-</span></span>

 `resourcename As resourcetype = resourceexpression`

## <a name="resourcelist-parts"></a><span data-ttu-id="192a1-118">resourcelist Parts</span><span class="sxs-lookup"><span data-stu-id="192a1-118">resourcelist Parts</span></span>

|<span data-ttu-id="192a1-119">詞彙</span><span class="sxs-lookup"><span data-stu-id="192a1-119">Term</span></span>|<span data-ttu-id="192a1-120">定義</span><span class="sxs-lookup"><span data-stu-id="192a1-120">Definition</span></span>|  
|---|---|  
|`resourcename`|<span data-ttu-id="192a1-121">必要項。</span><span class="sxs-lookup"><span data-stu-id="192a1-121">Required.</span></span> <span data-ttu-id="192a1-122">Reference variable that refers to a system resource that the `Using` block controls.</span><span class="sxs-lookup"><span data-stu-id="192a1-122">Reference variable that refers to a system resource that the `Using` block controls.</span></span>|  
|`New`|<span data-ttu-id="192a1-123">Required if the `Using` statement acquires the resource.</span><span class="sxs-lookup"><span data-stu-id="192a1-123">Required if the `Using` statement acquires the resource.</span></span> <span data-ttu-id="192a1-124">If you have already acquired the resource, use the second syntax alternative.</span><span class="sxs-lookup"><span data-stu-id="192a1-124">If you have already acquired the resource, use the second syntax alternative.</span></span>|  
|`resourcetype`|<span data-ttu-id="192a1-125">必要項。</span><span class="sxs-lookup"><span data-stu-id="192a1-125">Required.</span></span> <span data-ttu-id="192a1-126">The class of the resource.</span><span class="sxs-lookup"><span data-stu-id="192a1-126">The class of the resource.</span></span> <span data-ttu-id="192a1-127">The class must implement the <xref:System.IDisposable> interface.</span><span class="sxs-lookup"><span data-stu-id="192a1-127">The class must implement the <xref:System.IDisposable> interface.</span></span>|  
|`arglist`|<span data-ttu-id="192a1-128">選擇項。</span><span class="sxs-lookup"><span data-stu-id="192a1-128">Optional.</span></span> <span data-ttu-id="192a1-129">List of arguments you are passing to the constructor to create an instance of `resourcetype`.</span><span class="sxs-lookup"><span data-stu-id="192a1-129">List of arguments you are passing to the constructor to create an instance of `resourcetype`.</span></span> <span data-ttu-id="192a1-130">See [Parameter List](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="192a1-130">See [Parameter List](parameter-list.md).</span></span>|  
|`resourceexpression`|<span data-ttu-id="192a1-131">必要項。</span><span class="sxs-lookup"><span data-stu-id="192a1-131">Required.</span></span> <span data-ttu-id="192a1-132">Variable or expression referring to a system resource satisfying the requirements of `resourcetype`.</span><span class="sxs-lookup"><span data-stu-id="192a1-132">Variable or expression referring to a system resource satisfying the requirements of `resourcetype`.</span></span> <span data-ttu-id="192a1-133">If you use the second syntax alternative, you must acquire the resource before passing control to the `Using` statement.</span><span class="sxs-lookup"><span data-stu-id="192a1-133">If you use the second syntax alternative, you must acquire the resource before passing control to the `Using` statement.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="192a1-134">備註</span><span class="sxs-lookup"><span data-stu-id="192a1-134">Remarks</span></span>

 <span data-ttu-id="192a1-135">Sometimes your code requires an unmanaged resource, such as a file handle, a COM wrapper, or a SQL connection.</span><span class="sxs-lookup"><span data-stu-id="192a1-135">Sometimes your code requires an unmanaged resource, such as a file handle, a COM wrapper, or a SQL connection.</span></span> <span data-ttu-id="192a1-136">A `Using` block guarantees the disposal of one or more such resources when your code is finished with them.</span><span class="sxs-lookup"><span data-stu-id="192a1-136">A `Using` block guarantees the disposal of one or more such resources when your code is finished with them.</span></span> <span data-ttu-id="192a1-137">This makes them available for other code to use.</span><span class="sxs-lookup"><span data-stu-id="192a1-137">This makes them available for other code to use.</span></span>

 <span data-ttu-id="192a1-138">Managed resources are disposed of by the .NET Framework garbage collector (GC) without any extra coding on your part.</span><span class="sxs-lookup"><span data-stu-id="192a1-138">Managed resources are disposed of by the .NET Framework garbage collector (GC) without any extra coding on your part.</span></span> <span data-ttu-id="192a1-139">You do not need a `Using` block for managed resources.</span><span class="sxs-lookup"><span data-stu-id="192a1-139">You do not need a `Using` block for managed resources.</span></span> <span data-ttu-id="192a1-140">However, you can still use a `Using` block to force the disposal of a managed resource instead of waiting for the garbage collector.</span><span class="sxs-lookup"><span data-stu-id="192a1-140">However, you can still use a `Using` block to force the disposal of a managed resource instead of waiting for the garbage collector.</span></span>

 <span data-ttu-id="192a1-141">A `Using` block has three parts: acquisition, usage, and disposal.</span><span class="sxs-lookup"><span data-stu-id="192a1-141">A `Using` block has three parts: acquisition, usage, and disposal.</span></span>

- <span data-ttu-id="192a1-142">*Acquisition* means creating a variable and initializing it to refer to the system resource.</span><span class="sxs-lookup"><span data-stu-id="192a1-142">*Acquisition* means creating a variable and initializing it to refer to the system resource.</span></span> <span data-ttu-id="192a1-143">The `Using` statement can acquire one or more resources, or you can acquire exactly one resource before entering the block and supply it to the `Using` statement.</span><span class="sxs-lookup"><span data-stu-id="192a1-143">The `Using` statement can acquire one or more resources, or you can acquire exactly one resource before entering the block and supply it to the `Using` statement.</span></span> <span data-ttu-id="192a1-144">If you supply `resourceexpression`, you must acquire the resource before passing control to the `Using` statement.</span><span class="sxs-lookup"><span data-stu-id="192a1-144">If you supply `resourceexpression`, you must acquire the resource before passing control to the `Using` statement.</span></span>

- <span data-ttu-id="192a1-145">*Usage* means accessing the resources and performing actions with them.</span><span class="sxs-lookup"><span data-stu-id="192a1-145">*Usage* means accessing the resources and performing actions with them.</span></span> <span data-ttu-id="192a1-146">The statements between `Using` and `End Using` represent the usage of the resources.</span><span class="sxs-lookup"><span data-stu-id="192a1-146">The statements between `Using` and `End Using` represent the usage of the resources.</span></span>

- <span data-ttu-id="192a1-147">*Disposal* means calling the <xref:System.IDisposable.Dispose%2A> method on the object in `resourcename`.</span><span class="sxs-lookup"><span data-stu-id="192a1-147">*Disposal* means calling the <xref:System.IDisposable.Dispose%2A> method on the object in `resourcename`.</span></span> <span data-ttu-id="192a1-148">This allows the object to cleanly terminate its resources.</span><span class="sxs-lookup"><span data-stu-id="192a1-148">This allows the object to cleanly terminate its resources.</span></span> <span data-ttu-id="192a1-149">The `End Using` statement disposes of the resources under the `Using` block's control.</span><span class="sxs-lookup"><span data-stu-id="192a1-149">The `End Using` statement disposes of the resources under the `Using` block's control.</span></span>

## <a name="behavior"></a><span data-ttu-id="192a1-150">行為</span><span class="sxs-lookup"><span data-stu-id="192a1-150">Behavior</span></span>

 <span data-ttu-id="192a1-151">A `Using` block behaves like a `Try`...`Finally` construction in which the `Try` block uses the resources and the `Finally` block disposes of them.</span><span class="sxs-lookup"><span data-stu-id="192a1-151">A `Using` block behaves like a `Try`...`Finally` construction in which the `Try` block uses the resources and the `Finally` block disposes of them.</span></span> <span data-ttu-id="192a1-152">Because of this, the `Using` block guarantees disposal of the resources, no matter how you exit the block.</span><span class="sxs-lookup"><span data-stu-id="192a1-152">Because of this, the `Using` block guarantees disposal of the resources, no matter how you exit the block.</span></span> <span data-ttu-id="192a1-153">This is true even in the case of an unhandled exception, except for a <xref:System.StackOverflowException>.</span><span class="sxs-lookup"><span data-stu-id="192a1-153">This is true even in the case of an unhandled exception, except for a <xref:System.StackOverflowException>.</span></span>

 <span data-ttu-id="192a1-154">The scope of every resource variable acquired by the `Using` statement is limited to the `Using` block.</span><span class="sxs-lookup"><span data-stu-id="192a1-154">The scope of every resource variable acquired by the `Using` statement is limited to the `Using` block.</span></span>

 <span data-ttu-id="192a1-155">If you specify more than one system resource in the `Using` statement, the effect is the same as if you nested `Using` blocks one within another.</span><span class="sxs-lookup"><span data-stu-id="192a1-155">If you specify more than one system resource in the `Using` statement, the effect is the same as if you nested `Using` blocks one within another.</span></span>

 <span data-ttu-id="192a1-156">If `resourcename` is `Nothing`, no call to <xref:System.IDisposable.Dispose%2A> is made, and no exception is thrown.</span><span class="sxs-lookup"><span data-stu-id="192a1-156">If `resourcename` is `Nothing`, no call to <xref:System.IDisposable.Dispose%2A> is made, and no exception is thrown.</span></span>

## <a name="structured-exception-handling-within-a-using-block"></a><span data-ttu-id="192a1-157">Structured Exception Handling Within a Using Block</span><span class="sxs-lookup"><span data-stu-id="192a1-157">Structured Exception Handling Within a Using Block</span></span>

 <span data-ttu-id="192a1-158">If you need to handle an exception that might occur within the `Using` block, you can add a complete `Try`...`Finally` construction to it.</span><span class="sxs-lookup"><span data-stu-id="192a1-158">If you need to handle an exception that might occur within the `Using` block, you can add a complete `Try`...`Finally` construction to it.</span></span> <span data-ttu-id="192a1-159">If you need to handle the case where the `Using` statement is not successful in acquiring a resource, you can test to see if `resourcename` is `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="192a1-159">If you need to handle the case where the `Using` statement is not successful in acquiring a resource, you can test to see if `resourcename` is `Nothing`.</span></span>

## <a name="structured-exception-handling-instead-of-a-using-block"></a><span data-ttu-id="192a1-160">Structured Exception Handling Instead of a Using Block</span><span class="sxs-lookup"><span data-stu-id="192a1-160">Structured Exception Handling Instead of a Using Block</span></span>

 <span data-ttu-id="192a1-161">If you need finer control over the acquisition of the resources, or you need additional code in the `Finally` block, you can rewrite the `Using` block as a `Try`...`Finally` construction.</span><span class="sxs-lookup"><span data-stu-id="192a1-161">If you need finer control over the acquisition of the resources, or you need additional code in the `Finally` block, you can rewrite the `Using` block as a `Try`...`Finally` construction.</span></span> <span data-ttu-id="192a1-162">The following example shows skeleton `Try` and `Using` constructions that are equivalent in the acquisition and disposal of `resource`.</span><span class="sxs-lookup"><span data-stu-id="192a1-162">The following example shows skeleton `Try` and `Using` constructions that are equivalent in the acquisition and disposal of `resource`.</span></span>

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
> <span data-ttu-id="192a1-163">The code inside the `Using` block should not assign the object in `resourcename` to another variable.</span><span class="sxs-lookup"><span data-stu-id="192a1-163">The code inside the `Using` block should not assign the object in `resourcename` to another variable.</span></span> <span data-ttu-id="192a1-164">When you exit the `Using` block, the resource is disposed, and the other variable cannot access the resource to which it points.</span><span class="sxs-lookup"><span data-stu-id="192a1-164">When you exit the `Using` block, the resource is disposed, and the other variable cannot access the resource to which it points.</span></span>

## <a name="example"></a><span data-ttu-id="192a1-165">範例</span><span class="sxs-lookup"><span data-stu-id="192a1-165">Example</span></span>

 <span data-ttu-id="192a1-166">The following example creates a file that is named log.txt and writes two lines of text to the file.</span><span class="sxs-lookup"><span data-stu-id="192a1-166">The following example creates a file that is named log.txt and writes two lines of text to the file.</span></span> <span data-ttu-id="192a1-167">The example also reads that same file and displays the lines of text:</span><span class="sxs-lookup"><span data-stu-id="192a1-167">The example also reads that same file and displays the lines of text:</span></span>

 <span data-ttu-id="192a1-168">Because the <xref:System.IO.TextWriter> and <xref:System.IO.TextReader> classes implement the <xref:System.IDisposable> interface, the code can use `Using` statements to ensure that the file is correctly closed after the write and read operations.</span><span class="sxs-lookup"><span data-stu-id="192a1-168">Because the <xref:System.IO.TextWriter> and <xref:System.IO.TextReader> classes implement the <xref:System.IDisposable> interface, the code can use `Using` statements to ensure that the file is correctly closed after the write and read operations.</span></span>

 [!code-vb[VbVbalrStatements#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#50)]

## <a name="see-also"></a><span data-ttu-id="192a1-169">請參閱</span><span class="sxs-lookup"><span data-stu-id="192a1-169">See also</span></span>

- <xref:System.IDisposable>
- [<span data-ttu-id="192a1-170">Try...Catch...Finally 陳述式</span><span class="sxs-lookup"><span data-stu-id="192a1-170">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
- [<span data-ttu-id="192a1-171">如何：處置系統資源</span><span class="sxs-lookup"><span data-stu-id="192a1-171">How to: Dispose of a System Resource</span></span>](../../programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md)
