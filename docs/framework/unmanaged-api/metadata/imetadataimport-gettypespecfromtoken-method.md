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
ms.openlocfilehash: 34b7cebfa063a3ad077b74a753fd37ba67ff53a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175313"
---
# <a name="imetadataimportgettypespecfromtoken-method"></a><span data-ttu-id="5e2aa-102">IMetaDataImport::GetTypeSpecFromToken 方法</span><span class="sxs-lookup"><span data-stu-id="5e2aa-102">IMetaDataImport::GetTypeSpecFromToken Method</span></span>
<span data-ttu-id="5e2aa-103">取得指定語彙基元所代表類型規格的二進位中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="5e2aa-103">Gets the binary metadata signature of the type specification represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e2aa-104">語法</span><span class="sxs-lookup"><span data-stu-id="5e2aa-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeSpecFromToken (
   [in]  mdTypeSpec            typespec,
   [out] PCCOR_SIGNATURE       *ppvSig,
   [out] ULONG                 *pcbSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e2aa-105">參數</span><span class="sxs-lookup"><span data-stu-id="5e2aa-105">Parameters</span></span>  
 `typespec`  
 <span data-ttu-id="5e2aa-106">[在]與請求的中繼資料簽名關聯的 TypeSpec 權杖。</span><span class="sxs-lookup"><span data-stu-id="5e2aa-106">[in] The TypeSpec token associated with the requested metadata signature.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="5e2aa-107">[出]指向二進位中繼資料簽名的指標。</span><span class="sxs-lookup"><span data-stu-id="5e2aa-107">[out] A pointer to the binary metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="5e2aa-108">[出]中繼資料簽名的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="5e2aa-108">[out] The size, in bytes, of the metadata signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5e2aa-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="5e2aa-109">Return Value</span></span>  
 <span data-ttu-id="5e2aa-110">指示成功或失敗的 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="5e2aa-110">An HRESULT that indicates success or failure.</span></span> <span data-ttu-id="5e2aa-111">可以使用 FAILED 宏測試故障。</span><span class="sxs-lookup"><span data-stu-id="5e2aa-111">Failures can be tested with the FAILED macro.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e2aa-112">需求</span><span class="sxs-lookup"><span data-stu-id="5e2aa-112">Requirements</span></span>  
 <span data-ttu-id="5e2aa-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5e2aa-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e2aa-114">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="5e2aa-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5e2aa-115">**庫：** 作為資源包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="5e2aa-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5e2aa-116">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e2aa-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e2aa-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e2aa-117">See also</span></span>

- [<span data-ttu-id="5e2aa-118">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="5e2aa-118">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="5e2aa-119">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="5e2aa-119">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
