---
title: "呼叫端資訊 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
ms.assetid: 15d556eb-4d0c-4497-98a3-7f60abb7d6a1
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: d9a028474a3bb7ae020f466d4dfe51608c43ab07
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="caller-information-visual-basic"></a><span data-ttu-id="53b8d-102">呼叫端資訊 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="53b8d-102">Caller Information (Visual Basic)</span></span>
<span data-ttu-id="53b8d-103">使用 Caller Info 屬性，您就可以取得有關方法之呼叫端的資訊。</span><span class="sxs-lookup"><span data-stu-id="53b8d-103">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="53b8d-104">您可以取得原始程式碼的檔案路徑、原始程式碼中的行號，以及呼叫端的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="53b8d-104">You can obtain file path of the source code, the line number in the source code, and the member name of the caller.</span></span> <span data-ttu-id="53b8d-105">這項資訊有助於追蹤、偵錯及建立診斷工具。</span><span class="sxs-lookup"><span data-stu-id="53b8d-105">This information is helpful for tracing, debugging, and creating diagnostic tools.</span></span>  
  
 <span data-ttu-id="53b8d-106">若要取得這項資訊，可使用套用至選擇性參數的屬性，每個屬性都有預設值。</span><span class="sxs-lookup"><span data-stu-id="53b8d-106">To obtain this information, you use attributes that are applied to optional parameters, each of which has a default value.</span></span> <span data-ttu-id="53b8d-107">下表列出中所定義的 Caller Info 屬性<xref:System.Runtime.CompilerServices?displayProperty=fullName>命名空間︰</xref:System.Runtime.CompilerServices?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="53b8d-107">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=fullName> namespace:</span></span>  
  
