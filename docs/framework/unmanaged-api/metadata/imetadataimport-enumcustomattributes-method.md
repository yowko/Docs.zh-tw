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
ms.openlocfilehash: 61b5678a546bdbadbcc6d8ee86447cb17ce72b99
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175521"
---
# <a name="imetadataimportenumcustomattributes-method"></a><span data-ttu-id="8624a-102">IMetaDataImport::EnumCustomAttributes 方法</span><span class="sxs-lookup"><span data-stu-id="8624a-102">IMetaDataImport::EnumCustomAttributes Method</span></span>
<span data-ttu-id="8624a-103">枚舉與指定類型或成員關聯的自訂屬性定義權杖。</span><span class="sxs-lookup"><span data-stu-id="8624a-103">Enumerates custom attribute-definition tokens associated with the specified type or member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8624a-104">語法</span><span class="sxs-lookup"><span data-stu-id="8624a-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="8624a-105">參數</span><span class="sxs-lookup"><span data-stu-id="8624a-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="8624a-106">[進出]指向返回的枚舉器的指標。</span><span class="sxs-lookup"><span data-stu-id="8624a-106">[in, out] A pointer to the returned enumerator.</span></span>  
  
 `tk`  
 <span data-ttu-id="8624a-107">[在]枚舉範圍的標記，所有自訂屬性為零。</span><span class="sxs-lookup"><span data-stu-id="8624a-107">[in] A token for the scope of the enumeration, or zero for all custom attributes.</span></span>  
  
 `tkType`  
 <span data-ttu-id="8624a-108">[在]要枚舉的屬性類型的建構函式或`null`所有類型的建構函式的權杖。</span><span class="sxs-lookup"><span data-stu-id="8624a-108">[in] A token for the constructor of the type of the attributes to be enumerated, or `null` for all types.</span></span>  
  
 `rCustomAttributes`  
 <span data-ttu-id="8624a-109">[出]自訂屬性權杖的陣列。</span><span class="sxs-lookup"><span data-stu-id="8624a-109">[out] An array of custom attribute tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="8624a-110">[in] `rCustomAttributes` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="8624a-110">[in] The maximum size of the `rCustomAttributes` array.</span></span>  
  
 `pcCustomAttributes`  
 <span data-ttu-id="8624a-111">[退出，可選]在 中`rCustomAttributes`返回的權杖值的實際數量。</span><span class="sxs-lookup"><span data-stu-id="8624a-111">[out, optional] The actual number of token values returned in `rCustomAttributes`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8624a-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="8624a-112">Return Value</span></span>  
  
|<span data-ttu-id="8624a-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8624a-113">HRESULT</span></span>|<span data-ttu-id="8624a-114">描述</span><span class="sxs-lookup"><span data-stu-id="8624a-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="8624a-115">`EnumCustomAttributes`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="8624a-115">`EnumCustomAttributes` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="8624a-116">沒有要枚舉的自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="8624a-116">There are no custom attributes to enumerate.</span></span> <span data-ttu-id="8624a-117">在這種情況下，`pcCustomAttributes`為零。</span><span class="sxs-lookup"><span data-stu-id="8624a-117">In that case, `pcCustomAttributes` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8624a-118">需求</span><span class="sxs-lookup"><span data-stu-id="8624a-118">Requirements</span></span>  
 <span data-ttu-id="8624a-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8624a-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8624a-120">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="8624a-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8624a-121">**庫：** 作為資源包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="8624a-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8624a-122">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8624a-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8624a-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8624a-123">See also</span></span>

- [<span data-ttu-id="8624a-124">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="8624a-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="8624a-125">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="8624a-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
