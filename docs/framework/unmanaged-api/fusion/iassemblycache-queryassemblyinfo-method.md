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
ms.openlocfilehash: 6935a72bb99e636b3732958ee88ad224b401513b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430716"
---
# <a name="iassemblycachequeryassemblyinfo-method"></a><span data-ttu-id="d707a-102">IAssemblyCache::QueryAssemblyInfo 方法</span><span class="sxs-lookup"><span data-stu-id="d707a-102">IAssemblyCache::QueryAssemblyInfo Method</span></span>
<span data-ttu-id="d707a-103">取得指定的組件的相關要求的資料。</span><span class="sxs-lookup"><span data-stu-id="d707a-103">Gets the requested data about the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d707a-104">語法</span><span class="sxs-lookup"><span data-stu-id="d707a-104">Syntax</span></span>  
  
```  
HRESULT QueryAssemblyInfo (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszAssemblyName,  
    [in, out] ASSEMBLY_INFO *pAsmInfo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d707a-105">參數</span><span class="sxs-lookup"><span data-stu-id="d707a-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="d707a-106">[in]支援下列值： 旗標。</span><span class="sxs-lookup"><span data-stu-id="d707a-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="d707a-107">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="d707a-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="d707a-108">QUERYASMINFO_FLAG_VALIDATE (0X00000001)</span><span class="sxs-lookup"><span data-stu-id="d707a-108">QUERYASMINFO_FLAG_VALIDATE (0x00000001)</span></span>  
  
-   <span data-ttu-id="d707a-109">QUERYASMINFO_FLAG_GETSIZE (0X00000002)</span><span class="sxs-lookup"><span data-stu-id="d707a-109">QUERYASMINFO_FLAG_GETSIZE (0x00000002)</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="d707a-110">[in]擷取資料的組件名稱。</span><span class="sxs-lookup"><span data-stu-id="d707a-110">[in] The name of the assembly for which data will be retrieved.</span></span>  
  
 `pAsmInfo`  
 <span data-ttu-id="d707a-111">[in、 out][ASSEMBLY_INFO](../../../../docs/framework/unmanaged-api/fusion/assembly-info-structure.md)結構，其中包含有關組件的資料。</span><span class="sxs-lookup"><span data-stu-id="d707a-111">[in, out] An [ASSEMBLY_INFO](../../../../docs/framework/unmanaged-api/fusion/assembly-info-structure.md) structure that contains data about the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d707a-112">需求</span><span class="sxs-lookup"><span data-stu-id="d707a-112">Requirements</span></span>  
 <span data-ttu-id="d707a-113">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d707a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d707a-114">**標頭：** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="d707a-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="d707a-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d707a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d707a-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d707a-116">See Also</span></span>  
 [<span data-ttu-id="d707a-117">IAssemblyCache 介面</span><span class="sxs-lookup"><span data-stu-id="d707a-117">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
