---
title: IMetaDataTables::GetNextBlob 方法
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextBlob
helpviewer_keywords:
- IMetaDataTables::GetNextBlob method [.NET Framework metadata]
- GetNextBlob method [.NET Framework metadata]
ms.assetid: 017c8ab4-4c09-4754-9935-5b0b49cabecb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: caf7faeea4bcec9b73f3c43f0923d308baebf6d0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447616"
---
# <a name="imetadatatablesgetnextblob-method"></a><span data-ttu-id="7a06d-102">IMetaDataTables::GetNextBlob 方法</span><span class="sxs-lookup"><span data-stu-id="7a06d-102">IMetaDataTables::GetNextBlob Method</span></span>
<span data-ttu-id="7a06d-103">取得資料表中的下一個二進位大型物件 (BLOB) 的索引。</span><span class="sxs-lookup"><span data-stu-id="7a06d-103">Gets the index of the next binary large object (BLOB) in the table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a06d-104">語法</span><span class="sxs-lookup"><span data-stu-id="7a06d-104">Syntax</span></span>  
  
```  
HRESULT GetNextBlob (  
    [in]  ULONG   ixBlob,  
    [out] ULONG   *pNext  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7a06d-105">參數</span><span class="sxs-lookup"><span data-stu-id="7a06d-105">Parameters</span></span>  
 `ixBlob`  
 <span data-ttu-id="7a06d-106">[in]索引中，傳回的資料行的 Blob。</span><span class="sxs-lookup"><span data-stu-id="7a06d-106">[in] The index, as returned from a column of BLOBs.</span></span>  
  
 `pNext`  
 <span data-ttu-id="7a06d-107">[out]索引的下一個 BLOB 的指標。</span><span class="sxs-lookup"><span data-stu-id="7a06d-107">[out] A pointer to the index of the next BLOB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a06d-108">需求</span><span class="sxs-lookup"><span data-stu-id="7a06d-108">Requirements</span></span>  
 <span data-ttu-id="7a06d-109">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7a06d-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a06d-110">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7a06d-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7a06d-111">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="7a06d-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7a06d-112">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a06d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a06d-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a06d-113">See Also</span></span>  
 [<span data-ttu-id="7a06d-114">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="7a06d-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="7a06d-115">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="7a06d-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
