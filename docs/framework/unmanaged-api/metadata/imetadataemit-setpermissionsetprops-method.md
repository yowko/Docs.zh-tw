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
ms.openlocfilehash: 1e6ee1f2f497ef30a5390e7afac55c54705248ed
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007802"
---
# <a name="imetadataemitsetpermissionsetprops-method"></a><span data-ttu-id="02e6a-102">IMetaDataEmit::SetPermissionSetProps 方法</span><span class="sxs-lookup"><span data-stu-id="02e6a-102">IMetaDataEmit::SetPermissionSetProps Method</span></span>
<span data-ttu-id="02e6a-103">設定或更新先前呼叫 IMetaDataEmit 時所定義之許可權集合的中繼資料簽章功能[：:D efinepermissionset](imetadataemit-definepermissionset-method.md)。</span><span class="sxs-lookup"><span data-stu-id="02e6a-103">Sets or updates features of the metadata signature of a permission set defined by a prior call to [IMetaDataEmit::DefinePermissionSet](imetadataemit-definepermissionset-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02e6a-104">語法</span><span class="sxs-lookup"><span data-stu-id="02e6a-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPermissionSetProps (
    [in]  mdToken         tk,
    [in]  DWORD           dwAction,
    [in]  void const      *pvPermission,
    [in]  ULONG           cbPermission,
    [out] mdPermission    *ppm
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="02e6a-105">參數</span><span class="sxs-lookup"><span data-stu-id="02e6a-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="02e6a-106">在表示要裝飾之物件的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="02e6a-106">[in] A metadata token that represents the object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="02e6a-107">在[CorDeclSecurity](cordeclsecurity-enumeration.md)值，指定要使用的宣告式安全性類型。</span><span class="sxs-lookup"><span data-stu-id="02e6a-107">[in] A [CorDeclSecurity](cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="02e6a-108">在許可權 BLOB。</span><span class="sxs-lookup"><span data-stu-id="02e6a-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="02e6a-109">在的大小（以位元組為單位） `pvPermission` 。</span><span class="sxs-lookup"><span data-stu-id="02e6a-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="02e6a-110">脫銷`mdPermission`表示已更新之許可權的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="02e6a-110">[out] An `mdPermission` metadata token that represents the updated permissions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02e6a-111">需求</span><span class="sxs-lookup"><span data-stu-id="02e6a-111">Requirements</span></span>  
 <span data-ttu-id="02e6a-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="02e6a-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02e6a-113">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="02e6a-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="02e6a-114">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="02e6a-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="02e6a-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02e6a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02e6a-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02e6a-116">See also</span></span>

- [<span data-ttu-id="02e6a-117">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="02e6a-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="02e6a-118">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="02e6a-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
