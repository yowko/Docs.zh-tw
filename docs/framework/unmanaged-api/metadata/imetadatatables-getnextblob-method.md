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
ms.openlocfilehash: 086448248364403b718408ad8bd32e48447742d0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490377"
---
# <a name="imetadatatablesgetnextblob-method"></a><span data-ttu-id="ae6ee-102">IMetaDataTables::GetNextBlob 方法</span><span class="sxs-lookup"><span data-stu-id="ae6ee-102">IMetaDataTables::GetNextBlob Method</span></span>
<span data-ttu-id="ae6ee-103">取得資料表中下一個二進位大型物件（BLOB）的索引。</span><span class="sxs-lookup"><span data-stu-id="ae6ee-103">Gets the index of the next binary large object (BLOB) in the table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae6ee-104">語法</span><span class="sxs-lookup"><span data-stu-id="ae6ee-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextBlob (  
    [in]  ULONG   ixBlob,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae6ee-105">參數</span><span class="sxs-lookup"><span data-stu-id="ae6ee-105">Parameters</span></span>  
 `ixBlob`  
 <span data-ttu-id="ae6ee-106">在從 Blob 的資料行傳回的索引。</span><span class="sxs-lookup"><span data-stu-id="ae6ee-106">[in] The index, as returned from a column of BLOBs.</span></span>  
  
 `pNext`  
 <span data-ttu-id="ae6ee-107">脫銷下一個 BLOB 之索引的指標。</span><span class="sxs-lookup"><span data-stu-id="ae6ee-107">[out] A pointer to the index of the next BLOB.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae6ee-108">規格需求</span><span class="sxs-lookup"><span data-stu-id="ae6ee-108">Requirements</span></span>  
 <span data-ttu-id="ae6ee-109">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ae6ee-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae6ee-110">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="ae6ee-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ae6ee-111">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="ae6ee-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ae6ee-112">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae6ee-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae6ee-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae6ee-113">See also</span></span>

- [<span data-ttu-id="ae6ee-114">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="ae6ee-114">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="ae6ee-115">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="ae6ee-115">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
