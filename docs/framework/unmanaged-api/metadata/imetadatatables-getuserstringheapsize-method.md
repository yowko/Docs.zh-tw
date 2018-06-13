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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a217a835e258052ace5b59a70cbc0fa31691d78e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452842"
---
# <a name="imetadatatablesgetuserstringheapsize-method"></a><span data-ttu-id="b6e6e-102">IMetaDataTables::GetUserStringHeapSize 方法</span><span class="sxs-lookup"><span data-stu-id="b6e6e-102">IMetaDataTables::GetUserStringHeapSize Method</span></span>
<span data-ttu-id="b6e6e-103">取得以位元組為單位的使用者字串堆積的大小。</span><span class="sxs-lookup"><span data-stu-id="b6e6e-103">Gets the size, in bytes, of the user string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6e6e-104">語法</span><span class="sxs-lookup"><span data-stu-id="b6e6e-104">Syntax</span></span>  
  
```  
HRESULT GetUserStringHeapSize (  
    [out] ULONG   *pcbBlobs  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b6e6e-105">參數</span><span class="sxs-lookup"><span data-stu-id="b6e6e-105">Parameters</span></span>  
 `pcbBlobs`  
 <span data-ttu-id="b6e6e-106">[out]大小，以位元組為單位，使用者字串堆積的指標。</span><span class="sxs-lookup"><span data-stu-id="b6e6e-106">[out] A pointer to the size, in bytes, of the user string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6e6e-107">需求</span><span class="sxs-lookup"><span data-stu-id="b6e6e-107">Requirements</span></span>  
 <span data-ttu-id="b6e6e-108">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b6e6e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6e6e-109">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b6e6e-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b6e6e-110">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="b6e6e-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b6e6e-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6e6e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6e6e-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6e6e-112">See Also</span></span>  
 [<span data-ttu-id="b6e6e-113">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="b6e6e-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="b6e6e-114">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="b6e6e-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
