---
title: 偵錯全域靜態函式
ms.date: 03/30/2017
helpviewer_keywords:
- global static functions [.NET Framework debugging]
- debugging global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], debugging
ms.assetid: efc64414-77c3-48d0-881a-8594ed416aad
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e2403d736d031aab52525fc12b5071e764a8bde1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406447"
---
# <a name="debugging-global-static-functions"></a><span data-ttu-id="d3504-102">偵錯全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="d3504-102">Debugging Global Static Functions</span></span>
<span data-ttu-id="d3504-103">本節說明偵錯 API 所使用的 Unmanaged 全域靜態函式。</span><span class="sxs-lookup"><span data-stu-id="d3504-103">This section describes the unmanaged global static functions that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d3504-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="d3504-104">In This Section</span></span>  
 [<span data-ttu-id="d3504-105">_EFN_GetManagedExcepStack 函式</span><span class="sxs-lookup"><span data-stu-id="d3504-105">_EFN_GetManagedExcepStack Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedexcepstack-function.md)  
 <span data-ttu-id="d3504-106">給予 Managed 例外狀況物件位址後，會傳回內部包含堆疊追蹤版本的字串。</span><span class="sxs-lookup"><span data-stu-id="d3504-106">Given a managed exception object address, returns a string version of the stack trace contained inside.</span></span>  
  
 [<span data-ttu-id="d3504-107">_EFN_GetManagedObjectFieldInfo 函式</span><span class="sxs-lookup"><span data-stu-id="d3504-107">_EFN_GetManagedObjectFieldInfo Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedobjectfieldinfo-function.md)  
 <span data-ttu-id="d3504-108">使用所提供的物件指標和欄位名稱來取得從物件開始到欄位的位移以及欄位的值。</span><span class="sxs-lookup"><span data-stu-id="d3504-108">Gets the offset from the start of an object to a field and the field's value, using the provided object pointer and field name.</span></span>  
  
 [<span data-ttu-id="d3504-109">_EFN_GetManagedObjectName 函式</span><span class="sxs-lookup"><span data-stu-id="d3504-109">_EFN_GetManagedObjectName Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedobjectname-function.md)  
 <span data-ttu-id="d3504-110">使用提供的 Managed 物件指標，以取得類型的名稱。</span><span class="sxs-lookup"><span data-stu-id="d3504-110">Gets the name of a type by using the provided managed object pointer.</span></span>  
  
 [<span data-ttu-id="d3504-111">_EFN_StackTrace 函式</span><span class="sxs-lookup"><span data-stu-id="d3504-111">_EFN_StackTrace Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/efn-stacktrace-function.md)  
 <span data-ttu-id="d3504-112">提供 Managed 堆疊追蹤以及 `CONTEXT` 記錄之陣列的文字表示，再各提供一個文字表示給 Unmanaged 和 Managed 程式碼之間的每個轉換。</span><span class="sxs-lookup"><span data-stu-id="d3504-112">Provides a text representation of a managed stack trace and an array of `CONTEXT` records, one for each transition between unmanaged and managed code.</span></span>  
  
 [<span data-ttu-id="d3504-113">CLRDataCreateInstance 函式</span><span class="sxs-lookup"><span data-stu-id="d3504-113">CLRDataCreateInstance Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatacreateinstance-function.md)  
 <span data-ttu-id="d3504-114">由通用語言執行階段 (CLR) 資料存取服務呼叫，以建立指定的介面物件給指定的目標處理序。</span><span class="sxs-lookup"><span data-stu-id="d3504-114">Called by the common language runtime (CLR) data access services to create the specified interface object for the specified target process.</span></span>  
  
 [<span data-ttu-id="d3504-115">PFN_CLRDataCreateInstance 函式指標</span><span class="sxs-lookup"><span data-stu-id="d3504-115">PFN_CLRDataCreateInstance Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/debugging/pfn-clrdatacreateinstance-function-pointer.md)  
 <span data-ttu-id="d3504-116">指向由 CLR 資料存取服務所呼叫的函式，以建立指定的介面物件給指定的目標處理序。</span><span class="sxs-lookup"><span data-stu-id="d3504-116">Points to a function that is called by the CLR data access services to create the specified interface object for the specified target process.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d3504-117">相關章節</span><span class="sxs-lookup"><span data-stu-id="d3504-117">Related Sections</span></span>  
 [<span data-ttu-id="d3504-118">偵錯 Coclass</span><span class="sxs-lookup"><span data-stu-id="d3504-118">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [<span data-ttu-id="d3504-119">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="d3504-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [<span data-ttu-id="d3504-120">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="d3504-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [<span data-ttu-id="d3504-121">偵錯結構</span><span class="sxs-lookup"><span data-stu-id="d3504-121">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
