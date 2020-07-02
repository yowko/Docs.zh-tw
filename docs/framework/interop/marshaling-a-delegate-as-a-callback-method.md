---
title: 做為回呼方法，委派封送處理
description: 瞭解如何將委派封送處理為回呼方法。 請參閱如何將委派傳遞至預期函式指標的非受控函式的範例。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data marshaling, Callback sample
- marshaling, Callback sample
ms.assetid: 6ddd7866-9804-4571-84de-83f5cc017a5a
ms.openlocfilehash: bf9ef3b9d48c0869dcc96820c3a2fb6fb608479e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618944"
---
# <a name="marshaling-a-delegate-as-a-callback-method"></a><span data-ttu-id="a1f54-104">做為回呼方法，委派封送處理</span><span class="sxs-lookup"><span data-stu-id="a1f54-104">Marshaling a Delegate as a Callback Method</span></span>
<span data-ttu-id="a1f54-105">此範例示範如何將委派傳遞至需要函式指標的 Unmanaged 函式。</span><span class="sxs-lookup"><span data-stu-id="a1f54-105">This sample demonstrates how to pass delegates to an unmanaged function expecting function pointers.</span></span> <span data-ttu-id="a1f54-106">委派是可保留方法參考的類別，並且相當於型別安全函式指標或回呼函式。</span><span class="sxs-lookup"><span data-stu-id="a1f54-106">A delegate is a class that can hold a reference to a method and is equivalent to a type-safe function pointer or a callback function.</span></span>

> [!NOTE]
> <span data-ttu-id="a1f54-107">當您在呼叫內使用委派時，Common Language Runtime 會在該呼叫的期間防止對委派進行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="a1f54-107">When you use a delegate inside a call, the common language runtime protects the delegate from being garbage collected for the duration of that call.</span></span> <span data-ttu-id="a1f54-108">不過，如果 Unmanaged 函式儲存要在呼叫完成之後使用的委派，您必須手動防止記憶體回收，直到 Unmanaged 函式與委派一起完成之前。</span><span class="sxs-lookup"><span data-stu-id="a1f54-108">However, if the unmanaged function stores the delegate to use after the call completes, you must manually prevent garbage collection until the unmanaged function finishes with the delegate.</span></span> <span data-ttu-id="a1f54-109">如需詳細資訊，請參閱 [HandleRef 範例](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hc662t8k(v=vs.100))和 [GCHandle 範例](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/44ey4b32(v=vs.100))。</span><span class="sxs-lookup"><span data-stu-id="a1f54-109">For more information, see the [HandleRef Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hc662t8k(v=vs.100)) and [GCHandle Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/44ey4b32(v=vs.100)).</span></span>

<span data-ttu-id="a1f54-110">Callback 範例會使用下列 Unmanaged 函式和其原始函式宣告，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a1f54-110">The Callback sample uses the following unmanaged functions, shown with their original function declaration:</span></span>

- <span data-ttu-id="a1f54-111">從 PinvokeLib.dll 匯出的 `TestCallBack`。</span><span class="sxs-lookup"><span data-stu-id="a1f54-111">`TestCallBack` exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestCallBack(FPTR pf, int value);
    ```

- <span data-ttu-id="a1f54-112">從 PinvokeLib.dll 匯出的 `TestCallBack2`。</span><span class="sxs-lookup"><span data-stu-id="a1f54-112">`TestCallBack2` exported from PinvokeLib.dll.</span></span>

    ```cpp
    void TestCallBack2(FPTR2 pf2, char* value);
    ```

<span data-ttu-id="a1f54-113">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) 是自訂的 Unmanaged 程式庫，其中包含先前所列出函式的實作。</span><span class="sxs-lookup"><span data-stu-id="a1f54-113">[PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) is a custom unmanaged library that contains an implementation for the previously listed functions.</span></span>

<span data-ttu-id="a1f54-114">在此範例中，`NativeMethods` 類別包含 `TestCallBack` 和 `TestCallBack2` 方法的 Managed 原型。</span><span class="sxs-lookup"><span data-stu-id="a1f54-114">In this sample, the `NativeMethods` class contains managed prototypes for the `TestCallBack` and `TestCallBack2` methods.</span></span> <span data-ttu-id="a1f54-115">這兩種方法都會將委派當成參數傳遞給回呼函式。</span><span class="sxs-lookup"><span data-stu-id="a1f54-115">Both methods pass a delegate to a callback function as a parameter.</span></span> <span data-ttu-id="a1f54-116">委派的簽章必須符合它所參考之方法的簽章。</span><span class="sxs-lookup"><span data-stu-id="a1f54-116">The signature of the delegate must match the signature of the method it references.</span></span> <span data-ttu-id="a1f54-117">例如，`FPtr` 和 `FPtr2` 委派的簽章與 `DoSomething` 和 `DoSomething2` 方法相同。</span><span class="sxs-lookup"><span data-stu-id="a1f54-117">For example, the `FPtr` and `FPtr2` delegates have signatures that are identical to the `DoSomething` and `DoSomething2` methods.</span></span>

## <a name="declaring-prototypes"></a><span data-ttu-id="a1f54-118">宣告原型</span><span class="sxs-lookup"><span data-stu-id="a1f54-118">Declaring Prototypes</span></span>
[!code-cpp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#37)]
[!code-csharp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#37)]
[!code-vb[Conceptual.Interop.Marshaling#37](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#37)]

## <a name="calling-functions"></a><span data-ttu-id="a1f54-119">呼叫函式</span><span class="sxs-lookup"><span data-stu-id="a1f54-119">Calling Functions</span></span>
[!code-cpp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#38)]
[!code-csharp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#38)]
[!code-vb[Conceptual.Interop.Marshaling#38](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#38)]

## <a name="see-also"></a><span data-ttu-id="a1f54-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1f54-120">See also</span></span>

- <span data-ttu-id="a1f54-121">[其他封送處理範例](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ss9sb93t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a1f54-121">[Miscellaneous Marshaling Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ss9sb93t(v=vs.100))</span></span>
- [<span data-ttu-id="a1f54-122">平台叫用資料類型</span><span class="sxs-lookup"><span data-stu-id="a1f54-122">Platform Invoke Data Types</span></span>](marshaling-data-with-platform-invoke.md#platform-invoke-data-types)
- [<span data-ttu-id="a1f54-123">在 Managed 程式碼中建立原型</span><span class="sxs-lookup"><span data-stu-id="a1f54-123">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
