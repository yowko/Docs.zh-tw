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
ms.openlocfilehash: c28182feff8e4b7d49b7d068da1496d44fa2f917
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59150354"
---
# <a name="icordebugmodulegettoken-method"></a><span data-ttu-id="5876a-102">ICorDebugModule::GetToken 方法</span><span class="sxs-lookup"><span data-stu-id="5876a-102">ICorDebugModule::GetToken Method</span></span>
<span data-ttu-id="5876a-103">取得資料表項目，此模組的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="5876a-103">Gets the token for the table entry for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5876a-104">語法</span><span class="sxs-lookup"><span data-stu-id="5876a-104">Syntax</span></span>  
  
```  
HRESULT GetToken(  
    [out] mdModule *pToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5876a-105">參數</span><span class="sxs-lookup"><span data-stu-id="5876a-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="5876a-106">[out]指標`mdModule`參考模組的中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="5876a-106">[out] A pointer to the `mdModule` token that references the module's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5876a-107">備註</span><span class="sxs-lookup"><span data-stu-id="5876a-107">Remarks</span></span>  
 <span data-ttu-id="5876a-108">權杖可傳遞至[IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)， [IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)，並[IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)中繼資料匯入介面。</span><span class="sxs-lookup"><span data-stu-id="5876a-108">The token can be passed to the [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md), [IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md), and [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) metadata import interfaces.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5876a-109">需求</span><span class="sxs-lookup"><span data-stu-id="5876a-109">Requirements</span></span>  
 <span data-ttu-id="5876a-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5876a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5876a-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5876a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5876a-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5876a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5876a-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5876a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5876a-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5876a-114">See also</span></span>

- [<span data-ttu-id="5876a-115">中繼資料</span><span class="sxs-lookup"><span data-stu-id="5876a-115">Metadata</span></span>](../../../../docs/framework/unmanaged-api/metadata/index.md)
