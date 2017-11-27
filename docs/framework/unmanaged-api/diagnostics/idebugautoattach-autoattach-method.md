---
title: "IDebugAutoAttach::AutoAttach 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDebugAutoAttach.AutoAttach
api_location: diasymreader.dll
api_type: COM
f1_keywords: IDebugAutoAttach::AutoAttach
helpviewer_keywords:
- AutoAttach method [.NET Framework debugging]
- IDebugAutoAttach::AutoAttach method [.NET Framework debugging]
ms.assetid: 3cf3bd9c-7d88-4afa-a476-94cdc7609aa6
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 359aaf96c42a661657028d508f096f9625d4ba71
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="idebugautoattachautoattach-method"></a><span data-ttu-id="826d4-102">IDebugAutoAttach::AutoAttach 方法</span><span class="sxs-lookup"><span data-stu-id="826d4-102">IDebugAutoAttach::AutoAttach Method</span></span>
<span data-ttu-id="826d4-103">執行伺服器叫用偵錯工具自動附加。</span><span class="sxs-lookup"><span data-stu-id="826d4-103">Performs server-invoked debugger auto attach.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="826d4-104">語法</span><span class="sxs-lookup"><span data-stu-id="826d4-104">Syntax</span></span>  
  
```  
HRESULT AutoAttach  
(  
    [in]  REFGUID   guidPort,  
    [in]  DWORD     dwPid,  
    [in]  AUTOATTACH_PROGRAM_TYPE dwProgramType,  
    [in]  DWORD     dwProgramId,  
    [in]  LPCWSTR   pszSessionId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="826d4-105">參數</span><span class="sxs-lookup"><span data-stu-id="826d4-105">Parameters</span></span>  
 `guidPort`  
 <span data-ttu-id="826d4-106">[in]一律設為`GUID_NULL`。</span><span class="sxs-lookup"><span data-stu-id="826d4-106">[in] Always set to `GUID_NULL`.</span></span>  
  
 `dwPid`  
 <span data-ttu-id="826d4-107">[in]處理序識別碼，通常會使用擷取`GetCurrentProcessId`函式。</span><span class="sxs-lookup"><span data-stu-id="826d4-107">[in] Process ID, normally retrieved with the `GetCurrentProcessId` function.</span></span>  
  
 `dwProgramType`  
 <span data-ttu-id="826d4-108">[in]程式類型： `AUTOATTACH_PROGRAM_WIN32`， `AUTOATTACH_PROGRAM_COMPLUS`，或`AUTOATTACH_PROGRAM_UNKNOWN`。</span><span class="sxs-lookup"><span data-stu-id="826d4-108">[in] Program type: `AUTOATTACH_PROGRAM_WIN32`, `AUTOATTACH_PROGRAM_COMPLUS`, or `AUTOATTACH_PROGRAM_UNKNOWN`.</span></span>  
  
 `dwProgramId`  
 <span data-ttu-id="826d4-109">[in]程式識別碼。</span><span class="sxs-lookup"><span data-stu-id="826d4-109">[in] Program ID.</span></span>  
  
 `pszSessionId`  
 <span data-ttu-id="826d4-110">[in]偵錯動詞命令所傳遞的字串。</span><span class="sxs-lookup"><span data-stu-id="826d4-110">[in] String passed by the debug verb.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="826d4-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="826d4-111">Return Value</span></span>  
 <span data-ttu-id="826d4-112">如果此方法成功為 S_OK。</span><span class="sxs-lookup"><span data-stu-id="826d4-112">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="826d4-113">需求</span><span class="sxs-lookup"><span data-stu-id="826d4-113">Requirements</span></span>  
 <span data-ttu-id="826d4-114">**標頭：** DbgAutoAttach.h</span><span class="sxs-lookup"><span data-stu-id="826d4-114">**Header:** DbgAutoAttach.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="826d4-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="826d4-115">See Also</span></span>  
 [<span data-ttu-id="826d4-116">IDebugAutoAttach 介面</span><span class="sxs-lookup"><span data-stu-id="826d4-116">IDebugAutoAttach Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)
