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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8fe6559eca2fef1c9481c8996b19ffb8a08c6019
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080029"
---
# <a name="imetadatatablesgetstringheapsize-method"></a><span data-ttu-id="53ccb-102">IMetaDataTables::GetStringHeapSize 方法</span><span class="sxs-lookup"><span data-stu-id="53ccb-102">IMetaDataTables::GetStringHeapSize Method</span></span>
<span data-ttu-id="53ccb-103">取得大小，以位元組為單位對字串堆積。</span><span class="sxs-lookup"><span data-stu-id="53ccb-103">Gets the size, in bytes, of the string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53ccb-104">語法</span><span class="sxs-lookup"><span data-stu-id="53ccb-104">Syntax</span></span>  
  
```  
HRESULT GetStringHeapSize (  
    [out] ULONG   *pcbStrings  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="53ccb-105">參數</span><span class="sxs-lookup"><span data-stu-id="53ccb-105">Parameters</span></span>  
 `pcbStrings`  
 <span data-ttu-id="53ccb-106">[out]大小 （位元組），對字串堆積的指標。</span><span class="sxs-lookup"><span data-stu-id="53ccb-106">[out] A pointer to the size, in bytes, of the string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53ccb-107">需求</span><span class="sxs-lookup"><span data-stu-id="53ccb-107">Requirements</span></span>  
 <span data-ttu-id="53ccb-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="53ccb-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53ccb-109">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="53ccb-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="53ccb-110">**LIBRARY:** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="53ccb-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="53ccb-111">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="53ccb-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="53ccb-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53ccb-112">See also</span></span>

- [<span data-ttu-id="53ccb-113">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="53ccb-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="53ccb-114">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="53ccb-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
