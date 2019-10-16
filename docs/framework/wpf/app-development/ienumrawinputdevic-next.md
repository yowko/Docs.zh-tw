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
# <a name="ienumrawinputdevicnext"></a>IEnumRAWINPUTDEVIC:Next
列舉枚舉器`celt`清單中的下一個[RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice)結構，並在中`rgelt`傳回它們，以及中`pceltFetched`的實際列舉元素數目。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Next(  
      [in] ULONG celt,  
      [out, size_is(celt), length_is(*pceltFetched)] RAWINPUTDEVICE *rgelt,  
      [out] ULONG *pceltFetched);  
```  
  
## <a name="parameters"></a>參數  
 `celt`  
  
 在在中 `rgelt` 傳回的 [RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice) 結構數目。  
  
 `rgelt`  
  
 [out] 要接收所列舉之 RAWINPUTDEVICE 結構的大小 celt (或更大) 陣列。  
  
 `pceltFetched`  
  
 [out] 指向 `rgelt` 中實際提供項目數的指標。 如果 `NULL` 是 1，呼叫端就可以傳入 `rgelt`。  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
 HRESULT:如果提供的元素數目為， `celt`則為 S_OK;否則為 S_FALSE。
