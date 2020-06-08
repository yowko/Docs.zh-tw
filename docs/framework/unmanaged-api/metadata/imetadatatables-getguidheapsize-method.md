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
ms.openlocfilehash: 71a75defa72e4fe3594b4d0ceff45273b3a35395
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490350"
---
# <a name="imetadatatablesgetguidheapsize-method"></a><span data-ttu-id="16252-102">IMetaDataTables::GetGuidHeapSize 方法</span><span class="sxs-lookup"><span data-stu-id="16252-102">IMetaDataTables::GetGuidHeapSize Method</span></span>
<span data-ttu-id="16252-103">取得 GUID 堆積的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="16252-103">Gets the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16252-104">語法</span><span class="sxs-lookup"><span data-stu-id="16252-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGuidHeapSize (  
    [out] ULONG   *pcbGuids  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16252-105">參數</span><span class="sxs-lookup"><span data-stu-id="16252-105">Parameters</span></span>  
 `pcbGuids`  
 <span data-ttu-id="16252-106">脫銷GUID 堆積大小的指標，以位元組為單位。</span><span class="sxs-lookup"><span data-stu-id="16252-106">[out] A pointer to the size, in bytes, of the GUID heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16252-107">規格需求</span><span class="sxs-lookup"><span data-stu-id="16252-107">Requirements</span></span>  
 <span data-ttu-id="16252-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="16252-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16252-109">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="16252-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="16252-110">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="16252-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="16252-111">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16252-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16252-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16252-112">See also</span></span>

- [<span data-ttu-id="16252-113">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="16252-113">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="16252-114">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="16252-114">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
