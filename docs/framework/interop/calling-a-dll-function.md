---
title: 呼叫 DLL 函式
description: 請參閱呼叫 DLL 函式的問題，這些問題可能看似令人困惑。 呼叫進程的函式會根據傳回型別是否為可複製的，而有所不同。
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged functions, calling
- unmanaged functions
- COM interop, platform invoke
- platform invoke, calling unmanaged functions
- interoperation with unmanaged code, platform invoke
- DLL functions
ms.assetid: 113646de-7ea0-4f0e-8df0-c46dab3e8733
ms.openlocfilehash: 09dd9d30c29660231feee6c624a025ade1fda1d3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96282947"
---
# <a name="calling-a-dll-function"></a><span data-ttu-id="7a58f-104">呼叫 DLL 函式</span><span class="sxs-lookup"><span data-stu-id="7a58f-104">Calling a DLL Function</span></span>

<span data-ttu-id="7a58f-105">雖然呼叫 Unmanaged DLL 函式與呼叫其他 Managed 程式碼幾乎完全相同，但具有一開始讓 DLL 函式混淆的差異。</span><span class="sxs-lookup"><span data-stu-id="7a58f-105">Although calling unmanaged DLL functions is nearly identical to calling other managed code, there are differences that can make DLL functions seem confusing at first.</span></span> <span data-ttu-id="7a58f-106">本節介紹描述一些異常呼叫相關問題的主題。</span><span class="sxs-lookup"><span data-stu-id="7a58f-106">This section introduces topics that describe some of the unusual calling-related issues.</span></span>  
  
 <span data-ttu-id="7a58f-107">從平台叫用呼叫傳回的結構必須是 Managed 和 Unmanaged 程式碼中的呈現方式相同的資料類型。</span><span class="sxs-lookup"><span data-stu-id="7a58f-107">Structures that are returned from platform invoke calls must be data types that have the same representation in managed and unmanaged code.</span></span> <span data-ttu-id="7a58f-108">這類類型稱為「Blittable 類型」，因為它們不需要轉換 (請參閱 [Blittable 和非 Blittable 類型](blittable-and-non-blittable-types.md))。</span><span class="sxs-lookup"><span data-stu-id="7a58f-108">Such types are called *blittable types* because they do not require conversion (see [Blittable and Non-Blittable Types](blittable-and-non-blittable-types.md)).</span></span> <span data-ttu-id="7a58f-109">若要呼叫的函式將非 Blittable 結構當成其傳回類型，您可以定義與非 Blittable 類型大小相同的 Blittable 協助程式類型，並在傳回函式之後轉換資料。</span><span class="sxs-lookup"><span data-stu-id="7a58f-109">To call a function that has a non-blittable structure as its return type, you can define a blittable helper type of the same size as the non-blittable type and convert the data after the function returns.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7a58f-110">本節內容</span><span class="sxs-lookup"><span data-stu-id="7a58f-110">In This Section</span></span>  

 [<span data-ttu-id="7a58f-111">傳遞結構</span><span class="sxs-lookup"><span data-stu-id="7a58f-111">Passing Structures</span></span>](passing-structures.md)  
 <span data-ttu-id="7a58f-112">識別傳遞具有預先定義配置之資料結構的問題。</span><span class="sxs-lookup"><span data-stu-id="7a58f-112">Identifies the issues of passing data structures with a predefined layout.</span></span>  
  
 [<span data-ttu-id="7a58f-113">回呼函式</span><span class="sxs-lookup"><span data-stu-id="7a58f-113">Callback Functions</span></span>](callback-functions.md)  
 <span data-ttu-id="7a58f-114">提供回呼函式的基本資訊。</span><span class="sxs-lookup"><span data-stu-id="7a58f-114">Provides basic information about callback functions.</span></span>  
  
 [<span data-ttu-id="7a58f-115">作法：實作回呼函式</span><span class="sxs-lookup"><span data-stu-id="7a58f-115">How to: Implement Callback Functions</span></span>](how-to-implement-callback-functions.md)  
 <span data-ttu-id="7a58f-116">描述如何在 Managed 程式碼中實作回呼函式。</span><span class="sxs-lookup"><span data-stu-id="7a58f-116">Describes how to implement callback functions in managed code.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7a58f-117">相關章節</span><span class="sxs-lookup"><span data-stu-id="7a58f-117">Related Sections</span></span>  

 [<span data-ttu-id="7a58f-118">使用 Unmanaged DLL 函式</span><span class="sxs-lookup"><span data-stu-id="7a58f-118">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)  
 <span data-ttu-id="7a58f-119">描述如何使用平台叫用呼叫 Unmanaged DLL 函式。</span><span class="sxs-lookup"><span data-stu-id="7a58f-119">Describes how to call unmanaged DLL functions using platform invoke.</span></span>  
  
 [<span data-ttu-id="7a58f-120">使用平台叫用封送處理資料</span><span class="sxs-lookup"><span data-stu-id="7a58f-120">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)  
 <span data-ttu-id="7a58f-121">描述如何宣告方法參數，以及將引數傳遞給 Unmanaged 程式庫所匯出的函式。</span><span class="sxs-lookup"><span data-stu-id="7a58f-121">Describes how to declare method parameters and pass arguments to functions exported by unmanaged libraries.</span></span>
