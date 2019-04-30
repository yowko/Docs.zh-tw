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
ms.openlocfilehash: 812794bc76d475c516effdc950ca6a0b877494c3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62042415"
---
# <a name="imetadatatablesgetguidheapsize-method"></a><span data-ttu-id="08901-102">IMetaDataTables::GetGuidHeapSize 方法</span><span class="sxs-lookup"><span data-stu-id="08901-102">IMetaDataTables::GetGuidHeapSize Method</span></span>
<span data-ttu-id="08901-103">取得大小，以位元組為單位，GUID 堆積。</span><span class="sxs-lookup"><span data-stu-id="08901-103">Gets the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08901-104">語法</span><span class="sxs-lookup"><span data-stu-id="08901-104">Syntax</span></span>  
  
```  
HRESULT GetGuidHeapSize (  
    [out] ULONG   *pcbGuids  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08901-105">參數</span><span class="sxs-lookup"><span data-stu-id="08901-105">Parameters</span></span>  
 `pcbGuids`  
 <span data-ttu-id="08901-106">[out]大小 （位元組），GUID 堆積的指標。</span><span class="sxs-lookup"><span data-stu-id="08901-106">[out] A pointer to the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08901-107">需求</span><span class="sxs-lookup"><span data-stu-id="08901-107">Requirements</span></span>  
 <span data-ttu-id="08901-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="08901-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08901-109">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="08901-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="08901-110">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="08901-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="08901-111">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08901-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08901-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="08901-112">See also</span></span>

- [<span data-ttu-id="08901-113">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="08901-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="08901-114">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="08901-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
