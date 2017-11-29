---
title: "ISymUnmanagedWriter4::GetDebugInfoWithPadding 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 881e20ca-8131-4bd0-ba41-c2d6391b0fe2
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d9f2f0aad37fcd63e2345cd32a00b44412ed8c7a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriter4getdebuginfowithpadding-method"></a><span data-ttu-id="c5888-102">ISymUnmanagedWriter4::GetDebugInfoWithPadding 方法</span><span class="sxs-lookup"><span data-stu-id="c5888-102">ISymUnmanagedWriter4::GetDebugInfoWithPadding Method</span></span>
<span data-ttu-id="c5888-103">函式與相同[GetDebugInfo 方法](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md)不同之處在於路徑字串以下列結束的 null 字元的固定的大小，讓字串資料的零填補`MAX_PATH`。</span><span class="sxs-lookup"><span data-stu-id="c5888-103">Functions the same as [GetDebugInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="c5888-104">如果路徑字串長度本身是填補只取得小於`MAX_PATH`。</span><span class="sxs-lookup"><span data-stu-id="c5888-104">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span>  
  
 <span data-ttu-id="c5888-105">這可讓您更輕鬆地撰寫工具類型的差異 PE 檔案。</span><span class="sxs-lookup"><span data-stu-id="c5888-105">This makes it easier to write tools that difference PE files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5888-106">語法</span><span class="sxs-lookup"><span data-stu-id="c5888-106">Syntax</span></span>  
  
```idl  
HRESULT GetDebugInfoWithPadding(    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,    [in] DWORD cData,    [out] DWORD *pcData,    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c5888-107">參數</span><span class="sxs-lookup"><span data-stu-id="c5888-107">Parameters</span></span>  
  
|<span data-ttu-id="c5888-108">參數</span><span class="sxs-lookup"><span data-stu-id="c5888-108">Parameter</span></span>|<span data-ttu-id="c5888-109">說明</span><span class="sxs-lookup"><span data-stu-id="c5888-109">Description</span></span>|  
|---------------|-----------------|  
|`pIDD`||  
|`cData`||  
|`pcData`||  
|`data`||  
  
## <a name="return-value"></a><span data-ttu-id="c5888-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="c5888-110">Return Value</span></span>  
 <span data-ttu-id="c5888-111">傳回 `HRESULT`。</span><span class="sxs-lookup"><span data-stu-id="c5888-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5888-112">需求</span><span class="sxs-lookup"><span data-stu-id="c5888-112">Requirements</span></span>  
 <span data-ttu-id="c5888-113">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c5888-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5888-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5888-114">See Also</span></span>  
 [<span data-ttu-id="c5888-115">ISymUnmanagedWriter4 介面</span><span class="sxs-lookup"><span data-stu-id="c5888-115">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
