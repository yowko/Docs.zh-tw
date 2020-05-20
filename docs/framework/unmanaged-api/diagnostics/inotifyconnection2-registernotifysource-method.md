---
title: INotifyConnection2::RegisterNotifySource 方法
ms.date: 03/30/2017
api_name:
- INotifyConnection2.RegisterNotifySource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifyConnection2::RegisterNotifySource
helpviewer_keywords:
- INotifyConnection2::RegisterNotifySource method [.NET Framework debugging]
- RegisterNotifySource method [.NET Framework debugging]
ms.assetid: 2632da80-6e4b-4429-8dee-b382745a5f81
topic_type:
- apiref
ms.openlocfilehash: b7fa777466e2c7edd7b3110dd91e776785c63c58
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442068"
---
# <a name="inotifyconnection2registernotifysource-method"></a><span data-ttu-id="791d1-102">INotifyConnection2::RegisterNotifySource 方法</span><span class="sxs-lookup"><span data-stu-id="791d1-102">INotifyConnection2::RegisterNotifySource Method</span></span>
<span data-ttu-id="791d1-103">安裝指定的通知來源。</span><span class="sxs-lookup"><span data-stu-id="791d1-103">Installs a specified notification source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="791d1-104">語法</span><span class="sxs-lookup"><span data-stu-id="791d1-104">Syntax</span></span>  
  
```cpp  
HRESULT RegisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource,  
    [out] INotifySink2**   out_ppNotifySink  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="791d1-105">參數</span><span class="sxs-lookup"><span data-stu-id="791d1-105">Parameters</span></span>  
 `in_pNotifySource`  
 <span data-ttu-id="791d1-106">在指定要當做通知來源使用的物件。</span><span class="sxs-lookup"><span data-stu-id="791d1-106">[in] Specifies the object to be used as the notification source.</span></span>  
  
 `out_ppNotifySink`  
 <span data-ttu-id="791d1-107">脫銷接收要當做通知接收使用的物件。</span><span class="sxs-lookup"><span data-stu-id="791d1-107">[out] Receives the object to be used as the notification sink.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="791d1-108">傳回值</span><span class="sxs-lookup"><span data-stu-id="791d1-108">Return Value</span></span>  
 <span data-ttu-id="791d1-109">如果方法成功，則 S_OK。</span><span class="sxs-lookup"><span data-stu-id="791d1-109">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="791d1-110">需求</span><span class="sxs-lookup"><span data-stu-id="791d1-110">Requirements</span></span>  
 <span data-ttu-id="791d1-111">**標頭：** ProtocolNotify2 .idl</span><span class="sxs-lookup"><span data-stu-id="791d1-111">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="791d1-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="791d1-112">See also</span></span>

- [<span data-ttu-id="791d1-113">INotifyConnection2 介面</span><span class="sxs-lookup"><span data-stu-id="791d1-113">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
- [<span data-ttu-id="791d1-114">INotifySource2 介面</span><span class="sxs-lookup"><span data-stu-id="791d1-114">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="791d1-115">INotifySink2 介面</span><span class="sxs-lookup"><span data-stu-id="791d1-115">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="791d1-116">UnregisterNotifySource 方法</span><span class="sxs-lookup"><span data-stu-id="791d1-116">UnregisterNotifySource Method</span></span>](inotifyconnection2-unregisternotifysource-method.md)
