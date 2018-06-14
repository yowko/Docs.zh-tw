---
title: ICorProfilerInfo::GetObjectSize 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetObjectSize
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetObjectSize
helpviewer_keywords:
- GetObjectSize method [.NET Framework profiling]
- ICorProfilerInfo::GetObjectSize method [.NET Framework profiling]
ms.assetid: 9f02e763-73f7-42cb-a41c-f78499d9482c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7ed27602dfa9090b46b842e4e65af8af373cc207
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453905"
---
# <a name="icorprofilerinfogetobjectsize-method"></a>ICorProfilerInfo::GetObjectSize 方法
取得指定之物件的大小。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetObjectSize(  
    [in]  ObjectID objectId,  
    [out] ULONG  *pcSize);  
```  
  
#### <a name="parameters"></a>參數  
 `objectId`  
 [in]物件的識別碼。  
  
 `pcSize`  
 [out]物件的大小 （位元組） 指標。  
  
## <a name="remarks"></a>備註  
  
> [!IMPORTANT]
>  這個方法已過時。 它會傳回 COR_E_OVERFLOW 物件大於 4 GB 在 64 位元平台上。 使用[icorprofilerinfo4:: Getobjectsize2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md)方法改為。  
  
 相同的類型不同的物件通常會有相同的大小。 不過，某些類型，例如陣列或字串，可能必須針對每個物件的大小不同。  
  
 所傳回的大小`GetObjectSize`方法不包含在記憶體回收堆積上物件之後，可能會出現任何對齊填補。 如果您使用`GetObjectSize`前進物件物件在記憶體回收堆積，方法中加入手動視需要填補的對齊方式。  
  
-   32 位元 Windows 上 COR_PRF_GC_GEN_0、 COR_PRF_GC_GEN_1 和 COR_PRF_GC_GEN_2 使用 4 位元組對齊，而 COR_PRF_GC_LARGE_OBJECT_HEAP 使用 8 位元組對齊。  
  
-   在 64 位元 Windows 上對齊一定是 8 個位元組。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorProfilerInfo 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
