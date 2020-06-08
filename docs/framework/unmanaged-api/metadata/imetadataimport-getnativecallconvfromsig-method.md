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
ms.openlocfilehash: 44439eda62f85c32893b73f17bd057195cf6b2e1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503545"
---
# <a name="imetadataimportgetnativecallconvfromsig-method"></a><span data-ttu-id="8e58c-102">IMetaDataImport::GetNativeCallConvFromSig 方法</span><span class="sxs-lookup"><span data-stu-id="8e58c-102">IMetaDataImport::GetNativeCallConvFromSig Method</span></span>
<span data-ttu-id="8e58c-103">取得由指定簽章指標代表的方法之原生呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="8e58c-103">Gets the native calling convention for the method that is represented by the specified signature pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e58c-104">語法</span><span class="sxs-lookup"><span data-stu-id="8e58c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNativeCallConvFromSig (  
   [in]  void const  *pvSig,  
   [in]  ULONG       cbSig,  
   [out] ULONG       *pCallConv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8e58c-105">參數</span><span class="sxs-lookup"><span data-stu-id="8e58c-105">Parameters</span></span>  
 `pvSig`  
 <span data-ttu-id="8e58c-106">在方法的中繼資料簽章指標，可傳回的呼叫慣例。</span><span class="sxs-lookup"><span data-stu-id="8e58c-106">[in] A pointer to the metadata signature of the method to return the calling convention for.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="8e58c-107">在的大小（以位元組為單位） `pvSig` 。</span><span class="sxs-lookup"><span data-stu-id="8e58c-107">[in] The size in bytes of `pvSig`.</span></span>  
  
 `pCallConv`  
 <span data-ttu-id="8e58c-108">脫銷原生呼叫慣例的指標。</span><span class="sxs-lookup"><span data-stu-id="8e58c-108">[out] A pointer to the native calling convention.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e58c-109">規格需求</span><span class="sxs-lookup"><span data-stu-id="8e58c-109">Requirements</span></span>  
 <span data-ttu-id="8e58c-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8e58c-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8e58c-111">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="8e58c-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8e58c-112">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="8e58c-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8e58c-113">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8e58c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e58c-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e58c-114">See also</span></span>

- <xref:System.Runtime.InteropServices.CallingConvention>
- [<span data-ttu-id="8e58c-115">IMetaDataImport 介面</span><span class="sxs-lookup"><span data-stu-id="8e58c-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="8e58c-116">IMetaDataImport2 介面</span><span class="sxs-lookup"><span data-stu-id="8e58c-116">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
