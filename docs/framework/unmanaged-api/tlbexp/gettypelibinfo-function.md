---
title: GetTypeLibInfo 函式
ms.date: 03/30/2017
api_name:
- GetTypeLibInfo
api_location:
- TlbRef.dll
api_type:
- DLLExport
f1_keywords:
- GetTypeLibInfo
helpviewer_keywords:
- GetTypeLibInfo function [.NET Framework]
ms.assetid: a1c4d165-9bdc-4ca8-940e-292d4ffcc338
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0ec28c581b8e6e0aff3a2765720b6e9795be931b
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46003096"
---
# <a name="gettypelibinfo-function"></a><span data-ttu-id="00541-102">GetTypeLibInfo 函式</span><span class="sxs-lookup"><span data-stu-id="00541-102">GetTypeLibInfo Function</span></span>
<span data-ttu-id="00541-103">傳回指定的類型程式庫的相關資訊，藉由檢查其[TLIBATTR](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagtlibattr)結構。</span><span class="sxs-lookup"><span data-stu-id="00541-103">Returns information about the specified type library by examining its [TLIBATTR](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagtlibattr) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00541-104">語法</span><span class="sxs-lookup"><span data-stu-id="00541-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="00541-105">參數</span><span class="sxs-lookup"><span data-stu-id="00541-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="00541-106">[in]型別程式庫檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="00541-106">[in] The file name of the type library.</span></span>  
  
 `pTypeLibID`  
 <span data-ttu-id="00541-107">[out]型別程式庫的 GUID。</span><span class="sxs-lookup"><span data-stu-id="00541-107">[out] The GUID of the type library.</span></span>  
  
 `pTypeLibLCID`  
 <span data-ttu-id="00541-108">[out]當地語系化類型程式庫的識別碼。</span><span class="sxs-lookup"><span data-stu-id="00541-108">[out] The localization ID of the type library.</span></span>  
  
 `pTypeLibPlatform`  
 <span data-ttu-id="00541-109">[out]A [SYSKIND](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ne-oaidl-tagsyskind)識別目標作業系統類型程式庫的旗標。</span><span class="sxs-lookup"><span data-stu-id="00541-109">[out] A [SYSKIND](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/ne-oaidl-tagsyskind) flag that identifies the target operating system for the type library.</span></span> <span data-ttu-id="00541-110">常見的值為 SYS_WIN32 和 SYS_WIN64。</span><span class="sxs-lookup"><span data-stu-id="00541-110">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pTypeLibMajorVer`  
 <span data-ttu-id="00541-111">[out]型別程式庫主要版本號碼。</span><span class="sxs-lookup"><span data-stu-id="00541-111">[out] The major version number of the type library.</span></span> <span data-ttu-id="00541-112">例如，針對版本*x.y*，主要版本號碼是*x*。</span><span class="sxs-lookup"><span data-stu-id="00541-112">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `pTypeLibMinorVer`  
 <span data-ttu-id="00541-113">[out]型別程式庫的次要版本號碼。</span><span class="sxs-lookup"><span data-stu-id="00541-113">[out] The minor version number of the type library.</span></span> <span data-ttu-id="00541-114">例如，針對版本*x.y*，次要版本號碼是*y*。</span><span class="sxs-lookup"><span data-stu-id="00541-114">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00541-115">備註</span><span class="sxs-lookup"><span data-stu-id="00541-115">Remarks</span></span>  
 <span data-ttu-id="00541-116">`GetTypeLibInfo`函式會呼叫[Tlbexp.exe （類型程式庫匯出工具）](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)。</span><span class="sxs-lookup"><span data-stu-id="00541-116">The `GetTypeLibInfo` function is called by the [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md).</span></span> <span data-ttu-id="00541-117">此工具會產生類型程式庫，描述 common language runtime (CLR) 組件中的類型。</span><span class="sxs-lookup"><span data-stu-id="00541-117">This tool generates a type library that describes the types in a common language runtime (CLR) assembly.</span></span>  
  
 <span data-ttu-id="00541-118">如果任何參數為 null，則函數會傳回`HRESULT`的`E_POINTER`。</span><span class="sxs-lookup"><span data-stu-id="00541-118">If any parameter is null, the function returns an `HRESULT` of `E_POINTER`.</span></span> <span data-ttu-id="00541-119">否則它會傳回 `S_OK`。</span><span class="sxs-lookup"><span data-stu-id="00541-119">Otherwise, it returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00541-120">需求</span><span class="sxs-lookup"><span data-stu-id="00541-120">Requirements</span></span>  
 <span data-ttu-id="00541-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="00541-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00541-122">**標頭：** TlbRef.h</span><span class="sxs-lookup"><span data-stu-id="00541-122">**Header:** TlbRef.h</span></span>  
  
 <span data-ttu-id="00541-123">**程式庫：** TlbRef.lib</span><span class="sxs-lookup"><span data-stu-id="00541-123">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="00541-124">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00541-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00541-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00541-125">See Also</span></span>  
 [<span data-ttu-id="00541-126">Tlbexp Helper 函式</span><span class="sxs-lookup"><span data-stu-id="00541-126">Tlbexp Helper Functions</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 [<span data-ttu-id="00541-127">LoadTypeLibEx 函式</span><span class="sxs-lookup"><span data-stu-id="00541-127">LoadTypeLibEx Function</span></span>](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
