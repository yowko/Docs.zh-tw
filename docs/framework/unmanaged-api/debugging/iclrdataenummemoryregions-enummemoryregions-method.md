---
title: ICLRDataEnumMemoryRegions::EnumMemoryRegions 方法
ms.date: 03/30/2017
api_name:
- ICLRDataEnumMemoryRegions.EnumMemoryRegions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataEnumMemoryRegions::EnumMemoryRegions
helpviewer_keywords:
- ICLRDataEnumMemoryRegions::EnumMemoryRegions method [.NET Framework debugging]
- EnumMemoryRegions method [.NET Framework debugging]
ms.assetid: 22d2e339-f174-40b5-a478-0b744501566f
topic_type:
- apiref
ms.openlocfilehash: e6cdc924df126e56d2e7c8c9cb8762ee88712fcc
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860696"
---
# <a name="iclrdataenummemoryregionsenummemoryregions-method"></a>ICLRDataEnumMemoryRegions::EnumMemoryRegions 方法
列舉指定的記憶體區域。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EnumMemoryRegions (  
    [in] ICLRDataEnumMemoryRegionsCallback  *callback,  
    [in] ULONG32                            miniDumpFlags,  
    [in] CLRDataEnumMemoryFlags             clrFlags  
);  
```  
  
## <a name="parameters"></a>參數  
 `callback`  
 在[ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md)實例的指標，此方法會針對每個列舉的記憶體區域呼叫，以通知偵錯工具結果。  
  
 即使回呼表示失敗，記憶體區域的列舉仍會繼續。  
  
 `miniDumpFlags`  
 在未使用。  
  
 `clrFlags`  
 在[CLRDataEnumMemoryFlags](clrdataenummemoryflags-enumeration.md)列舉的值，指定要列舉的記憶體區域。  
  
## <a name="remarks"></a>備註  
 這個方法會使用指定的[ICLRDataEnumMemoryRegionsCallback](iclrdataenummemoryregionscallback-interface.md)實例來通知呼叫者結果。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** ClrData .idl，ClrData。h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICLRDataEnumMemoryRegions 介面](iclrdataenummemoryregions-interface.md)
