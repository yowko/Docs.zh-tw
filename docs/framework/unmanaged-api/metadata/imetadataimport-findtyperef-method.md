---
title: "IMetaDataImport::FindTypeRef 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.FindTypeRef
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::FindTypeRef
helpviewer_keywords:
- IMetaDataImport::FindTypeRef method [.NET Framework metadata]
- FindTypeRef method [.NET Framework metadata]
ms.assetid: 1b2bbf3f-943e-412e-b66c-e802431b055c
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3321f8ea1897f807a06d5c9a812fded2fd7f6365
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportfindtyperef-method"></a><span data-ttu-id="97c9c-102">IMetaDataImport::FindTypeRef 方法</span><span class="sxs-lookup"><span data-stu-id="97c9c-102">IMetaDataImport::FindTypeRef Method</span></span>
<span data-ttu-id="97c9c-103">取得 TypeRef 語彙基元的指標<xref:System.Type>參考指定範圍中且具有指定之名稱。</span><span class="sxs-lookup"><span data-stu-id="97c9c-103">Gets a pointer to the TypeRef token for the <xref:System.Type> reference that is in the specified scope and that has the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97c9c-104">語法</span><span class="sxs-lookup"><span data-stu-id="97c9c-104">Syntax</span></span>  
  
```  
HRESULT FindTypeRef (  
   [in] mdToken        tkResolutionScope,  
   [in]  LPCWSTR       szName,  
   [out] mdTypeRef     *ptr  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="97c9c-105">參數</span><span class="sxs-lookup"><span data-stu-id="97c9c-105">Parameters</span></span>  
 `tkResolutionScope`  
 <span data-ttu-id="97c9c-106">[in]ModuleRef、 AssemblyRef 或 TypeRef 語彙基元，指定模組、 組件或類型，分別在型別參考其定義。</span><span class="sxs-lookup"><span data-stu-id="97c9c-106">[in] A ModuleRef, AssemblyRef, or TypeRef token that specifies the module, assembly, or type, respectively, in which the type reference is defined.</span></span>  
  
 `szName`  
 <span data-ttu-id="97c9c-107">[in]若要搜尋的型別參考的名稱。</span><span class="sxs-lookup"><span data-stu-id="97c9c-107">[in] The name of the type reference to search for.</span></span>  
  
 `ptr`  
 <span data-ttu-id="97c9c-108">[out]比對的 TypeRef 語彙基元的指標。</span><span class="sxs-lookup"><span data-stu-id="97c9c-108">[out] A pointer to the matching TypeRef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97c9c-109">需求</span><span class="sxs-lookup"><span data-stu-id="97c9c-109">Requirements</span></span>  
 <span data-ttu-id="97c9c-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="97c9c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97c9c-111">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="97c9c-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="97c9c-112">**程式庫：**包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="97c9c-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="97c9c-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97c9c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97c9c-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="97c9c-114">See Also</span></span>  
 [<span data-ttu-id="97c9c-115">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="97c9c-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="97c9c-116">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="97c9c-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
