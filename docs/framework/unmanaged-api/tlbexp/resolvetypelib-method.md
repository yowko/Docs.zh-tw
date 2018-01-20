---
title: "ResolveTypeLib 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ResolveTypeLib
api_location: tlbref.dll
f1_keywords: ResolveTypeLib
helpviewer_keywords:
- ITypeLibResolver::ResolveTypeLib method [.NET Framework]
- ResolveTypeLib method [.NET Framework]
ms.assetid: 95d2aa0d-8eeb-4a9f-a216-5249f7e2c167
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 72d1cedbfc1a1ec6c3588a7b0be9cf657d7369fd
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="resolvetypelib-method"></a><span data-ttu-id="21d5a-102">ResolveTypeLib 方法</span><span class="sxs-lookup"><span data-stu-id="21d5a-102">ResolveTypeLib Method</span></span>
<span data-ttu-id="21d5a-103">藉由傳回其完整的路徑來解析類型程式庫的簡單名稱。</span><span class="sxs-lookup"><span data-stu-id="21d5a-103">Resolves the simple name of a type library by returning its fully qualified path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21d5a-104">語法</span><span class="sxs-lookup"><span data-stu-id="21d5a-104">Syntax</span></span>  
  
```  
HRESULT ResolveTypeLib(  
    [in]  BSTR      bstrSimpleName,  
    [in]  GUID      tlbid,  
    [in]  LCID      lcid,  
    [in]  USHORT    wMajorVersion,  
    [in]  USHORT    wMinorVersion,  
    [in]  SYSKIND   syskind,  
    [out] BSTR     *pbstrResolvedTlbName);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="21d5a-105">參數</span><span class="sxs-lookup"><span data-stu-id="21d5a-105">Parameters</span></span>  
 `bstrSimpleName`  
 <span data-ttu-id="21d5a-106">[in]A [BSTR](http://msdn.microsoft.com/library/1b2d7d2c-47af-4389-a6b6-b01b7e915228) ，其中包含的類型程式庫的簡單名稱。</span><span class="sxs-lookup"><span data-stu-id="21d5a-106">[in] A [BSTR](http://msdn.microsoft.com/library/1b2d7d2c-47af-4389-a6b6-b01b7e915228) that contains the simple name of the type library.</span></span>  
  
 `tlbid`  
 <span data-ttu-id="21d5a-107">[in]指派給類型程式庫中登錄的 GUID。</span><span class="sxs-lookup"><span data-stu-id="21d5a-107">[in] The GUID assigned to the type library in the registry.</span></span>  
  
 `lcid`  
 <span data-ttu-id="21d5a-108">[in]當地語系化類型程式庫的識別碼。</span><span class="sxs-lookup"><span data-stu-id="21d5a-108">[in] The localization ID of the type library.</span></span>  
  
 `wMajorVersion`  
 <span data-ttu-id="21d5a-109">[in]類型程式庫的主要版本號碼。</span><span class="sxs-lookup"><span data-stu-id="21d5a-109">[in] The major version number of the type library.</span></span> <span data-ttu-id="21d5a-110">例如，針對版本*x.y*，主要版本號碼是*x*。</span><span class="sxs-lookup"><span data-stu-id="21d5a-110">For example, for version *x.y*, the major version number is *x*.</span></span>  
  
 `wMinorVersion`  
 <span data-ttu-id="21d5a-111">[in]類型程式庫的次要版本號碼。</span><span class="sxs-lookup"><span data-stu-id="21d5a-111">[in] The minor version number of the type library.</span></span> <span data-ttu-id="21d5a-112">例如，針對版本*x.y*，次要版本號碼是*y*。</span><span class="sxs-lookup"><span data-stu-id="21d5a-112">For example, for version *x.y*, the minor version number is *y*.</span></span>  
  
 `syskind`  
 <span data-ttu-id="21d5a-113">[in]A [SYSKIND](http://msdn.microsoft.com/library/662048b2-59a8-48ca-9e4f-2f9a5306faa1)識別的作業環境的旗標。</span><span class="sxs-lookup"><span data-stu-id="21d5a-113">[in] A [SYSKIND](http://msdn.microsoft.com/library/662048b2-59a8-48ca-9e4f-2f9a5306faa1) flag that identifies the operating environment.</span></span> <span data-ttu-id="21d5a-114">常見的值為 SYS_WIN32 和 SYS_WIN64。</span><span class="sxs-lookup"><span data-stu-id="21d5a-114">Common values are SYS_WIN32 and SYS_WIN64.</span></span>  
  
 `pbstrResolvedTlbName`  
 <span data-ttu-id="21d5a-115">[out]指標[BSTR](http://msdn.microsoft.com/library/1b2d7d2c-47af-4389-a6b6-b01b7e915228) ，其中包含名為中的類型程式庫的完整路徑`bstrSimpleName`參數。</span><span class="sxs-lookup"><span data-stu-id="21d5a-115">[out] A pointer to a [BSTR](http://msdn.microsoft.com/library/1b2d7d2c-47af-4389-a6b6-b01b7e915228) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21d5a-116">備註</span><span class="sxs-lookup"><span data-stu-id="21d5a-116">Remarks</span></span>  
 <span data-ttu-id="21d5a-117">`ResolveTypeLib`方法透過呼叫[LoadTypeLibWithResolver 函式](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md)期間[Tlbexp.exe （類型程式庫匯出工具）](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)處理。</span><span class="sxs-lookup"><span data-stu-id="21d5a-117">The `ResolveTypeLib` method is called by the [LoadTypeLibWithResolver function](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md) during [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) processing.</span></span>  
  
 <span data-ttu-id="21d5a-118">此介面的自訂實作必須傳回[BSTR](http://msdn.microsoft.com/library/1b2d7d2c-47af-4389-a6b6-b01b7e915228) ，其中包含名為中的類型程式庫的完整路徑`bstrSimpleName`參數。</span><span class="sxs-lookup"><span data-stu-id="21d5a-118">Custom implementations of this interface must return a [BSTR](http://msdn.microsoft.com/library/1b2d7d2c-47af-4389-a6b6-b01b7e915228) that contains the full path of the type library named in the `bstrSimpleName` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21d5a-119">需求</span><span class="sxs-lookup"><span data-stu-id="21d5a-119">Requirements</span></span>  
 <span data-ttu-id="21d5a-120">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="21d5a-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21d5a-121">**標頭：** TlbRef.idl、 TlbRef.h</span><span class="sxs-lookup"><span data-stu-id="21d5a-121">**Header:** TlbRef.idl, TlbRef.h</span></span>  
  
 <span data-ttu-id="21d5a-122">**程式庫：** TlbRef.lib</span><span class="sxs-lookup"><span data-stu-id="21d5a-122">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="21d5a-123">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21d5a-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21d5a-124">請參閱</span><span class="sxs-lookup"><span data-stu-id="21d5a-124">See Also</span></span>  
 [<span data-ttu-id="21d5a-125">Tlbexp Helper 函式</span><span class="sxs-lookup"><span data-stu-id="21d5a-125">Tlbexp Helper Functions</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 [<span data-ttu-id="21d5a-126">LoadTypeLibEx</span><span class="sxs-lookup"><span data-stu-id="21d5a-126">LoadTypeLibEx</span></span>](http://msdn.microsoft.com/library/56a7f9e1-810b-4a42-aa4d-691f4304f5ef)
