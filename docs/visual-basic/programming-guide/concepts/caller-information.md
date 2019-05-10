---
title: 呼叫端資訊 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 15d556eb-4d0c-4497-98a3-7f60abb7d6a1
ms.openlocfilehash: d9dc542ee9b800cfe6342f868ff9c2b170a4beec
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64642358"
---
# <a name="caller-information-visual-basic"></a><span data-ttu-id="2e307-102">呼叫端資訊 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e307-102">Caller Information (Visual Basic)</span></span>
<span data-ttu-id="2e307-103">使用 Caller Info 屬性，您就可以取得有關方法之呼叫端的資訊。</span><span class="sxs-lookup"><span data-stu-id="2e307-103">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="2e307-104">您可以取得原始程式碼的檔案路徑、原始程式碼中的行號，以及呼叫端的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="2e307-104">You can obtain file path of the source code, the line number in the source code, and the member name of the caller.</span></span> <span data-ttu-id="2e307-105">這項資訊有助於追蹤、偵錯及建立診斷工具。</span><span class="sxs-lookup"><span data-stu-id="2e307-105">This information is helpful for tracing, debugging, and creating diagnostic tools.</span></span>  
  
 <span data-ttu-id="2e307-106">若要取得這項資訊，可使用套用至選擇性參數的屬性，每個屬性都有預設值。</span><span class="sxs-lookup"><span data-stu-id="2e307-106">To obtain this information, you use attributes that are applied to optional parameters, each of which has a default value.</span></span> <span data-ttu-id="2e307-107">下表列出 <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> 命名空間中定義的 Caller Info 屬性：</span><span class="sxs-lookup"><span data-stu-id="2e307-107">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>  
  
