---
title: 重大變更：將 RCW 轉換成擲回 `InterfaceIsIInspectable` 例外狀況
description: 瞭解在 .NET 5.0 中將 RCW 轉換成介面時，會擲回 PlatformNotSupportedException 的 interop 重大變更 `InterfaceIsIInspectable` 。
ms.date: 09/13/2020
ms.openlocfilehash: 7c0f37057aebcc41d0c00d949b921ec3a4bdf012
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760716"
---
# <a name="casting-rcw-to-an-interfaceisiinspectable-interface-throws-platformnotsupportedexception"></a><span data-ttu-id="b1397-103">將 RCW 轉換成介面會擲回 `InterfaceIsIInspectable` PlatformNotSupportedException</span><span class="sxs-lookup"><span data-stu-id="b1397-103">Casting RCW to an `InterfaceIsIInspectable` interface throws PlatformNotSupportedException</span></span>

<span data-ttu-id="b1397-104">將執行時間可呼叫包裝函式 (RCW) 轉換為標示為的介面，現在會擲回 <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> <xref:System.PlatformNotSupportedException> 。</span><span class="sxs-lookup"><span data-stu-id="b1397-104">Casting a runtime callable wrapper (RCW) to an interface marked as <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> now throws a <xref:System.PlatformNotSupportedException>.</span></span> <span data-ttu-id="b1397-105">這項變更是 [從 .net 移除 WinRT 支援](built-in-support-for-winrt-removed.md)的後續變更。</span><span class="sxs-lookup"><span data-stu-id="b1397-105">This change is a follow up to the [removal of WinRT support from .NET](built-in-support-for-winrt-removed.md).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="b1397-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="b1397-106">Version introduced</span></span>

<span data-ttu-id="b1397-107">5.0 RC2</span><span class="sxs-lookup"><span data-stu-id="b1397-107">5.0 RC2</span></span>

## <a name="change-description"></a><span data-ttu-id="b1397-108">變更描述</span><span class="sxs-lookup"><span data-stu-id="b1397-108">Change description</span></span>

<span data-ttu-id="b1397-109">在 .net 5.0 preview 6 之前的 .NET 版本中，將 RCW 轉換為標示為如 <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> 預期般運作的介面。</span><span class="sxs-lookup"><span data-stu-id="b1397-109">In .NET versions prior to .NET 5.0 preview 6, casting an RCW to an interface marked as <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> works as expected.</span></span> <span data-ttu-id="b1397-110">在 .NET 5.0 預覽版6-8 和 RC1 中，您可以成功地將 RCW 轉換成 <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> 介面。</span><span class="sxs-lookup"><span data-stu-id="b1397-110">In .NET 5.0 previews 6-8 and RC1, you can successfully cast an RCW to an <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> interface.</span></span> <span data-ttu-id="b1397-111">不過，當您在介面上執行方法時，您可能會發生存取違規，因為執行時間中的基礎支援 [已在 .net 5.0 preview 6 中移除](built-in-support-for-winrt-removed.md)。</span><span class="sxs-lookup"><span data-stu-id="b1397-111">However, you might get access violations when you execute methods on the interface, because the underlying support in the runtime [was removed in .NET 5.0 preview 6](built-in-support-for-winrt-removed.md).</span></span>

<span data-ttu-id="b1397-112">在 .NET 5.0 RC2 和更新版本中，將 RCW 轉換成標記為的介面會 <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> <xref:System.PlatformNotSupportedException> 在轉換時間擲回。</span><span class="sxs-lookup"><span data-stu-id="b1397-112">In .NET 5.0 RC2 and later versions, casting an RCW to an interface marked as <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> throws a <xref:System.PlatformNotSupportedException> at cast time.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="b1397-113">變更的原因</span><span class="sxs-lookup"><span data-stu-id="b1397-113">Reason for change</span></span>

<span data-ttu-id="b1397-114">的支援 <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> 已 [在先前的 .net 5.0 preview 中移除](built-in-support-for-winrt-removed.md)。</span><span class="sxs-lookup"><span data-stu-id="b1397-114">The support for <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> was [removed in a previous .NET 5.0 preview](built-in-support-for-winrt-removed.md).</span></span> <span data-ttu-id="b1397-115">但是， <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> 不小心會忽略轉換成介面的。</span><span class="sxs-lookup"><span data-stu-id="b1397-115">However, casting to an <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> interface was accidentally overlooked.</span></span> <span data-ttu-id="b1397-116">因為執行時間中的基礎支援已不存在，所以擲回會 <xref:System.PlatformNotSupportedException> 啟用正常失敗路徑。</span><span class="sxs-lookup"><span data-stu-id="b1397-116">Since the underlying support in the runtime no longer exists, throwing a <xref:System.PlatformNotSupportedException> enables a graceful failure path.</span></span> <span data-ttu-id="b1397-117">擲回例外狀況也可讓您更容易發現這項功能已不再受到支援。</span><span class="sxs-lookup"><span data-stu-id="b1397-117">Throwing an exception also makes it more discoverable that this feature is no longer supported.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="b1397-118">建議的動作</span><span class="sxs-lookup"><span data-stu-id="b1397-118">Recommended action</span></span>

- <span data-ttu-id="b1397-119">如果您可以在 Windows 執行時間中繼資料中定義介面 (WinMD) 檔，請改用 c #/WinRT 工具。</span><span class="sxs-lookup"><span data-stu-id="b1397-119">If you can define the interface in a Windows runtime metadata (WinMD) file, use the C#/WinRT tool instead.</span></span>

- <span data-ttu-id="b1397-120">否則，請將介面標示為 <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIUnknown> 而不是 <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> ，然後將三個虛擬專案加入至方法的介面開頭 <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> 。</span><span class="sxs-lookup"><span data-stu-id="b1397-120">Otherwise, mark the interface as <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIUnknown> instead of <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable>, and add three dummy entries to the start of the interface for the <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable> methods.</span></span> <span data-ttu-id="b1397-121">下列程式碼片段顯示範例。</span><span class="sxs-lookup"><span data-stu-id="b1397-121">The following code snippet shows an example.</span></span>

  ```csharp
  [InterfaceType(ComInterfaceType.InterfaceIsIUnknown)]
  interface IMine
  {
      // Do not call these three methods.
      // They're exclusively to fill in the slots in the vtable.
      void GetIIdsSlot();
      void GetRuntimeClassNameSlot();
      void GetTrustLevelSlot();

      // The original members of the IMine interface go here.
      ...
  }
  ```

## <a name="affected-apis"></a><span data-ttu-id="b1397-122">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="b1397-122">Affected APIs</span></span>

- <xref:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable?displayProperty=fullName>

<!--

### Affected APIs

- `F:System.Runtime.InteropServices.ComInterfaceType.InterfaceIsIInspectable`

### Category

Interop

-->
