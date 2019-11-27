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
ms.openlocfilehash: 9d0f443b5b7d2d358534e888c3fc84ad3f554119
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450053"
---
# <a name="imetadataimportenumpermissionsets-method"></a><span data-ttu-id="bee5a-102">IMetaDataImport::EnumPermissionSets 方法</span><span class="sxs-lookup"><span data-stu-id="bee5a-102">IMetaDataImport::EnumPermissionSets Method</span></span>
<span data-ttu-id="bee5a-103">列舉指定中繼資料範圍內的物件權限。</span><span class="sxs-lookup"><span data-stu-id="bee5a-103">Enumerates permissions for the objects in a specified metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bee5a-104">語法</span><span class="sxs-lookup"><span data-stu-id="bee5a-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="bee5a-105">參數</span><span class="sxs-lookup"><span data-stu-id="bee5a-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="bee5a-106">[in、out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="bee5a-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="bee5a-107">第一次呼叫此方法時，此值必須為 Null。</span><span class="sxs-lookup"><span data-stu-id="bee5a-107">This must be NULL for the first call of this method.</span></span>  
  
 `tk`  
 <span data-ttu-id="bee5a-108">在限制搜尋範圍的元資料標記，或 Null 表示搜尋最廣泛的範圍。</span><span class="sxs-lookup"><span data-stu-id="bee5a-108">[in] A metadata token that limits the scope of the search, or NULL to search the widest scope possible.</span></span>  
  
 `dwActions`  
 <span data-ttu-id="bee5a-109">在旗標，代表要包含在 `rPermission`中的 <xref:System.Security.Permissions.SecurityAction> 值，否則為零以傳回所有動作。</span><span class="sxs-lookup"><span data-stu-id="bee5a-109">[in] Flags representing the <xref:System.Security.Permissions.SecurityAction> values to include in `rPermission`, or zero to return all actions.</span></span>  
  
 `rPermission`  
 <span data-ttu-id="bee5a-110">脫銷用來儲存許可權標記的陣列。</span><span class="sxs-lookup"><span data-stu-id="bee5a-110">[out] The array used to store the Permission tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="bee5a-111">[in] `rPermission` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="bee5a-111">[in] The maximum size of the `rPermission` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="bee5a-112">脫銷`rPermission`中傳回的許可權權杖數目。</span><span class="sxs-lookup"><span data-stu-id="bee5a-112">[out] The number of Permission tokens returned in `rPermission`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bee5a-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="bee5a-113">Return Value</span></span>  
  
|<span data-ttu-id="bee5a-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bee5a-114">HRESULT</span></span>|<span data-ttu-id="bee5a-115">描述</span><span class="sxs-lookup"><span data-stu-id="bee5a-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="bee5a-116">已成功傳回 `EnumPermissionSets`。</span><span class="sxs-lookup"><span data-stu-id="bee5a-116">`EnumPermissionSets` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="bee5a-117">沒有要列舉的權杖。</span><span class="sxs-lookup"><span data-stu-id="bee5a-117">There are no tokens to enumerate.</span></span> <span data-ttu-id="bee5a-118">在此情況下，`pcTokens` 為零。</span><span class="sxs-lookup"><span data-stu-id="bee5a-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bee5a-119">需求</span><span class="sxs-lookup"><span data-stu-id="bee5a-119">Requirements</span></span>  
 <span data-ttu-id="bee5a-120">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bee5a-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bee5a-121">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="bee5a-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bee5a-122">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="bee5a-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bee5a-123">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bee5a-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bee5a-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="bee5a-124">See also</span></span>

- [<span data-ttu-id="bee5a-125">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="bee5a-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="bee5a-126">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="bee5a-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
