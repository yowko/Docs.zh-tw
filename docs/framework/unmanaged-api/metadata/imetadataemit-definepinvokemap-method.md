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
ms.openlocfilehash: b46d39ab3958227c1fca24ceb3a9934f2778aa2c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719498"
---
# <a name="imetadataemitdefinepinvokemap-method"></a><span data-ttu-id="d4f44-102">IMetaDataEmit::DefinePinvokeMap 方法</span><span class="sxs-lookup"><span data-stu-id="d4f44-102">IMetaDataEmit::DefinePinvokeMap Method</span></span>

<span data-ttu-id="d4f44-103">設定指定之標記所參考之方法的 PInvoke 簽章功能。</span><span class="sxs-lookup"><span data-stu-id="d4f44-103">Sets features of the PInvoke signature of the method referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4f44-104">語法</span><span class="sxs-lookup"><span data-stu-id="d4f44-104">Syntax</span></span>  
  
```cpp  
HRESULT DefinePinvokeMap (
    [in]  mdToken            tk,
    [in]  DWORD              dwMappingFlags,
    [in]  LPCWSTR            szImportName,
    [in]  mdModuleRef        mrImportDLL
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4f44-105">參數</span><span class="sxs-lookup"><span data-stu-id="d4f44-105">Parameters</span></span>  

 `tk`  
 <span data-ttu-id="d4f44-106">在目標方法的標記。</span><span class="sxs-lookup"><span data-stu-id="d4f44-106">[in] The token for the target method.</span></span>  
  
 `dwMappingFlags`  
 <span data-ttu-id="d4f44-107">在PInvoke 用來進行對應的旗標。</span><span class="sxs-lookup"><span data-stu-id="d4f44-107">[in] Flags used by PInvoke to do the mapping.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="d4f44-108">在非受控 DLL 中目標匯出方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="d4f44-108">[in] The name of the target export method in an unmanaged DLL.</span></span>  
  
 `mrImportDLL`  
 <span data-ttu-id="d4f44-109">在目標原生 DLL 的標記。</span><span class="sxs-lookup"><span data-stu-id="d4f44-109">[in] The token for the target native DLL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4f44-110">需求</span><span class="sxs-lookup"><span data-stu-id="d4f44-110">Requirements</span></span>  

 <span data-ttu-id="d4f44-111">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d4f44-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4f44-112">**標頭：** Cor。h</span><span class="sxs-lookup"><span data-stu-id="d4f44-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d4f44-113">連結 **庫：** 當做 MSCorEE.dll 中的資源使用</span><span class="sxs-lookup"><span data-stu-id="d4f44-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d4f44-114">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4f44-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4f44-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4f44-115">See also</span></span>

- [<span data-ttu-id="d4f44-116">IMetaDataEmit 介面</span><span class="sxs-lookup"><span data-stu-id="d4f44-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="d4f44-117">IMetaDataEmit2 介面</span><span class="sxs-lookup"><span data-stu-id="d4f44-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
