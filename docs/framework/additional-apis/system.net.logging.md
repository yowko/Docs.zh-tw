---
title: 記錄類別（System.Net）
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Logging
- System.Net.Logging.Associate
- System.Net.Logging.Enter
- System.Net.Logging.Exception
- System.Net.Logging.Exit
- System.Net.Logging.get_Http
- System.Net.Logging.get_On
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: ad85fdd41252ed147eb5fe1a9db029db046d720c
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990335"
---
# <a name="logging-class"></a><span data-ttu-id="b21ad-102">Logging 類別</span><span class="sxs-lookup"><span data-stu-id="b21ad-102">Logging class</span></span>

<span data-ttu-id="b21ad-103">提供追蹤記錄功能。</span><span class="sxs-lookup"><span data-stu-id="b21ad-103">Provides trace logging functionality.</span></span>

```csharp
internal class Logging
```

> [!WARNING]
> <span data-ttu-id="b21ad-104">這個類別是內部的，不適合直接在程式碼中使用。</span><span class="sxs-lookup"><span data-stu-id="b21ad-104">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="b21ad-105">在任何情況下，Microsoft 不支援在生產應用程式中使用此類別。</span><span class="sxs-lookup"><span data-stu-id="b21ad-105">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="associate-method"></a><span data-ttu-id="b21ad-106">關聯方法</span><span class="sxs-lookup"><span data-stu-id="b21ad-106">Associate method</span></span>

<span data-ttu-id="b21ad-107">記錄兩個物件彼此關聯的資訊。</span><span class="sxs-lookup"><span data-stu-id="b21ad-107">Logs information that two objects are associated with each other.</span></span>

```csharp
internal static void Associate(TraceSource traceSource, object objA, object objB)
```

### <a name="parameters"></a><span data-ttu-id="b21ad-108">參數</span><span class="sxs-lookup"><span data-stu-id="b21ad-108">Parameters</span></span>

- <span data-ttu-id="b21ad-109">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="b21ad-109">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="b21ad-110">要記錄事件的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="b21ad-110">The trace source to log the event to.</span></span>

- <span data-ttu-id="b21ad-111">`objA` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="b21ad-111">`objA` <xref:System.Object></span></span>

  <span data-ttu-id="b21ad-112">要與相關聯的物件 `objB` 。</span><span class="sxs-lookup"><span data-stu-id="b21ad-112">The object to associate with `objB`.</span></span>

- <span data-ttu-id="b21ad-113">`objB` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="b21ad-113">`objB` <xref:System.Object></span></span>

  <span data-ttu-id="b21ad-114">要與相關聯的物件 `objA` 。</span><span class="sxs-lookup"><span data-stu-id="b21ad-114">The object to associate with `objA`.</span></span>

## <a name="entertracesource-object-string-string-method"></a><span data-ttu-id="b21ad-115">輸入（TraceSource、object、string、string）方法</span><span class="sxs-lookup"><span data-stu-id="b21ad-115">Enter(TraceSource, object, string, string) method</span></span>

<span data-ttu-id="b21ad-116">將進入方法的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="b21ad-116">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, object obj, string method, string param)
```

### <a name="parameters"></a><span data-ttu-id="b21ad-117">參數</span><span class="sxs-lookup"><span data-stu-id="b21ad-117">Parameters</span></span>

- <span data-ttu-id="b21ad-118">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="b21ad-118">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="b21ad-119">要記錄事件的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="b21ad-119">The trace source to log the event to.</span></span>

- <span data-ttu-id="b21ad-120">`obj` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="b21ad-120">`obj` <xref:System.Object></span></span>

  <span data-ttu-id="b21ad-121">呼叫方法的物件。</span><span class="sxs-lookup"><span data-stu-id="b21ad-121">The object that the method was called on.</span></span>

- <span data-ttu-id="b21ad-122">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="b21ad-122">`method` <xref:System.String></span></span>

  <span data-ttu-id="b21ad-123">要輸入的方法。</span><span class="sxs-lookup"><span data-stu-id="b21ad-123">The method that is being entered.</span></span>

- <span data-ttu-id="b21ad-124">`param` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="b21ad-124">`param` <xref:System.String></span></span>

  <span data-ttu-id="b21ad-125">傳遞給方法的參數。</span><span class="sxs-lookup"><span data-stu-id="b21ad-125">The parameters that were passed to the method.</span></span>

## <a name="entertracesource-object-string-object-method"></a><span data-ttu-id="b21ad-126">輸入（TraceSource、object、string、object）方法</span><span class="sxs-lookup"><span data-stu-id="b21ad-126">Enter(TraceSource, object, string, object) method</span></span>

<span data-ttu-id="b21ad-127">將進入方法的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="b21ad-127">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, object obj, string method, object paramObject)
```

