---
title: "COM 包裝函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- wrapper classes
- COM interop, COM wrappers
- COM wrappers
- COM, wrappers
- interoperation with unmanaged code, COM wrappers
- COM callable wrappers
ms.assetid: e56c485b-6b67-4345-8e66-fd21835a6092
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 733d7f3e56b8ed704003ca9d6c2aa858c713df93
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="com-wrappers"></a><span data-ttu-id="559b0-102">COM 包裝函式</span><span class="sxs-lookup"><span data-stu-id="559b0-102">COM Wrappers</span></span>
<span data-ttu-id="559b0-103">COM 與 .NET Framework 物件模型在數個重要方面不同：</span><span class="sxs-lookup"><span data-stu-id="559b0-103">COM differs from the .NET Framework object model in several important ways:</span></span>  
  
-   <span data-ttu-id="559b0-104">COM 物件用戶端必須管理這些物件的存留期；Common Language Runtime 會管理其環境中物件的存留期。</span><span class="sxs-lookup"><span data-stu-id="559b0-104">Clients of COM objects must manage the lifetime of those objects; the common language runtime manages the lifetime of objects in its environment.</span></span>  
  
-   <span data-ttu-id="559b0-105">COM 物件用戶端會透過要求提供該服務的介面並取回介面指標來探索服務是否可用。</span><span class="sxs-lookup"><span data-stu-id="559b0-105">Clients of COM objects discover whether a service is available by requesting an interface that provides that service and getting back an interface pointer, or not.</span></span> <span data-ttu-id="559b0-106">.NET 物件的用戶端可以取得使用反映之物件功能的描述。</span><span class="sxs-lookup"><span data-stu-id="559b0-106">Clients of .NET objects can obtain a description of an object's functionality using reflection.</span></span>  
  
-   <span data-ttu-id="559b0-107">NET 物件位在 .NET Framework 執行環境所管理的記憶體中。</span><span class="sxs-lookup"><span data-stu-id="559b0-107">NET objects reside in memory managed by the .NET Framework execution environment.</span></span> <span data-ttu-id="559b0-108">基於效能原因，執行環境可以在記憶體中移動物件，並更新所移動物件的所有參考。</span><span class="sxs-lookup"><span data-stu-id="559b0-108">The execution environment can move objects around in memory for performance reasons and update all references to the objects it moves.</span></span> <span data-ttu-id="559b0-109">已取得物件指標的 Unmanaged 用戶端依賴此物件來維持在相同的位置。</span><span class="sxs-lookup"><span data-stu-id="559b0-109">Unmanaged clients, having obtained a pointer to an object, rely on the object to remain at the same location.</span></span> <span data-ttu-id="559b0-110">這些用戶端沒有機制可以處理其位置不固定的物件。</span><span class="sxs-lookup"><span data-stu-id="559b0-110">These clients have no mechanism for dealing with an object whose location is not fixed.</span></span>  
  
 <span data-ttu-id="559b0-111">為了克服這些差異，執行階段提供包裝函式類別，讓 Managed 和 Unmanaged 用戶端認為它們在其各自環境內呼叫物件。</span><span class="sxs-lookup"><span data-stu-id="559b0-111">To overcome these differences, the runtime provides wrapper classes to make both managed and unmanaged clients think they are calling objects within their respective environment.</span></span> <span data-ttu-id="559b0-112">只要 Managed 用戶端對 COM 物件呼叫方法，執行階段就會建立[執行階段可呼叫包裝函式](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW)。</span><span class="sxs-lookup"><span data-stu-id="559b0-112">Whenever your managed client calls a method on a COM object, the runtime creates a [runtime callable wrapper](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW).</span></span> <span data-ttu-id="559b0-113">此外，RCW 會擷取 Managed 與 Unmanaged 參考機制之間的差異。</span><span class="sxs-lookup"><span data-stu-id="559b0-113">RCWs abstract the differences between managed and unmanaged reference mechanisms, among other things.</span></span> <span data-ttu-id="559b0-114">執行階段也會建立 [COM 可呼叫包裝函式](../../../docs/framework/interop/com-callable-wrapper.md) (CCW) 來反轉程序，讓 COM 用戶端在 .NET 物件上順暢地呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="559b0-114">The runtime also creates a [COM callable wrapper](../../../docs/framework/interop/com-callable-wrapper.md) (CCW) to reverse the process, enabling a COM client to seamlessly call a method on a .NET object.</span></span> <span data-ttu-id="559b0-115">如下圖所示，呼叫端程式碼的角度可決定執行階段所建立的包裝函式類別。</span><span class="sxs-lookup"><span data-stu-id="559b0-115">As the following illustration shows, the perspective of the calling code determines which wrapper class the runtime creates.</span></span>  
  
 <span data-ttu-id="559b0-116">![COM 包裝函式概觀](../../../docs/framework/interop/media/bidirectional.gif "bidirectional")</span><span class="sxs-lookup"><span data-stu-id="559b0-116">![COM wrapper overview](../../../docs/framework/interop/media/bidirectional.gif "bidirectional")</span></span>  
<span data-ttu-id="559b0-117">COM 包裝函式概觀</span><span class="sxs-lookup"><span data-stu-id="559b0-117">COM wrapper overview</span></span>  
  
 <span data-ttu-id="559b0-118">在大部分情況下，執行階段所產生的標準 RCW 或 CCW 提供呼叫的足夠封送處理，而這些呼叫跨越 COM 與 .NET Framework 之間的界限。</span><span class="sxs-lookup"><span data-stu-id="559b0-118">In most cases, the standard RCW or CCW generated by the runtime provides adequate marshaling for calls that cross the boundary between COM and the .NET Framework.</span></span> <span data-ttu-id="559b0-119">使用自訂屬性，您可以選擇性地調整執行階段呈現 Managed 和 Unmanaged 程式碼的方式。</span><span class="sxs-lookup"><span data-stu-id="559b0-119">Using custom attributes, you can optionally adjust the way the runtime represents managed and unmanaged code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="559b0-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="559b0-120">See Also</span></span>  
 [<span data-ttu-id="559b0-121">進階 COM 互通性</span><span class="sxs-lookup"><span data-stu-id="559b0-121">Advanced COM Interoperability</span></span>](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 [<span data-ttu-id="559b0-122">執行階段可呼叫包裝函式</span><span class="sxs-lookup"><span data-stu-id="559b0-122">Runtime Callable Wrapper</span></span>](../../../docs/framework/interop/runtime-callable-wrapper.md)  
 [<span data-ttu-id="559b0-123">COM 可呼叫包裝函式</span><span class="sxs-lookup"><span data-stu-id="559b0-123">COM Callable Wrapper</span></span>](../../../docs/framework/interop/com-callable-wrapper.md)  
 [<span data-ttu-id="559b0-124">自訂標準包裝函式</span><span class="sxs-lookup"><span data-stu-id="559b0-124">Customizing Standard Wrappers</span></span>](http://msdn.microsoft.com/en-us/c40d089b-6a3c-41b5-a20d-d760c215e49d)  
 [<span data-ttu-id="559b0-125">如何：自訂執行階段可呼叫包裝函式</span><span class="sxs-lookup"><span data-stu-id="559b0-125">How to: Customize Runtime Callable Wrappers</span></span>](http://msdn.microsoft.com/en-us/4a4bb3da-4d60-4517-99f2-78d46a681732)
