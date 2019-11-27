---
title: IMetaDataEmit::DefinePermissionSet 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefinePermissionSet
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefinePermissionSet
helpviewer_keywords:
- DefinePermissionSet method [.NET Framework metadata]
- IMetaDataEmit::DefinePermissionSet method [.NET Framework metadata]
ms.assetid: 36cffbf7-82ca-4cf9-bf60-50ab491ac2d9
topic_type:
- apiref
ms.openlocfilehash: 4e11a52c977de7796043868e80c147d8cfd1f506
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431580"
---
# <a name="imetadataemitdefinepermissionset-method"></a><span data-ttu-id="13052-102">IMetaDataEmit::DefinePermissionSet 方法</span><span class="sxs-lookup"><span data-stu-id="13052-102">IMetaDataEmit::DefinePermissionSet Method</span></span>
<span data-ttu-id="13052-103">使用指定的中繼資料簽章建立許可權集合的定義，並取得該許可權集合定義的 token。</span><span class="sxs-lookup"><span data-stu-id="13052-103">Creates a definition for a permission set with the specified metadata signature, and gets a token to that permission set definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13052-104">語法</span><span class="sxs-lookup"><span data-stu-id="13052-104">Syntax</span></span>  
  
```cpp  
HRESULT DefinePermissionSet (  
    [in]  mdToken        tk,   
    [in]  DWORD          dwAction,   
    [in]  void const     *pvPermission,   
    [in]  ULONG          cbPermission,   
    [out] mdPermission   *ppm   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13052-105">參數</span><span class="sxs-lookup"><span data-stu-id="13052-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="13052-106">在要裝飾的物件。</span><span class="sxs-lookup"><span data-stu-id="13052-106">[in] The object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="13052-107">在[CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md)值，指定要使用的宣告式安全性類型。</span><span class="sxs-lookup"><span data-stu-id="13052-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="13052-108">在許可權 BLOB。</span><span class="sxs-lookup"><span data-stu-id="13052-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="13052-109">在`pvPermission`的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="13052-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="13052-110">脫銷傳回的許可權 token。</span><span class="sxs-lookup"><span data-stu-id="13052-110">[out] The returned permission token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13052-111">需求</span><span class="sxs-lookup"><span data-stu-id="13052-111">Requirements</span></span>  
 <span data-ttu-id="13052-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="13052-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13052-113">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="13052-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="13052-114">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="13052-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="13052-115">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13052-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13052-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13052-116">See also</span></span>

- [<span data-ttu-id="13052-117">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="13052-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="13052-118">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="13052-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
