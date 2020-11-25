---
title: PreBindAssemblyEx 函式
ms.date: 03/30/2017
api_name:
- PreBindAssemblyEx
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- PreBindAssemblyEx
helpviewer_keywords:
- PreBindAssemblyEx function [.NET Framework fusion]
ms.assetid: bd285233-a4a2-4b52-bbca-0025a60e4864
topic_type:
- apiref
ms.openlocfilehash: a729249f7b0681941a0b1a478dbe2c0d9d6cd01c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723957"
---
# <a name="prebindassemblyex-function"></a><span data-ttu-id="6aaa2-102">PreBindAssemblyEx 函式</span><span class="sxs-lookup"><span data-stu-id="6aaa2-102">PreBindAssemblyEx Function</span></span>

<span data-ttu-id="6aaa2-103">取得元件的原則後顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="6aaa2-103">Gets the post-policy display name for an assembly.</span></span>  
  
 <span data-ttu-id="6aaa2-104">此函式支援 .NET Framework 基礎結構，而且不適合直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="6aaa2-104">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6aaa2-105">語法</span><span class="sxs-lookup"><span data-stu-id="6aaa2-105">Syntax</span></span>  
  
```cpp  
HRESULT PreBindAssemblyEx (  
    [in]  IApplicationContext *pAppCtx,  
    [in]  IAssemblyName       *pName,  
    [in]  IAssembly           *pAsmParent,  
    [in]  LPCWSTR             pwzRuntimeVersion,  
    [out] IAssemblyName       **ppNamePostPolicy,  
    [in]  LPVOID              pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="6aaa2-106">參數</span><span class="sxs-lookup"><span data-stu-id="6aaa2-106">Parameters</span></span>  

 `pAppCtx`  
 <span data-ttu-id="6aaa2-107">在識別應用程式內容。</span><span class="sxs-lookup"><span data-stu-id="6aaa2-107">[in] Identifies the application context.</span></span>  
  
 `pName`  
 <span data-ttu-id="6aaa2-108">在識別元件名稱。</span><span class="sxs-lookup"><span data-stu-id="6aaa2-108">[in] Identifies the assembly name.</span></span>  
  
 `pAsmParent`  
 <span data-ttu-id="6aaa2-109">在識別父元件。</span><span class="sxs-lookup"><span data-stu-id="6aaa2-109">[in] Identifies the parent assembly.</span></span> <span data-ttu-id="6aaa2-110">這個參數已忽略。</span><span class="sxs-lookup"><span data-stu-id="6aaa2-110">This parameter is ignored.</span></span>  
  
 `pwzRuntimeVersion`  
 <span data-ttu-id="6aaa2-111">在識別執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="6aaa2-111">[in] Identifies the runtime version.</span></span>  
  
 `ppNamePostPolicy`  
 <span data-ttu-id="6aaa2-112">擴展包含原則後顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="6aaa2-112">[out] Contains the post-policy display name.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="6aaa2-113">在保留供未來擴充性之用。</span><span class="sxs-lookup"><span data-stu-id="6aaa2-113">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="6aaa2-114">`pvReserved` 必須是 null 參考。</span><span class="sxs-lookup"><span data-stu-id="6aaa2-114">`pvReserved` must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6aaa2-115">備註</span><span class="sxs-lookup"><span data-stu-id="6aaa2-115">Remarks</span></span>  

 <span data-ttu-id="6aaa2-116">`ppNamePostPolicy`只有當函數傳回 HRESULT FUSION_E_REF_DEF_MISMATCH 時，才會設定 output 參數。</span><span class="sxs-lookup"><span data-stu-id="6aaa2-116">The `ppNamePostPolicy` output parameter is set only if the function returns HRESULT FUSION_E_REF_DEF_MISMATCH.</span></span> <span data-ttu-id="6aaa2-117">否則為 Null。</span><span class="sxs-lookup"><span data-stu-id="6aaa2-117">Otherwise, it is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6aaa2-118">需求</span><span class="sxs-lookup"><span data-stu-id="6aaa2-118">Requirements</span></span>  

 <span data-ttu-id="6aaa2-119">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6aaa2-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6aaa2-120">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="6aaa2-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="6aaa2-121">連結 **庫：** 以資源的形式包含在 MsCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="6aaa2-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6aaa2-122">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6aaa2-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6aaa2-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6aaa2-123">See also</span></span>

- [<span data-ttu-id="6aaa2-124">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="6aaa2-124">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
