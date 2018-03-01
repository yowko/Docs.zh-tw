---
title: "CreateInstallReferenceEnum 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CreateInstallReferenceEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateInstallReference
helpviewer_keywords:
- CreateInstallReference function [.NET Framework fusion]
ms.assetid: 80dbbbf8-54fc-4894-b74a-0179d3201083
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a0c902cf5d9d8b6295cab95552aae6775c5bf889
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="createinstallreferenceenum-function"></a><span data-ttu-id="711e3-102">CreateInstallReferenceEnum 函式</span><span class="sxs-lookup"><span data-stu-id="711e3-102">CreateInstallReferenceEnum Function</span></span>
<span data-ttu-id="711e3-103">取得指標[IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)執行個體，表示應用程式的參考指定組件的清單。</span><span class="sxs-lookup"><span data-stu-id="711e3-103">Gets a pointer to an [IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) instance that represents a list of an application's references to the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="711e3-104">語法</span><span class="sxs-lookup"><span data-stu-id="711e3-104">Syntax</span></span>  
  
```  
HRESULT CreateInstallReferenceEnum (  
    [out] IInstallReferenceEnum **ppRefEnum,  
    [in]  IAssemblyName         *pName,  
    [in]  DWORD                 dwFlags,  
    [in]  LPVOID                pvReserved  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="711e3-105">參數</span><span class="sxs-lookup"><span data-stu-id="711e3-105">Parameters</span></span>  
 `ppRefEnum`  
 <span data-ttu-id="711e3-106">[out]傳回`IInstallReferenceEnum`指標。</span><span class="sxs-lookup"><span data-stu-id="711e3-106">[out] The returned `IInstallReferenceEnum` pointer.</span></span>  
  
 `pName`  
 <span data-ttu-id="711e3-107">[in][IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)可識別列舉參考的組件。</span><span class="sxs-lookup"><span data-stu-id="711e3-107">[in] The [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) that identifies the assembly for which to enumerate references.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="711e3-108">[in]影響列舉值的行為的旗標。</span><span class="sxs-lookup"><span data-stu-id="711e3-108">[in] Flags that influence the enumerator's behavior.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="711e3-109">[in]保留供未來擴充。</span><span class="sxs-lookup"><span data-stu-id="711e3-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="711e3-110">`pvReserved`必須是 null 參考。</span><span class="sxs-lookup"><span data-stu-id="711e3-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="711e3-111">需求</span><span class="sxs-lookup"><span data-stu-id="711e3-111">Requirements</span></span>  
 <span data-ttu-id="711e3-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="711e3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="711e3-113">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="711e3-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="711e3-114">**程式庫：** Fusion.dll 和 Mscorwks.dll。</span><span class="sxs-lookup"><span data-stu-id="711e3-114">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="711e3-115">使用而不是 Mscorwks.dll 的 Fusion.dll，以確保您設為目標的.NET framework 正確版本。</span><span class="sxs-lookup"><span data-stu-id="711e3-115">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="711e3-116">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="711e3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="711e3-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="711e3-117">See Also</span></span>  
 [<span data-ttu-id="711e3-118">IInstallReferenceEnum 介面</span><span class="sxs-lookup"><span data-stu-id="711e3-118">IInstallReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)  
 [<span data-ttu-id="711e3-119">IAssemblyName 介面</span><span class="sxs-lookup"><span data-stu-id="711e3-119">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="711e3-120">融合全域靜態函式</span><span class="sxs-lookup"><span data-stu-id="711e3-120">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
