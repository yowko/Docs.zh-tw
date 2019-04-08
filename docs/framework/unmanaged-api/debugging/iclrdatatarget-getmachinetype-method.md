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
ms.openlocfilehash: ff9c88d534e0bfe51075a76581af37aba791a3da
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59148469"
---
# <a name="iclrdatatargetgetmachinetype-method"></a><span data-ttu-id="6ba20-102">ICLRDataTarget::GetMachineType 方法</span><span class="sxs-lookup"><span data-stu-id="6ba20-102">ICLRDataTarget::GetMachineType Method</span></span>
<span data-ttu-id="6ba20-103">取得目標處理序正在使用的指令集的類型識別項。</span><span class="sxs-lookup"><span data-stu-id="6ba20-103">Gets the identifier for the kind of instruction set that the target process is using.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ba20-104">語法</span><span class="sxs-lookup"><span data-stu-id="6ba20-104">Syntax</span></span>  
  
```  
HRESULT GetMachineType (  
    [out] ULONG32     *machineType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6ba20-105">參數</span><span class="sxs-lookup"><span data-stu-id="6ba20-105">Parameters</span></span>  
 `machineType`  
 <span data-ttu-id="6ba20-106">[out]使用值，指出的指令集，目標處理序的指標。</span><span class="sxs-lookup"><span data-stu-id="6ba20-106">[out] A pointer to a value that indicates the instruction set that the target process is using.</span></span> <span data-ttu-id="6ba20-107">傳回`machineType`是 WinNT.h 標頭檔中所定義的 IMAGE_FILE_MACHINE 常數之一。</span><span class="sxs-lookup"><span data-stu-id="6ba20-107">The returned `machineType` is one of the IMAGE_FILE_MACHINE constants, which are defined in the WinNT.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ba20-108">需求</span><span class="sxs-lookup"><span data-stu-id="6ba20-108">Requirements</span></span>  
 <span data-ttu-id="6ba20-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6ba20-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ba20-110">**標頭：** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="6ba20-110">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="6ba20-111">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6ba20-111">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="6ba20-112">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="6ba20-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6ba20-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6ba20-113">See also</span></span>

- [<span data-ttu-id="6ba20-114">ICLRDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="6ba20-114">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
