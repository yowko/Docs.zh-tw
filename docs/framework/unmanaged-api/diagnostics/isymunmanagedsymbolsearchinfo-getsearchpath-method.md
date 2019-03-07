---
title: ISymUnmanagedSymbolSearchInfo::GetSearchPath 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSymbolSearchInfo.GetSearchPath
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo::GetSearchPath
helpviewer_keywords:
- GetSearchPath method [.NET Framework debugging]
- ISymUnmanagedSymbolSearchInfo::GetSearchPath method [.NET Framework debugging]
ms.assetid: b588d470-53c2-4492-be8c-957323eaca0b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 04bf526b4868fc683eac92a84828ae36b02bb3ff
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479523"
---
# <a name="isymunmanagedsymbolsearchinfogetsearchpath-method"></a><span data-ttu-id="83465-102">ISymUnmanagedSymbolSearchInfo::GetSearchPath 方法</span><span class="sxs-lookup"><span data-stu-id="83465-102">ISymUnmanagedSymbolSearchInfo::GetSearchPath Method</span></span>
<span data-ttu-id="83465-103">取得搜尋路徑。</span><span class="sxs-lookup"><span data-stu-id="83465-103">Gets the search path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83465-104">語法</span><span class="sxs-lookup"><span data-stu-id="83465-104">Syntax</span></span>  
  
```  
HRESULT GetSearchPathLength(  
    [out] ULONG32 *pcchPath);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83465-105">參數</span><span class="sxs-lookup"><span data-stu-id="83465-105">Parameters</span></span>  
 `pcchPath`  
 <span data-ttu-id="83465-106">[out]指標`ULONG32`接收大小，以字元為單位，以包含搜尋路徑所需的緩衝區。</span><span class="sxs-lookup"><span data-stu-id="83465-106">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the search path.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="83465-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="83465-107">Return Value</span></span>  
 <span data-ttu-id="83465-108">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="83465-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83465-109">需求</span><span class="sxs-lookup"><span data-stu-id="83465-109">Requirements</span></span>  
 <span data-ttu-id="83465-110">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="83465-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83465-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83465-111">See also</span></span>
- [<span data-ttu-id="83465-112">ISymUnmanagedSymbolSearchInfo 介面</span><span class="sxs-lookup"><span data-stu-id="83465-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)