### <a name="parameters"></a><span data-ttu-id="b21ad-128">參數</span><span class="sxs-lookup"><span data-stu-id="b21ad-128">Parameters</span></span>

- <span data-ttu-id="b21ad-129">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="b21ad-129">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="b21ad-130">要記錄事件的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="b21ad-130">The trace source to log the event to.</span></span>

- <span data-ttu-id="b21ad-131">`obj` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="b21ad-131">`obj` <xref:System.Object></span></span>

  <span data-ttu-id="b21ad-132">呼叫方法的物件。</span><span class="sxs-lookup"><span data-stu-id="b21ad-132">The object that the method was called on.</span></span>

- <span data-ttu-id="b21ad-133">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="b21ad-133">`method` <xref:System.String></span></span>

  <span data-ttu-id="b21ad-134">要輸入的方法。</span><span class="sxs-lookup"><span data-stu-id="b21ad-134">The method that is being entered.</span></span>

- <span data-ttu-id="b21ad-135">`paramObject` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="b21ad-135">`paramObject` <xref:System.Object></span></span>

  <span data-ttu-id="b21ad-136">傳遞給方法的參數。</span><span class="sxs-lookup"><span data-stu-id="b21ad-136">The parameters that were passed to the method.</span></span>

## <a name="entertracesource-string-string-string-method"></a><span data-ttu-id="b21ad-137">Enter （TraceSource，string，string，string）方法</span><span class="sxs-lookup"><span data-stu-id="b21ad-137">Enter(TraceSource, string, string, string) method</span></span>

<span data-ttu-id="b21ad-138">將進入方法的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="b21ad-138">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, string obj, string method, string param)
```

### <a name="parameters"></a><span data-ttu-id="b21ad-139">參數</span><span class="sxs-lookup"><span data-stu-id="b21ad-139">Parameters</span></span>

- <span data-ttu-id="b21ad-140">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="b21ad-140">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="b21ad-141">要記錄事件的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="b21ad-141">The trace source to log the event to.</span></span>

- <span data-ttu-id="b21ad-142">`obj` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="b21ad-142">`obj` <xref:System.String></span></span>

  <span data-ttu-id="b21ad-143">呼叫方法的物件。</span><span class="sxs-lookup"><span data-stu-id="b21ad-143">The object that the method was called on.</span></span>

- <span data-ttu-id="b21ad-144">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="b21ad-144">`method` <xref:System.String></span></span>

  <span data-ttu-id="b21ad-145">要輸入的方法。</span><span class="sxs-lookup"><span data-stu-id="b21ad-145">The method that is being entered.</span></span>

- <span data-ttu-id="b21ad-146">`param` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="b21ad-146">`param` <xref:System.String></span></span>

  <span data-ttu-id="b21ad-147">傳遞給方法的參數。</span><span class="sxs-lookup"><span data-stu-id="b21ad-147">The parameters that were passed to the method.</span></span>

## <a name="entertracesource-string-string-object-method"></a><span data-ttu-id="b21ad-148">輸入（TraceSource、string、string、object）方法</span><span class="sxs-lookup"><span data-stu-id="b21ad-148">Enter(TraceSource, string, string, object) method</span></span>

<span data-ttu-id="b21ad-149">將進入方法的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="b21ad-149">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, string obj, string method, object paramObject)
```

### <a name="parameters"></a><span data-ttu-id="b21ad-150">參數</span><span class="sxs-lookup"><span data-stu-id="b21ad-150">Parameters</span></span>

- <span data-ttu-id="b21ad-151">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="b21ad-151">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="b21ad-152">要記錄事件的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="b21ad-152">The trace source to log the event to.</span></span>

