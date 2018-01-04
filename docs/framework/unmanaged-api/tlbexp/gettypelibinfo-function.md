---
title: "GetTypeLibInfo 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetTypeLibInfo
api_location: TlbRef.dll
api_type: DLLExport
f1_keywords: GetTypeLibInfo
helpviewer_keywords: GetTypeLibInfo function [.NET Framework]
ms.assetid: a1c4d165-9bdc-4ca8-940e-292d4ffcc338
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4f6b1ad18809b46b7a2b38137231028f696d51b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="gettypelibinfo-function"></a><span data-ttu-id="fe4d4-102">GetTypeLibInfo 函式</span><span class="sxs-lookup"><span data-stu-id="fe4d4-102">GetTypeLibInfo Function</span></span>
<span data-ttu-id="fe4d4-103">傳回指定的類型程式庫的相關資訊，藉由檢查其[TLIBATTR](https://msdn.microsoft.com/library/ms221376\(v=vs.85\).aspx)結構。</span><span class="sxs-lookup"><span data-stu-id="fe4d4-103">Returns information about the specified type library by examining its [TLIBATTR](https://msdn.microsoft.com/library/ms221376\(v=vs.85\).aspx) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe4d4-104">語法</span><span class="sxs-lookup"><span data-stu-id="fe4d4-104">Syntax</span></span>  
  
```  
HRESULT GetTypeLibInfo(  
    [in]   LPWSTR     szFile,  
    [out]  GUID      *pTypeLibID,  
    [out]  LCID      *pTypeLibLCID,  
    [out]  SYSKIND   *pTypeLibPlatform,  
    [out]  USHORT    *pTypeLibMajorVer,  
    [out]  USHORT    *pTypeLibMinorVer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fe4d4-105">參數</span><span class="sxs-lookup"><span data-stu-id="fe4d4-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="fe4d4-106">[in]類型程式庫檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="fe4d4-106">[in] The file name of the type library.</span></span>  
  
 `pTypeLibID`  
 <span data-ttu-id="fe4d4-107">[out]類型程式庫的 GUID。</span><span class="sxs-lookup"><span data-stu-id="fe4d4-107">[out] The GUID of the type library.</span></span>  
  
 `pTypeLibLCID`  
 <span data-ttu-id="fe4d4-108">[out]當地語系化類型程式庫的識別碼。</span><span class="sxs-lookup"><span data-stu-id="fe4d4-108">[out] The localization ID of the type library.</span></span>  
  
 `pTypeLibPlatform`  
 <span data-ttu-id="fe4d4-109">[out]A [SYSKIND](https://msdn.microsoft.com/library/ms221272\(v=vs.85\).aspx)識別目標作業系統類型程式庫的旗標。</span><span class="sxs-lookup"><span data-stu-id="fe4d4-109">[out] A [SYSKIND](https://msdn.microsoft.com/library/ms221272\(v=vs.85\).aspx) flag that identifies the target operating system for the type library.</span></span> <span data-ttu-id="fe4d4-110">常見的值為 SYS_WIN32 和 SYS_WIN64。</span><span class="sxs-lookup"><span data-stu-id="fe4d4-110">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pTypeLibMajorVer`  
 <span data-ttu-id="fe4d4-111">[out]類型程式庫的主要版本號碼。</span><span class="sxs-lookup"><span data-stu-id="fe4d4-111">[out] The major version number of the type library.</span></span> <span data-ttu-id="fe4d4-112">例如，針對版本*x.y*，主要版本號碼是*x*。</span><span class="sxs-lookup"><span data-stu-id="fe4d4-112">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `pTypeLibMinorVer`  
 <span data-ttu-id="fe4d4-113">[out]類型程式庫的次要版本號碼。</span><span class="sxs-lookup"><span data-stu-id="fe4d4-113">[out] The minor version number of the type library.</span></span> <span data-ttu-id="fe4d4-114">例如，針對版本*x.y*，次要版本號碼是*y*。</span><span class="sxs-lookup"><span data-stu-id="fe4d4-114">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fe4d4-115">備註</span><span class="sxs-lookup"><span data-stu-id="fe4d4-115">Remarks</span></span>  
 <span data-ttu-id="fe4d4-116">`GetTypeLibInfo`函式會呼叫[Tlbexp.exe （類型程式庫匯出工具）](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)。</span><span class="sxs-lookup"><span data-stu-id="fe4d4-116">The `GetTypeLibInfo` function is called by the [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md).</span></span> <span data-ttu-id="fe4d4-117">此工具會產生類型程式庫會描述 common language runtime (CLR) 組件中的類型。</span><span class="sxs-lookup"><span data-stu-id="fe4d4-117">This tool generates a type library that describes the types in a common language runtime (CLR) assembly.</span></span>  
  
 <span data-ttu-id="fe4d4-118">如果任何參數是 null，則此函數會傳回`HRESULT`的`E_POINTER`。</span><span class="sxs-lookup"><span data-stu-id="fe4d4-118">If any parameter is null, the function returns an `HRESULT` of `E_POINTER`.</span></span> <span data-ttu-id="fe4d4-119">否則它會傳回 `S_OK`。</span><span class="sxs-lookup"><span data-stu-id="fe4d4-119">Otherwise, it returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe4d4-120">需求</span><span class="sxs-lookup"><span data-stu-id="fe4d4-120">Requirements</span></span>  
 <span data-ttu-id="fe4d4-121">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fe4d4-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe4d4-122">**標頭：** TlbRef.h</span><span class="sxs-lookup"><span data-stu-id="fe4d4-122">**Header:** TlbRef.h</span></span>  
  
 <span data-ttu-id="fe4d4-123">**程式庫：** TlbRef.lib</span><span class="sxs-lookup"><span data-stu-id="fe4d4-123">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="fe4d4-124">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe4d4-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe4d4-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="fe4d4-125">See Also</span></span>  
 [<span data-ttu-id="fe4d4-126">Tlbexp Helper 函式</span><span class="sxs-lookup"><span data-stu-id="fe4d4-126">Tlbexp Helper Functions</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 <span data-ttu-id="fe4d4-127">[LoadTypeLibEx 函式](https://msdn.microsoft.com/library/ms221249\(v=vs.85\).aspx)</span><span class="sxs-lookup"><span data-stu-id="fe4d4-127">[LoadTypeLibEx Function](https://msdn.microsoft.com/library/ms221249\(v=vs.85\).aspx)</span></span>
