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
ms.openlocfilehash: 1aa7853602c1aaf484ef89d9c4fb06464e135f80
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501154"
---
# <a name="imetadatatablesgetstringheapsize-method"></a><span data-ttu-id="d3fdb-102">IMetaDataTables::GetStringHeapSize 方法</span><span class="sxs-lookup"><span data-stu-id="d3fdb-102">IMetaDataTables::GetStringHeapSize Method</span></span>
<span data-ttu-id="d3fdb-103">取得字串堆積的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="d3fdb-103">Gets the size, in bytes, of the string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3fdb-104">語法</span><span class="sxs-lookup"><span data-stu-id="d3fdb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStringHeapSize (  
    [out] ULONG   *pcbStrings  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3fdb-105">參數</span><span class="sxs-lookup"><span data-stu-id="d3fdb-105">Parameters</span></span>  
 `pcbStrings`  
 <span data-ttu-id="d3fdb-106">脫銷字串堆積大小的指標，以位元組為單位。</span><span class="sxs-lookup"><span data-stu-id="d3fdb-106">[out] A pointer to the size, in bytes, of the string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3fdb-107">規格需求</span><span class="sxs-lookup"><span data-stu-id="d3fdb-107">Requirements</span></span>  
 <span data-ttu-id="d3fdb-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d3fdb-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3fdb-109">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="d3fdb-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d3fdb-110">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="d3fdb-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d3fdb-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3fdb-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3fdb-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3fdb-112">See also</span></span>

- [<span data-ttu-id="d3fdb-113">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="d3fdb-113">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="d3fdb-114">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="d3fdb-114">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
