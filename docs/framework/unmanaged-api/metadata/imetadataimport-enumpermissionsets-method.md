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
ms.openlocfilehash: eef2c733f96d74e3353a940cc90f1a631cf48a36
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690492"
---
# <a name="imetadataimportenumpermissionsets-method"></a><span data-ttu-id="29701-102">IMetaDataImport::EnumPermissionSets 方法</span><span class="sxs-lookup"><span data-stu-id="29701-102">IMetaDataImport::EnumPermissionSets Method</span></span>

<span data-ttu-id="29701-103">列舉指定中繼資料範圍內的物件權限。</span><span class="sxs-lookup"><span data-stu-id="29701-103">Enumerates permissions for the objects in a specified metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29701-104">語法</span><span class="sxs-lookup"><span data-stu-id="29701-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="29701-105">參數</span><span class="sxs-lookup"><span data-stu-id="29701-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="29701-106">[in，out]列舉值的指標。</span><span class="sxs-lookup"><span data-stu-id="29701-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="29701-107">此方法的第一個呼叫必須是 Null。</span><span class="sxs-lookup"><span data-stu-id="29701-107">This must be NULL for the first call of this method.</span></span>  
  
 `tk`  
 <span data-ttu-id="29701-108">在限制搜尋範圍的元資料標記，或 Null 表示盡可能搜尋最廣泛的範圍。</span><span class="sxs-lookup"><span data-stu-id="29701-108">[in] A metadata token that limits the scope of the search, or NULL to search the widest scope possible.</span></span>  
  
 `dwActions`  
 <span data-ttu-id="29701-109">在旗標 <xref:System.Security.Permissions.SecurityAction> ，代表要包含在中的值 `rPermission` ，或零表示傳回所有動作。</span><span class="sxs-lookup"><span data-stu-id="29701-109">[in] Flags representing the <xref:System.Security.Permissions.SecurityAction> values to include in `rPermission`, or zero to return all actions.</span></span>  
  
 `rPermission`  
 <span data-ttu-id="29701-110">擴展用來儲存許可權權杖的陣列。</span><span class="sxs-lookup"><span data-stu-id="29701-110">[out] The array used to store the Permission tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="29701-111">[in] `rPermission` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="29701-111">[in] The maximum size of the `rPermission` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="29701-112">擴展中傳回的許可權權杖數目 `rPermission` 。</span><span class="sxs-lookup"><span data-stu-id="29701-112">[out] The number of Permission tokens returned in `rPermission`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="29701-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="29701-113">Return Value</span></span>  
  
|<span data-ttu-id="29701-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="29701-114">HRESULT</span></span>|<span data-ttu-id="29701-115">描述</span><span class="sxs-lookup"><span data-stu-id="29701-115">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="29701-116">`EnumPermissionSets` 傳回成功。</span><span class="sxs-lookup"><span data-stu-id="29701-116">`EnumPermissionSets` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="29701-117">沒有要列舉的權杖。</span><span class="sxs-lookup"><span data-stu-id="29701-117">There are no tokens to enumerate.</span></span> <span data-ttu-id="29701-118">在此情況下， `pcTokens` 是零。</span><span class="sxs-lookup"><span data-stu-id="29701-118">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="29701-119">需求</span><span class="sxs-lookup"><span data-stu-id="29701-119">Requirements</span></span>  

 <span data-ttu-id="29701-120">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="29701-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29701-121">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="29701-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="29701-122">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="29701-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="29701-123">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29701-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29701-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29701-124">See also</span></span>

- [<span data-ttu-id="29701-125">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="29701-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="29701-126">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="29701-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
