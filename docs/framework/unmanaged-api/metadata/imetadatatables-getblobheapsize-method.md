---
title: IMetaDataTables::GetBlobHeapSize 方法
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetBlobHeapSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetBlobHeapSize
helpviewer_keywords:
- GetBlobHeapSize method [.NET Framework metadata]
- IMetaDataTables::GetBlobHeapSize method [.NET Framework metadata]
ms.assetid: 6330a9ee-8cd5-4299-86f1-b4de2c701a0d
topic_type:
- apiref
ms.openlocfilehash: 68e29e932e477f286db00b0c989a3346bd13c9bc
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501218"
---
# <a name="imetadatatablesgetblobheapsize-method"></a><span data-ttu-id="ce4fc-102">IMetaDataTables::GetBlobHeapSize 方法</span><span class="sxs-lookup"><span data-stu-id="ce4fc-102">IMetaDataTables::GetBlobHeapSize Method</span></span>
<span data-ttu-id="ce4fc-103">取得二進位大型物件（BLOB）堆積的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="ce4fc-103">Gets the size, in bytes, of the binary large object (BLOB) heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce4fc-104">語法</span><span class="sxs-lookup"><span data-stu-id="ce4fc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBlobHeapSize (  
    [out] ULONG     *pcbBlobs  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="ce4fc-105">參數</span><span class="sxs-lookup"><span data-stu-id="ce4fc-105">Parameters</span></span>  
 `pcbBlobs`  
 <span data-ttu-id="ce4fc-106">脫銷BLOB 堆積大小的指標（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="ce4fc-106">[out] A pointer to the size, in bytes, of the BLOB heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce4fc-107">規格需求</span><span class="sxs-lookup"><span data-stu-id="ce4fc-107">Requirements</span></span>  
 <span data-ttu-id="ce4fc-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ce4fc-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce4fc-109">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="ce4fc-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ce4fc-110">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="ce4fc-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ce4fc-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce4fc-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce4fc-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce4fc-112">See also</span></span>

- [<span data-ttu-id="ce4fc-113">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="ce4fc-113">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="ce4fc-114">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="ce4fc-114">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
