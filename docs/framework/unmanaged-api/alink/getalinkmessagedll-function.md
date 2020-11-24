---
title: GetALinkMessageDll 函式
ms.date: 03/30/2017
api_name:
- GetALinkMessageDll
api_location:
- alink.dll
api_type:
- DLLExport
f1_keywords:
- GetALinkMessageDll
helpviewer_keywords:
- Alink API, GetALinkMessageDll function
- GetALinkMessageDll function
ms.assetid: 67985a22-88a2-4c54-8d99-4bcde9d6213e
topic_type:
- apiref
ms.openlocfilehash: 554bd32ae965b21a88a09577749bbd7975f5ec7e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684742"
---
# <a name="getalinkmessagedll-function"></a><span data-ttu-id="087fa-102">GetALinkMessageDll 函式</span><span class="sxs-lookup"><span data-stu-id="087fa-102">GetALinkMessageDll Function</span></span>

<span data-ttu-id="087fa-103">尋找並載入訊息 DLL。</span><span class="sxs-lookup"><span data-stu-id="087fa-103">Finds and loads the message DLL.</span></span> <span data-ttu-id="087fa-104">如果無法找到或載入訊息 DLL，則傳回0。</span><span class="sxs-lookup"><span data-stu-id="087fa-104">Returns 0 if the message DLL could not be located or loaded.</span></span> <span data-ttu-id="087fa-105">訊息 DLL 應該在名稱為語言識別項或目前目錄中的子目錄中。</span><span class="sxs-lookup"><span data-stu-id="087fa-105">The message DLL should be either in a subdirectory whose name is a language ID, or in the current directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="087fa-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="087fa-106">Syntax</span></span>  
  
```cpp  
HINSTANCE WINAPI GetALinkMessageDll();  
```  
  
## <a name="requirements"></a><span data-ttu-id="087fa-107">需求</span><span class="sxs-lookup"><span data-stu-id="087fa-107">Requirements</span></span>  

 <span data-ttu-id="087fa-108">**標頭：** alink。h</span><span class="sxs-lookup"><span data-stu-id="087fa-108">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="087fa-109">連結 **庫**： alink.dll</span><span class="sxs-lookup"><span data-stu-id="087fa-109">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="087fa-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="087fa-110">See also</span></span>

- [<span data-ttu-id="087fa-111">Al.exe (元件連結器) </span><span class="sxs-lookup"><span data-stu-id="087fa-111">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
