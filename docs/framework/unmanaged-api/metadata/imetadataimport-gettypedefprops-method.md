---
title: IMetaDataImport::GetTypeDefProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetTypeDefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeDefProps
helpviewer_keywords:
- GetTypeDefProps method [.NET Framework metadata]
- IMetaDataImport::GetTypeDefProps method [.NET Framework metadata]
ms.assetid: 00061a25-ba05-47a7-b984-fd916b06b149
topic_type:
- apiref
ms.openlocfilehash: 6346b1e34e508e5c173bfd0119ac7451d7eef40e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490792"
---
# <a name="imetadataimportgettypedefprops-method"></a><span data-ttu-id="85b35-102">IMetaDataImport::GetTypeDefProps 方法</span><span class="sxs-lookup"><span data-stu-id="85b35-102">IMetaDataImport::GetTypeDefProps Method</span></span>
<span data-ttu-id="85b35-103">傳回指定之 TypeDef token 所表示之的中繼資料資訊 <xref:System.Type> 。</span><span class="sxs-lookup"><span data-stu-id="85b35-103">Returns metadata information for the <xref:System.Type> represented by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85b35-104">語法</span><span class="sxs-lookup"><span data-stu-id="85b35-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeDefProps (  
   [in]  mdTypeDef   td,  
   [out] LPWSTR      szTypeDef,  
   [in]  ULONG       cchTypeDef,  
   [out] ULONG       *pchTypeDef,  
   [out] DWORD       *pdwTypeDefFlags,  
   [out] mdToken     *ptkExtends  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85b35-105">參數</span><span class="sxs-lookup"><span data-stu-id="85b35-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="85b35-106">在TypeDef token，表示要傳回中繼資料的類型。</span><span class="sxs-lookup"><span data-stu-id="85b35-106">[in] The TypeDef token that represents the type to return metadata for.</span></span>  
  
 `szTypeDef`  
 <span data-ttu-id="85b35-107">脫銷包含型別名稱的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="85b35-107">[out] A buffer containing the type name.</span></span>  
  
 `cchTypeDef`  
 <span data-ttu-id="85b35-108">在的大小（以寬字元為單位） `szTypeDef` 。</span><span class="sxs-lookup"><span data-stu-id="85b35-108">[in] The size in wide characters of `szTypeDef`.</span></span>  
  
 `pchTypeDef`  
 <span data-ttu-id="85b35-109">脫銷在中傳回的寬字元數 `szTypeDef` 。</span><span class="sxs-lookup"><span data-stu-id="85b35-109">[out] The number of wide characters returned in `szTypeDef`.</span></span>  
  
 `pdwTypeDefFlags`  
 <span data-ttu-id="85b35-110">脫銷任何修改類型定義之旗標的指標。</span><span class="sxs-lookup"><span data-stu-id="85b35-110">[out] A pointer to any flags that modify the type definition.</span></span> <span data-ttu-id="85b35-111">這個值是[CorTypeAttr](cortypeattr-enumeration.md)列舉中的位元遮罩。</span><span class="sxs-lookup"><span data-stu-id="85b35-111">This value is a bitmask from the [CorTypeAttr](cortypeattr-enumeration.md) enumeration.</span></span>  
  
 `ptkExtends`  
 <span data-ttu-id="85b35-112">脫銷TypeDef 或 TypeRef 元資料標記，代表所要求之類型的基底類型。</span><span class="sxs-lookup"><span data-stu-id="85b35-112">[out] A TypeDef or TypeRef metadata token that represents the base type of the requested type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85b35-113">規格需求</span><span class="sxs-lookup"><span data-stu-id="85b35-113">Requirements</span></span>  
 <span data-ttu-id="85b35-114">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="85b35-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85b35-115">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="85b35-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="85b35-116">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="85b35-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="85b35-117">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85b35-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85b35-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85b35-118">See also</span></span>

- [<span data-ttu-id="85b35-119">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="85b35-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="85b35-120">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="85b35-120">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
