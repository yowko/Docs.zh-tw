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
ms.openlocfilehash: 2a50814a67be5a01a7413050683a915355665f3c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720642"
---
# <a name="icorruntimehostgetconfiguration-method"></a><span data-ttu-id="e10c3-102">ICorRuntimeHost::GetConfiguration 方法</span><span class="sxs-lookup"><span data-stu-id="e10c3-102">ICorRuntimeHost::GetConfiguration Method</span></span>

<span data-ttu-id="e10c3-103">取得物件，這個物件可讓主機指定 common language runtime (CLR) 的回呼設定。</span><span class="sxs-lookup"><span data-stu-id="e10c3-103">Gets an object that allows the host to specify the callback configuration of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e10c3-104">語法</span><span class="sxs-lookup"><span data-stu-id="e10c3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetConfiguration(  
    [out] ICorConfiguration** pConfiguration  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e10c3-105">參數</span><span class="sxs-lookup"><span data-stu-id="e10c3-105">Parameters</span></span>  

 `pConfiguration`  
 <span data-ttu-id="e10c3-106">擴展可以用來設定 CLR 之 [ICorConfiguration](icorconfiguration-interface.md) 物件位址的指標。</span><span class="sxs-lookup"><span data-stu-id="e10c3-106">[out] A pointer to the address of an [ICorConfiguration](icorconfiguration-interface.md) object that can be used to configure the CLR.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e10c3-107">備註</span><span class="sxs-lookup"><span data-stu-id="e10c3-107">Remarks</span></span>  

 <span data-ttu-id="e10c3-108">CLR 必須在初始化之前設定;否則，方法會傳回 `GetConfiguration` 表示錯誤的 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="e10c3-108">The CLR must be configured prior to its initialization; otherwise, the `GetConfiguration` method returns an HRESULT indicating an error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e10c3-109">需求</span><span class="sxs-lookup"><span data-stu-id="e10c3-109">Requirements</span></span>  

 <span data-ttu-id="e10c3-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e10c3-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e10c3-111">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="e10c3-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e10c3-112">連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中</span><span class="sxs-lookup"><span data-stu-id="e10c3-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e10c3-113">**.NET Framework 版本：** 1.0、1。1</span><span class="sxs-lookup"><span data-stu-id="e10c3-113">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e10c3-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e10c3-114">See also</span></span>

- [<span data-ttu-id="e10c3-115">ICorRuntimeHost 介面</span><span class="sxs-lookup"><span data-stu-id="e10c3-115">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
