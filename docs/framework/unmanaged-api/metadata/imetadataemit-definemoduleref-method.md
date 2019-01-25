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
ms.openlocfilehash: 5f41eb1864ca2cc0640941abbbd8bc95801a0b31
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539008"
---
# <a name="imetadataemitdefinemoduleref-method"></a><span data-ttu-id="d6874-102">IMetaDataEmit::DefineModuleRef 方法</span><span class="sxs-lookup"><span data-stu-id="d6874-102">IMetaDataEmit::DefineModuleRef Method</span></span>
<span data-ttu-id="d6874-103">建立具有指定名稱的模組的中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="d6874-103">Creates the metadata signature for a module with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6874-104">語法</span><span class="sxs-lookup"><span data-stu-id="d6874-104">Syntax</span></span>  
  
```  
HRESULT DefineModuleRef (     
    [in]  LPCWSTR           szName,   
    [out] mdModuleRef       *pmur   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d6874-105">參數</span><span class="sxs-lookup"><span data-stu-id="d6874-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="d6874-106">[in]其他中繼資料檔案，通常是 DLL 名稱。</span><span class="sxs-lookup"><span data-stu-id="d6874-106">[in] The name of the other metadata file, typically a DLL.</span></span> <span data-ttu-id="d6874-107">這是檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="d6874-107">This is the file name only.</span></span> <span data-ttu-id="d6874-108">請勿使用完整路徑名稱。</span><span class="sxs-lookup"><span data-stu-id="d6874-108">Do not use a full path name.</span></span>  
  
 `pmur`  
 <span data-ttu-id="d6874-109">[out]指派`mdModuleRef`語彙基元。</span><span class="sxs-lookup"><span data-stu-id="d6874-109">[out] The assigned `mdModuleRef` token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6874-110">需求</span><span class="sxs-lookup"><span data-stu-id="d6874-110">Requirements</span></span>  
 <span data-ttu-id="d6874-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d6874-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6874-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d6874-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d6874-113">**程式庫：** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="d6874-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d6874-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6874-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6874-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d6874-115">See also</span></span>
- [<span data-ttu-id="d6874-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="d6874-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="d6874-117">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="d6874-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
