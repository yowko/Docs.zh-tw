---
title: IMetaDataImport2::GetGenericParamProps 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetGenericParamProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetGenericParamProps
helpviewer_keywords:
- IMetaDataImport2::GetGenericParamProps method [.NET Framework metadata]
- GetGenericParamProps method [.NET Framework metadata]
ms.assetid: dbb21e67-712b-49e7-a27c-a1e73ffd46c5
topic_type:
- apiref
ms.openlocfilehash: a8c5dd263401002deaee3d21f1e41b41a29faec2
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427304"
---
# <a name="imetadataimport2getgenericparamprops-method"></a><span data-ttu-id="bdf4b-102">IMetaDataImport2::GetGenericParamProps 方法</span><span class="sxs-lookup"><span data-stu-id="bdf4b-102">IMetaDataImport2::GetGenericParamProps Method</span></span>
<span data-ttu-id="bdf4b-103">取得與指定標記所表示的泛型參數相關聯的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="bdf4b-103">Gets the metadata associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdf4b-104">語法</span><span class="sxs-lookup"><span data-stu-id="bdf4b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGenericParamProps (  
   [in]  mdGenericParam  gp,  
   [out] ULONG           *pulParamSeq,  
   [out] DWORD           *pdwParamFlags,  
   [out] mdToken         *ptOwner,  
   [out] DWORD           *reserved,  
   [out] LPWSTR          wzName,  
   [in]  ULONG           cchName,  
   [out] ULONG           *pchName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bdf4b-105">參數</span><span class="sxs-lookup"><span data-stu-id="bdf4b-105">Parameters</span></span>  
 `gp`  
 <span data-ttu-id="bdf4b-106">在Token，代表要傳回中繼資料的泛型參數。</span><span class="sxs-lookup"><span data-stu-id="bdf4b-106">[in] The token that represents the generic parameter for which to return metadata.</span></span>  
  
 `pulParamSeq`  
 <span data-ttu-id="bdf4b-107">脫銷父函數或方法中 `Type` 參數的序數位置。</span><span class="sxs-lookup"><span data-stu-id="bdf4b-107">[out] The ordinal position of the `Type` parameter in the parent constructor or method.</span></span>  
  
 `pdwParamFlags`  
 <span data-ttu-id="bdf4b-108">脫銷[CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md)列舉的值，描述泛型參數的 `Type`。</span><span class="sxs-lookup"><span data-stu-id="bdf4b-108">[out] A value of the [CorGenericParamAttr](../../../../docs/framework/unmanaged-api/metadata/corgenericparamattr-enumeration.md) enumeration that describes the `Type` for the generic parameter.</span></span>  
  
 `ptOwner`  
 <span data-ttu-id="bdf4b-109">脫銷表示參數擁有者的 TypeDef 或 MethodDef token。</span><span class="sxs-lookup"><span data-stu-id="bdf4b-109">[out] A TypeDef or MethodDef token that represents the owner of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="bdf4b-110">脫銷保留以供未來擴充性之用。</span><span class="sxs-lookup"><span data-stu-id="bdf4b-110">[out] Reserved for future extensibility.</span></span>  
  
 `wzName`  
 <span data-ttu-id="bdf4b-111">脫銷泛型參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="bdf4b-111">[out] The name of the generic parameter.</span></span>  
  
 `cchName`  
 <span data-ttu-id="bdf4b-112">在`wzName` 緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="bdf4b-112">[in] The size of the `wzName` buffer.</span></span>  
  
 `pchName`  
 <span data-ttu-id="bdf4b-113">脫銷傳回的名稱大小（以寬字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="bdf4b-113">[out] The returned size of the name, in wide characters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdf4b-114">需求</span><span class="sxs-lookup"><span data-stu-id="bdf4b-114">Requirements</span></span>  
 <span data-ttu-id="bdf4b-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bdf4b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdf4b-116">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="bdf4b-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bdf4b-117">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="bdf4b-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bdf4b-118">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdf4b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdf4b-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bdf4b-119">See also</span></span>

- [<span data-ttu-id="bdf4b-120">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="bdf4b-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="bdf4b-121">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="bdf4b-121">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
