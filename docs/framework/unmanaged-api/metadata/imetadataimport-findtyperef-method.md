---
title: IMetaDataImport::FindTypeRef 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindTypeRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindTypeRef
helpviewer_keywords:
- IMetaDataImport::FindTypeRef method [.NET Framework metadata]
- FindTypeRef method [.NET Framework metadata]
ms.assetid: 1b2bbf3f-943e-412e-b66c-e802431b055c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b47369e8cee2215b3e7a21e9f069d18dffda847a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54691737"
---
# <a name="imetadataimportfindtyperef-method"></a><span data-ttu-id="811f1-102">IMetaDataImport::FindTypeRef 方法</span><span class="sxs-lookup"><span data-stu-id="811f1-102">IMetaDataImport::FindTypeRef Method</span></span>
<span data-ttu-id="811f1-103">取得 TypeRef 語彙基元的指標<xref:System.Type>，位於指定的範圍內且具有指定的名稱的參考。</span><span class="sxs-lookup"><span data-stu-id="811f1-103">Gets a pointer to the TypeRef token for the <xref:System.Type> reference that is in the specified scope and that has the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="811f1-104">語法</span><span class="sxs-lookup"><span data-stu-id="811f1-104">Syntax</span></span>  
  
```  
HRESULT FindTypeRef (  
   [in] mdToken        tkResolutionScope,  
   [in]  LPCWSTR       szName,  
   [out] mdTypeRef     *ptr  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="811f1-105">參數</span><span class="sxs-lookup"><span data-stu-id="811f1-105">Parameters</span></span>  
 `tkResolutionScope`  
 <span data-ttu-id="811f1-106">[in]ModuleRef、 一個 AssemblyRef 或 TypeRef 語彙基元，指定模組、 組件或類型，分別在型別參考的定義。</span><span class="sxs-lookup"><span data-stu-id="811f1-106">[in] A ModuleRef, AssemblyRef, or TypeRef token that specifies the module, assembly, or type, respectively, in which the type reference is defined.</span></span>  
  
 `szName`  
 <span data-ttu-id="811f1-107">[in]要搜尋的類型參考名稱。</span><span class="sxs-lookup"><span data-stu-id="811f1-107">[in] The name of the type reference to search for.</span></span>  
  
 `ptr`  
 <span data-ttu-id="811f1-108">[out]比對的 TypeRef 語彙基元指標。</span><span class="sxs-lookup"><span data-stu-id="811f1-108">[out] A pointer to the matching TypeRef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="811f1-109">需求</span><span class="sxs-lookup"><span data-stu-id="811f1-109">Requirements</span></span>  
 <span data-ttu-id="811f1-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="811f1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="811f1-111">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="811f1-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="811f1-112">**程式庫：** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="811f1-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="811f1-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="811f1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="811f1-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="811f1-114">See also</span></span>
- [<span data-ttu-id="811f1-115">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="811f1-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="811f1-116">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="811f1-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
