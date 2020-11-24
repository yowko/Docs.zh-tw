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
# <a name="icorprofilerinfo7applymetadata-method"></a><span data-ttu-id="01f23-102">ICorProfilerInfo7：： ApplyMetaData 方法</span><span class="sxs-lookup"><span data-stu-id="01f23-102">ICorProfilerInfo7::ApplyMetaData Method</span></span>

<span data-ttu-id="01f23-103">[在 .NET Framework 4.6.1 及更新版本中支援]</span><span class="sxs-lookup"><span data-stu-id="01f23-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="01f23-104">將方法新定義的中繼資料套用 `IMetadataEmit::Define*` 至指定的模組。</span><span class="sxs-lookup"><span data-stu-id="01f23-104">Applies the metadata newly defined by the `IMetadataEmit::Define*` methods to a specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01f23-105">語法</span><span class="sxs-lookup"><span data-stu-id="01f23-105">Syntax</span></span>  
  
```cpp
HRESULT ApplyMetaData(  
        [in] ModuleID moduleID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01f23-106">參數</span><span class="sxs-lookup"><span data-stu-id="01f23-106">Parameters</span></span>  

 `moduleID`  
 <span data-ttu-id="01f23-107">在其中繼資料已變更之模組的識別碼。</span><span class="sxs-lookup"><span data-stu-id="01f23-107">[in] The identifier of the module whose metadata was changed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01f23-108">備註</span><span class="sxs-lookup"><span data-stu-id="01f23-108">Remarks</span></span>  

 <span data-ttu-id="01f23-109">如果在 [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) 回呼之後進行中繼資料變更，您必須先呼叫這個方法，然後再使用新的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="01f23-109">If metadata changes are made after the [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback, you must call this method before using the new metadata.</span></span>  
  
 <span data-ttu-id="01f23-110">`ApplyMetaData` 僅支援新增下列類型的中繼資料：</span><span class="sxs-lookup"><span data-stu-id="01f23-110">`ApplyMetaData` only supports adding the following types of metadata:</span></span>  
  
- <span data-ttu-id="01f23-111">`AssemblyRef` 您藉由呼叫 IMetaDataAssemblyEmit 來建立的記錄 [：:D efineassemblyref](../metadata/imetadataassemblyemit-defineassemblyref-method.md)。</span><span class="sxs-lookup"><span data-stu-id="01f23-111">`AssemblyRef` records, which you create by calling the [IMetaDataAssemblyEmit::DefineAssemblyRef](../metadata/imetadataassemblyemit-defineassemblyref-method.md).</span></span> <span data-ttu-id="01f23-112">方法。</span><span class="sxs-lookup"><span data-stu-id="01f23-112">method.</span></span>  
  
- <span data-ttu-id="01f23-113">`TypeRef` 您藉由呼叫 [IMetaDataEmit：:D efinetyperefbyname](../metadata/imetadataemit-definetyperefbyname-method.md) 方法所建立的記錄。</span><span class="sxs-lookup"><span data-stu-id="01f23-113">`TypeRef` records, which you create by calling the [IMetaDataEmit::DefineTypeRefByName](../metadata/imetadataemit-definetyperefbyname-method.md) method.</span></span>  
  
- <span data-ttu-id="01f23-114">`TypeSpec` 您藉由呼叫 [IMetaDataEmit：： GetTokenFromTypeSpec](../metadata/imetadataemit-gettokenfromtypespec-method.md) 方法所建立的記錄。</span><span class="sxs-lookup"><span data-stu-id="01f23-114">`TypeSpec` records, which you create by calling the [IMetaDataEmit::GetTokenFromTypeSpec](../metadata/imetadataemit-gettokenfromtypespec-method.md) method.</span></span>  
  
- <span data-ttu-id="01f23-115">`MemberRef` 您藉由呼叫 [IMetaDataEmit：:D efinememberref](../metadata/imetadataemit-definememberref-method.md) 方法所建立的記錄。</span><span class="sxs-lookup"><span data-stu-id="01f23-115">`MemberRef` records, which you create by calling the [IMetaDataEmit::DefineMemberRef](../metadata/imetadataemit-definememberref-method.md) method.</span></span>  
  
- <span data-ttu-id="01f23-116">`MemberSpec` 您藉由呼叫 [IMetaDataEmit2：:D efinemethodspec](../metadata/imetadataemit2-definemethodspec-method.md) 方法所建立的記錄。</span><span class="sxs-lookup"><span data-stu-id="01f23-116">`MemberSpec` records, which you create by calling the [IMetaDataEmit2::DefineMethodSpec](../metadata/imetadataemit2-definemethodspec-method.md) method.</span></span>  
  
- <span data-ttu-id="01f23-117">`UserString` 您藉由呼叫 [IMetaDataEmit：:D efineuserstring](../metadata/imetadataemit-defineuserstring-method.md) 方法所建立的記錄。</span><span class="sxs-lookup"><span data-stu-id="01f23-117">`UserString` records, which you create by calling the [IMetaDataEmit::DefineUserString](../metadata/imetadataemit-defineuserstring-method.md) method.</span></span>  

<span data-ttu-id="01f23-118">從 .NET Core 3.0 開始， `ApplyMetaData` 也支援下列類型：</span><span class="sxs-lookup"><span data-stu-id="01f23-118">Starting with .NET Core 3.0, `ApplyMetaData` also supports the following types:</span></span>

- <span data-ttu-id="01f23-119">`TypeDef` 您藉由呼叫 [IMetaDataEmit：:D efinetypedef](../metadata/imetadataemit-definetypedef-method.md) 方法所建立的記錄。</span><span class="sxs-lookup"><span data-stu-id="01f23-119">`TypeDef` records, which you create by calling the [IMetaDataEmit::DefineTypeDef](../metadata/imetadataemit-definetypedef-method.md) method.</span></span>

- <span data-ttu-id="01f23-120">`MethodDef` 您藉由呼叫 [IMetaDataEmit：:D efinemethod](../metadata/imetadataemit-definemethod-method.md) 方法所建立的記錄。</span><span class="sxs-lookup"><span data-stu-id="01f23-120">`MethodDef` records, which you create by calling the [IMetaDataEmit::DefineMethod](../metadata/imetadataemit-definemethod-method.md) method.</span></span> <span data-ttu-id="01f23-121">但是，不支援將虛擬方法加入至現有的類型。</span><span class="sxs-lookup"><span data-stu-id="01f23-121">However, adding virtual methods to an existing type is not supported.</span></span> <span data-ttu-id="01f23-122">虛擬方法必須在 [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) 回呼之前新增。</span><span class="sxs-lookup"><span data-stu-id="01f23-122">Virtual methods must be added before the [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>

## <a name="requirements"></a><span data-ttu-id="01f23-123">需求</span><span class="sxs-lookup"><span data-stu-id="01f23-123">Requirements</span></span>  

 <span data-ttu-id="01f23-124">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="01f23-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01f23-125">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="01f23-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="01f23-126">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01f23-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01f23-127">**.NET Framework 版本：**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01f23-127">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01f23-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01f23-128">See also</span></span>

- [<span data-ttu-id="01f23-129">ICorProfilerInfo7 介面</span><span class="sxs-lookup"><span data-stu-id="01f23-129">ICorProfilerInfo7 Interface</span></span>](icorprofilerinfo7-interface.md)
