---
title: "IAssemblyCache::QueryAssemblyInfo 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyCache.QueryAssemblyInfo
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyCache::QueryAssemblyInfo
helpviewer_keywords:
- IAssemblyCache::QueryAssemblyInfo method [.NET Framework fusion]
- QueryAssemblyInfo method [.NET Framework fusion]
ms.assetid: 09313cb5-06f6-43bd-94f4-1055c6b0c99a
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 66e09f805b120239eef764b8cd61835e713e236c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iassemblycachequeryassemblyinfo-method"></a><span data-ttu-id="35caa-102">IAssemblyCache::QueryAssemblyInfo 方法</span><span class="sxs-lookup"><span data-stu-id="35caa-102">IAssemblyCache::QueryAssemblyInfo Method</span></span>
<span data-ttu-id="35caa-103">取得指定的組件的相關要求的資料。</span><span class="sxs-lookup"><span data-stu-id="35caa-103">Gets the requested data about the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35caa-104">語法</span><span class="sxs-lookup"><span data-stu-id="35caa-104">Syntax</span></span>  
  
```  
HRESULT QueryAssemblyInfo (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszAssemblyName,  
    [in, out] ASSEMBLY_INFO *pAsmInfo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="35caa-105">參數</span><span class="sxs-lookup"><span data-stu-id="35caa-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="35caa-106">[in]支援下列值： 旗標。</span><span class="sxs-lookup"><span data-stu-id="35caa-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="35caa-107">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="35caa-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="35caa-108">QUERYASMINFO_FLAG_VALIDATE (0X00000001)</span><span class="sxs-lookup"><span data-stu-id="35caa-108">QUERYASMINFO_FLAG_VALIDATE (0x00000001)</span></span>  
  
-   <span data-ttu-id="35caa-109">QUERYASMINFO_FLAG_GETSIZE (0X00000002)</span><span class="sxs-lookup"><span data-stu-id="35caa-109">QUERYASMINFO_FLAG_GETSIZE (0x00000002)</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="35caa-110">[in]擷取資料的組件名稱。</span><span class="sxs-lookup"><span data-stu-id="35caa-110">[in] The name of the assembly for which data will be retrieved.</span></span>  
  
 `pAsmInfo`  
 <span data-ttu-id="35caa-111">[in、 out][ASSEMBLY_INFO](../../../../docs/framework/unmanaged-api/fusion/assembly-info-structure.md)結構，其中包含有關組件的資料。</span><span class="sxs-lookup"><span data-stu-id="35caa-111">[in, out] An [ASSEMBLY_INFO](../../../../docs/framework/unmanaged-api/fusion/assembly-info-structure.md) structure that contains data about the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35caa-112">需求</span><span class="sxs-lookup"><span data-stu-id="35caa-112">Requirements</span></span>  
 <span data-ttu-id="35caa-113">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="35caa-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35caa-114">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="35caa-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="35caa-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35caa-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35caa-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="35caa-116">See Also</span></span>  
 [<span data-ttu-id="35caa-117">IAssemblyCache 介面</span><span class="sxs-lookup"><span data-stu-id="35caa-117">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
