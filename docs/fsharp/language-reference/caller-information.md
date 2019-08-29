---
title: 呼叫端資訊
description: 描述如何使用呼叫端資訊引數屬性, 從方法取得呼叫端資訊。
ms.date: 04/25/2017
ms.openlocfilehash: e7bbc3830a95bd25cfc2fb369b204d367b775815
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106588"
---
# <a name="caller-information"></a><span data-ttu-id="a2cb2-103">呼叫端資訊</span><span class="sxs-lookup"><span data-stu-id="a2cb2-103">Caller information</span></span>

<span data-ttu-id="a2cb2-104">使用 Caller Info 屬性，您就可以取得有關方法之呼叫端的資訊。</span><span class="sxs-lookup"><span data-stu-id="a2cb2-104">By using Caller Info attributes, you can obtain information about the caller to a method.</span></span> <span data-ttu-id="a2cb2-105">您可以取得原始程式碼的檔案路徑、原始程式碼中的行號，以及呼叫端的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="a2cb2-105">You can obtain file path of the source code, the line number in the source code, and the member name of the caller.</span></span> <span data-ttu-id="a2cb2-106">這項資訊有助於追蹤、偵錯及建立診斷工具。</span><span class="sxs-lookup"><span data-stu-id="a2cb2-106">This information is helpful for tracing, debugging, and creating diagnostic tools.</span></span>

<span data-ttu-id="a2cb2-107">若要取得這項資訊，可使用套用至選擇性參數的屬性，每個屬性都有預設值。</span><span class="sxs-lookup"><span data-stu-id="a2cb2-107">To obtain this information, you use attributes that are applied to optional parameters, each of which has a default value.</span></span> <span data-ttu-id="a2cb2-108">下表列出在[CompilerServices](/dotnet/api/system.runtime.compilerservices)命名空間中定義的呼叫端資訊屬性:</span><span class="sxs-lookup"><span data-stu-id="a2cb2-108">The following table lists the Caller Info attributes that are defined in the [System.Runtime.CompilerServices](/dotnet/api/system.runtime.compilerservices) namespace:</span></span>

|<span data-ttu-id="a2cb2-109">屬性</span><span class="sxs-lookup"><span data-stu-id="a2cb2-109">Attribute</span></span>|<span data-ttu-id="a2cb2-110">描述</span><span class="sxs-lookup"><span data-stu-id="a2cb2-110">Description</span></span>|<span data-ttu-id="a2cb2-111">類型</span><span class="sxs-lookup"><span data-stu-id="a2cb2-111">Type</span></span>|
|---------|-----------|----|
|[<span data-ttu-id="a2cb2-112">CallerFilePath</span><span class="sxs-lookup"><span data-stu-id="a2cb2-112">CallerFilePath</span></span>](/dotnet/api/system.runtime.compilerservices.callerfilepathattribute)|<span data-ttu-id="a2cb2-113">包含呼叫端的原始程式檔完整路徑。</span><span class="sxs-lookup"><span data-stu-id="a2cb2-113">Full path of the source file that contains the caller.</span></span> <span data-ttu-id="a2cb2-114">這是編譯時間的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="a2cb2-114">This is the file path at compile time.</span></span>|`String`
|[<span data-ttu-id="a2cb2-115">CallerLineNumber</span><span class="sxs-lookup"><span data-stu-id="a2cb2-115">CallerLineNumber</span></span>](/dotnet/api/system.runtime.compilerservices.callerlinenumberattribute)|<span data-ttu-id="a2cb2-116">原始程式檔中呼叫方法所在的行號。</span><span class="sxs-lookup"><span data-stu-id="a2cb2-116">Line number in the source file at which the method is called.</span></span>|`Integer`|
|[<span data-ttu-id="a2cb2-117">CallerMemberName</span><span class="sxs-lookup"><span data-stu-id="a2cb2-117">CallerMemberName</span></span>](/dotnet/api/system.runtime.compilerservices.callermembernameattribute)|<span data-ttu-id="a2cb2-118">呼叫端的方法或屬性名稱。</span><span class="sxs-lookup"><span data-stu-id="a2cb2-118">Method or property name of the caller.</span></span> <span data-ttu-id="a2cb2-119">請參閱本主題稍後的成員名稱一節。</span><span class="sxs-lookup"><span data-stu-id="a2cb2-119">See the Member Names section later in this topic.</span></span>|`String`|

## <a name="example"></a><span data-ttu-id="a2cb2-120">範例</span><span class="sxs-lookup"><span data-stu-id="a2cb2-120">Example</span></span>

