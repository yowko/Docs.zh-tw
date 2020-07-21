---
title: 風險降低：自訂 IMessageFilter.PreFilterMessage 實作
description: 瞭解以 .NET Framework 4.6.1 和更新版本為目標 Windows Forms 應用程式中所包含的自訂 Imessagefilter.prefiltermessage Imessagefilter.prefiltermessage 實作。
ms.date: 03/30/2017
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
ms.openlocfilehash: 5fe7500d3ed6ff293514495df150a747e7946dda
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475251"
---
# <a name="mitigation-custom-imessagefilterprefiltermessage-implementations"></a><span data-ttu-id="e607e-103">風險降低：自訂 IMessageFilter.PreFilterMessage 實作</span><span class="sxs-lookup"><span data-stu-id="e607e-103">Mitigation: Custom IMessageFilter.PreFilterMessage Implementations</span></span>

<span data-ttu-id="e607e-104">在以 .NET Framework 4.6.1 和之後 .NET Framework 版本為目標的 Windows Forms 應用程式中，自訂的 <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> 實作可以在呼叫 <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> 方法時安全地篩選訊息 (如果 <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> 實作有下列狀況)：</span><span class="sxs-lookup"><span data-stu-id="e607e-104">In Windows Forms apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1, a custom <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation can safely filter messages when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> method is called if the <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation:</span></span>

- <span data-ttu-id="e607e-105">則會執行下列其中一項或兩項：</span><span class="sxs-lookup"><span data-stu-id="e607e-105">Does one or both of the following:</span></span>

  - <span data-ttu-id="e607e-106">呼叫 <xref:System.Windows.Forms.Application.AddMessageFilter%2A> 方法來加入訊息篩選器。</span><span class="sxs-lookup"><span data-stu-id="e607e-106">Adds a message filter by calling the <xref:System.Windows.Forms.Application.AddMessageFilter%2A> method.</span></span>

  - <span data-ttu-id="e607e-107">呼叫 <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> 方法來移除訊息篩選器。</span><span class="sxs-lookup"><span data-stu-id="e607e-107">Removes a message filter by calling the <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> method.</span></span> <span data-ttu-id="e607e-108">方法。</span><span class="sxs-lookup"><span data-stu-id="e607e-108">method.</span></span>

- <span data-ttu-id="e607e-109">**並且**呼叫 <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> 方法來激發訊息。</span><span class="sxs-lookup"><span data-stu-id="e607e-109">**And** pumps messages by calling the <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> method.</span></span>

## <a name="impact"></a><span data-ttu-id="e607e-110">影響</span><span class="sxs-lookup"><span data-stu-id="e607e-110">Impact</span></span>

<span data-ttu-id="e607e-111">這項變更只會影響以 .NET Framework 4.6.1 和更新版本為目標的 Windows Forms 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e607e-111">This change only affects Windows Forms apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1.</span></span>

<span data-ttu-id="e607e-112">針對以舊版 .NET Framework 為目標的 Windows Forms 應用程式，在某些情況下這類實作會在呼叫 <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> 方法時擲回 <xref:System.IndexOutOfRangeException> 例外狀況</span><span class="sxs-lookup"><span data-stu-id="e607e-112">For Windows Forms apps that target previous versions of the .NET Framework, such implementations in some cases throw an <xref:System.IndexOutOfRangeException> exception when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> method is called</span></span>

## <a name="mitigation"></a><span data-ttu-id="e607e-113">降低</span><span class="sxs-lookup"><span data-stu-id="e607e-113">Mitigation</span></span>

<span data-ttu-id="e607e-114">如果不需要這項變更，以 .NET Framework 4.6.1 或更新版本為目標的應用程式可以藉由在 [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) 應用程式佈建檔的區段中新增下列設定，來選擇不使用此項：</span><span class="sxs-lookup"><span data-stu-id="e607e-114">If this change is undesirable, apps that target the .NET Framework 4.6.1 or a later version can opt out of it by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=true" />
</runtime>
```

<span data-ttu-id="e607e-115">此外，以舊版 .NET Framework 為目標但在 .NET Framework 4.6.1 或更新版本下執行的應用程式，可以藉由在 [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) 應用程式佈建檔的區段中新增下列設定，來加入宣告此行為：</span><span class="sxs-lookup"><span data-stu-id="e607e-115">In addition, apps that target previous versions of the .NET Framework but are running under the .NET Framework 4.6.1 or a later version can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=false" />
</runtime>
```

## <a name="see-also"></a><span data-ttu-id="e607e-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e607e-116">See also</span></span>

- [<span data-ttu-id="e607e-117">應用程式相容性</span><span class="sxs-lookup"><span data-stu-id="e607e-117">Application compatibility</span></span>](application-compatibility.md)
