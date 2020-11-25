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
ms.openlocfilehash: 16f69d571ffed87a2e848124ce16ac942d319c37
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702676"
---
# <a name="imetadataimport2getgenericparamprops-method"></a><span data-ttu-id="77ba2-102">IMetaDataImport2::GetGenericParamProps 方法</span><span class="sxs-lookup"><span data-stu-id="77ba2-102">IMetaDataImport2::GetGenericParamProps Method</span></span>

<span data-ttu-id="77ba2-103">取得與指定標記所表示之泛型參數相關聯的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="77ba2-103">Gets the metadata associated with the generic parameter represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77ba2-104">語法</span><span class="sxs-lookup"><span data-stu-id="77ba2-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="77ba2-105">參數</span><span class="sxs-lookup"><span data-stu-id="77ba2-105">Parameters</span></span>  

 `gp`  
 <span data-ttu-id="77ba2-106">在代表要傳回中繼資料之泛型參數的 token。</span><span class="sxs-lookup"><span data-stu-id="77ba2-106">[in] The token that represents the generic parameter for which to return metadata.</span></span>  
  
 `pulParamSeq`  
 <span data-ttu-id="77ba2-107">擴展 `Type` 參數在父函式或方法中的序數位置。</span><span class="sxs-lookup"><span data-stu-id="77ba2-107">[out] The ordinal position of the `Type` parameter in the parent constructor or method.</span></span>  
  
 `pdwParamFlags`  
 <span data-ttu-id="77ba2-108">擴展描述泛型參數之的 [CorGenericParamAttr](corgenericparamattr-enumeration.md) 列舉值 `Type` 。</span><span class="sxs-lookup"><span data-stu-id="77ba2-108">[out] A value of the [CorGenericParamAttr](corgenericparamattr-enumeration.md) enumeration that describes the `Type` for the generic parameter.</span></span>  
  
 `ptOwner`  
 <span data-ttu-id="77ba2-109">擴展代表參數擁有者的 TypeDef 或 MethodDef token。</span><span class="sxs-lookup"><span data-stu-id="77ba2-109">[out] A TypeDef or MethodDef token that represents the owner of the parameter.</span></span>  
  
 `reserved`  
 <span data-ttu-id="77ba2-110">擴展保留供未來擴充性之用。</span><span class="sxs-lookup"><span data-stu-id="77ba2-110">[out] Reserved for future extensibility.</span></span>  
  
 `wzName`  
 <span data-ttu-id="77ba2-111">擴展泛型參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="77ba2-111">[out] The name of the generic parameter.</span></span>  
  
 `cchName`  
 <span data-ttu-id="77ba2-112">在緩衝區的大小 `wzName` 。</span><span class="sxs-lookup"><span data-stu-id="77ba2-112">[in] The size of the `wzName` buffer.</span></span>  
  
 `pchName`  
 <span data-ttu-id="77ba2-113">擴展傳回的名稱大小（以寬字元為單位）。</span><span class="sxs-lookup"><span data-stu-id="77ba2-113">[out] The returned size of the name, in wide characters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77ba2-114">需求</span><span class="sxs-lookup"><span data-stu-id="77ba2-114">Requirements</span></span>  

 <span data-ttu-id="77ba2-115">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="77ba2-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77ba2-116">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="77ba2-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="77ba2-117">連結 **庫：** 當做 MsCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="77ba2-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="77ba2-118">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77ba2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77ba2-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77ba2-119">See also</span></span>

- [<span data-ttu-id="77ba2-120">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="77ba2-120">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="77ba2-121">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="77ba2-121">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
