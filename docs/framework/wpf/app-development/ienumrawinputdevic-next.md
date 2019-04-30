---
title: IEnumRAWINPUTDEVIC:Next
ms.date: 03/30/2017
helpviewer_keywords:
- Next method [WPF]
ms.assetid: 3698b44d-510e-4d18-b32b-85f17188ee26
ms.openlocfilehash: 05867af48b64cd1898b13fa055859c8cc0367c8c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949574"
---
# <a name="ienumrawinputdevicnext"></a><span data-ttu-id="fa120-102">IEnumRAWINPUTDEVIC:Next</span><span class="sxs-lookup"><span data-stu-id="fa120-102">IEnumRAWINPUTDEVIC:Next</span></span>
<span data-ttu-id="fa120-103">接下來`celt` [RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice)在列舉值的清單中，將其傳回在結構`rgelt`中列舉項目的實際數目`pceltFetched`。</span><span class="sxs-lookup"><span data-stu-id="fa120-103">Enumerates the next `celt` [RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice) structures in the enumerator's list, returning them in `rgelt` along with the actual number of enumerated elements in `pceltFetched`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa120-104">語法</span><span class="sxs-lookup"><span data-stu-id="fa120-104">Syntax</span></span>  
  
```  
HRESULT Next(  
      [in] ULONG celt,  
      [out, size_is(celt), length_is(*pceltFetched)] RAWINPUTDEVICE *rgelt,  
      [out] ULONG *pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fa120-105">參數</span><span class="sxs-lookup"><span data-stu-id="fa120-105">Parameters</span></span>  
 `celt`  
  
 <span data-ttu-id="fa120-106">[in]數目[RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice)中傳回的結構`rgelt`。</span><span class="sxs-lookup"><span data-stu-id="fa120-106">[in] Number of [RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice) structures returned in `rgelt`.</span></span>  
  
 `rgelt`  
  
 <span data-ttu-id="fa120-107">[out] 要接收所列舉之 RAWINPUTDEVICE 結構的大小 celt (或更大) 陣列。</span><span class="sxs-lookup"><span data-stu-id="fa120-107">[out] Array of size celt (or larger) to receive enumerated RAWINPUTDEVICE structures.</span></span>  
  
 `pceltFetched`  
  
 <span data-ttu-id="fa120-108">[out] 指向 `rgelt` 中實際提供項目數的指標。</span><span class="sxs-lookup"><span data-stu-id="fa120-108">[out] Pointer to the number of elements actually supplied in `rgelt`.</span></span> <span data-ttu-id="fa120-109">如果 `NULL` 是 1，呼叫端就可以傳入 `rgelt`。</span><span class="sxs-lookup"><span data-stu-id="fa120-109">Caller can pass in `NULL` if `rgelt` is one.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="fa120-110">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="fa120-110">Property Value/Return Value</span></span>  
 <span data-ttu-id="fa120-111">HRESULT:如果提供的項目數目，為 S_OK `celt`;否則為 S_FALSE。</span><span class="sxs-lookup"><span data-stu-id="fa120-111">HRESULT: S_OK if the number of elements supplied is `celt`; S_FALSE otherwise.</span></span>
