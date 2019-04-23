---
title: IAssemblyCache::QueryAssemblyInfo 方法
ms.date: 03/30/2017
api_name:
- IAssemblyCache.QueryAssemblyInfo
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache::QueryAssemblyInfo
helpviewer_keywords:
- IAssemblyCache::QueryAssemblyInfo method [.NET Framework fusion]
- QueryAssemblyInfo method [.NET Framework fusion]
ms.assetid: 09313cb5-06f6-43bd-94f4-1055c6b0c99a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 81b647032b2e9474e3b4472552ed884cec92ffc3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59216407"
---
# <a name="iassemblycachequeryassemblyinfo-method"></a><span data-ttu-id="0af82-102">IAssemblyCache::QueryAssemblyInfo 方法</span><span class="sxs-lookup"><span data-stu-id="0af82-102">IAssemblyCache::QueryAssemblyInfo Method</span></span>
<span data-ttu-id="0af82-103">取得指定的組件的相關要求的資料。</span><span class="sxs-lookup"><span data-stu-id="0af82-103">Gets the requested data about the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0af82-104">語法</span><span class="sxs-lookup"><span data-stu-id="0af82-104">Syntax</span></span>  
  
```  
HRESULT QueryAssemblyInfo (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszAssemblyName,  
    [in, out] ASSEMBLY_INFO *pAsmInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0af82-105">參數</span><span class="sxs-lookup"><span data-stu-id="0af82-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="0af82-106">[in]支援下列值： 旗標。</span><span class="sxs-lookup"><span data-stu-id="0af82-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="0af82-107">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="0af82-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="0af82-108">QUERYASMINFO_FLAG_VALIDATE (0x00000001)</span><span class="sxs-lookup"><span data-stu-id="0af82-108">QUERYASMINFO_FLAG_VALIDATE (0x00000001)</span></span>  
  
-   <span data-ttu-id="0af82-109">QUERYASMINFO_FLAG_GETSIZE (0x00000002)</span><span class="sxs-lookup"><span data-stu-id="0af82-109">QUERYASMINFO_FLAG_GETSIZE (0x00000002)</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="0af82-110">[in]將擷取資料的組件名稱。</span><span class="sxs-lookup"><span data-stu-id="0af82-110">[in] The name of the assembly for which data will be retrieved.</span></span>  
  
 `pAsmInfo`  
 <span data-ttu-id="0af82-111">[in、 out][ASSEMBLY_INFO](../../../../docs/framework/unmanaged-api/fusion/assembly-info-structure.md)包含組件的相關資料結構。</span><span class="sxs-lookup"><span data-stu-id="0af82-111">[in, out] An [ASSEMBLY_INFO](../../../../docs/framework/unmanaged-api/fusion/assembly-info-structure.md) structure that contains data about the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0af82-112">需求</span><span class="sxs-lookup"><span data-stu-id="0af82-112">Requirements</span></span>  
 <span data-ttu-id="0af82-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0af82-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0af82-114">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="0af82-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="0af82-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0af82-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0af82-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0af82-116">See also</span></span>

- [<span data-ttu-id="0af82-117">IAssemblyCache 介面</span><span class="sxs-lookup"><span data-stu-id="0af82-117">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
