---
title: "USER_THREAD 結構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: USER_THREAD
api_location: diasymreader.dll
api_type: COM
f1_keywords: USER_THREAD
helpviewer_keywords: USER_THREAD structure [.NET Framework debugging]
ms.assetid: a57c7d71-c4b0-41f9-a964-0c5ee84a3124
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d93002fe5460bfdb36d4e11c74410677b46a98d7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="userthread-structure"></a><span data-ttu-id="1fd75-102">USER_THREAD 結構</span><span class="sxs-lookup"><span data-stu-id="1fd75-102">USER_THREAD Structure</span></span>
<span data-ttu-id="1fd75-103">提供資訊給偵錯工具執行緒。</span><span class="sxs-lookup"><span data-stu-id="1fd75-103">Provides information to a debugger about a thread.</span></span> <span data-ttu-id="1fd75-104">如需詳細資訊，請參閱[inotifysource2:: Setnotifyfilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="1fd75-104">For more information, see the [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fd75-105">語法</span><span class="sxs-lookup"><span data-stu-id="1fd75-105">Syntax</span></span>  
  
```  
typedef struct tagUSER_THREAD  
{  
    BYTE    *pSidBuffer;  
    DWORD   dwSidLen;  
    DWORD   dwTid;  
} USER_THREAD;  
```  
  
## <a name="members"></a><span data-ttu-id="1fd75-106">成員</span><span class="sxs-lookup"><span data-stu-id="1fd75-106">Members</span></span>  
  
|<span data-ttu-id="1fd75-107">成員</span><span class="sxs-lookup"><span data-stu-id="1fd75-107">Member</span></span>|<span data-ttu-id="1fd75-108">說明</span><span class="sxs-lookup"><span data-stu-id="1fd75-108">Description</span></span>|  
|------------|-----------------|  
|`pSidBuffer`|<span data-ttu-id="1fd75-109">執行緒緩衝區的位址。</span><span class="sxs-lookup"><span data-stu-id="1fd75-109">Address of thread buffer.</span></span>|  
|`dwSidLen`|<span data-ttu-id="1fd75-110">執行緒的緩衝區，以位元組為單位的長度。</span><span class="sxs-lookup"><span data-stu-id="1fd75-110">Length of thread buffer, in bytes.</span></span>|  
|`dwTid`|<span data-ttu-id="1fd75-111">執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="1fd75-111">Thread ID.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1fd75-112">需求</span><span class="sxs-lookup"><span data-stu-id="1fd75-112">Requirements</span></span>  
 <span data-ttu-id="1fd75-113">**標頭：** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="1fd75-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fd75-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1fd75-114">See Also</span></span>  
 [<span data-ttu-id="1fd75-115">SetNotifyFilter 方法</span><span class="sxs-lookup"><span data-stu-id="1fd75-115">SetNotifyFilter Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md)  
 [<span data-ttu-id="1fd75-116">診斷符號存放區結構</span><span class="sxs-lookup"><span data-stu-id="1fd75-116">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
