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
ms.openlocfilehash: c515a8184e8c01b0e292057f3f66ffef28f2c5fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402877"
---
# <a name="iclrdatatargetgetmachinetype-method"></a><span data-ttu-id="16338-102">ICLRDataTarget::GetMachineType 方法</span><span class="sxs-lookup"><span data-stu-id="16338-102">ICLRDataTarget::GetMachineType Method</span></span>
<span data-ttu-id="16338-103">取得目標處理序正在使用的指令集類型的識別項。</span><span class="sxs-lookup"><span data-stu-id="16338-103">Gets the identifier for the kind of instruction set that the target process is using.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16338-104">語法</span><span class="sxs-lookup"><span data-stu-id="16338-104">Syntax</span></span>  
  
```  
HRESULT GetMachineType (  
    [out] ULONG32     *machineType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="16338-105">參數</span><span class="sxs-lookup"><span data-stu-id="16338-105">Parameters</span></span>  
 `machineType`  
 <span data-ttu-id="16338-106">[out]指標值，指出的指令集的目標處理序正在使用。</span><span class="sxs-lookup"><span data-stu-id="16338-106">[out] A pointer to a value that indicates the instruction set that the target process is using.</span></span> <span data-ttu-id="16338-107">傳回`machineType`是 IMAGE_FILE_MACHINE 常數、 WinNT.h 標頭檔中定義的其中一個。</span><span class="sxs-lookup"><span data-stu-id="16338-107">The returned `machineType` is one of the IMAGE_FILE_MACHINE constants, which are defined in the WinNT.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16338-108">需求</span><span class="sxs-lookup"><span data-stu-id="16338-108">Requirements</span></span>  
 <span data-ttu-id="16338-109">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="16338-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16338-110">**標頭：** ClrData.idl、 ClrData.h</span><span class="sxs-lookup"><span data-stu-id="16338-110">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="16338-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="16338-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16338-112">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16338-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16338-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16338-113">See Also</span></span>  
 [<span data-ttu-id="16338-114">ICLRDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="16338-114">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
