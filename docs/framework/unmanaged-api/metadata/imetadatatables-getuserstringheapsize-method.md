---
title: IMetaDataTables::GetUserStringHeapSize 方法
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetUserStringHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetUserStringHeapSize
helpviewer_keywords:
- IMetaDataTables::GetUserStringHeapSize method [.NET Framework metadata]
- GetUserStringHeapSize method [.NET Framework metadata]
ms.assetid: cba9e4d6-9461-4420-9614-96ff7039ec9c
topic_type:
- apiref
ms.openlocfilehash: 1aea017f17e29544e9288e1f57e6f84f9a2f6dae
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501101"
---
# <a name="imetadatatablesgetuserstringheapsize-method"></a><span data-ttu-id="6ac13-102">IMetaDataTables::GetUserStringHeapSize 方法</span><span class="sxs-lookup"><span data-stu-id="6ac13-102">IMetaDataTables::GetUserStringHeapSize Method</span></span>
<span data-ttu-id="6ac13-103">取得使用者字串堆積的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="6ac13-103">Gets the size, in bytes, of the user string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ac13-104">語法</span><span class="sxs-lookup"><span data-stu-id="6ac13-104">Syntax</span></span>  
  
```cpp  
HRESULT GetUserStringHeapSize (  
    [out] ULONG   *pcbBlobs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6ac13-105">參數</span><span class="sxs-lookup"><span data-stu-id="6ac13-105">Parameters</span></span>  
 `pcbBlobs`  
 <span data-ttu-id="6ac13-106">脫銷使用者字串堆積大小的指標，以位元組為單位。</span><span class="sxs-lookup"><span data-stu-id="6ac13-106">[out] A pointer to the size, in bytes, of the user string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ac13-107">規格需求</span><span class="sxs-lookup"><span data-stu-id="6ac13-107">Requirements</span></span>  
 <span data-ttu-id="6ac13-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6ac13-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ac13-109">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="6ac13-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6ac13-110">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="6ac13-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6ac13-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ac13-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ac13-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ac13-112">See also</span></span>

- [<span data-ttu-id="6ac13-113">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="6ac13-113">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="6ac13-114">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="6ac13-114">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
