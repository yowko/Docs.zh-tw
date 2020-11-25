---
title: CLRRuntimeHost Coclass
ms.date: 03/30/2017
api_name:
- CLRRuntimeHost Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CLRRuntimeHost
helpviewer_keywords:
- CLRRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 2ac9cbf5-8a2d-4e4f-8831-0dad8ef0a897
topic_type:
- apiref
ms.openlocfilehash: 7c77cb2e89cb8fd87bf219780b9460649de19c9d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731751"
---
# <a name="clrruntimehost-coclass"></a><span data-ttu-id="c8dbd-102">CLRRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="c8dbd-102">CLRRuntimeHost Coclass</span></span>

<span data-ttu-id="c8dbd-103">提供介面來管理執行時間所執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="c8dbd-103">Provides interfaces for managing code execution by the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8dbd-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="c8dbd-104">Syntax</span></span>  
  
```cpp  
coclass CLRRuntimeHost {  
    [default] interface  ICLRRuntimeHost;  
    interface            ICLRValidator;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="c8dbd-105">介面</span><span class="sxs-lookup"><span data-stu-id="c8dbd-105">Interfaces</span></span>  
  
|<span data-ttu-id="c8dbd-106">介面</span><span class="sxs-lookup"><span data-stu-id="c8dbd-106">Interface</span></span>|<span data-ttu-id="c8dbd-107">描述</span><span class="sxs-lookup"><span data-stu-id="c8dbd-107">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="c8dbd-108">ICLRRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="c8dbd-108">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)|<span data-ttu-id="c8dbd-109">提供方法來控制執行時間的應用程式執行。</span><span class="sxs-lookup"><span data-stu-id="c8dbd-109">Provides methods for controlling the execution of applications by the runtime.</span></span>|  
|[<span data-ttu-id="c8dbd-110">ICLRValidator 介面</span><span class="sxs-lookup"><span data-stu-id="c8dbd-110">ICLRValidator Interface</span></span>](iclrvalidator-interface.md)|<span data-ttu-id="c8dbd-111">提供驗證可攜式可執行檔映射和詳細報告驗證錯誤的方法。</span><span class="sxs-lookup"><span data-stu-id="c8dbd-111">Provides methods for validation of portable executable images and for detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c8dbd-112">需求</span><span class="sxs-lookup"><span data-stu-id="c8dbd-112">Requirements</span></span>  

 <span data-ttu-id="c8dbd-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c8dbd-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8dbd-114">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="c8dbd-114">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="c8dbd-115">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="c8dbd-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c8dbd-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8dbd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8dbd-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c8dbd-117">See also</span></span>

- [<span data-ttu-id="c8dbd-118">裝載 Coclass</span><span class="sxs-lookup"><span data-stu-id="c8dbd-118">Hosting Coclasses</span></span>](hosting-coclasses.md)
