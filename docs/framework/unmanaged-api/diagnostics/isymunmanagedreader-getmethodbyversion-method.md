---
title: ISymUnmanagedReader::GetMethodByVersion 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodByVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodByVersion
helpviewer_keywords:
- ISymUnmanagedReader::GetMethodByVersion method [.NET Framework debugging]
- GetMethodByVersion method [.NET Framework debugging]
ms.assetid: 6ddb0631-4569-41b3-93e4-50fdfaa486dc
topic_type:
- apiref
ms.openlocfilehash: 64e6b9a1942e9a69e43de3d2f09564814328ec08
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689611"
---
# <a name="isymunmanagedreadergetmethodbyversion-method"></a><span data-ttu-id="91d6a-102">ISymUnmanagedReader::GetMethodByVersion 方法</span><span class="sxs-lookup"><span data-stu-id="91d6a-102">ISymUnmanagedReader::GetMethodByVersion Method</span></span>

<span data-ttu-id="91d6a-103">取得符號讀取器方法，指定方法 token 和編輯和複製版本號碼。</span><span class="sxs-lookup"><span data-stu-id="91d6a-103">Gets a symbol reader method, given a method token and an edit-and-copy version number.</span></span> <span data-ttu-id="91d6a-104">版本號碼從1開始，並在每次方法因為編輯和複製作業的結果而變更時遞增。</span><span class="sxs-lookup"><span data-stu-id="91d6a-104">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-copy operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91d6a-105">語法</span><span class="sxs-lookup"><span data-stu-id="91d6a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodByVersion (  
    [in]  mdMethodDef  token,  
    [in]  int  version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91d6a-106">參數</span><span class="sxs-lookup"><span data-stu-id="91d6a-106">Parameters</span></span>  

 `token`  
 <span data-ttu-id="91d6a-107">在方法標記。</span><span class="sxs-lookup"><span data-stu-id="91d6a-107">[in] The method token.</span></span>  
  
 `version`  
 <span data-ttu-id="91d6a-108">在方法版本。</span><span class="sxs-lookup"><span data-stu-id="91d6a-108">[in] The method version.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="91d6a-109">擴展傳回之介面的指標。</span><span class="sxs-lookup"><span data-stu-id="91d6a-109">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="91d6a-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="91d6a-110">Return Value</span></span>  

 <span data-ttu-id="91d6a-111">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="91d6a-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91d6a-112">需求</span><span class="sxs-lookup"><span data-stu-id="91d6a-112">Requirements</span></span>  

 <span data-ttu-id="91d6a-113">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="91d6a-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91d6a-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91d6a-114">See also</span></span>

- [<span data-ttu-id="91d6a-115">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="91d6a-115">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
