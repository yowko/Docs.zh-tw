---
title: IMetaDataImport::GetTypeSpecFromToken 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetTypeSpecFromToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeSpecFromToken
helpviewer_keywords:
- GetTypeSpecFromToken method [.NET Framework metadata]
- IMetaDataImport::GetTypeSpecFromToken method [.NET Framework metadata]
ms.assetid: ee518bda-3296-482e-a7b7-e9d51dd1a181
topic_type:
- apiref
ms.openlocfilehash: 3ab24ab869e1f2cff9beafe50e6982ba2e7cf0aa
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436700"
---
# <a name="imetadataimportgettypespecfromtoken-method"></a><span data-ttu-id="c8898-102">IMetaDataImport::GetTypeSpecFromToken 方法</span><span class="sxs-lookup"><span data-stu-id="c8898-102">IMetaDataImport::GetTypeSpecFromToken Method</span></span>
<span data-ttu-id="c8898-103">取得指定語彙基元所代表類型規格的二進位中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="c8898-103">Gets the binary metadata signature of the type specification represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8898-104">語法</span><span class="sxs-lookup"><span data-stu-id="c8898-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeSpecFromToken (   
   [in]  mdTypeSpec            typespec,   
   [out] PCCOR_SIGNATURE       *ppvSig,   
   [out] ULONG                 *pcbSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8898-105">參數</span><span class="sxs-lookup"><span data-stu-id="c8898-105">Parameters</span></span>  
 `typespec`  
 <span data-ttu-id="c8898-106">[in] The TypeSpec token associated with the requested metadata signature.</span><span class="sxs-lookup"><span data-stu-id="c8898-106">[in] The TypeSpec token associated with the requested metadata signature.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="c8898-107">[out] A pointer to the binary metadata signature.</span><span class="sxs-lookup"><span data-stu-id="c8898-107">[out] A pointer to the binary metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="c8898-108">[out] The size, in bytes, of the metadata signature.</span><span class="sxs-lookup"><span data-stu-id="c8898-108">[out] The size, in bytes, of the metadata signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c8898-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="c8898-109">Return Value</span></span>  
 <span data-ttu-id="c8898-110">An HRESULT that indicates success or failure.</span><span class="sxs-lookup"><span data-stu-id="c8898-110">An HRESULT that indicates success or failure.</span></span> <span data-ttu-id="c8898-111">Failures can be tested with the FAILED macro.</span><span class="sxs-lookup"><span data-stu-id="c8898-111">Failures can be tested with the FAILED macro.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8898-112">需求</span><span class="sxs-lookup"><span data-stu-id="c8898-112">Requirements</span></span>  
 <span data-ttu-id="c8898-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c8898-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8898-114">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c8898-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c8898-115">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c8898-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c8898-116">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8898-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8898-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="c8898-117">See also</span></span>

- [<span data-ttu-id="c8898-118">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="c8898-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="c8898-119">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="c8898-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
