---
title: '呼叫端資訊 （F #）'
description: 描述如何使用呼叫端資訊引數屬性來取得方法的呼叫端資訊。
ms.date: 04/25/2017
ms.openlocfilehash: 6fd80213cdaf2c4662fd4c2ed9eaf8949e397efe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564774"
---
# <a name="caller-information"></a><span data-ttu-id="8db0b-103">呼叫端資訊</span><span class="sxs-lookup"><span data-stu-id="8db0b-103">Caller information</span></span>

<span data-ttu-id="8db0b-104">使用 Caller Info 屬性，您就可以取得有關方法之呼叫端的資訊。</span><span class="sxs-lookup"><span data-stu-id="8db0b-104">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="8db0b-105">您可以取得原始程式碼的檔案路徑、原始程式碼中的行號，以及呼叫端的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="8db0b-105">You can obtain file path of the source code, the line number in the source code, and the member name of the caller.</span></span> <span data-ttu-id="8db0b-106">這項資訊有助於追蹤、偵錯及建立診斷工具。</span><span class="sxs-lookup"><span data-stu-id="8db0b-106">This information is helpful for tracing, debugging, and creating diagnostic tools.</span></span>

<span data-ttu-id="8db0b-107">若要取得這項資訊，可使用套用至選擇性參數的屬性，每個屬性都有預設值。</span><span class="sxs-lookup"><span data-stu-id="8db0b-107">To obtain this information, you use attributes that are applied to optional parameters, each of which has a default value.</span></span> <span data-ttu-id="8db0b-108">下表列出中所定義的 Caller Info 屬性[System.Runtime.CompilerServices](/dotnet/api/system.runtime.compilerservices)命名空間：</span><span class="sxs-lookup"><span data-stu-id="8db0b-108">The following table lists the Caller Info attributes that are defined in the [System.Runtime.CompilerServices](/dotnet/api/system.runtime.compilerservices) namespace:</span></span>

|<span data-ttu-id="8db0b-109">屬性</span><span class="sxs-lookup"><span data-stu-id="8db0b-109">Attribute</span></span>|<span data-ttu-id="8db0b-110">描述</span><span class="sxs-lookup"><span data-stu-id="8db0b-110">Description</span></span>|<span data-ttu-id="8db0b-111">類型</span><span class="sxs-lookup"><span data-stu-id="8db0b-111">Type</span></span>|
|---------|-----------|----|
|[<span data-ttu-id="8db0b-112">CallerFilePath</span><span class="sxs-lookup"><span data-stu-id="8db0b-112">CallerFilePath</span></span>](/dotnet/api/system.runtime.compilerservices.callerfilepathattribute)|<span data-ttu-id="8db0b-113">包含呼叫端的原始程式檔完整路徑。</span><span class="sxs-lookup"><span data-stu-id="8db0b-113">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="8db0b-114">這是編譯時間的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="8db0b-114">This is the file path at compile time.</span></span>|`String`
|[<span data-ttu-id="8db0b-115">CallerLineNumber</span><span class="sxs-lookup"><span data-stu-id="8db0b-115">CallerLineNumber</span></span>](/dotnet/api/system.runtime.compilerservices.callerlinenumberattribute)|<span data-ttu-id="8db0b-116">原始程式檔中呼叫方法所在的行號。</span><span class="sxs-lookup"><span data-stu-id="8db0b-116">Line number in the source file at which the method is called.</span></span>|`Integer`|
|[<span data-ttu-id="8db0b-117">CallerMemberName</span><span class="sxs-lookup"><span data-stu-id="8db0b-117">CallerMemberName</span></span>](/dotnet/api/system.runtime.compilerservices.callermembernameattribute)|<span data-ttu-id="8db0b-118">呼叫端的方法或屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="8db0b-118">Method or property name of the caller.</span></span> <span data-ttu-id="8db0b-119">請參閱本主題稍後的成員名稱 > 一節。</span><span class="sxs-lookup"><span data-stu-id="8db0b-119">See the Member Names section later in this topic.</span></span>|`String`|

## <a name="example"></a><span data-ttu-id="8db0b-120">範例</span><span class="sxs-lookup"><span data-stu-id="8db0b-120">Example</span></span>

