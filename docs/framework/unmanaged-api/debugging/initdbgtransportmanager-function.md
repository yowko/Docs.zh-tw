---
title: InitDbgTransportManager 函式
ms.date: 03/30/2017
api_name:
- InitDbgTransportManager
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- InitDbgTransportManager
helpviewer_keywords:
- remote debugging API [Silverlight]
- InitDbgTransportManager function
- Silverlight, remote debugging
ms.assetid: a30102ff-c52e-48c9-b3a9-aa14286a42b2
topic_type:
- apiref
ms.openlocfilehash: a5b4783eadb8045733b9ebd6d10c4e31f7829498
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716677"
---
# <a name="initdbgtransportmanager-function"></a><span data-ttu-id="27087-102">InitDbgTransportManager 函式</span><span class="sxs-lookup"><span data-stu-id="27087-102">InitDbgTransportManager Function</span></span>

<span data-ttu-id="27087-103">針對處理序和執行階段列舉，初始化要與遠端目標連接的傳輸管理員。</span><span class="sxs-lookup"><span data-stu-id="27087-103">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27087-104">語法</span><span class="sxs-lookup"><span data-stu-id="27087-104">Syntax</span></span>  
  
```cpp  
HRESULT InitDbgTransportManager ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="27087-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="27087-105">Return Value</span></span>  

 <span data-ttu-id="27087-106">S_OK</span><span class="sxs-lookup"><span data-stu-id="27087-106">S_OK</span></span>  
 <span data-ttu-id="27087-107">成功。</span><span class="sxs-lookup"><span data-stu-id="27087-107">Success.</span></span>  
  
 <span data-ttu-id="27087-108">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="27087-108">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="27087-109">函式無法對傳輸管理員配置記憶體。</span><span class="sxs-lookup"><span data-stu-id="27087-109">The function was unable to allocate memory for a transport manager.</span></span>  
  
 <span data-ttu-id="27087-110">E_FAIL (或其他 E_ 傳回碼)</span><span class="sxs-lookup"><span data-stu-id="27087-110">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="27087-111">其他失敗。</span><span class="sxs-lookup"><span data-stu-id="27087-111">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27087-112">需求</span><span class="sxs-lookup"><span data-stu-id="27087-112">Requirements</span></span>  

 <span data-ttu-id="27087-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="27087-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27087-114">**標頭：** CoreClrRemoteDebuggingInterfaces。h</span><span class="sxs-lookup"><span data-stu-id="27087-114">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="27087-115">連結 **庫：** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="27087-115">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="27087-116">**.NET Framework 版本：** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="27087-116">**.NET Framework Versions:** 3.5 SP1</span></span>
