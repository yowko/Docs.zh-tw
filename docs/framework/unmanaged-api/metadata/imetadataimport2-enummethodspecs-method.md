---
title: "IMetaDataImport2::EnumMethodSpecs 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6e134d19eb6699f39e6d538f93f989b87ed8f37d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimport2enummethodspecs-method"></a><span data-ttu-id="09731-102">IMetaDataImport2::EnumMethodSpecs 方法</span><span class="sxs-lookup"><span data-stu-id="09731-102">IMetaDataImport2::EnumMethodSpecs Method</span></span>
<span data-ttu-id="09731-103">取得列舉值陣列的 MethodSpec 語彙基元相關聯的指定 MethodDef 或 MemberRef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="09731-103">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09731-104">語法</span><span class="sxs-lookup"><span data-stu-id="09731-104">Syntax</span></span>  
  
```  
HRESULT EnumMethodSpecs (  
    [in, out] HCORENUM      *phEnum,   
    [in]      mdToken       tk,  
    [out]     mdMethodSpec  rMethodSpecs[],  
    [in]      ULONG         cMax,  
    [out]     ULONG         *pcMethodSpecs  
);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="09731-105">參數</span><span class="sxs-lookup"><span data-stu-id="09731-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="09731-106">[in、 out]列舉值的指標`rMethodSpecs`。</span><span class="sxs-lookup"><span data-stu-id="09731-106">[in, out] A pointer to the enumerator for `rMethodSpecs`.</span></span>  
  
 `tk`  
 <span data-ttu-id="09731-107">[in]MemberRef 或 MethodDef 語彙基元所代表的 MethodSpec 語彙基元是要列舉的方法。</span><span class="sxs-lookup"><span data-stu-id="09731-107">[in] The MemberRef or MethodDef token that represents the method whose MethodSpec tokens are to be enumerated.</span></span> <span data-ttu-id="09731-108">如果值`tk`是 0 （零），會列舉在範圍內的所有 MethodSpec 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="09731-108">If the value of `tk` is 0 (zero), all MethodSpec tokens in the scope will be enumerated.</span></span>  
  
 `rMethodSpecs`  
 <span data-ttu-id="09731-109">[out]列舉的 MethodSpec 語彙基元的陣列。</span><span class="sxs-lookup"><span data-stu-id="09731-109">[out] The array of MethodSpec tokens to enumerate.</span></span>  
  
 `cMax`  
 <span data-ttu-id="09731-110">[in]將放置在權杖的要求的數目上限`rMethodSpecs`。</span><span class="sxs-lookup"><span data-stu-id="09731-110">[in] The requested maximum number of tokens to place in `rMethodSpecs`.</span></span>  
  
 `pcMethodSpecs`  
 <span data-ttu-id="09731-111">[out]傳回的語彙基元的數字放在`rMethodSpecs`。</span><span class="sxs-lookup"><span data-stu-id="09731-111">[out] The returned number of tokens placed in `rMethodSpecs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="09731-112">傳回值</span><span class="sxs-lookup"><span data-stu-id="09731-112">Return Value</span></span>  
  
|<span data-ttu-id="09731-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="09731-113">HRESULT</span></span>|<span data-ttu-id="09731-114">描述</span><span class="sxs-lookup"><span data-stu-id="09731-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="09731-115">`EnumMethodSpecs`已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="09731-115">`EnumMethodSpecs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="09731-116">`phEnum`不含任何成員的元素。</span><span class="sxs-lookup"><span data-stu-id="09731-116">`phEnum` has no member elements.</span></span> <span data-ttu-id="09731-117">在此情況下，`pcMethodSpecs`設為 0 （零）。</span><span class="sxs-lookup"><span data-stu-id="09731-117">In this case, `pcMethodSpecs` is set to 0 (zero).</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="09731-118">需求</span><span class="sxs-lookup"><span data-stu-id="09731-118">Requirements</span></span>  
 <span data-ttu-id="09731-119">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="09731-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09731-120">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="09731-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="09731-121">**程式庫：**做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="09731-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="09731-122">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09731-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09731-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="09731-123">See Also</span></span>  
 [<span data-ttu-id="09731-124">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="09731-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="09731-125">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="09731-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
