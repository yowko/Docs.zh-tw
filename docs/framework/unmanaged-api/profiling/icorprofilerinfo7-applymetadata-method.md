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
ms.openlocfilehash: 2c71db25422740880d8b29576eff247d5eba5f1d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686107"
---
# <a name="icorprofilerinfo7applymetadata-method"></a>ICorProfilerInfo7：： ApplyMetaData 方法

[在 .NET Framework 4.6.1 及更新版本中支援]  
  
 將方法新定義的中繼資料套用 `IMetadataEmit::Define*` 至指定的模組。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT ApplyMetaData(  
        [in] ModuleID moduleID  
);  
```  
  
## <a name="parameters"></a>參數  

 `moduleID`  
 在其中繼資料已變更之模組的識別碼。  
  
## <a name="remarks"></a>備註  

 如果在 [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) 回呼之後進行中繼資料變更，您必須先呼叫這個方法，然後再使用新的中繼資料。  
  
 `ApplyMetaData` 僅支援新增下列類型的中繼資料：  
  
- `AssemblyRef` 您藉由呼叫 IMetaDataAssemblyEmit 來建立的記錄 [：:D efineassemblyref](../metadata/imetadataassemblyemit-defineassemblyref-method.md)。 方法。  
  
- `TypeRef` 您藉由呼叫 [IMetaDataEmit：:D efinetyperefbyname](../metadata/imetadataemit-definetyperefbyname-method.md) 方法所建立的記錄。  
  
- `TypeSpec` 您藉由呼叫 [IMetaDataEmit：： GetTokenFromTypeSpec](../metadata/imetadataemit-gettokenfromtypespec-method.md) 方法所建立的記錄。  
  
- `MemberRef` 您藉由呼叫 [IMetaDataEmit：:D efinememberref](../metadata/imetadataemit-definememberref-method.md) 方法所建立的記錄。  
  
- `MemberSpec` 您藉由呼叫 [IMetaDataEmit2：:D efinemethodspec](../metadata/imetadataemit2-definemethodspec-method.md) 方法所建立的記錄。  
  
- `UserString` 您藉由呼叫 [IMetaDataEmit：:D efineuserstring](../metadata/imetadataemit-defineuserstring-method.md) 方法所建立的記錄。  

從 .NET Core 3.0 開始， `ApplyMetaData` 也支援下列類型：

- `TypeDef` 您藉由呼叫 [IMetaDataEmit：:D efinetypedef](../metadata/imetadataemit-definetypedef-method.md) 方法所建立的記錄。

- `MethodDef` 您藉由呼叫 [IMetaDataEmit：:D efinemethod](../metadata/imetadataemit-definemethod-method.md) 方法所建立的記錄。 但是，不支援將虛擬方法加入至現有的類型。 虛擬方法必須在 [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) 回呼之前新增。

## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo7 介面](icorprofilerinfo7-interface.md)
