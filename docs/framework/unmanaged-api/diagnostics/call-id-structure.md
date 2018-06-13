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
ms.openlocfilehash: f8d6b16f3eeb32e41f3568e0b237f18c945a8cb8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423893"
---
# <a name="callid-structure"></a><span data-ttu-id="a33ce-102">CALL_ID 結構</span><span class="sxs-lookup"><span data-stu-id="a33ce-102">CALL_ID Structure</span></span>
<span data-ttu-id="a33ce-103">提供偵錯工具所呼叫之函數的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="a33ce-103">Provides information to a debugger about a function that is being called.</span></span> <span data-ttu-id="a33ce-104">請參閱[INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)介面，如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="a33ce-104">See the [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) interface for more information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a33ce-105">語法</span><span class="sxs-lookup"><span data-stu-id="a33ce-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="a33ce-106">成員</span><span class="sxs-lookup"><span data-stu-id="a33ce-106">Members</span></span>  
  
|<span data-ttu-id="a33ce-107">成員</span><span class="sxs-lookup"><span data-stu-id="a33ce-107">Member</span></span>|<span data-ttu-id="a33ce-108">描述</span><span class="sxs-lookup"><span data-stu-id="a33ce-108">Description</span></span>|  
|------------|-----------------|  
|`szMachine`|<span data-ttu-id="a33ce-109">識別正在進行呼叫的電腦。</span><span class="sxs-lookup"><span data-stu-id="a33ce-109">Identifies the machine that is making the call.</span></span>|  
|`dwPid`|<span data-ttu-id="a33ce-110">識別電腦處理器。</span><span class="sxs-lookup"><span data-stu-id="a33ce-110">Identifies the machine processor.</span></span>|  
|`pUserThread`|<span data-ttu-id="a33ce-111">識別正在執行呼叫的執行緒。</span><span class="sxs-lookup"><span data-stu-id="a33ce-111">Identifies the thread that is executing the call.</span></span>|  
|`addrStackPointer`|<span data-ttu-id="a33ce-112">指定的呼叫堆疊的位址。</span><span class="sxs-lookup"><span data-stu-id="a33ce-112">Specifies the address of the call stack.</span></span>|  
|`szEntryPoint`|<span data-ttu-id="a33ce-113">指定呼叫的位址。</span><span class="sxs-lookup"><span data-stu-id="a33ce-113">Specifies the address of the call.</span></span>|  
|`szDestinationMachine`|<span data-ttu-id="a33ce-114">識別將會執行呼叫的電腦。</span><span class="sxs-lookup"><span data-stu-id="a33ce-114">Identifies the machine that will execute the call.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a33ce-115">需求</span><span class="sxs-lookup"><span data-stu-id="a33ce-115">Requirements</span></span>  
 <span data-ttu-id="a33ce-116">**標頭：** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="a33ce-116">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a33ce-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a33ce-117">See Also</span></span>  
 [<span data-ttu-id="a33ce-118">INotifySink2 介面</span><span class="sxs-lookup"><span data-stu-id="a33ce-118">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [<span data-ttu-id="a33ce-119">診斷符號存放區結構</span><span class="sxs-lookup"><span data-stu-id="a33ce-119">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
