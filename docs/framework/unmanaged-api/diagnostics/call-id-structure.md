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
ms.openlocfilehash: 2823c018ff22607052cb9a298f69dbd0c4fe2c23
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769506"
---
# <a name="callid-structure"></a><span data-ttu-id="d2387-102">CALL_ID 結構</span><span class="sxs-lookup"><span data-stu-id="d2387-102">CALL_ID Structure</span></span>
<span data-ttu-id="d2387-103">提供偵錯工具所呼叫之函數的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d2387-103">Provides information to a debugger about a function that is being called.</span></span> <span data-ttu-id="d2387-104">請參閱[INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)介面，如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="d2387-104">See the [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) interface for more information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2387-105">語法</span><span class="sxs-lookup"><span data-stu-id="d2387-105">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="d2387-106">成員</span><span class="sxs-lookup"><span data-stu-id="d2387-106">Members</span></span>  
  
|<span data-ttu-id="d2387-107">成員</span><span class="sxs-lookup"><span data-stu-id="d2387-107">Member</span></span>|<span data-ttu-id="d2387-108">說明</span><span class="sxs-lookup"><span data-stu-id="d2387-108">Description</span></span>|  
|------------|-----------------|  
|`szMachine`|<span data-ttu-id="d2387-109">識別正在進行呼叫的電腦。</span><span class="sxs-lookup"><span data-stu-id="d2387-109">Identifies the machine that is making the call.</span></span>|  
|`dwPid`|<span data-ttu-id="d2387-110">識別電腦處理器。</span><span class="sxs-lookup"><span data-stu-id="d2387-110">Identifies the machine processor.</span></span>|  
|`pUserThread`|<span data-ttu-id="d2387-111">識別正在執行呼叫的執行緒。</span><span class="sxs-lookup"><span data-stu-id="d2387-111">Identifies the thread that is executing the call.</span></span>|  
|`addrStackPointer`|<span data-ttu-id="d2387-112">指定的呼叫堆疊的位址。</span><span class="sxs-lookup"><span data-stu-id="d2387-112">Specifies the address of the call stack.</span></span>|  
|`szEntryPoint`|<span data-ttu-id="d2387-113">指定呼叫的位址。</span><span class="sxs-lookup"><span data-stu-id="d2387-113">Specifies the address of the call.</span></span>|  
|`szDestinationMachine`|<span data-ttu-id="d2387-114">識別將會執行呼叫的電腦。</span><span class="sxs-lookup"><span data-stu-id="d2387-114">Identifies the machine that will execute the call.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d2387-115">需求</span><span class="sxs-lookup"><span data-stu-id="d2387-115">Requirements</span></span>  
 <span data-ttu-id="d2387-116">**標頭：** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="d2387-116">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2387-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2387-117">See also</span></span>

- [<span data-ttu-id="d2387-118">INotifySink2 介面</span><span class="sxs-lookup"><span data-stu-id="d2387-118">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [<span data-ttu-id="d2387-119">診斷符號存放區結構</span><span class="sxs-lookup"><span data-stu-id="d2387-119">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
