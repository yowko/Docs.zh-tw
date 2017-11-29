---
title: "ICorDebugModule::GetToken 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.GetToken
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::GetToken
helpviewer_keywords:
- ICorDebugModule::GetToken method [.NET Framework debugging]
- GetToken method, ICorDebugModule interface [.NET Framework debugging]
ms.assetid: f759f87a-18ae-4c1a-8300-29b803432d0a
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c06c4c8ac937864748cbac8872de9b3994db2464
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmodulegettoken-method"></a><span data-ttu-id="01841-102">ICorDebugModule::GetToken 方法</span><span class="sxs-lookup"><span data-stu-id="01841-102">ICorDebugModule::GetToken Method</span></span>
<span data-ttu-id="01841-103">取得表格項目，此模組中的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="01841-103">Gets the token for the table entry for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01841-104">語法</span><span class="sxs-lookup"><span data-stu-id="01841-104">Syntax</span></span>  
  
```  
HRESULT GetToken(  
    [out] mdModule *pToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="01841-105">參數</span><span class="sxs-lookup"><span data-stu-id="01841-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="01841-106">[out]指標`mdModule`語彙基元所參考模組的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="01841-106">[out] A pointer to the `mdModule` token that references the module's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01841-107">備註</span><span class="sxs-lookup"><span data-stu-id="01841-107">Remarks</span></span>  
 <span data-ttu-id="01841-108">語彙基元可以傳遞至[IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)， [IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)，和[IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)中繼資料匯入介面。</span><span class="sxs-lookup"><span data-stu-id="01841-108">The token can be passed to the [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md), [IMetaDataImport2](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md), and [IMetaDataAssemblyImport](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) metadata import interfaces.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01841-109">需求</span><span class="sxs-lookup"><span data-stu-id="01841-109">Requirements</span></span>  
 <span data-ttu-id="01841-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="01841-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01841-111">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="01841-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="01841-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="01841-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01841-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01841-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01841-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01841-114">See Also</span></span>  
 [<span data-ttu-id="01841-115">中繼資料</span><span class="sxs-lookup"><span data-stu-id="01841-115">Metadata</span></span>](../../../../docs/framework/unmanaged-api/metadata/index.md)
