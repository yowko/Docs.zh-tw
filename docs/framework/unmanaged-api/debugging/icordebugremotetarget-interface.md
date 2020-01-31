---
title: ICorDebugRemoteTarget 介面
ms.date: 03/30/2017
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
ms.openlocfilehash: bab6b7f683b5563cf362366dfb007f83caeee12d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791928"
---
# <a name="icordebugremotetarget-interface"></a><span data-ttu-id="7adf0-102">ICorDebugRemoteTarget 介面</span><span class="sxs-lookup"><span data-stu-id="7adf0-102">ICorDebugRemoteTarget Interface</span></span>
<span data-ttu-id="7adf0-103">提供可讓開發人員對通用語言執行平台 (CLR) 環境中的 Silverlight 應用程式進行偵錯的方法。</span><span class="sxs-lookup"><span data-stu-id="7adf0-103">Provides methods that enable developers to debug Silverlight-based applications in the common language runtime (CLR) environment.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7adf0-104">語法</span><span class="sxs-lookup"><span data-stu-id="7adf0-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="methods"></a><span data-ttu-id="7adf0-105">方法</span><span class="sxs-lookup"><span data-stu-id="7adf0-105">Methods</span></span>  
  
|<span data-ttu-id="7adf0-106">方法</span><span class="sxs-lookup"><span data-stu-id="7adf0-106">Method</span></span>|<span data-ttu-id="7adf0-107">描述</span><span class="sxs-lookup"><span data-stu-id="7adf0-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7adf0-108">ICorDebugRemoteTarget::GetHostName 方法</span><span class="sxs-lookup"><span data-stu-id="7adf0-108">ICorDebugRemoteTarget::GetHostName Method</span></span>](icordebugremotetarget-gethostname-method.md)|<span data-ttu-id="7adf0-109">傳回遠端電腦的主機名稱或 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="7adf0-109">Returns the host name or the IP address of a remote machine.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7adf0-110">備註</span><span class="sxs-lookup"><span data-stu-id="7adf0-110">Remarks</span></span>  
 <span data-ttu-id="7adf0-111">Windows 95、Windows 98、Windows ME 或非 x86 的平台 (例如 IA-64 和 AMD64) 不支援混合模式 (也就是 Managed 和機器碼) 偵錯。</span><span class="sxs-lookup"><span data-stu-id="7adf0-111">Mixed-mode (that is, managed and native code) debugging is not supported on Windows 95, Windows 98, or Windows ME, or on non-x86 platforms (such as IA-64 and AMD64).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7adf0-112">需求</span><span class="sxs-lookup"><span data-stu-id="7adf0-112">Requirements</span></span>  
 <span data-ttu-id="7adf0-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7adf0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7adf0-114">**標頭：** Cordebug.h .idl</span><span class="sxs-lookup"><span data-stu-id="7adf0-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="7adf0-115">**Library：** ： corguids.lib. lib</span><span class="sxs-lookup"><span data-stu-id="7adf0-115">**Library:** : CorGuids.lib</span></span>  
  
 <span data-ttu-id="7adf0-116">**.NET Framework 版本：** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="7adf0-116">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7adf0-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="7adf0-117">See also</span></span>

- [<span data-ttu-id="7adf0-118">ICorDebugRemote 介面</span><span class="sxs-lookup"><span data-stu-id="7adf0-118">ICorDebugRemote Interface</span></span>](icordebugremote-interface.md)
- [<span data-ttu-id="7adf0-119">ICorDebug 介面</span><span class="sxs-lookup"><span data-stu-id="7adf0-119">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="7adf0-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="7adf0-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
