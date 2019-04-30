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
# <a name="ienumrawinputdevicnext"></a>IEnumRAWINPUTDEVIC:Next
接下來`celt` [RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice)在列舉值的清單中，將其傳回在結構`rgelt`中列舉項目的實際數目`pceltFetched`。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Next(  
      [in] ULONG celt,  
      [out, size_is(celt), length_is(*pceltFetched)] RAWINPUTDEVICE *rgelt,  
      [out] ULONG *pceltFetched);  
```  
  
## <a name="parameters"></a>參數  
 `celt`  
  
 [in]數目[RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice)中傳回的結構`rgelt`。  
  
 `rgelt`  
  
 [out] 要接收所列舉之 RAWINPUTDEVICE 結構的大小 celt (或更大) 陣列。  
  
 `pceltFetched`  
  
 [out] 指向 `rgelt` 中實際提供項目數的指標。 如果 `NULL` 是 1，呼叫端就可以傳入 `rgelt`。  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
 HRESULT:如果提供的項目數目，為 S_OK `celt`;否則為 S_FALSE。
