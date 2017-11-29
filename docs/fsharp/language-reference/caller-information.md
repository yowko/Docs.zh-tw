---
title: "呼叫端資訊 （F #）"
description: "描述如何使用呼叫端資訊引數屬性來取得方法的呼叫端資訊。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 04/25/2017
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: a3dcc335-433b-4672-ac2d-ae6b11b816f3
ms.openlocfilehash: 533d2f0429ddb31e6d1dd7efca2f0760069a2945
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="caller-information"></a><span data-ttu-id="c6d6a-104">呼叫端資訊</span><span class="sxs-lookup"><span data-stu-id="c6d6a-104">Caller information</span></span>

<span data-ttu-id="c6d6a-105">使用 Caller Info 屬性，您就可以取得有關方法之呼叫端的資訊。</span><span class="sxs-lookup"><span data-stu-id="c6d6a-105">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="c6d6a-106">您可以取得原始程式碼的檔案路徑、原始程式碼中的行號，以及呼叫端的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="c6d6a-106">You can obtain file path of the source code, the line number in the source code, and the member name of the caller.</span></span> <span data-ttu-id="c6d6a-107">這項資訊有助於追蹤、偵錯及建立診斷工具。</span><span class="sxs-lookup"><span data-stu-id="c6d6a-107">This information is helpful for tracing, debugging, and creating diagnostic tools.</span></span>

<span data-ttu-id="c6d6a-108">若要取得這項資訊，可使用套用至選擇性參數的屬性，每個屬性都有預設值。</span><span class="sxs-lookup"><span data-stu-id="c6d6a-108">To obtain this information, you use attributes that are applied to optional parameters, each of which has a default value.</span></span> <span data-ttu-id="c6d6a-109">下表列出中所定義的 Caller Info 屬性[System.Runtime.CompilerServices](/dotnet/api/system.runtime.compilerservices)命名空間：</span><span class="sxs-lookup"><span data-stu-id="c6d6a-109">The following table lists the Caller Info attributes that are defined in the [System.Runtime.CompilerServices](/dotnet/api/system.runtime.compilerservices) namespace:</span></span>

|<span data-ttu-id="c6d6a-110">屬性</span><span class="sxs-lookup"><span data-stu-id="c6d6a-110">Attribute</span></span>|<span data-ttu-id="c6d6a-111">描述</span><span class="sxs-lookup"><span data-stu-id="c6d6a-111">Description</span></span>|<span data-ttu-id="c6d6a-112">類型</span><span class="sxs-lookup"><span data-stu-id="c6d6a-112">Type</span></span>|
|---------|-----------|----|
|[<span data-ttu-id="c6d6a-113">CallerFilePath</span><span class="sxs-lookup"><span data-stu-id="c6d6a-113">CallerFilePath</span></span>](/dotnet/api/system.runtime.compilerservices.callerfilepathattribute)|<span data-ttu-id="c6d6a-114">包含呼叫端的原始程式檔完整路徑。</span><span class="sxs-lookup"><span data-stu-id="c6d6a-114">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="c6d6a-115">這是編譯時間的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="c6d6a-115">This is the file path at compile time.</span></span>|`String`
|[<span data-ttu-id="c6d6a-116">CallerLineNumber</span><span class="sxs-lookup"><span data-stu-id="c6d6a-116">CallerLineNumber</span></span>](/dotnet/api/system.runtime.compilerservices.callerlinenumberattribute)|<span data-ttu-id="c6d6a-117">原始程式檔中呼叫方法所在的行號。</span><span class="sxs-lookup"><span data-stu-id="c6d6a-117">Line number in the source file at which the method is called.</span></span>|`Integer`|
|[<span data-ttu-id="c6d6a-118">CallerMemberName</span><span class="sxs-lookup"><span data-stu-id="c6d6a-118">CallerMemberName</span></span>](/dotnet/api/system.runtime.compilerservices.callermembernameattribute)|<span data-ttu-id="c6d6a-119">呼叫端的方法或屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="c6d6a-119">Method or property name of the caller.</span></span> <span data-ttu-id="c6d6a-120">請參閱本主題稍後的成員名稱 > 一節。</span><span class="sxs-lookup"><span data-stu-id="c6d6a-120">See the Member Names section later in this topic.</span></span>|`String`|

## <a name="example"></a><span data-ttu-id="c6d6a-121">範例</span><span class="sxs-lookup"><span data-stu-id="c6d6a-121">Example</span></span>

<span data-ttu-id="c6d6a-122">下列範例顯示如何使用這些屬性來追蹤呼叫端。</span><span class="sxs-lookup"><span data-stu-id="c6d6a-122">The following example shows how you might use these attributes to trace a caller.</span></span>

