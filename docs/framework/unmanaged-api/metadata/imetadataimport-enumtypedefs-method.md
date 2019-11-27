---
title: IMetaDataImport::EnumTypeDefs 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeDefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeDefs
helpviewer_keywords:
- EnumTypeDefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeDefs method [.NET Framework metadata]
ms.assetid: 4e508711-da92-4381-aaf8-6803075cdaa2
topic_type:
- apiref
ms.openlocfilehash: 3854cb4aa3d229c87466c0a35a72447ceb235624
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450002"
---
# <a name="imetadataimportenumtypedefs-method"></a><span data-ttu-id="a6f3a-102">IMetaDataImport::EnumTypeDefs 方法</span><span class="sxs-lookup"><span data-stu-id="a6f3a-102">IMetaDataImport::EnumTypeDefs Method</span></span>
<span data-ttu-id="a6f3a-103">列舉代表目前範圍內的所有類型的 TypeDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="a6f3a-103">Enumerates TypeDef tokens representing all types within the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6f3a-104">語法</span><span class="sxs-lookup"><span data-stu-id="a6f3a-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeDefs (  
   [out] HCORENUM   *phEnum,   
   [in]  mdTypeDef  rTypeDefs[],  
   [in]  ULONG      cMax,   
   [out] ULONG      *pcTypeDefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6f3a-105">參數</span><span class="sxs-lookup"><span data-stu-id="a6f3a-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="a6f3a-106">脫銷新枚舉器的指標。</span><span class="sxs-lookup"><span data-stu-id="a6f3a-106">[out] A pointer to the new enumerator.</span></span> <span data-ttu-id="a6f3a-107">第一次呼叫此方法時，此值必須為 Null。</span><span class="sxs-lookup"><span data-stu-id="a6f3a-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeDefs`  
 <span data-ttu-id="a6f3a-108">在用來儲存 TypeDef 標記的陣列。</span><span class="sxs-lookup"><span data-stu-id="a6f3a-108">[in] The array used to store the TypeDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="a6f3a-109">[in] `rTypeDefs` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="a6f3a-109">[in] The maximum size of the `rTypeDefs` array.</span></span>  
  
 `pcTypeDefs`  
 <span data-ttu-id="a6f3a-110">脫銷`rTypeDefs`中傳回的 TypeDef 標記數目。</span><span class="sxs-lookup"><span data-stu-id="a6f3a-110">[out] The number of TypeDef tokens returned in `rTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a6f3a-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="a6f3a-111">Return Value</span></span>  
  
|<span data-ttu-id="a6f3a-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a6f3a-112">HRESULT</span></span>|<span data-ttu-id="a6f3a-113">描述</span><span class="sxs-lookup"><span data-stu-id="a6f3a-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="a6f3a-114">已成功傳回 `EnumTypeDefs`。</span><span class="sxs-lookup"><span data-stu-id="a6f3a-114">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="a6f3a-115">沒有要列舉的權杖。</span><span class="sxs-lookup"><span data-stu-id="a6f3a-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="a6f3a-116">在此情況下，`pcTypeDefs` 為零。</span><span class="sxs-lookup"><span data-stu-id="a6f3a-116">In that case, `pcTypeDefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a6f3a-117">備註</span><span class="sxs-lookup"><span data-stu-id="a6f3a-117">Remarks</span></span>  
 <span data-ttu-id="a6f3a-118">TypeDef token 代表類別或介面等類型，以及透過擴充性機制新增的任何類型。</span><span class="sxs-lookup"><span data-stu-id="a6f3a-118">The TypeDef token represents a type such as a class or an interface, as well as any type added via an extensibility mechanism.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6f3a-119">需求</span><span class="sxs-lookup"><span data-stu-id="a6f3a-119">Requirements</span></span>  
 <span data-ttu-id="a6f3a-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a6f3a-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6f3a-121">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="a6f3a-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a6f3a-122">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a6f3a-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a6f3a-123">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6f3a-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6f3a-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6f3a-124">See also</span></span>

- [<span data-ttu-id="a6f3a-125">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="a6f3a-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="a6f3a-126">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="a6f3a-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
