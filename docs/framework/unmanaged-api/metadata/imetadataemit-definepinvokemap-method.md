---
title: IMetaDataEmit::DefinePinvokeMap 方法
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefinePinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefinePinvokeMap
helpviewer_keywords:
- DefinePinvokeMap method [.NET Framework metadata]
- IMetaDataEmit::DefinePinvokeMap method [.NET Framework metadata]
ms.assetid: 03abf921-5154-4070-88fa-10b7092901fb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 480fedc8ae63ffa3222a74e39297cc64b6812e97
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444487"
---
# <a name="imetadataemitdefinepinvokemap-method"></a><span data-ttu-id="a48c2-102">IMetaDataEmit::DefinePinvokeMap 方法</span><span class="sxs-lookup"><span data-stu-id="a48c2-102">IMetaDataEmit::DefinePinvokeMap Method</span></span>
<span data-ttu-id="a48c2-103">設定指定的語彙基元所參考之方法的 PInvoke 簽章的功能。</span><span class="sxs-lookup"><span data-stu-id="a48c2-103">Sets features of the PInvoke signature of the method referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a48c2-104">語法</span><span class="sxs-lookup"><span data-stu-id="a48c2-104">Syntax</span></span>  
  
```  
HRESULT DefinePinvokeMap (   
    [in]  mdToken            tk,   
    [in]  DWORD              dwMappingFlags,   
    [in]  LPCWSTR            szImportName,   
    [in]  mdModuleRef        mrImportDLL   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a48c2-105">參數</span><span class="sxs-lookup"><span data-stu-id="a48c2-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="a48c2-106">[in]目標方法的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="a48c2-106">[in] The token for the target method.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="a48c2-107">[in]用來執行對應 PInvoke 旗標。</span><span class="sxs-lookup"><span data-stu-id="a48c2-107">[in] Flags used by PInvoke to do the mapping.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="a48c2-108">[in]Unmanaged DLL 中的方法匯出目標的名稱。</span><span class="sxs-lookup"><span data-stu-id="a48c2-108">[in] The name of the target export method in an unmanaged DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="a48c2-109">[in]目標的語彙基元原生 DLL。</span><span class="sxs-lookup"><span data-stu-id="a48c2-109">[in] The token for the target native DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a48c2-110">需求</span><span class="sxs-lookup"><span data-stu-id="a48c2-110">Requirements</span></span>  
 <span data-ttu-id="a48c2-111">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a48c2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a48c2-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a48c2-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a48c2-113">**程式庫：** 做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="a48c2-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a48c2-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a48c2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a48c2-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a48c2-115">See Also</span></span>  
 [<span data-ttu-id="a48c2-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="a48c2-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="a48c2-117">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="a48c2-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
