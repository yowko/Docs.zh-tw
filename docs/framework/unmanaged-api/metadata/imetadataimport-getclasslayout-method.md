---
title: IMetaDataImport::GetClassLayout 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetClassLayout
helpviewer_keywords:
- IMetaDataImport::GetClassLayout method [.NET Framework metadata]
- GetClassLayout method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 8f35414d-f40b-4b99-8768-9adb675c622a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 11748d3ad99c4050045cce3786eec5604c02ac0f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59197798"
---
# <a name="imetadataimportgetclasslayout-method"></a><span data-ttu-id="4eadb-102">IMetaDataImport::GetClassLayout 方法</span><span class="sxs-lookup"><span data-stu-id="4eadb-102">IMetaDataImport::GetClassLayout Method</span></span>
<span data-ttu-id="4eadb-103">取得指定 TypeDef 語彙基元所參考類別的配置資訊。</span><span class="sxs-lookup"><span data-stu-id="4eadb-103">Gets layout information for the class referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4eadb-104">語法</span><span class="sxs-lookup"><span data-stu-id="4eadb-104">Syntax</span></span>  
  
```  
HRESULT GetClassLayout  (   
   [in]  mdTypeDef          td,   
   [out] DWORD              *pdwPackSize,  
   [out] COR_FIELD_OFFSET   rFieldOffset[],  
   [in]  ULONG              cMax,  
   [out] ULONG              *pcFieldOffset,  
   [out] ULONG              *pulClassSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4eadb-105">參數</span><span class="sxs-lookup"><span data-stu-id="4eadb-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="4eadb-106">[in]使用版面配置，以傳回類別的 TypeDef 語彙基元。</span><span class="sxs-lookup"><span data-stu-id="4eadb-106">[in] The TypeDef token for the class with the layout to return.</span></span>  
  
 `pdwPackSize`  
 <span data-ttu-id="4eadb-107">[out]其中一個值 1、 2、 4、 8 或 16，表示類別的組件大小。</span><span class="sxs-lookup"><span data-stu-id="4eadb-107">[out] One of the values 1, 2, 4, 8, or 16, representing the pack size of the class.</span></span>  
  
 `rFieldOffset`  
 <span data-ttu-id="4eadb-108">[out]陣列[COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md)值。</span><span class="sxs-lookup"><span data-stu-id="4eadb-108">[out] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) values.</span></span>  
  
 `cMax`  
 <span data-ttu-id="4eadb-109">[in] `rFieldOffset` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="4eadb-109">[in] The maximum size of the `rFieldOffset` array.</span></span>  
  
 `pcFieldOffset`  
 <span data-ttu-id="4eadb-110">[out]傳回的項目數`rFieldOffset`。</span><span class="sxs-lookup"><span data-stu-id="4eadb-110">[out] The number of elements returned in `rFieldOffset`.</span></span>  
  
 `pulClassSize`  
 <span data-ttu-id="4eadb-111">[out]大小 （位元組） 所表示之類別的`td`。</span><span class="sxs-lookup"><span data-stu-id="4eadb-111">[out] The size in bytes of the class represented by `td`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4eadb-112">需求</span><span class="sxs-lookup"><span data-stu-id="4eadb-112">Requirements</span></span>  
 <span data-ttu-id="4eadb-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4eadb-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4eadb-114">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4eadb-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4eadb-115">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="4eadb-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4eadb-116">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4eadb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4eadb-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4eadb-117">See also</span></span>

- [<span data-ttu-id="4eadb-118">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="4eadb-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="4eadb-119">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="4eadb-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
