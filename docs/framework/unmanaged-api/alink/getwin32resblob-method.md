---
title: GetWin32ResBlob 方法
ms.date: 03/30/2017
api_name:
- IALink.GetWin32ResBlob
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetWin32ResBlob
helpviewer_keywords:
- GetWin32ResBlob method
ms.assetid: 36997e04-f9f6-4254-a041-6767ac6c51d9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b26f08548ac964fae2f4d64db50167add327eb2d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777363"
---
# <a name="getwin32resblob-method"></a><span data-ttu-id="e61ce-102">GetWin32ResBlob 方法</span><span class="sxs-lookup"><span data-stu-id="e61ce-102">GetWin32ResBlob Method</span></span>
<span data-ttu-id="e61ce-103">抓取 Win32 資源 blob。</span><span class="sxs-lookup"><span data-stu-id="e61ce-103">Retrieves Win32 resource blob.</span></span> <span data-ttu-id="e61ce-104">設定元件選項之後，請呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="e61ce-104">Call this method after setting assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e61ce-105">語法</span><span class="sxs-lookup"><span data-stu-id="e61ce-105">Syntax</span></span>  
  
```cpp  
HRESULT GetWin32ResBlob(  
    mdAssembly    AssemblyID,  
    mdToken       FileToken,  
    BOOL          fDll,  
    LPCWSTR       pszIconFile,  
    const void**  ppResBlob,  
    DWORD*        pcbResBlob  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="e61ce-106">參數</span><span class="sxs-lookup"><span data-stu-id="e61ce-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="e61ce-107">元件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="e61ce-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="e61ce-108">用來抓取要在建立 Win32 版本資源時使用之檔案名的檔案標記</span><span class="sxs-lookup"><span data-stu-id="e61ce-108">File token used to retrieve the filename to be used when constructing the Win32 Version resource</span></span>  
  
 `fDll`  
 <span data-ttu-id="e61ce-109">如果檔案是 DLL，則為 TRUE，如果是 EXE，則為 false。</span><span class="sxs-lookup"><span data-stu-id="e61ce-109">TRUE if file is a DLL, false for an EXE.</span></span>  
  
 `pszIconFile`  
 <span data-ttu-id="e61ce-110">要插入資源 blob 的選擇性圖示。</span><span class="sxs-lookup"><span data-stu-id="e61ce-110">Optional icon to insert into the resource blob.</span></span>  
  
 `ppResBlob`  
 <span data-ttu-id="e61ce-111">接收資源 blob。</span><span class="sxs-lookup"><span data-stu-id="e61ce-111">Receives the resource blob.</span></span>  
  
 `pcbResBlob`  
 <span data-ttu-id="e61ce-112">接收 blob 的大小。</span><span class="sxs-lookup"><span data-stu-id="e61ce-112">Receives the size of the blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e61ce-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="e61ce-113">Return Value</span></span>  
 <span data-ttu-id="e61ce-114">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="e61ce-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e61ce-115">需求</span><span class="sxs-lookup"><span data-stu-id="e61ce-115">Requirements</span></span>  
 <span data-ttu-id="e61ce-116">需要 alink. h</span><span class="sxs-lookup"><span data-stu-id="e61ce-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e61ce-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e61ce-117">See also</span></span>

- [<span data-ttu-id="e61ce-118">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="e61ce-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="e61ce-119">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="e61ce-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="e61ce-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="e61ce-120">ALink API</span></span>](index.md)
