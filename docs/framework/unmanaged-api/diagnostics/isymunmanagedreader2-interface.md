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
ms.openlocfilehash: 3f34be833d3ccb5c636d2c5f18ccb6e216ef2c49
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709072"
---
# <a name="isymunmanagedreader2-interface"></a><span data-ttu-id="bbbf2-102">ISymUnmanagedReader2 介面</span><span class="sxs-lookup"><span data-stu-id="bbbf2-102">ISymUnmanagedReader2 Interface</span></span>

<span data-ttu-id="bbbf2-103">代表可讓您存取符號存放區內文件、方法和變數的符號讀取器。</span><span class="sxs-lookup"><span data-stu-id="bbbf2-103">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span> <span data-ttu-id="bbbf2-104">這個介面會擴充 [ISymUnmanagedReader](isymunmanagedreader-interface.md) 介面。</span><span class="sxs-lookup"><span data-stu-id="bbbf2-104">This interface extends the [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bbbf2-105">方法</span><span class="sxs-lookup"><span data-stu-id="bbbf2-105">Methods</span></span>  
  
|<span data-ttu-id="bbbf2-106">方法</span><span class="sxs-lookup"><span data-stu-id="bbbf2-106">Method</span></span>|<span data-ttu-id="bbbf2-107">描述</span><span class="sxs-lookup"><span data-stu-id="bbbf2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bbbf2-108">GetMethodByVersionPreRemap 方法</span><span class="sxs-lookup"><span data-stu-id="bbbf2-108">GetMethodByVersionPreRemap Method</span></span>](isymunmanagedreader2-getmethodbyversionpreremap-method.md)|<span data-ttu-id="bbbf2-109">取得符號讀取器方法，並指定方法 token 和編輯後繼續版本號碼。</span><span class="sxs-lookup"><span data-stu-id="bbbf2-109">Get a symbol reader method, given a method token and an edit-and-continue version number.</span></span>|  
|[<span data-ttu-id="bbbf2-110">GetMethodsInDocument 方法</span><span class="sxs-lookup"><span data-stu-id="bbbf2-110">GetMethodsInDocument Method</span></span>](isymunmanagedreader2-getmethodsindocument-method.md)|<span data-ttu-id="bbbf2-111">取得在提供的檔中有行資訊的每個方法。</span><span class="sxs-lookup"><span data-stu-id="bbbf2-111">Gets every method that has line information in the provided document.</span></span>|  
|[<span data-ttu-id="bbbf2-112">GetSymAttributePreRemap 方法</span><span class="sxs-lookup"><span data-stu-id="bbbf2-112">GetSymAttributePreRemap Method</span></span>](isymunmanagedreader2-getsymattributepreremap-method.md)|<span data-ttu-id="bbbf2-113">根據名稱，取得自訂屬性。</span><span class="sxs-lookup"><span data-stu-id="bbbf2-113">Gets a custom attribute based upon its name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bbbf2-114">需求</span><span class="sxs-lookup"><span data-stu-id="bbbf2-114">Requirements</span></span>  

 <span data-ttu-id="bbbf2-115">**標頭：** CorSym .idl、CorSym。h</span><span class="sxs-lookup"><span data-stu-id="bbbf2-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbbf2-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bbbf2-116">See also</span></span>

- [<span data-ttu-id="bbbf2-117">診斷符號存放區介面</span><span class="sxs-lookup"><span data-stu-id="bbbf2-117">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="bbbf2-118">ISymUnmanagedReader 介面</span><span class="sxs-lookup"><span data-stu-id="bbbf2-118">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
