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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d4bc763d908156f3bbf8998c13073820686903f6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986371"
---
# <a name="isymunmanagedreadergetmethodbyversion-method"></a><span data-ttu-id="1cbf6-102">ISymUnmanagedReader::GetMethodByVersion 方法</span><span class="sxs-lookup"><span data-stu-id="1cbf6-102">ISymUnmanagedReader::GetMethodByVersion Method</span></span>
<span data-ttu-id="1cbf6-103">取得符號讀取器方法，指定方法的語彙基元和編輯複製版本號碼。</span><span class="sxs-lookup"><span data-stu-id="1cbf6-103">Gets a symbol reader method, given a method token and an edit-and-copy version number.</span></span> <span data-ttu-id="1cbf6-104">版本號碼從 1 開始，就會遞增每次編輯複製作業造成變更的方法時。</span><span class="sxs-lookup"><span data-stu-id="1cbf6-104">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-copy operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cbf6-105">語法</span><span class="sxs-lookup"><span data-stu-id="1cbf6-105">Syntax</span></span>  
  
```  
HRESULT GetMethodByVersion (  
    [in]  mdMethodDef  token,  
    [in]  int  version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1cbf6-106">參數</span><span class="sxs-lookup"><span data-stu-id="1cbf6-106">Parameters</span></span>  
 `token`  
 <span data-ttu-id="1cbf6-107">[in]方法的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="1cbf6-107">[in] The method token.</span></span>  
  
 `version`  
 <span data-ttu-id="1cbf6-108">[in]方法的版本。</span><span class="sxs-lookup"><span data-stu-id="1cbf6-108">[in] The method version.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="1cbf6-109">[out]傳回的介面指標。</span><span class="sxs-lookup"><span data-stu-id="1cbf6-109">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1cbf6-110">傳回值</span><span class="sxs-lookup"><span data-stu-id="1cbf6-110">Return Value</span></span>  
 <span data-ttu-id="1cbf6-111">如果方法成功，則為 S_OK否則，E_FAIL 或一些其他的錯誤程式碼。</span><span class="sxs-lookup"><span data-stu-id="1cbf6-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1cbf6-112">需求</span><span class="sxs-lookup"><span data-stu-id="1cbf6-112">Requirements</span></span>  
 <span data-ttu-id="1cbf6-113">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1cbf6-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cbf6-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1cbf6-114">See also</span></span>

- [<span data-ttu-id="1cbf6-115">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="1cbf6-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
