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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 74cb2c7d1f79d23e1331cc7192ba2d6acfd9835c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423659"
---
# <a name="initdbgtransportmanager-function"></a><span data-ttu-id="2a26f-102">InitDbgTransportManager 函式</span><span class="sxs-lookup"><span data-stu-id="2a26f-102">InitDbgTransportManager Function</span></span>
<span data-ttu-id="2a26f-103">針對處理序和執行階段列舉，對要與遠端目標連接的傳輸管理員初始化。</span><span class="sxs-lookup"><span data-stu-id="2a26f-103">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a26f-104">語法</span><span class="sxs-lookup"><span data-stu-id="2a26f-104">Syntax</span></span>  
  
```  
HRESULT InitDbgTransportManager ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="2a26f-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="2a26f-105">Return Value</span></span>  
 <span data-ttu-id="2a26f-106">S_OK</span><span class="sxs-lookup"><span data-stu-id="2a26f-106">S_OK</span></span>  
 <span data-ttu-id="2a26f-107">成功。</span><span class="sxs-lookup"><span data-stu-id="2a26f-107">Success.</span></span>  
  
 <span data-ttu-id="2a26f-108">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="2a26f-108">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="2a26f-109">函式無法對傳輸管理員配置記憶體。</span><span class="sxs-lookup"><span data-stu-id="2a26f-109">The function was unable to allocate memory for a transport manager.</span></span>  
  
 <span data-ttu-id="2a26f-110">E_FAIL (或其他 E_ 傳回碼)</span><span class="sxs-lookup"><span data-stu-id="2a26f-110">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="2a26f-111">其他失敗。</span><span class="sxs-lookup"><span data-stu-id="2a26f-111">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a26f-112">需求</span><span class="sxs-lookup"><span data-stu-id="2a26f-112">Requirements</span></span>  
 <span data-ttu-id="2a26f-113">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2a26f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a26f-114">**標頭：** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="2a26f-114">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="2a26f-115">**程式庫：** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="2a26f-115">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="2a26f-116">**.NET framework 版本：** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="2a26f-116">**.NET Framework Versions:** 3.5 SP1</span></span>