<span data-ttu-id="a2cb2-121">下列範例會示範如何使用這些屬性來追蹤呼叫端。</span><span class="sxs-lookup"><span data-stu-id="a2cb2-121">The following example shows how you might use these attributes to trace a caller.</span></span>

```fsharp
open System.Diagnostics
open System.Runtime.CompilerServices
open System.Runtime.InteropServices

type Tracer() =
    member __.DoTrace(message: string,
                      [<CallerMemberName; Optional; DefaultParameterValue("")>] memberName: string,
                      [<CallerFilePath; Optional; DefaultParameterValue("")>] path: string,
                      [<CallerLineNumber; Optional; DefaultParameterValue(0)>] line: int) =
        Trace.WriteLine(sprintf "Message: %s" message)
        Trace.WriteLine(sprintf "Member name: %s" memberName)
        Trace.WriteLine(sprintf "Source file path: %s" path)
        Trace.WriteLine(sprintf "Source line number: %d" line)
```

## <a name="remarks"></a><span data-ttu-id="a2cb2-122">備註</span><span class="sxs-lookup"><span data-stu-id="a2cb2-122">Remarks</span></span>

<span data-ttu-id="a2cb2-123">呼叫端資訊屬性只能套用至選擇性參數。</span><span class="sxs-lookup"><span data-stu-id="a2cb2-123">Caller Info attributes can only be applied to optional parameters.</span></span> <span data-ttu-id="a2cb2-124">呼叫端資訊屬性會使編譯器為每個以呼叫者資訊屬性裝飾的選擇性參數寫入適當的值。</span><span class="sxs-lookup"><span data-stu-id="a2cb2-124">The Caller Info attributes cause the compiler to write the proper value for each optional parameter decorated with a Caller Info attribute.</span></span>

<span data-ttu-id="a2cb2-125">在編譯時期，Caller Info 的值會做為常值發出至中繼語言 (IL)。</span><span class="sxs-lookup"><span data-stu-id="a2cb2-125">Caller Info values are emitted as literals into the Intermediate Language (IL) at compile time.</span></span> <span data-ttu-id="a2cb2-126">不同于例外狀況的[StackTrace](/dotnet/api/system.diagnostics.stacktrace)屬性結果, 結果不會受到模糊處理的影響。</span><span class="sxs-lookup"><span data-stu-id="a2cb2-126">Unlike the results of the [StackTrace](/dotnet/api/system.diagnostics.stacktrace) property for exceptions, the results aren't affected by obfuscation.</span></span>

<span data-ttu-id="a2cb2-127">您可以明確提供選擇性引數來控制呼叫端資訊，或是隱藏呼叫端資訊。</span><span class="sxs-lookup"><span data-stu-id="a2cb2-127">You can explicitly supply the optional arguments to control the caller information or to hide caller information.</span></span>

## <a name="member-names"></a><span data-ttu-id="a2cb2-128">成員名稱</span><span class="sxs-lookup"><span data-stu-id="a2cb2-128">Member names</span></span>

