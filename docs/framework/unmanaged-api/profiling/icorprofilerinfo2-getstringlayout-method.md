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
ms.openlocfilehash: 4d4efa7cb3bc98c54be2889855c3b756fdbf2847
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782235"
---
# <a name="icorprofilerinfo2getstringlayout-method"></a>ICorProfilerInfo2::GetStringLayout 方法
取得字串物件配置的相關資訊。 這個方法在.NET Framework 4 中，已被取代，並被取代[ICorProfilerInfo3::GetStringLayout2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md)方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetStringLayout(  
    [out] ULONG *pBufferLengthOffset,  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a>參數  
 `pBufferLengthOffset`  
 [out]指標位移的位置，相對於`ObjectID`指標，儲存字串的長度。 長度會儲存為`DWORD`。  
  
> [!NOTE]
>  此參數會傳回字串的長度，不是緩衝區的長度。 緩衝區的長度已無法再使用。  
  
 `PStringLengthOffset`  
 [out]指標位移的位置，相對於`ObjectID`儲存的字串本身長度的指標。 長度會儲存為`DWORD`。  
  
 `pBufferOffset`  
 [out]相對於的緩衝區位移的指標`ObjectID`儲存的寬字元字串的指標。  
  
## <a name="remarks"></a>備註  
 `GetStringLayout`方法會取得位移，相對於`ObjectID`指標，下列預存的位置：  
  
- 字串的緩衝區的長度。  
  
- 字串本身長度。  
  
- 包含實際的寬字元字串的緩衝區。  
  
 字串可能會以 null 結束。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
