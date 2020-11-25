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
ms.openlocfilehash: e508bcae15e72ce592529cf4b68af5d75ea49038
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721955"
---
# <a name="imetadatatablesgetblobheapsize-method"></a><span data-ttu-id="72402-102">IMetaDataTables::GetBlobHeapSize 方法</span><span class="sxs-lookup"><span data-stu-id="72402-102">IMetaDataTables::GetBlobHeapSize Method</span></span>

<span data-ttu-id="72402-103">取得二進位大型物件 (BLOB) 堆積的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="72402-103">Gets the size, in bytes, of the binary large object (BLOB) heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72402-104">語法</span><span class="sxs-lookup"><span data-stu-id="72402-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBlobHeapSize (  
    [out] ULONG     *pcbBlobs  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="72402-105">參數</span><span class="sxs-lookup"><span data-stu-id="72402-105">Parameters</span></span>  

 `pcbBlobs`  
 <span data-ttu-id="72402-106">擴展BLOB 堆積大小的指標，以位元組為單位。</span><span class="sxs-lookup"><span data-stu-id="72402-106">[out] A pointer to the size, in bytes, of the BLOB heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72402-107">需求</span><span class="sxs-lookup"><span data-stu-id="72402-107">Requirements</span></span>  

 <span data-ttu-id="72402-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="72402-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72402-109">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="72402-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="72402-110">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="72402-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="72402-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72402-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72402-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72402-112">See also</span></span>

- [<span data-ttu-id="72402-113">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="72402-113">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="72402-114">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="72402-114">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