|<span data-ttu-id="2e307-108">屬性</span><span class="sxs-lookup"><span data-stu-id="2e307-108">Attribute</span></span>|<span data-ttu-id="2e307-109">描述</span><span class="sxs-lookup"><span data-stu-id="2e307-109">Description</span></span>|<span data-ttu-id="2e307-110">類型</span><span class="sxs-lookup"><span data-stu-id="2e307-110">Type</span></span>|  
|---|---|---|  
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="2e307-111">包含呼叫端的原始程式檔完整路徑。</span><span class="sxs-lookup"><span data-stu-id="2e307-111">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="2e307-112">這是編譯時間的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="2e307-112">This is the file path at compile time.</span></span>|`String`|  
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="2e307-113">原始程式檔中呼叫方法所在的行號。</span><span class="sxs-lookup"><span data-stu-id="2e307-113">Line number in the source file at which the method is called.</span></span>|`Integer`|  
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="2e307-114">呼叫端的方法或屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="2e307-114">Method or property name of the caller.</span></span> <span data-ttu-id="2e307-115">請參閱本主題稍後的[成員名稱](#MEMBERNAMES)。</span><span class="sxs-lookup"><span data-stu-id="2e307-115">See [Member Names](#MEMBERNAMES) later in this topic.</span></span>|`String`|  
  
## <a name="example"></a><span data-ttu-id="2e307-116">範例</span><span class="sxs-lookup"><span data-stu-id="2e307-116">Example</span></span>  
 <span data-ttu-id="2e307-117">下列範例將示範如何使用 Caller Info 屬性。</span><span class="sxs-lookup"><span data-stu-id="2e307-117">The following example shows how to use Caller Info attributes.</span></span> <span data-ttu-id="2e307-118">每次呼叫 `TraceMessage` 方法時，呼叫端資訊會替代做為選擇性參數的引數。</span><span class="sxs-lookup"><span data-stu-id="2e307-118">On each call to the `TraceMessage` method, the caller information is substituted as arguments to the optional parameters.</span></span>  
  
```vb  
Private Sub DoProcessing()  
    TraceMessage("Something happened.")  
End Sub  
  
Public Sub TraceMessage(message As String,  
        <System.Runtime.CompilerServices.CallerMemberName> Optional memberName As String = Nothing,  
        <System.Runtime.CompilerServices.CallerFilePath> Optional sourcefilePath As String = Nothing,  
        <System.Runtime.CompilerServices.CallerLineNumber()> Optional sourceLineNumber As Integer = 0)  
  
    System.Diagnostics.Trace.WriteLine("message: " & message)  
    System.Diagnostics.Trace.WriteLine("member name: " & memberName)  
    System.Diagnostics.Trace.WriteLine("source file path: " & sourcefilePath)  
    System.Diagnostics.Trace.WriteLine("source line number: " & sourceLineNumber)  
End Sub  
  
' Sample output:  
'   message: Something happened.  
'   member name: DoProcessing  
'   source file path: C:\Users\username\Documents\Visual Studio 2012\Projects\CallerInfoVB\CallerInfoVB\Form1.vb  
'   source line number: 15  
```  
  
## <a name="remarks"></a><span data-ttu-id="2e307-119">備註</span><span class="sxs-lookup"><span data-stu-id="2e307-119">Remarks</span></span>  
 <span data-ttu-id="2e307-120">您必須為每個選擇性參數指定明確的預設值。</span><span class="sxs-lookup"><span data-stu-id="2e307-120">You must specify an explicit default value for each optional parameter.</span></span> <span data-ttu-id="2e307-121">您無法將 Caller Info 屬性套用至未指定為選擇性的參數。</span><span class="sxs-lookup"><span data-stu-id="2e307-121">You can't apply Caller Info attributes to parameters that aren't specified as optional.</span></span>  
  
 <span data-ttu-id="2e307-122">Caller Info 屬性不會讓參數成為選擇性，</span><span class="sxs-lookup"><span data-stu-id="2e307-122">The Caller Info attributes don't make a parameter optional.</span></span> <span data-ttu-id="2e307-123">而是會影響省略引數時傳入的預設值。</span><span class="sxs-lookup"><span data-stu-id="2e307-123">Instead, they affect the default value that's passed in when the argument is omitted.</span></span>  
  
 <span data-ttu-id="2e307-124">在編譯時期，Caller Info 的值會做為常值發出至中繼語言 (IL)。</span><span class="sxs-lookup"><span data-stu-id="2e307-124">Caller Info values are emitted as literals into the Intermediate Language (IL) at compile time.</span></span> <span data-ttu-id="2e307-125">結果不受模糊化所影響，與 <xref:System.Exception.StackTrace%2A> 屬性中例外狀況的結果不同。</span><span class="sxs-lookup"><span data-stu-id="2e307-125">Unlike the results of the <xref:System.Exception.StackTrace%2A> property for exceptions, the results aren't affected by obfuscation.</span></span>  
  
 <span data-ttu-id="2e307-126">您可以明確提供選擇性引數來控制呼叫端資訊，或是隱藏呼叫端資訊。</span><span class="sxs-lookup"><span data-stu-id="2e307-126">You can explicitly supply the optional arguments to control the caller information or to hide caller information.</span></span>  
  
### <a name="MEMBERNAMES"></a> <span data-ttu-id="2e307-127">成員名稱</span><span class="sxs-lookup"><span data-stu-id="2e307-127">Member Names</span></span>  
 <span data-ttu-id="2e307-128">您可以使用 `CallerMemberName` 屬性避免指定成員名稱做為所呼叫方法的 `String` 引數。</span><span class="sxs-lookup"><span data-stu-id="2e307-128">You can use the `CallerMemberName` attribute to avoid specifying the member name as a `String` argument to the called method.</span></span> <span data-ttu-id="2e307-129">利用這個技巧就可以避免發生 [重新命名重構] 未變更 `String` 值這個問題。</span><span class="sxs-lookup"><span data-stu-id="2e307-129">By using this technique, you avoid the problem that **Rename Refactoring** doesn't change the `String` values.</span></span> <span data-ttu-id="2e307-130">這項優點對於下列工作特別有用：</span><span class="sxs-lookup"><span data-stu-id="2e307-130">This benefit is especially useful for the following tasks:</span></span>  
  
- <span data-ttu-id="2e307-131">使用追蹤和診斷常式。</span><span class="sxs-lookup"><span data-stu-id="2e307-131">Using tracing and diagnostic routines.</span></span>  
  
- <span data-ttu-id="2e307-132">當繫結資料時，實作 <xref:System.ComponentModel.INotifyPropertyChanged> 介面。</span><span class="sxs-lookup"><span data-stu-id="2e307-132">Implementing the <xref:System.ComponentModel.INotifyPropertyChanged> interface when binding data.</span></span> <span data-ttu-id="2e307-133">這個介面可讓物件的屬性告知繫結的控制項屬性已變更，所以控制項可以顯示更新的資訊。</span><span class="sxs-lookup"><span data-stu-id="2e307-133">This interface allows the property of an object to notify a bound control that the property has changed, so that the control can display the updated information.</span></span> <span data-ttu-id="2e307-134">沒有 `CallerMemberName` 屬性 (Attribute)，您就必須指定屬性 (Property) 名稱做為常值。</span><span class="sxs-lookup"><span data-stu-id="2e307-134">Without the `CallerMemberName` attribute, you must specify the property name as a literal.</span></span>  
  
 <span data-ttu-id="2e307-135">下圖顯示當您使用 `CallerMemberName` 屬性時，傳回的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="2e307-135">The following chart shows the member names that are returned when you use the `CallerMemberName` attribute.</span></span>  
  
|<span data-ttu-id="2e307-136">呼叫發生於</span><span class="sxs-lookup"><span data-stu-id="2e307-136">Calls occurs within</span></span>|<span data-ttu-id="2e307-137">成員名稱結果</span><span class="sxs-lookup"><span data-stu-id="2e307-137">Member name result</span></span>|  
|-------------------------|------------------------|  
|<span data-ttu-id="2e307-138">方法、屬性或事件</span><span class="sxs-lookup"><span data-stu-id="2e307-138">Method, property, or event</span></span>|<span data-ttu-id="2e307-139">產生呼叫的方法、屬性或事件的名稱。</span><span class="sxs-lookup"><span data-stu-id="2e307-139">The name of the method, property, or event from which the call originated.</span></span>|  
|<span data-ttu-id="2e307-140">建構函式</span><span class="sxs-lookup"><span data-stu-id="2e307-140">Constructor</span></span>|<span data-ttu-id="2e307-141">字串 ".ctor"</span><span class="sxs-lookup"><span data-stu-id="2e307-141">The string ".ctor"</span></span>|  
|<span data-ttu-id="2e307-142">靜態建構函式</span><span class="sxs-lookup"><span data-stu-id="2e307-142">Static constructor</span></span>|<span data-ttu-id="2e307-143">字串 ".cctor"</span><span class="sxs-lookup"><span data-stu-id="2e307-143">The string ".cctor"</span></span>|  
|<span data-ttu-id="2e307-144">解構函式</span><span class="sxs-lookup"><span data-stu-id="2e307-144">Destructor</span></span>|<span data-ttu-id="2e307-145">字串 "Finalize"</span><span class="sxs-lookup"><span data-stu-id="2e307-145">The string "Finalize"</span></span>|  
|<span data-ttu-id="2e307-146">使用者定義的運算子或轉換</span><span class="sxs-lookup"><span data-stu-id="2e307-146">User-defined operators or conversions</span></span>|<span data-ttu-id="2e307-147">產生的成員名稱，例如 "op_Addition"。</span><span class="sxs-lookup"><span data-stu-id="2e307-147">The generated name for the member, for example, "op_Addition".</span></span>|  
|<span data-ttu-id="2e307-148">屬性建構函式</span><span class="sxs-lookup"><span data-stu-id="2e307-148">Attribute constructor</span></span>|<span data-ttu-id="2e307-149">套用屬性的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="2e307-149">The name of the member to which the attribute is applied.</span></span> <span data-ttu-id="2e307-150">如果屬性為成員內的任何項目 (例如參數、傳回值或泛型類型參數)，這個結果會是與該項目相關聯的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="2e307-150">If the attribute is any element within a member (such as a parameter, a return value, or a generic type parameter), this result is the name of the member that's associated with that element.</span></span>|  
|<span data-ttu-id="2e307-151">無包含的成員 (例如，組件層級或套用至類型的屬性)。</span><span class="sxs-lookup"><span data-stu-id="2e307-151">No containing member (for example, assembly-level or attributes that are applied to types)</span></span>|<span data-ttu-id="2e307-152">選擇性參數的預設值。</span><span class="sxs-lookup"><span data-stu-id="2e307-152">The default value of the optional parameter.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2e307-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e307-153">See also</span></span>

- [<span data-ttu-id="2e307-154">屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e307-154">Attributes (Visual Basic)</span></span>](../../../visual-basic/language-reference/attributes.md)
- [<span data-ttu-id="2e307-155">通用屬性 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e307-155">Common Attributes (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md)
- [<span data-ttu-id="2e307-156">選擇性參數</span><span class="sxs-lookup"><span data-stu-id="2e307-156">Optional Parameters</span></span>](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)
- [<span data-ttu-id="2e307-157">程式設計概念 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e307-157">Programming Concepts (Visual Basic)</span></span>](../../../visual-basic/programming-guide/concepts/index.md)
