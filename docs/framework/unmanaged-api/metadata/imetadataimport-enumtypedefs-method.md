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
ms.openlocfilehash: 2d6e86a7f5a93b900e79907f8ee0762869d7f737
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177289"
---
# <a name="imetadataimportenumtypedefs-method"></a><span data-ttu-id="b1717-102">IMetaDataImport::EnumTypeDefs 方法</span><span class="sxs-lookup"><span data-stu-id="b1717-102">IMetaDataImport::EnumTypeDefs Method</span></span>
<span data-ttu-id="b1717-103">列舉代表目前範圍內的所有類型的 TypeDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="b1717-103">Enumerates TypeDef tokens representing all types within the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1717-104">語法</span><span class="sxs-lookup"><span data-stu-id="b1717-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeDefs (  
   [out] HCORENUM   *phEnum,
   [in]  mdTypeDef  rTypeDefs[],  
   [in]  ULONG      cMax,
   [out] ULONG      *pcTypeDefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1717-105">參數</span><span class="sxs-lookup"><span data-stu-id="b1717-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="b1717-106">[出]指向新枚舉器的指標。</span><span class="sxs-lookup"><span data-stu-id="b1717-106">[out] A pointer to the new enumerator.</span></span> <span data-ttu-id="b1717-107">對於此方法的第一次調用，這必須為 Null。</span><span class="sxs-lookup"><span data-stu-id="b1717-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeDefs`  
 <span data-ttu-id="b1717-108">[在]用於存儲 TypeDef 權杖的陣列。</span><span class="sxs-lookup"><span data-stu-id="b1717-108">[in] The array used to store the TypeDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="b1717-109">[in] `rTypeDefs` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="b1717-109">[in] The maximum size of the `rTypeDefs` array.</span></span>  
  
 `pcTypeDefs`  
 <span data-ttu-id="b1717-110">[出]在 中`rTypeDefs`返回的 TypeDef 權杖數。</span><span class="sxs-lookup"><span data-stu-id="b1717-110">[out] The number of TypeDef tokens returned in `rTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b1717-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="b1717-111">Return Value</span></span>  
  
|<span data-ttu-id="b1717-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b1717-112">HRESULT</span></span>|<span data-ttu-id="b1717-113">描述</span><span class="sxs-lookup"><span data-stu-id="b1717-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="b1717-114">`EnumTypeDefs`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="b1717-114">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="b1717-115">沒有要枚舉的權杖。</span><span class="sxs-lookup"><span data-stu-id="b1717-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="b1717-116">在這種情況下，`pcTypeDefs`為零。</span><span class="sxs-lookup"><span data-stu-id="b1717-116">In that case, `pcTypeDefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1717-117">備註</span><span class="sxs-lookup"><span data-stu-id="b1717-117">Remarks</span></span>  
 <span data-ttu-id="b1717-118">TypeDef 權杖表示類或介面的類型，以及通過擴展機制添加的任何類型。</span><span class="sxs-lookup"><span data-stu-id="b1717-118">The TypeDef token represents a type such as a class or an interface, as well as any type added via an extensibility mechanism.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1717-119">需求</span><span class="sxs-lookup"><span data-stu-id="b1717-119">Requirements</span></span>  
 <span data-ttu-id="b1717-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b1717-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1717-121">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="b1717-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b1717-122">**庫：** 作為資源包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="b1717-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b1717-123">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1717-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1717-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1717-124">See also</span></span>

- [<span data-ttu-id="b1717-125">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="b1717-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="b1717-126">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="b1717-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
