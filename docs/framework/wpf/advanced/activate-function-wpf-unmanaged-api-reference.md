---
title: 啟用函式 (WPF Unmanaged API 參考)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- Activate
api_location:
- PresentationHost_v0400.dll
ms.assetid: 1400329c-b598-465f-80f2-e3dabf044811
ms.openlocfilehash: ee231653815bd5ef75d58979034e3b3be9f5ba54
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777165"
---
# <a name="activate-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="29478-102">啟用函式 (WPF Unmanaged API 參考)</span><span class="sxs-lookup"><span data-stu-id="29478-102">Activate Function (WPF Unmanaged API Reference)</span></span>

<span data-ttu-id="29478-103">此 API 支援 Windows Presentation Foundation (WPF) 基礎結構，並不是直接從您的程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="29478-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>

<span data-ttu-id="29478-104">使用 windows 管理的 Windows Presentation Foundation (WPF) 基礎結構。</span><span class="sxs-lookup"><span data-stu-id="29478-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>

## <a name="syntax"></a><span data-ttu-id="29478-105">語法</span><span class="sxs-lookup"><span data-stu-id="29478-105">Syntax</span></span>

```cpp
void Activate(
    const ActivateParameters* pParameters,
    __deref_out_ecount(1) LPUNKNOWN* ppInner,
    );
```

## <a name="parameters"></a><span data-ttu-id="29478-106">參數</span><span class="sxs-lookup"><span data-stu-id="29478-106">Parameters</span></span>

`pParameters`\
<span data-ttu-id="29478-107">指向視窗的啟動參數的指標。</span><span class="sxs-lookup"><span data-stu-id="29478-107">A pointer to the window's activation parameters.</span></span>

`ppInner`\
<span data-ttu-id="29478-108">包含一個指向單一項目緩衝區的位址指標<xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument>物件。</span><span class="sxs-lookup"><span data-stu-id="29478-108">A pointer to the address of a single-element buffer that contains a pointer to an <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> object.</span></span>

## <a name="requirements"></a><span data-ttu-id="29478-109">需求</span><span class="sxs-lookup"><span data-stu-id="29478-109">Requirements</span></span>

<span data-ttu-id="29478-110">**平台：** 請參閱[.NET Framework 系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="29478-110">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="29478-111">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="29478-111">**DLL:**</span></span>

<span data-ttu-id="29478-112">在.NET Framework 3.0 和 3.5:PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="29478-112">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>

<span data-ttu-id="29478-113">在.NET Framework 4 及更新版本：PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="29478-113">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>

<span data-ttu-id="29478-114">**.NET framework 版本：** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29478-114">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="29478-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29478-115">See also</span></span>

- [<span data-ttu-id="29478-116">WPF Unmanaged API 參考</span><span class="sxs-lookup"><span data-stu-id="29478-116">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
