---
title: IEnumRAWINPUTDEVIC:Next
ms.date: 03/30/2017
helpviewer_keywords:
- Next method [WPF]
ms.assetid: 3698b44d-510e-4d18-b32b-85f17188ee26
ms.openlocfilehash: 3cf3231bd48290c5b6b0ce8eeb6534de564c0c85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546402"
---
# <a name="ienumrawinputdevicnext"></a><span data-ttu-id="7f75a-102">IEnumRAWINPUTDEVIC:Next</span><span class="sxs-lookup"><span data-stu-id="7f75a-102">IEnumRAWINPUTDEVIC:Next</span></span>
<span data-ttu-id="7f75a-103">列舉的下一步 `celt` [RAWINPUTDEVICE](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp)中列舉值的清單中，傳回其結構`rgelt`列舉中的項目實際數目以及`pceltFetched`。</span><span class="sxs-lookup"><span data-stu-id="7f75a-103">Enumerates the next `celt` [RAWINPUTDEVICE](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp) structures in the enumerator's list, returning them in `rgelt` along with the actual number of enumerated elements in `pceltFetched`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f75a-104">語法</span><span class="sxs-lookup"><span data-stu-id="7f75a-104">Syntax</span></span>  
  
```  
HRESULT Next(  
      [in] ULONG celt,  
      [out, size_is(celt), length_is(*pceltFetched)] RAWINPUTDEVICE *rgelt,  
      [out] ULONG *pceltFetched);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7f75a-105">參數</span><span class="sxs-lookup"><span data-stu-id="7f75a-105">Parameters</span></span>  
 `celt`  
  
 <span data-ttu-id="7f75a-106">[in]數目[RAWINPUTDEVICE](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp)中傳回的結構`rgelt`。</span><span class="sxs-lookup"><span data-stu-id="7f75a-106">[in] Number of [RAWINPUTDEVICE](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp) structures returned in `rgelt`.</span></span>  
  
 `rgelt`  
  
 <span data-ttu-id="7f75a-107">[out] 要接收所列舉之 RAWINPUTDEVICE 結構的大小 celt (或更大) 陣列。</span><span class="sxs-lookup"><span data-stu-id="7f75a-107">[out] Array of size celt (or larger) to receive enumerated RAWINPUTDEVICE structures.</span></span>  
  
 `pceltFetched`  
  
 <span data-ttu-id="7f75a-108">[out] 指向 `rgelt` 中實際提供項目數的指標。</span><span class="sxs-lookup"><span data-stu-id="7f75a-108">[out] Pointer to the number of elements actually supplied in `rgelt`.</span></span> <span data-ttu-id="7f75a-109">如果 `NULL` 是 1，呼叫端就可以傳入 `rgelt`。</span><span class="sxs-lookup"><span data-stu-id="7f75a-109">Caller can pass in `NULL` if `rgelt` is one.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="7f75a-110">屬性值/傳回值</span><span class="sxs-lookup"><span data-stu-id="7f75a-110">Property Value/Return Value</span></span>  
 <span data-ttu-id="7f75a-111">HRESULT: 如果提供的項目數是 `celt`，則為 S_OK；否則為 S_FALSE。</span><span class="sxs-lookup"><span data-stu-id="7f75a-111">HRESULT: S_OK if the number of elements supplied is `celt`; S_FALSE otherwise.</span></span>
