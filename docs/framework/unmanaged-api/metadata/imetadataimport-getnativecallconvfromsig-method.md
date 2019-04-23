---
title: IMetaDataImport::GetNativeCallConvFromSig 方法
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetNativeCallConvFromSig
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetNativeCallConvFromSig
helpviewer_keywords:
- GetNativeCallConvFromSig method [.NET Framework metadata]
- IMetaDataImport::GetNativeCallConvFromSig method [.NET Framework metadata]
ms.assetid: 50e04026-4d4a-47d9-96c1-f4677d6d938b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ef1ac83b383a9f6bbee7f55441d2abfcb081afa6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59122742"
---
# <a name="imetadataimportgetnativecallconvfromsig-method"></a><span data-ttu-id="96057-102">IMetaDataImport::GetNativeCallConvFromSig 方法</span><span class="sxs-lookup"><span data-stu-id="96057-102">IMetaDataImport::GetNativeCallConvFromSig Method</span></span>
<span data-ttu-id="96057-103">取得由指定簽章指標代表的方法之原生呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="96057-103">Gets the native calling convention for the method that is represented by the specified signature pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96057-104">語法</span><span class="sxs-lookup"><span data-stu-id="96057-104">Syntax</span></span>  
  
```  
HRESULT GetNativeCallConvFromSig (  
   [in]  void const  *pvSig,  
   [in]  ULONG       cbSig,  
   [out] ULONG       *pCallConv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96057-105">參數</span><span class="sxs-lookup"><span data-stu-id="96057-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="96057-106">[in]中繼資料簽章，這個方法傳回的呼叫慣例的指標。</span><span class="sxs-lookup"><span data-stu-id="96057-106">[in] A pointer to the metadata signature of the method to return the calling convention for.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="96057-107">[in]以位元組為單位的大小`pvSig`。</span><span class="sxs-lookup"><span data-stu-id="96057-107">[in] The size in bytes of `pvSig`.</span></span>  
  
 `pCallConv`  
 <span data-ttu-id="96057-108">[out]指標的原生呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="96057-108">[out] A pointer to the native calling convention.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96057-109">需求</span><span class="sxs-lookup"><span data-stu-id="96057-109">Requirements</span></span>  
 <span data-ttu-id="96057-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="96057-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96057-111">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="96057-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="96057-112">**LIBRARY:** 包含做為 MsCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="96057-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="96057-113">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96057-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96057-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="96057-114">See also</span></span>

- <xref:System.Runtime.InteropServices.CallingConvention>
- [<span data-ttu-id="96057-115">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="96057-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="96057-116">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="96057-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
