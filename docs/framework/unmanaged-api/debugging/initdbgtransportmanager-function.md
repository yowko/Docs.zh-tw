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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761646"
---
# <a name="initdbgtransportmanager-function"></a><span data-ttu-id="e9e13-102">InitDbgTransportManager 函式</span><span class="sxs-lookup"><span data-stu-id="e9e13-102">InitDbgTransportManager Function</span></span>
<span data-ttu-id="e9e13-103">針對處理序和執行階段列舉，初始化要與遠端目標連接的傳輸管理員。</span><span class="sxs-lookup"><span data-stu-id="e9e13-103">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9e13-104">語法</span><span class="sxs-lookup"><span data-stu-id="e9e13-104">Syntax</span></span>  
  
```  
HRESULT InitDbgTransportManager ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="e9e13-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="e9e13-105">Return Value</span></span>  
 <span data-ttu-id="e9e13-106">S_OK</span><span class="sxs-lookup"><span data-stu-id="e9e13-106">S_OK</span></span>  
 <span data-ttu-id="e9e13-107">成功。</span><span class="sxs-lookup"><span data-stu-id="e9e13-107">Success.</span></span>  
  
 <span data-ttu-id="e9e13-108">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="e9e13-108">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="e9e13-109">函式無法對傳輸管理員配置記憶體。</span><span class="sxs-lookup"><span data-stu-id="e9e13-109">The function was unable to allocate memory for a transport manager.</span></span>  
  
 <span data-ttu-id="e9e13-110">E_FAIL (或其他 E_ 傳回碼)</span><span class="sxs-lookup"><span data-stu-id="e9e13-110">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="e9e13-111">其他失敗。</span><span class="sxs-lookup"><span data-stu-id="e9e13-111">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9e13-112">需求</span><span class="sxs-lookup"><span data-stu-id="e9e13-112">Requirements</span></span>  
 <span data-ttu-id="e9e13-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e9e13-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9e13-114">**標頭：** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="e9e13-114">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="e9e13-115">**程式庫：** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="e9e13-115">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="e9e13-116">**.NET framework 版本：** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="e9e13-116">**.NET Framework Versions:** 3.5 SP1</span></span>
