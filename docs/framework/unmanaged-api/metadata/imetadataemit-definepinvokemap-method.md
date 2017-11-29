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
ms.openlocfilehash: 0c15c6039f116597ee4f2c0f83bed4c5550b30a0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitdefinepinvokemap-method"></a><span data-ttu-id="330e6-102">IMetaDataEmit::DefinePinvokeMap 方法</span><span class="sxs-lookup"><span data-stu-id="330e6-102">IMetaDataEmit::DefinePinvokeMap Method</span></span>
<span data-ttu-id="330e6-103">設定指定的語彙基元所參考之方法的 PInvoke 簽章的功能。</span><span class="sxs-lookup"><span data-stu-id="330e6-103">Sets features of the PInvoke signature of the method referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="330e6-104">語法</span><span class="sxs-lookup"><span data-stu-id="330e6-104">Syntax</span></span>  
  
```  
HRESULT DefinePinvokeMap (   
    [in]  mdToken            tk,   
    [in]  DWORD              dwMappingFlags,   
    [in]  LPCWSTR            szImportName,   
    [in]  mdModuleRef        mrImportDLL   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="330e6-105">參數</span><span class="sxs-lookup"><span data-stu-id="330e6-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="330e6-106">[in]目標方法的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="330e6-106">[in] The token for the target method.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="330e6-107">[in]用來執行對應 PInvoke 旗標。</span><span class="sxs-lookup"><span data-stu-id="330e6-107">[in] Flags used by PInvoke to do the mapping.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="330e6-108">[in]Unmanaged DLL 中的方法匯出目標的名稱。</span><span class="sxs-lookup"><span data-stu-id="330e6-108">[in] The name of the target export method in an unmanaged DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="330e6-109">[in]目標的語彙基元原生 DLL。</span><span class="sxs-lookup"><span data-stu-id="330e6-109">[in] The token for the target native DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="330e6-110">需求</span><span class="sxs-lookup"><span data-stu-id="330e6-110">Requirements</span></span>  
 <span data-ttu-id="330e6-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="330e6-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="330e6-112">**標頭：** Cor.h</span><span class="sxs-lookup"><span data-stu-id="330e6-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="330e6-113">**程式庫：**做為 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="330e6-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="330e6-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="330e6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="330e6-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="330e6-115">See Also</span></span>  
 [<span data-ttu-id="330e6-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="330e6-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="330e6-117">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="330e6-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