<span data-ttu-id="8db0b-121">下列範例顯示如何使用這些屬性來追蹤呼叫端。</span><span class="sxs-lookup"><span data-stu-id="8db0b-121">The following example shows how you might use these attributes to trace a caller.</span></span>

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

## <a name="remarks"></a><span data-ttu-id="8db0b-122">備註</span><span class="sxs-lookup"><span data-stu-id="8db0b-122">Remarks</span></span>

<span data-ttu-id="8db0b-123">呼叫端資訊屬性只能套用至選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="8db0b-123">Caller Info attributes can only be applied to optional parameters.</span></span> <span data-ttu-id="8db0b-124">您必須提供明確的值為每個選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="8db0b-124">You must supply an explicit value for each optional parameter.</span></span> <span data-ttu-id="8db0b-125">Caller Info 屬性會導致編譯器寫入使用 Caller Info 屬性裝飾的每個選擇性參數的值。</span><span class="sxs-lookup"><span data-stu-id="8db0b-125">The Caller Info attributes cause the compiler to write the proper value for each optional parameter decorated with a Caller Info attribute.</span></span>

<span data-ttu-id="8db0b-126">在編譯時期，Caller Info 的值會做為常值發出至中繼語言 (IL)。</span><span class="sxs-lookup"><span data-stu-id="8db0b-126">Caller Info values are emitted as literals into the Intermediate Language (IL) at compile time.</span></span> <span data-ttu-id="8db0b-127">結果不同[StackTrace](/dotnet/api/system.diagnostics.stacktrace)屬性中的例外狀況，結果不受模糊化所影響。</span><span class="sxs-lookup"><span data-stu-id="8db0b-127">Unlike the results of the [StackTrace](/dotnet/api/system.diagnostics.stacktrace) property for exceptions, the results aren't affected by obfuscation.</span></span>

<span data-ttu-id="8db0b-128">您可以明確提供選擇性引數來控制呼叫端資訊，或是隱藏呼叫端資訊。</span><span class="sxs-lookup"><span data-stu-id="8db0b-128">You can explicitly supply the optional arguments to control the caller information or to hide caller information.</span></span>

## <a name="member-names"></a><span data-ttu-id="8db0b-129">成員名稱</span><span class="sxs-lookup"><span data-stu-id="8db0b-129">Member names</span></span>

<span data-ttu-id="8db0b-130">您可以使用[ `CallerMemberName` ](/dotnet/api/system.runtime.compilerservices.callermembernameattribute)屬性避免指定成員名稱做`String`引數呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="8db0b-130">You can use the [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) attribute to avoid specifying the member name as a `String` argument to the called method.</span></span> <span data-ttu-id="8db0b-131">您可以藉由使用這項技術，避免重新命名重構並不會變更的問題`String`值。</span><span class="sxs-lookup"><span data-stu-id="8db0b-131">By using this technique, you avoid the problem that Rename Refactoring doesn't change the `String` values.</span></span> <span data-ttu-id="8db0b-132">這項優點對於下列工作特別有用：</span><span class="sxs-lookup"><span data-stu-id="8db0b-132">This benefit is especially useful for the following tasks:</span></span>

* <span data-ttu-id="8db0b-133">使用追蹤和診斷常式。</span><span class="sxs-lookup"><span data-stu-id="8db0b-133">Using tracing and diagnostic routines.</span></span>
* <span data-ttu-id="8db0b-134">實作[INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged)資料繫結時的介面。</span><span class="sxs-lookup"><span data-stu-id="8db0b-134">Implementing the [INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged) interface when binding data.</span></span> <span data-ttu-id="8db0b-135">這個介面可讓物件的屬性告知繫結的控制項屬性已變更，所以控制項可以顯示更新的資訊。</span><span class="sxs-lookup"><span data-stu-id="8db0b-135">This interface allows the property of an object to notify a bound control that the property has changed, so that the control can display the updated information.</span></span> <span data-ttu-id="8db0b-136">不含[ `CallerMemberName` ](/dotnet/api/system.runtime.compilerservices.callermembernameattribute)屬性，您必須為常值指定屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="8db0b-136">Without the [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) attribute, you must specify the property name as a literal.</span></span>

