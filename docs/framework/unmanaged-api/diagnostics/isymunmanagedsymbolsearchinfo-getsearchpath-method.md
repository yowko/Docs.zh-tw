---
title: "ISymUnmanagedSymbolSearchInfo::GetSearchPath 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedSymbolSearchInfo.GetSearchPath
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedSymbolSearchInfo::GetSearchPath
helpviewer_keywords:
- GetSearchPath method [.NET Framework debugging]
- ISymUnmanagedSymbolSearchInfo::GetSearchPath method [.NET Framework debugging]
ms.assetid: b588d470-53c2-4492-be8c-957323eaca0b
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d1c4e1873aa3441e0348751717443e8189a67e61
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedsymbolsearchinfogetsearchpath-method"></a><span data-ttu-id="fcef5-102">ISymUnmanagedSymbolSearchInfo::GetSearchPath 方法</span><span class="sxs-lookup"><span data-stu-id="fcef5-102">ISymUnmanagedSymbolSearchInfo::GetSearchPath Method</span></span>
<span data-ttu-id="fcef5-103">取得搜尋路徑。</span><span class="sxs-lookup"><span data-stu-id="fcef5-103">Gets the search path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcef5-104">語法</span><span class="sxs-lookup"><span data-stu-id="fcef5-104">Syntax</span></span>  
  
```  
HRESULT GetSearchPathLength(  
    [out] ULONG32 *pcchPath);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fcef5-105">參數</span><span class="sxs-lookup"><span data-stu-id="fcef5-105">Parameters</span></span>  
 `pcchPath`  
 <span data-ttu-id="fcef5-106">[out]指標`ULONG32`接收以字元為單位，才能包含搜尋路徑之緩衝區的大小。</span><span class="sxs-lookup"><span data-stu-id="fcef5-106">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the search path.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fcef5-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="fcef5-107">Return Value</span></span>  
 <span data-ttu-id="fcef5-108">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="fcef5-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcef5-109">需求</span><span class="sxs-lookup"><span data-stu-id="fcef5-109">Requirements</span></span>  
 <span data-ttu-id="fcef5-110">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="fcef5-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcef5-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="fcef5-111">See Also</span></span>  
 [<span data-ttu-id="fcef5-112">ISymUnmanagedSymbolSearchInfo 介面</span><span class="sxs-lookup"><span data-stu-id="fcef5-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)
