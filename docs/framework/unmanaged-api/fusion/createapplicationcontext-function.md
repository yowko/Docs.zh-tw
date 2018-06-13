---
title: CreateApplicationContext 函式
ms.date: 03/30/2017
api_name:
- CreateApplicationContext
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- CreateApplicationContext
helpviewer_keywords:
- CreateApplicationContext function [.NET Framework fusion]
ms.assetid: 7bf8a141-b2c0-4058-9885-1cef7dcaa811
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 80012d030d0ea51ab3d150a7fd346b78e29dbde5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430096"
---
# <a name="createapplicationcontext-function"></a><span data-ttu-id="edd6e-102">CreateApplicationContext 函式</span><span class="sxs-lookup"><span data-stu-id="edd6e-102">CreateApplicationContext Function</span></span>
<span data-ttu-id="edd6e-103">此功能支援.NET Framework 基礎結構，並不是直接從您的程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="edd6e-103">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edd6e-104">語法</span><span class="sxs-lookup"><span data-stu-id="edd6e-104">Syntax</span></span>  
  
```  
HRESULT CreateApplicationContext (  
    [in]  IAssemblyName  *pName,  
    [out] LPPAPPLICATIONCONTEXT  *ppCtx  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="edd6e-105">參數</span><span class="sxs-lookup"><span data-stu-id="edd6e-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="edd6e-106">[in]指向的好記的名稱。</span><span class="sxs-lookup"><span data-stu-id="edd6e-106">[in] A pointer to a friendly name.</span></span>  
  
 `ppCtx`  
 <span data-ttu-id="edd6e-107">[out]應用程式內容的指標。</span><span class="sxs-lookup"><span data-stu-id="edd6e-107">[out] A pointer to an application context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="edd6e-108">需求</span><span class="sxs-lookup"><span data-stu-id="edd6e-108">Requirements</span></span>  
 <span data-ttu-id="edd6e-109">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="edd6e-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="edd6e-110">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="edd6e-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="edd6e-111">**程式庫：** 包含為 Fusion.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="edd6e-111">**Library:** Included as a resource in Fusion.dll</span></span>  
  
 <span data-ttu-id="edd6e-112">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="edd6e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edd6e-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="edd6e-113">See Also</span></span>  
 [<span data-ttu-id="edd6e-114">IAssemblyCache 介面</span><span class="sxs-lookup"><span data-stu-id="edd6e-114">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)  
 [<span data-ttu-id="edd6e-115">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="edd6e-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)  
 [<span data-ttu-id="edd6e-116">全域組件快取</span><span class="sxs-lookup"><span data-stu-id="edd6e-116">Global Assembly Cache</span></span>](../../../../docs/framework/app-domains/gac.md)
