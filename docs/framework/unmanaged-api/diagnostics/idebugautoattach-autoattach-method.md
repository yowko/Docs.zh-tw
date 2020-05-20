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
ms.openlocfilehash: aae03b0dc76639c50f4615d41eef73990226b5f7
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442120"
---
# <a name="idebugautoattachautoattach-method"></a><span data-ttu-id="20ae1-102">IDebugAutoAttach::AutoAttach 方法</span><span class="sxs-lookup"><span data-stu-id="20ae1-102">IDebugAutoAttach::AutoAttach Method</span></span>
<span data-ttu-id="20ae1-103">執行伺服器叫用的偵錯工具自動附加。</span><span class="sxs-lookup"><span data-stu-id="20ae1-103">Performs server-invoked debugger auto attach.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20ae1-104">語法</span><span class="sxs-lookup"><span data-stu-id="20ae1-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="20ae1-105">參數</span><span class="sxs-lookup"><span data-stu-id="20ae1-105">Parameters</span></span>  
 `guidPort`  
 <span data-ttu-id="20ae1-106">在一律設定為 `GUID_NULL` 。</span><span class="sxs-lookup"><span data-stu-id="20ae1-106">[in] Always set to `GUID_NULL`.</span></span>  
  
 `dwPid`  
 <span data-ttu-id="20ae1-107">在處理序識別碼，通常會使用函式來抓取 `GetCurrentProcessId` 。</span><span class="sxs-lookup"><span data-stu-id="20ae1-107">[in] Process ID, normally retrieved with the `GetCurrentProcessId` function.</span></span>  
  
 `dwProgramType`  
 <span data-ttu-id="20ae1-108">在程式類型： `AUTOATTACH_PROGRAM_WIN32` 、 `AUTOATTACH_PROGRAM_COMPLUS` 或 `AUTOATTACH_PROGRAM_UNKNOWN` 。</span><span class="sxs-lookup"><span data-stu-id="20ae1-108">[in] Program type: `AUTOATTACH_PROGRAM_WIN32`, `AUTOATTACH_PROGRAM_COMPLUS`, or `AUTOATTACH_PROGRAM_UNKNOWN`.</span></span>  
  
 `dwProgramId`  
 <span data-ttu-id="20ae1-109">在程式識別碼。</span><span class="sxs-lookup"><span data-stu-id="20ae1-109">[in] Program ID.</span></span>  
  
 `pszSessionId`  
 <span data-ttu-id="20ae1-110">在Debug 動詞命令所傳遞的字串。</span><span class="sxs-lookup"><span data-stu-id="20ae1-110">[in] String passed by the debug verb.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="20ae1-111">傳回值</span><span class="sxs-lookup"><span data-stu-id="20ae1-111">Return Value</span></span>  
 <span data-ttu-id="20ae1-112">如果方法成功，則 S_OK。</span><span class="sxs-lookup"><span data-stu-id="20ae1-112">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20ae1-113">需求</span><span class="sxs-lookup"><span data-stu-id="20ae1-113">Requirements</span></span>  
 <span data-ttu-id="20ae1-114">**標頭：** DbgAutoAttach。h</span><span class="sxs-lookup"><span data-stu-id="20ae1-114">**Header:** DbgAutoAttach.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20ae1-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="20ae1-115">See also</span></span>

- [<span data-ttu-id="20ae1-116">IDebugAutoAttach 介面</span><span class="sxs-lookup"><span data-stu-id="20ae1-116">IDebugAutoAttach Interface</span></span>](idebugautoattach-interface.md)
