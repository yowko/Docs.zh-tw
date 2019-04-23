---
title: CALL_ID 結構
ms.date: 03/30/2017
api_name:
- CALL_ID
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- CALL_ID
helpviewer_keywords:
- CALL_ID structure [.NET Framework debugging]
ms.assetid: bfd46324-afec-4782-9c18-586d81fb4740
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b6fa729b131d12b2825a2def700fd918ce8acc40
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59220171"
---
# <a name="callid-structure"></a><span data-ttu-id="9a043-102">CALL_ID 結構</span><span class="sxs-lookup"><span data-stu-id="9a043-102">CALL_ID Structure</span></span>
<span data-ttu-id="9a043-103">提供偵錯工具所呼叫之函數的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="9a043-103">Provides information to a debugger about a function that is being called.</span></span> <span data-ttu-id="9a043-104">請參閱[INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)介面，如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="9a043-104">See the [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) interface for more information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a043-105">語法</span><span class="sxs-lookup"><span data-stu-id="9a043-105">Syntax</span></span>  
  
```  
typedef struct tagCALL_ID  
{  
    LPCOLESTR       szMachine;  
    DWORD           dwPid;  
    USER_THREAD     *pUserThread;  
    STACK_ADDRESS   addrStackPointer;  
    LPCOLESTR       szEntryPoint;  
    LPCOLESTR       szDestinationMachine;  
} CALL_ID;  
```  
  
## <a name="members"></a><span data-ttu-id="9a043-106">成員</span><span class="sxs-lookup"><span data-stu-id="9a043-106">Members</span></span>  
  
|<span data-ttu-id="9a043-107">成員</span><span class="sxs-lookup"><span data-stu-id="9a043-107">Member</span></span>|<span data-ttu-id="9a043-108">描述</span><span class="sxs-lookup"><span data-stu-id="9a043-108">Description</span></span>|  
|------------|-----------------|  
|`szMachine`|<span data-ttu-id="9a043-109">識別正在進行呼叫的電腦。</span><span class="sxs-lookup"><span data-stu-id="9a043-109">Identifies the machine that is making the call.</span></span>|  
|`dwPid`|<span data-ttu-id="9a043-110">識別電腦處理器。</span><span class="sxs-lookup"><span data-stu-id="9a043-110">Identifies the machine processor.</span></span>|  
|`pUserThread`|<span data-ttu-id="9a043-111">識別正在執行呼叫的執行緒。</span><span class="sxs-lookup"><span data-stu-id="9a043-111">Identifies the thread that is executing the call.</span></span>|  
|`addrStackPointer`|<span data-ttu-id="9a043-112">指定的呼叫堆疊的位址。</span><span class="sxs-lookup"><span data-stu-id="9a043-112">Specifies the address of the call stack.</span></span>|  
|`szEntryPoint`|<span data-ttu-id="9a043-113">指定呼叫的位址。</span><span class="sxs-lookup"><span data-stu-id="9a043-113">Specifies the address of the call.</span></span>|  
|`szDestinationMachine`|<span data-ttu-id="9a043-114">識別將會執行呼叫的電腦。</span><span class="sxs-lookup"><span data-stu-id="9a043-114">Identifies the machine that will execute the call.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9a043-115">需求</span><span class="sxs-lookup"><span data-stu-id="9a043-115">Requirements</span></span>  
 <span data-ttu-id="9a043-116">**標頭：** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="9a043-116">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a043-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9a043-117">See also</span></span>

- [<span data-ttu-id="9a043-118">INotifySink2 介面</span><span class="sxs-lookup"><span data-stu-id="9a043-118">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [<span data-ttu-id="9a043-119">診斷符號存放區結構</span><span class="sxs-lookup"><span data-stu-id="9a043-119">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
