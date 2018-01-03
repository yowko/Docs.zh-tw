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
ms.workload: dotnet
ms.openlocfilehash: 328f44e797a49a899545fa43d940a3b0399ee8c1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreadergetuserentrypoint-method"></a><span data-ttu-id="3d1a7-102">ISymUnmanagedReader::GetUserEntryPoint 方法</span><span class="sxs-lookup"><span data-stu-id="3d1a7-102">ISymUnmanagedReader::GetUserEntryPoint Method</span></span>
<span data-ttu-id="3d1a7-103">傳回指定為模組的使用者進入點方法，如果有的話。</span><span class="sxs-lookup"><span data-stu-id="3d1a7-103">Returns the method that was specified as the user entry point for the module, if any.</span></span> <span data-ttu-id="3d1a7-104">例如，使用者的主要方法，而不是編譯器產生的虛設常式的主要方法之前，可能是這個方法。</span><span class="sxs-lookup"><span data-stu-id="3d1a7-104">For example, this method could be the user's main method rather than compiler-generated stubs before the main method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d1a7-105">語法</span><span class="sxs-lookup"><span data-stu-id="3d1a7-105">Syntax</span></span>  
  
```  
HRESULT GetUserEntryPoint (  
    [out, retval]  mdMethodDef  *pToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3d1a7-106">參數</span><span class="sxs-lookup"><span data-stu-id="3d1a7-106">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="3d1a7-107">[out]進入點會接收變數的指標。</span><span class="sxs-lookup"><span data-stu-id="3d1a7-107">[out] A pointer to a variable that receives the entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3d1a7-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="3d1a7-108">Return Value</span></span>  
 <span data-ttu-id="3d1a7-109">如果方法成功則為 S_OK否則，E_FAIL 或其他錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="3d1a7-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d1a7-110">需求</span><span class="sxs-lookup"><span data-stu-id="3d1a7-110">Requirements</span></span>  
 <span data-ttu-id="3d1a7-111">**標頭：**於 CorSym.idl、 CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3d1a7-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d1a7-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="3d1a7-112">See Also</span></span>  
 [<span data-ttu-id="3d1a7-113">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="3d1a7-113">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
