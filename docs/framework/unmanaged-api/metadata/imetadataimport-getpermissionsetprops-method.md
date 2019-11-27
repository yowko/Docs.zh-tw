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
ms.openlocfilehash: a020a0343eecceb4a85ebbddffe323c7f7bdca3d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437119"
---
# <a name="imetadataimportgetpermissionsetprops-method"></a><span data-ttu-id="99d37-102">IMetaDataImport::GetPermissionSetProps 方法</span><span class="sxs-lookup"><span data-stu-id="99d37-102">IMetaDataImport::GetPermissionSetProps Method</span></span>
<span data-ttu-id="99d37-103">取得與指定的許可權標記所表示的 <xref:System.Security.PermissionSet?displayProperty=nameWithType> 相關聯的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="99d37-103">Gets the metadata associated with the <xref:System.Security.PermissionSet?displayProperty=nameWithType> represented by the specified Permission token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99d37-104">語法</span><span class="sxs-lookup"><span data-stu-id="99d37-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPermissionSetProps (  
   [in]  mdPermission      pm,  
   [out] DWORD             *pdwAction,   
   [out] void const        **ppvPermission,   
   [out] ULONG             *pcbPermission  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="99d37-105">參數</span><span class="sxs-lookup"><span data-stu-id="99d37-105">Parameters</span></span>  
 `pm`  
 <span data-ttu-id="99d37-106">在許可權元資料標記，表示用來取得中繼資料屬性的許可權集合。</span><span class="sxs-lookup"><span data-stu-id="99d37-106">[in] The Permission metadata token that represents the permission set to get the metadata properties for.</span></span>  
  
 `pdwAction`  
 <span data-ttu-id="99d37-107">脫銷許可權集合的指標。</span><span class="sxs-lookup"><span data-stu-id="99d37-107">[out] A pointer to the permission set.</span></span>  
  
 `ppvPermission`  
 <span data-ttu-id="99d37-108">脫銷許可權集合之二進位中繼資料簽章的指標。</span><span class="sxs-lookup"><span data-stu-id="99d37-108">[out] A pointer to the binary metadata signature of the permission set.</span></span>  
  
 `pcbPermission`  
 <span data-ttu-id="99d37-109">脫銷`ppvPermission`的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="99d37-109">[out] The size in bytes of `ppvPermission`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99d37-110">需求</span><span class="sxs-lookup"><span data-stu-id="99d37-110">Requirements</span></span>  
 <span data-ttu-id="99d37-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="99d37-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99d37-112">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="99d37-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="99d37-113">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="99d37-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="99d37-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99d37-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99d37-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99d37-115">See also</span></span>

- <xref:System.Security.PermissionSet>
- [<span data-ttu-id="99d37-116">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="99d37-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="99d37-117">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="99d37-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
