---
title: ICLRDataTarget::GetMachineType 方法
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetMachineType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetMachineType
helpviewer_keywords:
- ICLRDataTarget::GetMachineType method [.NET Framework debugging]
- GetMachineType method [.NET Framework debugging]
ms.assetid: 5f1f9c61-3e3b-48b2-b111-a4395f7623a7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5727142f55e143cf144dae842f95a36effb33c68
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57482232"
---
# <a name="iclrdatatargetgetmachinetype-method"></a><span data-ttu-id="67217-102">ICLRDataTarget::GetMachineType 方法</span><span class="sxs-lookup"><span data-stu-id="67217-102">ICLRDataTarget::GetMachineType Method</span></span>
<span data-ttu-id="67217-103">取得目標處理序正在使用的指令集的類型識別項。</span><span class="sxs-lookup"><span data-stu-id="67217-103">Gets the identifier for the kind of instruction set that the target process is using.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67217-104">語法</span><span class="sxs-lookup"><span data-stu-id="67217-104">Syntax</span></span>  
  
```  
HRESULT GetMachineType (  
    [out] ULONG32     *machineType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67217-105">參數</span><span class="sxs-lookup"><span data-stu-id="67217-105">Parameters</span></span>  
 `machineType`  
 <span data-ttu-id="67217-106">[out]使用值，指出的指令集，目標處理序的指標。</span><span class="sxs-lookup"><span data-stu-id="67217-106">[out] A pointer to a value that indicates the instruction set that the target process is using.</span></span> <span data-ttu-id="67217-107">傳回`machineType`是 WinNT.h 標頭檔中所定義的 IMAGE_FILE_MACHINE 常數之一。</span><span class="sxs-lookup"><span data-stu-id="67217-107">The returned `machineType` is one of the IMAGE_FILE_MACHINE constants, which are defined in the WinNT.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67217-108">需求</span><span class="sxs-lookup"><span data-stu-id="67217-108">Requirements</span></span>  
 <span data-ttu-id="67217-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="67217-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67217-110">**標頭：** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="67217-110">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="67217-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="67217-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67217-112">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67217-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67217-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67217-113">See also</span></span>
- [<span data-ttu-id="67217-114">ICLRDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="67217-114">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
