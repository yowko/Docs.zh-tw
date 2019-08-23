---
title: ICorProfilerInfo2::GetStringLayout 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetStringLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetStringLayout
helpviewer_keywords:
- GetStringLayout method [.NET Framework profiling]
- ICorProfilerInfo2::GetStringLayout method [.NET Framework profiling]
ms.assetid: 43189651-a535-4803-a1d1-f1c427ace2ca
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 63ad2532240c9f18a00421281fae0d111dbfaec5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963797"
---
# <a name="icorprofilerinfo2getstringlayout-method"></a>ICorProfilerInfo2::GetStringLayout 方法
取得字串物件配置的相關資訊。 這個方法在 .NET Framework 4 中已被取代, 而且會被[ICorProfilerInfo3:: GetStringLayout2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md)方法所取代。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetStringLayout(  
    [out] ULONG *pBufferLengthOffset,  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a>參數  
 `pBufferLengthOffset`  
 脫銷相對`ObjectID`于指標的位置位移指標, 儲存字串的長度。 長度會儲存為`DWORD`。  
  
> [!NOTE]
> 這個參數會傳回字串本身的長度, 而不是緩衝區的長度。 緩衝區長度已無法再使用。  
  
 `PStringLengthOffset`  
 脫銷相對於`ObjectID`指標之位置位移的指標, 會儲存字串本身的長度。 長度會儲存為`DWORD`。  
  
 `pBufferOffset`  
 脫銷相對`ObjectID`于指標的緩衝區位移指標, 儲存寬字元的字串。  
  
## <a name="remarks"></a>備註  
 方法會取得下列位置的位移 (相對`ObjectID`于指標): `GetStringLayout`  
  
- 字串緩衝區的長度。  
  
- 字串本身的長度。  
  
- 包含寬字元實際字串的緩衝區。  
  
 字串可能是以 null 結束。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Corprof.idl .idl, Corprof.idl。h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
