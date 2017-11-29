---
title: "ISymENCUnmanagedMethod::GetSourceExtentInDocument 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymENCUnmanagedMethod.GetSourceExtentInDocument
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymENCUnmanagedMethod::GetSourceExtentInDocument
helpviewer_keywords:
- GetSourceExtentInDocument method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetSourceExtentInDocument method [.NET Framework debugging]
ms.assetid: 9c5566ab-4ec7-4b61-9753-839bb90ae78c
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3cff81968926f608de8d28d730a00e79dc8b1c3b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="isymencunmanagedmethodgetsourceextentindocument-method"></a><span data-ttu-id="a3683-102">ISymENCUnmanagedMethod::GetSourceExtentInDocument 方法</span><span class="sxs-lookup"><span data-stu-id="a3683-102">ISymENCUnmanagedMethod::GetSourceExtentInDocument Method</span></span>
<span data-ttu-id="a3683-103">取得最小起始行和最大的結尾行方法特定的文件中。</span><span class="sxs-lookup"><span data-stu-id="a3683-103">Gets the smallest start line and largest end line for the method in a specific document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3683-104">語法</span><span class="sxs-lookup"><span data-stu-id="a3683-104">Syntax</span></span>  
  
```  
HRESULT GetSourceExtentInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [out] ULONG32* pstartLine,  
    [out] ULONG32* pendLine);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a3683-105">參數</span><span class="sxs-lookup"><span data-stu-id="a3683-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="a3683-106">[in]文件指標。</span><span class="sxs-lookup"><span data-stu-id="a3683-106">[in] A pointer to the document.</span></span>  
  
 `pstartLine`  
 <span data-ttu-id="a3683-107">[out]指標`ULONG32`接收之起始行。</span><span class="sxs-lookup"><span data-stu-id="a3683-107">[out] A pointer to a `ULONG32` that receives the start line.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="a3683-108">[out]指標`ULONG32`接收之結尾行。</span><span class="sxs-lookup"><span data-stu-id="a3683-108">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a3683-109">傳回值</span><span class="sxs-lookup"><span data-stu-id="a3683-109">Return Value</span></span>  
 <span data-ttu-id="a3683-110">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="a3683-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3683-111">需求</span><span class="sxs-lookup"><span data-stu-id="a3683-111">Requirements</span></span>  
 <span data-ttu-id="a3683-112">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a3683-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3683-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3683-113">See Also</span></span>  
 [<span data-ttu-id="a3683-114">ISymENCUnmanagedMethod 介面</span><span class="sxs-lookup"><span data-stu-id="a3683-114">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
