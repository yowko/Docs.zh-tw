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
ms.openlocfilehash: e975db68252e866a0bf7898f1c9d3cbe67bbe24f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134585"
---
# <a name="iassemblycachequeryassemblyinfo-method"></a><span data-ttu-id="0068a-102">IAssemblyCache::QueryAssemblyInfo 方法</span><span class="sxs-lookup"><span data-stu-id="0068a-102">IAssemblyCache::QueryAssemblyInfo Method</span></span>
<span data-ttu-id="0068a-103">取得指定元件的要求資料。</span><span class="sxs-lookup"><span data-stu-id="0068a-103">Gets the requested data about the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0068a-104">語法</span><span class="sxs-lookup"><span data-stu-id="0068a-104">Syntax</span></span>  
  
```cpp  
HRESULT QueryAssemblyInfo (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszAssemblyName,  
    [in, out] ASSEMBLY_INFO *pAsmInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0068a-105">參數</span><span class="sxs-lookup"><span data-stu-id="0068a-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="0068a-106">在在融合 .idl 中定義的旗標。</span><span class="sxs-lookup"><span data-stu-id="0068a-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="0068a-107">支援下列值：</span><span class="sxs-lookup"><span data-stu-id="0068a-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="0068a-108">QUERYASMINFO_FLAG_VALIDATE （0x00000001）</span><span class="sxs-lookup"><span data-stu-id="0068a-108">QUERYASMINFO_FLAG_VALIDATE (0x00000001)</span></span>  
  
- <span data-ttu-id="0068a-109">QUERYASMINFO_FLAG_GETSIZE （0x00000002）</span><span class="sxs-lookup"><span data-stu-id="0068a-109">QUERYASMINFO_FLAG_GETSIZE (0x00000002)</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="0068a-110">在將抓取資料之元件的名稱。</span><span class="sxs-lookup"><span data-stu-id="0068a-110">[in] The name of the assembly for which data will be retrieved.</span></span>  
  
 `pAsmInfo`  
 <span data-ttu-id="0068a-111">[in、out]包含元件相關資料的[ASSEMBLY_INFO](assembly-info-structure.md)結構。</span><span class="sxs-lookup"><span data-stu-id="0068a-111">[in, out] An [ASSEMBLY_INFO](assembly-info-structure.md) structure that contains data about the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0068a-112">需求</span><span class="sxs-lookup"><span data-stu-id="0068a-112">Requirements</span></span>  
 <span data-ttu-id="0068a-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0068a-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0068a-114">**標頭：** 融合。h</span><span class="sxs-lookup"><span data-stu-id="0068a-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="0068a-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0068a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0068a-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="0068a-116">See also</span></span>

- [<span data-ttu-id="0068a-117">IAssemblyCache 介面</span><span class="sxs-lookup"><span data-stu-id="0068a-117">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
