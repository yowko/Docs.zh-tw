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
ms.openlocfilehash: 89c45c049ebadf9e1f16bef8d2626b4e2a17fb70
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729248"
---
# <a name="imetadataimportgetpermissionsetprops-method"></a><span data-ttu-id="00fb7-102">IMetaDataImport::GetPermissionSetProps 方法</span><span class="sxs-lookup"><span data-stu-id="00fb7-102">IMetaDataImport::GetPermissionSetProps Method</span></span>

<span data-ttu-id="00fb7-103">取得與指定的許可權權杖所表示之相關聯的中繼資料 <xref:System.Security.PermissionSet?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="00fb7-103">Gets the metadata associated with the <xref:System.Security.PermissionSet?displayProperty=nameWithType> represented by the specified Permission token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00fb7-104">語法</span><span class="sxs-lookup"><span data-stu-id="00fb7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPermissionSetProps (  
   [in]  mdPermission      pm,  
   [out] DWORD             *pdwAction,
   [out] void const        **ppvPermission,
   [out] ULONG             *pcbPermission  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="00fb7-105">參數</span><span class="sxs-lookup"><span data-stu-id="00fb7-105">Parameters</span></span>  

 `pm`  
 <span data-ttu-id="00fb7-106">在表示要取得之中繼資料屬性之許可權的許可權元資料標記。</span><span class="sxs-lookup"><span data-stu-id="00fb7-106">[in] The Permission metadata token that represents the permission set to get the metadata properties for.</span></span>  
  
 `pdwAction`  
 <span data-ttu-id="00fb7-107">擴展許可權集合的指標。</span><span class="sxs-lookup"><span data-stu-id="00fb7-107">[out] A pointer to the permission set.</span></span>  
  
 `ppvPermission`  
 <span data-ttu-id="00fb7-108">擴展許可權集合的二進位中繼資料簽章指標。</span><span class="sxs-lookup"><span data-stu-id="00fb7-108">[out] A pointer to the binary metadata signature of the permission set.</span></span>  
  
 `pcbPermission`  
 <span data-ttu-id="00fb7-109">擴展的大小（以位元組為單位） `ppvPermission` 。</span><span class="sxs-lookup"><span data-stu-id="00fb7-109">[out] The size in bytes of `ppvPermission`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00fb7-110">需求</span><span class="sxs-lookup"><span data-stu-id="00fb7-110">Requirements</span></span>  

 <span data-ttu-id="00fb7-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="00fb7-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00fb7-112">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="00fb7-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="00fb7-113">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="00fb7-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="00fb7-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00fb7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00fb7-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00fb7-115">See also</span></span>

- <xref:System.Security.PermissionSet>
- [<span data-ttu-id="00fb7-116">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="00fb7-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="00fb7-117">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="00fb7-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
