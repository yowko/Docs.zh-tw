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
ms.openlocfilehash: 36c0ffef2d984604be4ae19899e8f3f912cee123
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491468"
---
# <a name="imetadataimportgetclasslayout-method"></a><span data-ttu-id="04c9c-102">IMetaDataImport::GetClassLayout 方法</span><span class="sxs-lookup"><span data-stu-id="04c9c-102">IMetaDataImport::GetClassLayout Method</span></span>
<span data-ttu-id="04c9c-103">取得指定 TypeDef 語彙基元所參考類別的配置資訊。</span><span class="sxs-lookup"><span data-stu-id="04c9c-103">Gets layout information for the class referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04c9c-104">語法</span><span class="sxs-lookup"><span data-stu-id="04c9c-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="04c9c-105">參數</span><span class="sxs-lookup"><span data-stu-id="04c9c-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="04c9c-106">在具有要傳回之配置的類別的 TypeDef token。</span><span class="sxs-lookup"><span data-stu-id="04c9c-106">[in] The TypeDef token for the class with the layout to return.</span></span>  
  
 `pdwPackSize`  
 <span data-ttu-id="04c9c-107">脫銷其中一個值為1、2、4、8或16，代表類別的套件大小。</span><span class="sxs-lookup"><span data-stu-id="04c9c-107">[out] One of the values 1, 2, 4, 8, or 16, representing the pack size of the class.</span></span>  
  
 `rFieldOffset`  
 <span data-ttu-id="04c9c-108">脫銷[COR_FIELD_OFFSET](cor-field-offset-structure.md)值的陣列。</span><span class="sxs-lookup"><span data-stu-id="04c9c-108">[out] An array of [COR_FIELD_OFFSET](cor-field-offset-structure.md) values.</span></span>  
  
 `cMax`  
 <span data-ttu-id="04c9c-109">[in] `rFieldOffset` 陣列的大小上限。</span><span class="sxs-lookup"><span data-stu-id="04c9c-109">[in] The maximum size of the `rFieldOffset` array.</span></span>  
  
 `pcFieldOffset`  
 <span data-ttu-id="04c9c-110">脫銷在中傳回的元素數目 `rFieldOffset` 。</span><span class="sxs-lookup"><span data-stu-id="04c9c-110">[out] The number of elements returned in `rFieldOffset`.</span></span>  
  
 `pulClassSize`  
 <span data-ttu-id="04c9c-111">脫銷所表示之類別的大小（以位元組為單位） `td` 。</span><span class="sxs-lookup"><span data-stu-id="04c9c-111">[out] The size in bytes of the class represented by `td`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04c9c-112">規格需求</span><span class="sxs-lookup"><span data-stu-id="04c9c-112">Requirements</span></span>  
 <span data-ttu-id="04c9c-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="04c9c-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04c9c-114">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="04c9c-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="04c9c-115">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="04c9c-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="04c9c-116">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04c9c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04c9c-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04c9c-117">See also</span></span>

- [<span data-ttu-id="04c9c-118">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="04c9c-118">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="04c9c-119">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="04c9c-119">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
