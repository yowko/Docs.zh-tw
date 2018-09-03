---
title: IEnumRAWINPUTDEVIC:Next
ms.date: 03/30/2017
helpviewer_keywords:
- Next method [WPF]
ms.assetid: 3698b44d-510e-4d18-b32b-85f17188ee26
ms.openlocfilehash: 329a2cd96346e199ee834856dd6dbfac6175b722
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2018
ms.locfileid: "43481174"
---
# <a name="ienumrawinputdevicnext"></a>IEnumRAWINPUTDEVIC:Next
接下來`celt` [RAWINPUTDEVICE](https://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp)在列舉值的清單中，將其傳回在結構`rgelt`中列舉項目的實際數目`pceltFetched`。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Next(  
      [in] ULONG celt,  
      [out, size_is(celt), length_is(*pceltFetched)] RAWINPUTDEVICE *rgelt,  
      [out] ULONG *pceltFetched);  
```  
  
#### <a name="parameters"></a>參數  
 `celt`  
  
 [in]數目[RAWINPUTDEVICE](https://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp)中傳回的結構`rgelt`。  
  
 `rgelt`  
  
 [out] 要接收所列舉之 RAWINPUTDEVICE 結構的大小 celt (或更大) 陣列。  
  
 `pceltFetched`  
  
 [out] 指向 `rgelt` 中實際提供項目數的指標。 如果 `NULL` 是 1，呼叫端就可以傳入 `rgelt`。  
  
## <a name="property-valuereturn-value"></a>屬性值/傳回值  
 HRESULT: 如果提供的項目數是 `celt`，則為 S_OK；否則為 S_FALSE。