```fsharp
open System.Diagnostics
open System.Runtime.CompilerServices

type Tracer() =
    member __.DoTrace(msg: string,
                      [<CallerMemberName>] ?memberName: string,
                      [<CallerFilePath>] ?path: string
                      [<CallerLineNumber>] ?line: int) =
        Trace.WriteLine(sprintf "Message: %s" message)
        match (memberName, path, line) with
        | Some m, Some p, Some l ->
            Trace.WriteLine(sprintf "Member name: %s" m)
            Trace.WriteLine(sprintf "Source file path: %s" p)
            Trace.WriteLine(sprintf "Source line number: %d" l)
        | _,_,_ -> ()
```

## <a name="remarks"></a><span data-ttu-id="c6d6a-123">備註</span><span class="sxs-lookup"><span data-stu-id="c6d6a-123">Remarks</span></span>

<span data-ttu-id="c6d6a-124">呼叫端資訊屬性只能套用至選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="c6d6a-124">Caller Info attributes can only be applied to optional parameters.</span></span> <span data-ttu-id="c6d6a-125">您必須提供明確的值為每個選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="c6d6a-125">You must supply an explicit value for each optional parameter.</span></span> <span data-ttu-id="c6d6a-126">Caller Info 屬性會導致編譯器寫入使用 Caller Info 屬性裝飾的每個選擇性參數的值。</span><span class="sxs-lookup"><span data-stu-id="c6d6a-126">The Caller Info attributes cause the compiler to write the proper value for each optional parameter decorated with a Caller Info attribute.</span></span>

<span data-ttu-id="c6d6a-127">在編譯時期，Caller Info 的值會做為常值發出至中繼語言 (IL)。</span><span class="sxs-lookup"><span data-stu-id="c6d6a-127">Caller Info values are emitted as literals into the Intermediate Language (IL) at compile time.</span></span> <span data-ttu-id="c6d6a-128">結果不同[StackTrace](/dotnet/api/system.diagnostics.stacktrace)屬性中的例外狀況，結果不受模糊化所影響。</span><span class="sxs-lookup"><span data-stu-id="c6d6a-128">Unlike the results of the [StackTrace](/dotnet/api/system.diagnostics.stacktrace) property for exceptions, the results aren't affected by obfuscation.</span></span>

<span data-ttu-id="c6d6a-129">您可以明確提供選擇性引數來控制呼叫端資訊，或是隱藏呼叫端資訊。</span><span class="sxs-lookup"><span data-stu-id="c6d6a-129">You can explicitly supply the optional arguments to control the caller information or to hide caller information.</span></span>

## <a name="member-names"></a><span data-ttu-id="c6d6a-130">成員名稱</span><span class="sxs-lookup"><span data-stu-id="c6d6a-130">Member names</span></span>

<span data-ttu-id="c6d6a-131">您可以使用[ `CallerMemberName` ](/dotnet/api/system.runtime.compilerservices.callermembernameattribute)屬性避免指定成員名稱做`String`引數呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="c6d6a-131">You can use the [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) attribute to avoid specifying the member name as a `String` argument to the called method.</span></span> <span data-ttu-id="c6d6a-132">您可以藉由使用這項技術，避免重新命名重構並不會變更的問題`String`值。</span><span class="sxs-lookup"><span data-stu-id="c6d6a-132">By using this technique, you avoid the problem that Rename Refactoring doesn't change the `String` values.</span></span> <span data-ttu-id="c6d6a-133">這項優點對於下列工作特別有用：</span><span class="sxs-lookup"><span data-stu-id="c6d6a-133">This benefit is especially useful for the following tasks:</span></span>

* <span data-ttu-id="c6d6a-134">使用追蹤和診斷常式。</span><span class="sxs-lookup"><span data-stu-id="c6d6a-134">Using tracing and diagnostic routines.</span></span>
* <span data-ttu-id="c6d6a-135">實作[INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged)資料繫結時的介面。</span><span class="sxs-lookup"><span data-stu-id="c6d6a-135">Implementing the [INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged) interface when binding data.</span></span> <span data-ttu-id="c6d6a-136">這個介面可讓物件的屬性告知繫結的控制項屬性已變更，所以控制項可以顯示更新的資訊。</span><span class="sxs-lookup"><span data-stu-id="c6d6a-136">This interface allows the property of an object to notify a bound control that the property has changed, so that the control can display the updated information.</span></span> <span data-ttu-id="c6d6a-137">不含[ `CallerMemberName` ](/dotnet/api/system.runtime.compilerservices.callermembernameattribute)屬性，您必須為常值指定屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="c6d6a-137">Without the [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) attribute, you must specify the property name as a literal.</span></span>

