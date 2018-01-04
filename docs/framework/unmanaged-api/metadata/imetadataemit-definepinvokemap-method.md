---
title: "IMetaDataEmit::DefinePinvokeMap 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.DefinePinvokeMap
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::DefinePinvokeMap
helpviewer_keywords:
- DefinePinvokeMap method [.NET Framework metadata]
- IMetaDataEmit::DefinePinvokeMap method [.NET Framework metadata]
ms.assetid: 03abf921-5154-4070-88fa-10b7092901fb
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bd42c54990fd8aad1b9e6325d59ac7ccc5d6a3fc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefinepinvokemap-method"></a><span data-ttu-id="08194-102">IMetaDataEmit::DefinePinvokeMap 方法</span><span class="sxs-lookup"><span data-stu-id="08194-102">IMetaDataEmit::DefinePinvokeMap Method</span></span>
<span data-ttu-id="08194-103">設定指定的語彙基元所參考之方法的 PInvoke 簽章的功能。</span><span class="sxs-lookup"><span data-stu-id="08194-103">Sets features of the PInvoke signature of the method referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08194-104">語法</span><span class="sxs-lookup"><span data-stu-id="08194-104">Syntax</span></span>  
  
```  
HRESULT DefinePinvokeMap (   
    [in]  mdToken            tk,   
    [in]  DWORD              dwMappingFlags,   
    [in]  LPCWSTR            szImportName,   
    [in]  mdModuleRef        mrImportDLL   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="08194-105">參數</span><span class="sxs-lookup"><span data-stu-id="08194-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="08194-106">[in]目標方法的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="08194-106">[in] The token for the target method.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="08194-107">[in]用來執行對應 PInvoke 旗標。</span><span class="sxs-lookup"><span data-stu-id="08194-107">[in] Flags used by PInvoke to do the mapping.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="08194-108">[in]Unmanaged DLL 中的方法匯出目標的名稱。</span><span class="sxs-lookup"><span data-stu-id="08194-108">[in] The name of the target export method in an unmanaged DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="08194-109">[in]目標的語彙基元原生 DLL。</span><span class="sxs-lookup"><span data-stu-id="08194-109">[in] The token for the target native DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08194-110">需求</span><span class="sxs-lookup"><span data-stu-id="08194-110">Requirements</span></span>  
 <span data-ttu-id="08194-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="08194-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08194-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="08194-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="08194-113">**程式庫：**做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="08194-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="08194-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08194-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08194-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="08194-115">See Also</span></span>  
 [<span data-ttu-id="08194-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="08194-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="08194-117">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="08194-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
