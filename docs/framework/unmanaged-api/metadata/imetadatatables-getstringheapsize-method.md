---
title: IMetaDataTables::GetStringHeapSize 方法
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetStringHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetStringHeapSize
helpviewer_keywords:
- IMetaDataTables::GetStringHeapSize method [.NET Framework metadata]
- GetStringHeapSize method [.NET Framework metadata]
ms.assetid: ed8f6335-81f5-4c09-81a9-2a909fc530c9
topic_type:
- apiref
ms.openlocfilehash: 43599a7e39ca4cc9d27dab43a948dc2f04e5010a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426668"
---
# <a name="imetadatatablesgetstringheapsize-method"></a><span data-ttu-id="6bc4d-102">IMetaDataTables::GetStringHeapSize 方法</span><span class="sxs-lookup"><span data-stu-id="6bc4d-102">IMetaDataTables::GetStringHeapSize Method</span></span>
<span data-ttu-id="6bc4d-103">取得字串堆積的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="6bc4d-103">Gets the size, in bytes, of the string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bc4d-104">語法</span><span class="sxs-lookup"><span data-stu-id="6bc4d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStringHeapSize (  
    [out] ULONG   *pcbStrings  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6bc4d-105">參數</span><span class="sxs-lookup"><span data-stu-id="6bc4d-105">Parameters</span></span>  
 `pcbStrings`  
 <span data-ttu-id="6bc4d-106">脫銷字串堆積大小的指標，以位元組為單位。</span><span class="sxs-lookup"><span data-stu-id="6bc4d-106">[out] A pointer to the size, in bytes, of the string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bc4d-107">需求</span><span class="sxs-lookup"><span data-stu-id="6bc4d-107">Requirements</span></span>  
 <span data-ttu-id="6bc4d-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6bc4d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bc4d-109">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="6bc4d-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6bc4d-110">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="6bc4d-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6bc4d-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bc4d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bc4d-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="6bc4d-112">See also</span></span>

- [<span data-ttu-id="6bc4d-113">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="6bc4d-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="6bc4d-114">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="6bc4d-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
