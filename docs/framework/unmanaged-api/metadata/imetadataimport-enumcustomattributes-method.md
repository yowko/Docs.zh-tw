---
title: IMetaDataImport::EnumCustomAttributes 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumCustomAttributes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumCustomAttributes
helpviewer_keywords:
- EnumCustomAttributes method [.NET Framework metadata]
- IMetaDataImport::EnumCustomAttributes method [.NET Framework metadata]
ms.assetid: 798513a0-68b1-4d04-bc5b-782a4445ea68
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b53347e9f446d6340bfc5dab2d8f898ebbbf93f8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527103"
---
# <a name="imetadataimportenumcustomattributes-method"></a><span data-ttu-id="a0528-102">IMetaDataImport::EnumCustomAttributes 方法</span><span class="sxs-lookup"><span data-stu-id="a0528-102">IMetaDataImport::EnumCustomAttributes Method</span></span>
<span data-ttu-id="a0528-103">列舉指定的型別或成員相關聯的自訂屬性定義語彙基元。</span><span class="sxs-lookup"><span data-stu-id="a0528-103">Enumerates custom attribute-definition tokens associated with the specified type or member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0528-104">語法</span><span class="sxs-lookup"><span data-stu-id="a0528-104">Syntax</span></span>  
  
```  
HRESULT EnumCustomAttributes (   
   [in, out] HCORENUM      *phEnum,  
   [in]  mdToken            tk,   
   [in]  mdToken            tkType,   
   [out] mdCustomAttribute  rCustomAttributes[],   
   [in]  ULONG              cMax,  
   [out, optional] ULONG   *pcCustomAttributes  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a0528-105">參數</span><span class="sxs-lookup"><span data-stu-id="a0528-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="a0528-106">[in、 out]要傳回的列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="a0528-106">[in, out] A pointer to the returned enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="a0528-107">[in]語彙基元範圍的列舉型別或為零的所有自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="a0528-107">[in] A token for the scope of the enumeration, or zero for all custom attributes.</span></span>  
  
 `tkType`  
 <span data-ttu-id="a0528-108">[in]要列舉的屬性之型別的建構函式的語彙基元或`null`所有類型。</span><span class="sxs-lookup"><span data-stu-id="a0528-108">[in] A token for the constructor of the type of the attributes to be enumerated, or `null` for all types.</span></span>  
  
 `rCustomAttributes`  
 <span data-ttu-id="a0528-109">[out]自訂屬性的語彙基元的陣列。</span><span class="sxs-lookup"><span data-stu-id="a0528-109">[out] An array of custom attribute tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="a0528-110">[in] `rCustomAttributes` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="a0528-110">[in] The maximum size of the `rCustomAttributes` array.</span></span>  
  
 `pcCustomAttributes`  
 <span data-ttu-id="a0528-111">[out，optional]傳回的權杖值的實際數目`rCustomAttributes`。</span><span class="sxs-lookup"><span data-stu-id="a0528-111">[out, optional] The actual number of token values returned in `rCustomAttributes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a0528-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="a0528-112">Return Value</span></span>  
  
|<span data-ttu-id="a0528-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a0528-113">HRESULT</span></span>|<span data-ttu-id="a0528-114">描述</span><span class="sxs-lookup"><span data-stu-id="a0528-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="a0528-115">`EnumCustomAttributes` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="a0528-115">`EnumCustomAttributes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="a0528-116">沒有自訂屬性來列舉。</span><span class="sxs-lookup"><span data-stu-id="a0528-116">There are no custom attributes to enumerate.</span></span> <span data-ttu-id="a0528-117">在此情況下，`pcCustomAttributes`為零。</span><span class="sxs-lookup"><span data-stu-id="a0528-117">In that case, `pcCustomAttributes` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a0528-118">需求</span><span class="sxs-lookup"><span data-stu-id="a0528-118">Requirements</span></span>  
 <span data-ttu-id="a0528-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a0528-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0528-120">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a0528-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a0528-121">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a0528-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a0528-122">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0528-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0528-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0528-123">See also</span></span>
- [<span data-ttu-id="a0528-124">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="a0528-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="a0528-125">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="a0528-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
