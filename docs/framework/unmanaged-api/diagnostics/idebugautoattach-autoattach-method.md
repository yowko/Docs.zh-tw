---
title: IDebugAutoAttach::AutoAttach 方法
ms.date: 03/30/2017
api_name:
- IDebugAutoAttach.AutoAttach
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IDebugAutoAttach::AutoAttach
helpviewer_keywords:
- AutoAttach method [.NET Framework debugging]
- IDebugAutoAttach::AutoAttach method [.NET Framework debugging]
ms.assetid: 3cf3bd9c-7d88-4afa-a476-94cdc7609aa6
topic_type:
- apiref
ms.openlocfilehash: 766aeb31436101babeab31b615a1c633578bfcc5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445518"
---
# <a name="idebugautoattachautoattach-method"></a><span data-ttu-id="e57cd-102">IDebugAutoAttach::AutoAttach 方法</span><span class="sxs-lookup"><span data-stu-id="e57cd-102">IDebugAutoAttach::AutoAttach Method</span></span>
<span data-ttu-id="e57cd-103">Performs server-invoked debugger auto attach.</span><span class="sxs-lookup"><span data-stu-id="e57cd-103">Performs server-invoked debugger auto attach.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e57cd-104">語法</span><span class="sxs-lookup"><span data-stu-id="e57cd-104">Syntax</span></span>  
  
```cpp  
HRESULT AutoAttach  
(  
    [in]  REFGUID   guidPort,  
    [in]  DWORD     dwPid,  
    [in]  AUTOATTACH_PROGRAM_TYPE dwProgramType,  
    [in]  DWORD     dwProgramId,  
    [in]  LPCWSTR   pszSessionId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e57cd-105">參數</span><span class="sxs-lookup"><span data-stu-id="e57cd-105">Parameters</span></span>  
 `guidPort`  
 <span data-ttu-id="e57cd-106">[in] Always set to `GUID_NULL`.</span><span class="sxs-lookup"><span data-stu-id="e57cd-106">[in] Always set to `GUID_NULL`.</span></span>  
  
 `dwPid`  
 <span data-ttu-id="e57cd-107">[in] Process ID, normally retrieved with the `GetCurrentProcessId` function.</span><span class="sxs-lookup"><span data-stu-id="e57cd-107">[in] Process ID, normally retrieved with the `GetCurrentProcessId` function.</span></span>  
  
 `dwProgramType`  
 <span data-ttu-id="e57cd-108">[in] Program type: `AUTOATTACH_PROGRAM_WIN32`, `AUTOATTACH_PROGRAM_COMPLUS`, or `AUTOATTACH_PROGRAM_UNKNOWN`.</span><span class="sxs-lookup"><span data-stu-id="e57cd-108">[in] Program type: `AUTOATTACH_PROGRAM_WIN32`, `AUTOATTACH_PROGRAM_COMPLUS`, or `AUTOATTACH_PROGRAM_UNKNOWN`.</span></span>  
  
 `dwProgramId`  
 <span data-ttu-id="e57cd-109">[in] Program ID.</span><span class="sxs-lookup"><span data-stu-id="e57cd-109">[in] Program ID.</span></span>  
  
 `pszSessionId`  
 <span data-ttu-id="e57cd-110">[in] String passed by the debug verb.</span><span class="sxs-lookup"><span data-stu-id="e57cd-110">[in] String passed by the debug verb.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e57cd-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="e57cd-111">Return Value</span></span>  
 <span data-ttu-id="e57cd-112">S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="e57cd-112">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e57cd-113">需求</span><span class="sxs-lookup"><span data-stu-id="e57cd-113">Requirements</span></span>  
 <span data-ttu-id="e57cd-114">**Header:** DbgAutoAttach.h</span><span class="sxs-lookup"><span data-stu-id="e57cd-114">**Header:** DbgAutoAttach.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e57cd-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="e57cd-115">See also</span></span>

- [<span data-ttu-id="e57cd-116">IDebugAutoAttach 介面</span><span class="sxs-lookup"><span data-stu-id="e57cd-116">IDebugAutoAttach Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)
