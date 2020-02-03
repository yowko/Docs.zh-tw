---
title: 啟動函式-WPF 非受控 API 參考
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- Activate
api_location:
- PresentationHost_v0400.dll
ms.assetid: 1400329c-b598-465f-80f2-e3dabf044811
ms.openlocfilehash: 9c0a235e8b94294ab82da88e43f7446c29739c12
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734507"
---
# <a name="activate-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="fe49c-102">Activate 函式（WPF 非受控 API 參考）</span><span class="sxs-lookup"><span data-stu-id="fe49c-102">Activate Function (WPF Unmanaged API Reference)</span></span>

<span data-ttu-id="fe49c-103">這個 API 支援 Windows Presentation Foundation （WPF）基礎結構，但不適合直接從程式碼使用。</span><span class="sxs-lookup"><span data-stu-id="fe49c-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>

<span data-ttu-id="fe49c-104">由適用于 Windows 管理的 Windows Presentation Foundation （WPF）基礎結構使用。</span><span class="sxs-lookup"><span data-stu-id="fe49c-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>

## <a name="syntax"></a><span data-ttu-id="fe49c-105">語法</span><span class="sxs-lookup"><span data-stu-id="fe49c-105">Syntax</span></span>

```cpp
void Activate(
    const ActivateParameters* pParameters,
    __deref_out_ecount(1) LPUNKNOWN* ppInner,
    );
```

## <a name="parameters"></a><span data-ttu-id="fe49c-106">參數</span><span class="sxs-lookup"><span data-stu-id="fe49c-106">Parameters</span></span>

`pParameters`\
<span data-ttu-id="fe49c-107">視窗啟用參數的指標。</span><span class="sxs-lookup"><span data-stu-id="fe49c-107">A pointer to the window's activation parameters.</span></span>

`ppInner`\
<span data-ttu-id="fe49c-108">單一元素緩衝區的位址指標，其中包含指向 <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="fe49c-108">A pointer to the address of a single-element buffer that contains a pointer to an <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> object.</span></span>

## <a name="requirements"></a><span data-ttu-id="fe49c-109">需求</span><span class="sxs-lookup"><span data-stu-id="fe49c-109">Requirements</span></span>

<span data-ttu-id="fe49c-110">**平臺：** 請參閱[.NET Framework 系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="fe49c-110">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="fe49c-111">**URLMON.DLL**</span><span class="sxs-lookup"><span data-stu-id="fe49c-111">**DLL:**</span></span>

<span data-ttu-id="fe49c-112">在 .NET Framework 3.0 和3.5： PresentationHostDLL 中</span><span class="sxs-lookup"><span data-stu-id="fe49c-112">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>

<span data-ttu-id="fe49c-113">在 .NET Framework 4 和更新版本中： PresentationHost_v0400 .dll</span><span class="sxs-lookup"><span data-stu-id="fe49c-113">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>

<span data-ttu-id="fe49c-114">**.NET Framework 版本：** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe49c-114">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="fe49c-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fe49c-115">See also</span></span>

- [<span data-ttu-id="fe49c-116">WPF Unmanaged API 參考</span><span class="sxs-lookup"><span data-stu-id="fe49c-116">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)
