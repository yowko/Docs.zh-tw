---
title: "ISymUnmanagedReader::GetUserEntryPoint 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetUserEntryPoint
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetUserEntryPoint
helpviewer_keywords:
- GetUserEntryPoint method [.NET Framework debugging]
- ISymUnmanagedReader::GetUserEntryPoint method [.NET Framework debugging]
ms.assetid: 3fd3a34c-d176-46e9-9996-fb1646cff9b0
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 08a89ba20b48c3d7faa3f3d27d4c57c55b33c355
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreadergetuserentrypoint-method"></a><span data-ttu-id="999c4-102">ISymUnmanagedReader::GetUserEntryPoint 方法</span><span class="sxs-lookup"><span data-stu-id="999c4-102">ISymUnmanagedReader::GetUserEntryPoint Method</span></span>
<span data-ttu-id="999c4-103">傳回指定為模組的使用者進入點方法，如果有的話。</span><span class="sxs-lookup"><span data-stu-id="999c4-103">Returns the method that was specified as the user entry point for the module, if any.</span></span> <span data-ttu-id="999c4-104">例如，使用者的主要方法，而不是編譯器產生的虛設常式的主要方法之前，可能是這個方法。</span><span class="sxs-lookup"><span data-stu-id="999c4-104">For example, this method could be the user's main method rather than compiler-generated stubs before the main method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="999c4-105">語法</span><span class="sxs-lookup"><span data-stu-id="999c4-105">Syntax</span></span>  
  
```  
HRESULT GetUserEntryPoint (  
    [out, retval]  mdMethodDef  *pToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="999c4-106">參數</span><span class="sxs-lookup"><span data-stu-id="999c4-106">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="999c4-107">[out]進入點會接收變數的指標。</span><span class="sxs-lookup"><span data-stu-id="999c4-107">[out] A pointer to a variable that receives the entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="999c4-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="999c4-108">Return Value</span></span>  
 <span data-ttu-id="999c4-109">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="999c4-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="999c4-110">需求</span><span class="sxs-lookup"><span data-stu-id="999c4-110">Requirements</span></span>  
 <span data-ttu-id="999c4-111">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="999c4-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="999c4-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="999c4-112">See Also</span></span>  
 [<span data-ttu-id="999c4-113">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="999c4-113">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
