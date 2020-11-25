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
ms.openlocfilehash: 4abcf9f4575b32dd125fd8a00783043900993c3e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724100"
---
# <a name="icorprofilerinfogetobjectsize-method"></a>ICorProfilerInfo::GetObjectSize 方法

取得指定之物件的大小。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetObjectSize(  
    [in]  ObjectID objectId,  
    [out] ULONG  *pcSize);  
```  
  
## <a name="parameters"></a>參數  

 `objectId`  
 在物件的識別碼。  
  
 `pcSize`  
 擴展物件大小的指標（以位元組為單位）。  
  
## <a name="remarks"></a>備註  
  
> [!IMPORTANT]
> 這個方法已過時。 它會針對64位平臺上大於4GB 的物件傳回 COR_E_OVERFLOW。 請改用  [ICorProfilerInfo4：： GetObjectSize2](icorprofilerinfo4-getobjectsize2-method.md) 方法。  
  
 相同類型的不同物件通常具有相同的大小。 不過，某些類型（例如陣列或字串）的每個物件可能會有不同的大小。  
  
 方法所傳回的大小 `GetObjectSize` 不包括在物件位於垃圾收集堆積之後可能出現的對齊填補。 如果您使用 `GetObjectSize` 方法從物件移至垃圾收集堆積上的物件，請視需要手動加入對齊填補。  
  
- 在32位的 Windows 上，COR_PRF_GC_GEN_0、COR_PRF_GC_GEN_1 和 COR_PRF_GC_GEN_2 使用4位元組對齊，而 COR_PRF_GC_LARGE_OBJECT_HEAP 會使用8位元組對齊。  
  
- 在64位的 Windows 上，對齊一律為8個位元組。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo 介面](icorprofilerinfo-interface.md)
