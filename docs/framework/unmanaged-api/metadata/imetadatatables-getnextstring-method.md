---
title: IMetaDataTables::GetNextString 方法
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextString
helpviewer_keywords:
- IMetaDataTables::GetNextString method [.NET Framework metadata]
- GetNextString method [.NET Framework metadata]
ms.assetid: d9720428-c353-4f07-a7e8-899e106a1b37
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4e7e7d89f4c994c5ce37dc09d15826185ed1bb25
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61779856"
---
# <a name="imetadatatablesgetnextstring-method"></a><span data-ttu-id="b3f0a-102">IMetaDataTables::GetNextString 方法</span><span class="sxs-lookup"><span data-stu-id="b3f0a-102">IMetaDataTables::GetNextString Method</span></span>
<span data-ttu-id="b3f0a-103">取得目前的資料表資料行中的下一個字串的索引。</span><span class="sxs-lookup"><span data-stu-id="b3f0a-103">Gets the index of the next string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3f0a-104">語法</span><span class="sxs-lookup"><span data-stu-id="b3f0a-104">Syntax</span></span>  
  
```  
HRESULT GetNextString (   
    [in]  ULONG   ixString,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3f0a-105">參數</span><span class="sxs-lookup"><span data-stu-id="b3f0a-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="b3f0a-106">[in]字串資料表資料行的索引值。</span><span class="sxs-lookup"><span data-stu-id="b3f0a-106">[in] The index value from a string table column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="b3f0a-107">[out]索引資料行中的下一個字串的指標。</span><span class="sxs-lookup"><span data-stu-id="b3f0a-107">[out] A pointer to the index of the next string in the column.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3f0a-108">需求</span><span class="sxs-lookup"><span data-stu-id="b3f0a-108">Requirements</span></span>  
 <span data-ttu-id="b3f0a-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b3f0a-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3f0a-110">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b3f0a-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b3f0a-111">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b3f0a-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b3f0a-112">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3f0a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3f0a-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b3f0a-113">See also</span></span>

- [<span data-ttu-id="b3f0a-114">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="b3f0a-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="b3f0a-115">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="b3f0a-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
