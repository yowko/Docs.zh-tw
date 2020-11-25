---
title: IMetaDataImport::EnumEvents 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumEvents
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumEvents
helpviewer_keywords:
- IMetaDataImport::EnumEvents method [.NET Framework metadata]
- EnumEvents method [.NET Framework metadata]
ms.assetid: e1efedcb-3dd7-42ae-a399-21c24728aec5
topic_type:
- apiref
ms.openlocfilehash: 3a181f1ef29810058c57bdb13338a01aa1fe7dff
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700466"
---
# <a name="imetadataimportenumevents-method"></a><span data-ttu-id="84bc4-102">IMetaDataImport::EnumEvents 方法</span><span class="sxs-lookup"><span data-stu-id="84bc4-102">IMetaDataImport::EnumEvents Method</span></span>

<span data-ttu-id="84bc4-103">列舉指定 TypeDef 語彙基元的事件定義語彙基元。</span><span class="sxs-lookup"><span data-stu-id="84bc4-103">Enumerates event definition tokens for the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84bc4-104">語法</span><span class="sxs-lookup"><span data-stu-id="84bc4-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumEvents (
   [in, out] HCORENUM    *phEnum,
   [in]      mdTypeDef   td,
   [out]     mdEvent     rEvents[],
   [in]      ULONG       cMax,  
   [out]    ULONG        *pcEvents  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84bc4-105">參數</span><span class="sxs-lookup"><span data-stu-id="84bc4-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="84bc4-106">[in，out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="84bc4-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `td`  
 <span data-ttu-id="84bc4-107">在要列舉其事件定義的 TypeDef 標記。</span><span class="sxs-lookup"><span data-stu-id="84bc4-107">[in] The TypeDef token whose event definitions are to be enumerated.</span></span>  
  
 `rEvents`  
 <span data-ttu-id="84bc4-108">擴展傳回事件的陣列。</span><span class="sxs-lookup"><span data-stu-id="84bc4-108">[out] The array of returned events.</span></span>  
  
 `cMax`  
 <span data-ttu-id="84bc4-109">[in] `rEvents` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="84bc4-109">[in] The maximum size of the `rEvents` array.</span></span>  
  
 `pcEvents`  
 <span data-ttu-id="84bc4-110">擴展在中傳回的實際事件數 `rEvents` 。</span><span class="sxs-lookup"><span data-stu-id="84bc4-110">[out] The actual number of events returned in `rEvents`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="84bc4-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="84bc4-111">Return Value</span></span>  
  
|<span data-ttu-id="84bc4-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="84bc4-112">HRESULT</span></span>|<span data-ttu-id="84bc4-113">描述</span><span class="sxs-lookup"><span data-stu-id="84bc4-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="84bc4-114">`EnumEvents` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="84bc4-114">`EnumEvents` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="84bc4-115">沒有要列舉的事件。</span><span class="sxs-lookup"><span data-stu-id="84bc4-115">There are no events to enumerate.</span></span> <span data-ttu-id="84bc4-116">在此情況下， `pcEvents` 是零。</span><span class="sxs-lookup"><span data-stu-id="84bc4-116">In that case, `pcEvents` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="84bc4-117">需求</span><span class="sxs-lookup"><span data-stu-id="84bc4-117">Requirements</span></span>  

 <span data-ttu-id="84bc4-118">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="84bc4-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84bc4-119">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="84bc4-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="84bc4-120">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="84bc4-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="84bc4-121">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84bc4-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84bc4-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84bc4-122">See also</span></span>

- [<span data-ttu-id="84bc4-123">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="84bc4-123">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="84bc4-124">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="84bc4-124">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