- <span data-ttu-id="b21ad-153">`obj` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="b21ad-153">`obj` <xref:System.String></span></span>

  <span data-ttu-id="b21ad-154">呼叫方法的物件。</span><span class="sxs-lookup"><span data-stu-id="b21ad-154">The object that the method was called on.</span></span>

- <span data-ttu-id="b21ad-155">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="b21ad-155">`method` <xref:System.String></span></span>

  <span data-ttu-id="b21ad-156">要輸入的方法。</span><span class="sxs-lookup"><span data-stu-id="b21ad-156">The method that is being entered.</span></span>

- <span data-ttu-id="b21ad-157">`paramObject` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="b21ad-157">`paramObject` <xref:System.Object></span></span>

  <span data-ttu-id="b21ad-158">傳遞給方法的參數。</span><span class="sxs-lookup"><span data-stu-id="b21ad-158">The parameters that were passed to the method.</span></span>

## <a name="entertracesource-string-string-method"></a><span data-ttu-id="b21ad-159">輸入（TraceSource，string，string）方法</span><span class="sxs-lookup"><span data-stu-id="b21ad-159">Enter(TraceSource, string, string) method</span></span>

<span data-ttu-id="b21ad-160">將進入方法的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="b21ad-160">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, string method, string parameters)
```

### <a name="parameters"></a><span data-ttu-id="b21ad-161">參數</span><span class="sxs-lookup"><span data-stu-id="b21ad-161">Parameters</span></span>

- <span data-ttu-id="b21ad-162">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="b21ad-162">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="b21ad-163">要記錄事件的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="b21ad-163">The trace source to log the event to.</span></span>

- <span data-ttu-id="b21ad-164">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="b21ad-164">`method` <xref:System.String></span></span>

  <span data-ttu-id="b21ad-165">要輸入的方法。</span><span class="sxs-lookup"><span data-stu-id="b21ad-165">The method that is being entered.</span></span>

- <span data-ttu-id="b21ad-166">`parameters` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="b21ad-166">`parameters` <xref:System.String></span></span>

  <span data-ttu-id="b21ad-167">傳遞給方法的參數。</span><span class="sxs-lookup"><span data-stu-id="b21ad-167">The parameters that were passed to the method.</span></span>

## <a name="entertracesource-string-method"></a><span data-ttu-id="b21ad-168">輸入（TraceSource，string）方法</span><span class="sxs-lookup"><span data-stu-id="b21ad-168">Enter(TraceSource, string) method</span></span>

<span data-ttu-id="b21ad-169">將進入方法的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="b21ad-169">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, string msg)
```

### <a name="parameters"></a><span data-ttu-id="b21ad-170">參數</span><span class="sxs-lookup"><span data-stu-id="b21ad-170">Parameters</span></span>

- <span data-ttu-id="b21ad-171">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="b21ad-171">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="b21ad-172">要記錄事件的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="b21ad-172">The trace source to log the event to.</span></span>

- <span data-ttu-id="b21ad-173">`msg` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="b21ad-173">`msg` <xref:System.String></span></span>

  <span data-ttu-id="b21ad-174">要記錄至追蹤來源的進入訊息。</span><span class="sxs-lookup"><span data-stu-id="b21ad-174">The entrance message to log to the trace source.</span></span>

## <a name="exception-method"></a><span data-ttu-id="b21ad-175">Exception 方法</span><span class="sxs-lookup"><span data-stu-id="b21ad-175">Exception method</span></span>

<span data-ttu-id="b21ad-176">記錄例外狀況並還原縮排。</span><span class="sxs-lookup"><span data-stu-id="b21ad-176">Logs an exception and restores indentation.</span></span>

```csharp
internal static void Exception(TraceSource traceSource, object obj, string method, Exception e)
```

### <a name="parameters"></a><span data-ttu-id="b21ad-177">參數</span><span class="sxs-lookup"><span data-stu-id="b21ad-177">Parameters</span></span>

- <span data-ttu-id="b21ad-178">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="b21ad-178">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="b21ad-179">要記錄事件的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="b21ad-179">The trace source to log the event to.</span></span>

