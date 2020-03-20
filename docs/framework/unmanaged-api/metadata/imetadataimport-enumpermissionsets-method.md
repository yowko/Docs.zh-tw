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
ms.openlocfilehash: e628cf5dab8006b0df0ab6c60dc995cd0c6bb29d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175443"
---
# <a name="imetadataimportenumpermissionsets-method"></a><span data-ttu-id="60cee-102">IMetaDataImport::EnumPermissionSets 方法</span><span class="sxs-lookup"><span data-stu-id="60cee-102">IMetaDataImport::EnumPermissionSets Method</span></span>
<span data-ttu-id="60cee-103">列舉指定中繼資料範圍內的物件權限。</span><span class="sxs-lookup"><span data-stu-id="60cee-103">Enumerates permissions for the objects in a specified metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60cee-104">語法</span><span class="sxs-lookup"><span data-stu-id="60cee-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumPermissionSets  
   [in, out] HCORENUM      *phEnum,
   [in]      mdToken       tk,
   [in]      DWORD         dwActions,  
   [out]     mdPermission  rPermission[],  
   [in]      ULONG         cMax,  
   [out]     ULONG         *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="60cee-105">參數</span><span class="sxs-lookup"><span data-stu-id="60cee-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="60cee-106">[進出]指向枚舉器的指標。</span><span class="sxs-lookup"><span data-stu-id="60cee-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="60cee-107">對於此方法的第一次調用，這必須為 Null。</span><span class="sxs-lookup"><span data-stu-id="60cee-107">This must be NULL for the first call of this method.</span></span>  
  
 `tk`  
 <span data-ttu-id="60cee-108">[在]限制搜尋範圍的中繼資料權杖，或 Null 以搜索盡可能廣泛的範圍。</span><span class="sxs-lookup"><span data-stu-id="60cee-108">[in] A metadata token that limits the scope of the search, or NULL to search the widest scope possible.</span></span>  
  
 `dwActions`  
 <span data-ttu-id="60cee-109">[在]表示 要<xref:System.Security.Permissions.SecurityAction>包括在 中`rPermission`的值的標誌，或零以返回所有操作。</span><span class="sxs-lookup"><span data-stu-id="60cee-109">[in] Flags representing the <xref:System.Security.Permissions.SecurityAction> values to include in `rPermission`, or zero to return all actions.</span></span>  
  
 `rPermission`  
 <span data-ttu-id="60cee-110">[出]用於存儲許可權權杖的陣列。</span><span class="sxs-lookup"><span data-stu-id="60cee-110">[out] The array used to store the Permission tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="60cee-111">[in] `rPermission` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="60cee-111">[in] The maximum size of the `rPermission` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="60cee-112">[出]在 中`rPermission`返回的許可權權杖數。</span><span class="sxs-lookup"><span data-stu-id="60cee-112">[out] The number of Permission tokens returned in `rPermission`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="60cee-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="60cee-113">Return Value</span></span>  
  
|<span data-ttu-id="60cee-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="60cee-114">HRESULT</span></span>|<span data-ttu-id="60cee-115">描述</span><span class="sxs-lookup"><span data-stu-id="60cee-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="60cee-116">`EnumPermissionSets`已成功返回。</span><span class="sxs-lookup"><span data-stu-id="60cee-116">`EnumPermissionSets` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="60cee-117">沒有要枚舉的權杖。</span><span class="sxs-lookup"><span data-stu-id="60cee-117">There are no tokens to enumerate.</span></span> <span data-ttu-id="60cee-118">在這種情況下，`pcTokens`為零。</span><span class="sxs-lookup"><span data-stu-id="60cee-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="60cee-119">需求</span><span class="sxs-lookup"><span data-stu-id="60cee-119">Requirements</span></span>  
 <span data-ttu-id="60cee-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="60cee-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60cee-121">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="60cee-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="60cee-122">**庫：** 作為資源包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="60cee-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="60cee-123">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60cee-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60cee-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="60cee-124">See also</span></span>

- [<span data-ttu-id="60cee-125">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="60cee-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="60cee-126">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="60cee-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
