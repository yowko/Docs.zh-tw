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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f77e6e9711f05262e494f2814750af8ef7cd9f64
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750898"
---
# <a name="imetadataemitsetpermissionsetprops-method"></a><span data-ttu-id="524e9-102">IMetaDataEmit::SetPermissionSetProps 方法</span><span class="sxs-lookup"><span data-stu-id="524e9-102">IMetaDataEmit::SetPermissionSetProps Method</span></span>
<span data-ttu-id="524e9-103">設定或更新功能的資訊，請參閱先前呼叫所定義的權限集合的中繼資料簽章[imetadataemit:: Definepermissionset](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md)。</span><span class="sxs-lookup"><span data-stu-id="524e9-103">Sets or updates features of the metadata signature of a permission set defined by a prior call to [IMetaDataEmit::DefinePermissionSet](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="524e9-104">語法</span><span class="sxs-lookup"><span data-stu-id="524e9-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPermissionSetProps (   
    [in]  mdToken         tk,   
    [in]  DWORD           dwAction,   
    [in]  void const      *pvPermission,   
    [in]  ULONG           cbPermission,   
    [out] mdPermission    *ppm   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="524e9-105">參數</span><span class="sxs-lookup"><span data-stu-id="524e9-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="524e9-106">[in]中繼資料語彙基元，表示要裝飾的物件。</span><span class="sxs-lookup"><span data-stu-id="524e9-106">[in] A metadata token that represents the object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="524e9-107">[in]A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md)值，指定要使用的宣告式安全性的類型。</span><span class="sxs-lookup"><span data-stu-id="524e9-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="524e9-108">[in]BLOB 權限。</span><span class="sxs-lookup"><span data-stu-id="524e9-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="524e9-109">[in]大小，以位元組為單位的`pvPermission`。</span><span class="sxs-lookup"><span data-stu-id="524e9-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="524e9-110">[out]`mdPermission`中繼資料語彙基元，表示已更新的權限。</span><span class="sxs-lookup"><span data-stu-id="524e9-110">[out] An `mdPermission` metadata token that represents the updated permissions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="524e9-111">需求</span><span class="sxs-lookup"><span data-stu-id="524e9-111">Requirements</span></span>  
 <span data-ttu-id="524e9-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="524e9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="524e9-113">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="524e9-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="524e9-114">**LIBRARY:** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="524e9-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="524e9-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="524e9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="524e9-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="524e9-116">See also</span></span>

- [<span data-ttu-id="524e9-117">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="524e9-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="524e9-118">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="524e9-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
