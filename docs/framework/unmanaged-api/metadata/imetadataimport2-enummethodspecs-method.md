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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 24ad5ff05e4f7fe7fcfc06ff5fe096d47e8b3cbb
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468204"
---
# <a name="imetadataimport2enummethodspecs-method"></a><span data-ttu-id="09b4b-102">IMetaDataImport2::EnumMethodSpecs 方法</span><span class="sxs-lookup"><span data-stu-id="09b4b-102">IMetaDataImport2::EnumMethodSpecs Method</span></span>
<span data-ttu-id="09b4b-103">取得列舉值陣列的 methodspec Neobsahuje 相關聯的權杖與指定 MethodDef 或 MemberRef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="09b4b-103">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09b4b-104">語法</span><span class="sxs-lookup"><span data-stu-id="09b4b-104">Syntax</span></span>  
  
```  
HRESULT EnumMethodSpecs (  
    [in, out] HCORENUM      *phEnum,   
    [in]      mdToken       tk,  
    [out]     mdMethodSpec  rMethodSpecs[],  
    [in]      ULONG         cMax,  
    [out]     ULONG         *pcMethodSpecs  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="09b4b-105">參數</span><span class="sxs-lookup"><span data-stu-id="09b4b-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="09b4b-106">[in、 out]列舉值的指標`rMethodSpecs`。</span><span class="sxs-lookup"><span data-stu-id="09b4b-106">[in, out] A pointer to the enumerator for `rMethodSpecs`.</span></span>  
  
 `tk`  
 <span data-ttu-id="09b4b-107">[in]MemberRef 或 MethodDef 語彙基元，表示要列舉其 methodspec Neobsahuje 語彙基元的方法。</span><span class="sxs-lookup"><span data-stu-id="09b4b-107">[in] The MemberRef or MethodDef token that represents the method whose MethodSpec tokens are to be enumerated.</span></span> <span data-ttu-id="09b4b-108">如果值`tk`為 0 （零），會列舉所有 methodspec Neobsahuje 語彙基元在範圍內。</span><span class="sxs-lookup"><span data-stu-id="09b4b-108">If the value of `tk` is 0 (zero), all MethodSpec tokens in the scope will be enumerated.</span></span>  
  
 `rMethodSpecs`  
 <span data-ttu-id="09b4b-109">[out]列舉的 methodspec Neobsahuje 語彙基元的陣列。</span><span class="sxs-lookup"><span data-stu-id="09b4b-109">[out] The array of MethodSpec tokens to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="09b4b-110">[in]將放在權杖的要求的數目上限`rMethodSpecs`。</span><span class="sxs-lookup"><span data-stu-id="09b4b-110">[in] The requested maximum number of tokens to place in `rMethodSpecs`.</span></span>  
  
 `pcMethodSpecs`  
 <span data-ttu-id="09b4b-111">[out]語彙基元傳回的數字放在`rMethodSpecs`。</span><span class="sxs-lookup"><span data-stu-id="09b4b-111">[out] The returned number of tokens placed in `rMethodSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="09b4b-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="09b4b-112">Return Value</span></span>  
  
|<span data-ttu-id="09b4b-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="09b4b-113">HRESULT</span></span>|<span data-ttu-id="09b4b-114">描述</span><span class="sxs-lookup"><span data-stu-id="09b4b-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="09b4b-115">`EnumMethodSpecs` 已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="09b4b-115">`EnumMethodSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="09b4b-116">`phEnum` 有沒有成員項目。</span><span class="sxs-lookup"><span data-stu-id="09b4b-116">`phEnum` has no member elements.</span></span> <span data-ttu-id="09b4b-117">在此情況下，`pcMethodSpecs`設為 0 （零）。</span><span class="sxs-lookup"><span data-stu-id="09b4b-117">In this case, `pcMethodSpecs` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="09b4b-118">需求</span><span class="sxs-lookup"><span data-stu-id="09b4b-118">Requirements</span></span>  
 <span data-ttu-id="09b4b-119">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="09b4b-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09b4b-120">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="09b4b-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="09b4b-121">**程式庫：** 做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="09b4b-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="09b4b-122">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09b4b-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09b4b-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09b4b-123">See also</span></span>
- [<span data-ttu-id="09b4b-124">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="09b4b-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="09b4b-125">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="09b4b-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