|<span data-ttu-id="53b8d-108">屬性</span><span class="sxs-lookup"><span data-stu-id="53b8d-108">Attribute</span></span>|<span data-ttu-id="53b8d-109">描述</span><span class="sxs-lookup"><span data-stu-id="53b8d-109">Description</span></span>|<span data-ttu-id="53b8d-110">類型</span><span class="sxs-lookup"><span data-stu-id="53b8d-110">Type</span></span>|  
|---|---|---|  
|<span data-ttu-id="53b8d-111"><xref:System.Runtime.CompilerServices.CallerFilePathAttribute></xref:System.Runtime.CompilerServices.CallerFilePathAttribute></span><span class="sxs-lookup"><span data-stu-id="53b8d-111"><xref:System.Runtime.CompilerServices.CallerFilePathAttribute></span></span>|<span data-ttu-id="53b8d-112">包含呼叫端的原始程式檔完整路徑。</span><span class="sxs-lookup"><span data-stu-id="53b8d-112">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="53b8d-113">這是編譯時間的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="53b8d-113">This is the file path at compile time.</span></span>|`String`|  
|<span data-ttu-id="53b8d-114"><xref:System.Runtime.CompilerServices.CallerLineNumberAttribute></xref:System.Runtime.CompilerServices.CallerLineNumberAttribute></span><span class="sxs-lookup"><span data-stu-id="53b8d-114"><xref:System.Runtime.CompilerServices.CallerLineNumberAttribute></span></span>|<span data-ttu-id="53b8d-115">原始程式檔中呼叫方法所在的行號。</span><span class="sxs-lookup"><span data-stu-id="53b8d-115">Line number in the source file at which the method is called.</span></span>|`Integer`|  
|<span data-ttu-id="53b8d-116"><xref:System.Runtime.CompilerServices.CallerMemberNameAttribute></xref:System.Runtime.CompilerServices.CallerMemberNameAttribute></span><span class="sxs-lookup"><span data-stu-id="53b8d-116"><xref:System.Runtime.CompilerServices.CallerMemberNameAttribute></span></span>|<span data-ttu-id="53b8d-117">呼叫端的方法或屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="53b8d-117">Method or property name of the caller.</span></span> <span data-ttu-id="53b8d-118">請參閱[成員名稱](#MEMBERNAMES)稍後在本主題中。</span><span class="sxs-lookup"><span data-stu-id="53b8d-118">See [Member Names](#MEMBERNAMES) later in this topic.</span></span>|`String`|  
  
## <a name="example"></a><span data-ttu-id="53b8d-119">範例</span><span class="sxs-lookup"><span data-stu-id="53b8d-119">Example</span></span>  
 <span data-ttu-id="53b8d-120">下列範例將示範如何使用 Caller Info 屬性。</span><span class="sxs-lookup"><span data-stu-id="53b8d-120">The following example shows how to use Caller Info attributes.</span></span> <span data-ttu-id="53b8d-121">每次呼叫 `TraceMessage` 方法時，呼叫端資訊會替代做為選擇性參數的引數。</span><span class="sxs-lookup"><span data-stu-id="53b8d-121">On each call to the `TraceMessage` method, the caller information is substituted as arguments to the optional parameters.</span></span>  
  
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
  
## <a name="remarks"></a><span data-ttu-id="53b8d-122">備註</span><span class="sxs-lookup"><span data-stu-id="53b8d-122">Remarks</span></span>  
 <span data-ttu-id="53b8d-123">您必須為每個選擇性參數指定明確的預設值。</span><span class="sxs-lookup"><span data-stu-id="53b8d-123">You must specify an explicit default value for each optional parameter.</span></span> <span data-ttu-id="53b8d-124">您無法將 Caller Info 屬性套用至未指定為選擇性的參數。</span><span class="sxs-lookup"><span data-stu-id="53b8d-124">You can't apply Caller Info attributes to parameters that aren't specified as optional.</span></span>  
  
 <span data-ttu-id="53b8d-125">Caller Info 屬性不會讓參數成為選擇性，</span><span class="sxs-lookup"><span data-stu-id="53b8d-125">The Caller Info attributes don't make a parameter optional.</span></span> <span data-ttu-id="53b8d-126">而是會影響省略引數時傳入的預設值。</span><span class="sxs-lookup"><span data-stu-id="53b8d-126">Instead, they affect the default value that's passed in when the argument is omitted.</span></span>  
  
 <span data-ttu-id="53b8d-127">在編譯時期，Caller Info 的值會做為常值發出至中繼語言 (IL)。</span><span class="sxs-lookup"><span data-stu-id="53b8d-127">Caller Info values are emitted as literals into the Intermediate Language (IL) at compile time.</span></span> <span data-ttu-id="53b8d-128">結果不同<xref:System.Exception.StackTrace%2A>屬性中的例外狀況，結果不受模糊化所影響。</xref:System.Exception.StackTrace%2A></span><span class="sxs-lookup"><span data-stu-id="53b8d-128">Unlike the results of the <xref:System.Exception.StackTrace%2A> property for exceptions, the results aren't affected by obfuscation.</span></span>  
  
 <span data-ttu-id="53b8d-129">您可以明確提供選擇性引數來控制呼叫端資訊，或是隱藏呼叫端資訊。</span><span class="sxs-lookup"><span data-stu-id="53b8d-129">You can explicitly supply the optional arguments to control the caller information or to hide caller information.</span></span>  
  
###  <span data-ttu-id="53b8d-130"><a name="MEMBERNAMES"></a>成員名稱</span><span class="sxs-lookup"><span data-stu-id="53b8d-130"><a name="MEMBERNAMES"></a> Member Names</span></span>  
 <span data-ttu-id="53b8d-131">您可以使用 `CallerMemberName` 屬性避免指定成員名稱做為所呼叫方法的 `String` 引數。</span><span class="sxs-lookup"><span data-stu-id="53b8d-131">You can use the `CallerMemberName` attribute to avoid specifying the member name as a `String` argument to the called method.</span></span> <span data-ttu-id="53b8d-132">您可以使用這項技術，避免問題的**重新命名重構**並不會變更`String`值。</span><span class="sxs-lookup"><span data-stu-id="53b8d-132">By using this technique, you avoid the problem that **Rename Refactoring** doesn't change the `String` values.</span></span> <span data-ttu-id="53b8d-133">這項優點對於下列工作特別有用：</span><span class="sxs-lookup"><span data-stu-id="53b8d-133">This benefit is especially useful for the following tasks:</span></span>  
  
-   <span data-ttu-id="53b8d-134">使用追蹤和診斷常式。</span><span class="sxs-lookup"><span data-stu-id="53b8d-134">Using tracing and diagnostic routines.</span></span>  
  
-   <span data-ttu-id="53b8d-135">實作<xref:System.ComponentModel.INotifyPropertyChanged>介面資料繫結時。</xref:System.ComponentModel.INotifyPropertyChanged></span><span class="sxs-lookup"><span data-stu-id="53b8d-135">Implementing the <xref:System.ComponentModel.INotifyPropertyChanged> interface when binding data.</span></span> <span data-ttu-id="53b8d-136">這個介面可讓物件的屬性告知繫結的控制項屬性已變更，所以控制項可以顯示更新的資訊。</span><span class="sxs-lookup"><span data-stu-id="53b8d-136">This interface allows the property of an object to notify a bound control that the property has changed, so that the control can display the updated information.</span></span> <span data-ttu-id="53b8d-137">沒有 `CallerMemberName` 屬性 (Attribute)，您就必須指定屬性 (Property) 名稱做為常值。</span><span class="sxs-lookup"><span data-stu-id="53b8d-137">Without the `CallerMemberName` attribute, you must specify the property name as a literal.</span></span>  
  
 <span data-ttu-id="53b8d-138">下圖顯示當您使用 `CallerMemberName` 屬性時，傳回的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="53b8d-138">The following chart shows the member names that are returned when you use the `CallerMemberName` attribute.</span></span>  
  
|<span data-ttu-id="53b8d-139">呼叫發生於</span><span class="sxs-lookup"><span data-stu-id="53b8d-139">Calls occurs within</span></span>|<span data-ttu-id="53b8d-140">成員名稱結果</span><span class="sxs-lookup"><span data-stu-id="53b8d-140">Member name result</span></span>|  
|-------------------------|------------------------|  
|<span data-ttu-id="53b8d-141">方法、屬性或事件</span><span class="sxs-lookup"><span data-stu-id="53b8d-141">Method, property, or event</span></span>|<span data-ttu-id="53b8d-142">產生呼叫的方法、屬性或事件的名稱。</span><span class="sxs-lookup"><span data-stu-id="53b8d-142">The name of the method, property, or event from which the call originated.</span></span>|  
|<span data-ttu-id="53b8d-143">建構函式</span><span class="sxs-lookup"><span data-stu-id="53b8d-143">Constructor</span></span>|<span data-ttu-id="53b8d-144">字串 ".ctor"</span><span class="sxs-lookup"><span data-stu-id="53b8d-144">The string ".ctor"</span></span>|  
|<span data-ttu-id="53b8d-145">靜態建構函式</span><span class="sxs-lookup"><span data-stu-id="53b8d-145">Static constructor</span></span>|<span data-ttu-id="53b8d-146">字串 ".cctor"</span><span class="sxs-lookup"><span data-stu-id="53b8d-146">The string ".cctor"</span></span>|  
|<span data-ttu-id="53b8d-147">解構函式</span><span class="sxs-lookup"><span data-stu-id="53b8d-147">Destructor</span></span>|<span data-ttu-id="53b8d-148">字串 "Finalize"</span><span class="sxs-lookup"><span data-stu-id="53b8d-148">The string "Finalize"</span></span>|  
|<span data-ttu-id="53b8d-149">使用者定義的運算子或轉換</span><span class="sxs-lookup"><span data-stu-id="53b8d-149">User-defined operators or conversions</span></span>|<span data-ttu-id="53b8d-150">產生的成員名稱，例如 "op_Addition"。</span><span class="sxs-lookup"><span data-stu-id="53b8d-150">The generated name for the member, for example, "op_Addition".</span></span>|  
|<span data-ttu-id="53b8d-151">屬性建構函式</span><span class="sxs-lookup"><span data-stu-id="53b8d-151">Attribute constructor</span></span>|<span data-ttu-id="53b8d-152">套用屬性的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="53b8d-152">The name of the member to which the attribute is applied.</span></span> <span data-ttu-id="53b8d-153">如果屬性為成員內的任何項目 (例如參數、傳回值或泛型類型參數)，這個結果會是與該項目相關聯的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="53b8d-153">If the attribute is any element within a member (such as a parameter, a return value, or a generic type parameter), this result is the name of the member that's associated with that element.</span></span>|  
|<span data-ttu-id="53b8d-154">無包含的成員 (例如，組件層級或套用至類型的屬性)。</span><span class="sxs-lookup"><span data-stu-id="53b8d-154">No containing member (for example, assembly-level or attributes that are applied to types)</span></span>|<span data-ttu-id="53b8d-155">選擇性參數的預設值。</span><span class="sxs-lookup"><span data-stu-id="53b8d-155">The default value of the optional parameter.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="53b8d-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53b8d-156">See Also</span></span>  
 <span data-ttu-id="53b8d-157">[屬性 (Visual Basic)](../../../visual-basic/language-reference/attributes.md) </span><span class="sxs-lookup"><span data-stu-id="53b8d-157">[Attributes (Visual Basic)](../../../visual-basic/language-reference/attributes.md) </span></span>  
<span data-ttu-id="53b8d-158"> [常見屬性 (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md) </span><span class="sxs-lookup"><span data-stu-id="53b8d-158"> [Common Attributes (Visual Basic)](../../../visual-basic/programming-guide/concepts/attributes/common-attributes.md) </span></span>  
<span data-ttu-id="53b8d-159"> [選擇性參數](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="53b8d-159"> [Optional Parameters](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md) </span></span>  
<span data-ttu-id="53b8d-160"> [程式設計概念 (Visual Basic)](../../../visual-basic/programming-guide/concepts/index.md)</span><span class="sxs-lookup"><span data-stu-id="53b8d-160"> [Programming Concepts (Visual Basic)](../../../visual-basic/programming-guide/concepts/index.md)</span></span>
