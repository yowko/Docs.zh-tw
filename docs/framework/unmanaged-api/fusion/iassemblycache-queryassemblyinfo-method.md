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
ms.openlocfilehash: f764be9b80a8d4dcb15791d406412ece9e7e7c87
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95670923"
---
# <a name="iassemblycachequeryassemblyinfo-method"></a><span data-ttu-id="58b9b-102">IAssemblyCache::QueryAssemblyInfo 方法</span><span class="sxs-lookup"><span data-stu-id="58b9b-102">IAssemblyCache::QueryAssemblyInfo Method</span></span>

<span data-ttu-id="58b9b-103">取得所要求有關指定元件的資料。</span><span class="sxs-lookup"><span data-stu-id="58b9b-103">Gets the requested data about the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58b9b-104">語法</span><span class="sxs-lookup"><span data-stu-id="58b9b-104">Syntax</span></span>  
  
```cpp  
HRESULT QueryAssemblyInfo (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszAssemblyName,  
    [in, out] ASSEMBLY_INFO *pAsmInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="58b9b-105">參數</span><span class="sxs-lookup"><span data-stu-id="58b9b-105">Parameters</span></span>  

 `dwFlags`  
 <span data-ttu-id="58b9b-106">在在融合 .idl 中定義的旗標。</span><span class="sxs-lookup"><span data-stu-id="58b9b-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="58b9b-107">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="58b9b-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="58b9b-108">QUERYASMINFO_FLAG_VALIDATE (0x00000001) </span><span class="sxs-lookup"><span data-stu-id="58b9b-108">QUERYASMINFO_FLAG_VALIDATE (0x00000001)</span></span>  
  
- <span data-ttu-id="58b9b-109">QUERYASMINFO_FLAG_GETSIZE (0x00000002) </span><span class="sxs-lookup"><span data-stu-id="58b9b-109">QUERYASMINFO_FLAG_GETSIZE (0x00000002)</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="58b9b-110">在將取出資料的元件名稱。</span><span class="sxs-lookup"><span data-stu-id="58b9b-110">[in] The name of the assembly for which data will be retrieved.</span></span>  
  
 `pAsmInfo`  
 <span data-ttu-id="58b9b-111">[in，out]包含元件相關資料的 [ASSEMBLY_INFO](assembly-info-structure.md) 結構。</span><span class="sxs-lookup"><span data-stu-id="58b9b-111">[in, out] An [ASSEMBLY_INFO](assembly-info-structure.md) structure that contains data about the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58b9b-112">需求</span><span class="sxs-lookup"><span data-stu-id="58b9b-112">Requirements</span></span>  

 <span data-ttu-id="58b9b-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="58b9b-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58b9b-114">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="58b9b-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="58b9b-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58b9b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58b9b-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="58b9b-116">See also</span></span>

- [<span data-ttu-id="58b9b-117">IAssemblyCache 介面</span><span class="sxs-lookup"><span data-stu-id="58b9b-117">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
