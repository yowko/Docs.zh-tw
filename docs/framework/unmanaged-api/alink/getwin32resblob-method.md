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
ms.openlocfilehash: 295b150f6881a47b3816a93ac7a20382bc5c20c0
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57500573"
---
# <a name="getwin32resblob-method"></a><span data-ttu-id="02f0e-102">GetWin32ResBlob 方法</span><span class="sxs-lookup"><span data-stu-id="02f0e-102">GetWin32ResBlob Method</span></span>
<span data-ttu-id="02f0e-103">擷取 Win32 資源的 blob。</span><span class="sxs-lookup"><span data-stu-id="02f0e-103">Retrieves Win32 resource blob.</span></span> <span data-ttu-id="02f0e-104">設定組件選項之後呼叫這個方法。</span><span class="sxs-lookup"><span data-stu-id="02f0e-104">Call this method after setting assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02f0e-105">語法</span><span class="sxs-lookup"><span data-stu-id="02f0e-105">Syntax</span></span>  
  
```  
HRESULT GetWin32ResBlob(  
    mdAssembly    AssemblyID,  
    mdToken       FileToken,  
    BOOL          fDll,  
    LPCWSTR       pszIconFile,  
    const void**  ppResBlob,  
    DWORD*        pcbResBlob  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="02f0e-106">參數</span><span class="sxs-lookup"><span data-stu-id="02f0e-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="02f0e-107">組件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="02f0e-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="02f0e-108">用來擷取建構的 Win32 版本資源時所要使用的檔名語彙基元檔案</span><span class="sxs-lookup"><span data-stu-id="02f0e-108">File token used to retrieve the filename to be used when constructing the Win32 Version resource</span></span>  
  
 `fDll`  
 <span data-ttu-id="02f0e-109">如果檔案是 DLL，false EXE，則為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="02f0e-109">TRUE if file is a DLL, false for an EXE.</span></span>  
  
 `pszIconFile`  
 <span data-ttu-id="02f0e-110">若要將資源的 blob 插入的選擇性圖示。</span><span class="sxs-lookup"><span data-stu-id="02f0e-110">Optional icon to insert into the resource blob.</span></span>  
  
 `ppResBlob`  
 <span data-ttu-id="02f0e-111">收到資源的 blob。</span><span class="sxs-lookup"><span data-stu-id="02f0e-111">Receives the resource blob.</span></span>  
  
 `pcbResBlob`  
 <span data-ttu-id="02f0e-112">接收 blob 的大小。</span><span class="sxs-lookup"><span data-stu-id="02f0e-112">Receives the size of the blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="02f0e-113">傳回值</span><span class="sxs-lookup"><span data-stu-id="02f0e-113">Return Value</span></span>  
 <span data-ttu-id="02f0e-114">如果方法成功，則會傳回 S_OK。</span><span class="sxs-lookup"><span data-stu-id="02f0e-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02f0e-115">需求</span><span class="sxs-lookup"><span data-stu-id="02f0e-115">Requirements</span></span>  
 <span data-ttu-id="02f0e-116">需要 alink.h</span><span class="sxs-lookup"><span data-stu-id="02f0e-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02f0e-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02f0e-117">See also</span></span>
- [<span data-ttu-id="02f0e-118">IALink 介面</span><span class="sxs-lookup"><span data-stu-id="02f0e-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="02f0e-119">IALink2 介面</span><span class="sxs-lookup"><span data-stu-id="02f0e-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="02f0e-120">ALink API</span><span class="sxs-lookup"><span data-stu-id="02f0e-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