<span data-ttu-id="c6d6a-138">下圖顯示當您使用，CallerMemberName 屬性傳回的名稱的成員。</span><span class="sxs-lookup"><span data-stu-id="c6d6a-138">The following chart shows the member names that are returned when you use the CallerMemberName attribute.</span></span>

|<span data-ttu-id="c6d6a-139">呼叫發生於</span><span class="sxs-lookup"><span data-stu-id="c6d6a-139">Calls occurs within</span></span>|<span data-ttu-id="c6d6a-140">成員名稱結果</span><span class="sxs-lookup"><span data-stu-id="c6d6a-140">Member name result</span></span>|
|-------------------|------------------|
|<span data-ttu-id="c6d6a-141">方法、屬性或事件</span><span class="sxs-lookup"><span data-stu-id="c6d6a-141">Method, property, or event</span></span>|<span data-ttu-id="c6d6a-142">產生呼叫的方法、屬性或事件的名稱。</span><span class="sxs-lookup"><span data-stu-id="c6d6a-142">The name of the method, property, or event from which the call originated.</span></span>|
|<span data-ttu-id="c6d6a-143">建構函式</span><span class="sxs-lookup"><span data-stu-id="c6d6a-143">Constructor</span></span>|<span data-ttu-id="c6d6a-144">字串 ".ctor"</span><span class="sxs-lookup"><span data-stu-id="c6d6a-144">The string ".ctor"</span></span>|
|<span data-ttu-id="c6d6a-145">靜態建構函式</span><span class="sxs-lookup"><span data-stu-id="c6d6a-145">Static constructor</span></span>|<span data-ttu-id="c6d6a-146">字串 ".cctor"</span><span class="sxs-lookup"><span data-stu-id="c6d6a-146">The string ".cctor"</span></span>|
|<span data-ttu-id="c6d6a-147">解構函式</span><span class="sxs-lookup"><span data-stu-id="c6d6a-147">Destructor</span></span>|<span data-ttu-id="c6d6a-148">字串 "Finalize"</span><span class="sxs-lookup"><span data-stu-id="c6d6a-148">The string "Finalize"</span></span>|
|<span data-ttu-id="c6d6a-149">使用者定義的運算子或轉換</span><span class="sxs-lookup"><span data-stu-id="c6d6a-149">User-defined operators or conversions</span></span>|<span data-ttu-id="c6d6a-150">產生的成員名稱，例如 "op_Addition"。</span><span class="sxs-lookup"><span data-stu-id="c6d6a-150">The generated name for the member, for example, "op_Addition".</span></span>|
|<span data-ttu-id="c6d6a-151">屬性建構函式</span><span class="sxs-lookup"><span data-stu-id="c6d6a-151">Attribute constructor</span></span>|<span data-ttu-id="c6d6a-152">套用屬性的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="c6d6a-152">The name of the member to which the attribute is applied.</span></span> <span data-ttu-id="c6d6a-153">如果屬性為成員內的任何項目 (例如參數、傳回值或泛型類型參數)，這個結果會是與該項目相關聯的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="c6d6a-153">If the attribute is any element within a member (such as a parameter, a return value, or a generic type parameter), this result is the name of the member that's associated with that element.</span></span>|
|<span data-ttu-id="c6d6a-154">無包含的成員 (例如，組件層級或套用至類型的屬性)。</span><span class="sxs-lookup"><span data-stu-id="c6d6a-154">No containing member (for example, assembly-level or attributes that are applied to types)</span></span>|<span data-ttu-id="c6d6a-155">選擇性參數的預設值。</span><span class="sxs-lookup"><span data-stu-id="c6d6a-155">The default value of the optional parameter.</span></span>|

## <a name="see-also"></a><span data-ttu-id="c6d6a-156">請參閱</span><span class="sxs-lookup"><span data-stu-id="c6d6a-156">See also</span></span>
 [<span data-ttu-id="c6d6a-157">屬性</span><span class="sxs-lookup"><span data-stu-id="c6d6a-157">Attributes</span></span>](attributes.md)  
 [<span data-ttu-id="c6d6a-158">具名引數</span><span class="sxs-lookup"><span data-stu-id="c6d6a-158">Named arguments</span></span>](parameters-and-arguments.md#named-arguments)  
 [<span data-ttu-id="c6d6a-159">選擇性參數</span><span class="sxs-lookup"><span data-stu-id="c6d6a-159">Optional parameters</span></span>](parameters-and-arguments.md#optional-parameters)  
