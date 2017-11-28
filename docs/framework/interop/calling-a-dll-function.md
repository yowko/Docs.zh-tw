---
title: "呼叫 DLL 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unmanaged functions, calling
- unmanaged functions
- COM interop, platform invoke
- platform invoke, calling unmanaged functions
- interoperation with unmanaged code, platform invoke
- DLL functions
ms.assetid: 113646de-7ea0-4f0e-8df0-c46dab3e8733
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 36f84796b9682411d7907cfc10d584d772ef00a7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="calling-a-dll-function"></a><span data-ttu-id="b8421-102">呼叫 DLL 函式</span><span class="sxs-lookup"><span data-stu-id="b8421-102">Calling a DLL Function</span></span>
<span data-ttu-id="b8421-103">雖然呼叫 Unmanaged DLL 函式與呼叫其他 Managed 程式碼幾乎完全相同，但具有一開始讓 DLL 函式混淆的差異。</span><span class="sxs-lookup"><span data-stu-id="b8421-103">Although calling unmanaged DLL functions is nearly identical to calling other managed code, there are differences that can make DLL functions seem confusing at first.</span></span> <span data-ttu-id="b8421-104">本節介紹描述一些異常呼叫相關問題的主題。</span><span class="sxs-lookup"><span data-stu-id="b8421-104">This section introduces topics that describe some of the unusual calling-related issues.</span></span>  
  
 <span data-ttu-id="b8421-105">從平台叫用呼叫傳回的結構必須是 Managed 和 Unmanaged 程式碼中的呈現方式相同的資料類型。</span><span class="sxs-lookup"><span data-stu-id="b8421-105">Structures that are returned from platform invoke calls must be data types that have the same representation in managed and unmanaged code.</span></span> <span data-ttu-id="b8421-106">這類類型稱為「Blittable 類型」，因為它們不需要轉換 (請參閱 [Blittable 和非 Blittable 類型](../../../docs/framework/interop/blittable-and-non-blittable-types.md))。</span><span class="sxs-lookup"><span data-stu-id="b8421-106">Such types are called *blittable types* because they do not require conversion (see [Blittable and Non-Blittable Types](../../../docs/framework/interop/blittable-and-non-blittable-types.md)).</span></span> <span data-ttu-id="b8421-107">若要呼叫的函式將非 Blittable 結構當成其傳回類型，您可以定義與非 Blittable 類型大小相同的 Blittable 協助程式類型，並在傳回函式之後轉換資料。</span><span class="sxs-lookup"><span data-stu-id="b8421-107">To call a function that has a non-blittable structure as its return type, you can define a blittable helper type of the same size as the non-blittable type and convert the data after the function returns.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b8421-108">本章節內容</span><span class="sxs-lookup"><span data-stu-id="b8421-108">In This Section</span></span>  
 [<span data-ttu-id="b8421-109">傳遞結構</span><span class="sxs-lookup"><span data-stu-id="b8421-109">Passing Structures</span></span>](../../../docs/framework/interop/passing-structures.md)  
 <span data-ttu-id="b8421-110">識別傳遞具有預先定義配置之資料結構的問題。</span><span class="sxs-lookup"><span data-stu-id="b8421-110">Identifies the issues of passing data structures with a predefined layout.</span></span>  
  
 [<span data-ttu-id="b8421-111">回呼函式</span><span class="sxs-lookup"><span data-stu-id="b8421-111">Callback Functions</span></span>](../../../docs/framework/interop/callback-functions.md)  
 <span data-ttu-id="b8421-112">提供回呼函式的基本資訊。</span><span class="sxs-lookup"><span data-stu-id="b8421-112">Provides basic information about callback functions.</span></span>  
  
 [<span data-ttu-id="b8421-113">如何：實作回呼函式</span><span class="sxs-lookup"><span data-stu-id="b8421-113">How to: Implement Callback Functions</span></span>](../../../docs/framework/interop/how-to-implement-callback-functions.md)  
 <span data-ttu-id="b8421-114">描述如何在 Managed 程式碼中實作回呼函式。</span><span class="sxs-lookup"><span data-stu-id="b8421-114">Describes how to implement callback functions in managed code.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b8421-115">相關章節</span><span class="sxs-lookup"><span data-stu-id="b8421-115">Related Sections</span></span>  
 [<span data-ttu-id="b8421-116">使用 Unmanaged DLL 函式</span><span class="sxs-lookup"><span data-stu-id="b8421-116">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 <span data-ttu-id="b8421-117">描述如何使用平台叫用呼叫 Unmanaged DLL 函式。</span><span class="sxs-lookup"><span data-stu-id="b8421-117">Describes how to call unmanaged DLL functions using platform invoke.</span></span>  
  
 [<span data-ttu-id="b8421-118">使用平台叫用封送處理資料</span><span class="sxs-lookup"><span data-stu-id="b8421-118">Marshaling Data with Platform Invoke</span></span>](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md)  
 <span data-ttu-id="b8421-119">描述如何宣告方法參數，以及將引數傳遞給 Unmanaged 程式庫所匯出的函式。</span><span class="sxs-lookup"><span data-stu-id="b8421-119">Describes how to declare method parameters and pass arguments to functions exported by unmanaged libraries.</span></span>
