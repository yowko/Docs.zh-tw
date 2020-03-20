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
ms.openlocfilehash: e02d7dd4b287d027b633ae9bf2e98e036062bdd0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175404"
---
# <a name="imetadataimportgetclasslayout-method"></a><span data-ttu-id="17be9-102">IMetaDataImport::GetClassLayout 方法</span><span class="sxs-lookup"><span data-stu-id="17be9-102">IMetaDataImport::GetClassLayout Method</span></span>
<span data-ttu-id="17be9-103">取得指定 TypeDef 語彙基元所參考類別的配置資訊。</span><span class="sxs-lookup"><span data-stu-id="17be9-103">Gets layout information for the class referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17be9-104">語法</span><span class="sxs-lookup"><span data-stu-id="17be9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassLayout  (
   [in]  mdTypeDef          td,
   [out] DWORD              *pdwPackSize,  
   [out] COR_FIELD_OFFSET   rFieldOffset[],  
   [in]  ULONG              cMax,  
   [out] ULONG              *pcFieldOffset,  
   [out] ULONG              *pulClassSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17be9-105">參數</span><span class="sxs-lookup"><span data-stu-id="17be9-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="17be9-106">[在]要返回佈局的類的 TypeDef 權杖。</span><span class="sxs-lookup"><span data-stu-id="17be9-106">[in] The TypeDef token for the class with the layout to return.</span></span>  
  
 `pdwPackSize`  
 <span data-ttu-id="17be9-107">[出]值 1、2、4、8 或 16，表示類的包大小。</span><span class="sxs-lookup"><span data-stu-id="17be9-107">[out] One of the values 1, 2, 4, 8, or 16, representing the pack size of the class.</span></span>  
  
 `rFieldOffset`  
 <span data-ttu-id="17be9-108">[出][COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md)值的陣列。</span><span class="sxs-lookup"><span data-stu-id="17be9-108">[out] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) values.</span></span>  
  
 `cMax`  
 <span data-ttu-id="17be9-109">[in] `rFieldOffset` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="17be9-109">[in] The maximum size of the `rFieldOffset` array.</span></span>  
  
 `pcFieldOffset`  
 <span data-ttu-id="17be9-110">[出]中`rFieldOffset`返回的元素數。</span><span class="sxs-lookup"><span data-stu-id="17be9-110">[out] The number of elements returned in `rFieldOffset`.</span></span>  
  
 `pulClassSize`  
 <span data-ttu-id="17be9-111">[出]以 的類大小（以位元組為單位）。 `td`</span><span class="sxs-lookup"><span data-stu-id="17be9-111">[out] The size in bytes of the class represented by `td`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17be9-112">需求</span><span class="sxs-lookup"><span data-stu-id="17be9-112">Requirements</span></span>  
 <span data-ttu-id="17be9-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="17be9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17be9-114">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="17be9-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="17be9-115">**庫：** 作為資源包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="17be9-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="17be9-116">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17be9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17be9-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17be9-117">See also</span></span>

- [<span data-ttu-id="17be9-118">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="17be9-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="17be9-119">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="17be9-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
