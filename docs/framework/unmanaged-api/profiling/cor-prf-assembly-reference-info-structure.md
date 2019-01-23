---
title: COR_PRF_ASSEMBLY_REFERENCE_INFO 結構
ms.date: 03/30/2017
dev_langs:
- cpp
ms.assetid: c8c1d916-8d1a-4f82-8128-9fd3732383fc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 380dbe43c09e0be48410431b87d796f502a7012b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54634940"
---
# <a name="corprfassemblyreferenceinfo-structure"></a>COR_PRF_ASSEMBLY_REFERENCE_INFO 結構
[在 .NET Framework 4.5.2 及更新版本中支援]  
  
 提供執行組件參考關閉查核時應考量之組件參考的相關資訊給 Common Language Runtime。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef struct _COR_PRF_ASSEMBLY_REFERENCE_INFO {  
    void* pbPublicKeyOrToken;  
    ULONG cbPublicKeyOrToken;  
    LPCWSTR szName;  
    ASSEMBLYMETADATA* pMetaData;  
    void* pbHashValue;  
    ULONG cbHashValue;  
    DWORD dwAssemblyRefFlags;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`pbPublicKeyOrToken`|組件的公開金鑰或語彙基元的指標。|  
|`cbPublicKeyOrToken`|公開金鑰或語彙基元中的位元組數。|  
|`szName`|參考之組件的名稱。|  
|`pMetaData`|組件中繼資料的指標。|  
|`pbHashValue`|雜湊二進位大型物件 (BLOB) 的指標。|  
|`cbHashValue`|雜湊 BLOB 中的位元組數。|  
|`dwAssemblyRefFlags`|組件的旗標。|  
  
## <a name="remarks"></a>備註  
 `COR_PRF_EX_CLAUSE_INFO` 結構會在其宣告 Common Language Runtime 在執行組件參考關閉查核時應考量的其他組件參考時，由分析工具填入。  
  
 如果分析工具註冊[ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)回呼方法，執行階段會傳遞要載入，以及一個指向組件的名稱與路徑[ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)介面物件，該方法。 然後可以呼叫分析工具[icorprofilerassemblyreferenceprovider:: Addassemblyreference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)方法`COR_PRF_ASSEMBLY_REFERENCE_INFO`每個目標組件計劃要從指定的組件參考的物件[ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)回呼。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [分析結構](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
- [GetAssemblyReferences 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)
- [AddAssemblyReference 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)
