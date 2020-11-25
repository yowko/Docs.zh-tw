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
ms.openlocfilehash: 5ec67758e3174493cbd5cec1de0dcce30013ac43
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698581"
---
# <a name="isymunmanageddocumentfindclosestline-method"></a><span data-ttu-id="44625-102">ISymUnmanagedDocument::FindClosestLine 方法</span><span class="sxs-lookup"><span data-stu-id="44625-102">ISymUnmanagedDocument::FindClosestLine Method</span></span>

<span data-ttu-id="44625-103">如果本檔中不一定是序列點的行，則傳回最接近序列點的行。</span><span class="sxs-lookup"><span data-stu-id="44625-103">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44625-104">語法</span><span class="sxs-lookup"><span data-stu-id="44625-104">Syntax</span></span>  
  
```cpp  
HRESULT FindClosestLine(  
    [in]  ULONG32  line,  
    [out, retval] ULONG32*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44625-105">參數</span><span class="sxs-lookup"><span data-stu-id="44625-105">Parameters</span></span>  

 `line`  
 <span data-ttu-id="44625-106">在這份檔中有一行。</span><span class="sxs-lookup"><span data-stu-id="44625-106">[in] A line in this document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="44625-107">擴展接收該行之變數的指標。</span><span class="sxs-lookup"><span data-stu-id="44625-107">[out] A pointer to a variable that receives the line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="44625-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="44625-108">Return Value</span></span>  

 <span data-ttu-id="44625-109">如果方法成功，則為 S_OK;否則為錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="44625-109">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44625-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44625-110">See also</span></span>

- [<span data-ttu-id="44625-111">ISymUnmanagedDocument 介面</span><span class="sxs-lookup"><span data-stu-id="44625-111">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
