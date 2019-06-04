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
ms.openlocfilehash: faa5ecf63ac3795a58369d94f9fb15f853edb576
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490705"
---
# <a name="icorprofilerinfo2getstringlayout-method"></a>ICorProfilerInfo2::GetStringLayout 方法
取得字串物件配置的相關資訊。 這個方法在.NET Framework 4 中，已被取代，並被取代[ICorProfilerInfo3::GetStringLayout2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md)方法。  
  
## <a name="syntax"></a>語法  
  
```  
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
