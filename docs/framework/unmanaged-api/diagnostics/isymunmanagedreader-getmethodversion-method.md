---
title: ISymUnmanagedReader::GetMethodVersion 方法
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodVersion
helpviewer_keywords:
- GetMethodVersion method [.NET Framework debugging]
- ISymUnmanagedReader::GetMethodVersion method [.NET Framework debugging]
ms.assetid: d6f9ac84-302a-4f5e-b990-e76f4269fceb
topic_type:
- apiref
ms.openlocfilehash: b0590f93c6a4c5ef28e03fc909c1f6a1474e5fad
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720603"
---
# <a name="isymunmanagedreadergetmethodversion-method"></a><span data-ttu-id="0592c-102">ISymUnmanagedReader::GetMethodVersion 方法</span><span class="sxs-lookup"><span data-stu-id="0592c-102">ISymUnmanagedReader::GetMethodVersion Method</span></span>

<span data-ttu-id="0592c-103">取得方法版本。</span><span class="sxs-lookup"><span data-stu-id="0592c-103">Gets the method version.</span></span> <span data-ttu-id="0592c-104">方法版本從1開始，並在每次重新編譯方法時遞增。</span><span class="sxs-lookup"><span data-stu-id="0592c-104">The method version starts at 1 and is incremented each time the method is recompiled.</span></span> <span data-ttu-id="0592c-105">重新編譯可能會發生，而不需要變更方法。</span><span class="sxs-lookup"><span data-stu-id="0592c-105">Recompilation can happen without changes to the method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0592c-106">語法</span><span class="sxs-lookup"><span data-stu-id="0592c-106">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodVersion (  
    [in]  ISymUnmanagedMethod* pMethod,  
    [out] int* version);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0592c-107">參數</span><span class="sxs-lookup"><span data-stu-id="0592c-107">Parameters</span></span>  

 `pMethod`  
 <span data-ttu-id="0592c-108">在要取得版本的方法。</span><span class="sxs-lookup"><span data-stu-id="0592c-108">[in] The method for which to get the version.</span></span>  
  
 `version`  
 <span data-ttu-id="0592c-109">擴展接收方法版本之變數的指標。</span><span class="sxs-lookup"><span data-stu-id="0592c-109">[out] A pointer to a variable that receives the method version.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0592c-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="0592c-110">Return Value</span></span>  

 <span data-ttu-id="0592c-111">如果方法成功，則為 S_OK;否則，E_FAIL 或其他一些錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="0592c-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0592c-112">需求</span><span class="sxs-lookup"><span data-stu-id="0592c-112">Requirements</span></span>  

 <span data-ttu-id="0592c-113">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="0592c-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0592c-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0592c-114">See also</span></span>

- [<span data-ttu-id="0592c-115">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="0592c-115">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