- <span data-ttu-id="b21ad-180">`obj` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="b21ad-180">`obj` <xref:System.Object></span></span>

  <span data-ttu-id="b21ad-181">在上呼叫擲回例外狀況之方法的物件。</span><span class="sxs-lookup"><span data-stu-id="b21ad-181">The object that the method that threw an exception was called on.</span></span>

- <span data-ttu-id="b21ad-182">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="b21ad-182">`method` <xref:System.String></span></span>

  <span data-ttu-id="b21ad-183">擲回例外狀況的方法。</span><span class="sxs-lookup"><span data-stu-id="b21ad-183">The method that threw the exception.</span></span>

- <span data-ttu-id="b21ad-184">`e` <xref:System.Exception></span><span class="sxs-lookup"><span data-stu-id="b21ad-184">`e` <xref:System.Exception></span></span>

  <span data-ttu-id="b21ad-185">已擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b21ad-185">The exception that was thrown.</span></span>

## <a name="exittracesource-object-string-object-method"></a><span data-ttu-id="b21ad-186">Exit （TraceSource、object、string、object）方法</span><span class="sxs-lookup"><span data-stu-id="b21ad-186">Exit(TraceSource, object, string, object) method</span></span>

<span data-ttu-id="b21ad-187">記錄結束于函式。</span><span class="sxs-lookup"><span data-stu-id="b21ad-187">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, object obj, string method, object retObject)
```

### <a name="parameters"></a><span data-ttu-id="b21ad-188">參數</span><span class="sxs-lookup"><span data-stu-id="b21ad-188">Parameters</span></span>

- <span data-ttu-id="b21ad-189">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="b21ad-189">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="b21ad-190">要記錄事件的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="b21ad-190">The trace source to log the event to.</span></span>

- <span data-ttu-id="b21ad-191">`obj` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="b21ad-191">`obj` <xref:System.Object></span></span>

  <span data-ttu-id="b21ad-192">呼叫方法的物件。</span><span class="sxs-lookup"><span data-stu-id="b21ad-192">The object that the method was called on.</span></span>

- <span data-ttu-id="b21ad-193">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="b21ad-193">`method` <xref:System.String></span></span>

  <span data-ttu-id="b21ad-194">即將結束的方法。</span><span class="sxs-lookup"><span data-stu-id="b21ad-194">The method that is being exited.</span></span>

- <span data-ttu-id="b21ad-195">`retObject` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="b21ad-195">`retObject` <xref:System.Object></span></span>

  <span data-ttu-id="b21ad-196">方法所傳回的值。</span><span class="sxs-lookup"><span data-stu-id="b21ad-196">The value that's being returned by the method.</span></span>

## <a name="exittracesource-string-string-object-method"></a><span data-ttu-id="b21ad-197">Exit （TraceSource，string，string，object）方法</span><span class="sxs-lookup"><span data-stu-id="b21ad-197">Exit(TraceSource, string, string, object) method</span></span>

<span data-ttu-id="b21ad-198">記錄結束于函式。</span><span class="sxs-lookup"><span data-stu-id="b21ad-198">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, string obj, string method, object retObject)
```

### <a name="parameters"></a><span data-ttu-id="b21ad-199">參數</span><span class="sxs-lookup"><span data-stu-id="b21ad-199">Parameters</span></span>

- <span data-ttu-id="b21ad-200">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="b21ad-200">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="b21ad-201">要記錄事件的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="b21ad-201">The trace source to log the event to.</span></span>

- <span data-ttu-id="b21ad-202">`obj` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="b21ad-202">`obj` <xref:System.String></span></span>

  <span data-ttu-id="b21ad-203">呼叫方法的物件。</span><span class="sxs-lookup"><span data-stu-id="b21ad-203">The object that the method was called on.</span></span>

- <span data-ttu-id="b21ad-204">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="b21ad-204">`method` <xref:System.String></span></span>

  <span data-ttu-id="b21ad-205">即將結束的方法。</span><span class="sxs-lookup"><span data-stu-id="b21ad-205">The method that is being exited.</span></span>

- <span data-ttu-id="b21ad-206">`retObject` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="b21ad-206">`retObject` <xref:System.Object></span></span>

  <span data-ttu-id="b21ad-207">方法所傳回的值。</span><span class="sxs-lookup"><span data-stu-id="b21ad-207">The value that's being returned by the method.</span></span>

