---
title: 風險降低：自訂 IMessageFilter.PreFilterMessage 實作
ms.date: 03/30/2017
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
ms.openlocfilehash: 7757e8d1fd0258ab2d972b7321082e4afa37f710
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400117"
---
# <a name="mitigation-custom-imessagefilterprefiltermessage-implementations"></a><span data-ttu-id="b0a13-102">風險降低：自訂 IMessageFilter.PreFilterMessage 實作</span><span class="sxs-lookup"><span data-stu-id="b0a13-102">Mitigation: Custom IMessageFilter.PreFilterMessage Implementations</span></span>

<span data-ttu-id="b0a13-103">在以 .NET Framework 4.6.1 和之後 .NET Framework 版本為目標的 Windows Forms 應用程式中，自訂的 <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> 實作可以在呼叫 <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> 方法時安全地篩選訊息 (如果 <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> 實作有下列狀況)：</span><span class="sxs-lookup"><span data-stu-id="b0a13-103">In Windows Forms apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1, a custom <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation can safely filter messages when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> method is called if the <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> implementation:</span></span>

- <span data-ttu-id="b0a13-104">則會執行下列其中一項或兩項：</span><span class="sxs-lookup"><span data-stu-id="b0a13-104">Does one or both of the following:</span></span>

  - <span data-ttu-id="b0a13-105">呼叫 <xref:System.Windows.Forms.Application.AddMessageFilter%2A> 方法來加入訊息篩選器。</span><span class="sxs-lookup"><span data-stu-id="b0a13-105">Adds a message filter by calling the <xref:System.Windows.Forms.Application.AddMessageFilter%2A> method.</span></span>

  - <span data-ttu-id="b0a13-106">呼叫 <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> 方法來移除訊息篩選器。</span><span class="sxs-lookup"><span data-stu-id="b0a13-106">Removes a message filter by calling the <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A> method.</span></span> <span data-ttu-id="b0a13-107">方法。</span><span class="sxs-lookup"><span data-stu-id="b0a13-107">method.</span></span>

- <span data-ttu-id="b0a13-108">**並且**呼叫 <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> 方法來激發訊息。</span><span class="sxs-lookup"><span data-stu-id="b0a13-108">**And** pumps messages by calling the <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> method.</span></span>

## <a name="impact"></a><span data-ttu-id="b0a13-109">影響</span><span class="sxs-lookup"><span data-stu-id="b0a13-109">Impact</span></span>

<span data-ttu-id="b0a13-110">這項變更只會影響以 .NET Framework 4.6.1 和更新版本為目標的 Windows Forms 應用程式。</span><span class="sxs-lookup"><span data-stu-id="b0a13-110">This change only affects Windows Forms apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1.</span></span>

<span data-ttu-id="b0a13-111">針對以舊版 .NET Framework 為目標的 Windows Forms 應用程式，在某些情況下這類實作會在呼叫 <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> 方法時擲回 <xref:System.IndexOutOfRangeException> 例外狀況</span><span class="sxs-lookup"><span data-stu-id="b0a13-111">For Windows Forms apps that target previous versions of the .NET Framework, such implementations in some cases throw an <xref:System.IndexOutOfRangeException> exception when the <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> method is called</span></span>

## <a name="mitigation"></a><span data-ttu-id="b0a13-112">降低</span><span class="sxs-lookup"><span data-stu-id="b0a13-112">Mitigation</span></span>

<span data-ttu-id="b0a13-113">如果此更改不可取，則針對 .NET Framework 4.6.1 或更高版本的應用可以通過將以下配置設置添加到應用設定檔的[\<運行時>](../configure-apps/file-schema/runtime/runtime-element.md)部分來退出宣告：</span><span class="sxs-lookup"><span data-stu-id="b0a13-113">If this change is undesirable, apps that target the .NET Framework 4.6.1 or a later version can opt out of it by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=true" />
</runtime>
```

<span data-ttu-id="b0a13-114">此外，針對 .NET Framework 的早期版本但在 .NET Framework 4.6.1 或更高版本下運行的應用可以加入宣告此行為，將以下配置設置添加到應用設定檔的[\<運行時>](../configure-apps/file-schema/runtime/runtime-element.md)部分：</span><span class="sxs-lookup"><span data-stu-id="b0a13-114">In addition, apps that target previous versions of the .NET Framework but are running under the .NET Framework 4.6.1 or a later version can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=false" />
</runtime>
```

## <a name="see-also"></a><span data-ttu-id="b0a13-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0a13-115">See also</span></span>

- [<span data-ttu-id="b0a13-116">應用程式相容性</span><span class="sxs-lookup"><span data-stu-id="b0a13-116">Application compatibility</span></span>](application-compatibility.md)
