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
ms.openlocfilehash: cf455b3fb34d8eed78ffaadffad621062c2b9b22
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443490"
---
# <a name="imetadatatablesgetguidheapsize-method"></a><span data-ttu-id="a7e46-102">IMetaDataTables::GetGuidHeapSize 方法</span><span class="sxs-lookup"><span data-stu-id="a7e46-102">IMetaDataTables::GetGuidHeapSize Method</span></span>
<span data-ttu-id="a7e46-103">取得 GUID 堆積的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="a7e46-103">Gets the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7e46-104">語法</span><span class="sxs-lookup"><span data-stu-id="a7e46-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGuidHeapSize (  
    [out] ULONG   *pcbGuids  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7e46-105">參數</span><span class="sxs-lookup"><span data-stu-id="a7e46-105">Parameters</span></span>  
 `pcbGuids`  
 <span data-ttu-id="a7e46-106">脫銷GUID 堆積大小的指標，以位元組為單位。</span><span class="sxs-lookup"><span data-stu-id="a7e46-106">[out] A pointer to the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7e46-107">需求</span><span class="sxs-lookup"><span data-stu-id="a7e46-107">Requirements</span></span>  
 <span data-ttu-id="a7e46-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a7e46-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7e46-109">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="a7e46-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a7e46-110">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="a7e46-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a7e46-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7e46-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7e46-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="a7e46-112">See also</span></span>

- [<span data-ttu-id="a7e46-113">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="a7e46-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="a7e46-114">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="a7e46-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
