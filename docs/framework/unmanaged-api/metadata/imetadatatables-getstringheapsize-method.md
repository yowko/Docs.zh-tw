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
ms.openlocfilehash: 1d814a741bc88bb50bfe9ddc3db57635a7266a82
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449916"
---
# <a name="imetadatatablesgetstringheapsize-method"></a><span data-ttu-id="abbde-102">IMetaDataTables::GetStringHeapSize 方法</span><span class="sxs-lookup"><span data-stu-id="abbde-102">IMetaDataTables::GetStringHeapSize Method</span></span>
<span data-ttu-id="abbde-103">取得大小，單位為位元組字串堆積。</span><span class="sxs-lookup"><span data-stu-id="abbde-103">Gets the size, in bytes, of the string heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abbde-104">語法</span><span class="sxs-lookup"><span data-stu-id="abbde-104">Syntax</span></span>  
  
```  
HRESULT GetStringHeapSize (  
    [out] ULONG   *pcbStrings  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="abbde-105">參數</span><span class="sxs-lookup"><span data-stu-id="abbde-105">Parameters</span></span>  
 `pcbStrings`  
 <span data-ttu-id="abbde-106">[out]大小，單位為位元組字串堆積的指標。</span><span class="sxs-lookup"><span data-stu-id="abbde-106">[out] A pointer to the size, in bytes, of the string heap.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abbde-107">需求</span><span class="sxs-lookup"><span data-stu-id="abbde-107">Requirements</span></span>  
 <span data-ttu-id="abbde-108">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="abbde-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abbde-109">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="abbde-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="abbde-110">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="abbde-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="abbde-111">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abbde-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abbde-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="abbde-112">See Also</span></span>  
 [<span data-ttu-id="abbde-113">IMetaDataTables 介面</span><span class="sxs-lookup"><span data-stu-id="abbde-113">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="abbde-114">IMetaDataTables2 介面</span><span class="sxs-lookup"><span data-stu-id="abbde-114">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