<span data-ttu-id="8db0b-137">下圖顯示當您使用，CallerMemberName 屬性傳回的名稱的成員。</span><span class="sxs-lookup"><span data-stu-id="8db0b-137">The following chart shows the member names that are returned when you use the CallerMemberName attribute.</span></span>

|<span data-ttu-id="8db0b-138">呼叫發生於</span><span class="sxs-lookup"><span data-stu-id="8db0b-138">Calls occurs within</span></span>|<span data-ttu-id="8db0b-139">成員名稱結果</span><span class="sxs-lookup"><span data-stu-id="8db0b-139">Member name result</span></span>|
|-------------------|------------------|
|<span data-ttu-id="8db0b-140">方法、屬性或事件</span><span class="sxs-lookup"><span data-stu-id="8db0b-140">Method, property, or event</span></span>|<span data-ttu-id="8db0b-141">產生呼叫的方法、屬性或事件的名稱。</span><span class="sxs-lookup"><span data-stu-id="8db0b-141">The name of the method, property, or event from which the call originated.</span></span>|
|<span data-ttu-id="8db0b-142">建構函式</span><span class="sxs-lookup"><span data-stu-id="8db0b-142">Constructor</span></span>|<span data-ttu-id="8db0b-143">字串 ".ctor"</span><span class="sxs-lookup"><span data-stu-id="8db0b-143">The string ".ctor"</span></span>|
|<span data-ttu-id="8db0b-144">靜態建構函式</span><span class="sxs-lookup"><span data-stu-id="8db0b-144">Static constructor</span></span>|<span data-ttu-id="8db0b-145">字串 ".cctor"</span><span class="sxs-lookup"><span data-stu-id="8db0b-145">The string ".cctor"</span></span>|
|<span data-ttu-id="8db0b-146">解構函式</span><span class="sxs-lookup"><span data-stu-id="8db0b-146">Destructor</span></span>|<span data-ttu-id="8db0b-147">字串 "Finalize"</span><span class="sxs-lookup"><span data-stu-id="8db0b-147">The string "Finalize"</span></span>|
|<span data-ttu-id="8db0b-148">使用者定義的運算子或轉換</span><span class="sxs-lookup"><span data-stu-id="8db0b-148">User-defined operators or conversions</span></span>|<span data-ttu-id="8db0b-149">產生的成員名稱，例如 "op_Addition"。</span><span class="sxs-lookup"><span data-stu-id="8db0b-149">The generated name for the member, for example, "op_Addition".</span></span>|
|<span data-ttu-id="8db0b-150">屬性建構函式</span><span class="sxs-lookup"><span data-stu-id="8db0b-150">Attribute constructor</span></span>|<span data-ttu-id="8db0b-151">套用屬性的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="8db0b-151">The name of the member to which the attribute is applied.</span></span> <span data-ttu-id="8db0b-152">如果屬性為成員內的任何項目 (例如參數、傳回值或泛型類型參數)，這個結果會是與該項目相關聯的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="8db0b-152">If the attribute is any element within a member (such as a parameter, a return value, or a generic type parameter), this result is the name of the member that's associated with that element.</span></span>|
|<span data-ttu-id="8db0b-153">無包含的成員 (例如，組件層級或套用至類型的屬性)。</span><span class="sxs-lookup"><span data-stu-id="8db0b-153">No containing member (for example, assembly-level or attributes that are applied to types)</span></span>|<span data-ttu-id="8db0b-154">選擇性參數的預設值。</span><span class="sxs-lookup"><span data-stu-id="8db0b-154">The default value of the optional parameter.</span></span>|

## <a name="see-also"></a><span data-ttu-id="8db0b-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8db0b-155">See also</span></span>
 [<span data-ttu-id="8db0b-156">屬性</span><span class="sxs-lookup"><span data-stu-id="8db0b-156">Attributes</span></span>](attributes.md)  
 [<span data-ttu-id="8db0b-157">具名引數</span><span class="sxs-lookup"><span data-stu-id="8db0b-157">Named arguments</span></span>](parameters-and-arguments.md#named-arguments)  
 [<span data-ttu-id="8db0b-158">選擇性參數</span><span class="sxs-lookup"><span data-stu-id="8db0b-158">Optional parameters</span></span>](parameters-and-arguments.md#optional-parameters)  
