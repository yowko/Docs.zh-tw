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
ms.openlocfilehash: 25364330dafdf858c4b41e9a05731c37e97fbb57
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795440"
---
# <a name="createapplicationcontext-function"></a><span data-ttu-id="bb32c-102">CreateApplicationContext 函式</span><span class="sxs-lookup"><span data-stu-id="bb32c-102">CreateApplicationContext Function</span></span>
<span data-ttu-id="bb32c-103">此函式支援 .NET Framework 的基礎結構，但不適合直接從您的程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="bb32c-103">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb32c-104">語法</span><span class="sxs-lookup"><span data-stu-id="bb32c-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateApplicationContext (  
    [in]  IAssemblyName  *pName,  
    [out] LPPAPPLICATIONCONTEXT  *ppCtx  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb32c-105">參數</span><span class="sxs-lookup"><span data-stu-id="bb32c-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="bb32c-106">在易記名稱的指標。</span><span class="sxs-lookup"><span data-stu-id="bb32c-106">[in] A pointer to a friendly name.</span></span>  
  
 `ppCtx`  
 <span data-ttu-id="bb32c-107">脫銷應用程式內容的指標。</span><span class="sxs-lookup"><span data-stu-id="bb32c-107">[out] A pointer to an application context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb32c-108">需求</span><span class="sxs-lookup"><span data-stu-id="bb32c-108">Requirements</span></span>  
 <span data-ttu-id="bb32c-109">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bb32c-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb32c-110">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="bb32c-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="bb32c-111">**LIBRARY:** 納入為融合 .dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="bb32c-111">**Library:** Included as a resource in Fusion.dll</span></span>  
  
 <span data-ttu-id="bb32c-112">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb32c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb32c-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb32c-113">See also</span></span>

- [<span data-ttu-id="bb32c-114">IAssemblyCache 介面</span><span class="sxs-lookup"><span data-stu-id="bb32c-114">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
- [<span data-ttu-id="bb32c-115">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="bb32c-115">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
- [<span data-ttu-id="bb32c-116">全域組件快取</span><span class="sxs-lookup"><span data-stu-id="bb32c-116">Global Assembly Cache</span></span>](../../app-domains/gac.md)
