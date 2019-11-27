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
ms.openlocfilehash: a43c1883038e41cac1b58c78bc26f20d436ebbd1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440246"
---
# <a name="imetadataimportenumcustomattributes-method"></a><span data-ttu-id="61db9-102">IMetaDataImport::EnumCustomAttributes 方法</span><span class="sxs-lookup"><span data-stu-id="61db9-102">IMetaDataImport::EnumCustomAttributes Method</span></span>
<span data-ttu-id="61db9-103">列舉與指定的類型或成員相關聯的自訂屬性定義標記。</span><span class="sxs-lookup"><span data-stu-id="61db9-103">Enumerates custom attribute-definition tokens associated with the specified type or member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61db9-104">語法</span><span class="sxs-lookup"><span data-stu-id="61db9-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumCustomAttributes (   
   [in, out] HCORENUM      *phEnum,  
   [in]  mdToken            tk,   
   [in]  mdToken            tkType,   
   [out] mdCustomAttribute  rCustomAttributes[],   
   [in]  ULONG              cMax,  
   [out, optional] ULONG   *pcCustomAttributes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61db9-105">參數</span><span class="sxs-lookup"><span data-stu-id="61db9-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="61db9-106">[in、out]傳回之列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="61db9-106">[in, out] A pointer to the returned enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="61db9-107">在列舉範圍的 token，如果是所有自訂屬性，則為零。</span><span class="sxs-lookup"><span data-stu-id="61db9-107">[in] A token for the scope of the enumeration, or zero for all custom attributes.</span></span>  
  
 `tkType`  
 <span data-ttu-id="61db9-108">在要列舉之屬性類型的函式的 token，或所有類型的 `null`。</span><span class="sxs-lookup"><span data-stu-id="61db9-108">[in] A token for the constructor of the type of the attributes to be enumerated, or `null` for all types.</span></span>  
  
 `rCustomAttributes`  
 <span data-ttu-id="61db9-109">脫銷自訂屬性標記的陣列。</span><span class="sxs-lookup"><span data-stu-id="61db9-109">[out] An array of custom attribute tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="61db9-110">[in] `rCustomAttributes` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="61db9-110">[in] The maximum size of the `rCustomAttributes` array.</span></span>  
  
 `pcCustomAttributes`  
 <span data-ttu-id="61db9-111">[out，optional]`rCustomAttributes`中傳回的實際標記值數目。</span><span class="sxs-lookup"><span data-stu-id="61db9-111">[out, optional] The actual number of token values returned in `rCustomAttributes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="61db9-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="61db9-112">Return Value</span></span>  
  
|<span data-ttu-id="61db9-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="61db9-113">HRESULT</span></span>|<span data-ttu-id="61db9-114">描述</span><span class="sxs-lookup"><span data-stu-id="61db9-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="61db9-115">已成功傳回 `EnumCustomAttributes`。</span><span class="sxs-lookup"><span data-stu-id="61db9-115">`EnumCustomAttributes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="61db9-116">沒有可列舉的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="61db9-116">There are no custom attributes to enumerate.</span></span> <span data-ttu-id="61db9-117">在此情況下，`pcCustomAttributes` 為零。</span><span class="sxs-lookup"><span data-stu-id="61db9-117">In that case, `pcCustomAttributes` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="61db9-118">需求</span><span class="sxs-lookup"><span data-stu-id="61db9-118">Requirements</span></span>  
 <span data-ttu-id="61db9-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="61db9-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61db9-120">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="61db9-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="61db9-121">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="61db9-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="61db9-122">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61db9-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61db9-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61db9-123">See also</span></span>

- [<span data-ttu-id="61db9-124">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="61db9-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="61db9-125">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="61db9-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
