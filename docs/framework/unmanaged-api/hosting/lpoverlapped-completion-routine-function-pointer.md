---
title: LPOVERLAPPED_COMPLETION_ROUTINE 函式指標
ms.date: 03/30/2017
api_name:
- LPOVERLAPPED_COMPLETION_ROUTINE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- LPOVERLAPPED_COMPLETION_ROUTINE
helpviewer_keywords:
- LPOVERLAPPED_COMPLETION_ROUTINE function pointer [.NET Framework hosting]
ms.assetid: 5fb645d9-b818-401c-8c2c-c30d86de58ba
topic_type:
- apiref
ms.openlocfilehash: a3a45a13073cf422064d28554a274e068db6f517
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727506"
---
# <a name="lpoverlapped_completion_routine-function-pointer"></a><span data-ttu-id="d0a22-102">LPOVERLAPPED_COMPLETION_ROUTINE 函式指標</span><span class="sxs-lookup"><span data-stu-id="d0a22-102">LPOVERLAPPED_COMPLETION_ROUTINE Function Pointer</span></span>

<span data-ttu-id="d0a22-103">指向函式，此函式會在重迭 (（也就是對裝置的非同步) i/o 完成）時通知主機。</span><span class="sxs-lookup"><span data-stu-id="d0a22-103">Points to a function that notifies the host when an overlapped (that is, asynchronous) I/O to a device has completed.</span></span>  
  
 <span data-ttu-id="d0a22-104">在 .NET Framework 4 中，此函式指標已被取代。</span><span class="sxs-lookup"><span data-stu-id="d0a22-104">This function pointer has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0a22-105">語法</span><span class="sxs-lookup"><span data-stu-id="d0a22-105">Syntax</span></span>  
  
```cpp  
typedef VOID (*LPOVERLAPPED_COMPLETION_ROUTINE) (  
    [in] DWORD  dwErrorCode,  
    [in] DWORD  dwNumberOfBytesTransfered,  
    [in] LPVOID lpOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0a22-106">參數</span><span class="sxs-lookup"><span data-stu-id="d0a22-106">Parameters</span></span>  

 `dwErrorCode`  
 <span data-ttu-id="d0a22-107">在如果裝置已關閉，則為錯誤碼的值;否則，此值為零。</span><span class="sxs-lookup"><span data-stu-id="d0a22-107">[in] A value that is an error code if the device has been closed; otherwise, this value is zero.</span></span>  
  
 <span data-ttu-id="d0a22-108">關閉裝置會立即完成裝置的所有暫止 i/o。</span><span class="sxs-lookup"><span data-stu-id="d0a22-108">Closing a device causes all pending I/O to the device to be completed immediately.</span></span>  
  
 `dwNumberOfBytesTransfered`  
 <span data-ttu-id="d0a22-109">在I/o 作業傳送的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="d0a22-109">[in] The number of bytes transferred by the I/O operation.</span></span>  
  
 `lpOverlapped`  
 <span data-ttu-id="d0a22-110">在結構的指標，其中包含要用來完成 i/o 要求的資訊。</span><span class="sxs-lookup"><span data-stu-id="d0a22-110">[in] A pointer to a structure that contains information to be used to complete the I/O request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d0a22-111">備註</span><span class="sxs-lookup"><span data-stu-id="d0a22-111">Remarks</span></span>  

 <span data-ttu-id="d0a22-112">指向函式的函式 `LPOVERLAPPED_COMPLETION_ROUTINE` 是回呼函式，而且必須由主控應用程式的寫入器實作為。</span><span class="sxs-lookup"><span data-stu-id="d0a22-112">The function to which `LPOVERLAPPED_COMPLETION_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="d0a22-113">回呼函數可讓主機處理已完成的 i/o 要求。</span><span class="sxs-lookup"><span data-stu-id="d0a22-113">The callback function allows the host to process the completed I/O request.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0a22-114">需求</span><span class="sxs-lookup"><span data-stu-id="d0a22-114">Requirements</span></span>  

 <span data-ttu-id="d0a22-115">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d0a22-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0a22-116">**標頭：** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="d0a22-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d0a22-117">連結 **庫：** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="d0a22-117">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="d0a22-118">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0a22-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0a22-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0a22-119">See also</span></span>

- [<span data-ttu-id="d0a22-120">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="d0a22-120">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
