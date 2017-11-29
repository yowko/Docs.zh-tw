---
title: "ISymUnmanagedSymbolSearchInfo::GetHRESULT 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedSymbolSearchInfo.GetHRESULT
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedSymbolSearchInfo::GetHRESULT
helpviewer_keywords:
- ISymUnmanagedSymbolSearchInfo::GetHRESULT method [.NET Framework debugging]
- GetHRESULT method [.NET Framework debugging]
ms.assetid: 6999dc3d-65d7-4bf6-bb0a-6efc0fc72588
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 42f2e0053a83d4ef7414791626ec204671429a3f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedsymbolsearchinfogethresult-method"></a><span data-ttu-id="b66fa-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT 方法</span><span class="sxs-lookup"><span data-stu-id="b66fa-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT Method</span></span>
<span data-ttu-id="b66fa-103">取得 HRESULT。</span><span class="sxs-lookup"><span data-stu-id="b66fa-103">Gets the HRESULT.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b66fa-104">語法</span><span class="sxs-lookup"><span data-stu-id="b66fa-104">Syntax</span></span>  
  
```  
HRESULT GetHRESULT(  
    [out] HRESULT *phr);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b66fa-105">參數</span><span class="sxs-lookup"><span data-stu-id="b66fa-105">Parameters</span></span>  
 `phr`  
 <span data-ttu-id="b66fa-106">[out]HRESULT 指標。</span><span class="sxs-lookup"><span data-stu-id="b66fa-106">[out] A pointer to the HRESULT.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b66fa-107">傳回值</span><span class="sxs-lookup"><span data-stu-id="b66fa-107">Return Value</span></span>  
 <span data-ttu-id="b66fa-108">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="b66fa-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b66fa-109">需求</span><span class="sxs-lookup"><span data-stu-id="b66fa-109">Requirements</span></span>  
 <span data-ttu-id="b66fa-110">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b66fa-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b66fa-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b66fa-111">See Also</span></span>  
 [<span data-ttu-id="b66fa-112">ISymUnmanagedSymbolSearchInfo 介面</span><span class="sxs-lookup"><span data-stu-id="b66fa-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)
