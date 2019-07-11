---
title: ICorDebugAppDomain::GetModuleFromMetaDataInterface 方法
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetModuleFromMetaDataInterface
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetModuleFromMetaDataInterface
helpviewer_keywords:
- ICorDebugAppDomain::GetModuleFromMetaDatainterface method [.NET Framework debugging]
- GetModuleFromMetaDatainterface method [.NET Framework debugging]
ms.assetid: f35225b3-5dda-4d5a-913d-b3373e9ab81e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 48249bb634c301b7fda2c360c3b793e9206a759a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67737898"
---
# <a name="icordebugappdomaingetmodulefrommetadatainterface-method"></a><span data-ttu-id="b8ccd-102">ICorDebugAppDomain::GetModuleFromMetaDataInterface 方法</span><span class="sxs-lookup"><span data-stu-id="b8ccd-102">ICorDebugAppDomain::GetModuleFromMetaDataInterface Method</span></span>
<span data-ttu-id="b8ccd-103">取得對應於指定之中繼資料介面的模組。</span><span class="sxs-lookup"><span data-stu-id="b8ccd-103">Gets the module that corresponds to the given metadata interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8ccd-104">語法</span><span class="sxs-lookup"><span data-stu-id="b8ccd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleFromMetaDataInterface (  
    [in] IUnknown           *pIMetaData,  
    [out] ICorDebugModule  **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8ccd-105">參數</span><span class="sxs-lookup"><span data-stu-id="b8ccd-105">Parameters</span></span>  
 `pIMetaData`  
 <span data-ttu-id="b8ccd-106">[in]是其中一個物件的指標[中繼資料介面](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)。</span><span class="sxs-lookup"><span data-stu-id="b8ccd-106">[in] A pointer to an object that is one of the [Metadata interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span></span>  
  
 `ppModule`  
 <span data-ttu-id="b8ccd-107">[out]ICorDebugModule 物件，表示對應的模組指定的中繼資料介面的位址指標。</span><span class="sxs-lookup"><span data-stu-id="b8ccd-107">[out] A pointer to the address of an ICorDebugModule object that represents the module corresponding to the given metadata interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8ccd-108">需求</span><span class="sxs-lookup"><span data-stu-id="b8ccd-108">Requirements</span></span>  
 <span data-ttu-id="b8ccd-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b8ccd-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8ccd-110">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b8ccd-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b8ccd-111">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b8ccd-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8ccd-112">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8ccd-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