## <a name="exittracesource-object-string-string-method"></a><span data-ttu-id="b21ad-208">Exit （TraceSource，object，string，string）方法</span><span class="sxs-lookup"><span data-stu-id="b21ad-208">Exit(TraceSource, object, string, string) method</span></span>

<span data-ttu-id="b21ad-209">記錄結束于函式。</span><span class="sxs-lookup"><span data-stu-id="b21ad-209">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, object obj, string method, string retValue)
```

### <a name="parameters"></a><span data-ttu-id="b21ad-210">參數</span><span class="sxs-lookup"><span data-stu-id="b21ad-210">Parameters</span></span>

- <span data-ttu-id="b21ad-211">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="b21ad-211">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="b21ad-212">要記錄事件的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="b21ad-212">The trace source to log the event to.</span></span>

- <span data-ttu-id="b21ad-213">`obj` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="b21ad-213">`obj` <xref:System.Object></span></span>

  <span data-ttu-id="b21ad-214">呼叫方法的物件。</span><span class="sxs-lookup"><span data-stu-id="b21ad-214">The object that the method was called on.</span></span>

- <span data-ttu-id="b21ad-215">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="b21ad-215">`method` <xref:System.String></span></span>

  <span data-ttu-id="b21ad-216">即將結束的方法。</span><span class="sxs-lookup"><span data-stu-id="b21ad-216">The method that is being exited.</span></span>

- <span data-ttu-id="b21ad-217">`retValue` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="b21ad-217">`retValue` <xref:System.String></span></span>

  <span data-ttu-id="b21ad-218">方法所傳回的值。</span><span class="sxs-lookup"><span data-stu-id="b21ad-218">The value that's being returned by the method.</span></span>

## <a name="exittracesource-string-string-string-method"></a><span data-ttu-id="b21ad-219">Exit （TraceSource，string，string，string）方法</span><span class="sxs-lookup"><span data-stu-id="b21ad-219">Exit(TraceSource, string, string, string) method</span></span>

<span data-ttu-id="b21ad-220">記錄結束于函式。</span><span class="sxs-lookup"><span data-stu-id="b21ad-220">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, string obj, string method, string retValue)
```

### <a name="parameters"></a><span data-ttu-id="b21ad-221">參數</span><span class="sxs-lookup"><span data-stu-id="b21ad-221">Parameters</span></span>

- <span data-ttu-id="b21ad-222">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="b21ad-222">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="b21ad-223">要記錄事件的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="b21ad-223">The trace source to log the event to.</span></span>

- <span data-ttu-id="b21ad-224">`obj` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="b21ad-224">`obj` <xref:System.String></span></span>

  <span data-ttu-id="b21ad-225">呼叫方法的物件。</span><span class="sxs-lookup"><span data-stu-id="b21ad-225">The object that the method was called on.</span></span>

- <span data-ttu-id="b21ad-226">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="b21ad-226">`method` <xref:System.String></span></span>

  <span data-ttu-id="b21ad-227">即將結束的方法。</span><span class="sxs-lookup"><span data-stu-id="b21ad-227">The method that is being exited.</span></span>

- <span data-ttu-id="b21ad-228">`retValue` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="b21ad-228">`retValue` <xref:System.String></span></span>

  <span data-ttu-id="b21ad-229">方法所傳回的值。</span><span class="sxs-lookup"><span data-stu-id="b21ad-229">The value that's being returned by the method.</span></span>

## <a name="exittracesource-string-string-method"></a><span data-ttu-id="b21ad-230">Exit （TraceSource，string，string）方法</span><span class="sxs-lookup"><span data-stu-id="b21ad-230">Exit(TraceSource, string, string) method</span></span>

