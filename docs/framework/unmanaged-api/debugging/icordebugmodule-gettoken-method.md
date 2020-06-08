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
ms.openlocfilehash: 1cf4d82200709971201da60d06d0cb929641a104
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501881"
---
# <a name="icordebugmodulegettoken-method"></a><span data-ttu-id="91e82-102">ICorDebugModule::GetToken 方法</span><span class="sxs-lookup"><span data-stu-id="91e82-102">ICorDebugModule::GetToken Method</span></span>
<span data-ttu-id="91e82-103">取得此模組之資料表專案的 token。</span><span class="sxs-lookup"><span data-stu-id="91e82-103">Gets the token for the table entry for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91e82-104">語法</span><span class="sxs-lookup"><span data-stu-id="91e82-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken(  
    [out] mdModule *pToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91e82-105">參數</span><span class="sxs-lookup"><span data-stu-id="91e82-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="91e82-106">脫銷`mdModule`參考模組中繼資料之標記的指標。</span><span class="sxs-lookup"><span data-stu-id="91e82-106">[out] A pointer to the `mdModule` token that references the module's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91e82-107">備註</span><span class="sxs-lookup"><span data-stu-id="91e82-107">Remarks</span></span>  
 <span data-ttu-id="91e82-108">Token 可以傳遞至[IMetaDataImport](../metadata/imetadataimport-interface.md)、 [IMetaDataImport2](../metadata/imetadataimport2-interface.md)和[IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md)中繼資料匯入介面。</span><span class="sxs-lookup"><span data-stu-id="91e82-108">The token can be passed to the [IMetaDataImport](../metadata/imetadataimport-interface.md), [IMetaDataImport2](../metadata/imetadataimport2-interface.md), and [IMetaDataAssemblyImport](../metadata/imetadataassemblyimport-interface.md) metadata import interfaces.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91e82-109">規格需求</span><span class="sxs-lookup"><span data-stu-id="91e82-109">Requirements</span></span>  
 <span data-ttu-id="91e82-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="91e82-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91e82-111">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="91e82-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="91e82-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="91e82-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91e82-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91e82-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91e82-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91e82-114">See also</span></span>

- [<span data-ttu-id="91e82-115">中繼資料</span><span class="sxs-lookup"><span data-stu-id="91e82-115">Metadata</span></span>](../metadata/index.md)
