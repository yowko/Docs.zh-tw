---
title: ICorProfilerInfo7::ApplyMetaData 方法
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8f261b02dd19ead0d6803cae543f39a06c99f033
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64586692"
---
# <a name="icorprofilerinfo7applymetadata-method"></a><span data-ttu-id="aab62-102">ICorProfilerInfo7::ApplyMetaData 方法</span><span class="sxs-lookup"><span data-stu-id="aab62-102">ICorProfilerInfo7::ApplyMetaData Method</span></span>
<span data-ttu-id="aab62-103">[在 .NET Framework 4.6.1 及更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="aab62-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="aab62-104">適用於新所定義的中繼資料`IMetadataEmit::Define*`方法，以指定的模組。</span><span class="sxs-lookup"><span data-stu-id="aab62-104">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aab62-105">語法</span><span class="sxs-lookup"><span data-stu-id="aab62-105">Syntax</span></span>  
  
```cpp
HRESULT ApplyMetaData(  
        [in] ModuleID moduleID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aab62-106">參數</span><span class="sxs-lookup"><span data-stu-id="aab62-106">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="aab62-107">[in]其中繼資料已變更之模組的識別碼。</span><span class="sxs-lookup"><span data-stu-id="aab62-107">[in] The identifier of the module whose metadata was changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aab62-108">備註</span><span class="sxs-lookup"><span data-stu-id="aab62-108">Remarks</span></span>  
 <span data-ttu-id="aab62-109">如果中繼資料變更後[ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)回呼中，您必須使用新的中繼資料之前呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="aab62-109">If metadata changes are made after the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback, you must call this method before using the new metadata.</span></span>  
  
 <span data-ttu-id="aab62-110">`ApplyMetaData` 僅支援加入下列類型的中繼資料：</span><span class="sxs-lookup"><span data-stu-id="aab62-110">`ApplyMetaData` only supports adding the following types of metadata:</span></span>  
  
- <span data-ttu-id="aab62-111">`AssemblyRef` 您呼叫建立的記錄[imetadataassemblyemit:: Defineassemblyref](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)。</span><span class="sxs-lookup"><span data-stu-id="aab62-111">`AssemblyRef` records, which you create by calling the [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md).</span></span> <span data-ttu-id="aab62-112">方法。</span><span class="sxs-lookup"><span data-stu-id="aab62-112">method.</span></span>  
  
- <span data-ttu-id="aab62-113">`TypeRef` 您呼叫建立的記錄[imetadataemit:: Definetyperefbyname](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="aab62-113">`TypeRef` records, which you create by calling the [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) method.</span></span>  
  
- <span data-ttu-id="aab62-114">`TypeSpec` 您呼叫建立的記錄[imetadataemit:: Gettokenfromtypespec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="aab62-114">`TypeSpec` records, which you create by calling the [IMetaDataEmit::GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
- <span data-ttu-id="aab62-115">`MemberRef` 您呼叫建立的記錄[imetadataemit:: Definememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="aab62-115">`MemberRef` records, which you create by calling the [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) method.</span></span>  
  
- <span data-ttu-id="aab62-116">`MemberSpec` 您呼叫建立的記錄[IMetaDataEmit2::DefineMethodSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="aab62-116">`MemberSpec` records, which you create by calling the [IMetaDataEmit2::DefineMethodSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md) method.</span></span>  
  
- <span data-ttu-id="aab62-117">`UserString` 您呼叫建立的記錄[imetadataemit:: Defineuserstring](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="aab62-117">`UserString` records, which you create by calling the [IMetaDataEmit::DefineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) method.</span></span>  

<span data-ttu-id="aab62-118">開始使用.NET Core 3.0，`ApplyMetaData`也支援下列類型：</span><span class="sxs-lookup"><span data-stu-id="aab62-118">Starting with .NET Core 3.0, `ApplyMetaData` also supports the following types:</span></span>

- <span data-ttu-id="aab62-119">`TypeDef` 您呼叫建立的記錄[imetadataemit:: Definetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="aab62-119">`TypeDef` records, which you create by calling the [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) method.</span></span>

- <span data-ttu-id="aab62-120">`MethodDef` 您呼叫建立的記錄[imetadataemit:: Definemethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="aab62-120">`MethodDef` records, which you create by calling the [IMetaDataEmit::DefineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md) method.</span></span> <span data-ttu-id="aab62-121">不過，不支援將虛擬方法加入至現有的類型。</span><span class="sxs-lookup"><span data-stu-id="aab62-121">However, adding virtual methods to an existing type is not supported.</span></span> <span data-ttu-id="aab62-122">必須新增虛擬方法，才能[ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="aab62-122">Virtual methods must be added before the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="aab62-123">需求</span><span class="sxs-lookup"><span data-stu-id="aab62-123">Requirements</span></span>  
 <span data-ttu-id="aab62-124">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="aab62-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aab62-125">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="aab62-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="aab62-126">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aab62-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aab62-127">**.NET framework 版本：**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aab62-127">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aab62-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aab62-128">See also</span></span>

- [<span data-ttu-id="aab62-129">ICorProfilerInfo7 介面</span><span class="sxs-lookup"><span data-stu-id="aab62-129">ICorProfilerInfo7 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
