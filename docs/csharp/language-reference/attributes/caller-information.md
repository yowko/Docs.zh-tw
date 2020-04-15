---
title: C# 保留屬性:追蹤呼叫者資訊
ms.date: 04/09/2020
description: 這些屬性指示編譯器生成有關調用成員的代碼的資訊。 您可以使用呼叫者檔案路徑、呼叫者行號和通話名稱提供詳細的追蹤資訊
ms.openlocfilehash: ee061d4cae35bdcc0b89007e360e94fee8c5f87c
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389874"
---
# <a name="reserved-attributes-determine-caller-information"></a><span data-ttu-id="45a1e-104">保留屬性:確定呼叫者資訊</span><span class="sxs-lookup"><span data-stu-id="45a1e-104">Reserved attributes: Determine caller information</span></span>

<span data-ttu-id="45a1e-105">使用資訊屬性,可以獲取有關方法調用方的資訊。</span><span class="sxs-lookup"><span data-stu-id="45a1e-105">Using info attributes, you obtain information about the caller to a method.</span></span> <span data-ttu-id="45a1e-106">獲取原始碼的檔案路徑、原始碼中的行號和呼叫方的成員姓名。</span><span class="sxs-lookup"><span data-stu-id="45a1e-106">You obtain the file path of the source code, the line number in the source code, and the member name of the caller.</span></span> <span data-ttu-id="45a1e-107">若要取得成員呼叫端資訊，請使用套用至選擇性參數的屬性。</span><span class="sxs-lookup"><span data-stu-id="45a1e-107">To obtain member caller information, you use attributes that are applied to optional parameters.</span></span> <span data-ttu-id="45a1e-108">每個選擇性參數都會指定預設值。</span><span class="sxs-lookup"><span data-stu-id="45a1e-108">Each optional parameter specifies a default value.</span></span> <span data-ttu-id="45a1e-109">下表列出 <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> 命名空間中定義的 Caller Info 屬性：</span><span class="sxs-lookup"><span data-stu-id="45a1e-109">The following table lists the Caller Info attributes that are defined in the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace:</span></span>

|<span data-ttu-id="45a1e-110">屬性</span><span class="sxs-lookup"><span data-stu-id="45a1e-110">Attribute</span></span>|<span data-ttu-id="45a1e-111">描述</span><span class="sxs-lookup"><span data-stu-id="45a1e-111">Description</span></span>|<span data-ttu-id="45a1e-112">類型</span><span class="sxs-lookup"><span data-stu-id="45a1e-112">Type</span></span>|
|---|---|---|
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|<span data-ttu-id="45a1e-113">包含呼叫端的原始程式檔完整路徑。</span><span class="sxs-lookup"><span data-stu-id="45a1e-113">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="45a1e-114">完整路徑是編譯時的路徑。</span><span class="sxs-lookup"><span data-stu-id="45a1e-114">The full path is the path at compile time.</span></span>|`String`|
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|<span data-ttu-id="45a1e-115">原始程式檔中呼叫方法的行號。</span><span class="sxs-lookup"><span data-stu-id="45a1e-115">Line number in the source file from which the method is called.</span></span>|`Integer`|
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|<span data-ttu-id="45a1e-116">呼叫端的方法名稱或屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="45a1e-116">Method name or property name of the caller.</span></span>|`String`|

<span data-ttu-id="45a1e-117">此資訊可説明您編寫追蹤、除錯和創建診斷工具。</span><span class="sxs-lookup"><span data-stu-id="45a1e-117">This information helps you write tracing, debugging, and create diagnostic tools.</span></span> <span data-ttu-id="45a1e-118">下面的範例示範如何使用調用方資訊屬性。</span><span class="sxs-lookup"><span data-stu-id="45a1e-118">The following example shows how to use caller info attributes.</span></span> <span data-ttu-id="45a1e-119">每次呼叫 `TraceMessage` 方法時，呼叫端資訊會替代做為選擇性參數的引數。</span><span class="sxs-lookup"><span data-stu-id="45a1e-119">On each call to the `TraceMessage` method, the caller information is substituted as arguments to the optional parameters.</span></span>