<span data-ttu-id="a2cb2-129">您可以使用[`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute)屬性, 避免將成員名稱指定`String`為所呼叫方法的引數。</span><span class="sxs-lookup"><span data-stu-id="a2cb2-129">You can use the [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) attribute to avoid specifying the member name as a `String` argument to the called method.</span></span> <span data-ttu-id="a2cb2-130">藉由使用這項技術, 您可以避免重新命名重構不會`String`變更值的問題。</span><span class="sxs-lookup"><span data-stu-id="a2cb2-130">By using this technique, you avoid the problem that Rename Refactoring doesn't change the `String` values.</span></span> <span data-ttu-id="a2cb2-131">這項優點對於下列工作特別有用：</span><span class="sxs-lookup"><span data-stu-id="a2cb2-131">This benefit is especially useful for the following tasks:</span></span>

- <span data-ttu-id="a2cb2-132">使用追蹤和診斷常式。</span><span class="sxs-lookup"><span data-stu-id="a2cb2-132">Using tracing and diagnostic routines.</span></span>
- <span data-ttu-id="a2cb2-133">系結資料時, 執行[INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged)介面。</span><span class="sxs-lookup"><span data-stu-id="a2cb2-133">Implementing the [INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged) interface when binding data.</span></span> <span data-ttu-id="a2cb2-134">這個介面可讓物件的屬性告知繫結的控制項屬性已變更，所以控制項可以顯示更新的資訊。</span><span class="sxs-lookup"><span data-stu-id="a2cb2-134">This interface allows the property of an object to notify a bound control that the property has changed, so that the control can display the updated information.</span></span> <span data-ttu-id="a2cb2-135">如果沒有[`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute)屬性, 您必須將屬性名稱指定為常值。</span><span class="sxs-lookup"><span data-stu-id="a2cb2-135">Without the [`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute) attribute, you must specify the property name as a literal.</span></span>

<span data-ttu-id="a2cb2-136">下圖顯示當您使用 CallerMemberName 屬性時, 所傳回的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="a2cb2-136">The following chart shows the member names that are returned when you use the CallerMemberName attribute.</span></span>

|<span data-ttu-id="a2cb2-137">呼叫發生於</span><span class="sxs-lookup"><span data-stu-id="a2cb2-137">Calls occurs within</span></span>|<span data-ttu-id="a2cb2-138">成員名稱結果</span><span class="sxs-lookup"><span data-stu-id="a2cb2-138">Member name result</span></span>|
|-------------------|------------------|
|<span data-ttu-id="a2cb2-139">方法、屬性或事件</span><span class="sxs-lookup"><span data-stu-id="a2cb2-139">Method, property, or event</span></span>|<span data-ttu-id="a2cb2-140">產生呼叫的方法、屬性或事件的名稱。</span><span class="sxs-lookup"><span data-stu-id="a2cb2-140">The name of the method, property, or event from which the call originated.</span></span>|
|<span data-ttu-id="a2cb2-141">建構函式</span><span class="sxs-lookup"><span data-stu-id="a2cb2-141">Constructor</span></span>|<span data-ttu-id="a2cb2-142">字串 ".ctor"</span><span class="sxs-lookup"><span data-stu-id="a2cb2-142">The string ".ctor"</span></span>|
|<span data-ttu-id="a2cb2-143">靜態建構函式</span><span class="sxs-lookup"><span data-stu-id="a2cb2-143">Static constructor</span></span>|<span data-ttu-id="a2cb2-144">字串 ".cctor"</span><span class="sxs-lookup"><span data-stu-id="a2cb2-144">The string ".cctor"</span></span>|
|<span data-ttu-id="a2cb2-145">解構函式</span><span class="sxs-lookup"><span data-stu-id="a2cb2-145">Destructor</span></span>|<span data-ttu-id="a2cb2-146">字串 "Finalize"</span><span class="sxs-lookup"><span data-stu-id="a2cb2-146">The string "Finalize"</span></span>|
|<span data-ttu-id="a2cb2-147">使用者定義的運算子或轉換</span><span class="sxs-lookup"><span data-stu-id="a2cb2-147">User-defined operators or conversions</span></span>|<span data-ttu-id="a2cb2-148">產生的成員名稱，例如 "op_Addition"。</span><span class="sxs-lookup"><span data-stu-id="a2cb2-148">The generated name for the member, for example, "op_Addition".</span></span>|
|<span data-ttu-id="a2cb2-149">屬性建構函式</span><span class="sxs-lookup"><span data-stu-id="a2cb2-149">Attribute constructor</span></span>|<span data-ttu-id="a2cb2-150">套用屬性的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="a2cb2-150">The name of the member to which the attribute is applied.</span></span> <span data-ttu-id="a2cb2-151">如果屬性為成員內的任何項目 (例如參數、傳回值或泛型類型參數)，這個結果會是與該項目相關聯的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="a2cb2-151">If the attribute is any element within a member (such as a parameter, a return value, or a generic type parameter), this result is the name of the member that's associated with that element.</span></span>|
|<span data-ttu-id="a2cb2-152">無包含的成員 (例如，組件層級或套用至類型的屬性)。</span><span class="sxs-lookup"><span data-stu-id="a2cb2-152">No containing member (for example, assembly-level or attributes that are applied to types)</span></span>|<span data-ttu-id="a2cb2-153">選擇性參數的預設值。</span><span class="sxs-lookup"><span data-stu-id="a2cb2-153">The default value of the optional parameter.</span></span>|

## <a name="see-also"></a><span data-ttu-id="a2cb2-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a2cb2-154">See also</span></span>

- [<span data-ttu-id="a2cb2-155">屬性</span><span class="sxs-lookup"><span data-stu-id="a2cb2-155">Attributes</span></span>](attributes.md)
- [<span data-ttu-id="a2cb2-156">具名引數</span><span class="sxs-lookup"><span data-stu-id="a2cb2-156">Named arguments</span></span>](parameters-and-arguments.md#named-arguments)
- [<span data-ttu-id="a2cb2-157">選擇性參數</span><span class="sxs-lookup"><span data-stu-id="a2cb2-157">Optional parameters</span></span>](parameters-and-arguments.md#optional-parameters)
