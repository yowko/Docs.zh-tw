---
title: IMetaDataImport2::EnumMethodSpecs 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.EnumMethodSpecs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::EnumMethodSpecs
helpviewer_keywords:
- IMetaDataImport2::EnumMethodSpecs method [.NET Framework metadata]
- EnumMethodSpecs method [.NET Framework metadata]
ms.assetid: b3fc1e6c-bcb6-4915-baf8-7dc0a31b8724
topic_type:
- apiref
ms.openlocfilehash: 2df53ba53c64e042abc54a1d2ac043d301acdde9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177178"
---
# <a name="imetadataimport2enummethodspecs-method"></a><span data-ttu-id="56e98-102">IMetaDataImport2::EnumMethodSpecs 方法</span><span class="sxs-lookup"><span data-stu-id="56e98-102">IMetaDataImport2::EnumMethodSpecs Method</span></span>
<span data-ttu-id="56e98-103">獲取與指定方法Def或會員Ref權杖關聯的 MethodSpec 權杖陣列的枚舉器。</span><span class="sxs-lookup"><span data-stu-id="56e98-103">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56e98-104">語法</span><span class="sxs-lookup"><span data-stu-id="56e98-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethodSpecs (  
    [in, out] HCORENUM      *phEnum,
    [in]      mdToken       tk,  
    [out]     mdMethodSpec  rMethodSpecs[],  
    [in]      ULONG         cMax,  
    [out]     ULONG         *pcMethodSpecs  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="56e98-105">參數</span><span class="sxs-lookup"><span data-stu-id="56e98-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="56e98-106">[進出]指向 的枚舉器的`rMethodSpecs`指標。</span><span class="sxs-lookup"><span data-stu-id="56e98-106">[in, out] A pointer to the enumerator for `rMethodSpecs`.</span></span>  
  
 `tk`  
 <span data-ttu-id="56e98-107">[在]代表其方法Spec權杖的方法的會員Ref或 MethodDef 權杖。</span><span class="sxs-lookup"><span data-stu-id="56e98-107">[in] The MemberRef or MethodDef token that represents the method whose MethodSpec tokens are to be enumerated.</span></span> <span data-ttu-id="56e98-108">如果 值`tk`為 0（零），則將枚舉作用域中的所有 MethodSpec 權杖。</span><span class="sxs-lookup"><span data-stu-id="56e98-108">If the value of `tk` is 0 (zero), all MethodSpec tokens in the scope will be enumerated.</span></span>  
  
 `rMethodSpecs`  
 <span data-ttu-id="56e98-109">[出]要枚舉的 MethodSpec 權杖的陣列。</span><span class="sxs-lookup"><span data-stu-id="56e98-109">[out] The array of MethodSpec tokens to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="56e98-110">[在]要放置在 中`rMethodSpecs`的最大權杖數。</span><span class="sxs-lookup"><span data-stu-id="56e98-110">[in] The requested maximum number of tokens to place in `rMethodSpecs`.</span></span>  
  
 `pcMethodSpecs`  
 <span data-ttu-id="56e98-111">[出]放置在 的`rMethodSpecs`返回的權杖數。</span><span class="sxs-lookup"><span data-stu-id="56e98-111">[out] The returned number of tokens placed in `rMethodSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="56e98-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="56e98-112">Return Value</span></span>  
  
|<span data-ttu-id="56e98-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="56e98-113">HRESULT</span></span>|<span data-ttu-id="56e98-114">描述</span><span class="sxs-lookup"><span data-stu-id="56e98-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="56e98-115">`EnumMethodSpecs`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="56e98-115">`EnumMethodSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="56e98-116">`phEnum`沒有成員元素。</span><span class="sxs-lookup"><span data-stu-id="56e98-116">`phEnum` has no member elements.</span></span> <span data-ttu-id="56e98-117">在這種情況下，`pcMethodSpecs`設置為 0（零）。</span><span class="sxs-lookup"><span data-stu-id="56e98-117">In this case, `pcMethodSpecs` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="56e98-118">需求</span><span class="sxs-lookup"><span data-stu-id="56e98-118">Requirements</span></span>  
 <span data-ttu-id="56e98-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="56e98-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56e98-120">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="56e98-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="56e98-121">**庫：** 用作 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="56e98-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="56e98-122">**.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56e98-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56e98-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56e98-123">See also</span></span>

- [<span data-ttu-id="56e98-124">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="56e98-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="56e98-125">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="56e98-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
