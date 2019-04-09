---
title: IMetaDataImport::EnumPermissionSets 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumPermissionSets
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumPermissionSets
helpviewer_keywords:
- EnumPermissionSets method [.NET Framework metadata]
- IMetaDataImport::EnumPermissionSets method [.NET Framework metadata]
ms.assetid: 347d7e5c-c90f-45ad-bd1e-2c7912b0b19c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 28e6ad309af808638400fc27255acdee381b4c6e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59196693"
---
# <a name="imetadataimportenumpermissionsets-method"></a><span data-ttu-id="94257-102">IMetaDataImport::EnumPermissionSets 方法</span><span class="sxs-lookup"><span data-stu-id="94257-102">IMetaDataImport::EnumPermissionSets Method</span></span>
<span data-ttu-id="94257-103">列舉指定中繼資料範圍內的物件權限。</span><span class="sxs-lookup"><span data-stu-id="94257-103">Enumerates permissions for the objects in a specified metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94257-104">語法</span><span class="sxs-lookup"><span data-stu-id="94257-104">Syntax</span></span>  
  
```  
HRESULT EnumPermissionSets  
   [in, out] HCORENUM      *phEnum,   
   [in]      mdToken       tk,   
   [in]      DWORD         dwActions,  
   [out]     mdPermission  rPermission[],  
   [in]      ULONG         cMax,  
   [out]     ULONG         *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94257-105">參數</span><span class="sxs-lookup"><span data-stu-id="94257-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="94257-106">[in、 out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="94257-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="94257-107">首次呼叫這個方法，這必須是 NULL。</span><span class="sxs-lookup"><span data-stu-id="94257-107">This must be NULL for the first call of this method.</span></span>  
  
 `tk`  
 <span data-ttu-id="94257-108">[in]範圍搜尋，則為 NULL 來搜尋最寬的範圍可能限制中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="94257-108">[in] A metadata token that limits the scope of the search, or NULL to search the widest scope possible.</span></span>  
  
 `dwActions`  
 <span data-ttu-id="94257-109">[in]加上旗標表示<xref:System.Security.Permissions.SecurityAction>值，以納入`rPermission`，或是零則表示傳回所有的動作。</span><span class="sxs-lookup"><span data-stu-id="94257-109">[in] Flags representing the <xref:System.Security.Permissions.SecurityAction> values to include in `rPermission`, or zero to return all actions.</span></span>  
  
 `rPermission`  
 <span data-ttu-id="94257-110">[out]陣列，用來儲存權限的權杖。</span><span class="sxs-lookup"><span data-stu-id="94257-110">[out] The array used to store the Permission tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="94257-111">[in] `rPermission` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="94257-111">[in] The maximum size of the `rPermission` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="94257-112">[out]權限權杖中傳回的數目`rPermission`。</span><span class="sxs-lookup"><span data-stu-id="94257-112">[out] The number of Permission tokens returned in `rPermission`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="94257-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="94257-113">Return Value</span></span>  
  
|<span data-ttu-id="94257-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="94257-114">HRESULT</span></span>|<span data-ttu-id="94257-115">描述</span><span class="sxs-lookup"><span data-stu-id="94257-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|`EnumPermissionSets` <span data-ttu-id="94257-116">已成功傳回。</span><span class="sxs-lookup"><span data-stu-id="94257-116">returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="94257-117">沒有列舉語彙基元。</span><span class="sxs-lookup"><span data-stu-id="94257-117">There are no tokens to enumerate.</span></span> <span data-ttu-id="94257-118">在此情況下，`pcTokens`為零。</span><span class="sxs-lookup"><span data-stu-id="94257-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="94257-119">需求</span><span class="sxs-lookup"><span data-stu-id="94257-119">Requirements</span></span>  
 <span data-ttu-id="94257-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="94257-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94257-121">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="94257-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="94257-122">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="94257-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="94257-123">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="94257-123">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="94257-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="94257-124">See also</span></span>

- [<span data-ttu-id="94257-125">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="94257-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="94257-126">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="94257-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
