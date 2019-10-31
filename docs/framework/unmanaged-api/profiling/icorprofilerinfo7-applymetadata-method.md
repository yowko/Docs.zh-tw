---
title: ICorProfilerInfo7：： ApplyMetaData 方法
ms.date: 02/15/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo7.ApplyMetaData
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: a1bfb649-4584-4d35-b3e6-8fe59b53992a
ms.openlocfilehash: 00d9bef1e2b59a2d2207d1e343380e0e81bee848
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130356"
---
# <a name="icorprofilerinfo7applymetadata-method"></a>ICorProfilerInfo7：： ApplyMetaData 方法
[在 .NET Framework 4.6.1 及更新版本中支援]  
  
 將 `IMetadataEmit::Define*` 方法新定義的中繼資料套用至指定的模組。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT ApplyMetaData(  
        [in] ModuleID moduleID  
);  
```  
  
## <a name="parameters"></a>參數  
 `moduleID`  
 在已變更其中繼資料之模組的識別碼。  
  
## <a name="remarks"></a>備註  
 如果在[ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)回呼之後進行中繼資料變更，您必須先呼叫這個方法，然後再使用新的中繼資料。  
  
 `ApplyMetaData` 只支援新增下列類型的中繼資料：  
  
- `AssemblyRef` 記錄，您可以藉由呼叫[IMetaDataAssemblyEmit：:D efineassemblyref](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)來建立。 方法。  
  
- `TypeRef` 記錄，您可以藉由呼叫[IMetaDataEmit：:D efinetyperefbyname](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md)方法來建立。  
  
- `TypeSpec` 記錄，您可以藉由呼叫[IMetaDataEmit：： GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md)方法來建立。  
  
- `MemberRef` 記錄，您可以藉由呼叫[IMetaDataEmit：:D efinememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md)方法來建立。  
  
- `MemberSpec` 記錄，您可以藉由呼叫[IMetaDataEmit2：:D efinemethodspec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md)方法來建立。  
  
- `UserString` 記錄，您可以藉由呼叫[IMetaDataEmit：:D efineuserstring](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md)方法來建立。  

從 .NET Core 3.0 開始，`ApplyMetaData` 也支援下列類型：

- `TypeDef` 記錄，您可以藉由呼叫[IMetaDataEmit：:D efinetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)方法來建立。

- `MethodDef` 記錄，您可以藉由呼叫[IMetaDataEmit：:D efinemethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md)方法來建立。 不過，不支援將虛擬方法加入至現有的類型。 虛擬方法必須在[ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)回呼之前加入。

## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorProfilerInfo7 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
