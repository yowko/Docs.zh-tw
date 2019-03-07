---
title: ISymUnmanagedWriter::SetUserEntryPoint 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetUserEntryPoint
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetUserEntryPoint
helpviewer_keywords:
- ISymUnmanagedWriter::SetUserEntryPoint method [.NET Framework debugging]
- SetUserEntryPoint method [.NET Framework debugging]
ms.assetid: d4dcc575-3ac8-4453-9be1-2b24f47363d7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3bd3d411ad6fe7f65d1eeb25754794704752009e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57488353"
---
# <a name="isymunmanagedwritersetuserentrypoint-method"></a><span data-ttu-id="759fc-102">ISymUnmanagedWriter::SetUserEntryPoint 方法</span><span class="sxs-lookup"><span data-stu-id="759fc-102">ISymUnmanagedWriter::SetUserEntryPoint Method</span></span>
<span data-ttu-id="759fc-103">指定的使用者定義的方法，此模組的進入點。</span><span class="sxs-lookup"><span data-stu-id="759fc-103">Specifies the user-defined method that is the entry point for this module.</span></span> <span data-ttu-id="759fc-104">例如，此進入點可能是使用者的主要方法，而不是在 main 之前編譯器所產生的虛設常式。</span><span class="sxs-lookup"><span data-stu-id="759fc-104">For example, this entry point could be the user's main method instead of compiler-generated stubs before main.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="759fc-105">語法</span><span class="sxs-lookup"><span data-stu-id="759fc-105">Syntax</span></span>  
  
```  
HRESULT SetUserEntryPoint(  
    [in] mdMethodDef entryMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="759fc-106">參數</span><span class="sxs-lookup"><span data-stu-id="759fc-106">Parameters</span></span>  
 `entryMethod`  
 <span data-ttu-id="759fc-107">[in]是使用者的項目方法的中繼資料語彙基元點。</span><span class="sxs-lookup"><span data-stu-id="759fc-107">[in] The metadata token for the method that is the user entry point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="759fc-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="759fc-108">Return Value</span></span>  
 <span data-ttu-id="759fc-109">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="759fc-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="759fc-110">需求</span><span class="sxs-lookup"><span data-stu-id="759fc-110">Requirements</span></span>  
 <span data-ttu-id="759fc-111">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="759fc-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="759fc-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="759fc-112">See also</span></span>
- [<span data-ttu-id="759fc-113">ISymUnmanagedWriter 介面</span><span class="sxs-lookup"><span data-stu-id="759fc-113">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
