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
ms.openlocfilehash: fb96949e22b4edfc0e64780a54bb38da44eb8369
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129554"
---
# <a name="icordebugmodulegetmetadatainterface-method"></a><span data-ttu-id="62c7e-102">ICorDebugModule::GetMetaDataInterface 方法</span><span class="sxs-lookup"><span data-stu-id="62c7e-102">ICorDebugModule::GetMetaDataInterface Method</span></span>
<span data-ttu-id="62c7e-103">取得可用於檢查模組中繼資料的中繼資料介面物件。</span><span class="sxs-lookup"><span data-stu-id="62c7e-103">Gets a metadata interface object that can be used to examine the metadata for the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62c7e-104">語法</span><span class="sxs-lookup"><span data-stu-id="62c7e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataInterface (  
    [in] REFIID      riid,  
    [out] IUnknown **ppObj  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="62c7e-105">參數</span><span class="sxs-lookup"><span data-stu-id="62c7e-105">Parameters</span></span>  
 `riid`  
 <span data-ttu-id="62c7e-106">在指定中繼資料介面的參考識別碼。</span><span class="sxs-lookup"><span data-stu-id="62c7e-106">[in] The reference ID that specifies the metadata interface.</span></span>  
  
 `ppObj`  
 <span data-ttu-id="62c7e-107">脫銷屬於其中一個[中繼資料介面](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)之 `T:IUnknown` 物件的位址指標。</span><span class="sxs-lookup"><span data-stu-id="62c7e-107">[out] A pointer to the address of an `T:IUnknown` object that is one of the [metadata interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62c7e-108">備註</span><span class="sxs-lookup"><span data-stu-id="62c7e-108">Remarks</span></span>  
 <span data-ttu-id="62c7e-109">偵錯工具可以使用 `GetMetaDataInterface` 方法，針對模組建立原始中繼資料的複本，它必須執行此操作才能編輯該模組。</span><span class="sxs-lookup"><span data-stu-id="62c7e-109">The debugger can use the `GetMetaDataInterface` method to make a copy of the original metadata for a module, which it must do in order to edit that module.</span></span> <span data-ttu-id="62c7e-110">偵錯工具會呼叫 `GetMetaDataInterface` 來取得模組的[IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)介面物件，然後呼叫[IMetaDataEmit：： SaveToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md) ，將模組的中繼資料複本儲存至記憶體。</span><span class="sxs-lookup"><span data-stu-id="62c7e-110">The debugger calls `GetMetaDataInterface` to get an [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) interface object for the module, then calls [IMetaDataEmit::SaveToMemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md) to save a copy of the module's metadata to memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62c7e-111">需求</span><span class="sxs-lookup"><span data-stu-id="62c7e-111">Requirements</span></span>  
 <span data-ttu-id="62c7e-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="62c7e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62c7e-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="62c7e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="62c7e-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="62c7e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62c7e-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62c7e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62c7e-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="62c7e-116">See also</span></span>

- [<span data-ttu-id="62c7e-117">中繼資料</span><span class="sxs-lookup"><span data-stu-id="62c7e-117">Metadata</span></span>](../../../../docs/framework/unmanaged-api/metadata/index.md)
