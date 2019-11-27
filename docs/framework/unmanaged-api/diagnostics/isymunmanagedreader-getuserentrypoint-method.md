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
ms.openlocfilehash: 50f41bb55b7c3dc45646a465032074ce90be0abf
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444515"
---
# <a name="isymunmanagedreadergetuserentrypoint-method"></a><span data-ttu-id="2b21f-102">ISymUnmanagedReader::GetUserEntryPoint 方法</span><span class="sxs-lookup"><span data-stu-id="2b21f-102">ISymUnmanagedReader::GetUserEntryPoint Method</span></span>
<span data-ttu-id="2b21f-103">傳回指定為模組之使用者進入點的方法（如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="2b21f-103">Returns the method that was specified as the user entry point for the module, if any.</span></span> <span data-ttu-id="2b21f-104">例如，這個方法可以是使用者的 main 方法，而不是編譯器在 main 方法之前產生的存根。</span><span class="sxs-lookup"><span data-stu-id="2b21f-104">For example, this method could be the user's main method rather than compiler-generated stubs before the main method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b21f-105">語法</span><span class="sxs-lookup"><span data-stu-id="2b21f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetUserEntryPoint (  
    [out, retval]  mdMethodDef  *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2b21f-106">參數</span><span class="sxs-lookup"><span data-stu-id="2b21f-106">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="2b21f-107">脫銷接收進入點之變數的指標。</span><span class="sxs-lookup"><span data-stu-id="2b21f-107">[out] A pointer to a variable that receives the entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2b21f-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="2b21f-108">Return Value</span></span>  
 <span data-ttu-id="2b21f-109">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="2b21f-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b21f-110">需求</span><span class="sxs-lookup"><span data-stu-id="2b21f-110">Requirements</span></span>  
 <span data-ttu-id="2b21f-111">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="2b21f-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b21f-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b21f-112">See also</span></span>

- [<span data-ttu-id="2b21f-113">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="2b21f-113">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
