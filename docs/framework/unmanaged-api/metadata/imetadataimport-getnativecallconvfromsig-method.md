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
ms.openlocfilehash: 06ff6a1885a5e9bb819c2897aaf85e5c2b9b1147
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437247"
---
# <a name="imetadataimportgetnativecallconvfromsig-method"></a><span data-ttu-id="12571-102">IMetaDataImport::GetNativeCallConvFromSig 方法</span><span class="sxs-lookup"><span data-stu-id="12571-102">IMetaDataImport::GetNativeCallConvFromSig Method</span></span>
<span data-ttu-id="12571-103">取得由指定簽章指標代表的方法之原生呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="12571-103">Gets the native calling convention for the method that is represented by the specified signature pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12571-104">語法</span><span class="sxs-lookup"><span data-stu-id="12571-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNativeCallConvFromSig (  
   [in]  void const  *pvSig,  
   [in]  ULONG       cbSig,  
   [out] ULONG       *pCallConv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12571-105">參數</span><span class="sxs-lookup"><span data-stu-id="12571-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="12571-106">在方法的中繼資料簽章指標，可傳回的呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="12571-106">[in] A pointer to the metadata signature of the method to return the calling convention for.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="12571-107">在`pvSig`的大小（以位元組為單位）。</span><span class="sxs-lookup"><span data-stu-id="12571-107">[in] The size in bytes of `pvSig`.</span></span>  
  
 `pCallConv`  
 <span data-ttu-id="12571-108">脫銷原生呼叫慣例的指標。</span><span class="sxs-lookup"><span data-stu-id="12571-108">[out] A pointer to the native calling convention.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12571-109">需求</span><span class="sxs-lookup"><span data-stu-id="12571-109">Requirements</span></span>  
 <span data-ttu-id="12571-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="12571-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12571-111">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="12571-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="12571-112">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="12571-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="12571-113">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12571-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12571-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="12571-114">See also</span></span>

- <xref:System.Runtime.InteropServices.CallingConvention>
- [<span data-ttu-id="12571-115">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="12571-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="12571-116">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="12571-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
