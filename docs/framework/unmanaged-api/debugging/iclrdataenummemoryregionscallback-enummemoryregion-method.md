---
title: ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion 方法
ms.date: 03/30/2017
api_name:
- ICLRDataEnumMemoryRegionsCallback.EnumMemoryRegion
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion
helpviewer_keywords:
- EnumMemoryRegion method [.NET Framework debugging]
- ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion method [.NET Framework debugging]
ms.assetid: 9bb93fab-57e8-4f9a-9ef3-1794504fa896
topic_type:
- apiref
ms.openlocfilehash: 2ebe7ef37fb072e3688cc4dcfa5ed89832e886e9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122940"
---
# <a name="iclrdataenummemoryregionscallbackenummemoryregion-method"></a>ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion 方法
由[ICLRDataEnumMemoryRegions：： EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md)呼叫，以向偵錯工具報告嘗試列舉指定的記憶體區域的結果。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumMemoryRegion (  
    [in] CLRDATA_ADDRESS  address,  
    [in] ULONG32          size  
);  
```  
  
## <a name="parameters"></a>參數  
 `address`  
 在要列舉之記憶體區域的起始位址。  
  
 `size`  
 在記憶體區域的大小（以位元組為單位）。  
  
## <a name="remarks"></a>備註  
 `ICLRDataEnumMemoryRegions::EnumMemoryRegions` 方法會在每次嘗試列舉記憶體區域之後，呼叫此回呼方法。 即使這個方法會傳回表示失敗的 HRESULT，列舉仍會繼續。  
  
 此回呼所報告的區域可能是重複或重迭的區域。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** ClrData .idl，ClrData。h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICLRDataEnumMemoryRegionsCallback 介面](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md)
