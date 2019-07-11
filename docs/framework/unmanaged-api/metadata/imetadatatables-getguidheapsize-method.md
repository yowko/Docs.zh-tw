---
title: IMetaDataTables::GetGuidHeapSize 方法
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetGuidHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetGuidHeapSize
helpviewer_keywords:
- GetGuidHeapSize method [.NET Framework metadata]
- IMetaDataTables::GetGuidHeapSize method [.NET Framework metadata]
ms.assetid: e875cbee-1ad9-4f1a-bf03-38cdb8ff371a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0ddbd1c034708326d75c59f8ed4764156f617b81
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781488"
---
# <a name="imetadatatablesgetguidheapsize-method"></a><span data-ttu-id="25eff-102">IMetaDataTables::GetGuidHeapSize 方法</span><span class="sxs-lookup"><span data-stu-id="25eff-102">IMetaDataTables::GetGuidHeapSize Method</span></span>
<span data-ttu-id="25eff-103">取得大小，以位元組為單位，GUID 堆積。</span><span class="sxs-lookup"><span data-stu-id="25eff-103">Gets the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25eff-104">語法</span><span class="sxs-lookup"><span data-stu-id="25eff-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGuidHeapSize (  
    [out] ULONG   *pcbGuids  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25eff-105">參數</span><span class="sxs-lookup"><span data-stu-id="25eff-105">Parameters</span></span>  
 `pcbGuids`  
 <span data-ttu-id="25eff-106">[out]大小 （位元組），GUID 堆積的指標。</span><span class="sxs-lookup"><span data-stu-id="25eff-106">[out] A pointer to the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25eff-107">需求</span><span class="sxs-lookup"><span data-stu-id="25eff-107">Requirements</span></span>  
 <span data-ttu-id="25eff-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="25eff-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25eff-109">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="25eff-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="25eff-110">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="25eff-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="25eff-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25eff-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25eff-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25eff-112">See also</span></span>

- [<span data-ttu-id="25eff-113">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="25eff-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="25eff-114">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="25eff-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
