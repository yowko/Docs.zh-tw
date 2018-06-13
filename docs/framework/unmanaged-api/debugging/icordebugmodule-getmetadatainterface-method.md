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
ms.openlocfilehash: fef23f2b128b1e5393c5104b6e33758882b34882
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420878"
---
# <a name="icordebugmodulegetmetadatainterface-method"></a><span data-ttu-id="035bb-102">ICorDebugModule::GetMetaDataInterface 方法</span><span class="sxs-lookup"><span data-stu-id="035bb-102">ICorDebugModule::GetMetaDataInterface Method</span></span>
<span data-ttu-id="035bb-103">取得可以用來檢查模組的中繼資料的中繼資料介面物件。</span><span class="sxs-lookup"><span data-stu-id="035bb-103">Gets a metadata interface object that can be used to examine the metadata for the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="035bb-104">語法</span><span class="sxs-lookup"><span data-stu-id="035bb-104">Syntax</span></span>  
  
```  
HRESULT GetMetaDataInterface (  
    [in] REFIID      riid,  
    [out] IUnknown **ppObj  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="035bb-105">參數</span><span class="sxs-lookup"><span data-stu-id="035bb-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="035bb-106">[in]指定的中繼資料介面的參考識別碼。</span><span class="sxs-lookup"><span data-stu-id="035bb-106">[in] The reference ID that specifies the metadata interface.</span></span>  
  
 `ppObj`  
 <span data-ttu-id="035bb-107">[out]位址指標`T:IUnknown`物件的其中一個[中繼資料介面](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)。</span><span class="sxs-lookup"><span data-stu-id="035bb-107">[out] A pointer to the address of an `T:IUnknown` object that is one of the [metadata interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="035bb-108">備註</span><span class="sxs-lookup"><span data-stu-id="035bb-108">Remarks</span></span>  
 <span data-ttu-id="035bb-109">偵錯工具可以使用`GetMetaDataInterface`方法來建立模組，則必須執行才能編輯該模組的原始中繼資料的副本。</span><span class="sxs-lookup"><span data-stu-id="035bb-109">The debugger can use the `GetMetaDataInterface` method to make a copy of the original metadata for a module, which it must do in order to edit that module.</span></span> <span data-ttu-id="035bb-110">偵錯工具呼叫`GetMetaDataInterface`取得[IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)介面物件模組，然後呼叫[imetadataemit:: Savetomemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md)模組的中繼資料的副本儲存至記憶體。</span><span class="sxs-lookup"><span data-stu-id="035bb-110">The debugger calls `GetMetaDataInterface` to get an [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface object for the module, then calls [IMetaDataEmit::SaveToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md) to save a copy of the module's metadata to memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="035bb-111">需求</span><span class="sxs-lookup"><span data-stu-id="035bb-111">Requirements</span></span>  
 <span data-ttu-id="035bb-112">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="035bb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="035bb-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="035bb-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="035bb-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="035bb-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="035bb-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="035bb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="035bb-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="035bb-116">See Also</span></span>  
 [<span data-ttu-id="035bb-117">中繼資料</span><span class="sxs-lookup"><span data-stu-id="035bb-117">Metadata</span></span>](../../../../docs/framework/unmanaged-api/metadata/index.md)
