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
ms.openlocfilehash: 9d4ea16a212ac5f0120d63510f07eaee69af739e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431482"
---
# <a name="imetadataemitdefinepinvokemap-method"></a><span data-ttu-id="b5a2d-102">IMetaDataEmit::DefinePinvokeMap 方法</span><span class="sxs-lookup"><span data-stu-id="b5a2d-102">IMetaDataEmit::DefinePinvokeMap Method</span></span>
<span data-ttu-id="b5a2d-103">設定指定之標記所參考之方法的 PInvoke 簽章功能。</span><span class="sxs-lookup"><span data-stu-id="b5a2d-103">Sets features of the PInvoke signature of the method referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5a2d-104">語法</span><span class="sxs-lookup"><span data-stu-id="b5a2d-104">Syntax</span></span>  
  
```cpp  
HRESULT DefinePinvokeMap (   
    [in]  mdToken            tk,   
    [in]  DWORD              dwMappingFlags,   
    [in]  LPCWSTR            szImportName,   
    [in]  mdModuleRef        mrImportDLL   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b5a2d-105">參數</span><span class="sxs-lookup"><span data-stu-id="b5a2d-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="b5a2d-106">在目標方法的 token。</span><span class="sxs-lookup"><span data-stu-id="b5a2d-106">[in] The token for the target method.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="b5a2d-107">在PInvoke 用來執行對應的旗標。</span><span class="sxs-lookup"><span data-stu-id="b5a2d-107">[in] Flags used by PInvoke to do the mapping.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="b5a2d-108">在非受控 DLL 中的目標匯出方法名稱。</span><span class="sxs-lookup"><span data-stu-id="b5a2d-108">[in] The name of the target export method in an unmanaged DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="b5a2d-109">在目標原生 DLL 的 token。</span><span class="sxs-lookup"><span data-stu-id="b5a2d-109">[in] The token for the target native DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5a2d-110">需求</span><span class="sxs-lookup"><span data-stu-id="b5a2d-110">Requirements</span></span>  
 <span data-ttu-id="b5a2d-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b5a2d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5a2d-112">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="b5a2d-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b5a2d-113">連結**庫：** 做為 Mscoree.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="b5a2d-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b5a2d-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5a2d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5a2d-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b5a2d-115">See also</span></span>

- [<span data-ttu-id="b5a2d-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="b5a2d-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="b5a2d-117">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="b5a2d-117">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
