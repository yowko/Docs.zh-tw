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
ms.openlocfilehash: 15c843fe138be55a3480f46e0ef8b37bcb445ad0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497968"
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
 脫銷物件大小的指標（以位元組為單位）。  
  
## <a name="remarks"></a>備註  
  
> [!IMPORTANT]
> 這個方法已過時。 它會傳回64位平臺上大於4GB 之物件的 COR_E_OVERFLOW。 請改用[ICorProfilerInfo4：： GetObjectSize2](icorprofilerinfo4-getobjectsize2-method.md)方法。  
  
 相同類型的不同物件通常具有相同的大小。 不過，某些類型（例如陣列或字串）可能會有不同的大小供每個物件使用。  
  
 方法所傳回的大小 `GetObjectSize` 不包含物件在垃圾收集堆積上之後可能出現的任何對齊填補。 如果您使用 `GetObjectSize` 方法從物件前進到垃圾收集堆積上的物件，請視需要手動新增對齊填補。  
  
- 在32位 Windows 上，COR_PRF_GC_GEN_0、COR_PRF_GC_GEN_1 和 COR_PRF_GC_GEN_2 使用4位元組對齊，而 COR_PRF_GC_LARGE_OBJECT_HEAP 使用8位元組對齊。  
  
- 在64位 Windows 上，對齊一律為8個位元組。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo 介面](icorprofilerinfo-interface.md)
