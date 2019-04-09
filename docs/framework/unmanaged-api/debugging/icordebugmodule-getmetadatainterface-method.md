---
title: ICorDebugModule::GetMetaDataInterface 方法
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetMetaDataInterface
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetMetaDataInterface
helpviewer_keywords:
- ICorDebugModule::GetMetaDatainterface method [.NET Framework debugging]
- GetMetaDatainterface method [.NET Framework debugging]
ms.assetid: 30d906f2-cf35-4fa9-9d4c-0c31b58c9f3a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 37710fbb7acc50b80d7acebe4194b019c0b64660
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102592"
---
# <a name="icordebugmodulegetmetadatainterface-method"></a><span data-ttu-id="67ebb-102">ICorDebugModule::GetMetaDataInterface 方法</span><span class="sxs-lookup"><span data-stu-id="67ebb-102">ICorDebugModule::GetMetaDataInterface Method</span></span>
<span data-ttu-id="67ebb-103">取得可用來檢查模組的中繼資料的中繼資料介面物件。</span><span class="sxs-lookup"><span data-stu-id="67ebb-103">Gets a metadata interface object that can be used to examine the metadata for the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67ebb-104">語法</span><span class="sxs-lookup"><span data-stu-id="67ebb-104">Syntax</span></span>  
  
```  
HRESULT GetMetaDataInterface (  
    [in] REFIID      riid,  
    [out] IUnknown **ppObj  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67ebb-105">參數</span><span class="sxs-lookup"><span data-stu-id="67ebb-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="67ebb-106">[in]指定的中繼資料介面的參考識別碼。</span><span class="sxs-lookup"><span data-stu-id="67ebb-106">[in] The reference ID that specifies the metadata interface.</span></span>  
  
 `ppObj`  
 <span data-ttu-id="67ebb-107">[out]位址指標`T:IUnknown`物件，其中[中繼資料介面](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)。</span><span class="sxs-lookup"><span data-stu-id="67ebb-107">[out] A pointer to the address of an `T:IUnknown` object that is one of the [metadata interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67ebb-108">備註</span><span class="sxs-lookup"><span data-stu-id="67ebb-108">Remarks</span></span>  
 <span data-ttu-id="67ebb-109">偵錯工具可以使用`GetMetaDataInterface`方法來建立一份模組，它必須執行才能編輯該模組的原始中繼資料。</span><span class="sxs-lookup"><span data-stu-id="67ebb-109">The debugger can use the `GetMetaDataInterface` method to make a copy of the original metadata for a module, which it must do in order to edit that module.</span></span> <span data-ttu-id="67ebb-110">偵錯工具呼叫`GetMetaDataInterface`以取得[IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)介面物件模組，然後呼叫[imetadataemit:: Savetomemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md)到模組的中繼資料的副本儲存到記憶體。</span><span class="sxs-lookup"><span data-stu-id="67ebb-110">The debugger calls `GetMetaDataInterface` to get an [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface object for the module, then calls [IMetaDataEmit::SaveToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md) to save a copy of the module's metadata to memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67ebb-111">需求</span><span class="sxs-lookup"><span data-stu-id="67ebb-111">Requirements</span></span>  
 <span data-ttu-id="67ebb-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="67ebb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67ebb-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="67ebb-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="67ebb-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="67ebb-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="67ebb-115">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="67ebb-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="67ebb-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67ebb-116">See also</span></span>

- [<span data-ttu-id="67ebb-117">中繼資料</span><span class="sxs-lookup"><span data-stu-id="67ebb-117">Metadata</span></span>](../../../../docs/framework/unmanaged-api/metadata/index.md)
