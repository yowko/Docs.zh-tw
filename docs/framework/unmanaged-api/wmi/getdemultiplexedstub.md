---
title: 獲取多工Stub函數（非託管 API 引用）
description: GetDe多工Stub函數創建一個物件轉寄站接收器，以説明用戶端接收來自 Windows 管理的非同步調用。
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
ms.openlocfilehash: d15fed261db2ca2cda6dbf824dc9cb0d5c56eed3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174962"
---
# <a name="getdemultiplexedstub-function"></a><span data-ttu-id="f0261-103">GetDemultiplexedStub 函式</span><span class="sxs-lookup"><span data-stu-id="f0261-103">GetDemultiplexedStub function</span></span>
<span data-ttu-id="f0261-104">建立物件轉寄站接收以協助用戶端從 Windows Management 接收非同步呼叫。</span><span class="sxs-lookup"><span data-stu-id="f0261-104">Creates an object forwarder sink to assist a client in receiving asynchronous calls from Windows Management.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="f0261-105">語法</span><span class="sxs-lookup"><span data-stu-id="f0261-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDemultiplexedStub (
   [in] IUnknown*    pObject,
   [in] boolean      isLocal,
   [out] IUnknown**  ppObject
);
```  

## <a name="parameters"></a><span data-ttu-id="f0261-106">參數</span><span class="sxs-lookup"><span data-stu-id="f0261-106">Parameters</span></span>

`pObject`  
<span data-ttu-id="f0261-107">[在]指向用戶端在進程中實現[IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink)的指標。</span><span class="sxs-lookup"><span data-stu-id="f0261-107">[in] A pointer to the client's in-process implementation of [IWbemObjectSink](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectsink).</span></span>

`isLocal`  
<span data-ttu-id="f0261-108">[在]指示事件是否為本地的標誌 （`true`;否則， `false`.</span><span class="sxs-lookup"><span data-stu-id="f0261-108">[in] A flag that indicates whether the event is local (`true`); otherwise, `false`.</span></span>

`ppObject`  
<span data-ttu-id="f0261-109">[出]物件轉寄站接收器，用於説明用戶端接收來自 Windows 管理的非同步調用。</span><span class="sxs-lookup"><span data-stu-id="f0261-109">[out] A object forwarder sink to assist a client in receiving asynchronous calls from Windows Management.</span></span>

## <a name="return-value"></a><span data-ttu-id="f0261-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="f0261-110">Return value</span></span>

<span data-ttu-id="f0261-111">如果函數成功，則傳回值為`S_OK`（0）。</span><span class="sxs-lookup"><span data-stu-id="f0261-111">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="f0261-112">如果函數失敗，傳回值是非零錯誤代碼。</span><span class="sxs-lookup"><span data-stu-id="f0261-112">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="f0261-113">要獲取擴展的錯誤資訊，請致電[GetErrorInfo](geterrorinfo.md)函數。</span><span class="sxs-lookup"><span data-stu-id="f0261-113">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="f0261-114">需求</span><span class="sxs-lookup"><span data-stu-id="f0261-114">Requirements</span></span>  
 <span data-ttu-id="f0261-115">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f0261-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0261-116">**標題：** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="f0261-116">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="f0261-117">**.NET 框架版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f0261-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0261-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f0261-118">See also</span></span>

- [<span data-ttu-id="f0261-119">WMI 與效能計數器 (非受控 API 參考)</span><span class="sxs-lookup"><span data-stu-id="f0261-119">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
