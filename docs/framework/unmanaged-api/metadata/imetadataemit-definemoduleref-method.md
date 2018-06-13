---
title: IMetaDataEmit::DefineModuleRef 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineModuleRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineModuleRef
helpviewer_keywords:
- DefineModuleRef method [.NET Framework metadata]
- IMetaDataEmit::DefineModuleRef method [.NET Framework metadata]
ms.assetid: f2833594-d90b-4a71-9a53-34b12470c64a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4503c3c745fde148c77ff30c9ece008dd9d54829
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445792"
---
# <a name="imetadataemitdefinemoduleref-method"></a><span data-ttu-id="99fbd-102">IMetaDataEmit::DefineModuleRef 方法</span><span class="sxs-lookup"><span data-stu-id="99fbd-102">IMetaDataEmit::DefineModuleRef Method</span></span>
<span data-ttu-id="99fbd-103">建立具有指定名稱的模組的中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="99fbd-103">Creates the metadata signature for a module with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99fbd-104">語法</span><span class="sxs-lookup"><span data-stu-id="99fbd-104">Syntax</span></span>  
  
```  
HRESULT DefineModuleRef (     
    [in]  LPCWSTR           szName,   
    [out] mdModuleRef       *pmur   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="99fbd-105">參數</span><span class="sxs-lookup"><span data-stu-id="99fbd-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="99fbd-106">[in]其他中繼資料檔案，通常是 DLL 名稱。</span><span class="sxs-lookup"><span data-stu-id="99fbd-106">[in] The name of the other metadata file, typically a DLL.</span></span> <span data-ttu-id="99fbd-107">這是檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="99fbd-107">This is the file name only.</span></span> <span data-ttu-id="99fbd-108">請勿使用完整路徑名稱。</span><span class="sxs-lookup"><span data-stu-id="99fbd-108">Do not use a full path name.</span></span>  
  
 `pmur`  
 <span data-ttu-id="99fbd-109">[out]受指派`mdModuleRef`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="99fbd-109">[out] The assigned `mdModuleRef` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99fbd-110">需求</span><span class="sxs-lookup"><span data-stu-id="99fbd-110">Requirements</span></span>  
 <span data-ttu-id="99fbd-111">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="99fbd-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99fbd-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="99fbd-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="99fbd-113">**程式庫：** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="99fbd-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="99fbd-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99fbd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99fbd-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99fbd-115">See Also</span></span>  
 [<span data-ttu-id="99fbd-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="99fbd-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="99fbd-117">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="99fbd-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
