---
title: IMetaDataEmit::SetFieldMarshal 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldMarshal
helpviewer_keywords:
- SetFieldMarshal method [.NET Framework metadata]
- IMetaDataEmit::SetFieldMarshal method [.NET Framework metadata]
ms.assetid: be232314-7f69-4855-bfab-63361bd22307
topic_type:
- apiref
ms.openlocfilehash: 1037cd4210605192870d43d88979b89af6536380
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175651"
---
# <a name="imetadataemitsetfieldmarshal-method"></a><span data-ttu-id="61cca-102">IMetaDataEmit::SetFieldMarshal 方法</span><span class="sxs-lookup"><span data-stu-id="61cca-102">IMetaDataEmit::SetFieldMarshal Method</span></span>
<span data-ttu-id="61cca-103">為指定權杖引用的欄位、方法返回或方法參數設置 PInvoke 封送資訊。</span><span class="sxs-lookup"><span data-stu-id="61cca-103">Sets the PInvoke marshaling information for the field, method return, or method parameter referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61cca-104">語法</span><span class="sxs-lookup"><span data-stu-id="61cca-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldMarshal (  
    [in]  mdToken          tk,
    [in]  PCCOR_SIGNATURE  pvNativeType,
    [in]  ULONG            cbNativeType
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61cca-105">參數</span><span class="sxs-lookup"><span data-stu-id="61cca-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="61cca-106">[在]目標資料項目的權杖。</span><span class="sxs-lookup"><span data-stu-id="61cca-106">[in] The token for target data item.</span></span> <span data-ttu-id="61cca-107">這是 或`mdFieldDef``mdParamDef`標記。</span><span class="sxs-lookup"><span data-stu-id="61cca-107">This is either a `mdFieldDef` or a `mdParamDef` token.</span></span>  
  
 `pvNativeType`  
 <span data-ttu-id="61cca-108">[在]非託管類型的簽名。</span><span class="sxs-lookup"><span data-stu-id="61cca-108">[in] The signature for unmanaged type.</span></span>  
  
 `cbNativeType`  
 <span data-ttu-id="61cca-109">[在]中的`pvNativeType`位元組計數。</span><span class="sxs-lookup"><span data-stu-id="61cca-109">[in] The count of bytes in `pvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61cca-110">需求</span><span class="sxs-lookup"><span data-stu-id="61cca-110">Requirements</span></span>  
 <span data-ttu-id="61cca-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="61cca-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61cca-112">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="61cca-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="61cca-113">**庫：** 用作 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="61cca-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="61cca-114">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61cca-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61cca-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61cca-115">See also</span></span>

- [<span data-ttu-id="61cca-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="61cca-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="61cca-117">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="61cca-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
