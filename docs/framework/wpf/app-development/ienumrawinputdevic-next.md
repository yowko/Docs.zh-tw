---
title: IEnumRAWINPUTDEVIC:Next
ms.date: 03/30/2017
helpviewer_keywords:
- Next method [WPF]
ms.assetid: 3698b44d-510e-4d18-b32b-85f17188ee26
ms.openlocfilehash: c7450a9ababa9cf3cb02d572f5ed84f0791d74e4
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053404"
---
# <a name="ienumrawinputdevicnext"></a><span data-ttu-id="ba330-102">IEnumRAWINPUTDEVIC:Next</span><span class="sxs-lookup"><span data-stu-id="ba330-102">IEnumRAWINPUTDEVIC:Next</span></span>
<span data-ttu-id="ba330-103">列舉枚舉器`celt`清單中的下一個[RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice)結構，並在中`rgelt`傳回它們，以及中`pceltFetched`的實際列舉元素數目。</span><span class="sxs-lookup"><span data-stu-id="ba330-103">Enumerates the next `celt` [RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice) structures in the enumerator's list, returning them in `rgelt` along with the actual number of enumerated elements in `pceltFetched`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba330-104">語法</span><span class="sxs-lookup"><span data-stu-id="ba330-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
      [in] ULONG celt,  
      [out, size_is(celt), length_is(*pceltFetched)] RAWINPUTDEVICE *rgelt,  
      [out] ULONG *pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba330-105">參數</span><span class="sxs-lookup"><span data-stu-id="ba330-105">Parameters</span></span>  
 `celt`  
  
 <span data-ttu-id="ba330-106">在在中 `rgelt` 傳回的 [RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice) 結構數目。</span><span class="sxs-lookup"><span data-stu-id="ba330-106">[in] Number of [RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice) structures returned in `rgelt`.</span></span>  
  
 `rgelt`  
  
 <span data-ttu-id="ba330-107">[out] 要接收所列舉之 RAWINPUTDEVICE 結構的大小 celt (或更大) 陣列。</span><span class="sxs-lookup"><span data-stu-id="ba330-107">[out] Array of size celt (or larger) to receive enumerated RAWINPUTDEVICE structures.</span></span>  
  
 `pceltFetched`  
  
 <span data-ttu-id="ba330-108">[out] 指向 `rgelt` 中實際提供項目數的指標。</span><span class="sxs-lookup"><span data-stu-id="ba330-108">[out] Pointer to the number of elements actually supplied in `rgelt`.</span></span> <span data-ttu-id="ba330-109">如果 `NULL` 是 1，呼叫端就可以傳入 `rgelt`。</span><span class="sxs-lookup"><span data-stu-id="ba330-109">Caller can pass in `NULL` if `rgelt` is one.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="ba330-110">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="ba330-110">Property Value/Return Value</span></span>  
 <span data-ttu-id="ba330-111">HRESULT:如果提供的元素數目為， `celt`則為 S_OK;否則為 S_FALSE。</span><span class="sxs-lookup"><span data-stu-id="ba330-111">HRESULT: S_OK if the number of elements supplied is `celt`; S_FALSE otherwise.</span></span>
