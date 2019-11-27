---
title: IMetaDataEmit::SetPermissionSetProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPermissionSetProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPermissionSetProps
helpviewer_keywords:
- SetPermissionSetProps method [.NET Framework metadata]
- IMetaDataEmit::SetPermissionSetProps method [.NET Framework metadata]
ms.assetid: 8eaee971-40bf-45e2-a3d8-6e57674213b6
topic_type:
- apiref
ms.openlocfilehash: 53a75b8e7edd15cd233577e0a3714fb5d981495f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74432334"
---
# <a name="imetadataemitsetpermissionsetprops-method"></a><span data-ttu-id="c3486-102">IMetaDataEmit::SetPermissionSetProps 方法</span><span class="sxs-lookup"><span data-stu-id="c3486-102">IMetaDataEmit::SetPermissionSetProps Method</span></span>
<span data-ttu-id="c3486-103">設定或更新先前呼叫 IMetaDataEmit 時所定義之許可權集合的中繼資料簽章功能[：:D efinepermissionset](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md)。</span><span class="sxs-lookup"><span data-stu-id="c3486-103">Sets or updates features of the metadata signature of a permission set defined by a prior call to [IMetaDataEmit::DefinePermissionSet](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3486-104">語法</span><span class="sxs-lookup"><span data-stu-id="c3486-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPermissionSetProps (   
    [in]  mdToken         tk,   
    [in]  DWORD           dwAction,   
    [in]  void const      *pvPermission,   
    [in]  ULONG           cbPermission,   
    [out] mdPermission    *ppm   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3486-105">參數</span><span class="sxs-lookup"><span data-stu-id="c3486-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="c3486-106">在表示要裝飾之物件的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="c3486-106">[in] A metadata token that represents the object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="c3486-107">在[CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md)值，指定要使用的宣告式安全性類型。</span><span class="sxs-lookup"><span data-stu-id="c3486-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="c3486-108">在許可權 BLOB。</span><span class="sxs-lookup"><span data-stu-id="c3486-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="c3486-109">在`pvPermission`的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="c3486-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="c3486-110">脫銷`mdPermission` 元資料標記，表示已更新的許可權。</span><span class="sxs-lookup"><span data-stu-id="c3486-110">[out] An `mdPermission` metadata token that represents the updated permissions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3486-111">需求</span><span class="sxs-lookup"><span data-stu-id="c3486-111">Requirements</span></span>  
 <span data-ttu-id="c3486-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c3486-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3486-113">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="c3486-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c3486-114">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="c3486-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c3486-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3486-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3486-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3486-116">See also</span></span>

- [<span data-ttu-id="c3486-117">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="c3486-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="c3486-118">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="c3486-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
