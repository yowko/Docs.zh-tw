---
title: ICorProfilerInfo3::GetStringLayout2 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetStringLayout2 Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetStringLayout2
helpviewer_keywords:
- ICorProfilerInfo3::GetStringLayout2 method [.NET Framework profiling]
- GetStringLayout2 method [.NET Framework profiling]
ms.assetid: 1a268496-ee51-4d84-8700-ee56fd0c499d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1ac724db000f84e37995a34e808d3df4b1e7a960
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765402"
---
# <a name="icorprofilerinfo3getstringlayout2-method"></a>ICorProfilerInfo3::GetStringLayout2 方法
取得字串物件配置的相關資訊。 這個方法會取代[ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md)方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetStringLayout2(  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a>參數  
 `pStringLengthOffset`  
 [out]指標位移的位置，相對於`ObjectID`儲存的字串本身長度的指標。 長度會儲存為`DWORD`。  
  
 `pBufferOffset`  
 [out]相對於的緩衝區位移的指標`ObjectID`指標，其中儲存的寬字元字串。  
  
## <a name="remarks"></a>備註  
 字串可能會或可能不是以 null 結尾。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo3 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [分析介面](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
