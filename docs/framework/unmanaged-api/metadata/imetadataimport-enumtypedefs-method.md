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
ms.openlocfilehash: cdfd4e10236d546af2555b125d44233172849a21
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503727"
---
# <a name="imetadataimportenumtypedefs-method"></a><span data-ttu-id="3ae78-102">IMetaDataImport::EnumTypeDefs 方法</span><span class="sxs-lookup"><span data-stu-id="3ae78-102">IMetaDataImport::EnumTypeDefs Method</span></span>
<span data-ttu-id="3ae78-103">列舉代表目前範圍內的所有類型的 TypeDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="3ae78-103">Enumerates TypeDef tokens representing all types within the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ae78-104">語法</span><span class="sxs-lookup"><span data-stu-id="3ae78-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeDefs (  
   [out] HCORENUM   *phEnum,
   [in]  mdTypeDef  rTypeDefs[],  
   [in]  ULONG      cMax,
   [out] ULONG      *pcTypeDefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3ae78-105">參數</span><span class="sxs-lookup"><span data-stu-id="3ae78-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="3ae78-106">脫銷新枚舉器的指標。</span><span class="sxs-lookup"><span data-stu-id="3ae78-106">[out] A pointer to the new enumerator.</span></span> <span data-ttu-id="3ae78-107">第一次呼叫此方法時，此值必須為 Null。</span><span class="sxs-lookup"><span data-stu-id="3ae78-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeDefs`  
 <span data-ttu-id="3ae78-108">在用來儲存 TypeDef 標記的陣列。</span><span class="sxs-lookup"><span data-stu-id="3ae78-108">[in] The array used to store the TypeDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="3ae78-109">[in] `rTypeDefs` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="3ae78-109">[in] The maximum size of the `rTypeDefs` array.</span></span>  
  
 `pcTypeDefs`  
 <span data-ttu-id="3ae78-110">脫銷在中傳回的 TypeDef 標記數目 `rTypeDefs` 。</span><span class="sxs-lookup"><span data-stu-id="3ae78-110">[out] The number of TypeDef tokens returned in `rTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3ae78-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="3ae78-111">Return Value</span></span>  
  
|<span data-ttu-id="3ae78-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3ae78-112">HRESULT</span></span>|<span data-ttu-id="3ae78-113">說明</span><span class="sxs-lookup"><span data-stu-id="3ae78-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="3ae78-114">`EnumTypeDefs`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="3ae78-114">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="3ae78-115">沒有要列舉的權杖。</span><span class="sxs-lookup"><span data-stu-id="3ae78-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="3ae78-116">在此情況下， `pcTypeDefs` 是零。</span><span class="sxs-lookup"><span data-stu-id="3ae78-116">In that case, `pcTypeDefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ae78-117">備註</span><span class="sxs-lookup"><span data-stu-id="3ae78-117">Remarks</span></span>  
 <span data-ttu-id="3ae78-118">TypeDef token 代表類別或介面等類型，以及透過擴充性機制新增的任何類型。</span><span class="sxs-lookup"><span data-stu-id="3ae78-118">The TypeDef token represents a type such as a class or an interface, as well as any type added via an extensibility mechanism.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ae78-119">規格需求</span><span class="sxs-lookup"><span data-stu-id="3ae78-119">Requirements</span></span>  
 <span data-ttu-id="3ae78-120">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3ae78-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ae78-121">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="3ae78-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3ae78-122">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="3ae78-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3ae78-123">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ae78-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ae78-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ae78-124">See also</span></span>

- [<span data-ttu-id="3ae78-125">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="3ae78-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="3ae78-126">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="3ae78-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
