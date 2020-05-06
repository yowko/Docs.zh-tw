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
ms.openlocfilehash: 9d86b23b91702929a86334f557a8d647e19861a4
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860598"
---
# <a name="iclrdatatargetgetmachinetype-method"></a><span data-ttu-id="9e300-102">ICLRDataTarget::GetMachineType 方法</span><span class="sxs-lookup"><span data-stu-id="9e300-102">ICLRDataTarget::GetMachineType Method</span></span>
<span data-ttu-id="9e300-103">取得目標進程所使用之指令集種類的識別碼。</span><span class="sxs-lookup"><span data-stu-id="9e300-103">Gets the identifier for the kind of instruction set that the target process is using.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e300-104">語法</span><span class="sxs-lookup"><span data-stu-id="9e300-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMachineType (  
    [out] ULONG32     *machineType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9e300-105">參數</span><span class="sxs-lookup"><span data-stu-id="9e300-105">Parameters</span></span>  
 `machineType`  
 <span data-ttu-id="9e300-106">脫銷值的指標，表示目標進程所使用的指令集。</span><span class="sxs-lookup"><span data-stu-id="9e300-106">[out] A pointer to a value that indicates the instruction set that the target process is using.</span></span> <span data-ttu-id="9e300-107">傳回`machineType`的是在 WinNT 標頭檔中定義的其中一個 IMAGE_FILE_MACHINE 常數。</span><span class="sxs-lookup"><span data-stu-id="9e300-107">The returned `machineType` is one of the IMAGE_FILE_MACHINE constants, which are defined in the WinNT.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e300-108">需求</span><span class="sxs-lookup"><span data-stu-id="9e300-108">Requirements</span></span>  
 <span data-ttu-id="9e300-109">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9e300-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e300-110">**標頭：** ClrData .idl，ClrData。h</span><span class="sxs-lookup"><span data-stu-id="9e300-110">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="9e300-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9e300-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e300-112">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e300-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e300-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="9e300-113">See also</span></span>

- [<span data-ttu-id="9e300-114">ICLRDataTarget 介面</span><span class="sxs-lookup"><span data-stu-id="9e300-114">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
