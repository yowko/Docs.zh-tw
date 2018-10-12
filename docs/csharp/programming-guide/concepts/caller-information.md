---
title: 呼叫端資訊 (C#)
ms.date: 07/20/2015
ms.assetid: ffad3d24-2fb7-4641-9124-53b5bc91d339
ms.openlocfilehash: 27f2e7624369061ff3089357c455ae51237e6dfa
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2018
ms.locfileid: "46586448"
---
# <a name="caller-information-c"></a><span data-ttu-id="da24c-102">呼叫端資訊 (C#)</span><span class="sxs-lookup"><span data-stu-id="da24c-102">Caller Information (C#)</span></span>

<span data-ttu-id="da24c-103">使用 Caller Info 屬性，您就可以取得有關方法之呼叫端的資訊。</span><span class="sxs-lookup"><span data-stu-id="da24c-103">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="da24c-104">您可以取得原始程式碼的檔案路徑、原始程式碼中的行號，以及呼叫端的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="da24c-104">You can obtain file path of the source code, the line number in the source code, and the member name of the caller.</span></span> <span data-ttu-id="da24c-105">這項資訊有助於追蹤、偵錯及建立診斷工具。</span><span class="sxs-lookup"><span data-stu-id="da24c-105">This information is helpful for tracing, debugging, and creating diagnostic tools.</span></span>

<span data-ttu-id="da24c-106">若要取得這項資訊，可使用套用至選擇性參數的屬性，每個屬性都有預設值。</span><span class="sxs-lookup"><span data-stu-id="da24c-106">To obtain this information, you use attributes that are applied to optional parameters, each of which has a default value.</span></span> <span data-ttu-id="da24c-107">下表列出 <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> 命名空間中定義的 Caller Info 屬性：</span><span class="sxs-lookup"><span data-stu-id="da24c-107">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>

|<span data-ttu-id="da24c-108">屬性</span><span class="sxs-lookup"><span data-stu-id="da24c-108">Attribute</span></span>|<span data-ttu-id="da24c-109">描述</span><span class="sxs-lookup"><span data-stu-id="da24c-109">Description</span></span>|<span data-ttu-id="da24c-110">類型</span><span class="sxs-lookup"><span data-stu-id="da24c-110">Type</span></span>|
|---|---|---|
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="da24c-111">包含呼叫端的原始程式檔完整路徑。</span><span class="sxs-lookup"><span data-stu-id="da24c-111">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="da24c-112">這是編譯時間的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="da24c-112">This is the file path at compile time.</span></span>|`String`|
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="da24c-113">原始程式檔中呼叫方法所在的行號。</span><span class="sxs-lookup"><span data-stu-id="da24c-113">Line number in the source file at which the method is called.</span></span>|`Integer`|
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="da24c-114">呼叫端的方法或屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="da24c-114">Method or property name of the caller.</span></span> <span data-ttu-id="da24c-115">請參閱本主題稍後的[成員名稱](#member-names)。</span><span class="sxs-lookup"><span data-stu-id="da24c-115">See [Member Names](#member-names) later in this topic.</span></span>|`String`|

## <a name="example"></a><span data-ttu-id="da24c-116">範例</span><span class="sxs-lookup"><span data-stu-id="da24c-116">Example</span></span>

<span data-ttu-id="da24c-117">下列範例將示範如何使用 Caller Info 屬性。</span><span class="sxs-lookup"><span data-stu-id="da24c-117">The following example shows how to use Caller Info attributes.</span></span> <span data-ttu-id="da24c-118">每次呼叫 `TraceMessage` 方法時，呼叫端資訊會替代做為選擇性參數的引數。</span><span class="sxs-lookup"><span data-stu-id="da24c-118">On each call to the `TraceMessage` method, the caller information is substituted as arguments to the optional parameters.</span></span>

```csharp
public void DoProcessing()
{
    TraceMessage("Something happened.");
}

public void TraceMessage(string message,
        [System.Runtime.CompilerServices.CallerMemberName] string memberName = "",
        [System.Runtime.CompilerServices.CallerFilePath] string sourceFilePath = "",
        [System.Runtime.CompilerServices.CallerLineNumber] int sourceLineNumber = 0)
{
    System.Diagnostics.Trace.WriteLine("message: " + message);
    System.Diagnostics.Trace.WriteLine("member name: " + memberName);
    System.Diagnostics.Trace.WriteLine("source file path: " + sourceFilePath);
    System.Diagnostics.Trace.WriteLine("source line number: " + sourceLineNumber);
}

// Sample Output:
//  message: Something happened.
//  member name: DoProcessing
//  source file path: c:\Visual Studio Projects\CallerInfoCS\CallerInfoCS\Form1.cs
//  source line number: 31
```

## <a name="remarks"></a><span data-ttu-id="da24c-119">備註</span><span class="sxs-lookup"><span data-stu-id="da24c-119">Remarks</span></span>

<span data-ttu-id="da24c-120">您必須為每個選擇性參數指定明確的預設值。</span><span class="sxs-lookup"><span data-stu-id="da24c-120">You must specify an explicit default value for each optional parameter.</span></span> <span data-ttu-id="da24c-121">您無法將 Caller Info 屬性套用至未指定為選擇性的參數。</span><span class="sxs-lookup"><span data-stu-id="da24c-121">You can't apply Caller Info attributes to parameters that aren't specified as optional.</span></span>

<span data-ttu-id="da24c-122">Caller Info 屬性不會讓參數成為選擇性，</span><span class="sxs-lookup"><span data-stu-id="da24c-122">The Caller Info attributes don't make a parameter optional.</span></span> <span data-ttu-id="da24c-123">而是會影響省略引數時傳入的預設值。</span><span class="sxs-lookup"><span data-stu-id="da24c-123">Instead, they affect the default value that's passed in when the argument is omitted.</span></span>

<span data-ttu-id="da24c-124">在編譯時期，Caller Info 的值會做為常值發出至中繼語言 (IL)。</span><span class="sxs-lookup"><span data-stu-id="da24c-124">Caller Info values are emitted as literals into the Intermediate Language (IL) at compile time.</span></span> <span data-ttu-id="da24c-125">結果不受模糊化所影響，與 <xref:System.Exception.StackTrace%2A> 屬性中例外狀況的結果不同。</span><span class="sxs-lookup"><span data-stu-id="da24c-125">Unlike the results of the <xref:System.Exception.StackTrace%2A> property for exceptions, the results aren't affected by obfuscation.</span></span>

<span data-ttu-id="da24c-126">您可以明確提供選擇性引數來控制呼叫端資訊，或是隱藏呼叫端資訊。</span><span class="sxs-lookup"><span data-stu-id="da24c-126">You can explicitly supply the optional arguments to control the caller information or to hide caller information.</span></span>

### <a name="member-names"></a><span data-ttu-id="da24c-127">成員名稱</span><span class="sxs-lookup"><span data-stu-id="da24c-127">Member names</span></span>

<span data-ttu-id="da24c-128">您可以使用 `CallerMemberName` 屬性避免指定成員名稱做為所呼叫方法的 `String` 引數。</span><span class="sxs-lookup"><span data-stu-id="da24c-128">You can use the `CallerMemberName` attribute to avoid specifying the member name as a `String` argument to the called method.</span></span> <span data-ttu-id="da24c-129">利用這個技巧就可以避免發生 [重新命名重構] 未變更 `String` 值這個問題。</span><span class="sxs-lookup"><span data-stu-id="da24c-129">By using this technique, you avoid the problem that **Rename Refactoring** doesn't change the `String` values.</span></span> <span data-ttu-id="da24c-130">這項優點對於下列工作特別有用：</span><span class="sxs-lookup"><span data-stu-id="da24c-130">This benefit is especially useful for the following tasks:</span></span>

- <span data-ttu-id="da24c-131">使用追蹤和診斷常式。</span><span class="sxs-lookup"><span data-stu-id="da24c-131">Using tracing and diagnostic routines.</span></span>

- <span data-ttu-id="da24c-132">當繫結資料時，實作 <xref:System.ComponentModel.INotifyPropertyChanged> 介面。</span><span class="sxs-lookup"><span data-stu-id="da24c-132">Implementing the <xref:System.ComponentModel.INotifyPropertyChanged> interface when binding data.</span></span> <span data-ttu-id="da24c-133">這個介面可讓物件的屬性告知繫結的控制項屬性已變更，所以控制項可以顯示更新的資訊。</span><span class="sxs-lookup"><span data-stu-id="da24c-133">This interface allows the property of an object to notify a bound control that the property has changed, so that the control can display the updated information.</span></span> <span data-ttu-id="da24c-134">沒有 `CallerMemberName` 屬性 (Attribute)，您就必須指定屬性 (Property) 名稱做為常值。</span><span class="sxs-lookup"><span data-stu-id="da24c-134">Without the `CallerMemberName` attribute, you must specify the property name as a literal.</span></span>

<span data-ttu-id="da24c-135">下圖顯示當您使用 `CallerMemberName` 屬性時，傳回的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="da24c-135">The following chart shows the member names that are returned when you use the `CallerMemberName` attribute.</span></span>

|<span data-ttu-id="da24c-136">呼叫發生於</span><span class="sxs-lookup"><span data-stu-id="da24c-136">Calls occurs within</span></span>|<span data-ttu-id="da24c-137">成員名稱結果</span><span class="sxs-lookup"><span data-stu-id="da24c-137">Member name result</span></span>|
|-|-|
|<span data-ttu-id="da24c-138">方法、屬性或事件</span><span class="sxs-lookup"><span data-stu-id="da24c-138">Method, property, or event</span></span>|<span data-ttu-id="da24c-139">產生呼叫的方法、屬性或事件的名稱。</span><span class="sxs-lookup"><span data-stu-id="da24c-139">The name of the method, property, or event from which the call originated.</span></span>|
|<span data-ttu-id="da24c-140">建構函式</span><span class="sxs-lookup"><span data-stu-id="da24c-140">Constructor</span></span>|<span data-ttu-id="da24c-141">字串 ".ctor"</span><span class="sxs-lookup"><span data-stu-id="da24c-141">The string ".ctor"</span></span>|
|<span data-ttu-id="da24c-142">靜態建構函式</span><span class="sxs-lookup"><span data-stu-id="da24c-142">Static constructor</span></span>|<span data-ttu-id="da24c-143">字串 ".cctor"</span><span class="sxs-lookup"><span data-stu-id="da24c-143">The string ".cctor"</span></span>|
|<span data-ttu-id="da24c-144">解構函式</span><span class="sxs-lookup"><span data-stu-id="da24c-144">Destructor</span></span>|<span data-ttu-id="da24c-145">字串 "Finalize"</span><span class="sxs-lookup"><span data-stu-id="da24c-145">The string "Finalize"</span></span>|
|<span data-ttu-id="da24c-146">使用者定義的運算子或轉換</span><span class="sxs-lookup"><span data-stu-id="da24c-146">User-defined operators or conversions</span></span>|<span data-ttu-id="da24c-147">產生的成員名稱，例如 "op_Addition"。</span><span class="sxs-lookup"><span data-stu-id="da24c-147">The generated name for the member, for example, "op_Addition".</span></span>|
|<span data-ttu-id="da24c-148">屬性建構函式</span><span class="sxs-lookup"><span data-stu-id="da24c-148">Attribute constructor</span></span>|<span data-ttu-id="da24c-149">套用屬性的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="da24c-149">The name of the member to which the attribute is applied.</span></span> <span data-ttu-id="da24c-150">如果屬性為成員內的任何項目 (例如參數、傳回值或泛型類型參數)，這個結果會是與該項目相關聯的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="da24c-150">If the attribute is any element within a member (such as a parameter, a return value, or a generic type parameter), this result is the name of the member that's associated with that element.</span></span>|
|<span data-ttu-id="da24c-151">無包含的成員 (例如，組件層級或套用至類型的屬性)。</span><span class="sxs-lookup"><span data-stu-id="da24c-151">No containing member (for example, assembly-level or attributes that are applied to types)</span></span>|<span data-ttu-id="da24c-152">選擇性參數的預設值。</span><span class="sxs-lookup"><span data-stu-id="da24c-152">The default value of the optional parameter.</span></span>|

## <a name="see-also"></a><span data-ttu-id="da24c-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da24c-153">See also</span></span>

- [<span data-ttu-id="da24c-154">屬性 (C#)</span><span class="sxs-lookup"><span data-stu-id="da24c-154">Attributes (C#)</span></span>](../../../csharp/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="da24c-155">常見屬性 (C#)</span><span class="sxs-lookup"><span data-stu-id="da24c-155">Common Attributes (C#)</span></span>](../../../csharp/programming-guide/concepts/attributes/common-attributes.md)
- [<span data-ttu-id="da24c-156">具名和選擇性引數</span><span class="sxs-lookup"><span data-stu-id="da24c-156">Named and Optional Arguments</span></span>](../../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md)
- [<span data-ttu-id="da24c-157">程式設計概念 (C#)</span><span class="sxs-lookup"><span data-stu-id="da24c-157">Programming Concepts (C#)</span></span>](../../../csharp/programming-guide/concepts/index.md)