<span data-ttu-id="b21ad-231">記錄結束于函式。</span><span class="sxs-lookup"><span data-stu-id="b21ad-231">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, string method, string parameters)
```

### <a name="parameters"></a><span data-ttu-id="b21ad-232">參數</span><span class="sxs-lookup"><span data-stu-id="b21ad-232">Parameters</span></span>

- <span data-ttu-id="b21ad-233">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="b21ad-233">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="b21ad-234">要記錄事件的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="b21ad-234">The trace source to log the event to.</span></span>

- <span data-ttu-id="b21ad-235">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="b21ad-235">`method` <xref:System.String></span></span>

  <span data-ttu-id="b21ad-236">即將結束的方法。</span><span class="sxs-lookup"><span data-stu-id="b21ad-236">The method that is being exited.</span></span>

- <span data-ttu-id="b21ad-237">`parameters` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="b21ad-237">`parameters` <xref:System.String></span></span>

  <span data-ttu-id="b21ad-238">傳遞至即將結束之方法的參數。</span><span class="sxs-lookup"><span data-stu-id="b21ad-238">The parameters that were passed to the method that's being exited.</span></span>

## <a name="exittracesource-string-method"></a><span data-ttu-id="b21ad-239">Exit （TraceSource，string）方法</span><span class="sxs-lookup"><span data-stu-id="b21ad-239">Exit(TraceSource, string) method</span></span>

<span data-ttu-id="b21ad-240">記錄結束于函式。</span><span class="sxs-lookup"><span data-stu-id="b21ad-240">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, string msg)
```

### <a name="parameters"></a><span data-ttu-id="b21ad-241">參數</span><span class="sxs-lookup"><span data-stu-id="b21ad-241">Parameters</span></span>

- <span data-ttu-id="b21ad-242">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="b21ad-242">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="b21ad-243">要記錄事件的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="b21ad-243">The trace source to log the event to.</span></span>

- <span data-ttu-id="b21ad-244">`msg` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="b21ad-244">`msg` <xref:System.String></span></span>

  <span data-ttu-id="b21ad-245">要記錄到追蹤來源的結束訊息。</span><span class="sxs-lookup"><span data-stu-id="b21ad-245">The exit message to log to the trace source.</span></span>

## <a name="http-property"></a><span data-ttu-id="b21ad-246">Http 屬性</span><span class="sxs-lookup"><span data-stu-id="b21ad-246">Http property</span></span>

<span data-ttu-id="b21ad-247">取得 "System .Net. Http" 的追蹤來源。</span><span class="sxs-lookup"><span data-stu-id="b21ad-247">Gets the trace source for "System.Net.Http".</span></span>

```csharp
internal static TraceSource Http { get; }
```

### <a name="property-value"></a><span data-ttu-id="b21ad-248">屬性值</span><span class="sxs-lookup"><span data-stu-id="b21ad-248">Property value</span></span>

<xref:System.Diagnostics.TraceSource>\
<span data-ttu-id="b21ad-249">"System .Net. Http" 的追蹤來源， `null` 如果未啟用記錄，則為。</span><span class="sxs-lookup"><span data-stu-id="b21ad-249">The trace source for "System.Net.Http", or `null` if logging is not enabled.</span></span>

## <a name="on-property"></a><span data-ttu-id="b21ad-250">On 屬性</span><span class="sxs-lookup"><span data-stu-id="b21ad-250">On property</span></span>

<span data-ttu-id="b21ad-251">取得值，這個值表示是否啟用記錄。</span><span class="sxs-lookup"><span data-stu-id="b21ad-251">Gets a value that indicates whether logging is enabled.</span></span>

```csharp
internal static bool On { get; }
```

### <a name="property-value"></a><span data-ttu-id="b21ad-252">屬性值</span><span class="sxs-lookup"><span data-stu-id="b21ad-252">Property value</span></span>

<xref:System.Boolean>\
<span data-ttu-id="b21ad-253">如果已啟用記錄，則為 `true`，否則為 `false`。</span><span class="sxs-lookup"><span data-stu-id="b21ad-253">`true` if logging is enabled; otherwise, `false`.</span></span>

## <a name="requirements"></a><span data-ttu-id="b21ad-254">需求</span><span class="sxs-lookup"><span data-stu-id="b21ad-254">Requirements</span></span>

<span data-ttu-id="b21ad-255">**命名空間：** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="b21ad-255">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="b21ad-256">**元件：** 系統（在 System.dll 中）</span><span class="sxs-lookup"><span data-stu-id="b21ad-256">**Assembly:** System (in System.dll)</span></span>
