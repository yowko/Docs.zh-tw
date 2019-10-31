---
title: ICorRuntimeHost::GetConfiguration 方法
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.GetConfiguration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::GetConfiguration
helpviewer_keywords:
- ICorRuntimeHost::GetConfiguration method [.NET Framework hosting]
- GetConfiguration method [.NET Framework hosting]
ms.assetid: c431617a-b055-44a0-8730-48b7a86d9610
topic_type:
- apiref
ms.openlocfilehash: 87549118742da797ef0dd1b08ae9e72c466f7841
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139573"
---
# <a name="icorruntimehostgetconfiguration-method"></a><span data-ttu-id="6a4d4-102">ICorRuntimeHost::GetConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="6a4d4-102">ICorRuntimeHost::GetConfiguration Method</span></span>
<span data-ttu-id="6a4d4-103">取得物件，可讓主機指定 common language runtime （CLR）的回呼設定。</span><span class="sxs-lookup"><span data-stu-id="6a4d4-103">Gets an object that allows the host to specify the callback configuration of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a4d4-104">語法</span><span class="sxs-lookup"><span data-stu-id="6a4d4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetConfiguration(  
    [out] ICorConfiguration** pConfiguration  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a4d4-105">參數</span><span class="sxs-lookup"><span data-stu-id="6a4d4-105">Parameters</span></span>  
 `pConfiguration`  
 <span data-ttu-id="6a4d4-106">脫銷[ICorConfiguration](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)物件位址的指標，可用於設定 CLR。</span><span class="sxs-lookup"><span data-stu-id="6a4d4-106">[out] A pointer to the address of an [ICorConfiguration](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md) object that can be used to configure the CLR.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a4d4-107">備註</span><span class="sxs-lookup"><span data-stu-id="6a4d4-107">Remarks</span></span>  
 <span data-ttu-id="6a4d4-108">CLR 必須在初始化之前設定;否則，`GetConfiguration` 方法會傳回 HRESULT，指出發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="6a4d4-108">The CLR must be configured prior to its initialization; otherwise, the `GetConfiguration` method returns an HRESULT indicating an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a4d4-109">需求</span><span class="sxs-lookup"><span data-stu-id="6a4d4-109">Requirements</span></span>  
 <span data-ttu-id="6a4d4-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6a4d4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a4d4-111">**標頭：** Mscoree.dll. h</span><span class="sxs-lookup"><span data-stu-id="6a4d4-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6a4d4-112">連結**庫：** 包含為 Mscoree.dll 中的資源</span><span class="sxs-lookup"><span data-stu-id="6a4d4-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6a4d4-113">**.NET Framework 版本：** 1.0、1。1</span><span class="sxs-lookup"><span data-stu-id="6a4d4-113">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a4d4-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="6a4d4-114">See also</span></span>

- [<span data-ttu-id="6a4d4-115">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="6a4d4-115">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
