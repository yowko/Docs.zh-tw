---
title: "做為回呼方法，委派封送處理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data marshaling, Callback sample
- marshaling, Callback sample
ms.assetid: 6ddd7866-9804-4571-84de-83f5cc017a5a
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c8c4eca35c406b38da603dc10358920ee887b137
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="marshaling-a-delegate-as-a-callback-method"></a><span data-ttu-id="3f5f2-102">做為回呼方法，委派封送處理</span><span class="sxs-lookup"><span data-stu-id="3f5f2-102">Marshaling a Delegate as a Callback Method</span></span>
<span data-ttu-id="3f5f2-103">此範例示範如何將委派傳遞至需要函式指標的 Unmanaged 函式。</span><span class="sxs-lookup"><span data-stu-id="3f5f2-103">This sample demonstrates how to pass delegates to an unmanaged function expecting function pointers.</span></span> <span data-ttu-id="3f5f2-104">委派是可保留方法參考的類別，並且相當於型別安全函式指標或回呼函式。</span><span class="sxs-lookup"><span data-stu-id="3f5f2-104">A delegate is a class that can hold a reference to a method and is equivalent to a type-safe function pointer or a callback function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3f5f2-105">當您在呼叫內使用委派時，Common Language Runtime 會在該呼叫的期間防止對委派進行記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="3f5f2-105">When you use a delegate inside a call, the common language runtime protects the delegate from being garbage collected for the duration of that call.</span></span> <span data-ttu-id="3f5f2-106">不過，如果 Unmanaged 函式儲存要在呼叫完成之後使用的委派，您必須手動防止記憶體回收，直到 Unmanaged 函式與委派一起完成之前。</span><span class="sxs-lookup"><span data-stu-id="3f5f2-106">However, if the unmanaged function stores the delegate to use after the call completes, you must manually prevent garbage collection until the unmanaged function finishes with the delegate.</span></span> <span data-ttu-id="3f5f2-107">如需詳細資訊，請參閱 [HandleRef 範例](http://msdn.microsoft.com/en-us/ab23b04e-1d53-4ec7-b27a-e892d9298959)和 [GCHandle 範例](http://msdn.microsoft.com/en-us/6acce798-0385-4ded-a790-77da842c113f)。</span><span class="sxs-lookup"><span data-stu-id="3f5f2-107">For more information, see the [HandleRef Sample](http://msdn.microsoft.com/en-us/ab23b04e-1d53-4ec7-b27a-e892d9298959) and [GCHandle Sample](http://msdn.microsoft.com/en-us/6acce798-0385-4ded-a790-77da842c113f).</span></span>  
  
 <span data-ttu-id="3f5f2-108">Callback 範例會使用下列 Unmanaged 函式和其原始函式宣告，如下所示：</span><span class="sxs-lookup"><span data-stu-id="3f5f2-108">The Callback sample uses the following unmanaged functions, shown with their original function declaration:</span></span>  
  
-   <span data-ttu-id="3f5f2-109">從 PinvokeLib.dll 匯出的 **TestCallBack**。</span><span class="sxs-lookup"><span data-stu-id="3f5f2-109">**TestCallBack** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    void TestCallBack(FPTR pf, int value);  
    ```  
  
-   <span data-ttu-id="3f5f2-110">從 PinvokeLib.dll 匯出的 **TestCallBack2**。</span><span class="sxs-lookup"><span data-stu-id="3f5f2-110">**TestCallBack2** exported from PinvokeLib.dll.</span></span>  
  
    ```  
    void TestCallBack2(FPTR2 pf2, char* value);  
    ```  
  
 <span data-ttu-id="3f5f2-111">[PinvokeLib.dll](http://msdn.microsoft.com/en-us/5d1438d7-9946-489d-8ede-6c694a08f614) 是自訂的 Unmanaged 程式庫，其中包含先前所列出函式的實作。</span><span class="sxs-lookup"><span data-stu-id="3f5f2-111">[PinvokeLib.dll](http://msdn.microsoft.com/en-us/5d1438d7-9946-489d-8ede-6c694a08f614) is a custom unmanaged library that contains an implementation for the previously listed functions.</span></span>  
  
 <span data-ttu-id="3f5f2-112">在此範例中，`LibWrap` 類別包含 `TestCallBack` 和 `TestCallBack2` 方法的 Managed 原型。</span><span class="sxs-lookup"><span data-stu-id="3f5f2-112">In this sample, the `LibWrap` class contains managed prototypes for the `TestCallBack` and `TestCallBack2` methods.</span></span> <span data-ttu-id="3f5f2-113">這兩種方法都會將委派當成參數傳遞給回呼函式。</span><span class="sxs-lookup"><span data-stu-id="3f5f2-113">Both methods pass a delegate to a callback function as a parameter.</span></span> <span data-ttu-id="3f5f2-114">委派的簽章必須符合它所參考之方法的簽章。</span><span class="sxs-lookup"><span data-stu-id="3f5f2-114">The signature of the delegate must match the signature of the method it references.</span></span> <span data-ttu-id="3f5f2-115">例如，`FPtr` 和 `FPtr2` 委派的簽章與 `DoSomething` 和 `DoSomething2` 方法相同。</span><span class="sxs-lookup"><span data-stu-id="3f5f2-115">For example, the `FPtr` and `FPtr2` delegates have signatures that are identical to the `DoSomething` and `DoSomething2` methods.</span></span>  
  
## <a name="declaring-prototypes"></a><span data-ttu-id="3f5f2-116">宣告原型</span><span class="sxs-lookup"><span data-stu-id="3f5f2-116">Declaring Prototypes</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#37)]
 [!code-csharp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#37)]
 [!code-vb[Conceptual.Interop.Marshaling#37](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#37)]  
  
## <a name="calling-functions"></a><span data-ttu-id="3f5f2-117">呼叫函式</span><span class="sxs-lookup"><span data-stu-id="3f5f2-117">Calling Functions</span></span>  
 [!code-cpp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#38)]
 [!code-csharp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#38)]
 [!code-vb[Conceptual.Interop.Marshaling#38](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#38)]  
  
## <a name="see-also"></a><span data-ttu-id="3f5f2-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f5f2-118">See Also</span></span>  
 [<span data-ttu-id="3f5f2-119">其他封送處理範例</span><span class="sxs-lookup"><span data-stu-id="3f5f2-119">Miscellaneous Marshaling Samples</span></span>](http://msdn.microsoft.com/en-us/a915c948-54e9-4d0f-a525-95a77fd8ed70)  
 [<span data-ttu-id="3f5f2-120">平台叫用資料類型</span><span class="sxs-lookup"><span data-stu-id="3f5f2-120">Platform Invoke Data Types</span></span>](http://msdn.microsoft.com/en-us/16014d9f-d6bd-481e-83f0-df11377c550f)  
 [<span data-ttu-id="3f5f2-121">在 Managed 程式碼中建立原型</span><span class="sxs-lookup"><span data-stu-id="3f5f2-121">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
