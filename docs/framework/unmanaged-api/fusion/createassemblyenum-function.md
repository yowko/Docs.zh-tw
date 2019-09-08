---
title: CreateAssemblyEnum 函式
ms.date: 03/30/2017
api_name:
- CreateAssemblyEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyEnum
helpviewer_keywords:
- CreateAssemblyEnum function [.NET Framework fusion]
ms.assetid: 3506df38-6cea-42f6-946e-4287863bcfb3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1db72c44b53b5abff9aee35094abc1e0e577fad4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795382"
---
# <a name="createassemblyenum-function"></a>CreateAssemblyEnum 函式
取得[IAssemblyEnum](iassemblyenum-interface.md)實例的指標，這個實例可以使用指定的[IAssemblyName](iassemblyname-interface.md)來列舉元件中的物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CreateAssemblyEnum (  
    [out] IAssemblyEnum  **pEnum,  
    [in]  IUnknown       *pUnkReserved,  
    [in]  IAssemblyName  *pName,  
    [in]  DWORD          dwFlags,  
    [in]  LPVOID         pvReserved  
 );  
```  
  
## <a name="parameters"></a>參數  
 `pEnum`  
 脫銷包含所要求`IAssemblyEnum`指標之記憶體位置的指標。  
  
 `pUnkReserved`  
 在保留以供未來擴充性之用。 `pUnkReserved`必須是 null 參考。  
  
 `pName`  
 在所`IAssemblyName`要求之元件的。 這個名稱是用來篩選列舉型別。 它可以是 null，以列舉全域組件快取中的所有元件。  
  
 `dwFlags`  
 在用來修改列舉值行為的旗標。 此參數只包含[ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md)列舉中的一個位。  
  
 `pvReserved`  
 在保留以供未來擴充性之用。 `pvReserved`必須是 null 參考。  
  
## <a name="remarks"></a>備註  
 參數只包含`ASM_CACHE_FLAGS`列舉中的一個位。 `dwFlags`  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** 融合。h  
  
 **LIBRARY:** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [IAssemblyEnum 介面](iassemblyenum-interface.md)
- [IAssemblyName 介面](iassemblyname-interface.md)
- [融合全域靜態函式](fusion-global-static-functions.md)
