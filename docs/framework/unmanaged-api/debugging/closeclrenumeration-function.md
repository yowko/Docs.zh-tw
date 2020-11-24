---
title: CloseCLREnumeration 函式
ms.date: 03/30/2017
api_name:
- CloseCLREnumeration
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- CloseCLREnumeration
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- CloseCLR Enumeration function
ms.assetid: 5e3c3958-80bb-43b1-a96b-dd3e6dbd9cd7
topic_type:
- apiref
ms.openlocfilehash: 575e194cf952f02a3fe4fce9e955e45e1bc3653d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673909"
---
# <a name="closeclrenumeration-function"></a><span data-ttu-id="ad483-102">CloseCLREnumeration 函式</span><span class="sxs-lookup"><span data-stu-id="ad483-102">CloseCLREnumeration Function</span></span>

<span data-ttu-id="ad483-103">關閉任何有效的 common language runtime (CLR) 繼續 [EnumerateCLRs](enumerateclrs-function.md)函式所傳回之控制碼陣列中的啟動事件，並釋放控制碼和字串路徑陣列的記憶體。</span><span class="sxs-lookup"><span data-stu-id="ad483-103">Closes any valid common language runtime (CLR) continue-startup events located in an array of handles returned by the [EnumerateCLRs function](enumerateclrs-function.md), and frees the memory for the handle and string path arrays.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad483-104">語法</span><span class="sxs-lookup"><span data-stu-id="ad483-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseCLREnumeration (  
    [in]  DWORD      pHandleArray,  
    [in]  LPWSTR**   pStringArray,  
    [in]  DWORD*     dwArrayLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad483-105">參數</span><span class="sxs-lookup"><span data-stu-id="ad483-105">Parameters</span></span>  

 `pHandleArray`  
 <span data-ttu-id="ad483-106">在從 [EnumerateCLRs](enumerateclrs-function.md)函式傳回之事件控制碼陣列的指標。</span><span class="sxs-lookup"><span data-stu-id="ad483-106">[in] Pointer to the array of event handles returned from the [EnumerateCLRs function](enumerateclrs-function.md).</span></span>  
  
 `pStringArray`  
 <span data-ttu-id="ad483-107">在從 [EnumerateCLRs](enumerateclrs-function.md)函式傳回之 CLR 字串路徑陣列的指標。</span><span class="sxs-lookup"><span data-stu-id="ad483-107">[in] Pointer to the array of CLR string paths returned from the [EnumerateCLRs function](enumerateclrs-function.md).</span></span>  
  
 `dwArrayLength`  
 <span data-ttu-id="ad483-108">[in] 包含 `pHandleArray` 或 `pStringArray` 之大小 (長度) (兩者相同) 的 DWORD。</span><span class="sxs-lookup"><span data-stu-id="ad483-108">[in] DWORD that contains the size (length) of either `pHandleArray` or `pStringArray` (they are the same).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ad483-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="ad483-109">Return Value</span></span>  

 <span data-ttu-id="ad483-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="ad483-110">S_OK</span></span>  
 <span data-ttu-id="ad483-111">[EnumerateCLRs](enumerateclrs-function.md)函式所開啟的控制碼已關閉，而配置給控制碼和字串陣列的記憶體則會釋放。</span><span class="sxs-lookup"><span data-stu-id="ad483-111">Handles opened by the [EnumerateCLRs function](enumerateclrs-function.md) are closed, and memory allocated for the handle and string arrays is freed.</span></span>  
  
 <span data-ttu-id="ad483-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="ad483-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="ad483-113">`pHandleArray` 的長度不符合以 `dwArrayLength` 傳遞的長度。</span><span class="sxs-lookup"><span data-stu-id="ad483-113">The length of `pHandleArray` does not match the length that is passed in `dwArrayLength`.</span></span>  
  
 <span data-ttu-id="ad483-114">E_FAIL (或其他 E_ 傳回碼)</span><span class="sxs-lookup"><span data-stu-id="ad483-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="ad483-115">這個函式無法釋放用於 `pHandleArray` 和 `pStringArray` 的記憶體。</span><span class="sxs-lookup"><span data-stu-id="ad483-115">The function is unable to free the memory for `pHandleArray` and `pStringArray`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad483-116">需求</span><span class="sxs-lookup"><span data-stu-id="ad483-116">Requirements</span></span>  

 <span data-ttu-id="ad483-117">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ad483-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad483-118">**標頭：** dbgshim。h</span><span class="sxs-lookup"><span data-stu-id="ad483-118">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="ad483-119">連結 **庫：** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="ad483-119">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="ad483-120">**.NET Framework 版本：** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="ad483-120">**.NET Framework Versions:** 3.5 SP1</span></span>
