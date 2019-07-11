---
title: IMetaDataImport::GetPermissionSetProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPermissionSetProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPermissionSetProps
helpviewer_keywords:
- GetPermissionSetProps method [.NET Framework metadata]
- IMetaDataImport::GetPermissionSetProps method [.NET Framework metadata]
ms.assetid: 9855f0e4-12c0-4d3d-ab5d-d6bc52d25eae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 48cd62f89f1112a1007a5661dc55fe2977dace2b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778912"
---
# <a name="imetadataimportgetpermissionsetprops-method"></a><span data-ttu-id="69da5-102">IMetaDataImport::GetPermissionSetProps 方法</span><span class="sxs-lookup"><span data-stu-id="69da5-102">IMetaDataImport::GetPermissionSetProps Method</span></span>
<span data-ttu-id="69da5-103">取得相關聯的中繼資料<xref:System.Security.PermissionSet?displayProperty=nameWithType>指定的權限語彙基元所代表。</span><span class="sxs-lookup"><span data-stu-id="69da5-103">Gets the metadata associated with the <xref:System.Security.PermissionSet?displayProperty=nameWithType> represented by the specified Permission token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69da5-104">語法</span><span class="sxs-lookup"><span data-stu-id="69da5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPermissionSetProps (  
   [in]  mdPermission      pm,  
   [out] DWORD             *pdwAction,   
   [out] void const        **ppvPermission,   
   [out] ULONG             *pcbPermission  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69da5-105">參數</span><span class="sxs-lookup"><span data-stu-id="69da5-105">Parameters</span></span>  
 `pm`  
 <span data-ttu-id="69da5-106">[in]表示要其取得中繼資料屬性設定的權限的權限中繼資料語彙基元。</span><span class="sxs-lookup"><span data-stu-id="69da5-106">[in] The Permission metadata token that represents the permission set to get the metadata properties for.</span></span>  
  
 `pdwAction`  
 <span data-ttu-id="69da5-107">[out]一組權限的指標。</span><span class="sxs-lookup"><span data-stu-id="69da5-107">[out] A pointer to the permission set.</span></span>  
  
 `ppvPermission`  
 <span data-ttu-id="69da5-108">[out]二進位中繼資料簽章的權限集的指標。</span><span class="sxs-lookup"><span data-stu-id="69da5-108">[out] A pointer to the binary metadata signature of the permission set.</span></span>  
  
 `pcbPermission`  
 <span data-ttu-id="69da5-109">[out]以位元組為單位的大小`ppvPermission`。</span><span class="sxs-lookup"><span data-stu-id="69da5-109">[out] The size in bytes of `ppvPermission`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69da5-110">需求</span><span class="sxs-lookup"><span data-stu-id="69da5-110">Requirements</span></span>  
 <span data-ttu-id="69da5-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="69da5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69da5-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="69da5-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="69da5-113">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="69da5-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="69da5-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69da5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69da5-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69da5-115">See also</span></span>

- <xref:System.Security.PermissionSet>
- [<span data-ttu-id="69da5-116">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="69da5-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="69da5-117">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="69da5-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
