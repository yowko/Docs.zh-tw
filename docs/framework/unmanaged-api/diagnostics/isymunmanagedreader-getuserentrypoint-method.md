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
ms.openlocfilehash: d465f830fa73016c3cf3f7df3a4a4d0c42bc0980
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615497"
---
# <a name="isymunmanagedreadergetuserentrypoint-method"></a><span data-ttu-id="fbb6f-102">ISymUnmanagedReader::GetUserEntryPoint 方法</span><span class="sxs-lookup"><span data-stu-id="fbb6f-102">ISymUnmanagedReader::GetUserEntryPoint Method</span></span>
<span data-ttu-id="fbb6f-103">傳回指定為模組之使用者進入點的方法（如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="fbb6f-103">Returns the method that was specified as the user entry point for the module, if any.</span></span> <span data-ttu-id="fbb6f-104">例如，這個方法可以是使用者的 main 方法，而不是編譯器在 main 方法之前產生的存根。</span><span class="sxs-lookup"><span data-stu-id="fbb6f-104">For example, this method could be the user's main method rather than compiler-generated stubs before the main method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbb6f-105">語法</span><span class="sxs-lookup"><span data-stu-id="fbb6f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetUserEntryPoint (  
    [out, retval]  mdMethodDef  *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fbb6f-106">參數</span><span class="sxs-lookup"><span data-stu-id="fbb6f-106">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="fbb6f-107">脫銷接收進入點之變數的指標。</span><span class="sxs-lookup"><span data-stu-id="fbb6f-107">[out] A pointer to a variable that receives the entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fbb6f-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="fbb6f-108">Return Value</span></span>  
 <span data-ttu-id="fbb6f-109">如果方法成功，則 S_OK;否則，E_FAIL 或一些其他錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="fbb6f-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbb6f-110">需求</span><span class="sxs-lookup"><span data-stu-id="fbb6f-110">Requirements</span></span>  
 <span data-ttu-id="fbb6f-111">**標頭：** CorSym .idl，CorSym。h</span><span class="sxs-lookup"><span data-stu-id="fbb6f-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbb6f-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fbb6f-112">See also</span></span>

- [<span data-ttu-id="fbb6f-113">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="fbb6f-113">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
