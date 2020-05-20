---
title: ISymUnmanagedWriter4::GetDebugInfoWithPadding 方法
ms.date: 03/30/2017
ms.assetid: 881e20ca-8131-4bd0-ba41-c2d6391b0fe2
ms.openlocfilehash: cfc6c22558cee780823c8cca0c36b883147e9496
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614639"
---
# <a name="isymunmanagedwriter4getdebuginfowithpadding-method"></a><span data-ttu-id="3f179-102">ISymUnmanagedWriter4::GetDebugInfoWithPadding 方法</span><span class="sxs-lookup"><span data-stu-id="3f179-102">ISymUnmanagedWriter4::GetDebugInfoWithPadding Method</span></span>
<span data-ttu-id="3f179-103">函式與[GetDebugInfo 方法](isymunmanagedwriter-getdebuginfo-method.md)相同，不同之處在于路徑字串會在結束的 null 字元之後以零填補，使字串資料成為固定大小 `MAX_PATH` 。</span><span class="sxs-lookup"><span data-stu-id="3f179-103">Functions the same as [GetDebugInfo Method](isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="3f179-104">只有在路徑字串長度本身小於時，才會提供填補 `MAX_PATH` 。</span><span class="sxs-lookup"><span data-stu-id="3f179-104">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span>  
  
 <span data-ttu-id="3f179-105">這可讓您更輕鬆地撰寫與 PE 檔案不同的工具。</span><span class="sxs-lookup"><span data-stu-id="3f179-105">This makes it easier to write tools that difference PE files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f179-106">語法</span><span class="sxs-lookup"><span data-stu-id="3f179-106">Syntax</span></span>  
  
```idl  
HRESULT GetDebugInfoWithPadding(    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,    [in] DWORD cData,    [out] DWORD *pcData,    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f179-107">參數</span><span class="sxs-lookup"><span data-stu-id="3f179-107">Parameters</span></span>  
  
|<span data-ttu-id="3f179-108">參數</span><span class="sxs-lookup"><span data-stu-id="3f179-108">Parameter</span></span>|<span data-ttu-id="3f179-109">說明</span><span class="sxs-lookup"><span data-stu-id="3f179-109">Description</span></span>|  
|---------------|-----------------|  
|`pIDD`||  
|`cData`||  
|`pcData`||  
|`data`||  
  
## <a name="return-value"></a><span data-ttu-id="3f179-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="3f179-110">Return Value</span></span>  
 <span data-ttu-id="3f179-111">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="3f179-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f179-112">需求</span><span class="sxs-lookup"><span data-stu-id="3f179-112">Requirements</span></span>  
 <span data-ttu-id="3f179-113">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="3f179-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f179-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f179-114">See also</span></span>

- [<span data-ttu-id="3f179-115">ISymUnmanagedWriter4 介面</span><span class="sxs-lookup"><span data-stu-id="3f179-115">ISymUnmanagedWriter4 Interface</span></span>](isymunmanagedwriter4-interface.md)
