---
title: ISymUnmanagedReader::GetMethod 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethod
helpviewer_keywords:
- GetMethod method, ISymUnmanagedReader interface [.NET Framework debugging]
- ISymUnmanagedReader::GetMethod method [.NET Framework debugging]
ms.assetid: ae6cfb29-bc2c-4606-af86-1d32ebd31020
topic_type:
- apiref
ms.openlocfilehash: 3f0d0e060bba832080dd8fbfab62f3115fec0aab
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689637"
---
# <a name="isymunmanagedreadergetmethod-method"></a><span data-ttu-id="ee171-102">ISymUnmanagedReader::GetMethod 方法</span><span class="sxs-lookup"><span data-stu-id="ee171-102">ISymUnmanagedReader::GetMethod Method</span></span>

<span data-ttu-id="ee171-103">取得符號讀取器方法（指定方法標記）。</span><span class="sxs-lookup"><span data-stu-id="ee171-103">Gets a symbol reader method, given a method token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee171-104">語法</span><span class="sxs-lookup"><span data-stu-id="ee171-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethod (  
    [in]  mdMethodDef  token,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ee171-105">參數</span><span class="sxs-lookup"><span data-stu-id="ee171-105">Parameters</span></span>  

 `token`  
 <span data-ttu-id="ee171-106">在方法標記。</span><span class="sxs-lookup"><span data-stu-id="ee171-106">[in] The method token.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="ee171-107">擴展傳回之介面的指標。</span><span class="sxs-lookup"><span data-stu-id="ee171-107">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ee171-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="ee171-108">Return Value</span></span>  

 <span data-ttu-id="ee171-109">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="ee171-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee171-110">需求</span><span class="sxs-lookup"><span data-stu-id="ee171-110">Requirements</span></span>  

 <span data-ttu-id="ee171-111">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="ee171-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee171-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee171-112">See also</span></span>

- [<span data-ttu-id="ee171-113">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="ee171-113">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
