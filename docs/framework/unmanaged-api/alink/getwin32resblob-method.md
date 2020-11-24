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
ms.openlocfilehash: 03f6c97b4a5bbbdc0aeaf7b3f07277e66d7d0e9a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684508"
---
# <a name="getwin32resblob-method"></a><span data-ttu-id="59eb7-102">GetWin32ResBlob 方法</span><span class="sxs-lookup"><span data-stu-id="59eb7-102">GetWin32ResBlob Method</span></span>

<span data-ttu-id="59eb7-103">抓取 Win32 資源 blob。</span><span class="sxs-lookup"><span data-stu-id="59eb7-103">Retrieves Win32 resource blob.</span></span> <span data-ttu-id="59eb7-104">在設定元件選項之後，請呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="59eb7-104">Call this method after setting assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59eb7-105">語法</span><span class="sxs-lookup"><span data-stu-id="59eb7-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="59eb7-106">參數</span><span class="sxs-lookup"><span data-stu-id="59eb7-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="59eb7-107">元件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="59eb7-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="59eb7-108">用來抓取在建立 Win32 版本資源時所使用之檔案名的檔案 token</span><span class="sxs-lookup"><span data-stu-id="59eb7-108">File token used to retrieve the filename to be used when constructing the Win32 Version resource</span></span>  
  
 `fDll`  
 <span data-ttu-id="59eb7-109">如果 file 是 DLL，則為 TRUE，EXE 則為 false。</span><span class="sxs-lookup"><span data-stu-id="59eb7-109">TRUE if file is a DLL, false for an EXE.</span></span>  
  
 `pszIconFile`  
 <span data-ttu-id="59eb7-110">要插入至資源 blob 的選擇性圖示。</span><span class="sxs-lookup"><span data-stu-id="59eb7-110">Optional icon to insert into the resource blob.</span></span>  
  
 `ppResBlob`  
 <span data-ttu-id="59eb7-111">接收資源 blob。</span><span class="sxs-lookup"><span data-stu-id="59eb7-111">Receives the resource blob.</span></span>  
  
 `pcbResBlob`  
 <span data-ttu-id="59eb7-112">接收 blob 的大小。</span><span class="sxs-lookup"><span data-stu-id="59eb7-112">Receives the size of the blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="59eb7-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="59eb7-113">Return Value</span></span>  

 <span data-ttu-id="59eb7-114">如果方法成功，則傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="59eb7-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59eb7-115">需求</span><span class="sxs-lookup"><span data-stu-id="59eb7-115">Requirements</span></span>  

 <span data-ttu-id="59eb7-116">需要 alink。h</span><span class="sxs-lookup"><span data-stu-id="59eb7-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59eb7-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59eb7-117">See also</span></span>

- [<span data-ttu-id="59eb7-118">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="59eb7-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="59eb7-119">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="59eb7-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="59eb7-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="59eb7-120">ALink API</span></span>](index.md)
