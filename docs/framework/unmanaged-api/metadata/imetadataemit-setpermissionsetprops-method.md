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
ms.openlocfilehash: 4c3e0953d71020ba62ee4ab68aa9e21ea3f0f521
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675031"
---
# <a name="imetadataemitsetpermissionsetprops-method"></a><span data-ttu-id="c678e-102">IMetaDataEmit::SetPermissionSetProps 方法</span><span class="sxs-lookup"><span data-stu-id="c678e-102">IMetaDataEmit::SetPermissionSetProps Method</span></span>

<span data-ttu-id="c678e-103">設定或更新由先前呼叫 [IMetaDataEmit：:D efinepermissionset](imetadataemit-definepermissionset-method.md)所定義之許可權集合的中繼資料簽章功能。</span><span class="sxs-lookup"><span data-stu-id="c678e-103">Sets or updates features of the metadata signature of a permission set defined by a prior call to [IMetaDataEmit::DefinePermissionSet](imetadataemit-definepermissionset-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c678e-104">語法</span><span class="sxs-lookup"><span data-stu-id="c678e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPermissionSetProps (
    [in]  mdToken         tk,
    [in]  DWORD           dwAction,
    [in]  void const      *pvPermission,
    [in]  ULONG           cbPermission,
    [out] mdPermission    *ppm
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c678e-105">參數</span><span class="sxs-lookup"><span data-stu-id="c678e-105">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="c678e-106">在元資料標記，代表要裝飾的物件。</span><span class="sxs-lookup"><span data-stu-id="c678e-106">[in] A metadata token that represents the object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="c678e-107">在 [CorDeclSecurity](cordeclsecurity-enumeration.md) 值，指定要使用的宣告式安全性類型。</span><span class="sxs-lookup"><span data-stu-id="c678e-107">[in] A [CorDeclSecurity](cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="c678e-108">在許可權 BLOB。</span><span class="sxs-lookup"><span data-stu-id="c678e-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="c678e-109">在的大小（以位元組為單位） `pvPermission` 。</span><span class="sxs-lookup"><span data-stu-id="c678e-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="c678e-110">擴展 `mdPermission` 代表更新之許可權的元資料標記。</span><span class="sxs-lookup"><span data-stu-id="c678e-110">[out] An `mdPermission` metadata token that represents the updated permissions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c678e-111">需求</span><span class="sxs-lookup"><span data-stu-id="c678e-111">Requirements</span></span>  

 <span data-ttu-id="c678e-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c678e-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c678e-113">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="c678e-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c678e-114">連結 **庫：** 當做 MSCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="c678e-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c678e-115">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c678e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c678e-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c678e-116">See also</span></span>

- [<span data-ttu-id="c678e-117">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="c678e-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="c678e-118">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="c678e-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