```csharp
public void DoProcessing()
{
    TraceMessage("Something happened.");
}

public void TraceMessage(string message,
        [CallerMemberName] string memberName = "",
        [CallerFilePath] string sourceFilePath = "",
        [CallerLineNumber] int sourceLineNumber = 0)
{
    Trace.WriteLine("message: " + message);
    Trace.WriteLine("member name: " + memberName);
    Trace.WriteLine("source file path: " + sourceFilePath);
    Trace.WriteLine("source line number: " + sourceLineNumber);
}

// Sample Output:
//  message: Something happened.
//  member name: DoProcessing
//  source file path: c:\Visual Studio Projects\CallerInfoCS\CallerInfoCS\Form1.cs
//  source line number: 31
```

<span data-ttu-id="45a1e-120">為每個可選參數指定顯式預設值。</span><span class="sxs-lookup"><span data-stu-id="45a1e-120">You specify an explicit default value for each optional parameter.</span></span> <span data-ttu-id="45a1e-121">不能將調用方資訊屬性應用於未指定為可選的參數。</span><span class="sxs-lookup"><span data-stu-id="45a1e-121">You can't apply caller info attributes to parameters that aren't specified as optional.</span></span> <span data-ttu-id="45a1e-122">調用方資訊屬性不使參數成為可選參數。</span><span class="sxs-lookup"><span data-stu-id="45a1e-122">The caller info attributes don't make a parameter optional.</span></span> <span data-ttu-id="45a1e-123">而是會影響省略引數時傳入的預設值。</span><span class="sxs-lookup"><span data-stu-id="45a1e-123">Instead, they affect the default value that's passed in when the argument is omitted.</span></span> <span data-ttu-id="45a1e-124">調用方資訊值在編譯時以文本身份發送到中間語言 (IL)。</span><span class="sxs-lookup"><span data-stu-id="45a1e-124">Caller info values are emitted as literals into the Intermediate Language (IL) at compile time.</span></span> <span data-ttu-id="45a1e-125">結果不受模糊化所影響，與 <xref:System.Exception.StackTrace%2A> 屬性中例外狀況的結果不同。</span><span class="sxs-lookup"><span data-stu-id="45a1e-125">Unlike the results of the <xref:System.Exception.StackTrace%2A> property for exceptions, the results aren't affected by obfuscation.</span></span> <span data-ttu-id="45a1e-126">您可以明確提供選擇性引數來控制呼叫端資訊，或是隱藏呼叫端資訊。</span><span class="sxs-lookup"><span data-stu-id="45a1e-126">You can explicitly supply the optional arguments to control the caller information or to hide caller information.</span></span>

### <a name="member-names"></a><span data-ttu-id="45a1e-127">成員名稱</span><span class="sxs-lookup"><span data-stu-id="45a1e-127">Member names</span></span>

<span data-ttu-id="45a1e-128">您可以使用 `CallerMemberName` 屬性避免指定成員名稱做為所呼叫方法的 `String` 引數。</span><span class="sxs-lookup"><span data-stu-id="45a1e-128">You can use the `CallerMemberName` attribute to avoid specifying the member name as a `String` argument to the called method.</span></span> <span data-ttu-id="45a1e-129">利用這個技巧就可以避免發生 [重新命名重構]\*\*\*\* 未變更 `String` 值這個問題。</span><span class="sxs-lookup"><span data-stu-id="45a1e-129">By using this technique, you avoid the problem that **Rename Refactoring** doesn't change the `String` values.</span></span> <span data-ttu-id="45a1e-130">這項優點對於下列工作特別有用：</span><span class="sxs-lookup"><span data-stu-id="45a1e-130">This benefit is especially useful for the following tasks:</span></span>

- <span data-ttu-id="45a1e-131">使用追蹤和診斷常式。</span><span class="sxs-lookup"><span data-stu-id="45a1e-131">Using tracing and diagnostic routines.</span></span>
- <span data-ttu-id="45a1e-132">當繫結資料時，實作 <xref:System.ComponentModel.INotifyPropertyChanged> 介面。</span><span class="sxs-lookup"><span data-stu-id="45a1e-132">Implementing the <xref:System.ComponentModel.INotifyPropertyChanged> interface when binding data.</span></span> <span data-ttu-id="45a1e-133">這個介面可讓物件的屬性告知繫結的控制項屬性已變更，所以控制項可以顯示更新的資訊。</span><span class="sxs-lookup"><span data-stu-id="45a1e-133">This interface allows the property of an object to notify a bound control that the property has changed, so that the control can display the updated information.</span></span> <span data-ttu-id="45a1e-134">沒有 `CallerMemberName` 屬性 (Attribute)，您就必須指定屬性 (Property) 名稱做為常值。</span><span class="sxs-lookup"><span data-stu-id="45a1e-134">Without the `CallerMemberName` attribute, you must specify the property name as a literal.</span></span>

