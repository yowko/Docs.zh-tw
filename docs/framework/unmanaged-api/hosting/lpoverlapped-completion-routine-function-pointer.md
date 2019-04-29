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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce2ce6dd1210eef94e77b5d6a2d58a35cf971e6d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765254"
---
# <a name="lpoverlappedcompletionroutine-function-pointer"></a><span data-ttu-id="799e6-102">LPOVERLAPPED_COMPLETION_ROUTINE 函式指標</span><span class="sxs-lookup"><span data-stu-id="799e6-102">LPOVERLAPPED_COMPLETION_ROUTINE Function Pointer</span></span>
<span data-ttu-id="799e6-103">指向主應用程式時之重疊的函式 (也就是非同步) 至裝置的 I/O 已完成。</span><span class="sxs-lookup"><span data-stu-id="799e6-103">Points to a function that notifies the host when an overlapped (that is, asynchronous) I/O to a device has completed.</span></span>  
  
 <span data-ttu-id="799e6-104">中已被取代此函式指標[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="799e6-104">This function pointer has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="799e6-105">語法</span><span class="sxs-lookup"><span data-stu-id="799e6-105">Syntax</span></span>  
  
```  
typedef VOID (*LPOVERLAPPED_COMPLETION_ROUTINE) (  
    [in] DWORD  dwErrorCode,  
    [in] DWORD  dwNumberOfBytesTransfered,  
    [in] LPVOID lpOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="799e6-106">參數</span><span class="sxs-lookup"><span data-stu-id="799e6-106">Parameters</span></span>  
 `dwErrorCode`  
 <span data-ttu-id="799e6-107">[in]如果裝置已關閉; 為錯誤碼的值否則，此值為零。</span><span class="sxs-lookup"><span data-stu-id="799e6-107">[in] A value that is an error code if the device has been closed; otherwise, this value is zero.</span></span>  
  
 <span data-ttu-id="799e6-108">關閉裝置，讓所有擱置 I/O 裝置中的立即完成。</span><span class="sxs-lookup"><span data-stu-id="799e6-108">Closing a device causes all pending I/O to the device to be completed immediately.</span></span>  
  
 `dwNumberOfBytesTransfered`  
 <span data-ttu-id="799e6-109">[in]I/O 作業所傳送的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="799e6-109">[in] The number of bytes transferred by the I/O operation.</span></span>  
  
 `lpOverlapped`  
 <span data-ttu-id="799e6-110">[in]包含用來完成的 I/O 要求的資訊結構的指標。</span><span class="sxs-lookup"><span data-stu-id="799e6-110">[in] A pointer to a structure that contains information to be used to complete the I/O request.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="799e6-111">備註</span><span class="sxs-lookup"><span data-stu-id="799e6-111">Remarks</span></span>  
 <span data-ttu-id="799e6-112">函式，其中`LPOVERLAPPED_COMPLETION_ROUTINE`點是回呼函式，而且必須在裝載應用程式寫入器實作。</span><span class="sxs-lookup"><span data-stu-id="799e6-112">The function to which `LPOVERLAPPED_COMPLETION_ROUTINE` points is a callback function and must be implemented by the writer of the hosting application.</span></span> <span data-ttu-id="799e6-113">回呼函式可讓主應用程式處理已完成的 I/O 要求。</span><span class="sxs-lookup"><span data-stu-id="799e6-113">The callback function allows the host to process the completed I/O request.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="799e6-114">需求</span><span class="sxs-lookup"><span data-stu-id="799e6-114">Requirements</span></span>  
 <span data-ttu-id="799e6-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="799e6-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="799e6-116">**標頭：** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="799e6-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="799e6-117">**LIBRARY:** MSCorWks.dll</span><span class="sxs-lookup"><span data-stu-id="799e6-117">**Library:** MSCorWks.dll</span></span>  
  
 <span data-ttu-id="799e6-118">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="799e6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="799e6-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="799e6-119">See also</span></span>

- [<span data-ttu-id="799e6-120">已被取代的 CLR 裝載函式</span><span class="sxs-lookup"><span data-stu-id="799e6-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
