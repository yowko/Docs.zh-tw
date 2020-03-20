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
ms.openlocfilehash: e414bc5a7d537e8d153541f05b22dd91578e8739
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177745"
---
# <a name="imetadataemitdefinepinvokemap-method"></a><span data-ttu-id="03caa-102">IMetaDataEmit::DefinePinvokeMap 方法</span><span class="sxs-lookup"><span data-stu-id="03caa-102">IMetaDataEmit::DefinePinvokeMap Method</span></span>
<span data-ttu-id="03caa-103">設置指定權杖引用的方法的 PInvoke 簽名的功能。</span><span class="sxs-lookup"><span data-stu-id="03caa-103">Sets features of the PInvoke signature of the method referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03caa-104">語法</span><span class="sxs-lookup"><span data-stu-id="03caa-104">Syntax</span></span>  
  
```cpp  
HRESULT DefinePinvokeMap (
    [in]  mdToken            tk,
    [in]  DWORD              dwMappingFlags,
    [in]  LPCWSTR            szImportName,
    [in]  mdModuleRef        mrImportDLL
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03caa-105">參數</span><span class="sxs-lookup"><span data-stu-id="03caa-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="03caa-106">[在]目標方法的權杖。</span><span class="sxs-lookup"><span data-stu-id="03caa-106">[in] The token for the target method.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="03caa-107">[在]PInvoke 用於執行映射的標誌。</span><span class="sxs-lookup"><span data-stu-id="03caa-107">[in] Flags used by PInvoke to do the mapping.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="03caa-108">[在]非託管 DLL 中的目標匯出方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="03caa-108">[in] The name of the target export method in an unmanaged DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="03caa-109">[在]目標本機 DLL 的權杖。</span><span class="sxs-lookup"><span data-stu-id="03caa-109">[in] The token for the target native DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03caa-110">需求</span><span class="sxs-lookup"><span data-stu-id="03caa-110">Requirements</span></span>  
 <span data-ttu-id="03caa-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="03caa-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03caa-112">**標題：** 科爾赫</span><span class="sxs-lookup"><span data-stu-id="03caa-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="03caa-113">**庫：** 用作 MSCorEE.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="03caa-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="03caa-114">**.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03caa-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03caa-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="03caa-115">See also</span></span>

- [<span data-ttu-id="03caa-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="03caa-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="03caa-117">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="03caa-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
