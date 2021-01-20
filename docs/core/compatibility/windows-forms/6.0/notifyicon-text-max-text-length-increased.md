---
title: 重大變更： NotifyIcon。文字長度上限增加
description: 瞭解 .NET 6.0 中的重大變更，其中 NotifyIcon 的文字長度上限已增加。
ms.date: 01/19/2021
ms.openlocfilehash: 0029556f3ec2795fb079575b329e7fbd187d486f
ms.sourcegitcommit: 632818f4b527e5bf3c48fc04e0c7f3b4bdb8a248
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2021
ms.locfileid: "98617988"
---
# <a name="notifyicontext-maximum-text-length-increased"></a><span data-ttu-id="89304-103">NotifyIcon。文字長度上限增加</span><span class="sxs-lookup"><span data-stu-id="89304-103">NotifyIcon.Text maximum text length increased</span></span>

<span data-ttu-id="89304-104">屬性所允許的最大文字長度（ <xref:System.Windows.Forms.NotifyIcon.Text?displayProperty=nameWithType> 從63增加到127）。</span><span class="sxs-lookup"><span data-stu-id="89304-104">The maximum text length allowed for the <xref:System.Windows.Forms.NotifyIcon.Text?displayProperty=nameWithType> property increased from 63 to 127.</span></span>

## <a name="change-description"></a><span data-ttu-id="89304-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="89304-105">Change description</span></span>

<span data-ttu-id="89304-106">在先前的 .NET 版本中，屬性允許的最大文字長度 <xref:System.Windows.Forms.NotifyIcon.Text?displayProperty=nameWithType> 為63個字元。</span><span class="sxs-lookup"><span data-stu-id="89304-106">In previous .NET versions, the maximum text length allowed for the <xref:System.Windows.Forms.NotifyIcon.Text?displayProperty=nameWithType> property is 63 characters.</span></span> <span data-ttu-id="89304-107">從 .NET 6.0 開始，允許的文字長度上限是127個字元。</span><span class="sxs-lookup"><span data-stu-id="89304-107">Starting in .NET 6.0, the maximum allowed text length is 127 characters.</span></span> <span data-ttu-id="89304-108">在任何版本中， <xref:System.ArgumentException> 當您嘗試設定的值超過限制時，就會擲回。</span><span class="sxs-lookup"><span data-stu-id="89304-108">In any version, an <xref:System.ArgumentException> is thrown when you attempt to set a value that's longer than the limit.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="89304-109">變更的原因</span><span class="sxs-lookup"><span data-stu-id="89304-109">Reason for change</span></span>

<span data-ttu-id="89304-110">允許的文字長度上限已增加，使其與 [基礎 WINDOWS API](/windows/win32/api/shellapi/ns-shellapi-notifyicondataw#nif_showtip-0x00000080)對齊。</span><span class="sxs-lookup"><span data-stu-id="89304-110">The maximum allowed text length was increased to be in line with the [underlying Windows API](/windows/win32/api/shellapi/ns-shellapi-notifyicondataw#nif_showtip-0x00000080).</span></span> <span data-ttu-id="89304-111">Windows API 在 Windows 2000 中已更新，但由於相容性的緣故，此屬性的大小限制未在 .NET Framework 中更新。</span><span class="sxs-lookup"><span data-stu-id="89304-111">The Windows API was updated in Windows 2000, but due to compatibility reasons, the size limit for this property wasn't updated in .NET Framework.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="89304-112">引進的版本</span><span class="sxs-lookup"><span data-stu-id="89304-112">Version introduced</span></span>

<span data-ttu-id="89304-113">.NET 6.0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="89304-113">.NET 6.0 Preview 1</span></span>

## <a name="recommended-action"></a><span data-ttu-id="89304-114">建議的動作</span><span class="sxs-lookup"><span data-stu-id="89304-114">Recommended action</span></span>

<span data-ttu-id="89304-115">如有必要，請檢查您的程式碼，並放寬任何現有的防護條件。</span><span class="sxs-lookup"><span data-stu-id="89304-115">Review your code and relax any existing guard conditions, if necessary.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="89304-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="89304-116">Affected APIs</span></span>

<xref:System.Windows.Forms.NotifyIcon.Text?displayProperty=fullName>

<!--

### Affected APIs

- `P:System.Windows.Forms.NotifyIcon.Text`

### Category

Windows Forms

-->