<span data-ttu-id="45a1e-135">下圖顯示當您使用 `CallerMemberName` 屬性時，傳回的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="45a1e-135">The following chart shows the member names that are returned when you use the `CallerMemberName` attribute.</span></span>

|<span data-ttu-id="45a1e-136">呼叫發生在</span><span class="sxs-lookup"><span data-stu-id="45a1e-136">Calls occur within</span></span>|<span data-ttu-id="45a1e-137">成員名稱結果</span><span class="sxs-lookup"><span data-stu-id="45a1e-137">Member name result</span></span>|
|-|-|
|<span data-ttu-id="45a1e-138">方法、屬性或事件</span><span class="sxs-lookup"><span data-stu-id="45a1e-138">Method, property, or event</span></span>|<span data-ttu-id="45a1e-139">產生呼叫的方法、屬性或事件的名稱。</span><span class="sxs-lookup"><span data-stu-id="45a1e-139">The name of the method, property, or event from which the call originated.</span></span>|
|<span data-ttu-id="45a1e-140">建構函式</span><span class="sxs-lookup"><span data-stu-id="45a1e-140">Constructor</span></span>|<span data-ttu-id="45a1e-141">字串 ".ctor"</span><span class="sxs-lookup"><span data-stu-id="45a1e-141">The string ".ctor"</span></span>|
|<span data-ttu-id="45a1e-142">靜態建構函式</span><span class="sxs-lookup"><span data-stu-id="45a1e-142">Static constructor</span></span>|<span data-ttu-id="45a1e-143">字串 ".cctor"</span><span class="sxs-lookup"><span data-stu-id="45a1e-143">The string ".cctor"</span></span>|
|<span data-ttu-id="45a1e-144">解構函式</span><span class="sxs-lookup"><span data-stu-id="45a1e-144">Destructor</span></span>|<span data-ttu-id="45a1e-145">字串 "Finalize"</span><span class="sxs-lookup"><span data-stu-id="45a1e-145">The string "Finalize"</span></span>|
|<span data-ttu-id="45a1e-146">使用者定義的運算子或轉換</span><span class="sxs-lookup"><span data-stu-id="45a1e-146">User-defined operators or conversions</span></span>|<span data-ttu-id="45a1e-147">產生的成員名稱，例如 "op_Addition"。</span><span class="sxs-lookup"><span data-stu-id="45a1e-147">The generated name for the member, for example, "op_Addition".</span></span>|
|<span data-ttu-id="45a1e-148">屬性建構函式</span><span class="sxs-lookup"><span data-stu-id="45a1e-148">Attribute constructor</span></span>|<span data-ttu-id="45a1e-149">套用屬性 (attribute) 的方法或屬性 (property) 名稱。</span><span class="sxs-lookup"><span data-stu-id="45a1e-149">The name of the method or property to which the attribute is applied.</span></span> <span data-ttu-id="45a1e-150">如果屬性為成員內的任何項目 (例如參數、傳回值或泛型類型參數)，這個結果會是與該項目相關聯的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="45a1e-150">If the attribute is any element within a member (such as a parameter, a return value, or a generic type parameter), this result is the name of the member that's associated with that element.</span></span>|
|<span data-ttu-id="45a1e-151">無包含的成員 (例如，組件層級或套用至類型的屬性)。</span><span class="sxs-lookup"><span data-stu-id="45a1e-151">No containing member (for example, assembly-level or attributes that are applied to types)</span></span>|<span data-ttu-id="45a1e-152">選擇性參數的預設值。</span><span class="sxs-lookup"><span data-stu-id="45a1e-152">The default value of the optional parameter.</span></span>|

## <a name="see-also"></a><span data-ttu-id="45a1e-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45a1e-153">See also</span></span>

- [<span data-ttu-id="45a1e-154">具名和選擇性引數</span><span class="sxs-lookup"><span data-stu-id="45a1e-154">Named and Optional Arguments</span></span>](../../programming-guide/classes-and-structs/named-and-optional-arguments.md)
- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="45a1e-155">屬性</span><span class="sxs-lookup"><span data-stu-id="45a1e-155">Attributes</span></span>](../../../standard/attributes/index.md)
