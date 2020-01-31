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
ms.openlocfilehash: b9e488a512ad506a8975bfff44ae02cd84c29f74
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861693"
---
# <a name="icorprofilerinfo7applymetadata-method"></a><span data-ttu-id="2c973-102">ICorProfilerInfo7：： ApplyMetaData 方法</span><span class="sxs-lookup"><span data-stu-id="2c973-102">ICorProfilerInfo7::ApplyMetaData Method</span></span>
<span data-ttu-id="2c973-103">[在 .NET Framework 4.6.1 及更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="2c973-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="2c973-104">將 `IMetadataEmit::Define*` 方法新定義的中繼資料套用至指定的模組。</span><span class="sxs-lookup"><span data-stu-id="2c973-104">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c973-105">語法</span><span class="sxs-lookup"><span data-stu-id="2c973-105">Syntax</span></span>  
  
```cpp
HRESULT ApplyMetaData(  
        [in] ModuleID moduleID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c973-106">參數</span><span class="sxs-lookup"><span data-stu-id="2c973-106">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="2c973-107">在已變更其中繼資料之模組的識別碼。</span><span class="sxs-lookup"><span data-stu-id="2c973-107">[in] The identifier of the module whose metadata was changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c973-108">備註</span><span class="sxs-lookup"><span data-stu-id="2c973-108">Remarks</span></span>  
 <span data-ttu-id="2c973-109">如果在[ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md)回呼之後進行中繼資料變更，您必須先呼叫這個方法，然後再使用新的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="2c973-109">If metadata changes are made after the [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback, you must call this method before using the new metadata.</span></span>  
  
 <span data-ttu-id="2c973-110">`ApplyMetaData` 只支援新增下列類型的中繼資料：</span><span class="sxs-lookup"><span data-stu-id="2c973-110">`ApplyMetaData` only supports adding the following types of metadata:</span></span>  
  
- <span data-ttu-id="2c973-111">`AssemblyRef` 記錄，您可以藉由呼叫[IMetaDataAssemblyEmit：:D efineassemblyref](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)來建立。</span><span class="sxs-lookup"><span data-stu-id="2c973-111">`AssemblyRef` records, which you create by calling the [IMetaDataAssemblyEmit::DefineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md).</span></span> <span data-ttu-id="2c973-112">方法。</span><span class="sxs-lookup"><span data-stu-id="2c973-112">method.</span></span>  
  
- <span data-ttu-id="2c973-113">`TypeRef` 記錄，您可以藉由呼叫[IMetaDataEmit：:D efinetyperefbyname](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md)方法來建立。</span><span class="sxs-lookup"><span data-stu-id="2c973-113">`TypeRef` records, which you create by calling the [IMetaDataEmit::DefineTypeRefByName](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md) method.</span></span>  
  
- <span data-ttu-id="2c973-114">`TypeSpec` 記錄，您可以藉由呼叫[IMetaDataEmit：： GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md)方法來建立。</span><span class="sxs-lookup"><span data-stu-id="2c973-114">`TypeSpec` records, which you create by calling the [IMetaDataEmit::GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
- <span data-ttu-id="2c973-115">`MemberRef` 記錄，您可以藉由呼叫[IMetaDataEmit：:D efinememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md)方法來建立。</span><span class="sxs-lookup"><span data-stu-id="2c973-115">`MemberRef` records, which you create by calling the [IMetaDataEmit::DefineMemberRef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md) method.</span></span>  
  
- <span data-ttu-id="2c973-116">`MemberSpec` 記錄，您可以藉由呼叫[IMetaDataEmit2：:D efinemethodspec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md)方法來建立。</span><span class="sxs-lookup"><span data-stu-id="2c973-116">`MemberSpec` records, which you create by calling the [IMetaDataEmit2::DefineMethodSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md) method.</span></span>  
  
- <span data-ttu-id="2c973-117">`UserString` 記錄，您可以藉由呼叫[IMetaDataEmit：:D efineuserstring](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md)方法來建立。</span><span class="sxs-lookup"><span data-stu-id="2c973-117">`UserString` records, which you create by calling the [IMetaDataEmit::DefineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md) method.</span></span>  

<span data-ttu-id="2c973-118">從 .NET Core 3.0 開始，`ApplyMetaData` 也支援下列類型：</span><span class="sxs-lookup"><span data-stu-id="2c973-118">Starting with .NET Core 3.0, `ApplyMetaData` also supports the following types:</span></span>

- <span data-ttu-id="2c973-119">`TypeDef` 記錄，您可以藉由呼叫[IMetaDataEmit：:D efinetypedef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)方法來建立。</span><span class="sxs-lookup"><span data-stu-id="2c973-119">`TypeDef` records, which you create by calling the [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md) method.</span></span>

- <span data-ttu-id="2c973-120">`MethodDef` 記錄，您可以藉由呼叫[IMetaDataEmit：:D efinemethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md)方法來建立。</span><span class="sxs-lookup"><span data-stu-id="2c973-120">`MethodDef` records, which you create by calling the [IMetaDataEmit::DefineMethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md) method.</span></span> <span data-ttu-id="2c973-121">不過，不支援將虛擬方法加入至現有的類型。</span><span class="sxs-lookup"><span data-stu-id="2c973-121">However, adding virtual methods to an existing type is not supported.</span></span> <span data-ttu-id="2c973-122">虛擬方法必須在[ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md)回呼之前加入。</span><span class="sxs-lookup"><span data-stu-id="2c973-122">Virtual methods must be added before the [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="2c973-123">需求</span><span class="sxs-lookup"><span data-stu-id="2c973-123">Requirements</span></span>  
 <span data-ttu-id="2c973-124">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2c973-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c973-125">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2c973-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2c973-126">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c973-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c973-127">**.NET framework 版本：** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c973-127">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c973-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="2c973-128">See also</span></span>

- [<span data-ttu-id="2c973-129">ICorProfilerInfo7 介面</span><span class="sxs-lookup"><span data-stu-id="2c973-129">ICorProfilerInfo7 Interface</span></span>](icorprofilerinfo7-interface.md)
