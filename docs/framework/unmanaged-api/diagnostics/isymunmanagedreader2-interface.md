---
title: ISymUnmanagedReader2 介面
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2
helpviewer_keywords:
- ISymUnmanagedReader2 interface [.NET Framework debugging]
ms.assetid: a01a881b-82a3-4b3e-a3a9-9dc305c2e5f7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a08695c4e5df6aaa63bedecf68b741302e5ddd8e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54524934"
---
# <a name="isymunmanagedreader2-interface"></a><span data-ttu-id="d97f8-102">ISymUnmanagedReader2 介面</span><span class="sxs-lookup"><span data-stu-id="d97f8-102">ISymUnmanagedReader2 Interface</span></span>
<span data-ttu-id="d97f8-103">表示符號讀取器可存取文件、 方法和符號存放區內的變數。</span><span class="sxs-lookup"><span data-stu-id="d97f8-103">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span> <span data-ttu-id="d97f8-104">這個介面會擴充[ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="d97f8-104">This interface extends the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d97f8-105">方法</span><span class="sxs-lookup"><span data-stu-id="d97f8-105">Methods</span></span>  
  
|<span data-ttu-id="d97f8-106">方法</span><span class="sxs-lookup"><span data-stu-id="d97f8-106">Method</span></span>|<span data-ttu-id="d97f8-107">描述</span><span class="sxs-lookup"><span data-stu-id="d97f8-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d97f8-108">GetMethodByVersionPreRemap 方法</span><span class="sxs-lookup"><span data-stu-id="d97f8-108">GetMethodByVersionPreRemap Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodbyversionpreremap-method.md)|<span data-ttu-id="d97f8-109">取得符號讀取器方法，指定方法的語彙基元 」 和 「 編輯後繼續版本號碼。</span><span class="sxs-lookup"><span data-stu-id="d97f8-109">Get a symbol reader method, given a method token and an edit-and-continue version number.</span></span>|  
|[<span data-ttu-id="d97f8-110">GetMethodsInDocument 方法</span><span class="sxs-lookup"><span data-stu-id="d97f8-110">GetMethodsInDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodsindocument-method.md)|<span data-ttu-id="d97f8-111">取得每個提供的文件中具有行資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="d97f8-111">Gets every method that has line information in the provided document.</span></span>|  
|[<span data-ttu-id="d97f8-112">GetSymAttributePreRemap 方法</span><span class="sxs-lookup"><span data-stu-id="d97f8-112">GetSymAttributePreRemap Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getsymattributepreremap-method.md)|<span data-ttu-id="d97f8-113">取得自訂屬性，根據其名稱。</span><span class="sxs-lookup"><span data-stu-id="d97f8-113">Gets a custom attribute based upon its name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d97f8-114">需求</span><span class="sxs-lookup"><span data-stu-id="d97f8-114">Requirements</span></span>  
 <span data-ttu-id="d97f8-115">**標頭：** 於 CorSym.idl CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d97f8-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d97f8-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d97f8-116">See also</span></span>
- [<span data-ttu-id="d97f8-117">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="d97f8-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="d97f8-118">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="d97f8-118">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
