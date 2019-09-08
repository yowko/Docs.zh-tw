---
title: GetDemultiplexedStub 函式（非受控 API 參考）
description: GetDemultiplexedStub 函式會建立物件轉寄站接收，以協助用戶端接收來自 Windows 管理的非同步呼叫。
ms.date: 11/06/2017
api_name:
- GetDemultiplexedStub
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetDemultiplexedStub
helpviewer_keywords:
- GetDemultiplexedStub function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a2d3885a4a9e54950909053ba18de5b1891e7edf
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798605"
---
# <a name="getdemultiplexedstub-function"></a><span data-ttu-id="8b1a0-103">GetDemultiplexedStub 函式</span><span class="sxs-lookup"><span data-stu-id="8b1a0-103">GetDemultiplexedStub function</span></span>
<span data-ttu-id="8b1a0-104">建立物件轉寄站接收以協助用戶端從 Windows Management 接收非同步呼叫。</span><span class="sxs-lookup"><span data-stu-id="8b1a0-104">Creates an object forwarder sink to assist a client in receiving asynchronous calls from Windows Management.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="8b1a0-105">語法</span><span class="sxs-lookup"><span data-stu-id="8b1a0-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDemultiplexedStub (
   [in] IUnknown*    pObject, 
   [in] boolean      isLocal, 
   [out] IUnknown**  ppObject
); 
```  

## <a name="parameters"></a><span data-ttu-id="8b1a0-106">參數</span><span class="sxs-lookup"><span data-stu-id="8b1a0-106">Parameters</span></span>

`pObject`  
<span data-ttu-id="8b1a0-107">在[IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink)的用戶端同進程執行的指標。</span><span class="sxs-lookup"><span data-stu-id="8b1a0-107">[in] A pointer to the client's in-process implementation of [IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink).</span></span>

`isLocal`  
<span data-ttu-id="8b1a0-108">在指出事件是否為本機（`true`）的旗標， `false`否則為。</span><span class="sxs-lookup"><span data-stu-id="8b1a0-108">[in] A flag that indicates whether the event is local (`true`); otherwise, `false`.</span></span>

`ppObject`  
<span data-ttu-id="8b1a0-109">脫銷物件轉寄站接收，可協助用戶端接收來自 Windows 管理的非同步呼叫。</span><span class="sxs-lookup"><span data-stu-id="8b1a0-109">[out] A object forwarder sink to assist a client in receiving asynchronous calls from Windows Management.</span></span>

## <a name="return-value"></a><span data-ttu-id="8b1a0-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="8b1a0-110">Return value</span></span>

<span data-ttu-id="8b1a0-111">如果函式成功，則傳回值為`S_OK` （0）。</span><span class="sxs-lookup"><span data-stu-id="8b1a0-111">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="8b1a0-112">如果函式失敗，則傳回值為非零的錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="8b1a0-112">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="8b1a0-113">若要取得擴充的錯誤資訊，請呼叫[GetErrorInfo](geterrorinfo.md)函式。</span><span class="sxs-lookup"><span data-stu-id="8b1a0-113">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>
    
## <a name="requirements"></a><span data-ttu-id="8b1a0-114">需求</span><span class="sxs-lookup"><span data-stu-id="8b1a0-114">Requirements</span></span>  
 <span data-ttu-id="8b1a0-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8b1a0-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b1a0-116">**標頭：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="8b1a0-116">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="8b1a0-117">**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8b1a0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b1a0-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b1a0-118">See also</span></span>

- [<span data-ttu-id="8b1a0-119">WMI 和效能計數器（非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="8b1a0-119">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
