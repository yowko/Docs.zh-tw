---
title: CoreClrDebugRuntimeInfo 結構
ms.date: 03/30/2017
api_name:
- CoreClrDebugRuntimeInfo
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CoreClrDebugRuntimeInfo
helpviewer_keywords:
- remote debugging API [Silverlight]
- CoreDebugRuntimeInfo structure
- Silverlight, remote debugging
ms.assetid: bd01c30f-b7a8-4179-9497-622b6599b1a6
topic_type:
- apiref
ms.openlocfilehash: 3cc9a1cfb26a784c32d66168bb01d41f91dd5f66
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722365"
---
# <a name="coreclrdebugruntimeinfo-structure"></a><span data-ttu-id="d6d02-102">CoreClrDebugRuntimeInfo 結構</span><span class="sxs-lookup"><span data-stu-id="d6d02-102">CoreClrDebugRuntimeInfo Structure</span></span>

<span data-ttu-id="d6d02-103">代表載入遠端電腦上之處理序的 Common Language Runtime (CLR) 執行個體。</span><span class="sxs-lookup"><span data-stu-id="d6d02-103">Represents a common language runtime (CLR) instance that is loaded in a process on a remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6d02-104">語法</span><span class="sxs-lookup"><span data-stu-id="d6d02-104">Syntax</span></span>  
  
```cpp  
struct  CoreClrDebugRuntimeInfo {  
    DWORD m_dwInternalID;  
};  
```  
  
## <a name="members"></a><span data-ttu-id="d6d02-105">成員</span><span class="sxs-lookup"><span data-stu-id="d6d02-105">Members</span></span>  
  
|<span data-ttu-id="d6d02-106">member</span><span class="sxs-lookup"><span data-stu-id="d6d02-106">Member</span></span>|<span data-ttu-id="d6d02-107">描述</span><span class="sxs-lookup"><span data-stu-id="d6d02-107">Description</span></span>|  
|------------|-----------------|  
|`m_dwInternalID`|<span data-ttu-id="d6d02-108">在目標電腦上執行之遠端偵錯 Proxy 所指派的執行階段識別項。</span><span class="sxs-lookup"><span data-stu-id="d6d02-108">Runtime identifier that is assigned by the remote debugging proxy running on the target machine.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d6d02-109">需求</span><span class="sxs-lookup"><span data-stu-id="d6d02-109">Requirements</span></span>  

 <span data-ttu-id="d6d02-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d6d02-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6d02-111">**標頭：** CoreClrRemoteDebuggingInterfaces。h</span><span class="sxs-lookup"><span data-stu-id="d6d02-111">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="d6d02-112">連結 **庫：** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="d6d02-112">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="d6d02-113">**.NET Framework 版本：** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="d6d02-113">**.NET Framework Versions:** 3.5 SP1</span></span>
