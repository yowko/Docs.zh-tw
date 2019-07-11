---
title: ICorDebugModule::GetToken 方法
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetToken
helpviewer_keywords:
- ICorDebugModule::GetToken method [.NET Framework debugging]
- GetToken method, ICorDebugModule interface [.NET Framework debugging]
ms.assetid: f759f87a-18ae-4c1a-8300-29b803432d0a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 30097ff0cd92253897a366a5a18f305eddb06b5b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763525"
---
# <a name="icordebugmodulegettoken-method"></a><span data-ttu-id="e4bda-102">ICorDebugModule::GetToken 方法</span><span class="sxs-lookup"><span data-stu-id="e4bda-102">ICorDebugModule::GetToken Method</span></span>
<span data-ttu-id="e4bda-103">取得資料表項目，此模組的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="e4bda-103">Gets the token for the table entry for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4bda-104">語法</span><span class="sxs-lookup"><span data-stu-id="e4bda-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken(  
    [out] mdModule *pToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4bda-105">參數</span><span class="sxs-lookup"><span data-stu-id="e4bda-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="e4bda-106">[out]指標`mdModule`參考模組的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="e4bda-106">[out] A pointer to the `mdModule` token that references the module's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4bda-107">備註</span><span class="sxs-lookup"><span data-stu-id="e4bda-107">Remarks</span></span>  
 <span data-ttu-id="e4bda-108">權杖可傳遞至[IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)， [IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)，並[IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)中繼資料匯入介面。</span><span class="sxs-lookup"><span data-stu-id="e4bda-108">The token can be passed to the [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md), [IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md), and [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) metadata import interfaces.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4bda-109">需求</span><span class="sxs-lookup"><span data-stu-id="e4bda-109">Requirements</span></span>  
 <span data-ttu-id="e4bda-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e4bda-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4bda-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e4bda-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e4bda-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e4bda-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e4bda-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4bda-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4bda-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4bda-114">See also</span></span>

- [<span data-ttu-id="e4bda-115">中繼資料</span><span class="sxs-lookup"><span data-stu-id="e4bda-115">Metadata</span></span>](../../../../docs/framework/unmanaged-api/metadata/index.md)
