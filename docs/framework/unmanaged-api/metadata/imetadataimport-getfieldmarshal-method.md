---
title: IMetaDataImport::GetFieldMarshal 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetFieldMarshal
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetFieldMarshal
helpviewer_keywords:
- GetFieldMarshal method [.NET Framework metadata]
- IMetaDataImport::GetFieldMarshal method [.NET Framework metadata]
ms.assetid: 4e2d88c6-8a3a-4fbe-900b-b4f4c06bf6bf
topic_type:
- apiref
ms.openlocfilehash: 35f73135dbeea1c79d15e0a9e9367c5d533487ce
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676853"
---
# <a name="imetadataimportgetfieldmarshal-method"></a><span data-ttu-id="8ecaf-102">IMetaDataImport::GetFieldMarshal 方法</span><span class="sxs-lookup"><span data-stu-id="8ecaf-102">IMetaDataImport::GetFieldMarshal Method</span></span>

<span data-ttu-id="8ecaf-103">取得指定之欄位元資料標記所代表之欄位的原生非受控型別指標。</span><span class="sxs-lookup"><span data-stu-id="8ecaf-103">Gets a pointer to the native, unmanaged type of the field represented by the specified field metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ecaf-104">語法</span><span class="sxs-lookup"><span data-stu-id="8ecaf-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFieldMarshal (  
   [in]  mdToken             tk,
   [out] PCCOR_SIGNATURE     *ppvNativeType,  
   [out] ULONG               *pcbNativeType
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ecaf-105">參數</span><span class="sxs-lookup"><span data-stu-id="8ecaf-105">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="8ecaf-106">在元資料標記，代表要取得其 interop 封送處理資訊的欄位。</span><span class="sxs-lookup"><span data-stu-id="8ecaf-106">[in] The metadata token that represents the field to get interop marshaling information for.</span></span>  
  
 `ppvNativeType`  
 <span data-ttu-id="8ecaf-107">擴展欄位原生類型的中繼資料簽章指標。</span><span class="sxs-lookup"><span data-stu-id="8ecaf-107">[out] A pointer to the metadata signature of the field's native type.</span></span>  
  
 `pcbNativeType`  
 <span data-ttu-id="8ecaf-108">擴展的大小（以位元組為單位） `ppvNativeType` 。</span><span class="sxs-lookup"><span data-stu-id="8ecaf-108">[out] The size in bytes of `ppvNativeType`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ecaf-109">需求</span><span class="sxs-lookup"><span data-stu-id="8ecaf-109">Requirements</span></span>  

 <span data-ttu-id="8ecaf-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8ecaf-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ecaf-111">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="8ecaf-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8ecaf-112">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="8ecaf-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8ecaf-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ecaf-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ecaf-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ecaf-114">See also</span></span>

- [<span data-ttu-id="8ecaf-115">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="8ecaf-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="8ecaf-116">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="8ecaf-116">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
