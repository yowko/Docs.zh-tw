---
title: ISymUnmanagedDocument::FindClosestLine 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.FindClosestLine
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::FindClosestLine
helpviewer_keywords:
- FindClosestLine method [.NET Framework debugging]
- ISymUnmanagedDocument::FindClosestLine method [.NET Framework debugging]
ms.assetid: 628f2a04-e529-407d-841e-3b3da219a9cb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8d6be64137b59c84dfadbd7f0e4895eac2fb27e4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776794"
---
# <a name="isymunmanageddocumentfindclosestline-method"></a><span data-ttu-id="81b32-102">ISymUnmanagedDocument::FindClosestLine 方法</span><span class="sxs-lookup"><span data-stu-id="81b32-102">ISymUnmanagedDocument::FindClosestLine Method</span></span>
<span data-ttu-id="81b32-103">在此可能會或可能不是序列點的文件中會傳回是序列點，最接近的一行。</span><span class="sxs-lookup"><span data-stu-id="81b32-103">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81b32-104">語法</span><span class="sxs-lookup"><span data-stu-id="81b32-104">Syntax</span></span>  
  
```cpp  
HRESULT FindClosestLine(  
    [in]  ULONG32  line,  
    [out, retval] ULONG32*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81b32-105">參數</span><span class="sxs-lookup"><span data-stu-id="81b32-105">Parameters</span></span>  
 `line`  
 <span data-ttu-id="81b32-106">[in]這份文件中的資料行。</span><span class="sxs-lookup"><span data-stu-id="81b32-106">[in] A line in this document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="81b32-107">[out]此變數會接收列指標。</span><span class="sxs-lookup"><span data-stu-id="81b32-107">[out] A pointer to a variable that receives the line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="81b32-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="81b32-108">Return Value</span></span>  
 <span data-ttu-id="81b32-109">如果方法成功，則為 S_OK否則，出現錯誤代碼。</span><span class="sxs-lookup"><span data-stu-id="81b32-109">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81b32-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81b32-110">See also</span></span>

- [<span data-ttu-id="81b32-111">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="81b32-111">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
