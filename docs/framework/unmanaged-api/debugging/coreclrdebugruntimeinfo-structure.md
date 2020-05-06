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
ms.openlocfilehash: 2c41e7db32ee8557a6c03217b95fd5b040655c70
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860936"
---
# <a name="coreclrdebugruntimeinfo-structure"></a><span data-ttu-id="a0f1d-102">CoreClrDebugRuntimeInfo 結構</span><span class="sxs-lookup"><span data-stu-id="a0f1d-102">CoreClrDebugRuntimeInfo Structure</span></span>
<span data-ttu-id="a0f1d-103">代表載入遠端電腦上之處理序的 Common Language Runtime (CLR) 執行個體。</span><span class="sxs-lookup"><span data-stu-id="a0f1d-103">Represents a common language runtime (CLR) instance that is loaded in a process on a remote machine.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0f1d-104">語法</span><span class="sxs-lookup"><span data-stu-id="a0f1d-104">Syntax</span></span>  
  
```cpp  
struct  CoreClrDebugRuntimeInfo {  
    DWORD m_dwInternalID;  
};  
```  
  
## <a name="members"></a><span data-ttu-id="a0f1d-105">成員</span><span class="sxs-lookup"><span data-stu-id="a0f1d-105">Members</span></span>  
  
|<span data-ttu-id="a0f1d-106">member</span><span class="sxs-lookup"><span data-stu-id="a0f1d-106">Member</span></span>|<span data-ttu-id="a0f1d-107">描述</span><span class="sxs-lookup"><span data-stu-id="a0f1d-107">Description</span></span>|  
|------------|-----------------|  
|`m_dwInternalID`|<span data-ttu-id="a0f1d-108">在目標電腦上執行之遠端偵錯 Proxy 所指派的執行階段識別項。</span><span class="sxs-lookup"><span data-stu-id="a0f1d-108">Runtime identifier that is assigned by the remote debugging proxy running on the target machine.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a0f1d-109">需求</span><span class="sxs-lookup"><span data-stu-id="a0f1d-109">Requirements</span></span>  
 <span data-ttu-id="a0f1d-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a0f1d-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0f1d-111">**標頭：** CoreClrRemoteDebuggingInterfaces。h</span><span class="sxs-lookup"><span data-stu-id="a0f1d-111">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="a0f1d-112">連結**庫：** mscordbi_macx86 .dll</span><span class="sxs-lookup"><span data-stu-id="a0f1d-112">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="a0f1d-113">**.NET Framework 版本：** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="a0f1d-113">**.NET Framework Versions:** 3.5 SP1</span></span>
