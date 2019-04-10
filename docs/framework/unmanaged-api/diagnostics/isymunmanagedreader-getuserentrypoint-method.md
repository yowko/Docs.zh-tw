---
title: ISymUnmanagedReader::GetUserEntryPoint 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetUserEntryPoint
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetUserEntryPoint
helpviewer_keywords:
- GetUserEntryPoint method [.NET Framework debugging]
- ISymUnmanagedReader::GetUserEntryPoint method [.NET Framework debugging]
ms.assetid: 3fd3a34c-d176-46e9-9996-fb1646cff9b0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0267ae8b57c837b097d496c8e119085d03417e36
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211266"
---
# <a name="isymunmanagedreadergetuserentrypoint-method"></a><span data-ttu-id="ba5f0-102">ISymUnmanagedReader::GetUserEntryPoint 方法</span><span class="sxs-lookup"><span data-stu-id="ba5f0-102">ISymUnmanagedReader::GetUserEntryPoint Method</span></span>
<span data-ttu-id="ba5f0-103">如果有的話，會傳回已指定為模組的使用者進入點方法。</span><span class="sxs-lookup"><span data-stu-id="ba5f0-103">Returns the method that was specified as the user entry point for the module, if any.</span></span> <span data-ttu-id="ba5f0-104">比方說，這個方法可能是使用者的主要方法，而不是編譯器所產生的虛設常式之前的主要方法。</span><span class="sxs-lookup"><span data-stu-id="ba5f0-104">For example, this method could be the user's main method rather than compiler-generated stubs before the main method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba5f0-105">語法</span><span class="sxs-lookup"><span data-stu-id="ba5f0-105">Syntax</span></span>  
  
```  
HRESULT GetUserEntryPoint (  
    [out, retval]  mdMethodDef  *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba5f0-106">參數</span><span class="sxs-lookup"><span data-stu-id="ba5f0-106">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="ba5f0-107">[out]接收的進入點的變數指標。</span><span class="sxs-lookup"><span data-stu-id="ba5f0-107">[out] A pointer to a variable that receives the entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ba5f0-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="ba5f0-108">Return Value</span></span>  
 <span data-ttu-id="ba5f0-109">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="ba5f0-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba5f0-110">需求</span><span class="sxs-lookup"><span data-stu-id="ba5f0-110">Requirements</span></span>  
 <span data-ttu-id="ba5f0-111">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ba5f0-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba5f0-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ba5f0-112">See also</span></span>

- [<span data-ttu-id="ba5f0-113">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="ba5f0-113">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
