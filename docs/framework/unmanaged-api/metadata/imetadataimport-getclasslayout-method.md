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
ms.openlocfilehash: 8360a74e9e18e5b68ecc9edd7be2e3a711cb61c9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437775"
---
# <a name="imetadataimportgetclasslayout-method"></a><span data-ttu-id="2cb95-102">IMetaDataImport::GetClassLayout 方法</span><span class="sxs-lookup"><span data-stu-id="2cb95-102">IMetaDataImport::GetClassLayout Method</span></span>
<span data-ttu-id="2cb95-103">取得指定 TypeDef 語彙基元所參考類別的配置資訊。</span><span class="sxs-lookup"><span data-stu-id="2cb95-103">Gets layout information for the class referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cb95-104">語法</span><span class="sxs-lookup"><span data-stu-id="2cb95-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="2cb95-105">參數</span><span class="sxs-lookup"><span data-stu-id="2cb95-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="2cb95-106">在具有要傳回之配置的類別的 TypeDef token。</span><span class="sxs-lookup"><span data-stu-id="2cb95-106">[in] The TypeDef token for the class with the layout to return.</span></span>  
  
 `pdwPackSize`  
 <span data-ttu-id="2cb95-107">脫銷其中一個值為1、2、4、8或16，代表類別的套件大小。</span><span class="sxs-lookup"><span data-stu-id="2cb95-107">[out] One of the values 1, 2, 4, 8, or 16, representing the pack size of the class.</span></span>  
  
 `rFieldOffset`  
 <span data-ttu-id="2cb95-108">脫銷[COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md)值的陣列。</span><span class="sxs-lookup"><span data-stu-id="2cb95-108">[out] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) values.</span></span>  
  
 `cMax`  
 <span data-ttu-id="2cb95-109">[in] `rFieldOffset` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="2cb95-109">[in] The maximum size of the `rFieldOffset` array.</span></span>  
  
 `pcFieldOffset`  
 <span data-ttu-id="2cb95-110">脫銷`rFieldOffset`中傳回的元素數目。</span><span class="sxs-lookup"><span data-stu-id="2cb95-110">[out] The number of elements returned in `rFieldOffset`.</span></span>  
  
 `pulClassSize`  
 <span data-ttu-id="2cb95-111">脫銷`td`所代表之類別的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="2cb95-111">[out] The size in bytes of the class represented by `td`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2cb95-112">需求</span><span class="sxs-lookup"><span data-stu-id="2cb95-112">Requirements</span></span>  
 <span data-ttu-id="2cb95-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2cb95-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2cb95-114">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="2cb95-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2cb95-115">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="2cb95-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2cb95-116">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2cb95-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cb95-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2cb95-117">See also</span></span>

- [<span data-ttu-id="2cb95-118">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="2cb95-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="2cb95-119">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="2cb95-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
