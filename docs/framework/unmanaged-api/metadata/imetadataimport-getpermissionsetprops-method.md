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
ms.openlocfilehash: 54c75156c32e5b40aa933ef6530b2cc33edf7de4
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490987"
---
# <a name="imetadataimportgetpermissionsetprops-method"></a><span data-ttu-id="de031-102">IMetaDataImport::GetPermissionSetProps 方法</span><span class="sxs-lookup"><span data-stu-id="de031-102">IMetaDataImport::GetPermissionSetProps Method</span></span>
<span data-ttu-id="de031-103">取得與 <xref:System.Security.PermissionSet?displayProperty=nameWithType> 指定的許可權標記所表示之相關聯的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="de031-103">Gets the metadata associated with the <xref:System.Security.PermissionSet?displayProperty=nameWithType> represented by the specified Permission token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de031-104">語法</span><span class="sxs-lookup"><span data-stu-id="de031-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPermissionSetProps (  
   [in]  mdPermission      pm,  
   [out] DWORD             *pdwAction,
   [out] void const        **ppvPermission,
   [out] ULONG             *pcbPermission  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="de031-105">參數</span><span class="sxs-lookup"><span data-stu-id="de031-105">Parameters</span></span>  
 `pm`  
 <span data-ttu-id="de031-106">在許可權元資料標記，表示用來取得中繼資料屬性的許可權集合。</span><span class="sxs-lookup"><span data-stu-id="de031-106">[in] The Permission metadata token that represents the permission set to get the metadata properties for.</span></span>  
  
 `pdwAction`  
 <span data-ttu-id="de031-107">脫銷許可權集合的指標。</span><span class="sxs-lookup"><span data-stu-id="de031-107">[out] A pointer to the permission set.</span></span>  
  
 `ppvPermission`  
 <span data-ttu-id="de031-108">脫銷許可權集合之二進位中繼資料簽章的指標。</span><span class="sxs-lookup"><span data-stu-id="de031-108">[out] A pointer to the binary metadata signature of the permission set.</span></span>  
  
 `pcbPermission`  
 <span data-ttu-id="de031-109">脫銷的大小（以位元組為單位） `ppvPermission` 。</span><span class="sxs-lookup"><span data-stu-id="de031-109">[out] The size in bytes of `ppvPermission`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de031-110">規格需求</span><span class="sxs-lookup"><span data-stu-id="de031-110">Requirements</span></span>  
 <span data-ttu-id="de031-111">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="de031-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de031-112">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="de031-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="de031-113">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="de031-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="de031-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de031-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de031-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="de031-115">See also</span></span>

- <xref:System.Security.PermissionSet>
- [<span data-ttu-id="de031-116">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="de031-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="de031-117">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="de031-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
