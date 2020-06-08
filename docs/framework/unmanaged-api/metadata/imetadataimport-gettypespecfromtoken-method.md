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
ms.openlocfilehash: 43e9671afa92d36966e51bbdc630db4a9d9083b7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503496"
---
# <a name="imetadataimportgettypespecfromtoken-method"></a><span data-ttu-id="6cf84-102">IMetaDataImport::GetTypeSpecFromToken 方法</span><span class="sxs-lookup"><span data-stu-id="6cf84-102">IMetaDataImport::GetTypeSpecFromToken Method</span></span>
<span data-ttu-id="6cf84-103">取得指定語彙基元所代表類型規格的二進位中繼資料簽章。</span><span class="sxs-lookup"><span data-stu-id="6cf84-103">Gets the binary metadata signature of the type specification represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cf84-104">語法</span><span class="sxs-lookup"><span data-stu-id="6cf84-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeSpecFromToken (
   [in]  mdTypeSpec            typespec,
   [out] PCCOR_SIGNATURE       *ppvSig,
   [out] ULONG                 *pcbSig  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6cf84-105">參數</span><span class="sxs-lookup"><span data-stu-id="6cf84-105">Parameters</span></span>  
 `typespec`  
 <span data-ttu-id="6cf84-106">在與所要求之中繼資料簽章相關聯的 TypeSpec token。</span><span class="sxs-lookup"><span data-stu-id="6cf84-106">[in] The TypeSpec token associated with the requested metadata signature.</span></span>  
  
 `ppvSig`  
 <span data-ttu-id="6cf84-107">脫銷二進位中繼資料簽章的指標。</span><span class="sxs-lookup"><span data-stu-id="6cf84-107">[out] A pointer to the binary metadata signature.</span></span>  
  
 `pcbSig`  
 <span data-ttu-id="6cf84-108">脫銷中繼資料簽章的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="6cf84-108">[out] The size, in bytes, of the metadata signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6cf84-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="6cf84-109">Return Value</span></span>  
 <span data-ttu-id="6cf84-110">表示成功或失敗的 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="6cf84-110">An HRESULT that indicates success or failure.</span></span> <span data-ttu-id="6cf84-111">您可以使用 FAILED 宏來測試失敗。</span><span class="sxs-lookup"><span data-stu-id="6cf84-111">Failures can be tested with the FAILED macro.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cf84-112">規格需求</span><span class="sxs-lookup"><span data-stu-id="6cf84-112">Requirements</span></span>  
 <span data-ttu-id="6cf84-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6cf84-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cf84-114">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="6cf84-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6cf84-115">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6cf84-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6cf84-116">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cf84-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cf84-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6cf84-117">See also</span></span>

- [<span data-ttu-id="6cf84-118">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="6cf84-118">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="6cf84-119">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="6cf84-119">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
