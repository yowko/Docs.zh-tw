---
title: "ICorDebugRemoteTarget 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugRemoteTarget
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget
helpviewer_keywords:
- ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: bd9936a6-cc24-4869-8761-0988664464e6
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fcfdab2857745dee7c40823ad25592de5dc833ea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugremotetarget-interface"></a><span data-ttu-id="d3c34-102">ICorDebugRemoteTarget 介面</span><span class="sxs-lookup"><span data-stu-id="d3c34-102">ICorDebugRemoteTarget Interface</span></span>
<span data-ttu-id="d3c34-103">提供可讓開發人員對通用語言執行平台 (CLR) 環境中的 Silverlight 應用程式進行偵錯的方法。</span><span class="sxs-lookup"><span data-stu-id="d3c34-103">Provides methods that enable developers to debug Silverlight-based applications in the common language runtime (CLR) environment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3c34-104">語法</span><span class="sxs-lookup"><span data-stu-id="d3c34-104">Syntax</span></span>  
  
```  
interface ICorDebugRemoteTarget  : IUnknown  
{  
    HRESULT GetHostName (  
        [in]  ULONG32                    cchHostName,  
        [out] ULONG32*                   pcchHostName,  
        [out, size_is(cchHostName),  
              length_is(*pcchHostName)]  
                  WCHAR szHostName[]  
        );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="d3c34-105">方法</span><span class="sxs-lookup"><span data-stu-id="d3c34-105">Methods</span></span>  
  
|<span data-ttu-id="d3c34-106">方法</span><span class="sxs-lookup"><span data-stu-id="d3c34-106">Method</span></span>|<span data-ttu-id="d3c34-107">描述</span><span class="sxs-lookup"><span data-stu-id="d3c34-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d3c34-108">ICorDebugRemoteTarget::GetHostName 方法</span><span class="sxs-lookup"><span data-stu-id="d3c34-108">ICorDebugRemoteTarget::GetHostName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-gethostname-method.md)|<span data-ttu-id="d3c34-109">傳回遠端電腦的主機名稱或 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="d3c34-109">Returns the host name or the IP address of a remote machine.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3c34-110">備註</span><span class="sxs-lookup"><span data-stu-id="d3c34-110">Remarks</span></span>  
 <span data-ttu-id="d3c34-111">Windows 95、Windows 98、Windows ME 或非 x86 的平台 (例如 IA-64 和 AMD64) 不支援混合模式 (也就是 Managed 和機器碼) 偵錯。</span><span class="sxs-lookup"><span data-stu-id="d3c34-111">Mixed-mode (that is, managed and native code) debugging is not supported on Windows 95, Windows 98, or Windows ME, or on non-x86 platforms (such as IA-64 and AMD64).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3c34-112">需求</span><span class="sxs-lookup"><span data-stu-id="d3c34-112">Requirements</span></span>  
 <span data-ttu-id="d3c34-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d3c34-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3c34-114">**標頭：** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="d3c34-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="d3c34-115">**程式庫：** : CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d3c34-115">**Library:** : CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3c34-116">**.NET framework 版本：** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="d3c34-116">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3c34-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="d3c34-117">See Also</span></span>  
 [<span data-ttu-id="d3c34-118">ICorDebugRemote 介面</span><span class="sxs-lookup"><span data-stu-id="d3c34-118">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 [<span data-ttu-id="d3c34-119">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="d3c34-119">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 [<span data-ttu-id="d3c34-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="d3c34-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
