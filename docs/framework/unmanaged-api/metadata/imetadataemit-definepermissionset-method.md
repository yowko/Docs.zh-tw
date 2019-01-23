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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 56665997e529227ca82b34a2303f4a2a705c3b1f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54522504"
---
# <a name="imetadataemitdefinepermissionset-method"></a><span data-ttu-id="29ec0-102">IMetaDataEmit::DefinePermissionSet 方法</span><span class="sxs-lookup"><span data-stu-id="29ec0-102">IMetaDataEmit::DefinePermissionSet Method</span></span>
<span data-ttu-id="29ec0-103">建立使用權限集合與指定之中繼資料簽章的定義，並取得該權限集定義的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="29ec0-103">Creates a definition for a permission set with the specified metadata signature, and gets a token to that permission set definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29ec0-104">語法</span><span class="sxs-lookup"><span data-stu-id="29ec0-104">Syntax</span></span>  
  
```  
HRESULT DefinePermissionSet (  
    [in]  mdToken        tk,   
    [in]  DWORD          dwAction,   
    [in]  void const     *pvPermission,   
    [in]  ULONG          cbPermission,   
    [out] mdPermission   *ppm   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="29ec0-105">參數</span><span class="sxs-lookup"><span data-stu-id="29ec0-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="29ec0-106">[in]要裝飾的物件。</span><span class="sxs-lookup"><span data-stu-id="29ec0-106">[in] The object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="29ec0-107">[in]A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md)值，指定要使用的宣告式安全性的類型。</span><span class="sxs-lookup"><span data-stu-id="29ec0-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="29ec0-108">[in]BLOB 權限。</span><span class="sxs-lookup"><span data-stu-id="29ec0-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="29ec0-109">[in]大小，以位元組為單位的`pvPermission`。</span><span class="sxs-lookup"><span data-stu-id="29ec0-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="29ec0-110">[out]傳回的權限的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="29ec0-110">[out] The returned permission token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29ec0-111">需求</span><span class="sxs-lookup"><span data-stu-id="29ec0-111">Requirements</span></span>  
 <span data-ttu-id="29ec0-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="29ec0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29ec0-113">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="29ec0-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="29ec0-114">**程式庫：** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="29ec0-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="29ec0-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29ec0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29ec0-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29ec0-116">See also</span></span>
- [<span data-ttu-id="29ec0-117">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="29ec0-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="29ec0-118">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="29ec0-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
