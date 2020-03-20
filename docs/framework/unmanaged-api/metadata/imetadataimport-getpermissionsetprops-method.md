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
ms.openlocfilehash: 5faf1a6ae89045b2ef17fab789ee6e5bf23eecf2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175339"
---
# <a name="imetadataimportgetpermissionsetprops-method"></a><span data-ttu-id="7c4a7-102">IMetaDataImport::GetPermissionSetProps 方法</span><span class="sxs-lookup"><span data-stu-id="7c4a7-102">IMetaDataImport::GetPermissionSetProps Method</span></span>
<span data-ttu-id="7c4a7-103">獲取與指定許可權權杖<xref:System.Security.PermissionSet?displayProperty=nameWithType>表示的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="7c4a7-103">Gets the metadata associated with the <xref:System.Security.PermissionSet?displayProperty=nameWithType> represented by the specified Permission token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c4a7-104">語法</span><span class="sxs-lookup"><span data-stu-id="7c4a7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPermissionSetProps (  
   [in]  mdPermission      pm,  
   [out] DWORD             *pdwAction,
   [out] void const        **ppvPermission,
   [out] ULONG             *pcbPermission  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c4a7-105">參數</span><span class="sxs-lookup"><span data-stu-id="7c4a7-105">Parameters</span></span>  
 `pm`  
 <span data-ttu-id="7c4a7-106">[在]表示獲取中繼資料屬性的許可權集的許可權中繼資料權杖。</span><span class="sxs-lookup"><span data-stu-id="7c4a7-106">[in] The Permission metadata token that represents the permission set to get the metadata properties for.</span></span>  
  
 `pdwAction`  
 <span data-ttu-id="7c4a7-107">[出]指向許可權集的指標。</span><span class="sxs-lookup"><span data-stu-id="7c4a7-107">[out] A pointer to the permission set.</span></span>  
  
 `ppvPermission`  
 <span data-ttu-id="7c4a7-108">[出]指向許可權集的二進位中繼資料簽名的指標。</span><span class="sxs-lookup"><span data-stu-id="7c4a7-108">[out] A pointer to the binary metadata signature of the permission set.</span></span>  
  
 `pcbPermission`  
 <span data-ttu-id="7c4a7-109">[出]的大小（以位元組為單位）。 `ppvPermission`</span><span class="sxs-lookup"><span data-stu-id="7c4a7-109">[out] The size in bytes of `ppvPermission`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c4a7-110">需求</span><span class="sxs-lookup"><span data-stu-id="7c4a7-110">Requirements</span></span>  
 <span data-ttu-id="7c4a7-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7c4a7-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c4a7-112">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="7c4a7-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7c4a7-113">**庫：** 作為資源包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="7c4a7-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7c4a7-114">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c4a7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c4a7-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c4a7-115">See also</span></span>

- <xref:System.Security.PermissionSet>
- [<span data-ttu-id="7c4a7-116">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="7c4a7-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="7c4a7-117">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="7c4a7-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
